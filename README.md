# Book #33: DRAM Capacitor Dielectric Etch — Removing, Stopping on, and Thinning the ZrO₂/Al₂O₃/ZrO₂ High-k Film of Stacked DRAM Capacitors

## Overview

**Book #33** is a technical reference on **DRAM capacitor dielectric etch**: the etches whose target, or whose stop layer, is the 5.5 nm high-k film that insulates every storage capacitor. The film is ZrO₂/Al₂O₃/ZrO₂ ("ZAZ"). It is grown by atomic-layer deposition on everything the wafer exposes: the outside of seventeen billion pillars, the periphery, the scribe lines, the bevel, and the backside edge. It is needed in exactly one place, the array. Everywhere else it is a liability, and it is among the hardest films in the fab to remove.

Book #32 (*DRAM Capacitor Electrode Etch*) treats the dielectric clear as the last step of the plate etch. This book takes the dielectric out of that role and treats it as four etches of its own.

**Edge etch (Module E)** removes the ZAZ from the outer 3 mm of the wafer, the bevel, and the backside edge, while the film is still amorphous and before the top electrode buries it. There is no mask. Without it, 1.4 × 10¹⁶ zirconium atoms per cm² ride on the backside of every wafer into the next chuck and the next furnace; the limit is 10¹⁰, six decades lower.

**Periphery clear (Module P)** removes the ZAZ from the periphery and scribe after the plate is cut. The conductor etch must stop on 5.5 nm of dielectric with a loss under 0.3 nm, which needs a TiN-to-ZAZ selectivity of 18. The resist is then stripped, and the plate itself becomes the mask for a hot, low-energy clear. That route takes the high-k step out of the resist budget and out of the veil problem, and puts a 2.3 nm loss on the tungsten strap, a charging clamp of 1.3 V, and a 1.8 nm titanium-oxide shell in their place.

**Trim and rework (Module T)** thins or strips the ZAZ with plasma-free thermal atomic-layer etching, at 0.07 nm per cycle. Thinning by 0.2 nm raises C_s by 3.8% and the leakage by 2.8×. The trade shows why this is a recovery tool and not a tuning knob.

**ALD-chamber clean (Module C)** removes zirconia from the deposition tool's walls. It is a dielectric etch too, and the same rule applies: chlorine, never fluorine, because ZrF₄ does not volatilize below 900 °C.

**One film, four removals, and one rule: take it off where it is not wanted, stop on it where it is, and do not change it where it stays.** This book covers the chemistry, equipment, process phenomena, and production engineering of all four.

---

## Intended Audience

This book is written for **semiconductor industry professionals** with working knowledge of plasma processing:

- **Process Engineers**: developing edge, periphery, and trim recipes for ZAZ; choosing the conductor-etch stop; controlling zirconium residue, fluorine skins, tungsten loss, and the titanium-oxide shell; qualifying thermal and plasma atomic-layer etching
- **Equipment Engineers**: specifying bevel-etch chambers with plasma confinement, hot-chuck resist-free clear chambers, plasma-free thermal-etch reactors with HF handling, in-situ ellipsometry for a 5 nm film, and zirconium-safe cleaning of etch and deposition tools
- **Integration Engineers**: choosing among integrated, strip-then-clear, thermal, and hybrid clears; setting plate overlap and edge seal; deciding where the bevel etch sits relative to crystallization; managing contamination zones
- **Device Engineers**: understanding how vacancies, halogens, and charging in a cut dielectric edge appear as leakage and TDDB tails, and how trim trades capacitance against retention
- **Researchers**: studying ion-assisted and thermal removal of metal oxides, self-limiting etch kinetics, diffusion-limited dosing in 100:1 channels, and dry etching of strontium- and barium-bearing dielectrics

The material assumes Books #1–5 (plasma fundamentals), Books #6–10 (dielectric etch), and Books #11–15 (advanced plasma engineering). **Book #32 (*DRAM Capacitor Electrode Etch*)** is the immediate companion: it supplies the plate stack, the BCl₃/Cl₂ high-k step, and the grain-tail clearing model that this book extends. Book #29 (*DRAM Capacitor Hole Etch*) and **Book #30 (*DRAM Capacitor Mold Etch*)** define the array and the free-standing pillar forest that the dielectric covers. Book #31 (*DRAM High-Aspect-Ratio Capacitor Etch*) carries the capacitor to taller molds. The companion volumes *Gate Oxide Etch*, *Silicon Nitride Etch*, *Aluminum Metal Etch*, *Deposition Materials*, and *Metrology & Inspection* cover related chemistries and tools in more general settings.

