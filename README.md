# Book #33: DRAM Capacitor Dielectric Etch — Clearing, Trimming, and Edge Removal of ZrO₂/Al₂O₃ High-k Capacitor Dielectrics

## Overview

**Book #33** is a technical reference on **DRAM capacitor dielectric etch**: every etch whose target is the high-k film between the two electrodes of the storage capacitor. The capacitor dielectric is the most carefully made film in the DRAM: 5.5 nm of zirconia and alumina, laid down one atomic layer at a time over seventeen billion pillars per die, with a leakage specification of one femtoampere per cell. It is deposited by atomic-layer deposition, which coats everything it can reach. Most of what it reaches is not a capacitor.

The dielectric must therefore be **removed** where it does not belong, and, in the most advanced flows, **thinned** where it does. Three etches do this work:

**Bevel and backside removal.** ALD wraps the dielectric over the wafer apex and 2–3 mm onto the backside, under the top-electrode TiN. Left there, it becomes a source of zirconium on every wafer handler, chuck, and furnace boat downstream, and the base of a film stack that flakes. A confined bevel plasma must remove 5.5 nm of crystallized ZrO₂ from a ring 1.2 mm wide on the front, from the apex, and from the backside edge, at ion energies barely above the point where BCl₃ plasmas stop etching and start depositing, and must end the film on the front with a boundary placed to ±0.1 mm.

**Periphery clearing.** At the end of the plate etch, the dielectric lies exposed over 45% of the wafer: the periphery and the scribe lines. Every grain of it must go, because a ZrO₂ grain left at the bottom of any of thirty million periphery contacts per die will stop that contact etch dead. A continuous BCl₃ etch removes most of the film quickly but leaves a tail of grains whose spread it created itself; an atomic-layer finish removes that tail at a tenth of the SiN loss and half the high-energy ion dose, and at the cost of two and a half minutes per wafer.

**In-array trim.** At the 1c generation and beyond, the gap between pillars is too narrow for the dielectric to be deposited at its best thickness. A thicker film crystallizes better and leaks less. Isotropic thermal atomic-layer etching can deposit thick, crystallize, and trim back by a nanometre, everywhere, inside a forest of pillars whose open channels are 200 times deeper than they are wide, without opening a single grain boundary into a leakage path.

**Three etches, one film, and a film that is the capacitor.** This book covers the chemistry, equipment, process phenomena, and production engineering of all three.

---

## Intended Audience

This book is written for **semiconductor industry professionals** with working knowledge of plasma processing:

- **Process Engineers**: developing BCl₃-based high-k clearing recipes, plasma and thermal atomic-layer etch finishes and trims, and bevel high-k removal; controlling grain residue, SiN loss, plate-edge integrity, bevel boundary placement, and halogen and boron uptake
- **Equipment Engineers**: specifying ICP chambers with narrow ion-energy distributions and fast gas switching, heated chucks, confined bevel-plasma systems, thermal ALE reactors, and endpoint systems for nanometre films; cleaning zirconium, aluminium, and boron from chamber walls and from the ALD reactors that make the film
- **Integration Engineers**: choosing among continuous, ALE-finished, hot, and wet-hybrid clearing; setting the bevel edge exclusion; deciding whether a trim earns its place; and managing the hand-offs to the periphery contacts and the back-end
- **Device Engineers**: understanding how grain residue, edge damage, chlorine, boron, fluorine, and trimmed grain boundaries appear as contact opens, edge leakage, retention tails, and dielectric breakdown
- **Researchers**: studying ion-assisted chlorination of refractory oxides, the etch–deposition transition in BCl₃ plasmas, plasma and thermal ALE of high-k oxides, reactant transport in extreme-aspect-ratio gaps, and the statistics of clearing granular films

The material assumes Books #1–5 (plasma fundamentals), Books #6–10 (dielectric etch), and Books #11–15 (advanced plasma engineering). **Book #32 (*DRAM Capacitor Electrode Etch*)** patterns the plate whose last step this book's periphery clear completes, and treats the high-k step as one of four films in the plate stack; this book treats the dielectric itself as the subject and shares Book #32's reference array. **Book #29 (*DRAM Capacitor Hole Etch*)** and **Book #30 (*DRAM Capacitor Mold Etch*)** make the pillars the dielectric coats; **Book #31 (*DRAM High-Aspect-Ratio Capacitor Etch*)** carries them taller. The companion volumes *Gate Oxide Etch* (high-k gate dielectric removal) and *Etch Chamber Design* cover related problems in other settings.

