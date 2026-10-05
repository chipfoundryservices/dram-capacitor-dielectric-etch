# Chapter 8: Endpoint & In-Situ Monitoring for Nanometre Dielectrics

## Overview

Endpoint detection usually answers one question: has the film cleared? For the capacitor dielectric, that question is the wrong one, or at least not enough. The main step of module 2 is designed never to clear the film; the ALE finish is designed to keep going for many cycles after the film has visibly cleared, because the grains that matter are far below any optical detection limit; the bevel etch has no endpoint at all; and the thermal trim must stop within a single layer of a film it can never see. What the in-situ signals can do is **measure the process while it runs**: the rate of the main step on this wafer, the cycle at which the bulk of the periphery clears, the steadiness of the ALE, the condition of the chamber.

This chapter describes the optical emission from the species involved, the transition at the end of the TiN clear, the aluminium marker that measures each wafer's ZrO₂ rate, the cycle-resolved emission of the ALE finish, the optical measurement of thin films on test pads, monitoring of the bevel and thermal steps, and the ways each signal fails.

**Learning Objectives:**
- Identify emission lines for Ti, Zr, Al, B, Cl, N₂, and Ar used in the dielectric clear
- Use the TiN-clear transition and the Al marker to set the main-step time on each wafer
- Interpret the cycle-resolved Zr emission of the ALE finish as a clearing curve
- Explain why optical endpoint cannot see the residue tail, and what it is used for instead
- Estimate the sensitivity of reflectometry and ellipsometry to a few tenths of a nanometre of ZrO₂
- List the failure modes of each signal

---

## 8.1 Emission Lines

```
Lines used in the periphery clear (illustrative):

  Species     Line (nm)          Origin                          Use
  ──────────────────────────────────────────────────────────────────────────────
  Ti I        399.9, 453.3       TiClₓ from the TE TiN           TiN-clear endpoint
  Zr I        360.1, 468.8       ZrClₓ fragments                 ZAZ presence;
  Zr II       343.8              (weak; low product density)     ALE clearing curve
  Al I        396.2, 394.4       AlClₓ from the Al₂O₃ insertion  Al marker
  AlCl        261.4 (band)
  B I         249.7              BCl₃ fragments                  dose verification
  BCl         272 (band)
  Cl I        837.6              atomic chlorine                 actinometric
                                                                 ratio, wall state
  N₂ (2⁺)     337.1              SiN exposure (N₂ product)        landing indicator
  Si I        288.2              SiClₓ from SiN                   landing indicator
  Ar I        750.4              actinometer
```

The Zr lines are weak. The product flux is small (Section 8.3.1) and ZrClₓ fragments emit less efficiently than Ti. The Al lines are strong for their concentration, because Al has resonance lines with large cross-sections at 394–396 nm, which is what makes the 0.3 nm insertion layer visible.

---

## 8.2 The TiN-Clear Transition

During the TiN clear, Ti emission is high. As the TE TiN clears from the periphery, it falls; when it has cleared everywhere, it reaches the background from the plate sidewall:

```
Ti I 399.9 nm during the TiN clear (normalized to Ar 750.4):

  1.0 ┤▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓╲
      │                                            ╲
  0.5 ┤                                             ╲    clearing
      │                                              ╲   distribution
      │                                               ╲
  0.1 ┤                                                ╲________________
      ┼──────────┬──────────┬──────────┬──────────┬──────────┬────── t (s)
      0          2          4          6          8         10
                                          t_TiN = 7.4 s (50% point)
```

The 50% point of this transition, t_TiN, marks the moment the main step effectively begins on ZrO₂ across the wafer. The step continues for its fixed 2.5 s overetch and then switches to the main step, whose clock starts at the switch.

---

## 8.3 The Al Marker: Measuring Each Wafer's Rate

### 8.3.1 Why a Marker

The main step must remove 4.44 nm, not "run 45 s". A wafer whose ZrO₂ etches 3% slower, because of a chamber state, a crystalline fraction, or a thickness, would otherwise arrive at the finish with 0.13 nm more than the cycle count assumes. The Al₂O₃ insertion layer, 2.6 nm below the surface, is a marker inside the film: when the etch front passes it, Al emission rises and falls.