---

## Technical Scope

### Core Concepts Covered

**Architecture & Films:**
- The ZAZ dielectric in the cell: EOT, capacitance, leakage, and the retention budget
- Amorphous as grown, tetragonal after the top electrode and plate fill; what each state does to the etch
- ALD wrap-around into the wafer-edge gap; the backside and bevel inventory
- The neighbouring films the clears must spare: TiN, SiN, SiO₂, W, SiGe, Si

**Etch Chemistry:**
- Ion-assisted chlorination in BCl₃/Cl₂; thermal fluorination and ligand exchange in HF/DMAC; dilute-HF wet removal
- Thermochemistry map for Zr, Hf, Al, Ti, Nb, Sr, Ba, and rare-earth oxides
- The selectivity matrix: ZAZ against every film, in every chemistry
- Fluorine skins (ZrF₄, AlF₃) and the boron conversion that removes one but not the other

**Equipment Design:**
- Edge-ring bevel-etch chambers; confinement, exclusion zone, and centring
- Plasma-free thermal-etch reactors; dosing of 13 nm, 1.4 µm deep channels
- Hot-chuck resist-free clear chambers; downstream strip
- In-situ ellipsometry, OES, and cycle counting for a 5 nm film
- Zirconium-safe cleaning of etch chambers and the ALD tool

**Process Phenomena:**
- Stopping on the dielectric: TiN overetch, ZAZ loss, fluorine memory
- The dielectric edge: undercut, overlap, damage penetration, seal
- Vacancies, halogens, Poole–Frenkel leakage, and TDDB after etch
- Thinning, trim non-uniformity, and rework limits
- Advanced dielectrics (HZO, TiO₂, Nb-doped, SrTiO₃) and 3D DRAM lateral clears

**Production Integration:**
- Metrology and inspection for a 5 nm film, edge zirconium, and periphery opens
- Electrical monitors: capacitor arrays, antenna and polarity structures, contact chains
- Yield signatures, equipment sizing, and cost of ownership of five routes

### Technology Context

- **Device architectures:** 6F² buried-channel DRAM from the 1x to the 1c generation (DDR5, LPDDR5X, HBM core dies); 4F² vertical-channel and 3D DRAM as emerging forms
- **Capacitor structures:** single-sided solid TiN pillar capacitors with top and middle nitride supports (primary focus); ZAZ high-k; TiN/SiGe/W plate
- **Process sequence:** Module E follows the ZAZ ALD and precedes the top-electrode TiN. Module T sits at the same point in the flow. Module P follows the plate deposition, in the place of Book #32's high-k step. Module C acts on the ALD tool every few hundred wafers
- **Manufacturing scale:** 300 mm wafers; one edge etch (about 2 min of plasma), one conductor stop etch (about 40 s), one strip (60 s), and one hot clear (about 40 s) per wafer

---

## Book Organization

### Part I: Fundamentals (4 Chapters)

**Chapter 1: The Capacitor Dielectric & Why It Is Etched**
- What the dielectric does in the cell: C_s, EOT, leakage, retention
- Why it must go from the edge, bevel, backside, periphery, and scribe
- The four dielectric etches and where they sit in the capacitor module
- The specification sheet

**Chapter 2: The ZAZ Film as the Etch Sees It — Growth, Crystallization, Wrap-Around & Stress**
- ALD growth, phase states, and etch rate against crystallinity
- Where the film lies: array, support, periphery, scribe, bevel, backside
- The wrap-around model and the edge inventory
- Thickness, stress, and incoming variation

**Chapter 3: Surface Chemistry of Metal-Oxide Removal — Plasma, Thermal & Wet**
- Ion-assisted chlorination, thermal fluorination with ligand exchange, wet HF
- Thermochemistry of the three routes; the BCl₃ conversion of ZrF₄
- Yield model, ALE window, self-limiting saturation
- What each route leaves on the surface

