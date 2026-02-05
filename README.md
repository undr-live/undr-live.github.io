# Seoul Underground Live - Static Site

This is a **static site** automatically deployed from the private crawler repository.

## Build Information

- **Build Time**: 2026-02-05T05:34:54Z
- **Source Commit**: [`92bdf33b221175ba16993cb503ed79899d57d072`](https://github.com/keunwoochoi/seoulunderground.live/commit/92bdf33b221175ba16993cb503ed79899d57d072)
- **Branch**: `main`
- **Workflow Run**: [View logs](https://github.com/keunwoochoi/seoulunderground.live/actions/runs/21700103202)

## Commit Details

- **Author**: Keunwoo Choi <gnuchoi+github@gmail.com>
- **Message**: fix: Export highlights to static JSON for GitHub Pages (#91)

Two issues were preventing highlighted events from showing:

1. Missing weekly_job.sh - the launchd plist referenced this file but
   it didn't exist, so highlight selection never ran on Mondays

2. Highlights not exported to static JSON - frontend in static mode
   (GitHub Pages) couldn't fetch highlights because:
   - export_static_json.py didn't include highlights
   - App.tsx api() function didn't handle /api/highlights path

Fixes:
- Add weekly_job.sh that runs highlight_job.sh on Mondays
- Add export_highlights() to export weekly_highlights.json
- Add /api/highlights routing in static mode frontend

## Deployment

- **Live Site**: https://undr.live
- **GitHub Pages**: https://undr-live.github.io

## Data Snapshot

The static JSON files in `/api/` were exported from the local backend at build time.
Events shown are from the crawler's database as of the build timestamp above.

---

*This README is auto-generated during deployment. Do not edit manually.*
