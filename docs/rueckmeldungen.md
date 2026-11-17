# Mattenzeit: Rückmeldungen zum Prototyp

Gesammelte Rückmeldungen aus den Tests. App: https://fgrab.github.io/mattenzeit/

---

## Übersicht

Aufwand: **S** = klein, **M** = mittel, **L** = groß. Die Nummern in Klammern verweisen auf die Abschnitte unten.

### Offen, aufsteigend nach Aufwand
| # | Punkt | Aufwand | Nutzen | Bemerkung |
|---|---|---|---|---|
| 1 | Vorher-Nachher beim Wiederholungstest (1) | S | hoch | Test wiederholen geht schon, es fehlt der Vergleich mit dem letzten Test |
| 2 | Datenmodell fertig sync-fähig machen (7) | S | mittel | Trainings, Tests und Messungen haben schon IDs; fehlt: Änderungszeitpunkt für Profil und Übungsstände |
| 3 | App-Symbol: Varianten und Startbildschirm (12) | S | niedrig | Erster Entwurf läuft |
| 4 | Takt und automatisches Zählen im Einstufungstest (10) | M | hoch | Nutzt den vorhandenen Halte-Rhythmus; macht Tests vergleichbar; sollte vor dem ersten Wiederholungstest fertig sein |
| 5 | Tempo-Coach für alle Übungen (4) | M | hoch | Automatisches Weiter auch ohne Haltezeit; Tempo pro Übung, Seitenwechsel |
| 6 | Fitness-Einordnung der Testergebnisse (11) | M | hoch | Normwerte recherchieren, ggf. freiwillige Angabe zum Geschlecht |
| 7 | Kopfhörer-Taste als „Geschafft“ (5) | M | hoch | Auf iOS als Web-App unsicher: klappt nur, solange die App Ton abspielt; erst kurz ausprobieren |
| 8 | „So nicht“-Figur in der Seitenansicht (2) | M | mittel | Eine Fehler-Pose pro Übung |
| 9 | Sync mit eigenem Server auf dem NAS (7) | M–L | hoch | Braucht Docker, HTTPS und Zugriff von unterwegs |
| 10 | Figuren in 3D mit Front- und Schrägansicht (2) | L | hoch | Erst mit 4–5 Übungen ausprobieren |
| 11 | Hinweise mit passender Ansicht verknüpfen (2) | L | hoch | Setzt 3D voraus |
| 12 | Sprachbefehle, Apple Health, Apple Watch, iCloud-Sync (5, 7) | L | hoch | Nur mit nativer iOS-App sinnvoll |

### Erledigt
- **Prototyp 2:** Sprachansagen mit Fortschritt, Restzeit und Ausgangsposition (3, 6), Halte-Rhythmus (4), ganzer Bildschirm als „Geschafft“ (5), Profil und Einstufungstest (1)
- **Prototyp 3a „Echt testbar“:** installierbare Web-App mit Offline-Betrieb und App-Symbol (12), Bildschirm bleibt an (9), Sicherung/Wiederherstellung und Kopieren/Einfügen (7), mehrere Ziele (8), Haltezeit im Bridge-Test (10), BMI und Taille-zu-Größe (11), Hinweis bei neuer Version

---

## 1. Einstieg: Profil und Einstufungstest
**Status:** Profil und Einstufungstest in Prototyp 2 umgesetzt; Wiederholungstest mit Vorher-Nachher offen

**Profil (alles überspringbar, später nachtragbar)**
- Vorname (Ansprache, auch in der Sprachansage)
- Größe, Gewicht, optional Alter
- Bauchumfang, mit kurzer Anleitung: morgens, nüchtern, auf Höhe des Bauchnabels, entspannt ausatmen
- Ziel: allgemein fitter / Kraft / Beweglichkeit / Rücken / abnehmen
- Einschränkungen: Knie, Rücken, Schulter → Übungen ausschließen oder ersetzen
- Realistische Trainings pro Woche: 2 / 3 / 4

**Einstufungstest (zählt als erstes Training, ca. 10 Min.)**
- Max. Liegestütze (oder Knie-Liegestütze) → Drücken
- Max. Kniebeugen in 60 s → Kniebeuge
- Unterarmstütz halten → Rumpf
- Glute Bridge max. Wiederholungen → Hüftbeuge
- Einbeinstand mit geschlossenen Augen → Einbeinig
- Vorbeuge im Stand → Mobilität

Daraus: Startstufe und Startdosis pro Bewegungsmuster.

**Wiederholung alle 4–6 Wochen**
- Fester „Testtag“, ein paar Tage vorher angekündigt
- Vorher-Nachher-Ansicht (z. B. „Liegestütze 12 → 18, Bauchumfang 94 → 91 cm“)
- Testergebnisse korrigieren den Plan, falls das Feedback zu vorsichtig war

