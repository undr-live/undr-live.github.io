# Seoul Underground Live - Static Site

This is a **static site** automatically deployed from the private crawler repository.

## Build Information

- **Build Time**: 2026-03-16T18:36:13Z
- **Source Commit**: [`acd27e2b2e859bb0ae3780f5c9ce96c751a6fd28`](https://github.com/keunwoochoi/seoulunderground.live/commit/acd27e2b2e859bb0ae3780f5c9ce96c751a6fd28)
- **Branch**: `main`
- **Workflow Run**: [View logs](https://github.com/keunwoochoi/seoulunderground.live/actions/runs/23159880873)

## Commit Details

- **Author**: Keunwoo Choi <gnuchoi+github@gmail.com>
- **Message**: feat: musician pipeline phase 2 — crawling efficiency, event linking, musician pages (#102)

Squash of feat/musician-pipeline-phase2:

- Fix link_events silent syntax failure (broke every daily run)
- musicians_fetch: separate profile/posts cooldowns + score-based re-fetch intervals
- classify_local: priority-sorted queue (yield 1/200 → 87/200) + prompt version tracking
- seed_own_account: one-time registry seeding from own IG account
- musician_job.sh: CLASSIFY_LIMIT 20→200, hourly launchd for scale-up sprint
- Frontend: musician list + profile pages, typedLang reactivity fix
- Gemini review fixes: dead code, regex, unused imports

## Deployment

- **Live Site**: https://undr.live
- **GitHub Pages**: https://undr-live.github.io

## Data Snapshot

The static JSON files in `/api/` were exported from the local backend at build time.
Events shown are from the crawler's database as of the build timestamp above.

---

*This README is auto-generated during deployment. Do not edit manually.*
