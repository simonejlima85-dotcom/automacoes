# 📊 Relatórios de Campanhas

Automação que gera e envia relatórios semanais automáticos de desempenho de campanhas (Google Ads + Meta Ads).

## O que faz

- Dispara todo domingo às 9h
- Busca clientes ativos em uma planilha do Google Sheets
- Puxa dados dos últimos 7 dias via Windsor.ai
- Gera um relatório em HTML bonito com resumo, campanhas e top criativos
- Envia por e-mail para os gestores/account managers

## Como configurar

1. Configure a credencial do Google Sheets
2. Substitua `{{ SUA_PLANILHA_ID_AQUI }}` pelo ID da sua planilha de clientes
3. Configure a credencial do Gmail
4. (Opcional) Adicione WINDSOR_API_KEY nas variáveis de ambiente do n8n

## Observações

- O relatório considera o período de domingo a sábado da semana anterior
- Atualmente o gestor revisa antes de encaminhar para o cliente
- Fácil de adaptar para envio direto aos clientes

---

**Arquivo principal:** `relatorio-v4-semanal.json`