# Game QA & Gameplay Testing Portfolio

Manuelles Gameplay-Testing, Bugreports und QA-Fallstudien aus einem privaten MMORPG-Prototyp.

## 1. Über mich und meine Rolle

Ich prüfe Gameplay aus Spielersicht. Ich beschreibe, wie sich eine Mechanik verhalten soll, teste die Umsetzung im Spiel und reproduziere Auffälligkeiten. Fehler dokumentiere ich mit Bildschirmaufnahmen, und nach jeder Korrektur prüfe ich erneut. Diese Arbeit mache ich in einem eigenen MMORPG-Prototyp, den ich zusammen mit einem langjährigen Freund entwickle.

Beruflich arbeite ich im digitalen Marketing. Von dort bringe ich Erfahrung in eigenständiger Projektorganisation mit.

| Auf einen Blick | |
|---|---|
| Meine Rolle | Gameplay-Anforderungen, manuelles Testing, Fehlerreproduktion, Nachtests, visuelle Qualitätsprüfung |
| Technische Umsetzung | Programmcode und automatisierte Tests überwiegend durch Claude Code und OpenAI Codex; Server, Netzwerk und Datenhaltung durch meinen Projektpartner |
| Arbeitsproben | 5 Fallstudien, davon 4 mit eigenen Bildschirmaufnahmen; 30 manuelle Testfälle (27 PASS, 1 FAIL, 2 BLOCKED) |
| Am besten belegt | [Visuelle Qualitätsprüfung](bug-reports/01-visual-quality-review.md): Meine Beanstandung führte dazu, dass eine positive KI-Bewertung zurückgenommen und die Freigabe gestoppt wurde |

## 2. Das Projekt

Ein kleiner MMORPG-Prototyp nach dem Vorbild von Fly For Fun (FlyFF). Mein Projektpartner und ich haben dieses ältere MMORPG lange zusammen mit Freunden gespielt; wir kennen uns seit der Grundschule. Unser Ziel ist ein Spiel mit ähnlichem Spielgefühl, bei dem einige Dinge besser gelöst sind.

Der Server ist autoritativ und verwaltet den gesamten Spielzustand; der Client stellt dar und sendet Eingaben. Für die Tests in diesem Portfolio sind relevant:

- Bewegung mit WASD relativ zur Kamera und Klick-zu-Bewegen
- Zielauswahl per Klick, Kampf per Doppelklick, automatisches Heranlaufen an das Ziel
- Auto-Attack mit getakteten Schlägen
- Idle-, Lauf- und Angriffsanimationen, auch bei anderen Spielern
- Eine eigene Charakterbasis, die gerade entsteht (bisher wird eine Platzhalterfigur verwendet)

Das Projekt ist ein Prototyp, kein veröffentlichtes Spiel. Der Quellcode bleibt privat.

## 3. Meine QA-relevanten Tätigkeiten

