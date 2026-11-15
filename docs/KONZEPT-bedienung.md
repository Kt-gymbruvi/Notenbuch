# Konzept: Neue Bedienung des Notenbuchs

Stand: 15.11.2026 · abgestimmt mit der Lehrkraft, Etappen 1–6 gebaut (Branch, nicht veröffentlicht).

## Ausgangslage (Probleme heute)
- Dieselbe Klasse hat zwei verschiedene Bedienleisten: aus dem Stundenplan das Sitzplan-Vollbild mit eigener Modusspalte
  (`fsSeatsHTML`, `.fsl`), aus „Erfassen → Liste“ eine Knopfreihe oben (`erfassenHTML`). Ein Tipp auf einen Namen bewirkt
  im Sitzplan den gewählten Modus, in der Liste öffnet er immer den Schnelldialog (`quick`).
- Anwesenheit gibt es dreifach (Sitzplan-Modus, Reiter „Fehlzeiten“, Handy-Reiter „Anwesenheit“), Vergessen doppelt.
- Die Hauptnavigation wechselt je nach Gerät und Fach (`tabsFor`); auf dem iPad verschwindet sie im Sitzplan ganz.
- Lehrstoff, Listen, AV/SV-Übersicht und Beobachtungen liegen unter „Mehr“ zwischen Einstellungen und Backup.

## Grundregeln
1. **Eine Klassenansicht, egal von wo.** Plan, Klassenwahl, Suche: immer derselbe Bildschirm, dieselbe linke Spalte.
   Sitzplan/Namen ist nur ein Umschalter über dem Inhalt.
2. **Erst Modus, dann Tippen.** Der Modus links bestimmt, was ein Tipp auf einen Namen tut – im Sitzplan und in der
   Namensliste gleich. Der bisherige Schnelldialog entfällt als Standard.
3. **Feste Orte.** Knöpfe stehen immer an derselben Stelle; was gerade nicht passt, wird grau statt ausgeblendet.
   Ausnahmen nur durch feste Eigenschaften der Lerngruppe (AV/SV nur Sek I, Messwerte nur Sport).
4. **Erfassen oben, Auswerten darunter.**
5. **Ein Wort pro Sache:** „Erfassen“ (nicht „Eintragen“), „Anwesenheit“ = Modus, „Fehlzeiten“ = Auswertung,
   „Liste“ nur für Abhaklisten, Umschalter heißt „Sitzplan | Namen“.

## Klassenansicht iPad und PC

Die heutige Hauptnavigation entfällt in der Klassenansicht vollständig; es gibt nur noch diese linke Spalte.

| Gruppe | Einträge | Verhalten |
|---|---|---|
| Kopf | Klassenname, aktuelle Stunde | Antippen = Lerngruppe wechseln |
| Unterricht | Lehrstoff · Zufall · Liste | Werkzeuge (Fenster/Overlay). Liste zeigt Zähler der aktiven Liste (z. B. 12/28) |
| Erfassen | Anwesenheit · Mitarbeit · AV/SV (Sek I) · Vergessen · Note für Gruppe · Arbeiten | Modi; aktiver Modus hervorgehoben |
| Erfassen (Sport) | Anwesenheit · Mitarbeit · Messwerte · Vermerke · Note für Gruppe · Arbeiten | wie oben |
| Überblick | Noten · Fehlzeiten · (Sport: Messwerte) · AV/SV · Beobachtungen | Auswertungen, ersetzen den Inhaltsbereich |
| Unten | Hinweis Stundenende (falls nötig) · Stundenplan · Mehr | |

- **Kopfzeile des Inhalts:** Umschalter „Sitzplan | Namen“, Modus und Datum, rechts „Tische umstellen“ (nur im Sitzplan).
  Tische umstellen ist kein Erfassungsmodus mehr.
- **Rechte Spalte:** nur Kontext zum aktiven Modus – Datum (früher/später/heute), bei Mitarbeit Zeitraum
  (Tag / 4 Wochen / bis dahin), bei Vergessen/Vermerken die Art, bei Messwerten die Sportart. Im iPad-Hochformat
  darf sie als Leiste über den Raum rücken.
- **Außerhalb einer Klasse** (Stundenplan, Mehr): schlanke Leiste mit Stundenplan · zuletzt geöffnete Klasse · Mehr.
  Haus-Knopf zur Startseite und „Sperren“ wandern unten in die Spalte bzw. nach Mehr.

## Die Modi

- **Start immer mit Anwesenheit.** Ausnahme: Ist die Anwesenheit für heute in dieser Lerngruppe schon erfasst
  (zweites Öffnen, Doppelstunde), öffnet die Klasse mit Mitarbeit. Gilt auch für Sport.
- **Anwesenheit:** Standard „alle da“. Großer Knopf „Alle da, weiter“ bestätigt und schaltet auf Mitarbeit.
  Tippen schaltet da → E → U → V → da. Oben Zusammenfassung („2 fehlen, 1 unentschuldigt“).
- **Mitarbeit:** Tippen öffnet die Notenauswahl (Tendenz, Noten, letzte Einträge). „Mehr …“ darin für Kategorie und
  Bemerkung – damit lassen sich auch andere Noten erfassen (ersetzt den Schnelldialog `quick`).
