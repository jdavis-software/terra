# ASTRA execution goal — Terra v2

This is the canonical implementation prompt. It replaces the earlier observatory/sunlight-lab baseline. Read the current repository before changing files; this planning revision does not contain a running application.

```text
/goal Build Terra into a polished, cinematic, interactive Earth-history
portfolio website in jdavis-software/terra. Follow AGENTS.md and the
recording-based v2 specifications. Execute TE-001 through TE-072 in
docs/ROADMAP.md with actual implementation and verification evidence.

The actual reference is a two-part narrative website, not a sunlight lab.
Use docs/REFERENCE_ANALYSIS.md for the inspected recording evidence,
docs/VISUAL_SPEC.md for its composition, and docs/STORY_CONTENT.md
for the complete ten-anchor/eighteen-chapter inventory. Do not execute
obsolete TR tasks or restore UTC clocks, tilt sliders, astronomy adapters
or dashboard features from the superseded plan.

Build The Planet and Civilization. Preserve the reference's minimal
editorial composition: original terra. wordmark, two central navigation
items, Sources, an enormous live globe on the right, elegant light-weight
sans-serif story text on the left, contextual date at upper right and a
bottom timeline. Use original prose and independently permitted assets,
not the creator's branding, copied code or source-video frames.

The Planet starts at present day and travels through these exact rail
anchors: 4.54 Ga, 4.3 Ga, 2.4 Ga, 650 Ma, 540 Ma, 400 Ma, 300 Ma,
200 Ma, 100 Ma and Today. Implement piecewise narrative spacing,
real scrubbing/play/pause and distinct world states: formation/lava,
oceans, atmospheric change, extensive ice, ancient continents,
convergence, Pangea, breakup, later oceans and modern Earth.
Natural, After dark and Blue hour are artistic appearance presets.

Civilization has an unnumbered introduction and exactly eighteen
chapters: African origins; White Sands; cultivation/settlement; Uruk;
Giza; Mohenjo-daro; East/Central Asian exchange; Teotihuacan; Cahokia;
Polynesian navigation; northern Chinese walls; Machu Picchu; Timbuktu;
1492 Atlantic contact; Philadelphia 1776; industrial transformation;
Pearl Street 1882; and today's night-lit planet. Preserve the authored
order and approximate/overlapping date ranges. Give each chapter
appropriate camera framing, subtle illustrative regions/sites/routes,
source context and real navigation. End with a deliberate city-lights reveal.

Use React, strict TypeScript, Vite and Three.js/React Three Fiber with
verified compatible pinned versions and one lockfile. This is Terra's
stack choice, not a verified claim about the original app. Keep runtime
client-only and assets same-origin. No backend, accounts, database,
AI API, paid service, Temporal, live weather or unrelated infrastructure.

Implement docs/SIMULATION_SPEC.md: one authoritative monotonic
transport drives text/date/rail/assets/overlays; one camera director
arbitrates scripted and manual motion; both visible Play/Pause buttons
share state. Manual orbit cancels scripted motion and pauses playback.
Scrubbing pauses; opening panels, switching sections and tab hiding
pause/re-anchor. Speed changes remain continuous. Never let an old
texture request overwrite a newer seek, or show a new era's date over
an unrelated stale globe without a truthful buffering state.

The hardest visual requirement is changing continental arrangements,
not spinning or recoloring a modern map. Prove a low-resolution
Pangea-to-breakup-to-present path early. Use a pinned supported
paleogeographic model and offline-derived masks/intermediates with
item-level provenance where required. Early Earth is explicitly
conceptual. Mask/SDF interpolation is illustrative, not plate physics.
Do not claim exact ancient coastlines, a climate model or live imagery.

Modern global city lights are forbidden before present-day contexts.
C17 is local Pearl Street lighting; global night imagery belongs to C18
and Planet Today. Rewinding removes future sites and forbidden lights.
Footprints/routes are illustrative story geography, not population or
political borders. Verify historical claims, dates and coordinates using
exact primary/site-authority sources and write concise original text.

Finish every primary control: orbit, plus/minus zoom, timeline seeking,
Play/Pause, 1x/2x/5x, chapter previous/next, All chapters, section tabs,
appearance presets, contextual Sources, reset and help. Mobile/open
panel designs are Terra-specific completions because they are not
shown in the recording. Make them useful, accessible and visually
consistent. Preserve browser/page scrolling and zoom outside the
owned stage gesture. Provide reduced-motion and keyboard paths.

Work through dependency-ready tasks in small coherent commits.
Start with assets/contracts, the real opening globe and geological
feasibility, not days of decorative UI. Parallelize isolated content,
rendering and tests only after contracts stabilize, using separate
worktrees with one integration owner. Preserve user changes and do
not touch other repos or global configuration. Maintain actual status,
commands, commits, screenshots and blockers in docs/PROGRESS.md.

Implement and run meaningful lint/type/unit/content/asset/docs/build
checks and production-build Playwright tests. Inspect the actual app
at 1440x900, 1280x800 and 390x844 at minimum. Compare opening,
formation, ice, Pangea, Civilization intro, regional chapters, local
lighting and the night finale to the recording checkpoints. Test all
ten anchors and eighteen chapters, reverse/random seeks, camera
interruption, stale requests, quality changes, hidden tabs, reduced
motion, asset failure, context loss and far-side label occlusion.
Passing TypeScript alone is not completion. Fix material visual drift.

Treat 60 fps as a measured target on named real hardware, not a
claim inferred from the recording. Use progressive loading, bounded
texture residency, sensible quality tiers, no per-frame React rerenders
and explicit GPU resource disposal. Do not use software-rendering CI
as proof of laptop/mobile GPU performance.

Finish with an accurate portfolio README and engineering case study,
actual Terra screenshots and a short captured demo, all source/asset
credits, CI and a static deployment under /terra/. Verify the real public
URL and assets before claiming deployment. If permissions block it,
record the exact blocker and reproducible build evidence rather than
inventing a live link or checking off the blocked task.

Do not stop at another roadmap, scaffold, shader demo or five sample
chapters. Finish the core experience, verify it, and report actual shipped
behavior, tests, visual comparisons, measured performance, deployment
status and remaining limitations. Do not fabricate source access,
asset rights, scientific precision, benchmarks or completed tests.
```

## Completion contract

All ten Planet and eighteen Civilization states are usable, with both introductions and real controls. Core tests and actual visual comparisons pass. Sources/asset rights are verified; real project media depicts Terra rather than the reference video. Progress checkboxes agree with evidence. A permission-blocked deployment remains an explicit incomplete public release, not an all-done claim.

Use the roadmap for detailed per-task files, dependencies and acceptance criteria. The raw recording need not be republished; use its local copy for visual review when available and the timestamped analysis for implementation guidance. Original source-code identity is still unknown and is not a prerequisite for an independent reconstruction.
