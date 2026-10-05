# Appendix C: Standard Procedures

Step-by-step procedures for qualifying and monitoring the dielectric etch modules. Each procedure lists purpose, materials, steps, and acceptance criteria. Values are illustrative.

---

## C.1 Edge-Etch Chamber Qualification

**Purpose:** Qualify an edge-etch chamber after installation, wet clean, or ring replacement.

**Materials:** 5 seasoning wafers (blanket ALD ZAZ on Si); 4 blanket-ZAZ monitor wafers (amorphous, 5.5 nm); 2 bare silicon sacrificial wafers; 3 product-equivalent wafers with a ZAZ-coated forest and a ZAZ-coated backside (from the same ALD run).

**Steps:**
1. Run the chlorine-first WAC (Chapter 9) and 5 seasoning wafers through the full recipe (BCl₃/Cl₂/Ar, 121 s).
2. On the monitor wafers measure ZAZ thickness by ellipsometry along four radial line scans (r = 140–150 mm) before and after the etch; locate the ZAZ edge.
3. Run 2 bare silicon wafers through the recipe with a dummy plasma; measure Si loss on the backside (ellipsometry on a Si step) and particles (> 30 nm).
4. Run 3 product-equivalent wafers. After the edge wet clean, collect VPD-ICPMS in 8 sectors × 3 zones (top ring, bevel, backside).
5. Measure the Al-marker peak time, averaged over four azimuthal sensors.
6. Compare with the fleet reference.

**Acceptance:**
```
Boundary position 147.0 ± 0.3 mm at all four scans; 3σ azimuthal variation ≤ 0.25 mm
ZAZ loss at r < 146 mm ≤ 0.1 nm
Zr after clean ≤ 1 × 10¹⁰ cm⁻² in every sector of every zone (VPD-ICPMS)
Si loss on backside ≤ 10 nm; particles added ≤ 10 per wafer (> 30 nm)
Al-marker time within ± 10% of fleet mean (expected 47 s)
Etch rate (amorphous ZrO₂) within ± 5% of fleet mean (3.7 nm/min)
```

---

## C.2 Boundary and Zone Verification

**Purpose:** Verify that the edge zone covers the ALD wrap-around, after any change of ALD pulse, gap, or mold height.

**Materials:** 3 product wafers after ALD and before the edge etch; 3 after the edge etch and clean.

**Steps:**
1. Measure the backside ZAZ thickness profile on the pre-etch wafers by reflectometry or XRF line scans from r = 150 mm inward to r = 140 mm, at 8 azimuths.
2. Fit x_sat (distance at which thickness falls to 50%) and the distance at which it falls to 10%.
3. Compute the required backside zone width W ≥ 1.5 x_sat + 0.4 mm and compare it with the pedestal radius setting (146.5 mm → 3.5 mm).
4. On the post-etch wafers confirm no ZAZ signal inside the zone and a boundary at the pedestal radius.

**Acceptance:**
```
Thickness at the zone's inner edge (r = 146.5 mm) ≤ 1% of full thickness (x_sat ≤ 2.1 mm for 3.5 mm zone)
Backside zone width ≥ 1.5 x_sat + 0.4 mm
If x_sat > 2.4 mm: widen the zone (Chapter 2) or reduce the ALD pulse/gap before release
```

---

## C.3 Conductor and Stop Chamber Qualification (P1/P2)

**Purpose:** Qualify the SiGe/TiN-stop chamber (and the fluorine chamber for BARC/W) after installation or wet clean.

**Materials:** Blanket monitors (TiN 5 nm on tetragonal ZAZ on SiN; TiOₓ-oxidized TiN; SiGe; resist); in-situ ellipsometry pad wafers (periphery pad, ZAZ on SiN); 3 full-stack plate wafers.

**Steps:**
1. Run the WAC (NF₃/O₂ then Cl₂ in the F chamber; fluorine-safe in the Cl/Br chamber, Chapter 9) and 5 seasoning wafers.
2. Measure TiN rate in Cl₂/Ar at 40 eV at 49 sites (blank TiN on SiN); breakthrough rate on oxidized TiN.
3. On pad wafers, run P2 (BT, Cl₂/Ar, 100% overetch relative to the Ti I inflection). Record Ti I inflection time, post-endpoint slope, and the in-situ ZAZ loss.
4. Measure ZAZ thickness before and after by ellipsometry on the pad and fit; measure F on the ZAZ by XPS or TOF-SIMS (ZrF₄ patches).
5. Run 3 plate wafers; measure SiGe foot notch (OCD) and TiN recess (cross-section) after P2.

