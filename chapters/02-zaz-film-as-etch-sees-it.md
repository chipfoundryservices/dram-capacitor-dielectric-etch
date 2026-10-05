# Chapter 2: The ZAZ Film as the Etch Sees It — Growth, Crystallization, Wrap-Around & Stress

## Overview

An etch is only as predictable as the film it meets. The ZAZ that the dielectric etches must remove is not one film but several: amorphous at the edge etch, partly crystalline at the moment the top electrode closes over it, fully tetragonal at the plate etch, and of different thickness on the pillar, the periphery, the bevel, and the backside. How fast it etches, whether it leaves grains, how far it reaches under the wafer, and whether it flakes at the bevel are all set by the deposition and the thermal history behind it.

This chapter describes the film as the etches of Chapters 3–7 see it. It follows the ALD growth, derives the crystallization history from the thermal budget, shows how the etch rate varies with crystallinity, maps where the film lies, and builds a model of how far the ALD wraps around the wafer edge. The model ties the width of the backside zone to the same precursor pulse that coats the capacitor forest. The chapter closes with stress, adhesion, and the incoming variations that the etches must absorb.

**Learning Objectives:**
- Describe the ALD growth of the ZAZ and the cycle count and time behind 5.5 nm
- Compute the crystallized fraction after each thermal step of the capacitor module
- Relate etch rate to crystallinity and explain the origin of the grain tail
- Compute the precursor pulse needed to coat the forest and the backside wrap-around it causes
- Size the edge-etch zone from the wrap-around model
- Estimate the strain energy of the plate stack at the bevel and compare it with adhesion

---

## 2.1 The Film and How It Grows

### 2.1.1 The ALD Process

```
ZAZ ALD (reference, illustrative):
  Zr precursor      cyclopentadienyl-type Zr amide, bulky ligands
  Al precursor      trimethylaluminium (TMA)
  Oxidant           ozone
  Temperature       280 °C
  Growth per cycle  ZrO₂  0.05 nm       Al₂O₃  0.09 nm
  Sequence          ZrO₂ 52 cycles → Al₂O₃ 3 cycles → ZrO₂ 52 cycles
  Thickness         2.6 + 0.27 + 2.6 = 5.5 nm
  Cycles / time     107 cycles × 8 s = 14 min per wafer (single-wafer equivalent)
  Thickness uniformity   ± 0.2 nm (3σ) across the wafer
```

The Al₂O₃ insertion layer, 0.3 nm and less than two monolayers, is not there for its dielectric constant. It interrupts the growth of ZrO₂ grains, keeps the stack amorphous through deposition, and lowers the leakage after crystallization by breaking grain boundaries that would otherwise run from electrode to electrode.

### 2.1.2 What the Film Is Made Of

```
Film at deposition (illustrative):
  ZrO₂ density        ≈ 5.2–5.4 g/cm³ amorphous; 5.7–6.1 g/cm³ tetragonal
  Carbon, nitrogen    < 1 at% (ligand remnants)
  Hydroxyl            ≈ 1–2 at% in the outer nanometre
  Interface to TiN    1.0–1.5 nm TiOₓNᵧ from the pillar (Book #32, Chapter 2)
  Breakdown field     ≈ 4.5 MV/cm after crystallization
```

The hydroxyl and carbon in the outer nanometre matter at two points. Before the top-electrode TiN is deposited, the surface adsorbs water and hydrocarbons from the air within hours, which sets the queue limit of Chapter 1. And at the periphery clear, the surface carries the carbon and chlorine of the plate etch on top of whatever the ALD left (Chapter 10).

---

## 2.2 Three States of One Film

### 2.2.1 Crystallization as a Thermal-Budget Problem

The film crystallizes from the amorphous state as it is heated. A simple Avrami model with an Arrhenius time constant describes the progress:

