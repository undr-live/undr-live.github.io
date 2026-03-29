# Seoul Underground Live - Static Site

This is a **static site** automatically deployed from the private crawler repository.

## Build Information

- **Build Time**: 2026-03-29T20:35:47Z
- **Source Commit**: [`338f1a1484ace8d761774a11fbf06af1655bce14`](https://github.com/keunwoochoi/seoulunderground.live/commit/338f1a1484ace8d761774a11fbf06af1655bce14)
- **Branch**: `main`
- **Workflow Run**: [View logs](https://github.com/keunwoochoi/seoulunderground.live/actions/runs/23718467070)

## Commit Details

- **Author**: Keunwoo Choi <gnuchoi+github@gmail.com>
- **Message**: feat: links section on musician profile page (phase 4) (#148)

* feat: prominent Instagram CTA button on musician profile page

Replace small @handle text link with a filled pill button "Instagram ↗"
plus muted @handle as secondary label alongside it.

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* fix: use plain text link style for Instagram CTA on musician profile

Match venue/event link pattern: plain colored text link + · separator
+ muted @handle. Remove the pill button which was off-brand.

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* revert: restore original @handle text link on musician profile

The pill button and text link variants were both worse.
Original monospace @handle link is cleaner.

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* feat: links section on musician profile page

Add a '링크' section below instruments showing all known links for the
musician. Currently shows Instagram (인스타그램/Instagram) from ig_handle.
Structured to grow: websites field maps youtube/soundcloud/spotify/bandcamp
to labeled links, unknown domains fall back to bare hostname.

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* fix: show handle in Instagram link label on musician profile

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* fix: display links as cards on musician profile, matching event panel style

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* refactor: use KNOWN_SITES map for website label lookup in links section

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
