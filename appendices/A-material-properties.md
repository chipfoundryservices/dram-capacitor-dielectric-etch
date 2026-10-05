# Appendix A: Material Properties

Properties of the dielectrics, conductors, landing films, gases, and precursors used in this book. Values are representative of thin films deposited as described in Chapter 2; bulk or handbook values are given where the film value is not well defined. All values are illustrative.

---

## A.1 The Capacitor Dielectric and Candidates

```
Property                    ZrO₂ (tetragonal)  ZrO₂ (amorphous)  Al₂O₃ (ALD)    ZAZ stack        HfO₂
────────────────────────────────────────────────────────────────────────────────────────────────────────
Thickness (reference)       2 × 2.6 nm          2 × 2.6 nm         0.3 nm          5.5 nm           —
Dielectric constant         ≈ 40–47             ≈ 20–25            ≈ 9             k_eff ≈ 43       ≈ 20–25
EOT (reference)             —                   —                  —               0.50 nm          —
Band gap (eV)               ≈ 5.8               ≈ 5.8              ≈ 8.8           —                ≈ 5.8
Density (g/cm³)             5.7–6.1             5.2–5.4            3.0–3.2         —                9.7
Molar mass (g/mol)          123.2               123.2              102.0           —                210.5
Monolayer areal density     ≈ 8.3 × 10¹⁴ Zr cm⁻² (0.3 nm of ZrO₂)
Zr per cm² in 5.2 nm        1.44 × 10¹⁶
Al per cm² in 0.3 nm        1.1 × 10¹⁵
Crystallization             ≈ 350–400 °C (on TiN); Avrami n = 2, E_a = 3.0 eV (Ch. 2)    Al₂O₃ > 800 °C
Breakdown field (MV/cm)     ≈ 4.5 (ZAZ, crystallized)
Leakage at 1.0 V            ≈ 1 fA per cell (8 × 10⁻⁷ A/cm²); J = J₁ exp[(V − 1.0)/0.12 V]
Leakage vs thickness        one decade per 0.45 nm (illustrative)
Stress (crystallized)       ≈ +1.0 GPa (ZAZ); ≈ +0.1–0.3 GPa as deposited
```

```
Candidate dielectrics (Chapter 14):
Material               k (typical)    Band gap (eV)   Density (g/cm³)   Molar mass   Notes
─────────────────────────────────────────────────────────────────────────────────────────────────
TiO₂ (rutile)           80–100         ≈ 3.0           4.23              79.9        needs Ru or RuO₂ template
Nb₂O₅                   40–60          ≈ 3.4           4.6               265.8       volatile Cl and F halides
SrTiO₃                  > 100          ≈ 3.2           5.12              183.5       a = 0.3905 nm; Sr non-volatile
HfO₂/ZrO₂ (HZO)         30–50          ≈ 5.5           7.5–9.0           —           FE/AFE phases; phase-sensitive
```

---

## A.2 Conductors, Shells, and Landing Films

```
Property                TiN (ALD top)    TiOₓ shell      W (PVD strap)     WOₓ top        SiGe:B (plate)   PECVD SiN
─────────────────────────────────────────────────────────────────────────────────────────────────────────────────────
Thickness (reference)   5 nm             1.8 nm (strip)  40 nm             2.5 nm (strip) 150 nm           120 nm
Density (g/cm³)         4.8–5.1          ≈ 4.2           19.0–19.3         ≈ 7.2          ≈ 3.4            ≈ 2.8
Molar mass (g/mol)      61.9             79.9 (TiO₂)     183.8             231.8 (WO₃)    —                —
Resistivity             ≈ 250 µΩ·cm     insulating      ≈ 15 µΩ·cm        insulating     ≈ 2 mΩ·cm        —
Stress (MPa)            ≈ +1000          —               ≈ +1000           —              −100 to +100     ≈ +300
Pilling–Bedworth ratio  TiN → TiO₂ ≈ 1.7 —               W → WO₃ ≈ 3.4     —              —                —
Plate R_s (Ω/□)         500 (5 nm)       —               3.75 (40 nm)      —              133 (150 nm)     —
                                          Parallel stack: 3.62 Ω/□; limit 4.0; W ≥ 36.1 nm
```

---

## A.3 Halides: Volatility

