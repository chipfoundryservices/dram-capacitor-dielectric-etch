# Chapter 11: The Dielectric Edge — Profile, Undercut, Overlap & Seal

## Overview

Wherever the dielectric is cut, it has an edge, and the edge is where an etch's other effects accumulate: the lateral reach of the chemistry, the penetration of halogens and vacancies, the position tolerance of the mask, and the notch of the electrode that covers it. In the reference layout the edge of the plate lies 1.5 µm beyond the last dummy row, and every effect in this chapter amounts to a few tens of nanometres. The reference is comfortable. A product that wants to shrink the overlap, or a route that undercuts the edge by a hundred nanometres, needs the numbers.

This chapter describes the dielectric edge for each of the five routes. It builds the overlap budget from placement, undercut, damage penetration, and notch, compares it with the layout, treats the isotropic routes' grain-boundary penetration, examines what seals the cut edge and what the seal must resist, and handles the other dielectric edge of the book: the inner boundary of the edge etch, where the plasma redeposits boron and chlorine on dies that carry cells.

**Learning Objectives:**
- Draw the plate edge profile by layer for the anisotropic, thermal, and wet routes
- Compute the lateral reach of isotropic removal, including grain-boundary penetration
- Build the minimum-overlap budget and compare it with the 1.5 µm of the reference
- Describe the options for sealing a cut dielectric edge and what each protects against
- Estimate the redeposition profile inside the boundary of the edge etch and its limit
- State the checks required before shrinking the overlap

---

## 11.1 Two Dielectric Edges

```
Edge 1: the plate edge (Module P)         the cut ZAZ under the plate foot; electrical region
                                          boundary 1.5 µm from the last dummy row
Edge 2: the edge-etch boundary (Module E) r = 147.0 mm on the top surface; the ZAZ is not
                                          cut inside it, but the plasma redeposits B, Cl, Zr
                                          on the edge dies at r = 140–146 mm
Module T has no edge: it thins the film uniformly across the wafer.
```

The first edge is a design question; the second is a process-control question. Both concern how far an effect reaches from the place where it was made.

---

## 11.2 The Plate Edge by Route

### 11.2.1 Anisotropic Routes (R0, R1)

```
Plate-edge profile, R1 (strip-then-clear), reference:
  Layer       Thickness   Edge                                   Note
  ─────────────────────────────────────────────────────────────────────────────────────────
  W (WOₓ top) 40 nm       84–86° taper; 0.74 nm of W converted    oxide removed or buried
  SiGe        150 nm      86–88°; foot notch 2.7–4.2 nm           passivation SiOₓBrᵧ + 0.3 nm
  TiN         5 nm        recessed 2.1 nm under the SiGe;          shell 0.54 nm left after P4
                          TiOₓ shell
  ZAZ         5.5 nm      cut flush with the SiGe edge ± 5 nm;     self-aligned: the plate is
                          foot of 2–5 nm beyond it (Book #32)      the mask
  SiN         landing     recessed 0.65 nm in the open area
```

