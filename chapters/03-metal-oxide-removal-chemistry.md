# Chapter 3: Surface Chemistry of Metal-Oxide Removal — Plasma, Thermal & Wet

## Overview

Zirconia and alumina are chosen for the capacitor because they do not react. They survive 425 °C furnaces, oxidizing ozone, and a decade at 1 MV/cm, and that stability is what makes them hard to remove. Book #32 (Chapter 4) developed one answer: an ion-assisted BCl₃/Cl₂ plasma at 60 °C, in which boron takes the oxygen, chlorine takes the metal, and ions break the lattice. This book needs three answers, because it has four removals to make, in places where a plasma is not always the right tool.

This chapter sets the three routes side by side: ion-assisted chlorination, thermal fluorination with ligand exchange, and wet etching in dilute HF. It builds a thermochemistry map that explains why chlorine and boron remove zirconia while fluorine alone does not, and why a fluorine step followed by a ligand exchange can. It restates the ion-yield model used throughout the book, develops the temperature window and self-limiting saturation of thermal atomic-layer etching, and ends with what each route leaves on the surface.

**Learning Objectives:**
- Compare plasma, thermal, and wet removal of ZrO₂ by driver, isotropy, temperature, and by-products
- Compute reaction enthalpies for chlorination, fluorination, and fluoride conversion from handbook data
- Explain why ZrF₄ is a trap and AlF₃ a worse one, and why BCl₃ converts the first and not the second
- Apply the ion-yield model to amorphous and tetragonal ZrO₂ and identify the etch–deposition transition
- Describe the temperature window and the self-limiting saturation of HF/ligand thermal ALE
- State what each route leaves on the dielectric surface

---

## 3.1 Three Routes

```
Route                  Driver                  Isotropy     Temperature   Products leave as
─────────────────────────────────────────────────────────────────────────────────────────────
Ion-assisted           ions break the lattice;  anisotropic  60–250 °C     ZrCl₄, AlCl₃ gas;
chlorination           B takes O, Cl takes M    (vertical)                  boron oxychlorides
(BCl₃/Cl₂ plasma)

Thermal ALE            HF fluorinates; ligand   isotropic    250–300 °C    volatile Zr / Al
(HF + DMAC or TMA)     exchange volatilizes     (conformal)                 complexes (ligand-
                                                                            exchanged fluoride)

Wet                    dissolution in dilute    isotropic    25 °C         soluble fluorides
(0.5% HF, hot H₃PO₄)   HF or hot acid                                       and oxyfluorides
```

The three differ in what they cannot do. A plasma cannot reach into the shadowed gaps of the forest; thermal ALE has no ions and no sharp boundary at a mask edge; wet etching cannot enter 13 nm channels without collapsing them, and it leaves nothing at the surface that the next step does not have to clean. Each has a place in the modules of this book, and Section 3.7 assigns them.

---

## 3.2 The Thermochemistry Map

### 3.2.1 Why Fluorine Alone Fails and Chlorine Alone Fails

Reaction enthalpies at 298 K from handbook formation enthalpies (solid products; illustrative to ± 10 kJ/mol; entropy shifts the picture at 250 °C but not its order):

```
Enthalpy of formation (kJ/mol):
  ZrO₂ −1100.6    ZrCl₄(s) −980.5   ZrF₄ −1911.3
  HfO₂ −1144.7    HfCl₄    −990.4   HfF₄ −1930.5
  Al₂O₃ −1675.7   AlCl₃    −704.2   AlF₃ −1510.4
  TiO₂ −944.0                       TiF₄ −1649
  B₂O₃ −1273.5    BCl₃(g)  −403.8   BF₃(g) −1136.0
  HF(g) −273.3    H₂O(g) −241.8     HCl(g) −92.3
  SiO₂ −910.7                       SiF₄(g) −1615.0

Reaction                                          ΔH (kJ/mol)    Reading
────────────────────────────────────────────────────────────────────────────────────
ZrO₂ + 2 Cl₂ → ZrCl₄ + O₂                          +120          chlorine alone: uphill
ZrO₂ + 4 HCl → ZrCl₄ + 2 H₂O                       +6            HCl: neutral
ZrO₂ + 4/3 BCl₃ → ZrCl₄ + 2/3 B₂O₃                 −191          BCl₃: downhill
ZrO₂ + 4 HF → ZrF₄ + 2 H₂O                         −201          fluorination: strongly down
HfO₂ + 4 HF → HfF₄ + 2 H₂O                         −176
Al₂O₃ + 6 HF → 2 AlF₃ + 3 H₂O                      −431          (−215 per Al)
TiO₂ + 4 HF → TiF₄ + 2 H₂O                         −95
SiO₂ + 4 HF → SiF₄(g) + 2 H₂O                      −95           volatile product
```

