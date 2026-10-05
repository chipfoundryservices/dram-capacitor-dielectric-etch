# Chapter 15: Metrology, Inspection & Advanced Process Control

## Overview

The dielectric etches are judged by quantities that are small and, in two cases, invisible. A film of 5.5 nm must be measured to a hundredth of a nanometre to decide a trim of one cycle. A zirconium density six decades below the film must be read on a ring at the wafer rim and in sectors around it. A contact that will not open months later because of one grain in a hundred million cannot be seen at all, and has to be bounded statistically. This chapter sets out what is measured, with what tool, and with what resolution, and how the measurements are turned into control.

It begins with the measurement map. It then treats thickness metrology of a 5 nm film, where the calibration chain matters more than the instrument; the zirconium metrologies and the decades each can resolve; edge and bevel inspection; the electrical monitors and the statistics of the contact chains; feed-forward from the ALD thickness and the stop; feedback on the removal per cycle; and fault detection and sampling.

**Learning Objectives:**
- Map each specification of the book to its measurement, tool, and frequency
- Explain the calibration chain for a 5.5 nm film and the precision each instrument contributes
- Choose TXRF or VPD-ICPMS for each of the three zirconium limits
- Compute the number of contacts and wafers needed to bound the periphery open rate by chains
- Design feed-forward from ALD thickness to trim cycles, and an EWMA on the removal per cycle
- State the fault-detection signals of each module and the sampling plan

---

## 15.1 The Measurement Map

```
Quantity                          Specification                 Measured by                  Frequency
────────────────────────────────────────────────────────────────────────────────────────────────────────────
ALD ZAZ thickness, lot mean       ± 0.2 nm (3σ); trim decision   ellipsometry; XRF check       every lot, 9 sites
ZAZ loss in the stop (P2)         ≤ 0.3 nm                       in-situ ellipsometry (Ch. 8)  every wafer
ZAZ at r = 140–150 mm             loss ≤ 0.1 nm at r < 146 mm    reflectometry line scan       weekly + each PM
Zr on backside and bevel          ≤ 1 × 10¹⁰ cm⁻²               VPD-ICPMS, sectors            weekly + PM + excursion
Zr on backside (trend)            ≤ 1 × 10¹¹ cm⁻²               TXRF                          daily
Zr on periphery pad               ≤ 1 × 10¹³ cm⁻²               TXRF                          weekly + after PM
Periphery contact opens           ≤ 0.01 per die                 scribe contact chains         each lot (weeks later)
TiN notch, plate edge             ≤ 15 nm                        OCD on scribe gratings        each lot
Shell on the TiN edge             ≥ 1.64 nm after strip          TEM/EELS                      monthly; after strip change
W loss; plate R_s                 ≤ 2.7 nm; ≤ 4.0 Ω/□           XRF; four-point probe         each lot
SiN loss, periphery               ≤ 15 nm                        ellipsometry on pad           each wafer
Cl, B on SiN; B at r = 146 mm     ≤ 2, ≤ 1 at%; ≤ 2×10¹³         XPS                           weekly
Cell leakage, C_s, TDDB           Chapters 1, 12                 capacitor arrays              each lot; monthly
```

---

## 15.2 Thickness Metrology of a 5.5 nm Film

### 15.2.1 The Instruments

```
Method              Measures                          Precision (1σ)   Accuracy         Notes
─────────────────────────────────────────────────────────────────────────────────────────────────────
Spectroscopic       film stack thickness by optical   0.01 nm          ± 0.1 nm after   model: TiOₓNᵧ interface
ellipsometry        model                                              TEM calibration  (1.0–1.5 nm), ZAZ, roughness
XRR                 thickness, density, roughness     0.03 nm          ± 0.05 nm        large pad (≥ 5 mm); slow
XRF (Zr Kα)         Zr atoms per cm² → thickness      0.3% = 0.016 nm  ± 1% = 0.05 nm   calibration to XRR/TEM
TEM / STEM          thickness directly; interfaces    ± 0.1 nm         reference        destructive; monthly
```

XRF measures atoms, not thickness: 1.44 × 10¹⁶ Zr cm⁻² for 5.2 nm of ZrO₂, so each nanometre is 2.78 × 10¹⁵ cm⁻². One ALE cycle of 0.073 nm removes 2.0 × 10¹⁴ Zr cm⁻², and XRF's repeatability, 0.3% of 1.44 × 10¹⁶ = 4.3 × 10¹³ cm⁻², resolves it with a signal-to-noise of about 5. Ellipsometry sees thickness with a model and is more precise on a single site (0.01 nm) but depends on the model of the interface layer.

### 15.2.2 The Calibration Chain

