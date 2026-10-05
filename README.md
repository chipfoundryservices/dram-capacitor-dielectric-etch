# Book #33: DRAM Capacitor Dielectric Etch — Periphery Clearing, Cut-Edge Control, and Atomic-Layer Removal of ZrO₂-Based Node Dielectrics

## Overview

**Book #33** is a technical reference on **DRAM capacitor dielectric etch**: the removal of the high-k node dielectric from everywhere the capacitor does not need it. The dielectric of a stacked DRAM capacitor is a 5.5 nm laminate of zirconium oxide and aluminium oxide, ZrO₂ 2.6 nm / Al₂O₃ 0.3 nm / ZrO₂ 2.6 nm ("ZAZ"), with an equivalent oxide thickness of 0.50 nm. It is grown by atomic-layer deposition, and atomic-layer deposition does not know where the capacitors are. It coats seventeen billion TiN pillars per die, and with the same thickness it coats the periphery, the scribe lines, the alignment marks, the wafer bevel, and the edge of the backside.

Inside the array, about 2.2 m² of dielectric per wafer stores charge. Outside it, about 318 cm², roughly 1.4% of the film, does nothing useful and causes trouble. Crystallized ZrO₂ is an etch stop for the fluorocarbon chemistry of the periphery contacts, so a single grain left under one of thirty million contacts per die is an open circuit. Zirconium carried on the bevel and backside reaches lithography chucks and furnaces. Al₂O₃ blocks the hydrogen that later anneals passivate transistors with. The film must go, and it must go **completely**: the specification is set by the one grain in 10¹⁰ that survives, not by the average.

The film is hard to remove. Zr–O and Hf–O bonds are as strong as Si–O. The fluorides of Zr, Hf, and Al do not volatilize below 600 °C, so the fluorine chemistry of every oxide etch is useless against them. Only chlorides volatilize, and only with help: boron trichloride takes the oxygen, chlorine takes the metal, and ions or heat carry the products away. In a cold chamber this needs 150 eV ions and gives a selectivity to the underlying silicon nitride below one. **This book takes the dielectric etch out of the plate etch and gives it its own chamber**, heated to 250 °C so that 70 eV ions suffice and the selectivity to nitride reaches three, or replaces continuous etching with atomic-layer cycles that remove 0.1 nm at a time.

Removing the field film is half the job. The other half is **the edge**. Where the cell plate ends, the dielectric is cut, and its cut face sits under a 5 nm TiN top electrode whose sidewall is exposed to the same chlorine. Anisotropic etching clears flat surfaces and leaves the dielectric on every vertical face, as stringers 1.6 µm tall on scribe-line marks. Isotropic etching removes stringers and undercuts the edge. Every route trades one against the other.

**Remove 1.4% of the dielectric from the wafer, completely, without touching the 98.6% that stores the charge.** This book covers the chemistry, equipment, process phenomena, and production engineering of doing that.

---

## Intended Audience

This book is written for **semiconductor industry professionals** with working knowledge of plasma processing:

- **Process Engineers**: developing hot BCl₃/Cl₂ and atomic-layer recipes for high-k removal; controlling clearing, grain residue, nitride landing loss, plate-edge recess and undercut, stringers on topography, and halogen and boron residues
- **Equipment Engineers**: specifying heated-chuck ICP chambers, ALE-capable chambers with fast gas switching, thermal-ALE reactors, endpoint systems for a 5.5 nm film, chamber materials that survive BCl₃, bevel etchers, and zirconium contamination controls
- **Integration Engineers**: choosing between the in-situ cold high-k step, the split hot route, plasma ALE, thermal ALE, wet finishes, and area-selective deposition; setting the plate overlap and the hard-mask cap; owning the hand-off to the periphery contacts
- **Device Engineers**: understanding how residual grains, edge undercut, chlorine and hydrogen uptake, charging, and zirconium contamination appear as contact opens, plate leakage, retention tails, and transistor shifts
- **Researchers**: studying ion-assisted and thermal etching of metal oxides, ligand-exchange chemistry, clearing statistics of granular films, area-selective processing, and dielectric separation in 3D DRAM

