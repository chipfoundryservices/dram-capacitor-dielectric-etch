# Appendix F: Metrology Reference

Methods used for the dielectric etch modules: what each measures, its sensitivity and precision, its sampling cost, and its main pitfalls. Values are illustrative.

---

## F.1 Thickness and Dimensional Metrology

```
Method          Measures                        Precision        Time/site   Pitfalls
─────────────────────────────────────────────────────────────────────────────────────────────────
Spectroscopic   ZAZ stack thickness; ZAZ loss;  0.01 nm (1σ)     ≈ 1 s       interface layer model
ellipsometry    SiN thickness (periphery pad)   accuracy ± 0.1 nm             (TiOₓNᵧ 1.0–1.5 nm);
                                                 after TEM cal.               needs a flat pad ≥ 1 mm
XRR             thickness, density, roughness   0.03 nm          ≈ 5 min     large pad (≥ 5 mm); slow
XRF (Zr Kα)     Zr atoms/cm² → ZAZ thickness   0.3% = 0.016 nm  ≈ 10 s      calibration; Al layer not
                W thickness (W Lα)              0.2 nm                        counted in Zr
Reflectometry   ZAZ edge position, r = 140–150  ± 0.05 mm        ≈ 30 s/scan edge shape; backside optics
                backside film (line scan)
OCD             plate-edge profile, foot notch, 0.3 nm (notch)   ≈ 2 s       gratings in the scribe only
                TiN recess (gratings)
CD-SEM          plate CD, placement             3 nm             ≈ 5 s       charging on SiN
TEM / STEM      ZAZ thickness; shell; plate     ± 0.1 nm         hours       sampling; FIB damage at
                edge; pillar heights                                           TiN/SiGe edges
EELS / EDX      TiOₓ shell; WOₓ; F, Cl, B       ≈ 0.5 at%        hours       beam damage
```

Calibration chain for the 5.5 nm film: TEM (± 0.1 nm, monthly) → XRR (± 0.05 nm, quarterly) → XRF counts and ellipsometry model (daily). One cycle of thermal ALE is 0.073 nm; the lot-mean thickness must be known to ± 0.03 nm (3σ).

---

## F.2 Zirconium and Contamination

```
Method          Measures                       Floor (Zr cm⁻²)     Area           Notes
─────────────────────────────────────────────────────────────────────────────────────────────
TXRF            Zr, Ti, W, Ge, Fe, Ni, Cu, Y   10⁹–10¹¹            ≈ 1 cm² spot   averages; daily trend;
                                                                                    blind to a sector
VPD-ICPMS       metals, front and back          10⁸–10⁹             whole surface  destructive; the proof
                                                                    or a sector     for 10¹⁰ cm⁻²
XPS             Zr, Cl, B, F, C, O; states      ≈ 10¹³ (0.1 at%)    ≈ 50 µm        top 5–8 nm
TOF-SIMS        Zr maps; F, Cl, B depth         ppm                 ≈ 100 µm       islands; ZrF₄ patches
                profiles
E-beam          islands ≳ 20 nm with contrast   —                   die-scale      grain clusters, veils
inspection
Contact chains  open contacts through the       functional          full module    the only tail test
                contact module
```

---

## F.3 Edge, Bevel, and Particles

```
Method                      Detects                                 Resolution        Frequency
─────────────────────────────────────────────────────────────────────────────────────────────
Bevel optical / dark-field  flakes, film edges, particles            ≈ 0.5 µm          every wafer
Reflectometry line scan     ZAZ boundary position; loss inside       ± 0.05 mm         weekly; PM
Macro imaging (sectors)     BₓClᵧ haze, Si roughness, nozzle marks   macro             each lot
Surface scanner             particles > 30 nm on front side          30 nm             per wafer / lot
VPD sectors (8 × 3 zones)   Zr by azimuth and zone                   floor 8 × 10⁹      weekly; PM
                                                                     atoms per sector
```

---

## F.4 Electrical Structures

```
Structure                       Reads                                        Role
─────────────────────────────────────────────────────────────────────────────────────────────
Reference capacitor array       C_s; leakage at 0.55 and 1.0 V (median,      baseline
(10⁶ cells)                     tail); breakdown on sacrificial structures
Trim-dose array                 leakage and C_s vs cycles (0–4)              trim chemistry
Edge-proximity arrays           leakage vs overlap (0.3, 0.6, 1.0, 1.5 µm)   edge damage reach
Antenna arrays (1×, 10×, 100×)  leakage vs antenna ratio                     charging (Ch. 7, 12)
Polarity pairs (n⁺/p, p⁺/n)     negative- vs positive-plate stress            charging vs material
Large-area TDDB capacitors      Weibull β, η vs area and field                defect density
Plate sheet-resistance patterns R_s; W loss                                   strip/clear budget
Contact chains (2 × 10⁶ per site) opens in the periphery contact module     residue tail
```

---

## F.5 In-Situ Sensors

```
Sensor                  Signal                                   Used for
─────────────────────────────────────────────────────────────────────────────────────────────
OES: Ti I 399.9, 453.3, 498.2; N₂ 337.1; Cl I 837.6    TiN clearing (P2); stop endpoint
OES: Al I 394.4, 396.2; Zr I 360.1, 339.2 (weak)      Al marker (edge drift check; P4 clear)
OES: CO 483.5                                          resist and BARC clearing (P1, P3)
OES: SiCl 287, N₂ 337.1                                SiN onset
Ar I 750.4, 811.5                                      actinometry
In-situ ellipsometer    ZAZ on a pad: thickness vs time      ZAZ loss in P2; EPC; SiN loss
Witness crystal (QCM)   Δf per cycle: 3.2 Hz at 6 MHz        EPC in thermal ALE
Cycle counter, pressure traces                               dose and purge verification
RF: V_pp, reflected power, harmonics                         plasma and wafer state
Chuck / liner / foreline temperatures and pressure           rate drift; condensation
```

---

## F.6 Uncertainty Rules of Thumb

```
Decision                       Quantity               Needed             Method
────────────────────────────────────────────────────────────────────────────────────────────
Trim cycle count               lot-mean thickness      σ ≤ 0.010 nm       ellipsometry + XRF check
Stop quality                   ZAZ loss                ± 0.01 nm          in-situ ellipsometry
Zirconium at the furnace       backside Zr             1 × 10¹⁰ with 10×  VPD-ICPMS
                                                       margin
Periphery opens                P_open                  3.3 × 10⁻¹⁰ (0.01 per die)   chains: 9 × 10⁹ contacts
EPC control                    removal per cycle       ± 3%              witness crystal
Overlap                        placement, damage       ± 100 nm, ± 50 nm CD-SEM; TEM
Edge boundary                  r = 147.0 mm            ± 0.05 mm          line scan
```

---

## F.7 Sampling Summary

```
Module E:  VPD sectors weekly and each PM; TXRF daily; boundary scan weekly; bevel inspection every wafer
Module P:  in-situ ZAZ loss and Al marker every wafer; TXRF periphery pad weekly; OCD, XRF, R_s every lot;
           TEM shell monthly; contact chains each lot (trend over 45 wafers)
Module T:  ALD thickness every lot; EPC (pad) one wafer per lot; witness crystal each cycle;
           trim-dose array monthly
Module C:  first-wafer thickness and particles after every clean; Zr canary weekly
```

---

**Appendix F Version:** 1.0
