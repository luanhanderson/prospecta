# 2. Auditoria e nota de oportunidade

## O que verificar (só fatos públicos, sempre com fonte)

**Site (se existir)**
- Abre? Erro, timeout ou domínio expirado são o argumento mais forte.
- HTTPS? Tem `<meta name="viewport">` (versão celular)?
- Plataforma grátis com faixa da plataforma ("Este site foi criado no Wix")?
- Ano do rodapé (© antigo = desatualizado). Botão de WhatsApp ou agendamento visível?
- Velocidade: PageSpeed API (`https://www.googleapis.com/pagespeedonline/v5/runPagespeed?url=<URL>&strategy=mobile`). Sem chave, a cota costuma estar esgotada. Plano B: com o site aberto, rode `performance.getEntriesByType('navigation')[0].loadEventEnd` e considere acima de 4000 ms como lento (medição aproximada).

**Instagram**
- Seguidores, número de posts, data aproximada da última postagem.
- Link da bio: vazio / só WhatsApp / Linktree / quebrado / site.
- Perfil privado? Bio diz cidade, serviço e como contratar ou comprar?

**Mapa**
- Tem site cadastrado? Telefone? Horário? Avaliações?

## Nota (0 a 100)

Adapte os sinais ao serviço do usuário (veja a tabela no SKILL.md). Para quem vende **sites / landing pages**:

| Sinal | Pontos |
|---|---|
| **Base, escolha uma:** sem site / só rede social, WhatsApp ou Linktree | +50 |
| **Base, escolha uma:** site fora do ar ou domínio expirado | +50 |
| **Base, escolha uma:** site em construtor grátis ou subdomínio | +30 |
| Link da bio quebrado (404) | +20 |
| Site desatualizado (© antigo, layout quebrado) | +10 |
| Site sem versão para celular | +20 |
| Site lento (PageSpeed < 0,5 ou carregamento > 4 s) | +10 |
| Sem HTTPS | +10 |
| Site sem botão de WhatsApp ou agendamento | +10 |
| Instagram ativo com público (500+ seguidores, posts recentes) | +10 |
| Negócio estabelecido (muitos anos, muitas avaliações, cargo de destaque) | +10 |
| Instagram privado ou parado há mais de 6 meses | −10 |
| Indício de fechamento ou mudança de cidade | −40, marcar "Confirmar antes" |

Para **social media / design**, troque a base por: Instagram sem identidade visual (+40), sem postar há 30+ dias (+30), posts só com foto de celular (+20), muitos seguidores e pouco engajamento (+10).

**Faixas:** 80+ prioridade máxima · 60–79 boa · 40–59 média · abaixo de 40 baixa.

## O que vai para a mensagem

Escolha **1 problema** (no máximo 2) que o dono consiga confirmar em 10 segundos. Prefira, nesta ordem:
1. Algo quebrado (link 404, site fora do ar)
2. Algo ausente e óbvio ("ainda não tem um site")
3. Algo desatualizado (faixa do Wix, © 2019)

Nunca use jargão (LCP, SEO, responsividade). Traduza: "demora para abrir no celular".
