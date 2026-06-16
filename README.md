# Measuring Gravitational Acceleration with a Simple Pendulum

A Physics 1 group project that measures the local gravitational acceleration *g* using a
simple pendulum and applies physical corrections from Nelson & Olsson (1986) to push the
measurement beyond the idealized point-mass model. The experiment was carried out in
Daegu, South Korea (accepted local *g* ≈ 9.797 m/s²).

> **Status:** Data collected; analysis in progress. See `docs/` for the pre-lab and the
> raw data sheet.

## Live demo

An interactive visualization lives at the repository root (`index.html`) and is published
with GitHub Pages:

**https://<your-username>.github.io/<repo-name>/**

It shows two pendulums running 20 oscillations at Daegu gravity — a clean simple pendulum and
one with a hooked knot that drifts into a faint double pendulum — plus a calculator that solves
`g = 4π²·l·N²/t²` from a length and a stopwatch time. All physics formulas are documented at
the top of the `<script>` block in `index.html`.

---

## Team Members

- **Munkh-Iveel**
- **Zevarniso**
- **Bolor**
- **Munkhtemuulen**

---

## Project Overview

- **Problem.** The textbook formula `g = 4π²l / T₀²` assumes an ideal pendulum: a point mass
  on a massless, inextensible cord swinging through an infinitesimal angle. A real pendulum
  violates every one of those assumptions, so the naive value of *g* carries a systematic
  bias.
- **Goal.** Measure *g* from the period of a real pendulum, then correct the measured period
  toward the ideal period using the dominant physical corrections, and compare the raw and
  corrected results against the accepted local value.
- **Approach.** Time 20 oscillations per trial across several release angles (5°, 10°, 15°,
  20°), repeat for multiple trials, average, and apply the finite-amplitude, finite-bob-radius,
  and cord-mass corrections. The multi-angle data also lets us *demonstrate* the
  finite-amplitude effect directly: the period visibly grows with the release angle.

---

## Research Inspiration

The project is inspired by **R. A. Nelson & M. G. Olsson, "The pendulum — Rich physics from
a simple system," *American Journal of Physics* 54(2), 112–121 (1986).** That paper measures
*g* to four significant figures with a 3 m pendulum and a long list of corrections
(finite amplitude, mass distribution, air buoyancy, damping, added mass, wire stretching,
support motion). Our project adopts the same conceptual framework but at an introductory
scale: a shorter pendulum, a stopwatch instead of a cathetometer, 20 oscillations instead of
100, and a deliberately small subset of the corrections that actually matter at our precision.

---

## Methodology

### Materials
- Steel ball, diameter 27 mm (radius *a* = 13.5 mm), mass *m* = 200.0 ± 0.1 g
- Thin thread/wire, length ≈ 85 cm (and a shorter length for the refined run)
- Small balancing weights for the stand/ring
- Foam board used as a release/guide surface
- Wood piece inserted at the knot to suppress double-pendulum motion

### Equipment
- Digital calipers (ball diameter)
- Laboratory scale (ball mass, cord mass)
- Ruler / measuring tape, resolution ≤ 1 mm (effective length)
- Angle-measuring device (verified release plane to ≈ 89.7°, i.e. ~0.3° from vertical)
- Smartphone stopwatch and camera

### Software
- Spreadsheet (period averaging, standard deviation, error propagation)
- Plotting tool for period-vs-angle and *g* comparison

### Experimental procedure
1. Measure ball diameter (3×) and mass; measure cord mass.
2. Tie the cord to a fixed pivot; measure effective length *l* from pivot to ball center (3×, mean).
3. Set the release angle with the angle device; release without lateral push.
4. Time 20 complete oscillations; repeat for 6 trials per angle.
5. Repeat for angles 5°, 10°, 15°, 20°.
6. Compute `T = time / 20`, average, then correct toward `T₀` and solve for *g*.

### Corrections applied
| Correction | Formula (ΔT/T₀) | Effect |
|---|---|---|
| Finite amplitude | (1/16)θ₀² + (11/3072)θ₀⁴ | Largest; increases period |
| Finite bob radius | (1/5)(a/l)² | Small; increases period |
| Cord mass | −(1/12)(m_w/m) | Decreases period |

---

## Results

- **Finite-amplitude effect observed directly.** In the refined run the mean period rose
  steadily with release angle (≈ 1.757 s at 5° → ≈ 1.772 s at 20°), an ~0.8% increase that
  matches the (1/16)θ₀² prediction.
- **Corrected vs. raw *g*.** Applying the corrections brings the period toward the
  small-angle ideal and the corrected *g* toward the accepted local value (≈ 9.797 m/s²).
  *(Final numeric value to be inserted once the effective length of the refined run is
  confirmed — see `docs/`.)*
- **Engineering iterations mattered.** Early trials suffered from (a) a hook that turned the
  system into a double pendulum and (b) forward/back swinging of the thread. Fixes — a wood
  piece at the knot, a foam-board guide, securing the ruler, and closing the pivot gap —
  produced markedly cleaner, more repeatable timing.

---

## Repository Structure

```
project/
├── index.html       # Interactive pendulum demo + g calculator (served by GitHub Pages)
├── data/            # Raw timing data (CSV/spreadsheet), period calculations
├── images/          # Photos of the apparatus, angle device, setup iterations
├── videos/          # Experiment clips (oscillation counting, before/after fixes)
├── src/             # Analysis scripts / spreadsheet for period + g + error propagation
├── docs/            # Pre-lab report, scanned data sheet, reference paper notes
├── report/          # LaTeX source (.tex) and compiled PDF report
└── README.md
```

---

## How To Reproduce

1. **Build the pendulum.** Tie a thin thread to a rigid pivot. Attach the steel ball. Insert a
   small wood piece at the knot to prevent the knot from acting as a second hinge.
2. **Measure inputs.** Ball diameter (calipers), ball mass and cord mass (scale), effective
   length *l* from pivot to ball center (ruler, 3× averaged).
3. **Stabilize the release.** Use a foam-board guide so the ball is released in a single
   vertical plane; verify the plane with an angle tool (aim for < 1° from vertical).
4. **Collect timing.** For each angle in {5°, 10°, 15°, 20°}, time 20 oscillations × 6 trials.
   Record everything in `data/`.
5. **Analyze.** For each angle compute `T = t/20`, the mean, the standard deviation, and
   `σ_T = SD/√N`. Correct the small-angle period with the three corrections above, then
   compute `g = 4π²l / T₀²`.
6. **Propagate error.** `(σ_g/g)² = (σ_l/l)² + (2σ_T/T)²`.
7. **Compare.** Report raw and corrected *g* and percent error vs. the accepted local value.

---

## References

1. R. A. Nelson and M. G. Olsson, "The pendulum — Rich physics from a simple system,"
   *Am. J. Phys.* **54**(2), 112–121 (1986).
2. Course lab/pre-lab handout: *Measurement of Gravitational Acceleration Using a Simple
   Pendulum* (Physics 1, 2026).

---

*This project was completed for an introductory university physics course. The full write-up
is in `report/` and the methodology follows the conceptual framework of Nelson & Olsson (1986).*
