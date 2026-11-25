<img src="assets/icon.svg" width="64" height="64" alt="">

# stanislaw.wiackowski.pl

Strona personalna Stanisława Wiąckowskiego. Statyczny HTML hostowany jako Cloudflare Worker (static assets).

```
public/        ← to idzie na produkcję (index, kontakt, podstrony książek)
drafts/        ← odrzucone warianty wyglądu, nie są deployowane
wrangler.jsonc ← konfiguracja Workera i domen
```

## Codzienna praca

```bash
npm install        # raz, po sklonowaniu
npm run dev        # podgląd lokalny: http://localhost:8787
git commit -am "…" && git push   # push na main = automatyczny deploy
```

Nowa podstrona = nowy plik w `public/`, np. `public/ksiazka-ekologia-ogolna.html`
będzie dostępny pod `stanislaw.wiackowski.pl/ksiazka-ekologia-ogolna`.

## Jednorazowa konfiguracja

1. **GitHub:** repozytorium [mwiacko/strona-personalna](https://github.com/mwiacko/strona-personalna).
2. **Cloudflare:** Workers & Pages → Create → *Import a repository* → wybierz repo.
   - Project name: `strona-personalna` (musi być zgodne z `name` w `wrangler.jsonc`)
   - Build command: puste
   - Deploy command: `npx wrangler deploy` (domyślne)
3. Pierwszy deploy sam podepnie domenę `stanislaw.wiackowski.pl`.
   Jeśli w DNS strefy `wiackowski.pl` istnieje już rekord dla `stanislaw`, usuń go wcześniej,
   inaczej podpięcie domeny się nie uda.

## Deploy ręczny (bez GitHuba)

```bash
npx wrangler login
npm run deploy
```
