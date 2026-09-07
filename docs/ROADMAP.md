# Terra v2 implementation roadmap

## Execute this version

**72 core tasks, TE-001–TE-072, in nine eight-task epics.** This replaces the 62-task observatory/sunlight-lab plan. Old TR IDs remain in Git history for traceability, not as implementation requirements. All TE tasks begin unchecked; the recording analysis and specification are completed planning deliverables, not proof of implemented code.

Read AGENTS.md, ASTRA_GOAL.md and the linked specifications first. Each task below has dependencies, intended files, work and acceptance evidence. `PROGRESS.md` records actual status, commands, screenshots, commits and blockers. Do not create 72 separate issues by default: the GitHub epic checklists organize these canonical tasks.

**Core result:** ten geological anchors, eighteen human chapters, both introductions, all visible primary controls, original narrative copy, independently permitted assets, responsive/accessibility paths, real tests and a verified portfolio release. No solar lab, generic location dashboard, backend or AI API is required.

```mermaid
flowchart LR
  M0[M0 Evidence and feasibility] --> M1[M1 Real opening slice]
  M1 --> M2[M2 Cinematic renderer]
  M2 --> M3[M3 Planet history]
  M2 --> M4[M4 Civilization]
  M3 --> M5[M5 Integrated interactions]
  M4 --> M5
  M5 --> M6[M6 Responsive and resilient]
  M6 --> M7[M7 Verification]
  M7 --> M8[M8 Portfolio release]
```

Task dependencies permit isolated content/math work before the visual integration milestone. One owner integrates shared state, camera and renderer. Use separate worktrees for independent work, never simultaneous writes to the same lockfile or contract. A stage that fails its exit gate is not complete because its code compiles.

## M0 — Evidence, assets and implementation contracts

**Exit:** the implementer understands the actual recording, has a feasible asset path and a locked, coherent scope.

### TE-001 — Establish a safe implementation baseline
- [ ] Verified complete.
- **Depends:** none. **Files:** `docs/PROGRESS.md`, task branch/worktree.
- **Work:** inspect current repository, branch, existing implementation and uncommitted changes. Record the starting commit. Reuse legitimate existing code if another session has advanced the repository; do not overwrite it with a scaffold.
- **Accept / verify:** a safe isolated worktree or branch exists, user changes are preserved, and no unrelated project/global configuration is changed. Record the baseline and selected next task without private machine paths.

### TE-002 — Consume the recording analysis and lock reference scope
- [ ] Verified complete.
- **Depends:** TE-001. **Files:** `docs/REFERENCE_ANALYSIS.md`, `docs/DECISIONS.md`.
- **Work:** review the timestamp ledger, recording manifest, ten Planet keys and eighteen Civilization chapters. Inspect actual reference frames when available. Explicitly retire the solar-lab concept and distinguish visible controls from untested panel behavior.
- **Accept / verify:** scope is the two-journey website, not a generic simulator. Do not repeat endless X-access attempts or claim original source-code/stack inspection. Log material ambiguities before implementation.

### TE-003 — Prove permitted modern and historical asset sources
- [ ] Verified complete.
- **Depends:** TE-002. **Files:** `docs/ASSETS_AND_SOURCES.md`, acquisition records.
- **Work:** identify exact usable day/night items, cloud/mask options and one supported reconstruction dataset. Check item terms, credits, projection, supported ages and downloadable representations. Establish a procedural fallback only for explicitly conceptual early Earth.
- **Accept / verify:** concrete source files can be acquired and redistributed as intended, or a precise blocker is recorded. No hotlinks to the creator's app, invented license, raw recording upload or unsupported 4.54 Ga reconstruction claim.

### TE-004 — Select and verify a compatible toolchain
- [ ] Verified complete.
- **Depends:** TE-001. **Files:** `docs/DECISIONS.md`, toolchain notes.
- **Work:** verify compatible stable Node, pnpm, React, Vite, TypeScript, Three.js and R3F versions using current official package/documentation information. Choose narrow helper/test dependencies and one package manager.
- **Accept / verify:** peer requirements and runtime constraints are documented before installation; no independently selected incompatible major versions, floating production tags or unnecessary backend/AI dependencies. Exact installation proof follows in TE-009.

### TE-005 — Establish full-screen visual targets
- [ ] Verified complete.
- **Depends:** TE-002. **Files:** `docs/VISUAL_SPEC.md`, permitted local design references.
- **Work:** define desktop opening, Civilization chapter and mobile compositions from the recording. Lock type, globe scale/position, date placement, rail, CTA colors and panel language. Mobile/open-panel designs are original Terra completions, not observed reference states.
- **Accept / verify:** targets cover the full app surface, not a marketing hero. Record five concrete visual criteria and direct reference comparisons. Do not call an agent-selected design user-approved without approval.

### TE-006 — Freeze content IDs and domain schemas
- [ ] Verified complete.
- **Depends:** TE-002. **Files:** `src/story/types.ts`, `src/data/*`, schema notes.
- **Work:** define exactly P01–P10, C01–C18 and unnumbered intros; structured historical dates, source IDs, camera/overlay keys, appearance permissions and tagged story state. Keep overlapping date ranges and authored order.
- **Accept / verify:** no nineteenth chapter, duplicated IDs, implicit JavaScript Date chronology or solar-lab fields. Draft records can remain clearly pending until content review; schema validation must reject invalid production records.

### TE-007 — Prove low-resolution changing-continent feasibility
- [ ] Verified complete.
- **Depends:** TE-003. **Files:** `scripts/assets/`, reconstruction proof records.
- **Work:** obtain a permitted pinned-model sample for Pangea, breakup and modern geography. Produce canonical low-resolution land/coastline masks or equivalent inspectable previews offline; verify model/frame/layer meaning. Test an intermediate blend concept before committing to a large asset set.
- **Accept / verify:** three genuinely different plausible land configurations exist with provenance. Modern-map recoloring, plate polygons mislabeled coastlines and unsupported epochs fail. A documented image/mask proof suffices here; the browser shader is TE-030.

