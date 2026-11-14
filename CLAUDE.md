# Notenbuch – Projektregeln

Notenbuch der Lehrkraft (Biologie/Sport, Gymnasium Bruchhausen-Vilsen): Noten, Fehlzeiten, Arbeiten, Sport-Messwerte,
Sitzplan, Stundenplan. Teil der Unterrichtsplattform https://kt-gymbruvi.github.io/ (Startseite „Lehrraum“), erreichbar
unter https://kt-gymbruvi.github.io/Notenbuch/. Bis 14.11.2026 war es ein Claude-Artefakt; der Quelltext wurde übernommen.
Schwesterprojekte (eigene Repos): Startseite (`../Kt-gymbruvi.github.io`), Lehrraum/Tafel (`../Lehrraum`), Quizzo, Klassenfunk.
Stand: `docs/PROJECT-STATUS.md`, Entscheidungen: `docs/DECISIONS.md`. Gesamtplan zur Verzahnung mit der Tafel:
`../Lehrraum/docs/SPEC-klassen-namen-und-notenbuch.md`.

## Technik
- Eine Datei `index.html` (HTML/CSS/JS, kein Build, keine npm-Abhängigkeiten). Was im Repo liegt, wird so ausgeliefert.
- Hosting: GitHub Pages, Repository `Kt-gymbruvi/Notenbuch`, „Deploy from a branch“ (`main`, Root), `.nojekyll`.
- Bibliotheken liegen in `bibliotheken/` (supabase-js 2.119 UMD, pdf.js 3.11.174, jsPDF 2.5.1, jspdf-autotable 3.8.2,
  tesseract.js 5.1.1 mit Kern und deutschem Modell). Schrift Atkinson Hyperlegible in `schriften/`. Nichts von fremden Servern.
- Aufbau in `index.html`: `Core` (Notenrechnung, Schlüssel, Messwerte, Namenslisten, Krypto) → Speicher/Sync/Sperre → Ansichten → Dialoge → Aktionen (`A` für Klicks, `CH` für Änderungen) → Start.

## Daten und Sicherheit
- Alles wird auf dem Gerät mit dem Notenbuch-Passwort verschlüsselt (PBKDF2-SHA-256, 250 000 Runden → AES-256-GCM).
  Lokal: `localStorage` `nb_vault_v1` (verschlüsselt), automatische Sicherungen in IndexedDB `notenbuch-snapshots` (verschlüsselt).
- Abgleich zwischen Geräten: Supabase (Frankfurt), Tabelle `lr_tresore`, Art `notenbuch`, gespeichert nur über
  `lr_tresor_speichern` mit erwarteter Fassung (`rev`). Migration `../Quizzo/supabase/migrations/011_tresore.sql`.
  Nie Klartext an den Server, nie das Passwort speichern, nur der öffentliche publishable-Schlüssel.
- Anmeldung mit dem gemeinsamen Lehrkraft-Konto (supabase-js, gleicher Speicherort wie Quizzo und Tafel). Ohne Anmeldung arbeitet das Notenbuch nur lokal.
- Keine KI-Aufrufe, keine Tracker. Texterkennung (Foto) und PDF-Auslesen laufen auf dem Gerät.
- Format des Tresors nicht stillschweigend ändern: Ältere Geräte und Backups müssen lesbar bleiben.

## Arbeitsweise
- Oberfläche, Bezeichner (neuer Code), Kommentare und Commit-Nachrichten auf Deutsch.
- Prüfen: `node ../Kt-gymbruvi.github.io/werkzeuge/pruefen.mjs index.html`; ansehen über die Vorschau „notenbuch“
  (`../Kt-gymbruvi.github.io/.claude/launch.json`, Port 5210). Handy, iPad und PC, hell und dunkel.
- Es gibt keine automatischen Tests. Sync-Logik mit nachgebautem Server im Browser prüfen; echter Abgleich nur mit zwei Geräten.
- `main` ist live. Nichts veröffentlichen (Push) und nichts löschen ohne ausdrückliche Zustimmung der Lehrkraft.
