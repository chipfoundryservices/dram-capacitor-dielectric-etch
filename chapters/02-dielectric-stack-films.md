# Chapter 2: The Dielectric Stack — ZAZ Films, Phases, Interfaces & Incoming Surfaces

## Overview

The dielectric clear inherits a film it did not make and a surface it did not prepare. The ZAZ was grown by ALD at 280 °C. It crystallized during the top-electrode and plate depositions, in a different way on the periphery nitride than on the TiN pillars. It was then covered by the plate stack, uncovered again by the plate conductor etch, touched by chlorine during that etch's overetch, and exposed to the products of a resist strip. What arrives at the dielectric chamber is a 5.4 nm film with a contaminated top surface, a mosaic of grains of two phases, a 0.3 nm amorphous layer in the middle, an oxidized interface with the nitride at the bottom, and a thinner version of itself on the walls of every piece of topography.

This chapter describes each of those features and the property of each that matters to the etch: thickness, phase, grain size, density, the interfaces, the surface contamination, and the incoming variations. It ends with a table of what the etch sees.

**Learning Objectives:**
- Describe the ALD of ZrO₂ and Al₂O₃ and the nucleation difference between TiN and SiN surfaces
- Explain how and when the film crystallizes, and why the periphery film is mixed-phase
- Relate phase, density, and grain structure to etch rate and clearing behaviour
- List the contaminants left on the ZAZ by the plate conductor etch and the strip, and their effect on the first seconds of the clear
- Describe the dielectric on topography and on the bevel
- Quantify the incoming variations the dielectric clear must absorb

---

## 2.1 Growing the Film

### 2.1.1 ALD of ZrO₂

```
ZrO₂ ALD (reference, illustrative):
  Precursor          CpZr(NMe₂)₃ (cyclopentadienyl tris(dimethylamino)
                     zirconium); alternatives TEMAZ, ZrCl₄ (not used:
                     Cl in the film)
  Oxidant            O₃ (≈ 200 g/m³)
  Temperature        280 °C
  Growth per cycle   ≈ 0.09 nm
  Cycles             ≈ 29 per 2.6 nm layer
  Impurities         C ≈ 0.5 at%, N ≈ 0.3 at%, H ≈ 1 at% (as deposited)
```

The amide ligands react with surface hydroxyls and leave the zirconium bound to oxygen; ozone burns off the remaining ligands and regenerates hydroxyls. The cyclopentadienyl ligand raises the thermal stability of the precursor, which allows a higher deposition temperature and therefore a denser, cleaner, partly crystalline film.

### 2.1.2 The Al₂O₃ Insertion

```
Al₂O₃ ALD:  TMA + O₃, 280 °C, ≈ 0.09 nm/cycle, 3–4 cycles → 0.3 nm
```

At 0.3 nm, the insertion is about one monolayer of Al₂O₃ and is not a continuous slab; it is an aluminium-rich, oxygen-bridged layer that remains amorphous through every later anneal. It interrupts the columnar growth of the lower ZrO₂, so grains in the upper ZrO₂ nucleate afresh and their boundaries do not line up with those below. Leakage paths along grain boundaries are broken; the breakdown field rises. For the etch, the insertion is a 0.3 nm layer of a different material in the middle of the film, and a useful endpoint marker (Chapter 8).

### 2.1.3 Nucleation on TiN and on SiN

The first ALD cycles depend on the surface. Inside the array, the precursor meets TiN whose surface was oxidized to TiOₓNᵧ by air and by the first ozone pulse: a dense population of hydroxyls, fast nucleation, no delay. On the periphery, it meets PECVD silicon nitride, whose surface carries fewer hydroxyls and some amine groups:

```
Nucleation (illustrative):
  Surface             Delay        ZAZ thickness after full sequence
  ─────────────────────────────────────────────────────────────────
  TiN (array)         none         5.5 nm
  PECVD SiN           ≈ 1–2 cycles 5.4 nm (≈ 0.1 nm thinner)
  SiO₂ (marks, cap)   ≈ 0–1 cycle  5.45 nm
```

The first ozone pulses also oxidize the top 0.5 nm or so of the SiN into an oxynitride, so the periphery stack is really ZAZ on SiOₓNᵧ on SiN. That interlayer matters at the end of the clear: the etch lands on an oxynitride before it lands on nitride.

---

## 2.2 Crystallization

### 2.2.1 When

