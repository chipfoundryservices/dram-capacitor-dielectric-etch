# Index: Book #33 Navigation Guide

## Quick Navigation

**Total Content:** 16 chapters + 7 appendices + glossary  
**Estimated Read Time:** 20–28 hours for the complete book; 5–9 hours for a focused reading path

| Part | Chapters | Theme |
|------|----------|-------|
| I | 1–4 | Fundamentals: the dielectric and why it is etched, the ZAZ film, metal-oxide removal chemistry, selectivity design |
| II | 5–9 | Hardware: edge chambers, thermal reactors, strip-then-clear chambers, in-situ monitoring, zirconium contamination and the ALD clean |
| III | 10–14 | Phenomena: stopping on the dielectric, the dielectric edge, etch-induced defects, trim and rework, advanced dielectrics and 3D |
| IV | 15–16 | Production: metrology, inspection, APC, integration, yield, cost |

---

## Part I: Fundamentals (Chapters 1–4)

### Chapter 1: [The Capacitor Dielectric & Why It Is Etched](./chapters/01-capacitor-dielectric-role.md)
**Estimated Time:** 55 min | **Difficulty:** Foundation | **Reading Level:** All roles  
**Focus:** What does the dielectric do, how much can it lose, and why must it go from everywhere else?

**Key Topics:**
- C_s = 8.57 fF; each 0.1 nm of film is 1.9% of capacitance and ×1.7 in leakage
- Retention headroom: 0.28 nm of equivalent thickness
- Film area 26× the flat wafer; Zr inventory 1.44 × 10¹⁶ cm⁻² and the three limits (10¹³, 10¹¹, 10¹⁰)
- The four dielectric etches (E, P, T, C) and their places in the flow; the specification sheet

**Critical Equations:** C_s = ε₀·3.9·A/EOT; EOT = 3.9t/k_eff; J(V) = J₁exp[(V − 1)/0.12]  
**Study Questions:** 6

---

### Chapter 2: [The ZAZ Film as the Etch Sees It — Growth, Crystallization, Wrap-Around & Stress](./chapters/02-zaz-film-as-etch-sees-it.md)
**Estimated Time:** 60 min | **Difficulty:** Intermediate | **Reading Level:** Process/Integration  
**Focus:** What does each etch inherit from the deposition and its thermal history?

**Key Topics:**
- 107 ALD cycles; amorphous until the top electrode (X = 0.41), tetragonal after the SiGe furnace
- Rate against crystallinity: 9 → 6 nm/min; the grain tail is absent in amorphous film
- Forest dosing t_sat = 1.6 s (AR 109); the same 2 s pulse wraps the backside by 2.1 mm
- Edge zone 3.0 mm top / 3.5 mm back; bevel stack energy 0.1 J/m²

**Critical Equations:** X(t) = 1 − exp[−(t/τ)ⁿ]; t_sat = 6N_sAR²/(n₀v̄); x_sat = g√(n₀v̄t/3N_s)  
**Study Questions:** 6

---

### Chapter 3: [Surface Chemistry of Metal-Oxide Removal — Plasma, Thermal & Wet](./chapters/03-metal-oxide-removal-chemistry.md)
**Estimated Time:** 65 min | **Difficulty:** Advanced | **Reading Level:** Process/Research  
**Focus:** Which route removes zirconia, and why does fluorine alone fail?

**Key Topics:**
- ΔH: Cl₂ +120, BCl₃ −191, HF −201 kJ/mol; ZrF₄ trap; BCl₃ converts ZrF₄ (−45) but not AlF₃ (+74)
- One yield model (K = 3.9 nm/s); E_th 45 eV (amorphous), 60 eV (tetragonal); no ions, no etch
- Thermal ALE: EPC(T), 0.073 nm at 280 °C, 1.2%/°C; 80 cycles strip the film
- What each route leaves on the surface

**Critical Equations:** ER = K·A(√E − √E_th); EPC(T) = EPC_max/[1 + exp(−(T − T₀)/ΔT)]  
**Study Questions:** 6

---

