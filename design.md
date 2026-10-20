# Gestaltungskonzept – Second Brain Index

Dokumentiert die Design-Entscheidungen in `index.html`, damit spätere Anpassungen
konsistent bleiben.

## Leitidee

Konsolen-/Launcher-Optik passend zum Namen „Command Center": ruhige, dunkle Fläche,
Einträge wirken wie Zeilen in einem Datei-/Seitenbaum, ein Suchfeld oben wie eine
Kommandozeile. Kein verspieltes Dashboard mit Diagrammen – reine Navigationsseite.

## Farb-Tokens (`:root` in `index.html`)

| Token | Dark (Standard) | Light | Verwendung |
|---|---|---|---|
| `--bg` | `#0e1117` | `#f3f4f7` | Seitenhintergrund |
| `--surface` | `#161b24` | `#ffffff` | Karten/Einträge |
| `--surface-2` | `#1d2430` | `#eceff4` | Hover-Zustand der Einträge |
| `--fg` | `#e7ebf3` | `#171a21` | Fließtext |
| `--muted` | `#8993a8` | `#5c6578` | Metadaten, Pfade, Zeitstempel |
| `--accent` | `#5fd0c7` (Cyan) | `#0f8f84` (Teal) | Eyebrow, Badges, Fokus/Hover-Rand |
| `--border` | `#262e3d` | `#dde1e9` | Rahmen, Trennlinien |

Dark ist die primäre Ausrichtung; Light-Werte sind bewusst dieselbe Teal-Familie, nur
heller/kontrastreicher, damit die Seite in beiden Themes als dieselbe Marke erkennbar bleibt.
Theme-Umschaltung folgt dem Standard-Muster: `prefers-color-scheme` + `[data-theme]`.

## Typografie

- **Sora** (600/700) – Überschriften, Eyebrow-Label. Geometrisch, leicht technisch.
- **Source Sans 3** (400/600) – Fließtext, Kurzbeschreibungen. Neutral, gut lesbar.
- **JetBrains Mono** (400/500) – Pfade, Zähler, Zeitstempel, „DB"/„Page"-Badges.
  Unterstreicht den „Konsolen"-Charakter bei Metadaten, ohne den Fließtext zu dominieren.

Alle drei über Google Fonts eingebunden (`fonts.googleapis.com`), mit System-Fallback-Stacks.

## Layout

- Fixer Header mit Eyebrow, Titel, Untertitel und Live-Suchfeld; bleibt beim Scrollen sichtbar
  (`position: sticky`, berücksichtigt `safe-area-inset-top`).
- Darunter Abschnitte je Notion-Bereich (Wissensbasis, Workflows, Agenten, Datenbanken,
  Verwandt), jeweils mit Überschrift + Trefferzahl.
- Einträge als Karten-Liste: Badge (Page/DB) + Titel, darunter Notion-Pfad (mono, klein),
  optionale Kurzbeschreibung, zuletzt-bearbeitet-Datum. Einheitliche Innenabstände und
  Eckenradius (10px) für alle Karten – Konsistenz statt Abwechslung.
- Ein Gutter von mind. 16px links/rechts, responsive bis ~400px Breite, keine horizontale
  Seiten-Scrollbar.

## Interaktion

- Suchfeld filtert client-seitig (kein Server/Backend) über Titel, Pfad, Kurzbeschreibung
  und Bereichsname; Trefferzahl wird live aktualisiert.
- Jede Karte verlinkt extern zur jeweiligen Notion-Seite (`target="_blank"`), öffnet also
  immer in einem neuen Tab.
- Fokuszustand (Tastatur) sichtbar über `outline` in Akzentfarbe, sowohl am Suchfeld als
  auch an den Karten.

## Bewusst nicht enthalten

- Keine Bearbeitung/Erstellung von Notion-Inhalten direkt auf der Seite (nur Links).
- Keine serverseitige Synchronisation – Einträge werden manuell nach erneuter
  Notion-Suche gepflegt (siehe `claude.md`, Abschnitt „Aktualisieren").