```
Thermal history of the ZAZ (reference):
  ZAZ ALD           280 °C, ≈ 40 min    partly crystalline on TiN;
                                        amorphous on SiN
  TE TiN (pulsed    400 °C, ≈ 15 min    tetragonal grains grow on TiN
  CVD, TiCl₄/NH₃)                       templates; nucleation on SiN
  SiGe fill         425 °C, ≈ 40 min    crystallization complete
  W strap           400 °C, ≈ 5 min     —
  Oxide cap         400 °C, ≈ 3 min     —
```

By the time the plate etch is done, the ZAZ is fully crystalline everywhere. What differs is which phase it crystallized into.

### 2.2.2 Which Phase

ZrO₂ has three common polymorphs. The monoclinic phase is stable in bulk at room temperature. The tetragonal and cubic phases are stable in bulk only at high temperature, but in films a few nanometres thick, small grains and surface energy stabilize them.

```
ZrO₂ phases (illustrative):
  Phase         Density (g/cm³)   k        Where in the reference
  ────────────────────────────────────────────────────────────────────
  Amorphous     5.5–5.7           ≈ 20–25  as deposited on SiN
  Monoclinic    5.68              ≈ 20     ≈ 30% of grains on SiN
  Tetragonal    6.1               35–45    on TiN (array); ≈ 70% on SiN
```

On TiN, the TiOₓNᵧ surface and the in-plane strain of the electrode template the tetragonal phase, and the array film crystallizes tetragonal with grains 10–30 nm across. On amorphous SiN, nothing templates it. Grains nucleate at random, grow larger (15–40 nm), and about a third of them take the monoclinic form. **The periphery film is not the capacitor film**: it is a mixed-phase, coarser-grained relative, and it is the one the etch must clear.

### 2.2.3 Grains and Boundaries

```
Periphery ZAZ microstructure (reference, illustrative):
  Lower ZrO₂ grains          15–40 nm lateral, columnar through 2.55 nm
  Al₂O₃ insertion            amorphous, continuous over most of the area
  Upper ZrO₂ grains          15–40 nm lateral, nucleated on the insertion;
                             boundaries offset from the lower layer
  Grain-boundary width       ≈ 0.5 nm; density ≈ 5–10% lower than grain
  Phase per grain            tetragonal ≈ 70%, monoclinic ≈ 30%
```

Grain boundaries etch faster than grain interiors in every chemistry. Monoclinic grains etch somewhat more slowly than tetragonal grains in halogen plasmas (Chapter 3). Together, these set the spread of local clearing times, the quantity that the overetch must cover (Chapter 10).

### 2.2.4 Why Phase Matters for the Etch

```
D1 etch rate by phase (250 °C, 70 eV, illustrative):
  ZrO₂ amorphous            14 nm/min
  ZrO₂ tetragonal            9.0 nm/min
  ZrO₂ monoclinic            8.0 nm/min
  Al₂O₃ (amorphous, 0.3 nm)  7.0 nm/min
```

The crystalline film etches 35–45% more slowly than the as-deposited film because it is denser and its lattice energy is higher. A thermal budget that drives more of the periphery film to the monoclinic phase, a longer SiGe deposition, a higher W temperature, lengthens the clear by a few percent and widens its spread. The dielectric clear inherits these changes without seeing them in any inline measurement (Chapter 15).

---

## 2.3 What Lies Beneath

### 2.3.1 The Periphery Top SiN

```
Periphery stack under the ZAZ (reference):
  SiOₓNᵧ interlayer        ≈ 0.5 nm (ozone-oxidized SiN surface)
  Top SiN                  120 nm PECVD, H ≈ 15 at%, Si-rich (n ≈ 2.02)
  Mold remains below       PE-TEOS 650 nm, mid SiN 50 nm, BPSG 760 nm,
                           bottom SiN 20 nm (Book #30)
```

The periphery top SiN is the landing film of the dielectric clear and an etch stop for the later periphery contacts, which must break through it. Its thickness after the clear enters the contact etch budget. The specification allows 5 nm of loss; the reference D1 loses 1.3 nm (Chapter 12).

### 2.3.2 The Plate Stack and Its Cap

```
Plate stack at the island edge (reference):
  Oxide cap        PE-TEOS 60 nm (hard mask for the dielectric clear)
  W strap          40 nm
  SiGe fill        150 nm, Si₀.₇Ge₀.₃, B ≈ 2 × 10²⁰ cm⁻³
  TE TiN           5 nm, pulsed CVD, Cl ≈ 0.5 at%
  ZAZ              5.5 nm (continuous under the plate)
  Total height     ≈ 260 nm above the ZAZ
```

