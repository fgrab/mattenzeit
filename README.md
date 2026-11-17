# Mattenzeit

Prototyp einer Heimtraining-App für Yogamatte, Eigengewicht und einfache Geräte (Kettlebell, Bänder).
Läuft als installierbare Web-App (PWA) direkt im Browser, auch offline.

**Installieren auf dem iPhone/iPad:** Seite in Safari öffnen → Teilen → „Zum Home-Bildschirm“.

## Funktionen
- Einstieg mit Profil und Einstufungstest
- Trainingsvorschlag nach verfügbarer Zeit, Tagesform und Lücken in den Bewegungsmustern
- Einweisung für neue Übungen, Sprachansagen mit Restzeit
- Tempo-Coach: Die Stimme gibt jede Wiederholung vor und geht automatisch weiter
- Einstufungstest im Takt mit automatischem Zählen, Vorher-Nachher beim Wiederholungstest
- Feedback pro Übung, automatische Steigerung
- Geräte-Empfehlungen auf Basis der Trainingsdaten
- Sicherung und Wiederherstellung der Daten als Datei
- Kopfhörer-Taste als „Geschafft“ (Versuch)

## Daten
Alle Trainingsdaten bleiben auf dem Gerät (localStorage). Nichts davon liegt in diesem Repository.

## Aufbau
| Datei | Zweck |
|---|---|
| `index.html` | Die komplette App (HTML, CSS, JavaScript) |
| `manifest.webmanifest` | Name, Farben und Symbole für die Installation |
| `sw.js` | Service Worker für den Offline-Betrieb; bei jeder neuen Version `VERSION` erhöhen |
| `fonts/` | Schriften Barlow und Barlow Condensed (SIL Open Font License) |
| `vendor/NoSleep.min.js` | Hält den Bildschirm während des Trainings an (MIT-Lizenz) |
| `icons/` | App-Symbole |

## Lokal testen
```bash
python3 -m http.server 8000
```
Dann http://localhost:8000 öffnen.