**Acceptance:**
```
TiN rate (Cl₂/Ar, 40 eV) 16.5 nm/min ± 5% at all sites; uniformity ≤ 3% (1σ)
t_c (Ti I inflection) 18.2 ± 1.0 s
ZAZ apparent loss ≤ 0.10 nm at all pad sites (target 0.03–0.05)
Zr as ZrF₄ ≤ 1 × 10¹¹ cm⁻² (split chambers); F on the ZAZ by TOF-SIMS at or below baseline
SiGe foot notch ≤ 4.2 nm after P2 (total, Chapter 10)
No ZAZ loss at pinholes: ≤ 0.1 nm by pad ellipsometry after BT
```

---

## C.4 Strip Qualification (P3)

**Purpose:** Verify the strip removes resist and sets the TiOₓ shell and the WOₓ top.

**Materials:** Blanket KrF resist (350 nm) on Si; blanket TiN (5 nm) and W (40 nm) monitor wafers; 3 plate wafers after P2 (resist on, ZAZ exposed).

**Steps:**
1. Run the strip (O₂/N₂, 250 °C, 60 s) on the resist monitor; measure the clearing time (CO or ellipsometry).
2. Run the TiN and W monitors; measure oxide thickness by XRF or ellipsometry and W consumed by sheet resistance.
3. On the plate wafers measure the TiOₓ shell on the TiN edge by TEM/EELS and the W top oxide by TEM.
4. Inspect for resist residue at the plate foot and in 3 µm spaces.

**Acceptance:**
```
Resist cleared in ≤ 25 s (rate ≥ 0.8 µm/min); no BARC residue at the foot
TiOₓ shell 1.8 nm (1.65–2.2); WOₓ 2.5 nm (2.1–3.1); W consumed 0.7 nm (≤ 0.9)
Shell thickness × time: parabolic growth within ± 10% of x² = k t
No carbon (XPS) on the ZAZ pad above 1 × 10¹² cm⁻²
```

---

## C.5 Hot Clear (P4) Chamber Qualification

**Purpose:** Qualify a hot clear chamber after installation or wet clean, and set the shell-limited ion energy.

**Materials:** Blanket tetragonal ZAZ on SiN with TiOₓ-shelled TiN edge structures; blanket W (40 nm, oxidized 2.5 nm), SiN, and TiOₓ monitors; TXRF monitors (blanket ZAZ on SiN); 3 plate wafers after P3.

**Steps:**
1. Run the chlorine-first WAC (BCl₃/Cl₂, no fluorine) and 5 seasoning wafers. Record chuck, liner, and window temperatures.
2. Measure blanket rates at 80 eV: ZrO₂, Al₂O₃, SiN, W, TiOₓ shell (chemical), at 49 sites.
3. Run TXRF monitors through P4 with the production overetch (40%); measure Zr at 5 sites.
4. Run 3 plate wafers. Record the Al-marker time and SiN-onset time. Measure W thickness (XRF) and plate R_s, TiN recess (cross-section), SiN loss (ellipsometry).
5. Check the ion-energy window: run one wafer at 74 eV and one at 100 eV; confirm the shell margin ≥ 1.3 at the lower energy.

**Acceptance:**
```
ZrO₂ rate 12 nm/min ± 5% at 250 ± 3 °C; uniformity ≤ 3%
Zr on TXRF monitors ≤ 1 × 10¹³ cm⁻² at all sites (target ≤ 3 × 10¹²)
SiN loss ≤ 1.0 nm; W loss in P4 ≤ 1.7 nm (total with the strip ≤ 2.7 nm); R_s ≤ 4.0 Ω/□
TiN recess ≤ 5 nm (target 2.1); shell remaining ≥ 0.3 nm at the end of the step
Al-marker time within ± 4% of fleet mean (expected 14 s)
No B₂O₃ particles; particles added ≤ 10 per wafer
```

---

## C.6 Thermal-ALE Reactor Qualification

**Purpose:** Qualify a thermal ALE reactor (trim, rework, finish) after installation, PM, or a pedestal change.

**Materials:** Blanket amorphous ZAZ monitors (5.5 nm) and tetragonal monitors; forest test wafers (ZAZ-coated pillar array, cross-sectionable); witness crystals; pad wafers.

