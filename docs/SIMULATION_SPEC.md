# Simulation, coordinates and numerical contracts

## 1. Honesty and units

Core Terra models sunlight geometry on a sphere and offers a deliberately simplified lab. It does not solve climate, weather, fluid dynamics, atmosphere chemistry, orbital perturbation for spacecraft, or geodesy. Artistic clouds, atmosphere thickness and surface appearance are separate from numerical results.

Use radians inside trigonometric functions, degrees at UI/API boundaries, milliseconds for clock values and Earth radii for render distances. Name units in variables and types. Use UTC epoch milliseconds for Earth time; never parse ambiguous locale dates. Lab elapsed time is not a UTC epoch.

The supported Earth date-input range is 2000-01-01T00:00:00Z through 2100-12-31T23:59:59.999Z. This is a product/testing boundary. It is not an assertion that the provider fails outside it.

## 2. Earth-fixed world coordinates

Terra uses a right-handed, Y-up frame. North pole is +Y; latitude 0°, longitude 0° is +X; latitude 0°, longitude 90°E is −Z. Longitude is east-positive, normalized to [−180°, 180°). The visible sphere has radius R=1.

For latitude φ, longitude λ and radius r:

```text
x = r cos(φ) cos(λ)
y = r sin(φ)
z = −r cos(φ) sin(λ)
```

Inverse for a nonzero vector:

```text
r = sqrt(x² + y² + z²)
φ = asin(clamp(y/r, −1, 1))
λ = atan2(−z, x)
```

At an exact pole, longitude is mathematically undefined. Preserve an explicit chosen longitude for camera configuration if needed; point-inspection inverse conversion should flag longitude as undefined instead of claiming high geographic precision. Normalize near-boundary values consistently.

Do not assume the default SphereGeometry UV orientation matches this convention. Produce canonical UVs or one documented texture transform. For an equirectangular image whose left edge is 180°W and top is north, use `u = (λ + π)/(2π)` and a documented vertical upload convention so north is at the top. Sphere vertices on either side of the seam may share positions but need distinct u=0/u=1 values. Verify five landmarks and both sides of the date line before shading polish. Do not combine untracked mesh rotations, texture offsets and longitude sign fixes.

Required anchor tests: (0,0)→(1,0,0); (0,90)→(0,0,−1); (0,−90)→(0,0,1); (90,any)→(0,1,0); south pole→(0,−1,0). Round-trip tolerance for ordinary nonpolar points: 1e−8 degrees in double-precision CPU tests. Near poles, test position/angular separation rather than unstable longitude.

## 3. Earth clock

Use an anchored, monotonic clock, not accumulated animation-frame deltas:

```text
simulationMs = anchorSimulationMs
             + (monotonicNowMs − anchorMonotonicMs) × speed
```

When paused, the evaluated time is the saved anchor value. On speed change, seek, mode switch or pause, evaluate the previous clock and establish a new anchor. This prevents discontinuity when the user changes from 1× to 3600×. It also prevents browser frame rate from changing the simulation result.

A hidden-tab event explicitly pauses and re-anchors; returning does not add hidden wall time. `Now` sets the Earth epoch from the device's current UTC clock and selects 1× play. The UI must not call historical textures live. At supported time bounds, stop playback, clamp and show a small boundary message.

Tests: a 10-second monotonic interval at 60× advances 600,000 simulated milliseconds; pause advances zero; speed change is continuous; seek resets correctly; hidden duration is excluded; different frame schedules with the same final monotonic timestamp give the same result.

## 4. Earth Sun direction provider

Use a small adapter around Astronomy Engine, with the installed API verified before coding. The official reference exposes geocentric vectors, EQJ→EQD rotation, equatorial conversion and Greenwich Apparent Sidereal Time. Source: https://github.com/cosinekitty/astronomy/blob/master/source/js/README.md . The following sequence is a Terra adapter design based on those APIs, not copied implementation code:

```text
sunEqj = GeoVector(Sun, date, aberration=true)
sunEqd = RotateVector(Rotation_EQJ_EQD(date), sunEqj)
(raHours, decDeg) = EquatorFromVector(sunEqd)
gastHours = SiderealTime(date)
subsolarLongitudeDeg = wrap180(15 × (raHours − gastHours))
subsolarLatitudeDeg = decDeg
sunDirection = unitVector(subsolarLatitudeDeg, subsolarLongitudeDeg)
```

Use consistent apparent/of-date conventions throughout. Do not mix J2000 right ascension with of-date sidereal time. Verify current function signatures and vector units against the installed package. Normalize the output vector and reject invalid dates/nonfinite output.

The surface is Earth-fixed; the Sun direction changes as time advances. Do not additionally spin the Earth mesh to simulate the same day. Camera movement changes what is seen, not the physical illumination at a location.

Cache ephemeris samples in simulated-time space. A reasonable initial interval is 30 simulated seconds, with normalized vector interpolation between adjacent samples; seek jumps evaluate the new bracket immediately. Bound cache size. Measure performance before tuning the interval. Check interpolation error against direct adapter evaluation; target less than 0.05° over the supported test fixtures. Avoid interpolation across a discontinuous longitude representation by interpolating vectors, not wrapped angles.