### TE-008 — Reconcile and freeze the build contract
- [ ] Verified complete.
- **Depends:** TE-003, TE-004, TE-005, TE-006, TE-007. **Files:** `docs/DECISIONS.md`, `docs/PROGRESS.md`.
- **Work:** reconcile visual scope, dataset limits, quality budgets, clocks, coordinate system, content provenance, initial states and deployment target. Map unresolved risks to tasks and select a vertical-slice plan.
- **Accept / verify:** no contradictory old TR requirement remains active. Data access/licensing failures have an explicit consequence, not a fake success. The next implementation task can proceed without inventing a different product.

## M1 — A real opening-screen vertical slice

**Exit:** today's Earth renders, the editorial composition resembles the recording, and real orbit/zoom works.

### TE-009 — Bootstrap the single application
- [ ] Verified complete.
- **Depends:** TE-008. **Files:** `package.json`, lockfile, TypeScript/Vite config, `index.html`, runtime pins.
- **Work:** initialize the verified React/TypeScript/Vite stack, strict typing, base-path configuration and minimal app. Pin the package manager and document runtime requirements. Avoid a monorepo or unused server scaffold.
- **Accept / verify:** clean install and production build succeed with one lockfile. Record versions and command results. `/terra/` and configurable root-base behavior are designed in, not patched through hardcoded absolute asset paths.

### TE-010 — Implement meaningful development checks
- [ ] Verified complete.
- **Depends:** TE-009. **Files:** lint config, Vitest config, package scripts, initial tests.
- **Work:** implement lint, typecheck, unit tests and documentation checks, with a real schema/state smoke test. Define fail-fast `check` composition and future asset/content validators without echo-success stubs.
- **Accept / verify:** actual work executes; a deliberate temporary negative fixture fails with nonzero status. Remove the deliberate failure afterward and record positive outputs. Browser tests are added as real scenes become available.

### TE-011 — Build the accessible editorial app shell
- [ ] Verified complete.
- **Depends:** TE-009, TE-005. **Files:** `src/app/`, `components/ui/`, styles.
- **Work:** implement terra. branding, two-section navigation, Sources, left story region, upper-right date, bottom rail region and appearance/transport controls. Use shared tokens, semantic DOM and stable layout dimensions.
- **Accept / verify:** no dashboard cards, login, fake counters or copied source branding. At 1440×900 and 1280×800, type and control placement follow the target without clipping. Label unfinished controls honestly during this slice; they cannot ship inert.

### TE-012 — Initialize the renderer and capability states
- [ ] Verified complete.
- **Depends:** TE-009. **Files:** `scene/GlobeCanvas.tsx`, capability/error helpers.
- **Work:** create one WebGL2 renderer/scene with bounded DPR, proper resize handling and error boundaries. Define a revision-aware scene-ready signal for tests after an actual render. Add a basic non-WebGL explanation pending the full fallback.
- **Accept / verify:** a real scene appears and survives resize; no duplicate contexts on ordinary UI changes. Capture renderer/browser details and test the unavailable-capability path. A DOM-mounted canvas alone does not count as ready.

### TE-013 — Implement the coordinate and UV contract
- [ ] Verified complete.
- **Depends:** TE-010, TE-012. **Files:** `src/geo/coordinates.ts`, sphere/UV helper, unit fixtures.
- **Work:** implement Y-up, east-positive coordinate conversion and a single documented equirectangular orientation. Handle date-line wrapping, poles and seam vertices. Use the same mapping for future camera/marker code.
- **Accept / verify:** numerical anchors and nonpolar round trips pass. A diagnostic map is north-up and not mirrored; seam/pole checks pass. Remove temporary labels before release, retaining tests and a concise orientation note.

### TE-014 — Render an approved modern preview Earth
- [ ] Verified complete.
- **Depends:** TE-003, TE-012, TE-013. **Files:** preview asset/manifest, `scene/Surface.tsx`.
- **Work:** load a permitted small modern texture through base-relative paths, assign correct color space and fit the globe to the opening composition. Preserve exact source/hash/credit for the preview.
- **Accept / verify:** continents are identifiable and aligned, Africa/Europe can be framed like the reference, and no placeholder generated globe image substitutes for geometry. Inspect actual browser screenshots and the network request under the chosen base path.

### TE-015 — Add reliable orbit, zoom and reset
- [ ] Verified complete.
- **Depends:** TE-011, TE-014. **Files:** `scene/camera/`, input adapter, zoom controls.
- **Work:** implement one camera owner, pointer orbit, plus/minus zoom and reset with safe distance/pole limits. Separate camera movement from historical time. Reserve wheel behavior for story travel rather than conflicting automatic zoom.
- **Accept / verify:** controls do not fight, panels do not rotate Earth, and the camera cannot enter the sphere. Verify mouse/trackpad/button use, cancellation hooks, resize and keyboard zoom/reset. Record a short interaction capture.

### TE-016 — Pass the opening visual-slice gate
- [ ] Verified complete.
- **Depends:** TE-010–TE-015. **Files:** browser smoke test, visual evidence, `PROGRESS.md`.
- **Work:** run the actual production build, compare opening composition against the recording, and fix globe scale, lighting direction, typography, CTA placement and timeline spacing before expanding features.
- **Accept / verify:** real globe/orbit/zoom/reset and legible editorial shell pass at two desktop sizes plus a mobile smoke viewport. Record at least five concrete comparisons and fixes. A generic-looking globe demo does not pass merely because compilation succeeds.

