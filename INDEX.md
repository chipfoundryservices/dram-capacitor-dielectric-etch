# Index: Book #33 Navigation Guide

## Quick Navigation

**Total Content:** 16 chapters + 7 appendices + glossary  
**Estimated Read Time:** 20–28 hours for the complete book; 5–9 hours for a focused reading path

| Part | Chapters | Theme |
|------|----------|-------|
| I | 1–4 | Fundamentals: the role of the dielectric, the ZAZ film, metal-oxide chlorination chemistry, ALE, thermal and wet removal |
| II | 5–9 | Hardware: heated-chuck ICP chambers, temperature and ion-energy uniformity, ALE and thermal reactors, endpoint, walls, contamination and the bevel |
| III | 10–14 | Phenomena: clearing statistics and residue, the plate edge, selectivity and surfaces, damage to the remaining dielectric, advanced schemes |
| IV | 15–16 | Production: metrology, inspection, APC, integration, yield, cost |

---

## Part I: Fundamentals (Chapters 1–4)

### Chapter 1: [The Capacitor Dielectric & Why It Is Etched](./chapters/01-capacitor-dielectric-role.md)
**Estimated Time:** 60 min | **Difficulty:** Foundation | **Reading Level:** All roles  
**Focus:** What does the dielectric do, where does ALD put it, and how clean must the periphery be?

**Key Topics:**
- C_s = 8.6 fF from EOT 0.50 nm; leakage ≤ 1 fA per cell (8 × 10⁻⁷ A/cm²)
- 2.2 m² of dielectric inside the plate; 318 cm² (≈ 1.4%) outside it
- ZrO₂ stops fluorocarbon contacts; why the contact etch cannot clear it
- Zr ≤ 1 × 10¹³ /cm² (99.93% removal) and < 8 × 10⁻¹¹ per domain; routes R0, D1, D2, T, W, ASD; the specification sheet

**Critical Equations:** C_s = ε₀·3.9·A/EOT; k_eff = 3.9·t/EOT; n_Zr = ρN_A/M  
**Study Questions:** 6

---

### Chapter 2: [The Dielectric Stack — ZAZ Films, Phases, Interfaces & Incoming Surfaces](./chapters/02-dielectric-stack-films.md)
**Estimated Time:** 50 min | **Difficulty:** Intermediate | **Reading Level:** Process/Integration  
**Focus:** What film and what surface does the clear inherit?

**Key Topics:**
- ALD of ZrO₂ (CpZr(NMe₂)₃/O₃) and Al₂O₃; nucleation delay on SiN
- Tetragonal on TiN; ≈ 30% monoclinic and coarser grains on SiN
- Rates by phase: amorphous 14, tetragonal 9.0, monoclinic 8.0 nm/min in D1
- Ti, Cl, F, Br, C on the incoming surface; the BT; ZAZ on walls and bevel

**Critical Equations:** cycles = t/GPC; Δt_clear from phase mix  
**Study Questions:** 6

---

### Chapter 3: [Plasma Chemistry of Metal-Oxide Etching](./chapters/03-metal-oxide-plasma-chemistry.md)
**Estimated Time:** 65 min | **Difficulty:** Advanced | **Reading Level:** Process/Research  
**Focus:** Why boron and heat, and how energy and temperature set rate and selectivity

**Key Topics:**
- Fluorides refractory, chlorides volatile when hot; ZrCl₄ 26 Torr at 250 °C
- ΔH: Cl₂ +120, BCl₃ −191, C-assisted −101, halogen exchange −48 kJ/mol
- BₓClᵧ etch–deposition transition; Cl₂ fraction trade-off
- Threshold-yield model: E_th 60 → 25 eV from 60 to 250 °C; 1.8%/eV and 0.7%/°C; ZrO₂:SiN 0.75 → 3

**Critical Equations:** ln(p/p₀) = −(ΔH/R)(1/T − 1/T₀); R = A(T)(√E − √E_th(T))  
**Study Questions:** 6

---

### Chapter 4: [Atomic-Layer, Thermal & Wet Removal of High-k Films](./chapters/04-ale-thermal-wet-removal.md)
**Estimated Time:** 60 min | **Difficulty:** Advanced | **Reading Level:** Process/Research  
**Focus:** What ALE, thermal ALE, and wet chemistry offer and cost

**Key Topics:**
- D2: 5.0 s cycle, 0.10 nm/cycle, 45–70 eV window, synergy 90%, why 100 °C
- Thermal ALE: HF fluorination, DMAC or BCl₃ exchange; isotropy and undercut
- Wet etch of crystalline ZrO₂; damage-enhanced hybrid
- Route comparison table

