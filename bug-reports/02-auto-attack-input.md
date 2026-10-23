# QA-02 – Auto-Attack: Reaktion bei schnellen Zielwechseln

> **Dokumenttyp: Historisch rekonstruierte Fallstudie**
> Das beobachtete Problem und die Spielsituation dahinter sind meine eigene Schilderung aus der Erinnerung. Ein Testprotokoll aus dieser Zeit existiert nicht. Die Änderungen am Verhalten sind in der Projekthistorie belegt (28.08.–11.09.2026). Die Reproduktionsschritte sind aus meiner Schilderung und den Änderungen abgeleitet.

| Feld | Inhalt |
|---|---|
| Case-ID | QA-02 |
| Zeitraum | 28.08.2026 – 11.09.2026 |
| Betroffene Funktion | Auto-Attack (Doppelklick auf Gegner, automatisches Heranlaufen, automatische Nahkampfschläge) |
| Technische Voraussetzungen | Client mit mehreren Testgegnern (Trainingspuppen); Server lokal oder Offline-Testszene |
| Getestete Version | Nicht protokolliert. Die Änderungen sind auf den 28.08., 30.08. und 11.09.2026 datiert. |
| Schweregrad (eigene Einschätzung) | Hoch für das geplante Spielprinzip: Der übliche Ablauf zum Sammeln vieler Gegner wäre nicht spielbar gewesen |
| Häufigkeit | Nicht gezählt; laut meiner Erinnerung bei schnellen Zielwechseln regelmäßig |
| Persönliche Beteiligung | Anforderung formuliert, im Spiel getestet, Problem beschrieben, KI-Korrekturen veranlasst, erneut getestet. Aufwand laut meiner groben Schätzung etwa ein Tag. |
| Aktueller Status | Das Grundproblem war laut meiner Erinnerung kurz nach der ersten Umsetzung behoben. Stand 23.10.2026: Doppelklick, Annäherung und Unterbrechung bestehen (CB-02 bis CB-10: PASS). Der vollständige Ablauf zum Gegnersammeln (CB-14) ist noch **FAIL**: Er funktioniert nur teilweise und wird weiter überarbeitet. |

## Hintergrund: Warum das wichtig ist

Das Kampfsystem soll sich an Fly For Fun (FlyFF) orientieren. Dort ist ein typischer Ablauf, viele Gegner zu sammeln und dann mit einem Flächenangriff (AoE) gleichzeitig zu treffen:

1. Gegner doppelt anklicken → die Figur läuft hin und schlägt einmal zu.
2. Wegklicken auf den Boden → die Figur läuft los.
3. Nächsten Gegner doppelt anklicken → einmal zuschlagen.
4. Wiederholen, bis genug Gegner folgen, dann Flächenangriff.

Dieser Ablauf lebt von **schnellen, sofort umgesetzten Klicks**. Reagiert das Spiel verzögert oder gar nicht, funktioniert das Spielprinzip nicht.

## Gewünschtes Verhalten

Meine Vorgabe war, das Auto-Attack-Verhalten aus FlyFF nachzubauen. Ein Doppelklick auf einen Gegner soll die Figur zum Gegner laufen und angreifen lassen. In den Projektanforderungen ist das so festgehalten:

- Ein **Doppelklick** auf einen Gegner startet Auto-Attack.
- Ist der Gegner außer Reichweite, läuft die Figur **automatisch heran** und greift dann an.
- **Bodenklick** beendet den Kampf; die Figur läuft zum Punkt.
- **WASD** bricht das Heranlaufen und die Angriffsdarstellung ab, **das Ziel bleibt erhalten**.

## Meine Beobachtung

| | |
|---|---|
| Erwartet | Jeder Doppelklick auf einen neuen Gegner wird sofort umgesetzt, auch wenn man schnell von einem Gegner zum nächsten wechselt. |
| Beobachtet (aus der Erinnerung) | Die Reaktion war ungenau und eher zu langsam. Beim schnellen Klicken von einem Monster zum nächsten kam teilweise **gar keine Reaktion** im Spiel. |
| Bedingung | Vor allem bei schnellen Zielwechseln, also genau in der Situation zum Sammeln von Gegnern |
| Zeitpunkt | Gleich bei der ersten Umsetzung von Auto-Attack im frühen Prototyp (Ende August 2026) |

