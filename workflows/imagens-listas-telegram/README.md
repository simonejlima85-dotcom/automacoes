# 📸 Imagens Listas Telegram

Workflow complexo de **extração automática de contatos** a partir de imagens de listas enviadas via Telegram.

## O que ele faz

Este workflow monitora grupos/canais do Telegram, recebe fotos de listas de contatos, usa inteligência artificial para extrair nomes e telefones, formata os números corretamente e envia os contatos para o CRM ASPA. Além disso, organiza os arquivos processados no Google Drive (sucesso x erro).

## Principais funcionalidades

- **Leitura de imagens** usando GPT-4o-mini (visão)
- **Extração inteligente** de nomes e telefones com regras complexas de DDD
- **Parseamento** de tabelas Markdown geradas pela IA
- **Envio automático** para o CRM ASPA (via Template + Journey)
- **Organização no Google Drive** (pasta de processados e pasta de erros)
- Suporte a **múltiplas listas** (31, 36, 43, 44, 45, 50, 29, Andreia, Indalina, etc.)
- Tratamento de erro robusto com múltiplos IFs e branches

## Como funciona (fluxo geral)

1. Telegram Trigger detecta novas mensagens com fotos
2. Baixa a imagem
3. Dependendo do chat/grupo, direciona para o branch correto (Switch)
4. GPT-4o-mini analisa a imagem e extrai os dados seguindo regras rigorosas de telefone
5. Code node parseia a tabela Markdown retornada pela IA
6. Valida se teve sucesso
7. Envia o contato para o ASPA CRM
8. Faz upload da imagem original para a pasta correta no Google Drive (sucesso ou erro)

## Tecnologias utilizadas

- n8n
- OpenAI (GPT-4o-mini Vision)
- Telegram Bot API
- ASPA CRM (API)
- Google Drive

## Como configurar (após importar)

1. **Telegram**
   - Configure sua credencial do Telegram
   - Ajuste os Chat IDs no nó **Switch** (cada lista tem um chat específico)

2. **OpenAI**
   - Configure sua credencial do OpenAI

3. **ASPA CRM**
   - Substitua `{{ SEU_TOKEN_ASPA }}` pelo seu token Bearer
   - Ajuste os `channel` e `template` conforme sua conta

4. **Google Drive**
   - Configure sua credencial
   - Substitua os Folder IDs pelas pastas corretas de sucesso e erro

5. **Regras de Telefone**
   - As regras estão bem detalhadas dentro dos nós de prompt do GPT. São 16 regras hierárquicas com prioridade.

## Estrutura do Workflow

- Vários branches paralelos (um para cada lista)
- Uso pesado de Merge nodes para juntar os fluxos
- Muitos nós de validação (IF)
- Upload condicional para pastas diferentes no Drive

## Observações

Este é um workflow bastante complexo e foi refinado ao longo do tempo com vários ajustes. Ele lida bem com variações de formatação de listas e tem bom tratamento de erro.

Se for usar como template, recomendo testar bem as regras de extração de telefone com suas listas reais.

---

**Criado e mantido por Simone Lima**  
Repositório: [automacoes](https://github.com/simonejlima85-dotcom/automacoes)