| Tätigkeit | Beispiel im Portfolio |
|---|---|
| Manuelles Gameplay-Testing | Bewegung, Auto-Attack, Targeting und Animationen; [30 Testfälle](#5-manuelle-testfälle) |
| Fehlererkennung und Reproduktion | Ausfälle bei schnellen Klickfolgen ([QA-02](bug-reports/02-auto-attack-input.md)), zurückspringende Laufanimation ([QA-05](bug-reports/05-run-animation-root-motion.md)) |
| Überprüfung von Spielmechaniken | Trennung von Auswahl und Kampfziel ([QA-03](bug-reports/03-targeting-behavior.md)) |
| Mehrspieler-Prüfung | Darstellung anderer Spieler mit zwei Clients auf einem Rechner ([QA-04](bug-reports/04-remote-player-display.md)) |
| Anforderungsdefinition | Auto-Attack nach FlyFF-Vorbild; Vorgaben und Prüfregeln für die Charakterbasis |
| Bewertung von Gameplay und Bedienbarkeit | Gegner sammeln für Flächenangriffe muss mit schnellen Klicks funktionieren ([CB-14](test-cases/combat-test-cases.md)) |
| Kritische Prüfung KI-generierter Ergebnisse | Sichtbarer Formfehler trotz positiver KI-Bewertung ([QA-01](bug-reports/01-visual-quality-review.md)) |
| Dokumentation und Nachtest | Aufnahmen vor und nach der Korrektur ([QA-04](bug-reports/04-remote-player-display.md), [QA-05](bug-reports/05-run-animation-root-motion.md)) |
| Zusammenarbeit im Team | Klare Arbeitsteilung mit meinem Projektpartner; Test seines World-Editors ([Testablauf](test-process/manual-testing-workflow.md#auch-werkzeuge-testen)) |

Mein Schwerpunkt ist der Client: Gameplay, Bedienung und Darstellung. Mein Projektpartner verantwortet Server, gemeinsame Spiellogik, Authentifizierung, Netzwerk, Datenhaltung und Infrastruktur. Die im Projekt dokumentierten manuellen Tests vom 07.09.2026 hat er durchgeführt.

## 4. Ausgewählte Praxisbeispiele

Jede Fallstudie nennt am Anfang ihren Typ:

- **Original belegter Qualitätsbefund:** Meine Meldung bzw. mein Fund ist direkt dokumentiert.
- **Historisch rekonstruierte Fallstudie:** Die Änderung ist belegt; meine damaligen Testschritte sind aus Erinnerung und Aufnahmen rekonstruiert.

| Nr. | Thema | Typ | Kern |
|---|---|---|---|
| [QA-02](bug-reports/02-auto-attack-input.md) | Auto-Attack bei schnellen Zielwechseln | Rekonstruiert, mit eigener Aufnahme | Schnelle Klickfolgen wurden nicht zuverlässig umgesetzt. Das hätte das Sammeln von Gegnern für Flächenangriffe verhindert. Der Gesamtablauf ist noch FAIL. |
| [QA-03](bug-reports/03-targeting-behavior.md) | Targeting: Auswahl und Kampfziel | Rekonstruiert, mit eigenen Aufnahmen | „Ausgewählt“ und „angegriffen“ sind getrennte Zustände, mit Grenzfällen für Zielwechsel und Doppelklick. |
| [QA-04](bug-reports/04-remote-player-display.md) | Darstellung anderer Spieler | Rekonstruiert, mit eigenen Aufnahmen | Mit zwei Clients geprüft: Animationen anderer Spieler wurden nicht übertragen. Aufnahmen vor und nach der Korrektur. |
| [QA-01](bug-reports/01-visual-quality-review.md) | Visuelle Qualitätsprüfung der Charakterbasis | **Original belegter Qualitätsbefund** | Sichtbarer Formfehler trotz positiver KI-Bewertung. Die Bewertung wurde zurückgenommen, die Freigabe gestoppt. |
| [QA-05](bug-reports/05-run-animation-root-motion.md) | Laufanimation: Figur springt zurück | **Original belegter Qualitätsbefund** | Selbst gefunden und selbst behoben; Aufnahmen vorher und 16 Minuten später. |

## 5. Manuelle Testfälle

| Datei | Inhalt |
|---|---|
| [Combat](test-cases/combat-test-cases.md) | Zielauswahl, Doppelklick, Auto-Attack, Reichweite, Escape, schnelle Eingaben |
| [Movement](test-cases/movement-test-cases.md) | WASD, Klick-zu-Bewegen, Unterbrechungen, Sprung |
| [Animation](test-cases/animation-test-cases.md) | Idle/Run/Attack, Übergänge, Rotation, andere Spieler, Sichtprüfung des Modells |

**Stand 23.10.2026:** 27 von 30 Testfällen **PASS**.
- **1 FAIL:** CB-14, das schnelle Sammeln von Gegnern funktioniert erst teilweise.
- **2 BLOCKED:** Der Test unter Netzwerkverzögerung ist noch nicht vorbereitet. Die Sichtprüfung des Charaktermodells wartet, bis die Modellbasis ausgetauscht ist.

## 6. Testprozess

Idee beschreiben → KI setzt um → im Spiel testen → Auffälligkeit eingrenzen und beschreiben → KI korrigiert → erneut testen → bewerten.

Der Ablauf ist in der Praxis entstanden und noch kein vollständiger professioneller QA-Prozess. Was ich bereits anwende und was ich ergänzen will: [Manueller Testablauf](test-process/manual-testing-workflow.md).

## 7. Technologien und KI-Unterstützung

| Bereich | Eingesetzt |
|---|---|
| Engine / Client | Godot 4.x mit C# |
| Server und gemeinsame Spiellogik | .NET 8 |
| Architektur | Autoritativer Server, Client mit Bewegungsvorhersage |
| Versionsverwaltung | Git, Pull Requests |
| KI-Werkzeuge | Claude Code, OpenAI Codex; ChatGPT für Schritt-für-Schritt-Anleitungen |
| 3D | Blender (durch KI-Agenten bedient) |

Den Großteil des Programmcodes und die automatisierten Tests haben Claude Code und Codex geschrieben, nicht ich. Mein Beitrag liegt darin, das gewünschte Verhalten festzulegen, die Ergebnisse im Spiel zu prüfen und zu entscheiden, ob eine Korrektur ausreicht. Seit Oktober 2026 lasse ich KI-Ergebnisse zusätzlich von getrennten KI-Prüfern bewerten, die Fehler melden, aber nicht selbst reparieren. Selbst umgesetzt habe ich zum Beispiel das Einbinden der Animationen in Godot ([QA-05](bug-reports/05-run-animation-root-motion.md)).

Ausführlich: [KI-gestützte Entwicklung](test-process/ai-assisted-development.md)

## 8. Projektstatus

Die Kernmechaniken sind vorhanden und manuell getestet. Einige automatisierte Server- und Klassentests des Projekts waren im Oktober 2026 weiterhin fehlerhaft. Die neue Charakterbasis ist noch nicht abgenommen.

Details mit Datum und Zuständigkeit: [PROJECT_STATUS.md](PROJECT_STATUS.md)

## 9.Grenzen

**Grenzen dieses Portfolios**

- Meine frühen Tests aus August und September 2026 sind nicht schriftlich protokolliert. Belegt sind sie über die Projekthistorie, meine Aufnahmen und meine eigene Angabe; die Fallstudien kennzeichnen das jeweils.
- Mehrspielertests habe ich mit zwei Clients auf einem Rechner durchgeführt, nicht mit mehreren echten Spielern.

## Datenschutz

Das MMORPG-Repository ist privat. Dieses Portfolio enthält keinen Quellcode, keine Zugangsdaten und keine internen Infrastrukturangaben. Die Bilder stammen aus dem Projekt; ihre Herkunft steht in der [Medienübersicht](media/README.md).
