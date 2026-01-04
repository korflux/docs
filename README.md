# 🤖 zNyx - Documentação dos Comandos

Bem-vindo à documentação oficial do **zNyx**, o bot essencial para comunidades de servidores de Minecraft. Aqui você encontrará detalhes sobre todos os comandos, subcomandos e opções disponíveis.

---

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