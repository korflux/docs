# zNyx Discord Bot - Documentação Técnica Avançada

**Versão:** 1.0.0
**Stack:** Node.js, Discord.js v14
**Arquitetura:** Modular Event-Driven

Esta documentação técnica destina-se a desenvolvedores e mantenedores. Ela detalha não apenas *o que* o bot faz, mas *como* ele funciona internamente, decisões de design, algoritmos utilizados e fluxo de dados.

---

## 1. Arquitetura do Sistema

O zNyx opera sob uma arquitetura de microsserviços monolíticos, onde cada "sistema" (Tickets, Sorteios) funciona como um módulo isolado com sua própria persistência e regras de negócio, mas compartilhando o mesmo runtime e barramento de eventos.

### Diagrama de Componentes

```mermaid
graph TD
    %% Core Layer
    Gateway[Discord Gateway] --> EventHandler
    EventHandler --> Router{Interaction Router}
    
    %% Routing Layer
    Router -- /Slash --> CmdHandler[Command Handler]
    Router -- Btn/Modal --> InteractionHandlers
    
    subgraph InteractionHandlers [Handlers de Interação]
        UH[Utility Handler]
        TH[Ticket Handler]
        RH[Review Handler]
        GH[Giveaway Handler]
    end

    %% Service Layer
    subgraph Services [Camada de Serviço]
        GS[Giveaway Service]
        TS[Ticket Service]
        SS[Status Service] --> |API Ext| McStatus[mcstatus.io]
    end
    
    CmdHandler --> Services
    InteractionHandlers --> Services

    %% Data Layer
    subgraph Persistence [Persistência (Write-Behind)]
        GStore[Giveaway Store]
        TStore[Ticket Store]
        SStore[Status Store]
        Cache[Cache Manager]
    end
    
    Services --> Persistence
```

### Padrões de Projeto Adotados

1.  **Singleton Pattern**: Aplicado nos *Stores* e *Services*. O Node.js garante que o `require` retorne a mesma instância do módulo, mantendo o estado (cache) consistente em toda a aplicação.
2.  **Write-Behind Caching**: Para evitar bloqueio do Event Loop com I/O de disco, toda escrita é feita primeiro na memória e agendada para o disco com um atraso (Debounce).
3.  **Factory Pattern**: Utilizado no `embedBuilder.js` para criar objetos visuais padronizados.
4.  **Strategy Pattern**: O `interactionCreate.js` atua como um Context que seleciona a Estratégia (Handler) correta baseada no tipo de interação e CustomID.

---

## 2. Análise Profunda: Core Engine

### Cache Manager (`src/services/cacheManager.js`)
O coração da performance do bot. Ele abstrai o sistema de arquivos para operações de zero-latência.

*   **Algoritmo de Escrita:**
    Ao chamar `updateCache`, o dado é atualizado na memória imediatamente (`dirty = true`). Um temporizador (`setTimeout`) é iniciado para 1000ms. Se novas escritas ocorrerem nesse período, o timer é resetado (Debounce). Isso converte múltiplas escritas sequenciais (ex: 50 pessoas entrando num sorteio simultaneamente) em apenas **uma** operação de disco.
*   **Integridade:**
    No evento de desligamento (`SIGINT`/`SIGTERM`), a função `flushAll()` é invocada sincronicamente, forçando a persistência de todos os caches marcados como `dirty` antes do processo morrer.

### Interaction Router (`src/events/interactionCreate.js`)
Centraliza o controle de fluxo. Ao contrário de frameworks que espalham lógica, o zNyx centraliza o roteamento para facilitar debugging.
*   **Utility Handler:** Lógicas simples (stateless) como "Copiar PIX" ou "Link Promocional" foram segregadas para `utilityHandler.js` para manter o Router limpo.

---

## 3. Deep Dive: Regras de Negócio

### 🎲 Sistema de Sorteios (`giveawayService.js`)
*   **Seleção de Ganhadores:** Utiliza o algoritmo **Fisher-Yates Shuffle** para garantir aleatoriedade imparcial e sem repetição na seleção de múltiplos ganhadores.
    ```javascript
    // Exemplo simplificado da lógica interna
    for (let i = pool.length - 1; i > 0; i--) {
        const j = Math.floor(Math.random() * (i + 1));
        [pool[i], pool[j]] = [pool[j], pool[i]];
    }
    return pool.slice(0, winnersCount);
    ```