---

## Technical Scope

### Core Concepts Covered

**The Dielectric & Its Films:**
- Capacitance, EOT, and leakage: what the dielectric is for, and what an etch can cost it
- ZAZ and its relatives: ZrO₂, Al₂O₃, HfO₂, doped and laminated stacks, phases and grains
- ALD conformality and wrap: where the film goes that the capacitor does not need
- The five places the dielectric meets an etch: periphery, plate edge, bevel, backside, and the channels between pillars

**Etch Chemistry:**
- Thermochemistry of refractory-oxide halogenation; why fluorides fail and chlorides need help
- BCl₃ as oxygen getter; the etch–deposition transition and its sensitivity to ion energy and temperature
- Orientation, grain boundaries, and the spread a continuous etch creates
- Plasma ALE: BCl₃ modification and Ar⁺ removal; the ALE window and synergy
- Thermal ALE: fluorination and ligand exchange with HF and DMAC; isotropy and selectivity

**Equipment Design:**
- ICP chambers for nanometre removal: narrow ion-energy distributions and fast gas switching
- Chuck temperature and the uniformity of continuous and cyclic etches
- Confined bevel-plasma systems: exclusion rings, boundary placement, and bevel ion energy
- Endpoint and in-situ monitoring for films thinner than their own noise
- Wall chemistry, boron and zirconium contamination, and the cleaning of high-k ALD reactors

**Process Phenomena:**
- Periphery clearing: residue statistics, the main-step tail, the ALE finish, SiN landing, veils
- The two edges of the dielectric: the plate edge in every die and the bevel at the wafer edge
- In-array trim: transport of HF and DMAC into 200:1 channels between pillars, top-to-bottom uniformity, grain-boundary attack
- Process-induced damage: edge exposure, halogen and boron incorporation, charging, fluorine, recovery, reliability
- Advanced dielectrics and architectures: HfO₂/ZrO₂ laminates, TiO₂ and SrTiO₃, antiferroelectric HZO, 4F² and 3D DRAM

**Production Integration:**
- Metrology and inspection: TXRF, VPD-ICP-MS, XPS, XRR, TEM-EELS, bevel inspection, electrical monitors
- Feed-forward of dielectric thickness; ALE cycle control; fault detection on cyclic signals
- Yield signatures, equipment sizing, and cost of ownership of each route

### Technology Context

- **Device architectures:** 6F² buried-channel DRAM from the 1x to the 1c generation (DDR5, LPDDR5X, HBM core dies); 4F² vertical-channel and 3D DRAM as emerging forms
- **Dielectrics:** ZrO₂/Al₂O₃/ZrO₂ (ZAZ, primary focus); HfO₂/ZrO₂ laminates, doped ZrO₂, TiO₂-based and SrTiO₃-class films as the alternatives
- **Process sequence:** The bevel removal follows the dielectric ALD and the TiN top electrode and precedes the SiGe plate fill. The periphery clear is the last step of the plate etch and precedes the inter-layer dielectric and the periphery contacts. The in-array trim, where used, follows the dielectric crystallization anneal and precedes the top electrode
- **Manufacturing scale:** 300 mm wafers; one bevel removal (about 3 min of plasma), one periphery clear (about 4 min of plasma), and, in the pilot flow, one in-array trim (about 10 min in a batch-capable thermal reactor) per wafer

---

## Book Organization

### Part I: Fundamentals (4 Chapters)

**Chapter 1: The Capacitor Dielectric & Why It Is Etched**
- What the dielectric does: capacitance, EOT, leakage, retention
- Why ALD puts it everywhere, and the five places it meets an etch
- Why a grain at a contact, a film on the bevel, and a nanometre in the gap each matter
- The three dielectric etches and their specification sheet

