# Chapter 12: In-Array Dielectric Trim by Thermal ALE

## Overview

Every other etch in this book removes the dielectric where it is not a capacitor. The trim removes it where it is. At the 1c generation, the open channel left between three neighbouring pillars after the dielectric becomes too narrow for the top electrode if the dielectric is deposited at the thickness at which its top ZrO₂ layer crystallizes best. The pilot flow resolves the conflict by depositing a thicker film, crystallizing it, and then thinning it back by a nanometre with thermal atomic-layer etching (ALE), so that the film keeps the crystal structure it formed at its deposited thickness and the channel keeps the room the top electrode needs.

The trim is isotropic and has no ions; it is uniform across the wafer to a few percent. Its difficulties lie inside the array. The reactants must reach the bottom of channels two hundred times deeper than they are wide, and the wafer's 2 m² of array surface consumes more reactant per cycle than the reactor holds. The trim etches grain boundaries faster than grains. It leaves fluorine, aluminium, and carbon in the surface the top electrode will be deposited on. And it touches every one of seventeen billion capacitors per die.

**Learning Objectives:**
- Explain the trade-off between dielectric thickness, crystallinity, and channel radius that motivates the trim
- Compute the reactant consumed per cycle by the array surface and the minimum dose time it implies
- Use a conformality model to estimate the exposure needed to saturate the bottom of a channel of given aspect ratio
- Explain why a soft-saturating fluorination makes the trim top-heavy, and estimate the bottom-to-top ratio
- Estimate the excess thinning at grain boundaries and its effect on leakage
- Compare the capacitance and leakage of the as-deposited, thick, and trimmed options

---

## 12.1 Why Trim

### 12.1.1 The 1c Pilot Geometry

```
1c-class pilot array (illustrative):
  Hexagonal storage-node pitch          41 nm
  Pillar CD below the top support       27 nm (top) / 24 nm (avg) / 21 nm (bottom)
  Mold height                           1.60 µm (as the reference)
  Channel depth below the top support   ≈ 1.48 µm
  Effective capacitor area              ≈ 1.05 × 10⁵ nm² per cell

Distance from a channel centre (between three pillars) to the pillar
centres: 41/√3 = 23.7 nm

  Channel radius before the dielectric:
    top 23.7 − 13.5 = 10.2 nm;  middle 11.7 nm;  bottom 13.2 nm
```

### 12.1.2 Three Options

```
                            (a) As reference   (b) Thick, no trim   (c) Thick + trim
                            5.5 nm              6.5 nm               6.5 → 5.5 nm
──────────────────────────────────────────────────────────────────────────────────────
Layers (ZrO₂/Al₂O₃/ZrO₂)    2.6/0.3/2.6         2.6/0.3/3.6          2.6/0.3/2.6
                                                                    (top crystallized
                                                                     at 3.6 nm)
Top-layer k                 ≈ 48                ≈ 55                 ≈ 55
EOT (measured scale)        0.50 nm             0.54 nm              0.475 nm
C_s (1.05 × 10⁵ nm²)        7.25 fF             6.7 fF               7.6 fF
Channel radius at the top   4.7 nm              3.7 nm               4.7 nm
after the dielectric
Top-electrode TiN reaching  4.7 nm              3.7 nm               4.7 nm
the bottom (≈ channel
radius at the top)
```

Option (b) gains crystallinity but loses capacitance to thickness, and starves the top electrode: a TE TiN of 3.7 nm is too thin for reliable continuity and work function. Option (c) keeps the channel of option (a) and adds about 5% of capacitance through the better-crystallized top layer. **The trim buys capacitance at constant geometry.** Whether that is worth touching every capacitor in the array is the question of this chapter.

### 12.1.3 The Pilot Sequence

```
  1. ZAZ ALD: ZrO₂ 2.6 / Al₂O₃ 0.3 / ZrO₂ 3.6 nm, 300 °C
  2. Post-deposition anneal, N₂, 420 °C, 10 min (top ZrO₂ ≈ 98% tetragonal)
  3. Thermal ALE trim, HF/DMAC, 250 °C, 17 cycles (≈ 1.0 nm)
  4. O₃ exposure, 250 °C, 30 s (fluorine and carbon reduction)
  5. TE TiN ALD, 5 nm (reaches 4.7 nm at the bottom of the channels)
```

Steps 2–4 run without breaking vacuum where possible: the trimmed surface is reactive and adsorbs water and hydrocarbons in air.

---

## 12.2 Reactant Supply: The Array as a Sink

### 12.2.1 How Much Surface

The array surface is about 2 m² per wafer (Chapter 1). Every cycle must fluorinate all of it and then exchange all of it:

```
Surface demand per cycle (illustrative):
  HF:    S_HF ≈ 1 × 10¹⁵ molecules/cm² → 2 × 10¹⁹ molecules per wafer
  DMAC:  S_DMAC ≈ 3 × 10¹⁴ molecules/cm² → 6 × 10¹⁸ molecules per wafer

Gas in the reactor (2 L at 0.5 Torr, 250 °C):
  n = pV/kT ≈ 66.7 Pa × 2 × 10⁻³ m³ / (7.2 × 10⁻²¹ J) ≈ 1.9 × 10¹⁹ molecules
```

One fill of the reactor holds about as many HF molecules as one cycle consumes. The dose cannot be a pulse; it must be a sustained flow until the surface has taken what it needs.

### 12.2.2 Minimum Dose Times

```
1 sccm ≈ 7.5 × 10¹⁵ molecules/s

HF at 500 sccm:     3.7 × 10¹⁸ /s →  5.4 s at 100% utilization
                                      ≈ 8 s at ≈ 70% utilization (reference)
DMAC at 80 sccm-    6.0 × 10¹⁷ /s → 10 s at 100% utilization
equivalent (vapour                    ≈ 12 s at ≈ 85% utilization (reference)
draw limited)
```

The blanket thermal ALE cycle of Chapter 4 took 5 s; on a patterned 1c wafer, the doses alone take 20 s. With purges long enough to clear HF from the reactor before DMAC arrives (otherwise HF and DMAC react in the gas and in the channels and deposit AlF₃), the cycle takes about 35 s:

```
Pilot cycle on product (reference):
  HF dose 8 s  |  purge 5 s  |  DMAC dose 12 s  |  purge 10 s  = 35 s
  17 cycles ≈ 10 min, plus heat-up and the O₃ step
```

---

## 12.3 Transport Into the Channels

### 12.3.1 Molecular Flow

```
Mean free path at 0.5 Torr, 250 °C:   ≈ 0.1 mm  ≫ channel width (7–13 nm)
Regime: free-molecular (Knudsen) flow

Mean molecular speed v̄ = √(8kT/πm), 250 °C:
  HF (20 amu)         ≈ 740 m/s
  DMAC (92.5 amu)     ≈ 350 m/s

Knudsen diffusivity D_K = d v̄ / 3, d = 7.4 nm (narrowest, top):
  HF     1.8 × 10⁻⁶ m²/s
  DMAC   8.6 × 10⁻⁷ m²/s

Diffusion time over the channel depth, L²/D_K (1.48 µm):
  HF ≈ 1 µs;  DMAC ≈ 2.5 µs   (without wall reactions)
```

Free diffusion is fast. What slows reactants down is that they react with the walls on the way.

### 12.3.2 Exposure Needed to Saturate the Bottom

For a self-limiting reaction in a long, narrow feature, the exposure (pressure × time) needed to saturate the full depth grows roughly as the square of the aspect ratio a = L/d. A widely used approximation for a cylindrical hole is:

```
(P t)_req ≈ S √(2π m k T) (1 + 19a/4 + 3a²/2)

Channel at the 1c pilot (narrowest diameter 7.4 nm, L = 1.48 µm): a ≈ 200
  Factor (1 + 950 + 60,000) ≈ 6.1 × 10⁴

HF:   S √(2πmkT) ≈ 1 × 10¹⁹ m⁻² × 3.9 × 10⁻²³ kg·m/s ≈ 3.9 × 10⁻⁴ Pa·s
      (P t)_req ≈ 24 Pa·s ≈ 0.18 Torr·s
DMAC: ≈ 3 × 10¹⁸ × 8.4 × 10⁻²³ ≈ 2.5 × 10⁻⁴ Pa·s
      (P t)_req ≈ 15 Pa·s ≈ 0.11 Torr·s

Reference doses: HF 0.5 Torr × 8 s = 4 Torr·s;  DMAC ≈ 0.2 Torr × 12 s = 2.4 Torr·s
Over-exposure factor at the channel bottom: ≈ 20×
```

The channel is not the bottleneck; the wafer-level supply is. Once the dose is long enough to satisfy the whole array surface, it has delivered far more than the channels need. The bottom of the channel saturates.

### 12.3.3 But Saturation Is Soft

Fluorination of ZrO₂ by HF is not perfectly self-limiting. The fluoride layer keeps thickening, slowly, as HF diffuses through it; the more exposure, the more fluoride, and the more the next DMAC step removes:

```
EPC = EPC₀ [1 + β ln(X)],   X = exposure / saturation exposure (X ≥ 1)
β ≈ 0.035 (illustrative, tetragonal ZrO₂, 250 °C)
```

The top of each channel sees the full dose from the moment the dose begins; the bottom sees it only after the wave of reaction has passed down the channel. The top is therefore over-exposed relative to the bottom:

```
Over-exposure of the top relative to the bottom ≈ 10× (illustrative)
EPC_top / EPC_bottom = 1 + 0.035 × ln 10 ≈ 1.08
Bottom-to-top trim ratio ≈ 0.92  (specification ≥ 0.90)
```

```
Bottom-to-top ratio versus dose (illustrative):

  HF dose (s)   DMAC dose (s)   Bottom saturated?   Ratio    EPC (top)
  ──────────────────────────────────────────────────────────────────────
     3              5           no (supply-limited) 0.70     0.058
     5              8           marginal            0.85     0.060
     8 (ref.)      12 (ref.)    yes                 0.92     0.061
    15             20           yes                 0.91     0.063
```

Beyond the reference doses, the ratio does not improve: the top keeps gaining from soft saturation as fast as the bottom catches up. The residual 8% is the trim's equivalent of the deposition's step coverage; the two multiply (Chapter 2, Section 2.5).

---

## 12.4 Grain Boundaries

### 12.4.1 Faster at the Boundaries

```
EPC on a grain interior (tetragonal ZrO₂)      0.060 nm/cycle
EPC at a grain boundary (initial)              0.085 nm/cycle
Ratio                                          ≈ 1.4
```

If the ratio held through the whole trim, 17 cycles would remove 1.0 nm from the grains and 1.45 nm at the boundaries, leaving a groove 0.45 nm deep along every boundary, beyond the 0.3 nm specification.

### 12.4.2 The Groove Starves Itself

A grain boundary is about 0.5 nm wide. As the groove along it deepens, the exchange reagent, DMAC, a molecule about 0.6 nm across, has increasing difficulty reaching the bottom of the groove:

```
Groove depth (nm)    Effective EPC at the groove bottom    Excess per cycle
───────────────────────────────────────────────────────────────────────────
0.0–0.1              0.085                                 0.025
0.1–0.2              0.075                                 0.015
0.2–0.3              0.064                                 0.004
> 0.3                ≈ 0.060 (groove follows the surface)  ≈ 0

Excess depth saturates at ≈ 0.25–0.3 nm after ≈ 10 cycles
Pilot (17 cycles), measured by TEM tomography: 0.25 nm
```

The groove limits itself at about half its width, because a narrower, deeper groove admits too little of the larger reactant. This is an argument from molecular size, and it has a corollary: a smaller exchange reagent (TMA, at about 0.5 nm, or SiCl₄) would not self-limit as early. DMAC's size is part of the pilot's design.

### 12.4.3 What the Groove Does to Leakage

```
Local thinning ≈ 0.25 nm over ≈ 5% of the area (the boundaries)
Local leakage factor = exp(0.25 / 0.25) ≈ 2.7  (λ = 0.25 nm, Chapter 1)

Area-weighted leakage change ≈ 0.95 × 1 + 0.05 × 2.7 ≈ +9%
```

The mean leakage rises by about 9%. The tail is protected by the Al₂O₃ insertion: a grain boundary in the top ZrO₂ does not continue through the insertion, so a thinned boundary in the top layer does not create a straight path from electrode to electrode. Without the insertion, a top-layer groove aligned with a bottom-layer boundary would be the leakiest spot in the cell.

---

## 12.5 What the Trim Leaves in the Surface

```
Surface of the trimmed ZrO₂ before the TE (illustrative):

  Species   After 17 cycles     After the O₃ step     Specification   Concern
            (ending on DMAC)    (250 °C, 30 s)
  ──────────────────────────────────────────────────────────────────────────────
  F         2–4 at%, top 0.3 nm 0.5–1 at%             ≤ 1 at%         fixed charge,
                                                                      traps (Ch. 13)
  Al        ≈ 1 × 10¹⁴ /cm²     unchanged (oxidized   —               raises local k
            (adsorbed AlFₓ,     to Al–O)                              slightly; benign
            AlCH₃)
  C         ≈ 1–2 at%           < 0.5 at%             ≤ 0.5 at%       leakage
  Cl        ≈ 0.5 at%           ≈ 0.3 at%             —               similar to the
                                                                      TE TiN's own Cl
```

The O₃ step exchanges surface fluorine for oxygen and burns off methyl groups. It does not remove aluminium, which is left as a fraction of a monolayer of Al–O on the ZrO₂ surface; at that level it behaves as a surface dopant and has no measurable effect on EOT.

---

## 12.6 Results of the Pilot

