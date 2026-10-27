# The Day I Was Born

A single-page website: enter your birth date, time and place and get a personal time capsule.

| Section | Data source |
|---|---|
| The world that day (events, observances) | Wikipedia "On this day" REST API |
| The sky above you (hourly temp, rain, wind, sunrise/sunset) | Open-Meteo Historical Weather API (ERA5, from 1940) + Open-Meteo Geocoding |
| Headlines | Wikipedia Current Events portal for that exact date (~1995 onward) |
| Birthday twins | Wikipedia "On this day" births (same-day births highlighted) |
| Life clock | Calculated in the browser, using the birthplace's UTC offset |
| Birth moment card | Drawn on a canvas, downloadable as PNG |

All APIs are free, need no API key, and allow browser (CORS) requests, so the site is fully static — just `index.html`.

## Deploy (pick one, ~2 minutes)

### Option A — Netlify Drop (easiest, no account setup needed beyond sign-in)
1. Go to https://app.netlify.com/drop
2. Drag the `day-i-was-born` folder onto the page.
3. You get a live URL like `https://random-name.netlify.app`. Rename it in **Site configuration → Change site name** (e.g. `the-day-i-was-born`).

### Option B — GitHub Pages
1. Create a new public repo, e.g. `the-day-i-was-born`.
2. Upload `index.html` (Add file → Upload files → Commit).
3. Repo **Settings → Pages → Source: Deploy from a branch → main / (root) → Save**.
4. Site goes live at `https://<your-username>.github.io/the-day-i-was-born/` within a minute.

### Option C — Vercel
```bash
npm i -g vercel
cd day-i-was-born
vercel --prod
```

## Notes
- Weather is a reanalysis estimate for a ~25 km grid, not a station reading; dates before 1940 show no weather.
- Day-by-day headlines exist from the mid-1990s; older dates fall back to that date's recorded events.
- Inside the Claude artifact viewer, outside APIs are blocked, so that version uses Claude to compile history and shows typical-month weather instead. The deployed site uses the live sources above.
