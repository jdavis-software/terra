# Architectural and product decisions

All decisions below are proposed implementation defaults established on 2026-09-06. None identify the source video's technology. Change a decision only with a concrete reason, affected task/test updates, and an evidence note.

## ADR-001 — Build a coherent baseline despite inaccessible reference

Choose an Earth observatory plus sunlight lab. The alternative is inventing source-video observations or blocking all useful planning. We reject both. Reference access remains an independent open item. Reconsider the baseline only if actual media demonstrates a materially different desired product; do not silently claim parity.

## ADR-002 — Static client, no backend

A portfolio simulation does not need accounts, a database or an inference service to satisfy its core journey. A static application is easier to reproduce and keep available. Add a backend only for a later explicitly approved requirement with a real need, never as default architectural ceremony.

## ADR-003 — React/Vite with Three.js through React Three Fiber

React serves accessible controls, Vite serves a small client application, and Three.js provides programmable graphics. React Three Fiber helps organize scene lifetime alongside UI. Cesium is a reasonable alternative for terrain/geospatial streaming; it is not selected because core Terra does not require globe-scale map tiling or terrain. A bare Three.js app would also work but offers less consistent React integration for this plan. Next.js/SSR has no core requirement here.

## ADR-004 — WebGL2 baseline; defer WebGPU

Do not build two renderer stacks at once. WebGL2 is the baseline supported by current Three.js WebGLRenderer documentation. A WebGPU experiment belongs to TR-087 after the baseline passes and must preserve a functioning fallback. Shader rewrites require before/after images, compatibility evidence and measured benefit.

## ADR-005 — Earth-fixed coordinates and a single authoritative clock

Keep surface geography fixed; transform the Sun into the Earth-fixed frame. A separate camera director handles presentation motion. This avoids duplicate daily rotation and inconsistent inspector values. All numerical and visual consumers share one simulation snapshot.

## ADR-006 — Provider-backed Earth, explicitly simplified lab

Use a documented astronomy adapter for Earth mode. Use a small, transparent geometric model for hypothetical tilt/season/day-length experiments. Do not turn an artistic parameter slider into a claim of scientific prediction. Exclude weather, atmosphere dynamics and climate feedback from core.

## ADR-007 — Local, credited historical textures

Bundle permitted optimized derivatives so the core app does not depend on remote image hotlinks or runtime credentials. Candidate NASA collections are promising, but individual items still need verification. Credits and observation periods are part of the product, not a final-minute README footnote.

## ADR-008 — Progressive quality, budget before spectacle

Deliver a complete low-resolution planet quickly, then upgrade selected assets. Cap pixel ratio and provide low/medium/high modes. Avoid loading all 8K maps by default. Add postprocessing only after the base material works and performance is measured.

## ADR-009 — Reproducible URL scenes, explicit saved-scene restoration

A portfolio demo should not open broken because an old camera position persisted. URL scenes take precedence; otherwise open the showcase. Persist accessibility/quality preferences independently. A saved scene is restored only through an explicit user action. Imported scenes open paused.

## ADR-010 — Canonical checklist plus milestone issues

Keep 62 detailed core tasks and 8 optional tasks in `ROADMAP.md`; create milestone issues for navigability rather than 70 noisy issues. Issue checklists link to stable task IDs. Progress records evidence; checkbox state alone does not prove completion.

## ADR-011 — Real visual review alongside tests

Unit tests establish model correctness and browser tests establish workflows; neither establishes taste or visual polish alone. A deterministic screenshot baseline must first be visually inspected. Cross-GPU differences and headless rendering limitations need documented treatment rather than false pixel-perfect or FPS claims.

## ADR-012 — GitHub Pages as deployment default

A static build under `/terra/` fits the repository. The app must also support a root base for other hosts. Actual account settings and deploy permissions are external dependencies; the agent must not report a deployment until it is reachable and checked.

## ADR-013 — Code license separated from asset rights

MIT is proposed for original application code. Asset-specific terms remain separate. Planning does not add a license file or claim rights over the source video, NASA imagery, third-party textures or icons.

## Decision change template

```text
Date:
Decision ID:
Previous default:
New decision:
Concrete reason/evidence:
Affected tasks/files:
Tests and visual comparisons rerun:
Compatibility/security/asset-rights impact:
Remaining limitations:
```
