# Chapter 11: The Two Edges — Plate Edge & Wafer Bevel

## Overview

Wherever the dielectric is removed, it ends. Module 2 ends it at the edge of every plate island, about 32 times per die. Module 1 ends it in a ring around the wafer at a radius of 148.8 mm. In both places, an edge of the capacitor dielectric is left exposed to the plasma that cut it, to the treatments that follow, to the air, and to the film deposited over it next. Edges are where etch chemistry enters a film, where films with different stresses meet, and where defects begin.

The two edges have little in common except their material. The plate edge is a few hundred nanometres tall, lies 1.5 µm from the nearest active capacitor, and is covered within hours by the inter-layer dielectric. The bevel boundary is a ring 0.3 mm wide on a wafer surface that curves away towards the apex, lies 1.8 mm outside the last die, and is covered within hours by the SiGe plate fill. This chapter describes the structure each etch leaves, the chemistry that enters each edge, how far it travels, what each edge does to the films deposited over it, and the treatments and test structures that keep the edges harmless.

**Learning Objectives:**
- Sketch the plate-edge structure after module 2, including the TE TiN notch and the exposed ZAZ edge
- Estimate the lateral etch of the TE TiN and the ZAZ at the plate edge in the main step and the finish
- Estimate how far chlorine and boron travel into the ZAZ from an exposed edge during later anneals
- Explain why the plate edge is an edge of an unbiased dielectric, and where that stops being true
- Describe the boundary staircase left by module 1, the boron ring in its transition zone, and the adhesion of later films over it
- Specify treatments and test structures for both edges

---

## 11.1 The Plate Edge After Module 2

### 11.1.1 Structure

```
Plate edge after the finish, before the strip (not to scale):

           resist (≈ 310 nm)
         ┌───────────────┐
         │      W 40     │
         │               │
         │  SiGe:B 150   │   ← SiOₓBrᵧ sidewall passivation (Book #32)
         │               │
         ├──────────┐    │   ← TE TiN notch: recessed ≈ 1.3 nm under the
         │  TE TiN 5│ ◄──┘      SiGe
   ──────┴──────────┴─╮       ← ZAZ edge: exposed face 5.5 nm tall; lateral
   ZAZ 5.5 nm         │          etch ≈ 0.4 nm; Cl and B in the first nm
   ═══════════════════╧═══════════════════════════════  top SiN (−0.4 nm)
          array side          periphery side

Distance from the plate edge to the last dummy pillar row:   1.5 µm
Distance to the nearest active capacitor:                    ≈ 1.6 µm
```

### 11.1.2 Lateral Etch at the Edge

```
Lateral loss at the plate edge (illustrative):

                          Main step (45 s,     ALE finish (36      Total
                          150 eV)              cycles)
  ────────────────────────────────────────────────────────────────────────
  TE TiN notch            ≈ 0.6 nm             ≈ 0.7 nm            ≈ 1.3 nm
                          (ions at grazing     (BCl₃ dose borates
                          incidence; Cl        the TiN face;
                          radicals)            0.02 nm/cycle)
  ZAZ edge recess         ≈ 0.05 nm            ≈ 0.35 nm           ≈ 0.4 nm
                          (vertical face sees  (dose modifies the
                          few ions)            face; weak removal)
  SiGe sidewall           < 1 nm               < 0.2 nm            < 1 nm

Continuous route (93 s at 150 eV, Book #32):
  TE TiN notch ≈ 4 nm;  ZAZ edge recess ≈ 0.2 nm
```

The TE TiN notches because it etches eight times faster than ZrO₂ in the main step (Chapter 3) and ten times faster in the ALE (Chapter 4), and because chlorine radicals reach its edge from the side. The notch is small in the reference because the main step is short; it was 4 nm in the continuous route because the TE edge was exposed for the whole 93 s step.

### 11.1.3 Why the Notch Matters

A 1.3 nm notch under 150 nm of SiGe is a slot that the inter-layer dielectric must fill. A 4 nm notch is a slot that it may not: deposition with poor conformality leaves a void there, which traps moisture and chlorine and becomes a corrosion site for the TE TiN. The notch is also where the TE TiN surface, its chlorine, and the boron from the main step are closest to the ZAZ edge.

---

## 11.2 Chemistry Entering the ZAZ Edge

### 11.2.1 What Arrives

