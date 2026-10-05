# Chapter 15: Metrology, Inspection & Advanced Process Control

## Overview

The three dielectric etches are judged by quantities that are hard to measure. The periphery clear is judged by the probability that one grain-sized site in ten billion keeps a grain; no instrument samples ten billion sites on one wafer except the product itself. The bevel removal is judged by a few billion zirconium atoms per square centimetre on a curved surface a millimetre wide. The trim is judged by a nanometre removed at the bottom of channels 1.5 µm deep and 7 nm wide, and by grooves a quarter of a nanometre deep along grain boundaries. Each of these is measured somewhere, by something, with a delay.

This chapter maps what must be measured for each module and how; explains why surface analysis of the periphery cannot certify the tail and what can; describes the thickness, profile, bevel, and electrical measurements; and builds the control system around them: feed-forward of dielectric thickness, within-wafer adaptation from the Al marker, feedback on the ALE clearing curve, ring-hour compensation of the cycle count, run-to-run control of the trim, and fault detection on cyclic signals.

**Learning Objectives:**
- Build a measurement map for the three dielectric modules, with sensitivity, sampling, and delay
- Explain why TXRF and XPS measure the average residue and not the tail, and how contact chains, voltage contrast, and cycle ladders measure the tail
- Describe bevel metrology: boundary radius, haze, and bevel VPD
- Design feed-forward and feedback loops for the main-step time and the ALE cycle count
- Run an EWMA controller on the ALE clearing curve for three lots
- Set up fault detection on the per-cycle signals of the ALE finish and the thermal trim

---

## 15.1 The Measurement Map

```
Module 1 (bevel)
──────────────────────────────────────────────────────────────────────────────────
Quantity                    Method                       Sensitivity      Sampling / delay
──────────────────────────────────────────────────────────────────────────────────
Boundary radius, width      optical edge inspection      ± 20 µm          every wafer / min
Haze ring, flakes           optical edge inspection;     ≥ 1 µm defects   every wafer / min
                            SEM review
Zr on bevel and backside    VPD-ICP-MS (bevel scan;      ≈ 10⁸ /cm²       1 wafer per lot /
                            whole backside)                               hours
Film profile at boundary    SEM-EDX cross-section        ≈ 1 nm, ≈ 5 µm   monthly / days
Bevel plasma state          V_pp, impedance, OES         —                every wafer / s

Module 2 (periphery clear)
──────────────────────────────────────────────────────────────────────────────────
ZAZ thickness (incoming)    ellipsometry / XRR on        ± 0.02 nm        every wafer, 9
                            scribe pads                                   sites / min
Main-step removal           Al marker (in situ);         ± 1%             every wafer / s
                            post-etch pad ellipsometry
ALE clearing curve          per-cycle OES (n₅₀, n₉₈)     ± 0.5 cycle      every wafer / s
SiN loss                    ellipsometry on SiN pads;    ± 0.1 nm         sample / min
                            N₂ plateau (virtual)
Average Zr residue          TXRF on monitor wafers or    ≈ 10¹⁰ /cm²      daily monitor /
                            large pads                                    hours
B, Cl on SiN                TOF-SIMS, XPS                ≈ 10¹³ B/cm²;    weekly / days
                                                         0.3 at% Cl
Plate-edge notch, ZAZ edge  TEM / STEM-EELS              ≈ 0.3 nm         weekly / days
Residue tail                contact chains; voltage      see §15.2        per lot / weeks
                            contrast; product test

Module 3 (trim, pilot)
──────────────────────────────────────────────────────────────────────────────────
EPC (flat)                  QCM in reactor; SE on        ± 0.005 nm       every run / s–min
                            blanket pads
Trim at channel bottom      TEM (HAADF-STEM)             ± 0.1 nm         per lot sample /
                                                                          days
Grain-boundary grooves      TEM tomography; AFM on       ± 0.05 nm        weekly / days
                            blanket
F, C in the surface         SIMS, XPS on pads            ≈ 0.1 at%        weekly / days
EOT, leakage                C–V, I–V on capacitor        ± 0.005 nm EOT   per lot / weeks
                            arrays
```

---

## 15.2 Measuring Absence

### 15.2.1 Surface Analysis Measures the Average