```
X(t) = 1 − exp[−(t/τ)ⁿ],   τ(T) = τ₀ exp(E_a/kT),   n = 2,   E_a = 3.0 eV   (illustrative)

Calibration: X = 0.40 after the top-electrode TiN (400 °C, 17 min) → τ(673 K) = 1430 s
  τ(698 K) = 1430 × exp[(3.0/8.617×10⁻⁵)(1/698 − 1/673)] = 221 s       (425 °C)
  τ(553 K) = 1.05 × 10⁸ s                                              (280 °C)
```

The thermal history, step by step:

```
Step                          T (°C)    Time        τ (s)        X after step
──────────────────────────────────────────────────────────────────────────────
ZAZ ALD                        280      14 min      1.05 × 10⁸    7 × 10⁻¹¹   amorphous
Edge etch, trim (E, T)        ≤ 280     minutes     —             amorphous
Top-electrode TiN ALD          400      17 min      1430          0.41
SiGe plate fill (LPCVD)        425      1 h         221           1.00        tetragonal
W strap (PVD)                 ≤ 250     minutes     —             1.00
Hot ZAZ clear (P4)             250      38 s        3.9 × 10⁹     1 × 10⁻¹⁶   no change
```

The film is amorphous for the whole of the ALD and any edge or trim step, 41% crystalline after the top electrode, and fully crystalline after the SiGe furnace. The hot clear at 250 °C changes nothing: τ at 250 °C is 10⁹ s.

### 2.2.2 What Crystallization Does

Crystallization densifies the film by about 5–10% and makes it partly polycrystalline. The grains are tetragonal ZrO₂ 10–30 nm across, a few times wider than the film is thick; the Al₂O₃ layer stays amorphous. Three consequences follow for etching:

```
1. The film is denser: Zr–O bonds are the same, but there are more of them per unit
   volume, and the chloride products must leave from a more tightly packed surface.
2. The film has grain boundaries: less dense, with excess O vacancies; they etch faster
   than the grain interiors.
3. The film is stressed: densification under constraint raises the tensile stress
   (Section 2.7).
```

---

## 2.3 Etch Rate Against Crystallinity

### 2.3.1 The Rate Table

The ion-assisted etch rate in the ambient BCl₃/Cl₂ chemistry of Book #32 (150 eV, 60 °C) is 9 nm/min for amorphous ZrO₂ and 6 nm/min for tetragonal. To first order, the rate of a partly crystalline film is the mixture:

```
R(X) = 9 (1 − X) + 6 X   nm/min

   X       R (nm/min)     Film state
 ───────────────────────────────────────────
  0.00       9.0          as deposited (edge etch, trim)
  0.41       7.8          after the top electrode (not etched here)
  1.00       6.0          after the SiGe furnace (periphery clear)
```

The same ion-yield model of Book #32 (Y = A(√E − √E_th), K = 3.9 nm/s per unit yield) reproduces both columns with different thresholds:

```
Amorphous:     E_th ≈ 45 eV,  A = 0.0069       Tetragonal:  E_th ≈ 60 eV,  A = 0.0057

   E (eV)     ZrO₂ amorphous (nm/min)     ZrO₂ tetragonal (nm/min)
 ─────────────────────────────────────────────────────────────────
     50              0.6                         0
     70              ≈ 2.7                       0.8
    100              5.4                         3.0
    150              9.0                         6.0
    250             14.8                        10.8
```

The lower threshold of the amorphous film matters at the edge: the edge plasma has a low ion flux (about a quarter of the main chamber), and the amorphous film clears in 93 s at 250 eV (Chapter 5) where a crystalline film would need 125 s.

### 2.3.2 The Grain Tail

Book #32 derived the overetch needed to clear a granular film from a normal distribution of grain-level clearing times with σ_g = 8%. The origin of σ_g is the grain boundary: the boundaries clear first, and the last few tenths of a nanometre of each grain interior clears later. An amorphous film has no boundaries, no grains, and no such tail; its clearing time is set by thickness uniformity and rate uniformity alone (about 3%, Chapter 6):

