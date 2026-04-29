# mag7-dashboard

Private dashboard for the daily Mag 7 valuation cron.

## How it's fed

`mag7_daily.py` runs at 16:07 ET on weekdays (post-close) via OpenClaw cron. It writes `memory/mag7-daily-state.json` in the OpenClaw workspace, then copies it to `data/state.json` here, commits, and pushes. GitHub Pages re-publishes within ~1 minute.

## Layout

- `index.html` — single static page, vanilla JS, inline SVG sparklines.
- `data/state.json` — raw history (rolling 60 runs).

## Local preview

```sh
python3 -m http.server -d /Users/openclaw/Code/mag7-dashboard 8000
```

Then open <http://localhost:8000/>.
