# Seoul Underground Live - Static Site

This is a **static site** automatically deployed from the private crawler repository.

## Build Information

- **Build Time**: 2026-05-13T20:22:03Z
- **Source Commit**: [`516cf298ffeff5665eab7b3528d7a8b42deb4f37`](https://github.com/keunwoochoi/seoulunderground.live/commit/516cf298ffeff5665eab7b3528d7a8b42deb4f37)
- **Branch**: `main`
- **Workflow Run**: [View logs](https://github.com/keunwoochoi/seoulunderground.live/actions/runs/25824171695)

## Commit Details

- **Author**: Keunwoo Choi <gnuchoi+github@gmail.com>
- **Message**: fix: extend export cutoff to yesterday KST so today's events are visible (#173)

* fix: extend export cutoff to yesterday KST so today's events are always visible

The export filtered from midnight KST of the current KST day. Any cron run
after 15:00 UTC (= midnight KST) has already rolled over to the next KST day,
dropping today's Seoul evening events (stored as ~11:00-14:00 UTC). Result:
the frontend showed 0 events for what viewers in non-KST timezones see as today.

Fix: subtract 1 day from the KST cutoff (renamed to export_from) so yesterday
KST events are always included. The frontend does its own KST-based today
filtering client-side, so shipping an extra day is harmless.

* fix: always switch to keunwoochoi account before gh workflow trigger

Multiple gh accounts are configured. The active account drifted to
keunwoo-ortet, causing `gh workflow run` to return 404 and silently
breaking all deploys for ~2 weeks (May 9–13). The auth status check
passes for any authenticated account, so it didn't catch the wrong account.

Switch explicitly to keunwoochoi and treat failure as fatal (exit 1) so
a bad account state aborts loudly rather than silently deploying to the
wrong place.

## Deployment

- **Live Site**: https://undr.live
- **GitHub Pages**: https://undr-live.github.io

## Data Snapshot

The static JSON files in `/api/` were exported from the local backend at build time.
Events shown are from the crawler's database as of the build timestamp above.

---

*This README is auto-generated during deployment. Do not edit manually.*
