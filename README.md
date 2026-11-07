# Prospecta

**Skill para o Claude Code que encontra clientes para você, de qualquer nicho, e te ajuda a abordar cada um com uma mensagem humana pelo WhatsApp.**

Feita para freelancers, agências e pequenas empresas brasileiras: designers, desenvolvedores, social medias, fotógrafos, gestores de tráfego, contadores, consultores...

> "Prospecta advogados em Curitiba que não têm site."
> "Manda 5 mensagens de hoje."
> "Manda o follow-up de quem não respondeu."

## O que ela faz

| Etapa | O que acontece |
|---|---|
| **0. Perfil** | Pergunta uma vez quem você é, o que vende, para quem e qual a oferta grátis. Guarda em `perfil.md` |
| **1. Descoberta** | Busca negócios do nicho na sua cidade (Bing Maps) e confere um por um se têm site, Instagram etc. |
| **2. Auditoria** | Registra fatos com fonte (site fora do ar, link da bio quebrado, só Instagram...) e dá uma nota de 0 a 100 |
| **3. Mensagens** | Escreve a 1ª mensagem e 2 follow-ups, curtos, verdadeiros e sem cara de robô, respeitando OAB, CFM e outros conselhos |
| **4. Envio** | Envia pelo **seu** WhatsApp Web no Chrome, **só depois da sua aprovação**, um por um e com limite diário |
| **5. Acompanhamento** | Mantém uma planilha com status, respostas e a próxima ação de cada lead |
| **6. Vigia + automações** 🆕 | Confere o WhatsApp a cada 30 min, escreve a resposta no seu estilo e **te avisa no celular para aprovar**. Também cria as respostas rápidas (`/valor`, `/esboco`...) e a mensagem de ausência do WhatsApp Business |

### 🆕 Vigia de respostas

```
Mac ligado      →  o vigia confere a cada 30 min, escreve a resposta e avisa no seu celular
Você aprova     →  "envia" e a mensagem sai
Mac desligado   →  a mensagem de ausência do WhatsApp Business responde por você
Você online     →  digita "/" e usa as respostas rápidas
```

O vigia **nunca responde sozinho**: ele lê, sugere e espera o seu ok. Mensagens dos leads são tratadas como dados, nunca como ordens.

## Instalação

**Pré-requisitos:** [Claude Code](https://claude.com/claude-code) (CLI ou app desktop). Para enviar pelo WhatsApp, também o Google Chrome com a extensão **Claude in Chrome**.

```bash
git clone https://github.com/luanhanderson/prospecta.git ~/.claude/skills/prospecta
```

Ou, se usa o instalador `skills`:

```bash
npx skills add luanhanderson/prospecta --agent claude-code -g
```

Depois, numa conversa com o Claude, diga: **"vamos prospectar clientes"**. Ele vai pedir seus dados na primeira vez.

## Exemplo de mensagem gerada

```
Olá, Dra. Ana! Tudo bem?

Vi que o seu escritório ainda não tem um site, então gostaria de saber se tem interesse em ter uma página profissional, com suas áreas de atuação e seus contatos.

Posso montar um esboço sem custo para você ver como ficaria.

João, designer aqui de Curitiba (@joaodesign)
```

## Princípios

- **Você no controle:** nada é enviado sem o seu "pode enviar".
- **Pouco e bem feito:** 5 a 10 mensagens por dia, personalizadas, em vez de disparos em massa que derrubam o número.
- **Verdade acima de tudo:** a mensagem só cita o que foi verificado.
- **Respeito:** canais comerciais públicos, opt-out imediato, no máximo 3 mensagens por lead.
- **Sem gambiarra:** não resolve CAPTCHA, não raspa dados em massa, não segue nem curte em massa.

## Estrutura

```
prospecta/
├── SKILL.md                    # instruções principais para o Claude
├── perfil.exemplo.md           # modelo do seu perfil (copie para perfil.md)
├── references/
│   ├── 1-descoberta.md         # como achar e conferir leads (com scripts)
│   ├── 2-auditoria-e-nota.md   # o que checar e como pontuar
│   ├── 3-mensagens.md          # modelos por nicho, follow-ups e respostas
│   ├── 4-envio-whatsapp.md     # envio passo a passo e limites
│   ├── 5-conformidade.md       # LGPD, conselhos profissionais, termos das plataformas
│   ├── 6-vigia-e-automacoes.md # vigia de respostas + WhatsApp Business
│   └── planilha.md             # colunas da planilha de leads
├── templates/
│   ├── leads-modelo.csv
│   └── whatsapp-business-textos.modelo.md
└── campanhas/                  # seus dados (criado no uso, fora do Git)
```

## Combina bem com

Skills opcionais de [coreyhaines31/marketingskills](https://github.com/coreyhaines31/marketingskills) (MIT): `copywriting`, `cold-email`, `copy-editing` e `offers`. A Prospecta funciona sem elas.

## Aviso

Use com responsabilidade. Você é responsável pelas mensagens enviadas do seu número e pelo cumprimento da LGPD, dos termos do WhatsApp e do Instagram e das regras do conselho profissional dos seus leads. Este projeto não tem vínculo com WhatsApp, Meta, Microsoft ou Google.

## Licença

MIT. Veja [LICENSE](LICENSE).

---
Criado por **Luan Handerson** ([@luandesignr](https://www.instagram.com/luandesignr/)) · Santarém-PA
