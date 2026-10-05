# Appendix C: Standard Procedures

Reference procedures for qualifying and maintaining the three dielectric etch modules. Each lists its purpose, frequency, steps, and acceptance criteria. Values are illustrative and must be replaced by each fab's qualified limits.

---

## C.1 Plate-Chamber Qualification for the Periphery Clear (Module 2)

**Purpose:** confirm the main step, the ALE finish, and the TiN clear meet the reference before production. **Frequency:** after wet clean, after any hardware change, monthly.

```
Steps:
  1. Season: 20 wafer-equivalents of the full plate recipe on dummies
  2. Blanket t-ZrO₂ (5.5 nm on SiN, crystallized): main step 30 s;
     measure removal by SE at 49 sites
  3. Blanket t-ZrO₂: 20 ALE cycles; measure EPC (49 sites)
  4. Blanket PECVD SiN: 100 ALE cycles; measure SiN EPC
  5. Blanket TiN 20 nm: TiN-clear step 15 s; measure rate
  6. Patterned monitor (reference plate mask): full module 2; TXRF on
     large pads; SiN loss on pads; TEM sample at the plate edge (monthly)
  7. Bias-mode check: retarding-field analyser wafer or V_dc waveform log
     in the ALE removal step

Acceptance:
  Main-step rate          6.0 ± 0.12 nm/min; radial edge band within ± 1.5%
  ALE EPC (t-ZrO₂)        0.100 ± 0.003 nm; uniformity ± 1.2% (3σ)
  SiN EPC                 ≤ 0.020 nm/cycle
  TiN-clear rate          40 ± 3 nm/min
  IEDF (ALE step)         ≥ 98% of ions within 45–75 eV
  Particles               ≤ 10 adders ≥ 45 nm
  Backside Zr (VPD)       ≤ 5 × 10⁹ atoms/cm²
```

---

## C.2 ALE Window and Synergy Measurement

**Purpose:** establish the ALE window and synergy for a new chamber, bias generator, or dielectric. **Frequency:** at qualification and after bias-system changes.

```
Steps:
  1. On blanket t-ZrO₂, run 30 cycles at Ar⁺ energies of 30, 40, 50, 60,
     70, 80, 90, 100 eV (same times); measure EPC
  2. At 60 eV: run 30 cycles of BCl₃ dose only (α) and 30 cycles of Ar⁺
     only (β); measure removal
  3. Vary the dose time (0.25–2.0 s) and the removal time (0.5–4.0 s) at
     60 eV; fit τ_A and τ_B

Acceptance:
  Plateau EPC flat within ± 5% over ≥ 25 eV of energy
  Synergy S = (EPC − α − β)/EPC ≥ 90%
  τ_A ≤ 0.4 s, τ_B ≤ 0.9 s
```

---

## C.3 Cycle Ladder (Residue Tail Calibration)

**Purpose:** measure σ and R_slow of the residue distribution on product-like structures. **Frequency:** after major chamber changes; quarterly.

```
Steps:
  1. Five patterned wafers with periphery contact chains (monitor mask)
  2. Run module 2 with N = 20, 24, 26, 28, 30 cycles (all else reference)
  3. Complete ILD, contact etch, fill; test chains at the slowest band
     (r > 140 mm) and at the centre
  4. Convert open fractions to probabilities per grain site; plot probit(P)
     against N; fit slope (EPC/σ) and intercept (R_slow)
  5. Extrapolate to production N; compare with the model of Chapter 6

Acceptance:
  σ ≤ 0.38 nm; R_slow ≤ 1.40 nm
  Extrapolated P at production N ≤ 8 × 10⁻¹¹ at the slowest band
```

---

## C.4 Bevel Chamber Qualification (Module 1)

**Purpose:** confirm boundary placement, clearing, and cleanliness. **Frequency:** after PEZ part changes, monthly.

```
Steps:
  1. Centring check: edge-inspection of a bare wafer run with a marker film;
     measure eccentricity
  2. Blanket TE TiN / ZAZ wafers (partly crystalline, as at module 1): full
     bevel recipe
  3. Edge inspection: boundary radius (360 points), transition width, haze
  4. Bevel VPD-ICP-MS: front ring, apex, back ring; whole-backside VPD
  5. SEM-EDX on a cleaved edge at four azimuths (monthly)
  6. Log V_pp and impedance of the lower electrode as the baseline

Acceptance:
  Boundary radius         148.80 ± 0.08 mm (mean ± 3σ around the wafer)
  Eccentricity            ≤ 50 µm
  Transition (each film)  ≤ 300 µm
  Zr, bevel and back ring ≤ 5 × 10⁹ atoms/cm² (alert), ≤ 1 × 10¹⁰ (limit)
  No front TiN loss for r < 148.6 mm
```

