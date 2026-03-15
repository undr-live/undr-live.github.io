# Seoul Underground Live - Static Site

This is a **static site** automatically deployed from the private crawler repository.

## Build Information

- **Build Time**: 2026-03-15T23:10:49Z
- **Source Commit**: [`814891fc1a6bb9fd5a2a06bd6834dfdebe2b1cdd`](https://github.com/keunwoochoi/seoulunderground.live/commit/814891fc1a6bb9fd5a2a06bd6834dfdebe2b1cdd)
- **Branch**: `main`
- **Workflow Run**: [View logs](https://github.com/keunwoochoi/seoulunderground.live/actions/runs/23121503778)

## Commit Details

- **Author**: Keunwoo Choi <gnuchoi+github@gmail.com>
- **Message**: feat: musician pipeline phase 2 — event linking, musician pages, crawling improvements (#102)

## Musician pipeline completions

**link_events** (new): links Event rows to Musician DB records via three paths —
IG handle exact match, fuzzy name match from descriptions, and leader-name
extraction from group titles (e.g. "X Trio"). Also upserts all encountered raw
names into EntityNameIndex for future discovery. Was silently failing on every
pipeline run due to Unicode typographic characters in the module docstring; fixed.

**extract_instruments** (new): keyword + emoji pass over IG bio text to populate
Musician.instruments. Updated 68/128 musicians on first run.

**seed_own_account** (new): seeds the fetch registry with high-priority handles
from the project's own IG account — post @mentions (priority 9) and followers
(priority 8). Runs as Step 1b in the daily musician pipeline.

**scan_venue_mentions** (new): scans musician post captions for venue @handle
and display-name mentions, producing caption_mention counts for the two-way
musician-venue connection handshake.

**apply_overrides** (new): applies human-curated corrections from
musician_overrides.json after all automated steps. Runs last so manual
judgment always wins.

## Crawling improvements (musicians_fetch)

- Separate cooldowns: profile_fetch_until (7d) vs posts_fetch_until (14d) tracked
  independently so profiles can refresh without re-fetching posts
- Stale bypass: handles not seen in >60 days skip the policy gate and are
  force-fetched, rescuing 69 previously stuck handles
- MUS_FETCH_MAX raised to 80 for initial scale-up phase (discovery queue:
  ~1,300 pending handles, ~550 expected promotions -> ~678 total musicians)

## Frontend: musician pages

- /seoul/jazz/en/musicians — list with search, IG-style cards showing name_irl,
  @handle, instruments, name_en/ko, qwen confidence
- /seoul/jazz/en/musicians/:handle — profile page with upcoming shows
- Event cards now show linked musician real names as internal links to profile pages

## Data export

export_static_json: events include inline musicians array
{id, ig_handle, name_ko, name_en, name_irl}; musicians export adds
name_ko, name_en, other_names, qwen_score, instruments

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

## Deployment

- **Live Site**: https://undr.live
- **GitHub Pages**: https://undr-live.github.io

## Data Snapshot

The static JSON files in `/api/` were exported from the local backend at build time.
Events shown are from the crawler's database as of the build timestamp above.

---

*This README is auto-generated during deployment. Do not edit manually.*
