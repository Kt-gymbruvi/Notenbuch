# Projektstand – Notenbuch

Stand: 14.11.2026 · **Etappe 1 (Umzug auf die Plattform) veröffentlicht** unter https://kt-gymbruvi.github.io/Notenbuch/.
Migration `011_tresore.sql` ausgeführt (Tabelle vorhanden, ohne Anmeldung gesperrt). Die Lehrkraft hat ihre Daten aus dem
Artefakt übernommen und den Abgleich zwischen zwei Geräten mit ihrem Konto erfolgreich geprüft (14.11.2026).

## Neue Bedienung – Etappe 4: Fehlzeiten als Auswertung, Messwerte als Modus (gebaut 15.11.2026, nicht veröffentlicht)
- **Fehlzeiten** ist reine Auswertung: Tabelle je Person mit E, U, V, Vergessen/Vermerken (Halbjahr, ab 3 rot) und letztem Fehltag, sortierbar nach Namen oder Fehltagen; Zeile → Schülerkarte. Darunter „Tage mit Fehlzeiten“ (antippen = diesen Tag im Modus Anwesenheit bearbeiten). Oben „Anwesenheit heute erfassen“ und „anderer Tag“. Erfasst wird nur noch im Modus Anwesenheit. Handy-Reiter heißt jetzt „Fehlzeiten“.
- **Namensliste** hat eine Datumswahl (‹ Datum › Heute, vergangener Tag gelb) – wie der Sitzplan, für alle Modi.
- **Schülerkarte:** Kästen Fehlzeiten, Vergessen und Nicht aktiv sind antippbar und filtern die Zeitleiste (alle Tage mit Datum).
- **Messwerte (Sport)** als Erfassungsmodus: Disziplin rechts bzw. oben wählen, Person antippen → Fenster mit Messwert, Note live aus der Leistungstabelle, letzte Werte; „Speichern, nächste Person“ (Enter) springt zur nächsten anwesenden, nicht befreiten Person ohne Wert. Tische/Namen zeigen den heutigen Wert. Gespeichert wie bisher (Kategorie Praxis, Bemerkung „Disziplin: Wert“). Überblick „Sport“ (Tabelle für viele Werte, Befreiungen) bleibt.
- Geprüft in der Vorschau mit Testdaten (Sport-Lerngruppe, Testtabelle 50 m): Messwert live, Enter speichert und springt weiter, Rückgängig, Kennzeichen am Tisch/Namen; Fehlzeiten-Auswertung, Tag bearbeiten, anderer Tag, rote U-Werte; Schülerkarte-Filter; Handy-Reiter und Modusleiste. **Nicht geprüft:** echtes iPad (Tastatur im Messwert-Fenster), dunkel.

## Neue Bedienung – Etappe 3: feste linke Spalte (gebaut 15.11.2026, nicht veröffentlicht)
- iPad/PC in einer Klasse (Erfassen, Noten, Fehlzeiten, Arbeiten, Sport): nur noch die linke Spalte `klassenSpalteHTML` – Kopf (Lerngruppe wechseln) · Unterricht (Lehrstoff, Zufall, Liste mit Zähler) · Erfassen (Anwesenheit, Mitarbeit, AV/SV, Vergessen/Vermerke, Note für Gruppe) · Überblick (Noten, Fehlzeiten, Arbeiten, Sport) · Sync-Anzeige, Stundenplan, Mehr. Keine Kopfzeile, keine Navigation; Sitzplan auf iPad und PC gleich.
- Ein Modus aus Noten usw. springt zurück zur Erfassung (Sitzplan oder Namen wie zuletzt).
- Sitzplan: alte Modusspalte entfällt; Kopfzeile über dem Raum mit „Sitzplan | Namen“, aktuellem Modus und „Tische umstellen“ / „Fertig“ (zurück zum vorigen Modus). „Neu ordnen/Alle verteilen“ in der rechten Raum-Spalte. Der Modus „Listen“ entfällt: Liste über die Spalte wählen; solange aktiv, rechts Stand und „Liste beenden“.
- Namensliste iPad/PC: Werkzeuge und Modi nur in der Spalte, oben nur noch Kontext zum Modus.
- Außerhalb einer Klasse (Stundenplan, Mehr): Kopfzeile wie bisher (Startseite, Sperren), Navigation nur Plan · zuletzt geöffnete Klasse · Mehr.
- Handy unverändert (Etappe 6).
- Geprüft in der Vorschau: PC 1180 hell (alle Wechsel Spalte ↔ Ansichten, Tische, Liste, Mehr ↔ Klasse, Lerngruppenwahl), iPad hochkant 820 dunkel (Sitzplan mit Notenauswahl, Fehlzeiten), Handy unverändert. **Nicht geprüft:** echtes iPad (Vollbild, Querformat), Druck.