**Chapter 4: Selectivity Design — The Dielectric as Target and as Stop Layer**
- The selectivity matrix: six chemistries against ten films
- The stop requirement: TiN:ZAZ ≥ 18
- Selectivity to SiN, W, TiOₓ, and resist
- Amorphous against crystalline, and the argument for early removal

### Part II: Hardware Design (5 Chapters)

**Chapter 5: Edge & Bevel Etch Chambers**
- Edge-ring and bottom-electrode geometry; confinement and purge
- Ion-assisted boundaries and why they are sharp
- Centring, zone control, and edge-die protection
- Rates, time, and throughput for amorphous ZAZ

**Chapter 6: Thermal & Vapor-Phase Etch Reactors**
- Plasma-free HF/DMAC reactors; hot walls and materials
- Dosing of dead-end channels: the 6N_sAR²/(n₀v̄) model
- Cycle design, batch versus single-wafer
- HF safety and effluent

**Chapter 7: Dedicated Dielectric-Clear Chambers & the Strip-Then-Clear Route**
- The plate as its own mask: strip, shell, and clear
- Hot-chuck ICP with ion-energy control; pulsing
- Tungsten loss, shell lifetime, and charging with the plate exposed
- Downstream strip hardware

**Chapter 8: In-Situ Monitoring & Etch-Amount Control for a 5 nm Film**
- OES at the edge, at the stop, and at the clear
- In-situ ellipsometry on a periphery pad
- Counting cycles; etch-per-cycle drift
- Failure modes of thin-film endpoint

**Chapter 9: Zirconium Contamination, Chamber Walls & the ALD-Chamber Clean**
- Contamination zones, transfer coefficients, and the 10¹⁰ limit
- Etch-chamber walls: the Zr–F trap and the chlorine-first order
- Cleaning zirconia from the ALD tool: BCl₃ and the failure of NF₃
- Monitors and recovery

### Part III: Process Phenomena (5 Chapters)

**Chapter 10: Stopping on the Dielectric — Conductor Overetch, Fluorine Skins & Surface Modification**
- TiN clearing, overetch, and ZAZ loss
- Fluorine memory and the ZrF₄/AlF₃ skin
- Chlorine and bromine uptake; conversion in the hot clear
- Resist, strip, and the shell as by-products

**Chapter 11: The Dielectric Edge — Profile, Undercut, Overlap & Seal**
- Edge profile by route: anisotropic, thermal, wet
- The overlap budget and the minimum plate overlap
- Seal by ILD, liner, and TiN wrap
- Skirt options and edge-die effects at the wafer rim

**Chapter 12: Etch-Induced Defects in the Dielectric — Vacancies, Halogens, Leakage & TDDB**
- Ion damage depth, vacancy generation, halogen incorporation
- Poole–Frenkel leakage and the trap model
- Weibull TDDB and the area scaling of defects
- Recovery anneals and verification

**Chapter 13: Thinning, Trim & Rework**
- Thermal ALE per-cycle removal, saturation, and uniformity along the pillar
- The capacitance–leakage trade of trimming
- Rework strip of the dielectric and its cost to the electrode
- Limits and rules

**Chapter 14: Advanced Dielectrics & 3D Architectures**
- Volatility of candidate oxides: HfO₂, TiO₂, Nb₂O₅, SrTiO₃, rare earths
- Dry versus wet removal for Sr- and Ba-bearing dielectrics
- 4F², 3D DRAM, and lateral isotropic clears
- Capacitorless cells and what is left to etch

### Part IV: Production Scale (2 Chapters)

**Chapter 15: Metrology, Inspection & Advanced Process Control**
- Ellipsometry, XRR, and XRF for 5 nm; VPD-ICPMS and TXRF for zirconium
- Edge and bevel inspection; contact chains for periphery opens
- Capacitor-array, antenna, and polarity monitors
- Feed-forward and feedback control of edge, stop, clear, and trim

**Chapter 16: Integration, Yield & Cost of Ownership**
- Hand-offs to the plate deposition and to the back end
- Yield signatures of each dielectric etch
- Equipment sizing and cost of ownership of five routes
- Decisions and the new-product checklist

---

## Key Technical Themes

