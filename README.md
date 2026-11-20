# Champions Journal v1.3

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
- Match-Formular: Ergebnis, Datum, Archetyp, Gegner, bis zu sechs gegnerische Pokémon (mit Suchvorschlägen), optional im Kampf gesehene gegnerische Pokémon, vier eigene gewählte Pokémon, Lead, Wendepunkt, Fehlerursache, Learning, Notes, optionale Screenshot-Datei und **manuell erfasste Häufigkeit eingesetzter Attacken**.
- Statistik: Ergebnisse, Pokémon-Auswahlhäufigkeit und Siegquote, gegnerische Pokémon nach Preview/Sichtung und jeweilige Gewinnrate, Archetyp-Statistik und tatsächliche (manuell erfasste) Move-Nutzung.
- Backup: JSON-Export des gesamten Journals oder nur eines Teams; CSV-Export der Matchliste; JSON-Import. Eine Team-JSON-Datei kannst du in ChatGPT hochladen und auswerten lassen.

## Wichtig: Speicherung

**Die Daten liegen im `localStorage` des jeweiligen Browsers/Geräts.** GitHub Pages stellt nur die Website bereit. Es gibt ohne Backend weder automatische Cloud-Synchronisierung noch Account-Login. Inkognito-Modus und das Löschen von Browserdaten können den Speicher leeren. **Regelmäßig JSON-Backups exportieren.** Bilder werden komprimiert als Teil der Matches gespeichert und können den lokalen Speicher füllen.

## Pokémon-Daten / Bilder

- Basis-Roster: 231 Arten, Regulation **M-C** (Stand Herbst 2026) und 30 weitere ausgewählte Formen. Referenz: https://www.operationsports.com/all-pokemon-in-pokemon-champions-full-list-and-how-to-get-them/
- Namen: englische Bezeichnungen plus zahlreiche deutsche Suchnamen; nicht alle Übersetzungen wurden manuell erfasst. Die Pokémon-Auswahl prüft die eingebettete Liste; bei Roster-Updates `roster.js` erneuern.
- Sprites: öffentlich abrufbare Dateien über `https://play.pokemonshowdown.com/sprites/gen5/`. Für neue Champions-Megas und einzelne Sonderformen stehen dort ggf. keine eigenen Sprites bereit, deshalb zeigt der Builder Basis- oder Fallback-Bilder. Die Anwendung selbst funktioniert auch ohne Bildserver weiter.
- Fähigkeiten, Attacken und Items: **Freitext**, keine Verifikation der legalen Champions-Learnsets; das wäre eine separate Datenpflege-Aufgabe.

Pokémon ist eine Marke der jeweiligen Rechteinhaber. Nicht-offizielles, nichtkommerzielles Fanprojekt.

## Neu in Version 1.1: Gegnerische Pokémon

- Im Match-Formular stehen sechs suchbare Felder für die gegnerische Teamvorschau zur Verfügung. Die Felder unterstützen deutsche/englische Roster-Namen, erlauben aber auch freie Namen.
- Die Checkbox **„Im Kampf gesehen“** ist optional. Bitte nur tatsächlich im Kampf gezeigte Pokémon markieren; nicht automatisch alle sechs aus der Teamvorschau.
- Die Statistik zeigt pro gegnerischem Pokémon, wie oft es im Preview war und wie oft du es im Kampf gesehen hast, inklusive deiner Siegquote in diesen jeweiligen Matchgruppen.
- Beim Bearbeiten bleiben alle Angaben erhalten. Alte Freitext-Einträge „Gegnerische Pokémon“ werden in die neuen Felder übernommen, soweit sie durch Kommas, Semikola oder Zeilenumbrüche getrennt sind.
- CSV- und JSON-Export enthalten diese Angaben. **Wichtig:** Die Website benutzt denselben Browser-Speicherschlüssel wie Version 1.0. Ersetze auf GitHub nur die Website-Dateien, deine auf dieser Domain gespeicherten Daten bleiben erhalten. Vor der Aktualisierung ist ein JSON-Backup trotzdem empfohlen.

## Neu in Version 1.2: Pokémon-Sprites im Matcharchiv

- Im Matcharchiv werden jetzt **zwei 3×2-Sprite-Gruppen** angezeigt, statt Textlisten: dein Team und das gegnerische Team aus dem Preview.
- Auf deiner Seite sind die **vier mitgenommenen Pokémon** hell, nicht mitgenommene Team-Pokémon sind abgedunkelt. Ein **violetter Punkt** markiert deine beiden Lead-Pokémon.
- Gegnerische Pokémon, die im Kampf gesehen wurden, erhalten einen **türkisen Punkt**. Pokémon-Namen stehen zusätzlich als Tooltip zur Verfügung.
- Fehlende Bilder werden zunächst aus einem alternativen Sprite-Verzeichnis geladen; wenn auch dort nichts vorhanden ist, bleiben lesbare Initialen als Ersatz sichtbar. Die Website bleibt ohne Sprite-Verbindung nutzbar.
- Alte Team- und Matchdaten werden ohne Migration weiterverwendet. Der `localStorage`-Schlüssel ist unverändert.
- **Update auf GitHub Pages:** `app.js` und `styles.css` ersetzen (oder alle Dateien hochladen), dann die Seite neu laden. Vorher vorsichtshalber unter Backup die Daten exportieren.

## Update v1.3 (Darstellung)

- In der Teamübersicht passen alle **sechs Pokémon-Sprites** vollständig in ihre Team-Kachel – auch bei schmalen Karten.
- Im Matcharchiv werden **eigene eingesetzte Pokémon** und **gegenspielerische gesehene Pokémon** mit derselben deutlichen Umrandung und Hintergrundfarbe hervorgehoben.
- Wenn beim Gegner mindestens ein Pokémon als gesehen markiert ist, werden unbestätigte Preview-Pokémon wie nicht mitgenommene eigene Pokémon abgedunkelt. Ohne Sichtungsangaben bleiben alle Gegner-Sprites normal sichtbar (keine falschen Annahmen über Auswahl).
- Lead- und Gesehen-Markierungen bleiben als kleine farbige Punkte erhalten.
- **Keine Änderung am Datenformat**: vorhandene Teams/Matches bleiben nach einem Austausch von `app.js` und `styles.css` erhalten. Vor Updates trotzdem ein JSON-Backup herunterladen.
