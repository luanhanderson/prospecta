# 4. Envio pelo WhatsApp

## Pré-requisitos

- **Google Chrome** com a extensão **Claude in Chrome** conectada. O WhatsApp Web recusa outros navegadores, incluindo o navegador embutido do app ("O WhatsApp funciona no Google Chrome 100 ou posterior").
- O usuário conectado no `web.whatsapp.com` (QR code escaneado **por ele**). De preferência com **WhatsApp Business**.
- **Aprovação explícita** do lote: o usuário viu a lista e as mensagens e disse "pode enviar".

## Procedimento por lead

1. Pegue o contexto das abas (`tabs_context_mcp`) e use uma aba **do seu grupo**. Se a aba sumir (o usuário fechou), crie outra e abra `web.whatsapp.com` de novo.
2. Monte a URL com o texto codificado:
   ```js
   const t = `...mensagem com quebras de linha...`;
   location.href = 'https://web.whatsapp.com/send?phone=55' + 'DDDNUMERO' + '&text=' + encodeURIComponent(t);
   ```
   Use só dígitos no número: `55` + DDD + número (ex.: `5511912345678`).
3. Espere 15 a 20 s (aparece "Iniciando conversa").
4. **Tire um print e confira:** o número no topo é o certo e o texto está completo na caixa. O WhatsApp pode mostrar o número sem o 9 extra (ex.: +55 93 9141-3124); isso é normal.
5. Clique no botão de enviar (ícone de avião no canto inferior direito; a posição muda com o tamanho da janela, então confirme no print).
6. Tire outro print e confirme a mensagem enviada com o horário.
7. Espere **pelo menos 1 minuto** (o ideal são 3 a 5) antes do próximo.

## Situações comuns

| Situação | O que fazer |
|---|---|
| "O número ... não está no WhatsApp" | Clique em OK, marque "Sem WhatsApp" e siga para o próximo. Não tente outro número sem aprovação |
| Telefone fixo | Geralmente não tem WhatsApp. Pode testar uma vez, mas o padrão é ligar |
| Resposta automática ("agradece seu contato") | Não é resposta humana. Anote e mantenha a cadência |
| Tela de QR code | O usuário precisa escanear. Peça e espere |
| Aba fechada no meio | Abra outra. Confira no histórico de conversas se a última mensagem saiu antes de reenviar |
| Algo inesperado (bloqueio, aviso de spam) | **Pare tudo** e avise o usuário |

## Limites e risco de bloqueio

O WhatsApp **não publica um limite diário fixo**. O bloqueio vem de comportamento:
- muitas pessoas **bloqueando ou denunciando** (o fator principal);
- muitas conversas novas com quem não tem seu número, em sequência rápida;
- textos idênticos para todos; links na 1ª mensagem;
- número novo ou sem histórico.

| Fase | Novas conversas por dia |
|---|---|
| Primeira semana | 5 a 10 |
| Sem bloqueios por 1–2 semanas | 15 a 20 |
| Arriscado | 30+ ou disparos em sequência |

Personalize cada mensagem, espace os envios e pare de insistir depois da msg 3.

## Instagram DM (alternativa)

- O usuário faz login no Chrome. Você abre o perfil, clica em "Enviar mensagem", cola o texto, confere e envia.
- DMs de quem não segue a conta caem em "Solicitações de mensagem" e são menos vistas. Funciona melhor para negócios que vivem no Instagram (lojas, estética, alimentação).
- 5 a 10 por dia. **Nunca** siga, curta ou comente em massa.
