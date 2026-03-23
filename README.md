# Seoul Underground Live - Static Site

This is a **static site** automatically deployed from the private crawler repository.

## Build Information

- **Build Time**: 2026-03-23T02:11:28Z
- **Source Commit**: [`87bf5114699cfa2225ce8c4b452eaa390733d533`](https://github.com/keunwoochoi/seoulunderground.live/commit/87bf5114699cfa2225ce8c4b452eaa390733d533)
- **Branch**: `main`
- **Workflow Run**: [View logs](https://github.com/keunwoochoi/seoulunderground.live/actions/runs/23418448410)

## Commit Details

- **Author**: Keunwoo Choi <gnuchoi+github@gmail.com>
- **Message**: feat: iCal export per event (PR D) (#125)

* feat: iCal export — add to calendar button on event cards (#PR-D)

Each event card now shows a calendar icon button next to the external link
icon. Clicking it downloads a standards-compliant .ics file (RFC 5545)
pre-filled with title, time (UTC, 2h default duration), venue location,
description, and source URL.

Zero infra cost — generated client-side via Blob URL.

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* fix: trigger production deploy at end of musician_job.sh

After link_events + apply_overrides update musician data in the DB,
the static JSON must be regenerated for changes to reach the frontend.
musician_job.sh now calls deploy_with_main.sh at the end, matching
the pattern already used by event_job.sh.

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* fix: RFC 5545 line folding + robust UID fallback in iCal export

- foldLine(): fold lines exceeding 75 octets with CRLF+space per RFC 5545 §3.1;
  uses TextEncoder for accurate UTF-8 byte counting (Korean titles are 3 bytes/char)
- UID fallback: use datetime+title+venue_name composite instead of datetime alone
  to avoid collisions when two events share the same start time

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
