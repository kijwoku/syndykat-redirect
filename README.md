# syndykat-redirect

Mikrostrona-pośrednik dla custom URL protocol `syndykat://` używanego przez
[Syndykat.Desktop](https://github.com/kijwoku/Syndykat.Desktop).

To trzeci element przepływu obok:

- `Syndykat_KRZ` - generuje raport HTML i linki "Dodaj do mojej listy",
- `Syndykat.Desktop` - odbiera `syndykat://add?...` i zapisuje ogłoszenie,
- `syndykat-redirect` - zamienia bezpieczny link HTTPS z maila na lokalny protokół.

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

Ręczne uzupełnianie formularza po samym URL nie przechodzi przez tę stronę.
Ten przepływ obsługuje `Syndykat.LinkApi` w repo `Syndykat_KRZ`.

## Hosting

GitHub Pages z gałęzi `main` w folderze `/`. Publikuje na
`https://kijwoku.github.io/syndykat-redirect/`.
