# Seoul Underground Live - Static Site

This is a **static site** automatically deployed from the private crawler repository.

## Build Information

- **Build Time**: 2026-03-18T00:13:11Z
- **Source Commit**: [`a16556386f02b2fb6f00fde554a86f6c57ccf518`](https://github.com/keunwoochoi/seoulunderground.live/commit/a16556386f02b2fb6f00fde554a86f6c57ccf518)
- **Branch**: `main`
- **Workflow Run**: [View logs](https://github.com/keunwoochoi/seoulunderground.live/actions/runs/23222535541)

## Commit Details

- **Author**: Keunwoo Choi <gnuchoi+github@gmail.com>
- **Message**: fix: embed highlight in cover URL to avoid async race condition (#105)

* fix: embed highlight in cover URL to avoid async race condition

The cover overlay reads highlights via an async useEffect fetch. When
the screenshot is taken right after networkidle fires (especially on
cached page loads), the fetch may not have completed yet, leaving
highlights={} and showing the genre title fallback instead of the
featured event.

Fix: read weekly_highlights.json locally before navigating, then pass
test_date + test_highlight as URL params for scr_idx=0. App.tsx already
reads these synchronously from the URL, bypassing the async fetch
entirely.

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* fix: title extraction, set labels, iCloud sync, and highlight URL params

- events_extract.py: store title_ko/title_en from v4.0.x LLM response
  instead of legacy title field (which was always null); fix has_musician
  check to use name_ko/name_en; fix is_title_empty to handle all schema variants
- screenshot_table_view.py: pass today_kst as arg to get_today_highlight
  instead of recalculating inside; refactor to avoid redundant date calc
- ig_story_notify.py: remove icloud_sync step and its Slack notification
- App.tsx: fix formatSets to return primary time only (no label) for time
  column and showTime comparison; add formatSetSchedule for labeled sets
- EventTableView.tsx: render setSchedule as secondary text below title

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