## Neue Bedienung – Etappe 2: Namensliste folgt dem Modus (gebaut 15.11.2026, nicht veröffentlicht)
- Namensliste (bisher „Liste“, jetzt „Namen“) hat oben eine Modusleiste: Anwesend · Mitarbeit · Vergessen/Vermerke · AV/SV (Sek I), darunter Kontext („Alle da, weiter“, Art des Vermerks, Hinweise). Vorläufig, bis die feste linke Spalte kommt (Etappe 3).
- Antippen eines Namens wirkt wie im Sitzplan (`seat`/`pick`): Mitarbeit öffnet dieselbe Notenauswahl wie am Tisch (`pickPopHTML`, neben bzw. unter/über dem Namen); „Mehr: Kategorie, Bemerkung …“ öffnet den bisherigen Schnelldialog. Datum der Namensliste = Datum des Sitzplans.
- Rückgängig-Leiste nach jedem Tipp: Anwesenheit, Vergessen/Vermerke, Abhaken in Listen, „Alle da, weiter“ (Noten und AV/SV hatten sie schon).
- Lange drücken (Finger, 0,55 s) oder Rechtsklick auf Tisch oder Namen öffnet die Schülerkarte, in jedem Modus außer „Tische“.
- Geprüft in der Vorschau mit Testdaten: alle Modi in der Namensliste, Rückgängig je Modus, Notenauswahl (PC breit, Handy dunkel), Langdruck ohne zusätzlichen Tipp, Rechtsklick in Liste und Sitzplan, Sitzplan unverändert. **Nicht geprüft:** echter Finger auf iPad/Handy (Langdruck nur nachgestellt), iOS-Kontextmenü.

## Neue Bedienung – Etappe 1: gemeinsamer Einstieg (gebaut 15.11.2026, nicht veröffentlicht)
Konzept: `docs/KONZEPT-bedienung.md`.
- `UI.seatMode` heißt jetzt `UI.modus` (Aktion `modus` statt `seatmode`); Sitzplan und Namensliste lesen denselben Zustand.
- Stundenplan und Lerngruppenwahl öffnen die Klasse gleich (`klasseOeffnen`). In Noten, Fehlzeiten, Arbeiten, Sport und Mehr wechselt die Lerngruppenwahl nur die Gruppe und bleibt in der Ansicht.
- Start mit **Anwesenheit**. Ist sie heute schon erfasst (Eintrag vorhanden oder „Alle da“ bestätigt), Start mit Mitarbeit.
- Sitzplan, Modus Anwesend: rechts „Alle da, weiter“ bzw. „Fertig, weiter“ → schaltet auf Mitarbeit. Die Bestätigung merkt sich nur das Gerät (`localStorage` `nb_anw_ok`, nur Lerngruppen-Kennung und Datum), weil „alle anwesend“ im Tresor keinen Eintrag erzeugt. Tresorformat unverändert. „Alle anwesend“ unter Fehlzeiten zählt auch als Bestätigung.
- Geprüft in der Vorschau (PC, hell, Testdaten): Plan → Anwesenheit; „Alle da, weiter“ → Mitarbeit; erneutes Öffnen → Mitarbeit; andere Gruppe → Anwesenheit; Tisch antippen → „Fertig, weiter“; Lerngruppenwahl aus Erfassen öffnet wie der Plan, aus Noten bleibt Noten. Keine Konsolenfehler. **Nicht geprüft:** iPad, Handy, dunkel; auf einem zweiten Gerät startet eine schon bestätigte Gruppe wieder mit Anwesenheit (gewollt einfach gehalten).

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
