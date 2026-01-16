# Seoul Underground Live - Static Site

This is a **static site** automatically deployed from the private crawler repository.

## Build Information

- **Build Time**: 2026-01-16T20:55:42Z
- **Source Commit**: [`d1997184a8aefc2a322887a705a9542984615ee0`](https://github.com/keunwoochoi/seoulunderground.live/commit/d1997184a8aefc2a322887a705a9542984615ee0)
- **Branch**: `main`
- **Workflow Run**: [View logs](https://github.com/keunwoochoi/seoulunderground.live/actions/runs/21080559182)

## Commit Details

- **Author**: Keunwoo Choi <gnuchoi+github@gmail.com>
- **Message**: chore: remove legacy iPhone mirroring code (#71)

* chore: remove legacy iPhone mirroring code

Removed deprecated iPhone mirroring + Ollama vision automation:
- etl/ig/iphone_mirror_controller.py
- etl/ig/ollama_vision.py
- etl/ig/upload_instagram_post.py
- etl/ig/repost_as_story.py
- config/launchd/com.seoulmusic.upload_post.plist
- config/launchd/com.seoulmusic.repost_story.plist
- Various INSTAGRAM_*.md documentation files

Kept all Meta Graph API posting code and iCloud sync.

* fix: address code review issues

CRITICAL:
- Remove .env.bak with secrets from git (add *.bak and .env* to .gitignore)
- Fix bash syntax error: else: → else in upload_post_job.sh

Medium:
- Handle bytes in subprocess_utils.py (decode before logging)
- Remove stderr suppression in deploy_daily_images.sh for better debugging
- Fix sync_venue_manual_info.py to use proper JSONL format (line-by-line)

* no need to include backfill script

## Deployment

- **Live Site**: https://undr.live
- **GitHub Pages**: https://undr-live.github.io

## Data Snapshot

The static JSON files in `/api/` were exported from the local backend at build time.
Events shown are from the crawler's database as of the build timestamp above.

---

*This README is auto-generated during deployment. Do not edit manually.*