```
Exposed ZAZ edge face after the finish (illustrative):
  Cl    3–8 at% in the outer 1 nm (from the main step and the BCl₃ doses)
  B     2–5 at% in the outer 1 nm
  H     from the O₂/H₂O strip and later films
After the O₂/H₂O strip and treatment:
  Cl    ≤ 3 at% (specification)
  B     ≈ 1–2 at%
```

### 11.2.2 How Far It Travels

Chlorine and boron diffuse into polycrystalline ZrO₂ mainly along grain boundaries. At process temperatures in the etch chamber (60 °C) they move a few ångströms. In the later anneals of the back-end, they move further:

```
Diffusion length along ZrO₂ grain boundaries (illustrative):
  L = √(D t)

  Step                         T (°C)   t        D_gb (cm²/s)    L
  ───────────────────────────────────────────────────────────────────
  Etch, strip                  60–250   minutes  ≤ 10⁻¹⁸          < 1 nm
  ILD deposition               400      1 h      ≈ 10⁻¹⁵          ≈ 20 nm
  Back-end anneals (total)     400–420  ≈ 5 h    ≈ 10⁻¹⁵          ≈ 40 nm
  Forming-gas alloy            420      0.5 h    ≈ 10⁻¹⁵          ≈ 13 nm
  ───────────────────────────────────────────────────────────────────
  Cumulative                                                     ≈ 50 nm
```

Fifty nanometres is far from the 1.6 µm to the nearest active capacitor. Edge chemistry stays at the edge.

### 11.2.3 An Unbiased Edge

At the plate edge, the ZAZ lies on SiN, with the TE TiN above it and **no bottom electrode beneath it**. In operation, the plate is at 0.55 V and the SiN and mold oxide below the ZAZ are insulators: there is no field across the ZAZ at the plate edge, and no current path through it. A damaged ZAZ edge face on SiN is electrically inert.

This changes in three cases:

1. **Dummy rows too close.** If the plate edge lies within the reach of edge chemistry (≈ 50 nm) of a dummy or active pillar, the damaged ZAZ is biased. Design rules keep 1.5 µm.
2. **Edge-intensive test structures.** Test arrays deliberately place plate edges a few hundred nanometres from active capacitors to measure edge sensitivity (Section 11.6).
3. **Charging during the etch.** During the plate etch, the plate and the storage nodes are connected to the plasma through the plate edge and the substrate, and the ZAZ *is* biased, by the plasma (Chapter 13 and Book #32, Chapter 13).

---

## 11.3 Corrosion at the Plate Edge

The plate edge carries TiN, W, and SiGe within a few nanometres of boron and chlorine. In air, BOₓClᵧ hydrolyses:

```
BOₓClᵧ + H₂O → H₃BO₃ + HCl
HCl + TiN (notch face)  → TiOₓClᵧ, Ti dissolution under moisture
HCl + W (top, sidewall) → WOₓClᵧ; W oxide growth at the edge
```

```
Queue-time sensitivity (illustrative, plate edge, 45% RH fab air):

  Time from finish to strip     TE notch growth     W edge oxide
  ──────────────────────────────────────────────────────────────
  5 min (vacuum transfer)       none                none
  1 h (air)                     ≈ 0.5 nm            ≈ 1 nm
  8 h (air)                     ≈ 2 nm              ≈ 3 nm
```

The reference strips on the same platform within five minutes, under vacuum, and treats the surface with water at 250 °C in the strip chamber, where the HCl leaves through the pump rather than staying on the plate edge.

---

## 11.4 The Bevel Boundary After Module 1

### 11.4.1 The Staircase

The bevel plasma ends the ZAZ where ions stop reaching (the plasma edge in the PEZ gap) and the TE TiN where chlorine radicals fall below their etch threshold (the radical decay against the centre purge) (Chapter 7):

```
Front boundary after module 1 (radial profile, not to scale):

  film thickness
     ▲
  TE │▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓╲
     │                 ╲ TE TiN taper (radical creep)
  ZAZ│░░░░░░░░░░░░░░░░░░░░░░░░░░░╲
     │                            ╲ ZAZ taper (ion edge)
     │                             ╲
  SiN│═════════════════════════════════════════════════
     └──────────┬──────────┬──────────┬──────────┬──────► r (mm)
             148.4      148.6      148.8      149.0

  TE TiN 90% → 10%:   148.50 → 148.65 mm
  ZAZ 90% → 10%:      148.70 → 148.90 mm
  Bare ZAZ ring (no TE above): 148.65 → 148.80 mm, ≈ 0.15 mm wide
```

Inside 148.5 mm, both films are intact. Outside 148.9 mm, both are gone. In between is a staircase about 0.4 mm wide, within the ≤ 0.3 mm specification for each film's transition but wider for the pair.

### 11.4.2 The Boron Ring

In the ZAZ taper, the ion energy falls from about 85 eV to zero over 0.2 mm. Somewhere in that zone it passes through the etch–deposition transition, E₀ ≈ 60 eV (Chapter 3). There, the BCl₃ step does not etch: it deposits BₓClᵧ.

```
Boron ring (illustrative, after B2):
  Location        r ≈ 148.70–148.75 mm (where 0 < E < E₀)
  Thickness       1–3 nm BₓClᵧ / BOₓClᵧ over partly thinned ZAZ
  After B3 (O₂/N₂)  converted to B₂O₃-rich film, 1–2 nm
  Visible as      a faint haze ring in edge inspection
```

The B3 oxygen step converts the boron film to an oxide but cannot remove it at 60 °C. The reference relies on the pre-clean before the SiGe fill: a deionized-water rinse and a dilute HF dip, which dissolve B₂O₃ and boric acid. Wafers that wait between module 1 and the pre-clean in humid air develop boric acid crystals on the ring, a particle source; the queue time is limited to 24 h.

### 11.4.3 What the SiGe Fill Sees

```
Surfaces under the SiGe fill at the edge (after module 1 and pre-clean):

  r < 148.5 mm          TE TiN (as everywhere on the front)
  148.65–148.8 mm       bare ZAZ (TE removed, ZAZ intact)
  148.7–148.9 mm        thinned ZAZ, formerly boron-rich
  r > 148.9 mm, apex,   SiN, oxide, bare Si (films removed)
  backside ring
```

SiGe nucleates differently on each. On TiN and on bare silicon it nucleates readily; on ZrO₂ and on SiN, after a delay. The result is a SiGe film whose thickness and grain structure change across the staircase. Over it, the W strap is deposited by PVD with its own edge exclusion (its shield stops it at about r = 148 mm), so W does not reach the staircase.

### 11.4.4 Adhesion and Flakes

A film flakes when its stored elastic energy per unit area exceeds the adhesion energy of the interface beneath it:

```
G = σ² h / (2 E')

SiGe:B, 150 nm, σ ≈ 100 MPa, E' ≈ 150 GPa:   G ≈ 0.005 J/m²
(W stops at r ≈ 148 mm; not over the staircase)

Interface adhesion energy (illustrative):
  SiGe on TiN, on clean Si                    > 2 J/m²
  SiGe on clean ZrO₂ or SiN                   ≈ 1 J/m²
  SiGe on boron-oxide-contaminated ZrO₂       ≈ 0.05–0.2 J/m²
```

SiGe alone does not have enough stored energy to peel even from a contaminated interface. The danger comes later. The plate etch removes the plate from this region (the plate resist has a 1.5 mm edge-bead removal, so the front ring is etched as periphery), but the SiGe on the apex and backside, where no plate etch reaches, remains until a later bevel clean, and over the subsequent anneals (thermal mismatch adds stress at each cycle) a weakly adhered SiGe ring on a boron-contaminated ZrO₂ taper is where flaking begins. The two protections are the pre-clean, which removes the boron, and the transition width, which keeps the contaminated band narrow.

### 11.4.5 Module 2 Visits the Front Ring Again

Because the plate resist does not cover r > 148.5 mm, the plate etch and module 2 clear the front ring a second time: they remove the SiGe and any TE TiN or ZAZ left in the module 1 staircase, down to the SiN. Whatever the bevel step left on the **front** is removed by the periphery clear. The bevel step's own result matters for the **apex and backside**, which module 2 never reaches, and for the weeks between module 1 and module 2, when the staircase sits under the SiGe through the plate-fill anneal.

---

## 11.5 Treatments for Both Edges

```
Edge                Treatment                       Purpose
───────────────────────────────────────────────────────────────────────────────
Plate edge          In-situ transfer to strip,      Remove B and Cl from the ZAZ
                    ≤ 5 min                         edge and the TE notch before
                    O₂/H₂O remote plasma, 250 °C    air does; volatilize HCl
                    DIW/O₃ rinse                    Dissolve residual borate
                    No SC1                          TiN and W at the edge
Bevel boundary      B3 O₂/N₂ in the bevel tool      Convert BₓClᵧ to oxide
                    DIW + dilute HF pre-clean       Dissolve B₂O₃ before SiGe
                    before SiGe, ≤ 24 h queue
                    Bevel VPD and edge inspection   Verify Zr removal and
                    (sample)                        haze-free ring
```

---

## 11.6 Edge Test Structures

```
Structure                         What it measures                    Where
──────────────────────────────────────────────────────────────────────────────────
Edge-intensive capacitor array    leakage and TDDB of capacitors      test chip,
(plate edge at 0.2, 0.5, 1.5 µm   whose ZAZ is within reach of the    scribe
from active capacitors)           edge chemistry; ratio to an
                                  array-centre structure
Plate-edge comb (long plate       TE notch depth and ILD voids by     scribe
perimeter on periphery SiN)       TEM; edge corrosion after
                                  controlled air exposure
Long-perimeter plate on SiN       Cl and B at the edge by STEM-EELS   TEM sample
                                  and atom-probe tomography
Bevel boundary                    boundary radius, staircase width,   every wafer
                                  haze ring (optical edge             (inspection);
                                  inspection); Zr by bevel VPD        sample (VPD)
```

The edge-intensive capacitor array is the device engineer's measure of edge damage. In the reference process, its leakage at 1.0 V is within 10% of the array-centre monitor for edge distances of 0.5 µm and above, and rises by about 40% at 0.2 µm, where the edge chemistry's reach of about 50 nm and the plate-etch charging of Chapter 13 overlap the outermost capacitors. The design rule of 1.5 µm leaves a large margin.

---

## Summary and Key Takeaways

1. **Each etch leaves an edge.** Module 2 leaves the ZAZ edge at every plate foot; module 1 leaves a ring at 148.8 mm.

2. **The short main step keeps the plate edge tight.** TE TiN notch ≈ 1.3 nm and ZAZ edge recess ≈ 0.4 nm, against ≈ 4 nm notch in the continuous route.

3. **Edge chemistry stays at the edge.** Cl and B travel about 50 nm along grain boundaries through the back-end anneals; the nearest active capacitor is 1.6 µm away.

4. **The plate edge is unbiased.** With no bottom electrode beneath it, the damaged ZAZ face carries no field, except in edge-intensive test structures and during the etch itself.

5. **The bevel boundary is a staircase with a boron ring.** TiN ends 0.15 mm inside the ZAZ; where the bevel ion energy crosses E₀, BCl₃ deposits instead of etching.

6. **Water and time are the treatments.** O₂/H₂O at 250 °C for the plate edge within five minutes; dilute HF before the SiGe fill for the bevel ring within a day.

---

## Study Questions

1. Estimate the TE TiN notch for a main step of 60 s and an ALE finish of 30 cycles, using the lateral rates implied in Section 11.1.2. How does it compare with the continuous route?

2. Using L = √(Dt) with D_gb = 10⁻¹⁵ cm²/s, how long an anneal at 400 °C would carry chlorine 1.5 µm from the plate edge? What does this say about the design rule?

3. A product places active capacitors 0.3 µm from the plate edge to save area. Using Section 11.6, estimate the leakage increase of the outermost capacitors. What would you change in module 2 to make this layout acceptable?

4. Explain why a boron ring forms in the ZAZ taper of the bevel boundary but not in the periphery clear of module 2. Where in module 2 might a similar ring appear?

5. A W film 40 nm thick with σ = 1.2 GPa (E' = 450 GPa) were deposited over the bevel staircase. Compute G and compare it with the adhesion energies in Section 11.4.4. What would you expect?

6. The queue time between module 2 and the strip rises to 2 h because of a platform fault. Using Section 11.3, estimate the TE notch and W edge oxide, and propose a disposition for the affected lots.

---

**Next Chapter:** [Chapter 12: In-Array Dielectric Trim by Thermal ALE](./12-in-array-dielectric-trim.md)

---

**Chapter 11 Development Status:** Complete  
**Version:** 1.0
