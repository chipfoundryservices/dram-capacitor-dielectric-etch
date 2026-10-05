# Chapter 3: Plasma Chemistry of Metal-Oxide Etching

## Overview

Every etch chemistry is a plan for turning a solid into a gas. For silicon dioxide the plan is fluorine: SiF₄ boils at −86 °C, and fluorocarbon plasmas turn oxide into gas at hundreds of nanometres per minute. For zirconium oxide, fluorine is a dead end: ZrF₄ sublimes only near 900 °C at atmospheric pressure, and a fluorinated ZrO₂ surface is a passivation layer, not a product. Chlorine is the only practical halogen. ZrCl₄ is volatile enough to leave a hot surface, but chlorine alone cannot pull oxygen out of ZrO₂; the reaction is uphill. Something must take the oxygen. In a plasma, that something is boron.

This chapter develops the chemistry of the dielectric clear: bond strengths and halide volatility, the thermochemistry of chlorination with and without an oxygen getter, the BCl₃ plasma and its etch–deposition transition, an ion-yield model in which temperature lowers the threshold energy, and the selectivity to the nitride, the oxide cap, and the plate sidewall that follow from it. The model is calibrated to the in-situ cold step of Book #32 and carried to the 250 °C chamber of this book's reference process D1.

**Learning Objectives:**
- Rank the halides of Zr, Hf, Al, Ti, Si, and B by volatility and compute vapor pressures with the Clausius–Clapeyron relation
- Compute reaction enthalpies for chlorination of ZrO₂ and Al₂O₃ with Cl₂, BCl₃, and carbon-assisted Cl₂
- Explain the etch–deposition transition in BCl₃ plasmas and its temperature dependence
- Use a threshold-yield model with temperature-dependent parameters to predict rates at any energy and temperature
- Derive the selectivity of ZrO₂ to SiN and SiO₂ and its dependence on ion energy and temperature
- Explain why heat, not ion energy, is the efficient lever for high-k removal

---

## 3.1 Bonds and Volatility

### 3.1.1 Bonds

```
Element–oxygen bond dissociation energy (diatomic, kJ/mol, illustrative):
  B–O     806        ← the getter
  Hf–O    802
  Si–O    798
  Zr–O    766
  Ti–O    672
  Al–O    512        (lattice energy of Al₂O₃ is nevertheless very high)
  C–O    1077        (CO; carbon is an even stronger getter, if present)
```

### 3.1.2 Halide Volatility

```
Normal sublimation or boiling point (°C, at 760 Torr, illustrative):
  Chlorides                       Fluorides
  ───────────────────────────     ───────────────────────────
  BCl₃          12.5 (bp)         BF₃          −100 (bp)
  SiCl₄         58 (bp)           SiF₄          −86 (subl.)
  TiCl₄         136 (bp)          TiF₄          284 (subl.)
  AlCl₃         180 (subl.)       AlF₃         1276 (subl.)
  HfCl₄         317 (subl.)       HfF₄          ≈ 970 (subl.)
  ZrCl₄         331 (subl.)       ZrF₄          ≈ 905 (subl.)
  NbCl₅         254 (bp)          NbF₅          234 (bp)
  SrCl₂        1250 (bp)          SrF₂         2460 (bp)
```

Fluorides of Zr, Hf, and Al are refractory. Chlorides are volatile enough to leave a heated surface. NbCl₅ and NbF₅ are both volatile, which matters for the niobium-containing dielectrics of Chapter 14; SrCl₂ is not, which is why strontium titanate is so hard to dry-etch.

### 3.1.3 Vapor Pressure of ZrCl₄

The Clausius–Clapeyron relation with a sublimation enthalpy of about 110 kJ/mol, anchored at 760 Torr and 331 °C (604 K):

```
ln(p / 760 Torr) = −(ΔH_sub / R) (1/T − 1/604 K),   ΔH_sub / R ≈ 13,200 K

  T (°C)     p(ZrCl₄) (Torr)
  ─────────────────────────────
    60        1.4 × 10⁻⁵
   120        6 × 10⁻³
   190        ≈ 1
   250        ≈ 26
```

In the reference D1, the partial pressure of ZrCl₄ in the gas is about 2 × 10⁻⁵ Torr (Section 3.7). At a 60 °C surface, the equilibrium vapor pressure is about the same as the partial pressure: ZrCl₄ formed on the surface has no thermodynamic reason to leave, and ions must sputter it. At 250 °C, the equilibrium vapor pressure exceeds the partial pressure by six orders of magnitude: any ZrCl₄ that forms leaves at once. **At 250 °C the limit is forming the chloride, not removing it.**

