# Matten-Übersicht Helmut Körchnig Halle

Zwei Seiten, die über Firebase live verbunden sind:

- `index.html`: öffentliche Anzeige für Sportler, nur lesen
- `admin.html`: Bereich für die Hallenwärter, nur nach Anmeldung und Freischaltung

Jede Änderung im Hallenwärter-Bereich erscheint sofort auf der öffentlichen Anzeige.

## Einrichtung

1. Firebase-Projekt anlegen und eine Realtime Database in Europa (Region `europe-west1`) erstellen.
2. Unter „Regeln“ den Inhalt von `database.rules.json` einfügen und veröffentlichen.
3. Unter „Authentication“ die Anmeldemethode „E-Mail/Passwort“ aktivieren und die Konten der Hallenwärter anlegen.
4. Die Benutzer-ID (UID) jedes Hallenwärters unter `admins/<UID>` in der Datenbank auf `true` setzen. Die UID zeigt die Admin-Seite nach der Anmeldung an.
5. Die Werte aus der Firebase-Konsole in `js/config.js` eintragen.
6. `admin.html` öffnen, anmelden und einmal „Startliste anlegen“ drücken.

## Datenstruktur

`matten/<id>` mit diesen Feldern:

- `name`: Anzeigename
- `status`: `draussen`, `drinnen` oder fehlt (keine Angabe)
- `bisDatum`: bis wann die Matte draußen bleibt, Format `JJJJ-MM-TT`
- `reihenfolge`: Sortierung auf der Anzeige
- `geaendert`: Zeitpunkt der letzten Änderung

Achtung: Alles unter `matten` ist öffentlich lesbar. Dort keine persönlichen Daten speichern.

## Veröffentlichen

Über GitHub Pages: Repository → Settings → Pages → Branch `main`, Ordner `/ (root)`. Danach ist die Anzeige unter `index.html` erreichbar, der Hallenwärter-Bereich unter `admin.html`.
