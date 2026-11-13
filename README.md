# Matten-Übersicht Helmut Körchnig Halle

Zwei Seiten, die über Firebase live verbunden sind:

- `index.html`: öffentliche Anzeige für Sportler, nur lesen
- `admin.html`: Bereich für die Hallenwärter, nur mit Zugangscode

Jede Änderung im Hallenwärter-Bereich erscheint sofort auf der öffentlichen Anzeige.

## Einrichtung

1. Firebase-Projekt anlegen und eine Realtime Database in Europa (Region `europe-west1`) erstellen.
2. Unter „Authentication“ → „Anmeldemethode“ den Anbieter „Anonym“ aktivieren. Die Hallenwärter brauchen kein eigenes Konto, nur den Code.
3. In der Datenbank den Zugangscode unter `zugang/code` eintragen. Den Code nicht in dieses Repository schreiben, es ist öffentlich.
4. Unter „Regeln“ den Inhalt von `database.rules.json` einfügen und veröffentlichen.
5. Die Werte aus der Firebase-Konsole in `js/config.js` eintragen.
6. `admin.html` öffnen, den Code eingeben und einmal „Startliste anlegen“ drücken.

## Zugangscode ändern

Den neuen Code unter `zugang/code` eintragen. Alle bisherigen Anmeldungen werden dadurch ungültig, die Hallenwärter müssen sich mit dem neuen Code neu anmelden.

## Datenstruktur

`matten/<id>` mit diesen Feldern:

- `name`: Anzeigename
- `status`: `draussen`, `drinnen` oder fehlt (keine Angabe)
- `bisDatum`: bis wann die Matte draußen bleibt, Format `JJJJ-MM-TT`
- `aufbauAb`: ab wann die Matte wieder aufgebaut wird (nur bei `drinnen`), Format `JJJJ-MM-TT`
- `reihenfolge`: Sortierung auf der Anzeige
- `geaendert`: Zeitpunkt der letzten Änderung

`admins/<uid>`: Freischaltung einer Anmeldung. Sie entsteht beim Anmelden mit dem Code automatisch. Nicht von Hand ändern.

Achtung: Alles unter `matten` ist öffentlich lesbar. Dort keine persönlichen Daten speichern.

## Veröffentlichen

Über GitHub Pages: Repository → Settings → Pages → Branch `main`, Ordner `/ (root)`. Danach ist die Anzeige unter `index.html` erreichbar, der Hallenwärter-Bereich unter `admin.html`.