### Chapter 4: [Selectivity Design — The Dielectric as Target and as Stop Layer](./chapters/04-selectivity-target-and-stop.md)
**Estimated Time:** 65 min | **Difficulty:** Advanced | **Reading Level:** Process/Integration  
**Focus:** What selectivity does each etch need, and what do the five routes cost?

**Key Topics:**
- Selectivity matrix: six chemistries against ten films
- Stop requirement S ≥ 18 (5.4 nm TiN-equivalent over 0.3 nm); Cl₂/Ar at 40 eV gives 110–180
- W (≤ 2.7 nm), SiN, and shell (≥ 1.64 nm) budgets of the clear
- Early removal: overetch 19% (amorphous) against 51% (ambient tetragonal); routes R0–R4

**Critical Equations:** S ≥ OE·t_TiN/loss; t_W ≥ ρ_W/R_W; shell life = shell/2.0 nm/min  
**Study Questions:** 6

---

## Part II: Hardware Design (Chapters 5–9)

### Chapter 5: [Edge & Bevel Etch Chambers](./chapters/05-edge-bevel-etch-chambers.md)
**Estimated Time:** 50 min | **Difficulty:** Intermediate | **Reading Level:** Equipment/Process  
**Key Topics:** Plate gap 0.3 mm (p·g = 0.006 Torr·cm); sharp ion-assisted boundary; 121 s, 89 wph per mainframe; boundary budget 0.21 mm vs 0.30; plasma leaves 4 × 10¹³ Zr cm⁻², edge wet clean removes ×6,700  
**Critical Equations:** p·g; RSS of boundary contributions; throughput = 3600/(t + handling)  
**Study Questions:** 6

### Chapter 6: [Thermal & Vapor-Phase Etch Reactors](./chapters/06-thermal-vapor-etch-reactors.md)
**Estimated Time:** 50 min | **Difficulty:** Advanced | **Reading Level:** Equipment/Process  
**Key Topics:** ± 2 °C; film stays amorphous; t_sat(HF) 0.41 s, t_sat(DMAC) 0.84 s at AR 109; purge 9.5τ; single, mini-batch, and batch throughput by task; HF materials, delivery, and abatement  
**Critical Equations:** t_sat = 6N_sAR²/(n₀v̄); τ = pV/Q  
**Study Questions:** 6

### Chapter 7: [Dedicated Dielectric-Clear Chambers & the Strip-Then-Clear Route](./chapters/07-dedicated-dielectric-clear-chambers.md)
**Estimated Time:** 60 min | **Difficulty:** Advanced | **Reading Level:** Equipment/Integration  
**Key Topics:** P1–P5, 247 s; shell 1.8 nm and WOₓ 2.5 nm set by strip time; ion-energy window ≥ 74 eV; W loss 2.25 nm; charging 1.30 V and 1.7× the charge; vacuum transfer and P5  
**Critical Equations:** shell = 1.8√(t/60); ΔV = 0.12 ln(J/J₁); antenna ratio  
**Study Questions:** 6

### Chapter 8: [In-Situ Monitoring & Etch-Amount Control for a 5 nm Film](./chapters/08-insitu-monitoring-thin-dielectric.md)
**Estimated Time:** 50 min | **Difficulty:** Intermediate | **Reading Level:** Equipment/Process  
**Key Topics:** Edge emission 8–12× weaker than Book #32's HK step; endpoint-relative overetch; Al marker without resist; in-situ ellipsometry ± 0.01 nm; witness crystal 3.2 Hz per cycle; cycle-count control  
**Critical Equations:** release rate = area × inventory / time; Δf = C_f·Δm; N = round(d/EPC_now)  
**Study Questions:** 6

### Chapter 9: [Zirconium Contamination, Chamber Walls & the ALD-Chamber Clean](./chapters/09-zirconium-contamination-ald-chamber-clean.md)
**Estimated Time:** 50 min | **Difficulty:** Intermediate | **Reading Level:** Equipment/Facilities  
**Key Topics:** Zones and the 10¹⁰ rule; one dirty wafer contaminates 370 others; conductor chambers stay Zr-free in R1; ALD wall deposit 182 wafers per µm; fluorine makes ZrF₄ (×1.75 volume); remote BCl₃/Cl₂ clean, 19 s per wafer  
**Critical Equations:** C_w(n) = f·C_c·(1 − f)ⁿ; clean time = thickness/rate  
**Study Questions:** 6

