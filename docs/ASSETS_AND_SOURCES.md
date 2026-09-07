# Assets, provenance and primary sources

## 1. Current acquisition status

No production texture, source video, screenshot, font, model, audio file, or application binary was acquired or committed during planning. The sources below are research starting points. Exact download URLs, terms, hashes and derivatives must be established in TR-002 and TR-020 before release.

Use independently obtained, permitted assets. Do not hotlink the reference app's textures or redistribute the X video merely because it is public. Do not add NASA branding or suggest endorsement. An Earth rendered from data is the product; a generated photo of a globe is not a replacement for interactive geography.

## 2. Candidate asset inventory

| Asset | Candidate source | Planned derivatives | Usage / fallback |
| --- | --- | --- | --- |
| Day surface | NASA Blue Marble: Next Generation | 1024×512 preview; 2048×1024 low; 4096×2048 medium; 8192×4096 optional high | Verify projection, orientation, baked cloud/shading content and individual credits |
| Night emission | NASA Earth at Night/Black Marble flat maps | Aligned 2:1 maps at appropriate tiers | Label acquisition/composite year; never live city data |
| Cloud alpha | Separately licensed global cloud texture or original procedural texture | 2K low/medium, 4K optional | Credit historical texture; procedural/artistic fallback must be labeled |
| Ocean mask | Verified land/water mask from an appropriate data source | Single-channel linear data at 2K/4K | Omit dedicated specular mask if reliable data cannot be acquired |
| Surface normal/roughness | Verified source or documented derived map | Linear non-color maps only where visually valuable | Do not invent topography from arbitrary color brightness |
| Place records | Small curated, source-checked list | Bundled JSON/TS with provenance | Coordinates/names only; no unnecessary third-party service |
| Stars | Original seeded point distribution | Runtime geometry | Decorative, not an astronomical catalogue |
| Fallback poster / README media | Actual Terra screenshots after rendering exists | Responsive WebP/PNG and short demo clip | Never claim concept images are screenshots of the running app |
| Icons | One permitted icon package or original simple icons | Tree-shaken/code-native | Retain its license notice |
| Fonts | System fonts | No bundled font download | No external font needed for core |

