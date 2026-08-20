# Flood insurance pool explorer

An interactive explorer for catastrophe-bond risk-sharing pools across the U.S. states.
Runs **entirely in the browser** — no server, no backend. Just static files.

Brush the parallel-coordinates plot to select a trade-off and watch the co-membership cluster
network redraw; click a point in the scatter to drill into one partition (pool map, per-pool
tail risk, chronic loss, strain, per-state defection, and a loss-year timeseries).

## What's in here
- `index.html` — the whole app (uses Plotly.js from a CDN)
- `data.json` — everything precomputed (~10 MB; the fronts and every panel's data)
- `.nojekyll` — tells GitHub Pages to serve the files as-is

## Put it online with GitHub Pages (free)
1. Create a new repository on GitHub (e.g. `flood-pool-explorer`), **Public**.
2. Upload these three files to the repo root — either drag them into the GitHub web
   uploader ("Add file → Upload files"), or from a terminal:
   ```bash
   git init
   git add index.html data.json .nojekyll README.md
   git commit -m "Flood insurance pool explorer (static)"
   git branch -M main
   git remote add origin https://github.com/<your-username>/flood-pool-explorer.git
   git push -u origin main
   ```
3. In the repo: **Settings → Pages**. Under "Build and deployment", set
   **Source = Deploy from a branch**, **Branch = main**, **Folder = / (root)**, then **Save**.
4. Wait ~1 minute. Your site is live at:
   `https://<your-username>.github.io/flood-pool-explorer/`

That's it — nothing to maintain, and GitHub serves `data.json` gzipped (~2–3 MB over the wire).

## Run it locally first (optional)
It must be served over HTTP (it `fetch`es `data.json`, so double-clicking the file won't work):
```bash
python -m http.server 8070   # then open http://127.0.0.1:8070
```

## Note
The only external dependency is `https://cdn.plot.ly/plotly-2.35.2.min.js`. If you'd rather have a
single self-contained file with no CDN, inline Plotly into `index.html`.
