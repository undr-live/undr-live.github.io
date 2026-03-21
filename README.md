# Seoul Underground Live - Static Site

This is a **static site** automatically deployed from the private crawler repository.

## Build Information

- **Build Time**: 2026-03-21T21:18:36Z
- **Source Commit**: [`bb1141af9668210083c6a912878af1b9e38a2fb0`](https://github.com/keunwoochoi/seoulunderground.live/commit/bb1141af9668210083c6a912878af1b9e38a2fb0)
- **Branch**: `main`
- **Workflow Run**: [View logs](https://github.com/keunwoochoi/seoulunderground.live/actions/runs/23388990345)

## Commit Details

- **Author**: Keunwoo Choi <gnuchoi+github@gmail.com>
- **Message**: fix: ensure Instagram footer is always visible in screenshot pages (#115)

* fix: ensure Instagram footer is always visible in screenshot pages

Rows with 1부/2부 set schedules are taller than single-set rows,
pushing the footer below the viewport crop window. Fix:

1. Add data-ig-footer attribute to InstagramFooter for reliable
   Playwright targeting.
2. Before taking screenshots, probe page 1 and measure whether the
   footer is within the viewport. If clipped, reduce epp by 1 and
   re-probe until it fits (min epp: 5).

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* fix: probe all pages for footer visibility, not just page 1

Reducing epp reshuffles which events land on which page, so a
single page-1 probe is insufficient — later pages may still clip
the footer. Now probes pages 1..N in order; if any clips, reduces
epp by 1 and restarts the probe from page 1.

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* fix: probe at EVENTS_PER_PAGE_MIN before giving up on footer visibility

The previous loop reduced epp then re-checked, meaning EVENTS_PER_PAGE_MIN
was never actually probed. Now uses while True — check first, then either
break (fits), give up at min epp with a warning, or reduce and retry.

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* fix: per-page adaptive event count to keep footer visible in screenshots

Each story page now independently probes from 7 down to 3 events to find
the maximum count that keeps the @undr.live footer within the 593px crop
boundary. This preserves 1부/2부 set detail while ensuring the footer is
never clipped, regardless of row height variation across pages.

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
