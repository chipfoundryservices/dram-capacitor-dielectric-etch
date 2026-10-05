# Appendix A: Material Properties

Properties of the dielectric films, the materials around them, the chamber materials, and the process gases used in this book. Values are representative of thin films deposited as described in Chapter 2; bulk values are given where the film value is not well defined. All values are illustrative.

---

## A.1 Capacitor Dielectrics

```
Property               ZrO₂           ZrO₂           ZrO₂           Al₂O₃          HfO₂
                       amorphous      tetragonal     monoclinic     (ALD)          monoclinic
─────────────────────────────────────────────────────────────────────────────────────────────
Reference thickness    as deposited   2.6 nm × 2     ≈ 30% of       0.3 nm         (variants)
                                      (array)        periphery      insertion
                                                     grains
Density (g/cm³)        5.5–5.7        6.1            5.68           3.0–3.3        9.7
Molar mass (g/mol)     123.2          123.2          123.2          102.0          210.5
Formula units (cm⁻³)   2.8 × 10²²     3.0 × 10²²     2.8 × 10²²     1.9 × 10²²     2.8 × 10²²
Metal areal density    2.8 × 10¹⁵     3.0 × 10¹⁵     2.8 × 10¹⁵     3.8 × 10¹⁵ Al  2.8 × 10¹⁵
per nm (cm⁻²)
Refractive index       ≈ 2.05         ≈ 2.15–2.2     ≈ 2.1          ≈ 1.65         ≈ 2.0–2.1
(633 nm)
Dielectric constant    20–25          35–45          ≈ 20           ≈ 9            18–20
Band gap (eV)          ≈ 5.6          ≈ 5.8          ≈ 5.8          ≈ 8.8          ≈ 5.7
Crystallization        —              ≈ 350–400 °C on TiN            stays amorphous ≈ 450 °C
Grain size             —              10–30 nm (TiN) 15–40 nm (SiN)  —              10–30 nm
```

```
Reference ZAZ (Chapter 2):
  Array (on TiN)        ZrO₂ 2.6 / Al₂O₃ 0.3 / ZrO₂ 2.6 nm = 5.5 nm; tetragonal;
                        EOT 0.50 nm; k_eff ≈ 43
  Periphery (on SiN)    5.4 nm (ZrO₂ 2.55 / 0.3 / 2.55); ≈ 70% tetragonal,
                        ≈ 30% monoclinic; on ≈ 0.5 nm SiOₓNᵧ
  Zr in the periphery   ≈ 1.5 × 10¹⁶ atoms/cm²; one monolayer ≈ 8.3 × 10¹⁴ /cm²
```

---

## A.2 Higher-k and Variant Dielectrics (Chapter 14)

```
Film               k           Band gap (eV)   Cation halide volatility        Electrode
─────────────────────────────────────────────────────────────────────────────────────────
HZO (Zr-rich)      45–55       ≈ 5.7           HfCl₄, ZrCl₄ (≈ 190 °C @ 1 Torr) TiN
Nb₂O₅              ≈ 40–50     ≈ 3.4           NbCl₅ bp 254 °C; NbF₅ bp 234 °C  TiN
TiO₂ (rutile)      80–100      3.0–3.5         TiCl₄ bp 136 °C; TiF₄ subl. 284 Ru, RuO₂
SrTiO₃             100–200     3.2             SrCl₂ bp 1250 °C; SrF₂ 2460 °C   Ru, SrRuO₃
La₂O₃ (dopant)     ≈ 25        ≈ 5.5           LaCl₃ involatile                 —
Y₂O₃ (dopant)      ≈ 15        ≈ 5.6           YCl₃ mp 721 °C, involatile        —
```

---

## A.3 Materials Around the Dielectric

```
Property                Periphery SiN    PE-TEOS cap      TE TiN           Si₀.₇Ge₀.₃:B     W strap
                        (PECVD)                           (ALD, 400 °C)    (LPCVD)          (PVD)
───────────────────────────────────────────────────────────────────────────────────────────────────
Thickness (reference)   120 nm           60 nm            5 nm             150 nm           40 nm
Density (g/cm³)         2.6–2.8          2.15–2.2         4.8–5.1          ≈ 3.4            19.0–19.3
Refractive index        2.02             1.46             (metallic)       (absorbing)      (metallic)
(633 nm)
H content               ≈ 15 at%         ≈ 3–5 at%        —                —                —
Cl content              —                —                ≈ 0.5 at%        —                —
Resistivity             insulator        insulator        ≈ 250 µΩ·cm      ≈ 2 mΩ·cm        ≈ 15 µΩ·cm
D1 rate (nm/min)        3.0 vertical     2.0 vertical     1.2 lateral      1.0 lateral      0.5 lateral
D2 EPC (nm/cycle)       0.012            0.010            ≈ 0.005 lateral  ≈ 0              ≈ 0
```

---

## A.4 Chamber Materials (Chapter 5)

```
Material              Use                   Thermal cond.   Relative erosion in      Contaminant
                                            (W/m·K)         BCl₃/Cl₂ (wall sheath)
──────────────────────────────────────────────────────────────────────────────────────────────
Anodized Al           (not used on plasma   —               1.0 (reference)          Al
                      surfaces)
Sintered Al₂O₃        window substrate      ≈ 30            0.6                      Al
Quartz                (not used)            1.4             0.8                      Si
SiC                   (alternative ring)    ≈ 120           0.5                      Si, C
AlN (doped)           J-R chuck puck        ≈ 100           0.3                      Al
Y₂O₃ (plasma spray)   liners, walls         ≈ 10 (bulk)     0.05                     Y (low)
Y₂O₃ (bulk)           edge ring             ≈ 10            0.05                     Y
YOF / dense Y₂O₃      window coating        —               0.03                     Y (lowest)
(aerosol deposition)
Perfluoroelastomer    seals                 —               —                        ≤ 200 °C
                                                                                     (used ≤ 150 °C)
```

---

## A.5 Silicon Wafer (Heat-Up, Chapter 5)

```
Thickness                       775 µm
Density                         2.33 g/cm³
Specific heat                   0.70 J/g·K (25 °C) → 0.80 J/g·K (250 °C)
Heat capacity per area          ≈ 0.13 J/cm²·K
Thermal expansion               2.6 × 10⁻⁶ /K → 88 µm at the edge of a 300 mm
                                wafer from 25 to 250 °C
```

---

## A.6 Process Gases and Reagents

```
Gas / reagent    Formula        Boiling / sublimation   Vapor pressure          Hazards
                                (°C, 760 Torr)          at 20 °C
─────────────────────────────────────────────────────────────────────────────────────────────
Boron            BCl₃           12.5                    ≈ 1.3 bar               toxic; hydrolyses
trichloride                                                                     to HCl + B(OH)₃
Chlorine         Cl₂            −34                     ≈ 6.8 bar               toxic, oxidizer
Argon            Ar             −186                    (gas)                   asphyxiant
Water vapor      H₂O            100                     17.5 Torr               —
(PET)
Hydrogen         HF             19.5                    ≈ 1 bar                 highly toxic,
fluoride                                                                        corrosive
DMAC             Al(CH₃)₂Cl     ≈ 126                   ≈ 5 Torr (est.)         pyrophoric;
                                                                                water-reactive
TMA              Al(CH₃)₃       125                     ≈ 11 Torr               pyrophoric
Ozone (ALD)      O₃             −112                    (generated)             toxic, oxidizer
```

---

**Appendix A Version:** 1.0  
**Last Updated:** 2026-10-05
