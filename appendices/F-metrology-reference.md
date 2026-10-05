# Appendix F: Metrology Reference

Measurement techniques used for the three dielectric etches: what each measures, its sensitivity and spot, its throughput, and its limits. Values are typical; they depend on the instrument and the sample.

---

## F.1 Technique Summary

```
Technique             Measures                    Sensitivity          Spot / area        Throughput      Limits
──────────────────────────────────────────────────────────────────────────────────────────────────────────────────────
Spectroscopic         film thickness, optical     ± 0.02 nm (ZrO₂ on   30–50 µm           ≈ 1 min/wafer   needs pads; ZrO₂/SiN
ellipsometry (SE)     constants                   SiN)                                    (9–49 sites)    correlation
XRR                   thickness, density,         ± 0.05 nm; ρ ± 2%    ≈ mm               ≈ 10 min/site   large pads or blanket
                      roughness
TXRF                  surface metals (Zr, Ti,     ≈ 10¹⁰ atoms/cm²     ≈ 10 mm            ≈ 5 min/site    average only; needs
                      Al)                                                                                 open areas
VPD-ICP-MS            surface metals, whole       ≈ 10⁸ atoms/cm²      whole surface or   ≈ 1 h/wafer     destructive for the
(whole / bevel)       surface or bevel scan                            bevel ring                         surface oxide
XPS                   composition, bonding (Zr,   ≈ 0.3 at%            0.1–1 mm           ≈ 10 min/site   average; top ≈ 5 nm
                      B, Cl, F, C)
TOF-SIMS              trace species, depth        ≈ 10¹² atoms/cm²     ≈ 100 µm           ≈ 30 min        semi-quantitative
                      profiles (B, Cl, F)
Atom-probe            3D composition at grain     single atoms         ≈ 50 nm tip        days            tiny volume
tomography            boundaries and edges
HAADF-STEM / EELS     thickness, profile,         ≈ 0.1 nm; EELS       ≈ 100 nm lamella   days            few sites
                      notch, grooves, Cl/B maps   ≈ 1 at%
TEM tomography        3D groove geometry          ≈ 0.05 nm            ≈ 50 nm            days            very few sites
QCM (in situ)         mass per half-step (ALE)    ≈ 0.01 ng/cm²        crystal            real time       flat surface only
Optical edge          bevel boundary, haze,       ± 20 µm; ≥ 1 µm      full edge          ≈ 1 min/wafer   no chemistry
inspection            flakes                      defects
SEM-EDX (cleaved      staircase profile at the    ≈ 1 nm; EDX ≈ 1%     ≈ 5 µm             hours           destructive
edge)                 bevel boundary
Voltage-contrast      open contacts after         single contacts      10⁸–10⁹ contacts   hours/wafer     after contact etch
e-beam                contact etch/fill                                per wafer
Contact chains        opens, R distribution       single opens         10⁵ per chain      per lot         weeks of delay
C–V / I–V arrays      EOT, leakage, TDDB          ± 0.005 nm EOT       10⁻³ cm² arrays    per lot         weeks of delay
```

---

## F.2 Ellipsometry Model for the Periphery Pad

```
Stack (top → bottom):  ZrO₂ (Tauc–Lorentz) / Al₂O₃ (Cauchy) / ZrO₂ /
                        SiN (Tauc–Lorentz) / SiO₂ / Si
Fitted:                 total ZrO₂ thickness (Al₂O₃ fixed at 0.3 nm);
                        SiN thickness
Correlation:            ZrO₂ and SiN thicknesses correlate (similar n);
                        fix the SiN from a pre-measurement on the same
                        pad, then fit ZrO₂ alone
Calibration:            XRR on blanket monitors monthly
```

---

## F.3 Bevel VPD Procedure

```
1. Expose the wafer to HF vapour (dissolves the top oxide/nitride surface
   and the metals on it)
2. Scan a droplet (≈ 100 µL, HF/H₂O₂) around the bevel ring, then the
   apex, then the back ring (separate droplets for each zone)
3. ICP-MS of each droplet; report atoms/cm² for the scanned area
4. Whole-backside VPD on a separate wafer when the backside specification
   is in question
Detection limit ≈ 10⁸–10⁹ atoms/cm² for Zr, depending on the area scanned
```

---

## F.4 Contact-Chain Design for Residue Detection

```
Kelvin chains in the scribe line:
  Contacts per chain          10⁵ (open detected as a resistance jump)
  Contact bottom              40 × 40 nm, on periphery-type landing pads
  Placement                   ≥ 0.5 µm from any plate edge; chains in the
                              outermost dies (slowest band) and at the centre
Sensitivity per wafer         8 × 10⁶ contacts → detects P(site) ≥ ≈ 10⁻⁸
Use                           excursion detection; cycle ladders (App. C.3)
```

---

## F.5 Electrical Structures for the Dielectric

```
Structure                         Area                      Measures
──────────────────────────────────────────────────────────────────────────────
Centre capacitor array            ≈ 10⁻³ cm² (≈ 10⁶ cells)  EOT, J(V), TDDB
Edge-intensive arrays             plate edges at 0.2, 0.5,   edge leakage ratio
                                  1.5 µm from active cells
Antenna arrays                    small plate islands with   charging damage
                                  long perimeters
Bevel-proximity arrays            dies at r = 145–147 mm     module-1 edge effects
Trim / no-trim split arrays       pilot                      module 3
Product retention test            whole dies                 retention-time
                                                             distribution
```

---

## F.6 In-Situ Signals

```
Signal                          Module   Use
───────────────────────────────────────────────────────────────────────────────
Ti I 399.9 nm                   2        TiN-clear transition (t_TiN)
Al I 396.2 nm                   2        Al marker (t_Al → main-step adaptation)
Zr I 360.1 nm, per ALE cycle    2        clearing curve (n₅₀, n₉₈); WAC end
N₂ 337.1 nm, per ALE cycle      2        SiN exposure; virtual SiN loss
Cl I 837.6 / Ar I 750.4         2        wall state
V_dc, V_pp, reflected power     1, 2     ion energy; match health; ignition
Purge-end pressure per cycle    2        residual BCl₃; valve health
QCM mass per half-step          3        EPC, saturation
DMAC pressure rise per dose     3        supply
```

---

**Appendix F Version:** 1.0
