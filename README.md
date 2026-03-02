# Drone Strikes Map

An interactive map that visualizes **US drone strikes in Northwest Pakistan** from 2004 to 2017. Strike locations appear as markers on a Google Map; you can filter by year and step through time to see how the pattern of strikes changed.

## What it does

- **Map view** — Centered on the Pakistan–Afghanistan border region (lat/lng ~32.3, 69.5). Each strike is a marker at the location from the data.
- **Year filter** — Use the slider or the year buttons (2004–2017) to show only strikes for that year.
- **Play / Pause** — The play button in the header auto-advances the year so you can watch the timeline.
- **Strike data** — The app loads `strikedata.csv`, which includes date, location name, min/max deaths, civilian and child death ranges, and coordinates.

## How to run it

The app loads `strikedata.csv` over HTTP, so you need to serve the project from a local web server. Opening `index.html` directly in the browser (file://) will not work.

**Option 1 — Python (no install if you have Python):**

```bash
cd MapDroneStrikes
python3 -m http.server 8080
```

Then open **http://localhost:8080** in your browser.

**Option 2 — Node (if you have npx):**

```bash
cd MapDroneStrikes
npx serve -p 8080
```

Then open **http://localhost:8080**.

## Requirements

- **Google Maps API key** — The map is powered by the Google Maps JavaScript API. The key is embedded in `index.html`. If the map does not load, the key may be invalid or restricted; replace it with your own key in the script tag that loads the Maps API.
- **Modern browser** — Any recent browser that supports the APIs used (e.g. Chrome, Firefox, Safari, Edge).

## Project layout

| File / folder   | Purpose |
|-----------------|--------|
| `index.html`    | Main page: map, year controls, and app logic (AngularJS + jQuery). |
| `styles.css`    | Layout and styling for the map and controls. |
| `strikedata.csv`| Strike records: date, location, death counts, latitude/longitude. |
| `drone128.png`  | Icon/asset used in the visualization. |
| `timer-example-js.html` | Separate example/timer demo. |

## Tech stack

- **AngularJS 1.6** — App structure and data binding.
- **jQuery 3.3** — DOM and event handling (slider, buttons).
- **Google Maps JavaScript API** — Map and markers.
- **Font Awesome** — Play/pause and other icons.

## Data

`strikedata.csv` columns include: `date`, `location`, `minDeaths`, `maxDeaths`, `minCivilianDeaths`, `maxCivilianDeaths`, `minChildDeaths`, `maxChildDeaths`, `mapIndex`, `exactdate`, `longitude`, `latitude`. The visualization uses the coordinates to place markers and the date/year to filter by the selected year.

---

*Inspired by [The National’s Pakistan drone visual](https://multimedia.thenational.ae/assets/visual_assets/pakistan_drone_visual).*