---

## 3.2 Thermochemistry of Chlorination

### 3.2.1 Chlorine Alone

```
Standard enthalpies of formation (kJ/mol, illustrative):
  ZrO₂(s) −1101   ZrCl₄(s) −981   ZrCl₄(g) −870   ZrF₄(s) −1911
  HfO₂(s) −1145   HfCl₄(s) −990
  Al₂O₃(s) −1676  AlCl₃(s) −704
  BCl₃(g) −403    B₂O₃(s) −1274   BF₃(g) −1136
  CO(g) −110.5    SiO₂ −911       SiCl₄(g) −663

ZrO₂ + 2 Cl₂ → ZrCl₄(s) + O₂          ΔH ≈ +120 kJ/mol
Al₂O₃ + 3 Cl₂ → 2 AlCl₃(s) + 3/2 O₂   ΔH ≈ +268 kJ/mol
```

Both are endothermic. Chlorine atoms and ions can still chlorinate the surface, because each ion impact supplies tens of electronvolts, but the oxygen released has nowhere to go except back to the metal. The surface stays oxygen-rich and the rate is low.

### 3.2.2 Boron as the Getter

```
ZrO₂ + 4/3 BCl₃ → ZrCl₄(s) + 2/3 B₂O₃     ΔH ≈ −191 kJ/mol
ZrO₂ + 4/3 BCl₃ → ZrCl₄(g) + 2/3 B₂O₃     ΔH ≈ −80 kJ/mol
Al₂O₃ + 2 BCl₃ → 2 AlCl₃(s) + B₂O₃        ΔH ≈ −198 kJ/mol
```

Boron takes the oxygen, chlorine takes the metal. In the plasma, the boron oxide does not remain as B₂O₃: it reacts with Cl and BClₓ to form volatile boron oxychlorides, chiefly (BOCl)₃ and BOCl, and what remains is sputtered by BCl₂⁺ ions.

### 3.2.3 Carbon as a Getter

```
ZrO₂ + 2 Cl₂ + 2 C → ZrCl₄(s) + 2 CO      ΔH ≈ −101 kJ/mol
```

Carbon is a strong getter too; this is the industrial carbochlorination route by which zirconium is refined. In a plasma etch under resist, carbon sputtered from the resist reaches the surface and contributes some gettering. Book #32's cold in-situ step benefits from it. The hard-mask route of this book is carbon-free: boron must do all of the gettering. The benefit is that the hard-mask route has no carbon to redeposit as micromasks, apart from what the strip leaves behind (Chapter 10).

### 3.2.4 Halogen Exchange on a Fluorinated Surface

A ZrO₂ surface that has picked up fluorine from chamber memory (Chapter 2) carries Zr–F bonds. BCl₃ exchanges them:

```
ZrF₄ + 4/3 BCl₃ → ZrCl₄ + 4/3 BF₃         ΔH ≈ −48 kJ/mol
```

The exchange is mildly exothermic and needs no ion assistance once the surface is hot. It is the same reaction that thermal ALE uses on purpose (Chapter 4). In the reference D1, the BCl₃-rich breakthrough removes any fluorinated skin in its first second.

---

## 3.3 The BCl₃ Plasma

### 3.3.1 Species

```
BCl₃/Cl₂/Ar plasma, 8 mTorr, 900 W ICP (illustrative):
  Ions        BCl₂⁺ (dominant), Cl⁺, Cl₂⁺, Ar⁺, BCl⁺
  Radicals    Cl (dominant), BCl₂, BCl
  Neutral     BCl₃ (≈ 40–60% dissociated)
  Deposits    BₓClᵧ on surfaces with low ion flux or low energy
```

### 3.3.2 Etch Versus Deposition

BCl₃ plasmas deposit a boron–chlorine film wherever ions do not clean the surface fast enough. On an oxide being etched, the net rate is a race:

```
R_net = R_etch(E, T) − D(T, f_Cl₂)

  D = BₓClᵧ deposition rate (nm/min)
  at 60 °C:    D ≈ 1–2 nm/min
  at 250 °C:   D ≈ 0.3 nm/min (BₓClᵧ less sticky, partly volatile;
               more Cl recombination products leave)
```