**Chapter 2: The Dielectric Stack — Films, Phases, Interfaces & Wrap**
- The ZAZ stack: ALD of ZrO₂ and Al₂O₃, thickness, and EOT
- Crystallization, phases, grains, and grain boundaries
- The interfaces with TiN, and what the top electrode does to the film
- Conformality in the array, wrap onto the bevel and backside, and incoming variation

**Chapter 3: Halide Plasma Chemistry of High-k Oxides**
- Thermochemistry and volatility of Zr, Hf, Al, Ti, and Sr halides
- BCl₃ chemistry: oxygen gettering, deposition, and the transition between them
- Ion-assisted kinetics, orientation dependence, and the spread a continuous etch creates
- Selectivity to SiN, TiN, oxide, and resist; temperature

**Chapter 4: Atomic-Layer & Thermal Etching of High-k**
- The ALE cycle, its window, and its synergy
- Plasma ALE with BCl₃ and Ar⁺: modification, removal, and what limits each
- Thermal ALE with HF and DMAC: fluorination, ligand exchange, and isotropy
- Selectivity, smoothing, and what ALE cannot do

### Part II: Hardware Design (5 Chapters)

**Chapter 5: ICP Chambers & Ion-Energy Control for Nanometre Removal**
- Why the clearing chamber is an ICP
- Ion-energy distributions: sinusoidal, tailored, and pulsed bias
- Fast gas switching and the ALE cycle
- Throughput of cyclic etch

**Chapter 6: Chuck Temperature, Uniformity & the Clearing-Time Map**
- Temperature dependence of the continuous and the cyclic steps
- Building the clearing-time map from thickness and rate
- Edge rings, edge ion energy, and the slowest site
- Matching chambers on a nanometre film

**Chapter 7: Bevel Etch Systems for High-k Removal**
- The wafer edge and where the dielectric goes there
- Confined bevel plasmas: exclusion rings, gaps, and the boundary
- Bevel ion energy, BCl₃ deposition, and the bevel recipe
- Centring, boundary placement, and throughput

**Chapter 8: Endpoint & In-Situ Monitoring for Nanometre Dielectrics**
- Emission from Zr, Al, B, and the landing SiN
- The clearing curve and what it measures
- Cycle-resolved signals in ALE; reflectometry and ellipsometry on test pads
- Bevel and trim monitoring; failure modes

**Chapter 9: Walls, Boron, Metal Contamination & ALD-Reactor Cleaning**
- Zr, Al, and B on the chamber wall; seasoning and first-wafer effects
- Cleaning order and chemistry
- Zirconium cross-contamination: limits, paths, and the bevel's share
- Cleaning the ALD reactor that made the film

### Part III: Process Phenomena (5 Chapters)

**Chapter 10: Periphery Clearing — Residue Statistics, the ALE Finish & SiN Landing**
- Where the last dielectric is, and why
- The tail the main step creates and the finish that removes it
- SiN landing, boron and chlorine on the landing film, veils
- Comparison of continuous, ALE-finished, hot, and wet-hybrid routes

**Chapter 11: The Two Edges — Plate Edge & Wafer Bevel**
- The exposed dielectric edge at the plate: lateral etch, undercut, and uptake
- The bevel boundary: transition zone, partial films, and flakes
- Post-etch treatments for both edges
- Edge leakage and edge defects

**Chapter 12: In-Array Dielectric Trim by Thermal ALE**
- Why trim: thickness, crystallinity, and the gap
- Transport of HF and DMAC into 200:1 channels between pillars
- Top-to-bottom uniformity and saturation
- Grain boundaries, roughness, fluorine, and leakage

**Chapter 13: Process-Induced Damage & Dielectric Reliability**
- What each etch does to the film it leaves
- Charging, ultraviolet light, halogens, boron, hydrogen, and fluorine
- Leakage, TDDB, and retention tails
- Recovery anneals and test structures

**Chapter 14: Advanced Dielectrics & Architectures**
- HfO₂/ZrO₂ laminates and doped ZrO₂
- TiO₂ and SrTiO₃: when the metal is volatile and when it is not
- Antiferroelectric and ferroelectric HZO
- 4F² vertical-channel and 3D DRAM: lateral dielectric removal

### Part IV: Production Scale (2 Chapters)

