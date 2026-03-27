# Seoul Underground Live - Static Site

This is a **static site** automatically deployed from the private crawler repository.

## Build Information

- **Build Time**: 2026-03-27T04:02:34Z
- **Source Commit**: [`d1b0a44cb0092e0d3724053c6dd20499e16577cb`](https://github.com/keunwoochoi/seoulunderground.live/commit/d1b0a44cb0092e0d3724053c6dd20499e16577cb)
- **Branch**: `main`
- **Workflow Run**: [View logs](https://github.com/keunwoochoi/seoulunderground.live/actions/runs/23630411245)

## Commit Details

- **Author**: Keunwoo Choi <gnuchoi+github@gmail.com>
- **Message**: fix: unknown event time — '—' display, image retry, safer IG delays (#137)

* fix: unknown event time — display '—', retry image fetch, safer delays

ETL:
- Retry image fetch for posts saved without images (files=None): on next
  run, posts with metadata but no files will re-attempt web.post() detail
  fetch instead of being skipped — auto-backfill once session is restored
- Add DOWNLOAD_DELAY pause before web.post() detail fetch (was missing)
- Bump post delay default 1-3s → 2-5s; download delay 0.5-1.5s → 1.5-3.5s

Frontend:
- formatSets() now returns null when no set time is known (was falling
  back to datetime field, which is midnight sentinel — not a real time)
- EventCard and EventTableView show '—' when displayTime is null,
  instead of the raw ISO datetime string or a misleading "12:00 AM"

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* chore: bump IG delays, upgrade moviepy to 2.x, install ensta from GitHub

- IG delays significantly increased (safe_mult 1.8→2.0; handle 8-18s,
  post 4-9s, download 3-7s) to reduce ban risk
- moviepy upgraded 1.0.3→2.2.1 (required by latest ensta from GitHub)
- ensta reinstalled from GitHub HEAD (88ed256) — same version 5.2.9 but
  with latest fixes

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* fix: corrupted metadata handling, pin ensta to GitHub for moviepy 2.x compat

- Wrap meta.json read in try/except (json.JSONDecodeError, AttributeError)
  and add isinstance(dict) check per code review
- Pin ensta to GitHub source in pyproject.toml so CI gets the same version
  as local (PyPI 5.2.9 uses moviepy.editor, GitHub HEAD uses moviepy 2.x)

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* feat: Slack alert when IG web auth fails (session blocked)

Sends send_error('IG Auth Blocked', ...) via SlackNotifier when
Web(username, password) raises — the clearest signal that Instagram
has blocked the session and image fetching is down.

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* fix: use venue typical_show_times as fallback when post has no time

- Events prompt: allow typical_show_times (venue's own advertised schedule)
  as fallback when the post itself contains no time info
- Venues prompt: require 24h HH:MM format for typical_show_times, never AM/PM
- Also converted all existing venue JSON data to HH:MM format (local only,
  gitignored) — fixes africa_since1988 (8PM→20:00), blueming_jazz,
  eulji_libro, houseofbrown.seoul, jazzclub_evans, rustic_jazz, seobs_bar,
  sounddog_jazz, dido_jazz_lounge (46 values across 17 files)

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