Chlorine alone is uphill; BCl₃ is downhill because the B–O bond is the strongest in the system. Fluorination is the most exothermic of all, and for that reason it is a trap: the fluoride sits at the bottom of the energy well, and what is left must then be volatilized.

### 3.2.2 Volatility Decides the Next Step

```
Sublimation / boiling point (°C, handbook values, rounded):
  ZrCl₄   331        ZrF₄    ≈ 906
  HfCl₄   317        HfF₄    ≈ 970
  AlCl₃   180        AlF₃    ≈ 1276
  TiCl₄   136 (bp)   TiF₄    284
  SiCl₄    57 (bp)   SiF₄    −86 (sublimes)
```

TiF₄ sublimes at 284 °C and SiF₄ is a gas, so HF alone removes titanium oxides and silicon oxides at modest temperatures. ZrF₄ and AlF₃ do not. In an HF vapor at 280 °C, zirconia converts to a ZrF₄ layer of limited thickness and then stops: the fluoride is the end of the reaction, not a volatile product. This is the **ZrF₄ trap**, and it is the reason Book #32 (Chapter 7) forbids a fluorine clean on a zirconium-coated wall, and the reason this book forbids fluorine in the ALD-chamber clean (Chapter 9) and in the conductor-etch overetch (Chapter 10).

### 3.2.3 Converting a Fluoride

A fluoride skin can sometimes be converted back to a chloride, whose product is volatile, by BCl₃. The driving force is the formation of BF₃, a very stable gas:

```
Reaction                                          ΔH (kJ/mol)     Reading
─────────────────────────────────────────────────────────────────────────────────
ZrF₄ + 4/3 BCl₃ → ZrCl₄ + 4/3 BF₃                   −45         converts; ZrCl₄ subl. 331 °C
HfF₄ + 4/3 BCl₃ → HfCl₄ + 4/3 BF₃                   −36         converts
AlF₃ + BCl₃ → AlCl₃ + BF₃                           +74         does NOT convert
```

The zirconium and hafnium skins convert, mildly exothermic, and the product leaves as a chloride at 250 °C. The AlF₃ skin does not. AlF₃ is the one fluoride that BCl₃ cannot remove, and the 0.3 nm Al₂O₃ layer of the ZAZ is where it forms. The layer is small: 0.3 nm of Al₂O₃ holds 1.1 × 10¹⁵ Al cm⁻², which is 110 times the periphery limit for zirconium, so a fluorinated Al layer is not negligible on a monolayer scale, though it lies between two ZrO₂ layers, and the ZrO₂ above it clears before the Al layer is reached. Chapter 10 shows how much fluorine can reach it.

---

## 3.3 Ion-Assisted Chlorination

### 3.3.1 The Yield Model

Book #32 used one model for TiN, SiN, and ZrO₂: the etch rate is the ion flux times a yield that rises as the square root of the ion energy above a threshold:

```
ER = Y(E) · K,    Y = A (√E − √E_th),    K = Γ_i θ / n = 3.9 nm/s per unit yield

Calibrated to Book #32 (TiN 42 nm/min at 70 eV, E_th = 25 eV, A = 0.053):
  K = 0.70 nm/s / 0.178 = 3.92 nm/s

ZrO₂ tetragonal:  E_th = 60 eV;  A = 0.0057   (6 nm/min at 150 eV)
ZrO₂ amorphous:   E_th = 45 eV;  A = 0.0069   (9 nm/min at 150 eV)
```

