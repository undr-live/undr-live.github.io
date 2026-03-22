# Seoul Underground Live - Static Site

This is a **static site** automatically deployed from the private crawler repository.

## Build Information

- **Build Time**: 2026-03-22T04:39:56Z
- **Source Commit**: [`f101763985192b3c88c174bb38a64bd359f88b07`](https://github.com/keunwoochoi/seoulunderground.live/commit/f101763985192b3c88c174bb38a64bd359f88b07)
- **Branch**: `main`
- **Workflow Run**: [View logs](https://github.com/keunwoochoi/seoulunderground.live/actions/runs/23395782310)

## Commit Details

- **Author**: Keunwoo Choi <gnuchoi+github@gmail.com>
- **Message**: refactor: remove hardcoded paths and inline config values (#119)

* refactor: remove hardcoded paths and inline config values

1. deploy-pages.yml: replace /Users/keunwoo/... with $DEV_WORKSPACE
   (configurable via GitHub Actions variable, defaults to $HOME/Codes/seoul.music)
   and $HOME for the github_actions temp dir sweep.

2. launchd plists: replace /Users/keunwoo/... with __PROJECT_DIR__ and
   __HOME_DIR__ placeholders. Add config/launchd/install.sh to stamp in
   real paths and load into ~/Library/LaunchAgents/ on any machine.

3. ig_post_daily.py: replace inline {"jazz": "재즈", ...} dict with
   config.GENRES[genre]["display_name_ko"].

4. generate_seo_pages.py: replace hardcoded LOCALITIES = [("seoul","jazz")]
   with a derivation from config.LOCALITY_GENRE_REGISTRY (enabled entries).
   Fix output path collision: now writes to public/{locality}/{genre}/.
   Add display_name/display_name_ko to config.LOCALITIES and config.GENRES.

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* docs: add no-hardcoded-paths rule to CLAUDE.md working philosophy

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* fix: address code review on install.sh and sitemap

- install.sh: fix argument parsing — was using positional $1 so
  --project-dir flag was assigned literally as the path. Now parses
  --project-dir <value> correctly with an error if value is missing.
- generate_seo_pages.py: add generate_sitemap() — rewrites sitemap.xml
  automatically from enabled LOCALITY_GENRE_REGISTRY entries, including
  all app routes (with hreflang), events.html, and digest pages per locality.
  Sitemap is now always in sync with config; no manual edits needed.

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* refactor: address 3rd-round review on PR #119

- install.sh: escape $PROJECT_DIR/$HOME_DIR before sed substitution
  so paths containing &, \, or | are handled safely
- generate_seo_pages.py: remove unnecessary sys.path.insert (PYTHONPATH=.
  already set by workflow and local invocation); use xml.etree.ElementTree
  for sitemap generation instead of f-string XML to guarantee well-formed,
  properly-escaped output

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* test: add tests for generate_seo_pages.py

Covers _fmt_time_hhmm, _fmt_date_ko, _event_time, _upcoming_by_date,
_render_event, and generate_sitemap (the ElementTree rewrite).

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* fix: parameterize _render_page locality/genre; clean up generate_sitemap

Critical: _render_page had three hardcoded seoul/jazz references (CTA link,
footer service description, IG handle) that caused Germany pages to link to
the Seoul frontend and identify themselves as a Seoul service.

Fix: add locality/genre params, derive CTA URL from config primary language,
build footer text from display_name_ko, derive IG handle from naming
convention undr.live_{locality}.{genre}.

Also: replace seen_localities set with root_added bool; compute today_date
once instead of calling datetime.now() twice; add _render_page tests that
catch any regression in per-locality rendering.

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* fix: resolve runner.home error + opt into Node.js 24 across all workflows

runner.home is not available in job-level env: expressions; move
DEV_WORKSPACE resolution to a dedicated setup step using $GITHUB_ENV
with vars.DEV_WORKSPACE as override and $HOME/Codes/seoul.music as
fallback. Apply to both deploy-pages.yml and deploy-test.yml.

Also fix hardcoded /Users/keunwoo path in deploy-test.yml (uses
$DEV_WORKSPACE now like deploy-pages.yml).

Add FORCE_JAVASCRIPT_ACTIONS_TO_NODE24: true to all jobs to opt in
before the June 2026 forced migration; bump node-version 20 → 24
in all setup-node steps.

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* fix: locale-aware SEO pages + regenerate stale HTML

- Add _UI dict for ko/de/en: html lang, CTA text, last-updated label,
  performers label, service description
- Add _fmt_date() for locale-aware date headers (Korean / English)
- _render_event: add lang param; uses locale performers label
- _render_page: use primary_lang to drive all UI strings; html lang attr
- generate(): load events.{primary_lang}.json (not hardcoded ko); generate
  locale-appropriate title/subtitle/description for non-ko localities
- Regenerate all HTML with corrected output:
  - Germany: <html lang="de">, German CTA/labels, English event text,
    correct CTA URL (/germany/jazz/de), correct IG handle
- Add 11 new tests covering i18n (45 total, all pass)

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
