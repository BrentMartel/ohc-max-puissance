# OHC Max Puissance Tournament Dashboard

Live-updating dashboard for OHC Max Puissance in the 2012 D3 Contact division.

The page fetches the official tournament Google Sheets every time someone loads it and auto-refreshes every 5 minutes. Edit the sheets and the dashboard catches up on its own. No redeploy needed.

## Live site

https://brentmartel.github.io/ohc-max-puissance/

## How it works

- `index.html` is a single self-contained file: React from CDN, Babel in the browser, PapaParse for CSV.
- On load, it fetches both sheets via the Google Sheets gviz CSV endpoint.
- Standings are parsed by locating the `2012 D3 Contact` section header and reading teams until the next blank row.
- Schedule is parsed by walking rows, tracking day headers, and keeping any `2012 D3` game where OHC or Max Puissance is on either side.
- Auto-refresh runs every 5 minutes while the tab is open. A manual Refresh button is in the header.

## Data sources

- Schedule: tournament Google Sheet
- Standings: tournament Google Sheet

Both sheets need to be set to "Anyone with the link can view" for the dashboard to fetch them.

## Changing the division or team

Edit the constants at the top of the script block in `index.html`:

- `DIVISION_LABEL` — exact text of the division header row in the standings sheet
- `LEVEL_TAG` — value in the Level column on the schedule sheet
- `OHC_ALIASES` — lowercase substrings used to match team names
