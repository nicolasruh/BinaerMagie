# Binärmagie – Projektkontext

## Zweck und Technik

Kleine Webapp für eine Vorführung im Unterricht: Die Lehrperson behauptet,
sich ein Farbmuster einzuprägen, und findet anschliessend eine heimliche Änderung.
Die gesamte App steckt in [index.html](./index.html): HTML, CSS und lokales
JavaScript, ohne Bibliotheken, Backend, Build-Schritt oder externe Ressourcen.
Die Datei lässt sich direkt im Browser öffnen und offline verwenden.

## Ablauf und Verhalten

- Die Matrix erscheint sofort; Grössen von 5 × 5 bis 10 × 10 sind auswählbar.
- Drei Schritte: Lehrperson prägt sich das Muster ein → bestätigt und schaut
  weg → Schüler:in ändert mit einem Klick eine Farbe → Lehrperson klickt auf
  das vermutete Feld und erhält Rückmeldung.
- Der aktuelle Schritt wird hervorgehoben. Vor der Bestätigung und nach dem
  Ergebnis sind die Felder gesperrt; die Vermutung verändert keine Farbe.
- Normale Ansicht: nur Farben, keine Zahlen, Randmarkierungen oder Hinweise
  auf die Methode. Die Anleitung beschreibt ausschliesslich den Ablauf.
- Native Dropdowns. Farben wechseln sofort, ohne die Runde zurückzusetzen;
  Weiss steht immer für 0, Blau/Violett/Orange für 1.
- Neue Matrix oder Grössenwechsel startet beim ersten Schritt und entfernt
  auch sämtliche Spoiler-Markierungen.
- „Das Geheimnis …“ öffnet zuerst eine Spoiler-Warnung. Erst nach Bestätigung
  erscheint die Erklärung. „Erklärung schliessen“ ergänzt in der aktuellen
  Matrix 0/1 und markiert die letzte Zeile und Spalte gelb, ohne Muster,
  Spielphase oder Ergebnis zu verändern.

## Methode (Spoiler)

Das Grundprinzip wurde anhand der ursprünglichen Magic.jar nachvollzogen.
Bei n × n Feldern sind (n − 1) × (n − 1) Bits zufällig. Letzte Zeile und
Spalte ergänzen gerade Parität, einschliesslich der Ecke unten rechts.
Genau eine Änderung erzeugt eine ungerade Zeile und Spalte; ihr Schnittpunkt
ist das geänderte Feld. Das gilt auch für geänderte Prüfbits, nicht aber
zuverlässig für mehrere Änderungen.

## Veröffentlichung und Prüfung

- Repository: https://github.com/nicolasruh/BinaerMagie
- Webseite: https://nicolasruh.github.io/BinaerMagie/
- GitHub Pages veröffentlicht den Repository-Stamm vom Branch `main`.
  Änderungen mit `git push origin main` veröffentlichen; kein Build nötig.
- Bisher im Browser geprüft: alle 355 Änderungspositionen der sechs Grössen,
  richtige/falsche Vermutungen, sofortige Einstellungswechsel, Spoiler-
  Bestätigung, Zahlen/Markierungen samt Rücksetzung sowie mobiles Layout.
- Es gibt noch keine automatisierte Testsuite im Repository. Bei Änderungen
  insbesondere Randfelder, Ecke, Farbwechsel und Spoiler-Zustände mitprüfen.