On the floor of the periphery, ions arrive at full energy and the race goes to etching above a transition energy. On the plate sidewall, ions arrive at grazing incidence and the race goes to deposition. The same film that stops a cold etch at 40 eV protects the plate sidewall during a hot etch at 70 eV (Chapter 11).

### 3.3.3 The Cl₂ Fraction

```
Effect of Cl₂ fraction in BCl₃/Cl₂ (250 °C, 70 eV, illustrative):
  Cl₂ / (BCl₃ + Cl₂)   ZrO₂ (nm/min)   SiN (nm/min)   TiN lateral (nm/min)
  ──────────────────────────────────────────────────────────────────────────
     0%                   7.5             2.5            0.4
    10% (reference)       9.0             3.0            1.2
    20%                   9.5             3.8            2.8
    30%                   9.0             4.6            5.5
    50%                   6.5             5.5            > 10
```

A little Cl₂ raises the Cl atom density, removes BₓClᵧ from the floor, and raises the ZrO₂ rate. Too much dilutes the boron that takes the oxygen, and raises the attack on everything else: the SiN floor and, above all, the TiN top electrode at the plate edge. The reference uses 10%.

---

## 3.4 Ion-Assisted Yield and Temperature

### 3.4.1 The Model

The etch rate of ZrO₂ is modelled as an ion-assisted reaction with a threshold:

```
R(E, T) = A(T) · (√E − √E_th(T))       (nm/min; E in eV)
```

E_th is the ion energy below which ions cannot complete the removal; A collects the ion flux, the surface coverage of chlorine and boron, and the number density of the film. Both depend on temperature: heat helps desorb products, so less energy is needed per removal event (E_th falls), and heat accelerates the chemical steps of chlorination, so each ion is more productive (A rises).

### 3.4.2 Calibration

Book #32 measured tetragonal ZrO₂ at 150 eV in BCl₃/Cl₂ at three temperatures. Assigning thresholds of 60, 40, and 25 eV and solving for A:

```
T (°C)   R at 150 eV   E_th (eV)   √150 − √E_th   A (nm/min/√eV)
─────────────────────────────────────────────────────────────────
  60          6           60           4.50           1.33
 150         12           40           5.92           2.03
 250         20           25           7.25           2.76
```

### 3.4.3 Predictions

```
Tetragonal ZrO₂ rate from the model (nm/min, before BₓClᵧ deposition):
  E (eV)      60 °C       150 °C       250 °C
  ──────────────────────────────────────────────
   40         —           0            3.6
   50         —           1.5          5.7
   70         0.8         4.2          9.3   ← D1 main etch
  100         3.0         7.5          13.8  ← D1 breakthrough
  150         6.0         12.0         20.0
  250         10.7        19.3         29.8
```

At 60 °C and 70 eV, the predicted etch rate is below the deposition rate: the surface gains a BₓClᵧ film. This is why the cold route of Book #32 needs 150 eV. At 250 °C, 70 eV etches at 9 nm/min, half again as fast as the cold route at 150 eV.

### 3.4.4 Yield per Ion

```
Ion flux (reference D1): Γ_i ≈ 2 × 10¹⁶ cm⁻² s⁻¹
ZrO₂ formula units: n = 3.0 × 10²² cm⁻³
R = 9.0 nm/min = 1.5 × 10⁻⁸ cm/s → removal flux 4.5 × 10¹⁴ cm⁻² s⁻¹
Y = 4.5 × 10¹⁴ / 2 × 10¹⁶ ≈ 0.022 ZrO₂ per ion
```

Two percent of an oxide formula unit per ion is typical of refractory oxides, and a reminder of how little a single ion accomplishes. Compare the 0.2–0.3 Si atoms per ion of polysilicon in chlorine.

### 3.4.5 Sensitivities at the Operating Point

```
d ln R / d E = 1 / (2 √E (√E − √E_th))
  at 70 eV, E_th = 25 eV:   1 / (2 × 8.37 × 3.37) = 1.8% per eV
  at 150 eV, E_th = 25 eV:  1 / (2 × 12.25 × 7.25) = 0.56% per eV

d ln R / d T (250 °C, 70 eV), from the calibration:
  via A:       (2.76 − 2.03)/100 / 2.76         ≈ 0.27% per °C
  via E_th:    0.15 eV/°C × 1/(2√E_th) / 3.37    ≈ 0.45% per °C
  total                                          ≈ 0.7% per °C
```

