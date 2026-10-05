# Chapter 1: The Capacitor Dielectric & Why It Is Etched

## Overview

The node dielectric is the part of a DRAM capacitor that holds the charge apart. In the reference array it is a laminate of zirconium oxide and aluminium oxide 5.5 nm thick, with the capacitance of 0.50 nm of silicon dioxide. It sits between the TiN storage-node pillar of every cell and the shared TiN top electrode of the cell plate, and it must pass less than a femtoampere per cell for the bit to survive a refresh interval.

It is deposited by atomic-layer deposition (ALD), because no other method can lay 5.5 nm of film on the outside of seventeen billion pillars 1.4 µm tall, the same thickness at the top as at the bottom. ALD has no notion of where the capacitors are. It grows the same film on the periphery, the scribe lines, the alignment marks, the wafer bevel, and the outer millimetre of the backside. Almost all of the film on the wafer is inside the array and is needed. About one part in seventy is not, and that part must be removed so completely that no grain of it is left under any of thirty million periphery contacts per die.

This chapter explains what the dielectric does, where it ends up, why the excess must go, where it must stay, how clean "removed" has to be, the routes by which the removal can be done, and the specification sheet that the rest of the book works against.

**Learning Objectives:**
- Compute the cell capacitance and the leakage current density the dielectric must hold
- Account for where ALD places the dielectric on a wafer and how much of it is excess
- Explain why ZrO₂ left in the periphery opens contacts, and why the contact etch cannot remove it itself
- Express the residue specification in atoms per square centimetre, monolayers, and grains per die
- Place the dielectric etch in the capacitor module and compare the routes by which it can be done
- List the specification of the dielectric clear and the failure each line protects against

---

## 1.1 What the Dielectric Does

### 1.1.1 Capacitance

```
1T1C cell (reference):

   Bit line ──┤ access transistor ├── landing pad ── storage node (TiN pillar)
                                                           │
                                                   ZAZ dielectric, 5.5 nm
                                                   (EOT 0.50 nm)
                                                           │
                                               top electrode TiN 5 nm
                                               + SiGe 150 nm + W 40 nm (plate)
                                                           │
                                                V_plate = V_core/2 = 0.55 V
```

The storage capacitance is set by the dielectric's equivalent oxide thickness (EOT) and the electrode area it covers:

```
C_s = ε₀ · 3.9 · A / EOT

  A    = outer pillar area = π × 28 nm × 1410 nm = 1.24 × 10⁵ nm² = 1.24 × 10⁻⁹ cm²
  EOT  = 0.50 nm
  C_s  = 8.85 × 10⁻¹² × 3.9 / 0.50 × 10⁻⁹ × 1.24 × 10⁻¹³ m² = 8.6 fF
```

The ZAZ is physically 5.5 nm thick and electrically 0.50 nm. Its effective permittivity is

```
k_eff = 3.9 × 5.5 / 0.50 ≈ 43
```

carried almost entirely by the tetragonal ZrO₂. The 0.3 nm Al₂O₃ in the middle has k ≈ 9 and costs about 0.13 nm of EOT; it is there to interrupt grain boundaries that would otherwise run straight through the film and to raise the breakdown field (Chapter 2).

### 1.1.2 Leakage

A cell holding a "1" has 0.55 V across its dielectric, a field of 0.55 V / 5.5 nm = 1.0 MV/cm. Book #32 (Chapter 1) derived the retention budget: about 30 fA of total leakage per cell in the weakest cells at 85 °C, of which the dielectric may take about 1 fA.

```
Dielectric leakage specification:
  I ≤ 1 fA per cell at ±0.55 V, 85 °C
  J ≤ 1 × 10⁻¹⁵ A / 1.24 × 10⁻⁹ cm² ≈ 8 × 10⁻⁷ A/cm²
```

That current density is a property of the whole film inside the array. The dielectric etch does not touch that film directly, but it runs a few micrometres away from it, at the edge of every plate island, in chlorine at 250 °C (Chapters 11 and 13).

### 1.1.3 Why ZrO₂

