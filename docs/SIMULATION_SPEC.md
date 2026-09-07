# Terra v2 — story engine, coordinates and temporal contracts

## 0. Replacement of v1

This file no longer specifies an Earth-observatory ephemeris or an axial-tilt lab. Terra v2 animates **authored narrative time**. A geological reconstruction dataset, illustrative appearance effects, camera choreography and human chapter metadata are separate inputs. Do not install Astronomy Engine or reintroduce UTC/solar-time controls merely because v1 mentioned them.

## 1. Coordinate convention

Use a right-handed Y-up, Earth-fixed frame. Latitude φ is north-positive; longitude λ is east-positive. For radius r:

```text
x = r cos(φ) cos(λ)
y = r sin(φ)
z = -r cos(φ) sin(λ)
```

Latitude/longitude are degrees at content boundaries and radians for trigonometry. Normalize longitude to [-180,180). Inverse mapping is φ=asin(clamp(y/r,-1,1)), λ=atan2(-z,x). At the exact poles, longitude is undefined; preserve camera azimuth as a presentation choice rather than reporting precise longitude. Model radius is 1. Coordinates refer to the same sphere for textures, labels, routes, picking and camera targets.

Canonical equirectangular images have north at the top and -180° longitude at the left edge. Define one explicit geometry/texture UV transform and test it. Duplicated seam vertices can have u=0 and u=1. Do not stack undocumented texture offsets and mesh rotations to fix a flipped map. Verify Greenwich, 90°E, 90°W, both poles and actual continent/site landmarks.

## 2. Geological story coordinate

Let p be normalized story position in [0,1]. Use these fixed anchors:

```ts
const agesMa = [4540, 4300, 2400, 650, 540, 400, 300, 200, 100, 0] as const;
const positions = agesMa.map((_, i) => i / 9);
```

For p in segment i, compute u=(p-position[i])/(position[i+1]-position[i]) and ageMa=lerp(agesMa[i],agesMa[i+1],u). Handle p=1 explicitly as 0 Ma. Implement an inverse age-to-position function using the descending age bracket. All anchor round trips must match within numerical tolerance.

This is **piecewise-linear narrative spacing**, not uniformly linear years and not an unspecified logarithmic scale. Keep the real age numeric and the label formatter separate from p. Use Ga at >=1000 Ma, Ma below that, and Today at exactly zero; avoid rounding a positive old age into a misleading Today label. In playback use appropriate display precision rather than jittery many-decimal values.

Default narrative content key is the nearest anchor in story-position space (ties select the later key); this approximates the visible source progression. Surface layers may continuously interpolate between neighboring asset keys independently of the headline's threshold. Store any refined editorial thresholds as data, not scattered if statements. Exact original thresholds are unknown.

P10 has a present-day intro variant and a journey-finale variant without adding a rail anchor. Selecting any anchor sets p exactly; scrubbing pauses and updates the visible state without accumulating animation-frame rounding error.

## 3. Civilization coordinate and dates

Use an explicit ordered list of 18 IDs, never chronological sorting of range labels. Maintain `chapterIndex` 0–17 and `localProgress` 0–1. A normalized transport coordinate may be `(chapterIndex + localProgress)/18`; at p=1 clamp to chapter 17/localProgress=1. The visible count is chapterIndex+1, followed by `/18`. The unnumbered introduction has its own state and no 19th stop.

Historical dates are structured tagged data, for example:

```ts
type HistoricalDate =
 | { kind: 'yearsAgo'; earliest: number; latest?: number; referenceYear: number; display: string }
 | { kind: 'bce'; year: number; endYear?: number; approximate: boolean; display: string }
 | { kind: 'ce'; year: number; endYear?: number; approximate: boolean; display: string }
 | { kind: 'centuries'; display: string }
 | { kind: 'present'; display: 'Today' };
```

`yearsAgo` is a narrative convention with an explicit editorial reference year, not silently radiocarbon BP=1950. Use the source's convention where a claim specifically uses BP. Do not use JavaScript Date for geological dates or broad human chronology. Do not invent year zero in public BCE/CE formatting. Since authored chapter order is authoritative, no numeric conversion is needed merely to navigate.

Keep the date label attached to the chapter; do not animate 1492 to 1776 through fabricated per-year historical states. Overlapping century ranges are expected and must not fail validation as unsorted.

## 4. One authoritative transport

Use a pure reducer/state machine plus a monotonic anchored runtime. Anchor elapsed story seconds at a monotonic timestamp; evaluate from elapsed real seconds × speed, not accumulated `delta` additions. Pause, speed changes and seeks evaluate the old anchor then re-anchor continuously.

Initial Terra durations: Planet 75 seconds at 1×; Civilization 12 seconds per chapter at 1×, including camera arrival and readable dwell. Speeds: 1×/2×/5×. These are proposed configurable values, not exact source measurements. At 5×, shorten camera travel within a bounded minimum and ensure a chapter's camera arrives before the next chapter begins. Increase duration rather than overlapping transitions when necessary.