The material assumes Books #1–5 (plasma fundamentals), Books #6–10 (dielectric etch), and Books #11–15 (advanced plasma engineering). **Book #32 (*DRAM Capacitor Electrode Etch*)** is the direct predecessor: its plate etch cuts the conductors that this book's etch lands beside, and its Chapter 4 introduces high-k etch chemistry at the level needed for an in-situ step. Book #29 (*DRAM Capacitor Hole Etch*) and Book #30 (*DRAM Capacitor Mold Etch*) build the array this book inherits. The companion volumes *Gate Oxide Etch* (high-k gate dielectric removal), *Silicon Nitride Etch*, and *Etch: The Sub-Nanometer Chisel* cover related chemistry and atomic-layer methods in more general settings.

---

## Technical Scope

### Core Concepts Covered

**Function & Films:**
- What the node dielectric does: capacitance, EOT, leakage, and the 1 fA per cell budget
- Where ALD puts it: array, periphery, scribe topography, bevel, and backside
- Why it must leave the periphery: contact opens, contamination, hydrogen blocking
- The ZAZ stack: precursors, crystallization, phases and grains on TiN and on SiN, the Al₂O₃ insertion, and the surfaces left by the plate etch

**Etch Chemistry:**
- Metal–oxygen bonds, halide volatility, and BCl₃ as an oxygen getter
- The etch–deposition transition, ion-assisted yield, and threshold energies
- Temperature: how heat lowers the threshold and raises selectivity to SiN and SiO₂
- Plasma ALE (chlorination and Ar⁺ removal), thermal ALE (fluorination and ligand exchange), conversion etching, and wet removal

**Equipment Design:**
- Heated-chuck ICP chambers at 250 °C; chamber materials that BCl₃ does not consume
- Temperature, ion energy, and clearing uniformity across the wafer and at its edge
- ALE-capable chambers with sub-second gas switching; thermal-ALE single-wafer and batch reactors
- Endpoint for a 5.5 nm film: zirconium, aluminium, and silicon emission markers; cycle counting; in-situ ellipsometry
- Boron and zirconium wall deposits, seasoning, cross-contamination, and bevel removal

**Process Phenomena:**
- Clearing statistics, grain residue, micromasking, and stringers on vertical faces
- The cut edge: top-electrode recess, dielectric undercut, halogen ingress, and the plate-edge void
- Selectivity to the landing nitride, the oxide cap, and the plate sidewall
- Damage to the remaining dielectric: charging, chlorine, hydrogen, ultraviolet light, and heat
- Advanced schemes: TiO₂, SrTiO₃, Nb₂O₅, and HfO₂–ZrO₂ dielectrics; area-selective deposition; dielectric separation in 3D DRAM

**Production Integration:**
- Metrology for sub-monolayer residue: TXRF and its VPD blind spot, XPS, LEIS, e-beam inspection
- Electrical monitors: periphery contact chains, plate-edge combs, capacitor arrays
- Feed-forward of dielectric thickness and phase; EWMA control of overetch and cycle count
- Yield signatures, equipment sizing, and cost of ownership for each route

### Technology Context

- **Device architectures:** 6F² buried-channel DRAM from the 1x to the 1c generation (DDR5, LPDDR5X, HBM core dies); 4F² vertical-channel and 3D DRAM as emerging forms
- **Dielectric stacks:** ZrO₂/Al₂O₃/ZrO₂ on TiN (primary focus); HfO₂–ZrO₂ laminates; TiO₂ and SrTiO₃ on Ru; Nb₂O₅-inserted ZrO₂
- **Process sequence:** The dielectric is deposited after Book #30's mold dip-out and before the top electrode. It is etched after Book #32's plate conductor etch has stopped on it, and before the inter-layer dielectric and the periphery contacts
- **Manufacturing scale:** 300 mm wafers; one dielectric clear per wafer, about 1 min of plasma in the hot route and about 6 min of cycling in the ALE route

---

## Book Organization

### Part I: Fundamentals (4 Chapters)

**Chapter 1: The Capacitor Dielectric & Why It Is Etched**
- What the node dielectric does and how little leakage it may pass
- Where atomic-layer deposition puts it, and how much of it is useless
- Why it must leave the periphery, the scribe, and the bevel
- The four routes, their place in the flow, and the specification sheet

