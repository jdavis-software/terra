# Product specification

## 1. Product definition

**Terra is a cinematic Earth observatory with an educational sunlight sandbox.** It runs as a static client application, opens directly into an interactive planet, and needs no account or service key. This is the chosen Terra baseline, not a verified description of the X reference.

Primary audience: people browsing Jordan's GitHub portfolio, engineering hiring teams, and curious visitors. The first interaction should be obvious; deeper controls should reward exploration without burying the planet under panels.

Product priorities, in order: striking first impression; responsive real interactions; coherent simulation; readable interface; reliable cross-device operation; concise engineering story. More overlays are not inherently better.

## 2. Required first-session journey

The initial showcase preset loads a readable Earth with deliberate lighting, a short interaction hint and visible simulation time. The visitor drags to orbit, zooms, searches for a place, sees it selected with useful sunlight readouts, plays or scrubs time, switches to the lab, changes axial tilt, and launches a cinematic tour or copies a scene URL. All of those actions must alter real application state.

A fresh visit starts from the curated showcase, not an unpredictable persisted camera buried inside Earth. Apply explicit URL state first; otherwise use the showcase. Persist accessibility and quality preferences only. Offer a separate action to restore a locally saved scene.

## 3. Functional requirements

| ID | Requirement | Core definition of done |
| --- | --- | --- |
| FR-01 | Cinematic Earth | Textured Earth, ocean response, historical city lights, clouds, restrained atmosphere, decorative star field, working orbit/zoom |
| FR-02 | Time controls | Play/pause, speeds 1×/60×/3600×, UTC date/time input, one-day scrubber, Now and reset; all use one clock |
| FR-03 | Place exploration | Bundled curated search, click selection, keyboard selection, fly-to, back-face marker occlusion |
| FR-04 | Location inspector | Latitude/longitude, geometric solar altitude, day/twilight/night category, local apparent solar time, model/source notes |
| FR-05 | Sunlight lab | Explicitly simulated mode; axial tilt, season angle, solar-day duration, phase controls and normalized sunlight curve |
| FR-06 | Layers | Cloud, atmosphere, night-lights, graticule and place-marker toggles; restore defaults; meaningful state |
| FR-07 | Presentation | User-started cinematic tour, photo mode, quality selection, scene sharing, presets, help |
| FR-08 | Accessibility and resilience | Keyboard alternatives, reduced motion, mobile layout, loading/failure states, WebGL fallback, no focus traps |
| FR-09 | Reproducibility | Validated versioned scene URLs, deterministic presets, reset, fixed test clock/seed and scene-ready signal |
| FR-10 | Portfolio release | Build/test scripts, verified static-path behavior, original demo media, architecture documentation and truthful status |

## 4. Screen anatomy

A compact top bar contains Terra, mode switch, preset chooser, tour/photo actions and an overflow menu. The central stage is the primary surface. A narrow left rail opens Explore, Layers and Settings; a right inspector opens only after selection. A bottom timeline displays the authoritative clock and playback controls. Help and Credits are real dialogs, not decorative icons.

Do not add a marketing landing page before the simulator. Do not add pricing, testimonials, login, analytics cards, or unexplained global counters. The GitHub README is the primary project explanation; the app is the demonstration.

On mobile, replace side panels with mutually exclusive bottom sheets. Keep at least half the stage visible when possible. A sheet must not block the only way to pause a moving scene. Respect safe-area insets and browser chrome changes.

## 5. Earth mode

### Initial state

Default to `2026-09-06T12:00:00.000Z`, paused, a camera centered roughly over 15°N/15°E at distance 4 Earth radii, Earth mode, medium quality, clouds/atmosphere/night lights on and graticule/markers off. This is a clearly labeled showcase time, not a claim that imagery was acquired then. `Now` uses the device clock and switches to 1× playback; it does not turn historical imagery into live imagery.

### Clock behavior

Play advances the current epoch; pause freezes it. Speed changes preserve continuity. Scrubbing pauses playback during the drag, previews the selected time and remains paused after release. The scrubber covers the UTC day containing the selected epoch. Crossing midnight through playback updates the day rather than snapping backward. Invalid dates are rejected without corrupting the last valid scene. Restrict the supported UI date range to 2000-01-01 through 2100-12-31 and document it as a Terra product limit, not the astronomy library's limit.

When the tab becomes hidden, pause and stop visual animation. On return, remain paused and explain briefly that playback was paused while hidden; do not advance by a large background delta. This is a simulation timeline, not a continuously synchronized live clock.

### Scientific labels