**Chapter 15: Metrology, Inspection & Advanced Process Control**
- Measuring what is not there: TXRF, VPD-ICP-MS, XPS, and contact chains
- Thickness and profile: XRR, ellipsometry, TEM-EELS, bevel inspection
- Electrical monitors for the dielectric
- Feed-forward, ALE cycle control, and fault detection

**Chapter 16: Integration, Yield & Cost of Ownership**
- Hand-offs: to the SiGe fill, to the periphery contacts, to the back-end
- Yield signatures of each dielectric etch
- Equipment sizing and cost of ownership
- Route decisions and the new-product checklist

---

## Key Technical Themes

1. **The film is the device.** Every etch in this book either removes the dielectric where it is not a capacitor or touches it where it is. The second kind has no margin for damage.
2. **Clearing is a tail problem.** The specification is a grain in 10¹⁰, not an average. The tail is set by the main step; a finish decides only how gently it is removed.
3. **Refractory oxides need boron and ions.** Fluorides do not volatilize; chlorides need BCl₃ to take the oxygen and ions to take the chloride. Below about 60 eV, BCl₃ deposits instead of etching.
4. **The ALE finish trades time for gentleness.** It removes the residue tail with a tenth of the SiN loss and half the high-energy ion dose, at about 1.3 nm per minute.
5. **ALD goes everywhere.** The bevel and the backside carry the dielectric unless an etch removes it, and the boundary of that removal is a film edge of its own.
6. **Trimming a crystal attacks its boundaries.** An isotropic etch that thins a crystallized film by a nanometre thins its grain boundaries by more.

---

## Cross-References to Prior Books

**Related Books in the Series:**

- **Books #1–5** (Plasma Physics & Chemistry Fundamentals): sheaths, ion energy, radical generation
- **Books #6–10** (Dielectric Etch & Fluorocarbon Chemistry): the fluorocarbon chemistry of the later periphery contacts, which stop on any surviving ZrO₂
- **Books #11–15** (Advanced Plasma Engineering): RF delivery, tailored waveforms, chucks, endpoint, chamber matching
- **Book #29** (DRAM Capacitor Hole Etch): the holes, the mold, and the reference array
- **Book #30** (DRAM Capacitor Mold Etch): the freestanding pillars and supports the dielectric coats
- **Book #31** (DRAM High-Aspect-Ratio Capacitor Etch): taller capacitors and narrower gaps
- **Book #32** (DRAM Capacitor Electrode Etch): the plate etch whose last step is this book's periphery clear; plasma-induced damage through the plate
- **Companion volumes:** *Gate Oxide Etch* (high-k gate dielectric removal), *Etch Chamber Design* (ICP and bevel hardware), *Silicon Nitride Etch* (the landing film)

Book #32 cut the electrodes. This book removes the film between them from everywhere it is not wanted, and thins it where it is.

---

## File Organization

```
dram-capacitor-dielectric-etch/
├── README.md            ← You are here
├── PREFACE.md
├── INDEX.md
├── GLOSSARY.md
│
├── chapters/
│   ├── 01-capacitor-dielectric-role.md
│   ├── 02-dielectric-stack-films.md
│   ├── 03-high-k-halide-plasma-chemistry.md
│   ├── 04-atomic-layer-thermal-etching.md
│   ├── 05-icp-chambers-ion-energy-control.md
│   ├── 06-chuck-temperature-uniformity.md
│   ├── 07-bevel-etch-systems.md
│   ├── 08-endpoint-monitoring-nanometre-dielectrics.md
│   ├── 09-walls-contamination-ald-reactor-cleaning.md
│   ├── 10-periphery-clearing-residue-ale-finish.md
│   ├── 11-dielectric-edges-plate-bevel.md
│   ├── 12-in-array-dielectric-trim.md
│   ├── 13-process-induced-damage-reliability.md
│   ├── 14-advanced-dielectrics-architectures.md
│   ├── 15-metrology-inspection-apc.md
│   └── 16-integration-yield-coo.md
│
└── appendices/
    ├── A-material-properties.md
    ├── B-chemistry-thermochemistry-data.md
    ├── C-standard-procedures.md
    ├── D-process-windows.md
    ├── E-clearing-ale-transport-calculations.md
    ├── F-metrology-reference.md
    └── G-troubleshooting-guide.md
```

