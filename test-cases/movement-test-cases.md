# Manuelle Testfälle – Movement

> **Dokumenttyp: Testentwurf.** Abgeleitet aus den Projektanforderungen zu Bewegung, Kamera und Kampfbewegung (Stand Oktober 2026). Keiner dieser Fälle wurde in dieser Form ausgeführt. Meine früheren Bewegungstests sind nicht protokolliert und werden hier nicht als Ergebnis eingetragen.

**Statuswerte:** NOT EXECUTED · PASS · FAIL · BLOCKED · UNKNOWN / HISTORICAL

## Gemeinsame Voraussetzungen

- Aktueller Client-Build mit lokalem Server oder Offline-Testszene; Stand bei Ausführung notieren
- Ebener Boden, mindestens eine Trainingspuppe
- Standardsteuerung: WASD, rechte Maustaste halten = Kamera drehen, Mausrad = Zoom, Linksklick auf Boden = Hinlaufen, Leertaste = Springen

## Übersicht

| ID | Titel | Status |
|---|---|---|
| MV-01 | WASD bewegt relativ zur Kamera | NOT EXECUTED |
| MV-02 | Figur dreht sich in Laufrichtung | NOT EXECUTED |
| MV-03 | Klick-zu-Bewegen mit Zielmarker | UNKNOWN / HISTORICAL |
| MV-04 | WASD bricht Klick-zu-Bewegen ab | NOT EXECUTED |
| MV-05 | Bodenklick beendet Kampf, Auswahl bleibt | UNKNOWN / HISTORICAL |
| MV-06 | Schneller Richtungswechsel | NOT EXECUTED |
| MV-07 | Sprung während der Bewegung | NOT EXECUTED |
| MV-08 | Bewegung unter Netzwerkverzögerung | BLOCKED |

---

### MV-01 – WASD bewegt relativ zur Kamera

- **Testziel:** „Vorwärts“ bedeutet immer „von der Kamera weg“.
- **Voraussetzungen:** Figur steht still.
- **Schritte:**
  1. `W` halten: Laufrichtung notieren.
  2. Kamera mit gehaltener rechter Maustaste um 90° drehen.
  3. `W` erneut halten.
  4. `A`, `S`, `D` einzeln wiederholen.
- **Expected Result:** Die Figur läuft in Schritt 1 und 3 jeweils von der Kamera weg. A/S/D entsprechen links/zurück/rechts aus Kamerasicht.
- **Actual Result:** –
- **Execution Status:** NOT EXECUTED
- **Dokumentationshinweis:** –

### MV-02 – Figur dreht sich in Laufrichtung

- **Testziel:** Die Blickrichtung folgt der Bewegung, im Stand dem Kampfziel.
- **Voraussetzungen:** Puppe A ausgewählt und angegriffen.
- **Schritte:**
  1. Im Kreis um A laufen (W + A/D).
  2. Anhalten.
- **Expected Result:** Beim Laufen schaut die Figur in Laufrichtung, die Drehung ist weich und nicht ruckartig. Nach dem Anhalten dreht sie sich zu A.
- **Actual Result:** –
- **Execution Status:** NOT EXECUTED
- **Dokumentationshinweis:** Zusammen mit AN-04 ausführbar.

### MV-03 – Klick-zu-Bewegen mit Zielmarker

- **Testziel:** Die Figur läuft zum angeklickten Punkt, der Marker verhält sich korrekt.
- **Voraussetzungen:** Freier Boden, kein Ziel aktiv.
- **Schritte:**
  1. Auf einen Punkt etwa 10 m entfernt klicken.
  2. Ankunft abwarten.
- **Expected Result:** Ein türkisfarbener Marker erscheint am Punkt, die Figur läuft hin und hält an. Der Marker verschwindet bei Ankunft.
- **Actual Result:** –
- **Execution Status:** UNKNOWN / HISTORICAL
- **Dokumentationshinweis:** Teamtest vom 07.09.2026 (Projektpartner). Kein aktueller Status.

### MV-04 – WASD bricht Klick-zu-Bewegen ab

