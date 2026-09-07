# Terra agent contract — v2 recording-based reconstruction

## Mission and precedence

Build a polished, original implementation of the cinematic Earth/history experience visible in Jordan's uploaded screen recording. Two sections: **The Planet** with ten geological anchors and **Civilization** with eighteen chapters. Use the `terra.` identity, original prose and independently permitted assets.

The earlier Earth-observatory/sunlight-lab proposal is superseded. **Do not execute the old TR-001–TR-087 tasks or import their solar/UTC/tilt requirements.** Canonical active task IDs are TE-001–TE-072 in `docs/ROADMAP.md`. Existing GitHub issues are being reconciled to that v2 roadmap, which is authoritative over stale comments.

Read in order: `docs/ASTRA_GOAL.md`, `docs/REFERENCE_ANALYSIS.md`, `docs/PRODUCT_SPEC.md`, `docs/VISUAL_SPEC.md`, `docs/STORY_CONTENT.md`, `docs/SIMULATION_SPEC.md`, `docs/ARCHITECTURE.md`, `docs/ASSETS_AND_SOURCES.md`, `docs/ROADMAP.md`, `docs/QA_AND_RELEASE.md`, `docs/PROGRESS.md`. Use `docs/DECISIONS.md` to resolve a material change. User instructions outrank the plan; otherwise evidence and factual honesty outrank cosmetic imitation.

## Reference handling

The recording was visually analyzed; exact source code/stack, original app interactions outside the recorded paths, source font identity and mobile behavior remain unknown. Do not tell the user the video is still wholly unavailable. Do not waste the first implementation session repeatedly retrying X when the recording-based analysis exists. If the raw recording is not mounted in the implementation environment, use the timestamped ledger and visual specification; ask for the actual recording only when direct visual comparison requires it.

The 60-fps recording is not proof of source-app performance. Visible land changes do not identify the original algorithm. Three.js/R3F is Terra's implementation choice, not independently verified original technology. Sources/All chapters/speed-menu open states and mobile design are useful Terra completions, not observed source screens.

## Core boundaries

Work only in Terra and its task branch/worktree. Inspect current files and git status; preserve user changes and existing implementation if the repository has advanced. Never force-push or modify global .codex/toolchains, DriftGate, AvatarOps, Valkyrie or unrelated repos. No accounts, backend, database, AI inference, paid runtime APIs, Temporal, live weather, climate solver, solar lab or destruction simulator.

Do not republish the 348 MB reference recording, X-player chrome, macOS capture UI, unlicensed textures or source prose. Do not commit secrets, cookies, private paths or fabricated measurements. No runtime API key is required. Do not purchase services or change unrelated account settings.

## Technical defaults

React + strict TypeScript + Vite, Three.js/R3F, narrowly scoped helpers, low-frequency state store, pure narrative reducer/mapping, CSS tokens and real browser tests. Verify compatible stable versions and commit one lockfile. One application, not a monorepo. Keep frame-loop mutations out of React state updates; one camera owner and one transport clock. One renderer survives chapter/tab changes.

Follow `SIMULATION_SPEC.md` for the piecewise geological slider, explicit eighteen-chapter order, date conventions, coordinate mapping, loader generation IDs, camera cancellation and city-light guards. Modern city lights are forbidden in ancient states. The Pearl Street chapter is local; global night imagery belongs to the finale/present day. Footprints are illustrative, not populations or borders.

Use independently sourced optimized assets. Model-informed late paleogeography and conceptual early Earth have different labels. Prove changing land configurations early; a rotating modern globe with color filters does not satisfy the goal. A mask/SDF transition is not a plate-physics solver and must not be called one.

## Work loop

Execute dependency-ready TE tasks, not another planning-only response. For each slice: state the task, implement, run relevant checks, inspect the real page, compare screenshots to the recorded target, repair issues, record evidence and commit with the TE ID. Continue through the core release. Do not stop after a scaffold, shader experiment or five sample chapters.

Parallel work is allowed only with separate worktrees/file ownership and stable shared contracts. Give rendering/materials and camera integration a clear single owner. Never let multiple agents concurrently rewrite the lockfile, scene root, shared state schema or the same roadmap section.

## Checks and proof

Implement meaningful scripts: `pnpm dev`, `pnpm build`, `pnpm preview`, `pnpm lint`, `pnpm typecheck`, `pnpm test:unit`, `pnpm test:e2e`, `pnpm test:visual`, `pnpm assets:verify`, `pnpm content:verify`, `pnpm docs:check`, `pnpm check`. They are future contracts, not working commands in the planning-only repository.

`check` must fail on lint/type/unit/content/asset/docs/build failure; browser suites run in configured jobs against the production build. No echo-success stubs, disabled checks, manufactured screenshots, fake source citations or unexplained tolerance inflation. Record actual commands/results. Do not claim browser checks passed when only a build passed.

Use fixed story IDs/positions, seeds, quality, viewport, DPR and a GPU-ready scene signal for deterministic captures. Compare opening, formation, ice, Pangea, selected human chapters and the night finale. Review copy/layout/globe/lighting/rail/controls and mobile separately. Source-video fidelity is not proven by creating a screenshot baseline of your own wrong implementation.

## Completion

A task is done only with its stated deliverables and evidence. Use not_started/in_progress/blocked/done in `PROGRESS.md`. Separate completed recording analysis from pending implementation and pending live-source verification. A deployment blocked by settings remains blocked; a guessed URL is not a live demo.

Final handoff: exact shipped features, all 10+18 story states, tests with outcomes, visually inspected evidence, measured device/browser performance, source/asset credit status, verified deployment or precise blocker, and remaining limitations. Optional enhancements must not delay or replace the reference core. Keep the final project inviting and fun rather than turning the portfolio into infrastructure administration.
