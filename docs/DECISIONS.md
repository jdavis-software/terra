# Terra v2 decisions and supersession record

## ADR-201 — Replace the speculative observatory with the actual narrative product

**Decision:** the recording-based website is the active scope: The Planet, ten geological anchors; Civilization, eighteen human chapters. Retire the former UTC sunlight clock, solar ephemeris, axial-tilt lab, daily sunlight graph and generic point-inspection dashboard.

**Evidence:** the uploaded recording's header, timelines, chapter counter and visible story states. See REFERENCE_ANALYSIS.md. The v1 documents were authored without accessible source frames and picked the wrong product subtype. Their history remains in Git; their TR tasks are not silently recycled with different meanings. New TE-001–TE-072 IDs avoid ambiguity.

## ADR-202 — Keep observation separate from implementation inference

A recording proves composition and visible outcomes, not the original shader/library/source code. Three.js/R3F is chosen for Terra; Jordan's report of Three.js comments remains an uncorroborated lead. No source framework version, exact font, original easing or hidden panel behavior is asserted. Mobile/open-panel designs are explicit Terra completions.

## ADR-203 — Use two different chronology models

Planet uses a piecewise-linear story coordinate across ten approximately equal screen positions; real geological age is interpolated within each segment. Civilization uses eighteen ordered chapter slots and structured date labels. Overlapping ranges and century labels must not be forced through JavaScript Date or a uniformly spaced calendar. Intro screens do not add rail stops.

## ADR-204 — Original identity and concise, source-reviewed narration

Use `terra.`, not a public clone branded as the reference creator's `earth.`. Preserve the recognizable screen skeleton and chapter subjects, write original short prose, and verify historical claims/coordinates with exact sources. Include uncertainty and context without turning the visual experience into a textbook or making grand unsupported first/only claims.

## ADR-205 — One client app, no service dependency at runtime

React/TypeScript/Vite and Three.js/R3F meet the interface/rendering requirement. No backend, accounts, database, AI inference, Temporal, live feed or paid map service is justified by the core story. Static Pages hosting under `/terra/` is the default; root base remains configurable. Offline data preparation does not imply a production service.

## ADR-206 — Prove ancient geography early

Changing land configuration is essential. Prove low-resolution Pangea/breakup/present data before polishing every panel. Use one pinned, supported reconstruction model with item-level rights and identifiable layer/frame semantics. Do not confuse plate polygons with exact coastlines or extend a model beyond its supported age range.

For the core, offline masks/SDFs and intermediate frames provide smooth illustrative transitions. They are not full plate dynamics. Early Earth outside meaningful dataset coverage is explicitly conceptual. A later all-conceptual fallback for supported ancient epochs is a material fidelity downgrade that needs an explicit decision, not silent success.

## ADR-207 — Coordinate, transport and camera ownership are shared contracts

Use the documented Y-up/east-positive Earth-fixed convention everywhere. One anchored monotonic story clock drives all visible content. One camera director arbitrates scripted and manual movement. Manual input, panels, tab visibility and required buffering pause/re-anchor transport. Separate presentation motion from historical chronology and avoid two transport buttons creating two timers.

## ADR-208 — Modern night imagery cannot leak into earlier history

Global modern city emission is allowed only at Planet Today and Civilization C18. C17 is a local Pearl Street story. After dark is a presentation control, not permission to show modern infrastructure in ancient epochs. Rewind derives all overlays/emission from the target chapter, not the user's previous visited-state history.

## ADR-209 — Footprints are qualitative narrative aids

Regions, routes and prior sites help follow selected stories. They are not population density, political borders, measured trade volume or complete migration reconstructions. The interface must state that distinction and keep current/earlier layers independently controllable. Broad origins and culture networks should not be falsely located at one precise point.

## ADR-210 — Asynchronous scene consistency beats apparent instant loading

A new date over an unrelated stale Earth is a factual visual defect. Use a correct-era preview or explicit buffering; commit a coherent scene projection using request-generation IDs. Freeze/re-anchor the effective clock while required assets load. Keep a bounded current/neighbor cache and release GPU resources by ownership.

## ADR-211 — Quality targets require actual measurements

The recording reports 60 fps at the file level, which says nothing conclusive about source-app frame cadence. Terra's desktop/mobile targets require named real hardware, production builds and documented workloads. Software-rendering CI verifies correctness, not portable GPU performance. Optimize a clean base material before adding bloom; defer DOF/WebGPU/terrain unless explicitly justified after core release.

## ADR-212 — Use actual visual comparisons, not self-approved screenshots alone

Unit and browser tests establish behavior. Recording-to-render inspection establishes fidelity. Controlled screenshot snapshots prevent regressions after a good baseline exists. Record intentional differences (original branding/copy, source panels/mobile) separately from accidental mismatch (wrong globe framing, fake drift, unreadable rail). Source/capture chrome is never part of the product.

## ADR-213 — Preserve the public portfolio's rights and provenance

Do not commit the raw user recording or unlicensed source frame dumps. Use independently acquired permitted runtime assets with exact source, terms, credits, hashes and recipes. Original code licensing is separate from image/model/font licensing. No claim of NASA endorsement, creator collaboration or recovered original code.

## ADR-214 — Nine epic issues, one canonical detailed tasklist

ROADMAP.md holds all 72 TE task definitions. Reuse existing epic issues where possible, replacing their obsolete scope; create only missing epics. Closed duplicate issues remain closed. Recording analysis can be marked delivered without marking implementation or original source-code verification complete. Issue numbers are navigation, not task IDs or proof of work.

## Change template

Record date, decision ID, previous default, new default, concrete evidence/reason, affected tasks/files, model/rights/performance impact, tests/visual comparisons rerun and remaining limitations. An active source or schema change must update the catalogue, asset manifest and acceptance tests together.
