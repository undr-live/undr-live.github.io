# Seoul Underground Live - Static Site

This is a **static site** automatically deployed from the private crawler repository.

## Build Information

- **Build Time**: 2026-03-18T22:14:30Z
- **Source Commit**: [`429b1d4240f826a70201b5493db2684c68e7aa7b`](https://github.com/keunwoochoi/seoulunderground.live/commit/429b1d4240f826a70201b5493db2684c68e7aa7b)
- **Branch**: `main`
- **Workflow Run**: [View logs](https://github.com/keunwoochoi/seoulunderground.live/actions/runs/23269642351)

## Commit Details

- **Author**: Keunwoo Choi <gnuchoi+github@gmail.com>
- **Message**: fix: venue context loading, Pydantic schemas, and silent-failure hardening (#106)

* feat: Pydantic schema as single source of truth for event extraction

Define EventExtractionResponse, ExtractedEvent, EventMusician, EventSet
as Pydantic models. to_prompt_str() auto-generates the SCHEMA block from
field definitions, replacing the hardcoded JSON schema string in extract.py.
_parse_llm_events() uses model_validate() so field renames are caught
immediately rather than silently producing null values (root cause of the
recent (untitled) event bug).

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* fix: add Pydantic models for venue and musician LLM responses

- Create etl/prompt/musicians/schema.py with AccountClassificationResponse model
- Create etl/prompt/venues/schema.py with VenueAnalysisResponse and related models
- Use model_validate() in classify_account.py to catch classification field drift
- Use model_validate() in venues_analyze.py to catch venue analysis field drift
- Replace {"raw": text} silent fallbacks with logged warnings + {} return
- Add status field to venue analyze state ("success"/"error") and use 1-day error
  cooldown so transient failures retry quickly (vs 7-day normal cooldown)

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* fix: add warning logging to silent exception handlers

- extract_core.py: _parse_llm_json now logs warning + returns {} instead of {"raw": text}
- events_extract.py: log meta.json read failures and venue context load failures
- base_fetcher.py: log profile snapshot index.json load failures
- import_events.py: use EventMusician.model_validate() when extracting IG handles;
  log ValidationError as warning and fall back to raw dict access
- import_musicians.py: call enr.get("name") once, assign to variable before isinstance check
- build_connections.py: add type annotation for shared_venues JSON parse and validate
  the parsed value is a list before constructing a set

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* fix: replace print() warnings with logger.warning() for centralized log management

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* fix: save Korean titles and normalize bilingual instrument field

- add_or_update_translations now builds {en, ko} dict from title_ko/title_en
  flat fields (new schema) when ann['title'] is None — fixes Korean mode
  showing English titles on frontend
- normalize instrument: {en, ko} dicts to plain string before EventMusician
  model_validate — silences spurious validation warnings from old event JSONs

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* fix: full ETL pipeline audit — subgenres, sets crash, age_limit, and schema gaps

- Add genres column to Event DB model + SQLite migration for subgenres data
- EventData.genres field maps LLM subgenres through import → DB → export
- import_events: extract ann['subgenres'] → EventData.genres; use _pick_bilingual
  for age_limit (was silently dropped when stored as {en, ko} dict)
- export_static_json: add genres to event export; replace bare json.loads(sets)
  with safe _parse_sets() helper (was an unhandled crash path)
- crud._to_event_schema: add genres field; replace bare json.loads(obj.sets) with
  safe _parse_sets_json() helper (same crash risk in API path)
- schemas.EventBase: add genres field
- CLAUDE.md: add working philosophy — fix the pipeline not the data; trace the
  full data path; full automation is the goal

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* docs: strengthen CLAUDE.md working philosophy with lessons from pipeline audit

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