## M2 — Cinematic rendering and bounded assets

**Exit:** modern Earth, appearance presets and resource ownership are credible without relying on bloom to conceal defects.

### TE-017 — Build the progressive asset manager
- [ ] Verified complete.
- **Depends:** TE-014, TE-010. **Files:** `src/assets/manager.ts`, manifest types, loader tests.
- **Work:** implement request deduplication, preview-to-quality upgrades, cancellation generations, bounded cache and ownership. Distinguish downloaded, decoded, GPU-ready and active states. Keep local base-relative URLs.
- **Accept / verify:** delayed/out-of-order responses cannot overwrite a newer request. Old assets remain valid until replacement readiness, then are released. Test cache bounds, retries and honest progress stages with controlled fake loaders.

### TE-018 — Finish the modern surface shader
- [ ] Verified complete.
- **Depends:** TE-017. **Files:** `scene/materials/modern-earth*`, surface component.
- **Work:** implement coherent albedo, directional illumination and historical night emission using a shared coordinate frame. Use correct linear/sRGB handling and one output/tone-mapping conversion. Keep city emission independently controllable by story policy.
- **Accept / verify:** day/night maps align, the surface is neither washed out nor doubly gamma-corrected, and daytime emission is suppressed. Compare close/wide day/night screenshots with fixed camera and light settings.

### TE-019 — Tune oceans and directional lighting
- [ ] Verified complete.
- **Depends:** TE-018, TE-003. **Files:** surface uniforms, ocean-mask derivation, appearance config.
- **Work:** add a controlled water highlight using a valid mask or an explicit conservative fallback. Tune roughness, ambient fill and light direction to preserve the reference's readable Earth and dramatic contrast.
- **Accept / verify:** highlights do not cover whole continents, land does not gleam like water, and baked source shading does not imply a second contradictory Sun. Inspect multiple orientations and document any omitted unreliable map.

### TE-020 — Add a separate cloud layer
- [ ] Verified complete.
- **Depends:** TE-017, TE-018. **Files:** `scene/Clouds.tsx`, cloud material.
- **Work:** use a permitted map or original procedural field with correct alpha/color interpretation, shell spacing, lighting and deterministic artistic drift. Clouds must not intercept geographic input intended for the globe.
- **Accept / verify:** no black fringes, clipping, obvious seam, doubled opaque planet or cloud cover obscuring every historical state. Pause/reduced-motion behavior is controllable. Record identical-seed captures and layer-off comparison.

### TE-021 — Build the restrained atmosphere
- [ ] Verified complete.
- **Depends:** TE-018. **Files:** `scene/Atmosphere.tsx`, material/constants.
- **Work:** implement a thin view-angle/light-weighted atmospheric shell, tuned to the reference's blue limb. Keep its artistic status explicit and distinguish it from geological atmospheric-history claims.
- **Accept / verify:** the limb follows the sphere, is weaker where appropriate on the dark side, and is not a detached neon ring. Test wide/close views and all planned appearance presets without depth-order artifacts.

### TE-022 — Implement appearance presets and emission policy
- [ ] Verified complete.
- **Depends:** TE-018–TE-021, TE-006. **Files:** appearance config, segmented controls, policy tests.
- **Work:** wire Natural/After dark/Blue hour in Planet and Natural/After dark in Civilization. Separate presentation choices from age. Centralize permission for modern global city emission at P10/Today and C18 only.
- **Accept / verify:** changing appearance preserves story/camera; forbidden combinations recover predictably. A test attempts After dark on every ancient chapter and observes no modern global lights. C17 remains a local effect later implemented in TE-039.

### TE-023 — Finish background and visual hierarchy
- [ ] Verified complete.
- **Depends:** TE-021, TE-011. **Files:** `scene/Space.tsx`, stage fades, visual tokens.
- **Work:** create a nearly black, sparse, seeded space background and subtle narrative-side contrast treatment. Keep the planet focal and UI sharp. Evaluate optional bloom only if the base scene already works.
- **Accept / verify:** no dense decorative wallpaper, stars through Earth, unreadable story copy or heavy full-screen blur. Compare base/postprocessed variants and retain only measurable, visible improvements with a lower-quality fallback.

### TE-024 — Verify rendering quality tiers and resource lifecycle
- [ ] Verified complete.
- **Depends:** TE-017–TE-023. **Files:** quality config, lifecycle tests, resource report.
- **Work:** define useful low/medium/high tiers, DPR caps and bounded texture residency; test remounts and upgrades. Dispose materials, geometries, textures, targets and workers according to actual ownership.
- **Accept / verify:** switching quality preserves story/camera without a blank globe. After warm-up, repeated switches do not produce an ever-growing resource count. Report texture estimates separately from measured browser data; no fabricated total-GPU-memory metric.

## M3 — The Planet: real geological story progression

**Exit:** all ten anchors and continuous narrative scrubbing work with distinct era-appropriate surfaces.

### TE-025 — Implement piecewise geological time mapping
- [ ] Verified complete.
- **Depends:** TE-006, TE-010. **Files:** `story/geological-mapping.ts`, formatter/tests.
- **Work:** map normalized positions i/9 to the ten descending Ma values, implement inverse mapping, endpoint handling and stable Ga/Ma/Today formatting. Store narrative thresholds explicitly.
- **Accept / verify:** exact anchor and random round trips pass; ages remain finite/nonnegative; positive ages do not become Today through rounding. Clearly identify the rail as story-paced rather than proportional elapsed years. No JavaScript Date or unspecified logarithmic transform.