Ziel: Einstieg max. 2 Min. Fragen + ca. 10 Min. Test.

---

## 2. Strichmännchen aus mehreren Perspektiven
**Status:** offen

- Figuren grundsätzlich beibehalten (kommen gut an)
- Zusätzlich zur Seitenansicht eine **Frontansicht** und eine **Schrägansicht** (ca. 45°)
- Technisch: Gelenkpositionen in 3D statt 2D speichern, dann lassen sich beliebige Blickwinkel daraus berechnen
- Bedienung: 2–3 feste Ansichten zum Antippen, optional frei drehen per Wischen
- **Jeder Technikhinweis bekommt seine passende Ansicht.** Tippt man auf „Knie zeigen in Richtung Zehen“, springt die Figur in die Frontansicht und die Knie werden farbig hervorgehoben
- Standardansicht pro Übung = die Ansicht, in der der wichtigste Hinweis am besten zu sehen ist
- Frontansicht besonders wichtig für: Kniebeuge, Goblet Squat, Ausfallschritt, Bulgarische Kniebeuge, Kettlebell-Swing, Glute Bridge
- Ansicht von oben nur, wo sie wirklich hilft (z. B. Fußstellung)
- Typische Fehler als **zweite, rot markierte Figur** zeigen („so nicht“)

---

## 3. Fortschritt per Sprachansage
**Status:** in Prototyp 2 umgesetzt

- Bei jedem Wechsel ansagen: „Übung 8 von 9“
- Besondere Ansagen: „Halbzeit“, „Letzte Runde“, „Letzte Übung“
- Ansage in der Pause, zusammen mit „Als Nächstes: …“

---

## 4. Halten und Tempo per Stimme anleiten
**Status:** Haltezeit mit Halte-Rhythmus in Prototyp 2 umgesetzt (bei Übungen mit Haltezeit geht es automatisch weiter); Tempo-Coach für alle Übungen offen

- Übungen bekommen eine **Haltezeit** an der entscheidenden Stelle, z. B. Glute Bridge oben, Superman oben, Kniebeuge unten (pausiert)
- Stimme zählt mit: „Halten … 3, 2, 1 … und runter“
- Haltezeit passt sich an: Anfang 2 s, steigt mit dem Feedback auf 3, 4, 5 s. Neben Wiederholungen und Gewicht ist das ein zusätzlicher Weg zur Steigerung
- Ausbaustufe **Tempo-Coach**: Die Stimme gibt jede Wiederholung vor („runter … halten … hoch … 1“, „… 2“). Dann weiß die App, wann der Satz fertig ist, und geht **automatisch** weiter, ganz ohne Tippen
- Abschaltbar für alle, die ihr eigenes Tempo wollen

---

## 5. Freihändige Bedienung
**Status:** großer Tippbereich in Prototyp 2 umgesetzt; Kopfhörer-Taste und Sprachbefehle offen

Ziel: nicht aus der Übung heraus zum Handy auf dem Boden gehen müssen.

- **Sprachbefehle:** „Geschafft“, „Weiter“, „Pause“, „Nochmal“, „Überspringen“
  - In der nativen iOS-App gut machbar: Spracherkennung direkt auf dem Gerät, hört nur auf wenige Befehlswörter
  - Als Web-App auf dem iPhone nur eingeschränkt: Mikrofon muss erlaubt sein, Erkennung bricht ab, Atemgeräusche stören
- **Kopfhörer-Taste** (AirPods antippen, Kabel-Fernbedienung) = „Geschafft/Weiter“. Funktioniert auch in einer Web-App, sehr zuverlässig
- **Automatisch weiter** durch den Tempo-Coach (siehe Punkt 4) und bei Zeitübungen ohnehin
- **Großer Tippbereich:** ganzer Bildschirm als „Geschafft“-Taste, kein kleiner Knopf
- **Apple Watch:** Tippen am Handgelenk (spätere iOS-Version)

---

## 6. Sprachansagen neu aufbauen
**Status:** in Prototyp 2 umgesetzt

**Was der Prototyp heute sagt**
- Pausenbeginn: „Pause. Als Nächstes: [Übung]. [erster Technikhinweis].“
- Übungsstart: „[Übung]. [12] Wiederholungen.“ bzw. „[30] Sekunden. Los.“
- Letzte 3 Sekunden: nur Pieptöne
- Seitstütz: „Seite wechseln“

**Probleme**
- Die Menge (Wiederholungen/Sekunden) kommt erst beim Start, nicht in der Pause
- Keine eigene Ansage zur Ausgangsposition. Vorgelesen wird nur der erste Technikhinweis, der oft schon die Bewegung beschreibt (z. B. Swing)
- Alles wird am Pausenanfang gesagt, danach Stille. Kein „Geh in Position“
- Bildschirm und Stimme zeigen/sagen während der Übung unterschiedliche Hinweise

