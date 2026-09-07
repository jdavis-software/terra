# Terra documentation — active v2

The current project is a recording-inspired cinematic Earth/history website: **ten Planet anchors and eighteen Civilization chapters**. The earlier observatory/sunlight-lab plan is retired. Active task IDs are **TE-001–TE-072**. The app is not implemented by this planning revision.

**Execution tracking:** [master issue #12](https://github.com/jdavis-software/terra/issues/12) and the [nine-epic issue map](ISSUE_INDEX.md).

## Reading order

For implementation: [AGENTS](../AGENTS.md) → [ASTRA goal](ASTRA_GOAL.md) → [recording analysis](REFERENCE_ANALYSIS.md) → [product](PRODUCT_SPEC.md) / [visuals](VISUAL_SPEC.md) / [story catalogue](STORY_CONTENT.md) → [story engine](SIMULATION_SPEC.md) / [architecture](ARCHITECTURE.md) / [assets](ASSETS_AND_SOURCES.md) → [roadmap](ROADMAP.md) / [QA](QA_AND_RELEASE.md) → [progress](PROGRESS.md).

| Concern | Source of truth |
| --- | --- |
| Actual visible source evidence and unknowns | [REFERENCE_ANALYSIS.md](REFERENCE_ANALYSIS.md) |
| Recording identity, metadata and inspection limits | [reference/recording-manifest.json](reference/recording-manifest.json) |
| Required screens and interaction outcomes | [PRODUCT_SPEC.md](PRODUCT_SPEC.md) |
| Composition, typography, globe presentation and visual gates | [VISUAL_SPEC.md](VISUAL_SPEC.md) |
| Ten geological and eighteen human records | [STORY_CONTENT.md](STORY_CONTENT.md) |
| Coordinates, narrative time, date conventions and state invariants | [SIMULATION_SPEC.md](SIMULATION_SPEC.md) |
| Stack, module boundaries and resource ownership | [ARCHITECTURE.md](ARCHITECTURE.md) |
| Acquisition, model limits, licensing and provenance | [ASSETS_AND_SOURCES.md](ASSETS_AND_SOURCES.md) |
| Canonical task IDs/dependencies/acceptance | [ROADMAP.md](ROADMAP.md) |
| GitHub epic and master-tracker navigation | [ISSUE_INDEX.md](ISSUE_INDEX.md) |
| Cross-cutting tests, performance and release gates | [QA_AND_RELEASE.md](QA_AND_RELEASE.md) |
| Why defaults changed and when to reconsider them | [DECISIONS.md](DECISIONS.md) |
| Actual implementation and verification status | [PROGRESS.md](PROGRESS.md) |

`ASTRA_REFERENCE_FIRST_GOAL.md` is a compatibility entry point to the current goal. `REFERENCE_RECONSTRUCTION_TASKS.md` records residual source unknowns; it is no longer an instruction to keep retrying an inaccessible X video.

## Precedence and evidence vocabulary

User requirements and honest source representation come first. Product scope and the story catalogue define the required experience; numerical/state contracts define correct behavior; the visual specification defines presentation; the roadmap defines execution. Resolve material conflicts in DECISIONS.md and update tests together rather than silently adding a second behavior.

**Observed** means visible in an inspected recording frame/window. **Demonstrated** means a before/after interaction is visible, not that the live application was exhaustively tested. **Proposed** means Terra's implementation choice. **Conceptual** and **model-informed** distinguish artistic early Earth from bounded reconstruction data. **Verified complete** requires actual implementation and test evidence, not just a written specification.

The source's typography family, source code, exact algorithms, comments and unrecorded mobile/panel behavior remain unknown. Keep those limits distinct from the now-completed visual recording review.