### TE-026 — Author and review all ten Planet narratives
- [ ] Verified complete.
- **Depends:** TE-006, TE-003. **Files:** planet data, source records, content validator.
- **Work:** write original concise copy for P01–P10 and intro/finale variants; verify milestone framing, dates and uncertainty with authoritative sources. Attach interpretation labels: conceptual, model-informed or modern reference.
- **Accept / verify:** ten valid unique keys, reviewed claims and exact source links exist. Early oceans/oxygen/ice dates are not presented as exact event-years or climate predictions. No copied reference prose or placeholder citations pass release validation.

### TE-027 — Build the conceptual early-Earth sequence
- [ ] Verified complete.
- **Depends:** TE-024, TE-025, TE-026. **Files:** `materials/early-earth*`, early-epoch parameters.
- **Work:** implement seeded dark crust/lava, cooling and ocean emergence, then atmospheric appearance progression. Use seam-safe noise and explicit conceptual surface parameters instead of modern continents under a red overlay.
- **Accept / verify:** P01–P03 look materially different and transition coherently; modern cities stay off. Random seeking reproduces the same state. Document artistic choices and inspect formation/midpoint/ocean screenshots against recording cues.

### TE-028 — Implement the ice-world state
- [ ] Verified complete.
- **Depends:** TE-024, TE-026. **Files:** ice mask/material parameters, era metadata.
- **Work:** build a visually distinct extensive-ice state and transitions to neighboring ocean/ancient-world keys. Preserve shell depth and ocean readability where appropriate.
- **Accept / verify:** the glacier/ice appearance affects the planet, not the UI; it is not a plain white overlay disguising unchanged modern geography. Show an illustrative-extent limitation, avoid temperature metrics, and verify scrubbing into/out of the state without flashes.

### TE-029 — Produce the model-informed ancient-world asset set
- [ ] Verified complete.
- **Depends:** TE-007, TE-017, TE-026. **Files:** offline reconstruction/rasterization scripts, masks, manifest.
- **Work:** generate a bounded set of permitted 650–0 Ma samples/intermediates using one pinned supported model/frame. Record age, layer meaning, projection, hashes and derivation. Inspect ancient seas, convergence, Pangea, breakup, late oceans and present alignment.
- **Accept / verify:** correct land configurations change across keys; no unsupported epoch extrapolation or plate-boundary-as-coastline substitution. Asset verification passes and all public derivatives have explicit rights/provenance.

### TE-030 — Integrate smooth, cancellable geological transitions
- [ ] Verified complete.
- **Depends:** TE-025, TE-027–TE-029. **Files:** paleo material, scene projection, transition manager.
- **Work:** blend canonical masks/SDFs and appearance parameters with sufficient intermediates to avoid obvious double-continent ghosts. Integrate latest-request-wins loading, correct-era previews and buffering when required.
- **Accept / verify:** rapid forward/backward seeks never show a stale era under a new date. Midpoints visibly change land without transparent duplicate globes. Label the technique illustrative, not physical plate simulation. Capture the Pangea-to-breakup-to-present proof in-browser.

### TE-031 — Wire the Planet rail and transport
- [ ] Verified complete.
- **Depends:** TE-025, TE-030, TE-011. **Files:** `features/planet/`, story runtime/reducer.
- **Work:** implement ten labeled stops, continuous pointer/keyboard scrub, age readout, Go back in time, Play/Pause and Back to today. Use anchored monotonic time and defined intro/completion behavior.
- **Accept / verify:** text, active key, age and world derive from one position. Scrubbing pauses; play is frame-rate independent; endpoints clamp; buffering re-anchors without jumps. The present intro and finale reuse P10 without adding an extra stop.

### TE-032 — Pass the full ten-anchor Planet gate
- [ ] Verified complete.
- **Depends:** TE-026–TE-031. **Files:** Planet E2E fixtures, visual evidence.
- **Work:** traverse all ten anchors forward/backward at multiple speeds, seek between keys and check each visible state. Review formation, ice, ancient geography, Pangea, breakup and modern Earth against the recording.
- **Accept / verify:** all ten states are distinct and source-labeled, all timeline controls function, and no stale texture/date mismatch or premodern city emission occurs. Fix visual defects rather than approving a wrong screenshot baseline.

## M4 — Civilization: eighteen complete chapters

**Exit:** the entire recorded human-story sequence exists with reviewed copy, purposeful geography and rewind-safe overlays.

### TE-033 — Author and source chapters C01–C06
- [ ] Verified complete.
- **Depends:** TE-006, TE-003. **Files:** civilization content/sources, site data.
- **Work:** complete Africa, White Sands, cultivation, Uruk, Giza and Mohenjo-daro. Verify dates/coordinates with exact primary or site-authority sources and write original 35–65-word narratives.
- **Accept / verify:** broad origins and multiple agricultural pathways are respected; Uruk is not an unsupported unique first. Every claim/source link and precise site coordinate is reviewable. Pending content cannot pass the release validator.

### TE-034 — Author and source chapters C07–C12
- [ ] Verified complete.
- **Depends:** TE-006, TE-003. **Files:** civilization content/sources, routes/site data.
- **Work:** complete Eurasian exchange, Teotihuacan, Cahokia, Polynesian voyaging, northern Chinese walls and Machu Picchu. Preserve recorded order and overlapping ranges.
- **Accept / verify:** routes are illustrative networks, Teotihuacan is not mislabeled Aztec-built, Indigenous histories are represented, and Ming/Polynesian chapter periods are not falsely treated as the beginning of all related history. Source and coordinate checks pass.