```
Signal magnitude (reference wafer):
  ZrO₂ removal on the periphery:
    318 cm² × 2.9 × 10¹⁵ Zr/cm²/nm × 0.1 nm/s ≈ 9 × 10¹⁶ Zr atoms/s
  Al removal while crossing the insertion:
    318 cm² × ≈ 1.1 × 10¹⁵ Al/cm² / 3.6 s ≈ 1 × 10¹⁷ Al atoms/s

Al I emission relative to the Al-free background:  × 5–10 at the peak
```

### 8.3.2 Timing

```
Al I 396.2 nm during the main step (reference, centre of the wafer):

      ▲
  1.0 ┤                       ╭──╮
      │                      ╱    ╲
  0.5 ┤                     ╱      ╲
      │                    ╱        ╲
  0.1 ┤___________________╱          ╲__________________
      ┼─────┬─────┬─────┬─────┬─────┬─────┬─────┬───── t (s)
      0     5    10    15    20    25    30    35    40
                                t_Al ≈ 27.8 s (peak)

Nominal:  t_Al = (2.6 nm / 6.0 nm/min) + ½ × (0.3 nm / 5.0 nm/min)
             = 26.0 + 1.8 = 27.8 s
```

The peak is broadened by the wafer's clearing-time distribution: different sites cross the insertion at different times. Its centroid measures the area-averaged rate of the top ZrO₂ layer on this wafer.

### 8.3.3 Adapting the Main Step

```
Rate of this wafer:   R_w = R_nom × (27.8 / t_Al)
Main-step time:       t_main = 45 s × (R_nom / R_w) = 45 × (t_Al / 27.8)

  t_Al = 27.0 s (fast wafer, +3%):   t_main = 43.7 s
  t_Al = 28.6 s (slow wafer, −3%):   t_main = 46.3 s
```

The adaptation assumes that the bottom ZrO₂ etches at the same rate as the top on the same wafer. That holds for rate changes from the chamber; it holds less well for changes in crystallinity, which can differ between the top and bottom layers. The adaptation is limited to ±5% of the nominal time; a marker outside that range stops the wafer for disposition (Section 8.8).

### 8.3.4 A Marker That Moves With the Stack

A laminate with two Al₂O₃ layers (ZAZAZ) gives two markers and a measured rate over a known thickness between them. A stack without Al (HZH, Chapter 14) has no marker. In that case the main step falls back to a time set by feed-forward of the ALD thickness and by the last few wafers' ALE clearing curves (Section 8.4).

---

## 8.4 The ALE Clearing Curve

### 8.4.1 Cycle-Resolved Emission

In each ALE cycle, the Ar⁺ removal step releases the modified layer from every area still covered by ZrO₂. The Zr emission during that step, integrated over the step, is proportional to the covered area times the EPC:

```
S_n = k × f_n × EPC     f_n = fraction of the periphery still covered
                            at cycle n
```

As the cycles proceed, f_n falls from 1 to 0 along the clearing distribution:

```
Integrated Zr I emission per cycle (reference wafer, normalized):

  1.0 ┤● ● ● ● ● ● ●
      │              ●
  0.8 ┤                ●
      │                  ●
  0.5 ┤                    ●                ← 50% cleared ≈ cycle 11
      │                      ●
  0.2 ┤                        ●
      │                          ● ●
  0.02┤─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─●─●─ ─ ─ ─ ─ ─ ─ ─ ─ ─ detection floor
      ┼─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬── cycle
      0     5    10    15    20    25    30    35    40
                              n₉₈ ≈ 18                  N = 36
```

The curve is the cumulative clearing distribution read cycle by cycle. Its midpoint gives the mean remaining thickness after the main step (≈ 1.06 nm ÷ 0.10 nm ≈ 11 cycles, less the first-cycle bonus). Its width gives the combined wafer-level and grain-level spread.

### 8.4.2 Why the Curve Cannot End the Step

