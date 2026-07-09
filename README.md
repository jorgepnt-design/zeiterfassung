# Zeiterfassung

Statische Web-App zur Arbeitszeiterfassung auf Basis des bisherigen Excel-Makros.

## Funktionen

- Eingabe von `Kommt` und `Geht`
- Optionaler zweiter Zeitblock
- Eintragen von `Urlaub` und `Gleittag`, auch fuer mehrere Tage auf einmal
- Mehrtages-Eintraege fuer Urlaub/Gleittag speichern nur Montag bis Freitag
- Monats-Kalender mit farblicher Anzeige von Urlaub und Gleittagen
- Berechnung der Gesamt-Anwesenheit
- SAP-aehnliche Pausenbewertung passend zu den geprueften ESS-Beispielen
- Netto-Zeit wird ab mehr als `9,99 h` rot hervorgehoben
- CSV-Export für Excel
- App-Icon und Web-App-Manifest für Installation auf Handy/Desktop
- Cloud-Speicherung mit Firebase Auth und Firestore
- Konto-Login nur fuer eigene Cloud-Daten und Zugriff von mehreren Geraeten
- Passwort-Reset per E-Mail

## Zeitberechnung

- Einzelner Arbeitsblock ueber 6 Stunden wird auf maximal 6,00 Netto-Stunden begrenzt.
- Bei zwei Arbeitsbloecken wird die tatsaechliche Pause gegen eine 45-Minuten-Pausenbewertung gerechnet.
- Bei einer ersten Geht-Zeit ab 14:00 und weniger als 30 Minuten Pause werden 30 Minuten abgezogen.
- Der Abzug reduziert kurze Tage nicht unter 6,00 Netto-Stunden.

## Nutzung

Die App liegt in `index.html` und kann direkt im Browser geöffnet werden.

Für GitHub Pages:

1. Dateien in das Repository `jorgepnt-design/zeiterfassung` hochladen.
2. In GitHub unter `Settings > Pages` die Quelle `GitHub Actions` auswählen.
3. Nach dem Push auf `main` wird die App automatisch veröffentlicht.

## Firebase

Die App nutzt das Firebase-Projekt `arbeitsapp-3364c`.

In Firebase Authentication müssen E-Mail/Passwort-Anmeldungen aktiviert sein. Außerdem muss die GitHub-Pages-Domain unter `Authentication > Settings > Authorized domains` eingetragen sein:

```txt
jorgepnt-design.github.io
```

Für Firestore müssen angemeldete Benutzer nur auf ihre eigenen Daten zugreifen dürfen:

```txt
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /users/{userId}/{document=**} {
      allow read, write: if request.auth != null && request.auth.uid == userId;
    }
  }
}
```