- **Testziel:** Manuelle Eingabe hat sofort Vorrang.
- **Voraussetzungen:** Wie MV-03.
- **Schritte:**
  1. Auf einen entfernten Punkt klicken.
  2. Nach etwa 1 Sekunde kurz `D` drücken und loslassen.
- **Expected Result:** Die Figur reagiert sofort auf `D`. Der Marker verschwindet. Nach dem Loslassen läuft die Figur **nicht** zum alten Punkt weiter.
- **Actual Result:** –
- **Execution Status:** NOT EXECUTED
- **Dokumentationshinweis:** Grenzfall „Unterbrechung“.

### MV-05 – Bodenklick beendet Kampf, Auswahl bleibt

- **Testziel:** Wegklicken beendet den Kampf, nicht die Auswahl.
- **Voraussetzungen:** Auto-Attack läuft gegen A.
- **Schritte:**
  1. Auf den Boden neben A klicken.
- **Expected Result:** Der Angriff endet, der rote Ring wird grau, A bleibt ausgewählt. Die Figur läuft zum Punkt.
- **Actual Result:** –
- **Execution Status:** UNKNOWN / HISTORICAL
- **Dokumentationshinweis:** Teamtest vom 07.09.2026 (Projektpartner). Kein aktueller Status.

### MV-06 – Schneller Richtungswechsel

- **Testziel:** Schnelle Wechsel führen nicht zu Ruckeln, Hängenbleiben oder Zurückspringen.
- **Voraussetzungen:** Figur steht still.
- **Schritte:**
  1. Zehnmal schnell abwechselnd `A` und `D` drücken.
  2. `W` und `S` gleichzeitig halten.
  3. Alle Tasten loslassen.
- **Expected Result:** Die Figur folgt jeder Eingabe ohne sichtbares Zurückspringen. Bei W+S bleibt sie stehen oder bewegt sich nachvollziehbar. Nach dem Loslassen steht sie still und spielt Idle.
- **Actual Result:** –
- **Execution Status:** NOT EXECUTED
- **Dokumentationshinweis:** Das Verhalten bei W+S gleichzeitig ist in den Anforderungen nicht festgelegt; beobachtetes Verhalten notieren.

### MV-07 – Sprung während der Bewegung

- **Testziel:** Sprung funktioniert in Bewegung und wird nicht doppelt ausgelöst.
- **Voraussetzungen:** Freier, ebener Boden.
- **Schritte:**
  1. `W` halten und Leertaste einmal drücken.
  2. In der Luft Leertaste erneut drücken.
  3. Nach der Landung weiterlaufen.
- **Expected Result:** Ein Sprung nach vorne. Kein zweiter Sprung in der Luft. Nach der Landung läuft die Figur ohne Ruckeln weiter.
- **Actual Result:** –
- **Execution Status:** NOT EXECUTED
- **Dokumentationshinweis:** Für den Sprung existieren automatisierte Tests im Projekt (nicht von mir). Diese ersetzen keinen Sichttest: Laut meiner Erinnerung war der Sprung anfangs im Code vorhanden, funktionierte im Spiel aber nicht (siehe [QA-04](../bug-reports/04-remote-player-display.md)).

### MV-08 – Bewegung unter Netzwerkverzögerung

- **Testziel:** Die Steuerung reagiert auch bei Verzögerung sofort, Korrekturen sind kaum sichtbar.
- **Voraussetzungen:** Client mit simulierter Verzögerung (150 ms) und 5 % Paketverlust.
- **Schritte:**
  1. 30 Sekunden mit WASD in verschiedene Richtungen laufen.
  2. Auf sichtbare Sprünge oder Gleiten achten.
- **Expected Result:** WASD reagiert sofort. Korrekturen sind unsichtbar oder höchstens ein kurzes Gleiten.
- **Actual Result:** –
- **Execution Status:** BLOCKED
- **Dokumentationshinweis:** Diese Sichtprüfung ist auch in den Projektanforderungen noch offen. Ich habe bisher nicht geprüft, wie die Verzögerung im aktuellen Stand eingeschaltet wird; bis das geklärt ist, bleibt der Fall blockiert.
