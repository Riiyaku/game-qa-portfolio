# Projektstatus

Stand: **23.10.2026**. Grundlage sind die Projektdokumentation, die Versionshistorie und meine manuellen Testfälle.

## Legende

| Spalte | Bedeutung |
|---|---|
| **Vorhanden** | Funktion ist im aktuellen Projektstand umgesetzt |
| **Historisch** | Umsetzung ist mit Datum in der Versionshistorie dokumentiert |
| **Manuelle Testfälle** | Ergebnis meiner Testfälle, Stand 23.10.2026 |
| **Automatisch** | Automatisierte Tests vorhanden (nicht von mir geschrieben) |
| **Team (manuell)** | Zusätzlich von meinem Projektpartner manuell getestet |
| **Offen** | Unvollständig, fehlerhaft oder nicht testbar |

## Gameplay

| Funktion | Vorhanden | Historisch | Manuelle Testfälle | Automatisch | Team (manuell) | Offen |
|---|---|---|---|---|---|---|
| WASD-Bewegung relativ zur Kamera | ja | 27.08.2026 | MV-01, MV-02, MV-06: PASS | ja | – | Test unter Netzwerkverzögerung (MV-08: BLOCKED) |
| Klick-zu-Bewegen | ja | 30.08.2026 | MV-03, MV-04: PASS | – | 07.09.2026 | – |
| Automatisches Annähern an Gegner | ja | 28.08., 30.08.2026 | CB-03: PASS | – | – | – |
| Unterbrechung durch WASD | ja | 30.08., 11.09.2026 | CB-06, CB-07: PASS | – | – | – |
| Auswahl vs. Kampfziel | ja | 28.08.2026 | CB-01, CB-04, MV-05: PASS | ja | 07.09.2026 | – |
| Doppelklick-Erkennung pro Ziel | ja | 11.09.2026 | CB-02, CB-09, CB-10: PASS | – | – | – |
| Auto-Attack-Rhythmus | ja | 28.08., 30.08., 11.09.2026 | CB-05, CB-08, CB-12: PASS | ja | – | Server-Kampftest im Oktober weiterhin fehlerhaft |
| Gegner sammeln mit schnellen Zielwechseln | teilweise | – | CB-14: **FAIL** | – | – | Funktioniert nur teilweise, in Arbeit |
| Escape bricht Kampf ab | ja | 30.08., 11.09.2026 | CB-11: PASS | – | 07.09.2026 | – |
| Spieler auswählbar, nicht angreifbar | ja | 12.09.2026 | CB-13: PASS | – | – | – |
| Sprung | ja | 10.09.2026 | MV-07: PASS | ja | – | – |
| Idle/Run/Attack lokal | ja | 30.08.2026 | AN-01 bis AN-05: PASS | – | – | – |
| Drehung und Laufanimation anderer Spieler | ja | 10.09.2026 | AN-06: PASS ([QA-04](bug-reports/04-remote-player-display.md)) | ja | – | Test unter Netzwerkverzögerung |
| Angriffe anderer Spieler, gemeinsames Angreifen | ja | – | AN-07: PASS | ja | – | – |

Für Auto-Attack und für das Laufen habe ich nach eigener grober Schätzung jeweils etwa einen Tag mit Testen und Nachbessern verbracht. Beim Laufen habe ich die Platzhalterfigur und ihre Animationen am 29.08.2026 selbst in Godot eingebunden ([QA-05](bug-reports/05-run-animation-root-motion.md)); im Projektverlauf gespeichert wurde das am 30.08.2026.

„Automatisch: ja“ heißt nur, dass im Projekt automatisierte Tests oder Testläufe für den Bereich existieren – nicht, dass alle aktuell bestehen.

**Zeitliche Einordnung:** Die Teamtests vom 07.09.2026 liegen vor den Änderungen vom 10.–12.09.2026 und sind deshalb nur historisch relevant.

## Charakterbasis

| Schritt | Datum | Status |
|---|---|---|
| Vorgaben (glatt, gesichtslos, sichtbare Prüfung) | 13.10.2026 | Von mir formuliert |
| Zehenkorrektur rechts | 15.10.2026 | Nach meiner Beanstandung **blockiert** ([QA-01](bug-reports/01-visual-quality-review.md)) |
| Neuer Vorfuß-Ansatz | 15.–18.10.2026 | Blockiert |
| Gesamtüberarbeitung, Endkandidat | 18.–19.10.2026 | Menschliche Abnahme offen |
| Austausch der Modellbasis | laufend | Sichtprüfung AN-08: **BLOCKED** bis zum Abschluss |

## Automatisierte Tests (Teamprojekt, nicht von mir)

| Bereich | Letzter dokumentierter Stand | Status |
|---|---|---|
| Server-Testsuite | 12.–13.10.2026: in vier Gesamtläufen jeweils ein bis zwei wechselnde Fehler, ein Angriffstest reproduzierbar fehlerhaft | Offen |
| Automatisierte Client-Klassentests | 12.–13.10.2026: zwei Klassen mit 4 bzw. 2 fehlgeschlagenen Prüfungen | Offen |
| Release-Export | 13.10.2026 fehlgeschlagen | Offen |

## Nicht nachgewiesen

- Eigene Programmierung des Gameplay-Codes
- Eigene automatisierte Tests
- Tests mit mehreren echten Spielern gleichzeitig (meine Mehrspielertests liefen mit zwei Clients auf einem Rechner)
- Abschließende Abnahme der Charakterbasis
