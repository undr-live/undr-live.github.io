# Seoul Underground Live - Static Site

This is a **static site** automatically deployed from the private crawler repository.

## Build Information

- **Build Time**: 2026-02-03T04:25:53Z
- **Source Commit**: [`d8cafec7818ded8d6b50bd526252fae4495670d6`](https://github.com/keunwoochoi/seoulunderground.live/commit/d8cafec7818ded8d6b50bd526252fae4495670d6)
- **Branch**: `main`
- **Workflow Run**: [View logs](https://github.com/keunwoochoi/seoulunderground.live/actions/runs/21616929448)

## Commit Details

- **Author**: Keunwoo Choi <gnuchoi+github@gmail.com>
- **Message**: fix: Use UTC-based weekday calculation for cover date color (#86)

The previous implementation used .getDay() which returns the weekday
in the local timezone of the machine running the code. This caused
incorrect coloring when the GitHub Actions runner is in a different
timezone than KST - e.g., Monday in KST was being colored red (Sunday)
because the runner's local time was still Sunday.

Fix: Use .getUTCDay() with a UTC-based timestamp to ensure we get the
weekday for the actual calendar date regardless of local timezone.

Color scheme (unchanged):
- Sunday: red (#FF6B9D)
- Saturday: blue (#6BB6FF)
- Friday: gold (#FFD700)
- Weekdays: white (#fff)

## Deployment

- **Live Site**: https://undr.live
- **GitHub Pages**: https://undr-live.github.io

## Data Snapshot

The static JSON files in `/api/` were exported from the local backend at build time.
Events shown are from the crawler's database as of the build timestamp above.

---

*This README is auto-generated during deployment. Do not edit manually.*
