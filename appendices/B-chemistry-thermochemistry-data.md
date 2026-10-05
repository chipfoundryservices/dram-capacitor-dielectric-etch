# Appendix B: Chemistry & Thermochemistry Data

Thermochemical data, reaction enthalpies, and model parameters used in Chapters 3, 4, 9, 10, and 14. Enthalpies are handbook formation enthalpies at 298 K (solid products unless marked), rounded; they are illustrative to ± 10 kJ/mol, and entropy shifts the picture at 250–350 °C without changing its order.

---

## B.1 Enthalpies of Formation (kJ/mol)

```
Oxides                    Chlorides                   Fluorides                  Other
────────────────────────────────────────────────────────────────────────────────────────────────────
ZrO₂      −1100.6         ZrCl₄(s)   −980.5           ZrF₄      −1911.3          BCl₃(g)   −403.8
HfO₂      −1144.7         HfCl₄(s)   −990.4           HfF₄      −1930.5          BF₃(g)   −1136.0
Al₂O₃     −1675.7         AlCl₃(s)   −704.2           AlF₃      −1510.4          B₂O₃(s)  −1273.5
TiO₂      −944.0          TiCl₄(g)   −763.2           TiF₄      −1649            HF(g)     −273.3
SiO₂      −910.7          SiCl₄(g)   −662.7           SiF₄(g)   −1615.0          H₂O(g)    −241.8
SrO       −592.0          SrCl₂      −828.9           SrF₂      −1216.3          HCl(g)     −92.3
BaO       −548.0          BaCl₂      −858.6           BaF₂      −1207.1
```

---

## B.2 Reaction Enthalpies (kJ/mol of oxide or fluoride)

```
Chlorination
  ZrO₂ + 2 Cl₂ → ZrCl₄ + O₂                                +120      uphill
  ZrO₂ + 4 HCl → ZrCl₄ + 2 H₂O                              +6       neutral
  ZrO₂ + 4/3 BCl₃ → ZrCl₄ + 2/3 B₂O₃                       −191      downhill (B–O bond)

Fluorination (HF vapor)
  ZrO₂ + 4 HF → ZrF₄ + 2 H₂O                               −201      trap: ZrF₄ subl. ≈ 906 °C
  HfO₂ + 4 HF → HfF₄ + 2 H₂O                               −176
  Al₂O₃ + 6 HF → 2 AlF₃ + 3 H₂O                            −431      (−215 per Al)
  TiO₂ + 4 HF → TiF₄ + 2 H₂O                                −95      TiF₄ subl. 284 °C: volatile
  SiO₂ + 4 HF → SiF₄ + 2 H₂O                                −95      SiF₄ gas
  SrO + 2 HF → SrF₂ + H₂O                                  −320      no volatile product
  BaO + 2 HF → BaF₂ + H₂O                                  −354      no volatile product

Fluoride conversion by BCl₃
  ZrF₄ + 4/3 BCl₃ → ZrCl₄ + 4/3 BF₃                         −45      converts
  HfF₄ + 4/3 BCl₃ → HfCl₄ + 4/3 BF₃                         −36      converts
  AlF₃ + BCl₃ → AlCl₃ + BF₃                                +74      does not convert
```

---

## B.3 Ion-Yield Model Parameters

