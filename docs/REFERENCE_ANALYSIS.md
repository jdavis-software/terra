# Recording-based reference analysis — Terra v2

## Scope correction

The uploaded recording changes the product definition. The reference is a cinematic, two-part narrative about Earth history and human civilization. It is **not** the Earth observatory and solar-tilt laboratory proposed before the video was available. The v1 TR-001–TR-087 roadmap is superseded; implement the v2 TE-001–TE-072 roadmap instead.

The new visual evidence comes from Jordan's uploaded `Screen Recording 2026-09-06 at 10.07.01 PM.mov` (the original filename has a narrow no-break space before PM). File metadata: 83.281792 seconds, 2940 × 1912 pixels, H.264 video at a reported 60 fps, AAC audio, 348,351,663 bytes. SHA-256: `d914fc281e92e6366f23b617236e9a03a4bfdbe48d02e2dbda53aad4ed8964b7`. See `reference/recording-manifest.json`.

Review method: decoded video frames sampled across the recording at four-second and one-second intervals, contact-sheet inspection, and enlarged individual screens/text regions. Approximate timestamps below are **upload-relative**, not the original X player's timeline. This is a visual recording analysis; audio was not transcribed, and no original app DOM, network traffic, source code, or comment thread was inspected. The reported recording frame rate does not establish the application's frame rate.

The original references remain:
- https://x.com/akshdeeps_001/status/2096776530005488028
- https://x.com/akshdeeps_001/status/2096776530005488028/video/1

Raw recording and extracted frames are review material, not authorized public runtime assets. Do not commit the 348 MB recording, desktop chrome, X controls, or recording-toolbar imagery to this public repository. Textual observations and asset-independent implementation specifications are sufficient for the public plan.

## 1. What is now established

| Evidence ID | Observation | Evidence / confidence |
| --- | --- | --- |
| R01 | A small `earth.` wordmark, centered The Planet / Civilization navigation, Sources at upper right | Clearly visible throughout |
| R02 | Near-black full-screen stage; large light-weight sans-serif headline and paragraph on the left; large globe behind/right; date at upper right | Opening and all narrative states |
| R03 | The Planet starts at present day and offers a journey into deep time | Approximately 00:01–00:13 |
| R04 | Ten labeled geological anchors, irregular real-time gaps but approximately equal screen spacing | Enlarged opening timeline |
| R05 | Deep-time surface appearance changes: incandescent early globe, water/land, ice, changed continental arrangements, Pangea-like assembly and separation | Approximately 00:13–00:26 |
| R06 | Headline, numeric age and globe appearance change together during playback | Same interval; some text is visibly crossfading |
| R07 | Natural / After dark / Blue hour controls appear in Planet mode; visibly different lighting states occur | Opening approximately 00:01–00:12 |
| R08 | Civilization has an introduction, then 18 numbered chapter positions and a current/total counter | Approximately 00:26–00:79 |
| R09 | Civilization changes camera focus between continents and sites; location labels and subtle overlays are visible | Human chapter sequence |
| R10 | A lower-right human-footprint card distinguishes expanding story regions from earlier sites and explicitly disclaims borders/population density | Enlarged chapter screen at approximately 00:38.5 |
| R11 | Playback affordances appear both in the narrative area and near the lower-right stage; 5× is visible | Human journey and Planet playback |
| R12 | Civilization shows Natural / After dark controls, prev/next, All chapters and Behind the story | Human chapter screens; panels themselves not opened |
| R13 | Modern finale uses Earth-at-night imagery with city lights | Approximately 00:77–00:79 |
| R14 | Source video-player and operating-system capture overlays obscure the very end | Approximately 00:80–00:83; exclude from app spec |

An on-screen control establishes that the control is present, not that every possible click path was tested. The recording demonstrates selected paths; it is not an interactive browser audit.

## 2. Chronological recording inventory