```
Candidate capacitor dielectrics (illustrative):
  Film              k        Band gap (eV)   Comment
  ───────────────────────────────────────────────────────────────────────
  SiO₂              3.9       9.0            reference; far too low k
  Al₂O₃             9         8.8            low leakage; low k
  HfO₂ (monocl.)    18–20     5.7            stable; moderate k
  ZrO₂ (tetrag.)    35–45     5.8            high k when tetragonal;
                                             crystallizes on TiN at ≈ 400 °C
  TiO₂ (rutile)     80–100    3.0–3.5        needs Ru/RuO₂ electrode;
                                             leaky at small gap
  SrTiO₃            100–200   3.2            needs high-temperature
                                             crystallization; Sr is hard to etch
```

ZrO₂ in its tetragonal phase gives the highest permittivity among films that still have a band gap near 6 eV, crystallize at temperatures the rest of the module tolerates, and grow well on TiN. Those same properties, strong bonds and stable crystals, make it hard to etch (Chapter 3). Chapter 14 returns to the higher-k films that may replace it, and to how each of them etches.

---

## 1.2 Where the Dielectric Goes

### 1.2.1 ALD Coats Everything

The ZAZ is deposited after Book #30's mold dip-out has freed the pillars. It is grown by alternating pulses of a zirconium precursor and ozone (and, for the insertion, trimethylaluminium and ozone), each pulse saturating the surface. Every surface the precursors reach is coated to the same thickness:

```
After ZAZ deposition (cross-section at the array edge, not to scale):

   periphery                       │ array
                                   │
   ┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┐ ┌┐ ┌┐ ┌┐ ┌┐ ┌┐ ┌┐   ← ZAZ on top of the
   ▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓│ ││ ││ ││ ││ ││ ││     support lattice
   (periphery top SiN on mold)   │ ││ ││ ││ ││ ││ ││   ← ZAZ wrapping each
                                 │ ││ ││ ││ ││ ││ ││     free-standing pillar
                                 │ ││ ││ ││ ││ ││ ││
                                 └─┘└─┘└─┘└─┘└─┘└─┘└─ ← ZAZ on the bottom SiN
   ┄┄┄ = ZAZ 5.5 nm, everywhere
```

### 1.2.2 Accounting

```
Dielectric area per 300 mm wafer (reference, illustrative):
  Plate islands cover 55% of the wafer                 389 cm²
  Cell array within the plate islands (70%)            272 cm²
  Surface enhancement in the array: 1.24 × 10⁵ / 1734  ≈ 71×
  Dielectric on pillars                                ≈ 19,500 cm²
  On supports, bottom stop, array-edge walls           ≈ 2,500 cm²
  Total inside the plate                               ≈ 2.2 m²

  Periphery and scribe (open, 45% of the wafer)        318 cm²
  Fraction of the dielectric outside the plate         ≈ 1.4%
```

The dielectric etch removes about one part in seventy of the film on the wafer. All of it lies flat on the periphery top SiN, except at topography (Section 1.2.4) and at the bevel (Section 1.2.3).

### 1.2.3 The Bevel and the Backside

ALD precursors diffuse around the wafer edge. On a 300 mm wafer held on a heated pedestal, the ZAZ covers the top bevel, the apex, the bottom bevel, and typically 1–3 mm of the backside before thinning out. That film is not removed by any front-side etch. It is the dielectric module's largest contribution to zirconium on wafer backsides, and Chapter 9 treats its removal.

### 1.2.4 Topography

The periphery is flat over most of its area, but not everywhere. Overlay and alignment marks, process-control structures in the scribe, and test structures for the capacitor itself contain holes and trenches cut through the mold. ALD coats their vertical walls with the same 5.5 nm. A directional etch clears the floors and leaves the walls; the result is a free-standing ZAZ fence, a **stringer**, up to the height of the mold step. Chapter 10 treats stringers and their consequences.

---

## 1.3 Why It Must Leave the Periphery

### 1.3.1 Periphery Contacts

After the capacitor module, an inter-layer dielectric (ILD) about 1.8 µm thick covers the wafer. The periphery contacts are etched through it, through the periphery top SiN, and down to the bit-line level, the gates, and the active areas of the periphery transistors: about 3 × 10⁷ contacts per 16 Gb die, each about 40 nm across at the bottom. They are etched in fluorocarbon chemistry. Fluorocarbon plasmas do not etch ZrO₂; they form a ZrF₄ skin on it and stop (Chapter 3).

