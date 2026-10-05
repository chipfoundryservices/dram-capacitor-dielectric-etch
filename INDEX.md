# Index: Book #33 Navigation Guide

## Quick Navigation

**Total Content:** 16 chapters + 7 appendices + glossary  
**Estimated Read Time:** 20–28 hours for the complete book; 5–9 hours for a focused reading path

| Part | Chapters | Theme |
|------|----------|-------|
| I | 1–4 | Fundamentals: the dielectric and where it is etched, the ZAZ stack, halide plasma chemistry, plasma and thermal ALE |
| II | 5–9 | Hardware: ICP chambers and ion energy, chuck uniformity, bevel systems, endpoint, walls and ALD-reactor cleaning |
| III | 10–14 | Phenomena: periphery clearing, the two edges, in-array trim, damage and reliability, advanced dielectrics and architectures |
| IV | 15–16 | Production: metrology, inspection, APC, integration, yield, cost |

---

## Part I: Fundamentals (Chapters 1–4)

### Chapter 1: [The Capacitor Dielectric & Why It Is Etched](./chapters/01-capacitor-dielectric-role.md)
**Estimated Time:** 55 min | **Difficulty:** Foundation | **Reading Level:** All roles  
**Focus:** Where does ALD put the dielectric, and why must each unwanted part be removed?

**Key Topics:**
- C_s = 8.6 fF from 1.24 × 10⁵ nm², k_eff 43, EOT 0.50 nm; 1.8% per 0.1 nm; leakage ×1.5 per 0.1 nm
- ≈ 2 m² of dielectric per wafer; the five places it meets an etch
- ZrF₄ stops contacts; 1.5 × 10⁶ removal factor at the bevel; the channel at 1c
- The three modules in the flow; the specification sheet

**Critical Equations:** C_s = ε₀kA/t; J ∝ exp(−t/λ)  
**Study Questions:** 6

---

### Chapter 2: [The Dielectric Stack — Films, Phases, Interfaces & Wrap](./chapters/02-dielectric-stack-films.md)
**Estimated Time:** 55 min | **Difficulty:** Intermediate | **Reading Level:** Process/Integration  
**Focus:** What does each dielectric etch inherit?

**Key Topics:**
- ZAZ layers and ALD; EOT layer sum vs measurement; relatives
- Crystalline fraction through the module; thickness-dependent crystallization
- Grains and boundaries; TiOₓNᵧ and TE interfaces
- Wrap over the apex and onto the backside to the ALD seal; incoming variation

**Critical Equations:** EOT = 3.9 Σ tᵢ/kᵢ  
**Study Questions:** 6

---

### Chapter 3: [Halide Plasma Chemistry of High-k Oxides](./chapters/03-high-k-halide-plasma-chemistry.md)
**Estimated Time:** 65 min | **Difficulty:** Advanced | **Reading Level:** Process/Research  
**Focus:** Why does ZrO₂ need boron and ions, and how does a continuous etch create its own tail?

**Key Topics:**
- Volatility groups; ΔH with Cl₂, BCl₃, and carbon
- R_net = A(√E − √E_th) − D; E₀ ≈ 60 eV; sensitivity 0.9–10% per eV
- Cl₂ fraction; temperature; σ_r vs energy and temperature
- σ_rem = √((σ_r x)² + σ_t²); selectivities; TiN clear; residues; alternatives

**Critical Equations:** R_net = A(√E − √E_th) − D; σ_rem(x)  
**Study Questions:** 6

---

### Chapter 4: [Atomic-Layer & Thermal Etching of High-k](./chapters/04-atomic-layer-thermal-etching.md)
**Estimated Time:** 60 min | **Difficulty:** Advanced | **Reading Level:** Process/Research  
**Focus:** How do plasma and thermal ALE remove ZrO₂, and what can they not do?

**Key Topics:**
- ALE window 45–75 eV; synergy 96%; saturation τ_A, τ_B
- EPC by material; ZrO₂:SiN 6.7 vs 0.75
- HF/DMAC thermal ALE; temperature; fluorine left behind
- Throughput optimization; quasi-ALE; ALE adds spread, never removes it

**Critical Equations:** S = (EPC − α − β)/EPC; EPC = EPC_sat(1 − e^(−t_A/τ_A))(1 − e^(−t_B/τ_B))  
**Study Questions:** 6

---

## Part II: Hardware Design (Chapters 5–9)

### Chapter 5: [ICP Chambers & Ion-Energy Control for Nanometre Removal](./chapters/05-icp-chambers-ion-energy-control.md)
**Estimated Time:** 50 min | **Difficulty:** Intermediate | **Reading Level:** Equipment/Process  
**Key Topics:** Γ_i 1.5 and 1.0 × 10¹⁶ cm⁻²s⁻¹; voltage control; arcsine IEDF, 59% outside the window at 13.56 MHz; tailored waveform; residence time and residual BCl₃; divert lines; preset match, delayed bias; 400 s vs 270 s per wafer  
**Critical Equations:** Γ_i = 0.61 n_e u_B; F(x) = ½ + (1/π)arcsin[(x − E)/(ΔE/2)]; τ = pV/Q  
**Study Questions:** 6