During the dielectric clear, the cap protects the top of the plate, and the plate sidewall, W, SiGe, and TiN, is exposed to the plasma at grazing incidence. Chapter 11 follows each sidewall material through the clear.

---

## 2.4 The Surface the Etch Receives

### 2.4.1 After the Plate Conductor Etch

The last step of the plate conductor etch removes the 5 nm TE TiN in Cl₂/Ar at about 50 eV and stops on the ZAZ. In that chemistry, TiN etches at about 50 nm/min and ZrO₂ at less than 0.5 nm/min, so the stop is good, but not clean:

```
Periphery ZAZ surface after the plate TiN step (illustrative):
  ZAZ loss                     ≤ 0.3 nm (TiN overetch on ZrO₂)
  Ti residue                   1–3 × 10¹⁴ Ti/cm² as TiOₓClᵧ, in patches
                               where TiN cleared last
  Cl                           3–5 at% in the top 1 nm
  Br                           ≤ 1 at% (memory of the SiGe HBr step)
  F                            ≤ 1 at%; ZrF₄-like bonding at the surface
                               (memory of the W SF₆ step on chamber walls)
```

### 2.4.2 After the Strip

The plate resist and BARC are stripped in situ in a downstream N₂/H₂ plasma with the wafer at 250 °C. An oxygen strip would oxidize the exposed W sidewall to WO₃, which BCl₃ later reduces unevenly, so the reference uses a reducing chemistry:

```
After the N₂/H₂ strip (illustrative):
  Carbon on the periphery ZAZ   2–5 × 10¹⁴ C/cm², mostly as scattered
                                carbonaceous fragments redeposited from
                                the stripped resist
  Hydrogen                      uptake in the top nanometre of ZAZ;
                                Zr–OH and Zr–H sites
  Cl                            reduced (≈ 1–2 at%), partly lost as HCl
```

### 2.4.3 Why the First Seconds Matter

Each of these contaminants can delay the onset of etching locally:

```
Contaminant          Effect on the clear                     Handled by
──────────────────────────────────────────────────────────────────────────────
TiOₓClᵧ patches      etch readily in BCl₃; little delay       BT step
Zr–F surface         halogen exchange with BCl₃ needed        BT step (BCl₃-rich)
                     before chlorination proceeds
Carbon fragments     micromask: C is removed slowly by        BT ion energy; strip
                     BCl₃/Cl₂ without oxygen                  quality (Ch. 10)
Moisture (queue)     Zr–OH and B–O chemistry; mild            vacuum transfer;
                     incubation                               queue-time limit
```

The reference D1 opens with a 3 s breakthrough (BT) in BCl₃/Ar at about 100 eV to remove all of these at once (Chapter 3). The breakthrough also removes about 0.65 nm of ZAZ, which shortens the main etch.

---

## 2.5 The Dielectric on Topography and at the Bevel

### 2.5.1 Vertical Walls

