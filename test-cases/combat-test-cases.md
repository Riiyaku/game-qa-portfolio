# Manuelle Testfälle – Combat und Targeting

> **Dokumenttyp: Testentwurf.** Die Testfälle wurden im Oktober 2026 aus den Projektanforderungen und den Fallstudien [QA-02](../bug-reports/02-auto-attack-input.md) und [QA-03](../bug-reports/03-targeting-behavior.md) abgeleitet. Keiner davon wurde in dieser Form ausgeführt.

**Statuswerte:** NOT EXECUTED · PASS · FAIL · BLOCKED · UNKNOWN / HISTORICAL
PASS und FAIL werden erst nach einer protokollierten Ausführung eingetragen.

## Gemeinsame Voraussetzungen

- Aktueller Client-Build; Version bzw. Stand wird bei Ausführung notiert
- Testszene mit mindestens zwei Trainingspuppen (A, B) in unterschiedlicher Entfernung
- Figur mit Nahkampfwaffe, voller Gesundheit, keine offenen Fenster
- Standardsteuerung: Linksklick = Auswahl, Doppelklick = Angriff, WASD = Bewegung, Esc = Abbrechen

## Übersicht

| ID | Titel | Status |
|---|---|---|
| CB-01 | Einfacher Klick wählt aus, ohne anzugreifen | UNKNOWN / HISTORICAL |
| CB-02 | Doppelklick startet Angriff | UNKNOWN / HISTORICAL |
| CB-03 | Angriff außer Reichweite: automatisches Annähern | NOT EXECUTED |
| CB-04 | Zielwechsel während des Kampfes | UNKNOWN / HISTORICAL |
| CB-05 | Erneuter Doppelklick auf das aktive Ziel | NOT EXECUTED |
| CB-06 | WASD unterbricht Annäherung, Ziel bleibt | NOT EXECUTED |
| CB-07 | Doppelklick während WASD-Bewegung | NOT EXECUTED |
| CB-08 | Skill-Annäherung durch neuen Angriff ersetzt | NOT EXECUTED |
| CB-09 | Schnelle Klicks auf zwei verschiedene Gegner | NOT EXECUTED |
| CB-10 | Bodenklick zwischen zwei Klicks | NOT EXECUTED |
| CB-11 | Escape bricht den Kampf ab | UNKNOWN / HISTORICAL |
| CB-12 | Ziel stirbt während Auto-Attack | NOT EXECUTED |
| CB-13 | Anderer Spieler kann nicht angegriffen werden | NOT EXECUTED |
| CB-14 | Gegner sammeln: schnelle Zielwechsel | NOT EXECUTED |

**Vorgeschlagene Regressionsauswahl** (noch nicht ausgeführt) nach Änderungen an Klickerkennung oder Zielauswahl: CB-01, CB-02, CB-04, CB-05, CB-07, CB-09, CB-10, CB-13, CB-14. Nach Änderungen an Bewegung oder Kampfrhythmus zusätzlich CB-03, CB-06, CB-08 sowie [MV-04](movement-test-cases.md) und [AN-03](animation-test-cases.md).

---

### CB-01 – Einfacher Klick wählt aus, ohne anzugreifen

- **Testziel:** Auswahl und Angriff sind getrennt.
- **Voraussetzungen:** Kein Ziel ausgewählt. Puppe A in Nahkampfreichweite.
- **Schritte:**
  1. Puppe A einmal anklicken.
  2. 3 Sekunden warten.
- **Expected Result:** A zeigt einen grauen Ring und ein graues Dreieck, das Zielfenster zeigt A. Die Figur greift nicht an und bewegt sich nicht.
- **Actual Result:** –
- **Execution Status:** UNKNOWN / HISTORICAL
- **Dokumentationshinweis:** Teamtest vom 07.09.2026 (Projektpartner) als bestanden dokumentiert. Seitdem wurde die Klickerkennung geändert (11.09.2026). Kein aktueller Status, nicht meine Ausführung.

### CB-02 – Doppelklick startet Angriff

- **Testziel:** Doppelklick macht den Gegner zum Angriffsziel.
- **Voraussetzungen:** Puppe A in Nahkampfreichweite.
- **Schritte:**
  1. Puppe A zweimal schnell hintereinander anklicken (innerhalb von ca. 0,5 s).
- **Expected Result:** Ring und Dreieck an A werden rot. Die Figur dreht sich zu A, die Angriffsanimation startet etwa einmal pro Sekunde, Schadenszahlen erscheinen über A.
- **Actual Result:** –
- **Execution Status:** UNKNOWN / HISTORICAL
- **Dokumentationshinweis:** Wie CB-01.

### CB-03 – Angriff außer Reichweite: automatisches Annähern

- **Testziel:** Die Figur läuft selbstständig in Reichweite und greift erst dort an.
- **Voraussetzungen:** Puppe B mindestens 8 m entfernt.
- **Schritte:**
  1. Auf Puppe B doppelklicken.
  2. Beobachten, bis die Figur angekommen ist.