Earth mode computes the Sun's apparent direction through the documented ephemeris adapter. The spherical surface, exaggerated atmospheric shell, artistic cloud motion and historical image composites are simplifications. Show `Geometric solar altitude` rather than promising observed sunrise or refraction-corrected altitude. Do not display temperature, cloud forecast, population, orbital altitude, or environmental measurements without a real source/model.

## 6. Location inspection

Bundle at least 24 named places covering all hemispheres and important edge cases; include a polar site, a date-line site, an equatorial site, and near-antipodal pairs. Each record needs an ID, display name, latitude, longitude and provenance. Store only what is used. Avoid a full country database unless it serves a required interaction.

Search is local, case-insensitive and tolerant of diacritics. Support arrows/Enter/Escape, clear and no-results states. A selected named place retains its name. A surface click elsewhere is labeled `Selected point`, never automatically called the nearest city. Clicking empty space clears a point selection only if no camera drag occurred. Pointer movement beyond a 6 CSS-pixel threshold counts as a drag.

The inspector uses the same scene Sun vector as the material. Local apparent solar time is not a civil time zone and must be labeled. At a mathematical pole, longitude-derived local solar time is undefined and should display an explanatory dash. Geometric day/twilight classification excludes refraction and must not be marketed as a precise sunrise service.

## 7. Sunlight lab

The lab is a separate hypothetical mode. Entering it stores the last Earth state; exiting restores that state without silently changing its UTC time. The lab displays `Educational simulation — not a climate forecast` persistently.

Controls:

| Control | Range/default | Observable effect |
| --- | --- | --- |
| Axial tilt | 0°–60°; 23.44° default | Changes the relationship between season and solar declination |
| Season angle | 0°–360°; 90° default | 0° northward equinox, 90° northern summer, 180° southward equinox, 270° southern summer |
| Solar day duration | 0.5–96 simulated hours; 24 default | Changes how quickly the subsolar longitude completes a cycle |
| Day phase | 0%–100% | Moves the hypothetical Sun around the fixed planet |
| Reset lab | One action | Restores all defaults and clears modified-state indicator |

The season angle is held fixed while a lab day plays; this is a daily sunlight experiment, not a full orbital/climate model. Derive the selected location's normalized direct sunlight curve over one lab solar day from the same Sun geometry. Label its vertical axis `Relative direct sunlight (0–1)`, never watts, temperature or energy production. A longer day changes the duration axis, not the curve's normalized noon intensity by itself.

Include three explanatory presets: `No seasons` (0° tilt), `Earth-like tilt` (23.44°), and `Extreme tilt` (60°). The label Earth-like describes one parameter, not a validated complete Earth model.

## 8. Showcase behavior

Tour: explicit start, 35–50 seconds, four coherent scenes, deterministic camera/time/layer state, concise optional captions, pause/resume/exit. User pointer, wheel, keyboard camera input or reduced-motion preference cancels or prevents automated camera motion. Never fight the user's input. Restore the pre-tour state on exit; `Keep this view` may explicitly retain the current state.

Photo mode: hide chrome, retain a visible/focusable Exit control, support Escape and touch exit. Export a canvas-only PNG when available; say that UI panels are not included. Handle browser capture failure honestly. Keep attribution accessible in the app and attach provenance in the accompanying export metadata or filename/readme convention.

Scene sharing: copy a URL that encodes versioned, bounded scene parameters and opens paused. No arbitrary asset URLs, executable expressions, external fetch URLs or user identifiers. A clipboard denial must expose a selectable link. Full scene equality means serialized camera, time/lab parameters and layers; device quality preferences remain local unless a test fixture explicitly pins them.

Presets: `Blue Marble`, `Night Lights`, `Terminator`, and `Polar Day` for Earth; three lab presets above. Each has a stable ID, explicit time, camera and layers. Names such as Polar Day require numerical validation of the chosen latitude/time.

## 9. Core exclusions

No climate or fluid solver, sea-level damage prediction, plate tectonics, live global weather, terrain landing, destruction effects, multiplayer, AI chat, satellite fleet, lunar eclipses, high-precision geodesy, or planetary formation in the core release. Those are materially different engineering projects. Select extensions only after the core experience is demonstrably finished.

No sound is necessary. Do not add autoplay audio. No tracking or analytics are required. No visitor location permission is needed for the core product.

## 10. Product acceptance

A reviewer must be able to follow the first-session journey without reading the README. Every visible primary control must work. Keyboard-only users must have meaningful equivalents to pointer exploration. A missing asset cannot trap the app behind an infinite spinner. A scene link must reproduce the intended state on a clean browser profile. The README must distinguish planned features from implemented ones until each is verified.
