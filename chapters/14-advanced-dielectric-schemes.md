# Chapter 14: Advanced Schemes — Higher-k Films, Area-Selective Deposition, 4F² & 3D DRAM

## Overview

The reference process clears a zirconia laminate from a flat periphery next to a stacked capacitor array. Each part of that sentence is changing. The dielectric is moving toward films with higher permittivity, some of which etch more easily than ZrO₂ and some of which hardly etch at all. Area-selective deposition promises a dielectric that is never deposited where it is not wanted, so that nothing has to be cleared. Atomic-layer etching is being considered not only for clearing the periphery but for trimming the capacitor dielectric itself. And the capacitor is changing shape: 4F² vertical-channel cells shrink the array, and 3D DRAM turns the capacitor on its side and stacks it in tiers, where the dielectric must be removed from vertical slits and recessed laterally into cavities, problems that a directional plasma cannot touch.

This chapter takes each of these in turn, asks what it does to the dielectric clear, and estimates the numbers that decide whether it is practical.

**Learning Objectives:**
- Predict how TiO₂, SrTiO₃, Nb₂O₅-containing, HfO₂–ZrO₂, and rare-earth-doped dielectrics behave in the dielectric clear and in the later contact etch
- Explain the chlorinate-and-rinse approach for dielectrics with involatile cations
- Evaluate area-selective deposition of the capacitor dielectric, including its failure modes inside the array
- Estimate the capacitance gain and the risks of ALE trimming of the capacitor dielectric
- Describe the dielectric-removal steps of 4F² and 3D DRAM and why isotropic, highly selective ALE is central to them
- Estimate recess uniformity and precursor transport in a 3D DRAM slit

---

## 14.1 Higher-k Dielectrics and How They Etch

### 14.1.1 The Candidates

```
Dielectrics beyond ZAZ (illustrative):
  Film                        k          Electrode      Status
  ──────────────────────────────────────────────────────────────────────
  ZrO₂/Al₂O₃/ZrO₂ (ZAZ)        ≈ 43 eff   TiN            reference
  HfO₂–ZrO₂ (HZO, Zr-rich,    45–55      TiN            in development;
  antiferroelectric-like)                               field-induced high k
  ZrO₂ with Nb₂O₅ insertion   ≈ 45–50    TiN            lower leakage than Al₂O₃
                                                        insertion at same EOT
  TiO₂ (rutile)               80–100     Ru / RuO₂      needs a rutile template
  SrTiO₃ (STO)                100–200    Ru, SrRuO₃     needs ≥ 600 °C
                                                        crystallization
  Rare-earth-doped ZrO₂       ≈ 45       TiN            dopant stabilizes the
  (La, Y)                                               tetragonal phase
```

### 14.1.2 How Each Clears

```
Behaviour in the dielectric clear and the contact etch (illustrative):

Film            Cation halide        D1-type clear            Residue under
                volatility                                    fluorocarbon contact
─────────────────────────────────────────────────────────────────────────────────────
HZO             HfCl₄ ≈ ZrCl₄        ≈ ZrO₂; Hf I lines for    stops (HfF₄ involatile)
                                     endpoint
Nb₂O₅ insert    NbCl₅, NbF₅ both     faster; no Al marker,     Nb part etches; ZrO₂
                volatile             Nb I lines instead        part still stops
TiO₂            TiCl₄ very volatile; fast in BCl₃/Cl₂;          slows but does not stop
                TiF₄ subl. 284 °C    selectivity to SiN > 5    (partial TiF₄ volatility)
SrTiO₃          SrCl₂ bp 1250 °C,    Ti leaves; Sr stays as    SrF₂ stops completely
                SrF₂ 2460 °C         SrCl₂ crust: dry clear
                                     stalls
La, Y dopants   LaCl₃, YCl₃          dopant left at ≈ 10¹³ /cm² minor; counted as metal
(≈ 5%)          involatile           on the SiN after clearing contamination
```

The higher-k films divide into those that are easier than ZrO₂ (TiO₂, niobium-containing films), those that are about the same (HZO), and those that cannot be cleared by any purely dry process (strontium titanate, and to a lesser extent rare-earth dopants).

### 14.1.3 Chlorinate and Rinse

SrCl₂ does not volatilize, but it dissolves readily in water. A strontium-containing dielectric can be cleared by converting it to chlorides in the plasma and dissolving the result:

