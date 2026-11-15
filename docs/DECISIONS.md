# Entscheidungen – Notenbuch

## 2026-11-15 – Aussehen wie die Tafel (Wunsch der Lehrkraft)
- **Gleiche Farben wie Tafel und Startseite** (`gemeinsam/tokens.css`, `Lehrraum/src/index.css`): helle, kühle Flächen, Dunkelblau als Farbe des Gewählten (dunkler Modus: Türkis), Türkis als Fokus. Gelb nur noch für Hinweise (vergangener Tag, Stundenende, Planung).
- **Kopfzeile und Reiterleiste als Glas** statt dunkelblauer Balken; Klassenkopf in der Spalte hell.
- **Systemschrift statt Atkinson Hyperlegible**, wie in der Tafel (wirkt auf Apple-Geräten wie eine Apple-App). Die Schriftdateien bleiben in `schriften/`, werden aber nicht mehr geladen.
- **Symbole als SVG statt Emojis** in Spalte, Werkzeugreihe und Listen-Kennzeichen (Sportarten behalten ihre Emojis).
- **Hell/dunkel gemeinsam:** Das Notenbuch liest die Auswahl `lehrraum-design` (gleiche Herkunft wie Startseite und Tafel) und nutzt `data-design` statt des alten, nie gesetzten `data-theme`.

## 2026-11-15 – Handy: vier Reiter (Bedienung Etappe 6)
- **Plan · Klasse · Überblick · Mehr.** Klasse = Werkzeugreihe (Lehrstoff, Zufall, Liste, Gruppe), Datum, waagerecht scrollbare Modusleiste (bleibt beim Scrollen oben), Namensliste.
- **Überblick mit Unterreitern** Noten · Fehlzeiten · Arbeiten · (Sport) · (AV/SV) · Beobachtungen; der Reiter öffnet den zuletzt gesehenen Unterreiter. AV/SV und Beobachtungen wie in der iPad-Spalte, damit beide Geräte gleich gegliedert sind.
- **Mehr** auf allen Geräten nur noch klassenübergreifend.

## 2026-11-14 – Gemeinsamer Schlüsselbund, keine Zeitsperre (Tafel-SPEC Etappe B)
- Das Passwort gilt einmal je Gerät für Notenbuch, Tafel und Startseite; abgelegt wird nur ein nicht exportierbarer PBKDF2-Grundschlüssel (IndexedDB `lehrraum-schluessel`). Tresorformat unverändert. Die Zeitsperre entfällt auf Wunsch der Lehrkraft; gesperrt wird bewusst („Auf diesem Gerät sperren“) oder durch Abmelden. Begründung ausführlich in `../Lehrraum/docs/DECISIONS.md`.

## 2026-11-14 – Namensliste für die Tafel (Etappe 2)
- **Eigene Liste statt Zugriff aufs Notenbuch:** Die Tafel soll nie Noten sehen; sie bekommt nur, was sie für Zufall und Gruppen braucht.
- **Gleiches Passwort, eigenes Salz:** ein Passwort für die Lehrkraft, aber ein anderer Schlüssel. Wer die Namensliste entschlüsselt, kann damit das Notenbuch nicht öffnen. Das Salz liegt im (verschlüsselten) Notenbuch, damit alle Geräte dasselbe verwenden und die Tafel nicht immer wieder nach dem Passwort fragt.
- **Immer ganz neu gebildet, neuester Stand gewinnt:** Die Liste wird aus dem Notenbuch abgeleitet, daher keine Rückfrage bei gleichzeitigem Speichern.
- **Standard: freigegeben**, abschaltbar unter Mehr → Daten (dann wird sie auf dem Server gelöscht).

## 2026-11-14 – Umzug vom Claude-Artefakt auf die Plattform (Etappe 1)
- **Warum:** Die Tafel (Lehrraum) soll die Klassen und Namen aus dem Notenbuch automatisch bekommen. Ein Artefakt auf claude.ai und eine Seite auf kt-gymbruvi.github.io können ihre Speicher nicht gegenseitig lesen. Entschieden von der Lehrkraft am 14.11.2026, mit demselben Passwort für Notenbuch und Namen.
- **Eigenes Repo `Notenbuch`**, reines HTML ohne Build – so bleibt die Einzeldatei des Artefakts erhalten und lässt sich weiter pflegen.
- **Verschlüsselung unverändert** (PBKDF2 250 000 Runden, AES-256-GCM, Format von Backup und `nb_vault_v1` gleich). So lassen sich Backups aus dem Artefakt direkt einspielen.
- **Ein Tresor je Lehrkraft in `lr_tresore`** (statt Aufteilung in Stücke wie beim Claude-Speicher). Gespeichert wird über `lr_tresor_speichern` nur, wenn die erwartete Fassung noch stimmt – sonst Rückfrage wie bisher. Dieselbe Tabelle dient später für die Namensliste (`namen`) und die Lehrraum-Klassen (`klassen`).
- **Anmeldung mit supabase-js** (im Repo), gleicher Speicherort wie Quizzo und Tafel – eine Anmeldung gilt überall. Ohne Anmeldung arbeitet das Notenbuch nur auf dem Gerät.
- **Änderungen anderer Geräte durch Nachsehen** (alle 30 s, beim Zurückkehren) statt Echtzeit-Kanal: einfacher, keine Freigabe der Tabelle für Echtzeit nötig.
- **Bibliotheken im Repo** statt CDN (Plattformregel). Texterkennung mit dem kleineren deutschen Modell (best_int, 1,3 MB) und nur den LSTM-Kernen.
- **Aussehen vorerst unverändert** (Dunkelblau/Gelb des Artefakts), damit der Umzug nichts an der Bedienung ändert.