**Steps:**
1. Set the pedestal to 280 °C (265 °C for trim); measure temperature uniformity at 9 sites.
2. Run a saturation curve: removal per cycle against HF exposure (0.01–0.3 Torr·s) and DMAC exposure on blanket monitors. Find the saturation exposure; set pulses at ≥ 2× saturation.
3. Run 20 cycles on blanket amorphous and tetragonal monitors; measure removal at 49 sites by ellipsometry; compute EPC.
4. Run 20 cycles on forest wafers; cross-section at the top, middle, and bottom of pillars by TEM; compute removal at each height.
5. Calibrate the witness crystal: Δf per cycle against pad EPC.
6. Run the purge check: HF residual before the DMAC pulse (mass spectrometer or witness).

**Acceptance:**
```
Pedestal temperature uniformity ≤ ± 2 °C (3σ)
EPC (280 °C) amorphous 0.073 ± 0.004 nm; tetragonal 0.047 ± 0.003 nm; uniformity ≤ 3% (1σ)
Saturation exposure found; pulses ≥ 2× it; DMAC dose margin ≥ 1.5 along the pillar
Removal at the pillar bottom within 10% of that at the top
Witness crystal Δf per cycle 3.2 Hz ± 0.3 Hz (6 MHz)
HF residual after purge ≤ 10⁻⁴ of the dose
```

---

## C.7 ALD-Chamber Clean Verification

**Purpose:** Verify an ALD chamber clean (Module C) after recipe change or at a wafer-count trigger revision.

**Materials:** 2 witness coupons per location (wall, showerhead, pedestal edge) with ALD ZAZ of the accumulated thickness; 5 bare silicon wafers; thickness and particle metrology.

**Steps:**
1. Record wafers since the last clean and the accumulated deposit (5.5 nm per wafer).
2. Run the remote-plasma BCl₃/Cl₂ clean at 350 °C; remove coupons and measure residual film by XRF Zr.
3. Season the chamber (2–3 dummy ZAZ depositions); run 5 bare wafers; measure particles and thickness (9 sites) on the first wafer.
4. Inspect the showerhead and pedestal edge for ZrF₄ or flakes (visual, particle counts).

**Acceptance:**
```
Residual Zr on coupons ≤ 1 × 10¹⁵ cm⁻² (≈ 0.1 nm); no fluorine used at any step
First wafer thickness within ± 0.2 nm of nominal; uniformity ≤ ± 0.2 nm
Particles ≤ 10 per wafer (> 30 nm)
Clean interval ≤ flake onset (0.5–1 µm; 91–182 wafers)
```

---

## C.8 Zirconium Canary

**Purpose:** Detect zirconium transfer into a clean-zone tool.

**Materials:** Bare silicon wafers (prime), TXRF and VPD-ICPMS access.

**Steps:**
1. Run a bare wafer through the tool with a dummy recipe (temperature, chuck, transfer path as production).
2. Measure Zr on the front by TXRF at 5 sites and on the backside by VPD-ICPMS (8 sectors).
3. If any value exceeds the limit, quarantine the tool; trace by sector to the contact surface; swap the chuck or ring; wet-clean; repeat the canary.

**Acceptance:**
```
Zr on front and backside ≤ 1 × 10¹⁰ cm⁻² at all sites and sectors
Fe, Ni, Cu on the backside ≤ 5 × 10¹⁰ cm⁻² (Book #32, Chapter 9)
```

---

## C.9 Trim-Dose Array Experiment

**Purpose:** Calibrate leakage, capacitance, and TDDB against trim cycles, and detect chemical damage.

**Materials:** Monitor wafers carrying capacitor test arrays (10⁶ cells), processed through ALD and the thermal reactor with 0, 1, 2, 3, and 4 cycles in separate regions or on separate wafers; the oxidizing step after the trim; top electrode and plate.

**Steps:**
1. Trim regions by cycle count (mask the others with a removable cap, or use separate wafers).
2. Complete the capacitor (top electrode, plate, contacts) with the production flow.
3. Measure C_s, leakage at 0.55 V and 1.0 V (median and tail), and TDDB on large-area capacitors.
4. Fit log₁₀(leakage) against cycles; compare with 0.162 per cycle (10^(0.073/0.45) = 1.45).

**Acceptance:**
```
C_s change per cycle +1.3% (± 0.2%)
Leakage factor per cycle 1.45 ± 0.15 (slope below 1.6 = no excess chemical damage)
TDDB multiplier consistent with M = (t₀/t)^(nβ)
Monthly; and after any change of ligand donor, temperature, or oxidizing step
```

---

**Appendix C Version:** 1.0