```
A ZrO₂ grain under a periphery contact (reference):
  Grain residue thickness       0.5–1.5 nm
  Contact overetch removes      ≈ 1 nm of ZrO₂ (sputtering at high bias)
  Grain > 1 nm                  contact stops on it → open or high resistance
  Grain < 1 nm                  contact punches through, often with a
                                partial-area bottom → resistance tail
```

A single surviving grain under a single contact fails the die unless repair covers it, and periphery contacts are not repairable the way cells are.

### 1.3.2 Why Not Let the Contact Etch Remove It?

The contact etch could, in principle, end with a BCl₃ step that breaks through high-k. In practice it does not, for three reasons:

```
1. Access     The contact is 40 nm wide and 1.8 µm deep (AR ≈ 45). The ZAZ at its
              bottom would be etched with the ion angular spread and the transport
              limits of a high-aspect-ratio hole, at 150 eV or more.
2. Materials  Contacts land on W, CoSi₂/NiSi, doped Si, and SiN; a BCl₃ step
              at the bottom attacks several of them.
3. Ownership  Most contacts do not land under residual ZrO₂. A breakthrough
              step costs every contact damage and CD to rescue a few.
```

It is cheaper and safer to clear the ZAZ once, on a flat surface, before the ILD goes down.

### 1.3.3 Zirconium Contamination

Zirconium is not a dopant in silicon and diffuses slowly, so it is not a lifetime killer the way iron or copper is. It is a cross-contamination hazard: it accumulates on the walls of chambers that etch it and transfers to other wafers, and the ZAZ on the bevel and backside rubs off on lithography chucks, end effectors, and furnace boats shared with other layers. Fabs set backside limits of the order of 10¹⁰ atoms/cm² for Zr on wafers entering shared tools (Chapter 9).

### 1.3.4 Hydrogen

The final alloy anneal of a DRAM process supplies hydrogen to passivate interface traps at the transistor gates. A continuous high-k film with an Al₂O₃ insertion slows hydrogen transport. Over the periphery, ZAZ left on the wafer would sit between the hydrogen sources above (the ILD and passivation nitride) and the periphery transistors below. The effect is secondary next to contact opens, but it appears as threshold-voltage shifts in periphery transistors when large areas of high-k remain.

### 1.3.5 Marks and Measurements

ZAZ and its stringers on alignment and overlay marks change their optical signals and their edge profiles. Metrology targets in the scribe are designed on the assumption that the high-k is gone.

---

## 1.4 Where It Must Stay: The Plate Edge

Under each plate island the ZAZ is the capacitor dielectric of the array, and at the island edge it is cut:

```
Plate edge after the plate conductor etch (reference, not to scale):

     oxide cap 60 nm  ██████████████████
     W 40 nm          ██████████████████
     SiGe 150 nm      ██████████████████
     TE TiN 5 nm      ██████████████████
     ZAZ 5.5 nm       ┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄┄  ← exposed ZAZ to remove
     top SiN          ▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓
                      │← 1.5 µm overlap →│ periphery
     last dummy row ──┘
```

After the dielectric clear, the cut face of the ZAZ is at the plate edge, directly under the top-electrode TiN. Three things can go wrong there:

```
1. Top-electrode recess   Cl attacks the 5 nm TiN sidewall laterally,
                          exposing the ZAZ top surface at the edge
2. Dielectric undercut    an isotropic etch removes ZAZ from under the TiN,
                          leaving a slot 5.5 nm tall
3. Ingress                halogen, boron, and later moisture enter along
                          the slot and the ZAZ/TiN interface
```

The overlap of 1.5 µm keeps the first real capacitors away from the edge. Product designers want to reduce it to save die area. How far it can be reduced is set by the edge chemistry of this book (Chapter 11).

---

## 1.5 How Clean Is Clean

### 1.5.1 Atoms and Monolayers

```
ZrO₂ (tetragonal): ρ ≈ 6.1 g/cm³, M = 123.2 g/mol
  Zr atoms per cm³ = 6.1 / 123.2 × 6.02 × 10²³ = 3.0 × 10²² cm⁻³
  Zr areal density per nm of film = 3.0 × 10¹⁵ cm⁻²
  One monolayer (≈ 0.28 nm)       ≈ 8.3 × 10¹⁴ cm⁻²

Periphery ZAZ: 5.1 nm of ZrO₂ → 1.5 × 10¹⁶ Zr/cm²
Specification: Zr ≤ 1 × 10¹³ /cm² (average, by TXRF) → 1.2% of a monolayer
Required removal: 1 − 1 × 10¹³ / 1.5 × 10¹⁶ = 99.93%
```

