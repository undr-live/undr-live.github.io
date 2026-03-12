# Seoul Underground Live - Static Site

This is a **static site** automatically deployed from the private crawler repository.

## Build Information

- **Build Time**: 2026-03-12T02:26:15Z
- **Source Commit**: [`9e0858603feda9086af47fa9bb4c5bc003499d74`](https://github.com/keunwoochoi/seoulunderground.live/commit/9e0858603feda9086af47fa9bb4c5bc003499d74)
- **Branch**: `main`
- **Workflow Run**: [View logs](https://github.com/keunwoochoi/seoulunderground.live/actions/runs/22983778301)

## Commit Details

- **Author**: Keunwoo Choi <gnuchoi+github@gmail.com>
- **Message**: feat: event schema v2 + eval infrastructure (#99)

* feat: event schema v2 — date/sets/musicians + updated prompt

## Schema changes
- Replace datetime+show_time with date (YYYY-MM-DD) and sets (JSON array
  of {label, time}) to properly model multi-set shows (1부/2부)
- Add musicians as structured array {name_ko, name_en, instrument,
  ig_handle, role} replacing unstructured musicians_text field
- Log model_name in all Gemini result JSON files for traceability

## Prompt updates
- Updated event extraction prompt and JSON schema to reflect new fields
- Clarify multi-set rule: same band/lineup → one event with sets list;
  different bands → separate event records

## Pipeline & DB
- import_events.py handles new sets/musicians fields
- export_static_json.py correctly serializes sets (list or JSON string)
- DB migration: added date and sets columns (ALTER TABLE applied)
- annot_to_db.py: removed obsolete show_time field reference

## Frontend
- App.tsx renders sets array on event cards (time display)

## Config
- Add MODEL_EVENT, MODEL_VENUE constants (overridable via env vars)
  so model name is never hardcoded

Made-with: Cursor

* feat: eval infrastructure — ground truth labeler + golden dataset (187 cases)

## Eval manifest
- evals/manifest.json: 187 event cases (3 per venue, 64 venues) +
  71 venue cases for seoul/jazz
- evals/collect_baseline.py: gathers gemini-2.5-flash baseline results

## Ground Truth Labeler (evals/labeler/)
- FastAPI backend (server.py) serving cases with model output pre-filled
- Single-page frontend (static/index.html) for manual annotation:
  - Events: structured editors for sets (1부/2부), musicians
    (name_ko, name_en, instrument, ig_handle, role), subgenres
  - Venues: editable golden fields mirroring venue_analyzed.json schema
  - Hotkeys for fast navigation and annotation
  - Auto-sets is_event=true when saving events with golden data
  - ig_handle auto-prefixes "@" on save

## Golden dataset (data/golden/events/)
- 187 case directories, each with:
  - meta.json (post metadata + caption)
  - p*.jpg (post images, stored via Git LFS)
  - venue_context.json (venue snapshot used during prediction)
  - label.json (manual annotation, present for labeled cases)
- .gitattributes: configures Git LFS for data/golden/**/*.jpg
- .gitignore: added !data/golden/ exception

## One-off utility scripts
- scripts/collect_golden_data.py: copies source data into data/golden/
- scripts/backfill_model_name.py: backfills model_name into existing JSONs
- scripts/migrate_datetime_to_sets.py: migrates old datetime→date+sets

Made-with: Cursor

* fix: move golden dataset from data/golden/ to evals/golden/

The deploy workflow creates a symlink: ln -s .../data ./data
With data/golden/ tracked in git, checkout materializes data/ as a real
directory before ln -s runs, placing the symlink at data/data/ instead.
This broke the DB path (data/app.db not found).

Moving to evals/golden/ keeps the dataset clear of the symlink.
Also update .gitattributes LFS pattern and all path references.

Made-with: Cursor

* fix: restore _to_kst_hhmm as shim for test compatibility

_to_kst_hhmm was absorbed into _event_date_hhmm during schema v2 refactor,
breaking test imports. Add a thin wrapper so existing tests pass unchanged.

Made-with: Cursor

* test: add TestEventDateHhmm covering new date+sets primary path

The shim fix only kept legacy tests passing but left the new schema
(date + sets[]) with zero test coverage. Add TestEventDateHhmm to cover:
- date + single/multi set, first set's time used for folder name
- date with no sets / null time → hhmm is None
- fallback to legacy datetime ISO string when date is absent
- empty event dict

Made-with: Cursor

## Deployment

- **Live Site**: https://undr.live
- **GitHub Pages**: https://undr-live.github.io

## Data Snapshot

The static JSON files in `/api/` were exported from the local backend at build time.
Events shown are from the crawler's database as of the build timestamp above.

---

*This README is auto-generated during deployment. Do not edit manually.*