| Approximate upload time | Visible state | Reconstruction requirement |
| --- | --- | --- |
| 00:01–00:04 | Present-day Africa/Europe; intro, Now, ten-anchor rail | Opening composition, legible typography, full globe and explicit story CTA |
| 00:04–00:12 | Camera orientation changes; globe illumination differs; lighting-selector states visible | Orbitable globe and three Planet appearance modes; exact input implementation unknown |
| 00:13.5 | Early Earth, hot crust/lava; age around 4.48 Ga | Distinct emissive early-Earth material, not a red tint on present-day geography |
| 00:14.5 | Ocean emergence, around 4.2 Ga | Conceptual cooling/water transition |
| 00:15.5 | Atmosphere/life chapter, around 2.76 Ga while traveling | Separate age interpolation and narrative state; transitional frames are not scientific date evidence |
| 00:16.5–00:17.5 | Large ice cover; later clearly the deep-freeze chapter around 600 Ma | Distinct ice material/mask and explanatory uncertainty |
| 00:18.5 | Ancient seas, around 525 Ma | A historical continental arrangement, not modern continents with a recolor |
| 00:19.5–00:20.5 | Continental convergence, around 439–351 Ma | Observable land-configuration progression |
| 00:21.5 | Pangea-like world, around 282 Ma | Recognizable joined landmass / surrounding ocean |
| 00:22.5–00:23.5 | Breakup, around 214–150 Ma | Transition to separated continental masses |
| 00:24.5 | Expanding oceans, around 83 Ma | Later reconstruction intermediate |
| 00:25.5 | Near-present world, around 20 Ma | Smooth return toward present geography |
| 00:26.5–00:28.5 | Civilization introductory screen, approximately 300,000 years ago | Intro is distinct from numbered chapter 01 |
| 00:29.5–00:31.5 | Chapter 01, Africa | Human origin chapter and broad, explicitly illustrative region |
| 00:32.5–00:34 | Chapter 02, White Sands | Camera moves to North America |
| 00:35.5–00:36.5 | Chapter 03, cultivation/settlement | Southwest Asia focus, multiple-origin caveat |
| 00:37.5–00:39.5 | Chapter 04, Uruk | Mesopotamia site label |
| 00:40.5–00:42.5 | Chapter 05, Giza | Egypt focus |
| 00:43.5–00:45.5 | Chapter 06, Mohenjo-daro | Indus focus |
| 00:46.5–00:47.5 | Chapter 07, exchange across East/Central Asia | Illustrative route network, not one exact Silk Road |
| 00:48.5–00:50.5 | Chapter 08, Teotihuacan | Central Mexico focus |
| 00:51.5–00:53.5 | Chapter 09, Cahokia | Mississippi Valley focus |
| 00:54.5–00:56.5 | Chapter 10, Polynesian navigation | Pacific camera orientation and island/route cues |
| 00:57.5–00:59.5 | Chapter 11, northern China / Ming-era walls | East Asia focus |
| 00:60.5–00:62 | Chapter 12, Machu Picchu | Andes focus |
| 00:63.5–00:64.5 | Chapter 13, Timbuktu | West Africa focus |
| 00:65.5–00:67.5 | Chapter 14, Atlantic contact in 1492 | Atlantic view with historical context, not an empty-world narrative |
| 00:68.5–00:70.5 | Chapter 15, Philadelphia 1776 | Eastern North America; equality/slavery/exclusion context |
| 00:71.5–00:73 | Chapter 16, industrial transformation / Ironbridge | Britain focus |
| 00:74.5–00:76 | Chapter 17, Pearl Street 1882 | Local electrical-lighting story, not instant global electrification |
| 00:77–00:79 | Chapter 18, present-day night Earth | Deliberate city-lights finale |
| 00:80–00:83 | End-of-video and capture overlays | Not Terra controls; do not reproduce |

These are representative observation windows, not millisecond-accurate edit boundaries. The deep-time numeric ages are sampled playback values, not replacement dates for the ten canonical rail anchors. All 18 chapter subjects and ten rail anchors are specified in `STORY_CONTENT.md`.

## 3. Grok prompt: what it gets right and what needs correction

| Prompt claim | Recording result / decision |
| --- | --- |
| Two main sections, cinematic globe, left narrative, bottom timeline | Supported; this becomes the actual core |
| Natural / After dark / Blue hour everywhere | Three options visible in Planet; only Natural / After dark visible in Civilization. Keep that distinction |
| Continuous chronology | Planet is continuous **piecewise story time**; Civilization uses 18 chapter stops with overlapping date ranges. Do not use one linear 4.54-billion-year slider for both |
| Some example human chapters | Correct but incomplete; the recording has 18, including White Sands, cultivation, Giza, Silk Roads, Teotihuacan, Polynesia, northern Chinese walls, Timbuktu and industrialization |
| Globe morphs through continental drift | Appearance/land configuration changes are visible. The clip does not prove vertex morphing, plate simulation, texture blending or the source algorithm |
| Three.js / React Three Fiber | Sensible Terra implementation choice; original stack is still unverified. Jordan reports Three.js comments, but comments were not supplied in this upload |
| Depth of field | Not established. Keep the core globe sharp; defer DOF rather than adding blur on assumption |
| Buttery 60 fps | Target for Terra on measured hardware, not a measured property of the source. A 60-fps recording is not a benchmark |
| Sources and chapter navigation | Links/buttons visible; their destination/panel design is unobserved. Specify useful original implementations |
| Atmospheric/lighting changes | Visually supported; physical realism of the original is not established |

## 4. Visual implementation hypotheses

A sphere with aligned color/emission/data textures can explain the modern globe. A separate shell can explain the thin blue limb; another shell/material can explain clouds. A directed surface light and masked ocean highlight can explain the specular response. A sequence of paleogeographic textures or reconstructed geometry can explain changing land. Camera direction interpolation can explain the geographic flyovers. DOM overlays can explain sharp type and fixed controls.

These are **reconstruction hypotheses**, not recovered source code. Terra chooses a Three.js/R3F implementation because it fits these requirements. No framework, shader, hidden feature, exact font family, backend, or original data license can be identified from the recording alone.

## 5. Important things not to copy accidentally

Do not rebuild X's video controls or the macOS recording UI. Do not make modern cities glow in prehistoric chapters. Do not label illustrative footprints as population or political borders. Do not infer a first city, first farmer, single origin point for humanity, or exact ancient coastline from cinematic imagery. Do not silently transform a broad historical date range into a precise date for animation. Do not bring the superseded solar-lab dashboard into this minimal storytelling interface.

## 6. Result and remaining limits

The visual reference gap is now substantially closed: the supplied recording has been inspected and decomposed into a feature inventory, 28 authored story anchors/chapters and implementable state/rendering contracts. **Original source-code analysis, live-app interaction verification, comment-based technology confirmation, mobile behavior, precise original easing/durations and original asset provenance remain unknown.** Terra implementation and visual comparison against the reference have not happened yet.

A release may claim an independently built, recording-inspired reconstruction after its tests pass. It must not claim the original source was recovered, its hidden controls were verified, or its scientific models were reproduced exactly.