The low-energy operating point that buys selectivity also makes the rate steeply sensitive to ion energy: a 5 eV lower ion energy at the wafer edge costs 9% of the rate there. Chapter 6 returns to what this means for uniformity.

---

## 3.5 Selectivity

### 3.5.1 To Silicon Nitride

Silicon nitride etches in BCl₃/Cl₂ by chlorination of silicon (SiCl₄ is very volatile) and release of nitrogen as N₂ or NCl. Its threshold is set mainly by breaking Si–N bonds; because SiCl₄ is volatile at any temperature, heat helps it much less than it helps ZrO₂.

```
SiN model (illustrative):  R_SiN = A_SiN (√E − √30 eV)
  A_SiN ≈ 1.18 at 60 °C; ≈ 1.05 at 250 °C (more boron passivation of
  the nitride surface as BN-like bonds at higher temperature)

  E (eV)    SiN 60 °C   SiN 250 °C   ZrO₂ 250 °C   Selectivity at 250 °C
  ───────────────────────────────────────────────────────────────────────
   40         1.0          0.9          3.6           ≈ 4 (near deposition)
   50         1.9          1.7          5.7           3.4
   70 (D1)    3.4          3.0          9.3           3.1
  100         5.3          4.8          13.8          2.9
  150         8.0          7.1          20.0          2.8

Cold route (Book #32): ZrO₂ 6 / SiN 8 at 150 eV, 60 °C → 0.75
```

Raising the temperature from 60 to 250 °C quadruples the selectivity at the same ion energy class, because it helps the ZrO₂ and not the SiN. Lowering the energy at 250 °C raises it only a little further, until the BₓClᵧ deposition makes the floor non-uniform below about 50 eV.

### 3.5.2 To the Oxide Cap

```
PE-TEOS in D1 (250 °C, 70 eV):  ≈ 2.0 nm/min
  ZrO₂ : SiO₂ ≈ 4.5
  Cap loss over 61 s: ≈ 2 nm of 60 nm
```

SiO₂ etches in BCl₃ by the same boron gettering, with a higher threshold than ZrO₂ at 250 °C because SiCl₄ formation from SiO₂ needs more oxygen removal per silicon. The cap is comfortably sufficient.

### 3.5.3 To the Plate Sidewall

The plate sidewall receives few ions. What attacks it is spontaneous chemistry: Cl atoms on TiN (TiCl₄ is volatile at room temperature), on SiGe (Ge chlorinates readily), and on W.

```
Spontaneous lateral attack in D1 (250 °C, 10% Cl₂, under BₓClᵧ, illustrative):
  TE TiN       1.2 nm/min
  SiGe         1.0 nm/min
  W            0.5 nm/min
```

These are low because BₓClᵧ deposition protects the grazing-incidence surfaces, and because the Cl₂ fraction is kept at 10%. They rise steeply with the Cl₂ fraction (Section 3.3.3). Chapter 11 uses them to compute the plate-edge recess.

---

## 3.6 The Other Oxides in the Stack

```
D1 rates by film (250 °C, 70 eV, illustrative):
  Film                       Rate (nm/min)    Comment
  ─────────────────────────────────────────────────────────────────────
  ZrO₂ amorphous                14            as deposited; lower density
  ZrO₂ tetragonal                9.0          reference periphery majority
  ZrO₂ monoclinic                8.0          ≈ 30% of periphery grains
  Al₂O₃ (insertion)              7.0          AlCl₃ volatile; strong lattice
  HfO₂ monoclinic                7.5          for HfO₂-based variants
  SiOₓNᵧ interlayer              3.5          between oxide and nitride
  PECVD SiN                      3.0          landing film
  PE-TEOS                        2.0          plate cap
```

The 0.3 nm Al₂O₃ insertion etches more slowly than tetragonal ZrO₂ and takes about 2.6 s to clear. Its emission signature, the Al I lines at 394.4 and 396.2 nm, is brief but distinct and marks the middle of the film (Chapter 8).

---

## 3.7 Products in the Gas

```
Product generation in D1 (reference, illustrative):
  Open area: 318 cm²; ZrO₂ rate 9 nm/min = 0.15 nm/s
  Zr removal: 318 × 1.5 × 10⁻⁸ cm/s × 3.0 × 10²² cm⁻³ = 1.4 × 10¹⁷ s⁻¹
  Total gas flow: 150 sccm ≈ 6.7 × 10¹⁹ molecules/s
  ZrCl₄ mole fraction ≈ 2 × 10⁻³ → partial pressure ≈ 2 × 10⁻⁵ Torr at 8 mTorr
  Boron consumed as (BOCl)₃/BOCl: ≈ 2.8 × 10¹⁷ O atoms/s → ≈ 3 × 10¹⁷ B/s
  (≈ 0.5% of the BCl₃ flow)
```

