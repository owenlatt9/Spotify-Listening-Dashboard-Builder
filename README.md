# 🎧 Spotify Listening Dashboard Builder

Turn your Spotify streaming history into an interactive, personal dashboard — top artists, how your taste shifted year to year, when you actually listen, and which artists stuck around the longest.

**[Try it live →](#)** *(add your GitHub Pages link here once it's deployed)*

Everything runs entirely in your browser. No server, no account, no analytics — your listening history never leaves your computer.

---

## What it does

Drop in your Spotify data export and this builds a full dashboard, including:

- **Hero stats** — total hours listened, unique artists/tracks, longest streak, biggest single day
- **Top lists** — top artists, tracks, and albums, browsable all-time or by year
- **Timeline** — a month-by-month slider showing your top artists and most-played track for any point in your history
- **Taste over time** — a stacked chart of how your listening mix shifted year to year
- **When you listen** — a day-of-week × hour heatmap
- Distribution charts (histogram/boxplot/scatter) for daily listening patterns

Once it's built, you can **save it as a standalone HTML file** — the computed dashboard gets baked into a single static file you can host anywhere (like this repo's own `listening-dashboard.html`), with no build step and no server needed.

## How to use it

1. **Request your data from Spotify** — go to your Spotify account's **Privacy settings** and request your **Extended streaming history**. This is a different, richer export than the basic "Account data" download, and it can take Spotify a few days to email you the zip.
2. **Unzip it.** You'll get a folder containing files named like `Streaming_History_Audio_2023_1.json`. You may have several — that's normal.
3. **Open this tool and drop them in.** Select every `Streaming_History_Audio_*.json` file at once. Anything else in the export is ignored.
4. Optionally:
   - **Exclude specific artists** — handy for filtering out background/study-music channels or white-noise "artists" that would otherwise dominate your numbers without really being "listening."
   - **Pick a color theme** — a few presets, or set your own main/accent/background colors.
   - **Set a minimum-minutes-per-day threshold** — treats very short days as accidental opens rather than real listening sessions, and excludes them from the daily-distribution stats.
5. Click **Build my dashboard**.
6. Click **Save as standalone file** to download a self-contained `listening-dashboard.html` you can host on your own site, no rebuilding required.

## Privacy

This is a single HTML file with no backend. All parsing, cleaning, and aggregation happens client-side in JavaScript — the files you select are read locally and never uploaded anywhere. You can save this page and run it completely offline.

## Tech

Plain HTML/CSS/JavaScript. No frameworks, no build step, no dependencies — charts are hand-rolled SVG. Open `index.html` in any modern browser and it works.

## Notes on the data

- Duplicate rows in Spotify's export (a known quirk of the extended history) are automatically de-duplicated.
- Only rows with a track, artist, and timestamp are counted as "plays."
- Also accepts a pre-parsed `.csv`/`.tsv` if you'd rather work from a spreadsheet than Spotify's raw JSON — see `recordsFromCSV` in the source for expected column names.

---

Built by [Owen Latt](https://owenlatt9.github.io) — originally made to build the ["Listening Stats"](https://owenlatt9.github.io/listening.html) page on my portfolio, then cleaned up so anyone can build their own.