```
ER (nm/min)         E = 40    70     100    150    250 eV
─────────────────────────────────────────────────────────
TiN                 16.5     42      62     —      —
ZrO₂ tetragonal      0       0.8     3.0    6.0    10.8
ZrO₂ amorphous       0       2.7     5.4    9.0    14.8
```

The table reproduces Book #32's values for TiN and crystalline ZrO₂ and extends them to amorphous film. At 40 eV TiN etches at 16.5 nm/min and zirconia not at all. That is the basis for the conductor stop of Chapter 4.

### 3.3.2 The Etch–Deposition Transition

In BCl₃-rich plasmas a boron–chlorine film deposits wherever the ions do not remove it faster (Book #32, Chapter 4). The net rate is Y K − D with D ≈ 1–2 nm/min. For amorphous ZrO₂ the yield at 55 eV is 0.0049, so Y K = 1.2 nm/min and the net rate crosses zero; for tetragonal it is zero below 60 eV. In practice both films need more than 60 eV to etch in BCl₃. The ion energy for each step of this book is therefore chosen as:

```
Step                        Chemistry            Ion energy        Why
─────────────────────────────────────────────────────────────────────────────────────
P2  TiN stop                Cl₂/Ar (no BCl₃)     ≈ 40 eV           below ZrO₂ threshold; no B film
P4  hot ZAZ clear           BCl₃/Cl₂/Ar, 250 °C  ≈ 80 eV          hot: E_th lower; Cl volatilizes
E   edge etch               BCl₃/Cl₂/Ar          ≈ 250 eV          low ion flux at edge; high E
```

At 250 °C the energy threshold falls (Book #32, Chapter 4: 60 → 25 eV) because ZrCl₄ desorbs thermally; at the edge the ion flux is a quarter of the main chamber's, so the energy is raised to compensate.

### 3.3.3 No Ions, No Etch

At zero ion energy, chlorine atoms alone do not etch ZrO₂: the reaction is uphill by 120 kJ/mol. The consequence is geometric. An ion-assisted etch of zirconia is sharp at the edge of the region where ions arrive. The plasma boundary and the mask edge define the etched region to within the sheath thickness, and radicals that diffuse beyond it do nothing. Chapter 5 uses this for the sharp inner boundary of the edge etch; Chapter 11 contrasts it with the isotropic undercut of thermal and wet removal.

---

## 3.4 Thermal Atomic-Layer Etching

### 3.4.1 The Cycle

```
Thermal ALE of ZrO₂ (reference, illustrative):
  Step 1   HF dose, 2 s       ZrO₂ surface → ZrF₄ layer (self-limiting thickness)
  Step 2   purge, 3 s
  Step 3   DMAC dose, 2 s     ligand exchange: volatile Zr complex leaves
  Step 4   purge, 3 s
  Cycle    10 s;  280 °C;  HF 0.1 Torr, DMAC 0.05 Torr partial pressure
  Removal  0.07 nm per cycle (amorphous),  0.045 nm per cycle (tetragonal)
```

The first half-cycle makes the fluoride whose formation is so exothermic (−201 kJ/mol). The second moves fluorine onto the ligand donor and carries the metal away in a volatile complex. The exact gas-phase products have been proposed rather than settled in the literature, and for the purpose of an etch design what matters is that the second half-cycle is **self-limiting** (it stops when the fluorinated layer is gone) and the first is **self-limiting** (the fluoride layer reaches a fixed thickness). Each cycle therefore removes a fixed amount, independent of exposure above saturation and independent of the position of the surface.

### 3.4.2 The Temperature Window

```
EPC(T) = EPC_max / [1 + exp(−(T − T₀)/ΔT)]     EPC_max = 0.10 nm, T₀ = 258 °C, ΔT = 22 °C
                                                (amorphous ZrO₂; illustrative)

 T (°C)     EPC amorphous (nm)     EPC tetragonal (nm, ×0.65)
 ───────────────────────────────────────────────────────────
  200           0.007                 0.004
  225           0.018                 0.012
  250           0.041                 0.027
  265           0.058                 0.038
  280 (ref)     0.073                 0.048
  300           0.087                 0.057
  325           0.095                 0.062
```

Below about 225 °C the ligand exchange is too slow to remove the fluoride; above 325 °C the rate saturates and parasitic reactions (thermal decomposition of the ligand donor, which leaves carbon) set in. The reference sits at 280 °C, on the steep part of the curve where a 5 °C error is a 6% change in removal; Chapter 6 specifies the temperature uniformity this demands. The tetragonal film etches at 0.65× the amorphous rate, the same ratio as in the plasma.

### 3.4.3 Saturation

On a flat monitor, the HF half-cycle saturates at an exposure of about 10⁵ Langmuir (1 L = 10⁻⁶ Torr·s). The reference dose is 0.1 Torr × 2 s = 2 × 10⁵ L, twice the saturation exposure. The minimum exposure for the bottom of a 13 nm channel 1.4 µm deep, from the transport model of Chapter 6, is 4 × 10⁴ L, so transport is not the limit. The dose is set by saturation on the flat wafer and checked against the channel.

```
Removal per wafer with N cycles: d = N × EPC  (amorphous at 280 °C)
  0.2 nm trim:    3 cycles       0.5 min
  0.8 nm finish (tetragonal, +30%):  0.8 × 1.3 / 0.045 = 23 cycles   3.9 min
  5.5 nm full strip (amorphous):     5.2 / 0.07 + 0.3 / 0.05 = 74 + 6 = 80 cycles   13 min
```

---

## 3.5 Wet Removal

```
Wet etch rates, 25 °C (Book #32, Chapter 4; illustrative):
  Film                  0.5% HF           Hot H₃PO₄ (160 °C)
  ──────────────────────────────────────────────────────────
  ZrO₂ amorphous        2 nm/min          3 nm/min
  ZrO₂ tetragonal       0.1–0.3 nm/min    1 nm/min
  Al₂O₃ amorphous       3 nm/min          fast
  SiN (PECVD)           2 nm/min          5 nm/min
  TiN                   < 0.1 nm/min      slow
  W                     < 0.1 nm/min      attacked
```

Amorphous ZAZ would clear in 5.5/2 × 60 = 165 s in 0.5% HF. Wet etching is out of the question for the free-standing forest: dilute HF wets the 13 nm channels, and the capillary pressure at the drying meniscus (Book #30, Chapter 14) collapses unsupported pillars. It is acceptable only where there is no forest: on the periphery after the plate is cut (the hybrid route R4, Chapter 4), on the bevel in a stand-alone edge tool, and for rework of the whole film in a single-wafer cell with a supercritical or low-surface-tension dry (Chapter 13). Crystalline ZrO₂ resists dilute HF at 0.1–0.3 nm/min, so a 1 nm finish takes 5 minutes at 0.2 nm/min (300 s) and attacks the plate-edge dielectric laterally by the same amount.

---

## 3.6 What Each Route Leaves on the Surface

```
Route                  Residues on the ZAZ surface               Removed by
─────────────────────────────────────────────────────────────────────────────────────────
BCl₃/Cl₂ plasma        BₓClᵧ / BOₓClᵧ film ≈ 0.5 nm, hygroscopic   O₂/H₂O plasma or water rinse
                       Cl 2–5 at% in the outer nanometre            anneal; post-etch treatment
                       Zr redeposition (sputtered ZrClₓ)            megasonic rinse (before dry)
Cl₂/Ar stop (P2)       Cl 1–3 at% on the ZAZ; TiClₓ traces          hot BCl₃ conversion (Ch. 10)
                       F from wall memory → ZrF₄/AlF₃ patches       BCl₃ (ZrF₄ only)
Thermal ALE            F 1–3 at% in the surface; C < 1 at%          anneal; vacancy repair (Ch. 12)
                       ligand-donor remnants                        purge; higher T
Wet HF                 F-terminated surface; oxyfluorides           rinse; anneal
```

No route leaves the surface as it found it. The edge etch leaves a surface that is buried under the top electrode only after the edge zone is excluded; the thermal etch leaves the array's dielectric slightly fluorinated; the periphery routes leave a surface that the next step must tolerate. Chapter 12 returns to what these residues do to the film that stays.

---

## 3.7 Which Route for Which Module

```
Module   Task                         Route                          Chapter
──────────────────────────────────────────────────────────────────────────────────────
E        edge, bevel, backside        ion-assisted chlorination,     5
                                      amorphous, resistless
P2       stop on ZAZ                  Cl₂/Ar, 40 eV (below E_th)     4, 10
P4       periphery clear              ion-assisted chlorination,     7
                                      hot (250 °C), plate as mask
P4+      finishing last 1 nm          thermal ALE (R2)               6, 13
T        trim, rework                 thermal ALE                    6, 13
C        ALD-chamber clean            thermal / remote BCl₃, Cl₂     9
R4       hybrid dry + wet             dilute HF finish               4, 11
```

---

## Summary and Key Takeaways

1. **Chlorine alone is uphill (+120 kJ/mol); BCl₃ is downhill (−191); fluorination is the deepest well (−201).** The first two give volatile ZrCl₄; the third gives ZrF₄, which sublimes near 906 °C.

2. **BCl₃ converts ZrF₄ and HfF₄ (−45 and −36 kJ/mol) but not AlF₃ (+74).** A fluorine-contaminated 0.3 nm Al₂O₃ layer is the one trap that survives a BCl₃ step.

3. **One yield model covers every plasma step.** ER = K A(√E − √E_th), with E_th = 45 eV (amorphous) and 60 eV (tetragonal); at 40 eV TiN etches at 16.5 nm/min and ZrO₂ not at all.

4. **No ions, no etch, sharp boundary.** Radicals alone cannot etch zirconia, so the edge of an ion-assisted etch is the edge of the ion flux.

5. **Thermal ALE is a window and a saturation.** 0.07 nm per 10 s cycle on amorphous film at 280 °C, 6% per 5 °C on the steep part, 0.65× on tetragonal; 80 cycles (13 min) strips the whole film (the 0.3 nm Al₂O₃ layer at an assumed 0.05 nm per cycle).

6. **Each route leaves something.** BₓClᵧ and Cl from the plasma, F and ligand remnants from thermal ALE, F-terminated surface from wet; Chapter 12 asks what they do to the film that stays.

---

## Study Questions

1. Compute ΔH for HfO₂ + 4HF → HfF₄ + 2H₂O and for HfF₄ + 4/3 BCl₃ → HfCl₄ + 4/3 BF₃ from the data of Section 3.2.1. Compare with ZrO₂ and say which bond-energy fact explains the difference.

2. Using the yield model of Section 3.3.1, compute the amorphous ZrO₂ rate at 180 eV with the edge plasma's ion flux at 0.25 of the main chamber's. How long does the edge etch take to clear 5.5 nm of ZAZ (rates of Al₂O₃ scaled as 5/9 of the ZrO₂ rate)?

3. Using the logistic EPC(T) of Section 3.4.2, compute the removal per cycle at 270 °C for amorphous ZrO₂. By what percentage does the removal per wafer (80 cycles) change for a chuck 5 °C hotter than 280 °C?

4. A rework needs to remove 5.5 nm of amorphous ZAZ. Compute the cycles and time at the reference 10 s cycle, and at 280 °C for a film that has partly crystallized to X = 0.41 (use R(X) of Chapter 2 as a weight on EPC).

5. A wall coated with 0.3 nm of Al₂O₃ is exposed to a fluorine plasma and fully converted to AlF₃. How many Al atoms per cm² must a following BCl₃ step remove, and why can it not do so by conversion? What step could?

6. Wet 0.5% HF removes amorphous ZAZ at 2 nm/min and etches tetragonal at 0.2 nm/min. For a 1 nm finish on tetragonal film, compute the time and the lateral undercut at the plate edge. Compare with the 1.5 µm plate overlap.

---

**Next Chapter:** [Chapter 4: Selectivity Design — The Dielectric as Target and as Stop Layer](./04-selectivity-target-and-stop.md)

---

**Chapter 3 Development Status:** Complete  
**Version:** 1.0
