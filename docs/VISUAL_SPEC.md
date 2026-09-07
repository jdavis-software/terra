# Terra v2 — visual specification from the recording

## Visual thesis

An editorial story told around one enormous planet. Near-black background; airy, light-weight sans-serif headlines; restrained small labels; thin separator rules; almost no cards. The globe occupies the right/central field, with narrative text at left and time at upper right. This is not a monitoring dashboard or a generic space-game HUD.

The recording is the primary design reference. It is a 2940 × 1912-pixel capture, not a measurement of CSS viewport size or device-pixel ratio. Evaluate proportions after cropping external player/capture chrome. Do not claim the exact source font, CSS values or original viewport were recovered. Values below are implementation targets chosen from the visible composition.

## Composition targets

At a 1440 × 900 implementation viewport, use approximately 56–64px outer horizontal gutters, a 78–90px header band, and a thin horizontal rule. The story starts near x=8% of the viewport and uses roughly 28–35% width. The globe's visual center is around x=68–70%, y=47–49% in Planet mode; it is somewhat larger and more central in Civilization. Preserve readable text over a subtle left-to-right scene fade, not an opaque giant panel.

Planet globe diameter target: roughly 70–82% of usable scene height. Civilization: roughly 85–100%, with purposeful partial overlap behind the narrative/upper area, as in the recording. Keep the atmospheric limb visible wherever not intentionally clipped. The date occupies the upper-right negative space, not a badge in a card. The geological/chapter rail sits around the lower fifth; footer appearance controls and compact utilities sit below a separator.

Use DOM overlays for all interactive controls and text. Do not bake UI into a screenshot. A projection/view-offset helper may frame the globe asymmetrically, but geographic coordinates remain centered on one unchanged sphere. Opening panels must not change the geographic coordinate convention.

## Typography and tokens

Choose a licensed sans-serif that actually resembles the reference's narrow, clean, light-weight letterforms, or a suitable system stack. Source font identity is unknown. Confirm the license before bundling any font. Use actual 300/400 weights where available; never compress letters with a CSS transform to fake the design.

Suggested 1440px desktop type: headline clamp 44–68px, line-height 1.03–1.10, moderate negative tracking; body 14–16px, line-height 1.55–1.7; section labels 10–12px with restrained tracking; date 34–48px depending on length; standard controls 12–14px. Long date ranges need explicit wrapping rules. Mobile body stays at least 14px and headline around 32–44px. Increase tiny source labels when necessary for accessibility; do not reproduce unreadable miniature type just for literal fidelity.

Initial tokens, to refine against the recording:

```css
--bg: #030609;
--text: #edf1ef;
--muted: #a6afaf;
--rule: #1b292b;
--surface: #091211;
--planet-accent: #d7e8dc;
--civilization-accent: #e5d8b4;
--accent-text: #152019;
--focus: #a4d9cb;
--radius-button: 3px;
--radius-pill: 999px;
```

The large story CTA is pale mint in Planet and warm parchment in Civilization, with dark text and a small action icon. The small transport pill is dark/translucent with an outline. The appearance switch is a compact segmented control in a dark green-black container. Avoid bright cobalt dashboard buttons. Check contrast in final rendered context.

## Header and narrative

Use `terra.` as original branding, not the creator's `earth.` identity. Preserve The Planet / Civilization / Sources labels. A subtle active marker under the selected top section is sufficient. No avatar, search field, login or extra top navigation.

Narrative anatomy: context label; headline; short body; one primary action and a small source action. The recording shows open text, not a bordered narrative card. Preserve a stable block height so transitions do not jerk the timeline or controls. Fade/translate text modestly; no typewriter effect. Keep outgoing text inaccessible to screen readers during a transition and expose only one live chapter.

## Planet materials

Recognizable modern texture detail, dark blue oceans and green/brown land. Ocean highlights exist in the reference but should not obscure whole continents. Clouds are separate, modest and not a full white blanket. Atmosphere is a narrow cool-blue edge, not a thick luminous ring. Space is nearly black with sparse/dim detail; do not add a dense star wallpaper.

The early-Earth globe needs dark crust and lava emission with genuinely different surface structure. Ice needs a distinct mask and albedo, not a white opacity overlay over every interface element. Ancient continental geometry must change. Late geological keys cannot all be present-day Earth under different color filters.

Natural, After dark and Blue hour are artistic appearance presets. Global city emission is enabled only for present-day contexts. Tone mapping and sRGB conversion must happen correctly once; diagnose color-space problems rather than fixing them with arbitrary exposure.

## Civilization materials and overlays

The globe appears larger and darker/clearer, with focus on the selected geographic region. Surface labels are subtle, tightly connected to places, and occluded on the far side. Current-site halos are soft and small, not red map pins. Route arcs and region masks are restrained. The footprint card is the one purposeful floating information panel, near the lower right above the rail.

At C17, emphasize one neighborhood/site. At C18, fade into modern night imagery with fine city patterns and a controlled pullback. Do not wash the whole Earth in bloom. A globe turning through a dark ocean is acceptable during a short intentional transition, but a chapter's final pose must expose its subject.

## Motion and control ownership

Proposed timing: panel fade 180–240ms; text transition 250–450ms; camera move 1.0–1.8 seconds at normal speed. Final timings are Terra choices, not recovered source constants. At 5× playback, camera transitions need a minimum perceptible duration and remain within the chapter slot; never overlap multiple camera owners. A manual drag cancels scripted motion immediately and pauses story time.

Use direction interpolation along the sphere plus separate distance interpolation, not Cartesian chords through Earth. At antipodal targets choose a stable intermediate direction. Easing should be quiet and continuous; no spring overshoot across continents. Reduced motion replaces flyovers and pulsing with stable changes and never prevents content access.

## Unobserved surfaces to complete

All chapters panel, Sources/details panel, speed menu, failure states, narrow/mobile layouts and keyboard focus states were not opened or demonstrated in the recording. Build these in the same visual language and label their design in the fidelity ledger as Terra-specific completions, not source observations.

On mobile, place story copy above/below a usable globe rather than layering text over every continent. Use a compact chapter rail with horizontal overflow confined to that component, prev/next buttons and a readable date. Allow vertical page scrolling. Do not force the desktop fullscreen canvas composition into a 390px-wide device.

## Visual checkpoints

Capture reproducible implementation states corresponding to: opening Africa, modern After dark, Blue hour, hot formation, ocean emergence, ice, Pangea, breakup, Civilization intro, C01 Africa, C04 Uruk, C06 Indus, C10 Pacific, C12 Andes, C13 West Africa, C17 local light and C18 night globe. Compare composition, globe scale/position, geographic subject, material state, headline rhythm, date fit, CTA color, rail anatomy and overlay restraint.

Exclude external video-player/capture chrome. Compare at matching aspect ratio and document any viewport crop. Automated pixel comparisons are for regressions on a controlled renderer; they do not replace human visual review of fidelity and polish. Release blockers include wrong hemisphere, mirrored maps, fake continental drift, future city lights, unreadable copy, dead controls, camera fighting, generic dashboard chrome or only a handful of the required chapters.