- **AV/SV:** wie bisher, in Sitzplan und Namensliste gleich.
- **Vergessen / Vermerke:** Art rechts wählen, Tippen setzt/entfernt; bei Sport Verletzt/Erkrankt mit E/U-Kreislauf.
- **Messwerte (Sport):** Sportart rechts wählen, Tippen öffnet die Messwerteingabe für die Person.
- **Note für Gruppe:** bleibt eigener Eintrag in der Spalte (bisheriger Dialog „Gruppe eintragen“); keine zusätzliche
  Mehrfachauswahl im Modus Mitarbeit.
- **Einheitliche Kennzeichen** auf Tischen und Namenskacheln in allen Modi: fehlt (E/U/V), befreit, NTA, heutige Vermerke.

## Werkzeuge
- **Lehrstoff:** Fenster zum Eintragen (gemacht / geplant) **und daneben die letzten Stunden** dieser Lerngruppe
  (bisher Mehr → Lehrstoff). Auf dem Handy die letzten Stunden unter dem Eingabefeld.
- **Zufall:** wie bisher (nur Anwesende, ohne Wiederholung), aus jedem Modus erreichbar.
- **Liste:** aktive Abhakliste wählen bzw. anlegen; solange aktiv, haken Tipps ab (wie heute), mit deutlichem Banner
  und „Fertig“.

## Querschnitt
- **Rückgängig-Leiste:** Nach jedem Tipp unten ca. 5 s „Greta: 2 eingetragen · Rückgängig“. In allen Modi, auch für
  „Alle da, weiter“. Ein neuer Tipp ersetzt die Leiste; Rückgängig gilt nur für den letzten Schritt.
- **Hinweis Stundenende:** Ist die Stunde laut Plan vorbei und für heute kein Lehrstoff erfasst, erscheint unten in der
  Spalte (Handy: über der Modusleiste) „Lehrstoff noch nicht eingetragen“ → öffnet das Lehrstoff-Fenster.
- **Schülerkarte von überall:** Lang drücken (iPad/Handy) bzw. Rechtsklick (PC) auf einen Namen öffnet in jedem Modus
  die Detailansicht der Person.
- **Fehlzeiten auch in der Schülerkarte:** Summen E/U/V, Verspätungen, Vermerke und die Tage mit Datum.
  Die Klassenauswertung „Fehlzeiten“ bleibt zusätzlich bestehen.
- **Befreiungen** (Sport) gehören in die Schülerkarte.

## Handy
- Unten vier feste Reiter: **Plan · Klasse · Überblick · Mehr**.
- **Klasse:** oben Klassenname mit Symbolen für Lehrstoff, Zufall, Liste; darunter waagerecht scrollbare Modusleiste;
  darunter die Namensliste. Start mit Anwesenheit und „Alle da, weiter“ wie oben.
- **Überblick:** Unterreiter Noten · Fehlzeiten (Sport: Messwerte) · AV/SV · Beobachtungen.
- **Arbeiten** gehört zu Erfassen (Nachtrag 15.11.2026): iPad/PC in der Spalte unter „Note für Gruppe“, Handy in der Werkzeugreihe der Klasse.

## „Mehr“ danach
Nur noch Klassenübergreifendes: Suche, Lerngruppen, Schülerliste/Import, Leistungstabellen Sport, Sportarten und
Gewichtung, Daten und Sicherheit. Lehrstoff, Listen, AV/SV-Übersicht und Beobachtungen werden über die Klasse erreicht
(Werkzeuge bzw. Überblick).

## Nicht übernommen
- Karte zum Stundenstart (geplanter Lehrstoff, offene Listen) – stört beim Start mit Anwesenheit.
- Letzten Modus pro Klasse merken – ersetzt durch „immer Anwesenheit“.

## Umsetzung in Etappen
Tresorformat bleibt unverändert; nur Oberfläche und `UI`-Zustand. Jede Etappe einzeln nutzbar und veröffentlichbar.

1. **Gemeinsamer Zustand:** `UI.seatMode` → `UI.modus`, von Sitzplan und Namensliste gelesen. `A.slot` und Klassenwahl
   öffnen dieselbe Klassenansicht mit Startregel (Anwesenheit bzw. Mitarbeit, wenn schon erfasst).
2. **Namensliste folgt dem Modus:** Kachel-Tipp nutzt dieselbe Logik wie der Tisch-Tipp (`desksHTML`);
   Schnelldialog wird „Mehr …“ in der Notenauswahl. Rückgängig-Leiste und Langdruck → Schülerkarte.
3. **Neue linke Spalte (iPad/PC):** gemeinsame Funktion (z. B. `klassenSpalteHTML(c)`) ersetzt `tabsFor`-Navigation
   und `.fsl`; Sitzplan nutzt sie auch im Vollbild. Rechte Spalte nur Kontext. Tische umstellen in die Kopfzeile.
4. **Anwesenheit/Fehlzeiten trennen:** Erfassung in den Modus, `fehlHTML` wird reine Auswertung;
   Fehlzeiten in die Schülerkarte. Messwerte als Modus (Sport).
5. **Werkzeuge und Mehr:** Lehrstoff-Fenster mit letzten Stunden, Hinweis Stundenende; Mehr aufräumen; Begriffe
   vereinheitlichen.
6. **Handy:** vier Reiter, Modusleiste.

Prüfen jeweils mit `pruefen.mjs` und in der Vorschau „notenbuch“: Handy, iPad, PC, hell und dunkel.
