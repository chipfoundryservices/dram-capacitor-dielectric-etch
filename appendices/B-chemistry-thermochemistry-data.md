# Appendix B: Chemistry & Thermochemistry Data

Reaction enthalpies, halide volatilities, bond energies, model parameters, ALE data, and emission lines used in the chemistry chapters. Values are rounded literature-class values for illustration; use evaluated data for design work.

---

## B.1 Standard Enthalpies of Formation (kJ/mol, 298 K)

```
Species         ΔH_f        Species          ΔH_f
──────────────────────────────────────────────────────
ZrO₂(s)         −1101       BCl₃(g)          −403
ZrCl₄(s)        −981        B₂O₃(s)          −1274
ZrCl₄(g)        ≈ −870      BF₃(g)           −1136
ZrF₄(s)         −1911       HF(g)            −273
HfO₂(s)         −1145       H₂O(g)           −242
HfCl₄(s)        −990        HCl(g)           −92
Al₂O₃(s)        −1676       CO(g)            −110.5
AlCl₃(s)        −704        SiO₂(s)          −911
TiO₂(s)         −944        SiCl₄(g)         −663
TiCl₄(g)        −763        Cl₂, O₂, N₂      0
```

---

## B.2 Key Reactions

```
Reaction                                          ΔH (kJ/mol)   Comment
──────────────────────────────────────────────────────────────────────────────────
ZrO₂ + 2 Cl₂ → ZrCl₄(s) + O₂                      +120          uphill; needs getter
HfO₂ + 2 Cl₂ → HfCl₄(s) + O₂                      +155
Al₂O₃ + 3 Cl₂ → 2 AlCl₃(s) + 3/2 O₂               +268
ZrO₂ + 4/3 BCl₃ → ZrCl₄(s) + 2/3 B₂O₃             −191          boron getter
ZrO₂ + 4/3 BCl₃ → ZrCl₄(g) + 2/3 B₂O₃             −80           gas-phase product
HfO₂ + 4/3 BCl₃ → HfCl₄(s) + 2/3 B₂O₃             −156
Al₂O₃ + 2 BCl₃ → 2 AlCl₃(s) + B₂O₃                −198
ZrO₂ + 2 Cl₂ + 2 C → ZrCl₄(s) + 2 CO              −101          carbon getter
ZrF₄ + 4/3 BCl₃ → ZrCl₄(s) + 4/3 BF₃              −48           halogen exchange
ZrO₂ + 4 HF → ZrF₄ + 2 H₂O(g)                     −200          thermal-ALE
                                                                fluorination
TiO₂ + 4/3 BCl₃ → TiCl₄(g) + 2/3 B₂O₃             −131          fast in D1
BCl₃ + 3/2 H₂O → ½ B₂O₃ + 3 HCl                   (exothermic)  line moisture,
                                                                PET chemistry
```

---

## B.3 Bond Energies (diatomic, kJ/mol)

```
C–O 1077    B–O 806    Hf–O 802    Si–O 798    Zr–O 766    Ti–O 672    Al–O 512
B–N 389     Si–N ≈ 470 Zr–Cl ≈ 530 B–Cl ≈ 530  Zr–F ≈ 620  B–F ≈ 760   H–Cl 431
```

---

## B.4 Halide Volatility

```
Normal sublimation or boiling point (°C):
  BCl₃ 12.5    SiCl₄ 58    TiCl₄ 136    AlCl₃ 180 (subl.)    NbCl₅ 254
  HfCl₄ 317 (subl.)    ZrCl₄ 331 (subl.)    LaCl₃, YCl₃, SrCl₂ involatile
  BF₃ −100    SiF₄ −86 (subl.)    NbF₅ 234    TiF₄ 284 (subl.)
  ZrF₄ ≈ 905 (subl.)    HfF₄ ≈ 970 (subl.)    AlF₃ 1276 (subl.)    SrF₂ 2460

ZrCl₄ vapor pressure (Clausius–Clapeyron, ΔH_sub ≈ 110 kJ/mol, Chapter 3):
  ln(p / 760 Torr) = −13,200 K × (1/T − 1/604 K)
  60 °C: 1.4 × 10⁻⁵ Torr   120 °C: 6 × 10⁻³   190 °C: ≈ 1   250 °C: ≈ 26
```

