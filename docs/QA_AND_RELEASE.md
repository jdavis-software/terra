# Terra v2 verification and release contract

## Status and evidence policy

This document specifies future implementation tests. No application, test suite, measured frame rate, production asset set or deployment has been completed by the planning revision. The supplied recording was visually analyzed; source-code identity and unrecorded live-app behavior remain unverified.

Record actual outputs against a commit. A checkbox, mock screenshot, conceptual shader description or successful TypeScript build is not evidence that the site works. Do not disable tests, fabricate logs, enlarge screenshot thresholds without explanation or label a software-rendering CI run a real-device GPU benchmark.

## 1. Required commands

| Script | Required work |
| --- | --- |
| `pnpm dev` | Local application server, documented host/port |
| `pnpm build` | Real strict production build with configurable base |
| `pnpm preview` | Inspect the built output; not an asserted production hosting service |
| `pnpm lint` / `pnpm typecheck` | Actual lint and strict type checks |
| `pnpm test:unit` | Pure/component tests with deterministic clock/fixtures |
| `pnpm test:e2e` | Playwright against the production build |
| `pnpm test:visual` | Controlled visual regression fixtures and diagnostic artifacts |
| `pnpm assets:verify` | Local file, hash, dimensions, purpose, rights, credit and model metadata checks |
| `pnpm content:verify` | Ten/18 IDs, required prose, reviewed claims, structured dates, coordinates and source references |
| `pnpm docs:check` | Internal path/link checks and absence of stale active-plan contradictions |
| `pnpm check` | Fail-fast lint/type/unit/content/assets/docs/build; browser suites run in explicit configured jobs |

No command may be an `echo passed` substitute. Negative validator fixtures must prove failures are detected. Offline validators verify recorded source metadata/local integrity; network link checks are a separate bounded audit so an intermittent publisher outage does not masquerade as invalid local content.

## 2. Deterministic fixture contract

Each visual fixture pins section, anchor/chapter ID, story position, camera pose, appearance, overlays, quality, viewport, DPR, random seed, browser/OS and renderer information. Freeze presentation noise/cloud phase where needed. Wait for the **requested scene revision's** assets to decode/upload and render, not simply network-idle or canvas-mounted.

Expose test-only readiness instrumentation behind a build/test gate. Do not ship a public debug API that can fetch arbitrary URLs or mutate internal state. A missed ready signal is a failing test, not permission to capture whatever previous chapter happens to remain visible.

Maintain snapshots on a controlled renderer/environment. Different GPUs/drivers can render small differences; record appropriate tolerances with review. Visual snapshots detect regression, while direct recording-to-render comparison establishes fidelity. These are different jobs.

## 3. Required pure-function cases

| Family | Cases and invariants |
| --- | --- |
| Coordinates | Greenwich/90°E/90°W/poles; ordinary round trips; date-line wrapping; singular pole handling; nonfinite rejection |
| Geological mapping | All ten exact anchors; inverse mapping; random p/age round trips; descending brackets; p=0/1; positive age never mislabeled Today |
| Chapter chronology | Exactly eighteen unique authored records plus unnumbered intro; overlapping range dates retain authored order; BCE/CE formatting has no accidental year zero |
| Clock | Same elapsed monotonic time under 30/60/144Hz schedules; pause zero advance; continuous speed changes; seek re-anchor; bounds clamp; hidden intervals excluded |
| State transitions | Intro/start/end/replay; section bookmark restoration; unsupported appearance normalization; modal/manual-input pause; no unexpected resume |
| Overlays | Same chapter produces same set independent of navigation history; future sites disappear on rewind; current/earlier toggles independent |
| Emission | P01–P09 and C01–C17 cannot enable global modern lights; C17 only local effect; P10 exact Today and C18 can enable modern emission |
| Camera | Nearly identical/antipodal directions; poles/date line; positive safe radius; immediate cancellation; one owner |
| Async assets | Latest revision wins; old completion cannot change display; buffer stops effective clock; retry recovery; bounded cache and release ownership |
| Scene URL | Valid round trips; known IDs only; bounded finite numbers; oversized/malformed/unknown-version inputs recover; no executable/remote-resource values |

Expected values must come from independent simple fixtures or derivations, not another invocation of the implementation under test. Random/property tests need recorded seeds for reproduction.

## 4. Required browser journeys

