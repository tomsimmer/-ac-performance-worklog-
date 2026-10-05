# AC Performance – Arbeitsnachweis

Web-App zur Zeiterfassung mit Login und Datenbank (Firebase). Läuft auf allen Geräten, Daten werden synchronisiert.

**Funktionen:** Kommen/Gehen, Tätigkeit + Beschreibung, Diktieren, Zeiten nachtragen, Einträge korrigieren/löschen, Wochenfortschritt (22 h), PDF-Export pro Monat.

## Einrichtung (einmalig)

### 1. Firebase-Projekt
1. https://console.firebase.google.com > **Projekt hinzufügen**.
2. **Build > Authentication > Los geht's > E-Mail/Passwort** aktivieren.
3. **Build > Firestore Database > Datenbank erstellen** (Standort `eur3` / Europa, Produktionsmodus).
4. Reiter **Regeln** öffnen, folgendes einfügen und **Veröffentlichen**:

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /users/{uid}/entries/{id} {
      allow read, write: if request.auth != null && request.auth.uid == uid;
    }
  }
}
```

5. **Projekteinstellungen (Zahnrad) > Allgemein > Deine Apps > Web (</>)** > App registrieren. Die angezeigte `firebaseConfig` kopieren.

### 2. Konfiguration eintragen
In diesem Repo die Datei `firebase-config.js` öffnen (Stift-Symbol auf GitHub) und die Werte ersetzen. Committen.

### 3. Veröffentlichen mit GitHub Pages
**Settings > Pages > Source: Deploy from a branch > Branch `main` / `/ (root)` > Save.**
Nach ca. 1 Minute ist die App unter `https://tomsimmer.github.io/-ac-performance-worklog-/` erreichbar.

### 4. Domain freigeben
Firebase Console > **Authentication > Einstellungen > Autorisierte Domains** > `tomsimmer.github.io` hinzufügen.

## Hinweise
- Der Firebase-API-Key im Frontend ist normal und kein Geheimnis. Geschützt sind die Daten durch Login und die Firestore-Regeln.
- Wochenziel ändern: `WEEKLY_HOURS` in `firebase-config.js`.
- Diktieren funktioniert in Chrome, Edge und Safari.
