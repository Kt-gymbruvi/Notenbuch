# Notenbuch

Notenbuch der Lehrkraft auf der Unterrichtsplattform https://kt-gymbruvi.github.io/ – erreichbar unter
https://kt-gymbruvi.github.io/Notenbuch/.

Alle Daten werden auf dem Gerät mit dem Notenbuch-Passwort verschlüsselt (AES-256). Zum Abgleich zwischen den Geräten
der Lehrkraft liegen sie nur verschlüsselt in der Plattform-Datenbank (Supabase, Frankfurt). Ohne das Passwort kann sie
niemand lesen. Das Repository enthält nur das Programm, keine Daten.

## Einrichtung (einmalig)
1. Im Supabase-Dashboard `../Quizzo/supabase/migrations/011_tresore.sql` ausführen (SQL Editor → New query → Run).
2. Auf GitHub das Repository `Kt-gymbruvi/Notenbuch` anlegen, hochladen, unter Settings → Pages „Deploy from a branch“, `main`, `/ (root)`.

## Umzug aus dem Claude-Artefakt
Im bisherigen Notenbuch: Mehr → Daten → „Backup speichern“. Im neuen Notenbuch auf dem ersten Bildschirm „Backup
einspielen“ und das bisherige Passwort eingeben. Danach mit dem Lehrkraft-Konto anmelden, damit der Abgleich läuft.
