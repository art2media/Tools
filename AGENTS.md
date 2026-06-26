# art2media — Tools

Sammlung interner, statischer **HTML/JS-Tools**. Ein Unterverzeichnis pro Tool, jeweils mit `index.html`.

## Hosting / Veröffentlichung
- Repo: **öffentlich** (`github.com/art2media/Tools`) — bewusst öffentlich, damit GitHub Pages auf dem **Free**-Plan veröffentlicht (Pages aus einem privaten Repo bräuchte **Team**).
- **Live** über GitHub Pages unter Domain **`tools.art2.media`**, ein Tool je Pfad → `tools.art2.media/<tool>/`.
- **`.nojekyll`** im Root schaltet Jekyll ab → Dateien werden 1:1 ausgeliefert; **`index.html` im Root** ist die Startseite (sonst baut Jekyll aus der README einen verlinkten „Tools"-Auto-Header).
- Hinweis: Bei rein **clientseitigen** Tools ist der Quellcode im veröffentlichten HTML ohnehin einsehbar (View Source).

## Konventionen
- Jedes Tool ist **eigenständig**, ohne externe Abhängigkeiten und **ohne Build-Schritt** (Pages „Deploy from a branch", kein Actions-Build).
- Tool-Ordner: `kebab-case`; Einstieg immer `index.html`.
- Repo-Root: `index.html` (Tool-Übersicht) + `.nojekyll`, dazu `CLAUDE.md`→`@AGENTS.md`, `AGENTS.md`, `README.md`. Neues Tool → in der `index.html`-Übersicht **und** der `README.md`-Tabelle ergänzen.

## Tools

### `shopify-galerie/` — „Shopify Galerie Konfigurator"
Baut & pflegt den `_Galerie`-Property-String für die per-Option Galerie-Steuerung (zuerst Wohnberger-Schallabsorber; Shopify, CustomLayer-App `cl-po`).

- **Format:** `Name=Wert&Name=Wert:1,2;…` — `;` trennt Regeln · `:` trennt Bedingungen von Bild-Indizes (1-basiert) · `&` = UND · `=` Name→Wert · `,` Indizes. Trennzeichen `; : , = &` dürfen nicht in Namen/Werten vorkommen.
- **Auto-Nummerierung:** fortlaufende Bild-Indizes je „Bilder pro Kombination"; zusätzlich **feste Indizes** pro Regel (z. B. Bilder am Galerie-Ende, regelübergreifend teilbar).
- **Reader-JS im Theme bleibt unverändert** — es unterscheidet nicht zwischen automatischen und festen Indizes (configuredSet/selectedSet).
- Optionsnamen/Werte müssen **exakt** wie im Konfigurator heißen (Umlaute, „°", Leerzeichen).
