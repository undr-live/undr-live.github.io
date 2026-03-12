# Seoul Underground Live - Static Site

This is a **static site** automatically deployed from the private crawler repository.

## Build Information

- **Build Time**: 2026-03-12T16:43:40Z
- **Source Commit**: [`c162d49d60a7aab17493be59cb17f9c5539a532e`](https://github.com/keunwoochoi/seoulunderground.live/commit/c162d49d60a7aab17493be59cb17f9c5539a532e)
- **Branch**: `main`
- **Workflow Run**: [View logs](https://github.com/keunwoochoi/seoulunderground.live/actions/runs/23013142188)

## Commit Details

- **Author**: Keunwoo Choi <gnuchoi+github@gmail.com>
- **Message**: feat: restructure evals/ to locality/genre layout + multi-model eval dashboard (#100)

* feat: restructure evals/ to seoul/jazz locality layout + multi-model eval dashboard

- Add evals/paths.py: centralized path helpers parameterized by locality/genre,
  mirroring the data/seoul/jazz/ directory structure
- Move evals/golden/, evals/results/, evals/manifest.json →
  evals/seoul/jazz/{golden,results,manifest.json}
- Update .gitattributes LFS pattern to evals/*/*/golden/events/**/*.jpg
- Update all eval scripts (run, analyze, inspect, compare, collect_baseline,
  labeler/server, scripts/collect_golden_data) to use evals.paths helpers
- Fix evals/compare.py: split title_match_rate → title_match_strict + title_match_fuzzy,
  add TP/FP/FN/TN confusion matrix rows
- Add evals/seoul/jazz/DASHBOARD.md: full comparison of three models on 58 labeled cases
  (v4.0.3 prompt + post-date + venue context)

Results (58-case ground truth, v4.0.3 prompt):
  gemini-2.5-flash:          is_event 98.3%, date 100%, title fuzzy 90.2%
  gemini-3-flash-preview:    is_event 96.6%, date 100%, title fuzzy 96.4% (best title)
  gemini-3.1-flash-lite:     is_event 94.8%, date 100%, title fuzzy 96.3% (most FN)

Made-with: Cursor

* chore: clean up git tracking + add eval documentation

- Gitignore LOCAL_*.md (local working notes, never for commit)
- Gitignore evals/*/*/results/*/events/ and venues/ — per-case prediction
  files are regenerable with evals.run; only aggregate summaries committed
- Remove already-tracked LOCAL_*.md and 759 per-case JSON files from index
  (all files remain on disk)
- Add docs/EVALS.md: eval system architecture, directory layout, usage,
  metrics reference, and current model comparison results
- Whitelist docs/EVALS.md from the docs/*.md gitignore pattern

Made-with: Cursor

* docs: expand EVALS.md results table with all metrics

Made-with: Cursor

## Deployment

- **Live Site**: https://undr.live
- **GitHub Pages**: https://undr-live.github.io

## Data Snapshot

The static JSON files in `/api/` were exported from the local backend at build time.
Events shown are from the crawler's database as of the build timestamp above.

---

*This README is auto-generated during deployment. Do not edit manually.*
