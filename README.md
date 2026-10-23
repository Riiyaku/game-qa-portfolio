# Game QA & Gameplay Testing Portfolio

Manuelle Gameplay-Tests, Bugreports und QA-Fallstudien aus einem privaten MMORPG-Prototyp.

## Auf einen Blick

| Frage | Antwort |
|---|---|
| Was ist das Projekt? | Ein privater MMORPG-Prototyp (Godot, C#/.NET, Client-Server-Architektur), den ich mit einem langjährigen Freund als Projektpartner entwickle. |
| Was habe ich gemacht? | Gameplay-Ideen und gewünschtes Verhalten beschrieben, Funktionen im Spiel manuell geprüft, Auffälligkeiten gemeldet, Korrekturen veranlasst und erneut geprüft, Charaktermodell und Animationen visuell bewertet. |
| Was hat die KI gemacht? | Den überwiegenden Teil des Programmcodes und der automatisierten Tests haben Claude Code und OpenAI Codex umgesetzt. Ich habe weder den Großteil des Codes noch automatisierte Tests selbst geschrieben. |
| Was ist belegt? | Ein visueller Qualitätsbefund mit dokumentierter Rücknahme einer positiven KI-Bewertung (siehe [Fallstudie 01](bug-reports/01-visual-quality-review.md)). Weitere Fälle sind aus der Projekthistorie rekonstruiert und als solche gekennzeichnet. 30 manuelle Testfälle mit aktuellem Status: 27 PASS, 1 FAIL, 2 BLOCKED. |
| Wo sind Beispiele? | [Bugreports und Fallstudien](#ausgewählte-qa-fallstudien) und [manuelle Testfälle](#manuelle-testfälle) |

## Kurze Vorstellung

Ich komme aus dem Marketing und orientiere mich in Richtung Softwarequalität und Game QA. Ich bin weder ausgebildeter Softwaretester noch eigenständig arbeitender C#-Entwickler. Dieses Portfolio zeigt, wie ich in einem eigenen Projekt Spielverhalten prüfe, Fehler beschreibe und Korrekturen begleite – nicht, dass ich ein MMORPG programmiert habe.

## Über das MMORPG-Projekt

Ein kleiner MMORPG-Prototyp nach dem Vorbild von Fly For Fun (FlyFF). Mein Projektpartner und ich haben dieses ältere MMORPG lange zusammen mit Freunden gespielt. Wir kennen uns seit der Grundschule. Unser Ziel ist ein Spiel mit ähnlichem Spielgefühl, bei dem einige Dinge besser gelöst sind.

Der Server ist autoritativ und verwaltet den gesamten Spielzustand; der Client stellt dar und sendet Eingaben.

Für die Tests in diesem Portfolio relevant:

- Bewegung mit WASD relativ zur Kamera und Klick-zu-Bewegen
- Zielauswahl per Klick, Kampfaufnahme per Doppelklick, automatisches Annähern an das Ziel
- Auto-Attack mit zeitlich getakteten Schlägen
- Idle-, Lauf- und Angriffsanimationen, auch für andere Spieler
- Eine eigene Charakterbasis, die sich noch in Arbeit befindet (bisher wird eine Platzhalterfigur verwendet)

Das Projekt ist ein Prototyp, kein veröffentlichtes Spiel. Der Quellcode bleibt privat.

## Technischer Kontext

| Bereich | Eingesetzt |
|---|---|
| Engine / Client | Godot 4.x mit C# |
| Server und gemeinsame Spiellogik | .NET 8 |
| Architektur | Autoritativer Server, Client mit Bewegungsvorhersage |
| Versionsverwaltung | Git, Pull Requests |
| KI-Werkzeuge | Claude Code, OpenAI Codex |
| 3D | Blender (durch KI-Agenten bedient) |

## Meine persönliche Rolle

**Arbeitsteilung im Team**

| Ich (Client-Gameplay, Prüfung) | Projektpartner (Technik) |
|---|---|
| Gameplay-Ideen und gewünschte Mechaniken | Server und gemeinsame Spiellogik |
| Anforderungen für KI-Implementierungen formulieren | Authentifizierung, Netzwerk |
| Manuelle Prüfung im Spiel, Fehler beschreiben | Persistenz, Infrastruktur |
| Korrekturen veranlassen und erneut prüfen | |
| Bedienbarkeit, Spielgefühl, visuelle Qualität | |

**Was ich laut eigener Angabe getestet habe:** Spielerbewegung, Auto-Attack, Targeting und Animationen, auch die Darstellung anderer Spieler mit zwei gleichzeitig gestarteten Clients. Für diese Tests existieren keine personenbezogenen Testprotokolle aus der damaligen Zeit. Die passenden Änderungen sind in der Projekthistorie nachvollziehbar; die Testabläufe in diesem Portfolio sind daraus rekonstruiert und entsprechend gekennzeichnet.

**Was nicht von mir stammt:** Die im Projekt dokumentierten manuellen Tests vom 07.09.2026 (Kamera, Targeting, Benutzeroberfläche) hat mein Projektpartner durchgeführt.

## Zusammenarbeit mit KI-Tools

Die Implementierung erfolgte überwiegend durch Claude Code und Codex. Meine Aufgabe war, das gewünschte Verhalten so genau zu beschreiben, dass es umgesetzt werden konnte, und danach im Spiel zu prüfen, ob es tatsächlich so funktioniert. Ab Oktober 2026 habe ich außerdem verlangt, dass KI-Prüfer Ergebnisse anhand tatsächlicher Bilder und Abläufe bewerten und Fehler melden, statt sie selbst zu reparieren.

Ausführlich: [KI-gestützte Entwicklung](test-process/ai-assisted-development.md)

## Manueller Testprozess

Mein Ablauf: Idee beschreiben → KI setzt um → im Spiel testen → Auffälligkeit eingrenzen und beschreiben → KI korrigiert → erneut testen → bewerten.

Das ist ein informeller Entwicklungs- und Testprozess, kein vollständiger professioneller QA-Prozess. Was mir dazu noch fehlt, steht ebenfalls dort: [Manueller Testablauf](test-process/manual-testing-workflow.md)

## Ausgewählte QA-Fallstudien

Jedes Dokument nennt seinen Typ am Anfang:

- **Original belegter Qualitätsbefund** – meine Meldung ist im Projekt dokumentiert.
- **Historisch rekonstruierte Fallstudie** – die Änderung ist belegt, meine damaligen Testschritte nicht vollständig.

| Nr. | Thema | Typ | Kern |
|---|---|---|---|
| [01](bug-reports/01-visual-quality-review.md) | Zehenform und Fußstellung der Charakterbasis | Original belegter Qualitätsbefund | Meine Beanstandung führte zur Rücknahme einer positiven KI-Bewertung und zum Stopp der Weiterarbeit. Mit Bildvergleich Vorlage ↔ Modell. |
| [02](bug-reports/02-auto-attack-input.md) | Auto-Attack bei schnellen Zielwechseln | Historisch rekonstruierte Fallstudie | Beim schnellen Wechsel zwischen Gegnern kam teilweise keine Reaktion. Das hätte das Sammeln von Gegnern für Flächenangriffe verhindert. |
| [03](bug-reports/03-targeting-behavior.md) | Targeting: Auswahl und Kampfziel | Historisch rekonstruierte Fallstudie | Trennung von „ausgewählt“ und „angegriffen“, Zielwechsel |
| [04](bug-reports/04-remote-player-display.md) | Darstellung anderer Spieler | Historisch rekonstruierte Fallstudie | Mit zwei Clients geprüft: Drehung und Laufanimation anderer Spieler fehlten |

## Manuelle Testfälle

| Datei | Inhalt |
|---|---|
| [Combat](test-cases/combat-test-cases.md) | Zielauswahl, Doppelklick, Auto-Attack, Reichweite, Escape, schnelle Eingaben |
| [Movement](test-cases/movement-test-cases.md) | WASD, Klick-zu-Bewegen, Unterbrechung des automatischen Annäherns |
| [Animation](test-cases/animation-test-cases.md) | Idle/Run/Attack, Übergänge, Rotation, andere Spieler, Sichtprüfung des Modells |

**Stand 23.10.2026:** 27 von 30 Testfällen **PASS**. **1 FAIL:** CB-14, das schnelle Sammeln von Gegnern funktioniert erst teilweise und wird weiter überarbeitet. **2 BLOCKED:** Test unter Netzwerkverzögerung noch nicht möglich; Sichtprüfung des Charaktermodells, weil die Modellbasis gerade ausgetauscht wird.

## Projektstatus

Was im Projekt vorhanden, was geprüft und was offen ist – und von wem und wann geprüft: [PROJECT_STATUS.md](PROJECT_STATUS.md)

Kurz: Die Kernmechaniken sind vorhanden. Einige automatisierte Server- und Klassentests waren im Oktober 2026 weiterhin fehlerhaft. Die neue Charakterbasis wartet auf die menschliche Abnahme.

## Fähigkeiten und Lernfelder

**Praktisch angewendet**

- Spielverhalten aus Spielersicht prüfen und Abweichungen beschreiben
- Erwartetes Verhalten vorab formulieren (Anforderungen mit Akzeptanzkriterien)
- Visuelle Fehler erkennen, auch gegen eine bereits positive automatische Bewertung
- Nach einer Korrektur erneut prüfen
- Mehrspieler-Darstellung mit zwei lokal gestarteten Clients prüfen
- Mit Git-basiertem Projektablauf und KI-Entwicklungswerkzeugen arbeiten

**Noch nicht nachgewiesen bzw. Lernziele**

- Strukturierte, versionierte Testprotokolle von Anfang an führen
- Testmanagement- und Bugtracking-Werkzeuge (z. B. Jira, TestRail)
- Regressionstests planen und dokumentieren
- Testkoordination mit mehreren Spielern
- Linux-Grundlagen, Testumgebungen, Netzwerkbedingungen (Latenz, Paketverlust) gezielt testen
- Eigene automatisierte Tests schreiben

## Datenschutz und privater Quellcode

Das MMORPG-Repository ist privat und wird nicht veröffentlicht. Dieses Portfolio enthält keinen Quellcode, keine Zugangsdaten und keine internen Infrastrukturangaben. Fehlerbeschreibungen und Abläufe sind in eigenen Worten zusammengefasst. Die enthaltenen Bilder stammen aus dem Projekt; ihre Herkunft ist in der [Medienübersicht](media/README.md) angegeben.