```
Amorphous (edge etch):     σ ≈ 3%     OE for z = 6.4:  6.4 × 3%  = 19%
Tetragonal, ambient:       σ_g ≈ 8%                    6.4 × 8%  = 51%
Tetragonal, hot (250 °C):  σ_g ≈ 5%                    6.4 × 5%  = 32%
```

This is why Chapter 4 argues for removing the film early where it can be done, and for heat where it cannot.

---

## 2.4 Where the Film Lies

```
Surface                    Film (reference)            Needed?   Removed by
────────────────────────────────────────────────────────────────────────────────────────
Pillar outer wall          5.5 nm, conformal           yes       —
Support faces (both sides) 5.5 nm                      yes       —
Bottom stop (SiN)          5.5 nm                      yes       —
Top of top support         5.5 nm (in the array)       yes       —
Periphery top SiN          5.5 nm, flat                no        Module P
Scribe lines, marks        5.5 nm                      no        Module P
Top edge ring (r > 147)    5.5 nm                      no        Module E
Bevel (apex, upper/lower)  5.5 nm, thinning            no        Module E
Backside, outer 3.5 mm     5.5 nm to ≈ 2 mm, tail      no        Module E
Pedestal / showerhead      same per wafer, cumulative  no        Module C
```

On the pillars the film is conformal to within ± 0.3 nm from top to bottom of the 1.41 µm wall. That it is possible at all depends on the precursor dosing of Section 2.5.1.

---

## 2.5 Wrap-Around

### 2.5.1 Dosing the Forest

The gaps between ZAZ-coated pillars are dead-end channels. In the hexagonal array of 45 nm pitch, the void between three neighbouring pillars of radius 14 nm plus 5.5 nm of film has an inscribed circle of

```
r = p/√3 − (14 + 5.5) = 45/1.732 − 19.5 = 6.5 nm  →  d = 13 nm,   AR = 1410/13 = 109
```

The Zr precursor must reach the bottom of each channel and saturate the wall at every cycle. Treat the channel as a long tube of diameter d. A front of saturated surface at depth x advances as the precursor diffuses in by Knudsen transport, with D_K = d·v̄/3. Molecules arriving at the front must supply N_s per unit wall area:

```
Molecules consumed per unit length of advance:     N_s π d dx
Knudsen flux to the front:                         (π d²/4)(d v̄/3)(n₀/x)

   N_s π d dx/dt = π d³ v̄ n₀ / (12 x)
   x dx = d² v̄ n₀ dt / (12 N_s)

   t_sat = 6 N_s AR² / (n₀ v̄)                       (tube, closed end)
```

For the Zr precursor at 553 K:

```
M = 323 amu → v̄ = √(8kT/πm) = 190 m/s
p = 20 mTorr = 2.67 Pa → n₀ = p/kT = 3.5 × 10²⁰ m⁻³
N_s = 1.5 × 10¹⁴ cm⁻² = 1.5 × 10¹⁸ m⁻²   (bulky ligands; saturation per cycle)

t_sat = 6 × 1.5×10¹⁸ × 109² / (3.5×10²⁰ × 190) = 1.60 s
```