**Critical Equations:** S = (EPC − α − β)/EPC; u_top ≈ t_rem, u_bottom ≈ t_rem − t_f  
**Study Questions:** 6

---

## Part II: Hardware Design (Chapters 5–9)

### Chapter 5: [Heated-Chuck ICP Chambers for Dielectric Clearing](./chapters/05-heated-chuck-icp-chambers.md)
**Estimated Time:** 55 min | **Difficulty:** Intermediate | **Reading Level:** Equipment  
**Focus:** How to hold a wafer at 250 °C in BCl₃ at 70 eV

**Key Topics:**
- Five reasons for a separate chamber; ICP flux 2 × 10¹⁶ cm⁻² s⁻¹, ≈ 70 eV
- Bias-voltage control; ion energy spread at 13.56 MHz
- J-R AlN chuck; 14 °C wafer offset; heat-up and 88 µm expansion
- Yttria walls, window, ring; BCl₃ delivery; split mainframe at ≈ 60 wph

**Critical Equations:** Γ_i = 0.61 n_e u_B; E_i ≈ e(V_p + P/I_i); ΔT = q/h  
**Study Questions:** 6

---

### Chapter 6: [Temperature, Ion Energy & Clearing Uniformity](./chapters/06-temperature-ion-energy-uniformity.md)
**Estimated Time:** 45 min | **Difficulty:** Intermediate | **Reading Level:** Equipment/Process  
**Focus:** Shrinking the time between first and last clearing

**Key Topics:**
- Rate budget: flux, ion energy, temperature → 1.1% (1σ) tuned
- Edge-thick ALD film; zone-temperature feed-forward (+5 °C at the edge)
- Sheath bending, ring wear, ion tilt and floor shadows next to plate edges
- No loading jump in D1; ALE fixes rate but not thickness non-uniformity

**Critical Equations:** σ_tc/t_c = √((σ_t/t)² + (σ_R/R)²)  
**Study Questions:** 6

---

### Chapter 7: [ALE & Thermal-Etch Reactors](./chapters/07-ale-thermal-etch-reactors.md)
**Estimated Time:** 55 min | **Difficulty:** Advanced | **Reading Level:** Equipment  
**Focus:** Hardware for cyclic etching

**Key Topics:**
- Purge design: τ = pV/Q; 1% residual in 0.08 s with a confined volume
- Residual Cl in step B erodes synergy; valve life
- Continuous plasma with pulsed bias; frequency tuning; tailored waveforms
- Single-wafer, batch (≈ 30 wph), and spatial thermal-ALE reactors; HF and DMAC safety; EPC matching

**Critical Equations:** f = exp(−t/τ); τ = pV/Q  
**Study Questions:** 6

---

### Chapter 8: [Endpoint & In-Situ Monitoring of a 5.5 nm Film](./chapters/08-endpoint-in-situ-monitoring.md)
**Estimated Time:** 50 min | **Difficulty:** Intermediate | **Reading Level:** Equipment/Process  
**Focus:** Detecting the mean clearing time of a film gone in 36 s

**Key Topics:**
- Product fluxes; Zr, Al, Si, BO, N₂ signals and their sizes
- Al marker: predicts t_EP 18 s early; its width measures the spread
- Landing signal as a cumulative distribution; 50%-rise algorithm
- Why reflectometry fails; in-situ ellipsometry; ALE per-cycle signals and feed-forward counts

**Critical Equations:** t_EP,pred = t_Al + t_Al₂O₃/2 + t_lower/R_u; F(t) = Φ((t − t_EP)/σ_tc)  
**Study Questions:** 6

---

### Chapter 9: [Walls, Boron Deposits, Zirconium Contamination & the Bevel](./chapters/09-walls-boron-zirconium-bevel.md)
**Estimated Time:** 50 min | **Difficulty:** Intermediate | **Reading Level:** Equipment/Integration  
**Focus:** Keeping the chamber steady and the zirconium where it belongs

**Key Topics:**
- Wall deposits: ≈ 0.01 nm Zr-equivalent and 0.05 nm boron per wafer
- The fluorine trap; chlorine-first waferless cleans; seasoning
- Zr sources: the bevel wrap dominates by 10⁴; limits for shared tools
- ALD edge exclusion, plasma bevel etch with BCl₃, wet backside clean, batch thermal ALE

