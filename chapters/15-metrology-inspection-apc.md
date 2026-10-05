# Chapter 15: Metrology, Inspection & Advanced Process Control

## Overview

The dielectric clear has the awkward property that its most important output cannot be measured when the wafer leaves the chamber. The average zirconium left on the periphery can be measured, to a part in ten thousand of a monolayer. The SiN loss, the cap loss, the boron and chlorine on the surface can all be measured. But the number that sets yield, the probability that one clearing domain in 10¹⁰ survives under a contact, is eight orders of magnitude below what any surface analysis can see, and it shows up only as contact opens months later.

Metrology for this module is therefore a ladder. At the bottom are fast, sensitive, averaging methods that catch gross failures within minutes. Above them are imaging methods that find individual islands on small areas. Above those are electrical structures that count opens in millions of contacts, and at the top is product yield, which counts them in billions. Process control uses the fast rungs to steer the process and the slow rungs to verify that the steering works. This chapter describes each rung, what it can and cannot see, and how feed-forward and feedback control and fault detection are built on them.

**Learning Objectives:**
- Compare TXRF, VPD-ICPMS, XPS, LEIS, and ToF-SIMS for residual zirconium, and explain the VPD blind spot for crystalline ZrO₂
- Show quantitatively why average surface measurements cannot see the residue tail
- Size e-beam inspection and electrical contact-chain sampling for a given residue rate
- Choose metrology for the incoming film, the plate edge, and the cleared surface
- Build feed-forward, feedback, and fault-detection loops for D1 and D2
- Write a sampling plan for the dielectric clear

---

## 15.1 What Must Be Measured

```
Metrology map for the dielectric clear (reference):

Stage        Quantity                         Method                    Section
─────────────────────────────────────────────────────────────────────────────────
Incoming     periphery ZAZ thickness, radial   ellipsometry on pads      15.4
             monoclinic fraction               GIXRD (monitor)           15.4
             surface Ti, C, F                  XPS (monitor)             15.4
In situ      t_EP, Al-marker time and width    OES (every wafer)         Ch. 8
             V_pp, wafer T offset, He flow     FDC (every wafer)         15.6
After clear  Zr average                        TXRF                      15.2
             residual islands                  e-beam inspection         15.3
             SiN loss, cap loss                ellipsometry, OCD         15.4
             B, Cl on SiN                      XPS, TXRF (Cl)            15.4
             TE recess, undercut               TEM, OCD on edge gratings 15.4
             backside Zr                       TXRF, VPD-ICPMS           15.2
Electrical   contact opens                     contact chains            15.3
             edge leakage, damage reach        comb, overlap ladder      Ch. 11, 13
             array leakage                     capacitor arrays          Ch. 13
```

---

## 15.2 Measuring a Hundredth of a Monolayer

### 15.2.1 The Methods

```
Methods for residual Zr on the periphery (illustrative):

Method          Detection limit        Depth            Area         Notes
──────────────────────────────────────────────────────────────────────────────────────
TXRF            ≈ 10¹⁰ Zr/cm²          top few nm       ≈ 1 cm²      fast, non-destructive;
                                                        spot         Zr Kα 15.7 keV
VPD-ICPMS       ≈ 10⁸ Zr/cm²           whatever the     whole wafer  blind to crystalline
                                       droplet dissolves             ZrO₂ (15.2.2)
XPS             ≈ 0.1 at% ≈ 10¹³ /cm²  ≈ 5 nm           ≈ 50 µm      chemical state
                                                                     (Zr 3d 182 eV)
LEIS            ≈ 10¹² /cm²            top monolayer    ≈ 1 mm       outermost layer only
ToF-SIMS        ≈ 10¹⁰–10¹¹ /cm²       ≈ 1 nm, mapping  ≈ 100 µm     maps islands ≳ 1 µm
                                                                     clusters
```

TXRF is the production method for the average specification (≤ 1 × 10¹³ /cm²): it has three orders of magnitude of margin, takes minutes, and does not destroy the wafer. XPS sits near its limit at the specification and is used on monitor pads to identify chemical states, Zr–O versus Zr–Cl versus Zr–F.

### 15.2.2 The VPD Blind Spot

Vapor-phase decomposition (VPD) exposes the wafer to HF vapor, which dissolves the native oxide and surface contaminants into a thin water film; a droplet scanned across the wafer collects them for ICP-MS. It is the most sensitive method for metals on silicon. But HF vapor at room temperature does not dissolve crystalline ZrO₂ (Chapter 4). Residual grains stay on the wafer, and the droplet collects only the zirconium that was adsorbed or amorphous:

```
VPD-ICPMS versus TXRF on the same cleared wafers (illustrative):
  Wafer condition             TXRF Zr (/cm²)      VPD-ICPMS Zr (/cm²)
  ──────────────────────────────────────────────────────────────────────
  Good clear                  3 × 10¹¹            2 × 10¹¹
  Under-etched (5 s short)    8 × 10¹³            6 × 10¹¹   ← blind
```

For residual crystalline ZrO₂, VPD must be replaced by a collection chemistry that dissolves it (hot HF/H₂SO₄ or HF/H₂O₂/HNO₃ droplets, with longer contact), or TXRF must be used. For backside contamination, where the zirconium is mostly adsorbed and amorphous, VPD remains the right method.

### 15.2.3 Why Averages Cannot See the Tail

```
Zr content of the tail at the specification (illustrative):
  Allowed fatal islands        ≈ 20 per cm² of periphery (Chapter 10)
  Zr per island                25 nm diameter × 1 nm × 3 × 10²² cm⁻³
                               ≈ 1.5 × 10⁴ atoms
  Zr from the tail             ≈ 3 × 10⁵ atoms/cm²
  TXRF detection limit         ≈ 10¹⁰ atoms/cm²
  Ratio                        ≈ 3 × 10⁴ below detection
```

A wafer can carry ten thousand times the allowed island density and still read clean on TXRF, if the islands are the only residue. Average methods catch under-etched wafers, failed chambers, and wrong recipes. They cannot qualify the tail.

---

## 15.3 Finding Single Islands

### 15.3.1 E-Beam Inspection

ZrO₂ islands on SiN are visible in backscattered-electron imaging by atomic-number contrast (Zr, Z = 40, against Si, Z = 14), and in secondary-electron imaging at low landing energy by charging contrast.

```
E-beam inspection for residual islands (illustrative):
  Pixel                      ≈ 5 nm
  Detectable island          ≥ 15 nm across, ≥ 0.5 nm thick
  Area rate                  ≈ 20 mm²/h including stage overhead
  Monitor plan               20 sites × 1 mm² = 20 mm² per wafer ≈ 1 h
  Expected count at spec     20 /cm² × 0.2 cm² = 4 islands per wafer
```

### 15.3.2 What a Sample Can Prove

```
Poisson statistics of island counting (illustrative):
  Inspected area A, true density ρ, expected count λ = ρA
  Zero found in A = 20 mm²: 95% upper bound λ ≤ 3 → ρ ≤ 15 /cm²
  At spec (ρ = 20 /cm², λ = 4): P(count ≥ 10) ≈ 0.8%
  At 3× spec (ρ = 60 /cm², λ = 12): P(count ≥ 10) ≈ 76%
```

One wafer per lot at 20 mm² detects a threefold excursion with good probability and a tenfold excursion almost certainly. It cannot distinguish 10 from 20 islands per cm² on one wafer. Trends over many lots can. E-beam inspection is the earliest rung that sees the tail, and it is a monitor for excursions, not a measurement of the specification.

### 15.3.3 Contact Chains

The contact etch is the customer, and a contact chain measures the customer directly:

```
Periphery contact chains (illustrative):
  Chain             10⁶ contacts in series, landing on the cleared SiN
                    region through the full contact stack
  Per wafer         50 chains in the scribe → 5 × 10⁷ contacts tested
  Measurement       after the first metal: open or high-resistance chains
  Sensitivity       one open in 5 × 10⁷ → 2 × 10⁻⁸ per contact per wafer
  Specification     0.01 opens per die / 3 × 10⁷ contacts ≈ 3 × 10⁻¹⁰
```

Contact chains reach two orders of magnitude closer to the specification than inspection does, and they integrate all causes of contact opens, not only the dielectric clear. Their signals are separated by failure analysis of the open chains: an open on a zirconium-containing island points to the clear; an open on an under-etched oxide points to the contact etch.

### 15.3.4 The Ladder

```
The residue measurement ladder (illustrative):
  Rung                     Sensitivity per contact     Available
  ───────────────────────────────────────────────────────────────────
  TXRF average             gross failures only          minutes after etch
  E-beam inspection        ≈ 10⁻⁶ (excursions)          hours after etch
  Contact-chain VC         ≈ 10⁻⁷                       after contact etch
  (e-beam, inline)                                      (≈ 1–2 weeks)
  Contact chains           ≈ 10⁻⁸ per wafer             after metal 1
  (electrical)                                          (≈ 3–4 weeks)
  Product yield, bitmaps   ≈ 10⁻¹⁰ (die level)          end of line
                                                        (≈ 2–3 months)
```