Transport states: intro, paused, playing, scrubbing, buffering and complete. Buffering retains a desired resume state but freezes effective story progression; it must not skip missed chapters after an asset finishes. Opening dialogs, switching sections, manual orbit, tab hiding and explicit seeks pause. Playback never starts automatically after a hidden-tab return or modal close.

The two visible transport controls dispatch the same action. Browser wheel time travel and timeline dragging do not run a second independent clock. Playback completion clamps at the end and stops, without hidden looping. Replay is explicit.

## 5. Separation of narrative, camera and appearance

One `deriveScene` function produces age/chapter, text ID, asset pair/blend, overlay set, appearance intent and scripted camera target from story state. User camera orientation is separate from story position. Manual input switches camera ownership from scripted to user; it does not mutate a historical date.

Camera owners: user orbit, chapter transition or brief reset. A new owner cancels the old transition before starting. Interpolate normalized viewing directions along a great-circle/quaternion path and interpolate radius independently. Do not lerp camera positions through the globe. For nearly antipodal directions choose a deterministic intermediate axis; test poles and cross-date-line travel. Keep r safely above the surface, with initial limits roughly 1.65–10 radii, tuned visually.

Use story-evaluated time or a separately paused deterministic presentation clock for cloud advection, halo pulses and lava noise. Fix seeds. Neither cloud motion nor camera orbit proves geological motion. UI readouts can update at a bounded rate; avoid per-frame React state updates.

## 6. Geological surfaces and fidelity tiers

The preferred core representation is precomputed, model-informed land/coastline masks at a bounded sequence of ages plus artistic appearance parameters. Early P01–P03 are explicitly conceptual. For 650–0 Ma use one named/pinned supported reconstruction model, such as MERDITH2021, subject to item-level data rights and acquisition checks. Do not mix reference frames between adjacent samples.

Reconstructed present-day coastlines rotated backward are not automatically exact paleocoastlines. Static plate polygons are not land boundaries. The asset manifest must identify the layer type, model, age, anchor/reference frame and limitations. Use appropriate continental/coastline data and review it; label it `model-informed illustration` unless stronger validation is actually performed.

Core baseline: blend aligned **land masks / signed-distance fields** and appearance layers in a shader using the same geographic UVs, with additional authored intermediate frames where a two-endpoint crossfade would look like two translucent globes. This yields a smooth illustrative land transition, not a physical plate solver. Acceptance requires real changing land configurations and no obvious doubled-continent ghosting. A minimal implementation that merely rotates a modern Earth fails.

A data-driven plate-quaternion deformation path is an optional later enhancement, not necessary for v2. Do not claim the mask blend implements continuous plate dynamics. Before rendering many assets, prove Pangea → breakup → present at low resolution and inspect halfway states.

Use a procedural early-Earth material only for explicitly conceptual epochs. Seeded spherical 3D noise avoids a texture seam; its seed is stable across quality settings. Lava emission decays toward the ocean epoch, water coverage increases, and city lights remain zero. Ice extent is illustrative with a named state and uncertainty note, not a climate model or an inferred temperature.

## 7. Bounded asynchronous asset transitions

The asset manager owns pending/active asset keys and monotonically increasing request IDs. A seek creates a new request generation. Only the newest generation may commit its pair; older responses can enter a bounded cache but cannot alter the displayed scene. Keep the currently valid pair alive until the next correct pair is ready, or use the new epoch's low-resolution preview. Do not display a new age over an unrelated old texture without an explicit loading state.

Pause transport during required buffering and re-anchor on completion. Keep at most current adjacent maps and a small prefetch window resident. Respect texture capability limits and estimated memory; release evicted textures/render targets with clear ownership. Context loss invalidates GPU-ready status and requires a controlled reload, not stale success flags.

## 8. Human overlays and nighttime policy

The visible set is a pure function of active chapter and overlay toggles. Future markers must disappear immediately on rewind. Current story regions and earlier story sites are separate layers. Broad origins/cultural networks use illustrative regions/routes, not fabricated quantitative heatmaps. Use local site animation at C17. Global modern city emission is allowed at C18 and Planet P10 only; manually selecting After dark elsewhere must not bypass that guard.

For a point on a sphere centered at origin and a finite camera position c, visible surface points satisfy p·c > R² (with horizon epsilon) when p lies on the radius-R surface. A simpler normal·cameraDirection >0 test is not sufficiently strict near the finite-distance horizon. Use correct ray/sphere occlusion or this derived criterion, then additionally check projection bounds and label collisions. Raised markers need proper occlusion against the Earth sphere. No far-side labels or routes visible through Earth.

## 9. Required invariants

Coordinate anchors and round trips; correct texture orientation; geologic anchor/inverse mapping; bounded p and nonnegative ages; explicit end handling; 18 chapters plus an unnumbered intro; stable authored order despite overlapping dates; continuous speed changes; frame-schedule independence; pause/visibility behavior; cancellable camera arbitration; stale-loader rejection; deterministic rewind overlay sets; premodern global-light prohibition; memory/cache bounds; valid scene-link round trips. Validate these numerically and in the actual browser. A plausible screenshot alone does not prove state correctness.