- **Expected Result:** Die Figur läuft mit Laufanimation zu B. Während des Laufens erscheinen keine Schadenszahlen. Nach Ankunft beginnt der Angriffsrhythmus.
- **Actual Result:** –
- **Execution Status:** NOT EXECUTED
- **Dokumentationshinweis:** Zusätzlich prüfen, ob die Figur vor dem Ziel stehen bleibt und nicht hineinläuft.

### CB-04 – Zielwechsel während des Kampfes

- **Testziel:** Eine neue Auswahl leitet den laufenden Angriff nicht um.
- **Voraussetzungen:** Auto-Attack läuft gegen Puppe A. Puppe B sichtbar.
- **Schritte:**
  1. Puppe B einmal anklicken.
  2. 3 Sekunden beobachten.
- **Expected Result:** A behält den roten Ring und wird weiter angegriffen. B zeigt den grauen Ring, das Zielfenster zeigt B.
- **Actual Result:** –
- **Execution Status:** UNKNOWN / HISTORICAL
- **Dokumentationshinweis:** Teil des Teamtests vom 07.09.2026 (Projektpartner). Kein aktueller Status.

### CB-05 – Erneuter Doppelklick auf das aktive Ziel

- **Testziel:** Ein erneuter Angriffsbefehl auf dasselbe Ziel unterbricht den laufenden Schlag nicht.
- **Voraussetzungen:** Auto-Attack läuft gegen A.
- **Schritte:**
  1. Mitten in einer Angriffsanimation erneut auf A doppelklicken.
  2. Fünfmal wiederholen.
- **Expected Result:** Die Animation springt nicht zurück auf den Anfang, der Rhythmus der Schadenszahlen bleibt gleichmäßig. Keine doppelten Treffer.
- **Actual Result:** –
- **Execution Status:** NOT EXECUTED
- **Dokumentationshinweis:** Grenzfall „schnelle Eingabe“. Siehe [QA-02](../bug-reports/02-auto-attack-input.md), Teilproblem C.

### CB-06 – WASD unterbricht Annäherung, Ziel bleibt

- **Testziel:** Manuelle Bewegung hat Vorrang, das Kampfziel geht nicht verloren.
- **Voraussetzungen:** Puppe B mindestens 8 m entfernt.
- **Schritte:**
  1. Auf B doppelklicken.
  2. Während die Figur läuft, kurz `S` drücken und loslassen.
  3. 3 Sekunden warten.
  4. Mit WASD selbst in Reichweite von B laufen und loslassen.
- **Expected Result:**
  - Nach Schritt 2: Die Figur stoppt das automatische Annähern; der rote Ring an B bleibt.
  - Nach Schritt 3: Die Figur läuft **nicht** von selbst weiter.
  - Nach Schritt 4: Die Angriffe setzen wieder ein, sobald B in Reichweite ist.
- **Actual Result:** –
- **Execution Status:** NOT EXECUTED
- **Dokumentationshinweis:** Zentraler Fall für das Zusammenspiel von Bewegung und Kampf.

### CB-07 – Doppelklick während WASD-Bewegung

- **Testziel:** Ein Angriffsbefehl wird auch während manueller Bewegung angenommen.
- **Voraussetzungen:** Puppe A sichtbar, etwa 5 m entfernt.
- **Schritte:**
  1. `W` gedrückt halten.
  2. Währenddessen auf A doppelklicken.
  3. `W` loslassen.
- **Expected Result:** A bekommt den roten Ring, obwohl die Figur sich bewegt. Die Figur läuft nicht automatisch los, solange `W` gehalten wird. Sobald A in Reichweite ist und keine Taste gedrückt ist, beginnt der Angriff.
- **Actual Result:** –
- **Execution Status:** NOT EXECUTED
- **Dokumentationshinweis:** Ob nach dem Loslassen ein automatisches Annähern starten soll, ist in den Anforderungen nicht eindeutig. Bei Ausführung das tatsächliche Verhalten notieren und klären.

### CB-08 – Skill-Annäherung durch neuen Angriff ersetzt

- **Testziel:** Ein wartender Skill wird bei einem neuen Angriffsbefehl verworfen.
- **Voraussetzungen:** Ein Ziel-Skill liegt in der Skillleiste. Puppe B weit entfernt, Puppe A nah.
- **Schritte:**
  1. B auswählen, Skill-Taste drücken (Figur läuft los).
  2. Vor der Ankunft auf A doppelklicken.
- **Expected Result:** Die Figur greift A an. Der Skill wird nicht nachträglich auf B ausgelöst.
- **Actual Result:** –
- **Execution Status:** NOT EXECUTED
- **Dokumentationshinweis:** Siehe [QA-02](../bug-reports/02-auto-attack-input.md), Teilproblem B.

### CB-09 – Schnelle Klicks auf zwei verschiedene Gegner

- **Testziel:** Zwei schnelle Klicks auf verschiedene Einheiten gelten nicht als Doppelklick.
- **Voraussetzungen:** A und B nah beieinander, kein Angriff aktiv.
- **Schritte:**
  1. A anklicken und sofort B anklicken (unter 0,5 s).
