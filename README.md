# Seoul Underground Live - Static Site

This is a **static site** automatically deployed from the private crawler repository.

## Build Information

- **Build Time**: 2026-03-22T05:32:06Z
- **Source Commit**: [`53e4b82869141bd9e9d81e6a9acfd2eebb0c7f38`](https://github.com/keunwoochoi/seoulunderground.live/commit/53e4b82869141bd9e9d81e6a9acfd2eebb0c7f38)
- **Branch**: `main`
- **Workflow Run**: [View logs](https://github.com/keunwoochoi/seoulunderground.live/actions/runs/23396538359)

## Commit Details

- **Author**: Keunwoo Choi <gnuchoi+github@gmail.com>
- **Message**: fix: export venue tier in static JSON (#120)

* fix: export venue tier field in static JSON

tier was missing from the venues export, causing all venues to default
to tier 1 in static mode. Tier-3 venues like @gc_jazzpicnic were ranking
as high as tier-0/1 venues since the frontend sort fell back to event
count alone.

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* test: verify venue tier is present in export JSON

Regression test: creates tier-0 and tier-3 venues, runs export_venues,
and asserts both tiers appear correctly in the output JSON.

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
