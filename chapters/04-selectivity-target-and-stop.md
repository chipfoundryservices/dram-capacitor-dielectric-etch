# Chapter 4: Selectivity Design — The Dielectric as Target and as Stop Layer

## Overview

In Book #32 the ZAZ is only ever the thing being removed. In this book it is also the thing that must not be. The conductor etch of module P ends by clearing 5 nm of TiN on top of 5.5 nm of ZAZ, and the clear that follows must remove the ZAZ without eating the tungsten above, the nitride below, or the oxide shell that protects the TiN sidewall. The edge etch must clear the same film from a backside of silicon. Every one of these is a selectivity requirement, and every one is a different number.

This chapter collects them. It builds the selectivity matrix of the six chemistries of Chapter 3 against ten films, derives the stop requirement for the conductor etch from the clearing-time spread, and contrasts the two ways of stopping on a dielectric: below its ion-energy threshold, and in a deposition regime. It then derives the three selectivity budgets of the periphery clear (nitride, tungsten, and oxide shell), argues quantitatively for removing the film while it is amorphous, and closes with a first-pass comparison of the five routes that Chapter 16 will price.

**Learning Objectives:**
- Read and extend the selectivity matrix for the dielectric etches
- Derive the minimum TiN:ZAZ selectivity from the TiN overetch and the clearing-time spread
- Contrast threshold stops and deposition stops, and choose between them
- Set the W, SiN, and TiOₓ budgets of the strip-then-clear route and the selectivity each implies
- Quantify what removing the film early (amorphous) saves
- Compare routes R0–R4 on time, loss, undercut, and residue tail

---

## 4.1 The Selectivity Matrix

```
Rates in nm/min unless noted        E edge        R0 integrated   P2 stop       P4 hot clear   T thermal ALE   Wet
                                    BCl₃/Cl₂      BCl₃/Cl₂        Cl₂/Ar        BCl₃/Cl₂/Ar    HF/DMAC         0.5% HF
                                    250 eV, ×0.25 150 eV, 60 °C   40 eV, 60 °C  80 eV, 250 °C  280 °C, nm/cycle 25 °C
──────────────────────────────────────────────────────────────────────────────────────────────────────────────────
ZrO₂ amorphous                       3.7           9              0             —              0.07            2
ZrO₂ tetragonal                      —             6              0             12             0.045           0.2
Al₂O₃ (0.3 nm layer)                 2.1           5              0             9              0.05            3
TiN (vertical)                       —             50             16.5          120            ≈ 0             < 0.1
TiOₓ shell (1.8 nm)                  —             —              0             2.0 (chem.)    ≈ 0             < 0.1
SiN (PECVD periphery)                3.3           8              0.8           4              ≈ 0             2
SiO₂ (PE-TEOS)                       2.1           5              0.5           2              ≈ 0.01          3
W (40 nm strap)                      —             —              under resist  2.4            ≈ 0             < 0.1
Si (backside)                        10.7          —              —             —              —               0
Resist (KrF)                         —             50             13            stripped       —               —
```

The columns come from the chemistry of Chapter 3 and the rates of Book #32; entries marked "—" are films that are absent or masked in that step. Four rows deserve comment before the budgets are drawn from them.

**TiN against ZrO₂.** In the integrated step of Book #32 (R0), TiN etches only 50/6 = 8 times faster than tetragonal ZrO₂. That is acceptable there because the step is not trying to stop on the ZAZ; it is clearing it. In the stop step P2, TiN etches at 16.5 nm/min and zirconia not at all: the ion energy of 40 eV is below the 45 and 60 eV thresholds. The selectivity is limited by surface modification, not by etching (Chapter 10).

**ZrO₂ against SiN.** The ambient route has ZrO₂:SiN of 0.75. The hot route has 3.0. The edge route has 3.7/3.3 = 1.1 against periphery SiN at the top edge ring, where nitride loss does not matter.

**ZrO₂ against Si.** At the backside the film lies on silicon. In a Cl-rich plasma silicon etches faster than zirconia: 10.7 nm/min against 3.7. A 28 s overetch removes 5 nm of silicon, inside the 10 nm limit of Chapter 1. It is the film on which the edge etch is least selective, and it stays exposed to the end of the step.

**ZrO₂ against W and the shell.** These two rows exist only in the strip-then-clear route, where the plate is its own mask. They set the P4 budgets of Section 4.4.

---

## 4.2 The Stop Requirement

### 4.2.1 What "Stop" Means Here