```
1c pilot, capacitor arrays (illustrative):

                                  (a) 5.5 nm      (c) 6.5 → 5.5 nm trim
                                  as deposited
  ─────────────────────────────────────────────────────────────────────────
  EOT (C–V)                       0.50 nm         0.475 nm
  Within-wafer EOT (3σ)           ± 0.010 nm      ± 0.012 nm
  C_s, median                     7.25 fF         7.6 fF (+5%)
  C_s, top-to-bottom of pillar    ± 1%            ± 2% (trim ratio 0.92)
  Leakage at 1.0 V, median        1.0 (norm.)     1.1
  Leakage at 1.0 V, 10⁻⁶ tail     1.0 (norm.)     1.2
  TDDB (t₆₃ at 2.0 V, 125 °C)     1.0 (norm.)     0.9
  TE TiN at the channel bottom    4.7 nm          4.7 nm
```

The trim delivers its 5% of capacitance at a cost of about 10–20% in leakage and 10% in breakdown lifetime. At the retention margins of Chapter 1, that is a trade most products would take, provided the excursions are controlled: a trim that goes wrong goes wrong in every cell of every die on the wafer.

---

## 12.7 Risks and Controls

```
Risk                              Mechanism                          Control
───────────────────────────────────────────────────────────────────────────────────
Over-trim                         EPC drift (temperature, HF          QCM per run; blanket
                                  purity); extra cycles               pad SE per wafer;
                                                                      cycle-count interlock
Under-saturated bottom            DMAC vapour supply low              DMAC bubbler level and
                                  (bubbler level, temperature)        temperature; pressure
                                                                      rise per dose
AlF₃ deposition in channels       HF left when DMAC arrives           purge length; HF
                                  (short purge)                       partial pressure at
                                                                      DMAC start
Groove beyond 0.3 nm              exchange reagent changed;           reagent qualification;
                                  temperature high                    TEM tomography sample
Fluorine > 1 at%                  O₃ step skipped or short            interlock; SIMS sample
Air exposure before the TE        surface reacts with H₂O, C          vacuum transfer;
                                                                      ≤ 2 h queue if not
Whole-array excursion             any of the above, on every cell     hold lots until
                                                                      electrical data; small
                                                                      pilot volume
```

The trim's metrology problem is that the measurement that matters, the thickness and grain-boundary profile at the bottom of a 1.5 µm channel, is available only by TEM on a few sites and by capacitance and leakage weeks later. Production control relies on blanket pads in the scribe line and on the QCM, which see the flat-surface EPC; the transport model of Section 12.3 connects them to the array (Chapter 15).

---

## Summary and Key Takeaways

1. **The trim buys capacitance at constant geometry.** Deposit 6.5 nm, crystallize the top layer at 3.6 nm, trim to 5.5 nm: EOT 0.475 nm, +5% C_s, and the same 4.7 nm channel for the TE.

2. **The array is a reactant sink.** 2 m² per wafer consumes about one reactor-fill of HF per cycle; doses of 8–12 s and cycles of 35 s follow.

3. **The channels are not the bottleneck.** The exposure needed at a = 200 is about 0.2 Torr·s; the doses deliver twenty times that.

4. **Soft saturation makes the trim top-heavy.** EPC rises with ln(exposure); the bottom-to-top ratio is about 0.92 and does not improve with longer doses.

5. **Grain boundaries groove, then stop.** The groove self-limits at about 0.25 nm because DMAC cannot reach the bottom of a narrower, deeper slot; mean leakage rises by about 9%.

6. **Every cell is touched.** The trim's gain and its risk are both array-wide; it is a pilot module for that reason.

---

## Study Questions

1. Compute the channel radius at the top after a 6.0 nm deposition followed by a 0.5 nm trim in the 1c pilot geometry. Using the layer permittivities of Chapter 2, what EOT would you expect if the top layer were deposited at 3.1 nm and trimmed to 2.6 nm?

2. A product has 2.6 m² of array surface per wafer. Recompute the HF and DMAC dose times for the same flows and utilizations. What is the new cycle time if the purges are unchanged?

3. Using the conformality approximation, compute the exposure needed to saturate a channel with a = 300. Is the reference HF dose still sufficient?

4. If β were 0.06 instead of 0.035, what would the bottom-to-top trim ratio be? Would the pilot meet its specification?

5. A team proposes TMA instead of DMAC as the exchange reagent, to avoid chlorine. Using Chapter 4 and Section 12.4.2, discuss the effect on the ZrO₂ EPC and on grain-boundary grooving.

6. Estimate the change in median leakage if the groove depth were 0.4 nm instead of 0.25 nm. Why is the 10⁻⁶ leakage tail more sensitive to the groove than the median?

---

**Next Chapter:** [Chapter 13: Process-Induced Damage & Dielectric Reliability](./13-process-induced-damage-reliability.md)

---

**Chapter 12 Development Status:** Complete  
**Version:** 1.0
