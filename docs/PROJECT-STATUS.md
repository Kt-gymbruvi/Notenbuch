# Projektstand – Notenbuch

Stand: 14.11.2026 · **Etappe 1 (Umzug auf die Plattform) gebaut, noch nicht veröffentlicht.**

## Implementiert
- Quelltext des Claude-Artefakts „Notenbuch“ (Fassung vom 13.11.2026) übernommen, alle Ansichten unverändert.
- Abgleich über Supabase (`lr_tresore`, Art `notenbuch`) statt über den Claude-Speicher. Verschlüsselung, Sperre,
  automatische Sicherungen und Konfliktabfrage wie bisher. Änderungen anderer Geräte: alle 30 s und beim Zurückkehren zur Seite.
- Anmeldung mit dem Lehrkraft-Konto im Sperrbildschirm und unter Mehr → Daten (auch Abmelden). Eine schon bestehende
  Anmeldung aus Quizzo, Tafel oder Startseite gilt mit.
- Umzug: Auf dem ersten Bildschirm „Backup einspielen“ – übernimmt eine Backup-Datei aus dem Artefakt samt Passwort.
- Downloads (Backup, CSV, PDF) direkt im Browser statt über Claude.
- Alle Bibliotheken und die Schrift liegen im Repo; Rückweg zur Startseite (Haus-Knopf, „← Lehrraum“).

## Geprüft (Vorschau, 14.11.2026)
- Anlegen, Sperren/Entsperren, Backup einspielen auf leerem Gerät, PDF-Erzeugung (jsPDF), pdf.js laden, Texterkennung
  eines Testbilds mit dem lokalen deutschen Modell; Netzwerk: nur eigene Dateien.
- Abgleich mit nachgebautem Server: Hochladen, Übernahme vom anderen Gerät, gleichzeitige Änderung mit Rückfrage.
- Handy (375 px) dunkel, PC hell.

## Nicht geprüft / offen
- **Echter Abgleich mit Supabase:** Die Migration `011_tresore.sql` (im Quizzo-Repo) muss erst im Supabase-Dashboard ausgeführt werden.
- Echtes iPad und Handy; Datei-Download auf dem iPad (Safari).
- GitHub-Repository `Kt-gymbruvi/Notenbuch` anlegen, Pages einschalten (Branch `main`, Root).
- Aussehen noch mit Gelb als Akzent (wie das Artefakt); Umstellung auf die Plattformfarben (Türkis) später.
- Klären mit Schulleitung/Datenschutz: Noten auf privaten Geräten und Abgleich über Supabase (siehe Hinweis unter Mehr → Daten).

## Nächste Schritte
1. Migration ausführen, Repo anlegen, veröffentlichen (nach Zustimmung), mit echtem Konto auf zwei Geräten prüfen.
2. Daten umziehen: im Artefakt Backup speichern, hier einspielen.
3. Etappe 2: Namensliste für die Tafel (`lr_tresore`, Art `namen`, nur Klassen und Namen).
