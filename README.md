# Seoul Underground Live - Static Site

This is a **static site** automatically deployed from the private crawler repository.

## Build Information

- **Build Time**: 2026-01-29T22:49:18Z
- **Source Commit**: [`208077577b8c100b07ee65f18abfc4c9d670df7b`](https://github.com/keunwoochoi/seoulunderground.live/commit/208077577b8c100b07ee65f18abfc4c9d670df7b)
- **Branch**: `main`
- **Workflow Run**: [View logs](https://github.com/keunwoochoi/seoulunderground.live/actions/runs/21497502368)

## Commit Details

- **Author**: Keunwoo Choi <gnuchoi+github@gmail.com>
- **Message**: feat: Add weekly highlighted shows feature (#82)

* feat: Add weekly highlighted shows feature

Implement a weekly highlighted show selection system that:
- Selects one featured event per day (Wed-Sun) on Monday
- Visually highlights events in frontend (card & table views)
- Enhances cover screenshot to preview highlighted event
- Uses bilingual i18n for all UI labels

Backend:
- Add event_select_weekly_highlights.py script with filtering logic
  - Filters by venue location (Seoul/Gyeonggi-do)
  - Filters by event time (18:00-22:00)
  - Prioritizes top 15 venues by event count
  - Random selection from eligible pool
- Add /api/highlights endpoint to serve weekly_highlights.json
- Save selections to data/{locality}/{genre}/weekly_highlights.json

Frontend:
- Add highlight translations (en/ko/de) to i18n
- Add gold highlight CSS variables to theme
- Update EventCard with gold border, badge, and tinted background
- Update EventTableView with gold left border and background tint
- Load highlights data and create isHighlighted() helper
- Create EnhancedCoverOverlay component with 3-section layout:
  - Top: undr.live logo + date
  - Middle: Featured event details or genre title fallback
  - Bottom: Footer text
- Pass isHighlighted prop to event components

Automation:
- Add highlight_job.sh shell script wrapper
- Add launchd plist for Monday 9:00 AM KST execution

Testing:
- Add comprehensive unit tests for selection logic
- Test week date calculations, venue filtering, event filtering

Features:
- Seoul-only for now (Germany not included)
- Graceful degradation if no highlights file exists
- Selection stability (fixed for the week after Monday selection)
- Bilingual throughout (ko/en/de support)

* fix: Address code review feedback for highlighted shows

Critical fixes:
- Add documentation to launchd plist about customizing paths
- Extract shared types (I18nField, HighlightInfo, HighlightsResponse) to frontend/src/types/highlights.ts
- Fix incorrect test dates (Feb 3 was Tuesday, not Monday)
- Replace print() with proper logging in api/app/crud.py and scripts/event_select_weekly_highlights.py

Changes:
1. config/launchd/com.seoulmusic.weekly_highlights.plist: Added XML comment with instructions for customizing paths
2. frontend/src/types/highlights.ts: New shared type definitions
3. frontend/src/App.tsx: Import and use shared types
4. frontend/src/components/EnhancedCoverOverlay.tsx: Import and use shared types
5. tests/etl/test_weekly_highlights.py: Corrected test dates (2026-02-02 is Monday, 2026-02-04 is Wednesday)
6. api/app/crud.py: Added logging module and replaced print with logger.error
7. scripts/event_select_weekly_highlights.py: Added logging configuration and replaced all print statements with logger calls

All tests passing.

* fix: Correct import path in EnhancedCoverOverlay (datetime -> timezone)

## Deployment

- **Live Site**: https://undr.live
- **GitHub Pages**: https://undr-live.github.io

## Data Snapshot

The static JSON files in `/api/` were exported from the local backend at build time.
Events shown are from the crawler's database as of the build timestamp above.

---

*This README is auto-generated during deployment. Do not edit manually.*
