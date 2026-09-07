# Terra documentation map

## Current state

This is an implementation-ready **proposal** for Terra, not a finished application or verified reconstruction of the source video. The user supplied the Earth-simulator description and reference links. Direct video inspection and source implementation identification remain unresolved.

## Reading routes

**ASTRA implementation:** `../AGENTS.md` → `ASTRA_GOAL.md` → `REFERENCE_ANALYSIS.md` → `PRODUCT_SPEC.md` → `VISUAL_SPEC.md` → `ARCHITECTURE.md` → `SIMULATION_SPEC.md` → `ROADMAP.md` → `QA_AND_RELEASE.md`.

**Portfolio reviewer:** `../README.md` → `PRODUCT_SPEC.md` → `ARCHITECTURE.md` → `PROGRESS.md`. Once the app exists, actual media and a verified deployment should appear in the root README.

**Asset work:** `ASSETS_AND_SOURCES.md` is authoritative for provenance and acquisition. A candidate source is not an acquired asset.

## Source of truth

| Concern | Canonical document |
| --- | --- |
| User intent, known evidence, unknown reference details | `REFERENCE_ANALYSIS.md` |
| Required product behavior and exclusions | `PRODUCT_SPEC.md` |
| Art direction, screen composition, interaction presentation | `VISUAL_SPEC.md` |
| Technical boundaries and module/API ownership | `ARCHITECTURE.md` |
| Coordinates, units, time, physical interpretation | `SIMULATION_SPEC.md` |
| Task IDs, dependencies, deliverables, task acceptance | `ROADMAP.md` |
| Cross-cutting quality gates and release process | `QA_AND_RELEASE.md` |
| Changes to defaults and why they were made | `DECISIONS.md` |
| Actual progress and verification evidence | `PROGRESS.md` |

## Vocabulary

- **Reference-observed:** actually visible in an inspected source frame, with a timestamp or frame ID.
- **User-described:** supplied by Jordan but not independently verified.
- **Proposed:** chosen for Terra; not attributed to the reference.
- **Derived:** calculated from a documented model or dataset.
- **Artistic:** deliberately adjusted for presentation, not a scientific result.
- **Historical composite:** imagery assembled from observations in a stated period; never live.
- **Core:** the 62 tasks in M0–M7.
- **Extension:** one of TR-080–TR-087; excluded from the initial `/goal` completion gate.

## Change discipline

Update the affected specification, record the decision, and update task acceptance and tests together. Do not let an issue body or an implementation comment silently supersede the coordinate system, scope boundaries, or honesty rules. Never mark progress complete just because the corresponding plan exists.
