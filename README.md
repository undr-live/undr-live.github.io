# Seoul Underground Live - Static Site

This is a **static site** automatically deployed from the private crawler repository.

## Build Information

- **Build Time**: 2026-03-30T13:23:26Z
- **Source Commit**: [`1dba0ccf9490438492be67551d89b84b7b897222`](https://github.com/keunwoochoi/seoulunderground.live/commit/1dba0ccf9490438492be67551d89b84b7b897222)
- **Branch**: `main`
- **Workflow Run**: [View logs](https://github.com/keunwoochoi/seoulunderground.live/actions/runs/23746912617)

## Commit Details

- **Author**: Keunwoo Choi <gnuchoi+github@gmail.com>
- **Message**: fix: add missing JSON-LD offers fields (Search Console) (#153)

* fix: disable musician highlight Slack notification

Feature is not ready for production — data quality (names, scores)
not yet reliable enough to surface publicly.

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* fix: disable musician highlight pipeline — feature not ready

Comment out musician_highlight_job.sh from weekly_job.sh.
Revert accidental select_highlight.py Slack change from previous commit.

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* fix: add missing JSON-LD offers fields for Google Search Console

Fixes 5 structured data warnings:
- price: parse free-text KRW string to number (e.g. "20,000원" → 20000; "무료" → 0)
- priceCurrency: always "KRW" (was omitted when no price)
- availability: always InStock
- validFrom: event startDate
- Remove conditional offers — always emit all fields

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* refactor: remove redundant isNaN check in parsePriceKRW

match[0] is always a digit string when match is non-null.

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
