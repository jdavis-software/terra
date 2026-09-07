# Reference reconstruction tasklist

## Purpose and current limit

This is the detailed execution protocol for **TR-001** in [ROADMAP.md](ROADMAP.md), tracked by [reference-audit issue #4](https://github.com/jdavis-software/terra/issues/4). It expands one existing task into ten research subtasks; it does not add ten speculative application features or claim that the research has been completed.

Jordan wants to reverse engineer the Earth-simulator experience in the supplied X video for a fun GitHub portfolio project. The planning session could not inspect the video or comments. The latest access results and unverified feature inventory are in [reference/ACCESS_AND_FEATURES.md](reference/ACCESS_AND_FEATURES.md). Three.js is a **user-reported lead from comments**, not a confirmed original dependency. React, React Three Fiber, Vite, shader techniques, data sources and simulation fidelity are also unverified for the original.

The existing 62-task Terra roadmap is a proposed build specification. Source observation must determine what is actually reconstruction scope; optional Terra enhancements must not be passed off as reference features.

## Execution order and evidence vocabulary

Run RF-001 first. With usable content, run RF-002, then RF-003/RF-005, then RF-004/RF-006, then RF-007 through RF-010. Dependencies below are authoritative. These are inspection/specification tasks, not a requirement to implement the app before beginning M1. Application fidelity verification occurs in TR-072.

Every finding has two independent fields:

- **Evidence class:** `user_reported`, `video_observed`, `live_app_tested`, `author_claimed`, `implementation_corroborated`, `hypothesis`, or `unknown`.
- **Product disposition:** `source_core`, `terra_enhancement`, `deferred`, or `unresolved`.

A visible effect may be `video_observed` while its shader implementation is only a `hypothesis`. A comment by the author is an `author_claimed` stack statement, not proof that the published app uses that exact version. A library's presence somewhere in a bundle does not by itself prove that it renders the globe.

Task status is `not_started`, `in_progress`, `blocked`, or `done`. An access attempt can be done while video inspection remains blocked. Do not turn missing evidence into successful analysis by changing labels.

## RF-001 — Establish legitimate access

- [ ] Complete in ASTRA's execution environment and record evidence.
- **Depends on:** none.
- **Read:** the latest access audit and exact reference URLs; do not search for a merely similar Earth demo and substitute it.
- **Actions:** discover whether Computer actually exposes browser actions. If it does, invoke them to open the exact post and its video. Otherwise use an available authorized browser and name the fallback accurately. Record the resulting URL, visible page state, exact error where applicable, and whether post text, replies and video independently load. Existing user-authenticated access may be used only through the authorized browser interface; never extract cookies or tokens.
- **Outputs:** an appended access record in `docs/reference/ACCESS_AND_FEATURES.md`; permitted local evidence of the result.
- **Acceptance:** a capability discovery result is not described as a successful browser invocation. A browser navigation is not described as video playback. Do not infer deletion/privacy from a 403 or environment block. Do not bypass administrator restrictions, change permissions, sign up for services, post, like, follow or contact the creator.
- **Failure path:** after checking the actual available legitimate routes, stop repeated retries against the same blocker. Set downstream observation tasks to `blocked`, retain the exact reason, and take the explicitly labeled baseline branch described below. No source frames may be invented.

## RF-002 — Identify the exact post and creator context

- [ ] Complete and record evidence.
- **Depends on:** RF-001 with readable source content.
- **Actions:** read the post text, visible date, any project name, creator replies, relevant technical comments and author-linked application/source URLs. Distinguish replies to this post from unrelated profile posts. Separate creator statements from third-party guesses. The Three.js lead is a targeted question to resolve, not a conclusion to impose.
- **Outputs:** `docs/reference/POST_AND_STACK.md`, containing supported metadata, short attributed excerpts or paraphrases, exact comment/permalink references where available, and a list of accessible linked artifacts.
- **Acceptance:** each claimed dependency has its own evidence. Confirming Three.js does not confirm React, R3F, Vite, WebGPU, a physics engine or a backend. Record missing/unreadable comments instead of manufacturing a transcript. Do not quote more than is necessary or copy the complete discussion into public Git history.

## RF-003 — Inspect the complete video

- [ ] Complete and record evidence.
- **Depends on:** RF-002 with playable or legitimately supplied video.
- **Actions:** watch the complete video, then revisit every material transition. Record actual duration, dimensions and playback observations when available. Listen to any relevant narration; distinguish narration from independently verified behavior. Identify the opening, every control activation, significant camera/scene change and final state. Sample additional frames roughly every 2–3 seconds when useful, but do not treat uniform sampling as a substitute for watching interaction boundaries.
- **Outputs:** `docs/reference/FRAME_LEDGER.md`, with actual timecodes/frame IDs and associated local evidence. If an authorized media file is available, record its SHA-256 and source. Store raw video outside the public repository unless redistribution is permitted.
- **Acceptance:** every claimed visual state has an actual evidence anchor. Note video cuts and overlays; do not infer smooth in-app transitions across an edited cut. Record unreadable text as unreadable. Use direct visual inspection; OCR is a last resort, not the default.
- **Ledger columns:** timestamp or frame ID; composition; readable text; apparent action; before/after state; observed change; uncertainty; task mapping.

## RF-004 — Inventory visible UI and composition

- [ ] Complete and record evidence.
- **Depends on:** RF-003.
- **Actions:** describe viewport aspect, globe size and position, panel/toolbar anatomy, visible controls and their readable labels, typography hierarchy, dominant colors, atmosphere/cloud treatment, geographic overlays and explanatory copy. Measure normalized proportions relative to the video content area, excluding the X player's chrome. Inspect open/closed states separately. Record numerical visual estimates as estimates rather than exact CSS values.
- **Outputs:** `docs/reference/UI_INVENTORY.md` and an updated feature matrix in `ACCESS_AND_FEATURES.md`; permitted reference diagrams/frames when available.
- **Acceptance:** no invented controls or default dashboard sections. A desktop-only video does not establish the original's mobile behavior. Mobile adaptations can be designed for Terra, but they must be labeled Terra decisions. No generated concept may masquerade as an inspected original frame.

## RF-005 — Corroborate the rendering stack

- [ ] Complete and record evidence.
- **Depends on:** RF-002; a linked live app is helpful but not guaranteed.
- **Actions:** inspect accessible creator statements and any legitimately published source. If a live app is linked, inspect public DOM/script resources and network requests through ordinary authorized browser tools. Record URLs, package/version evidence and whether the evidence is tied to the scene implementation. Do not bypass access controls or extract proprietary/secret material.
- **Outputs:** a technology table in `POST_AND_STACK.md`: component, evidence, confidence, caveat, and Terra implementation decision.
- **Acceptance:** a canvas or a WebGL context does not prove Three.js; a Three.js-like appearance does not prove R3F; a CDN/script name can support presence but not every implementation claim. Distinguish WebGL/WebGPU evidence from visual similarity. If source remains inaccessible, keep the original stack unknown while separately selecting Three.js for Terra.
- **Decision boundary:** use the existing React/Three.js baseline unless evidence or actual project constraints justify a documented change. This task is not a reason to chase every possible engine.

## RF-006 — Specify the interaction/state model

- [ ] Complete and record evidence.
- **Depends on:** RF-003 and RF-004.
- **Actions:** for every visible interaction, record input, precondition, state mutation, rendered result, animation, cancellation and reset behavior. Where an accessible live demo exists, test those controls directly and distinguish tests from video-only inference. Cover orbit/zoom/selection/parameter changes only where present; explicitly note unshown behavior. Inspect keyboard, viewport changes and errors only if testing the actual app is possible.
- **Outputs:** `docs/reference/INTERACTIONS.md`, containing state tables and Given/When/Then scenarios.
- **Acceptance:** no inert control is accepted merely because it looks correct. Camera movement, Earth rotation, lighting changes and time progression are not conflated. Pausing video playback is not evidence of an in-app pause control. Source behavior outside the clip remains unknown until tested.

## RF-007 — Decompose effects and asset requirements

- [ ] Complete and record evidence.
- **Depends on:** RF-004, RF-005 and RF-006.
- **Actions:** map each observed visual effect to plausible implementation techniques. For each technique state inputs, output, frame/update frequency, resource ownership, potential artifacts, and a simpler fallback. Analyze surface/day-night material, clouds, atmosphere, camera and overlays only to the extent observed. Identify which data/assets can be independently acquired with appropriate rights.
- **Outputs:** `docs/reference/TECHNICAL_DECOMPOSITION.md`; asset additions to `ASSETS_AND_SOURCES.md`; changed architectural decisions where warranted.
- **Acceptance:** plausible reconstruction techniques are labeled hypotheses/choices, not recovered source code. No unlicensed copying of reference shaders, branded UI, media or hotlinked assets. Never infer a climate/physics solver from a plausible animation.
- **Engineering checks for the chosen Three.js baseline:** WebGLRenderer is a WebGL2 renderer; color/data texture semantics differ; GPU resources need explicit ownership; compressed file size is not total GPU memory. Consult the primary sources below and the existing architecture rather than deriving these details from the unviewed video.

## RF-008 — Reconcile source scope with the implementation roadmap

- [ ] Complete and record evidence.
- **Depends on:** RF-007.
- **Actions:** give each confirmed source feature a stable feature ID and one or more TR task IDs. Classify every proposed baseline capability as `source_core`, `terra_enhancement`, `deferred`, or `unresolved`. Identify actual omissions before adding more polish features. Implement recognizable source composition and interactions before non-source extras.
- **Outputs:** `docs/reference/SCOPE_DIFF.md`; updates to PRODUCT_SPEC, VISUAL_SPEC, ROADMAP and DECISIONS where necessary.
- **Acceptance:** nothing in the video is silently dropped merely because the earlier proposal omitted it. Nothing in the proposal is falsely attributed to the creator. In particular, the sunlight lab, city search, tours, photo export and scene URLs are not known source features yet. Keep task IDs stable where possible; when scope truly changes, update counts, dependencies, issues and the goal together instead of preserving an obsolete 62-task claim.
- **Material mismatch:** if the source is a terrain, destruction, climate or planetary-formation simulator rather than an orbital observatory, record that explicitly. Do not spend the entire implementation budget building the wrong product under a parity label.

## RF-009 — Define reference-based acceptance scenarios

- [ ] Complete and record evidence.
- **Depends on:** RF-008.
- **Actions:** select representative observed states, including the opening and major interactions, and specify replay steps, viewport, camera/time inputs when knowable, visible results, and allowable intentional differences. Use all meaningful states if there are fewer than five; never invent states to meet a quota. Define visual checks for globe framing, orientation, lighting, layer ordering, panel proportions, copy and transitions.
- **Outputs:** `docs/reference/FIDELITY_SCENARIOS.md`, linked to the relevant TR acceptance sections and TR-072.
- **Acceptance:** a later implementer can reproduce each scenario without guessing what to inspect. Unknown parameters are identified and visually calibrated later; they are not presented as exact original values. Any tolerances are Terra test targets, not measured original performance. Passing lint, unit tests or a generic snapshot is not sufficient for visual parity.
- **No dependency cycle:** this task designs the tests. It does not require TR-017/TR-072 to be implemented before TR-001 can finish.

## RF-010 — Publish the actual analysis and handoff decision

- [ ] Complete and record evidence.
- **Depends on:** RF-008 and RF-009, or the explicit blocked-access branch below.
- **Actions:** summarize observed experience, stack evidence, reconstruction choices, source/asset constraints, scope differences, unresolved questions and task order. Link every nontrivial claim to its evidence. Reconcile the new report with REFERENCE_ANALYSIS.md and PROGRESS.md. Do not overwrite concurrent user/agent edits; inspect repository and issue state first.
- **Outputs:** updated analysis, feature matrix and progress; a clear build path in `ASTRA_REFERENCE_FIRST_GOAL.md` or a documented decision linked from it.
- **Acceptance:** publish one of `reference_verified_for_planning`, `reference_partially_inspected`, or `reference_blocked`. The first means the reviewed evidence supports the planned reconstruction; it does not mean the app has been implemented or compared successfully. Any source-code/stack uncertainty remains visible. App parity remains a separate TR-072 outcome.

## Blocked-reference branch

RF-001 can finish with a documented blocker. RF-002–RF-009 remain blocked wherever they depend on unavailable content; RF-010 may publish a **blocked-reference handoff**, not a completed analysis. Keep observed frames/states at zero when none were inspected. Retain the Three.js comment lead as user-reported.

Continue useful implementation against the explicitly proposed Terra baseline in ROADMAP.md rather than inventing a source specification. Label progress and public claims as an original inspired build. Do not claim source fidelity, creator-stack confirmation, frame-by-frame inspection or source-derived controls. The numerical/asset/quality requirements still apply to any baseline features that are built.

A later accessible video triggers reconciliation before further non-source enhancement work. It does not automatically authorize copying the creator's source or assets. Actual visual comparison is required before any parity claim can change.

## Evidence storage and publication

Public documentation may contain factual observations, links, concise attributed excerpts and original implementation decisions. Raw source video, full comment dumps, credentials, session recordings containing unrelated personal browser content, and unlicensed reference captures must not be committed. Keep local working evidence separate and publish only material with appropriate rights. Record filenames/checksums only when the underlying files actually exist.

## Primary technical references

These inform the proposed implementation, not identification of the source app:

- Three.js WebGLRenderer: https://threejs.org/docs/pages/WebGLRenderer.html
- Three.js color management: https://threejs.org/manual/en/color-management.html
- Three.js KTX2 loader: https://threejs.org/docs/pages/KTX2Loader.html
- Existing Terra architecture and asset specifications: [ARCHITECTURE.md](ARCHITECTURE.md), [ASSETS_AND_SOURCES.md](ASSETS_AND_SOURCES.md).

The three linked Three.js pages were retrieved in this planning follow-up. No original-video content was retrieved.
