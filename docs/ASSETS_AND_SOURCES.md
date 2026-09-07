# Terra v2 — asset pipeline and source provenance

## Status

The uploaded screen recording was decoded and visually inspected. **No production Earth textures, plate datasets, fonts, scene models or application media have been acquired or committed in this planning revision.** Source pages listed as consulted were read; candidate institutions and assets still need item-level acquisition and validation. Do not confuse the reference recording with distributable application assets.

## 1. Runtime inventory

| Asset | Chosen direction | Initial quality / acceptance |
| --- | --- | --- |
| Present-day surface | NASA Blue Marble collection, specific credited item | 1K preview, 2K medium, optional 4K high; aligned north-up equirectangular |
| Present-day night emission | NASA Black Marble item/derived emission | 2K medium, optional 4K high; record composite year and derivation |
| Clouds | Separately permitted cloud map or original procedural field | 1K/2K, artistic drift, no false live-weather claim |
| Ocean mask/roughness | Reliable source-derived mask or controlled fallback | Linear non-color map; no guessed geographic classification from arbitrary RGB threshold |
| Early Earth | Original seeded procedural crust/lava/water material | No borrowed creator asset; explicitly conceptual |
| Ice | Authored mask informed by cited epoch explanation | Explicitly illustrative, no temperature/precise extent claims |
| Paleogeography | Offline, model-informed continent/coastline masks and intermediates | 1K preview / 2K primary; one pinned model/reference frame; provenance per output |
| Civilization regions/routes/sites | Small original data set | Source-checked site coordinates, illustrative broad regions/routes |
| Modern local electricity pulse | Original site effect | Restricted to Pearl Street chapter; not global modern lights |
| Fonts/icons | System stack or permitted font; one small icon family | License and notices checked before bundling; exact source font is unknown |
| README/social/demo assets | Actual Terra renders after implementation | No concept image passed off as a running app screenshot |

1K/2K/4K means horizontal dimension of a 2:1 map (1024×512, 2048×1024, 4096×2048). The core release does not require 8K textures.

## 2. Highest-risk pipeline: changing continents

The source visibly changes land configuration. Rotating a present-day Earth or recoloring its surface cannot satisfy this requirement. Establish a low-resolution, real-data proof before spending days polishing atmospheric bloom.

Use a pinned GPlates-compatible model that supports the target interval, with its actual data terms and frame. The official GPlates Web Service exposes reconstructed coastline GeoJSON/PNG: https://gwsdoc.gplates.org/reconstruction/reconstruct-coastlines/ . Its model catalogue warns that a default can change; specify the model explicitly: https://gwsdoc.gplates.org/models/ . Never assume plate boundaries are shorelines.

Initial candidate sampling ages in Ma: 650, 600, 540, 500, 450, 400, 350, 300, 275, 250, 225, 200, 175, 150, 125, 100, 75, 50, 25, 0. This is a **Terra pipeline proposal**, not an assertion that these files exist. Refine sample density from visual midpoint tests, rather than downloading a thousand global maps. Generate canonical masks/SDFs and licensed derivatives offline; record model, age, layer type, reference frame, acquisition and recipe.

For P01–P03 and unsupported intervals, use labeled conceptual surfaces. Do not extrapolate a 0–1000 Ma model back to 4540 Ma or show exact ancient land boundaries without data. A 2024 research model extends to 1.8 Ga, still not Earth's entire history: https://doi.org/10.1016/j.gsf.2024.101922 . A larger model range is not automatic justification to add more dependencies to the baseline.

Do not make the public app depend on a live reconstruction service. Download/prepare the permitted inputs in a reproducible development pipeline, then serve compact same-origin results. If a service request fails, preserve the exact error and try a documented downloadable model path; do not invent a successful dataset acquisition. A completely conceptual fallback for the later continent stages is a material fidelity downgrade requiring an explicit decision, not a silent pass.

## 3. Manifest contract

Create one typed manifest with an entry for every distributed file. Required fields: asset ID, local base-relative path, kind, quality tier, actual dimensions/bytes/hash, source page, exact download URL or original-generation declaration, credited creator, item-specific terms/terms URL, attribution text, observation/model age where relevant, projection/orientation/color space, model/layer/frame where relevant, transformation recipe/tool versions, parent hashes, and `status`.

Allowed statuses include pending, verified and excluded. A release validator rejects pending runtime assets, missing local files, bad hashes, unknown terms, mismatched dimensions, untracked transforms and data maps wrongly tagged as color. Generated original assets still need their seed/recipe recorded. Do not fill missing rights information with the word MIT.

