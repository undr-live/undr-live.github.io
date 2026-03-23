# Seoul Underground Live - Static Site

This is a **static site** automatically deployed from the private crawler repository.

## Build Information

- **Build Time**: 2026-03-23T00:32:22Z
- **Source Commit**: [`6db689c2f55cadbe56855ea29778994e94449f7d`](https://github.com/keunwoochoi/seoulunderground.live/commit/6db689c2f55cadbe56855ea29778994e94449f7d)
- **Branch**: `main`
- **Workflow Run**: [View logs](https://github.com/keunwoochoi/seoulunderground.live/actions/runs/23416307869)

## Commit Details

- **Author**: Keunwoo Choi <gnuchoi+github@gmail.com>
- **Message**: feat: show performer instruments in event card (#124)

* feat: show performer instruments in event cards

Add instruments field to musicians_inline in export_static_json.py so
per-musician instrument data flows through to the frontend. Update
EventMusicianSummary type in EventCard.tsx and App.tsx, and render
instruments in parentheses after each performer name in event cards.

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* fix: use i18n for musicians/featuring label in EventCard

Hardcoded 'Musicians'/'Featuring' strings were showing in English
regardless of the active language. Now routes through t(lang, key).

Added musicians/featuring keys to en/ko/de in i18n.ts.
Added rule to CLAUDE.md: all UI labels must respect the active language.

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* fix: use 연주자 instead of 뮤지션 for Korean musicians label

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* feat: translate instrument names to Korean and German

Added translateInstrument() to i18n.ts with translations for all 15
instruments currently in the DB (bass, piano, drums, trumpet, saxophone,
guitar, vocals, keyboard, violin, flute, trombone, vibraphone, percussion,
composer, conductor).

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* fix: prefer name_ko on Korean page when displaying musician names

Was always picking name_en first regardless of lang.

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* fix: musician profile link uses current lang instead of hardcoded 'en'

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* fix: filter empty strings from instruments split; deduplicate EventMusicianSummary type

- export_static_json: filter empty strings after split/strip (review suggestion)
- App.tsx: import EventMusicianSummary from EventCard instead of duplicating the type

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
