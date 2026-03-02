# Seoul Underground Live - Static Site

This is a **static site** automatically deployed from the private crawler repository.

## Build Information

- **Build Time**: 2026-03-02T04:31:18Z
- **Source Commit**: [`bcc4689b7fb22ed653a7836c06dbef90d29a4dbe`](https://github.com/keunwoochoi/seoulunderground.live/commit/bcc4689b7fb22ed653a7836c06dbef90d29a4dbe)
- **Branch**: `main`
- **Workflow Run**: [View logs](https://github.com/keunwoochoi/seoulunderground.live/actions/runs/22561460193)

## Commit Details

- **Author**: Keunwoo Choi <gnuchoi+github@gmail.com>
- **Message**: Implement tier-based venue sampling for weekly highlights (#98)

* Implement tier-based venue sampling for weekly highlights

Introduces a 4-tier venue classification system with weighted probability
sampling to ensure diverse and quality venue selection in weekly highlights.

Tier probabilities (relative to base probability p0):
- Tier 0 (great places): p0
- Tier 1 (real jazz bars): p0/3
- Tier 2 (hybrid venues): p0/9
- Tier 3 (not recommended): 0 (excluded from selection)

Changes:
- Add venue_handles.csv with tier, valid, and note columns for all venues
- Add read_venue_handles_with_tiers() to support both CSV and TXT formats
- Update weekly highlights selection to use tier-based weighted sampling
- Maintain uniqueness guarantee (no duplicate venues within same week)

Test results (1000 simulations):
- Tier 0: 52.28% of selections (expected ~55%)
- Tier 1: 33.82% of selections (expected ~31%)
- Tier 2: 13.90% of selections (expected ~14%)
- Tier 3: 0% (correctly excluded)

Made-with: Cursor

* Remove venue_handles.csv from git tracking

The CSV file should remain local-only (like venue_handles.txt) and not be
tracked in git. This prevents triggering the deployment workflow on PRs.

Made-with: Cursor

* Fix test to match weighted sampling without replacement implementation

Updated test_weighted_sampling_ensures_unique_venues to use the same
weighted sampling without replacement algorithm as the actual code.

Made-with: Cursor

* Add tier-based venue sorting

Add tier field to venues table and update frontend to sort venues by tier
first (0=great, 1=real jazz bar, 2=hybrid, 3=not recommended), then by
event count within each tier.

Backend changes:
- Add tier column to Venue model (Integer, default=1)
- Update Venue schema to include tier field
- Include tier in API responses from list_venues endpoint
- Create migration script to populate tier from venue_handles.csv

Frontend changes:
- Add tier field to Venue type
- Update venue sorting logic to sort by tier (ascending), then event count (descending)

Migration:
- Run scripts/db_add_venue_tier_column.py to add column and populate data
- Reads from venue_handles.csv (if exists) or venue_handles.txt (defaults to tier 1)

Made-with: Cursor

* Fix code review issues

- Keep strict=False for linter but add comment explaining Python <3.10 compatibility
- Fix N+1 query problem: batch fetch venues instead of individual queries
- Make CSV parsing robust against empty values
- Simplify tier weight mapping using dictionary

Made-with: Cursor

* Add tier migration to deployment workflows

Both production and test deployments now run the tier migration script
to populate venue tier information after importing data.

Changes:
- deploy-pages.yml: Run migration after venue/event imports
- deploy-test.yml: Run migration before exporting static JSON

This ensures tier-based venue sorting works on deployed sites.

Made-with: Cursor

## Deployment

- **Live Site**: https://undr.live
- **GitHub Pages**: https://undr-live.github.io

## Data Snapshot

The static JSON files in `/api/` were exported from the local backend at build time.
Events shown are from the crawler's database as of the build timestamp above.

---

*This README is auto-generated during deployment. Do not edit manually.*
