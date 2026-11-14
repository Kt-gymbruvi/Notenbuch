# Entscheidungen – Notenbuch

## 2026-11-14 – Umzug vom Claude-Artefakt auf die Plattform (Etappe 1)
- **Warum:** Die Tafel (Lehrraum) soll die Klassen und Namen aus dem Notenbuch automatisch bekommen. Ein Artefakt auf claude.ai und eine Seite auf kt-gymbruvi.github.io können ihre Speicher nicht gegenseitig lesen. Entschieden von der Lehrkraft am 14.11.2026, mit demselben Passwort für Notenbuch und Namen.
- **Eigenes Repo `Notenbuch`**, reines HTML ohne Build – so bleibt die Einzeldatei des Artefakts erhalten und lässt sich weiter pflegen.
- **Verschlüsselung unverändert** (PBKDF2 250 000 Runden, AES-256-GCM, Format von Backup und `nb_vault_v1` gleich). So lassen sich Backups aus dem Artefakt direkt einspielen.
- **Ein Tresor je Lehrkraft in `lr_tresore`** (statt Aufteilung in Stücke wie beim Claude-Speicher). Gespeichert wird über `lr_tresor_speichern` nur, wenn die erwartete Fassung noch stimmt – sonst Rückfrage wie bisher. Dieselbe Tabelle dient später für die Namensliste (`namen`) und die Lehrraum-Klassen (`klassen`).
- **Anmeldung mit supabase-js** (im Repo), gleicher Speicherort wie Quizzo und Tafel – eine Anmeldung gilt überall. Ohne Anmeldung arbeitet das Notenbuch nur auf dem Gerät.
- **Änderungen anderer Geräte durch Nachsehen** (alle 30 s, beim Zurückkehren) statt Echtzeit-Kanal: einfacher, keine Freigabe der Tabelle für Echtzeit nötig.
- **Bibliotheken im Repo** statt CDN (Plattformregel). Texterkennung mit dem kleineren deutschen Modell (best_int, 1,3 MB) und nur den LSTM-Kernen.
- **Aussehen vorerst unverändert** (Dunkelblau/Gelb des Artefakts), damit der Umzug nichts an der Bedienung ändert.