### TE-035 — Author and source chapters C13–C18
- [ ] Verified complete.
- **Depends:** TE-006, TE-003. **Files:** civilization content/sources, final chapter data.
- **Work:** complete Timbuktu, 1492 Atlantic contact, Philadelphia 1776, industrialization, Pearl Street 1882 and today's night world. Include regional specificity and the limitations of historical image composites.
- **Accept / verify:** 1492 acknowledges existing societies and consequences; 1776 does not erase slavery/exclusion; 1882 is localized. No fabricated global electrification/population claims. Final copy and exact source links receive an editorial review.

### TE-036 — Build chapter-specific camera choreography
- [ ] Verified complete.
- **Depends:** TE-015, TE-033–TE-035. **Files:** camera presets/director/path tests.
- **Work:** create meaningful poses for all eighteen chapters, using unit-direction interpolation and separate radius with deterministic antipodal handling. Fit the date/story layout without losing the geographic subject.
- **Accept / verify:** each final pose exposes its intended region; no through-Earth path, pole flip, abrupt date-line jump or competing orbit controller. Manual input cancels cleanly. Inspect every chapter's final frame, not just Africa and Europe.

### TE-037 — Render sites, regions, routes and labels
- [ ] Verified complete.
- **Depends:** TE-013, TE-033–TE-035, TE-024. **Files:** `scene/overlays/`, occlusion/route math.
- **Work:** add subtle current-site halos, geographic labels, broad illustrative regions and a few story-network arcs. Implement finite-camera Earth occlusion, viewport clipping and label collision handling.
- **Accept / verify:** far-side geometry/text does not show through Earth; labels do not obscure the main story or become a pin forest. Region/route data are not presented as political borders, traffic or population density. Test limb and antimeridian cases.

### TE-038 — Implement the human-footprint card and rewind rules
- [ ] Verified complete.
- **Depends:** TE-037, TE-006. **Files:** footprint UI, pure overlay membership selector/tests.
- **Work:** build current-story-regions and earlier-story-sites toggles with a concise illustrative-data disclaimer. Derive the visible set solely from active chapter and preferences, not an irreversible visited-sites accumulator.
- **Accept / verify:** toggles actually change independent layers. Seeking backward removes future features; repeated random chapter orders produce the same final set. Disabled/current states are accessible and visually understated like the recording.

### TE-039 — Distinguish local electrification from the modern finale
- [ ] Verified complete.
- **Depends:** TE-022, TE-035, TE-036, TE-037. **Files:** chapter appearance policy, local light effect, finale config.
- **Work:** stage a localized Pearl Street pulse for C17 and a deliberate pullback/city-emission reveal at C18. Connect the night texture's historical observation-period credit.
- **Accept / verify:** global modern lights cannot appear in C01–C17 even when After dark is selected. C18 shows recognizable fine city patterns without excessive bloom. Rewinding from C18 immediately removes forbidden emission.

### TE-040 — Integrate the intro and eighteen-chapter journey
- [ ] Verified complete.
- **Depends:** TE-033–TE-039, TE-031. **Files:** Civilization intro/rail/narrative, story reducer/runtime.
- **Work:** connect the unnumbered introduction, all eighteen authored records, count, date, camera and overlays to the shared transport. Preserve approximate/range labels instead of interpolating fabricated precise dates.
- **Accept / verify:** intro is not chapter nineteen, the visible counter matches the selected ID, and all chapters are reachable in both directions. Dates with overlapping ranges remain in editorial order. Playback completion stops at C18.

## M5 — Complete interaction and narrative integration

**Exit:** the app behaves as one coherent product, with no disconnected controls or competing animations.

### TE-041 — Unify playback and speed controls
- [ ] Verified complete.
- **Depends:** TE-031, TE-040. **Files:** shared transport controls, speed menu/runtime tests.
- **Work:** connect both visible Play/Pause locations to one state, implement 1×/2×/5×, replay/end states and continuous speed changes. Bound camera transition duration so fast playback still reaches each subject.
- **Accept / verify:** no duplicate timers or divergent button labels. Pause freezes story progress; a speed change never jumps position. Verify both controls, all speeds, buffering and completion using a fake monotonic clock plus a real browser.

### TE-042 — Resolve wheel, drag, touch and panel input ownership
- [ ] Verified complete.
- **Depends:** TE-015, TE-031, TE-040. **Files:** input routing adapter, interaction tests.
- **Work:** implement stage-wheel time travel, debounced Civilization chapter steps, timeline pointer capture, globe orbit and touch pinch. Keep plus/minus zoom; preserve browser Ctrl/Cmd zoom and normal panel/page scrolling.
- **Accept / verify:** one gesture never both scrubs and orbits/zooms. Manual globe input cancels scripted camera and pauses story before applying input. Test trackpad bursts, touch cancellation, drag release outside the rail and focused form controls.

### TE-043 — Build All chapters and previous/next navigation
- [ ] Verified complete.
- **Depends:** TE-040, TE-011. **Files:** `features/story/ChapterDrawer.tsx`, navigation tests.
- **Work:** show all eighteen titles, date labels and regions in an accessible drawer/dialog, with active state and keyboard focus management. Selecting a row closes the drawer and enters that chapter paused.
- **Accept / verify:** all entries are actionable, previous/next clamps at the ends and no hidden wrap creates a nonexistent chapter. Focus returns predictably. The panel's detailed design is explicitly a Terra completion, since the recording does not show it open.

### TE-044 — Build Sources and contextual story explanations
- [ ] Verified complete.
- **Depends:** TE-026, TE-033–TE-035, TE-011. **Files:** sources/credits UI and source selector.
- **Work:** implement Sources sections for Story, Imagery and Reconstruction; Read the record/Behind the story opens active context, limitations and exact citations. Include observation periods and asset attribution.
- **Accept / verify:** links are real, relevant and clearly external; no placeholder source button. Opening pauses story/camera and closing remains paused. Keyboard focus, long URLs/titles, mobile scrolling and unavailable-link handling are reviewed.

