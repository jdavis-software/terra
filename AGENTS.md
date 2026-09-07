# Agent instructions — Terra

## Mission

Build a beautiful, credible, client-only Earth observatory and educational sunlight sandbox for Jordan Davis's GitHub portfolio. Optimize for a polished usable experience, not the number of dependencies or the size of the feature list. This repository initially contains planning documents only.

The supplied X video was inaccessible during planning. Do not say it was watched, identify its stack, invent timestamps, or claim visual parity without evidence. All proposed Terra features are original implementation decisions unless explicitly reclassified in the reference ledger after inspection.

## Read before implementation

1. `docs/ASTRA_GOAL.md` — execution goal and completion contract.
2. `docs/REFERENCE_ANALYSIS.md` — what is and is not known.
3. `docs/PRODUCT_SPEC.md` and `docs/VISUAL_SPEC.md` — what to build and how it should feel.
4. `docs/ARCHITECTURE.md` and `docs/SIMULATION_SPEC.md` — technical and numerical contracts.
5. `docs/ASSETS_AND_SOURCES.md`, `docs/ROADMAP.md`, `docs/QA_AND_RELEASE.md`.
6. `docs/DECISIONS.md` and `docs/PROGRESS.md` — decisions and current evidence.

User instructions override this baseline. Otherwise preserve scientific honesty and scope first, numerical/API contracts second, the visual specification third, and task ordering fourth. Resolve contradictions in `docs/DECISIONS.md` rather than silently choosing different behavior. The roadmap is the canonical task registry; GitHub issues group tasks into epics.

## Non-negotiable boundaries

- Work only in Terra and its task branch/worktree. Do not modify DriftGate, AvatarOps, Valkyrie, global `.codex`, shell profiles, global toolchains, credentials, or unrelated repositories.
- No backend, authentication, billing, database, Temporal, agent orchestration framework, external AI inference, paid map tiles, or mandatory live service in the core release.
- No cloning another creator's branding, source code, or restricted assets. Link the inspiration and record asset-specific terms. Publicly viewable does not mean freely redistributable.
- Do not add destructive planetary events, climate prediction, terrain flight, satellites, or real-time weather to core scope merely because they sound impressive.
- No fake telemetry, fake loading percentages, hardcoded performance claims, or nonfunctional controls. Historical composites, artistic effects, modeled sunlight, and optional live data must have different labels.
- No secrets in the client, repository, screenshots, logs, or scene URLs. Do not purchase services or change account settings without authorization.
- Do not overwrite user changes. Inspect `git status`, existing files, and branch state before writing. Use ordinary commits; never force-push or rewrite unrelated history.

## Implementation defaults

Use React, TypeScript in strict mode, Vite, Three.js through React Three Fiber, narrow Drei imports, Zustand for low-frequency state, and Astronomy Engine behind a small adapter. Use WebGL2 and GLSL for the baseline. Confirm current package compatibility, select stable versions, pin the package manager/runtime and commit one lockfile. Do not upgrade the stack midway without a documented blocker and regression results.

One application, not a monorepo. Keep pure simulation/math modules independent of React and Three.js. Keep GPU resources, frame-loop mutation and camera control outside React's per-frame state updates. Do not introduce a worker until profiling identifies work worth moving; KTX2's transcoder worker is a justified exception.

Respect the Earth-fixed coordinate convention and single authoritative simulation clock. Camera auto-orbit is not planetary rotation. Day/night calculations and inspector readouts must use the same Sun direction. Lab results must never masquerade as present-day Earth measurements.

## Working loop

Select the next dependency-ready task from `docs/ROADMAP.md`. Record its status and intended verification. Implement a small coherent slice, run relevant checks, open the actual application, inspect screenshots, repair defects, then record evidence and commit with the task ID. Continue into the next core task; do not stop at scaffolding or another plan.

When parallel execution is useful, give separate worktrees and file ownership to numerical simulation, UI, and tests. Rendering/materials have one integration owner. Do not allow two agents to write the same lockfile, scene root, shared state contract, or specification concurrently. Merge frequently and rerun integration tests.

Keep the default branch usable. A temporary shader spike is not a shipped feature. Delete abandoned experiments and debug UI before release. Keep curated verification evidence; exclude transient browser videos and large raw source imagery from normal Git history.

## Verification contract

The implementation must provide these scripts: `pnpm dev`, `pnpm build`, `pnpm preview`, `pnpm lint`, `pnpm typecheck`, `pnpm test:unit`, `pnpm test:e2e`, `pnpm check`, `pnpm assets:verify`, and `pnpm docs:check`. Their implementation and actual outputs are required; they do not exist in the initial planning commit.

Use real browser inspection for every visual milestone. Compare actual screenshots to the baseline visual specification and, only when available, inspected reference frames. Passing TypeScript or screenshot-difference automation alone is not visual sign-off. Verify desktop and mobile separately.

Use deterministic scene inputs, fixed seeds, controlled clocks, a ready signal after asset upload, and recorded browser/OS/GPU details. Do not claim GPU performance from a headless software-rendering run. Do not disable tests, lower thresholds, invent outputs, or approve a bad baseline just to obtain green CI.

## Completion and blockers

A task is complete only when its stated acceptance criteria and relevant tests pass and its evidence is recorded. Mark work `not_started`, `in_progress`, `blocked`, or `done`. A missing reference video can be accepted as an explicit visual-fidelity limitation; a missing renderer or broken core interaction cannot.

A permissions-dependent deployment must be reported as blocked rather than called deployed. Do not fabricate a production URL. No reference-video access, pending real-device testing, and deployment restrictions must remain visible in the final handoff where applicable.

The final handoff must state what actually shipped, commands and results, remaining limitations, screenshot/demo locations, source attribution, and deployment status. Optional extensions are not required for core completion.