The precursor pulse must exceed 1.6 s. The reference uses 2.0 s, a 25% margin. The dependence is on AR²: a mold 25% taller (Book #31) needs a pulse 1.56× longer.

### 2.5.2 The Same Pulse Wraps the Wafer

The wafer rests on a pedestal. Between its backside and the pedestal is a gap g, set by surface roughness, wafer bow, and the edge ring, and the precursor enters it from the edge. Treat it as a slit closed at the far end, with two coated walls (the wafer backside and the pedestal):

```
Molecules consumed per unit edge length per advance:     2 N_s dx
Knudsen flux in the slit (D_K = g v̄/3):                  (g² v̄/3)(n₀/x)

   x_sat = g √( n₀ v̄ t / (3 N_s) )                       (slit, closed end)

Reference: g = 12 µm (roughness and bow), t = 2.0 s:
   x_sat = 12×10⁻⁶ × √( 3.5×10²⁰ × 190 × 2.0 / (3 × 1.5×10¹⁸) ) = 2.06 mm
```

At the full pulse, the ZAZ is at full thickness out to **2.1 mm** from the wafer edge, and tails off beyond:

```
Backside thickness profile (illustrative), distance from the edge in units of x_sat:

  x / x_sat     t / t₀
  ──────────────────────
    0.5          1.00
    1.0          0.95
    1.25         0.50
    1.5          0.10      ← 3.1 mm
    2.0          0.01
```

The same pulse that coats the forest wraps the backside. Shortening it to save wrap would starve the bottom of the pillars (t = 1.6 s gives x_sat = 1.85 mm, a saving of 0.2 mm); lengthening it to 4 s gives 2.9 mm. The width scales as g √(p t): a 20% variation in the gap is a 20% variation in wrap, and a doubling of precursor partial pressure is a 41% increase.

### 2.5.3 Sizing the Edge Zone

```
Edge-zone design (reference):
  Backside zone width ≥ 1.5 x_sat + margin = 3.1 + 0.4 = 3.5 mm
  Top-side zone       3.0 mm (outside the die edge exclusion; Chapter 5)
  Bevel               apex and both slopes, about 0.6 mm of arc

  Areas       top 28.0 cm²;  bevel 5.7 cm²;  backside 32.6 cm²;  total 66 cm²
  Zr atoms    66 cm² × 1.44×10¹⁶ cm⁻² = 9.6 × 10¹⁷ per wafer (ZAZ at full thickness)
```

A product that moves to a taller mold, or a tool with a larger gap, widens the zone. The zone is a design variable of the edge etch (Chapter 5), tied to the deposition recipe by the formula above.

---

## 2.6 Thickness at the Edge of the Deposition

At the very edge, the ALD thickness is not uniform. Gas-flow edge effects and the edge ring change the precursor dose on the top surface in the outer few millimetres, typically by a few percent in thickness. The edge die, at r = 140–147 mm, are where this edge profile reaches active cells (110 dies lie between r = 140 and 150 mm; about 13% of the wafer). The edge etch must therefore not alter the ZAZ at r < 146 mm (Chapter 1, specification), and the deposition must hold ± 0.2 nm out to the die edge.

---

## 2.7 Stress and Adhesion at the Bevel

The plate stack at the bevel is a thin-film system under tension. The strain-energy release rate for a biaxially stressed film of thickness h on a stiff substrate is

```
G = (1 − ν) σ² h / E

Film                σ (GPa)    h (nm)    E (GPa)    ν      G (J/m²)
───────────────────────────────────────────────────────────────────────
ZAZ (tetragonal)     +1.0         5.5      220      0.30     0.018
W strap              +1.0        40        411      0.28     0.070
SiGe (B-doped)       +0.1       150        150      0.30     0.007
TiN (5 nm)           small        5         —        —       ≈ 0.003
Stack                                                         ≈ 0.10
```

The stack stores about 0.1 J/m². The film peels only if its adhesion energy at the interface is lower than this. On the flat wafer the adhesion of the stack on SiN or on ZAZ exceeds 1 J/m² and nothing happens. At the bevel the surface is rough, partly covered by polymer and by films from earlier modules, and the adhesion falls to 0.05–0.3 J/m². A fraction of the bevel then peels, usually after a thermal cycle, and lands on the die.

The dielectric is a minor contributor to the stored energy (18% of the stack) but it is the interface on which the tungsten and TiN lie. Removing it from the bevel before the plate is deposited leaves the TiN to adhere to the cleaner, rougher surface beneath, and removes the zirconium from the flakes that do come loose.

---

## 2.8 Incoming Variation

```
Module E (edge etch) inherits:
  ZAZ thickness (3σ, die area)       ± 0.2 nm      → clearing time ± 3.6%
  Edge-ring thickness profile        ± 3% outer 5 mm
  Backside wrap x_sat                2.1 mm ± 20%  → zone design margin
  Surface carbon/hydroxyl            queue time    → none for the etch; matters for TiN interface

Module P (periphery clear) inherits:
  Crystallinity X                    1.00 (± 0.02 with furnace position)
  ZAZ thickness                      ± 0.2 nm, minus ZAZ loss in P2 (≤ 0.3 nm)
  Fluorine and chlorine on the surface   from the conductor etch (Chapter 10)
  Plate edge: W top, TiOₓ shell      from the strip (Chapter 7)

Module T (trim) inherits:
  ZAZ thickness                      ± 0.2 nm      → removal set per wafer from the map
  Surface                            amorphous, hydroxylated; first cycles differ (Chapter 13)
```

Each item is absorbed by an overetch, by feed-forward control of the time or cycle count, or by a design margin (the zone width). Chapter 15 shows which.

---

## Summary and Key Takeaways

1. **The ZAZ grows in 107 cycles and 14 minutes.** ZrO₂ 52 cycles, Al₂O₃ 3, ZrO₂ 52; the Al₂O₃ interrupts grains and lowers leakage.

2. **It is amorphous until the top electrode.** 41% crystalline after the 400 °C TiN, 100% after the SiGe furnace; the 250 °C clear changes nothing.

3. **Amorphous etches 1.5× faster with no grain tail.** 9 against 6 nm/min at 150 eV; the overetch for z = 6.4 falls from 51% to 19%.

4. **The forest sets the pulse and the pulse sets the wrap.** t_sat = 6N_sAR²/(n₀v̄) = 1.6 s for AR = 109; the same 2 s pulse wraps the backside by x_sat = g√(n₀v̄t/3N_s) = 2.1 mm.

5. **The edge zone is 3.0 mm on top and 3.5 mm on the back.** 66 cm² and 9.6 × 10¹⁷ Zr atoms per wafer.

6. **The bevel stores 0.1 J/m² and holds it by a thread.** Adhesion at the bevel of 0.05–0.3 J/m² is the margin; removing the dielectric there also removes zirconium from the flakes.

---

## Study Questions

1. Recompute the crystallized fraction after the top electrode if the TiN deposition is lengthened to 25 minutes at 400 °C and the activation energy is 2.5 eV (keep τ(673 K) = 1430 s). What happens to X after the SiGe furnace?

2. A taller mold (Book #31) has pillars 2.0 µm tall in the same 45 nm pitch. Compute AR for the 13 nm channel, the minimum pulse, and the new backside wrap x_sat at g = 12 µm if the pulse is set to 25% above the minimum.

3. A new pedestal has a gap of 8 µm. Compute x_sat and the minimum backside zone width at the reference pulse. What would you check before narrowing the zone?

4. Compute the ambient etch rate and clearing time (for 5.5 nm of ZAZ) at X = 0, 0.41, and 1.0, using R(X) of Section 2.3.1 for ZrO₂ and scaling Al₂O₃ in proportion to the ZrO₂ rate (Al₂O₃ = 5 nm/min at X = 0 rate of 9 nm/min).

5. Using Section 2.7, estimate the strain energy of the plate stack if the W stress rises to 1.4 GPa. Does it exceed the lowest bevel adhesion of 0.05 J/m²? By how much does it change the stack total?

6. For the amorphous edge etch of Section 2.3.2, σ = 3% and the clearing-probability target is the periphery value, P < 8 × 10⁻¹¹ (z = 6.4). Compute the overetch it implies. Why is a grain-tail target the wrong test for an amorphous film, and what should replace it for the 10¹⁰ cm⁻² backside limit?

---

**Next Chapter:** [Chapter 3: Surface Chemistry of Metal-Oxide Removal — Plasma, Thermal & Wet](./03-metal-oxide-removal-chemistry.md)

---

**Chapter 2 Development Status:** Complete  
**Version:** 1.0