### 1.5.2 Averages and Tails

The average specification is necessary and not sufficient. A wafer can show 3 × 10¹² Zr/cm² by TXRF and still fail its periphery contacts, if that zirconium is concentrated in a few grains that each stop a contact. The binding specification is a tail:

```
Contacts per die                    3 × 10⁷
Grains under the contacts per die   ≈ 1.2 × 10⁸   (≈ 4 per contact)
Target opened contacts per die      < 0.01
Required P(grain left) per grain    < 8 × 10⁻¹¹
```

Chapter 10 develops the statistics. The result is that the dielectric clear is designed against one grain in about 10¹⁰, and confirmed only by electrical tests at the end of the line.

---

## 1.6 Routes and Their Place in the Flow

### 1.6.1 The Flow

```
Capacitor module and the dielectric clear (reference, split route):

  Storage-node separation (Book #32, module 1)
  Support open, dip-out, dry (Book #30)
  ZAZ ALD (5.5 nm) ─────────────────────── the film of this book
  TE TiN, SiGe fill, W strap, oxide cap
  Plate lithography (KrF resist on BARC)
  Plate conductor etch: cap → W → SiGe → TiN, stop on ZAZ (Book #32)
  In-situ strip (N₂/H₂, 250 °C)
  ► Dielectric clear: D1 (hot) or D2 (ALE) ◄ ────── this book
  Post-etch treatment (H₂O/N₂ remote plasma), rinse
  ILD deposition and CMP
  Periphery and plate contacts ──────────── the customer
```

### 1.6.2 The Routes

```
Route                     How                                   Where treated
─────────────────────────────────────────────────────────────────────────────────
R0  In-situ cold          last step of the plate etch: BCl₃/Cl₂  Book #32, Ch. 4, 12
                          at 150 eV, 60 °C, under resist
D1  Hot split (reference) separate chamber, 250 °C chuck,       Ch. 3, 5, 6, 10–12
                          BCl₃/Cl₂ at 70 eV, oxide cap as mask
D2  Plasma ALE            BCl₃/Cl₂ chlorination + Ar⁺ 60 eV,    Ch. 4, 7, 10
                          0.10 nm/cycle, 100 °C
T   Thermal ALE           HF fluorination + ligand exchange,    Ch. 4, 7, 11, 14
                          isotropic, 250–300 °C
W   Hybrid wet            dry to ≈ 1 nm, then a wet finish      Ch. 4, 10, 11
ASD Area-selective dep.   no ZAZ grown on the periphery         Ch. 14
```

Each route makes a different trade among residue tail, landing loss, edge attack, stringers, damage, and cost. Chapter 16 compares them by cost of ownership; Chapters 10 and 11 compare them by the two failure modes that matter most.

---

## 1.7 The Specification Sheet

```
Dielectric clear specification (reference, illustrative):

Parameter                              Target                 Protects against
─────────────────────────────────────────────────────────────────────────────────────
Zr on periphery SiN (TXRF average)     ≤ 1 × 10¹³ /cm²        gross under-etch
Residual islands (e-beam, ≥ 15 nm)     0 per inspected area   contact opens
Periphery contact opens attributable   < 0.01 per die         die loss
SiN landing loss                       ≤ 5 nm (ref 1.3 nm)    contact etch margin,
                                                              periphery planarity
Oxide cap loss                         ≤ 15 nm (ref ≈ 2 nm)   W exposure, plate contact
TE TiN lateral recess at plate edge    ≤ 3 nm (ref 1.2 nm)    edge field, ingress
ZAZ undercut under TE                  ≤ 2 nm                 edge void, ingress
SiGe / W lateral loss                  ≤ 3 nm / ≤ 2 nm        plate-edge profile, voids
Stringers on scribe topography         none free-standing     flakes, mark signal
B on SiN after PET                     ≤ 2 × 10¹⁴ /cm²        ILD adhesion, outgassing
Cl on SiN after PET                    ≤ 1 at%                corrosion, ILD adhesion
Array capacitor leakage shift          ≤ 10% at ±1 V          dielectric damage
Plate-edge comb leakage                ≤ 1 pA/mm at 1.1 V     edge damage, ingress
Backside Zr (exiting the module)       ≤ 1 × 10¹⁰ /cm²        cross-contamination
Particle adders (≥ 30 nm)              ≤ 10 per wafer         flakes, residues
Throughput (D1 chamber)                ≥ 30 wafers/h          cost
```