Blue Marble Next Generation describes a monthly Earth-image collection; choose a specific source image and identify its period. Black Marble flat maps include historical night-light composites such as the 2016 collection. Those are different from a live satellite feed. Sources: [Blue Marble](https://science.nasa.gov/earth/earth-observatory/blue-marble-next-generation/) and [Black Marble flat maps](https://science.nasa.gov/earth/earth-observatory/earth-at-night/maps/).

## 3. Required manifest

Create `public/assets/manifest.json` and a typed loader contract. Each shipped file needs:

```json
{
  "id": "earth-day-medium",
  "path": "assets/earth/day-4096.ktx2",
  "kind": "albedo",
  "status": "pending-acquisition",
  "sourcePage": "record exact item page before shipping",
  "downloadUrl": "record verified source file before shipping",
  "creator": "record exact credited creator",
  "licenseOrTerms": "record item-specific terms",
  "termsUrl": "record verified terms page",
  "attribution": "record required credit text",
  "acquisitionDate": null,
  "observationPeriod": null,
  "sha256": null,
  "width": 4096,
  "height": 2048,
  "projection": "equirectangular",
  "colorSpace": "srgb",
  "transformRecipe": "record orientation, resize, compression and tool versions",
  "derivedFrom": null
}
```

This is an illustrative manifest contract, not a real asset entry. `assets:verify` must fail release validation for pending status, missing source/terms/hash, absent local files, dimensions that do not match, unknown texture purpose, and incompatible UV/orientation metadata. Do not invent hashes or mark a pending asset as shipped.

Keep original scientific data outside normal Git history when large. Commit reproducible acquisition/derivation scripts and small verified runtime derivatives. Acquisition scripts must use an allowlisted exact HTTPS URL, check content type/size and verify hashes; no arbitrary URL execution. Record checksums before changing a derivative recipe.

## 4. Production asset pipeline

Acquire an item with identifiable terms and attribution. Inspect its projection and geographic alignment. Preserve a source copy locally with a checksum. Normalize to one canonical longitude/north-up convention. Generate quality tiers with pinned tooling. Encode color textures with correct color metadata; encode masks/normal maps as linear non-color. Generate mipmaps. Compare at equal camera distances. Record transferred bytes and estimated/actual GPU texture cost separately.

Only then add the derivative to the manifest and credits panel. Test the same deployed asset path under `/terra/`. Do not bundle an 86K scientific map directly into the browser because its source is impressive.

KTX2/Basis is an optional encoding choice, not an excuse to assume all devices support one native compression format. Use Three.js's capability-aware loader and matching local transcoder, or fall back to ordinary textures. Source: https://threejs.org/docs/pages/KTX2Loader.html .

## 5. Memory budgeting

Uncompressed RGBA8 approximate storage without mipmaps is width × height × 4 bytes. A full mip chain adds roughly one third. For example, a 4096×2048 RGBA8 map is about 32 MiB before mipmaps and about 42.7 MiB with them; an 8192×4096 map is about 128 MiB before mipmaps and about 170.7 MiB with them. These are estimates for that representation, not browser-reported total GPU memory.

Several such maps plus render targets can exceed a laptop/mobile budget quickly. Compressed transfer size is not equivalent to GPU residency. Target estimated active textures ≤128 MiB on low/medium and ≤256 MiB on high after measuring the actual representation and fallbacks. High-resolution upgrades are opt-in/capability-gated and must not require retaining every lower tier forever.

No universally reliable cross-browser total GPU-memory API is assumed. Record estimate methodology and resource counts; do not present a made-up GPU-memory meter as measured fact.

## 6. Rights and credits

NASA's media guidance generally permits educational/informational use of much NASA content, while requiring attention to third-party rights and avoiding endorsement implications. Check the individual item's credit and current guidance rather than labeling all material on NASA websites unrestricted. Use source acknowledgments, not NASA logos as Terra branding. Official guidance: https://www.nasa.gov/nasa-brand-center/images-and-media/ .

For original application code, MIT is the proposed license. External assets retain their own terms and must be excluded from any blanket claim that the entire repository's media are MIT. Add an asset credits document, an accessible in-app Credits dialog, and appropriate notices for libraries/icons. Preserve raw license texts where distribution requires them.

The reference author receives inspiration credit via the original links, without implying their involvement or granting rights over their code/video. Do not copy the creator's project title, logo or prose beyond necessary factual attribution.

## 7. Primary technical source register

| ID | Source | Used for | Planning status |
| --- | --- | --- | --- |
| S01 | https://x.com/akshdeeps_001/status/2096776530005488028 | User's inspiration post | Inaccessible; no content verified |
| S02 | https://x.com/akshdeeps_001/status/2096776530005488028/video/1 | User's reference video | Inaccessible; no frames inspected |
| S03 | https://threejs.org/docs/pages/WebGLRenderer.html | WebGL2 baseline, renderer diagnostics | Documentation consulted |
| S04 | https://threejs.org/manual/en/color-management.html | Texture color spaces and output correctness | Documentation consulted |
| S05 | https://threejs.org/manual/en/how-to-dispose-of-objects.html | GPU/resource teardown | Documentation consulted |
| S06 | https://threejs.org/docs/pages/KTX2Loader.html | Texture transcoding and capabilities | Documentation consulted |
| S07 | https://github.com/cosinekitty/astronomy/blob/master/source/js/README.md | Sun vector and coordinate/time API | Documentation consulted; installed-version verification pending |
| S08 | https://science.nasa.gov/earth/earth-observatory/blue-marble-next-generation/ | Candidate day imagery | Collection page consulted; item acquisition pending |
| S09 | https://science.nasa.gov/earth/earth-observatory/earth-at-night/maps/ | Candidate night imagery | Collection page consulted; item acquisition pending |
| S10 | https://www.nasa.gov/nasa-brand-center/images-and-media/ | Media/attribution constraints | Guidance consulted; item checks pending |
| S11 | https://vite.dev/guide/static-deploy.html | Static hosting and Pages base | Documentation consulted |
| S12 | https://playwright.dev/docs/test-snapshots | Controlled browser visual regression | Documentation consulted |
| S13 | https://r3f.docs.pmnd.rs/advanced/scaling-performance | R3F performance implementation reference | Reader failed; revisit at implementation time |
| S14 | https://r3f.docs.pmnd.rs/advanced/pitfalls | R3F frame-loop/state guidance | Reader failed; revisit at implementation time |
| S15 | https://www.weather.gov/lmk/twilight-types | Twilight terminology | Candidate reference; verify before publishing explanations |

Do not claim a failed or pending source was read successfully. Recheck API and usage-policy details at implementation time. This register documents why a source matters; it is not a substitute for item-level provenance or runnable verification.
