# Appendix C: Standard Procedures

Step-by-step procedures for qualifying and monitoring the dielectric-clear module. Each procedure lists purpose, materials, steps, and acceptance criteria. Values are illustrative.

---

## C.1 D1 Chamber Qualification

**Purpose:** Qualify a hot dielectric-clear chamber after installation or wet clean.

**Materials:** 30 seasoning wafers (blanket crystallized ZrO₂ 20 nm on PECVD SiN); blanket monitors: crystallized ZrO₂ (20 nm), PECVD SiN, PE-TEOS; 3 full-structure wafers (plate etched and stripped, periphery ZAZ, edge gratings, contact-chain test sites); 1 particle wafer; 1 backside-contamination wafer.

**Steps:**
1. Bake the chamber at operating wall temperature (120 °C) for 4 h after pump-down. Verify chuck zones at 236 °C setpoint and wafer offset (thermocouple wafer) of 14 ± 2 °C under a standard plasma.
2. Run the per-wafer waferless clean, then seasoning wafers through the full recipe until the ZrO₂ rate and the Al-marker time on two consecutive structure-like wafers are within 1% of the fleet baseline.
3. Measure blanket ZrO₂, SiN, and PE-TEOS rates at 49 sites in the ME chemistry for 30 s.
4. Run the particle wafer (full recipe, no film) and the backside wafer (full recipe, then backside TXRF).
5. Run 3 structure wafers. Record BT reflected power, t_EP, Al-marker centre and width, Si-rise slope, BO drop, V_pp, wafer offset.
6. On structure wafers: TXRF Zr on 5 periphery sites; e-beam inspection 20 mm²; SiN and cap remaining (ellipsometry); edge-grating OCD for TE and SiGe recess; TEM at centre and edge.
7. Compare with the fleet reference.

**Acceptance:**
```
ZrO₂ rate 9.0 ± 0.2 nm/min; uniformity ≤ 1.5% (1σ) with zone tuning
SiN rate 3.0 ± 0.3 nm/min; PE-TEOS 2.0 ± 0.3 nm/min; selectivity ≥ 2.7
t_EP 36 ± 1.5 s; Al-marker width 4.0 ± 0.4 s
TXRF Zr ≤ 1 × 10¹² /cm² (typical) and ≤ 1 × 10¹³ (limit)
E-beam islands ≤ 4 in 20 mm²
SiN loss ≤ 2 nm at all sites; cap remaining ≥ 48 nm
TE recess ≤ 2 nm (OCD, TEM); ZAZ undercut ≤ 0.5 nm (TEM)
Particles ≤ 10 adders ≥ 30 nm; backside Zr ≤ 1 × 10¹⁰ /cm²
```

---

## C.2 D1 Daily Monitor

**Purpose:** Detect drift in rate, selectivity, and uniformity.

**Steps:**
1. Run one blanket crystallized-ZrO₂ monitor and one SiN monitor in the ME chemistry for 30 s.
2. Measure 49 sites by ellipsometry.

**Acceptance:**
```
ZrO₂ rate within ± 3% of the chamber baseline; uniformity ≤ 2% (1σ)
SiN rate within ± 10%
Centre-to-edge difference within ± 2% (ring wear indicator)
```

---

## C.3 D2 (Plasma ALE) Chamber Qualification

**Purpose:** Qualify an ALE chamber after installation or major maintenance.

**Steps:**
1. Verify gas switching: pressure trace shows purge to ≤ 1% residual within 0.2 s (residual-gas analyser or OES Cl 837.6 nm in step B).
2. Verify bias: step-B ion energy distribution (retarding-field analyser wafer) 60 ± 3 eV mean; > 99% inside 45–70 eV; turn-on overshoot ≤ 10 eV.
3. Saturation curves: EPC versus step-A time (0.3–3 s) and step-B time (0.5–5 s) on crystallized ZrO₂, 50 cycles each.
4. Window: EPC versus step-B bias (20–120 eV equivalent).
5. Synergy: α (A only, 50 cycles) and β (B only, 50 cycles).
6. SiN EPC: 100 cycles on blanket SiN.
7. Structure wafers as in C.1 steps 5–6, with the per-cycle signals.

