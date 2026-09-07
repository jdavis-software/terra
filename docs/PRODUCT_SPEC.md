# Terra v2 — product specification

## Mission

Build a beautiful single-page, browser-based story of Earth and human civilization for Jordan Davis's GitHub portfolio. The uploaded screen recording is the visual/behavioral reference. Terra uses its own `terra.` wordmark and original narrative copy while preserving the recognizable experience: two top-level journeys, oversized globe, left-side storytelling, upper-right date and bottom narrative timeline.

This specification supersedes the unverified v1 observatory/sunlight-lab proposal. Core scope is now ten geological anchors and eighteen human chapters, not a UTC sunlight sandbox. No authentication, backend, database, paid runtime APIs, AI inference, weather feed or governance infrastructure is needed.

## Core screens

### The Planet

A first visit opens the present-day introduction, paused, Africa/Europe visible, Natural lighting, clean black stage. The header contains terra., The Planet, Civilization and Sources. The left narrative contains a small contextual label, large original headline, short paragraph, `Go back in time` and `Read the record`. The upper-right date is Now. The bottom rail contains the ten exact anchors in STORY_CONTENT.md. A visible instruction distinguishes time travel from orbiting.

`Go back in time` sets the chronology to P01 and starts playback unless reduced motion is active, in which case it selects P01 paused. `Play the story` starts from the current story position; from the present-day introduction/completed end it starts P01. Pause freezes story progression without resetting it. `Back to today` selects P10, stops story playback and returns to the present-day intro. Manual scrubbing selects time and pauses playback.

The globe changes through conceptual formation, oceans/atmosphere, an ice state, ancient geography, continental assembly/breakup and present Earth. Numeric age is continuous through the piecewise timeline. Story copy changes at defined chapter thresholds. Raw time scale is **not linear** across 4.54 billion years. Show a quiet note that the rail is paced for the story, not proportionally spaced years.

Lighting controls: Natural, After dark, Blue hour. They change presentation, not historical time. Artificial city emission is forbidden for prehuman deep-time states. An early-Earth night view may show intrinsic lava emission. Blue hour is an artistic preset, not an astronomical claim.

### Civilization

First entry presents an unnumbered introduction. Starting the journey selects chapter 01. The main experience has exactly eighteen numbered stops, current/total counter, previous/next buttons, All chapters, an upper-right approximate/range date and left story. Reuse the same renderer but change camera choreography, globe scale, narrative color accent and overlay mode.

Each chapter has an explicit authored order, data-bound location/region, original headline/body, camera preset, appearance intent and source references. Dates are not evenly spaced and ranges overlap. Do not sort records by historical year or interpolate a fabricated precise year between broad century ranges. Chapter 18 is the city-lights finale. Chapter 17 is localized Pearl Street lighting, not the global night map.

The lower-right human-footprint card has two real toggles: current story regions and earlier story sites. Its limitation identifies these as illustrative, not borders/population density. Current points/regions can pulse gently; earlier sites are dim. Rewinding removes future features. The basic human geography is modern reference geography, clearly distinguished from the deep-time reconstruction layer.

Civilization has Natural and After dark only, matching the visible reference. Before C18, After dark darkens the natural Earth but does not enable modern global urban lights. This explicit Terra safety rule fills unobserved source-control behavior rather than claiming it was tested in the video.

### Contextual panels

All chapters opens an accessible list of all eighteen chapters with date, region and active state. Selection closes the panel, goes to that chapter paused and starts the appropriate camera transition. Sources opens a readable source browser with Story, Imagery and Reconstruction sections. Read the record/Behind the story opens the active chapter's explanation, limitations and citations. The recording shows these affordances, not their open panels; their detailed layouts are original Terra completions.

Opening a panel pauses the story and animated camera; closing it stays paused. External references open as ordinary clearly identified links. Never hide a running timeline behind a modal.

## Interaction contracts

| Input | Required action |
| --- | --- |
| Drag on globe | Orbit; manual input pauses story and cancels camera automation before applying input |
| Timeline drag | Capture pointer, scrub deterministically, remain paused after release; no camera orbit from the same gesture |
| Desktop wheel on unobstructed stage | Time travel in Planet; debounced next/previous chapter in Civilization; do not also zoom |
| Plus/minus controls | Controlled camera zoom; bounded distance, keyboard equivalents |
| Optional modified wheel | Not core; preserve browser zoom shortcuts rather than intercepting Ctrl/Cmd-wheel |
| Touch | One-finger orbit; explicit timeline scrub; two-finger pinch within stage for camera zoom; page/panel scrolling outside stage |
| Play/Pause in either visible location | One authoritative transport state, never two timers |
| Speed | Implement 1×, 2×, 5×; only 5× is visibly confirmed in the reference, others are Terra choices |
| Tab switch | Cancel in-flight transitions; preserve section bookmark; enter target intro or restore bookmark paused |
| Previous/next | One chapter, clamped at ends; no hidden wraparound |
| Escape | Close active panel/fullscreen/presentation surface as applicable; never trap the user |
| Reset view | Restore the active chapter's camera, not all content preferences |
| Document hidden | Pause/re-anchor story and presentation clocks; remain paused on return |

Do not steal the page's wheel/touch events when a panel, text field or menu owns them. Provide visible keyboard equivalents. A static screenshot is not an acceptable substitute for a live globe.

## State priorities

Explicit valid URL state wins; otherwise use the present-day Planet intro. Persist quality/reduced-motion preferences independently. Per-section bookmarks exist during the session; restoring a saved story from storage is explicit. A shared scene opens paused. No automatic tour on first load.

There is one scene projection derived from section, story position, view mode and user camera state. Date, headline, active rail item, overlays and textures cannot be driven by unrelated timers. An asset still loading must not allow a new date to describe an old world silently; enter a clear loading/buffering state or use an era-correct lower-resolution preview.

## Portfolio additions included after reference core

Versioned scene links, quality selection, an accessible fallback story reader and real project/demo media are supporting release features, not observations attributed to the source. Keep them in overflow or documentation instead of changing the primary composition. A custom photo/video editor, shader control panel and generic place-search dashboard are not core.

## Out of scope

The v1 axial-tilt lab, solar ephemeris/UTC timeline, daily sunlight curves, location-inspector dashboard, satellite tracking, terrain landing, climate prediction, live global weather, population-density simulation, destruction modes, AI chat, audio narration, WebGPU rewrite and billing/accounts are excluded. Do not import infrastructure from DriftGate or AvatarOps. Accurate full Earth history is not claimed: pre-reconstruction periods are conceptual, historical dates are qualified, and footprint overlays are illustrative.

## Definition of product complete

A visitor can explore today's Earth, play/scrub all ten geological anchors, switch into Civilization, traverse all eighteen chapters, pause/change speed, manually orbit, inspect sources, jump chapters, rewind without future data leaking, and use the same core story on mobile or with a keyboard. Visual comparisons against recording checkpoints and actual browser tests must pass. A planning document, a modern globe alone, or a linear timeline with five sample chapters is not completion.
