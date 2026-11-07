# 1. Descoberta de leads

## Fontes (em ordem de preferência)

| Fonte | Para quê | Observações |
|---|---|---|
| **Bing Maps** | Lista de negócios por nicho + cidade | Funciona sem login e traz nome, endereço, telefone e site em dados estruturados |
| **Busca Bing** | Conferir se o negócio tem site próprio | Busque `"<nome exato>" <cidade>` |
| **Instagram (perfil público)** | Bio, seguidores, link da bio | Abre sem login; não faça login nem siga ninguém |
| Google Maps | Conferência pontual | Sem login mostra só 2 ou 3 resultados ("visualização limitada") |
| Google Busca | Evitar | Pede CAPTCHA com facilidade. **Nunca resolva CAPTCHA**: mude de fonte |

## Bing Maps: extrair a lista

1. Abra `https://www.bing.com/maps?q=<nicho>+<cidade>+<UF>` no navegador.
2. Espere carregar (~3 s) e rode este JavaScript de **leitura**:

```js
await new Promise(r => setTimeout(r, 3000));
[...document.querySelectorAll('li')]
  .filter(li => li.querySelector('[data-entity]'))
  .map(li => {
    let e = {};
    try { e = JSON.parse(li.querySelector('[data-entity]').getAttribute('data-entity')).entity } catch (x) {}
    return [e.title, e.primaryCategoryName, e.address, e.phone, e.website || ''].join(' | ');
  }).join('\n');
```

3. O campo `website` às vezes traz Instagram, `wa.me` ou Linktree, e não um site. Classifique assim:
   - vazio → **Sem site** (a confirmar)
   - instagram.com / wa.me / linktr.ee / bio.site / facebook → **Só rede social**
   - wixsite / ueniweb / canva.site / growdoc / offstore / blogspot → **Site fraco (construtor grátis)**
   - domínio próprio → **Tem site** (só vale se o serviço do usuário for outro, ou se o site estiver ruim)
4. Faça 2 a 4 buscas com sinônimos do nicho e junte os resultados, removendo duplicados por **nome + endereço**.

## Conferir se tem site (busca pelo nome)

Numa aba do Bing (`bing.com/search?q=teste`), rode em lote, com pausa entre buscas:

```js
const nomes = ["Nome do Negócio 1 Cidade", "Nome do Negócio 2 Cidade"];
const out = [];
for (const n of nomes) {
  const h = await (await fetch('/search?q=' + encodeURIComponent(n) + '&setlang=pt-BR')).text();
  const d = new DOMParser().parseFromString(h, 'text/html');
  const sites = [...d.querySelectorAll('#b_results li.b_algo')].slice(0, 6)
    .map(li => (li.querySelector('cite')?.textContent || '').split(' ')[0].replace(/^https?:\/\//, '').slice(0, 40));
  out.push(n + ' => ' + sites.join(' ; '));
  await new Promise(r => setTimeout(r, 1000));
}
out.join('\n');
```

- Só diretórios (encontrasantarem, cylex, listamais, cnpj.biz, escavador, jusbrasil, doctoralia...) e redes sociais → **sem site próprio**.
- Apareceu um domínio com o nome do negócio → **abra e confirme** que é o mesmo negócio e a mesma cidade (existem homônimos em outros estados).
- Rode no máximo ~15 nomes por vez, para o script não passar do tempo limite do navegador.

## Instagram

- Abra `https://www.instagram.com/<perfil>/` e leia o texto da página: seguidores, posts, bio e link da bio.
- O perfil só é "confirmado" se: o link veio do próprio mapa, **ou** a bio cita a cidade, **ou** o telefone bate.
- Abra o link da bio: link quebrado (404) é um ótimo sinal de oportunidade. Linktree com 1 botão também.
- Perfil "indisponível" pode significar que o negócio fechou ou mudou de nome. Marque "Confirmar antes".
- Links `bit.ly` costumam abrir uma tela de cookies: marque "não verificado" e não cite.

## Qualidade dos dados

- Os dados do mapa envelhecem. Endereço diferente entre site e mapa é comum, e isso também é um argumento de venda.
- Se dois profissionais aparecem no mesmo endereço, talvez sejam do mesmo escritório. Aborde como um lead só.
- DDD diferente do da cidade não é erro por si só, mas vale anotar.
- Registre a **fonte e a data** de cada contato (exigência de boa prática da LGPD).