**Neuer Ablauf einer Pause (Beispiel 20 s)**
1. Sofort: „Gut. 20 Sekunden Pause. Das war Übung 4 von 9.“
2. Danach: „Als Nächstes: Glute Bridge, 12 Wiederholungen, oben 2 Sekunden halten.“
3. Bei 10 s: Ausgangsposition, z. B. „Leg dich auf den Rücken, Füße hüftbreit nah am Po.“
4. Bei Ortswechsel/Gerät: „Runter auf die Matte“, „Kettlebell bereitstellen“
5. Zum Schluss: 3, 2, 1 als Pieptöne (wie bisher), danach gesprochen „Los“
6. In der ersten Wiederholung: der wichtigste Technikhinweis

**Restzeit in längeren Pausen**
- Alle 10 Sekunden: „Noch 30 Sekunden“, „Noch 20“, „Noch 10“, dann „Noch 5“
- Bei 3, 2, 1 die bestehenden Pieptöne
- Gleiches Muster auch bei längeren Zeitübungen (z. B. Unterarmstütz 60 s)
- Inhaltliche Ansagen haben Vorrang: Fällt eine Restzeit-Ansage in eine laufende Ansage, wird sie übersprungen statt dazwischenzureden
- Bei kurzen Pausen (≤ 20 s) nur „Noch 10“ und „Noch 5“, damit es nicht zu voll wird
- Einstellbar: Restzeit-Ansagen an/aus

**Dafür nötig**
- Jede Übung bekommt ein eigenes Feld **Ausgangsposition** (getrennt von den Technikhinweisen)
- Jede Übung bekommt eine **Lage**: stehend / Boden / Bauchlage / Rückenlage / Vierfüßler, damit die App Ortswechsel erkennt
- Ausführlichkeit nach Status: neue Übungen ausführlich, sichere Übungen kurz
- Bildschirm zeigt immer denselben Hinweis, der gerade gesprochen wurde

---

## 7. Datenablage und Sync zwischen Geräten
**Status:** offen

**Problem heute:** Daten liegen nur im Browser des jeweiligen Geräts. Kein Abgleich zwischen iPhone und iPad. Beim Löschen der Website-Daten, Gerätewechsel oder wenn iOS den Speicher aufräumt, sind sie weg.

**Grundsatz:** Das Gerät bleibt die Hauptablage („offline zuerst“). Training funktioniert immer, auch ohne Netz. Sync passiert im Hintergrund, sobald der Server erreichbar ist.

**Stufen**
1. **Export/Import** als Datei (JSON). Sichern in iCloud Drive/Dateien-App, auf dem anderen Gerät importieren. Einfach, sofort machbar
2. **Datenmodell sync-fähig:** jede Übung/jedes Training mit eindeutiger ID und Zeitstempel, Trainings werden nur angehängt. Dann lassen sich Daten von zwei Geräten später ohne Konflikte zusammenführen
3. **Eigener Server auf dem NAS (Docker)**
   - Kandidaten: CouchDB (mit PouchDB im Browser, bewährt für Offline-Sync) oder PocketBase (ein einzelner Container, einfache Oberfläche)
   - Voraussetzungen: HTTPS (eine Web-App über HTTPS darf keinen unverschlüsselten Server ansprechen), Login, Backup des NAS
   - Zugriff von unterwegs: Tailscale/VPN statt Port im Router öffnen
   - In der App: Server-Adresse und Zugangsdaten eintragen, Status „Zuletzt synchronisiert: vor 2 Min.“
4. **iCloud-Sync** in der späteren iOS-App: für die meisten Nutzer die bequemste Lösung, kein Server nötig. NAS-Sync als Option für alle, die ihre Daten selbst halten wollen

**Konflikte:** Trainings kollidieren praktisch nie (jedes ist ein eigener Eintrag). Bei Profil und Übungsständen gewinnt die neueste Änderung; Übungsstände lassen sich notfalls aus dem Trainingsverlauf neu berechnen

---

## 8. Mehrere Ziele gleichzeitig
**Status:** in Prototyp 3a umgesetzt

- Heute nur ein Ziel wählbar. Das war eine Vereinfachung im Prototyp, keine bewusste Entscheidung
- Neu: bis zu 2–3 Ziele wählbar, z. B. „Mehr Kraft“ + „Abnehmen“ (passt gut zusammen)
- Das zuerst gewählte Ziel ist der Schwerpunkt, die anderen wirken schwächer auf den Plan
- Wirkung kombinieren: Kraft → mehr Sätze in den Hauptmustern; Abnehmen → Finisher auch bei 15 Min., kürzere Pausen; Rücken → mehr Ziehen, Hüftbeuge, Rumpf; Beweglich → Abschluss-Dehnung