```
TEM (± 0.1 nm, reference)  →  XRR (± 0.05 nm)  →  XRF counts and ellipsometry model
         monthly                  quarterly              every lot / daily
```

The chain matters because the decision it supports, the trim, is made at the level of one cycle (0.073 nm). A lot-mean thickness known to ± 0.03 nm (3σ, σ = 0.01 nm) gives a probability of choosing the wrong cycle count of

```
P(wrong N) = 2 × [1 − Φ(0.0365 / σ_meas)]       half a cycle = 0.0365 nm
  σ_meas = 0.010 nm:   0.03%
  σ_meas = 0.015 nm:   1.5%
  σ_meas = 0.030 nm:   22%
```

An ellipsometer that has drifted by 0.03 nm (1σ) would give the wrong cycle count on one lot in five. Calibration, not instrument noise, sets the trim's reliability.

---

## 15.3 Zirconium

### 15.3.1 Which Tool for Which Limit

```
Method        Floor (Zr cm⁻²)    Area               1 × 10¹³   1 × 10¹¹   1 × 10¹⁰    Use
──────────────────────────────────────────────────────────────────────────────────────────────────
TXRF          1 × 10⁹–10¹¹       ≈ 1 cm² spot        ✓          marginal   ✗           daily trend
VPD-ICPMS     1 × 10⁸–10⁹        whole surface or    ✓          ✓          ✓ (10×)     weekly proof;
                                 a sector                                              furnace entry
XPS           ≈ 1 × 10¹³         ≈ 50 µm             marginal   ✗          ✗           chemical state
TOF-SIMS      ppm                ≈ 100 µm            —          —          —           islands, maps
Contact chain functional         full contact module                                   tail of the
                                                                                       periphery clear
```

TXRF is a spot and an average; it cannot prove 10¹⁰ cm⁻² on the backside, where a 10% sector of full film would be missed by a single spot. VPD-ICPMS collects the surface onto a droplet and reads it by mass spectrometry; with a floor of 10⁸–10⁹ cm⁻² it resolves 10¹⁰ with a margin of ten.

### 15.3.2 Sector Sampling

The edge zone is read in sectors, because a partial failure (Chapter 9) shows only in one azimuth:

```
Collection: 8 azimuthal sectors × 3 zones (top ring, bevel, backside)  = 24 areas
  Sector area  ≈ 66 cm² / 8 ≈ 8 cm² (all zones)
  Floor in atoms:  1 × 10⁹ cm⁻² × 8 cm² = 8 × 10⁹ atoms per sector
  At the 10¹⁰ limit: 8 × 10¹⁰ atoms per sector: a factor 10 above the floor
```

The sacrificial wafer is a bare silicon wafer run through the edge etch and clean with a dummy recipe; the weekly proof uses product-equivalent wafers from a randomly chosen lot.

---

## 15.4 Edge and Bevel Inspection

```
Inspection                       Detects                                  Resolution        Frequency
────────────────────────────────────────────────────────────────────────────────────────────
Bevel optical / dark-field       flakes, particles, film edges at the     ≈ 0.5 µm          every wafer
                                 bevel apex and slopes
Reflectometry line scan,         position of the ZAZ edge at r = 147 mm;   ± 0.05 mm         weekly; PM
r = 140–150 mm                   loss inside the boundary
Top-ring and backside sector     residue films (BₓClᵧ haze), Si roughness  macro              each lot
macro images
```

The boundary position is checked against ± 0.3 mm (Chapter 5); a line scan resolves it to ± 0.05 mm, six times finer than the specification.

---

## 15.5 Electrical Monitors

```
Structure                         Reads                          Role (Chapters)
───────────────────────────────────────────────────────────────────────────────────────────
Reference capacitor arrays        C_s, leakage at 0.55 and 1.0 V  baseline (1, 12)
Trim-dose arrays                  leakage vs cycles               trim chemistry (12, 13)
Edge-proximity arrays             leakage vs overlap              edge damage (11, 12)
Antenna and polarity arrays       leakage vs antenna ratio        charging (7, 12)
Large-area TDDB capacitors        Weibull slope, area scaling     defect density (12)
Periphery contact chains          opens through the contact module  residue tail (4, 10)
```

### 15.5.1 Bounding the Periphery Open Rate With Chains

The requirement is 0.01 opens per die, i.e. P_open ≤ 0.01 / (3 × 10⁷) = 3.3 × 10⁻¹⁰ per contact. With zero failures in N contacts, the 95% upper bound on P_open is 3/N:

```
Contacts needed for P_open ≤ 3.3 × 10⁻¹⁰ at 95% (zero failures):
  N = −ln(0.05) / 3.3×10⁻¹⁰ = 9.0 × 10⁹ contacts = 300 dies' worth

Scribe chains: 2 × 10⁶ contacts per site × 100 sites per wafer = 2 × 10⁸ per wafer
  → 45 wafers of chains with no open
  20 wafers (4 × 10⁹ contacts): upper bound 7.5 × 10⁻¹⁰   (not enough)
Expected opens in 4 × 10⁹ contacts at P_open = 3.3 × 10⁻¹⁰:   1.3
```

A chain test can bound the tail only after dozens of wafers have been measured, and weeks after the plate etch. It is the arbiter of a change, not a lot-by-lot control. The in-line control of the periphery clear rests on the Al marker (Chapter 8), the ellipsometer on the stop, the chuck temperature, and the energy window of Chapter 7.

---

## 15.6 Feed-Forward

### 15.6.1 ALD Thickness to Trim

```
Input        lot-mean ZAZ thickness, 9 sites (ellipsometry; XRF cross-check)
Model        Δt = t_meas − t_nom;   N = 0 if Δt < EPC;   N = round(Δt / EPC_now) otherwise
Limits       N ≤ 4 at 265 °C (0.23 nm) or N ≤ 3 at 280 °C (0.22 nm); a lot with Δt > 0.26 nm is
             held for review (a larger trim spends the headroom; Δt > 0.5 nm goes to rework)
Trim time    10 s per cycle (single-wafer); added to the queue limit (Chapter 1)
```

### 15.6.2 ALD Thickness and TiN Thickness to the Stop and Clear

The incoming ZAZ thickness (± 0.2 nm, 3σ) and the TiN thickness (± 0.3 nm) are known per wafer from XRF. They give the expected clearing times:

```
P2:  t_c = t_TiN / R_TiN = 5.0 nm / 16.5 nm/min = 18.2 s  (± 6%: ± 1.1 s from thickness)
P4:  t_clear = 28 s ± 3.6% (± 1.0 s from ZAZ thickness)
```

The expected times are compared with the measured endpoints (Ti I inflection in P2, Al-marker in P4). A measured t_c more than 10% from the expected value, or an Al peak more than 10% off, holds the wafer for review.

---

## 15.7 Feedback

### 15.7.1 EWMA on the Removal per Cycle

```
Thermal ALE removal per cycle (reference):
  Measurement   pad ellipsometry, one wafer per lot (EPC = thickness removed / cycles)
  Update        EPC_{n+1} = λ EPC_meas,n + (1 − λ) EPC_n,   λ = 0.3
  Use           N = round(Δt / EPC_{n+1})

Example: EPC_n = 0.0730 nm;  lot n measures 0.0690 nm
  EPC_{n+1} = 0.3 × 0.0690 + 0.7 × 0.0730 = 0.0718 nm
  A lot with Δt = 0.20 nm:  0.20 / 0.0718 = 2.79 → N = 3
Next lot measures 0.0660 nm:
  EPC_{n+2} = 0.3 × 0.0660 + 0.7 × 0.0718 = 0.0701 nm → 0.20/0.0701 = 2.85 → N = 3
```

The witness crystal (Chapter 8) supplies EPC between lots; the pad measurement anchors it. A sustained fall in EPC is a pedestal or DMAC problem, not a quantity to be compensated indefinitely: when EPC falls more than 8% from its calibration, the loop stops and the chamber is held (Chapter 6).

### 15.7.2 The Stop

The in-situ ZAZ loss of every wafer (Chapter 8) feeds the stop's action limits:

```
Apparent ZAZ loss L (nm)     Action
──────────────────────────────────────────────────────────────────
L ≤ 0.10                     none (reference 0.03–0.05)
0.10 < L ≤ 0.15              warn; check wall F (WAC log), bias at the stop
0.15 < L ≤ 0.30              reduce bias power 5%; check the F chamber split
L > 0.30                     hold the lot; check for pinholes in the TiN
```

### 15.7.3 Edge Compensation

Ring wear and plate erosion in the edge chamber change the boundary and the wrap coverage slowly. RF hours on the powered ring and the weekly reflectometry boundary scan trigger a ring replacement; a boundary drift of more than 0.15 mm from nominal is an action limit (half the specification).

---

## 15.8 Fault Detection

```
Signal                                   Module    Indicates
─────────────────────────────────────────────────────────────────────────────────────────────
Centre-purge flow; plate-gap capacitance E         shield integrity; boundary
Reflected power; self-bias               E, P4     plasma ring condition; ion energy
Al-peak time (4-azimuth average)         E, P4     ZrO₂ rate drift
Ti I inflection time t_c                 P2        TiN rate; thickness
Post-endpoint slope of Ti I / N₂         P2        late edge; incomplete clearing
In-situ ZAZ loss on the pad              P2        stop quality (F, energy)
Strip time to CO end                     P3        resist and BARC cleared; shell proxy
Chuck and liner temperatures             P4        ZrO₂ rate; B condensation
Foreline pressure                        P4, T     AlCl₃/ZrCl₄/ZrF₄ condensation
Witness-crystal Δf per cycle             T         EPC; DMAC/HF dose; pedestal T
Pedestal temperature; pulse pressure traces T      EPC; dose margin
Wafers since ALD clean; first-wafer thickness C    wall state; flake risk
```