```
Sublimation / boiling point (°C, handbook, rounded)
Metal    Chloride          Fluoride           Class
──────────────────────────────────────────────────────────────────
Zr       ZrCl₄   331       ZrF₄    ≈ 906      V (chloride, marginal)
Hf       HfCl₄   317       HfF₄    ≈ 970      V (chloride, marginal)
Al       AlCl₃   180       AlF₃    ≈ 1276     V (chloride)
Ti       TiCl₄   136       TiF₄     284       V (either)
Nb       NbCl₅   248       NbF₅     234       V (either)
Ta       TaCl₅   239       TaF₅     229       V (either)
Si       SiCl₄    57       SiF₄    −86        V (either)
B        BCl₃    12.5      BF₃    −100        V (either)
Sr       SrCl₂ ≈ 1250      SrF₂    2460       N
Ba       BaCl₂   1560      BaF₂    2260       N
La       LaCl₃   1812      LaF₃   ≈ 2330      N
Y        YCl₃    1507      YF₃    ≈ 2230      N
```

Class V: a halide volatile below about 350 °C. Class N: none. See Chapter 14.

---

## A.4 Etch Rates and Selectivities (reference)

```
Rates in nm/min unless noted        E edge        R0 integrated   P2 stop       P4 hot clear   T thermal ALE    Wet
                                    BCl₃/Cl₂      BCl₃/Cl₂        Cl₂/Ar        BCl₃/Cl₂/Ar    HF/DMAC          0.5% HF
                                    250 eV, ×0.25 150 eV, 60 °C   40 eV, 60 °C  80 eV, 250 °C  280 °C, nm/cycle 25 °C
──────────────────────────────────────────────────────────────────────────────────────────────────────────────────────
ZrO₂ amorphous                       3.7           9              0             —              0.07             2
ZrO₂ tetragonal                      —             6              0             12             0.045            0.2
Al₂O₃ (0.3 nm layer)                 2.1           5              0             9              0.05             3
TiN (vertical)                       —             50             16.5          120            ≈ 0              < 0.1
TiOₓ shell (1.8 nm)                  —             —              0             2.0 (chem.)    ≈ 0              < 0.1
SiN (PECVD periphery)                3.3           8              0.8           4              ≈ 0              2
SiO₂ (PE-TEOS)                       2.1           5              0.5           2              ≈ 0.01           3
W (40 nm strap)                      —             —              under resist  2.4            ≈ 0              < 0.1
Si (backside)                        10.7          —              —             —              —                0
Resist (KrF)                         —             50             13            stripped       —                —
```

---

## A.5 Gases and Precursors

```
Substance     Formula       Boiling point (°C)   Vapor pressure (25 °C)   Delivery / hazard note
──────────────────────────────────────────────────────────────────────────────────────────────────────
Boron trichloride  BCl₃       12.5                 ≈ 1.3 atm (20 °C)       heated cylinder; lines warmer;
                                                                            hydrolyses to B(OH)₃ + HCl
Chlorine           Cl₂        −34                  gas                     ceiling 1 ppm (OSHA)
Hydrogen fluoride  HF         19.5                 ≈ 1 atm (20 °C)         PEL 3 ppm; IDLH 30 ppm; heated
                                                                            cylinder; sensors at 1 ppm
Dimethylacetamide  DMAC       165                  ≈ 1.3 Torr              vapor draw / liquid injection;
                                                                            lines ≥ 120 °C
Trimethylaluminium TMA        125                  ≈ 12 Torr               pyrophoric; full hazard controls
Ozone              O₃         −112                 gas                     oxidant for ALD; destructor
Nitrogen trifluoride NF₃      −129                 gas                     clean gas for Si, W; never on Zr
Zr precursor       Cp-Zr amide  —                  low                     bulky ligands; N_s ≈ 1.5 × 10¹⁴ cm⁻²
```

---

## A.6 Constants and Conversions

```
k_B = 1.381 × 10⁻²³ J/K = 8.617 × 10⁻⁵ eV/K          1 amu = 1.661 × 10⁻²⁷ kg
ε₀ = 8.854 × 10⁻¹² F/m                                  Avogadro 6.022 × 10²³ mol⁻¹
1 Torr = 133.3 Pa;  1 sccm = 0.0127 Torr·L/s            1 Langmuir = 10⁻⁶ Torr·s
300 mm wafer area 706.9 cm²;  die 860 per wafer;  cells per die 1.72 × 10¹⁰
Dielectric area per cell 1.24 × 10⁻⁹ cm²;  per die 21.3 cm²;  per wafer 1.83 × 10⁴ cm²
```

---

**Appendix A Version:** 1.0
