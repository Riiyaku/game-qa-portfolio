# QA-04 – Darstellung anderer Spieler: Drehung und Laufanimation

> **Dokumenttyp: Historisch rekonstruierte Fallstudie**
> Beobachtung, Testaufbau und Nachtest sind meine eigene Schilderung aus der Erinnerung. Ein Testprotokoll existiert nicht. Die Korrektur ist in der Projekthistorie belegt (10.09.2026).

| Feld | Inhalt |
|---|---|
| Case-ID | QA-04 |
| Zeitraum | bis 10.09.2026 (genaue Testtage nicht protokolliert) |
| Betroffene Funktion | Darstellung anderer Spieler im Mehrspielerbetrieb: Blickrichtung, Lauf- und Idle-Animation, später Angriffe; außerdem der Sprung |
| Technische Voraussetzungen | Lokaler Server, zwei Clients auf demselben Rechner, zwei Spielfiguren |
| Getestete Version | Nicht protokolliert |
| Schweregrad (eigene Einschätzung) | Hoch für ein MMORPG: Andere Spieler sind ständig sichtbar |
| Häufigkeit | Vor der Korrektur nach meiner Erinnerung immer |
| Persönliche Beteiligung | Testaufbau mit zwei Clients, Beobachtung, Beschreibung, Korrektur per KI veranlasst, erneut geprüft |
| Aktueller Status | Korrektur umgesetzt. Kein protokollierter Nachtest |

## Testaufbau

Ich habe den Server lokal gestartet und den Client zweimal gestartet. So war ich mit zwei Figuren gleichzeitig im Spiel und konnte im einen Fenster beobachten, was die Figur im anderen Fenster tut. Für diese Prüfung brauchte ich keinen zweiten Tester.

## Reproduktion

1. Lokalen Server starten.
2. Client 1 und Client 2 starten, jeweils mit einer eigenen Figur einloggen.
3. Beide Figuren in Sichtweite bringen.
4. In Client 2 die Figur drehen, laufen und stehen bleiben lassen.
5. In Client 1 beobachten.

## Erwartetes Ergebnis

Client 1 zeigt die Figur aus Client 2 mit derselben Blickrichtung, mit Laufanimation während der Bewegung und Idle im Stand.

## Beobachtetes Ergebnis (aus der Erinnerung)

| Nr. | Beobachtung |
|---|---|
| 1 | Drehte ein Spieler seine Figur, sah der andere Spieler die Drehung **nicht**. |
| 2 | Andere Spieler bewegten sich **ohne Laufanimation**. |
| 3 | Der **Sprung** war im Code bereits eingebaut, funktionierte im Spiel aber zunächst nicht. |

## Korrektur

Die Änderung vom 10.09.2026 ändert, wie andere Spieler dargestellt werden. Laufen bzw. Stehen und die Blickrichtung werden jetzt aus der tatsächlich angezeigten Bewegung der Figur bestimmt. Bei langsamer Bewegung bleibt die letzte Blickrichtung erhalten, ein Sprung löst keine Laufanimation aus. Die Implementierung erfolgte durch KI.

Am selben Tag wurde auch der Sprung eingecheckt, mit automatisierten Tests (unter anderem: kein zweiter Sprung in der Luft). Laut meiner Erinnerung wurden Sprung, Drehung und Laufanimation anderer Spieler in einem gemeinsamen Durchgang korrigiert und anschließend zusammen geprüft.

## Ergebnisse späterer Prüfungen

- Laut meiner Erinnerung habe ich danach mit denselben zwei Clients erneut geprüft und anschließend weitere Abläufe getestet: Angriffsanimationen und gemeinsames Angreifen von Monstern. Version, Datum und Einzelergebnisse sind nicht protokolliert.
- Im Projekt gibt es außerdem eine automatisierte Prüfung für Angriffsanimationen anderer Spieler (nicht von mir).

## Beteiligung anderer

- Anfängliche Verbindungsprobleme zum Server hat mein Projektpartner behoben.
- Die fehlende Laufanimation haben wir nach meiner Erinnerung gemeinsam beheben lassen. Die Prüfung mit zwei Clients habe ich allein durchgeführt.

## Grenzen der Nachweisbarkeit

- Beobachtung, Ablauf und Nachtest beruhen auf meiner Erinnerung.
- Ob Drehung und Laufanimation nacheinander oder gemeinsam korrigiert wurden, lässt sich nicht trennen; belegt ist eine gemeinsame Änderung vom 10.09.2026.
- Verhalten unter Netzwerkverzögerung oder Paketverlust ist nicht geprüft. Das ist auch in den Projektanforderungen noch offen.

Als ausführbare Testfälle: [AN-06 und AN-07](../test-cases/animation-test-cases.md).
