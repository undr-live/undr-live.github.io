# Seoul Underground Live - Static Site

This is a **static site** automatically deployed from the private crawler repository.

## Build Information

- **Build Time**: 2026-03-26T22:39:19Z
- **Source Commit**: [`a43a96abc8cab6c192f32343b30ece4ed0764f18`](https://github.com/keunwoochoi/seoulunderground.live/commit/a43a96abc8cab6c192f32343b30ece4ed0764f18)
- **Branch**: `main`
- **Workflow Run**: [View logs](https://github.com/keunwoochoi/seoulunderground.live/actions/runs/23621472466)

## Commit Details

- **Author**: Keunwoo Choi <gnuchoi+github@gmail.com>
- **Message**: feat: filter fixes, layout swap, GA tracking (#136)

* feat: filter fixes, layout swap, GA tracking

- Fix 'this week'/'next week' overlap: endOfWeekFrom now ends on Sunday (Mon–Sun week)
- Fix 'all' filter URL param: encode as all=1 so urlParamsToFilter can distinguish it from default
- Fix GA ID: was G-3E3NPW57WD, now matches index.html (G-6T1KPG2K45)
- Move view/map toggle buttons left of search bar
- Add trackEvent helper and GA4 event tracking on: filter pills, group-by toggle, view mode buttons, search

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* fix: update endOfWeekFrom JSDoc to reflect Mon-Sun week

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* fix: update timezone tests for Mon-Sun week; add local test rule to CLAUDE.md

Tests were written for old Sun-Sat week definition. Updated to reflect
Mon-Sun week (Sunday = end of week) and added year-boundary case.

Also added rule to CLAUDE.md: run tests locally before pushing.

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* feat: invert map button color when active

When the venue map panel is open, the map toggle button now shows
a light background with dark icon (inverted) for clear visual feedback.

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* feat: collapsible search bar — icon-only by default, expands on click

- Default: shows magnifier icon only
- Click/tap: expands with animated width + border + placeholder text
- Click outside (with empty input): collapses back to icon
- Escape: clears query and collapses
- If URL has ?q=...: opens pre-expanded with query

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* fix: smooth search bar animation, stable height, no focus ring

- Input always in DOM; width 26→200 via cubic-bezier transition (no pop-in)
- Input fades in via opacity transition, slightly delayed after width starts
- Fixed height 26px matches button group — zero layout shift when opening
- Removed border from active state; background change alone signals active
- outline:none + border:none on input removes browser focus ring (the reddish glow)
- tabIndex=-1 when closed to prevent accidental keyboard focus

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