Acquisition scripts use fixed allowlisted HTTPS sources, bounded response sizes/content types and explicit checksums; no arbitrary URL from scene input. Preserve high-resolution source files outside normal Git history. Commit permitted optimized derivatives and scripts, not enormous source movies or scientific archives.

## 4. Day and night sources

NASA Blue Marble Next Generation provides historical monthly surface composites. The collection/base-map pages consulted are:
- https://science.nasa.gov/earth/earth-observatory/blue-marble-next-generation/
- https://science.nasa.gov/earth/earth-observatory/blue-marble-next-generation/base-map/

Choose a specific item. Prefer a base map for programmable lighting; a pre-shaded topographic version can produce contradictory baked illumination if treated as pure albedo. Inspect clouds, snow, water and longitude seam before committing a derivative.

NASA's Earth at Night flat-map page provides historical composites, including 2016 color/grayscale options: https://science.nasa.gov/earth/earth-observatory/earth-at-night/maps/ . The date of the app's Today chapter is not the observation date of that map. Label the image period. Do not display it as live light intensity, population, wealth or real-time human presence.

NASA media guidance: https://www.nasa.gov/nasa-brand-center/images-and-media/ . Check the actual item's credits and any third-party terms, acknowledge sources and avoid endorsement/branding implications. Do not claim all NASA-hosted material has identical unrestricted rights. Original code licensing and external asset terms are separate.

## 5. GPU and transfer budgets

Suggested goals, to measure rather than advertise in advance: <=5 MB initial cold transfer at the medium opening view; <=900 KiB gzip of initial JavaScript where feasible; <=128 MiB estimated active texture residency on low/medium and <=256 MiB on high. Maintain a small current/neighbor cache, not all geological maps plus every quality tier.

RGBA8 storage is width×height×4 bytes before mipmaps. A full mip chain is roughly another third: a 2048×1024 map is about 10.7 MiB including mipmaps; 4096×2048 is about 42.7 MiB. These are representation estimates, not browser-measured total GPU memory. Track render targets and other resources separately. Do not show a fake real-time VRAM meter.

KTX2/Basis can be evaluated with capability detection, a matching local transcoder and a tested fallback: https://threejs.org/docs/pages/KTX2Loader.html . Do not assume a tiny compressed download remains tiny after fallback decompression. Quality switching must preserve chapter/camera and dispose obsolete resources only after replacement readiness.

## 6. Research register

| Source | Use | Revision status |
| --- | --- | --- |
| Uploaded recording, identified in reference/recording-manifest.json | Visual structure, story inventory, selected interactions | Visually inspected; no public media redistribution implied |
| User-supplied Grok prompt | Secondary intent/checklist | Compared with recording; not treated as source-code evidence |
| Original X URLs | Inspiration attribution | Linked; post/comments not independently read in this revision |
| Three.js WebGLRenderer: https://threejs.org/docs/pages/WebGLRenderer.html | Renderer baseline | Official documentation consulted |
| Three.js color management: https://threejs.org/manual/en/color-management.html | Linear lighting/color/output | Official documentation consulted |
| Three.js KTX2Loader: https://threejs.org/docs/pages/KTX2Loader.html | Optional compressed texture pipeline | Official documentation consulted |
| R3F: https://github.com/pmndrs/react-three-fiber | React/Three.js integration | Official repository consulted; exact installed compatibility pending |
| GPlates models and reconstructed coastlines pages above | Named model and offline data path | Documentation consulted; dataset downloads/rights pending |
| Cao et al. 2024 DOI above | Scope/limits of long-span reconstruction | Primary paper abstract consulted; not a Terra accuracy validation |
| NASA day/night/media pages above | Candidate textures and credit requirements | Pages consulted; exact files not acquired |
| Vite deployment: https://vite.dev/guide/static-deploy.html | Static dist/base/hosting behavior | Official guide consulted |
| Playwright snapshots: https://playwright.dev/docs/test-snapshots | Deterministic visual regression practice | Official guide consulted |
| Historical sources in STORY_CONTENT.md | Human narratives | Initial sources consulted; full eighteen-chapter editorial audit pending |

## 7. Credits and scientific labels

Provide in-app credits and source pages, not just a hidden repository comment. Distinguish conceptual early Earth, model-informed ancient geography, modern-reference geography used for human stories, historical satellite composites and illustrative footprints. No blanket physical-simulation claim. Credit the reference author as inspiration without implying collaboration, permission to reuse their code/art, or affiliation.

Use MIT for original application code only if finalized during implementation; retain all required third-party notices. A license file is not created by this planning revision. Do not publish the user's recording or upload private machine paths in performance evidence.
