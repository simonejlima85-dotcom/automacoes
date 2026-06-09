# 🔔 Monitoramento e Resumos de Grupos no Telegram

Este conjunto de workflows foi criado para **monitorar conversas em grupos de clientes** no Telegram, detectar riscos (reclamações, churn, cancelamento) em tempo real e gerar resumos diários automáticos.

## 🔄 Como os dois workflows trabalham juntos

### 1. Agente de Monitoramento (tempo real)
- Monitora mensagens em grupos autorizados
- Usa IA para classificar o risco da mensagem (normal / reclamação / risco de churn / cancelamento)
- Salva todas as mensagens em uma tabela (DataTable ou Google Sheets)
- Envia alerta imediato para Customer Success quando detecta risco alto

### 2. Resumos Diários (todo dia às 18h)
- Pega todas as mensagens ainda não processadas da tabela
- Agrupa por grupo/chat
- Envia para IA gerar um resumo objetivo e acionável
- Marca as mensagens como processadas
- Envia o resumo para as pessoas configuradas (Customer Success, gerente de projeto, etc.)

## 📦 Estrutura da pasta

```
monitoramento-telegram/
├── agente-monitoramento-telegram.json
├── resumos-grupos-telegram.json
└── README.md
```

## ⚙️ Configuração necessária

### 1. Telegram
- Crie um bot no @BotFather
- Configure a credencial do Telegram nos dois workflows

### 2. Whitelist de Grupos
No workflow **Agente de Monitoramento**, no node `whitelist de grupo`, adicione os `chat_id` dos grupos que devem ser monitorados.

### 3. Tabela de dados (DataTable ou Google Sheets)

Atualmente os workflows usam **DataTable** do n8n. 

**Quer usar Google Sheets?** É fácil trocar:
- Substitua os nodes de DataTable por nodes de Google Sheets
- Mantenha as mesmas colunas: `chat_id`, `user_id`, `text`, `processed`, `group_title`, `user_name`, `username`

### 4. IA (Gemini ou GPT)
- Configure sua credencial do Google Gemini (ou OpenAI) nos dois workflows
- O primeiro workflow usa IA para classificar risco
- O segundo usa IA para gerar resumos

### 5. Destinatários dos alertas e resumos (IMPORTANTE)

Nos nodes `Code in JavaScript1` de cada workflow, você vai encontrar algo assim:

```js
const RECIPIENTS = [
  { id: "{{ SEU_CHAT_ID_SIMONE }}", role: "Simone" },
  { id: "{{ SEU_CHAT_ID_MAYARA }}" , role: "Mayara" }
];
```

**Substitua** `{{ SEU_CHAT_ID_SIMONE }}` e `{{ SEU_CHAT_ID_MAYARA }}` pelos chat_ids reais das pessoas que devem receber os alertas e resumos.

Para descobrir o chat_id de uma pessoa:
1. Envie uma mensagem para o seu bot
2. Use o bot `@userinfobot` ou `@getidsbot`

---

**Criado por Simone Lima**  
Repositório: [automacoes](https://github.com/simonejlima85-dotcom/automacoes)