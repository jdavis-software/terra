# Visual and interaction specification

## Status and direction

This is the **proposed Terra visual baseline**. No X frames or generated design concepts were available/approved during planning. Do not describe it as extracted from the source video. At TR-004, create and inspect desktop and mobile concepts or equivalent explicit visual references before detailed UI implementation, then record the selected baseline. Generated concept art must not be substituted for scientific Earth textures or a functioning interface.

Creative direction: a quiet orbital observatory. A believable Earth, restrained instrument chrome, spacious framing, precise typography and meaningful motion. Avoid a neon science-fiction dashboard, overexposed bloom, rainbow overlays, giant cards, fake telemetry and heavy decoration.

## 1. Proposed design tokens

```css
:root {
  --space: #05080f;
  --surface: #0d1420;
  --surface-raised: #142031;
  --text: #edf3fa;
  --muted: #a5b2c3;
  --border: #283447;
  --accent: #79c9ff;
  --accent-strong: #39a9f0;
  --warning: #f1bf71;
  --danger: #ff8e8e;
  --radius-control: 8px;
  --radius-panel: 12px;
  --space-unit: 4px;
}
```

These are starting choices, not sampled reference colors. Check actual contrast before locking them. Use a system sans-serif stack for prose/UI and a system monospace stack for time and numeric readouts. Avoid an external font request in the critical path. Typography: brand 18–20px; primary panel heading 16px/1.35; body/control labels 14px/1.45; secondary labels 12px/1.45; numeric clock 14px with tabular figures. Do not make all labels tiny uppercase tracking exercises.

Spacing follows 4/8/12/16/24/32px. Target controls at least 44×44 CSS pixels on touch layouts. A single understated line-icon family is enough. Every icon-only action needs a visible tooltip and accessible name; color is never the sole state indicator.

## 2. Desktop composition

Primary reference viewport: 1440×900. Also test 1280×800 and 1920×1080.

Top bar: 64px. Bottom timeline region: approximately 92px. Left rail: 56px. Optional Explore/Layers panel: 280px. Optional inspector: 300–320px. The stage receives remaining space and its camera aspect updates when panels open. Prefer resizing the stage over translating the planet in world space. Coordinate calculations must remain unchanged by UI layout.

The initial screen has both detail panels closed. Earth occupies approximately 65–72% of stage height at the default camera, not 90% of the whole viewport. Leave room for the atmospheric limb and a small interaction hint. Default vertical field of view is 42°, radius is 1 world unit and camera distance is approximately 4 units. Tune composition from screenshots, not guessed CSS.

Keep the stage background continuous with the application shell. Panels can use a restrained translucent finish but must remain readable without expensive full-screen blur. Do not apply blur to large moving surfaces on mobile.

## 3. Narrow-screen composition

At 390×844 and 360×800, use a 56px top bar, a compact playback strip and a bottom action bar. Hide secondary actions in overflow. Panels become one bottom sheet at a time, with a clear close handle/button and a visible heading. The selected point remains visible above a half-height inspector sheet.

Use `100dvh` with a safe fallback and safe-area padding. Verify landscape phone orientation, 200% text zoom and long place names. The body must not horizontally scroll. Avoid blocking pinch gestures intended for browser zoom outside the stage. Do not globally disable touch behavior on the page.

## 4. Planet treatment

Surface: recognizable continent detail, dark but not black oceans, and no obvious baked second Sun. Use night/day maps aligned to the same canonical UV frame. Ocean highlights should be narrow, controlled and masked away from land. If a valid ocean mask is unavailable, disable the dedicated ocean effect rather than inventing water from color thresholds and presenting it as reliable classification.

Night side: warm, fine city patterns. Darkness should retain limited form without illuminating the full night surface evenly. Bright lights must be suppressed on the day side. Bloom is optional and must be selective, restrained, and off on lower quality if needed.

Atmosphere: thin blue/cyan limb on the lit side, a subtler dusk edge, and a much weaker dark-side rim. Use an artistic shell in core; do not call it a physically integrated scattering model. The atmosphere must not resemble a thick luminous ring.

Clouds: separate layer with coherent sunlight, no black alpha fringes, no doubled opaque planet, and no uniformly white globe. Cloud movement is artistic advection of a historical/procedural texture, clearly identified in Credits.

Stars: sparse, dim, fixed-seed points. No star visibility through the planet or UI panels. This is decorative space, not an accurate star catalogue.

## 5. Interaction timing

Ordinary hover/focus changes: 120–160ms. Panel transitions: 180–240ms. Camera fly-to: roughly 900–1400ms, based on angular distance, using smooth ease-in/out and cancellation. Do not bounce the globe. At reduced motion, replace long camera paths with an immediate or very short state change and leave auto-orbit/tour motion off.

Camera constraints: no panning in core; distance 1.5–10 Earth radii; prevent unstable exact-pole camera positions; normalize orientation. Wheel zoom must remain controllable on a trackpad. Avoid camera position interpolation along a chord through Earth. Interpolate a unit viewing direction and radial distance separately, with an explicit fallback for antipodal directions.

Toggling a layer changes the scene immediately or with a short material fade; it must not reset the camera, clock, quality or selection. Hovering a panel must not rotate the planet. Keyboard shortcuts apply only when focus is outside editable controls, except Escape for closing the active modal/mode.

## 6. Required visual states

| State | Must show | Must not show |
| --- | --- | --- |
| Initial showcase | Recognizable lit Earth, compact chrome, paused UTC time, clear controls | Login, dashboard cards, unexplained counters |
| Night Lights | Fine visible urban emission and coherent terminator | Bloom washing out continents |
| Selected place | Named point, inspector, readable marker | Labels on the far side of Earth |
| Lab | Distinct simulated-mode indicator and coherent controls/curve | A badge falsely saying live or scientifically validated |
| Mobile inspector | Legible sheet and usable stage/playback | Clipped controls, horizontal scrolling |
| Loading | Truthful asset stages and actionable failure | Fake percentage or infinite spinner |
| WebGL unavailable | Real poster, capability explanation, static documentation links | A blank black box |
| Photo mode | Clean rendered planet and clear exit affordance | Inescapable hidden UI |

## 7. Showcase storyboard — proposed, not source-video timestamps

A 35–50 second optional tour should have four scenes: a lit Earth establishing shot; a controlled move toward the terminator; a nighttime city reveal; and a wider polar/seasonal view. Each scene is a structured preset with an explicit clock and camera. Transitions interpolate both light/time and camera intentionally; they must not jump to an unrelated instant unless a cut is specified.

Keep captions short and factual: `Explore Earth`, `Follow the light`, `Cities after dark`, `A different perspective`. Do not imply these captions were present in the X video. Avoid AI-model claims or performance statistics inside the scene.

## 8. Visual verification procedure

Before sign-off, inspect the selected visual concept/baseline and the current application screenshot side by side at matching dimensions. Compare composition, globe size, continent orientation, lighting, atmosphere thickness, city-light strength, type scale, control density, whitespace, focus states and mobile sheet behavior. Capture a mismatch ledger with at least five concrete comparison points and fix material mismatches.

Automated screenshot baselines protect against regressions; they do not judge whether the first baseline looks good. Do not use pixel-perfect cross-GPU image matching as the only acceptance criterion. Fix time, seed, DPR, browser and quality settings for deterministic comparisons and maintain renderer-specific tolerances where justified.

Core visual blockers: mirrored continents, a broken texture seam, city lights in daylight, detached atmosphere, clouds clipping through the surface, a blank canvas, unreadable chrome, clipped controls, jittery camera motion, or decorative controls that do nothing.