**B01 Opening:** fresh profile opens present-day Planet intro, Natural mode, correct Africa/Europe framing, ten rail anchors and no unsolicited playback. Preview imagery loads under the production base.

**B02 Complete Planet:** start at formation; reach all ten anchors by play, click and keyboard; scrub forward/backward through each interval. Numeric age, narrative ID, asset state and rail agree. Pangea and breakup are visibly different land configurations.

**B03 Complete Civilization:** switch to intro; start chapter 01; traverse all eighteen; assert exact current/total count, recorded order, date label, camera subject and overlay set. Intro must not produce 19 entries.

**B04 Transport coherence:** both visible play/pause controls agree; all three speeds preserve continuity; end clamps; replay resets as specified. Camera travel at 5× does not overlap multiple owners.

**B05 Input arbitration:** stage wheel, rail drag, globe orbit, plus/minus zoom and touch pinch each have one effect. Panel scrolling and browser zoom remain usable. Manual input cancels automation before applying input.

**B06 Panels:** All chapters reaches every item; Sources and contextual explanations have real data/links; opening pauses, closing stays paused; focus returns predictably. Long text/date labels do not overflow.

**B07 Rewind correctness:** from modern night Earth seek to C17, C04, P07 and P01. No future markers or global lights remain. Toggle After dark in every premodern state to verify the policy cannot be bypassed.

**B08 Race conditions:** rapidly seek among formation, Pangea, present, Pacific chapter and night finale while artificially delaying assets. The latest state wins, text/date cannot silently describe stale geography, and retry/buffering are truthful.

**B09 Visibility/motion:** hide/restore the page during play, open/close panels, change reduced-motion preference mid-flight. No hidden-time jump or surprise resume occurs; all story content remains accessible.

**B10 URL/static host:** copy a scene link to a clean profile; refresh at root and `/terra/`; test malformed links and denied clipboard. All local assets/transcoders use correct base paths.

**B11 Resilience:** fail an image, reject a decode, simulate no WebGL and context loss/restoration. No blank permanent canvas, fake success or infinite spinner; fallback story and source access remain available.

**B12 Lifecycle:** after warm-up, run twenty cycles of sections/chapters/qualities and inspect renderer/texture/listener/worker counts. Distinguish a bounded cache from a genuine leak using ownership records and repeated final-state measurements.

## 5. Visual comparison fixtures

Use source upload-relative timestamps as orientation, not exact scripted camera constants. Exclude X playback chrome and macOS recording controls. The source's 2940×1912 pixel dimensions do not establish CSS viewport/DPR. Match aspect ratio and document any crop before comparing proportions.

| Fixture | Reference direction | Primary visual checks |
| --- | --- | --- |
| V01 | Present-day opening, ~00:01–00:04 | Huge globe right; clean left headline; Now upper right; ten-stop rail; mint CTA |
| V02 | Modern After dark, opening variation | Coherent dark-side appearance and restrained historical city lights |
| V03 | Blue hour, opening variation | Deliberate artistic lighting change without changing age/geography |
| V04 | Formation, ~00:13.5 | Dark crust/lava rather than recolored modern continents |
| V05 | Oceans, ~00:14.5 | Clear cooling/water transition, coherent material |
| V06 | Ice, ~00:17.5 | Extensive ice, readable rim, no UI-white overlay |
| V07 | Pangea, ~00:21.5 | Recognizable joined land configuration and stable shader seams |
| V08 | Breakup, ~00:22.5–00:23.5 | Different land arrangement and no obvious translucent duplicate continents |
| V09 | Civilization intro, ~00:26.5 | Larger globe, parchment CTA, intro not counted as chapter |
| V10 | Africa, ~00:29.5 | Broad origin framing and restrained illustrative footprint |
| V11 | Uruk, ~00:38.5 | Correct regional camera/label, count/18, functional footprint card |
| V12 | Indus, ~00:44.5 | Geographic subject, date wrapping and stable narrative hierarchy |
| V13 | Pacific, ~00:55.5 | Wide ocean framing, restrained illustrative island/network cues |
| V14 | Andes, ~00:61.5 | Correct western South America view and label occlusion |
| V15 | West Africa, ~00:63.5 | Timbuktu-region framing, no accidental Europe default camera |
| V16 | Local electrical light, ~00:74.5 | Localized site effect, no modern global city emission |
| V17 | Modern finale, ~00:77.5 | Fine night-light pattern, purposeful pullback and final chapter state |

