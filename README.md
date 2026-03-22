# Seoul Underground Live - Static Site

This is a **static site** automatically deployed from the private crawler repository.

## Build Information

- **Build Time**: 2026-03-22T19:53:13Z
- **Source Commit**: [`5ab8b5ffa8f96e01d0a4f7de4459feb0904ddda8`](https://github.com/keunwoochoi/seoulunderground.live/commit/5ab8b5ffa8f96e01d0a4f7de4459feb0904ddda8)
- **Branch**: `main`
- **Workflow Run**: [View logs](https://github.com/keunwoochoi/seoulunderground.live/actions/runs/23411147470)

## Commit Details

- **Author**: Keunwoo Choi <gnuchoi+github@gmail.com>
- **Message**: feat: human-readable filter pills + group-by toggle (PR A) (#122)

* feat: human-readable filter pills, group-by toggle, fix musician_ig_handles crash

- Replace D+0/D+1/W+0/W+1 pills with Today/Tomorrow/This week/Next week labels
- Add group-by toggle (date ↔ venue) in card view, URL param ?group=venue
- Two-row filter bar: pills on row 1, group-by right-aligned on row 2 (mobile-friendly)
- API: parse musician_ig_handles JSON string → list[str] in crud._to_event_schema
- Schema: EventBase.musician_ig_handles str|None → list[str]|None
- EventCard: defensive normalization in case of stale cached string value
- Header: fix missing key prop on language switcher fragment
- timezone.ts: add WEEKDAYS, formatShortDate, formatShortDateWithDay, formatShortDateRange
- i18n: add group_by_date, group_by_venue, unknown_venue for en/ko/de

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* feat: default filter to today, move all-events dot pill to end

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* feat: sort group-by-venue by tier then event count (same as 공연장 tab)

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* fix: always show group-by toggle regardless of view mode

Was hidden in table view, so desktop users with saved table preference
couldn't see it.

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* fix: capitalize Today in English i18n

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* fix: sanitize musician_ig_handles list elements consistently

Apply same str(h)/if h filtering to the already-a-list path as the
JSON-parsed path, per code review suggestion.

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* feat: single-row filter bar, de-emphasize search input

- Merge filter pills + group-by into one row (group-by right-aligned)
- Shrink search input: smaller padding, secondary text color, font-size 12

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* fix: auto-switch to card view when group-by-venue is selected

In table view clicking 공연장별 set the URL param but the venue-grouped
render was gated behind viewMode === 'card', so nothing changed visually.

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