---

## 9. Bildschirm geht während des Tests aus (Fehler)
**Status:** in Prototyp 3a umgesetzt (Wake Lock + NoSleep-Fallback + Hinweis)

- Ursache: Die App hält den Bildschirm nur im Training wach, im Einstufungstest wurde das vergessen
- Folge: Sprachansagen verstummen, Tippen zum Stoppen geht nicht
- Fix: Bildschirm auch im Test (und in der Einweisung) wach halten
- Fallback, falls iOS das verweigert (z. B. innerhalb des Artifact-Rahmens): stummes Video im Hintergrund abspielen, das bewährte Mittel gegen die Sperre in Safari
- Wenn beides nicht greift: beim Start einen Hinweis zeigen („Automatische Sperre kurz auf ‚Nie‘ stellen: Einstellungen → Anzeige & Helligkeit → Automatische Sperre“)
- Grundsätzlich: Ansagen bei gesperrtem Bildschirm gehen erst mit der nativen iOS-App zuverlässig

---

## 10. Tempo und Haltezeit im Einstufungstest
**Status:** Haltezeit-Hinweis im Bridge-Test umgesetzt; Takt und automatisches Zählen im Test offen

- Glute Bridge im Test: Haltezeit angeben, z. B. „oben 1 Sekunde halten“
- Besser noch: Die Stimme gibt im Test den Takt vor (wie im Halte-Rhythmus) und zählt die Wiederholungen selbst. Man tippt nur, wenn es nicht mehr geht, und muss danach keine Zahl eintragen
- Vorteil: Tests werden vergleichbar. Beim Wiederholungstest in 6 Wochen gilt dasselbe Tempo, sonst misst man auch, ob man diesmal schneller oder langsamer war
- Gleiches Prinzip für Liegestütze (z. B. 2 s runter, 1 s hoch)

---

## 11. Einschätzung von Körperwerten und Fitness
**Status:** BMI und Taille-zu-Größe umgesetzt; Fitness-Einordnung der Tests offen

**Körperwerte (in Profil und Verlauf)**
- BMI aus Größe und Gewicht, mit Einordnung (Untergewicht / Normal / Übergewicht / Adipositas) und dem Hinweis, dass der BMI Muskeln nicht von Fett unterscheidet
- Wichtiger: **Taille-zu-Größe-Verhältnis** (Bauchumfang ÷ Größe). Unter 0,5 gilt als günstig, aussagekräftiger als der BMI
- Verlauf über die Messungen

**Fitness (bei den Testergebnissen)**
- Pro Test eine grobe Einordnung: ausbaufähig / durchschnittlich / gut / sehr gut
- Grundlage: veröffentlichte Normwerte (z. B. für Liegestütze nach Alter und Geschlecht). Dafür bräuchte das Profil eine freiwillige Angabe zum Geschlecht, sonst nur grobe Einordnung ohne Geschlecht
- Für Unterarmstütz, Einbeinstand und Vorbeuge gibt es nur grobe Richtwerte, entsprechend vorsichtig formulieren
- Statt einer Gesamtnote: Profil pro Bewegungsmuster (Balken), daraus „Deine Stärke: Beine“, „Ausbaufähig: Rumpf“
- Beim Wiederholungstest: Vorher-Nachher pro Test
- Klarer Hinweis: grobe Orientierung, keine medizinische Bewertung

---

## 12. App-Symbol für die Web-App (PWA)
**Status:** erster Entwurf umgesetzt (Glute Bridge auf Kobaltblau); Varianten und Startbildschirm offen

**Gestaltung**
- Passend zur App: Strichfigur auf der Matte (z. B. Glute Bridge oder Kniebeuge als klare Silhouette), Kobaltblau als Grundfarbe
- Muss auch winzig erkennbar sein: wenige, dicke Formen, kein Text, keine feinen Linien
- 2–3 Entwürfe zur Auswahl, im Hell- und Dunkelmodus des Homescreens prüfen

**Technisch nötig**
- iOS: `apple-touch-icon` 180 × 180 px PNG, ohne Transparenz (iOS füllt sonst schwarz auf), ohne eigene abgerundete Ecken (iOS rundet selbst ab)
- Manifest: Icons in 192 × 192 und 512 × 512 px, zusätzlich eine „maskable“-Variante mit Sicherheitsrand (Motiv in den inneren 80 %), damit Android das Symbol beliebig zuschneiden kann
- Favicon für den Browser-Tab
- Name unter dem Symbol: „Mattenzeit“ passt (kurz genug, wird nicht abgeschnitten)
- Optional: Startbildschirm beim Öffnen (iOS-Splashscreen) in App-Farben

**Einordnung:** gehört zur installierbaren Web-App (Prototyp 3), Aufwand klein bis mittel
