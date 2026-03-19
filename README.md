# Seoul Underground Live - Static Site

This is a **static site** automatically deployed from the private crawler repository.

## Build Information

- **Build Time**: 2026-03-19T05:02:42Z
- **Source Commit**: [`a52d693d6151546cb5c190720ea9775ea1f2ce3c`](https://github.com/keunwoochoi/seoulunderground.live/commit/a52d693d6151546cb5c190720ea9775ea1f2ce3c)
- **Branch**: `main`
- **Workflow Run**: [View logs](https://github.com/keunwoochoi/seoulunderground.live/actions/runs/23280599639)

## Commit Details

- **Author**: Keunwoo Choi <gnuchoi+github@gmail.com>
- **Message**: fix: refresh highlight titles from DB on export (#108)

* fix: refresh highlight titles from DB on export to prevent stale cache

weekly_highlights.json caches event titles at selection time (Monday).
When the ETL later corrects an event, the cached title goes stale and
the wrong title shows up in the screenshot cover.

export_highlights() now re-fetches title/translations from the DB for
each event_id before writing to frontend/public/api/highlights.json,
so the exported file always reflects the current DB state.

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* perf: batch-fetch events and translations in export_highlights

Fixes N+1 query pattern: was doing 2 queries per highlight inside the
loop. Now fetches all events and translations in 2 queries total using
IN clauses.

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

---------

Co-authored-by: Claude Sonnet 4.6 <noreply@anthropic.com>

## Deployment

- **Live Site**: https://undr.live
- **GitHub Pages**: https://undr-live.github.io

## Data Snapshot

The static JSON files in `/api/` were exported from the local backend at build time.
Events shown are from the crawler's database as of the build timestamp above.

---

*This README is auto-generated during deployment. Do not edit manually.*
