# Appendix G: Troubleshooting Guide

Symptom-driven guide for DRAM capacitor dielectric etch excursions. For each symptom: likely causes ranked from most to least common, checks to separate them, and corrective actions. Chapter references point to the underlying physics.

---

## G.1 Zirconium Above the Limit on a Backside or in a Clean-Zone Tool

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────────
1. Edge etch bypassed or recipe skipped    Lot history; MES route; VPD         Hold lots; trace chuck
   (Ch. 1.4, 9.2)                          sectors on the wafer                contacts; canary the tools
2. Backside zone too narrow for the wrap   x_sat line scan; ALD pulse/gap      Widen zone or shorten pulse;
   (ALD pulse up, gap up) (Ch. 2.5)        log; mold height change             re-run C.2
3. Edge wet clean skipped or weak          HF dose and time; nozzle           Restore clean; recheck
   (Ch. 5.6)                               alignment; VPD after clean          removal factor (≥ 4,000)
4. Edge ring worn; plasma shadowed         RF hours; sector map shows one      Replace ring; check
   (Ch. 5.5)                               azimuth high                        centring
5. Fluorine on a Zr-coated wall (ZrF₄      WAC log; wall inspection;           Wet clean; replace liner and
   flakes) (Ch. 9.3, 9.4)                  particles with Zr and F             ring; re-season
```

## G.2 Edge-Die Capacitance or Leakage Shift (r = 140–146 mm)

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────────
1. Boundary inside r = 146 mm              ZAZ line scan; plate gap and        Replace plate; check gap
   (plate gap, purge, centring) (Ch. 5.4)  purge flow; centring log            and purge; re-centre
2. B or Cl redeposit on the edge dies      XPS at r = 144–146 mm; O₂/H₂O       Restore strip; lengthen
   (Ch. 11.6)                              strip log                           strip; check wall T
3. ALD edge thickness profile              Ellipsometry r = 140–147 mm         Fix ALD edge ring / flow
   (Ch. 2.6)
4. Edge-ring wear in the top-electrode     Edge thickness of TiN; RF hours     Replace ring (not an etch
   or plate tools                                                              issue)
```

## G.3 Periphery Contact Opens (Wafer Edge or Random)

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────────
1. σ_g drift (chuck cold; film crystal.    Al-marker time; chuck T log; TEM   Raise OE to 40–45% (shell
   change) (Ch. 16.3.1)                    of grains                            ≥ 1.3×); restore chuck T
2. Ion energy below 74 eV (bias drift)     Bias V_pp; IEDF; shell margin       Restore bias; check
   (Ch. 7.3)                                                                    matching
3. ZrF₄ patches not converted (F memory;   TOF-SIMS F on ZAZ at P2 exit;       Split F/Cl chambers; check
   cold P4) (Ch. 10.3)                     WAC log                             P4 chuck T
4. Hot chuck non-uniform at the edge       Edge Al-marker time; ring           Replace ring; heater zone
   (Ch. 7.5)                               condition                           offset
5. Veil or flake from walls (Ch. 9)        Particle composition (Zr, B)        Wall clean; chlorine first
```

## G.4 ZAZ Loss in the Stop Above 0.15 nm

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────────
1. Ion energy up at the stop (bias, IEDF   V_pp; pad ellipsometry vs E;       Restore 40 eV; reduce bias 5%
   tail) (Ch. 4.2.3, 10.2)                 post-endpoint slope
2. Fluorine on the ZAZ (wall memory)       WAC log; time from W step; XPS/     Split chambers; clean WAC;
   (Ch. 10.3)                              TOF-SIMS F                          lengthen W→P2 interval
3. BT energy hitting the ZAZ at pinholes   BT V_pp; pinhole density on TiN     Lower BT energy; shorten BT
   (Ch. 4.3.1)
4. Overetch too long relative to t_c       P2 time log vs t_c                  Restore endpoint-relative
   (Ch. 8.2.3)                                                                  overetch (100%)
```

## G.5 TiN Notch Above 15 nm or ILD Voids

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────────────
1. Shell breached: strip short, P4 long,   TEM/EELS shell; strip time; P4       Strip ≥ 50 s; step ≤ 41.5 s;
   energy low (Ch. 4.4.3, 7.2)             step time                           E ≥ 74 eV