The conductor etch P2 clears the 5 nm of TiN under the SiGe. When a site has cleared, the ZAZ is exposed and then loses material at its own rate until the step ends. The loss at the site that clears first is the largest. The specification is a ZAZ loss of at most 0.3 nm (Chapter 1). Why 0.3 nm? Because the clearing time of P4 is set from the ZAZ thickness; a loss of 0.3 nm is 5.5% of the film, comparable to the thickness tolerance of ± 0.2 nm, and it keeps the 28 s clearing time of P4 predictable to better than ± 1.5 s.

### 4.2.2 The Arithmetic

```
TiN step (reference):  Cl₂/Ar, 40 eV, TiN 16.5 nm/min  → nominal clearing time
  t_c = 5.0 nm / 16.5 nm/min = 18.2 s
  Step time (100% overetch)  t_step = 36.3 s

Clearing-time spread (3σ):
  TiN thickness   ± 0.3 nm   = ± 6.0%
  Rate non-uniformity (ESC, edge)  ± 5%
  Combined  √(6.0² + 5.0²) = 7.8%

Fastest site clears at   18.2 × (1 − 0.078) = 16.7 s
  → overetch at that site 36.3 − 16.7 = 19.6 s
  → TiN-equivalent removed in that overetch   16.5 × 19.6/60 = 5.4 nm

Required selectivity   S = R_TiN / R_ZAZ ≥ 5.4 nm / 0.3 nm = 18
```

The stop must be at least 18 times more selective than a 100% TiN overetch needs; with the overetch lowered to 60% the requirement falls to 11. The measured ZAZ loss in Cl₂/Ar at 40 eV is 0.03–0.05 nm (Chapter 10), which gives S ≈ 110–180 and a margin of 6–10 times. The margin is not wasted: it is what absorbs fluorine memory, Cl uptake, and a worn edge ring.

### 4.2.3 Energy Window

```
Cl₂/Ar stop, TiN rate against ion energy (yield model of Chapter 3):
  E (eV)     TiN (nm/min)    ZrO₂ (BCl₃-free, 0.3× model)    TiN : ZrO₂
  ─────────────────────────────────────────────────────────────────────
   30           6.0               0                              ∞
   40          16.5               0                              ∞
   50          25.8               0                              ∞
   60          34.3               0                              ∞
   70          42.0               0.25                           170
   80          49.2               0.48                           100
  100          62.4               0.90                            70
```

Below 60 eV the stop is limited by the threshold; above it, by selectivity that falls slowly. The reference sits at 40 eV for two other reasons: it is the energy at which ions do not mix chlorine into the ZAZ deeper than about a nanometre (Chapter 12), and it is low enough that the resist and SiGe sidewall passivation survive the step. Raising it to 60 eV would shorten the step from 36 s to 17 s, but it would put the ions at the ZrO₂ threshold, where a 20 eV drift in the edge ion energy would start etching the ZAZ.

---

## 4.3 Two Ways to Stop

A dielectric can be a stop layer in two ways.

```
Threshold stop (reference P2):  Cl₂/Ar, no BCl₃, E below E_th of ZrO₂
  + ZAZ is not etched at all; no deposition on it
  + Chemistry is simple: TiN → TiCl₄
  − No boron passivation of the SiGe sidewall at the foot (Chapter 10: +1.2 nm notch)
  − Cl uptake and fluorine memory reach an unprotected ZAZ surface

Deposition stop:  BCl₃/Cl₂ below the etch–deposition transition (< 55 eV)
  + ZAZ gains a BₓClᵧ film (≈ 0.5 nm in 20 s) and is protected; B passivates the SiGe foot
  + Selectivity formally infinite; ZAZ cannot be consumed
  − The BₓClᵧ film is hygroscopic; the O₂ strip turns it into B₂O₃, which the hot clear
    must remove first (adds ≈ 3 s to P4 and a risk of non-uniform removal)
  − Film thickness depends on the BCl₃ fraction and on wall condition
```

The deposition stop is the more conservative regarding the dielectric and the more demanding regarding everything that follows. The reference uses the threshold stop and keeps the deposition stop as a fallback if the foot notch exceeds 5 nm (Chapter 10).

---

### 4.3.1 The Breakthrough