The ZAZ edge is cut by ions arriving at the wafer from above, so it is vertical, and it lies under the SiGe edge: the hot clear is self-aligned to the plate. The TiN, recessed by 2.1 nm (4.2 nm in Book #32), leaves a slot under the SiGe with the ZAZ as its floor. The slot is 5 nm high and 2 nm deep: too small to fill, and too small to matter.

### 11.2.2 Isotropic Routes (R2, R3, R4)

Thermal and wet removal etch sideways at the rate at which they etch down. The ZAZ under the TiN edge is attacked from its exposed edge:

```
Lateral reach of isotropic removal (to remove the stated film thickness d_v):
  Route                          d_v (nm)    Lateral, uniform (nm)    Along grain boundaries (≤ 3×)
  ─────────────────────────────────────────────────────────────────────────────────────────────────
  R2  ALE finish (29 cycles)      1.0 × 1.3 = 1.3        1.3                      3.9
  R3  all-thermal (158 cycles)    5.5 × 1.3 = 7.1        7.1                      21
  R4  hybrid wet finish            1.0 × 1.3 = 1.3        1.3                      3.9
```

The crystalline film has grain boundaries 10–30 nm apart that etch faster than the grains (Chapter 2). A channel of fast etch can follow a boundary in under the plate. For a stated enhancement of 3×, the all-thermal route reaches 21 nm along boundaries, still two orders of magnitude less than the overlap. The enhancement itself should be measured (a cross-section after a deliberately long etch) and not assumed.

### 11.2.3 The Void Under the Plate

The isotropic undercut plus the TiN notch leave a void between the plate edge and the ZAZ edge:

```
Void depth (lateral), R3:   undercut 7.1 nm (21 nm along boundaries) + TiN notch 2.1 nm
Void height:                the ZAZ thickness removed + the TiN thickness: 5.5 + 5 nm
```

A void under a conductor edge is filled, or not, by the ILD that follows; a void a few nanometres deep is not filled and is not a path for anything. One tens of nanometres deep is a path for moisture (Book #32, Chapter 11) and for HDP-ILD plasma species, and it is covered in the seal of Section 11.5.

---

## 11.3 The Overlap Budget

### 11.3.1 What Must Fit

```
Reference layout:
  Last dummy row to plate edge      O = 1.5 µm
  Dummy rows inside the last one    3 rows × 39 nm = 0.12 µm  (pitch × √3/2 per row; 3 rows assumed)
  → first active row to plate edge  1.62 µm
```

The effects that must fit inside this distance, in the sense that their reach plus tolerance must not touch an active cell:

```
Contribution                            R0     R1     R2     R3     R4     Source
──────────────────────────────────────────────────────────────────────────────────────────────
Plate-edge placement (3σ)               100    100    100    100    100    Book #32 specification
Dielectric undercut (along boundaries)    0      0     3.9    21    3.9     § 11.2
Damage penetration after anneals         50     50     50     50    50      Chapter 12; Book #32 ch. 13
TiN notch (toward the plate interior)    4.2   2.1    2.1    2.1   2.1     Chapter 10
Sum (nm)                                154    152    156    173   156
```

### 11.3.2 Minimum Overlap

```
O_min = 1.5 × (sum of contributions)     (design factor 1.5 on the worst-case sum)
  R0  1.5 × 154 = 0.23 µm        reference O = 1.5 µm → margin 6.5×
  R1  1.5 × 152 = 0.23 µm                              → margin 6.6×
  R2  1.5 × 156 = 0.23 µm                              → margin 6.4×
  R3  1.5 × 173 = 0.26 µm                              → margin 5.8×
  R4  1.5 × 156 = 0.23 µm                              → margin 6.4×
```

On this budget every route clears the reference overlap by more than 5×. The margin is not for the etch; it is for what the budget does not contain. Book #32 (Chapter 13) lists ultraviolet light and halogens as edge mechanisms and sets the overlap floor at "a few hundred nanometres"; this chapter's sum confirms the floor at about 0.25 µm. The reference of 1.5 µm was set for lithographic and design reasons, not etch ones.

### 11.3.3 If the Overlap Is Shrunk

A product team that shrinks the overlap from 1.5 µm to 0.4 µm (the case of Book #32's study question) reduces the margin to 0.4/0.23 = 1.7×. On the checks that Book #32 required, the following now apply:

```
Check                                       Why
─────────────────────────────────────────────────────────────────────────────────────
Damage penetration, measured (not assumed)  50 nm is a model; it is 12% of the 0.4 µm
Halogen penetration after the longest anneal  Cl and B diffuse along grain boundaries
Plate-edge placement, measured at the wafer edge   ± 100 nm becomes ± 25% of the overlap
Isotropic route: undercut along boundaries  R3's 21 nm is 5% of 0.4 µm
Edge-array leakage vs overlap (test arrays) 0.3, 0.6, 1.0, 1.5 µm arrays (Chapter 12)
Polarity pairs on the edge arrays           charging near the edge (Chapter 7)
```

---

## 11.4 Field at the Edge

The edge of the electrode over a cut dielectric edge is a convex conductor corner, and the field at such a corner is enhanced:

```
E_edge / E_flat = t / (r ln(1 + t/r))    (cylindrical corner, dielectric t = 5.5 nm)
  r = 2 nm:  5.5 / (2 × ln 3.75)  = 2.08
  r = 5 nm:  5.5 / (5 × ln 2.1)   = 1.48
```

A TiN edge rounded to 2 nm by the shell conversion has a field 2.1× higher than the flat. Over the periphery SiN, with no storage node underneath, no field is applied: the dielectric edge at the plate foot lies over an insulator and carries no capacitor. The enhancement matters only if the overlap is reduced until the plate edge lies over cells, which is not an option within the 0.4 µm of Section 11.3.3.

---

## 11.5 Sealing the Edge

After P5 the cut ZAZ edge, the TiN notch, the shell, and the SiGe foot are covered by the inter-layer dielectric. The ILD deposition is a plasma process (HDP or PECVD oxide), which is a source of hydrogen, charge, and moisture at the exposed edge.

```
Seal option                          Protects against                  Cost per wafer    Notes
──────────────────────────────────────────────────────────────────────────────────────────────────
ILD alone (HDP oxide, 400 °C)         — (reference)                       0                 H and plasma species
                                                                                             reach the void
Conformal ALD SiN liner, 5–10 nm      moisture, H, HDP plasma species;     + $0.8–1.2        fills voids ≤ 10 nm;
                                      closes the TiN notch                                    one more step
Low-temperature ALD Al₂O₃, 3–5 nm     moisture; H (less than SiN)          + $0.6–0.9        thin; weak vs plasma
Oxide hard-mask remnant (R1 variant)  charging; plasma on the plate top    + $2–3            also removes the
                                                                                             antenna (Chapter 7)
```

The reference routes use ILD alone, because the edge is over the periphery, 1.5 µm from the cells, and none of the species the seal would stop can reach them in the anneal budget. The liner is the option for a product with a small overlap: it fills the void, removes the moisture path, and is the only seal that does not depend on the shape of the ILD fill.

---

## 11.6 The Other Edge: the Boundary of the Edge Etch

### 11.6.1 Redeposition Inside r = 147 mm

The edge plasma redeposits what it sputters and what it deposits (BₓClᵧ) on the nearest surface, which includes the wafer top just inside the boundary, where the plasma is absent but its products can condense. With a decay length λ set by the gap and the surface sticking:

```
Boron film at the boundary (r = 147): ≈ 0.5 nm BₓClᵧ ≈ 1 × 10¹⁵ B cm⁻²  (before the O₂ step)
Decay inward:   C(x) = C₀ exp(−x/λ),  λ ≈ 0.4 mm (the gap 0.3 mm plus a stick factor)

  r (mm)    x from boundary (mm)   B (cm⁻²)
  ────────────────────────────────────────────
  147.0       0                     1.0 × 10¹⁵
  146.0       1.0                   8.2 × 10¹³
  145.0       2.0                   6.7 × 10¹²
  143.0       4.0                   4.5 × 10¹⁰
  140.0       7.0                   2.5 × 10⁷
```

The edge dies lie at r ≤ 146 mm. The boron limit on the ZAZ surface under the future top electrode is 2 × 10¹³ cm⁻² (a few hundredths of a monolayer; the top-electrode ALD interface is sensitive to boron). At r = 146 mm the unmitigated value is 8.2 × 10¹³, a factor 4 over; with the O₂/H₂O strip that follows the plasma, which reduces B by about 10, it is 8 × 10¹², inside the limit with a factor 2.5 margin.

### 11.6.2 Zirconium Inside the Boundary

Zirconium redeposited onto the ZAZ is a minor matter: the surface it lands on is ZrO₂ already, and 5 × 10¹² cm⁻² of extra zirconia on 1.4 × 10¹⁶ is 0.04%. Boron and chlorine are the species that change the interface. They are limited as above; chlorine is removed with the strip and by the anneal that precedes the top-electrode ALD.

### 11.6.3 What Is Measured

```
Inner-boundary control (reference):
  ZAZ thickness line-scan, r = 140–150 mm      loss ≤ 0.1 nm at r < 146; locates the boundary
  B and Cl by XPS/TXRF on the ZAZ at r = 144–146   ≤ 2 × 10¹³ B cm⁻² (weekly, and after PM)
  Edge-die capacitor arrays (test structures)  C_s and leakage vs radius at r = 140–146 mm
```

---

## Summary and Key Takeaways

1. **The plate edge is self-aligned.** In the strip-then-clear route the ZAZ is cut flush with the SiGe edge; the TiN is recessed 2.1 nm and covered by a shell (4.2 nm in Book #32).

2. **Isotropic routes undercut by as much as they etch.** 1.3 nm for a 1 nm finish; 7.1 nm for the all-thermal clear, up to 21 nm along grain boundaries if their rate is 3× faster.

3. **The overlap budget sums to 152–173 nm.** Placement 100 nm, undercut 0–21 nm, damage 50 nm, notch 2–4 nm; a design factor of 1.5 gives O_min = 0.23–0.26 µm, 5.8–6.6× below the 1.5 µm reference.

4. **A smaller overlap needs measured numbers.** At 0.4 µm the margin is 1.7×; damage penetration, halogen diffusion, undercut along boundaries, and edge-array leakage must be measured.

5. **The seal is optional at 1.5 µm.** An ALD SiN liner (+$0.8–1.2) closes the void and is the option for a small overlap.

6. **The edge etch's boundary matters to the edge dies.** Boron falls from 10¹⁵ to 8 × 10¹³ cm⁻² at 1 mm inside the boundary; the O₂/H₂O strip gets it to 8 × 10¹², inside the 2 × 10¹³ limit.

---

## Study Questions

1. Compute the lateral reach of an R3 clear of 5.5 nm of ZAZ with 40% over-cycling at EPC 0.045 nm/cycle (tetragonal, plus the Al₂O₃ layer), and its reach along boundaries if the enhancement is 5×. Compare with the damage penetration.

2. Recompute O_min if the placement tolerance is 150 nm and the damage penetration after the longest anneal is 80 nm, for R1 and R3. Is the 0.4 µm overlap still acceptable?

3. For r = 2 nm and r = 3 nm TiN edge rounding, compute E_edge/E_flat for a 5.5 nm dielectric. Why does the enhancement not matter over the periphery?

4. The boron film at the edge-etch boundary is 1.5 × 10¹⁵ cm⁻² and λ = 0.6 mm. Compute B at r = 146 mm and the strip factor needed to meet 2 × 10¹³. Which dies are exposed if the limit is not met?

5. A void under the plate edge is 21 nm deep and 10.5 nm high. Which seal options of Section 11.5 fill it? Which of the options leaves a path to the cells at a 0.4 µm overlap?

6. Describe the cross-section experiment that would measure the grain-boundary enhancement of the lateral etch, and what result would change the choice between R3 and R2.

---

**Next Chapter:** [Chapter 12: Etch-Induced Defects in the Dielectric — Vacancies, Halogens, Leakage & TDDB](./12-etch-induced-dielectric-defects.md)

---

**Chapter 11 Development Status:** Complete  
**Version:** 1.0
