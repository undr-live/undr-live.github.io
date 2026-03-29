# Seoul Underground Live - Static Site

This is a **static site** automatically deployed from the private crawler repository.

## Build Information

- **Build Time**: 2026-03-29T17:53:48Z
- **Source Commit**: [`ff031d05f30189b3e6929270bf7ae502c82cff3d`](https://github.com/keunwoochoi/seoulunderground.live/commit/ff031d05f30189b3e6929270bf7ae502c82cff3d)
- **Branch**: `main`
- **Workflow Run**: [View logs](https://github.com/keunwoochoi/seoulunderground.live/actions/runs/23715266545)

## Commit Details

- **Author**: Keunwoo Choi <gnuchoi+github@gmail.com>
- **Message**: feat: musician connection export + profile sections (phase 2) (#147)

* feat: musician connection export + profile sections (phase 2)

- export_static_json.py: add export_musician_connections() — top-5 venues
  and top-5 co-musicians per musician written to connections.json; call it
  in run_export_static_json() for each locality/genre
- App.tsx: add MusicianConnections type; add /api/connections static route
- MusicianList: fetch connections; show venue count badge on each card
- MusicianProfile: fetch connections; add "Venues" section (top venues,
  clickable → events tab filtered by venue) and "Musicians" section
  (top co-musicians, clickable → their profile); fix hardcoded Back button
  to use t(lang, 'back') and navigate back to /musicians list

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* fix: remove venue count badge from musician cards; fix venue nav on profile

- Remove "N venues" badge from musician list cards (was confusing)
- Venue links on musician profile now navigate to ?tab=venues&q=handle
  so the user lands on the venues tab with that venue pre-filtered,
  instead of the broken ?venue= param that showed all events

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* fix: venue links always show all events (add &all=1)

- Musician profile venue links: navigate to ?q=handle&all=1
- VenueCard '공연일정 보기': add &all=1 so all future events shown,
  not just this week's default

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* fix: venue nav → venues tab; fade upcoming date badge by days away

- Musician profile venue links now navigate to ?tab=venues&q=handle
  (was going to events tab)
- Upcoming show badge on musician cards fades based on days until show:
  today/tomorrow=100%, 2-3d=80%, 4-7d=65%, 8-14d=50%, 15+d=35%

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
