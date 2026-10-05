# Appendix F: Metrology Reference

Methods used for the dielectric-clear module: what each measures, its sensitivity and precision, its sampling cost, and its main pitfalls. Values are illustrative.

---

## F.1 Film Thickness and Dimensional Metrology

```
Method          Measures                       Precision (3σ)   Time/site   Pitfalls
──────────────────────────────────────────────────────────────────────────────────────────
Spectroscopic   periphery ZAZ thickness;       0.03 nm (ZAZ)     ≈ 2 s       ZAZ/SiN index contrast
ellipsometry    SiN and cap remaining;         0.1 nm (SiN)                  small: model must fix
                residual ZAZ ≥ 0.3 nm                                        SiN n; surface residues
                                                                             bias thin-film fits
In-situ         ZAZ thickness during the       0.05 nm/s         real time   window fogging; one pad;
ellipsometry    etch (development)                                           wafer-temperature n shift
OCD             TE and SiGe recess on edge     0.5 nm            ≈ 2 s       correlated parameters;
(scatterometry) gratings; cap corner                                         needs TEM anchors
AFM             SiN roughness after clear      0.05 nm rms       ≈ 5 min     tip wear; small area
                (σ_g proxy)
CD-SEM          plate edge placement           3 nm              ≈ 5 s       charging on SiN
TEM / STEM /    TE recess, ZAZ undercut,       0.2 nm            hours       sampling; FIB damage
EELS            Cl and O at the edge                                         at the cut face
GIXRD           ZrO₂ phase fraction            ± 5% (monoclinic) ≈ 20 min    blanket monitor only
                (monitor wafers)
```

---

## F.2 Surface and Contamination Analysis

```
Method          Detects                 Limit                 Area / depth       Pitfalls
──────────────────────────────────────────────────────────────────────────────────────────────
TXRF            Zr, Cl, Ti, Y, Al...    ≈ 10¹⁰ /cm² (Zr)      ≈ 1 cm² / few nm   averages; cannot see
                                                                                 the island tail
VPD-ICPMS       metals collected by     ≈ 10⁸ /cm²            whole wafer        misses crystalline
                HF vapor + droplet                                               ZrO₂ (blind spot)
Aggressive      crystalline ZrO₂        ≈ 10⁹ /cm²            whole wafer        etches the substrate;
droplet (hot                                                                     slow
HF/H₂SO₄)
XPS             Zr 3d, B 1s, Cl 2p,     ≈ 0.1 at%             50 µm / ≈ 5 nm     near limit at the Zr
                F 1s, chemical state    (≈ 10¹³ /cm²)                            spec; needs pads
LEIS            outermost monolayer     ≈ 10¹² /cm²           1 mm / 1 layer     ion-beam damage;
                composition                                                      calibration
ToF-SIMS        Cl, B, F, Zr maps and   10¹⁰–10¹¹ /cm²        100 µm / 1 nm      matrix effects;
                profiles                                                         semi-quantitative
```

---

## F.3 Defect Inspection

```
Method          Finds                           Sensitivity        Throughput      Pitfalls
──────────────────────────────────────────────────────────────────────────────────────────────
E-beam (BSE)    ZrO₂ islands on SiN by Z        ≥ 15 nm wide,      ≈ 20 mm²/h      sampling statistics;
                contrast                        ≥ 0.5 nm thick                     charging on SiN
E-beam VC       open periphery contacts         one open contact   ≈ 1 mm²/h at    after contact etch;
(after contact                                                     contact pitch   not specific to cause
etch)
Optical         particles, flakes, cap          ≥ 30 nm particles  whole wafer,    cannot see sub-nm
brightfield /   pinholes                                           minutes         islands
darkfield
Defect review   composition of particles        —                  per defect      sampling
(SEM-EDX)       (Zr, B, Y, Al)
```

---

## F.4 Electrical Monitors

```
Structure            Measures                        Sensitivity                When
──────────────────────────────────────────────────────────────────────────────────────────
Contact chains       periphery contact opens,         ≈ 2 × 10⁻⁸ per contact     metal 1
(10⁶ contacts each)  resistance tail                  per wafer (50 chains)
Plate-edge comb      leakage between facing plate     ≤ 1 pA/mm at 1.1 V         metal 1
                     edges across cleared SiN
Overlap ladder       damage reach and edge leakage    5% leakage change at       metal 1
                     vs overlap (0–0.8 µm)            0.1 µm rung (n ≥ 5)
Capacitor arrays     leakage, EOT, TDDB               ± 3% leakage               metal 1 / reliability
Plate resistance     W craters (cap pinholes)         ± 2%                       metal 1
Bitmap / retention   cells failing at the array       tail fraction 10⁻⁶         final test
                     boundary
```

---

## F.5 In-Situ Sensors

```
Sensor                  Measures                         Use
────────────────────────────────────────────────────────────────────────────────
OES (200–900 nm,        Zr, Al, Si, BO, N₂, Cl, Ar         endpoint, Al marker,
≤ 0.5 nm resolution)                                       per-cycle ALE signals,
                                                           wall state
Bias V_pp / V_dc probe  ion energy                         control (not power)
Wafer thermocouple /    wafer–chuck offset                 qualification
phosphor wafer
Backside He flow and    clamping, leaks                    FDC
pressure
Ion energy analyser     IED in step B                      ALE qualification
wafer
RGA / OES Cl in step B  purge residual                     ALE FDC
```

---

## F.6 Measurement Ladder Summary

```
Rung                     Sees                         Per-contact sensitivity   Delay
─────────────────────────────────────────────────────────────────────────────────────
TXRF                     average Zr                   gross failures only       minutes
E-beam inspection        islands ≥ 15 nm              ≈ 10⁻⁶ (excursions)       hours
E-beam VC on contacts    open contacts                ≈ 10⁻⁷                    1–2 weeks
Contact chains           opens per 10⁶ contacts       ≈ 10⁻⁸ per wafer          3–4 weeks
Product yield / bitmaps  die-level opens              ≈ 10⁻¹⁰                   2–3 months
```

---

**Appendix F Version:** 1.0  
**Last Updated:** 2026-10-05
