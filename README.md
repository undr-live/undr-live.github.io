# Seoul Underground Live - Static Site

This is a **static site** automatically deployed from the private crawler repository.

## Build Information

- **Build Time**: 2026-01-14T15:34:55Z
- **Source Commit**: [`38a5f981eb62ae9f08e59f4e3a45617047b816d9`](https://github.com/keunwoochoi/seoulunderground.live/commit/38a5f981eb62ae9f08e59f4e3a45617047b816d9)
- **Branch**: `main`
- **Workflow Run**: [View logs](https://github.com/keunwoochoi/seoulunderground.live/actions/runs/20999843766)

## Commit Details

- **Author**: Keunwoo Choi <gnuchoi+github@gmail.com>
- **Message**: Focus on Seoul/jazz only: disable Germany/jazz ETL and frontend (#66)

- Comment out Germany/jazz sections in event_job.sh and venue_job.sh
- Remove 'germany' from SUPPORTED_LOCALITIES in frontend
- Keep all Germany data and code intact for future reactivation
- Immediate cost savings by stopping Germany ETL pipeline

## Deployment

- **Live Site**: https://undr.live
- **GitHub Pages**: https://undr-live.github.io

## Data Snapshot

The static JSON files in `/api/` were exported from the local backend at build time.
Events shown are from the crawler's database as of the build timestamp above.

---

*This README is auto-generated during deployment. Do not edit manually.*
