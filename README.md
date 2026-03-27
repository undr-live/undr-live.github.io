# Seoul Underground Live - Static Site

This is a **static site** automatically deployed from the private crawler repository.

## Build Information

- **Build Time**: 2026-03-27T20:37:10Z
- **Source Commit**: [`11ce757501e34c035c427ca9b68f0ec8d0f744bb`](https://github.com/keunwoochoi/seoulunderground.live/commit/11ce757501e34c035c427ca9b68f0ec8d0f744bb)
- **Branch**: `main`
- **Workflow Run**: [View logs](https://github.com/keunwoochoi/seoulunderground.live/actions/runs/23666387425)

## Commit Details

- **Author**: Keunwoo Choi <gnuchoi+github@gmail.com>
- **Message**: fix: switch map to CartoDB Voyager for all languages (#143)

* fix: switch map to CartoDB Voyager for all languages

Replaces noisy OSM standard tiles (used for Korean) with CartoDB Voyager
across all languages. Voyager shows Seoul subway lines natively, has
Korean labels, and is visually much cleaner. Map no longer reinitializes
on language switch since tiles are now language-independent.

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* feat: add Naver map + website links to venue map popup

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* fix: update stale comments in VenueMap after tile unification

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
