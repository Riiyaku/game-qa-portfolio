# QA-01 – Zehenform und Fußstellung der neuen Charakterbasis

> **Dokumenttyp: Original belegter Qualitätsbefund**
> Meine Beanstandung und die Reaktion darauf sind in der Projektdokumentation vom 15.10.2026 festgehalten. Der genaue Wortlaut meiner Meldung ist dort nur zusammengefasst.

| Feld | Inhalt |
|---|---|
| Case-ID | QA-01 |
| Datum | 15.10.2026 (Folgeschritte bis 19.10.2026) |
| Betroffene Funktion | Neue männliche Charakterbasis (in Arbeit), rechter Fuß: Großzehe und zweite Zehe |
| Technische Voraussetzungen | Modellkandidat in Blender geöffnet, Testpose mit gebeugten Gelenken sowie Ruhepose; Import in Godot |
| Geprüfte Version | Modellkandidat vom 15.10.2026, im Projekt über eine Prüfsumme eindeutig identifiziert |
| Schweregrad (nachträgliche Einordnung) | Mittel – kein Absturz, aber ein sichtbarer Formfehler an der Grundfigur, auf der weitere Arbeit aufbauen sollte |
| Häufigkeit | Statischer Formfehler: in der Ruhepose und in der Testpose nachweisbar |
| Persönliche Beteiligung | Sichtprüfung, Beanstandung mit eigenen Bildschirmaufnahmen, Freigabe des Folgeschritts |
| Aktueller Status | Beanstandung angenommen, Weiterarbeit gestoppt. Behebung nicht abgeschlossen bzw. nicht von mir abgenommen |

## 1. Ursprüngliches Qualitätsziel

Gesucht war eine glatte, gesichtslose männliche Grundfigur im Stil der festgelegten Vorlage (Vorder-, Seiten- und Rückansicht). In diesem Arbeitsschritt sollten die beiden ersten Zehen des rechten Fußes an die bereits geprüfte linke Seite angepasst werden.

Abnahmekriterium im Arbeitsauftrag: *Die zwei rechten Zehen passen in Vorder-, Ober- und Seitenansicht zur Vorlage und zur linken Seite.*

## 2. Prüfung vor meiner Beanstandung

Die KI-Agenten hatten den Kandidaten umfangreich geprüft:

- Technisch: Geometrie, Texturkoordinaten und Gewichtung unverändert außerhalb des bearbeiteten Bereichs, 157 Posen ohne gemessene Durchdringung am Fuß, Import in Godot mit 19 bestandenen Prüfungen.
- Visuell: Ein KI-Prüfer für Charakterdarstellung bewertete Nahaufnahmen mit „begrenztes KEEP“ (Form beibehalten).
- Gesamturteil der KI-Prüfung: **PASS WITH NOTES**, Status „bereit zum Testen“, menschliche Abnahme offen.

## 3. Reproduktion

Rekonstruiert aus den dokumentierten Bildern; meine einzelnen Prüfschritte sind nicht protokolliert.

1. Kandidat in Blender öffnen (zum Zeitpunkt der Meldung stand die Szene auf einer Belastungs-Testpose).
2. Rechten Fuß in schräger Nahansicht betrachten.
3. Beide Füße in der Gesamtansicht betrachten.
4. Form der ersten beiden Zehen mit dem erwarteten Ergebnis vergleichen.

## 4. Erwartetes Ergebnis

Großzehe und zweite Zehe mit gewölbten Kuppen und weichem Übergang zum Vorfuß, passend zur Vorlage. Füße ohne auffällige Eindrehung.

## 5. Beobachtetes Ergebnis (meine Beanstandung)

- Die ersten beiden Zehen wirkten **stumpf** – auf den Bildern eher rechteckig bzw. zylindrisch als gewölbt.
- Der **Übergang zum Vorfuß** war abrupt.
- Die **Füße wirkten insgesamt eingedreht.**

Ich habe dazu eine schräge Nahaufnahme und eine Gesamtansicht der Füße als eigene Bildschirmaufnahmen vorgelegt.

## 6. Reaktion des Prüfsystems

- Der KI-Prüfer betrachtete beide Bilder erneut und **zog sein vorheriges „KEEP“ zurück**. Neues Urteil: **NO-GO** für die Übertragung auf die weiteren Zehen und für eine Formabnahme.
- Seine eigene Begründung: Breite und fehlende Risse waren zu stark gewichtet worden, die natürliche Form von Kuppe und Übergang zu wenig.
- Die technischen Prüfergebnisse blieben gültig, wurden aber ausdrücklich **nicht mehr als Nachweis guter Form** gewertet.
- Der Arbeitsauftrag wurde auf **blockiert** gesetzt, das Abnahmekriterium wieder geöffnet. An den restlichen sechs Zehen wurde nichts weiter verändert.

## 7. Ursachenklärung (durch KI, auf meine Meldung hin)

Eine anschließende Untersuchung verglich Ruhe- und Testpose mit identischer Kamera:

| Teil der Beanstandung | Ergebnis |
|---|---|
| Stumpfe Zehenform | **Bestätigt.** Der Formfehler bestand bereits in der Ruhepose, war also kein Problem der Animation oder Gewichtung. |
| Eingedrehte Füße | **Durch die Testpose erklärt.** In der geöffneten Szene waren die Oberschenkel für eine Belastungsprobe gegensinnig gedreht. Ein Fehler in den Zehen- oder Fußknochen wurde dafür nicht gefunden. |

Für mich war das eine wichtige Lehre: Eine Auffälligkeit kann aus dem Prüfaufbau stammen. Deshalb gehört zur Meldung, in welcher Pose und Szene etwas beobachtet wurde.

## 8. Weiterer Verlauf

| Datum | Schritt | Status laut Dokumentation |
|---|---|---|
| 15.10.2026 | Nach einem weiteren Bild von mir bestätigt: Zehen wirken auch in Ruhe kurz und dick. Ich gab einen neuen Ansatz frei (zusammenhängender Vorfuß statt einzeln aufgesetzter Zehen). | Erster Grobtest verworfen; Auftrag am 18.10. auf blockiert gesetzt |
| 18.–19.10.2026 | Neue Gesamtüberarbeitung der Figur, unter anderem am Fuß | Endkandidat liegt zur **menschlichen Sichtabnahme** vor; diese ist offen |

## 9. Grenzen der Nachweisbarkeit

- Eine **zurückgenommene Freigabe ist keine erfolgreiche Korrektur.** Dass die Zehenform inzwischen der Vorlage entspricht, ist nicht belegt.
- Die Analyse, Messungen und Modellarbeit stammen von KI-Agenten, nicht von mir. Mein Anteil sind die Sichtprüfung, die Beanstandung, die Bilder und die Freigabeentscheidung für den nächsten Schritt.
- Bilder werden hier nicht gezeigt, weil Herkunft und Rechte der Vorlage nicht abschließend geklärt sind.

## Was dieser Fall zeigt

Eine automatisierte bzw. KI-gestützte Prüfung kann technisch vollständig „grün“ sein und trotzdem ein sichtbar falsches Ergebnis freigeben. Die Sichtprüfung aus Spielersicht hat in diesem Fall die Weiterarbeit auf einer fehlerhaften Grundlage verhindert.
