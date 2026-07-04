# Seoul Underground Live - Static Site

This is a **static site** automatically deployed from the private crawler repository.

## Build Information

- **Build Time**: 2026-07-04T13:49:57Z
- **Source Commit**: [`81fd8dccec012e6ae0a6bb6a4c6566519d863eaa`](https://github.com/keunwoochoi/seoulunderground.live/commit/81fd8dccec012e6ae0a6bb6a4c6566519d863eaa)
- **Branch**: `main`
- **Workflow Run**: [View logs](https://github.com/keunwoochoi/seoulunderground.live/actions/runs/28708218381)

## Commit Details

- **Author**: Keunwoo Choi <gnuchoi+github@gmail.com>
- **Message**: fix: verify Pages deployment after image push, retry on failure (#179)

* fix: verify Pages deployment after image push, retry on failure

The undr-live-imgs.github.io Pages build failed two days running
(2026-07-03, 2026-07-04) with GitHub's transient "Deployment failed, try
again later" — image URLs 404'd and the daily IG feed/story post failed
both days. The job runs once daily, so a single failed build kills that
day's post with no retry.

ig_deploy_images.sh now verifies the deployment after pushing: it polls
the Actions run conclusion for the pushed commit (the legacy pages/builds
API is unreliable here — it stayed stuck at "building" and never recorded
the failure), retries once via an empty-commit push on failure, and exits
1 otherwise so ig_story_job.sh aborts loudly before attempting to post.
The push also now runs unconditionally, healing a previously
committed-but-unpushed state.

Validated live: the fixed script detected the failed 09d2350f deployment,
retried with 42af469, and all five image URLs came back 200.

Also: TODO update for PR #178 and this fix; fix stale TODO filename
reference in CLAUDE.md.

Claude-Session: https://claude.ai/code/session_01XdCMM4Hosjw8jdzuJyUdyP

* fix: use Actions run conclusion in deploy-pages.yml verify; surface gh errors

The 2026-07-04 21:40 KST failure proved the legacy pages/builds API also
lies on the site repo: it stayed stuck at "building" after the failed
deployment, so the verify step's errored-triggered rebuild never fired
and it could only time out. Port the Actions-runs-API approach from
ig_deploy_images.sh, with the retry as an empty-commit push using the
deploy token (the POST /pages/builds rebuild was never exercised and the
builds API can't be trusted to report the state it keys on).

Also address review: stop redirecting gh api stderr to /dev/null in
ig_deploy_images.sh so real errors reach the job log.

Claude-Session: https://claude.ai/code/session_01XdCMM4Hosjw8jdzuJyUdyP

* fix: push HEAD:main so pushed ref matches the verified SHA

Claude-Session: https://claude.ai/code/session_01XdCMM4Hosjw8jdzuJyUdyP

* fix: fetch origin main before force-with-lease push

Claude-Session: https://claude.ai/code/session_01XdCMM4Hosjw8jdzuJyUdyP

## Deployment

- **Live Site**: https://undr.live
- **GitHub Pages**: https://undr-live.github.io

## Data Snapshot

The static JSON files in `/api/` were exported from the local backend at build time.
Events shown are from the crawler's database as of the build timestamp above.

---

*This README is auto-generated during deployment. Do not edit manually.*