---

## 15.4 Incoming, Surface, and Edge Metrology

### 15.4.1 Incoming Film

```
Incoming metrology (illustrative):
  ZAZ thickness on periphery    spectroscopic ellipsometry on 50 µm pads;
                                precision ≈ 0.03 nm; 13–49 sites per wafer;
                                every lot (feeds zone temperatures, Ch. 6)
  Monoclinic fraction           GIXRD on a blanket monitor run with each
                                plate deposition batch; ± 5%
  Surface Ti, C, F after        XPS on a monitor pad, daily
  conductor etch and strip
```

### 15.4.2 After the Clear

```
Post-clear metrology (illustrative):
  SiN remaining                 ellipsometry on pads (± 0.1 nm)
  Cap remaining                 ellipsometry on plate-covered pads
  Cap corner                    TEM when the conductor recipe changes
  B, Cl on SiN                  XPS on monitor pad after PET + rinse;
                                Cl also by TXRF
  SiN roughness                 AFM on a pad, weekly: correlates with σ_g
                                (Chapter 12)
```

### 15.4.3 The Plate Edge

Recess and undercut of a few nanometres along a 147 mm perimeter are not measurable inline on product. They are measured on structures designed to make edges dense:

```
Edge metrology (illustrative):
  Edge grating           plate lines 200 nm wide on 400 nm pitch over
                         100 × 100 µm: ≈ 5 × 10⁴ µm of edge in the spot
  OCD on edge grating    TE recess and SiGe recess to ≈ ± 0.5 nm by model
                         fitting (correlated parameters; anchored by TEM)
  TEM / EELS             recess, undercut, Cl and O profiles at the edge;
                         monthly and at changes
  ToF-SIMS on grating    Cl, B, F inventory per unit edge length
```

---

## 15.5 Process Control

### 15.5.1 Feed-Forward

```
Feed-forward loops (D1, illustrative):
  Input                           Actuator                Model
  ───────────────────────────────────────────────────────────────────────
  ZAZ radial thickness profile    zone temperatures       0.7%/°C (Ch. 6)
  (per lot)
  Monoclinic fraction (per        OE fraction             + 1% OE per + 3%
  plate-deposition batch)                                 monoclinic
  Al-marker time (per wafer)      t_EP prediction window  Chapter 8
  Al-marker width (per wafer)     OE fraction             OE = 70% × (W/W₀)
                                                          when W > 1.2 W₀
```

The last loop is the one that defends the tail. The Al-marker width is the only per-wafer measurement of the local clearing spread available before the overetch begins; using it to lengthen the overetch on wafers with a wider spread converts a warning into a correction.

### 15.5.2 Feedback

```
EWMA feedback on the D1 rate (illustrative):
  Output       t_EP (target 36.0 s)
  Actuator     bias voltage setpoint (rate ∝ (√E − √E_th); 1.8%/eV)
  Filter       ŷ_k = λ y_k + (1 − λ) ŷ_{k−1}, λ = 0.3
  Update       total ΔE = + (ŷ_k / 36.0 − 1) / 0.018 eV (a longer t_EP means
               a slower rate, corrected by raising the ion energy),
               limited to ± 2 eV of change per lot

Example (lot means of t_EP, chamber drifting slow):
  Lot   t_EP (s)   ŷ (s)    Total ΔE (eV)
  ─────────────────────────────────────────
  1     36.0       36.00     0
  2     36.9       36.27     + 0.4
  3     37.4       36.61     + 0.9
```

The overetch, being 70% of each wafer's own t_EP, needs no correction for rate drift: it already scales. What the loop protects is the operating point, the ion energy window of the plate edge and the selectivity, which drift if the rate is allowed to wander far from its design point. A correction above + 3 eV in total is an alarm, not a control action: the cause (wall state, ring wear, He leak) must be found.

### 15.5.3 ALE Control

```
D2 control (illustrative):
  Cycle count   N = 1.3 × ((t_in − 0.3) / EPC + 3.75), rounded up; t_in from
                ellipsometry per lot; EPC from the daily monitor (EWMA,
                λ = 0.2)
  Example       t_in = 5.45 nm, EPC = 0.098 nm → N = 1.3 × (52.6 + 3.75)
                ≈ 73.3 → 74 cycles
  Guard         per-cycle Si-signal endpoint within ± 5 cycles of the
                prediction (Chapter 8)
```

