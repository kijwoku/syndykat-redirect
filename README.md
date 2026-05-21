# syndykat-redirect

Mikrostrona-pośrednik dla custom URL protocol `syndykat://` używanego przez
[Syndykat.Desktop](https://github.com/kijwoku/Syndykat.Desktop).

**Po co?** Gmail i większość mail clientów wycina atrybut `href` z linków
o nieznanym schemacie URI (akceptuje tylko `http`, `https`, `mailto`, `tel`).
Bez tej strony przyciski "+ Dodaj do mojej listy" w raporcie mailowym
nie działałyby — Gmail by zwyczajnie skasował `href="syndykat://..."`.

## Jak działa

Mail zawiera link do:

```
https://kijwoku.github.io/syndykat-redirect/?link=...&tytul=...&portal=...
```

JS odbiera query string, dodaje schemat `syndykat://add?` z przodu i robi
`window.location.href = ...`. Windows uruchamia zarejestrowaną aplikację
desktopową z URL'em jako argumentem.

## Hosting

GitHub Pages z gałęzi `main` w folderze `/`. Publikuje na
`https://kijwoku.github.io/syndykat-redirect/`.