```
Detection limits for Zr on SiN (illustrative):
  TXRF (spot ≈ 10 mm)               ≈ 1 × 10¹⁰ atoms/cm²
  VPD-ICP-MS (whole surface)         ≈ 1 × 10⁸ atoms/cm²
  XPS (spot ≈ 0.1–1 mm)              ≈ 0.3–0.5 at% ≈ 5 × 10¹² atoms/cm²
```

TXRF can see 10¹⁰ Zr/cm², about a hundred-thousandth of a monolayer. A single residual grain 20 nm across and 1 nm thick contains about 10⁴ Zr atoms. With 20 nm grains, a square centimetre of periphery holds about 2.5 × 10¹¹ grain sites; at a residue probability of 10⁻¹⁰ that is 25 grains, or 2.5 × 10⁵ atoms/cm² on average: forty thousand times below the TXRF detection limit. Even a grain probability ten thousand times worse than the target is invisible to TXRF. The average residue on the periphery after the reference finish, about 5 × 10¹² atoms/cm², is dominated by re-adsorbed scattered atoms (Chapter 10), not by grains. **Surface analysis certifies that the average is low; it cannot certify the tail.**

### 15.2.2 Contact Chains

A Kelvin contact chain in the scribe line puts many contacts in series; a single open breaks the chain:

```
Contact chains per wafer (reference monitor set):
  Chains per die-site sampled     4
  Contacts per chain              1 × 10⁵
  Sampled die-sites per wafer     20
  Contacts tested per wafer       8 × 10⁶ (≈ 3 × 10⁷ grain sites)

At the reference residue probability (P ≈ 3 × 10⁻¹¹ at the edge,
far lower elsewhere): expected residue opens per wafer of chains ≈ 10⁻³
```

Chains detect a residue problem only when it is about a thousand times worse than the target. They are an excursion detector, not a measurement of the tail.

### 15.2.3 The Product Is the Only Sensor Large Enough

```
Grain-sized sites under contacts on one wafer:
  950 dies × 1.2 × 10⁸ ≈ 1.1 × 10¹¹

Expected residue opens per wafer at the reference: ≈ 0.35 (Chapter 10)
```

Only the product's own contacts, tested at wafer sort as die failures and localized by bitmap and failure analysis, sample enough sites to see the tail at its design level. Their delay is weeks. The feedback that matters most is therefore the slowest.

### 15.2.4 Cycle Ladders: Measuring the Tail on Purpose

The tail can be measured faster by making it bigger on purpose. A **cycle ladder** runs monitor wafers with deliberately reduced cycle counts and measures the contact-chain open rate at each:

```
Cycle ladder (illustrative, chains at the slowest band):

  N cycles   z (model)   P (model)       Chain opens observed per 10⁷ contacts
  ─────────────────────────────────────────────────────────────────────────────
  20          2.0        2 × 10⁻²         saturated (most chains open)
  24          3.1        1 × 10⁻³         ≈ 4 × 10⁴
  26          3.7        1 × 10⁻⁴         ≈ 4 × 10³
  28          4.3        9 × 10⁻⁶         ≈ 350
  30          4.8        6 × 10⁻⁷         ≈ 25
```

Plotting the measured open rate on a probability scale against N gives a straight line whose slope is 1/(σ/EPC) and whose intercept locates R_slow. The ladder measures σ and R_slow directly, and the model extrapolates them to the 36-cycle production point. Running a ladder after every major chamber change, and quarterly otherwise, keeps the residue model honest.

### 15.2.5 Voltage Contrast

E-beam voltage-contrast inspection after the periphery contact etch and fill sees open contacts as dark spots. It samples about 10⁸–10⁹ contacts per wafer in a few hours, enough to see a residue problem a hundred times above the target, and its results arrive days rather than weeks after module 2.

---

## 15.3 Thickness, Profile, and the Bevel

### 15.3.1 Thickness on Pads

The ZAZ thickness and the main-step removal are measured on scribe-line pads of periphery-type SiN (50 × 50 µm), by spectroscopic ellipsometry with a model of ZrO₂, Al₂O₃, and SiN. XRR on larger pads gives density and roughness and calibrates the ellipsometry model.

### 15.3.2 TEM

```
TEM work per qualification (illustrative):
  Plate edge: TE notch, ZAZ edge recess, ILD fill        STEM, EELS (Cl, B)
  Periphery: residue islands after a short ladder        plan-view HAADF
  Trim: thickness at top, middle, bottom of channels     cross-section HAADF;
        grain-boundary grooves                           tomography
```