### Chapter 6: [Chuck Temperature, Uniformity & the Clearing-Time Map](./chapters/06-chuck-temperature-uniformity.md)
**Estimated Time:** 50 min | **Difficulty:** Intermediate | **Reading Level:** Equipment/Process  
**Key Topics:** ±5% clearing-time map; R_slow 1.34 nm; N = 36; 0.8%/°C; zone tuning; ring wear paid in cycles; ALE ±1.2% uniform but inflexible; matching on removed thickness; trim heater uniformity  
**Critical Equations:** N = ⌈(R_slow + zσ − b)/EPC⌉  
**Study Questions:** 6

### Chapter 7: [Bevel Etch Systems for High-k Removal](./chapters/07-bevel-etch-systems.md)
**Estimated Time:** 50 min | **Difficulty:** Advanced | **Reading Level:** Equipment/Integration  
**Key Topics:** PEZ geometry; Paschen exclusion; radical decay L = D/v; boundary budget ±0.08 mm; collisional bevel ion energies 80–90 eV; 3–4% per eV; reference recipe; residual Zr 3–8 × 10⁹; arcing; 16 chambers; alternatives  
**Critical Equations:** pd; L = D/v  
**Study Questions:** 6

### Chapter 8: [Endpoint & In-Situ Monitoring for Nanometre Dielectrics](./chapters/08-endpoint-monitoring-nanometre-dielectrics.md)
**Estimated Time:** 50 min | **Difficulty:** Intermediate | **Reading Level:** Equipment/Process  
**Key Topics:** Emission lines; TiN-clear transition; Al marker at 27.8 s and main-step adaptation; ALE clearing curve n₅₀ ≈ 11, n₉₈ ≈ 18; eight orders between signal floor and target; reflectometry vs ellipsometry; bevel V_pp; QCM; failure modes  
**Study Questions:** 6

### Chapter 9: [Walls, Boron, Metal Contamination & ALD-Reactor Cleaning](./chapters/09-walls-contamination-ald-reactor-cleaning.md)
**Estimated Time:** 50 min | **Difficulty:** Intermediate | **Reading Level:** Equipment/Facilities  
**Key Topics:** ZrCl₄ vapour pressure vs Zr–B–O–Cl deposits; 6 × 10¹³ Zr/cm² per wafer; wall state −7%; WAC order; Zr paths and the bevel's 4 × 10¹⁷ atoms; cover-wafer WAC; flake clusters; in-situ chlorine clean of the ALD reactor  
**Study Questions:** 6

---

## Part III: Process Phenomena (Chapters 10–14)

### Chapter 10: [Periphery Clearing — Residue Statistics, the ALE Finish & SiN Landing](./chapters/10-periphery-clearing-residue-ale-finish.md)
**Estimated Time:** 70 min | **Difficulty:** Advanced | **Reading Level:** Process/Integration/Research  
**Focus:** How small is the residue tail, what sets it, and what does the finish buy?

**Key Topics:**
- Where the last ZAZ lies; grain-centre islands
- z = 6.56 at the slowest site; ≈ 0.35 residue opens per wafer
- Non-Gaussian Pareto; N vs main-step share; σ_r as the lever
- SiN loss 0.35–0.42 nm; B and Cl removal; veils; five routes

**Critical Equations:** P = ½erfc(z/√2); N(x)  
**Study Questions:** 6

