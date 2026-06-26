# art2media — Tools

Sammlung interner, statischer **HTML/JS-Tools**. Ein Unterverzeichnis pro Tool, jeweils mit `index.html`.

## Hosting / Veröffentlichung
- Repo: **privat** (`github.com/art2media/Tools`).
- Ziel: GitHub Pages unter Domain **`tools.art2.media`**, ein Tool je Pfad → `tools.art2.media/<tool>/`.
- ⚠️ **Plan-Hürde:** Pages aus einem **privaten** Repo erfordert **GitHub Team**. Die Org ist aktuell auf **Free** → Pages geht dort nur aus **öffentlichen** Repos. Solange Free: entweder Repo öffentlich schalten **oder** auf Team upgraden.
- Hinweis: Bei rein **clientseitigen** Tools ist der Quellcode im veröffentlichten HTML ohnehin einsehbar (View Source). Ein privates Repo verbirgt dann nur Commit-Historie und noch **nicht veröffentlichte** Tools.

## Konventionen
- Jedes Tool ist **eigenständig**, ohne externe Abhängigkeiten und **ohne Build-Schritt** (damit Pages per „Deploy from a branch" ohne Actions ausliefert).
- Tool-Ordner: `kebab-case`; Einstieg immer `index.html`.
- Optional später: eine `index.html` im Repo-Root als Tool-Übersicht.

## Tools

### `shopify-galerie/` — „Shopify Galerie Konfigurator"
Baut & pflegt den `_Galerie`-Property-String für die per-Option Galerie-Steuerung (zuerst Wohnberger-Schallabsorber; Shopify, CustomLayer-App `cl-po`).

- **Format:** `Name=Wert&Name=Wert:1,2;…` — `;` trennt Regeln · `:` trennt Bedingungen von Bild-Indizes (1-basiert) · `&` = UND · `=` Name→Wert · `,` Indizes. Trennzeichen `; : , = &` dürfen nicht in Namen/Werten vorkommen.
- **Auto-Nummerierung:** fortlaufende Bild-Indizes je „Bilder pro Kombination"; zusätzlich **feste Indizes** pro Regel (z. B. Bilder am Galerie-Ende, regelübergreifend teilbar).
- **Reader-JS im Theme bleibt unverändert** — es unterscheidet nicht zwischen automatischen und festen Indizes (configuredSet/selectedSet).
- Optionsnamen/Werte müssen **exakt** wie im Konfigurator heißen (Umlaute, „°", Leerzeichen).
