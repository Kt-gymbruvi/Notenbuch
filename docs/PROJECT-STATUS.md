# Projektstand – Notenbuch

Stand: 14.11.2026 · **Etappe 1 (Umzug auf die Plattform) veröffentlicht** unter https://kt-gymbruvi.github.io/Notenbuch/.
Migration `011_tresore.sql` ausgeführt (Tabelle vorhanden, ohne Anmeldung gesperrt). Die Lehrkraft hat ihre Daten aus dem
Artefakt übernommen und den Abgleich zwischen zwei Geräten mit ihrem Konto erfolgreich geprüft (14.11.2026).

## Ein Passwort für Notenbuch, Tafel und Startseite (Tafel-SPEC Etappe B, gebaut 14.11.2026, nicht veröffentlicht)
- Gemeinsamer Schlüsselbund (`BUND` in `index.html`): Mit Anmeldung wird das Passwort beim Entsperren, Anlegen, Backup-Übernehmen und Passwortändern als nicht exportierbarer Grundschlüssel abgelegt; beim nächsten Öffnen (auch nach Eingabe in Tafel oder Startseite) öffnet das Notenbuch ohne Rückfrage („Wird geöffnet …“).
- Keine Zeitsperre mehr; „Sperren“ / „Auf diesem Gerät sperren“ löschen den Bund. Abmelden hier, Abmelden in einem anderen Tab oder einer anderen Anwendung (gemeinsame Anmeldung fehlt) löschen ihn ebenfalls; ein von woanders abgemeldetes, offenes Notenbuch sperrt sich.
- Passwort auf einem anderen Gerät geändert: Bund passt nicht → gelöscht, Hinweis „Das Passwort wurde geändert. Bitte einmal neu eingeben.“ Passwort hier geändert: erst Namensliste neu, dann Bund.
- Noch kein Notenbuch, aber Bund aus der Tafel: „Notenbuch anlegen“ übernimmt das Passwort ohne erneute Eingabe.
- Geprüft in der Vorschau (nachgestellte Anmeldung, ohne echten Server): ohne Anmeldung kein Bund; mit Bund ohne Rückfrage geöffnet; Sperren löscht den Bund; veralteter Bund → gelöscht mit Hinweis; richtiges Passwort legt den Bund an; fehlende Anmeldung beim Start löscht den Bund; Anlegen mit dem Bund aus der Tafel (Tresor mit diesem Passwort lesbar). **Nicht geprüft:** echtes Konto, zwei Geräte, Zusammenspiel unter derselben Adresse.

## Etappe 2 – Namensliste für die Tafel (gebaut 14.11.2026)
- Nach jedem erfolgreichen Abgleich legt das Notenbuch zusätzlich eine Namensliste ab (`lr_tresore`, Art `namen`): Lerngruppe (Name, Fach, Stufe, Schuljahr, Halbjahr, archiviert) und je Person Kennung, Vor- und Nachname. Keine Noten, Fehlzeiten, Notizen, NTA, Geburtsjahr, Geschlecht.
- Eigener Schlüssel aus demselben Passwort (Salz `S.namenSalt`, mit dem Notenbuch auf alle Geräte übertragen). Nach Passwortänderung neu verschlüsselt.
- Schalter unter Mehr → Daten „Lerngruppen und Namen für die Tafel freigeben“ (an). Aus = Liste wird auf dem Server gelöscht.
- Geprüft mit nachgebautem Server: Ablegen, Nachtrag einer neuen Lerngruppe, Aus/An, Passwortänderung, Sperren vergisst den Schlüssel, Inhalt ohne Noten/Notizen. Mit dem echten Server ungeprüft.

## Implementiert (Etappe 1)
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