### TE-045 — Synchronize narrative and date transitions
- [ ] Verified complete.
- **Depends:** TE-031, TE-040, TE-011. **Files:** shared narrative transition components, date layout.
- **Work:** bind headline/body/date/context to one scene projection, with short restrained fades and stable block sizing. Handle long century ranges, overlapping date windows and intro/finale copy variants.
- **Accept / verify:** no previous headline describing the new chapter after settled transition; no UI jumping or duplicate screen-reader announcements from outgoing text. Fast reverse seeks and 200% text zoom preserve a readable single active narrative.

### TE-046 — Finish section switching and bookmarks
- [ ] Verified complete.
- **Depends:** TE-041, TE-045. **Files:** section reducer, session bookmark state.
- **Work:** implement first-visit intros, paused section restoration and cancellation of in-flight camera/asset work. Keep quality/accessibility preferences separate and normalize unsupported appearance modes on switch.
- **Accept / verify:** Planet Blue hour does not leak as a nonexistent Civilization control. Rapid switching never resurrects a stale texture/chapter; returning to a section restores its intended bookmark paused. Fresh visits still open present-day Planet.

### TE-047 — Finish compact utilities and help
- [ ] Verified complete.
- **Depends:** TE-042–TE-046. **Files:** settings/help/reset utilities, control inventory.
- **Work:** complete reset-view, accessible zoom, concise interaction help and any retained fullscreen utility with a clear exit. Remove unexplained source-video/capture controls and unused icons instead of shipping inert imitations.
- **Accept / verify:** every visible primary utility has a real behavior, tooltip/name and keyboard path. Fullscreen denial fails gracefully; Escape/touch exit work. Reset changes the current camera only unless the action explicitly promises a full story reset.

### TE-048 — Pass the combined first-session and cancellation gate
- [ ] Verified complete.
- **Depends:** TE-041–TE-047, TE-032. **Files:** integrated E2E journey, fidelity ledger.
- **Work:** run opening → deep time → scrub → Civilization intro → several chapters → All chapters → source context → night finale → rewind. Interleave orbit, speed changes and section switches.
- **Accept / verify:** all controls affect real state, one camera/clock owns motion, and no stale story/asset/overlay survives cancellation. Record representative screenshots and fix material layout/interaction differences before hardening.

## M6 — Responsive, accessible, resilient and efficient

**Exit:** the full story works beyond one desktop happy path, with measured resource behavior.

### TE-049 — Complete narrow and touch layouts
- [ ] Verified complete.
- **Depends:** TE-048. **Files:** responsive shell, rails, drawers/styles.
- **Work:** build intentional mobile portrait/landscape layouts, readable story/date, usable globe and scoped timeline scrolling. Use dynamic viewport/safe-area handling and allow normal page scrolling where needed.
- **Accept / verify:** 390×844, 360×800 and landscape views have no body-level horizontal overflow, trapped page or inaccessible playback. Long chapter dates and opened panels remain usable. Label this as a Terra-specific responsive design, not a verified source layout.

### TE-050 — Complete keyboard and assistive-technology paths
- [ ] Verified complete.
- **Depends:** TE-043, TE-044, TE-049. **Files:** accessibility helpers, component tests.
- **Work:** provide meaningful slider semantics, chapter list/prev-next, zoom/reset, tab navigation, panel focus containment/return and text equivalents for the canvas. Use visible focus and no color-only states.
- **Accept / verify:** the complete story can be traversed without dragging. Editable controls are not hijacked by shortcuts; screen readers receive one current chapter/date. Run automated checks and a manual keyboard journey; an automated score alone is insufficient.

### TE-051 — Respect reduced motion and page visibility
- [ ] Verified complete.
- **Depends:** TE-041, TE-036, TE-049. **Files:** motion policy, visibility handling/tests.
- **Work:** disable automatic camera flyovers/pulses under reduced motion while preserving all content; pause/re-anchor when hidden or when panels open. Respect user preference changes during a session.
- **Accept / verify:** returning from a hidden tab or closing a modal never fast-forwards or unexpectedly resumes. Reduced motion yields stable readable chapters, not missing functionality. Test mid-transition toggles and long simulated hidden intervals.

### TE-052 — Add validated reproducible scene links
- [ ] Verified complete.
- **Depends:** TE-046, TE-006. **Files:** versioned serialization/schema, Share utility.
- **Work:** serialize bounded section/position/chapter/camera/appearance/overlay data into a static-host-safe URL. Imported scenes open paused; quality stays a local preference. Provide selectable-link fallback when clipboard access fails.
- **Accept / verify:** fresh-profile round trips reproduce scene content; malformed, oversized, unknown-version and unknown-ID inputs recover safely. No arbitrary external assets, executable expressions, secrets or user identifiers can enter the scene through the URL.

### TE-053 — Harden buffering, retries and stale requests
- [ ] Verified complete.
- **Depends:** TE-030, TE-017, TE-046. **Files:** asset state machine, failure UI/tests.
- **Work:** test delayed/missing/corrupt textures, rapid random seeks and canceled upgrades. Use era-correct preview or explicit buffering; freeze/re-anchor effective transport while required assets are unavailable.
- **Accept / verify:** retry is actionable, no infinite spinner/fake percentage appears, and a late obsolete request cannot overwrite the current chapter. Text/date cannot silently describe an unrelated old globe. Record deterministic forced-failure browser tests.