---

## Constraints & Scope

### What This Book Covers
✅ Dry removal of crystallized ZAZ from the periphery at the end of the plate etch, by continuous BCl₃/Cl₂ etch with a plasma-ALE finish (primary focus), with continuous-overetch, hot-chuck, and wet-hybrid routes as comparison  
✅ Confined-plasma removal of the dielectric and top-electrode TiN from the wafer bevel and backside edge  
✅ Thermal ALE trim of the dielectric inside the array (pilot flow, 1c-class)  
✅ Etch chemistry, chambers, bevel systems, endpoint, and wall and reactor cleaning  
✅ Residue, edge, transport, grain-boundary, and damage phenomena; reliability  
✅ Alternative dielectrics, 4F² and 3D DRAM, metrology, yield, and cost of ownership  

### What This Book Does NOT Cover
❌ The conductor steps of the plate etch (W, SiGe, TiN; see Book #32)  
❌ Storage-node separation (see Book #32), the hole etch (Books #29 and #31), or the mold etch (Book #30)  
❌ ALD precursor chemistry and deposition kinetics, except where they set what the etch inherits  
❌ The periphery contact etch itself, except as the customer of the periphery clear  
❌ Vendor-specific recipes or proprietary tool parameters  

### A Note on Numbers
Numbers in this book come from established thermochemistry and plasma–surface models, published etch-rate and atomic-layer-etch data and literature trends, and representative production practice. Worked examples use **illustrative values** chosen to show the method, and the arithmetic is written out so readers can substitute their own data. A single **reference process** is used across chapters so that examples connect. It inherits the array of Books #29–32: a 1b-class 6F² cell (F = 17 nm, cell area 1734 nm²) on a 45 nm hexagonal storage-node pitch, a 1.60 µm mold, and solid TiN pillars 32/28/24 nm wide (top/average/bottom). The dielectric is ZAZ, ZrO₂ 2.6 nm / Al₂O₃ 0.3 nm / ZrO₂ 2.6 nm (5.5 nm, k_eff ≈ 43, EOT 0.50 nm), tetragonal after the SiGe fill, giving C_s = 8.6 fF over an effective area of 1.24 × 10⁵ nm² per cell. **Module 1 (bevel)** removes 5 nm of top-electrode TiN and the ZAZ from front radius ≥ 148.8 mm, the apex, and the backside to radius 147.0 mm in a confined bevel plasma (Cl₂/Ar 15 s; BCl₃/Cl₂/Ar at 0.8 Torr and ≈ 90 eV, 150 s; O₂/N₂ 20 s). **Module 2 (periphery clear)** follows the plate conductor steps of Book #32 under 500 nm of KrF resist: a TiN clear in Cl₂/Ar (10 s), a timed BCl₃/Cl₂/Ar main step at 150 eV and 60 °C (45 s, 4.4 nm), and a plasma-ALE finish of 36 cycles of BCl₃ dose and 60 eV Ar⁺ (4.5 s each, 0.10 nm per cycle, 162 s), landing on the periphery top SiN with about 0.4 nm loss, then an O₂/H₂O strip and treatment. **Module 3 (in-array trim, pilot)** deposits ZAZ at 6.5 nm, crystallizes it, and removes 1.0 nm of the top ZrO₂ by thermal ALE with HF and DMAC at 250 °C (17 cycles at 0.06 nm). Treat recipe values as starting points for a design of experiments, never as qualified process conditions.

---

## Development Status

**Book #33 Foundation:** Complete  
**Part I (Chapters 1–4):** Complete  
**Part II (Chapters 5–9):** Complete  
**Part III (Chapters 10–14):** Complete  
**Part IV (Chapters 15–16):** Planned  
**Back Matter (Appendices A–G, Glossary):** Planned  

---

## Next Steps

1. **Read [PREFACE.md](./PREFACE.md)** for the motivation and reading guidance
2. **Begin [Chapter 1](./chapters/01-capacitor-dielectric-role.md)**: The Capacitor Dielectric & Why It Is Etched

---

**Book #33 Version:** 1.0  
**Last Updated:** 2026-10-05  
**Series:** ChipFoundryServices Technical Series