### Chapter 11: [The Two Edges — Plate Edge & Wafer Bevel](./chapters/11-dielectric-edges-plate-bevel.md)
**Estimated Time:** 50 min | **Difficulty:** Intermediate | **Reading Level:** Device/Process  
**Key Topics:** TE notch 1.3 nm; ZAZ edge recess 0.4 nm; L ≈ 50 nm of Cl/B diffusion; unbiased edge; corrosion queue times; bevel staircase; boron ring; adhesion G = σ²h/2E'; module 2 revisits the front ring; edge test structures  
**Critical Equations:** L = √(Dt); G = σ²h/(2E')  
**Study Questions:** 6

### Chapter 12: [In-Array Dielectric Trim by Thermal ALE](./chapters/12-in-array-dielectric-trim.md)
**Estimated Time:** 60 min | **Difficulty:** Advanced | **Reading Level:** Integration/Research  
**Focus:** Can every capacitor be thinned by a nanometre, uniformly and safely?

**Key Topics:**
- 1c pilot: 6.5 → 5.5 nm; EOT 0.475; +5% C_s; channel 4.7 nm
- The array as a reactant sink: one reactor-fill per cycle; 35 s cycles
- Exposure at a = 200; soft saturation; bottom-to-top 0.92
- Self-limiting grooves ≈ 0.25 nm; F, Al, C; pilot results and risks

**Critical Equations:** (Pt)_req ≈ S√(2πmkT)(1 + 19a/4 + 3a²/2); EPC = EPC₀[1 + β ln X]  
**Study Questions:** 6

### Chapter 13: [Process-Induced Damage & Dielectric Reliability](./chapters/13-process-induced-damage-reliability.md)
**Estimated Time:** 55 min | **Difficulty:** Advanced | **Reading Level:** Device/Research  
**Key Topics:** Damage inventory; wafer-wide TE clamp ≈ 1.2 V; ignition transients; VUV at the edge; species and trap-assisted leakage; Weibull area scaling (≈ 150×); recovery; test structures  
**Critical Equations:** J(V) = J₁exp((V − 1)/V₀); η(A) = η(A₀)(A₀/A)^(1/β)  
**Study Questions:** 6

### Chapter 14: [Advanced Dielectrics & Architectures](./chapters/14-advanced-dielectrics-architectures.md)
**Estimated Time:** 50 min | **Difficulty:** Advanced | **Reading Level:** Integration/Research  
**Key Topics:** HZH; La/Y dopants and water rinses; TiO₂ on Ru; SrTiO₃ dry–wet cycling; AFE/FE HZO; 4F² channels; wafer-bonded periphery; 3D DRAM lateral recess and staircase risers  
**Study Questions:** 6

---

## Part IV: Production Scale (Chapters 15–16)

### Chapter 15: [Metrology, Inspection & Advanced Process Control](./chapters/15-metrology-inspection-apc.md)
**Estimated Time:** 50 min | **Difficulty:** Intermediate | **Reading Level:** Process/Metrology  
**Key Topics:** Measurement map; TXRF cannot see the tail; contact chains; product as sensor; cycle ladders; voltage contrast; bevel metrology; feed-forward, Al-marker adaptation, EWMA on n₅₀; ring-hour N(h); bevel and trim loops; FDC on cyclic signals; sampling  
**Study Questions:** 6

### Chapter 16: [Integration, Yield & Cost of Ownership](./chapters/16-integration-yield-coo.md)
**Estimated Time:** 50 min | **Difficulty:** Intermediate | **Reading Level:** Integration/Management  
**Key Topics:** Hand-offs; yield signatures; 16 bevel, 28 plate, 11 trim tools; module costs ≈ $7, $10.60, $6.50; ALE finish +$4.80 vs ≈ $15 of yield; break-even Δλ 0.0013; hot bevel; trim vs taller mold; decisions and checklist  
**Critical Equations:** Y = exp(−λ)  
**Study Questions:** 6

---

## Appendices

- [Appendix A: Material Properties](./appendices/A-material-properties.md)
- [Appendix B: Chemistry & Thermochemistry Data](./appendices/B-chemistry-thermochemistry-data.md)
- [Appendix C: Standard Procedures](./appendices/C-standard-procedures.md)
- [Appendix D: Process Windows](./appendices/D-process-windows.md)
- [Appendix E: Clearing, ALE & Transport Calculations](./appendices/E-clearing-ale-transport-calculations.md)
- [Appendix F: Metrology Reference](./appendices/F-metrology-reference.md)
- [Appendix G: Troubleshooting Guide](./appendices/G-troubleshooting-guide.md)
- [Glossary](./GLOSSARY.md)

---

## Reading Paths by Role

**Process Engineer (8 h):** Ch. 1 → 2 → 3 → 4 → 10 → 11 → 12 → App. D, G  
**Equipment Engineer (7 h):** Ch. 1 → 5 → 6 → 7 → 8 → 9 → 15  
**Integration Engineer (8 h):** Ch. 1 → 2 → 10 → 11 → 12 → 14 → 16  
**Device Engineer (5 h):** Ch. 1 → 11 → 12 → 13 → 16  
**Researcher (8 h):** Ch. 3 → 4 → 10 → 12 → 14 → App. E

---

## Study Questions Overview

**Total Study Questions:** 96 (6 per chapter × 16 chapters)  
**Nature:** Mostly calculation-based  
**Topics:** Capacitance and EOT, leakage versus thickness, halide thermochemistry, etch–deposition transitions, grain-scale spread, ALE synergy and saturation, IEDF windows, purge design, clearing-time maps and cycle counts, ring wear, bevel confinement and ion energy, Al-marker adaptation, clearing curves, wall deposits and vapour pressures, contamination budgets, residue probability, SiN landing, veils, edge diffusion and adhesion, reactant demand and conformality, grain-boundary grooves, charging clamps, Weibull scaling, metrology sensitivity, EWMA control, equipment counts, cost and yield

Examples:
- Compute C_s and EOT for a new stack, and the leakage cost of thinning it
- Find the net ZrO₂ rate and its sensitivity at a new ion energy
- Compute the cycle count from the clearing-time map and the residue target
- Estimate the fraction of ions outside the ALE window for a bias waveform
- Place the bevel boundary and estimate the backside clearing time after ring wear
- Adapt the main step from an Al-marker time
- Estimate the zirconium a wall collects per lot
- Compute expected contact opens per wafer from the residue model
- Size HF and DMAC doses for a new array surface area
- Scale a test-capacitor breakdown result to a full die
- Size the equipment and cost for 150,000 wafer starts per month

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