2. Chuck too hot or Cl₂ fraction high      Chuck T; recipe Cl₂ %               Restore (≤ 260 °C; Cl₂ ≤ 30%)
   (Ch. 7.5)
3. Corrosion after P5 (Cl at the edge,     Queue log; XPS Cl; humidity         PET; shorten queue; vacuum
   moisture) (Ch. 7.6)                                                         transfer
4. SiGe foot notch from P2 (Cl₂ long)      OCD foot; P2 time                   HBr in P2; deposition-mode
   (Ch. 10.5)                                                                  fallback
```

## G.6 Plate Resistance High

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. Strip too long; WOₓ thick (Ch. 7.2)     Strip time; XRF W; TEM WOₓ         Reduce to 50–60 s
2. P4 energy high; W rate up (Ch. 7.3)     Bias V_pp; W loss in P4            Restore 80 eV
3. P4 overetch too long (Ch. 16.3)         Step time log                      ≤ 45% OE
4. W corrosion after P5 (Ch. 7.6)          Cl on W edge; queue                Shorten queue; PET
```

## G.7 Cell Leakage Tail or TDDB Shift After Module P

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────────
1. Charging with the plate exposed         Polarity pairs; antenna arrays;     Pulse P4 bias; cap the W
   (Ch. 7.4, 12)                           ring in the tail map                (5 nm SiN); shorten P4
2. Separation transient in P2 (bank-level) Bank map of the tail; t_c spread    Narrow the TiN clearing
   (Ch. 7.4.2)                                                                  spread; check uniformity
3. Edge damage reaching cells (small       Edge-proximity arrays               Increase overlap; liner
   overlap) (Ch. 11, 12)
```

## G.8 Capacitance Low or Leakage High After Trim

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────────
1. Wrong cycle count (ellipsometry offset) Calibration vs TEM/XRR; EPC log    Recalibrate; re-run C.6
   (Ch. 15.2)
2. EPC high (pedestal hot; DMAC high)      Witness Δf; pedestal T              Restore; hold loop at ±8%
   (Ch. 6.7)
3. Chemical damage (F, C) in the film      Trim-dose slope > 1.6×/cycle        Add or lengthen the
   (Ch. 12.3)                                                                  oxidizing step; lower T
4. Rework count > 1                        Lot history; C_s per rework 1.4%   Scrap or sort; enforce rule
   (Ch. 13.6)
```

## G.9 Thermal ALE Removal Low at the Pillar Bottom

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────────
1. DMAC dose margin < 1.5 (pulse or        Pulse and pressure traces;          Raise to 0.10 Torr or 3 s
   pressure low; AR up) (Ch. 6.2, 13.4)    TEM top/middle/bottom
2. DMAC line cold (condensation)           Line temperatures                   Heat ≥ 120 °C
3. HF depleted (cylinder cold)             Cylinder T; flow                    Restore cabinet T
4. Purge too short (CVD of HF + DMAC)      Residual HF; haze                   Lengthen purge to ≥ 9τ
```

## G.10 ALD-Chamber Flakes or First-Wafer Thickness Off

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────────
1. Clean interval beyond flake onset       Wafers since clean; deposit µm      Shorten to ≤ 120–180 wafers
   (Ch. 9.4)
2. Fluorine used on a Zr wall (ZrF₄)       Clean recipe history                Wet clean; replace parts
   (Ch. 9.4.2)
3. Season missing after clean              Season log; first-wafer ellipsometry Add 2–3 dummies
4. Pedestal film shrinking the gap         Gap g from wrap profile             Clean pedestal; recheck zone
   (Ch. 9.4.1)
```

---

## G.11 Decision Notes

```
"Zr on a clean-zone canary":      quarantine → sectors → contact surface → chuck swap → wet clean → re-canary
"Opens at the wafer edge only":   ring and chuck T first; then Al marker; then F skin (TOF-SIMS)
"Edge dies shifted, centre fine": boundary and redeposit first (G.2), not the plate etch
"Trim lots low C_s":              calibration (cycle count) before chemistry
"Everything tail-limited":        σ_g is the cheap lever: overetch to 40–45% within the shell margin
```

---

**Appendix G Version:** 1.0
