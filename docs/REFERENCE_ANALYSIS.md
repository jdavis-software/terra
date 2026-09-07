# Reference analysis and reconstruction strategy

Planning date: 2026-09-06, America/Los_Angeles.

## 1. Evidence boundary

The requested references are:

- Original post: https://x.com/akshdeeps_001/status/2096776530005488028
- Video view: https://x.com/akshdeeps_001/status/2096776530005488028/video/1
- Destination repository: https://github.com/jdavis-software/terra

**The video and post contents were not retrievable in the planning environment. No frames, audio, transcript, duration, title, controls, linked application URL, or original source code were inspected.** A claim of full frame-by-frame reverse engineering would therefore be false. This document supplies an evidence-aware implementation proposal and a concrete procedure for closing that gap.

The user's description is an Earth simulator suitable as inspiration for a visually impressive GitHub portfolio project. It does not establish whether the source is an orbital globe, procedural planet, terrain explorer, climate sandbox, destruction simulator, or another subtype. The baseline below deliberately chooses an orbital Earth observatory with a sunlight lab; it must not be presented as the source video's verified feature set.

## 2. Access log

| Attempt | Result | What may be concluded |
| --- | --- | --- |
| Direct X post and video through the web reader | Fetch errors | No post or video content verified |
| Exact post ID and author/topic searches | No usable match for this video | No verified metadata or feature inventory |
| Public embed/syndication and alternative reader endpoints | Access/fetch failures | No usable media URL or frames recovered |
| Container-side public metadata requests | Host resolution failures | No downloaded video or metadata |
| Connector search for an applicable X reader | No matching plugin returned | No available alternate connector resolved access |
| GitHub connector repository metadata and contents | Public repo, `main`, writable, initially empty | Terra could be initialized without replacing application code |

Failed access is not evidence that the post is deleted, private, fake, or lacks a playable video. Do not infer any of those things.

## 3. Evidence ledger

| ID | Claim | Classification | Confidence / action |
| --- | --- | --- | --- |
| E-01 | Jordan wants a fun Earth-simulator portfolio project | User-described | High; direct request |
| E-02 | The two X URLs identify the intended reference | User-supplied identifier | High; content unavailable |
| E-03 | Terra was an empty public repository with write access | Connector-observed | High at planning time |
| E-04 | The source uses Three.js, React, WebGPU, or any named engine | Unknown | Must not be asserted |
| E-05 | The video contains time controls, city lights, clouds, lab sliders, or particular panels | Unknown | Must not be asserted |
| E-06 | Terra should use those features as a cohesive proposed baseline | Proposed design | Intentional product decision |
| E-07 | NASA and graphics-library documentation provide viable research starting points | Documented sources | Specific asset downloads and compatibility still require implementation checks |

## 4. What can and cannot be reverse engineered from a video

Once the video is accessible, screen composition, visual transitions, control labels, pointer behavior, displayed values, apparent camera paths, loading states, and recording dimensions can be observed. Rendering techniques can be hypothesized from those observations, but multiple techniques can produce the same image.

A video alone generally does not prove the source framework, shader code, physics fidelity, data freshness, device performance, backend architecture, or whether an interaction was edited out. Report those as unknown unless corroborated by a linked app, published source, or an explicit author statement. Smooth playback is not an FPS benchmark.

## 5. Proposed visual/technical decomposition

Everything in this section is a Terra design proposal, **not an observed feature**.

| Proposed visual or interaction | Implementation mechanism | Proof required |
| --- | --- | --- |
| Recognizable high-detail Earth | Sphere with licensed equirectangular surface textures, controlled shading | Landmarks align with coordinates; no mirrored map or visible seam |
| Moving day/night boundary | Earth-fixed surface normals dotted with a time-derived Sun vector | Inspector altitude agrees with rendered illumination |
| Nighttime city lights | Historical night-emission texture, suppressed on sunlit side | Lights fade at the terminator, not through daytime oceans |
| Convincing blue limb | Separate atmosphere material with restrained view-angle and sunlight weighting | No neon outline or halo detached from the planet |
| Moving cloud layer | Separate shell and deterministic, explicitly artistic texture advection | Depth order, seam, sunlight and repeatability verified |
| Smooth orbit and place navigation | Constrained camera orbit and cancellable direction interpolation | No through-Earth path or fighting camera controllers |
| Educational seasons | Separate simplified lab state driving solar declination | Zero tilt removes seasonal declination variation |
| Screenshot-worthy tour | Data-driven camera/time/layer keyframes | Same inputs give the same poses; user input interrupts |
| Useful instrument panel | Real scene state, coordinates, solar altitude, provenance | No invented global statistics or decorative live feeds |

## 6. Reference acquisition task — TR-001

Try the supplied public post in the implementation environment's browser and inspect any accessible author-linked demo. Do not spend an entire milestone repeatedly retrying inaccessible endpoints. If it remains blocked, record that fact and continue against this proposed baseline. An accessible user-supplied video is the preferred way to close the visual gap; lack of it is not permission to invent observations.

When media is obtained, record its origin, duration, dimensions, acquisition date, and SHA-256. Keep the raw video outside public Git history unless redistribution is authorized. Use screenshots only as allowed by their rights; an internal reference ledger can cite timestamps without republishing the frames.

Inspect the opening, every material interaction/state transition, the midpoint, and ending. For a short clip, sample every 2–3 seconds plus every UI interaction. Record actual timestamps, not a prewritten imagined timeline. Compare adjacent frames before claiming animation mechanics. Listen to audio if it contains implementation claims; distinguish author statements from verified behavior.

Use this ledger structure:

| Frame/time | Visible composition | Interaction and before/after state | Text actually readable | Proposed mechanism | Confidence | Terra task mapping |
| --- | --- | --- | --- | --- | --- | --- |
| Pending accessible media | — | — | — | — | Unverified | TR-001 |

Do not fill the table with guessed observations.

## 7. If a linked live app becomes available

Inspect its DOM, network requests, public assets, and interactions using ordinary authorized browser access. Record observable technology hints and their strength. A package name in a downloaded bundle is stronger evidence than visual resemblance. Do not bypass access controls, extract secrets, or copy unlicensed code/assets.

Check initial loading, orbit/zoom limits, all visible controls, narrow-screen behavior, keyboard access, error states, and asset provenance. Capture comparisons at equal aspect ratios. Record differences between the video and app; the video may show an older build.

## 8. Fidelity decision after inspection

Classify each difference as: baseline cosmetic adjustment, missing core interaction, proposed Terra enhancement, unavailable/unsupported source feature, or intentionally excluded scope. Update `DECISIONS.md` before changing required architecture. Visual adjustments may proceed within the baseline; a wholesale switch to a terrain or destruction simulator is a material scope change and must be clearly surfaced rather than quietly absorbed.

There are two separate release claims:

1. **Terra baseline complete:** the proposed product meets its own specification and tests.
2. **Reference fidelity verified:** actual inspected reference states were compared and the differences documented.

The first can pass while the second remains unresolved. Never merge them into a blanket claim that the original was reproduced.

## 9. Portfolio differentiation

The intended value is not copying a viral clip. Terra should demonstrate original engineering decisions: a coherent coordinate system, separation of visual effects from numerical models, deterministic scene reproduction, GPU-aware asset management, robust input behavior, and a documented quality process. The public README should explain those choices using real screenshots and measured results after implementation.
