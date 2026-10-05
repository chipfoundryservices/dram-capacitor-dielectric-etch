# Appendix B: Chemistry & Thermochemistry Data

Thermochemical data, volatilities, reaction enthalpies, rates, and emission lines used in this book. Values are representative; check primary tables before quantitative use. All rate values are illustrative for the reference conditions.

---

## B.1 Standard Enthalpies of Formation (298 K, kJ/mol)

```
Oxides                      Halides                       Other
─────────────────────────────────────────────────────────────────────────────
ZrO₂(s)      −1100.6        ZrCl₄(s)       −980.5         BCl₃(g)    −403.8
HfO₂(s)      −1144.7        HfCl₄(s)       −990.4         B₂O₃(s)   −1273.5
Al₂O₃(s)     −1675.7        AlCl₃(s)       −704.2         CO(g)      −110.5
TiO₂(s)       −944.0        TiCl₄(g)       −763.2         CO₂(g)     −393.5
SrO(s)        −592.0        TiCl₄(l)       −804.2         HF(g)      −273.3
SiO₂(s)       −910.7        SrCl₂(s)       −828.9         HCl(g)      −92.3
                            ZrF₄(s)       −1911           H₂O(g)     −241.8
                            AlF₃(s)       −1510
```

---

## B.2 Reaction Enthalpies (kJ per mol of oxide)

```
Reaction                                                ΔH        Chapter
─────────────────────────────────────────────────────────────────────────
ZrO₂ + 2 Cl₂ → ZrCl₄ + O₂                               +120       3
ZrO₂ + 4/3 BCl₃ → ZrCl₄ + 2/3 B₂O₃                      −191       3
ZrO₂ + 2 Cl₂ + 2 C → ZrCl₄ + 2 CO                       −101       3
ZrO₂ + 2 Cl₂ + 2 CO → ZrCl₄ + 2 CO₂                     −446       3
HfO₂ + 2 Cl₂ → HfCl₄ + O₂                               +154       3
HfO₂ + 4/3 BCl₃ → HfCl₄ + 2/3 B₂O₃                      −156       3
Al₂O₃ + 3 Cl₂ → 2 AlCl₃ + 3/2 O₂                        +267       3
Al₂O₃ + 2 BCl₃ → 2 AlCl₃ + B₂O₃                         −198       3
TiO₂ + 2 Cl₂ → TiCl₄(g) + O₂                            +181       3, 14
TiO₂ + 4/3 BCl₃ → TiCl₄(g) + 2/3 B₂O₃                   −130       3, 14
SrO + Cl₂ → SrCl₂ + ½ O₂                                −237       3, 14
ZrO₂ + 4 HF → ZrF₄ + 2 H₂O(g)                           ≈ −201     4 (fluorination)
```

---

## B.3 Volatility

```
Species          T at ≈ 1 Torr (°C)   Sublimation/boiling (°C, 1 atm)   ΔH_sub/vap (kJ/mol)
─────────────────────────────────────────────────────────────────────────────────────────
BCl₃             −91                   12.5 (bp)                         ≈ 24
TiCl₄            −14                   136 (bp)                          ≈ 39
(BOCl)₃          ≈ 20                  —                                 —
AlCl₃ (Al₂Cl₆)   ≈ 100                 180 (subl.)                       ≈ 115
ZrCl₄            ≈ 190                 331 (subl.)                       ≈ 110
HfCl₄            ≈ 190                 317 (subl.)                       ≈ 100
ZrBr₄            ≈ 210                 357 (subl.)                       —
TiF₄             ≈ 200                 284 (subl.)                       —
ZrF₄, HfF₄       ≈ 600                 ≈ 900 (subl.)                     —
AlF₃             ≈ 1000                1290 (subl.)                      —
LaCl₃, YCl₃      > 700                 > 1400 (bp)                       —
SrCl₂            > 1000                1250 (bp)                         —

ZrCl₄ vapour pressure (Clausius–Clapeyron from 1 Torr at 190 °C, 110 kJ/mol):
  60 °C   1.4 × 10⁻⁵ Torr      120 °C   6 × 10⁻³ Torr      250 °C   ≈ 25 Torr
```

---

## B.4 Bond Dissociation Energies (Diatomic, kJ/mol)

```
C–O 1077    B–O 806    Hf–O 802    Si–O 798    La–O 798    Zr–O 766
Y–O 715     Ti–O 672   Al–O 512    Sr–O 426
```

---

## B.5 Rates and Etch per Cycle (Reference Conditions)