## Reproduktion (rekonstruiert)

1. Drei Trainingspuppen A, B, C mit je etwa 5 m Abstand aufstellen.
2. Auf A doppelklicken, den ersten Schlag abwarten.
3. Auf den Boden klicken.
4. Sofort auf B doppelklicken, den ersten Schlag abwarten.
5. Schritte 3–4 mit C wiederholen.
6. Das Ganze möglichst schnell wiederholen.

Als ausführbarer Testfall: [CB-14](../test-cases/combat-test-cases.md#cb-14--gegner-sammeln-schnelle-zielwechsel).

## Was technisch geändert wurde

Das Problem trat laut meiner Erinnerung im frühen Prototyp auf und war schnell behoben. In diesen Zeitraum fallen die Änderungen vom 28.08.2026. Welche einzelne Änderung mein Symptom behoben hat, ist nicht belegt.

**28.08.2026 – erster Prototyp (Zeitraum meiner Beobachtung)**

- Erneutes Anklicken des aktiven Ziels stoppte Auto-Attack. Danach wird nur noch beim Wechsel auf ein anderes Ziel gestoppt.
- Ein wartender Skill blieb nach einem neuen Angriff bestehen. Danach verwirft ein neuer Angriff den wartenden Skill.

**11.09.2026 – spätere Verfeinerung von Klick und Spielgefühl** (nicht als Behebung meines ursprünglichen Symptoms belegt)

| Bereich | Vorher | Nachher |
|---|---|---|
| Doppelklick-Erkennung | Allgemeine Doppelklick-Erkennung der Engine, unabhängig davon, was angeklickt wurde | Zwei Klicks auf **dieselbe** Einheit innerhalb von 600 ms. Ein Klick auf Boden oder ein anderes Objekt setzt die Folge zurück. |
| Doppelklick während WASD | Angriff startete immer mit automatischem Heranlaufen | Kampfziel wird auch während WASD gesetzt; Heranlaufen startet nur ohne manuelle Bewegung. |
| Erneuter Angriff auf dasselbe Ziel | Laufender Schlag wurde zurückgesetzt | Laufender Schlag läuft weiter. |
| Gedrückt gehaltenes WASD | Angriffsdarstellung wurde in jedem Frame zurückgesetzt | Abbruch nur im ersten Frame der Bewegung; danach pausiert der Angriffszyklus. |

## Ergebnisse späterer Prüfungen

- Laut meiner Erinnerung habe ich nach den Korrekturen erneut getestet, bis das Verhalten vernünftig lief. Version, Datum und Einzelergebnisse sind nicht protokolliert.
- Der Teamtest vom 07.09.2026 (Projektpartner) liegt **vor** der Änderung vom 11.09. und sagt über deren Ergebnis nichts aus.
- Stand 23.10.2026, meine Testfälle: CB-02 bis CB-10 PASS, CB-14 FAIL (siehe [Combat-Testfälle](../test-cases/combat-test-cases.md)).

## Grenzen der Nachweisbarkeit

- Beobachtung und Nachtest beruhen auf meiner Erinnerung, nicht auf einem Protokoll.
- Den Zeitpunkt (früher Prototyp, Ende August) kenne ich aus der Erinnerung; ein Datum der Beobachtung ist nicht protokolliert.
- Die Implementierung erfolgte durch KI.
- Ein automatisierter Server-Test zum Angriffsrhythmus (zwei Schadenspakete statt eines bzw. ein zu früher Angriff) war bei Prüfungen am 12. und 13.10.2026 weiterhin fehlerhaft. Er betrifft die Serverseite, nicht die Klickerkennung, zeigt aber: Eine vollständig fehlerfreie Angriffstaktung ist **nicht** belegt.

## Nächster sinnvoller Schritt

Das Fehlerbild von CB-14 genauer eingrenzen (bei welchem Schritt, wie oft) und als eigenen Bugreport erfassen. Dafür lohnt sich eine kurze Bildschirmaufnahme, weil sich Verzögerungen im Video besser zeigen lassen als im Text.