**Acceptance:**
```
EPC 0.100 ± 0.003 nm (ZrO₂ tetragonal); within ± 2% of fleet mean
Knee of both saturation curves ≤ 0.67 × the recipe step time
Window ≥ 20 eV wide, containing 60 eV with ≥ 10 eV margin on each side
Synergy ≥ 85%
SiN EPC 0.012 ± 0.003 nm
Per-cycle Si endpoint within ± 5 cycles of the feed-forward prediction
```

---

## C.4 Waferless Clean and Seasoning After Wet Clean

**Purpose:** Restore a steady wall state after a wet clean of the D1 chamber.

**Steps:**
1. Install the refurbished kit (liner, window, ring). Leak check ≤ 1 mTorr/min.
2. Pump down; bake at 120 °C wall temperature for 4 h.
3. Run 10 waferless cleans (with cover wafer) back-to-back.
4. Run 20–50 seasoning wafers through the full recipe with the per-wafer clean.
5. After every 10 seasoning wafers, run a structure-like monitor; record ZrO₂ rate and Al-marker time.

**Acceptance:**
```
Two consecutive monitors within 1% of the pre-clean baseline for ZrO₂ rate
and Al-marker time; Zr I baseline between wafers within 20% of baseline
```

**Never:** use NF₃, SF₆, or O₂ waferless cleans in this chamber (fluorine trap and boron glass, Chapter 9).

---

## C.5 BCl₃ Cylinder Change

**Purpose:** Change a BCl₃ cylinder without introducing moisture.

**Steps:**
1. Close the cylinder valve; pump the pigtail and line to the gas-cabinet vacuum.
2. Cycle-purge the pigtail with dry N₂ (≤ 10 ppb H₂O) and vacuum, 20 cycles.
3. Exchange the cylinder; leak check the connection (helium, ≤ 1 × 10⁻⁹ mbar·L/s).
4. Cycle-purge 20 more times; open the cylinder; flow BCl₃ to the divert line for 10 min.
5. Run one blanket ZrO₂ monitor; check rate and particle count.

**Acceptance:**
```
Leak rate within limit; ZrO₂ rate within ± 2% of baseline; particle adders ≤ 10
No boron-containing particles in the monitor's defect review
```

---

## C.6 Post-Etch Treatment and Rinse Check

**Purpose:** Verify surface chlorine and boron removal after D1.

**Steps:**
1. Process a structure wafer through D1, PET, and rinse.
2. XPS on a periphery pad: B 1s, Cl 2p, N 1s, Si 2p, Zr 3d.
3. TXRF Cl on 5 sites.
4. Optional: ToF-SIMS on the edge grating for Cl and B per unit edge length.

**Acceptance:**
```
Cl ≤ 1 at% (XPS); B ≤ 2 × 10¹⁴ /cm²; Zr 3d below XPS detection
Edge grating Cl within ± 30% of the qualification reference
```

---

## C.7 Backside and Bevel Zirconium Gate

**Purpose:** Release wafers from the high-k tool set to shared tools.

**Steps:**
1. After the bevel etch and before the ILD, sample one wafer per lot.
2. Backside TXRF at 5 sites (centre and four at 140 mm radius); bevel scan if available.
3. If any site exceeds the limit, hold the lot and measure all wafers.

**Acceptance:**
```
Backside Zr ≤ 1 × 10¹⁰ /cm² at every site; bevel Zr ≤ 1 × 10¹¹ /cm²
```

---

## C.8 Overlap-Ladder and Comb Evaluation

**Purpose:** Measure the damage reach and edge leakage of a route or a recipe change (Chapters 11 and 13).

**Steps:**
1. Process a split of at least 5 wafers per condition through to the first metal.
2. Measure ladder arrays (overlap 0, 0.1, 0.2, 0.4, 0.8 µm): leakage per cell at ±1 V, 85 °C; retention-tail fraction at 64 ms.
3. Measure plate-edge combs at 1.1 V, 85 °C.

**Acceptance:**
```
Ladder: leakage at 0.2 µm within 3% of 0.8 µm; damage reach ≤ 0.15 µm
Comb: ≤ 1 pA per mm of facing edge
No difference from the reference route beyond 2σ of the wafer-to-wafer spread
```

---

**Appendix C Version:** 1.0  
**Last Updated:** 2026-10-05
