# Champions Journal

Kleine, statische Fan-Webseite für **Pokémon Champions**: Teams bauen, Matches dokumentieren, statistisch auswerten und als JSON oder CSV exportieren.

## GitHub Pages veröffentlichen (ohne Programmieren)

1. Ein **öffentliches** neues Repository auf github.com erstellen, etwa `champions-journal`.
2. Den **Inhalt** dieses Projektordners ins Repository-Hauptverzeichnis laden: `index.html`, `styles.css`, `app.js`, `roster.js` (und optional `README.md`). Nicht nur die ZIP-Datei hochladen.
3. Im Repository **Settings → Pages** öffnen.
4. Unter **Build and deployment → Source** `Deploy from a branch` wählen. Branch `main`, Ordner `/ (root)` wählen und **Save**.
5. Website öffnen: `https://DEIN-GITHUB-NAME.github.io/champions-journal/` (ggf. kurz nach dem Deployment aktualisieren).

Zum lokalen Ausprobieren `index.html` per Doppelklick öffnen.

## Nutzung

- Startseite: Team erstellen oder auswählen.
- Team Builder: Pokémon-Suche, Spitzname, Fähigkeit, Item, Wesen, 4 Attacken und **Champions-SP: maximal 66 gesamt / 32 je Wert**.
- Match-Archiv: Siege grün / Niederlagen rot; jeden Eintrag anklicken und bearbeiten.
- Match-Formular: Ergebnis, Datum, Archetyp, Gegner, vier gewählte Pokémon, Lead, Wendepunkt, Fehlerursache, Learning, Notes, optionale Screenshot-Datei und **manuell erfasste Häufigkeit eingesetzter Attacken**.
- Statistik: Ergebnisse, Pokémon-Auswahlhäufigkeit und Siegquote, Archetyp-Statistik und tatsächliche (manuell erfasste) Move-Nutzung.
- Backup: JSON-Export des gesamten Journals oder nur eines Teams; CSV-Export der Matchliste; JSON-Import. Eine Team-JSON-Datei kannst du in ChatGPT hochladen und auswerten lassen.

## Wichtig: Speicherung

**Die Daten liegen im `localStorage` des jeweiligen Browsers/Geräts.** GitHub Pages stellt nur die Website bereit. Es gibt ohne Backend weder automatische Cloud-Synchronisierung noch Account-Login. Inkognito-Modus und das Löschen von Browserdaten können den Speicher leeren. **Regelmäßig JSON-Backups exportieren.** Bilder werden komprimiert als Teil der Matches gespeichert und können den lokalen Speicher füllen.

## Pokémon-Daten / Bilder

- Basis-Roster: 231 Arten, Regulation **M-C** (Stand Herbst 2026) und 30 weitere ausgewählte Formen. Referenz: https://www.operationsports.com/all-pokemon-in-pokemon-champions-full-list-and-how-to-get-them/
- Namen: englische Bezeichnungen plus zahlreiche deutsche Suchnamen; nicht alle Übersetzungen wurden manuell erfasst. Die Pokémon-Auswahl prüft die eingebettete Liste; bei Roster-Updates `roster.js` erneuern.
- Sprites: öffentlich abrufbare Dateien über `https://play.pokemonshowdown.com/sprites/gen5/`. Für neue Champions-Megas und einzelne Sonderformen stehen dort ggf. keine eigenen Sprites bereit, deshalb zeigt der Builder Basis- oder Fallback-Bilder. Die Anwendung selbst funktioniert auch ohne Bildserver weiter.
- Fähigkeiten, Attacken und Items: **Freitext**, keine Verifikation der legalen Champions-Learnsets; das wäre eine separate Datenpflege-Aufgabe.

Pokémon ist eine Marke der jeweiligen Rechteinhaber. Nicht-offizielles, nichtkommerzielles Fanprojekt.
