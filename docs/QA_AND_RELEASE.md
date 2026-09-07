# Quality assurance and release contract

## 1. Status

These are implementation requirements, not completed test results. The planning repository has no application, test suite, media capture or deployment yet. Every measured claim must be filled from an actual run.

Two independent outcomes must be reported: compliance with the proposed Terra specification, and fidelity to the original X video. The latter remains unverified until the actual video is inspected and compared.

## 2. Script contract

| Command | Required behavior |
| --- | --- |
| `pnpm dev` | Local development server with documented URL/base |
| `pnpm build` | Production static build; fail on build errors |
| `pnpm preview` | Serve the real built output for manual/browser verification |
| `pnpm lint` | Real source linting; no success stub |
| `pnpm typecheck` | Strict TypeScript validation without emitting app output |
| `pnpm test:unit` | Deterministic nonwatch unit/integration suite |
| `pnpm test:e2e` | Playwright against a production preview; meaningful failure exit |
| `pnpm assets:verify` | Verify local files, metadata, hashes, dimensions and required credits |
| `pnpm docs:check` | Verify local documentation links, task references and counts; external links checked separately |
| `pnpm check` | Lint, typecheck, unit tests, assets, docs and build; fail fast |

Do not claim these commands work until they exist and have run. Pin the runtime/package manager and one dependency lockfile. A clean clone must not need a private service, global `.codex` changes or undocumented environment variables.

## 3. Unit and numerical acceptance matrix

| Test family | Required cases | Expected result |
| --- | --- | --- |
| Coordinates | Anchor axes, 1,000 seeded random points, date line, near poles, invalid/zero vectors | Correct sign/orientation; nonpolar round-trip ≤1e−8° |
| UV mapping | Canonical seam/north orientation and landmark mapping | No mirror/flip; documented seam duplication |
| Clock | 1×/60×/3600×, pause/seek/speed/visibility, date bounds | Continuous, frame-schedule independent; hidden time excluded |
| Solar provider | Documented independent fixtures across seasons/leap day/year bounds | Display error ≤0.25° and additional interpolation error <0.05° |
| Solar readouts | Subsolar/antipodal/terminator points, category edges | Dot-product-consistent altitude and exact tested boundary rules |
| Apparent solar time | Subsolar noon, opposite midnight, wrap and poles | Correct 0–24h cycle; undefined-pole behavior |
| Lab model | 0°/23.44°/60° tilt, four season angles, duration/phase changes | Declination/phase invariants and no hidden UTC mutation |
| Daily curve | Equator, both poles, continuous day/night, long/short solar day | 361 finite samples in [0,1], endpoints equal, honest time axis |
| Camera math | Parallel/antipodal directions, near poles, min/max radius | Safe path outside Earth and deterministic cancellation |
| State | Presets, mode restoration, URL/local precedence and reset | No stale/cross-mode state corruption |
| Serialization | Round trip, unknown version, >8KiB, nonfinite, bad ID/date/URL | Reject safely and retain usable default |
| Asset manifest | Missing file/hash/credit, wrong dimensions, pending status | Fail release validation with actionable errors |

Fixtures must have origin, conventions, date and tolerance. Do not derive both expected and actual values from the same function and call that independent verification. Property/invariant tests complement but do not replace independent solar fixtures.

## 4. End-to-end journeys

**E2E-01 First visit:** load `/terra/` with a clean profile, wait for actual scene readiness, assert visible textured Earth/nonblank pixels, orbit/zoom/reset, open Help and Credits. Fail on uncaught errors, shader compile/link errors or required-asset failures.

**E2E-02 Explore:** search a named place, navigate, verify selection and inspector, click a new surface point, drag without accidental selection and test empty space. Confirm no far-side marker bleed.

**E2E-03 Time:** play, change speed without jump, pause, scrub, enter UTC date, cross midnight, use Now, reset, hide/show the tab. Compare readouts and lighting to the same expected state.

**E2E-04 Lab:** enter with a selected place, change tilt/season/day duration, check the chart and label, switch presets, leave and verify Earth restoration. Invalid parameter input is rejected.

**E2E-05 Showcase:** start/pause/resume/cancel tour, interrupt with wheel and keyboard, restore state, enter/exit photo mode via keyboard and touch, export and inspect an actual nonblank image.

**E2E-06 Share/storage:** copy scene, open in a fresh context, compare serialized values, deny clipboard, corrupt URL/storage, test oversized payload and reset only Terra settings.

**E2E-07 Keyboard/mobile:** complete the first-session journey without a pointer, then repeat primary paths with mobile touch emulation. Check modal focus and 200% text zoom.

**E2E-08 Failures:** block a required texture, fail a high-tier optional texture/decoder, disable storage, force unsupported WebGL and context loss/recovery. Every state remains informative and recoverable.

Run production-base tests under `/terra/`, not only `/`. No arbitrary sleeps in place of readiness or stable-state checks. A test seam may expose diagnostics in development/test builds, but production must not expose arbitrary state mutation or remote-asset loading. Prefer normal UI and validated scene URLs for tests. A simple read-only readiness marker is acceptable in production.

## 5. Visual test contract