*   **Reroll Inteligente:** O sistema mantém um histórico de `previousWinners` no JSON. Ao solicitar um reroll, os ganhadores anteriores são adicionados a uma "lista negra" temporária para garantir que o novo sorteio não selecione a mesma pessoa novamente.

### 🎫 Sistema de Tickets (`ticketStore.js` & `ticketLogService.js`)
*   **Geração de IDs:** Utiliza `uuidv4` truncado (8 caracteres) para IDs de categorias, garantindo unicidade suficiente dentro do escopo de um servidor sem URLs gigantes.
*   **Audit Logs:** O `ticketLogService` gera um arquivo `.txt` em memória (`Buffer`) contendo o transcript completo. Datas são formatadas usando `Intl.DateTimeFormat` com o locale configurado (`pt-BR`), garantindo consistência legal/auditoria.

### 📊 Monitor de Status (`statusService.js`)
*   **Cache de API:** Para respeitar Rate Limits da API `mcstatus.io` e evitar lag no Discord, o serviço implementa um cache interno de 60 segundos por IP. Requisições repetidas para o mesmo servidor dentro desse intervalo retornam o dado em memória instantaneamente.

---

## 4. Integração Discord + n8n (`connectionService.js`)

Sistema que permite conectar canais do Discord a fluxos de automação n8n via webhooks, transformando o bot em um gateway para agentes de IA.

**Fluxo de Dados:**
1.  Usuário envia mensagem no canal monitorado.
2.  `messageCreate.js` intercepta e verifica se há conexão ativa no `connectionStore`.
3.  Se houver, o bot envia um POST para o Webhook do n8n com o payload JSON.
4.  O payload inclui `messageId` (para reply), `userId`, `content`, `attachments`, etc.
5.  O n8n processa e responde usando a API do Discord (nó "Discord" ou nó "HTTP Request").

**Payload Enviado:**
```json
{
  "messageId": "123456...",
  "userId": "User ID",
  "username": "User Name",
  "content": "Mensagem do usuário",
  "channelId": "Channel ID",
  "guildId": "Guild ID",
  "timestamp": "ISO Date"
}
```

---

## 5. Estrutura de Dados (JSON Schemas)

Os dados são armazenados em `src/data/`. A estrutura é normalizada por `guildId` para permitir sharding/multitenancy futuro.

**`store.json`** (Configurações Gerais)
```json
{
  "suggestions": {
    "GUILD_ID": {
      "analyzeChannelId": "ID",
      "resultChannelId": "ID"
    }
  },
  "status": {
    "GUILD_ID": {
      "servers": ["hypixel.net"],
      "channelId": "ID"
    }
  },
  "connectionConfig": {
    "GUILD_ID": {
      "CHANNEL_ID": {
        "webhookUrl": "https://n8n...",
        "monitorMode": "all" // ou "mentions"
      }
    }
  }
}
```

**`giveaways.json`** (Estado dos Sorteios)
```json
{
  "MESSAGE_ID": {
    "guildId": "ID",
    "channelId": "ID",
    "prize": "Vip",
    "winnersCount": 1,
    "endsAt": TIMESTAMP,
    "participants": ["USER_ID_1", "USER_ID_2"],
    "winners": [],
    "status": "active" // ou "ended"
  }
}
```

---

## 6. Referência de Configuração e Constantes

### Internacionalização (`src/config/index.js`)
O bot suporta configuração centralizada de localidade.
*   `locale.language`: Padrão `'pt-BR'`
*   `locale.timezone`: Padrão `'America/Sao_Paulo'`
*   *Impacto:* Afeta logs de tickets, datas de expiração de promoções e sorteios.

