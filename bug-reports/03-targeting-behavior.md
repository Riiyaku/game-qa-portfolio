# QA-03 – Targeting: Auswahl, Kampfziel und Zielwechsel

> **Dokumenttyp: Historisch rekonstruierte Fallstudie**
> Die Mechanik und ihre Änderungen sind in der Projekthistorie belegt (27.08.–12.09.2026). Meine eigenen Targeting-Tests sind eine persönliche Angabe ohne damaliges Protokoll. Der dokumentierte manuelle Test vom 07.09.2026 stammt von meinem Projektpartner, nicht von mir.

| Feld | Inhalt |
|---|---|
| Case-ID | QA-03 |
| Zeitraum | 27.08.2026 – 12.09.2026 |
| Betroffene Funktion | Zielauswahl, aktives Kampfziel, Zielmarkierungen |
| Technische Voraussetzungen | Client mit mindestens zwei Gegnern; für Spielerziele ein zweiter Client |
| Getestete Version | Nicht protokolliert. Die Änderungen sind auf den 28.08., 11.09. und 12.09.2026 datiert. |
| Schweregrad / Häufigkeit | Nicht bewertet bzw. nicht bekannt – keine Originalmeldung vorhanden |
| Persönliche Beteiligung | Laut Eigenangabe: Targeting im Spiel getestet, Anpassungen per KI veranlasst |
| Aktueller Status | Mechanik umgesetzt. Stand 23.10.2026: CB-01, CB-02, CB-04, CB-09, CB-10, CB-13 PASS. |

## Das Problem: „ausgewählt“ ist nicht „angegriffen“

In MMORPGs dieser Art muss man einen Gegner ansehen (Name, Lebenspunkte), ohne ihn anzugreifen, und während eines Kampfes einen anderen Gegner auswählen können, ohne den Kampf abzubrechen. Im ersten Prototyp gab es dafür nur ein gemeinsames Ziel.

**Änderung (28.08.2026):** Getrennte Zustände für *ausgewähltes Ziel* und *Angriffsziel*.

## Gewünschtes Verhalten laut Anforderungen

| Aktion | Erwartet |
|---|---|
| Einfacher Klick auf Gegner | Gegner wird ausgewählt, **kein** Angriff |
| Doppelklick auf Gegner | Gegner wird zum Angriffsziel |
| Klick auf anderen Gegner während eines Kampfes | Auswahl wechselt, **Kampf läuft gegen das alte Ziel weiter** |
| Markierung | Nur ausgewählt: grauer Ring. Angriffsziel: roter Ring |
| Klick auf Boden | Kampf wird beendet, Auswahl bleibt, Figur läuft zum Punkt |
| Escape | Kampf, Bewegung und Skill-Absicht werden abgebrochen, danach die Auswahl gelöscht |
| Tod/Verschwinden des Ziels | Beide Markierungen verschwinden |
| Klick auf anderen Spieler (ab 12.09.2026) | Auswahl wie bei einem Gegner, aber **niemals** Angriff |

## Rekonstruierte Grenzfälle

Diese Abläufe ergeben sich aus den Änderungen am 11.09.2026. Ob ich sie damals genau so ausgeführt habe, ist nicht belegt.

| Nr. | Ablauf | Risiko |
|---|---|---|
| 1 | Gegner A klicken, sofort Gegner B klicken | Darf **kein** Doppelklick auf B sein (zwei Klicks auf verschiedene Einheiten) |
| 2 | Gegner A klicken, Boden klicken, Gegner A klicken | Darf **kein** Doppelklick sein, die Folge wird durch den Bodenklick zurückgesetzt |
| 3 | Während des Laufens mit WASD auf einen Gegner doppelklicken | Ziel muss trotzdem zum Angriffsziel werden |
| 4 | Kampf gegen A, dann B auswählen | Roter Ring bleibt bei A, grauer Ring bei B |

Als ausführbare Testfälle: CB-01, CB-02, CB-04, CB-09, CB-10 in [combat-test-cases.md](../test-cases/combat-test-cases.md).

## Ergebnisse späterer Prüfungen

| Datum | Wer | Was | Aussagekraft heute |
|---|---|---|---|
| 07.09.2026 | Projektpartner | Manuelle Prüfung von Auswahl/Engagement, Ringen und Escape als bestanden dokumentiert | Vor den Änderungen vom 11. und 12.09.; nicht als aktueller Status verwendbar |
| 11.09.2026 | nicht zuordenbar | Automatisierte Testläufe der Klassen laut Anforderungsdokument weiterhin bestanden, nach der Umstellung der Markierungen | Prüft Abläufe automatisch, nicht das Aussehen; das Aussehen ist als offen vermerkt |
| Stand 23.10.2026 | ich | Testfälle CB-01, CB-02, CB-04, CB-09, CB-10, CB-13 | PASS |

## Grenzen der Nachweisbarkeit

- Die Erweiterungen vom 11. und 12.09.2026 (Bodenringe als Projektion, Dreieck über dem Ziel, Escape-Reihenfolge, nicht angreifbare Spieler) hat nach meiner Angabe überwiegend mein Projektpartner veranlasst. Er hat die Varianten mit einem KI-Werkzeug abgewogen und direkt umsetzen lassen. Die Grundfunktionen, etwa die Ringe, gab es vorher schon. In den Anforderungen steht dazu nur „auf Wunsch des Nutzers“.
- Die Implementierung erfolgte durch KI.
- Ob die Grenzfälle oben schon im August/September genau so getestet wurden, ist nicht belegt; ihr aktueller Status steht in den Testfällen.
