# Seoul Underground Live - Static Site

This is a **static site** automatically deployed from the private crawler repository.

## Build Information

- **Build Time**: 2026-02-14T17:37:47Z
- **Source Commit**: [`a2a5baeaba9fbc1966eaaa6e38f0ded6b3911009`](https://github.com/keunwoochoi/seoulunderground.live/commit/a2a5baeaba9fbc1966eaaa6e38f0ded6b3911009)
- **Branch**: `main`
- **Workflow Run**: [View logs](https://github.com/keunwoochoi/seoulunderground.live/actions/runs/22021529193)

## Commit Details

- **Author**: Keunwoo Choi <gnuchoi+github@gmail.com>
- **Message**: feat: Dynamic events per page (7 or 8) with cascading trim logic (#94)

* feat: Dynamic events per page (7 or 8) with cascading trim logic

- Auto-select 7 events/page when ≤63 events, 8 when >63 (max 72)
- Add cascading trim when >72 events: drop no-datetime → dedupe venues → truncate tail
- Support epp URL param override for explicit control
- Compact InstagramFooter padding when epp=8
- Match Python screenshot pipeline to pass epp param to frontend

* refactor: Address code review - named constants + simplify trim loop

- Extract EVENTS_PER_PAGE_STANDARD=7, EVENTS_PER_PAGE_COMPACT=8 in Python
- Extract EPP_STANDARD=7, EPP_COMPACT=8, MAX_CONTENT_PAGES=9 in TypeScript
- Simplify busiest-venue removal using findLastIndex + Object.keys().find()

## Deployment

- **Live Site**: https://undr.live
- **GitHub Pages**: https://undr-live.github.io

## Data Snapshot

The static JSON files in `/api/` were exported from the local backend at build time.
Events shown are from the crawler's database as of the build timestamp above.

---

*This README is auto-generated during deployment. Do not edit manually.*
