# Seoul Underground Live - Static Site

This is a **static site** automatically deployed from the private crawler repository.

## Build Information

- **Build Time**: 2026-01-31T19:25:17Z
- **Source Commit**: [`2b56a20ff1b7694089b0d15d5510047df23d9c6c`](https://github.com/keunwoochoi/seoulunderground.live/commit/2b56a20ff1b7694089b0d15d5510047df23d9c6c)
- **Branch**: `main`
- **Workflow Run**: [View logs](https://github.com/keunwoochoi/seoulunderground.live/actions/runs/21549645720)

## Commit Details

- **Author**: Keunwoo Choi <gnuchoi+github@gmail.com>
- **Message**: fix: Fix cover screenshot alignment for center-crop (#84)

* fix: Fix cover screenshot alignment for center-crop

- Replace flexbox percentage sections with absolute centering technique
- Use transform: translate(-50%, -50%) for bulletproof centering
- Content now appears correctly in the center 1170px crop area
- Works for both non-highlighted days (genre title) and highlighted days (event card)
- Add test script for manual screenshot generation with date/highlight override
- Add App.tsx support for test_date and test_highlight URL parameters

Fixes the issue where date text was half trimmed off after the highlighted
shows feature was added (commit 2080775).

* refactor: Clean up test_cover_screenshot.py

- Remove unused inject_highlight_json function
- Move urllib.parse import to top of file (PEP 8)
- Remove unused Page import

## Deployment

- **Live Site**: https://undr.live
- **GitHub Pages**: https://undr-live.github.io

## Data Snapshot

The static JSON files in `/api/` were exported from the local backend at build time.
Events shown are from the crawler's database as of the build timestamp above.

---

*This README is auto-generated during deployment. Do not edit manually.*
