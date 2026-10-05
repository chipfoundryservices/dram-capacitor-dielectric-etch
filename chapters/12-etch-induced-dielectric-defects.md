# Chapter 12: Etch-Induced Defects in the Dielectric — Vacancies, Halogens, Leakage & TDDB

## Overview

Book #32 (Chapter 13) asked how a plasma above the plate can hurt a dielectric it never touches: through charging, ultraviolet light, and halogens at the plate edge. This chapter asks a different question, of the dielectric that *is* touched. Which dielectric is that? Not the periphery film, which is removed. It is the film at the cut edge of the plate, the film on the edge dies at the rim of the wafer, and, in module T, every nanometre of the film on every pillar in the array, because the trim acts on the product. For those, the question is what the etch leaves in the film: oxygen vacancies from ion collisions, halogens and boron from the plasma, fluorine and carbon from the thermal chemistry.

The chapter first derives the ion damage that each plasma step inflicts and its depth. It then lists the chemical species that each module leaves in the film and in what quantity. Its central device is to convert every kind of damage into an **equivalent thickness loss**, so that it can be compared directly with the 0.28 nm of headroom of Chapter 1: leakage, from a damaged layer of given thickness and barrier reduction; and TDDB, from field acceleration and area scaling. It ends with the recovery that the flow provides for free, and the structures that verify the result.

**Learning Objectives:**
- Compute the ion energy needed to displace oxygen and zirconium and the nominal damage per ion
- List what each module leaves in the surviving dielectric and where
- Convert a damaged layer into an equivalent thickness loss and its leakage factor
- Apply field acceleration and area scaling to the TDDB of a trimmed film
- Explain why edge damage does not reach TDDB when the overlap is adequate
- Choose test structures that separate ion damage, chemical damage, and charging

---

## 12.1 What Is Touched

```
Module   Film touched                       How                              Extent
──────────────────────────────────────────────────────────────────────────────────────────────────
E        edge dies at r = 140–146 mm         B, Cl redeposition from the      B ≤ 2 × 10¹³ cm⁻² at the
         (top surface)                       edge plasma (Ch. 11)             ZAZ/TiN interface
P2, P4   ZAZ at the plate cut edge            ions (grazing); Cl, B; charging  5–10 nm in the step;
                                                                                20–50 nm after anneals
P4       dielectric under the plate           charging only (1.3 V clamp)      Q ≈ 1.7 × 10⁻³ C/cm²
T        ALL dielectric in the array          F, C, ligand remnants in the     whole product film;
         (outer surface of every pillar)      outer 0.5 nm; no ions            f_d = 1
```

Module T is the severe case: no other etch in the book acts on the whole product. The edge of the plate is the mild one, where the reach is tens of nanometres against 1.6 µm of overlap. The structure of the chapter follows: the plasma damage is local, and its effect on the cells is zero if the overlap is respected; the trim damage is global, and its effect is the subject of the equivalent-thickness budget.

---

## 12.2 Ion Damage

### 12.2.1 Energy Transfer and Thresholds

An ion of mass m₁ and energy E transfers at most a fraction γ = 4m₁m₂/(m₁ + m₂)² of its energy to a target atom of mass m₂ in a head-on collision. Displacing an atom from its lattice site takes the displacement energy E_d, about 20 eV for oxygen and 40 eV for zirconium in ZrO₂ (illustrative):

```
Ion        γ to O     E to displace O      γ to Zr    E to displace Zr
─────────────────────────────────────────────────────────────────────
Ar⁺        0.82         24.5 eV             0.85         47 eV
Cl⁺        0.86         23.3 eV             0.81         50 eV
B⁺         0.96         20.8 eV             0.38         106 eV
BCl₂⁺      0.55         36.5 eV             1.00         40 eV
```

