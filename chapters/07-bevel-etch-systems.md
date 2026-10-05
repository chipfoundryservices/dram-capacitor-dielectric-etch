# Chapter 7: Bevel Etch Systems for High-k Removal

## Overview

The bevel removal of module 1 is the only etch in this book with no mask and no pattern, and the only one that must etch the back of the wafer. Its job is to take 5 nm of TiN and 5.5 nm of partly crystallized ZAZ off a ring 1.2 mm wide on the front, off the apex, and off a ring 3 mm wide on the backside, leaving fewer than 10¹⁰ zirconium atoms per square centimetre, while not touching a single nanometre of the same films 0.2 mm further in. It does this in a **confined bevel plasma**: a ring of plasma wrapped around the wafer edge, held away from the front and back surfaces by insulating plates a fraction of a millimetre from the wafer.

This chapter describes the wafer edge as the bevel tool sees it, the hardware that confines the plasma, the physics that sets the boundary, the ion energies the bevel plasma can deliver and why they sit uncomfortably close to the etch–deposition transition of Chapter 3, the reference bevel recipe, and the sources of boundary error and residual zirconium. It closes with alternatives to a plasma bevel step.

**Learning Objectives:**
- Describe the geometry of a confined bevel-etch system and identify what sets the front and back boundaries
- Explain with Paschen's law why the plasma does not form in the exclusion gap
- Estimate how far radicals penetrate the exclusion gap against a centre purge
- Compute bevel etch rates from the model of Chapter 3 at the ion energies available at the bevel, and their sensitivity
- Design a bevel recipe for TiN and ZAZ, and estimate its overetch at the slowest location
- List the sources of boundary error, residual Zr, and particles

---

## 7.1 What Must Be Removed

```
Films at the edge before module 1 (Chapter 2, Section 2.6):

  Location             r (mm)          ZAZ (nm)     TE TiN (nm)   Underneath
  ─────────────────────────────────────────────────────────────────────────────
  Front ring           148.8–149.6     5.5          5.0           top SiN
  Front bevel facet    149.6–150       5.4          4.8           SiN, oxide, Si
  Apex                 150             5.2          4.5           Si, oxide
  Back bevel facet     150–149.6       4.5          3.5           oxide, SiN
  Backside ring        149.6–147.6     4.0 → 0.3    3.0 → 0.2     LPCVD SiN
  Backside             < 147.5         trace        trace         LPCVD SiN

Target: remove TiN and ZAZ for r ≥ 148.8 mm (front), the apex, and
r ≥ 147.0 mm (back). Keep everything for r < 148.6 mm (front).
```

The front boundary must be placed to ±0.1 mm because the last full die ends at about 147 mm and the plate overlap of edge dies lies close behind it, while a residual front ring of dielectric outside the boundary would be left under the plate fill without a pattern to remove it.

---

## 7.2 The Confined Bevel Plasma

### 7.2.1 Geometry

```
Cross-section of the bevel chamber at the wafer edge (not to scale):

                      gas in (centre purge N₂)
                              │
        ┌─────────────────────┴───────────────┐ ┌──────────────┐
        │   upper PEZ insulator (ceramic)     │ │ upper edge   │ (grounded)
        └─────────────────────────────────────┘ │ electrode    │
              ↕ 0.35 mm gap                 ░░░░└──────────────┘
   ════════════════════ wafer ═══════════════▒▒▒▒╮   ← annular plasma
                                            ░░░░╯    (process gas fed
        ┌──────────────────────────────┐  ↕0.4mm┌──────────────┐  at the edge)
        │ lower electrode / chuck      │ lower  │ lower edge   │
        │ (RF, 13.56 MHz), r = 146.5 mm│ PEZ    │ electrode    │
        └──────────────────────────────┘ ring   └──────────────┘

PEZ = plasma-exclusion zone
```

The wafer rests on a lower electrode smaller than itself, so its outer 3.5 mm overhang. An insulating **upper plasma-exclusion-zone (PEZ) plate** covers the front almost to the edge, separated from the wafer by 0.35 mm. A **lower PEZ ring** does the same on the backside between the lower electrode and the edge. Grounded upper and lower edge electrodes surround the edge. RF applied to the lower electrode drives a plasma in the annular volume around the bevel, at about 0.8 Torr.

### 7.2.2 Why the Plasma Stays Out of the Gaps