Required captures: default Blue Marble, Night Lights, Terminator, selected place/inspector, lab with curve, mobile inspector, mobile lab, photo mode, loading error, WebGL fallback. Use fixed time, seed, paused motion, camera, quality and DPR. Wait for texture upload, shader compilation and a completed render before capturing.

Primary dimensions: 1440×900 and 390×844. Secondary: 1280×800, 1920×1080, 360×800 and a phone landscape layout. Record OS/browser/GPU or software-renderer status. Browser screenshots can vary across rendering environments; keep controlled baselines and defensible tolerances, not one unexplained global threshold.

Visually inspect every initial baseline. Compare the selected design/baseline and actual application, including at least: globe size/composition, continent alignment, terminator/lighting, atmospheric limb, typography, panel spacing, icon treatment, focus state and mobile overflow. Fix material defects before accepting baseline updates.

Playwright's documentation describes screenshot comparisons and environment considerations: https://playwright.dev/docs/test-snapshots . A green screenshot diff against a poor initial image is not evidence of good design.

## 6. Performance budgets — targets, not current results

Use a production build, stable 60-second scenario, 5-second warm-up, no devtools capture overhead during final measurement, and at least three runs. Report median and p95 frame interval along with long-task/interaction observations. Record refresh rate where known. Headless software rendering is useful for correctness smoke tests, not proof of laptop/mobile GPU speed.

| Dimension | Initial target | Measurement conditions |
| --- | --- | --- |
| Desktop medium | Median frame interval ≤18.2ms; p95 ≤33.3ms | Recorded real desktop/laptop, 1440×900, medium, normal refresh |
| Mobile low | Median frame interval ≤33.3ms; p95 ≤50ms | Recorded real mobile device, portrait, low |
| First meaningful Earth | ≤6 seconds | Cold load, 10Mbps down / 100ms latency; actual textured preview, not just spinner |
| Initial compressed JS | ≤900 KiB | Sum of required initial JS chunks, gzip-equivalent method recorded |
| Initial transferred assets | ≤4 MiB | Required initial scene assets before optional upgrades; exclude later high tier |
| Estimated active textures | ≤128 MiB low/medium; ≤256 MiB high | Include actual fallback representation/mipmaps; state estimation method |
| Steady interaction | No repeated >100ms main-thread stalls during orbit/scrub | Profile representative controls, not only idle scene |
| Resource stability | No monotonic growth after warm-up over 20 tier/remount cycles | Count geometries/textures/programs/workers; explain caches |
| Idle behavior | No unnecessary continuous frames when all motion is paused | Demand rendering and explicit invalidation |

These are engineering targets chosen for Terra, not capabilities already demonstrated. If they fail, identify the bottleneck and fix or document a justified budget revision in `DECISIONS.md` with before/after evidence. Do not silently lower quality or remove required features to disguise failure.

A screenshot pass cannot establish these budgets. An estimated texture footprint is not a total GPU-memory measurement. If target hardware is unavailable, state exactly which tests remain unverified; do not invent devices or benchmark numbers.

## 7. Accessibility and compatibility

Keyboard access must cover navigation, manual coordinate entry, search, time, lab, share, tour exit, photo exit and help. Dialogs require focus management and restoration. Inputs need visible labels; controls need readable focus states and meaningful accessible names. Charts require text/table equivalents. Announce selection/error changes sparingly, not every numerical frame update.

Respect reduced motion and user quality settings. Text and focus contrast must be checked against the actual selected tokens. Touch targets should be at least 44px where practical. Never disable browser zoom globally.

Compatibility target: current stable Chromium, Firefox and Safari, plus representative iOS/Android browsers. Record exact versions tested. Playwright WebKit is not identical to a real Safari/iPhone hardware run. Narrow support claims honestly when a device/browser has not been verified.

## 8. Security and supply-chain checks

No runtime secrets or mandatory external inference. No arbitrary remote assets from URL state. No `eval`/expression execution for lab parameters. Bound JSON input and validate all numbers. Use minimal Actions permissions, trusted deployment events and reviewed action versions. Do not run privileged deployment workflows against untrusted fork code.

Verify actual runtime requests and dependencies. Preserve third-party notices and asset terms. Avoid shipping large raw media, personal paths, private test data or credentials in traces/screenshots. A static app still needs this audit.

## 9. Deployment acceptance

`dist` must run with both the documented Pages base `/terra/` and a root base when rebuilt for another host. Use the configured base for textures, decoder files, posters and icons. Prefer hash scene state rather than routes requiring server rewrites. Verify deep-link refresh and corrupt hash handling.

A deployment is complete only when the actual public URL loads in a browser, the required assets return successfully, a scene link reproduces state and a deploy/workflow identifier is recorded. Do not create a fictional Pages URL or present a local preview as deployed. If settings/permissions prevent publication, mark deployment blocked and provide the build/runbook as partial completion.

## 10. Release evidence packet

The implementation release should include: exact dependency/runtime versions; command results; unit/ephemeris fixture provenance; browser/device matrix; performance measurements with conditions; selected visual baselines and mismatch ledger; source/asset credits; real screenshots/demo clip; known limitations; verified public URL or explicit blocked deployment status.

The root README must explain what is actually implemented and link the case study. Proposed/optional features remain labeled. Do not add build/coverage/performance badges unless they point to real evidence. Maintain the distinction between Terra-spec completion and unverified source-video parity.