---

## C.5 Waferless Auto-Clean Verification

**Purpose:** confirm the WAC removes Zr, Al, Ti, and B before fluorine steps. **Frequency:** weekly; after WAC recipe changes.

```
Steps:
  1. Run 25 product-equivalent wafers with WAC after each
  2. Monitor the Zr I 360.1 nm line in WAC step 1 (Cl₂/BCl₃); record the
     time to baseline
  3. Run a bare Si wafer through the W step (SF₆); TXRF for Zr and Al on
     the front
  4. First-wafer test: main-step rate of wafer 1 after a 2 h idle vs
     wafer 5

Acceptance:
  Zr line reaches baseline within 12 s of the 15 s step
  Zr on the bare wafer ≤ 1 × 10¹⁰ atoms/cm²; Al ≤ 5 × 10¹⁰
  First-wafer rate within 1% of steady state (with season)
```

---

## C.6 BCl₃ Cylinder Change and Moisture Control

```
Steps:
  1. Close the cylinder valve; purge the pigtail with N₂ (≥ 10 cycles of
     pressurize/vent)
  2. Change the cylinder; leak-check (He, ≤ 1 × 10⁻⁹ atm·cc/s)
  3. Purge with BCl₃ to the divert line for 10 min
  4. Run a moisture check: blanket ZrO₂ main-step rate and boron particles
     on a bare wafer after 5 min of BCl₃ flow

Acceptance:
  No B(OH)₃/B₂O₃ particles ≥ 45 nm above baseline
  Main-step rate within ± 2% of the pre-change value
```

---

## C.7 In-Situ Chlorine Clean of the ZAZ ALD Reactor

```
Steps:
  1. Run until 800 wafers or the flake alarm, whichever first
  2. Hold the reactor at deposition temperature; start BCl₃/Cl₂/Ar remote
     plasma, 1–2 Torr
  3. Monitor exhaust Zr species (FTIR or mass spectrometry) until the
     signal falls to 5% of its peak; continue 10% longer (≈ 110–130 min)
  4. Purge 30 min; O₃ treatment 10 min
  5. Season: deposit ≈ 30 nm ZrO₂ on the chamber parts (dummy wafer)
  6. First production-equivalent wafer: SIMS for B and Cl at the bottom
     interface; particles; thickness

Acceptance:
  B at the bottom interface ≤ 1 × 10¹³ atoms/cm²; Cl ≤ 0.5 at%
  Thickness 5.5 ± 0.08 nm; particles at baseline
```

---

## C.8 Thermal-ALE Trim Run Qualification (Module 3)

```
Steps:
  1. QCM baseline: 5 cycles on the reactor QCM; EPC from mass change
  2. Blanket t-ZrO₂ pad wafer: 17 cycles + O₃; SE thickness change at 49
     sites; XPS for F and C
  3. Patterned 1c monitor (weekly): HAADF-STEM at top, middle, bottom of
     channels at three wafer sites; TEM tomography of grooves (monthly)
  4. Supply check: DMAC pressure rise per dose; HF partial pressure at the
     start of the DMAC dose (must be < 1% of the HF dose value)

Acceptance:
  EPC (QCM)                0.060 ± 0.003 nm
  Trim (pad)               1.00 ± 0.05 nm
  Bottom-to-top ratio      ≥ 0.90
  Groove excess            ≤ 0.30 nm
  F after O₃               ≤ 1 at%; C ≤ 0.5 at%
```

---

## C.9 Plate-Edge TEM Sample

```
Steps:
  1. Select a long plate edge in the periphery of a monitor die at the
     slowest band and at the centre
  2. Protect with carbon and Pt; FIB lift-out perpendicular to the edge
  3. Thin to ≤ 30 nm at the edge
  4. HAADF-STEM: TE notch depth, ZAZ edge recess, ILD fill under the notch
  5. EELS maps: Cl, B, Zr, Ti across the edge (≈ 100 nm window)

Report: notch (nm), recess (nm), Cl and B profiles from the edge, voids
```

---

**Appendix C Version:** 1.0