```
Chlorinate-and-rinse clear for STO (illustrative):
  Plasma    BCl₃/Cl₂, 250 °C: Ti leaves as TiCl₄; Sr is converted to SrCl₂
            in a crust ≈ 1–2 nm thick that stops further chlorination
  Rinse     DI water or dilute HCl: dissolves SrCl₂
  Repeat    2–4 cycles for ≈ 8–10 nm of STO
  Issues    each rinse is a wafer exit and re-entry; Cl and water at the
            plate edge (Chapter 11) every cycle; Sr is a contamination
            concern for other tools
```

The same idea, a dry step that converts the film into a soluble compound followed by a wet step, is a general recipe for any dielectric whose cation has no volatile halide. It is the high-k analogue of the damage-enhanced hybrid of Chapter 4.

### 14.1.4 Ru Electrodes

TiO₂ and STO need noble-metal or conductive-oxide electrodes. Ruthenium is etched with O₂/Cl₂ plasmas, forming volatile RuO₄. In the plate etch, the Ru top electrode replaces the TE TiN step; in the dielectric clear, the exposed Ru sidewall at the plate edge is attacked by any oxygen in the chemistry, and RuO₄, which is toxic, appears in the exhaust. The dielectric-clear chemistry for Ru-electrode capacitors must be oxygen-free at the edge, which D1 already is.

---

## 14.2 Area-Selective Deposition

### 14.2.1 The Idea

If the ZAZ never grows on the periphery, the dielectric clear is unnecessary. Area-selective deposition (ASD) uses an inhibitor, a small molecule or a self-assembled monolayer that binds to one surface and blocks ALD nucleation there, while the film grows normally elsewhere:

```
ASD of ZrO₂ (illustrative):
  Growth surface    TiN (pillars)
  Non-growth        SiN (periphery), via an aminosilane or alkylsilane
                    inhibitor that reacts with Si–OH/Si–NH sites
  Selectivity       nucleation delayed by 20–40 cycles on inhibited SiN
  ZAZ cycles        ≈ 62 (29 + 4 + 29)
```

### 14.2.2 Why It Is Hard Here

```
Obstacles to ASD of the capacitor dielectric (illustrative):
  1. Cycles     62 cycles exceed the 20–40 cycle selectivity window;
                nuclei appear on the periphery after ≈ 30 cycles
  2. Defects    every nucleus on the periphery is a residue grain under a
                possible contact: the tail problem of Chapter 10 returns
                with no overetch to beat it
  3. The array  the support lattice is SiN. An inhibitor that blocks ZrO₂ on
                periphery SiN also blocks it on the supports, including the
                line where each support meets a pillar. A nucleation gap of
                a nanometre at that line lets the TE TiN touch the storage
                node: a short in every cell along the support
```

The third obstacle is decisive for stacked capacitors with nitride supports: an inhibitor selective between TiN and SiN cannot distinguish periphery nitride from support nitride. The inhibitor would have to be applied to the periphery only, which needs a patterning step, and at that point the dielectric clear has merely moved.

### 14.2.3 ASD Plus ALE

The usual remedy for ASD's limited selectivity is to alternate deposition with a short etch that removes the nuclei from the non-growth surface faster than it thins the film on the growth surface, then re-dose the inhibitor:

```
Deposition–etch–deposition with inhibitor (illustrative):
  25 ALD cycles → 4 ALE cycles (≈ 0.4 nm) → inhibitor re-dose → repeat
  The ALE removes nuclei (thin, discontinuous) and thins the growing film
  equally; net growth slows by ≈ 15%
```

This could reduce the periphery to a thin, sparse layer of nuclei that a short D2 clears, and might shorten the clear. It does not solve the support problem. ASD is more promising in geometries where the growth and non-growth surfaces are different materials everywhere, such as some 3D DRAM schemes (Section 14.5).

---

## 14.3 ALE Trimming of the Capacitor Dielectric

### 14.3.1 Crystallize Thick, Trim Thin

ZrO₂ crystallizes into the high-k tetragonal phase more reliably when it is thicker; very thin films stay amorphous or crystallize poorly, with lower k. A capacitor dielectric could be deposited and crystallized thick, then thinned by isotropic thermal ALE inside the pillar forest before the TE is deposited:

```
Trim scenario (illustrative):
  Deposit and crystallize    ZAZ 6.0 nm, k_eff ≈ 45 (anneal before TE)
  Trim                       thermal ALE removes 1.0 nm uniformly from the
                             outer ZrO₂ (≈ 20 cycles at 0.05 nm)
  Result                     5.0 nm, k_eff ≈ 45 if the phase is retained
  EOT                        3.9 × 5.0 / 45 = 0.43 nm (vs 0.50)
  C_s                        8.6 × 0.50 / 0.43 ≈ 10.0 fF (+ 16%)
```

### 14.3.2 Risks

```
Risks of dielectric trimming (illustrative):
  Grain boundaries     thermal ALE attacks boundaries faster (Chapter 4):
                       a 1 nm average trim may thin boundaries by 1.5–2 nm,
                       creating leakage hot spots
  Conformality         the trim must be uniform from the pillar top to the
                       bottom of a 1.4 µm, 17 nm-gap forest: a transport
                       question (Section 14.5.3)
  Anneal before TE     crystallizing without the TE cap favours the
                       monoclinic phase (lower k) unless a dopant or
                       template holds it tetragonal
  Surface state        F and Al from the trim chemistry at the ZAZ/TE
                       interface change the barrier and the leakage
```

Trimming is a research topic. It would turn the dielectric etch from a module that must not touch the array into one that deliberately etches every capacitor, and every risk of Chapters 10 and 13 would apply to the 98.6% of the film that matters.

---

## 14.4 4F² Vertical-Channel DRAM

In a 4F² cell, the access transistor stands vertically under the capacitor and the bit line is buried below it. The cell area falls from 6F² to 4F², and the capacitor still sits above, now on a tighter pitch:

```
4F² capacitor array (illustrative, F = 14 nm):
  Cell area            784 nm²
  Storage-node pitch   ≈ 32 nm (square or hexagonal)
  Capacitor            taller or double-sided to hold ≈ 8 fF on less area
  Dielectric           same family; thinner EOT pursued
```

For the dielectric clear, a 4F² array changes little in kind. The periphery and the plate edge are the same, and the chemistry is the same. What changes is the value of area: plate overlap and edge damage reach become a larger fraction of a smaller array block, so the edge chemistry of Chapters 11 and 13 matters more, and a 0.4 µm overlap becomes a requirement rather than an option.

---

## 14.5 3D DRAM

### 14.5.1 The Structure

In 3D DRAM, cells are stacked in tiers. Each tier is a horizontal layer of silicon channel with a lateral transistor and a lateral capacitor extending sideways from it. The storage node is a horizontal TiN tube or cylinder in a cavity in the stack; the dielectric and the plate are deposited into those cavities through vertical slits or holes that cut through all the tiers.

```
3D DRAM lateral capacitor (schematic, not to scale):

   slit │  tier n   ═══ transistor ═══[ SN TiN ⊃ ZAZ ⊃ plate ]═══
        │  SiO₂     ─────────────────────────────────────────────
        │  tier n−1 ═══ transistor ═══[ SN TiN ⊃ ZAZ ⊃ plate ]═══
        │  ...      (tens to a hundred tiers; slit several µm deep)
```

### 14.5.2 Where the Dielectric Must Be Removed

```
Dielectric-removal steps in a 3D DRAM capacitor flow (illustrative):
  1. Slit walls          ZAZ deposited on the vertical slit walls (several µm
                         tall) must be removed where the plate must not be:
                         a vertical-face stringer problem that cannot be
                         left in place
  2. Lateral recess      the ZAZ must be recessed laterally into each tier's
                         cavity to a defined depth, so that the plate and
                         dielectric end at the same place in every tier
  3. Tier isolation      in schemes with per-tier plates, the dielectric
                         and plate must be cut between tiers along the slit
```

Every one of these is an isotropic, highly selective removal in a deep, narrow structure. The directional plasma clears of this book cannot do them. Thermal ALE can, and its weakness in the stacked capacitor, the isotropic undercut, becomes the purpose of the step.

### 14.5.3 Transport and Uniformity

```
Thermal-ALE transport into a slit (illustrative):
  Slit width 100 nm, depth 5 µm, cavity height 30 nm, lateral recess 50 nm
  Knudsen diffusivity D_K ≈ (d/3) v̄ ≈ (100 nm / 3) × 300 m/s ≈ 0.1 cm²/s
  Diffusion time to the slit bottom: L² / D_K ≈ (5 µm)² / 0.1 cm²/s ≈ 3 µs
  Saturation dose: every surface in the slit and cavities must be reached;
  the internal surface area per cm² of wafer is ≈ 50–100 cm² → precursor
  depletion, not diffusion, sets the pulse length
```