Validate the adapter with independent solar-position fixtures or an independently implemented reference calculation with a documented source and matching geometric conventions. Comparing an adapter to itself is not independent validation. Store fixture origin/date/model/units/tolerance. Target ≤0.25° angular discrepancy for the core display; investigate larger errors rather than loosening the threshold blindly. This is a Terra acceptance target, not a quoted library accuracy guarantee.

## 5. Surface illumination and readouts

For normalized surface direction n and normalized Earth-fixed Sun direction s:

```text
mu = clamp(dot(n, s), −1, 1)
geometricSolarAltitudeRad = asin(mu)
relativeDirectSunlight = max(0, mu)
```

The dot product is both the basis for the physical readout and the direction used in the shader. Artistic shading may soften the visible boundary but must not move the numerical Sun. Use clamped functions to prevent NaN values at poles and extrema.

Classification based on geometric center altitude: day at >0°; civil twilight from 0° to −6°; nautical from −6° to −12°; astronomical from −12° to −18°; night below −18°. These category angles are conventional definitions; Terra's spherical, nonrefracted calculation is not an observed sunrise prediction. Verify category references during TR-005; official starting reference: https://www.weather.gov/lmk/twilight-types . Exact category boundary inclusion must be explicit and tested.

Local apparent solar time for nonpolar points:

```text
hourAngleDeg = wrap180(longitudeDeg − subsolarLongitudeDeg)
localSolarHours = positiveModulo(12 + hourAngleDeg/15, 24)
```

Label it `Local apparent solar time`, not local clock time. At the subsolar longitude it is 12:00; opposite that meridian it is 00:00. Near exact geographic poles, show that longitude-based solar time is undefined. The function does not provide civil time zones or daylight-saving rules.

Night light artistic mask example: `1 − smoothstep(−0.08, 0.02, mu)`. This is a proposed appearance parameter, not a physical twilight model. Keep inspector categories independent of artistic softness. A day texture should be interpreted as albedo rather than as a second baked-lighting model where possible.

## 6. Simplified lab model

The lab holds season angle fixed while a synthetic solar day advances. It does not solve orbital dynamics. Define axial tilt ε and season angle L, with 0° a northward equinox, 90° northern summer, 180° southward equinox and 270° southern summer:

```text
declination = asin(sin(ε) × sin(L))
dayPeriodMs = solarDayHours × 3,600,000
subsolarLongitudeDeg = wrap180(initialLongitudeDeg
                           − 360 × elapsedSimMs/dayPeriodMs)
sunDirection = unitVector(declination, subsolarLongitudeDeg)
```

`solarDayHours` means the time for the Sun to return to the same Earth-fixed longitude in this model. It is not a sidereal rotation period, and it is not a statement about orbital changes or conservation laws. Use 0.5–96 hours and tilt 0°–60° to keep the demonstration understandable. The surface geography remains a static Earth-shaped teaching surface even under hypothetical settings.

Changing tilt/season is instantaneous and explicitly hypothetical. Changing day duration preserves the current phase: compute current subsolar longitude, re-anchor initial longitude/time, then apply the new duration. Do not jump the Sun merely because a slider changed units. Direct phase control intentionally moves the Sun and pauses playback.

Entering the lab stores the Earth scene, including its time and selection. Leaving restores it paused. Lab presets never modify Earth mode's ephemeris or the system clock.

## 7. Daily sunlight curve

For the selected point, sample one full synthetic solar day at 361 phase points, including both endpoints. For each sample compute the same n·s used by the scene and clamp negative values to zero. Horizontal axis: elapsed simulated hours; vertical axis: relative direct sunlight, dimensionless 0–1. Do not claim these samples measure irradiance or temperature.

Cache by model parameters and selected latitude/longitude, not render frames. If sampling causes a measured stall, put only this calculation in a worker with cancellable request IDs. A selected-point or parameter change must invalidate the old curve. An empty selection shows an explanation, not an invented curve for an undisclosed location.

Numerical invariants: zero tilt gives zero declination for all season angles; ±season symmetry holds; at the equator with zero declination, a geometric day is half the cycle; increasing day duration stretches the time axis; all values remain finite in [0,1]; the first and last phase samples match. Polar day/night curves must remain stable and interpretable.

## 8. Artistic effects and reproducibility

Cloud phase is deterministic from a seed and the evaluated Earth/lab time using a documented slow artistic drift rate. It does not represent measured winds. Decorative stars use a fixed seed. Camera auto-orbit has its own presentation phase and must be disabled/fixed in screenshot fixtures; it does not change epoch or sunlight at a place.

Atmosphere radius and cloud-shell spacing may be exaggerated for visibility. Store these as named appearance constants, not fake measured altitude readouts. No temperature should be inferred from night-light brightness, cloud alpha, axial tilt or a normalized sunlight curve.

## 9. Required numerical test families

Coordinates/UV anchors; longitude wrap and poles; monotonic clock continuity and visibility; ephemeris frame/units; solar-angle dot products; daily direction progression; category boundaries; local solar time; lab phase continuity; daily-curve bounds/symmetry; serialization round trips; deterministic results under 30/60/144Hz frame schedules. Include leap-day, year-boundary, UTC-midnight, near-date-line and near-pole fixtures.

A physically plausible-looking screenshot is not proof that these calculations are correct. Numerical tests and visual orientation checks are separate release requirements.