The products are dilute. At a wall temperature of 120 °C, the ZrCl₄ vapor pressure (6 × 10⁻³ Torr) is far above its partial pressure, so ZrCl₄ does not condense as such. It does react with oxygen and moisture adsorbed on the walls to form zirconium oxychloride and oxide deposits, which are what accumulate (Chapter 9).

---

## 3.8 Why Heat Is the Efficient Lever

The dielectric clear can be made faster in two ways: more ion energy or more heat. They are not equivalent:

```
Two ways to reach ≈ 9 nm/min on tetragonal ZrO₂ (illustrative):
                          Cold, high energy        Hot, low energy (D1)
  ───────────────────────────────────────────────────────────────────────
  Wafer temperature        60 °C                    250 °C
  Ion energy               ≈ 200 eV                 70 eV
  ZrO₂ rate                ≈ 8.5 nm/min             9.3 nm/min
  SiN rate                 ≈ 10.2 nm/min            3.0 nm/min
  Selectivity ZrO₂:SiN     0.8                      3.1
  Mask                     resist (≤ 120 °C)        inorganic hard mask
  Sputtered Zr veils       significant              small
  Sidewall attack          ion-driven notching      spontaneous Cl; needs
                                                    BₓClᵧ and low Cl₂
```

Ions break every bond equally; heat helps the reaction whose bottleneck is product desorption. For ZrO₂ in chlorine, that is exactly where the bottleneck is. The price is paid elsewhere: a hard mask, a chamber that lives at 250 °C, and sidewalls that must be protected chemically rather than by the directionality of the ions.

---

## Summary and Key Takeaways

1. **Fluorides of Zr, Hf, and Al are refractory; chlorides are volatile when hot.** ZrCl₄ has 26 Torr of vapor pressure at 250 °C and 10⁻⁵ Torr at 60 °C.

2. **Chlorine alone is uphill; boron makes it downhill.** BCl₃ turns a +120 kJ/mol reaction into −191 kJ/mol. Carbon from resist helps the cold route; the hard-mask route relies on boron alone.

3. **BCl₃ deposits where ions do not clean.** The same BₓClᵧ that stops a cold etch at low energy protects the plate sidewall in a hot etch.

4. **Temperature lowers the threshold and raises the yield.** From 60 to 250 °C, E_th falls from about 60 to 25 eV, and the 70 eV rate goes from net deposition to 9 nm/min.

5. **Selectivity to SiN rises from 0.75 to 3** because heat helps ZrO₂ and not SiN.

6. **The low-energy point is steep.** At 70 eV the rate changes 1.8% per eV and 0.7% per °C; uniformity of ion energy and temperature becomes the key equipment problem.

---

## Study Questions

1. Using the Clausius–Clapeyron relation of Section 3.1.3, find the wafer temperature at which the equilibrium vapor pressure of ZrCl₄ equals 100 times its partial pressure in D1. What does this suggest about the minimum useful chuck temperature?

2. Compute ΔH for HfO₂ + 4/3 BCl₃ → HfCl₄(s) + 2/3 B₂O₃ and for Al₂O₃ + 3 Cl₂ + 3 C → 2 AlCl₃ + 3 CO. Which getter is more effective per oxygen atom?

3. With the model of Section 3.4, find the ion energy at 150 °C that gives the same ZrO₂ rate as D1. What is the selectivity to SiN there?

4. The bias drifts so that the ion energy at the wafer edge is 8 eV below the centre. Compute the edge-to-centre rate ratio in D1 and in the cold route at 150 eV.

5. The Cl₂ fraction is raised from 10% to 30% to shorten the main etch. Using Section 3.3.3, what happens to the clearing time, the SiN loss with a 70% overetch, and the TE TiN lateral recess over the whole step?

6. Estimate the BCl₃ utilization in D1 from Section 3.7. Why is it so low, and where does the rest of the boron go?

---

**Next Chapter:** [Chapter 4: Atomic-Layer, Thermal & Wet Removal of High-k Films](./04-ale-thermal-wet-removal.md)

---

**Chapter 3 Development Status:** Complete  
**Version:** 1.0
