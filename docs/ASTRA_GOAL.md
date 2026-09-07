# ASTRA autonomous build goal

## Before starting

Open this repository in the implementation environment. The initial repository contains documentation only. The `/goal` below instructs implementation; it is not a request to generate another plan. All versions, assets and environment capabilities must be verified when the build starts.

The exact X reference remains inaccessible from the planning environment. Reattempt it once through available legitimate browser access, document the outcome, and continue with the proposed baseline if still blocked. Never invent source-video observations or describe proposed Terra features as observed ones.

## Copy-ready goal

```text
/goal Implement Terra in this repository as a polished, portfolio-quality,
client-only Earth observatory and educational sunlight sandbox.

Read AGENTS.md and the complete documentation index in docs/README.md.
Then read REFERENCE_ANALYSIS.md, PRODUCT_SPEC.md, VISUAL_SPEC.md,
ARCHITECTURE.md, SIMULATION_SPEC.md, ASSETS_AND_SOURCES.md,
ROADMAP.md, QA_AND_RELEASE.md, DECISIONS.md and PROGRESS.md.
Treat these files as the implementation contract, not as a suggestion
to produce another planning response.

USER INTENT
Build an impressive, genuinely interactive GitHub portfolio project for
Jordan Davis. The experience must feel like a cinematic observatory,
not a generic dashboard containing a rotating globe. Make the default
view beautiful, the interactions responsive, and the engineering
credible and explainable.

REFERENCE HONESTY
The inspiration is:
https://x.com/akshdeeps_001/status/2096776530005488028
https://x.com/akshdeeps_001/status/2096776530005488028/video/1
The planning environment could not inspect this video. No source
frames, original stack or feature inventory have been verified.
Attempt legitimate access in the current browser. If successful,
create an actual timestamped evidence ledger and compare it with the
proposed baseline. If unsuccessful, record that explicitly and keep
building the specified Terra baseline. Never fabricate timestamps,
controls, source code, playback observations or a parity claim.
Do not redistribute the reference video or restricted assets.

SCOPE
Complete the 62 core tasks in docs/ROADMAP.md, M0 through M7, in
safe dependency order. The eight extension tasks TR-080 through
TR-087 are not required and must not distract from core completion.
Build the app, not just scaffolding, mockups, screenshots or docs.

The core experience must include:
- A real textured Earth with coherent day/night city lights, clouds,
  restrained atmosphere, decorative stars and smooth orbit/zoom.
- One authoritative UTC simulation clock with play/pause, speeds,
  daily scrubbing, date/time input, Now and reset.
- Searchable curated places, accurate point picking, safe fly-to,
  useful location inspection and keyboard equivalents.
- A clearly labeled educational sunlight lab with tilt, season,
  solar-day duration, phase and a normalized daily sunlight curve.
- Functional layers, deterministic presets, a user-started cinematic
  tour, photo mode, actual image export and validated scene URLs.
- A complete mobile interface, reduced-motion behavior, capability
  fallbacks, honest loading/errors and a credible performance story.
- Tests, CI, source credits, actual screenshots/demo media, an
  engineering case study and verified static deployment where the
  environment has the required authorization.

DEFAULT ARCHITECTURE
Use one React + strict TypeScript + Vite application. Use Three.js
through React Three Fiber, narrow Drei helpers, Zustand only for
low-frequency application state and Astronomy Engine behind an
adapter. Use WebGL2/GLSL as the baseline. Verify compatible stable
versions, pin the runtime/package manager and commit one lockfile.
Do not create a monorepo or add a backend, auth, database, billing,
Temporal, paid map services, AI runtime calls or an orchestration
framework. WebGPU and terrain are optional later experiments.

NUMERICAL CONTRACT
Honor docs/SIMULATION_SPEC.md exactly unless a documented correction
is required. North is +Y, zero longitude is +X and east-positive
90 degrees is -Z. Keep the Earth fixed and transform the Sun into
its frame. Do not rotate both Earth and Sun for the same day.
Camera motion must not change sunlight at a selected point.
Keep one anchored monotonic simulation clock, not frame-count time.
Materials, readouts and curves must share the same model inputs.
Validate the astronomy adapter with independently sourced fixtures.
Do not mix J2000 and of-date coordinates or radians/degrees/hours.
Lab time is hypothetical, not UTC. Artistic atmosphere/cloud effects
are not climate physics. Do not invent temperatures, live weather,
population statistics or performance numbers.

VISUAL EXECUTION
Establish full desktop and mobile visual targets at TR-004, then
implement from them. Generated concepts are not app screenshots and
are not scientific texture data. Keep Earth dominant, chrome quiet,
controls readable and motion purposeful. Open the actual app and
inspect screenshots after each visual milestone. Compare composition,
orientation, lighting, atmosphere, typography, spacing, icons and
mobile behavior. Fix material mismatches; a green build alone does
not establish visual quality. Do not claim user approval that did not
occur, or claim X-video fidelity without inspecting it.

ASSETS AND PERFORMANCE
Use permitted locally bundled assets with exact source/credit/terms,
observation period, dimensions, SHA-256 and reproducible transforms.
Use a preview first and progressively upgrade quality. Respect DPR,
texture-memory and initial-load budgets. Distinguish historical
composites, derived sunlight and artistic effects in the UI/credits.
No NASA branding or endorsement implication. Manage texture/material/
geometry/worker lifetimes and test repeated quality/remount cycles.
Profile before adding workers or expensive postprocessing. Do not
label headless software-rendering results as real hardware FPS.

EXECUTION LOOP
Inspect git status and the current repository before edits. Preserve
user changes and work in a normal Terra task branch/worktree. Do not
change other repositories, global .codex, shell profiles, credentials
or global toolchains. Never force-push.

For every task: read its dependencies and acceptance criteria;
implement a coherent slice; run relevant unit/browser/visual checks;
fix failures; update docs/PROGRESS.md with actual evidence; check off
the task only when it passes; then commit with the task ID. Continue
to the next core task. Keep milestone issues synchronized if GitHub
access is available. Do not treat writing documentation as proof that
application work is done.

Parallelize only isolated domains after contracts are stable. Assign
separate worktrees/file ownership to math, UI and tests. One owner
integrates scene/materials/shared state. Do not race on lockfiles,
shared contracts or the same scene root. Re-run integration checks
after merging.

VERIFICATION
Implement and run pnpm lint, pnpm typecheck, pnpm test:unit,
pnpm assets:verify, pnpm docs:check, pnpm build and pnpm test:e2e.
pnpm check must run real checks and fail honestly. Test the built
preview with /terra/ base, not only the dev server. Test a real
WebGL scene, shader errors, nonblank output, time/selection/lab,
share links, tours, export, keyboard/mobile and failure recovery.
Use deterministic time, seed, camera, quality and a real scene-ready
signal. Do not disable failing tests, approve bad snapshots or
invent outputs to satisfy the goal.

DEPLOYMENT AND PORTFOLIO
Prefer an authorized static deployment to GitHub Pages under /terra/.
Verify the actual public URL, texture/decoder paths and scene-link
reloads before calling it deployed. If settings or permissions block
publication, report that precise blocker and provide the build and
runbook; never fabricate a URL or claim local preview is production.
Publish only real application screenshots and a real demo clip.
Write a clear README/case study explaining the difficult engineering
choices, measured results, sources and limitations. Keep external
asset licenses separate from the proposed MIT original-code license.
Do not purchase services or change account permissions without
explicit authorization.

STOP CONDITION AND HANDOFF
The target is all core acceptance criteria passing, no material visual
blockers, tested clean-clone setup, traceable assets and honest release
evidence. Optional features are not a reason to delay this.
Report what actually shipped, exact checks/results, browser/device
coverage, media locations, verified deployment status and remaining
limitations. Distinguish Terra-spec completion from source-video
fidelity. A genuinely blocked deployment or unavailable hardware test
must remain blocked/unverified, not be relabeled done. Continue all
other dependency-ready work rather than stopping at the first external
limitation. Leave a precise next action for each real blocker.
```

## Suggested handoff structure

The implementation handoff should summarize actual core feature coverage, identify the release commit, show the real demo and screenshots, list checks with their results, report performance with device/test conditions, identify outstanding issues and state whether the X reference was eventually inspected. Do not repeat the full planning documents instead of showing the built result.

## Resuming after an interruption

Read `git status`, the latest commits, `PROGRESS.md` and the roadmap checkboxes. Re-run the last milestone's smoke tests before continuing. A chat statement that a task was finished is not sufficient evidence; use code, tests and recorded results. Select the next dependency-ready core task, not a new optional feature.
