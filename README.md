# Rolling In

Live at **https://gyeningcorp.github.io**

A single-page web app for finding small local bands playing at bars and restaurants **tonight**, starting in Pittsburgh and expanding globally via discovery links. "Rolling In" — as in, the band's rolling in, the crowd's rolling in.

## What it does

- 📍 **Geolocation** — detects your city via browser GPS + OpenStreetMap reverse geocoding (no API key).
- 🏙️ **Pittsburgh "home" mode** — attempts to live-scrape Thunderbird, Club Café, Crafthouse, Mr. Roboto, Mr. Smalls, Bottlerocket, and Stage AE through a public CORS proxy, then renders event cards with LIVE NOW badges.
- 🌍 **Global mode** — for every other city, renders 8 discovery tiles pre-filled for that city (Facebook Events, Instagram hashtags, Google Maps, Bandsintown, Yelp, Songkick, Eventbrite, DICE).
- 🎤 **Venue directory** — every venue is tagged **Scraped**, **Social Watch**, or **Linked Only** so users see exactly how each listing is sourced.
- 🏈 **NFL Draft banner** — auto-appears April 20–25, 2026.
- ⟳ **Refresh** button + auto-refresh every 30 min in Pittsburgh mode.
- 🌓 Dark / light theme toggle.

## Why static (for now)

GitHub Pages is static-only. The client-side scraper uses public CORS proxies, which are rate-limited and unreliable — expect the status bar to show red pills on some venues. This is the honest "Scraped / Social Watch / Linked Only" model from the spec.

When you migrate to a real domain + Vercel, move the scrape to `api/events.js` (server-side `cheerio`) as originally planned. Everything else stays the same.

## Project layout

```
gyeningcorp.github.io/
├── index.html            # entire app (HTML + CSS + JS)
├── manifest.json         # PWA manifest
├── privacy-policy.html
├── 404.html
└── README.md
```

## Local preview

```bash
python -m http.server 8080
# open http://localhost:8080
```

## Next refinements

- Real venue logos / photos
- Per-venue custom parsers (replace the generic date-line regex)
- Social Watch polling for venues like Elly's
- Capacitor shell for Android / iOS submission
- Migrate scraping to Vercel serverless (`api/events.js`) once a real domain is bought
