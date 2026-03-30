# Seoul Underground Live - Static Site

This is a **static site** automatically deployed from the private crawler repository.

## Build Information

- **Build Time**: 2026-03-30T00:21:20Z
- **Source Commit**: [`cb845f04b31fb7f95a21e566ecd0049a5fb2e26f`](https://github.com/keunwoochoi/seoulunderground.live/commit/cb845f04b31fb7f95a21e566ecd0049a5fb2e26f)
- **Branch**: `main`
- **Workflow Run**: [View logs](https://github.com/keunwoochoi/seoulunderground.live/actions/runs/23722615037)

## Commit Details

- **Author**: Keunwoo Choi <gnuchoi+github@gmail.com>
- **Message**: feat: extract YouTube channel links from musician bios (step 5c) (#149)

* feat: extract YouTube channel links from musician bios (step 5c)

- New etl/musicians/fetch_links.py: reads biography_links from
  profile/latest.json, extracts YouTube channel URLs (not video URLs),
  resolves Linktree pages via HTTP GET with 30-day disk cache,
  writes results to Link table
- export_static_json.py: export_musicians() now reads Link table to
  populate websites field (was always empty before)
- musician_job.sh: add step 5c after extract_instruments

Result: 131 of 814 seoul/jazz musicians now have YouTube channel links
in the exported JSON, rendered as "YouTube" cards in the 링크 section.

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* fix: parse Linktree __NEXT_DATA__ JSON for social button URLs

Linktree social buttons (YouTube channel etc.) are not in <a> tags —
they live in the Next.js __NEXT_DATA__ script block. Add a regex pass
over the embedded JSON before the <a> tag fallback.

Catches woonjo_'s @John-eh9xe YouTube channel which was previously missed.

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* refactor: links.json cache + code review fixes

- links.json per musician replaces linktree_resolved.json:
  structured with {updated_at, links: [{kind, url, source, via?}],
  linktree_fetched_at: {url: timestamp}}
- Fix N+1: batch-fetch all existing YouTube Link rows before musician loop
- export_static_json: select only (entity_id, url) columns from Link table
- Specific exceptions: json.JSONDecodeError/OSError/RequestException
  instead of broad Exception
- dict.fromkeys() for deduplication in _fetch_linktree_youtube_urls

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* refactor: traverse __NEXT_DATA__ JSON object instead of regex on string

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
