# Zeiterfassung

Statische Web-App zur Arbeitszeiterfassung auf Basis des bisherigen Excel-Makros.

## Funktionen

- Eingabe von `Kommt` und `Geht`
- Optionaler zweiter Zeitblock
- Berechnung der Gesamt-Anwesenheit
- Automatischer Abzug von `0,75 h`, wenn die Gesamt-Anwesenheit über `6 h` liegt
- Netto-Zeit wird ab mehr als `9,99 h` rot hervorgehoben
- Lokale Speicherung im Browser
- CSV-Export für Excel

## Nutzung

Die App liegt in `index.html` und kann direkt im Browser geöffnet werden.

Für GitHub Pages:

1. Dateien in das Repository `jorgepnt-design/zeiterfassung` hochladen.
2. In GitHub unter `Settings > Pages` die Quelle `GitHub Actions` auswählen.
3. Nach dem Push auf `main` wird die App automatisch veröffentlicht.