```
Main step: BCl₃ 80 / Cl₂ 20 / Ar 50 sccm, 5 mTorr, 800 W, E ≈ 150 eV, 60 °C
  Model: R_net = A(√E − √E_th) − D;  A = 1.33 nm/min/√eV, E_th = 30 eV,
         D = 3 nm/min (t-ZrO₂), E₀ ≈ 60 eV

  Film                      nm/min        Film                    nm/min
  ─────────────────────────────────────────────────────────────────────
  ZrO₂ tetragonal            6.0          PECVD SiN                8
  ZrO₂ amorphous             9            PE-TEOS SiO₂             5
  Al₂O₃                      5            KrF resist               50
  HfO₂                       5            TE TiN                   50
  TiO₂ (rutile)              ≈ 25         SiGe:B                   ≈ 60

Temperature dependence (t-ZrO₂):
  60 °C: A 1.33, E_th 30, D 3.0, E₀ 60, R(150 eV) 6
  150 °C: A 1.74, E_th 20, D 1.5, E₀ 28, R(150 eV) 12
  250 °C: A 2.33, E_th 12, D 0.5, E₀ 14, R(150 eV) 20

TiN clear: Cl₂ 60 / Ar 60, 6 mTorr, 600 W, ≈ 60 eV
  TiN 40 nm/min; ZrO₂ 0.5 nm/min; selectivity ≈ 80

Plasma ALE: BCl₃ dose 1.0 s (no plasma) / purge 0.75 s / Ar⁺ 60 eV 2.0 s /
purge 0.75 s; cycle 4.5 s
  Film                      EPC (nm/cycle)
  ─────────────────────────────────────────
  ZrO₂ tetragonal            0.10  (saturated ≈ 0.107; first cycle +0.05)
  ZrO₂ amorphous             0.12
  Al₂O₃                      0.08
  HfO₂                       0.09
  PECVD SiN                  0.015
  SiO₂                       0.03
  TiN flat / sidewall        0.15 / 0.02
  KrF resist                 0.25
  Window                     45–75 eV;  synergy 96%

Thermal ALE: HF / DMAC, 250 °C
  ZrO₂ tetragonal 0.06; grain boundary 0.085 (initial); Al₂O₃ 0.05;
  SiN ≈ 0.005; SiO₂ ≈ 0.01 nm/cycle
  Temperature: 200 °C 0.02, 225 °C 0.04, 250 °C 0.06, 275 °C 0.08,
  300 °C 0.10 nm/cycle

Bevel (BCl₃ 120 / Cl₂ 30 / Ar 400, 0.8 Torr, 400 W, 60 °C; ≈ 60% crystalline):
  A_mix 1.60, D 3.0:  front 85 eV 3.0; apex 90 eV 3.4; back facet 82 eV 2.7;
  backside 80 eV 2.5 nm/min
```

---

## B.6 Grain-Scale Spread of the Continuous Step

```
σ_r (relative, persistent)    60 °C     250 °C
  70 eV                        20%        5%
  100 eV                       10%        4%
  150 eV (reference)           7.5%       3.5%
  250 eV                        6%        3%

σ_t (deposited, grain scale) = 0.12 nm
ALE: random 3% per cycle; persistent 1% of removed thickness
```

---

## B.7 Reagents

```
Reagent        Formula          M (g/mol)   Notes
─────────────────────────────────────────────────────────────────────────────────
BCl₃           BCl₃             117.2       liquefied gas, 1.3 atm at 20 °C; lines
                                            heated to 40 °C; hydrolyses to B(OH)₃
                                            and HCl
HF             HF               20.0        anhydrous; corrosive; thermal ALE
                                            fluorination
DMAC           AlCl(CH₃)₂       92.5        pyrophoric liquid; vapour draw limited;
                                            ligand exchange with Cl and CH₃
TMA            Al(CH₃)₃         72.1        pyrophoric; etches Al₂O₃, HfO₂ more
                                            readily than ZrO₂ in thermal ALE
O₃             O₃               48.0        ALD oxidant; post-trim F and C removal
```

---

## B.8 Emission Lines

```
Species      λ (nm)                    Use
───────────────────────────────────────────────────────────────────
Ti I         399.9, 453.3              TiN clear transition
Zr I         360.1, 468.8              ZAZ presence; ALE clearing curve
Zr II        343.8
Al I         394.4, 396.2              Al marker
AlCl         261.4 (band)
B I          249.7                     BCl₃ dose verification
BCl          272 (band)
Cl I         837.6                     wall state (actinometry)
N₂ (2⁺)      337.1                     SiN exposure
Si I         288.2                     SiN exposure
Ar I         750.4                     actinometer
Ar (VUV)     104.8, 106.7              dielectric damage at exposed edges
```

---

**Appendix B Version:** 1.0