A multivariate model of these signals, trained on lots with good electrical results, gives each wafer a health score; wafers outside the envelope are held before the top-electrode deposition (modules E and T) or the ILD (module P).

---

## 15.9 Sampling Plan

```
Measurement                                       Frequency
─────────────────────────────────────────────────────────────────────────────────────
Module E
  VPD-ICPMS sectors (backside, bevel, top ring)   weekly; each PM; after excursions
  TXRF backside, daily trend                      daily monitor wafer
  Reflectometry boundary line scan                weekly; PM
  Bevel inspection                                every wafer
Module P
  In-situ ZAZ loss (P2); Al marker (P4)           every wafer
  SiN loss (ellipsometry on pad)                  every wafer
  TXRF Zr periphery pad                           weekly; first lot after PM
  OCD notch; XRF W; four-point R_s                every lot
  TEM / EELS shell, plate edge                    monthly; after strip or P4 change
  Contact chains                                  each lot (read later); trend by 45 wafers
Module T
  ALD thickness (ellipsometry; XRF)               every lot
  EPC (pad ellipsometry; witness crystal)         one wafer per lot; every cycle (witness)
  Trim-dose array leakage                         monthly
Module C
  First-wafer ZAZ thickness; particles            after every clean
  Zr canary in clean-zone tools                   weekly; after PM
```

---

## Summary and Key Takeaways

1. **Calibration sets the trim's reliability.** With σ_meas = 0.010 nm the wrong cycle count occurs in 0.03% of lots; at 0.030 nm it is 22%.

2. **XRF counts atoms.** 2.78 × 10¹⁵ Zr cm⁻² per nanometre; one ALE cycle is 2 × 10¹⁴, and XRF repeatability of 4.3 × 10¹³ resolves it with S/N ≈ 5.

3. **Match the tool to the decade.** TXRF for 10¹³ and as a trend at 10¹¹; VPD-ICPMS for 10¹⁰; contact chains for the tail.

4. **Read the edge in sectors.** 8 azimuths × 3 zones, floor 8 × 10⁹ atoms per sector against 8 × 10¹⁰ at the limit.

5. **Chains bound, they do not control.** 9 × 10⁹ contacts (45 wafers of chains) with zero opens bound P_open to 3.3 × 10⁻¹⁰; control is the Al marker, the stop ellipsometer, and the energy window.

6. **Feed forward the ALD thickness; feed back the EPC.** N = round(Δt/EPC_now) with an EWMA (λ = 0.3) on pad ellipsometry; stop the loop when EPC falls 8%.

---

## Study Questions

1. An ellipsometer is 0.04 nm too low on lot-mean ZAZ thickness. Compute the cycle count it gives for a lot with true Δt = 0.10 nm and the resulting thickness relative to nominal (EPC = 0.073 nm).

2. Compute the number of wafers of scribe chains (2 × 10⁶ contacts per site, 100 sites) needed to bound the open rate at 1 × 10⁻⁹ per contact at 95% with zero failures, and the bound after 10 wafers.

3. A VPD sector of 8 cm² reads 1.2 × 10¹¹ atoms. Compute its areal density and compare it with the 10¹⁰ cm⁻² limit. If the other seven sectors read at the floor (8 × 10⁹ atoms each), what is the ring average, and what does the comparison say about reading the ring as one sample?

4. Run the EWMA of Section 15.7.1 for three lots measuring 0.0710, 0.0700, 0.0680 nm from a start of 0.0730 (λ = 0.3). Give the EPC estimates and the cycle counts for Δt = 0.20 nm. When does the 8% stop trigger?

5. An XRF reading of Zr is 1.46 × 10¹⁶ cm⁻² before a trim and 1.43 × 10¹⁶ cm⁻² after. Compute the thickness removed and the number of cycles it implies, with the XRF uncertainty of 4.3 × 10¹³ cm⁻² on each reading.

6. Explain why a periphery-pad TXRF reading of 5 × 10¹² cm⁻² is consistent with both a good and a bad contact-open rate, and which monitors of this chapter would tell them apart.

---

**Next Chapter:** [Chapter 16: Integration, Yield & Cost of Ownership](./16-integration-yield-coo.md)

---

**Chapter 15 Development Status:** Complete  
**Version:** 1.0
