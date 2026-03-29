# Seoul Underground Live - Static Site

This is a **static site** automatically deployed from the private crawler repository.

## Build Information

- **Build Time**: 2026-03-29T06:45:41Z
- **Source Commit**: [`7ea1bddb88d8a464191b48ba51ee871493074b30`](https://github.com/keunwoochoi/seoulunderground.live/commit/7ea1bddb88d8a464191b48ba51ee871493074b30)
- **Branch**: `main`
- **Workflow Run**: [View logs](https://github.com/keunwoochoi/seoulunderground.live/actions/runs/23703401251)

## Commit Details

- **Author**: Keunwoo Choi <gnuchoi+github@gmail.com>
- **Message**: feat: musician list 2D grid with upcoming show info and filters (#146)

* feat: musician list 2D grid with upcoming show info and filters

- Replace 1-column list with responsive 2-column grid (minmax 160px)
- Remove confidence score display
- Add instrument filter chips (composer, piano, bass, vocals, drums, sax, guitar)
- Add "playing soon" toggle to filter to musicians with upcoming shows
- Show next show date/time/venue on each card (e.g. "● 오늘 8pm · Oleo Jazz Pub")
- Sort: upcoming-first by soonest show, then completeness, show count, alpha
- Mute @handle to text-secondary; all labels i18n'd

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* refactor: address code review feedback on MusicianList

- Use shiftDate() for tomorrow calculation instead of manual date math
- Extract processMusicianData() as a standalone pure function (testable)
- Simplify filter: remove IIFE, compute needle once outside the boolean

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* fix: collapsible inline search, consistent toggle chip style

- Move search bar into chips row as collapsible icon widget (after guitar)
- Same expand/collapse animation as events/venues search
- Fix playing soon chip: inactive now uses var(--text-secondary) not var(--link)

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* fix: instrument chips toggle off when clicked again

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
