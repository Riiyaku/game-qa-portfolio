# Projektstatus

Stand der Auswertung: **23.10.2026**. Grundlage ist die Projektdokumentation und Versionshistorie. Für diese Übersicht wurden keine Tests ausgeführt.

## Legende

| Kürzel | Bedeutung |
|---|---|
| **Vorhanden** | Funktion ist im aktuellen Projektstand umgesetzt |
| **Historisch** | Umsetzung ist mit Datum in der Versionshistorie dokumentiert |
| **Eigenangabe** | Von mir manuell geprüft laut eigener Angabe, ohne damaliges Protokoll |
| **Protokolliert** | Mit persönlichem Testnachweis belegt |
| **Automatisch** | Automatisierte Tests vorhanden (nicht von mir geschrieben) |
| **Team** | Nur von meinem Projektpartner manuell getestet |
| **Offen** | Unvollständig, fehlerhaft oder Abnahme ausstehend |
| **–** | Nicht nachgewiesen |

## Gameplay

| Funktion | Vorhanden | Historisch | Eigenangabe | Protokolliert | Automatisch | Team (manuell) | Offen |
|---|---|---|---|---|---|---|---|
| WASD-Bewegung relativ zur Kamera | ja | 27.08.2026 | ja | – | ja | – | Sichtprüfung unter Netzwerkverzögerung |
| Klick-zu-Bewegen | ja | 30.08.2026 | – | – | – | 07.09.2026 | – |
| Automatisches Annähern an Gegner | ja | 28.08., 30.08.2026 | ja | – | – | – | Aktueller manueller Test |
| Unterbrechung durch WASD | ja | 30.08., 11.09.2026 | ja | – | – | – | Aktueller manueller Test |
| Auswahl vs. Kampfziel | ja | 28.08.2026 | ja | – | ja | 07.09.2026 | Test nach Änderungen vom 11./12.09. |
| Doppelklick-Erkennung pro Ziel | ja | 11.09.2026 | ja | – | – | – | Aktueller manueller Test |
| Auto-Attack-Rhythmus | ja | 28.08., 30.08., 11.09.2026 | ja | – | ja | – | Server-Kampftest im Oktober weiterhin fehlerhaft |
| Escape bricht Kampf ab | ja | 30.08., 11.09.2026 | – | – | – | 07.09.2026 | Test nach Änderung vom 11.09. |
| Spieler auswählbar, nicht angreifbar | ja | 12.09.2026 | – | – | – | – | Manueller Test mit zwei Clients |
| Sprung | ja | 10.09.2026 | ja, zusammen mit [QA-04](bug-reports/04-remote-player-display.md) | – | ja | – | Aktueller Sichttest |
| Idle/Run/Attack lokal | ja | 30.08.2026 | ja | – | – | – | Aktueller Sichttest |
| Drehung und Laufanimation anderer Spieler | ja | 10.09.2026 | ja, mit zwei Clients ([QA-04](bug-reports/04-remote-player-display.md)) | – | ja | – | Aktueller Test; Test unter Netzwerkverzögerung |
| Angriffe anderer Spieler, gemeinsames Angreifen | ja | – | ja, mit zwei Clients | – | ja | – | Aktueller Test |

Für Auto-Attack und für das Laufen habe ich nach eigener grober Schätzung jeweils etwa einen Tag mit Testen und Nachbessern verbracht. Beim Laufen habe ich dabei auch die Platzhalterfigur samt Laufanimation einbauen lassen (30.08.2026).

„Automatisch: ja“ heißt nur, dass im Projekt automatisierte Tests oder Testläufe für den Bereich existieren – nicht, dass alle aktuell bestehen.

**Zeitliche Einordnung:** Die Teamtests vom 07.09.2026 liegen vor den Änderungen vom 10.–12.09.2026. Sie gelten deshalb nicht als aktueller Teststatus.

## Charakterbasis

| Schritt | Datum | Status |
|---|---|---|
| Vorgaben (glatt, gesichtslos, sichtbare Prüfung) | 13.10.2026 | Von mir formuliert |
| Zehenkorrektur rechts | 15.10.2026 | Nach meiner Beanstandung **blockiert** ([QA-01](bug-reports/01-visual-quality-review.md)) |
| Neuer Vorfuß-Ansatz | 15.–18.10.2026 | Blockiert |
| Gesamtüberarbeitung, Endkandidat | 18.–19.10.2026 | **Menschliche Abnahme offen** |

## Automatisierte Tests (Teamprojekt, nicht von mir)

| Bereich | Letzter dokumentierter Stand | Status |
|---|---|---|
| Server-Testsuite | 12.–13.10.2026: in vier Gesamtläufen jeweils ein bis zwei wechselnde Fehler, ein Angriffstest reproduzierbar fehlerhaft | Offen |
| Automatisierte Client-Klassentests | 12.–13.10.2026: zwei Klassen mit 4 bzw. 2 fehlgeschlagenen Prüfungen | Offen |
| Release-Export | 13.10.2026 fehlgeschlagen | Offen |

## Nicht nachgewiesen

- Eigene Programmierung des Gameplay-Codes
- Eigene automatisierte Tests
- Persönlich protokollierte Tests von Bewegung, Auto-Attack, Targeting oder Animation (die Tests selbst sind Eigenangabe)
- Tests mit mehreren echten Spielern gleichzeitig (meine Mehrspielertests liefen mit zwei Clients auf einem Rechner)
- Abschließende Abnahme der Charakterbasis
