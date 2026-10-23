# Manuelle Testfälle – Animation und visuelle Qualität

> **Dokumenttyp: Manuelle Testfälle mit Ausführungsstatus.** Im Oktober 2026 aus den Projektanforderungen und aus [QA-01](../bug-reports/01-visual-quality-review.md) formuliert. Die Abläufe habe ich im Spiel mehrfach ausgeführt, die Mehrspielerfälle mit zwei Clients auf einem Rechner ([QA-04](../bug-reports/04-remote-player-display.md)). Stand der Statusangaben: 23.10.2026.

**Statuswerte:** NOT EXECUTED · PASS · FAIL · BLOCKED · UNKNOWN / HISTORICAL

## Gemeinsame Voraussetzungen

- Aktueller Client-Build, Stand bei Ausführung notieren
- Spielfigur mit den drei Grundanimationen Idle, Run und Attack
- Für AN-06 und AN-07: zwei Clients am selben Server

## Übersicht

| ID | Titel | Status |
|---|---|---|
| AN-01 | Idle im Stand | PASS |
| AN-02 | Übergang Idle ↔ Run | PASS |
| AN-03 | Übergang Run → Attack → Run | PASS |
| AN-04 | Rotation während Bewegung und Kampf | PASS |
| AN-05 | Angriffsanimation bei schnellen Eingaben | PASS |
| AN-06 | Laufanimation anderer Spieler | PASS |
| AN-07 | Angriffsanimation anderer Spieler | PASS |
| AN-08 | Sichtprüfung des Charaktermodells | BLOCKED |

---

### AN-01 – Idle im Stand

- **Testziel:** Die Figur spielt im Stand gleichmäßig Idle.
- **Voraussetzungen:** Kein Ziel, keine Eingabe.
- **Schritte:**
  1. 30 Sekunden ohne Eingabe beobachten.
- **Expected Result:** Idle läuft in Schleife, ohne sichtbaren Sprung am Schleifenende. Die Füße rutschen nicht über den Boden.
- **Actual Result:** Wie erwartet.
- **Execution Status:** PASS
- **Dokumentationshinweis:** –

### AN-02 – Übergang Idle ↔ Run

- **Testziel:** Übergänge sind weich.
- **Voraussetzungen:** Figur steht.
- **Schritte:**
  1. `W` drücken, 2 Sekunden laufen, loslassen.
  2. Fünfmal wiederholen, auch mit sehr kurzen Tastendrücken.
- **Expected Result:** Weiche Überblendung (Bruchteil einer Sekunde) in beide Richtungen. Kein Einfrieren, kein Zucken, keine Laufanimation im Stand.
- **Actual Result:** Wie erwartet.
- **Execution Status:** PASS
- **Dokumentationshinweis:** Grenzfall „kurze Eingaben“.

### AN-03 – Übergang Run → Attack → Run

- **Testziel:** Angriff und Bewegung lösen sich sauber ab.
- **Voraussetzungen:** Puppe A etwa 8 m entfernt.
- **Schritte:**
  1. Auf A doppelklicken (Figur läuft heran und greift an).
  2. Während eines Schlags mit `S` weglaufen.
- **Expected Result:** Run beim Heranlaufen, Attack erst in Reichweite. Bei `S` bricht der Schlag sofort ab und Run setzt ein. Kein Weiterspielen des Schlags in der Bewegung.
- **Actual Result:** Wie erwartet.
- **Execution Status:** PASS
- **Dokumentationshinweis:** Zusammen mit CB-06 ausführbar.

### AN-04 – Rotation während Bewegung und Kampf

- **Testziel:** Die Figur zeigt immer in eine nachvollziehbare Richtung.
- **Voraussetzungen:** Auto-Attack gegen A läuft.
- **Schritte:**
  1. Seitlich an A vorbeilaufen.
  2. Anhalten.
  3. Kamera um die Figur drehen.
- **Expected Result:** In Bewegung zeigt die Figur in Laufrichtung, im Stand zu A. Die Drehung ist weich.
- **Actual Result:** Wie erwartet.
- **Execution Status:** PASS
- **Dokumentationshinweis:** –