The SiGe overetch is HBr/O₂ (Book #32). It leaves the 5 nm TiN covered by 1.0–1.5 nm of TiOₓNᵧ, which Cl₂ does not etch (the same oxide that Book #32 removes with a BCl₃ breakthrough before the TiN etch-back). P2 therefore starts with a breakthrough of 6 s in BCl₃/Ar at 70 eV, which removes the oxide at about 12 nm/min. It acts only on TiOₓ lying on TiN; no ZAZ is exposed during it, so the breakthrough costs nothing in dielectric loss. If the TiN is thin or pinholed, the breakthrough can reach the ZAZ at those sites, where a 70 eV BCl₃ plasma etches tetragonal ZrO₂ at 0.8 nm/min: a 6 s breakthrough then removes 0.08 nm. That is within the budget but takes 27% of it.

---

## 4.4 The Selectivity Budgets of the Clear

The hot clear P4 acts with the plate as its own mask (Chapter 7). Three films limit it.

### 4.4.1 W: the Strap

```
Plate sheet resistance specification:  R_s ≤ 4.0 Ω/□
  1/R_s = 1/R_W + 1/133 + 1/500  (SiGe, TiN)  →  R_W ≤ 4.16 Ω/□
  t_W ≥ 15×10⁻⁸ Ω·m / 4.16 Ω = 36.1 nm
  W loss allowed:   40 − 36.1 = 3.9 nm nominal;  ≤ 2.7 nm with the thickness tolerance (−3%)

Budget (reference):
  Strip oxidation   WOₓ 2.5 nm consumes 2.5 / 3.4 = 0.74 nm of W  (Pilling–Bedworth 3.4)
  P4 hot clear      2.4 nm/min × 37.8 s = 1.5 nm
  Total             2.3 nm   ≤ 2.7 nm   margin 0.4 nm
```

The selectivity ZrO₂:W required for the P4 step: remaining allowance 2.7 − 0.74 = 1.96 nm over 37.8 s requires W ≤ 3.1 nm/min, so S ≥ 12/3.1 = 3.9. The reference has 5.0.

### 4.4.2 SiN: the Landing Film

```
P4:  overetch exposure of SiN:  37.8 − 28 = 9.8 s  at 4 nm/min  →  0.65 nm
R0:  overetch exposure:         31 s               at 8 nm/min  →  4.1 nm
Specification ≤ 15 nm; the hot route uses 4% of it
```

### 4.4.3 TiOₓ: the Shell

The TiN sidewall of the plate edge is oxidized to a TiOₓ shell by the strip. In BCl₃ at 250 °C the shell is etched chemically at about 2.0 nm/min. TiN itself, once exposed, is attacked laterally at 70 nm/min. The shell must outlast the step with a margin:

```
Shell 1.8 nm → life 54 s;  step 37.8 s;  margin 1.43×
  Shell (nm)    Life (s)    Margin    Outcome
  ─────────────────────────────────────────────────────────────
   1.2            36         0.95      breach at 36 s → notch (70 nm/min × 2 s) ≈ 2 nm
   1.5            45         1.19      survives; margin small
   1.8            54         1.43      reference
   2.2            66         1.75      survives; thicker WOₓ on the W top (Chapter 7)
Shell required for a 1.3× margin:   1.3 × 37.8 s × 2.0 nm/min / 60 = 1.64 nm
```

The shell is both a protection and a budget item. A thicker shell protects the TiN longer, but it comes from a longer or hotter strip that also thickens the WOₓ on the strap and consumes more W.

---

## 4.5 The Case for Early Removal

The four ways of clearing a ZAZ differ in what the film is when they act. The numbers of Chapters 2 and 3 can be put side by side:

```
                              E edge          R0 integrated    R1 hot (P4)     T thermal
Film state                    amorphous       tetragonal       tetragonal      amorphous
Rate (nm/min or per cycle)    3.7 (flux ×0.25) 6                12              0.07/cycle
Overetch needed (z = 6.4)     19% (σ = 3%)    51% (σ_g = 8%)   32% (σ_g = 5%)  13% (σ = 2%) 
Reference overetch            30%             50%              35%             —
```

The advantage of the amorphous film is the absence of the grain tail: the overetch needed falls from 51% to 19%. The advantage of heat is partial: σ_g drops from 8% to 5% and the overetch from 51% to 32%. Neither removes the tail; only removing the film before it crystallizes does. This is why the edge etch is placed at step 9a and why the trim is placed before the top electrode: those are the only points at which the ZAZ can be etched without grains.

The reasons the periphery clear cannot move earlier are in Chapter 1: it needs the plate as its mask, and resist over the free-standing forest would infiltrate the 13 nm channels. The clear must therefore be done on crystalline film, and its tail must be controlled by the hot chuck and the ALE finish.

---

## 4.6 First-Pass Route Comparison

The five routes of module P, all acting after the SiGe over-etch, compared on the quantities of this chapter. Chapter 16 adds cost.

```
Route                  Steps after SiGe OE            Plasma / bake time    Thermal or wet step        SiN loss
───────────────────────────────────────────────────────────────────────────────────────────────────────────────
R0  integrated         HK step (BCl₃/Cl₂, 60 °C)       93 s                  —                          4.1 nm
R1  strip-then-clear   P2 + strip + P4 (hot)           42 + 60 + 38 s        —                          0.65 nm
R2  R1 + ALE finish    P2 + strip + P4 to 1 nm + ALE   42 + 60 + 23 s        29 cycles (4.8 min)        ≈ 0.2 nm
R3  all-thermal        P2 + strip + ALE                42 + 60 s             158 cycles (26 min)        ≈ 0
R4  hybrid dry + wet   P2 + strip + P4 to 1 nm + HF    42 + 60 + 23 s        wet 6.5 min (0.2 nm/min)   ≈ 13 nm

Route                  W loss     TiN notch / undercut           Residue tail                  Resist used
───────────────────────────────────────────────────────────────────────────────────────────────────────────────
R0  integrated         0          4.2 nm TiN notch               OE 50%, σ_g 8%; veils          218 nm
R1  strip-then-clear   2.3 nm     ≈ 2 nm (shell); 11 nm (1.0)   OE 35%, σ_g 5%; no veils       ≈ 152 nm
R2  R1 + ALE finish    1.7 nm     ≈ 2 nm; undercut 1.3 nm       ALE clears grains uniformly    ≈ 152 nm
R3  all-thermal        0.7 nm     ≈ 2 nm; undercut 7 nm         uniform; no ion dose            ≈ 152 nm
R4  hybrid dry + wet   1.7 nm     ≈ 2 nm; undercut 1.3 nm       isotropic; slow on tetragonal   ≈ 152 nm
```

Three things stand out. The strip-then-clear route (R1) trades 2.3 nm of tungsten and a shell margin for a 6× smaller SiN loss, no veils, and a lower overetch. The ALE finish (R2) buys the last decade of residue tail for 4.8 minutes of reactor time, and the all-thermal route (R3) only makes sense in a batch tool (Chapter 6). The hybrid wet route (R4) is dominated by the wet step, which at the tetragonal rate of 0.2 nm/min takes 6.5 minutes and costs 13 nm of SiN: its price is a nitride loss at 87% of the 15 nm limit.

---

## Summary and Key Takeaways

1. **One film, ten rows.** The same ZAZ is a target at the edge, a stop under the conductor etch, a mask-protected layer under the plate, and a wall coating; each needs its own selectivity.

2. **The stop requires S ≥ 18.** At 100% TiN overetch and a 7.8% clearing-time spread, the fastest site sees 5.4 nm of TiN-equivalent overetch against a 0.3 nm loss budget.

3. **Cl₂/Ar at 40 eV stops with a margin of 6–10.** Below the ZrO₂ threshold nothing is etched; the loss is surface modification, 0.03–0.05 nm.

4. **A deposition stop is the fallback.** BCl₃ below 55 eV puts a boron film on the ZAZ; it is conservative for the dielectric and heavier for the strip and the clear.

5. **The clear has three budgets.** W: ≤ 2.7 nm and S ≥ 3.9; SiN: ≤ 15 nm (0.65 nm used); shell: ≥ 1.64 nm for a 1.3× margin.

6. **Only early removal avoids the grain tail.** Amorphous film clears with 19% overetch against 51%; heat reduces the tail to 32% but does not remove it.

---

## Study Questions

1. Recompute the stop requirement S if the TiN is 6 nm ± 0.3 nm and the overetch is lowered to 70%, with the same rate non-uniformity. What ZAZ loss does the measured selectivity of 110 give?

2. Compute TiN:ZrO₂ at 150 eV and at 250 eV with the model of Section 4.2.3 (ZrO₂ at 0.3× the BCl₃/Cl₂ values of Chapter 3, TiN from the yield model with K = 3.9 nm/s). Does the requirement S ≥ 18 constrain the ion energy of the stop, and what does?

3. The breakthrough of Section 4.3.1 runs 6 s at 70 eV on a wafer where 0.5% of the TiN area is pinholed. How much ZAZ is removed at the pinholes, and what fraction of the 0.3 nm budget does that consume? Is the average affected?

4. Recompute the W budget if the strap is 38 nm thick and its resistivity is 16 µΩ·cm. What is the allowed W loss, and does the reference route fit?

5. The strip produces a 1.5 nm shell on one lot and the P4 step runs 42 s because of a slow clear. Compute the margin. If the shell were only 1.2 nm, compute the breach time and the TiN notch at 70 nm/min.

6. Using the table of Section 4.6, rank the five routes by SiN loss, by W loss, and by reactor time per wafer. Which route would you choose for a product whose SiN budget is 5 nm and whose strap cannot lose more than 1.0 nm?

---

**Next Chapter:** [Chapter 5: Edge & Bevel Etch Chambers](./05-edge-bevel-etch-chambers.md)

---

**Chapter 4 Development Status:** Complete  
**Version:** 1.0
