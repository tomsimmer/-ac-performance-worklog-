# AC-Performance Worklog

Mobile-first Web-App mit Supabase-Datenbank für geräteübergreifende Zeiterfassung.

## Enthalten
- Magic-Link-Login
- Kommen / Gehen
- Nachtragen und Korrigieren
- 22-Stunden-Abrechnungsintervalle
- PDF-Export
- Responsive Oberfläche für Handy und Desktop

## Start lokal
1. `npm install`
2. `.env.example` nach `.env` kopieren
3. Supabase-Werte eintragen
4. `npm run dev`

## Deployment
1. Neues privates GitHub-Repository anlegen
2. Dateien hochladen
3. Bei Vercel importieren
4. Umgebungsvariablen setzen:
   - `VITE_SUPABASE_URL`
   - `VITE_SUPABASE_ANON_KEY`
5. In Supabase `supabase/schema.sql` ausführen
6. Unter Authentication > URL Configuration die Vercel-URL eintragen