### AN-05 – Angriffsanimation bei schnellen Eingaben

- **Testziel:** Wiederholte Befehle und Unterbrechungen führen nicht zu flackernden Animationen.
- **Voraussetzungen:** Auto-Attack gegen A läuft.
- **Schritte:**
  1. Fünfmal schnell auf A doppelklicken.
  2. `W` 2 Sekunden gedrückt halten, dabei auf Zucken achten.
- **Expected Result:** In Schritt 1 läuft der Schlag ohne Neustart weiter. In Schritt 2 wird der Schlag einmal abgebrochen, danach läuft Run gleichmäßig.
- **Actual Result:** Wie erwartet.
- **Execution Status:** PASS
- **Dokumentationshinweis:** Dieses Verhalten wurde am 11.09.2026 geändert, siehe [QA-02](../bug-reports/02-auto-attack-input.md).

### AN-06 – Laufanimation anderer Spieler

- **Testziel:** Andere Spieler werden mit passender Animation und Blickrichtung dargestellt.
- **Voraussetzungen:** Lokaler Server, zwei Clients (1 und 2) auf demselben Rechner, je eine Figur eingeloggt.
- **Schritte:**
  1. In Client 2 im Stand die Figur drehen, dann im Kreis laufen, stehen bleiben, springen.
  2. In Client 1 beobachten.
- **Expected Result:** Run während der Bewegung, Idle im Stand, Blickrichtung in Laufrichtung. Kein Flackern zwischen Idle und Run. Der Sprung löst keine Laufanimation aus.
- **Actual Result:** Wie erwartet.
- **Execution Status:** PASS
- **Dokumentationshinweis:** Regressionstest zu [QA-04](../bug-reports/04-remote-player-display.md).

### AN-07 – Angriffsanimation anderer Spieler

- **Testziel:** Angriffe anderer Spieler sind sichtbar und enden sauber.
- **Voraussetzungen:** Wie AN-06, eine Puppe in der Nähe.
- **Schritte:**
  1. In Client 2 die Puppe angreifen, dann weglaufen.
  2. In Client 1 beobachten.
  3. Beide Figuren greifen gleichzeitig dieselbe Puppe an.
- **Expected Result:** Client 1 zeigt die Angriffsanimation und danach Run bzw. Idle. Bei gemeinsamen Angriffen sind in beiden Clients die Angriffe beider Figuren und die Schadenszahlen sichtbar.
- **Actual Result:** Wie erwartet.
- **Execution Status:** PASS
- **Dokumentationshinweis:** –

### AN-08 – Sichtprüfung des Charaktermodells

- **Testziel:** Das Modell entspricht der Vorlage, aus allen Blickwinkeln und in Bewegung.
- **Voraussetzungen:** Modellkandidat in einer Prüfszene; Vorlage mit Vorder-, Seiten- und Rückansicht.
- **Schritte:**
  1. Gesamtfigur von vorne, seitlich und hinten mit der Vorlage vergleichen.
  2. Zusätzlich aus schrägen Winkeln und von oben/unten betrachten.
  3. Nahansichten von Händen, Füßen und Gelenken.
  4. Idle, Run und Attack abspielen und Gelenke beobachten.
  5. Für jede Auffälligkeit notieren, in welcher Pose bzw. Animation sie sichtbar ist.
- **Expected Result:** Proportionen und Formen entsprechen der Vorlage. Keine Durchdringungen, Knicke oder unnatürlichen Formen in Ruhe und in Bewegung.
- **Actual Result:** –
- **Execution Status:** BLOCKED
- **Dokumentationshinweis:** Blockiert, weil die Basis des Charaktermodells gerade ausgetauscht wird. Schritt 5 ist eine direkte Lehre aus [QA-01](../bug-reports/01-visual-quality-review.md): Ein Teil der damaligen Auffälligkeit stammte aus der Testpose, nicht aus dem Modell.