The molecules reach the bottom of the slit in microseconds. The pulse must be long enough to deliver a saturating dose to an internal surface area fifty to a hundred times the wafer area, and the purge long enough to remove the products from it. Cycle times stretch to tens of seconds per cycle even on a single wafer, and batch reactors become the natural choice.

```
Lateral recess uniformity (illustrative):
  Target recess               50 nm in every tier
  EPC                         0.05 nm (tetragonal) → 1000 cycles
  EPC tier-to-tier variation  ± 2% (temperature, dose)
  Recess range                ± 1 nm
  Phase variation             a monoclinic-rich tier recesses ≈ 20% less
                              → the phase must be uniform tier to tier
```

The 3D DRAM dielectric recess is the most demanding application of high-k ALE now in view. It needs a self-limiting, isotropic, infinitely selective process with an EPC that does not depend on phase, and the thermal ALE chemistries of Chapter 4 do not yet meet the last requirement.

---

## 14.6 Where the Field Is Heading

```
Trends and their effect on the dielectric clear (illustrative):
  Trend                              Effect
  ────────────────────────────────────────────────────────────────────────
  Higher-k films                      easier (Ti, Nb) or harder (Sr, La) to
                                      clear; chlorinate-and-rinse for Sr
  ASD                                 cannot replace the clear in stacked
                                      capacitors with SiN supports; may
                                      thin what must be cleared
  ALE everywhere                      D2-type finishing becomes routine;
                                      thermal ALE becomes essential in 3D
  Smaller overlap (4F², cost)         edge chemistry and damage reach
                                      become yield-limiting
  3D DRAM                             directional clears give way to
                                      isotropic lateral recess
```

---

## Summary and Key Takeaways

1. **Higher-k films split into easier and harder.** TiO₂ and Nb-containing films clear faster than ZrO₂; HZO is similar; SrTiO₃ and rare-earth dopants leave involatile chlorides.

2. **Chlorinate and rinse handles involatile cations.** Convert to soluble chlorides in the plasma, dissolve them in water, repeat.

3. **ASD cannot remove the clear in stacked capacitors.** Its selectivity window is too short for ZAZ, and an inhibitor selective to SiN would starve the support–pillar junctions and short every cell.

4. **ALE trimming could add about 16% capacitance** by thinning a crystallized film, at the cost of etching every capacitor's dielectric.

5. **4F² keeps the problem and tightens the edge.** Overlap and damage reach become a larger share of a smaller array.

6. **3D DRAM makes isotropic, selective ALE essential.** Lateral recess to ± 1 nm over many tiers needs an EPC independent of phase and doses that saturate large internal areas.

---

## Study Questions

1. A TiO₂ dielectric (8 nm, rutile) replaces ZAZ. If TiO₂ etches at 30 nm/min in D1 and SiN at 3 nm/min, compute the clear time, the overetch for σ_g = 8% and z = 6.4, and the SiN loss.

2. For the chlorinate-and-rinse STO clear, estimate the number of cycles for 10 nm of STO if each plasma step converts 2 nm to a SrCl₂ crust and removes the Ti. List the edge risks of each rinse.

3. An inhibitor delays ZrO₂ nucleation on SiN by 35 cycles. With 62 ZAZ cycles, estimate the periphery thickness if growth on SiN after nucleation proceeds at the normal rate. How many deposition–etch–deposition loops would keep the periphery below one monolayer?

4. Recompute the trim scenario for a trim of 0.5 nm and for one of 1.5 nm. At what trim does the grain-boundary thinning of Section 14.3.2 reach 50% of the remaining film thickness?

5. For the 3D DRAM slit of Section 14.5.3, estimate the internal surface area per cm² of wafer for 64 tiers with cavities spaced 0.2 µm along the slit. How many DMAC molecules per cm² of wafer are needed per saturating pulse at 4 × 10¹⁴ sites/cm²?

6. Why is phase uniformity tier-to-tier a requirement for thermal-ALE lateral recess but not for the D1 periphery clear?

---

**Next Chapter:** [Chapter 15: Metrology, Inspection & Advanced Process Control](./15-metrology-inspection-apc.md)

---

**Chapter 14 Development Status:** Complete  
**Version:** 1.0