### 15.3.3 Bevel

```
Bevel metrology:
  Optical edge inspection (top, apex, back cameras)   boundary radius to ± 20 µm;
                                                      eccentricity; haze ring;
                                                      flakes
  Bevel VPD-ICP-MS (droplet scanned around the         Zr, Ti, B on the front ring,
  bevel and back ring)                                 apex, back ring
  Whole-backside VPD                                   Zr carried into later tools
  SEM-EDX of a cleaved edge                            staircase profile (Ch. 11)
```

---

## 15.4 Electrical Monitors

```
Structure                         Measures                          Module(s)
──────────────────────────────────────────────────────────────────────────────
Capacitor arrays (centre)         EOT (C–V), leakage at ± 1 V,       3 (and the ALD)
                                  85 °C; TDDB
Edge-intensive arrays             edge leakage ratio                 2
Antenna arrays                    charging damage per island         2 (and 1)
Periphery contact chains          opens, resistance distribution     2
(Kelvin)
Bevel-proximity arrays            edge-die leakage                   1
Product retention test            retention-time distribution         all
```

---

## 15.5 Control of the Periphery Clear

### 15.5.1 Feed-Forward of Dielectric Thickness

```
Incoming ZAZ (wafer mean from pads):  t_w
Main-step removal target:             x_w = 4.44 + (t_w − 5.50) × 0.8
  (most of a thickness change is absorbed by the main step; the finish
   keeps its margin)
ALE cycles (Chapter 6):               N_w = ⌈ (R_slow,w + 6.4 σ(x_w) − b) / EPC ⌉
                                      R_slow,w = 1.05 t_w − x_w

  t_w = 5.50 nm:  x_w = 4.44;  R_slow = 1.34;  σ = 0.356;  N_w = 36
  t_w = 5.60 nm:  x_w = 4.52;  R_slow = 1.36;  σ = 0.362;  N_w = 37
  t_w = 5.40 nm:  x_w = 4.36;  N_w = 35 → held at 36 (Section 15.5.5)
```

### 15.5.2 Within-Wafer Adaptation

The Al marker converts x_w into a time for this wafer on this chamber (Chapter 8): t_main = (x_w/4.44) × 45 s × (t_Al/27.8 s), clipped to ±5%.

### 15.5.3 Feedback From the Clearing Curve

The ALE clearing curve gives n₅₀ on every wafer. If n₅₀ drifts, the main step is leaving more or less than intended:

```
EWMA on n₅₀ (target 10.6, λ = 0.3):
  ñ_k = λ n₅₀,k + (1 − λ) ñ_{k−1}
  Correction to the main-step removal target: Δx = −(ñ_k − 10.6) × 0.10 nm

  Lot   n₅₀ (lot mean)   ñ        Δx (nm)    Main-step target
  ─────────────────────────────────────────────────────────────
   1        10.6        10.60      0          4.44
   2        11.4        10.84     −0.024 →    4.46 (+ 0.024)
   3        11.6        11.07     −0.047 →    4.49 (+ 0.047)
```

A rising n₅₀ means the finish is starting from more film; the controller raises the main-step removal target to compensate. The controller acts on the main step, never on the cycle count, because the cycle count protects the tail and must not be reduced by a noisy average.

### 15.5.4 Ring-Hour Compensation

The cycle count rises with edge-ring RF-hours (Chapter 6):

```
N(h) = 36 + ⌈ max(0, h − 50) / 100 ⌉     (illustrative fit to Chapter 6)

  h = 0–50:   36      h = 150:   37      h = 300:   39      h = 450:   41
```

A chamber with an actuated ring that holds ΔE_edge within ±1 eV runs N = 36 throughout.

### 15.5.5 What the Controller Must Never Do

1. Reduce N below the qualified 36 cycles, whether because the clearing curve looks early or because the incoming film is thin.
2. Adapt the main step beyond ±5% on the Al marker alone.
3. Use TXRF averages to justify fewer cycles.

---

## 15.6 Control of the Bevel and the Trim

