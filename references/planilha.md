# Planilha de leads

Um arquivo CSV por campanha (`leads-<nicho>-<cidade>-<AAAA-MM-DD>.csv`), em UTF-8. Modelo: `templates/leads-modelo.csv`.

| Coluna | Conteúdo |
|---|---|
| `score` | Hot / Warm / Cold / Skip |
| `business` | Nome do negócio |
| `category` | Nicho/especialidade |
| `area` | Endereço ou bairro |
| `website_status` | No site found / Social only / Weak site / Has site |
| `website_url` | URL ou "Not found" |
| `instagram` | URL do perfil ou "Não confirmado" |
| `instagram_confidence` | Confirmado / Provável / - |
| `other_social` | Facebook, LinkedIn, Jusbrasil, Doctoralia... |
| `phone` | Telefone público do negócio |
| `source_urls` | De onde veio cada dado |
| `why_prospect` | Motivo em 1 frase |
| `confidence` | High / Medium / Low |
| `verified_date` | Data da verificação |
| `notes` | Observações (homônimos, mesmo endereço, DDD diferente...) |
| `opportunity_score` | Nota 0–100 |
| `top_issues` | Problemas usados na mensagem |
| `best_channel` | WhatsApp / Instagram DM / Ligação / E-mail |
| `status` | Novo · Fila: enviar em DD/MM · Contatado (msg 1/2/3) · Sem WhatsApp · Respondeu · Reunião · Proposta · Fechado · Não contatar · Confirmar antes |
| `audit_date` | Data da auditoria |
| `contacted_at` | Data e hora do último envio |
| `channel_used` | Canal usado |
| `reply` | Resumo da resposta (ou "Resposta automática") |
| `next_step` | Próxima ação com data |

## Regras

- Sempre leia e escreva com um parser de CSV de verdade (ex.: `csv.DictReader` / `DictWriter` em Python), **nunca** com substituição de texto, porque vírgulas e aspas dentro dos campos quebram o arquivo.
- Ao gravar, abra o arquivo só depois de ter todas as linhas prontas na memória. Se a gravação falhar no meio, o arquivo fica cortado.
- Novas colunas vão sempre no final, sem apagar as antigas.
- Deduplicar por nome + endereço.
