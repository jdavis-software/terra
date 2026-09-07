# terra.

### One planet. Billions of years. Countless human stories.

Terra is a cinematic, interactive Earth-history experience planned for **Jordan Davis's GitHub portfolio**. Explore a changing planet across deep time, then follow eighteen human stories across its surface—from African origins to the illuminated modern world.

**Current status: recording analyzed and implementation plan published; application not yet implemented.** The active roadmap contains **72 core tasks in nine epics**, with no application tasks verified complete. There is no claimed live deployment or measured performance result yet.

## The experience

**The Planet** opens with today's Earth and travels through ten story anchors: formation, early oceans, atmospheric change, extensive ice, ancient seas, converging continents, Pangea, continental breakup, widening oceans and the present. A story-paced timeline controls the globe, age and narrative together.

**Civilization** opens with a separate introduction, then visits eighteen authored chapters with geographic camera transitions, subtle illustrative regions/routes, contextual sources and a modern Earth-at-night finale. Its numbered chapter rail is not a linear calendar scale.

The interface stays minimal: an enormous globe, elegant narrative text, a contextual date, two navigation sections and a bottom timeline. Orbit, scrub, pause, change speed, jump chapters and inspect sources. No account, backend, paid API or AI service is required at runtime.

## Build with ASTRA

Read [AGENTS.md](AGENTS.md), then use the complete execution prompt in [docs/ASTRA_GOAL.md](docs/ASTRA_GOAL.md).

```text
/goal Build Terra using AGENTS.md and docs/ASTRA_GOAL.md.
Execute the recording-based TE-001–TE-072 roadmap in docs/ROADMAP.md.
Deliver all ten Planet anchors and eighteen Civilization chapters,
verify the actual browser experience against the reference, and keep
real implementation/test/deployment evidence in docs/PROGRESS.md.
Do not implement the superseded observatory or sunlight-lab plan.
```

The documentation's `pnpm` commands are implementation contracts, not commands that already work in this planning-only repository. Exact compatible dependency versions and production assets must be verified during bootstrap.

## Start here

| Document | What it contains |
| --- | --- |
| [Recording analysis](docs/REFERENCE_ANALYSIS.md) | Timestamped observations, screen anatomy, evidence limits and comparison with the supplied Grok prompt |
| [Detailed tasklist](docs/ROADMAP.md) | All 72 tasks, dependencies, intended files, acceptance criteria and verification |
| [Story catalogue](docs/STORY_CONTENT.md) | Ten geological anchors and all eighteen human chapters, with source-review requirements |
| [ASTRA goal](docs/ASTRA_GOAL.md) | Complete copy-ready implementation instructions |
| [Visual specification](docs/VISUAL_SPEC.md) | Recording-based composition, typography, lighting, controls and responsive direction |
| [Architecture](docs/ARCHITECTURE.md) | Module ownership, state/data flow, shaders, camera and asset lifecycle |
| [Story engine contracts](docs/SIMULATION_SPEC.md) | Piecewise time, chapter dates, coordinates, cancellation and asynchronous scene consistency |
| [Quality and release](docs/QA_AND_RELEASE.md) | Full browser/visual/numerical/content/asset acceptance gates |
| [Progress](docs/PROGRESS.md) | What is actually done, what remains and how evidence is recorded |

[All documentation](docs/README.md) includes asset provenance, decisions and the issue map.

## Roadmap

| Epic | Tasks | Result |
| --- | --- | --- |
| M0 — Evidence and feasibility | TE-001–TE-008 | Correct scope, viable assets and stable contracts |
| M1 — Real opening slice | TE-009–TE-016 | The actual editorial shell and a navigable Earth |
| M2 — Cinematic renderer | TE-017–TE-024 | Materials, atmosphere, appearance presets and resource ownership |
| M3 — The Planet | TE-025–TE-032 | Ten geological anchors and changing land configurations |
| M4 — Civilization | TE-033–TE-040 | Eighteen sourced chapters, camera paths and illustrative overlays |
| M5 — Integrated interactions | TE-041–TE-048 | Playback, timelines, chapters, sources and cancellation all work together |
| M6 — Hardening | TE-049–TE-056 | Responsive layouts, accessibility, resilience and measured optimization |
| M7 — Verification | TE-057–TE-064 | All story states, visual comparisons, stress tests and release-candidate checks |
| M8 — Portfolio release | TE-065–TE-072 | Real media, case study, CI, credits and verified deployment |

## Proposed implementation

React + strict TypeScript + Vite; Three.js through React Three Fiber; small low-frequency state store; a pure narrative engine; CSS-based accessible controls; Vitest and Playwright. Static deployment under `/terra/` is the default target.

Ancient geography is the central engineering challenge. The plan uses independently permitted, model-informed offline masks/intermediates for supported periods, with clearly labeled conceptual early Earth. The runtime does not pretend that blending masks is a physical plate-tectonics solver. Modern city lights appear only in present-day contexts; the 1882 chapter is a localized historical scene.

## Inspiration and scope correction

Jordan supplied [this X post](https://x.com/akshdeeps_001/status/2096776530005488028) and [its video](https://x.com/akshdeeps_001/status/2096776530005488028/video/1), followed by an 83.28-second screen recording. The recording was visually inspected and revealed the two-part narrative experience described above.

An earlier speculative plan proposed an observatory and sunlight lab before the recording was available. **That plan is superseded.** Old TR task IDs remain in Git history, not in the active implementation scope.

The original project's source code, exact framework, font identity, unrecorded panel behavior and mobile implementation were not inspected. Three.js/R3F is Terra's chosen stack, not a verified claim about the original. Terra uses its own branding and original prose, with inspiration credit but no claim of affiliation or permission to reuse the creator's source/assets.

## Sources, interpretation and rights

Earth imagery and reconstruction data need item-specific terms, credits, observation periods and reproducible derivation records. Historical satellite composites are not live imagery. Footprints/routes are illustrative story geography, not population density or political borders. Deep-time scenes are not a climate forecast or an exact reconstruction of every ancient coastline.

The raw reference recording and extracted source frames are not committed or used as runtime assets. Original-code licensing will be finalized during implementation; third-party imagery, models, fonts and icons retain their own terms. See [assets and sources](docs/ASSETS_AND_SOURCES.md).