```
Bevel (module 1):
  Boundary radius feedback       edge-inspection mean → robot centring offset and
                                 PEZ position offset; EWMA, λ = 0.2
  Ion-energy drift               V_pp trend → RF power trim within ± 5%; beyond
                                 that, PEZ ring replacement
  Residual Zr                    VPD > 5 × 10⁹ /cm² → enable the bevel rinse for
                                 the lot; investigate ring wear and chamber Zr

Trim (module 3):
  Run-to-run cycle count         N = round(1.00 nm / EPC_QCM,last run) within
                                 16–18; outside → hold
  Supply check                   DMAC pressure rise per dose ≥ 90% of reference
  Post-trim                      blanket pad SE: 1.00 ± 0.05 nm; else hold the lot
```

---

## 15.7 Fault Detection on Cyclic Signals

```
Per-cycle features of the ALE finish (36 values per wafer each):
  Chamber pressure at the end of each purge       residual BCl₃ (Ch. 5)
  Ignition delay (RF on → density steady)         match health
  Reflected power peak at ignition                match preset drift
  Bias V_dc in the removal step                   ion energy
  Integrated Zr and N₂ emission per removal step  clearing curve; SiN EPC
  BCl₃ dose pressure rise                         dose delivery

Multivariate model: per-cycle features → T² statistic per wafer
  Typical faults found: a fast valve slowing (purge pressure rises in
  late cycles), a match preset drifting (ignition delay rises), an MFC
  divert failing (dose pressure overshoot)
```

**Virtual metrology** of SiN loss uses the N₂ emission plateau and the number of cycles after n₅₀: SiN loss ≈ k × (N − n₅₀) × (N₂ plateau / reference), calibrated weekly against pad ellipsometry.

---

## 15.8 Sampling

```
Detecting a doubling of the chain-open rate with chains (illustrative):
  Baseline chain opens per wafer (mostly non-residue mechanisms): 0.2
  To detect a rise to 0.4 per wafer at 95% confidence, Poisson:
    need ≈ 25 wafers of data
  At 4 chains × 20 sites per wafer, 1 wafer per lot: ≈ 25 lots
```

Chains respond slowly to small changes. Large changes, a tenfold rise from a failed purge or a missing cycle, appear within one or two lots. The design philosophy follows: prevent small drifts with in-situ control (marker, clearing curve, FDC), and use chains, voltage contrast, and product test to catch the large failures that in-situ control missed.

---

## Summary and Key Takeaways

1. **The tail is invisible to surface analysis.** One grain per 10¹⁰ sites averages to about 2.5 × 10⁵ Zr atoms/cm², forty thousand times below the TXRF detection limit.

2. **Only the product samples enough sites.** 10¹¹ grain sites per wafer; its feedback takes weeks. Chains and voltage contrast catch failures a hundred to a thousand times above target.

3. **Cycle ladders measure the tail deliberately.** Fewer cycles make the tail visible; its slope gives σ and its intercept R_slow.

4. **Feed forward thickness, adapt on the marker, feed back on n₅₀.** The controller moves the main step; the cycle count protects the tail and is changed only by ring hours and qualified models.

5. **The bevel and the trim have their own loops.** Boundary radius to centring offsets; V_pp to RF trim; QCM EPC to cycle count.

6. **Cyclic processes produce cyclic data.** Per-cycle pressure, ignition, bias, and emission features catch valve, match, and dose faults before metrology does.

---

## Study Questions

1. A residual grain is 15 nm across and 0.8 nm thick. How many Zr atoms does it contain? If one such grain is left per 10⁸ grain sites (15 nm grains), what average Zr density would TXRF report, and could it detect it?

2. Using the cycle-ladder table, estimate σ/EPC from the change in z between N = 26 and N = 30. If a new chamber gives 60 opens per 10⁷ contacts at N = 30, what is its R_slow, assuming the same σ?

3. A lot arrives with ZAZ at 5.65 nm. Compute the main-step removal target and the cycle count from Section 15.5.1.

4. Continue the EWMA of Section 15.5.3 for lots 4 and 5 with n₅₀ = 11.0 and 10.4. What main-step targets result?

5. Explain why the controller must not reduce N when n₅₀ is early. Give a scenario in which an early n₅₀ coexists with a worse tail.

6. Design an FDC rule that would detect a fast valve whose closing time rises from 20 ms to 200 ms over a week. Which per-cycle feature would show it first, and in which cycles of the finish?

---

**Next Chapter:** [Chapter 16: Integration, Yield & Cost of Ownership](./16-integration-yield-coo.md)

---

**Chapter 15 Development Status:** Complete  
**Version:** 1.0