### TE-054 — Complete non-WebGL and context-loss recovery
- [ ] Verified complete.
- **Depends:** TE-012, TE-044, TE-050. **Files:** fallback story reader, error boundary, context lifecycle.
- **Work:** provide a useful accessible story/source reader and a real Terra poster where graphics are unavailable. Handle context loss/restoration without stale ready flags, duplicate loops or inaccessible modal overlays.
- **Accept / verify:** visitors can still read all chapters/sources rather than see a blank rectangle. Simulated unsupported WebGL and context events produce accurate status/retry behavior. Do not call a static fallback a functioning 3D renderer.

### TE-055 — Establish real-device performance evidence
- [ ] Verified complete.
- **Depends:** TE-048, TE-024. **Files:** measurement harness/report, performance notes.
- **Work:** profile the production build on named available hardware/browser/DPR/quality after warm-up. Measure frame-time distributions, transfer sizes, input stalls and resource counts during representative journeys.
- **Accept / verify:** report method, sample duration and device conditions; distinguish rAF frame timing, CPU/GPU diagnostics and estimates. Headless software rendering is not a laptop GPU benchmark. Record targets missed and prioritize concrete fixes rather than publishing unmeasured 60-fps claims.

### TE-056 — Tune adaptive quality and resource budgets
- [ ] Verified complete.
- **Depends:** TE-055, TE-053, TE-024. **Files:** quality controller, residency policy, optimization evidence.
- **Work:** fix measured hot loops, redundant React rerenders, oversized textures and unbounded prefetch. Add conservative quality downgrade/recovery with hysteresis and manual override; verify fallback decompression costs.
- **Accept / verify:** tiers stay useful, do not oscillate or reset the story, and meet documented budgets or explain residual blockers. Show before/after evidence and stable resource counts over repeated journeys. Do not remove required content to fake a performance win.

## M7 — Comprehensive quality and reference verification

**Exit:** all core behavior and visible states are verified in the production build, with honest evidence.

### TE-057 — Complete pure numerical and state tests
- [ ] Verified complete.
- **Depends:** TE-025, TE-040, TE-052, TE-053. **Files:** unit/property tests.
- **Work:** cover coordinate/UV anchors, piecewise mapping/inverse, date tags, authored order, transport continuity, overlay membership, emission policy, serialization and loader generations. Exercise 30/60/144Hz schedules with identical final monotonic time.
- **Accept / verify:** invariants and boundary/negative cases pass without loosening tolerances to hide bugs. No expected value is generated by calling the same function under test. Record test counts/results and deterministic seeds.

### TE-058 — Complete component and accessibility tests
- [ ] Verified complete.
- **Depends:** TE-050, TE-051. **Files:** UI tests and manual audit record.
- **Work:** test both transport controls, rail semantics, speed menu, section tabs, chapter drawer, source panel, focus behavior, long copy and reduced-motion variants. Audit contrast/target sizes in rendered context.
- **Accept / verify:** keyboard-only users can reach every story state and leave every panel; no hidden duplicate active content remains in the accessibility tree. Automated and manual results are separate and accurately recorded.

### TE-059 — Exercise all ten anchors and eighteen chapters end-to-end
- [ ] Verified complete.
- **Depends:** TE-048, TE-053, TE-057. **Files:** production-build Playwright suite.
- **Work:** enumerate every story ID, assert headline/date/active rail/scene revision/appearance permissions, then test reverse/random order, fast playback, modal pauses, camera interruption and section restoration.
- **Accept / verify:** 10+18 states plus both intros pass on a clean browser profile. Tests wait for the intended GPU-ready revision rather than arbitrary sleep alone. Missing chapters, dead buttons and future-light leaks block release.

### TE-060 — Perform recording-to-implementation visual review
- [ ] Verified complete.
- **Depends:** TE-032, TE-048, TE-049, TE-056. **Files:** visual fixtures, mismatch ledger, curated screenshots.
- **Work:** capture the specified reference checkpoints with fixed viewport, seed, quality and state. Inspect actual source reference and current render side by side for globe framing, geography, material, type, date, CTA and rail.
- **Accept / verify:** fix material mismatches rather than blessing them as baselines. Distinguish intentional original copy/branding/mobile panels from accidental drift. Exclude external X/macOS chrome. Record source timestamp, test state and at least five concrete comparisons per major screen family.

### TE-061 — Stress race conditions and lifecycle recovery
- [ ] Verified complete.
- **Depends:** TE-053, TE-054, TE-056, TE-059. **Files:** stress suite and resource report.
- **Work:** run at least twenty warm-state cycles of chapter/quality/section changes, delayed seek responses, cancellation, mount/unmount where applicable and context recovery. Inspect listener, worker, renderer and texture ownership.
- **Accept / verify:** no monotonically growing owned-resource count, stale current scene, duplicate clock, leaked future overlay or dead recovery UI. Document normal cache warm-up separately from leaks; an unexplained rising count is not dismissed as browser caching.

### TE-062 — Verify cross-browser and real static-path behavior
- [ ] Verified complete.
- **Depends:** TE-059, TE-049, TE-054. **Files:** browser matrix, build/preview deployment fixtures.
- **Work:** test Chromium, Firefox and available WebKit/Safari paths, root and `/terra/` builds, fresh reloads, scene hashes, asset/transcoder paths and panel navigation. Record actual engines/versions, not assumed platform support.
- **Accept / verify:** no development-server-only success, root-relative asset 404s, unsupported WebGL crash or broken copied link. Playwright WebKit and real Safari/iOS checks are reported distinctly. Unavailable real-device coverage remains an explicit limitation.

### TE-063 — Audit content, provenance and interpretation labels
- [ ] Verified complete.
- **Depends:** TE-026, TE-033–TE-035, TE-029, TE-044. **Files:** content/assets validators, review ledger.
- **Work:** check every chapter claim/date/source, coordinate provenance, image observation period, reconstruction model/frame/range, license/credit and conceptual/illustrative label. Review culturally sensitive framing and copied-text risk.
- **Accept / verify:** pending production records fail; no arbitrary precision, fake live labels, population-map claims or blanket MIT grant over external assets remains. Exact source links and required attributions are accessible in the app and docs.