1. **Remove it here, stop on it there, never change it where it stays.** The same film is a waste to clear at the edge, a stop layer under the conductor etch, and the product under the plate.
2. **Amorphous is easy; crystalline is a tail.** Before the top electrode the ZAZ etches 1.5× faster (9 against 6 nm/min) and has no grain boundaries, so no grain tail. Every dielectric etch that can precede crystallization should.
3. **The stop is the hard half.** Stopping a conductor etch on 5.5 nm of dielectric needs TiN:ZAZ ≥ 18, and fluorine from the tungsten step can turn the stop layer into a non-volatile ZrF₄ skin.
4. **The plate can be its own mask.** Stripping the resist before the clear frees the 218 nm resist budget, removes the veil mechanism, and permits a 250 °C chuck. It exposes the tungsten top (2.3 nm lost, 1.3 V charging clamp) and depends on a 1.8 nm TiOₓ shell outlasting a 38 s step by 42%.
5. **Volatility decides everything.** ZrCl₄ sublimes at 331 °C, ZrF₄ at about 906 °C, SrCl₂ boils near 1250 °C. Chlorine, boron, and heat remove zirconia; fluorine does so only as the first half of a ligand-exchange cycle, and only where the second half follows.
6. **Zirconium is a contaminant before it is a film.** A wafer carries 1.4 × 10¹⁶ Zr cm⁻² as deposited; 10¹³ is the periphery specification, 10¹¹ the etch-chamber limit, 10¹⁰ the furnace-entry limit.

---

## Cross-References to Prior Books

**Related Books in the Series:**

- **Books #1–5** (Plasma Physics & Chemistry Fundamentals): sheaths, ion energy, radical generation
- **Books #6–10** (Dielectric Etch & Fluorocarbon Chemistry): fluorocarbon etch of the periphery contacts that ZrO₂ residue stops
- **Books #11–15** (Advanced Plasma Engineering): RF delivery, chucks, endpoint, chamber matching
- **Book #29** (DRAM Capacitor Hole Etch): the holes and the reference array
- **Book #30** (DRAM Capacitor Mold Etch): the free-standing pillar forest the ZAZ must coat
- **Book #31** (DRAM High-Aspect-Ratio Capacitor Etch): taller capacitors, taller channels to dose
- **Book #32** (DRAM Capacitor Electrode Etch): the plate stack, the integrated high-k step, the grain-tail model, and the charging circuit
- **Companion volumes:** *Gate Oxide Etch* (high-k gate dielectric removal), *Silicon Nitride Etch*, *Aluminum Metal Etch* (fences, veils, and corrosion), *Deposition Materials* (ALD of ZrO₂ and Al₂O₃), *Metrology & Inspection*

Book #32 cut the plate and cleared the periphery as one recipe. This book separates the dielectric from the conductor, so that each can be etched with the chemistry, temperature, and ion energy that suit it.

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
│   ├── 02-zaz-film-as-etch-sees-it.md
│   ├── 03-metal-oxide-removal-chemistry.md
│   ├── 04-selectivity-target-and-stop.md
│   ├── 05-edge-bevel-etch-chambers.md
│   ├── 06-thermal-vapor-etch-reactors.md
│   ├── 07-dedicated-dielectric-clear-chambers.md
│   ├── 08-insitu-monitoring-thin-dielectric.md
│   ├── 09-zirconium-contamination-ald-chamber-clean.md
│   ├── 10-stopping-on-the-dielectric.md
│   ├── 11-dielectric-edge-undercut-seal.md
│   ├── 12-etch-induced-dielectric-defects.md
│   ├── 13-thinning-trim-rework.md
│   ├── 14-advanced-dielectrics-3d.md
│   ├── 15-metrology-inspection-apc.md
│   └── 16-integration-yield-coo.md
│
└── appendices/
    ├── A-material-properties.md
    ├── B-chemistry-thermochemistry-data.md
    ├── C-standard-procedures.md
    ├── D-process-windows.md
    ├── E-etch-trim-wrap-charging-calculations.md
    ├── F-metrology-reference.md
    └── G-troubleshooting-guide.md
