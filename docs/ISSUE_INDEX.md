# Terra v2 GitHub execution map

The canonical definitions are in [ROADMAP.md](ROADMAP.md): **72 core tasks, TE-001–TE-072**. The issues below organize them into nine eight-task epics. They are issue checklists, not a claim that GitHub milestone objects or completed application tasks exist.

**[Master build tracker — #12](https://github.com/jdavis-software/terra/issues/12)** contains the full epic checklist and launch prompt. Start implementation from [AGENTS.md](../AGENTS.md) and [ASTRA_GOAL.md](ASTRA_GOAL.md).

| Epic | GitHub issue | Canonical tasks | Exit result |
| --- | --- | --- | --- |
| M0 — Evidence and feasibility | [#1](https://github.com/jdavis-software/terra/issues/1) | TE-001–TE-008 | Recording-based scope, viable assets and stable contracts |
| M1 — Real opening slice | [#2](https://github.com/jdavis-software/terra/issues/2) | TE-009–TE-016 | Editorial opening and live navigable Earth |
| M2 — Cinematic renderer | [#3](https://github.com/jdavis-software/terra/issues/3) | TE-017–TE-024 | Materials, atmosphere, appearance and bounded assets |
| M3 — The Planet | [#6](https://github.com/jdavis-software/terra/issues/6) | TE-025–TE-032 | Ten geological anchors and changing continents |
| M4 — Civilization | [#8](https://github.com/jdavis-software/terra/issues/8) | TE-033–TE-040 | Eighteen chapters, camera paths and illustrative footprints |
| M5 — Integrated interaction | [#9](https://github.com/jdavis-software/terra/issues/9) | TE-041–TE-048 | Coherent playback, navigation, sources and input |
| M6 — Hardening | [#10](https://github.com/jdavis-software/terra/issues/10) | TE-049–TE-056 | Responsive/accessibility/resilience and measured optimization |
| M7 — Verification | [#11](https://github.com/jdavis-software/terra/issues/11) | TE-057–TE-064 | All-state tests and recording-to-render review |
| M8 — Portfolio release | [#13](https://github.com/jdavis-software/terra/issues/13) | TE-065–TE-072 | Real media, credits, CI and verified public deployment |

## Evidence status

[Recording-analysis issue #4](https://github.com/jdavis-software/terra/issues/4) is closed because the supplied recording was visually inspected and the analysis/tasklist delivered. This does not close implementation fidelity, original source-code verification, asset licensing or deployment. Read its explicit remaining limits.

Issues #5 and #7 are historical duplicates; their closure is not proof that any build task was completed. Existing M0–M7 issues were updated in place to prevent duplicate active checklists. M8 was added. Old TR/RF references in historical comments do not override the active TE roadmap.

## Update discipline

Complete a task only after its acceptance criteria pass and evidence is recorded in [PROGRESS.md](PROGRESS.md). Update its canonical roadmap checkbox and corresponding epic checkbox together. Close an epic only when all of its required tasks are verified complete; do not convert a deployment permission blocker into a success. Update the master epic checklist only after the underlying issue's evidence supports closure.

The recording-based specification was published at commit `98927d65265558aa576f38923c5b79ff850150d8`. Always read the latest repository state and preserve later user changes before beginning work.
