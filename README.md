# Seoul Underground Live - Static Site

This is a **static site** automatically deployed from the private crawler repository.

## Build Information

- **Build Time**: 2026-01-31T00:51:47Z
- **Source Commit**: [`928151d374ef8ee7728992d366e6e75b3b0fc2b4`](https://github.com/keunwoochoi/seoulunderground.live/commit/928151d374ef8ee7728992d366e6e75b3b0fc2b4)
- **Branch**: `main`
- **Workflow Run**: [View logs](https://github.com/keunwoochoi/seoulunderground.live/actions/runs/21535789413)

## Commit Details

- **Author**: Keunwoo Choi <gnuchoi+github@gmail.com>
- **Message**: refactor: Restructure event extraction prompt for clarity (v3.1.0) (#83)

* refactor: Restructure event extraction prompt for clarity (v3.1.0)

Consolidate PartialPrompts and improve prompt structure without changing
functionality. Version bump to 3.1.0 with safeguard to prevent re-extraction.

Changes:
- Consolidated 7 genre-specific partials into 3 (core/rules/examples)
- Simplified timezone instructions
- Reduced redundancy in template
- Added version equivalence logic (3.0.3 → 3.1.0 treated as equivalent)
- Created comprehensive unit tests

Files:
- etl/prompt/events/extract.py: Restructured partials and template
- etl/prompt/events/extract_v3.0.3_backup.py: Backup of original
- etl/prompt/templates.py: Added 3.0.3→3.1.0 equivalence logic
- tests/etl/gemini/test_event_extraction_prompt.py: New test suite

Impact:
- NO re-extraction triggered (version equivalence safeguard)
- Logically equivalent to v3.0.3
- All tests pass (12/12)
- Prompts render successfully for all locality/genre combinations

* chore: Keep v3.0.3 backup locally only (not in git history)

* chore: Remove temporary transition scaffolding

- Remove temporary test file (test_event_extraction_prompt.py)
- Remove 3.0.3 → 3.1.0 special case logic from templates.py
- Update existing tests to use v3.1.0 consolidated partials
- All 18 tests in test_genre_aware_prompts.py passing

The v3.1.0 refactoring is now the standard, no need for
temporary transition support.

## Deployment

- **Live Site**: https://undr.live
- **GitHub Pages**: https://undr-live.github.io

## Data Snapshot

The static JSON files in `/api/` were exported from the local backend at build time.
Events shown are from the crawler's database as of the build timestamp above.

---

*This README is auto-generated during deployment. Do not edit manually.*