```
Detection floor:  ≈ 1–2% of the initial per-cycle signal (shot noise,
                  wall emission, Zr from the chamber)
Fraction still covered when the signal reaches 2%:  2 × 10⁻²
Fraction that must be cleared:                       8 × 10⁻¹¹ per grain site

Cycle at which the signal reaches the floor (n₉₈):  ≈ 18
Cycle at which the residue target is met:           36
```

There are eight orders of magnitude between what the signal can see and what the contacts need. The clearing curve can tell the process when the bulk of the film has gone; it cannot tell it when the tail has. The cycle count is therefore set by the statistics of Chapter 6, and the curve is used to **check** that statistics on every wafer:

```
Uses of the ALE clearing curve (reference):
  n₅₀ (50% cleared)    checks the main-step removal; alarms at ± 2 cycles
  n₉₈ (98% cleared)    checks the spread; alarms if n₉₈ − n₅₀ > 9 cycles
  Signal at cycle 1    checks the EPC (S₁ ∝ EPC); alarms at ± 10%
  N₂ 337 nm per cycle  rises as SiN is exposed; its plateau measures the
                       SiN EPC × exposed area
```

A wafer whose n₉₈ is late by three cycles has a wider or shifted distribution than the cycle count was designed for, and the automatic response is to add cycles (Chapter 15).

---

## 8.5 Thin-Film Optics on Test Pads

### 8.5.1 Reflectometry

A 5.5 nm film on SiN changes the reflectance only slightly:

```
Normal-incidence reflectance change from 1 nm of ZrO₂ (n ≈ 2.15) on
120 nm SiN over oxide, at 400 nm (illustrative):   ΔR ≈ 0.4% absolute

Reflectometer noise (single wafer, 100 ms):        ≈ 0.05%
Detectable thickness change:                       ≈ 0.15 nm
```

Reflectometry on a large periphery area can follow the main step in real time, but it confounds ZAZ thickness with SiN thickness: both have similar refractive indices in the visible. It is useful as a rate monitor, not as a clearing detector.

### 8.5.2 In-Situ Ellipsometry

Spectroscopic ellipsometry is far more sensitive to a thin film's thickness than reflectometry, and separates films with different dispersion:

```
In-situ SE on a 2 × 2 mm test pad in the scribe line (illustrative):
  Sensitivity to ZrO₂ thickness       ≈ 0.02 nm
  Time resolution                      ≈ 1 s
  Use: EPC per cycle on the pad; main-step rate; first-cycle effect
```

In-situ ellipsometry requires two windows at about 70° incidence and a pad large enough for the spot, both difficult on a production ICP. It is common on development chambers and used on production chambers that run ALE heavily. On the reference chamber, it is available as an option and used for EPC qualification.

---

## 8.6 Monitoring the Bevel Step

The bevel plasma has no endpoint. The area of film is small, the plasma is at high pressure, and the signals from the bevel are mixed with emission from deposits on the PEZ parts:

```
Bevel monitoring (reference):
  RF impedance and V_pp of the lower electrode   ion-energy proxy; drift as
                                                  PEZ rings wear (Chapter 7)
  OES of the annular plasma, Ti and Zr lines     fault detection: missing
                                                  Ti peak in B1 → no TiN or
                                                  no plasma at the edge
  Gap sensors (capacitive) for the PEZ plate      boundary placement
  Post-process: edge inspection, bevel VPD        the real measurements
  (Chapter 15)
```

The most useful single signal is the lower-electrode peak-to-peak voltage. Because the bevel etch rate depends so strongly on ion energy (Chapter 7, Section 7.3.3), a drift of a few percent in V_pp predicts a rise in backside clearing time long before a VPD monitor fails.

---

## 8.7 Monitoring the Thermal Trim

```
Thermal ALE reactor monitoring (module 3):
  QCM (quartz crystal microbalance) coated     mass change per half-step:
  with ZrO₂, in the reactor                    verifies fluorination and
                                               exchange saturate
  Pressure transients per pulse                dose delivery
  FTIR or mass spectrometry of the exhaust     ZrClₓ(CH₃)ᵧ products;
                                               DMAC decomposition
  Pre- and post-trim SE on blanket pads        thickness removed (pad, not
                                               array)
  Electrical: capacitance and leakage on       the real result, weeks later
  arrays (Chapter 15)
```

