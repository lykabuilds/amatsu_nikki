# Amatsu Nikki

*A gecko care diary.* **Nikki** is Japanese for "diary".

Amatsu Nikki is a care tracker for leopard geckos, named after my first gecko, Amatsu. It replaces scattered notes with one place to log meals, weigh-ins and profiles, and flags early warning signs like weight loss, long feeding gaps and dropping appetite. It runs in the browser with no account, works offline, and keeps your data on your device.

## Features

- **Homepage** with a card per gecko: photo, morph, age, last fed, latest weight and a health status.
- **"Needs a look" list** that surfaces any gecko with a flagged check.
- **Gecko profile:** photo, morph, hatch date (with age), purchase date, sex, breeder, sire/dam morphs and het notes.
- **Meal log:** date, time, insect type, how many eaten and how many refused.
- **Weight log** with a trend chart.
- **Rule-based health check:**
  - Feeding gap vs. life stage (baby / juvenile / adult)
  - Weight change over ~30 days
  - Appetite (refusal rate and drop vs. earlier weeks)
  - Feeder variety and fatty-treat share
- **Backup & restore** to a JSON file (photos included).
- **Installable** (Add to Home Screen) and works offline.

> The health check gives general guidelines based on your logs. It is not veterinary advice.

## Run it

It's a static site: open `index.html` in a browser, or serve the folder:

```bash
npx serve .
# or
python3 -m http.server 8000
```

## Deploy on GitHub Pages

1. Create a new repository on GitHub, e.g. `amatsu-nikki`.
2. Upload all files in this folder (`index.html`, `manifest.webmanifest`, `icon.svg`, `sw.js`, `README.md`) to the repository root.
3. Go to **Settings → Pages**.
4. Under **Build and deployment**, set **Source** to *Deploy from a branch*, choose `main` and `/ (root)`, then **Save**.
5. After a minute or two, the app is live at `https://<your-username>.github.io/amatsu-nikki/`.

## How data is stored

| Data | Where |
|---|---|
| Geckos, meals, weigh-ins | `localStorage` (key `geckoLog.v1`) |
| Photos | IndexedDB (`geckoLogPhotos`), resized to max 900 px |

Data stays on the device and browser you use. It does not sync between your phone and laptop, and clearing browser data erases it. Use **Download backup** regularly, and **Restore backup** to move your log to another device.

## Files

```
index.html             The whole app (HTML, CSS, JS in one file)
manifest.webmanifest   App name, icon and colors for Add to Home Screen
icon.svg               App icon
sw.js                  Service worker for offline use
```

## Tech

Plain HTML, CSS and JavaScript. No frameworks or build step. The only external resource is Google Fonts, with system-font fallbacks.

## Ideas for later

- Shed tracking (date, complete or stuck)
- Supplement log (calcium, D3, multivitamin)
- CSV export for analysis in Excel or Power BI
- Cloud sync across devices
