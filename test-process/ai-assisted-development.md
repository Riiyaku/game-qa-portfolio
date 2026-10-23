# KI-gestützte Entwicklung

Der Prototyp wird überwiegend mit KI-Werkzeugen entwickelt. Dieses Dokument erklärt offen, wer was macht.

## Eingesetzte Werkzeuge

| Werkzeug | Einsatz |
|---|---|
| Claude Code | Implementierung, später auch Koordination von Spezialagenten (Umsetzung und getrennte Prüfung) |
| OpenAI Codex | Implementierung und Korrekturen, unter anderem an automatisierten Tests; zeitweise Charaktermodell-Arbeit |
| ChatGPT | Erklärungen und Schritt-für-Schritt-Anleitungen, die ich selbst ausgeführt habe, z. B. das Einbinden von Animationen in Godot ([QA-05](../bug-reports/05-run-animation-root-motion.md)) |

Seit dem 18.10.2026 arbeitet das Projekt ausschließlich mit Claude Code.

## Wer was macht

| Bei mir | Bei der KI | Bei meinem Projektpartner |
|---|---|---|
| Was soll das Spiel tun? | Code schreiben | Server, gemeinsame Spiellogik |
| Wie soll es sich anfühlen? | Automatisierte Tests schreiben und ausführen | Authentifizierung, Netzwerk |
| Im Spiel testen, Fehler beschreiben | Fehlerursachen im Code suchen | Persistenz, Infrastruktur |
| Bewerten, ob eine Korrektur reicht | Modell- und Animationsarbeit in Blender | |
| Weiterarbeit freigeben oder stoppen | Technische Messungen und Prüfberichte | |

Ich habe den überwiegenden Teil des Programmcodes **nicht** selbst geschrieben und **keine** automatisierten Tests programmiert.

## Beispiele für meine Vorgaben (Oktober 2026)

- Die neue Charakterbasis sollte glatt und gesichtslos sein. Die KI sollte sie tatsächlich in Blender und Godot öffnen und sichtbar prüfen, statt nur Zahlen zu melden. Ich habe ausdrücklich festgelegt, dass ich nicht selbst modelliere.
- Modelle sollen aus vielen Blickwinkeln geprüft werden, nicht nur von vorne, seitlich und hinten.
- Für jede ausführende KI-Rolle gibt es eine **getrennte prüfende Rolle** mit Fachwissen, die detailliert prüft und Fehler meldet, aber nicht selbst repariert.

Im Projektablauf gilt außerdem: höchstens zwei Korrekturrunden pro Problem, danach wird die Methode hinterfragt statt endlos nachgebessert.

## Warum KI-Code trotzdem manuell geprüft werden muss

1. **Automatisch grün ist nicht dasselbe wie richtig.** In [QA-01](../bug-reports/01-visual-quality-review.md) waren alle technischen Prüfungen bestanden, die Form war trotzdem sichtbar falsch.
2. **Die KI prüft gegen das, was sie verstanden hat.** Wenn die Beschreibung ungenau ist, ist der Test es auch.
3. **Spielgefühl lässt sich schlecht messen.** Ob ein Doppelklick „sich richtig anfühlt“, zeigt sich erst beim Spielen.
4. **Automatisierte Tests haben eigene Fehler.** Im Projekt gab es Testfehler, die nicht am Spiel lagen, sondern am Testaufbau (zum Beispiel doppelt belegte Netzwerk-Ports).

## Grenzen dieser Arbeitsweise

- Ich kann Code nur eingeschränkt lesen und Ursachen im Code nicht selbst bestätigen. Ich bewerte das **Verhalten**, nicht die Implementierung.
- Ohne eigenes Protokoll hängt der Nachweis meiner Tests an der Projektdokumentation, die überwiegend die KI schreibt, und an meinen eigenen Bildschirmaufnahmen.
- Die KI kann Ergebnisse zu positiv darstellen. Ich habe deshalb gelernt, nach tatsächlichen Bildern und Abläufen zu fragen statt nach Zusammenfassungen.
- KI-Werkzeuge haben eigene Störungen. Ich habe zum Beispiel gemeldet, dass wiederholt Genehmigungsabfragen auftraten, und vermutet, dass Läufe unsichtbar im Hintergrund stattfanden, in denen ich gar nichts freigeben konnte. Die technische Analyse dazu hat die KI durchgeführt.
