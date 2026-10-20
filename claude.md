# CLAUDE.md – Projekt „Second Brain Index"

Dieses Projekt ist eine kleine, persönliche Hilfsseite: eine statische HTML-Übersicht
(„Launcher") für Nazans Notion-Workspace **„KI Second Brain – Command Center"**. Es hat
keinen Bezug zum Kursprojekt Radwerk Mitte.

## Zweck

Schneller Einstieg in die wichtigsten Bereiche des Notion Command Centers, ohne dort erst
suchen zu müssen: Wissensbasis, Workflows, Agenten und die zugehörigen Datenbanken
(Aufgaben, Quellen, Projekte).

## Quelle (Single Source of Truth)

Notion-Workspace, Hauptseite **„KI Second Brain – Command Center"**:
https://app.notion.com/p/3e85a657be008104a376fa4bcc357247

Alle Einträge auf der Seite stammen aus der Notion-Suche (`notion-search`, MCP-Server
„claude.ai Notion") und bilden den tatsächlichen Stand des Workspaces ab. Nichts erfinden –
neue Einträge immer per Notion-Suche verifizieren, bevor sie ergänzt werden.

## Ergebnis

- `index.html` – statische Seite, kein Build-Schritt nötig, einfach im Browser zu öffnen.
- Veröffentlicht als Claude Artifact: https://claude.ai/artifact/EaJDgRkvsCUgi88qG7aox2
  (privat, nur für den Besitzer/freigegebene Personen sichtbar).

Gestaltungskonzept siehe `design.md`.

## Struktur der Seite

Die Einträge sind in `index.html` als JS-Array `DATA` hinterlegt (Titel, URL, Notion-Pfad,
Typ Seite/Datenbank, Kurzbeschreibung, letztes Bearbeitungsdatum), gruppiert nach Bereich
(`section`: Start, Wissensbasis, Workflows, Agenten, Datenbanken, Verwandt). Ein Suchfeld
filtert client-seitig über Titel, Pfad und Kurzbeschreibung.

## Aktualisieren

1. In Notion erneut suchen (`notion-search`, kurze Stichworte wie „Second Brain Command
   Center"), um neue oder geänderte Seiten zu finden.
2. Neue/geänderte Einträge im `DATA`-Array in `index.html` ergänzen oder anpassen
   (Titel, URL, Pfad, Typ, Kurzbeschreibung, Datum – wie von Notion geliefert).
3. Seite erneut als Artifact veröffentlichen (gleicher Dateipfad, damit die URL erhalten
   bleibt).

## Ordnerstruktur

- `index.html` – die eigentliche Seite (Quelle für das Artifact).
- `claude.md` – diese Datei.
- `design.md` – Gestaltungskonzept (Tokens, Typografie, Layout).