For every major family, record at least five concrete comparisons across composition, type scale, globe framing, geography, appearance, date, CTA, rail, overlay density or spacing. Fix material errors before accepting regression baselines. Intentional differences include original Terra branding/prose, source/chapters panel design and mobile behavior; they do not excuse a generic dashboard or missing states.

## 6. Responsive and accessibility matrix

Minimum viewports: 1440×900, 1280×800, 390×844 and 360×800; add wide desktop and phone landscape. Test 200% text zoom, long historical ranges, keyboard-only navigation, reduced motion, touch input, visible focus, readable contrast and panel scrolling.

Required meaningful non-canvas path: chapter/anchor navigation, narrative/date/source text, playback control and explanation of the visual scene. A canvas accessible name alone does not make the history usable. Modal focus handling must allow exit and restore focus. Do not globally disable page pinch/scroll simply to simplify globe controls.

Browsers: actual available Chromium and Firefox, Playwright WebKit, and real Safari/iOS where available. Record versions and platform limitations. A Playwright WebKit pass is not a claimed test on Jordan's iPhone. Unavailable real-device coverage remains visible in the release report.

## 7. Performance targets and measurement

Targets are engineering goals, not current results. On a named representative laptop at medium quality, target smooth approximately 60-fps interaction; use average >=55 fps and p95 rAF frame interval <=25ms as initial diagnostic thresholds over at least 30 seconds after warm-up. On a named mobile device, target >=30 fps and p95 interval <=50ms. Report screen refresh rate, browser/OS, DPR, viewport, power mode, build commit and workload. rAF timing measures presented frame cadence, not GPU execution time.

Target initial medium cold transfer <=5 MB and initial JavaScript gzip <=900 KiB where feasible. Measure with cache disabled and a documented network profile. Aim for an interactive low-resolution Earth within three seconds on a stated realistic test connection; report actual results rather than promising universal load time. Lazy-load historical neighbors and secondary panels without making the source drawer unusable offline after initial content load.

Estimated active texture budget: <=128 MiB low/medium, <=256 MiB high, with a bounded current/neighbor cache. Record representation and mip estimates plus render-target/resource counts. No total GPU-memory API is assumed. Check ordinary-image fallback costs as well as compressed paths. A 4K RGBA8 texture with mipmaps is roughly 42.7 MiB, so loading twenty of them at once fails the intended design.

Use React profiling and browser performance tools to identify per-frame rerenders, allocations, long tasks and decode/upload stalls. Repeat before/after the optimization. Never claim the recording's reported 60 fps proves the original or Terra performance.

## 8. Scientific, historical and asset release gate

Ten Planet records and eighteen Civilization records must have reviewed prose and exact supporting source IDs. Source metadata includes publisher, title, URL, access date and claim coverage. Approximate/century/range dates stay qualified. Camera coordinates have a source, and broad-region narratives do not become falsely precise origin pins.

All runtime assets have verified local hashes, dimensions, interpretation, rights/credits and transform recipes. Model assets identify age, layer type and reference frame. Conceptual early Earth is not labeled reconstructed; mask blending is not called plate physics; historical night imagery is not live; footprints are not population/border data. Modern geography in the human story is identified as reference geography rather than a detailed 300,000-year paleoclimate map.

Separate original-code license from image/model/font terms. The creator's public video is inspiration, not permission to copy their source or distribute the user's recording. No private screenshots, credentials or source-video chrome belong in runtime assets or README media.

## 9. CI, deployment and final gate

CI runs meaningful checks on the target commit, with safe bounded artifacts for failures. Build and browser suites operate on `dist`, not only the development server. Configure root versus `/terra/` explicitly and verify texture/transcoder paths, scene hashes and refreshes. Review current official workflow guidance and pin appropriate action versions during implementation.

The Pages workflow and actual public deployment are separate tasks. Only publish a live-demo claim after loading the real deployed URL and checking both journeys, asset requests, scene sharing and sources. When configuration permissions are unavailable, record the exact blocker; a generated `dist` is useful but is not a deployed site.

Release cannot pass with a missing chapter, dead primary control, mirrored geography, fake drift, premodern global lights, unstable camera, stale scene race, unreadable primary content, missing asset rights or fabricated evidence. Curated actual screenshots/demo and a truthful engineering README complete the portfolio handoff. Retain an honest checklist of remaining lesser limitations rather than erasing them at release.