**Chapter 2: The Dielectric Stack — ZAZ Films, Phases, Interfaces & Incoming Surfaces**
- ALD of ZrO₂ and Al₂O₃; growth on TiN and on SiN
- Crystallization: tetragonal, monoclinic, and amorphous; grains and boundaries
- What the plate etch and the strip leave on top; what lies beneath
- The dielectric on topography and on the bevel; incoming variation

**Chapter 3: Plasma Chemistry of Metal-Oxide Etching**
- Bonds, halide volatility, and the thermochemistry of chlorination
- BCl₃ as an oxygen getter; the etch–deposition transition
- Ion-assisted yield and how temperature lowers the threshold
- Selectivity to SiN, SiO₂, and the plate sidewall

**Chapter 4: Atomic-Layer, Thermal & Wet Removal of High-k Films**
- Plasma ALE: the self-limiting window and synergy
- Thermal ALE: fluorination and ligand exchange; isotropy
- Conversion etching and crystallinity
- Wet and vapor removal; comparison of the routes

### Part II: Hardware Design (5 Chapters)

**Chapter 5: Heated-Chuck ICP Chambers for Dielectric Clearing**
- Why a separate chamber, and why ICP
- Chucks at 250 °C; heat-up, clamping, and backside gas
- Walls, windows, and liners that BCl₃ does not consume
- The hot chamber on the plate-etch mainframe

**Chapter 6: Temperature, Ion Energy & Clearing Uniformity**
- Sensitivity of rate to temperature and to ion energy near threshold
- Zone control and the edge ring
- Clearing-time spread and the overetch it demands
- Uniformity in ALE: what self-limitation does and does not fix

**Chapter 7: ALE & Thermal-Etch Reactors**
- Fast gas switching, purges, and RF synchronization
- Ion-energy control for the removal step
- Thermal-ALE reactors: precursor delivery, single-wafer and batch designs
- Matching and qualification of cyclic processes

**Chapter 8: Endpoint & In-Situ Monitoring of a 5.5 nm Film**
- Optical emission: zirconium, aluminium, silicon, and boron markers
- The Al marker and the landing signal
- Interferometry, in-situ ellipsometry, and why reflectance barely moves
- Cycle counting and monitors for ALE

**Chapter 9: Walls, Boron Deposits, Zirconium Contamination & the Bevel**
- BₓClᵧ, boron oxychloride, and ZrClₓ on the walls
- Seasoning, waferless cleans, and the fluorine trap
- Zirconium cross-contamination: sources, limits, and backside control
- The bevel and backside: ALD wrap and its removal

### Part III: Process Phenomena (5 Chapters)

**Chapter 10: Clearing the Periphery — Grain Residue, Micromasking & Stringers**
- How a mixed-phase film clears; the Gaussian tail and the overetch
- Non-Gaussian residue: carbon, titanium, boron, and particles
- Stringers on vertical faces and the isotropic finish
- The contact-open budget

**Chapter 11: The Cut Edge — Top-Electrode Recess, Undercut & Ingress**
- Geometry of the plate edge after the conductor etch
- Lateral attack of TiN, SiGe, and W at 250 °C; sidewall passivation
- Dielectric undercut by isotropic routes
- Halogen and moisture ingress, the edge void, and the plate overlap

**Chapter 12: Selectivity & the Materials Around the Dielectric**
- The landing nitride: loss, boron, chlorine, and surface state
- The oxide cap and the hard-mask budget
- Dielectric within the stack: Al₂O₃ versus ZrO₂
- Surfaces handed to the inter-layer dielectric; post-etch treatment

**Chapter 13: Damage to the Remaining Dielectric**
- The floating plate and the sidewall antenna
- Chlorine and hydrogen uptake; oxygen vacancies
- Ultraviolet light and heat
- Leakage, breakdown, retention, and their test structures