```

---

## Constraints & Scope

### What This Book Covers
✅ Dry, thermal, and wet removal of ZrO₂/Al₂O₃/ZrO₂ from the edge, bevel, backside, periphery, scribe, and ALD-tool walls  
✅ The conductor-etch stop on the dielectric and the surface it leaves  
✅ Edge, strip-then-clear, thermal, and hybrid routes, with their hardware and in-situ monitoring  
✅ Edge profile, overlap, etch-induced defects, leakage, and TDDB of the cut dielectric  
✅ Thermal atomic-layer trim and rework of the dielectric  
✅ Advanced dielectrics, 4F² and 3D DRAM, and the metrology, yield, and cost of all of the above  

### What This Book Does NOT Cover
❌ Storage-node separation or the W/SiGe/TiN etch chemistries in detail (see Book #32)  
❌ The capacitor hole etch (Books #29 and #31) or the mold etch (Book #30)  
❌ ALD deposition chemistry and growth kinetics, except wrap-around and tool cleaning  
❌ The periphery contact etch itself, except as the customer of high-k clearing  
❌ Vendor-specific recipes or proprietary tool parameters  

### A Note on Numbers
Numbers in this book come from established thermochemistry and plasma–surface models, published etch-rate data and literature trends, and representative production practice. Worked examples use **illustrative values** chosen to show the method, and the arithmetic is written out so readers can substitute their own data. A single **reference process** is used across chapters so that examples connect. It inherits the array and plate of Books #29, #30, and #32: a 1b-class 6F² cell (F = 17 nm, cell area 1734 nm²) on a 45 nm hexagonal storage-node pitch, a 1.60 µm mold, solid TiN pillars 32/28/24 nm wide (C_s = 8.6 fF), and a ZAZ dielectric of ZrO₂ 2.6 nm / Al₂O₃ 0.3 nm / ZrO₂ 2.6 nm (5.5 nm, EOT 0.50 nm, k_eff ≈ 43, leakage about 1 fA per cell at 1.0 V). The plate is 5 nm TiN, 150 nm B-doped Si₀.₇Ge₀.₃, and 40 nm W under 500 nm KrF resist, in 32 islands per die that cover 55% of the wafer and overlap the last dummy row by 1.5 µm; the periphery top SiN is 120 nm, and 3 × 10⁷ periphery contacts per die land on it. Rates follow the ion-yield model of Book #32 (K = 3.9 nm/s per unit yield), which reproduces its tabulated values for TiN and tetragonal ZrO₂. **Module E** removes amorphous ZAZ from the outer 3.0 mm of the top, the bevel, and the outer 3.5 mm of the backside (66 cm², 9.6 × 10¹⁷ Zr atoms) in a BCl₃/Cl₂/Ar edge plasma at 250 eV, in 121 s including 30% overetch, to Zr ≤ 10¹⁰ cm⁻². **Module P**, the reference *strip-then-clear* route (R1), etches BARC, W, and SiGe as in Book #32, breaks through and clears the 5 nm TiN in Cl₂/Ar at about 40 eV (42 s), strips the resist in a downstream O₂/N₂ plasma at 250 °C (60 s, leaving a 1.8 nm TiOₓ shell and a 2.5 nm WOₓ top), and clears the ZAZ with the plate as its own mask in BCl₃/Cl₂/Ar at 250 °C and about 80 eV (28 s to clear, 35% overetch, 38 s). **Module T** thins the amorphous ZAZ with HF/DMAC thermal ALE at 280 °C (0.07 nm per 10 s cycle). Treat recipe values as starting points for a design of experiments, never as qualified process conditions.

---

## Development Status

**Book #33 Foundation:** Complete  
**Part I (Chapters 1–4):** Complete  
**Part II (Chapters 5–9):** Complete  
**Part III (Chapters 10–14):** Complete  
**Part IV (Chapters 15–16):** Complete  
**Back Matter (Appendices A–G, Glossary):** Complete  

---

## Next Steps

1. **Read [PREFACE.md](./PREFACE.md)** for the motivation and reading guidance
2. **Read [INDEX.md](./INDEX.md)** for the detailed chapter outline and reading paths by role
3. **Begin [Chapter 1](./chapters/01-capacitor-dielectric-role.md)**: The Capacitor Dielectric & Why It Is Etched

---

**Book #33 Version:** 1.0  
**Last Updated:** 2026-10-05  
**Series:** ChipFoundryServices Technical Series
