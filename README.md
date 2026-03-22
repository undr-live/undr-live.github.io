# Seoul Underground Live - Static Site

This is a **static site** automatically deployed from the private crawler repository.

## Build Information

- **Build Time**: 2026-03-22T01:15:45Z
- **Source Commit**: [`da2757cf9f1a72853ac9b4808f9b44f3562cbec3`](https://github.com/keunwoochoi/seoulunderground.live/commit/da2757cf9f1a72853ac9b4808f9b44f3562cbec3)
- **Branch**: `main`
- **Workflow Run**: [View logs](https://github.com/keunwoochoi/seoulunderground.live/actions/runs/23392821571)

## Commit Details

- **Author**: Keunwoo Choi <gnuchoi+github@gmail.com>
- **Message**: chore: move actions-gh-pages temp dirs to ~/github_actions after each deploy (#118)

peaceiris/actions-gh-pages creates actions_github_pages_* dirs in $HOME
with no config option to change the location. This step moves them to
~/github_actions/ after every deploy run (even on failure).

Co-authored-by: Claude Sonnet 4.6 <noreply@anthropic.com>

## Deployment

- **Live Site**: https://undr.live
- **GitHub Pages**: https://undr-live.github.io

## Data Snapshot

The static JSON files in `/api/` were exported from the local backend at build time.
Events shown are from the crawler's database as of the build timestamp above.

---

*This README is auto-generated during deployment. Do not edit manually.*
