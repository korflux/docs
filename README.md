# 🤖 zNyx - Documentação Oficial

> **Bem-vindo à documentação oficial do zNyx**

## 🤖 O que é o zNyx?

O **zNyx** é a ferramenta definitiva para elevar o padrão da sua comunidade de Minecraft. Desenvolvido com foco em performance e personalização, ele centraliza a gestão do servidor, engajamento e suporte em uma única interface moderna.

Mais do que um bot, é uma solução completa para profissionalizar a comunicação e monetização do seu projeto.

* [**Suporte & Contato**](https://discord.gg/3Mz97UjDta): Entre em contato diretamente comigo para dúvidas ou suporte.

## ✨ Funcionalidades

Uma visão geral de tudo que o zNyx oferece para otimizar sua operação:

- **Anúncios e Monetização**: Crie comunicados visuais com embeds personalizados, gere cobranças de PIX facilitadas e cards de promoções profissionais.
- **Sorteios Seguros**: Sistema completo com requisitos de cargos, reroll inteligente e proteção anti-fraude para contas novas.
- **Sistema de Tickets**: Atendimento privado e organizado por categorias, com geração automática de logs (transcripts) para auditoria.
- **Monitoramento em Tempo Real**: Painéis de status que mostram ping e jogadores online dos seus servidores, com atualização automática.
- **Integração com n8n (IA)**: Conecte canais do Discord a fluxos de automação externos e agentes de Inteligência Artificial via Webhooks.
- **Sugestões e Votação**: Canal dedicado para feedback da comunidade com sistema de aprovação/reprovação pela staff.
- **Avaliações**: Coleta de feedbacks e prova social, com controle de quem pode avaliar e respostas públicas da equipe.
- **Configuração Global**: Defina cores e rodapés padrão para manter a identidade visual da sua marca em todos os comandos.
- **Organização de Tópicos**: Transformação automática de mensagens em threads para manter canais de mídia e divulgação limpos.

---

# 💎 Planos e Preços

O **zNyx** foi desenhado para escalar junto com o seu projeto. Oferecemos duas tiers focadas em momentos diferentes e um serviço adicional para quem quer potência máxima em IA sem dor de cabeça com infraestrutura.

### 🌟 Plano Plus
A base sólida para servidores que buscam organização e estética profissional.

### 👑 Plano Pro
A experiência definitiva com automação, white-label total e prioridade.

## Comparativo de Recursos

| Recurso | Plano Plus | Plano Pro |
| :--- | :---: | :---: |
| **Investimento Mensal** | **R$ 29,90** | **R$ 79,90** |
| **Suporte & Evolução** | | |
| Canal de Suporte | Ticket | Ticket |
| Tempo de Resposta (SLA) | 48h Úteis | ⚡ **12h Úteis** |
| Atualizações Globais | ✅ Gratuitas | ✅ Gratuitas |
| Uptime Garantido | 99,9% | 99,9% |
| **Identidade & Branding** | | |
| Identidade Visual (Embeds) | **zNyx Branding** (Fixo) | 🎨 **WhiteLabel Completo** |
| Config do Rodapé (`/padrao`) | ❌ (Bloqueado) | ✅ (Personalizável) |
| **Gestão & Utilitários** | | |
| `/anunciar` (Painel Interativo) | ✅ | ✅ |
| `/editanunciar` (Correção) | ❌ | ✅ |
| `/pix` (Embed Visual) | ✅ | ✅ |
| `/promo` (Embed Visual) | ❌ | ✅ |
| **Atendimento & Engajamento** | | |
| Sistema de Tickets | ✅ | ✅ |
| Sistema de Sugestões | ✅ | ✅ |
| Avaliações (`/avaliacao`) | ❌ | ✅ |
| Sorteios (`/sortear`) | ❌ | ✅ |
| Tópicos Automáticos | ❌ | ✅ |
| **Monitoramento & Automação** | | |
| `/status` (Painel em Tempo Real) | 1 Servidor | **Ilimitado** |
| Modo Manutenção | ❌ | ✅ |
| `/conexão` (Suporte a n8n) | ❌ | ✅ |
| **Planos & VIPs** | | |
| Max. Planos VIPs | 2 Planos | 10 Planos |

> **Nota sobre o Plano Plus:** O rodapé dos embeds manterá a assinatura fixa: *"Desenvolvido por znyx.com.br"*. Apenas o Plano Pro permite remover ou alterar essa assinatura via `/padrao`.

---

### 🧠 Add-on: WorkFlow AI (+ R$ 20,00 / Flow)
*Exclusivo para assinantes do Plano Pro.*

Quer usar Inteligência Artificial no seu Discord mas não tem onde hospedar o n8n ou não sabe configurar a segurança? Nós cuidamos disso.

Por um valor adicional, hospedamos e gerenciamos seu fluxo de IA com alto padrão de qualidade.

* **Hospedagem Premium:** Sem custo extra com VPS ou servidores.
* **Segurança Avançada:** Configuração com GuardRails para evitar respostas tóxicas ou alucinações da IA.
* **System Prompt Personalizado:** Ajustamos a personalidade do agente para falar exatamente como sua marca.
* **Pronto para Usar:** Entregamos o Webhook pronto para conectar no `/conexão`.

> **Ideal para:** Donos de servidores que querem um Chatbot de suporte inteligente ou NPC interativo, mas não querem lidar com a complexidade técnica de servidores externos.

---

# 📚 Documentação dos Comandos

Abaixo você encontra a referência técnica detalhada de todos os comandos disponíveis no zNyx.

## ⚙️ Configuração Global (Novo)

Ferramenta essencial para administradores definirem a identidade visual do servidor uma única vez.

### `/padrao`
Define valores que serão preenchidos automaticamente em todos os embeds do bot (Anúncios, Tickets, Status, etc), garantindo consistência visual e economizando tempo.
- **Subcomandos:**
  - `cor`: Define a cor lateral padrão (HEX).
    - *Ex:* `/padrao cor valor:#FF00AA`
  - `rodape`: Define o texto do rodapé. **(Exclusivo Plano Pro)**
    - *Ex:* `/padrao rodape texto:Rede zNyx - O melhor survival`
  - `ver`: Mostra as configurações atuais e a versão do bot.
- **Dica de Power User:** Use o valor especial `padrao#` em qualquer comando individual para forçar o uso dessa configuração global.

---

## 📢 Anúncios e Promoções

Ferramentas para comunicar novidades, promoções e solicitar pagamentos de forma profissional.

### `/anunciar`
Envia um anúncio personalizado no canal atual através de um painel interativo.
- **Como usar:** Digite o comando e preencha as opções opcionais. O bot pedirá o texto do anúncio em seguida.
- **Opções:**
  - `cor` (Opcional): Cor da lateral do embed em HEX (ex: `#FF0000`). Padrão: Verde ou Global.
  - `rodape` (Opcional): Texto pequeno no rodapé do anúncio.
  - `imagem` (Opcional): URL de uma imagem ou GIF para ilustrar o anúncio (Banner).

### `/editanunciar`
Edita um anúncio já enviado pelo bot, ideal para correções rápidas sem perder reações.
- **Opções:**
  - `mensagem_id` (Obrigatório): O ID da mensagem do anúncio (ative o Modo Desenvolvedor do Discord para pegar).
  - `manter_descricao` (Opcional): `True` para manter o texto atual, `False` para escrever um novo.
  - `cor`, `rodape`, `imagem` (Opcional): Novos valores para atualizar.
  - **Tokens Especiais:** Use `padrao#` para resetar para o global ou `remover#` para excluir o campo (ex: tirar a imagem).

### `/pix`
Gera um embed profissional de cobrança via PIX com botão "Copiar Chave".
- **Opções:**
  - `valor` (Obrigatório): O valor da cobrança (ex: `50,00`).
  - `chave` (Obrigatório): A chave PIX que será copiada pelo botão.
  - `cor`, `rodape` (Opcional): Personalização visual.

### `/promo`
Cria um cupom de desconto com contagem regressiva e botões.
- **Opções:**
  - `desconto` (Obrigatório): Texto do destaque (ex: `20% OFF`).
  - `cupom` (Obrigatório): O código do cupom (ex: `NATAL20`).
  - `data_limite` (Obrigatório): Validade no formato `DD/MM/AAAA HH:MM` (ex: `25/12/2026 23:59`).
  - `titulo`, `descricao`, `cor`, `imagem`, `rodape`, `link_compra`: Personalizações opcionais para deixar o card único.

---

## ⭐ Avaliações

Sistema para coletar e exibir feedbacks dos membros, gerando prova social.

### `/avaliacao configurar`
Configura onde os embeds e avaliações aparecerão e define regras de permissão.
- **Opções:**
  - `canal_embed` (Obrigatório): Canal onde ficará o painel fixo de "Deixe sua avaliação".
  - `canal_avaliacoes` (Obrigatório): Canal onde as avaliações recebidas serão postadas publicamente.
  - `cargos_staff` (Obrigatório): Menção dos cargos que podem responder avaliações (ex: @Admin @Mod).
  - `cargos_avaliadores` (Opcional): **Novo!** Menção dos cargos que podem *enviar* avaliações (ex: @Cliente). Se vazio, todos podem avaliar.
  - `anonimo`: Se `True`, oculta quem enviou a avaliação.
  - `texto_embed`, `cor`, `rodape`, `imagem`: Personalização do painel de solicitação.

### `/avaliacao iniciar`
Envia o painel com o botão de avaliar no canal configurado.

### `/avaliacao status`
Mostra as configurações atuais do sistema (canais, cargos permitidos, etc).

### `/responder`
Responde publicamente a uma avaliação enviada.
- **Opções:**
  - `avaliacao_id` (Obrigatório): ID da mensagem da avaliação.
  - `resposta` (Obrigatório): Texto da resposta da equipe (ex: "Obrigado pelo feedback!").

---

## 📡 Conexões (n8n & Webhooks)

Integração com n8n para agentes de IA ou automações externas.

### `/conexao adicionar`
Conecta um canal de texto a um webhook externo (n8n).
- **Opções:**
  - `canal` (Obrigatório): O canal que será monitorado.
  - `webhook` (Obrigatório): URL do webhook do n8n (POST).
  - `modo` (Obrigatório):
    - `Todas as mensagens`: Envia tudo o que é falado no canal (Logs/IA Geral).
    - `Apenas menções`: Envia apenas quando marcam o bot (Chatbots).

### `/conexao remover`
Remove a integração de um canal.

### `/conexao listar`
Lista todas as conexões ativas no servidor.

### `/conexao configurar`
Exibe um tutorial rápido de como configurar o workflow e o payload JSON no n8n.

### ⚙️ Guia de Integração: n8n (Tutorial Técnico)
Para criar seus agentes de IA, siga esta configuração exata no n8n.

#### 1. Recebendo Dados (Webhook Node)
Configure o nó **Webhook** no n8n para receber as mensagens do zNyx:
- **Webhook Path:** Livre (use um código seguro/difícil).
- **Method:** `POST`
- **Authentication:** `None`
- **Respond:** `Immediately` ⚠️ **Importante!** (Evita timeout no Discord).
- **Payload Recebido:** O bot enviará os seguintes dados:
  `messageId`, `userId`, `username`, `displayName`, `content`, `channelId`, `guildId`, `timestamp`, `attachments`.

#### 2. Enviando Respostas
Existem duas formas de devolver a resposta para o Discord:

**Opção A: Responder via Webhook do Discord (Simples)**
- **Nó:** HTTP Request
- **Method:** `POST`
- **URL:** [Cole o Webhook do Canal Discord]
- **Authentication:** `None`
- **Send Body:** Ativado (`JSON`)
- **JSON:**
  #CODE# json
  { "content": "Resposta do agente" }
  #CODE#
- *Como criar o Webhook:* Vá em Config. do Canal → Integrações → Webhooks → Novo.

**Opção B: Responder como o Bot (Recomendado)**
Mantém a identidade do bot e permite usar "Reply".
- **Nó:** Discord
- **Connection Type:** `Bot Token` (Configure o Token do seu Bot)
- **Resource:** `Message`
- **Operation:** `Send`
- **Send To:** `Channel`
- **Channel:** Use a expressão `{{ $json.channelId }}`
- **Message:** O texto da resposta do agente.
- **Para dar Reply (Citar mensagem):**
  - Vá em `Options` → `Add Option` → `Message to Reply to`
  - Use a expressão: `{{ $json.body.messageId }}`

---

## 🎉 Sorteios

Sistema completo de sorteios com requisitos e reroll.

### `/sortear`
Inicia um novo sorteio.
- **Opções:**
  - `ganhadores` (Obrigatório): Quantidade de vencedores.
  - `data_final` (Obrigatório): Encerramento em `DD/MM/AAAA HH:MM`.
  - `cargos` (Opcional): Menção de cargos obrigatórios para participar (vazio = todos).
  - `fraude` (Opcional): Se `True` (padrão), impede contas novas (< 7 dias) de ganhar.
  - `titulo`, `imagem`, `cor`, `rodape`: Personalização completa.

### `/reroll`
Sorteia novos ganhadores para um sorteio encerrado.
- **Opções:**
  - `mensagem_id` (Obrigatório): ID da mensagem do sorteio original.
  - `ganhadores` (Opcional): Quantidade de novos nomes (padrão é a mesma do sorteio original).

---

## 📊 Status e Monitoramento

Monitoramento em tempo real de servidores de Minecraft.

### `/status configurar`
Define quais servidores monitorar e onde exibir.
- **Opções:**
  - `canal` (Obrigatório): Onde o painel de status ficará.
  - `servidores` (Obrigatório): IPs dos servidores separados por vírgula (ex: `jogar.rede.com, rankup.rede.com`).
  - `titulo`, `cor`, `imagem`, `rodape`: Personalização.
  - `icone_online`, `icone_offline`, `icone_manutencao`: Emojis personalizados para cada estado (branding).

### `/status iniciar`
Envia o painel e inicia a atualização automática (a cada 10 minutos).

### `/status parar`
Para o monitoramento e apaga o painel.

### `/manutencao ligar`
Coloca o painel em modo "Manutenção" (icone amarelo).
- **Opção:** `texto` (Opcional): Motivo da manutenção para exibir no embed.

### `/manutencao desligar`
Volta o painel ao funcionamento normal (pingando os servidores).

---

## 💡 Sugestões

Sistema de votação democrática para melhorias no servidor.

### `/sugestao configurar`
Prepara os canais de sugestão.
- **Opções:**
  - `canal_analise` (Obrigatório): Onde os membros enviam e votam nas sugestões.
  - `canal_resultado` (Obrigatório): Onde aparecem as sugestões aprovadas/reprovadas.
  - `anonimo`: Se as sugestões são anônimas.
  - `emoji_positivo`, `emoji_negativo`, `cor`: Personalização dos botões e embed.

### `/sugestao iniciar`
Envia o painel com botão "💡 Enviar Sugestão" no canal de análise.

### `/resultado`
Aprova ou reprova uma sugestão administrativamente.
- **Opções:**
  - `sugestao_id` (Obrigatório): ID da mensagem da sugestão.
  - `decisao` (Obrigatório): `Aprovar` ou `Reprovar`.
  - `resposta` (Opcional): Comentário da equipe sobre a decisão.

---

## 🎫 Tickets

Sistema de atendimento privado via tickets com logs.

### `/categorias adicionar`
Cria uma categoria de atendimento no menu (ex: Financeiro, Dúvidas).
- **Opções:** `titulo`, `emoji`, `subtitulo`, `cargos` (quem pode atender, além de admins).

### `/categorias listar` / `/categorias remover` / `/categorias editar`
Gerencia as categorias existentes.

### `/ticket`
Configura o painel principal de tickets.
- **Opções:**
  - `categoria` (Obrigatório): ID da **Categoria do Discord** (aba de canais) onde os tickets serão abertos.
  - `logs` (Obrigatório): Canal de texto para logs de tickets (transcripts).
  - `titulo`, `cor`, `imagem_inicial`, `imagem_ticket`, `boas_vindas`: Personalização completa.

### `/fecharticket`
Fecha o ticket atual. Gera transcript/log no canal de logs e deleta o canal após 5 segundos.

---

## 💎 Planos (VIPs)

Sistema interativo para apresentação de planos/VIPs do servidor.

### `/planos adicionar`
Adiciona um novo plano ao sistema.
- **Fluxo:** Após executar, envie a descrição do plano no chat (5 minutos).
- **Opções:**
  - `titulo` (Opcional): Título do plano.
  - `thumbnail` (Opcional): URL de imagem 1x1.
  - `imagem` (Opcional): URL da imagem do embed.
  - `cor` (Opcional): Cor HEX da lateral.
  - `rodape` (Opcional): Texto do rodapé. **(Exclusivo Plano Pro)**
  - `link_compra` (Opcional): URL para o botão "Adquirir".
- **Limites:** Plus (2 planos) | Pro (10 planos).

### `/planos remover`
Remove um plano existente pelo ID.
- **Opção:** `id` (Obrigatório): ID do plano (visível em `/planos listar`).

### `/planos editar`
Edita campos de um plano existente.
- **Opções:** `id` (Obrigatório), `titulo`, `thumbnail`, `imagem`, `cor`, `rodape`, `link_compra`, `descricao`.
- **Tokens Especiais:** `padrao#` para resetar, `remover#` para limpar.

### `/planos listar`
Lista todos os planos configurados com IDs, títulos e links.

### `/planos configurar`
Configura o embed inicial que aparece com o dropdown.
- **Fluxo:** Após executar, envie a descrição no chat (5 minutos).
- **Opções:**
  - `canal` (Obrigatório): Canal onde o embed será enviado.
  - `imagem`, `cor`, `rodape`: Personalização do embed inicial.

### `/planos iniciar`
Envia o embed com dropdown no canal configurado. Usuários selecionam um plano para ver detalhes em mensagem privada (ephemeral).
- **Cooldown:** 30 segundos entre visualizações por usuário.

---

## 💬 Tópicos Automáticos

Organização de canais de bate-papo.

### `/topicos ativar`
Transforma todas as mensagens de um canal em tópicos (threads) automaticamente.
- **Útil para:** Canais de mídia, divulgações, apresentações.
- **Recomendação:** Use com `Modo Lento` ativado no canal para evitar spam.

### `/topicos desativar`
Para a criação automática de tópicos.

---

## 🛡️ Infraestrutura e Segurança

O zNyx foi construído para ser resiliente em ambientes de produção.

### Auto-Restart Nativo
Não se preocupe com quedas. O bot possui um sistema de vigilância (Watchdog) no container Docker:
- **Detecção de Falha:** Se o processo do bot travar ou fechar por erro crítico.
- **Ação Imediata:** O sistema captura o código de erro.
- **Recuperação:** O bot reinicia automaticamente em **5 segundos**.
- **Benefício:** Máxima disponibilidade (Uptime) e estabilidade para sua comunidade, sem intervenção manual.