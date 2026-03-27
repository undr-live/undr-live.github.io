# Seoul Underground Live - Static Site

This is a **static site** automatically deployed from the private crawler repository.

## Build Information

- **Build Time**: 2026-03-27T14:19:23Z
- **Source Commit**: [`a29aa999c8fd59f175fff65c7a2cbff5f84a0452`](https://github.com/keunwoochoi/seoulunderground.live/commit/a29aa999c8fd59f175fff65c7a2cbff5f84a0452)
- **Branch**: `main`
- **Workflow Run**: [View logs](https://github.com/keunwoochoi/seoulunderground.live/actions/runs/23650677425)

## Commit Details

- **Author**: Keunwoo Choi <gnuchoi+github@gmail.com>
- **Message**: fix: add missing JSON-LD fields for Google Search Console warnings (#142)

Adds all 6 missing fields to MusicEvent schema:
- endDate: same as startDate (best available — no end time in data)
- eventStatus: EventScheduled (always true for upcoming events)
- image: og-image.png fallback (no per-event images available)
- offers: price + ticket_link if available, else source URL
- performer: omit field entirely when empty (was [])
- description: already present, was already omitted when null

Co-authored-by: Claude Sonnet 4.6 <noreply@anthropic.com>

## Deployment

- **Live Site**: https://undr.live
- **GitHub Pages**: https://undr-live.github.io

## Data Snapshot

The static JSON files in `/api/` were exported from the local backend at build time.
Events shown are from the crawler's database as of the build timestamp above.

---

*This README is auto-generated during deployment. Do not edit manually.*
