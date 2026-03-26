# Seoul Underground Live - Static Site

This is a **static site** automatically deployed from the private crawler repository.

## Build Information

- **Build Time**: 2026-03-26T05:45:54Z
- **Source Commit**: [`ea8ceeb7574ef7d98132ee9691fe0ab250119c80`](https://github.com/keunwoochoi/seoulunderground.live/commit/ea8ceeb7574ef7d98132ee9691fe0ab250119c80)
- **Branch**: `main`
- **Workflow Run**: [View logs](https://github.com/keunwoochoi/seoulunderground.live/actions/runs/23579506069)

## Commit Details

- **Author**: Keunwoo Choi <gnuchoi+github@gmail.com>
- **Message**: fix: disable germany/jazz and serve Seoul lang routes with 200 (#133)

* fix: disable germany/jazz and create static files for Seoul lang routes

- config.py: set germany-jazz enabled=False so it's excluded from
  sitemap, JSON export, and SEO page generation
- deploy-pages.yml: after Vite build, copy dist/index.html to each
  /{locality}/{genre}/{lang}/index.html so GitHub Pages returns 200
  instead of 404 for SPA language routes that Google is trying to index

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* fix: remove germany venue enrich test (germany/jazz is now disabled)

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