**Critical Equations:** wall dose = f_stick × N_Zr / A_wall  
**Study Questions:** 6

---

## Part III: Process Phenomena (Chapters 10–14)

### Chapter 10: [Clearing the Periphery — Grain Residue, Micromasking & Stringers](./chapters/10-periphery-clearing-residue-stringers.md)
**Estimated Time:** 65 min | **Difficulty:** Advanced | **Reading Level:** Process/Integration  
**Focus:** How often does "nothing left" fail?

**Key Topics:**
- Clearing domains: 9 × 10¹⁰ per die, 1.2 × 10⁸ under contacts
- σ_g ≈ 10% (D1), 4% (D2), 12% (T); 70% OE → z = 6.5 at the slowest site
- Non-Gaussian residue: carbon, boron glass, F patches, nodules, particles
- Island budget ≈ 20 /cm²; stringers and layout; the contact-open budget ≈ 0.007 per die

**Critical Equations:** z = ((1 + OE)/s − 1)/σ_g; P = ½ erfc(z/√2); N_max = target/f_c  
**Study Questions:** 6

---

### Chapter 11: [The Cut Edge — Top-Electrode Recess, Undercut & Ingress](./chapters/11-cut-edge-recess-undercut-ingress.md)
**Estimated Time:** 55 min | **Difficulty:** Advanced | **Reading Level:** Process/Device/Integration  
**Focus:** Stopping cleanly at the plate edge

**Key Topics:**
- Lateral loss in D1: TE TiN 1.2, SiGe 1.0, W 0.5 nm; Cl₂ fraction sensitivity
- Sidewall protection: BₓClᵧ, nitridation, liners, lower temperature
- Undercut by route; the slot and its SiN seal
- Cl 8 nm along the interface; edge oxidation; plate-edge comb; minimum overlap ≈ 0.4 µm

**Critical Equations:** recess = R_lat·t; L_d = √(D_i t); Arrhenius scaling  
**Study Questions:** 6

---

### Chapter 12: [Selectivity & the Materials Around the Dielectric](./chapters/12-selectivity-surrounding-materials.md)
**Estimated Time:** 45 min | **Difficulty:** Intermediate | **Reading Level:** Process/Integration  
**Focus:** What the clear leaves on everything it touches

**Key Topics:**
- SiN loss 1.3 nm (D1), local range ≈ 1.2 nm; by route 4 → < 0.1 nm
- B and Cl on the nitride and their consequences
- H₂O/N₂ PET then DI rinse; queue times
- Oxide-cap budget; cap pinholes; the Al₂O₃ insertion and variant stacks; surfaces handed to the ILD

**Critical Equations:** loss = R_SiN × (t_total − t_clear,local)  
**Study Questions:** 6

---

### Chapter 13: [Damage to the Remaining Dielectric](./chapters/13-damage-remaining-dielectric.md)
**Estimated Time:** 50 min | **Difficulty:** Advanced | **Reading Level:** Device/Research  
**Focus:** Reaching the array dielectric without ions or light

**Key Topics:**
- Capped island antenna ratio 1.3 × 10⁻³; charging negligible
- Chlorine, oxygen loss, fluorine at the cut edge; UV reach 50–100 nm
- Hydrogen from the strip: + 3–5% array leakage
- Overlap ladder: damage reach ≈ 0.1–0.15 µm; route comparison

**Critical Equations:** J = f_imb·J_i·A_side/A_diel  
**Study Questions:** 6

---

### Chapter 14: [Advanced Schemes — Higher-k Films, Area-Selective Deposition, 4F² & 3D DRAM](./chapters/14-advanced-dielectric-schemes.md)
**Estimated Time:** 55 min | **Difficulty:** Advanced | **Reading Level:** Research/Integration  
**Focus:** Where the dielectric clear is going

**Key Topics:**
- HZO, Nb₂O₅, TiO₂, SrTiO₃, rare-earth dopants; chlorinate and rinse
- ASD and why SiN supports defeat it in stacked capacitors
- ALE trimming: + 16% capacitance and its risks
- 4F² edge pressure; 3D DRAM lateral recess and slit transport

**Critical Equations:** D_K = (d/3)v̄; t = L²/D_K; C ∝ k/t  
**Study Questions:** 6

---

## Part IV: Production Scale (Chapters 15–16)

### Chapter 15: [Metrology, Inspection & Advanced Process Control](./chapters/15-metrology-inspection-apc.md)
**Estimated Time:** 55 min | **Difficulty:** Intermediate | **Reading Level:** All roles  
**Focus:** Measuring an absence