### TE-064 — Sign off the release candidate
- [ ] Verified complete.
- **Depends:** TE-057–TE-063. **Files:** `docs/PROGRESS.md`, release-candidate report.
- **Work:** perform the complete first-session journey on a clean production build with no test bridge, verify all visible controls, inspect desktop/mobile and review unresolved issues by severity.
- **Accept / verify:** no P0/P1 functional, factual or visual blocker remains; any lesser limitation is explicit. Record commit/build/test evidence and intentional design differences. Do not confuse a finished candidate with a deployed public site.

## M8 — Portfolio presentation and verified release

**Exit:** a reproducible, credited, tested project with real media and a verified deployment or a precisely documented permission blocker.

### TE-065 — Write the actual portfolio README and case study
- [ ] Verified complete.
- **Depends:** TE-064. **Files:** `README.md`, engineering case study.
- **Work:** replace planning language only for genuinely shipped features. Explain the dual timeline, model-informed continent pipeline, state/asset cancellation and accessibility/performance decisions with concise real examples.
- **Accept / verify:** no invented testimonials, source-framework certainty, live-data label or unmeasured FPS claim. Setup commands reproduce the app. Distinguish inspiration, independent implementation, scientific approximations and third-party assets clearly.

### TE-066 — Capture original Terra screenshots and demo
- [ ] Verified complete.
- **Depends:** TE-060, TE-064. **Files:** curated permitted project media.
- **Work:** capture the actual Terra opening, formation, ice, Pangea, representative human chapters and modern night finale; create a roughly 30–60-second clean demo with intentional pacing and no private desktop data.
- **Accept / verify:** media depicts the running implementation, not source recording/concept art. Crop appropriately, optimize sizes, provide alt text/captions and retain relevant credit context. Verify playback and links before embedding in the README.

### TE-067 — Publish meaningful CI checks
- [ ] Verified complete.
- **Depends:** TE-057–TE-063. **Files:** `.github/workflows/`, CI notes.
- **Work:** implement pinned/reviewed workflow actions for install, lint, type, unit, asset/content/docs validation, build and configured browser suites. Cache safely and upload diagnostic failures with bounded retention.
- **Accept / verify:** a real CI run passes on the intended commit; deliberate negative checks fail in development verification. No skipped critical suite or dummy success is represented as coverage. Secrets are unnecessary for the core build.

### TE-068 — Implement static deployment workflow
- [ ] Verified complete.
- **Depends:** TE-062, TE-067. **Files:** Pages deployment workflow, deployment runbook.
- **Work:** configure production `dist` and `/terra/` base using current official deployment guidance. Inspect repository Pages/settings permissions before changing authorized configuration; preserve unrelated settings.
- **Accept / verify:** workflow artifacts contain the correct static paths and use minimal required permissions. Record any unavailable setup action as a blocker. Creating a workflow is not proof the site is deployed.

### TE-069 — Finalize licenses, credits and repository navigation
- [ ] Verified complete.
- **Depends:** TE-063, TE-065. **Files:** code license if finalized, asset notices, docs index, issue index.
- **Work:** finalize original-code licensing separately from imagery/model/font terms, make credits discoverable, update the documentation/epic map and remove obsolete active-plan links. Prepare an accurate repository description/demo reference only where permissions allow.
- **Accept / verify:** no old solar-lab task is presented as current; all internal links resolve. External notices and source credits are retained. Do not change Jordan's profile pins or other repositories without separate authorization.

### TE-070 — Verify the public deployment
- [ ] Verified complete.
- **Depends:** TE-068, TE-064. **Files:** deployment evidence and public smoke report.
- **Work:** open the actual deployed URL from a clean browser, verify assets, chapter links, refresh, both story journeys, source links and no console/network failures. Test a copied scene URL independently.
- **Accept / verify:** a real public URL and tested commit are recorded only after success. When permissions/services prevent deployment, mark this task blocked with the exact failure and reproducible build evidence; never invent a live URL or mark deployment done anyway.

### TE-071 — Audit clean-install and distribution hygiene
- [ ] Verified complete.
- **Depends:** TE-067, TE-069. **Files:** clean-check report, ignore rules, distribution audit.
- **Work:** install/build/test from a clean checkout using documented versions. Inspect shipped bundle/repo for unused dependencies, test-only mutation APIs, secrets, private paths, abandoned experiments and oversized raw assets.
- **Accept / verify:** no 348 MB source recording, unlicensed frame dump or irrelevant infrastructure is included. Required scripts and local assets work without hidden machine state. Record real outputs and remove transient QA dumps while preserving curated evidence.

### TE-072 — Publish the final implementation handoff
- [ ] Verified complete.
- **Depends:** TE-065–TE-071. **Files:** final `PROGRESS.md`, release notes, final README links.
- **Work:** reconcile every TE checkbox with implementation evidence, summarize the actual 10+18 experience, tests, visual comparisons, measured performance, assets and deployment. Publish release/tag only when appropriate permissions and gates pass.
- **Accept / verify:** no blocked task is silently counted done. A deployment-blocked handoff remains an explicitly incomplete public release. State remaining original-source/mobile/device uncertainties accurately. Optional experimentation must not replace this core completion audit.

## Deferred, not required for this goal

Full physical plate-motion interpolation, WebGPU, terrain landing, VR, narrated audio, live weather, population simulation and a solar-tilt lab are separate future decisions. Do not expand into them before the recording-based product passes its core gates. Original-code polish and reliable storytelling are more important than a larger feature count.
