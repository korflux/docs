# 🤖 zNyx - Documentação Oficial

> **Bem-vindo à documentação oficial do zNyx**

## 🤖 O que é o zNyx?

O **zNyx** é a ferramenta definitiva para elevar o padrão da sua comunidade de Minecraft. Desenvolvido com foco em performance e personalização, ele centraliza a gestão do servidor, engajamento e suporte em uma única interface moderna.

Mais do que um bot, é uma solução completa para profissionalizar a comunicação e monetização do seu projeto.

*   [**Suporte & Contato**](https://discord.gg/3Mz97UjDta): Entre em contato diretamente comigo para dúvidas ou suporte.

## ✨ Funcionalidades

Uma visão geral de tudo que o zNyx oferece para otimizar sua operação:

- **Anúncios e Monetização**: Crie comunicados visuais com embeds personalizados, envie cobranças de PIX facilitadas e envie anúncios de descontos facilitados.
- **Sorteios Seguros**: Sistema completo com requisitos de cargos, reroll inteligente e proteção anti-fraude para contas novas.
- **Sistema de Tickets**: Atendimento privado e organizado por categorias, com geração automática de logs (transcripts) para auditoria.
- **Monitoramento em Tempo Real**: Painéis de status que mostram ping e jogadores online dos seus servidores, com atualização automática.
- **Integração com n8n (IA)**: Conecte canais do Discord a fluxos de automação externos e agentes de Inteligência Artificial via Webhooks.
- **Sugestões e Votação**: Canal dedicado para feedback da comunidade com sistema de aprovação/reprovação pela staff.
- **Avaliações**: Coleta de feedbacks e prova social, permitindo respostas públicas da equipe.
- **Organização de Tópicos**: Transformação automática de mensagens em threads para manter canais de mídia e divulgação limpos e organizados.

---

# 💎 Planos e Preços

O **zNyx** foi desenhado para escalar junto com o seu projeto. Oferecemos duas tiers focadas em momentos diferentes: desde a profissionalização essencial até operações complexas que exigem automação e identidade própria.

### 🌟 Plano Plus
A base sólida para servidores que buscam organização e estética profissional.

### 👑 Plano Pro
A experiência definitiva com automação de IA, white-label total e recursos de engajamento.

## Comparativo de Recursos

Confira a matriz completa de funcionalidades e escolha a que melhor se adapta à sua operação.

| Recurso | Plano Plus | Plano Pro |
| :--- | :---: | :---: |
| **Investimento Mensal** | **R$ 49,00** | **R$ 149,00** |
| **Suporte & SLA** | | |
| Suporte via Discord | 24h Response Time | ⚡ **2h Response Time** |
| Uptime Garantido | 99,9% | 99,9% |
| Auto-Restart | ✅ | ✅ |
| Suporte a Automação (n8n) | ❌ | ✅ |
| **Identidade & Branding** | | |
| Identidade Visual (Embeds) | WhiteLabel Parcial* | 🎨 **WhiteLabel Completo** |
| **Gestão & Utilitários** | | |
| `/anunciar` (Painel Interativo) | ✅ | ✅ |
| `/editanunciar` (Correção) | ❌ | ✅ |
| `/pix` (Embed Visual de Cobrança) | ✅ | ✅ |
| `/promo` (Embed Visual de Promoções) | ❌ | ✅ |
| **Atendimento** | | |
| Sistema de Tickets Completo | ✅ | ✅ |
| Logs/Transcripts (.txt) | ✅ | ✅ |
| Categorias Personalizáveis | ✅ | ✅ |
| **Engajamento** | | |
| Sistema de Sugestões | ✅ | ✅ |
| Sistema de Sorteios / Reroll | ❌ | ✅ |
| Sistema de Avaliação | ❌ | ✅ |
| Tópicos Automáticos | ❌ | ✅ |
| **Monitoramento** | | |
| `/status` (Painel em Tempo Real) | 1 Servidor | **Ilimitado** |
| Modo Manutenção | ❌ | ✅ |
| `/conexão` (Webhooks n8n) | ❌ | ✅ |

> **Nota:** *WhiteLabel Parcial: O rodapé dos embeds manterá a assinatura padrão: "© 2025 znyx.com.br - Todos os direitos reservados."*

## Detalhes Importantes

### Sobre os Comandos Financeiros
Focamos na estética e no profissionalismo da sua comunicação:
* **/pix:** Gera um embed profissional e padronizado para exibir seus dados de recebimento. Não realiza processamento de pagamentos ou baixa automática.
* **/promo:** Cria comunicados visuais de alto impacto para divulgar suas ofertas. Não gerencia a validade técnica de cupons dentro do jogo ou loja.

### Plano Plus
Ideal para quem está profissionalizando a gestão.
* **Foco:** Atendimento via tickets, organização de sugestões e anúncios padronizados.
* **Limitação:** Exibe a marca do zNyx discretamente no rodapé.

### Plano Pro
Para quem trata o servidor como uma empresa.
* **Foco:** Retenção (Sorteios/Avaliações), Automação (n8n/IA) e Monitoramento total.
* **Diferencial:** Sua marca em 100% dos locais e atendimento prioritário da nossa equipe.

> ✅ **Pronto para escalar?** [Entre em contato conosco](https://discord.gg/3Mz97UjDta) para ativar sua licença e configurar seu bot hoje mesmo.

---

# 📚 Documentação dos Comandos (Referência Rápida)

Abaixo você encontra um resumo técnico dos comandos. Para detalhes visuais e exemplos, visite nossa [Documentação Completa](https://docs.znyx.com.br) (Link Exemplo).

## 📢 Anúncios e Promoções

Ferramentas para comunicar novidades, promoções e solicitar pagamentos de forma profissional.

### `/anunciar`
Envia um anúncio personalizado no canal atual através de um painel interativo.
- **Como usar:** Digite o comando e preencha as opções opcionais. O bot pedirá o texto do anúncio em seguida.
- **Opções:**
  - `cor` (Opcional): Cor da lateral do embed em HEX (ex: `#FF0000`). Padrão: Verde.
  - `rodape` (Opcional): Texto pequeno no rodapé do anúncio.
  - `imagem` (Opcional): URL de uma imagem ou GIF para ilustrar o anúncio.

### `/editanunciar`
Edita um anúncio já enviado pelo bot.
- **Opções:**
  - `mensagem_id` (Obrigatório): O ID da mensagem do anúncio (ative o Modo Desenvolvedor do Discord para pegar).
  - `manter_descricao` (Opcional): `True` para manter o texto atual, `False` para escrever um novo.
  - `cor`, `rodape`, `imagem` (Opcional): Novos valores para atualizar. Use `padrao#` para resetar ou `remover#` para excluir a imagem.

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
  - `titulo`, `descricao`, `cor`, `imagem`, `rodape`, `link_compra`: Personalizações opcionais.

---

## ⭐ Avaliações

Sistema para coletar e exibir feedbacks dos membros.

### `/avaliacao configurar`
Configura onde os embeds e avaliações aparecerão.
- **Opções:**
  - `canal_embed` (Obrigatório): Canal onde ficará o painel fixo de "Deixe sua avaliação".
  - `canal_avaliacoes` (Obrigatório): Canal onde as avaliações recebidas serão postadas.
  - `cargos_staff` (Obrigatório): Menção dos cargos que podem responder avaliações (@Admin @Mod).
  - `anonimo`: Se `True`, oculta quem enviou a avaliação.
  - `texto_embed`, `cor`, `rodape`, `imagem`: Personalização do painel.

### `/avaliacao iniciar`
Envia o painel com o botão de avaliar no canal configurado.

### `/avaliacao status`
Mostra as configurações atuais do sistema.

### `/responder`
Responde publicamente a uma avaliação enviada.
- **Opções:**
  - `avaliacao_id` (Obrigatório): ID da mensagem da avaliação.
  - `resposta` (Obrigatório): Texto da resposta da equipe.

---

## 📡 Conexões (n8n & Webhooks)

Integração com n8n para agentes de IA ou automações externas.

### `/conexao adicionar`
Conecta um canal de texto a um webhook externo (n8n).
- **Opções:**
  - `canal` (Obrigatório): O canal que será monitorado.
  - `webhook` (Obrigatório): URL do webhook do n8n (POST).
  - `modo` (Obrigatório):
    - `Todas as mensagens`: Envia tudo o que é falado no canal.
    - `Apenas menções`: Envia apenas quando marcam o bot.

### `/conexao remover`
Remove a integração de um canal.

### `/conexao listar`
Lista todas as conexões ativas no servidor.

### `/conexao configurar`
Exibe um tutorial rápido de como configurar o workflow no n8n.

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
  - `titulo`, `imagem`, `cor`, `rodape`: Personalização.

### `/reroll`
Sorteia novos ganhadores para um sorteio encerrado.
- **Opções:**
  - `mensagem_id` (Obrigatório): ID da mensagem do sorteio.
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
  - `icone_online`, `icone_offline`, `icone_manutencao`: Emojis personalizados para cada estado.

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

Sistema de votação para melhorias no servidor.

### `/sugestao configurar`
Prepara os canais de sugestão.
- **Opções:**
  - `canal_analise` (Obrigatório): Onde os membros enviam e votam nas sugestões.
  - `canal_resultado` (Obrigatório): Onde aparecem as sugestões aprovadas/reprovadas.
  - `anonimo`: Se as sugestões são anônimas.
  - `emoji_positivo`, `emoji_negativo`, `cor`: Personalização.

### `/sugestao iniciar`
Envia o painel com botão "Sugerir" no canal de análise.

### `/resultado`
Aprova ou reprova uma sugestão.
- **Opções:**
  - `sugestao_id` (Obrigatório): ID da mensagem da sugestão.
  - `decisao` (Obrigatório): `Aprovar` ou `Reprovar`.
  - `resposta` (Opcional): Comentário da equipe sobre a decisão.

---

## 🎫 Tickets

Sistema de atendimento privado via tickets.

### `/categorias adicionar`
Cria uma categoria de atendimento (ex: Financeiro, Dúvidas).
- **Opções:** `emoji`, `titulo`, `subtitulo`, `cargos` (quem pode atender, além de admins).

### `/ticket`
Configura o painel principal de tickets.
- **Opções:**
  - `categoria` (Obrigatório): ID da **Categoria do Discord** (aba de canais) onde os tickets serão abertos.
  - `logs` (Obrigatório): Canal de texto para logs de tickets.
  - `titulo`, `cor`, `imagem_inicial`, `imagem_ticket`, `boas_vindas`: Personalização completa.

### `/fecharticket`
Fecha o ticket atual (ou um específico). Gera transcript/log no canal de logs.

---

## 💬 Tópicos Automáticos

Organização de canais de bate-papo.

### `/topicos ativar`
Transforma todas as mensagens de um canal em tópicos (threads) automaticamente.
- **Útil para:** Canais de mídia, divulgações, apresentações.
- **Recomendação:** Use com `Modo Lento` ativado no canal para evitar spam.

### `/topicos desativar`
Para a criação automática de tópicos.