---

## Part III: Process Phenomena (Chapters 10–14)

### Chapter 10: [Stopping on the Dielectric — Conductor Overetch, Fluorine Skins & Surface Modification](./chapters/10-stopping-on-the-dielectric.md)
**Estimated Time:** 60 min | **Difficulty:** Advanced | **Reading Level:** Process/Research  
**Focus:** What does the stop do to the ZAZ, and what does it leave for the clear?

**Key Topics:**
- ZAZ loss 0.03–0.05 nm: tail ions < 0.004 nm, the rest surface modification
- Fluorine memory: 1.5 × 10¹³ F cm⁻² → 3.8 × 10¹² ZrF₄; split chambers ÷100; hot BCl₃ converts it
- SiGe foot notch 2.7–4.2 nm; TiN recess 2.1 nm (10.7 nm if the shell is 1.0 nm)
- Deposition-mode fallback

**Critical Equations:** n_F(t) = n₀[a e^(−t/τ₁) + b e^(−t/τ₂)]; dose = ∫¼ n v̄ s dt  
**Study Questions:** 6

### Chapter 11: [The Dielectric Edge — Profile, Undercut, Overlap & Seal](./chapters/11-dielectric-edge-undercut-seal.md)
**Estimated Time:** 50 min | **Difficulty:** Intermediate | **Reading Level:** Integration/Device  
**Key Topics:** Plate edge by route; isotropic reach 1.3–21 nm; overlap budget 152–173 nm, O_min 0.23–0.26 µm against 1.5 µm; seals; B redeposition inside the edge-etch boundary  
**Critical Equations:** O_min = 1.5 × Σ contributions; C(x) = C₀e^(−x/λ); E_edge/E_flat = t/[r ln(1 + t/r)]  
**Study Questions:** 6

### Chapter 12: [Etch-Induced Defects in the Dielectric — Vacancies, Halogens, Leakage & TDDB](./chapters/12-etch-induced-dielectric-defects.md)
**Estimated Time:** 60 min | **Difficulty:** Advanced | **Reading Level:** Device/Research  
**Key Topics:** O displaced at 24 eV, Zr at 47 eV; damage depth 1–2.7 nm; damage as equivalent thickness; the 10% leakage specification is 0.019 nm; 0.2 nm trim → TDDB ×3.0 shorter; the edge contributes nothing at 1.5 µm  
**Critical Equations:** γ = 4m₁m₂/(m₁ + m₂)²; ΔT_eq = w(1 − η); M = 1 + f_d(k^β − 1)  
**Study Questions:** 6

### Chapter 13: [Thinning, Trim & Rework](./chapters/13-thinning-trim-rework.md)
**Estimated Time:** 55 min | **Difficulty:** Intermediate | **Reading Level:** Process/Integration  
**Key Topics:** Trim to nominal, not below (13.7% of lots; 0.05–0.07 nm of headroom); 265 °C granularity; dose margin along the pillar; ALE finish worth it only below σ_EPC 5%; rework limit one (−1.4% C_s each)  
**Critical Equations:** N = round(Δt/EPC); z = OE/σ_EPC; saturated fraction = min(1, √M)  
**Study Questions:** 6

### Chapter 14: [Advanced Dielectrics & 3D Architectures](./chapters/14-advanced-dielectrics-3d.md)
**Estimated Time:** 50 min | **Difficulty:** Advanced | **Reading Level:** Integration/Research  
**Key Topics:** Volatility map (Class V and N); dopant residue 14–72× the limit; TiO₂ and HF alone; SrTiO₃ wet clear; 1d-class: AR 195, pulse ×3.2, zone 6.0 mm; 3D DRAM lateral recess of 205 cycles  
**Critical Equations:** residue = x × 1.44 × 10¹⁶; t_sat ∝ AR²; x_sat ∝ √t  
**Study Questions:** 6