Breakdown of a gas between two surfaces depends on the product of pressure and gap (Paschen's law). The minimum breakdown voltage lies near pd ≈ 1 Torr·cm for Ar and N₂; far to the left of the minimum, the breakdown voltage rises steeply:

```
Upper PEZ gap:   p d = 0.8 Torr × 0.035 cm = 0.028 Torr·cm
Annular volume:  p d ≈ 0.8 Torr × 1 cm     = 0.8 Torr·cm   (near the minimum)

At pd = 0.028 Torr·cm the breakdown voltage is many kilovolts;
the plasma cannot form in the gap and only its boundary enters it.
```

The plasma itself penetrates the mouth of the gap by about one or two sheath thicknesses (≈ 0.1–0.2 mm at 0.8 Torr), and that sets where ion-driven etching stops. The ZAZ, which etches only with ions above about 60 eV, is removed only where the plasma reaches. Its boundary is set by the upper PEZ radius plus this penetration.

### 7.2.3 Radicals Against the Purge

Radicals are not stopped by Paschen's law. Chlorine atoms diffuse into the gap, and a centre purge of N₂ flowing outward through the gap pushes them back. The radical density falls exponentially into the gap with a decay length set by the balance of diffusion and flow:

```
n(x) = n₀ exp(−x / L),   L = D / v

D (Cl in N₂ at 0.8 Torr) ≈ 0.15 cm²/s × (760 / 0.8) ≈ 140 cm²/s
Gap cross-section = 2π × 14.88 cm × 0.035 cm ≈ 3.3 cm²

Purge 500 sccm:   v ≈ 500 × (760/0.8) / 60 / 3.3 ≈ 2,400 cm/s → L ≈ 0.6 mm
Purge 2 slm:      v ≈ 9,600 cm/s                             → L ≈ 0.15 mm
(reference)
```

The TE TiN etches in chlorine radicals at a slow rate even without ions, so its boundary is set by the radical profile, not the plasma edge. With the reference 2 slm purge, the radical density falls to 10% within 2.3 L ≈ 0.35 mm of the plasma edge. Chapter 11 follows the consequence: the TE TiN ends a little inside the ZAZ boundary, and the transition between full films and bare surface is a staircase about 0.3 mm wide.

### 7.2.4 Placing the Boundary

```
Front boundary radius (reference):
  Upper PEZ plate radius             148.65 mm
  Plasma penetration into the gap    + 0.15 mm
  ZAZ boundary                       148.80 mm
  TE TiN boundary (radical creep)    ≈ 148.6 mm

Error sources (3σ):
  Wafer centring on the chuck        ± 0.05 mm (optical centring, robot
                                     offset correction)
  PEZ plate wear / deposits          ± 0.03 mm (over its life)
  Gap variation (wafer bow, chuck)   ± 0.05 mm in penetration
  ──────────────────────────────────────────────────────────
  Total                              ≈ ± 0.08 mm  (spec ± 0.1 mm)
```

Wafer bow matters because the plasma's penetration into the gap depends on the gap: a wafer bowed 50 µm upward at its edge narrows the gap from 0.35 to 0.30 mm and moves the boundary outward. The W strap is not yet deposited at module 1, so bow is small; a bevel step placed after the W would see much more.

---

## 7.3 Ion Energy at the Bevel

### 7.3.1 A Collisional Sheath

At 0.8 Torr the ion mean free path is about 60 µm, much shorter than the sheath (≈ 0.5 mm). Ions collide many times while crossing it and arrive with a broad distribution whose mean is a fraction of the sheath voltage:

```
Bevel plasma (reference, illustrative):
  Lower-electrode RF  400 W, 13.56 MHz;  sheath voltage ≈ 350 V
  Ion mean free path  ≈ 60 µm;  sheath ≈ 0.5 mm  (≈ 8 collisions)
  Mean ion energy     ≈ 80–90 eV, location-dependent:

    Front shoulder    ≈ 85 eV
    Apex              ≈ 90 eV   (field concentration on the curved edge)
    Back facet        ≈ 82 eV
    Backside ring     ≈ 80 eV   (deeper under the overhang)
```

More RF power would raise these energies, but it also raises the risk of arcing at the apex, widens the plasma's penetration into the PEZ gaps, and heats the edge. The bevel etch lives with ion energies only 20–30 eV above the etch–deposition transition.

### 7.3.2 Rates at the Bevel

The film at module 1 is about 60% crystalline (Chapter 2). The model of Chapter 3 with a mixed removal coefficient gives:

```
R_net = A_mix (√E − √E_th) − D
  A_mix = 0.6 × 1.33 + 0.4 × 2.0 = 1.60 nm/min/√eV   (amorphous A ≈ 1.5×)
  E_th ≈ 30 eV;  D ≈ 3 nm/min (BCl₃/Cl₂/Ar at 0.8 Torr, 60 °C)

  Location        E (eV)   Rate (nm/min)   Film (nm)   Clear time (s)
  ────────────────────────────────────────────────────────────────────
  Front shoulder    85         3.0            5.5           110
  Apex              90         3.4            5.2            92
  Back facet        82         2.7            4.5           100
  Backside ring     80         2.5            4.0            96
```

### 7.3.3 Sensitivity

```
d(ln R)/dE = A / (2 √E R)

  Backside ring (80 eV):  1.60 / (2 × 8.94 × 2.5) ≈ 3.6% per eV
  Front shoulder (85 eV): 1.60 / (2 × 9.22 × 3.0) ≈ 2.9% per eV
```

A 10 eV loss of ion energy on the backside ring, from a worn lower PEZ ring or a changed gap, drops its rate from 2.5 to about 1.6 nm/min and its clearing time from 96 to about 150 s: the whole step. **The bevel step's margin is its ion energy**, and the parts that set the ion energy, the PEZ rings and edge electrodes, are the parts that wear.

---

## 7.4 The Reference Bevel Recipe

```
Module 1 bevel recipe (reference, chuck 60 °C, illustrative):

  Step  Purpose        Gas (sccm)                  Pressure   RF      Time
  ─────────────────────────────────────────────────────────────────────────────
  B1    TE TiN         Cl₂ 100 / Ar 400            0.8 Torr   300 W   15 s
        removal        (+ N₂ 2 slm centre purge)
  B2    ZAZ removal    BCl₃ 120 / Cl₂ 30 / Ar 400  0.8 Torr   400 W   150 s
  B3    B and Cl       O₂ 300 / N₂ 200             1.0 Torr   300 W   20 s
        removal
  ─────────────────────────────────────────────────────────────────────────────
  Plasma time 185 s; wafer time ≈ 225 s with centring, pump-down, vent
```

**B1** removes the TE TiN. TiN etches easily in chlorine (≈ 40 nm/min at the bevel); 15 s clears the thickest TiN (5 nm) with margin and gives the ZAZ a clean start.

**B2** removes the ZAZ. Its slowest location, the front shoulder, clears at 110 s; the 150 s step gives a 36% overetch there and more elsewhere. The Cl₂ fraction (20% of the halogen gas) is the same as in the periphery main step.

**B3** converts BₓClᵧ and BOₓClᵧ on the bevel to oxides and drives off chlorine, so that the wafer leaves the tool without a hygroscopic film on its edge.

---

## 7.5 Residual Zirconium

Clearing the film is necessary but not sufficient: the specification is 10¹⁰ Zr atoms/cm², a removal factor of 1.5 × 10⁶:

```
Sources of residual Zr after B2 (illustrative):
  Unremoved islands (tail of clearing)   negligible at 36% overetch with the
                                         thin, partly amorphous film
  Zr implanted or mixed into the         ≈ 10⁹–10¹⁰ /cm²; removed partly by
  underlying film during the overetch    B3 and by the SiN loss of the
                                         overetch (≈ 1 nm at the bevel)
  Redeposition of ZrClₓ from the         ≈ 10⁹–10¹⁰ /cm²; worst on the backside
  plasma onto cooler bevel surfaces      ring, which faces the lower electrode
  Transfer from the chuck / PEZ          ≈ 10⁹ /cm²; depends on chamber
  surfaces                               cleanliness (Chapter 9)

Typical after B3 (VPD-ICP-MS, bevel scan):   3–8 × 10⁹ atoms/cm²
```

The dry process meets the specification, but with a factor of only 1.3–3. Fabs that need more margin add a single-wafer **bevel rinse**: dilute HF dispensed on the backside and bevel while an N₂ curtain protects the front, removing the top nanometre of the underlying SiN or oxide and the zirconium in it. The reference keeps the rinse as a fallback, triggered when the bevel VPD monitor exceeds 5 × 10⁹ atoms/cm² (Chapter 15).

---

## 7.6 Particles and Arcing

```
Bevel-tool defect mechanisms (illustrative):

  Mechanism                   Cause                          Control
  ────────────────────────────────────────────────────────────────────────────
  Flakes from the PEZ plate   ZrClₓ/BₓClᵧ deposits on the    in-situ clean every
  and edge electrodes         ceramic near the plasma        wafer (O₂ then Cl₂);
                                                             parts swap by RF-hours
  Arcing at the apex          conductive TE TiN at a sharp   ramp RF; remove TiN
                              edge; charge on partly         (B1) at lower power
                              etched films                   before ZAZ (B2)
  Front-side contact          wafer slides on the chuck;     edge-grip handling;
  marks                       PEZ plate touches a bowed      gap monitoring
                              wafer
  Backside scratches          lift pins, chuck surface       pin design; chuck
                                                             surface condition
```

Arcing deserves a note. The TE TiN is a continuous conductor over the whole front of the wafer, capacitively coupled to the plasma at the edge. During B1, as the TiN at the bevel thins and breaks into islands, charge can collect on the islands and discharge across the narrowing gaps between them. Running B1 at lower power than B2, and removing the TiN completely before the higher-power ZAZ step, keeps arcs away.

---

## 7.7 Throughput and Tool Count

```
Reference bevel tool:
  Wafer time per chamber            ≈ 225 s  →  16 wph
  Chambers per platform             4
  Platform throughput               ≈ 60 wph (with handling overhead)

For 150,000 wafer starts per month (≈ 210 wph):
  Chambers needed at 85% availability   ≈ 16  →  4 platforms
```

The bevel step is the longest of the three dielectric etches in plasma time per unit area removed: 3 minutes to clear 46 cm², against 4 minutes to clear 318 cm² in module 2. It is slow because it runs at low ion energy. Chapter 16 compares the cost.

---

## 7.8 Alternatives

```
Route                       How                         Limitation for crystalline ZAZ
───────────────────────────────────────────────────────────────────────────────────────
Hot bevel plasma (150 °C)   rates ≈ 2.5×, less          TiN creeps further under the PEZ
                            sensitive to ion energy     (chemical etch faster); boundary
                            (E₀ falls to ≈ 30 eV)       wider unless purge increased
Wet bevel etch (spin,       edge dispense of HF or      partly crystalline ZrO₂ etches
edge dispense)              hot H₃PO₄                   slowly in dilute HF; H₃PO₄ edge
                                                        dispense hard to control; good as
                                                        a rinse after a dry step
Edge-exclusion ring in      shadow ring keeps the       ALD gases diffuse under any ring;
the ALD chamber             precursor off the edge      reduces but does not remove wrap;
                                                        ring deposits flake
Bevel CMP / edge polish     mechanical removal          particles; slow; changes edge
                                                        profile; rarely used for films
                                                        this thin
Bevel step after the        one step removes ZAZ,       SiGe furnace contaminated first;
plate fill                  TiN, SiGe, W                five-film bevel; much longer etch
```

The confined plasma with a dry clean and an optional rinse remains the production choice. The hot variant is the most attractive improvement: it would roughly halve the bevel time and widen the ion-energy margin, at the cost of tighter control of TiN creep under the PEZ.

---

## Summary and Key Takeaways

1. **The bevel plasma is confined by gaps, not masks.** PEZ plates 0.35 mm from the wafer keep the plasma off the front and back; Paschen's law keeps it from forming in the gaps.

2. **Ions and radicals draw different boundaries.** The ZAZ boundary follows the plasma edge (148.8 mm); the TiN boundary follows the radical decay against a 2 slm centre purge (≈ 148.6 mm).

3. **The bevel lives near the transition.** Mean ion energies of 80–90 eV give ZAZ rates of 2.5–3.4 nm/min and sensitivities of 3–4% per eV.

4. **Worn parts cost ion energy.** A 10 eV loss on the backside ring stretches its clearing time to the whole 150 s step.

5. **Clearing is not enough.** 1.5 × 10⁶ removal leaves 3–8 × 10⁹ Zr/cm² after the dry steps; a backside rinse is the fallback.

6. **The step is slow.** About 225 s per wafer, 16 chambers for 150,000 wafers per month; a hot bevel plasma would halve it.

---

## Study Questions

1. Compute pd for the upper PEZ gap if the gap is increased to 0.6 mm and the pressure to 1.5 Torr. Is the plasma still excluded? What happens to the boundary?

2. Using the purge model of Section 7.2.3, find the centre-purge flow that gives a radical decay length of 0.1 mm. What other effect would such a large purge have on the plasma at the edge?

3. The back facet's ion energy falls from 82 to 74 eV after 600 RF-hours. Compute the new rate and clearing time. Does the 150 s step still clear it?

4. Design a hot-bevel B2 step at 150 °C using the parameters of Chapter 3, Section 3.3.4 (A scaled by 1.2 for the partly amorphous film). Estimate the rate at 85 eV and the step time for a 36% overetch. How much wafer time is saved?

5. A bevel VPD monitor reads 9 × 10⁹ Zr/cm². List three possible causes in order of likelihood and the check for each.

6. Explain why the TE TiN boundary lies inside the ZAZ boundary. What would the boundary staircase look like if the purge failed during B1?

---

**Next Chapter:** [Chapter 8: Endpoint & In-Situ Monitoring for Nanometre Dielectrics](./08-endpoint-monitoring-nanometre-dielectrics.md)

---

**Chapter 7 Development Status:** Complete  
**Version:** 1.0