### Cores e Estilo
*   **Cores (`src/constants/colors.js`):**
    *   `SUCCESS` (#15cb18): Operações bem sucedidas.
    *   `ERROR` (#ff4444): Erros de validação ou sistema.
    *   `WARNING` (#ffaa00): Alertas de manutenção.
    *   `INFO` (#5865F2): Informações neutras.

### Tokens de Comando
Valores especiais processados pelo `utils/formatters.js`:
*   `padrao#`: Reseta uma configuração para o valor default do `constants/defaults.js`.
*   `remover#`: Remove uma configuração opcional (define como null).

---

## 7. Fluxos de Eventos Internos

1.  **Inicialização (`ready.js`):**
    *   Inicia Cron Jobs (`setInterval`) para: Sorteios (30s), Promos (60s), Status (10m).
    *   Executa `sanitizeAll()`: Varredura pesada que remove referências a canais/mensagens deletados do banco de dados para evitar "lixo" acumulado.

2.  **Criação de Tópicos (`messageCreate.js`):**
    *   Verifica `isTopicChannel(channelId)`. Se verdadeiro, cria uma Thread automaticamente para cada nova mensagem, ideal para canais de sugestões/bugs sem comandos.

---

---

## 8. Catálogo de Comandos

Lista detalhada de todos os comandos Slash disponíveis, organizados por categoria.

### 📢 Anúncios e Promoções
| Comando | Subcomando | Descrição | Permissão |
|---------|-----------|-----------|-----------|
| `/anunciar` | - | Envia um embed personalizado no canal (suporta imagem, cor, rodapé). | Manage Messages |
| `/editanunciar` | - | Edita o conteúdo de uma mensagem enviada pelo bot. | Manage Messages |
| `/pix` | `exibir` | Mostra a chave PIX e QR Code configurados. | Public |
| `/pix` | `configurar` | Define a chave PIX, nome do beneficiário e cidade. | Administrator |
| `/promo` | `criar` | Gera um cupom de desconto com validade e limite de uso. | Administrator |
| `/promo` | `listar` | Lista cupons ativos. | Administrator |

### 🎲 Sorteios (Giveaways)
| Comando | Subcomando | Descrição | Permissão |
|---------|-----------|-----------|-----------|
| `/sortear` | - | Inicia um sorteio com duração, prêmio e requisitos (tempo de call, cargos). | Manage Guild |
| `/reroll` | - | Seleciona um novo ganhador para um sorteio finalizado (exclui ganhadores anteriores). | Manage Guild |

### 🎫 Tickets e Suporte
| Comando | Subcomando | Descrição | Permissão |
|---------|-----------|-----------|-----------|
| `/ticket` | `painel` | Envia o painel de abertura de tickets com select menu de categorias. | Administrator |
| `/fecharticket` | - | Fecha o ticket atual, gera transcript.txt e deleta o canal após 5s. | Public (Ticket) |
| `/categorias` | `adicionar` | Cria uma nova categoria de suporte. | Administrator |
| `/categorias` | `editar` | Edita emoji, título ou cargos de uma categoria. | Administrator |
| `/categorias` | `listar` | Exibe IDs e configurações das categorias. | Administrator |
| `/categorias` | `remover` | Deleta uma categoria existente. | Administrator |

### 📊 Status e Manutenção
| Comando | Subcomando | Descrição | Permissão |
|---------|-----------|-----------|-----------|
| `/status` | `adicionar` | Adiciona monitoramento de um servidor (IP) em um canal. | Administrator |
| `/status` | `remover` | Remove o monitoramento. | Administrator |
| `/manutencao` | `ativar` | Bloqueia interações públicas e exibe status de manutenção. | Administrator |
| `/manutencao` | `desativar` | Restaura o funcionamento normal. | Administrator |

### 💡 Sugestões e Avaliações
| Comando | Subcomando | Descrição | Permissão |
|---------|-----------|-----------|-----------|
| `/sugestao` | - | Envia uma sugestão para o canal configurado (com votação automática). | Public |
| `/resultado` | - | Aprova ou rejeita uma sugestão, notificando o autor. | Manage Guild |
| `/avaliacao` | `painel` | Envia o painel de "Avalie nosso Atendimento" (relatório público). | Administrator |
| `/responder` | - | Responde a uma avaliação específica. | Manage Guild |

### 📡 Integração e Utilidades
| Comando | Subcomando | Descrição | Permissão |
|---------|-----------|-----------|-----------|
| `/conexao` | `adicionar` | Conecta um canal a um webhook n8n para Agentes de IA. | Administrator |
| `/conexao` | `configurar` | Exibe manual de configuração do n8n (Payloads/JSON). | Administrator |
| `/topicos` | `configurar` | Ativa criação automática de Threads para todas as mensagens do canal. | Administrator |

---

## 9. Guia de Manutenção e Extensão

### Adicionar Novo Comando
1.  Crie o arquivo em `src/commands/<categoria>/<nome>.js`.
2.  Exporte `data` (SlashCommandBuilder) e `execute`.
3.  O `commandHandler` carregará automaticamente.

### Adicionar Nova Interação (Botão)
1.  Defina o `customId` no botão (ex: `action:arg1`).
2.  Se for utilitário simples, adicione ao `utilityHandler.js`.
3.  Se for complexo, crie um novo Handler em `src/handlers/interactions/` e registre no `interactionCreate.js`.

### Validar Mudanças
Sempre verifique o console. O `logger.js` estrutura erros com Stack Trace e Contexto (UserID, GuildID), facilitando o rastreio de bugs.

---

## 10. Catálogo de Arquivos (File Reference)

Referência rápida de responsabilidade por arquivo.

### `/src/config` & `/src/constants`
- **`config/index.js`**: Centraliza configs globais (Nome do bot, Versão, Locale, Timezone).
- **`constants/colors.js`**: Paleta de cores HEX (SUCCESS, ERROR, WARNING, INFO).
- **`constants/defaults.js`**: Objetos de configuração padrão para cada sistema (usados em resets).
- **`constants/messages.js`**: Textos padronizados de erro, sucesso e templates (PIX).

### `/src/handlers`
- **`commandHandler.js`**: Carregador recursivo de Slash Commands.
- **`eventHandler.js`**: Carregador recursivo de Eventos do Discord.
- **`interactions/giveawayHandler.js`**: Lógica de entrada/saída de sorteios (botões).
- **`interactions/reviewHandler.js`**: Menus de seleção e modais de avaliações.
- **`interactions/suggestionHandler.js`**: Modais e submissão de sugestões.
- **`interactions/ticketHandler.js`**: Abertura, fechamento e controle de tickets.
- **`interactions/utilityHandler.js`**: Ações genéricas (Copiar PIX/Cupom, Links).

### `/src/services` (Lógica e Dados)
- **`cacheManager.js`**: Engine de persistência com debounce e I/O não-bloqueante.
- **`connectionService.js`**: Motor de integração n8n (payload builder, envio webhook).
- **`connectionStore.js`**: Configs de conexões n8n (`store.json`).
- **`dataStore.js`**: Store para dados gerais (Tópicos) e orquestrador de sanitização.
- **`giveawayService.js`**: Motor de sorteios (Cron, Sorteio, Reroll).
- **`giveawayStore.js`**: Acesso a dados de sorteios (`giveaways.json`).
- **`promoService.js`**: Motor de cupons (Cron de expiração).
- **`promoStore.js`**: Acesso a dados de cupons (`promos.json`).
- **`statusService.js`**: Cliente da API mcstatus.io e gerador de embeds.
- **`statusStore.js`**: Configs de monitoramento (`store.json`).
- **`reviewStore.js`**: Configs e dados de avaliações (`store.json`).
- **`suggestionStore.js`**: Configs e dados de sugestões (`store.json`).
- **`ticketStore.js`**: Configs, categorias e tickets ativos (`tickets.json`).
- **`ticketLogService.js`**: Gerador de transcript (.txt) para tickets.

### `/src/utils`
- **`embedBuilder.js`**: Fábrica de Embeds (padroniza títulos, footers, timestamps).
- **`formatters.js`**: Formatação de tempo, strings e tokens especiais.
- **`logger.js`**: Logger estruturado com níveis e sanitização de dados.
- **`responseHandler.js`**: Helpers para respostas uniformes (`safeReply`, `replyError`).
- **`validators.js`**: Validação de inputs (Regex de Cores, URLs).