---

## 15.6 Fault Detection and Virtual Metrology

```
Per-wafer FDC features for D1 (illustrative):
  Feature                         Normal            Fault indicated
  ─────────────────────────────────────────────────────────────────────────
  t_EP                            36 ± 1.5 s        rate drift; thick film
  Al-marker width                 4.0 ± 0.4 s       wider spread → tail risk
  Si rise slope (10–90%)          9 ± 1.5 s         wider spread
  BO drop at clearing             75 ± 5%           pattern or wall change
  Bias V_pp                       ± 1%              ion-energy drift
  Wafer–chuck T offset            14 ± 2 °C         He leak, chuck change
  Backside He flow                ± 10%             clamping, leaks
  Reflected power in BT           < 2%              match, plasma instability
```

A virtual-metrology model combines these features into a residue-risk score per wafer. Wafers above a threshold are routed to e-beam inspection in place of the routine sample. This adaptive sampling concentrates the scarce inspection hours on the wafers most likely to carry the tail, and raises the effective sensitivity of the inspection rung by about an order of magnitude.

---

## 15.7 Sampling Plan

```
Sampling plan (reference, illustrative):
  Measurement                        Frequency                    Limit / action
  ────────────────────────────────────────────────────────────────────────────────
  ZAZ thickness (incoming)           every lot, 1 wafer, 49 sites  FF to zones
  Monoclinic fraction                each plate-dep batch monitor  FF to OE
  OES features, FDC                  every wafer                  hold on alarm
  TXRF Zr (front)                    1 wafer per lot, 5 sites     ≤ 1 × 10¹³
  E-beam islands                     1 wafer per lot + VM-flagged  ≥ 10 in 20 mm²
                                     wafers, 20 mm²               → hold
  SiN and cap remaining              1 wafer per lot              SiN loss ≤ 5 nm
  B, Cl (XPS, monitor)               daily                        B ≤ 2 × 10¹⁴;
                                                                  Cl ≤ 1 at%
  Edge grating OCD                   1 wafer per day              TE recess ≤ 3 nm
  Backside Zr (TXRF)                 1 wafer per lot leaving the  ≤ 1 × 10¹⁰
                                     high-k tool set
  Contact chains, comb, ladder       every wafer at metal 1 test  trend; FA on opens
  Particles (monitor)                weekly per chamber           ≤ 10 ≥ 30 nm
```

---

## Summary and Key Takeaways

1. **Measurement is a ladder.** TXRF in minutes, e-beam in hours, contact chains in weeks, product yield in months; each rung is about two orders of magnitude more sensitive than the one below.

2. **Averages cannot see the tail.** The allowed island density carries 10⁴ times less zirconium than TXRF can detect.

3. **VPD misses crystalline ZrO₂.** Use TXRF or an aggressive collection chemistry for residue; keep VPD for backsides.

4. **Edges are measured on dense edge gratings** by OCD anchored to TEM; product edges are not measurable inline.

5. **The Al-marker width is the per-wafer tail defence.** It measures the local spread before the overetch starts and can lengthen it.

6. **Feedback holds the operating point, not the overetch.** The overetch already scales with each wafer's t_EP; feedback protects the ion energy and selectivity.

---

## Study Questions

1. TXRF on a cleared wafer reads 4 × 10¹² Zr/cm². List three distributions of that zirconium consistent with the reading, and say which would fail contacts.

2. How much area must e-beam inspection cover, with zero islands found, to show at 95% confidence that the density is below 5 per cm²? How long does that take at 20 mm²/h?

3. A product's contact-open rate from all causes is 2 × 10⁻⁹ per contact. How many contact chains of 10⁶ contacts are needed per month to estimate the dielectric clear's share (about a third of the total) to ± 30%?

4. Redo the EWMA example of Section 15.5.2 for λ = 0.5 and a step change of t_EP to 37.4 s at lot 2 that persists. How many lots until the correction reaches 90% of its final value?

5. The Al-marker width rises 25% on one chamber over a week while t_EP is unchanged. List the causes you would check, in order, and the measurement that separates each.

6. Write the virtual-metrology feature list for D2 and explain which D1 features have no meaning for an ALE process.

---

**Next Chapter:** [Chapter 16: Integration, Yield & Cost of Ownership](./16-integration-yield-coo.md)

---

**Chapter 15 Development Status:** Complete  
**Version:** 1.0
