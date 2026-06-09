# 🚀 Automações e Processos - V4 Company

**Documentação das automações e processos criados por Simone Lima na V4 Company**

*Organizado no GitHub para fácil acesso, versão e colaboração.*

Atualizado: Junho 2026

---

## Visão Geral

Aqui documentamos os processos e automações que criamos para otimizar o trabalho diário, ganhar tempo, ter mais controle e clareza nos resultados. Tudo registrado de forma organizada para consulta rápida e atualizações futuras.

**Ferramentas principais usadas:** n8n, Windsor.ai, Grok e integrações com Meta Ads, Google Ads, etc.

---

## Automação de Relatórios de Campanhas

### Objetivo
- Dar controle e clareza semanal sobre o desempenho das campanhas para os gestores de tráfego e account managers.
- Facilitar o envio dos relatórios para os clientes.
- Economizar tempo dos gestores, que antes precisavam organizar as métricas manualmente.

### Quando é feito?
Toda segunda-feira (envio automático por e-mail).
O n8n é disparado automaticamente todo **domingo às 9h**.

### Passo a passo
- O **n8n** é acionado automaticamente todo domingo às 9h.
- O relatório considera o período de **domingo a sábado da semana anterior**.
- O [**Windsor.ai**](http://Windsor.ai) puxa os dados das campanhas do **Google Ads** e **Meta Ads**.
- Os dados passam por um **tratamento no n8n** para serem formatados em **HTML**.
- O **n8n** dispara automaticamente o e-mail com a tabela formatada.
- O e-mail é enviado para os **gestores de tráfego** e **account managers**.
- Atualmente, o **gestor de tráfego revisa** o relatório antes de encaminhar para os clientes (por segurança e qualidade). Também é possível configurar o envio direto para os clientes, se desejado.

### Observações
- Essa automação foi criada para reduzir o trabalho manual de organização de métricas toda semana.
- O envio é feito de forma automática, mas ainda existe uma etapa de revisão humana antes do envio ao cliente.

---

## Estrutura do Repositório

- `README.md` - Este arquivo (visão geral e documentação principal)
- Futuramente: pastas por automação (ex: `/relatorios-campanhas/`, `/n8n-workflows/`, etc.)
- Possível adição de JSONs de workflows do n8n, scripts, etc.

---

## Como Contribuir / Atualizar

1. Clone o repositório
2. Edite o README ou adicione novos arquivos
3. Commit e push

Ou edite diretamente no GitHub.

---

## Links Relacionados

- Notion: [Automações e processos](https://www.notion.so/3613771e10128058898ce116730a50bc)
- Outras databases: Clientes, Decisões e Propostas, Tarefas (no Notion)

---

*Repositório criado e organizado automaticamente para manter tudo limpo, versionado e fácil de acessar.*