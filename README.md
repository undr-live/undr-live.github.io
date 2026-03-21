# Seoul Underground Live - Static Site

This is a **static site** automatically deployed from the private crawler repository.

## Build Information

- **Build Time**: 2026-03-21T23:55:42Z
- **Source Commit**: [`8f4daeac681e05c13edee214f5af91b8e2a54a3d`](https://github.com/keunwoochoi/seoulunderground.live/commit/8f4daeac681e05c13edee214f5af91b8e2a54a3d)
- **Branch**: `main`
- **Workflow Run**: [View logs](https://github.com/keunwoochoi/seoulunderground.live/actions/runs/23391579762)

## Commit Details

- **Author**: Keunwoo Choi <gnuchoi+github@gmail.com>
- **Message**: feat: SEO and LLM optimization (#116)

* feat: SEO and LLM optimization — meta tags, structured data, GA4 update

- Update GA4 measurement ID to G-6T1KPG2K45 (new undr.live stream)
- Add descriptive <title>, <meta description>, Open Graph, Twitter Card tags
- Set lang="ko" (site is Korean-first)
- Add canonical URL
- Add robots.txt (allow all, sitemap reference)
- Add sitemap.xml with hreflang alternates for ko/en
- Inject dynamic JSON-LD structured data (schema.org WebSite + MusicEvent)
  so search engines and LLMs can cite individual upcoming events
- Fix 404.html title (was "Seoul Underground Live")

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* feat: static HTML pages for SEO crawlability + Naver/Google SC prep

- generate_seo_pages.py: generates events.html (full listing) and
  digest/YYYY-MM-DD/index.html (weekly digest) from exported JSON.
  Both are plain HTML — readable by Naver Yeti and other non-JS crawlers.
  Hooked into deploy workflow after JSON export, before npm build.
- sitemap.xml: add events.html entry
- index.html: add commented placeholders for Google SC + Naver verification
  meta tags (fill in after registering properties)
- Ship current week's events.html and digest page with this commit

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* feat: add Naver Search Advisor verification meta tag

Co-Authored-By: Claude Sonnet 4.6 <noreply@anthropic.com>

* fix: address code review on JSON-LD structured data

- Fix performer name: was using m.name (doesn't exist); now uses
  getI18nValueWithFallback(name_ko/name_en) || name_irl || ig_handle
- Fix SearchAction target and MusicEvent url fallback: were hardcoded to
  /seoul/jazz/ko; now use locality/genre/lang route variables
- Fix addressLocality/addressCountry: were hardcoded to 서울/KR; now derive
  from LOCALITY_GEO map in locality.ts (seoul→서울/KR, germany→Germany/DE)
- Sync canonical and og:url to current route in same useEffect
  (was hardcoded to root in index.html, wrong for /seoul/jazz/en etc.)
- Add LOCALITY_GEO to locality.ts dependency array

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