**Key Topics:**
- TXRF, VPD (and its blind spot), XPS, LEIS, ToF-SIMS
- Averages cannot see the tail (3 × 10⁴ below detection)
- E-beam inspection statistics; contact chains; the measurement ladder
- Feed-forward (zones, OE, Al-marker width), EWMA on ion energy, ALE counts, FDC and VM

**Critical Equations:** P(k) = λᵏe^(−λ)/k!; ŷ_k = λy_k + (1 − λ)ŷ_{k−1}  
**Study Questions:** 6

---

### Chapter 16: [Integration, Yield & Cost of Ownership](./chapters/16-integration-yield-coo.md)
**Estimated Time:** 45 min | **Difficulty:** Intermediate | **Reading Level:** Integration/Management  
**Focus:** Which route, at what cost, for what yield?

**Key Topics:**
- Customers of the clear: ILD, plate contact, periphery contacts, array, shared tools
- Yield signatures and their mechanisms
- Equipment: 3 split mainframes vs 4 cold-route; 18 ALE chambers; 7 batch reactors
- CoO: D1 ≈ + $1.2 vs cold; ALE + $6–8; value of levers; route selection; new-product checklist

**Critical Equations:** N = WPH/(WPH_tool × A); cost = (P/yr)/(WPH × 8760 × A)  
**Study Questions:** 6

---

## Appendices

- [Appendix A: Material Properties](./appendices/A-material-properties.md)
- [Appendix B: Chemistry & Thermochemistry Data](./appendices/B-chemistry-thermochemistry-data.md)
- [Appendix C: Standard Procedures](./appendices/C-standard-procedures.md)
- [Appendix D: Process Windows](./appendices/D-process-windows.md)
- [Appendix E: Clearing, ALE & Edge Calculations](./appendices/E-clearing-ale-edge-calculations.md)
- [Appendix F: Metrology Reference](./appendices/F-metrology-reference.md)
- [Appendix G: Troubleshooting Guide](./appendices/G-troubleshooting-guide.md)
- [Glossary](./GLOSSARY.md)

---

## Reading Paths by Role

**Process Engineer (8 h):** Ch. 1 → 2 → 3 → 4 → 10 → 11 → 12 → App. D, G  
**Equipment Engineer (7 h):** Ch. 1 → 5 → 6 → 7 → 8 → 9 → 15  
**Integration Engineer (8 h):** Ch. 1 → 2 → 10 → 11 → 14 → 16  
**Device Engineer (5 h):** Ch. 1 → 11 → 13 → 16  
**Researcher (8 h):** Ch. 3 → 4 → 10 → 14 → App. E

---

## Study Questions Overview

**Total Study Questions:** 96 (6 per chapter × 16 chapters)  
**Nature:** Mostly calculation-based  
**Topics:** Capacitance and leakage budgets, zirconium inventory, halide vapor pressures, reaction enthalpies, threshold-yield models, selectivity, ALE synergy and cycle counts, isotropic undercut, ion flux and bias, chuck heat balance, clearing spread and zone feed-forward, endpoint prediction, purge design, wall deposition, backside contamination, domain statistics, island budgets, lateral recess and ingress, PET chemistry, cap budget, charging, overlap ladders, transport in 3D slits, sampling statistics, EWMA control, equipment counts, cost

Examples:
- Compute the fraction of the dielectric that must be removed for a new array
- Find the chuck temperature at which ZrCl₄ leaves on its own
- Predict the rate and selectivity at a new ion energy and temperature
- Compute ALE synergy and cycle count after a chamber temperature drift
- Size the zone-temperature tilt for a new ALD radial profile
- Predict t_EP from the Al-marker time
- Find the overetch for a coarser-grained film or a denser contact layout
- Compute the TE TiN recess for a new Cl₂ fraction
- Size e-beam inspection to prove an island density
- Size the equipment for 150,000 wafer starts per month on each route

---

## How to Use This Index

1. **First time?** Read PREFACE.md, then this INDEX, then Chapter 1.
2. **Focused reading?** Pick your role from the reading paths above.
3. **Reference mode?** Jump to the chapter. Use Appendix G for symptoms and Appendix E for formulas.
4. **Deep dive?** Read Chapters 1–16 in order and work the study questions.

---

**Index Version:** 1.0  
**Last Updated:** 2026-10-05  
**Next:** Begin [Chapter 1: The Capacitor Dielectric & Why It Is Etched](./chapters/01-capacitor-dielectric-role.md)