---

## B.5 Threshold-Yield Model Parameters (Chapter 3)

```
R(E, T) = A(T) (√E − √E_th(T))   [nm/min, E in eV]

Film                 T (°C)    A (nm/min/√eV)   E_th (eV)
─────────────────────────────────────────────────────────
ZrO₂ tetragonal       60        1.33             60
                     150        2.03             40
                     250        2.76             25
PECVD SiN             60        1.18             30
                     250        1.05             30
PE-TEOS              250        0.98             40

D1 operating point (250 °C, 70 eV):
  ZrO₂ 9.3 nm/min (model) / 9.0 (reference); SiN 3.0; SiO₂ 2.0
  d ln R / dE = 1.8% per eV;  d ln R / dT ≈ 0.7% per °C
BₓClᵧ deposition: ≈ 1–2 nm/min at 60 °C; ≈ 0.3 nm/min at 250 °C
```

---

## B.6 Rates and EPCs Used in This Book

```
Film                 D1 (nm/min)   D2 (nm/cycle)   Thermal ALE      0.5% HF
                     250 °C, 70 eV 100 °C, 60 eV   (nm/cycle) 275 °C (nm/min)
──────────────────────────────────────────────────────────────────────────────
ZrO₂ amorphous         14            0.13            0.09             ≈ 2
ZrO₂ tetragonal         9.0          0.10            0.05             0.1–0.3
ZrO₂ monoclinic         8.0          0.095           0.04             ≈ 0.1
Al₂O₃                   7.0          0.08            0.06             ≈ 3
HfO₂ monoclinic         7.5          —               0.04             < 0.1
SiOₓNᵧ interlayer       3.5          0.03            —                —
PECVD SiN               3.0          0.012           < 0.005          ≈ 2
PE-TEOS                 2.0          0.010           < 0.005          ≈ 5
TE TiN (lateral)        1.2          ≈ 0.005         ≈ 0              < 0.1
SiGe (lateral)          1.0          ≈ 0             ≈ 0              < 0.1
W (lateral)             0.5          ≈ 0             ≈ 0              < 0.1
```

---

## B.7 Plasma ALE Data (Chapter 4)

```
D2 EPC vs step-B ion energy (ZrO₂ tetragonal):
  20 eV 0.01 | 35 eV 0.06 | 45 eV 0.095 | 60 eV 0.10 | 70 eV 0.11 | 90 eV 0.16 | 120 eV 0.24

D2 synergy: α (step A alone) ≈ 0.002 nm; β (step B alone) ≈ 0.008 nm;
            S = (EPC − α − β) / EPC ≈ 90% at 100 °C; 76% at 250 °C

Step saturation (EPC, nm): A 0.3 s 0.04 | 0.7 s 0.08 | 1.0 s 0.095 | 1.5 s 0.10
                           B 0.5 s 0.05 | 1.0 s 0.08 | 1.5 s 0.095 | 2.5 s 0.10
```

---

## B.8 Emission Lines and Bands (Chapter 8)

```
Species    Wavelength (nm)                 Use
─────────────────────────────────────────────────────────────────────
Zr I       360.1, 351.9, 349.6             ZrO₂ present (falls at clearing)
Hf I       368.2, 377.8                    HfO₂-containing variants
Al I       394.4, 396.2                    Al₂O₃ insertion marker
Nb I       405.9, 410.1                    Nb₂O₅ insertion marker
Si I       288.2; SiCl 280–290 band        SiN exposed (rises at clearing)
BO         α band heads ≈ 420–600          oxygen gettering (falls)
N₂         337.1, 357.7 (2nd positive)     SiN exposed
B I        249.7, 249.8                    BCl₃ dissociation
BCl        ≈ 272                           BCl₃ plasma
Cl I       837.6                           Cl density
Ar I       750.4, 811.5                    actinometry
```

---

**Appendix B Version:** 1.0  
**Last Updated:** 2026-10-05
