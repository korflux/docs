# 🤖 zNyx - Documentação Oficial

> **Bem-vindo à documentação oficial do zNyx**

## 🤖 O que é o zNyx?

O **zNyx** é a ferramenta definitiva para elevar o padrão da sua comunidade de Minecraft. Desenvolvido com foco em performance e personalização, ele centraliza a gestão do servidor, engajamento e suporte em uma única interface moderna.

Mais do que um bot, é uma solução completa para profissionalizar a comunicação e monetização do seu projeto.

* [**Suporte & Contato**](https://discord.gg/3Mz97UjDta): Entre em contato diretamente comigo para dúvidas ou suporte.

## ⚡ Resumo de Recursos

O zNyx centraliza todas as ferramentas que seu servidor precisa em um único lugar:

- **📢 Anúncios**: Envie comunicados visuais, edite mensagens e crie cards de PIX ou Promoção.
- **🎟️ Tickets**: Suporte organizado com categorias, cargos de staff e logs automáticos (Transcripts).
- **📊 Monitoramento**: Painéis de status em tempo real para seus servidores com atualização automática.
- **🎁 Sorteios**: Sistema seguro com requisitos de cargo e proteção anti-fraude.
- **🔗 Automação**: Conexão nativa com n8n para integrar Agentes de IA nos canais do seu servidor.
- **💡 Engajamento**: Sistemas de Sugestões, Avaliações e criação automática de Tópicos (Threads).

---

# 💎 Planos e Preços

O **zNyx** foi desenhado para escalar junto com o seu projeto. Oferecemos duas tiers focadas em momentos diferentes e um serviço adicional para quem quer potência máxima em IA sem dor de cabeça com infraestrutura.

### 🌟 Plano Plus
A base sólida para servidores que buscam organização e estética profissional. Ideal para comunidades em crescimento.

### 👑 Plano Pro
A experiência definitiva com automação, white-label total e recursos ilimitados para grandes redes.

## Comparativo de Planos

| Recurso | Plano Plus | Plano Pro |
| :--- | :---: | :---: |
| **Investimento Mensal** | **R$ 29,90** | **R$ 79,90** |
| Tempo de Resposta (SLA) | 24h | ⚡ 4h |
| Atualizações Globais | ✅ | ✅ |
| Auto-Restart | ✅ | ✅ |
| Monitoramento Proativo | ✅ | ✅ |
| **Identidade & Branding** | | |
| Identidade Visual (Embeds) | **zNyx Branding** (Fixo) | 🎨 **WhiteLabel Completo** |
| Customização de Rodapé | ❌ Assinatura Fixa | ✅ Totalmente Livre |
| **Anúncios & Vendas** | | |
| `/anuncio padrao` | ✅ (Modal) | ✅ (Modal) |
| `/anuncio editar` | ❌ | ✅ |
| `/anuncio pix` | ✅ | ✅ |
| `/anuncio promo` | ❌ | ✅ |
| **Engajamento & Suporte** | | |
| Sistema de Tickets | ✅ | ✅ |
| Sistema de Sugestões | ✅ | ✅ |
| Sistema de Avaliações | ❌ | ✅ |
| Sorteios Avançados | ❌ | ✅ |
| **Utilitários & Automação** | | |
| `/status` (Monitoramento) | 1 Servidor | ♾️ **Ilimitados** |
| `/status manutencao` | ❌ | ✅ |
| `/conexao` (Webhooks/IA) | ❌ | ✅ |
| `/topicos` (Threads Auto) | ❌ | ✅ |
| `/planos` (VIPs) | 2 Opções | 10 Opções |


# 📚 Referência de Comandos (Extremamente Detalhado)

O zNyx utiliza um sistema unificado. Subcomandos marcados com **PRO** possuem restrições ou são exclusivos.

## ⚙️ Configurações Globais (`/padrao`)
Gerencia a identidade visual e configurações base do bot no servidor.

| Subcomando | Descrição | Exemplo |
| :--- | :--- | :--- |
| `cor` | Define a cor lateral padrão (HEX) para todos os embeds enviadas pelo bot. | `/padrao cor valor:#15cb18` |
| `rodape` <Tooltip tip="Recurso exclusivo do Plano Pro">**PRO**</Tooltip> | Define o texto do rodapé padrão. Na versão Plus, este campo é fixado. | `/padrao rodape texto:Rede zNyx - O melhor survival` |
| `ver` | Exibe as configurações atuais de cor, rodapé e a versão ativa do bot. | `/padrao ver` |

---

## 📢 Anúncios e Vendas (`/anuncio`)
Sistema profissional para comunicados e automação de cobranças.

| Subcomando | Descrição | Exemplo |
| :--- | :--- | :--- |
| `padrao` | Abre um formulário (modal) para enviar um anúncio com descrição Markdown. | `/anuncio padrao cor:#FF0000` |
| `editar` <Tooltip tip="Recurso exclusivo do Plano Pro">**PRO**</Tooltip> | Altera o conteúdo de um anúncio já enviado. Requer o ID da mensagem. | `/anuncio editar mensagem_id:123...` |
| `pix` | Gera um card de pagamento visual com botão de copiar chave. | `/anuncio pix valor:50,00 chave:suachave` |
| `promo` <Tooltip tip="Recurso exclusivo do Plano Pro">**PRO**</Tooltip> | Cria um card de promoção com cronômetro e cupom de desconto. | `/anuncio promo desconto:20% cupom:ZNYX20` |

---

## 🎟️ Sistema de Tickets (`/ticket`)
Gestão de atendimento organizada com logs e categorias.

| Subcomando | Descrição | Exemplo |
| :--- | :--- | :--- |
| `configurar` | Define o canal de logs, categoria e configurações visuais do painel. | `/ticket configurar categoria:ID logs:#logs` |
| `iniciar` | Envia o embed de abertura de tickets no canal onde o comando for usado. | `/ticket iniciar` |
| `categorias adicionar` | Adiciona um novo tópico de atendimento ao menu de seleção. | `/ticket categorias adicionar emoji:🛠️ titulo:Suporte` |
| `categorias listar` | Lista todas as categorias configuradas para o painel de tickets. | `/ticket categorias listar` |
| `/fecharticket` | Encerra o ticket atual e gera o log (Transcript) automaticamente. | `/fecharticket` |

---

## 📊 Status de Servidores (`/status`)
Monitoramento em tempo real de servidores Minecraft.

| Subcomando | Descrição | Exemplo |
| :--- | :--- | :--- |
| `configurar` | Define os IPs dos servidores e o canal onde o painel ficará ativo. | `/status configurar servidores:jogar.znyx.com` |
| `iniciar` | Envia o painel de status e inicia a atualização automática (10min). | `/status iniciar` |
| `parar` | Interrompe o monitoramento e remove o painel de status do canal. | `/status parar` |
| `manutencao ligar` <Tooltip tip="Recurso exclusivo do Plano Pro">**PRO**</Tooltip> | Ativa o modo de manutenção global no painel de status. | `/status manutencao ligar texto:Limpando DB` |

---

## 🎁 Sorteios Avançados (`/sorteio`) <Tooltip tip="Recurso exclusivo do Plano Pro">**PRO**</Tooltip>
Sistema de sorteios com requisitos e proteção anti-fraude.

| Subcomando | Descrição | Exemplo |
| :--- | :--- | :--- |
| `criar` | Abre o configurador de sorteio (Data, Ganhadores, Cargos, Anti-fraude). | `/sorteio criar ganhadores:1 data:25/12/2026` |
| `reroll` | Escolhe um novo vencedor para um sorteio já finalizado. | `/sorteio reroll mensagem_id:123...` |

---

## 🔗 Automação e IA (`/conexao`) <Tooltip tip="Recurso exclusivo do Plano Pro">**PRO**</Tooltip>
Conecte seu servidor a fluxos do n8n ou Agentes de Inteligência Artificial.

| Subcomando | Descrição | Exemplo |
| :--- | :--- | :--- |
| `adicionar` | Define um canal para enviar mensagens a um Webhook externo. | `/conexao adicionar canal:#ia modo:mentions` |
| `listar` | Exibe todos os canais que possuem conexões ativas com Webhooks. | `/conexao listar` |

---

## 💬 Social e Prova Social

| Comando | Descrição | Exemplo |
| :--- | :--- | :--- |
| `/sugestao iniciar` | Envia o embed com botão para a comunidade sugerir melhorias. | `/sugestao iniciar` |
| `/sugestao resultado` | Define o veredito de uma sugestão (Aprovado/Reprovado) com motivo. | `/sugestao resultado id:123 decisao:aprovar` |
| `/avaliacao iniciar` <Tooltip tip="Recurso exclusivo do Plano Pro">**PRO**</Tooltip> | Envia o embed de coleta de avaliações e estrelas. | `/avaliacao iniciar` |
| `/topicos ativar` <Tooltip tip="Recurso exclusivo do Plano Pro">**PRO**</Tooltip> | Faz com que toda mensagem em um canal vire uma discussão (Thread). | `/topicos ativar canal:#midia` |

---

## 💎 Planos VIP (`/planos`)
Interface intuitiva para visualização e venda de VIPs.

| Subcomando | Descrição | Exemplo |
| :--- | :--- | :--- |
| `configurar` | Define o canal de chat oficial onde o embed de vendas será postado. | `/planos configurar chat:#vips` |
| `iniciar` | Envia o painel de planos configurados para os usuários. | `/planos iniciar` |

---

## 🛡️ Infraestrutura e Segurança

O zNyx foi construído para ser resiliente em ambientes de produção.

### Auto-Restart Nativo
O bot possui um sistema de vigilância (Watchdog) no container Docker:
- **Recuperação:** O bot reinicia automaticamente em **5 segundos** em caso de erro crítico.
- **Benefício:** Máxima disponibilidade (Uptime) sem intervenção manual.

### Monitoramento de Erros Proativo
Todo o bot é monitorado por uma camada de inteligência:
- **Dedupe:** Agrupa erros repetidos para evitar spam.
- **Diagnóstico:** A equipe de desenvolvimento recebe alertas em tempo real com o contexto exato da falha para correções rápidas.
