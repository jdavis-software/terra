# Terra

### A cinematic Earth observatory and educational sunlight sandbox.

Terra is a portfolio project for **Jordan Davis**: an interactive, browser-based Earth experience designed to demonstrate graphics engineering, thoughtful interaction design, reproducible simulation, accessibility, and performance discipline.

**Status: planning complete for the proposed Terra baseline; application not implemented.** The original X video could not be retrieved during planning. Its exact appearance, behavior, implementation stack, and feature set have **not** been verified. This repository contains an executable build specification, not a claim of source-code or frame-by-frame reverse engineering.

## The intended experience

Open directly into a beautifully rendered Earth. Orbit from sunlit oceans to illuminated cities, scrub time to move the day/night boundary, inspect places, and explore an explicitly labeled educational lab for axial tilt and seasonal sunlight. Finish with shareable scenes and an interruptible cinematic tour.

The product should feel like an observatory, not a dashboard with a globe bolted on. It must remain useful without accounts, paid APIs, external live feeds, or an AI service at runtime.

## Build with ASTRA

Read [AGENTS.md](AGENTS.md), then use the complete prompt in [docs/ASTRA_GOAL.md](docs/ASTRA_GOAL.md).

```text
/goal Build Terra according to AGENTS.md and docs/ASTRA_GOAL.md.
Implement the 62 core tasks in docs/ROADMAP.md in dependency order,
verify the functional and visual acceptance gates, and maintain
an honest evidence trail in docs/PROGRESS.md. Treat the X video
as unverified until actually inspected. Do not implement optional
extensions until the core release passes.
```

The full goal file includes execution rules, scope boundaries, verification requirements, and completion criteria. Commands described in the specification are **future implementation contracts**, not commands that work in this planning-only repository yet.

## Planning documents

| Document | Purpose |
| --- | --- |
| [Documentation index](docs/README.md) | Reading order and specification precedence |
| [Reference analysis](docs/REFERENCE_ANALYSIS.md) | Evidence ledger, access limitations, reconstruction strategy |
| [Product specification](docs/PRODUCT_SPEC.md) | Core experience, behavior, scope, user journeys |
| [Visual specification](docs/VISUAL_SPEC.md) | Layout, tokens, camera composition, visual acceptance targets |
| [Architecture](docs/ARCHITECTURE.md) | Stack, module ownership, data flow, rendering and state contracts |
| [Simulation specification](docs/SIMULATION_SPEC.md) | Coordinates, clocks, Sun direction, lab model, numerical tests |
| [Assets and sources](docs/ASSETS_AND_SOURCES.md) | Primary references, asset provenance, acquisition and licensing checks |
| [Implementation roadmap](docs/ROADMAP.md) | 62 core tasks, 8 optional tasks, dependencies and acceptance tests |
| [QA and release](docs/QA_AND_RELEASE.md) | Browser tests, performance budgets, deployment and release gates |
| [ASTRA goal](docs/ASTRA_GOAL.md) | Copy-ready autonomous implementation prompt |
| [Decisions](docs/DECISIONS.md) | Chosen defaults, alternatives and conditions for changing course |
| [Progress](docs/PROGRESS.md) | Current implementation status, evidence and handoff ledger |

## Proposed stack

React + TypeScript + Vite, Three.js with React Three Fiber, narrowly scoped Drei helpers, Zustand for low-frequency application state, Astronomy Engine behind an adapter, Vitest, and Playwright. WebGL2 is the baseline; WebGPU is an optional later experiment. Exact compatible versions must be verified and pinned during bootstrap.

A static build is the deployment target. GitHub Pages under `/terra/` is the planned default; provider configuration and a successful public deployment are not claimed by this planning repository.

## Roadmap at a glance

| Milestone | Core tasks | Exit result |
| --- | --- | --- |
| M0 — Evidence and feasibility | TR-001–TR-006 | Honest reference status, viable assets and locked contracts |
| M1 — Working vertical slice | TR-010–TR-017 | A real, navigable Earth in the browser |
| M2 — Cinematic Earth rendering | TR-020–TR-027 | Day/night, clouds, atmosphere and texture quality |
| M3 — Time and sunlight simulation | TR-030–TR-037 | Correct clock, solar direction and educational lab |
| M4 — Exploration and inspection | TR-040–TR-047 | Search, picking, camera transitions and useful readouts |
| M5 — Showcase interactions | TR-050–TR-057 | Tour, photo mode, scene sharing and polished controls |
| M6 — Hardening | TR-060–TR-067 | Performance, accessibility and robust failure handling |
| M7 — Verification and portfolio release | TR-070–TR-077 | Tested build, real media, documented deployment and release |

Optional work TR-080–TR-087 is not part of the core completion gate. See the roadmap for exact dependencies and definitions of done.

## Inspiration and attribution

The user supplied [this X post](https://x.com/akshdeeps_001/status/2096776530005488028) and [its video link](https://x.com/akshdeeps_001/status/2096776530005488028/video/1) as inspiration. Credit the reference author without implying collaboration, affiliation, permission to reuse assets, or that Terra is the original project.

Candidate Earth imagery comes from NASA collections, subject to item-specific credit and usage checks. Historical image composites must never be labeled as live Earth imagery. Third-party assets retain their own terms. See [asset provenance requirements](docs/ASSETS_AND_SOURCES.md).

## Scientific honesty

Terra is an interactive visualization and educational sunlight model, **not** a climate predictor, weather forecast, geodetic survey, navigation system, or validated orbital mission tool. The lab deliberately changes simplified parameters; its results must be labeled accordingly. Artistic atmosphere and cloud effects do not constitute atmospheric physics.

## License

The proposed license for original application code is MIT, to be finalized during implementation. No license grant over third-party imagery, reference videos, or other external assets is implied. This planning commit does not add a `LICENSE` file.