---

## Part IV: Production Scale (Chapters 15–16)

### Chapter 15: [Metrology, Inspection & Advanced Process Control](./chapters/15-metrology-inspection-apc.md)
**Estimated Time:** 50 min | **Difficulty:** Intermediate | **Reading Level:** Process/Metrology  
**Key Topics:** Calibration chain TEM → XRR → XRF/ellipsometry; XRF counts atoms; TXRF vs VPD-ICPMS by decade; sector sampling; contact chains need 9 × 10⁹ contacts; feed-forward of ALD thickness; EWMA on EPC; fault detection  
**Critical Equations:** P(wrong N) = 2[1 − Φ(0.0365/σ)]; N = −ln 0.05/P; EPC_{n+1} = λ·EPC_meas + (1 − λ)·EPC_n  
**Study Questions:** 6

### Chapter 16: [Integration, Yield & Cost of Ownership](./chapters/16-integration-yield-coo.md)
**Estimated Time:** 55 min | **Difficulty:** Intermediate | **Reading Level:** Integration/Management  
**Key Topics:** Hand-offs and yield signatures; R1 opens 1.5 × 10⁻⁴ per die and its steep σ_g sensitivity (6% → 0.33); 21 chambers against 24; R1 $10.53 vs R0 $10.70; edge etch $3.44 and its break-even; ALE finish as insurance; decisions and checklist  
**Critical Equations:** Y = exp(−N·P_open); depreciation = capex/5/(wph × 8760 × 0.85)  
**Study Questions:** 6

---

## Appendices

- [Appendix A: Material Properties](./appendices/A-material-properties.md)
- [Appendix B: Chemistry & Thermochemistry Data](./appendices/B-chemistry-thermochemistry-data.md)
- [Appendix C: Standard Procedures](./appendices/C-standard-procedures.md)
- [Appendix D: Process Windows](./appendices/D-process-windows.md)
- [Appendix E: Etch, Trim, Wrap & Charging Calculations](./appendices/E-etch-trim-wrap-charging-calculations.md)
- [Appendix F: Metrology Reference](./appendices/F-metrology-reference.md)
- [Appendix G: Troubleshooting Guide](./appendices/G-troubleshooting-guide.md)
- [Glossary](./GLOSSARY.md)

---

## Reading Paths by Role

**Process Engineer (8 h):** Ch. 1 → 2 → 3 → 4 → 10 → 13 → App. D, G  
**Equipment Engineer (7 h):** Ch. 1 → 5 → 6 → 7 → 8 → 9 → 15  
**Integration Engineer (8 h):** Ch. 1 → 2 → 4 → 7 → 11 → 13 → 16  
**Device Engineer (5 h):** Ch. 1 → 11 → 12 → 13 → 16  
**Researcher (8 h):** Ch. 3 → 6 → 12 → 13 → 14 → App. E

---

## Study Questions Overview

**Total Study Questions:** 96 (6 per chapter × 16 chapters)  
**Nature:** Mostly calculation-based  
**Topics:** Capacitance and leakage headroom, zirconium inventory, crystallization, dosing and wrap-around, enthalpies and yield, EPC and temperature, stop selectivity, strip and shell, ion-energy windows, charging clamps, release rates and ellipsometry, contamination transfer, fluorine dose, overlap budgets, vacancy and TDDB scaling, trim policy and rework, dopant residue, 3D recess, chain statistics, EWMA, equipment counts, cost and break-even

Examples:
- Compute the cell capacitance and sense signal for a thinner dielectric
- Find the backside zone for a taller mold from the ALD pulse
- Compute the minimum ion energy that keeps the TiOₓ shell alive for a 1.3× margin
- Estimate the fluorine dose and ZrF₄ coverage for a changed memory
- Compute the TDDB multiplier of a 0.15 nm trim
- Choose the trim cycle count and temperature for an over-thick lot
- Run the EWMA on the removal per cycle for three lots
- Compute the wafers of contact chains needed to bound an open rate
- Size chambers for 150,000 wafer starts per month
- Compute the break-even of the edge etch for a given event cost

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