ALD coats vertical walls with the same thickness as horizontal surfaces. Where topography lies outside the plate, the plate conductor etch has cleared W, SiGe, and TiN from it (Book #32); what is left is ZAZ on the floors and the walls:

```
Topography outside the plate (reference, illustrative):
  Feature                         Depth       Width        ZAZ on walls
  ───────────────────────────────────────────────────────────────────────
  Overlay marks (mold trenches)   1.6 µm      1–4 µm       5.4 nm, full height
  Capacitor-module monitor        1.6 µm      45 nm pitch  wraps free pillars
  arrays outside the plate
  Shallow steps (cap/plate edge)  0.26 µm     —            none (ZAZ under plate)
```

A directional etch sees the wall ZAZ edge-on. Its vertical thickness, measured along the ion direction, is the wall height: 1.6 µm. Only lateral, isotropic, or redeposition-assisted processes remove it (Chapter 10).

### 2.5.2 The Bevel

```
ZAZ at the wafer edge (illustrative, single-wafer ALD chamber):
  Top bevel and apex            ≈ 5.5 nm (full thickness)
  Bottom bevel                  ≈ 4–5 nm
  Backside, 0–1 mm from edge    ≈ 2–4 nm, thinning
  Backside, 1–3 mm              traces to ≈ 1 nm
  Backside, > 3 mm              < 1 × 10¹³ Zr/cm² (lifted-pin and
                                pocket marks may add spots)
```

The plate films also wrap the bevel to some extent, so the bevel carries a stack of TiN, SiGe, W, and oxide over ZAZ. Chapter 9 describes how the bevel is cleaned and why the front-side dielectric clear cannot do it.

---

## 2.6 Incoming Variations

```
Incoming variation the dielectric clear must absorb (illustrative):

Source                              Typical range                   Effect
────────────────────────────────────────────────────────────────────────────────────
Periphery ZAZ thickness             5.4 ± 0.2 nm (wafer range);     clearing time
                                    1σ ≈ 1.5%
Monoclinic fraction                 20–40% (thermal budget)          rate −1% to −3%
Grain size                          15–40 nm (wider with lower       clearing spread
                                    nucleation density)
ZAZ loss in the plate TiN step      0–0.3 nm                         clearing time
Ti residue                          0.5–3 × 10¹⁴ /cm²                BT sufficiency
F, Cl, Br on the surface            ≤ 5 at% total                    incubation
Carbon after strip                  1–5 × 10¹⁴ /cm²                  micromasking
Oxide cap thickness                 60 ± 3 nm                        cap budget
Plate-edge sidewall angle           84–88°                           sidewall exposure
Queue time strip → clear            0 (vacuum transfer, reference)   moisture
                                    to hours (if broken)
```

The largest contributors to the clearing-time spread are the thickness and the phase mix. The largest contributors to the residue tail are the carbon and particle micromasks. Chapters 6 and 10 treat the two separately because the cures differ.

---

## 2.7 What the Etch Sees

```
Summary of the incoming wafer at the dielectric clear (reference):

Region             Surface                     Below                   Must
──────────────────────────────────────────────────────────────────────────────────
Periphery (45%)    ZAZ 5.4 nm, mixed phase;    SiOₓNᵧ 0.5 nm on        clear to
                   Ti, Cl, F, C on top         SiN 120 nm              < 10⁻¹⁰ tail
Plate top (55%)    oxide cap 60 nm             W / SiGe / TiN / ZAZ    lose ≤ 15 nm
Plate sidewall     W, SiGe, TiN edge-on,       ZAZ (cut at the edge    lose ≤ 2–3 nm
(147 mm/die)       ≈ 195 nm tall               after the clear)        laterally
Topography walls   ZAZ 5.4 nm, vertical        oxide / SiN walls       no free-standing
(scribe, marks)                                                        stringers
Bevel / backside   ZAZ under plate films       Si                      (separate step)
```

---

## Summary and Key Takeaways

1. **ALD grows ZAZ everywhere at the same thickness**, about 0.1 nm thinner on SiN because of a nucleation delay.

2. **The periphery film is not the capacitor film.** On amorphous SiN it crystallizes into coarser grains with about 30% monoclinic phase; on TiN it is tetragonal and finer.

3. **Crystalline ZrO₂ etches 35–45% slower than amorphous ZrO₂**, and grain boundaries and phases spread the local clearing time.

4. **The 0.3 nm Al₂O₃ insertion is a different material in the middle of the film**: a slow layer for the etch, and a marker for endpoint.

5. **The incoming surface carries Ti, Cl, F, Br, and C** from the plate etch and the strip; a short, BCl₃-rich breakthrough removes them.

6. **Topography and the bevel carry ZAZ that a directional etch cannot reach**: stringers on walls up to 1.6 µm tall, and a wrap 1–3 mm onto the backside.

---

## Study Questions

1. How many ALD cycles are needed for the reference ZAZ at the growth rates of Section 2.1? If the nucleation delay on SiN grows to 4 cycles, how thick is the periphery film?

2. A thermal-budget change raises the monoclinic fraction from 30% to 45%. Using the rates of Section 2.2.4, estimate the change in the main-etch time of the reference D1.

3. Why does an oxygen strip before the dielectric clear create problems at the plate sidewall that a reducing strip avoids? What does the reducing strip cost on the periphery surface?

4. Compute the Zr content (atoms/cm² of wafer) of the ZAZ on the walls of a 2 µm-wide, 1.6 µm-deep mark trench, per micrometre of trench length. Compare it with the Zr on the same length of flat periphery 2 µm wide.

5. Estimate the time a fluorinated ZrO₂ surface (one monolayer of ZrF₄) delays the start of etching if halogen exchange with BCl₃ proceeds at 0.1 monolayer per second in the main-etch chemistry and 0.5 monolayer per second in the BT. What does this imply for a recipe with no BT?

6. Draw the periphery stack from the surface to the top SiN, with thickness and composition, as the dielectric clear receives it.

---

**Next Chapter:** [Chapter 3: Plasma Chemistry of Metal-Oxide Etching](./03-metal-oxide-plasma-chemistry.md)

---

**Chapter 2 Development Status:** Complete  
**Version:** 1.0