---

## 1.8 The Reference Process

The reference array, films, and plate are those of Book #32. What changes in this book is the route: the plate is etched under a 60 nm PE-TEOS oxide cap, the resist is stripped in situ, and the dielectric is cleared in a separate chamber.

```
Reference dielectric clear (illustrative):

Incoming:   periphery ZAZ 5.4 nm (ZrO₂ 2.55 / Al₂O₃ 0.3 / ZrO₂ 2.55),
            mixed tetragonal + monoclinic, grains 15–40 nm;
            on 120 nm periphery top SiN; oxide cap 60 nm on the plate

D1 (hot, ICP, ESC 250 °C, walls 120 °C):
  BT   BCl₃ 100 / Ar 50 sccm, 8 mTorr, 900 W / 200 W (≈ 100 eV)    3 s
  ME   BCl₃ 90 / Cl₂ 10 / Ar 50 sccm, 8 mTorr, 900 W / 120 W
       (≈ 70 eV), to endpoint                                        ≈ 33 s
  OE   same, 70% of the clearing time                                25 s
  Total                                                              61 s
  ZrO₂ 9.0 nm/min; SiN 3.0 nm/min; SiN loss 1.3 nm

D2 (plasma ALE, 100 °C):
  A  BCl₃/Cl₂ plasma, no bias, 1.5 s     B  Ar⁺ at 60 eV, 2.5 s
  purges 0.5 s each → 5.0 s per cycle; 0.10 nm/cycle in ZrO₂
  56 cycles nominal + 30% → 73 cycles, ≈ 6.1 min; SiN loss 0.2 nm

Post-etch treatment: remote H₂O/N₂ plasma, 250 °C, 30 s; DI rinse
```

---

## Summary and Key Takeaways

1. **The dielectric makes the capacitor.** 5.5 nm of ZAZ with EOT 0.50 nm gives 8.6 fF per cell and must pass less than 1 fA.

2. **ALD puts it everywhere.** About 1.4% of the film on the wafer lies outside the plate: on the periphery, scribe topography, bevel, and backside.

3. **Excess ZrO₂ opens contacts.** Fluorocarbon contact etches stop on it; one grain under one of 3 × 10⁷ contacts fails a die.

4. **The specification is a tail.** 99.93% removal meets the average; fewer than one grain in 10¹⁰ left meets the contacts.

5. **The plate edge must be preserved.** The cut face of the dielectric sits under a 5 nm TiN electrode exposed to the same chemistry.

6. **There are several routes.** In-situ cold, hot split, plasma ALE, thermal ALE, hybrid wet, and area-selective deposition each trade residue, landing loss, edge attack, stringers, and cost.

---

## Study Questions

1. Recompute C_s if the dielectric is changed to a 5.0 nm film with k_eff = 50 and the pillar average CD falls to 26 nm. What EOT is that?

2. A 1c-class array raises the surface enhancement factor to 95 and the plate coverage to 58%. What fraction of the deposited dielectric must now be removed?

3. Express a TXRF result of 4 × 10¹² Zr/cm² as a fraction of a monolayer. If all of it were concentrated in 1 nm-thick grains 25 nm across, how many grains per cm² would that be? How many under the contacts of one die (contact bottoms cover about 5 × 10⁻⁴ of the periphery area)?

4. List three reasons a BCl₃ breakthrough at the bottom of the periphery contact is a poor substitute for a dielectric clear at the plate.

5. Which lines of the specification sheet would be violated first if the dielectric clear were replaced with a wet etch in dilute HF? Which if it were replaced with Book #32's cold in-situ step?

6. The product team proposes cutting the plate overlap from 1.5 µm to 0.4 µm. Which three phenomena of this book must be quantified before the change can be approved?

---

**Next Chapter:** [Chapter 2: The Dielectric Stack — ZAZ Films, Phases, Interfaces & Incoming Surfaces](./02-dielectric-stack-films.md)

---

**Chapter 1 Development Status:** Complete  
**Version:** 1.0
