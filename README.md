# Signage for office

Live office TV signage for OptiSigns. One rotating screen cycling through three live-counting charity totals: UK, DE, and Global (USD).

## Deploy

1. Upload `index.html` to this repo's root (replacing the existing one to update).
2. Enable **GitHub Pages**: Settings → Pages → Deploy from branch `main` / root.
3. URL: `https://<your-username>.github.io/Signageforoffice/`

## OptiSigns setup

Add a **Website** app pointing at the Pages URL above.
- Display in iFrame: on
- Request Desktop Site: on
- Render Engine: **Other** (this is an OptiSigns stick, not a Fire Stick) → leave sub-option as "Normal"
- Update Interval: 600s is fine — the page itself live-updates every 10s, this interval just controls OptiSigns re-checking the URL

## How it works

- Single self-contained `index.html` — no external dependencies, safe to upload as-is.
- Rotates UK → DE → Global automatically **every 10 seconds** with a smooth 1.1s crossfade.
- Each total ticks up continuously and independently of the rotation (the counters keep running in the background even on hidden slides).
- Auto-scales to fill whatever screen size it's displayed on.

## To update

Replace `index.html` with a new version and commit. GitHub Pages redeploys in ~30–60 seconds (hard-refresh your browser to see it, Pages/CDN caching can lag a little).

### Changing rotation timing
In the source, the rotation interval is `10000` (ms) — search for `_rotateInterval` to adjust.

### Changing a total / growth rate
Each counter has a `startingTotal` and a per-second increment rate baked into the component — update these and re-export `index.html` to reflect new real-world figures.

## Roadmap

This is the first set — three slides (UK, DE, Global all-time charity raise). More slides will be added over time; structure for that isn't finalized yet.