```
ER = K · Y(E),   Y = A (√E − √E_th),   K = 3.92 nm/s per unit yield
(calibrated to Book #32: TiN 42 nm/min at 70 eV, A = 0.053, E_th = 25 eV)

Film / chemistry                      E_th (eV)     A        Calibration
─────────────────────────────────────────────────────────────────────────────────────────
TiN, Cl₂ or BCl₃/Cl₂                     25        0.0530    42 nm/min at 70 eV
ZrO₂ tetragonal, BCl₃/Cl₂, 60 °C         60        0.00566   6.0 nm/min at 150 eV
ZrO₂ amorphous, BCl₃/Cl₂, 60 °C          45        0.00690   9.0 nm/min at 150 eV
ZrO₂ tetragonal, BCl₃/Cl₂, 250 °C        25        0.01293   12.0 nm/min at 80 eV
SiN, BCl₃/Cl₂, 250 °C                    30        0.00490   4.0 nm/min at 80 eV
W, BCl₃/Cl₂, 250 °C                      40        0.00389   2.4 nm/min at 80 eV
ZrO₂ in BCl₃-free Cl₂                    —         0.3 × the BCl₃/Cl₂ value of the same energy

 E (eV)    TiN     ZrO₂ tet.   ZrO₂ amor.   ZrO₂ hot    SiN hot    W hot       (nm/min)
   40      16.5       0           0           —           —          —
   50      25.8       0          0.6          6.3         1.8        0.7
   70      42.0      0.83        2.7          —           —          —
   80      49.2      1.6         —            12.0        4.0        2.4
  100      62.4      3.0         5.4          15.2        5.2        3.4
  150       —        6.0         9.0          22.0        7.8        5.4
  250       —       10.8        14.8          —           —          —
```

The etch–deposition transition of BCl₃ plasmas is near 55–60 eV at 60 °C (Chapter 3).

---

## B.4 Thermal ALE Parameters

```
HF/DMAC cycle (reference): HF 0.1 Torr 2 s; purge 3 s; DMAC 0.05 Torr 2 s; purge 3 s; 10 s per cycle

EPC(T) = 0.10 nm / [1 + exp(−(T − 258 °C)/22 °C)]      (amorphous ZrO₂)
  T (°C)    EPC amorphous (nm)   EPC tetragonal (nm)   d ln EPC/dT   EOT per cycle (nm)
  200          0.007                0.004                —              —
  225          0.018                0.012                —              —
  250          0.041                0.027                2.7%/°C        0.0037
  265          0.058                0.038 (0.65×)        1.9%/°C        0.0053
  280 (ref)    0.073                0.048                1.2%/°C        0.0066
  300          0.087                0.057                —              —
  325          0.095                0.062                —              —

Reference values used in the text: 0.07 nm (amorphous) and 0.045 nm (tetragonal) at 280 °C;
Al₂O₃ layer 0.05 nm per cycle (assumed). Rounded 0.058 nm at 265 °C for trim.

Saturation: HF ≈ 10⁵ L on a flat monitor; reference 2 × 10⁵ L. Transport minimum for AR 109:
4.1 × 10⁴ L (HF), 0.84 s at 0.05 Torr (DMAC).
```

---

## B.5 Channel-Dosing Parameters

```
t_sat = 6 N_s AR² / (n₀ v̄)    (closed tube, Knudsen)        x_sat = g √(n₀ v̄ t / 3 N_s)   (closed slit)

Species     M (amu)   v̄ at 553 K (m/s)   N_s (m⁻²)         Reference partial pressure   n₀ (m⁻³)
Zr precursor  323        190              1.5 × 10¹⁸        20 mTorr                     3.5 × 10²⁰
HF            20         765              7.7 × 10¹⁸        0.1 Torr                     1.75 × 10²¹
DMAC          87         367              3.8 × 10¹⁸        0.05 Torr                    8.7 × 10²⁰

Channel d = p/√3 × 2 − 2(r_pillar + t) = 13.0 nm (45 nm pitch); AR = 109 (1.41 µm)
```

---

## B.6 Species on the ZAZ Surface After Each Step

```
Step                  Species                                             Removed by
────────────────────────────────────────────────────────────────────────────────────────────
P2 (Cl₂/Ar, 40 eV)    Cl 2–5 at% in the outer nm; ZrF₄ patches (F memory)  strip (Cl); hot BCl₃ (ZrF₄)
P3 (strip)            hydroxyl; clean, oxygen-terminated; Cl −80%          desorption at 250 °C
P4 (BCl₃/Cl₂ hot)     BₓClᵧ on cold parts; Cl on SiN                        P5: H₂O/O₂ plasma, rinse
Edge etch             BₓClᵧ film, ZrClₓ redeposit                           O₂/H₂O; 0.5% HF edge clean
Thermal ALE           F 1–3 at% in the outer 0.5 nm; C < 1 at%              oxidizing step; anneal
```

---

**Appendix B Version:** 1.0
