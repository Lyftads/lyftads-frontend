# Lyft Ads Dashboard — Frontend

Single Page App (HTML/JS puro, nessun framework).
Funziona su qualsiasi hosting statico: Vercel, Netlify, Cloudflare Pages.

## Deploy su Vercel (5 minuti)

1. Carica questa cartella su GitHub
2. Vai su https://vercel.com → New Project → importa il repo
3. Imposta variabile d'ambiente:
   - `LYFTADS_API_URL` → URL del tuo backend (es. https://lyftads-api.onrender.com)
4. Deploy!

## Deploy su Netlify

1. Vai su https://netlify.com → New site from Git
2. Build command: (lascia vuoto)
3. Publish directory: `.` (la cartella corrente)
4. Aggiungi env var `LYFTADS_API_URL` nelle site settings

## Configurazione URL backend

Il frontend legge l'URL del backend da `window.LYFTADS_API_URL`.
Se non configurato, usa `http://localhost:3001` in sviluppo.

Per produzione, aggiungi nello `<head>` di index.html prima dello script:

```html
<script>window.LYFTADS_API_URL = 'https://tuo-backend.onrender.com';</script>
```

Oppure usa le env variables del tuo hosting provider.

## Struttura

```
index.html   — App completa (SPA single-file)
vercel.json  — Config routing Vercel
_redirects   — Config routing Netlify
```

## Funzionalità

- Login/registrazione con JWT (token salvato in localStorage)
- Dashboard overview con 5 grafici aggregati
- Dettaglio per cliente con revenue, ROAS, MER e metriche per canale
- 6 piattaforme: Meta Ads, Google Ads, Shopify, Klaviyo, TikTok Ads, Amazon Ads
- Selettore date avanzato (preset + personalizzato) con fuso Europe/Rome
- Confronto periodi
- Alert automatici calo ≥15% ultimi 3 giorni
- Auto-refresh ogni 15 minuti
- Export CSV
- Funziona offline con dati mock se il backend non è ancora configurato