- **Expected Result:** B ist ausgewählt (grauer Ring). Kein Angriff startet.
- **Actual Result:** –
- **Execution Status:** NOT EXECUTED
- **Dokumentationshinweis:** Grenzfall „schnelle Eingabe“.

### CB-10 – Bodenklick zwischen zwei Klicks

- **Testziel:** Ein Klick auf etwas anderes setzt die Doppelklick-Folge zurück.
- **Voraussetzungen:** A in Reichweite.
- **Schritte:**
  1. A anklicken, Boden anklicken, A anklicken – alles innerhalb von ca. 0,5 s.
- **Expected Result:** Kein Angriff. A ist ausgewählt. Der Bodenklick startet eine Bewegung, die der zweite Klick auf A wieder abbricht.
- **Actual Result:** –
- **Execution Status:** NOT EXECUTED
- **Dokumentationshinweis:** –

### CB-11 – Escape bricht den Kampf ab

- **Testziel:** Escape beendet Kampf, Bewegung und Skill-Absicht und löscht danach die Auswahl.
- **Voraussetzungen:** Auto-Attack läuft gegen A, kein Fenster offen.
- **Schritte:**
  1. `Esc` drücken.
  2. `Esc` erneut drücken.
- **Expected Result:** Nach dem ersten Druck endet der Angriff und die Markierungen verschwinden. Der zweite Druck öffnet das Pausemenü. Jeder Druck bewirkt genau eine Sache.
- **Actual Result:** –
- **Execution Status:** UNKNOWN / HISTORICAL
- **Dokumentationshinweis:** Teamtest vom 07.09.2026 (Projektpartner). Die Escape-Reihenfolge wurde am 11.09.2026 erweitert. Kein aktueller Status.

### CB-12 – Ziel stirbt während Auto-Attack

- **Testziel:** Ziel- und Kampfzustand werden sauber zurückgesetzt.
- **Voraussetzungen:** Puppe A mit wenig Lebenspunkten, Auto-Attack läuft.
- **Schritte:**
  1. Angreifen, bis A besiegt ist.
- **Expected Result:** Beide Ringe, Dreieck und Zielfenster verschwinden. Es werden keine weiteren Angriffe ausgeführt. Die Schadenszahl des letzten Treffers bleibt kurz sichtbar.
- **Actual Result:** –
- **Execution Status:** NOT EXECUTED
- **Dokumentationshinweis:** Zusätzlich beobachten, ob die Figur in Idle zurückkehrt. Das ist naheliegend, in den Anforderungen aber nicht ausdrücklich festgelegt.

### CB-13 – Anderer Spieler kann nicht angegriffen werden

- **Testziel:** Spieler lassen sich auswählen, aber nicht angreifen.
- **Voraussetzungen:** Zwei Clients, beide Spieler in Sichtweite.
- **Schritte:**
  1. Im ersten Client auf den anderen Spieler doppelklicken.
- **Expected Result:** Der Spieler ist ausgewählt. Es startet kein Angriff und keine Annäherung.
- **Actual Result:** –
- **Execution Status:** NOT EXECUTED
- **Dokumentationshinweis:** Benötigt zwei Clients. Beide können auf einem Rechner gestartet werden (so habe ich andere Spieler bereits geprüft, siehe [QA-04](../bug-reports/04-remote-player-display.md)). Genau dieser Fall ist von mir nicht belegt.

### CB-14 – Gegner sammeln: schnelle Zielwechsel

- **Testziel:** Schnelle Wechsel zwischen Doppelklick, Bodenklick und nächstem Doppelklick werden ohne Verzögerung umgesetzt. Das ist der typische Ablauf, um Gegner für einen Flächenangriff zu sammeln.
- **Voraussetzungen:** Drei Trainingspuppen A, B, C mit je etwa 5 m Abstand. Kein Ziel aktiv.
- **Schritte:**
  1. Auf A doppelklicken, den ersten Treffer abwarten.
  2. Auf den Boden Richtung B klicken.
  3. Sofort auf B doppelklicken, den ersten Treffer abwarten.
  4. Auf den Boden Richtung C klicken.
  5. Sofort auf C doppelklicken, den ersten Treffer abwarten.
  6. Den Durchlauf dreimal so schnell wie möglich wiederholen.
- **Expected Result:** Jeder Doppelklick macht den Gegner sofort zum Angriffsziel (roter Ring), die Figur läuft ohne spürbare Verzögerung hin und schlägt zu. Jeder Bodenklick beendet den Kampf und startet die Bewegung. Kein Klick bleibt ohne Reaktion.
- **Actual Result:** –
- **Execution Status:** NOT EXECUTED
- **Dokumentationshinweis:** Abgeleitet aus meiner Beobachtung in [QA-02](../bug-reports/02-auto-attack-input.md). „Ohne spürbare Verzögerung“ ist eine subjektive Bewertung; bei der Ausführung eine Bildschirmaufnahme machen, damit Verzögerungen nachvollziehbar sind. Ob die getroffenen Gegner der Figur danach folgen, gehört nicht zu diesem Testziel und wäre ein eigener Testfall mit verfolgenden Monstern.
