# Seoul Underground Live - Static Site

This is a **static site** automatically deployed from the private crawler repository.

## Build Information

- **Build Time**: 2026-02-03T04:51:45Z
- **Source Commit**: [`14f9b282efc2c1c2f0aba8109f1634a813d9d5de`](https://github.com/keunwoochoi/seoulunderground.live/commit/14f9b282efc2c1c2f0aba8109f1634a813d9d5de)
- **Branch**: `main`
- **Workflow Run**: [View logs](https://github.com/keunwoochoi/seoulunderground.live/actions/runs/21617489109)

## Commit Details

- **Author**: Keunwoo Choi <gnuchoi+github@gmail.com>
- **Message**: fix: Use UTC-based dateStr for cover overlay (#87)

Apply the same timezone-agnostic technique to dateStr creation.
The previous implementation had:
- Hardcoded -05:00 for America/New_York (incorrect during DST)
- Only handled America/New_York, defaulting to +09:00 for all else

Since formatDateHeader already takes the timezone parameter and handles
conversion internally, we can simply pass a UTC timestamp.

Also refactored to create the Date object once (dateAtUtcNoon) and reuse
it for both dateStr and weekdayIdx.

## Deployment

- **Live Site**: https://undr.live
- **GitHub Pages**: https://undr-live.github.io

## Data Snapshot

The static JSON files in `/api/` were exported from the local backend at build time.
Events shown are from the crawler's database as of the build timestamp above.

---

*This README is auto-generated during deployment. Do not edit manually.*