At 40 eV, the ion energy of the stop, ions can displace oxygen but not zirconium. At 80 eV (the hot clear) and 150 eV (Book #32's HK step) they can displace both. The Kinchin–Pease estimate of the number of displaced atoms per ion is E/(2E_d):

```
E (eV):                 40     80     150    250
Displacements per ion:   1.0    2.0    3.8    6.2   (nominal; most recombine)
```

### 12.2.2 Depth

Ions of these energies stop within about 1–1.5 nm of the surface (a TRIM-class estimate, ± 30%):

```
Ion and energy                  Range in ZrO₂ (nm)    Damaged layer (range + straggle)
Cl₂⁺ at 40 eV (stop, P2)           0.5                    ≈ 1.0 nm
BCl₂⁺ at 80 eV (clear, P4)         0.8                    ≈ 1.3 nm
Ar⁺ at 150 eV (R0, HK step)        1.3                    ≈ 2.0 nm
Ar⁺ at 250 eV (edge etch)          1.8                    ≈ 2.7 nm
```

The damaged layer is the film's outer 1–3 nm, a layer rich in oxygen vacancies. For the periphery film, it does not matter: it is the layer being removed. At the plate's cut edge the same layer forms on the sidewall, a few nanometres wide, grazing incidence reducing the dose. It then does matter in so far as it is the entry for the chemical penetration of Section 12.3.

### 12.2.3 Oxygen Vacancies

An oxygen vacancy in ZrO₂ is a donor-like level whose position in the gap makes it a trap for trap-assisted conduction. Ion bombardment generates them directly; BCl₃, which getters oxygen, generates them chemically. The density that results at the cut edge is high in the outer 1–2 nm and falls with depth. The vacancies diffuse and recombine in the anneals that follow, the 400 °C top-electrode ALD and the 425 °C SiGe furnace, which are not designed as anneals but act as such (Section 12.6).

---

## 12.3 Chemical Incorporation

```
Species     Source                 Where                        Quantity (illustrative)
─────────────────────────────────────────────────────────────────────────────────────────────
Cl          P2, P4 plasmas         cut edge (5–10 nm in the      2–5 at% in the outer nm
                                   step; 20–50 nm after anneal)  (3 × 10¹⁴ cm⁻²)
B           P4 (BCl₃), edge etch   cut edge; edge-die surface    ≤ 2 × 10¹³ cm⁻² at the interface
                                                                  of the edge dies
F           module T (HF)          whole array film, outer       1–3 at% in the outer 0.5 nm
                                   0.5 nm                        (≈ 8 × 10¹³ F cm⁻² at 2 at%)
C           module T (DMAC);       whole array film, outer       < 1 at% (decomposition at > 325 °C)
            resist, BARC (P1)      surface
H, OH       air, water, strip      outer surface                 monolayer
```

F deserves a comment. Fluorine in HfO₂ and ZrO₂ is known to passivate oxygen vacancies (F⁻ substitutes for O²⁻ at a vacancy), and a small fluorine dose can lower leakage and improve stability. A large dose does the opposite: it forms ZrF bonds that lower the barrier, and it is the source of the TiF species that can form at the later TiN interface. The effect of 1–3 at% in the outer 0.5 nm is therefore of uncertain sign, and the verification of Section 12.7 must measure it, not assume it. The reference treats it as a *cost* (conservatively) in the budget of Section 12.4.

---

## 12.4 Leakage: Damage as Equivalent Thickness

### 12.4.1 The Conversion

Chapter 1 gave the leakage's dependence on thickness: one decade per 0.45 nm of physical film. A layer of thickness w whose barrier is lowered to a fraction η of its original height (η = 1 is undamaged) conducts as if the film were thinner by

```
ΔT_eq = w (1 − η)               leakage factor = 10^(ΔT_eq / 0.45 nm)

 w (nm)    η       ΔT_eq (nm)    Leakage ×
 ──────────────────────────────────────────
  1.0      0.90       0.10          1.7
  1.0      0.72       0.28          4.2        ← the headroom of Chapter 1
  0.5      0.50       0.25          3.6
  1.5      0.80       0.30          4.6
```

The headroom of Chapter 1 (0.28 nm) is a budget in equivalent thickness. Any damage layer, from any module, spends it. A damaged layer 1 nm thick whose barrier is 28% lower uses it all.

### 12.4.2 The Specification in These Units

The specification of cell leakage after module P is "within 10% of the unetched reference at 1.0 V". In equivalent thickness:

```
ΔT_eq = 0.45 nm × log₁₀(1.10) = 0.019 nm      (0.35% of the 5.5 nm film)
```

The specification is sensitive to a change of 0.019 nm, three-tenths of a monolayer of the film's own thickness. That is why it is a good detector of plate-etch charging (Chapter 7) and a very demanding requirement for a trim, which removes 0.07 nm per cycle: a single cycle is 3.8× that sensitivity, as a thickness effect alone.

### 12.4.3 Budget

```
Spending of the 0.28 nm equivalent-thickness headroom (reference; leakage only)
  Trim, 3 cycles (0.22 nm of physical film)                   0.22 nm
  Fluorine/carbon surface layer of module T (conservative)    0.03 nm
  Interface change at the top-electrode ALD after T            0.02 nm
  Total                                                       0.27 nm   of 0.28 nm
  Remaining for everything else (stress, process drift)        0.01 nm
```

A 3-cycle trim spends the headroom. A 2-cycle trim (0.15 nm) leaves 0.08 nm; a 1-cycle trim (0.07 nm) leaves 0.16 nm. The trim is not a free parameter, and the budget of Chapter 13 starts from this table.

---

## 12.5 TDDB

### 12.5.1 Field Acceleration and Area Scaling

Time-dependent dielectric breakdown follows a Weibull distribution whose characteristic life falls with the field and with the area:

```
F(t) = 1 − exp[−A (t/η₁)^β]       η₁ = characteristic life per cm² at use conditions
β = 1.2 (illustrative); η ∝ V^(−n) at fixed thickness; n = 30 (illustrative)
Field at use:  0.55 V / 5.5 nm = 1.0 MV/cm
Dielectric area per die:  1.72 × 10¹⁰ cells × 1.24 × 10⁻⁹ cm² = 21.3 cm²
```

A die specification of 10⁻⁵ probability of failure in 10 years gives

```
A (10 yr / η₁)^β = 10⁻⁵   →   (10/η₁)^1.2 = 4.7 × 10⁻⁷   →   10/η₁ = 5.3 × 10⁻⁶
  η₁ = 1.9 × 10⁶ years per cm²
```

### 12.5.2 What Trimming Does to TDDB

A thinner film at the same voltage carries a higher field: E = V/t. The characteristic life falls as (E/E₀)^(−n):

```
Trim (nm)    Field ×      η reduction k = (t₀/t)ⁿ      M = kᵝ     P(10 yr, die)
────────────────────────────────────────────────────────────────────────────────
0.1          1.019         1.73                          1.94        1.0×10⁻⁵ → 1.9×10⁻⁵
0.2          1.038         3.04                          3.79        1.0×10⁻⁵ → 3.8×10⁻⁵
0.3          1.058         5.38                          7.53        1.0×10⁻⁵ → 7.5×10⁻⁵
```

A trim of 0.2 nm shortens the TDDB life by a factor of 3.0 and raises the die-level 10-year failure probability by 3.8×. This is the same 3.8% field increase that raised the capacitance by 3.8%: a thinner film is paid for in lifetime as well as leakage. The two together define the trim's price (Chapter 13).

### 12.5.3 The Edge Contributes Nothing

If a fraction f_d of the area is damaged and its characteristic life is reduced by a factor k,

```
M = 1 + f_d (k^β − 1)

 f_d      k       M
 10⁻³     10      1.01
 10⁻²     10      1.15
 10⁻³     100     1.25
```

At the plate edge, f_d is the area of the damaged strip lying over cells. With the overlap of 1.5 µm and a damage length of 50 nm, **f_d = 0**: the strip lies over the periphery. The edge's damage does not enter the die's TDDB. Only if the overlap is reduced until the damage reaches the first active rows does the table above apply, and then it applies to the outermost rows alone, which fail first and which a repair resource can cover. The array's area dwarfs the edge, so even f_d = 10⁻² raises M by only 15%.

---

## 12.6 Recovery

Three thermal steps follow the dielectric's last exposure in modules E and T:

```
After module E or T:
  Top-electrode TiN ALD     400 °C, 17 min     TiCl₄/NH₃; N-rich ambient
  SiGe LPCVD                425 °C, 1 h        SiH₄/GeH₄/BCl₃; hydrogen-rich
  W PVD                     ≤ 250 °C           none
  ILD (HDP) after P5        400 °C             hydrogen and plasma species
```

```
Defect                         Recovered by the above?               Comment
────────────────────────────────────────────────────────────────────────────────────────
O vacancies in the outer nm    partly: diffusion of O from the film   the crystallization of the
                               and the interface; TiN ALD is not an   film (Ch. 2) also reconstructs
                               oxidizer                               the lattice
Cl, B in grain boundaries      no: they diffuse inward, they do not   penetration 20–50 nm after
                                leave (Book #32, Ch. 13)               anneals
F (module T)                   partly: HF can leave as the film        TiF interface species form
                                crystallizes; F bound at vacancies      at the TiN interface
                                stays
C (DMAC residue)               partly: burns at 400 °C in an          ZrC-like species if not
                                oxidizing ambient; TiN ALD is not       oxidized
```

For module T, an oxidizing step between the trim and the TiN deposition (a 3 min ozone or O₂-plasma exposure at 250 °C) is the one addition to the flow. It refills vacancies in the outer nm, oxidizes carbon, and removes loosely bound fluorine. The step also affects the amorphous film's surface, and adds 5–10 minutes to the 4 h queue limit of Chapter 1.

---

## 12.7 Verification

```
Structure                                  Purpose                              Distinguishes
────────────────────────────────────────────────────────────────────────────────────────────────────
Reference capacitor array (10⁶ cells)      baseline leakage and TDDB            —
Trim-dose array (0, 1, 2, 3 cycles by die  leakage and C vs trim dose           chemical vs thickness
  or by region on the monitor wafer)                                              effect of the trim
Edge-proximity arrays (overlap 0.3–1.5 µm) leakage vs distance to the cut edge  edge damage reach
Polarity pairs (n⁺/p, p⁺/n junctions)     negative- vs positive-plate stress   charging vs material
Antenna arrays (1×, 10×, 100× antenna)    leakage vs antenna ratio             charging
Large-area TDDB capacitors (1 mm²)         Weibull slope, area scaling          defect density
```

The trim-dose array is the most important structure in this book that has no counterpart in Book #32. It fits a line to leakage against the number of cycles: the slope per cycle should match the thickness model (a factor 1.45 per cycle, from 10^(0.073/0.45)). A slope above it points to chemical damage (F, C); below it to a net passivation.

---

## Summary and Key Takeaways

1. **Ions at 40 eV displace oxygen but not zirconium; at 80 eV and above they displace both.** Nominal damage is 1.0, 2.0, 3.8, and 6.2 displacements per ion at 40, 80, 150, and 250 eV, in a layer of 1.0–2.7 nm.

2. **Plasma damage is local, thermal-etch damage is global.** The plate edge touches only a strip tens of nanometres wide over the periphery; module T acts on every pillar of the array.

3. **Equivalent thickness unifies the budget.** ΔT_eq = w(1 − η); the leakage headroom of 0.28 nm is spent by a damaged layer of 1 nm with a barrier 28% lower.

4. **The 10% leakage specification is 0.019 nm.** One trim cycle is 3.8 times that; a 3-cycle trim spends 0.22 nm of the 0.28 nm.

5. **A 0.2 nm trim shortens TDDB life by 3.0× and raises die-level failure 3.8×.** The same 3.8% field increase that raises C_s by 3.8%.

6. **The edge does not reach TDDB.** With a 1.5 µm overlap f_d = 0; even at f_d = 10⁻² and k = 10 the multiplier is only 1.15.

---

## Study Questions

1. Compute the minimum ion energy to displace oxygen for an Ar⁺ ion and for an O₂⁺ ion (m = 32 amu) with E_d = 20 eV. Which of the steps of this book have enough energy for each?

2. A damaged layer 1.2 nm thick has a barrier lowered by 15%. Compute ΔT_eq and the leakage factor. Would it fit in the budget of Section 12.4.3 together with a 2-cycle trim?

3. Recompute the TDDB multiplier M for a 0.15 nm trim with β = 1.5 and n = 25. Compare with the table's 0.1 and 0.2 nm.

4. A product with a 0.4 µm overlap has a damage length of 80 nm after the longest anneal, and in the worst case that strip lies over active cells along the whole perimeter of each plate island (1.1 × 1.2 mm). Compute f_d as the strip area over the island area, and M for k = 30 with β = 1.2.

5. A trim-dose array gives leakage factors of 1.0, 1.9, 3.6, and 7.2 for 0, 1, 2, and 3 cycles. Compare the slope with the 1.45 per cycle of the thickness model, and say what the result implies for fluorine.

6. List the thermal steps that follow the trim and say which of the defect classes of Section 12.6 each can recover. What does the added ozone step do that they cannot?

---

**Next Chapter:** [Chapter 13: Thinning, Trim & Rework](./13-thinning-trim-rework.md)

---

**Chapter 12 Development Status:** Complete  
**Version:** 1.0