None of these sees the trim inside the array. The QCM and the blanket pads measure the trim on a flat surface; the array's channels receive less reactant at depth. Chapter 12 shows how the exposure is chosen so that the flat-surface measurement predicts the array.

---

## 8.8 Failure Modes

```
Signal             Failure                               Effect / response
───────────────────────────────────────────────────────────────────────────────
Ti transition      TE TiN partly oxidized (SiGe          late t_TiN; main step
                   interface), slow clear                starts late → OK, timed
                                                         from the switch
Al marker          Al from eroded Al₂O₃ parts            raised background;
                   (gas injector, chuck edge)            centroid biased early →
                                                         main step too short →
                                                         more residue for ALE
                   Window clouded by BₓClᵧ               weak peak; centroid
                                                         noisy → limit adaptation
                   Marker outside ± 5% window            wafer held; check
                                                         ALD thickness, chamber
ALE curve          Zr from chamber walls during          raised floor; n₉₈
                   Ar⁺ steps (Chapter 9)                 apparently late
                   EPC drop (purge too short,            n₅₀ late; S₁ low;
                   residual BCl₃)                        add cycles, fix purge
                   N₂ plateau high                       SiN EPC high: IEDF tail
                                                         (bias mode), Chapter 5
Bevel V_pp         Ring wear                             backside residual Zr
                                                         (Chapter 7)
```

The Al background problem is the most insidious, because it biases the measurement in the dangerous direction: an early apparent marker shortens the main step, which leaves more film than the cycle count expects, and the wafer arrives at the contacts with a wider tail. Chambers that run the periphery clear should have no Al-containing surface in view of the plasma.

---

## Summary and Key Takeaways

1. **Endpoint here means measurement, not stopping.** The main step is timed, the finish is counted, the bevel is fixed, the trim is invisible; signals measure the process on each wafer.

2. **The TiN-clear transition starts the clock.** Ti emission falls as the TE TiN clears; the main step is timed from the switch.

3. **The Al marker measures each wafer's rate.** Its centroid at ≈ 27.8 s adapts the main step within ±5% so that 4.44 nm, not 45 s, is removed.

4. **The ALE curve is a clearing distribution, cycle by cycle.** n₅₀ ≈ 11, n₉₈ ≈ 18; the residue target needs 36. Eight orders of magnitude lie between the signal floor and the contact specification.

5. **Ellipsometry sees 0.02 nm on a pad.** Reflectometry is a rate monitor; neither sees the tail.

6. **Aluminium in the chamber biases the marker the wrong way.** Y₂O₃ surfaces, not alumina, should face the plasma.

---

## Study Questions

1. The Al peak centroid on a wafer is at 26.6 s. Compute the wafer's top-layer rate and the adapted main-step time. How much more film would the wafer have carried into the finish without adaptation?

2. Estimate the Zr atoms released per ALE cycle from the periphery of a reference wafer at the start of the finish. Compare with the Zr atoms released per second in the main step. Why is the per-cycle Zr signal still usable?

3. On a wafer, n₅₀ = 13 and n₉₈ = 22. Estimate the mean remaining thickness after the main step and the combined spread. How many cycles would you run?

4. Explain why the ALE clearing curve cannot detect a grain-residue probability of 10⁻⁸, and give a measurement that can, with its delay.

5. A reflectometer measures a change of 0.6% in reflectance during the main step where 0.4% per nm of ZrO₂ is expected. List two explanations other than a faster ZrO₂ rate.

6. Design a monitoring plan for a ZAZAZ stack with Al₂O₃ insertions at 1.8 and 3.7 nm from the top. How would you use two markers to measure both the rate and the thickness of the middle ZrO₂?

---

**Next Chapter:** [Chapter 9: Walls, Boron, Metal Contamination & ALD-Reactor Cleaning](./09-walls-contamination-ald-reactor-cleaning.md)

---

**Chapter 8 Development Status:** Complete  
**Version:** 1.0