**Chapter 14: Advanced Schemes — Higher-k Films, Area-Selective Deposition, 4F² & 3D DRAM**
- TiO₂, SrTiO₃, Nb₂O₅, and HfO₂–ZrO₂ dielectrics and how each etches
- Area-selective deposition: a dielectric that is never in the periphery
- ALE-based thickness trimming
- Dielectric separation in vertical and lateral capacitors

### Part IV: Production Scale (2 Chapters)

**Chapter 15: Metrology, Inspection & Advanced Process Control**
- Measuring a hundredth of a monolayer: TXRF, VPD, XPS, LEIS
- Finding single grains: e-beam inspection and contact-chain voltage contrast
- Edge and damage metrology
- Feed-forward, feedback, and fault detection

**Chapter 16: Integration, Yield & Cost of Ownership**
- From the plate etch to the periphery contacts
- Yield signatures of the dielectric etch
- Equipment sizing and throughput
- Cost of ownership for the in-situ, hot, ALE, thermal-ALE, and hybrid routes

---

## Key Technical Themes

1. **The film has no job outside the plate.** 1.4% of the dielectric on the wafer is in the wrong place; every atom of it must go.
2. **Fluorine cannot do it.** ZrF₄, HfF₄, and AlF₃ do not volatilize. Boron takes the oxygen, chlorine takes the metal, and ions or heat take the products.
3. **Heat buys selectivity.** At 250 °C the ZrO₂ threshold falls from about 60 to 25 eV, the etch runs at 70 eV, and selectivity to SiN rises from 0.75 to 3.
4. **Clearing is a tail.** The overetch beats the Gaussian spread of grain clearing times by seven sigma; what remains are carbon, titanium, boron, and particle micromasks, which must be controlled at their source.
5. **Anisotropy leaves stringers; isotropy undercuts the edge.** The choice of route is a choice of which of the two to accept.
6. **The chamber is made of what it etches.** Y₂O₃ and Al₂O₃ parts meet BCl₃ too; zirconium leaves on the walls and on the bevel, and travels.

---

## Cross-References to Prior Books

**Related Books in the Series:**

- **Books #1–5** (Plasma Physics & Chemistry Fundamentals): sheaths, ion energy, radical generation
- **Books #6–10** (Dielectric Etch & Fluorocarbon Chemistry): why fluorocarbon contact etches stop on ZrO₂
- **Books #11–15** (Advanced Plasma Engineering): RF delivery, chucks, endpoint, chamber matching
- **Book #29** (DRAM Capacitor Hole Etch): the holes and the reference array
- **Book #30** (DRAM Capacitor Mold Etch): the free-standing pillars the dielectric coats
- **Book #31** (DRAM High-Aspect-Ratio Capacitor Etch): taller capacitors and their dielectrics
- **Book #32** (DRAM Capacitor Electrode Etch): the plate conductor etch that stops on the dielectric, and the in-situ high-k step that this book replaces
- **Companion volumes:** *Gate Oxide Etch* (HfO₂ gate dielectric removal), *Silicon Nitride Etch*, *Etch: The Sub-Nanometer Chisel* (atomic-layer etching), *Aluminum Metal Etch* (BCl₃ chambers, fences, and corrosion)

Book #32 cut the conductors of the plate and stopped on the dielectric. This book removes the dielectric they leave behind.

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
│   ├── 03-metal-oxide-plasma-chemistry.md
│   ├── 04-ale-thermal-wet-removal.md
│   ├── 05-heated-chuck-icp-chambers.md
│   ├── 06-temperature-ion-energy-uniformity.md
│   ├── 07-ale-thermal-etch-reactors.md
│   ├── 08-endpoint-in-situ-monitoring.md
│   ├── 09-walls-boron-zirconium-bevel.md
│   ├── 10-periphery-clearing-residue-stringers.md
│   ├── 11-cut-edge-recess-undercut-ingress.md
│   ├── 12-selectivity-surrounding-materials.md
│   ├── 13-damage-remaining-dielectric.md
│   ├── 14-advanced-dielectric-schemes.md
│   ├── 15-metrology-inspection-apc.md
│   └── 16-integration-yield-coo.md
│
└── appendices/
    ├── A-material-properties.md
    ├── B-chemistry-thermochemistry-data.md
    ├── C-standard-procedures.md
    ├── D-process-windows.md
    ├── E-clearing-ale-edge-calculations.md
    ├── F-metrology-reference.md
    └── G-troubleshooting-guide.md
```

---

## Constraints & Scope

### What This Book Covers
✅ Removal of ZrO₂-based capacitor dielectrics from the periphery after the plate conductor etch, by hot continuous plasma etching (primary focus) and plasma ALE  
✅ Thermal ALE, wet, vapor, and hybrid removal as alternatives and finishing steps  
✅ Chemistry, chambers, endpoint, wall management, and contamination control for high-k removal  
✅ Clearing statistics, residue, stringers, plate-edge recess and undercut, selectivity, and damage  
✅ Higher-k dielectrics, area-selective deposition, ALE trimming, 4F² and 3D DRAM  
✅ Metrology, electrical monitors, yield, and cost of ownership  

### What This Book Does NOT Cover
❌ The plate conductor etch (W, SiGe, TiN) in detail (see Book #32)  
❌ Storage-node separation (see Book #32) and the mold etch (see Book #30)  
❌ ALD precursor chemistry and dielectric deposition hardware in detail  
❌ The periphery contact etch itself, except as the customer of clearing  
❌ High-k gate stacks of logic transistors, except as comparison  
❌ Vendor-specific recipes or proprietary tool parameters  

### A Note on Numbers
Numbers in this book come from established thermochemistry and plasma–surface models, published etch-rate and ALE data and literature trends, and representative production practice. Worked examples use **illustrative values** chosen to show the method, and the arithmetic is written out so readers can substitute their own data. A single **reference process** is used across chapters so that examples connect. It inherits the array of Books #29, #30, and #32: a 1b-class 6F² cell (F = 17 nm, cell area 1734 nm²) on a 45 nm hexagonal storage-node pitch, a 1.60 µm mold, solid TiN pillars 32/28/24 nm wide, and C_s = 8.6 fF. The dielectric is **ZAZ**: ZrO₂ 2.6 nm / Al₂O₃ 0.3 nm / ZrO₂ 2.6 nm, EOT 0.50 nm, tetragonal on TiN and about 5.4 nm of mixed tetragonal and monoclinic film on the periphery SiN. The plate (5 nm TiN, 150 nm B-doped Si₀.₇Ge₀.₃, 40 nm W) is capped with **60 nm of PE-TEOS oxide**, etched in Book #32's conductor chemistry to a stop on the ZAZ, and stripped in situ. Two dielectric-clear processes are carried through the book. **D1** is a hot continuous etch in an ICP chamber with the chuck at 250 °C: a 3 s BCl₃/Ar breakthrough at about 100 eV, then BCl₃/Cl₂/Ar (90/10/50 sccm, 8 mTorr) at about 70 eV, clearing in 36 s with a 70% (25 s) overetch, ZrO₂ at 9.0 nm/min, SiN at 3.0 nm/min, and 1.3 nm of SiN lost. **D2** is plasma ALE at 100 °C: BCl₃/Cl₂ chlorination without bias, then Ar⁺ at 60 eV, 5.0 s per cycle and 0.10 nm per cycle in ZrO₂, 73 cycles in about 6 min, and 0.2 nm of SiN lost. The plate covers 55% of the wafer in 32 islands per die. Treat recipe values as starting points for a design of experiments, never as qualified process conditions.

---

## Development Status

**Book #33 Foundation:** Complete  
**Part I (Chapters 1–4):** Complete  
**Part II (Chapters 5–9):** Complete  
**Part III (Chapters 10–14):** Complete  
**Part IV (Chapters 15–16):** In progress  
**Back Matter (Appendices A–G, Glossary):** In progress  

---

## Next Steps

1. **Read [PREFACE.md](./PREFACE.md)** for the motivation and reading guidance
2. **Read [INDEX.md](./INDEX.md)** for the detailed chapter outline and reading paths by role
3. **Begin [Chapter 1](./chapters/01-capacitor-dielectric-role.md)**: The Capacitor Dielectric & Why It Is Etched

---

**Book #33 Version:** 1.0  
**Last Updated:** 2026-10-05  
**Series:** ChipFoundryServices Technical Series
