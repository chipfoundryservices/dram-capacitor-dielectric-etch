# Chapter 3: Halide Plasma Chemistry of High-k Oxides

## Overview

ZrO₂, HfO₂, and Al₂O₃ were chosen for the capacitor because they are among the most stable oxides that can be deposited at 300 °C. The same stability makes them some of the hardest films in the fab to etch. Their metal–oxygen bonds are as strong as Si–O. Their fluorides, the product of almost every other dielectric etch, are solids up to several hundred degrees. Their chlorides are volatile only with help, and chlorinating them at all is uphill unless something else takes the oxygen.

Book #32 (Chapter 4) introduced the BCl₃ chemistry that the plate etch uses to remove the ZAZ. This chapter develops it further, because in this book it is the main subject: the thermochemistry of every metal that appears in DRAM capacitor dielectrics, the competition between etching and boron-chlorine deposition that defines the useful ion-energy range, the reason a continuous ion-assisted etch of a crystalline film creates its own residue tail, the selectivities the three modules depend on, and the alternatives to BCl₃.

**Learning Objectives:**
- Compute reaction enthalpies for chlorination of ZrO₂, HfO₂, Al₂O₃, TiO₂, and SrO with Cl₂, BCl₃, and carbon-assisted chlorine
- Use a two-parameter model of net etch rate to locate the etch–deposition transition and its sensitivity to ion energy
- Explain why the grain-to-grain spread of a continuous etch grows with the thickness removed and with proximity to threshold
- State the selectivities of the BCl₃ main step and the Cl₂ TiN-clear step to the films each meets
- Identify the residues the chemistry leaves and the steps that remove them

---

## 3.1 Bonds and Volatility

### 3.1.1 Bond Strength

```
Diatomic M–O bond dissociation energy (kJ/mol, illustrative):
  B–O     806        ← the oxygen getter
  Hf–O    802
  Si–O    798
  La–O    798
  Zr–O    766
  Y–O     715
  Ti–O    672
  Al–O    512        (but Al₂O₃ lattice energy is very high)
  Sr–O    426
  C–O    1077        ← CO is stronger still (Section 3.8)
```

### 3.1.2 Volatility of Halides

```
Halide            Temperature for ≈ 1 Torr vapour     Normal sublimation /
                  pressure (°C, approximate)           boiling point (°C)
───────────────────────────────────────────────────────────────────────────
TiCl₄             −14                                  136 (bp)
BCl₃              −91                                  12.5 (bp)
(BOCl)₃           ≈ 20                                 —
AlCl₃ (Al₂Cl₆)    ≈ 100                                180 (subl.)
ZrCl₄             ≈ 190                                331 (subl.)
HfCl₄             ≈ 190                                317 (subl.)
ZrBr₄             ≈ 210                                357 (subl.)
TiF₄              ≈ 200                                284 (subl.)
ZrF₄, HfF₄        ≈ 600                                ≈ 900 (subl.)
AlF₃              ≈ 1000                               1290 (subl.)
LaCl₃, YCl₃       > 700                                > 1400 (bp)
SrCl₂             > 1000                               1250 (bp)
```

Three groups follow from the table:

- **Volatile without help:** Ti chlorides and fluorides, B chlorides. TiO₂ and TiN etch easily.
- **Volatile with heat or ions:** Zr, Hf, and Al chlorides. At a 60 °C wafer, ZrCl₄ has a vapour pressure of order 10⁻⁵ Torr; it leaves only when ions knock it off or the surface is heated.
- **Not volatile in any plasma etch:** every fluoride of the high-k metals, and the chlorides of Sr, La, and Y. These must be sputtered, or removed by wet chemistry, or converted to something else.

A fluorocarbon plasma that reaches ZrO₂ forms a ZrF₄ skin and stops. That is why the periphery contacts of Chapter 1 stop on ZrO₂ residue, and why the dielectric etches of this book use chlorine.

---

## 3.2 Thermochemistry

### 3.2.1 Formation Enthalpies Used in This Book

```
Species        ΔH_f (kJ/mol, 298 K)      Species        ΔH_f (kJ/mol, 298 K)
──────────────────────────────────────────────────────────────────────────────
ZrO₂(s)        −1100.6                    ZrCl₄(s)       −980.5
HfO₂(s)        −1144.7                    HfCl₄(s)       −990.4
Al₂O₃(s)       −1675.7                    AlCl₃(s)       −704.2
TiO₂(s)        −944.0                     TiCl₄(g)       −763.2
SrO(s)         −592.0                     SrCl₂(s)       −828.9
BCl₃(g)        −403.8                     B₂O₃(s)        −1273.5
CO(g)          −110.5                     CO₂(g)         −393.5
```

### 3.2.2 Chlorine Alone, BCl₃, and Carbon

```
Reaction                                                     ΔH (kJ/mol oxide)
──────────────────────────────────────────────────────────────────────────────
ZrO₂ + 2 Cl₂        → ZrCl₄ + O₂                              +120
ZrO₂ + 4/3 BCl₃     → ZrCl₄ + 2/3 B₂O₃                        −191
ZrO₂ + 2 Cl₂ + 2 C  → ZrCl₄ + 2 CO                            −101
ZrO₂ + 2 Cl₂ + 2 CO → ZrCl₄ + 2 CO₂                           −446

HfO₂ + 2 Cl₂        → HfCl₄ + O₂                              +154
HfO₂ + 4/3 BCl₃     → HfCl₄ + 2/3 B₂O₃                        −156

Al₂O₃ + 3 Cl₂       → 2 AlCl₃ + 3/2 O₂                        +267
Al₂O₃ + 2 BCl₃      → 2 AlCl₃ + B₂O₃                          −198

TiO₂ + 2 Cl₂        → TiCl₄(g) + O₂                           +181
TiO₂ + 4/3 BCl₃     → TiCl₄(g) + 2/3 B₂O₃                     −130

SrO + Cl₂           → SrCl₂ + ½ O₂                            −237
```

Chlorine alone cannot chlorinate the high-k oxides; something must take the oxygen. Boron does it, because the B–O bond is the strongest in the table apart from C–O. Carbon does it too: the carbochlorination of zircon with chlorine and coke is how the industry makes ZrCl₄ from ore. Strontium is the odd case: its chlorination is downhill, but the product cannot leave.

### 3.2.3 Where the Boron Goes

The B₂O₃ in these equations does not stay. In a chlorine-rich plasma the boron leaves as boron oxychlorides, chiefly the trimer (BOCl)₃, which is volatile near room temperature, and as BCl₃ re-formed at the surface; BCl₂⁺ and Ar⁺ ions sputter what is left. Where the ion flux is too low to keep up, the boron stays as a BOₓClᵧ film. That film is the deposition half of the competition in Section 3.3.

---

## 3.3 Etch Versus Deposition in BCl₃

### 3.3.1 The Plasma

```
BCl₃/Cl₂/Ar ICP (reference main step, illustrative):
  BCl₃ 80 / Cl₂ 20 / Ar 50 sccm, 5 mTorr, 800 W source, ESC 60 °C
  n_e ≈ 1 × 10¹¹ cm⁻³, T_e ≈ 3.5 eV
  Ions: BCl₂⁺ (≈ 50%), Cl⁺ and Cl₂⁺ (≈ 30%), Ar⁺ (≈ 15%), BCl⁺
  Ion flux to the wafer: Γ_i ≈ 1.5 × 10¹⁶ cm⁻² s⁻¹
  Neutrals: Cl, BCl₂, BCl, Cl₂, undissociated BCl₃
```

### 3.3.2 A Two-Parameter Model

The surface sees two processes at once: ion-assisted removal of a chlorinated, borated layer, which grows with ion energy above a threshold; and deposition of BₓClᵧ and BOₓClᵧ from the radicals, which does not depend on ion energy:

```
R_net(E) = A (√E − √E_th) − D

  E_th  ≈ 30 eV       threshold for removing the chlorinated layer
  A     ≈ 1.33 nm/min/√eV   (tetragonal ZrO₂, reference flux)
  D     ≈ 3 nm/min    deposition (ZrO₂-thickness equivalent)

  Net-zero point:  √E₀ = √E_th + D/A  →  E₀ ≈ 60 eV
```

```
Ion energy (eV)   Gross removal   Net rate (nm/min)   Surface
──────────────────────────────────────────────────────────────────────────────
   40               1.1            −1.9               BₓClᵧ film grows
   60               3.0             0.0               transition E₀
   70               3.8             0.8               marginal; non-uniform
   90               5.3             2.3               bevel regime (Chapter 7)
  100               6.0             3.0
  150               9.0             6.0               reference main step
  250              13.7            10.7               SiN and resist loss high
```

The model reproduces the rates of Book #32's high-k step and adds one thing that the simpler threshold picture hides: **sensitivity**. Near the transition, a small change of ion energy is a large relative change of rate:

```
d(ln R_net)/dE = A / (2 √E R_net)

  At 150 eV:  1.33 / (2 × 12.25 × 6.0)  = 0.9% per eV
  At  90 eV:  1.33 / (2 × 9.49 × 2.3)   = 3.0% per eV
  At  70 eV:  1.33 / (2 × 8.37 × 0.84)  = 9.5% per eV
```

A 5 eV sag in ion energy at the wafer edge costs 5% of the rate at 150 eV, 15% at 90 eV, and half the rate at 70 eV. The main step of module 2 sits at 150 eV for this reason. The bevel etch of module 1 cannot (Chapter 7) and pays for it in uniformity.

### 3.3.3 The Cl₂ Fraction

```
Halogen gas = BCl₃ + Cl₂; effect of the Cl₂ fraction at 150 eV (illustrative):

  Cl₂ fraction   D (nm/min)   A (relative)   Net ZrO₂ rate   Note
  ─────────────────────────────────────────────────────────────────────────
     0%            4.5          0.95            4.1          heavy BₓClᵧ;
                                                             micromasking risk
    20% (ref.)     3.0          1.00            6.0
    40%            1.8          0.85            5.9          less O gettering
    70%            0.8          0.55            4.2          surface stays
                                                             oxygen-rich
   100%            0            0.15            1.3          Cl₂ alone
```

More Cl₂ suppresses deposition but removes the boron that makes chlorination downhill. The optimum is broad, between 15 and 40% Cl₂.

### 3.3.4 Temperature

Heating the wafer helps three times: the chlorinated layer desorbs more easily (E_th falls), the chlorides leave faster once formed (A rises), and the BₓClᵧ film desorbs too (D falls):

```
Tetragonal ZrO₂, reference gases (illustrative):

  Wafer T (°C)   E_th (eV)   A (nm/min/√eV)   D (nm/min)   E₀ (eV)   Net at 150 eV
  ─────────────────────────────────────────────────────────────────────────────────
     60             30           1.33            3.0          60           6
    150             20           1.74            1.5          28          12
    250             12           2.33            0.5          14          20
```

At 250 °C, the transition falls to about 14 eV and the etch is nearly spontaneous; the main step could run at 60–80 eV with ZrO₂:SiN above 2. The price is a hard mask, because resist does not survive (Book #32, Chapter 7). Chapter 6 uses the same numbers to set chuck uniformity requirements at 60 °C.

---

## 3.4 The Spread a Continuous Etch Creates

### 3.4.1 Why Grains Etch at Different Rates

In a crystallized film, the local etch rate is not the same everywhere:

- **Orientation.** The density of surface oxygen, the chlorination depth, and the sputtering yield all depend on which crystal face is exposed. Tetragonal ZrO₂ grains present a different face in every grain.
- **Grain boundaries.** Boundaries are less dense and oxygen-deficient; they chlorinate faster and etch about 30% faster.
- **Composition.** Al from the insertion layer is not evenly distributed; Al-rich grains etch slightly slower in the main step.
- **Local ion energy.** The surface is rough on a 0.3 nm scale; protrusions see slightly more ion flux.

The combined effect, measured by the scatter of clearing times on a grain scale, is a relative rate spread σ_r:

```
Grain-to-grain relative rate spread σ_r, tetragonal ZrO₂ (illustrative):

  Ion energy (eV)    60 °C       250 °C
  ─────────────────────────────────────
       70            20%         5%
      100            10%         4%
      150 (ref.)     7.5%        3.5%
      250             6%         3%
```

The spread grows as the ion energy approaches the transition, for the same reason the sensitivity in Section 3.3.2 does: each grain's local threshold differs a little, and near threshold that difference is a large share of the rate. Heating flattens it, because the etch becomes more chemical and less dependent on the local details of ion-assisted removal.

### 3.4.2 Spread Grows With the Thickness Removed

If the film had a perfectly uniform thickness and the etch a grain-to-grain rate spread σ_r, the remaining thickness after removing x nm would have a spread σ_r·x. The film also starts with a small grain-scale thickness variation σ_t from deposition:

```
σ_rem(x) = √((σ_r x)² + σ_t²)

Reference (150 eV, 60 °C): σ_r = 7.5%, σ_t = 0.12 nm

  Removed x (nm)    σ_rem (nm)
  ──────────────────────────────
     0                0.12
     2.0              0.19
     4.4              0.35       ← end of the module 2 main step
     5.5              0.43       ← full clearing (≈ 8% of 5.5 nm, as in
                                    Book #32's σ_g)
```

This is the most important result of the chapter for module 2. **The continuous step makes the tail of the remaining-thickness distribution as it goes.** The longer it runs, the wider the tail it leaves for whatever comes next. An ALE finish removes material uniformly, grain by grain, but it does not narrow that distribution: it must remove the whole tail (Chapter 10). Heating, or a lower σ_r for any other reason, narrows it at the source.

---

## 3.5 Selectivity

### 3.5.1 In the Main Step

```
Reference main step, 150 eV, 60 °C (illustrative):

  Film                               Rate (nm/min)    vs tetragonal ZrO₂
  ──────────────────────────────────────────────────────────────────────
  ZrO₂, amorphous                       9               1.5
  ZrO₂, tetragonal                      6               1
  Al₂O₃ (insertion; as thin film)       5               0.83
  HfO₂, monoclinic                      5               0.83
  TiN (top electrode)                  50               8.3
  PECVD SiN (periphery top)             8               1.3
  PE-TEOS SiO₂                          5               0.83
  KrF resist                           50               8.3
  SiGe:B (plate sidewall)              ≈ 60             10
  W (plate top, under resist)           —               (masked)
```

The selectivity to SiN is below 1: ZrO₂:SiN = 0.75. With a continuous overetch, every second costs 0.13 nm of SiN. This is why module 2 stops its main step before the film clears anywhere on the wafer and finishes with ALE, whose SiN loss per cycle is much smaller (Chapter 4).

### 3.5.2 Why SiN Etches in BCl₃

Boron getters oxygen far better than nitrogen. On SiN, chlorine and ions remove silicon as SiClₓ, and nitrogen leaves as N₂ and NCl; boron deposits as BNₓClᵧ and is sputtered. The SiN surface after the step carries boron at a few atomic percent and chlorine at 2–5 at% (Section 3.7).

### 3.5.3 The Plate Sidewall

The plate sidewall exposes SiGe and W to the main step. Under the reference conditions, the sidewall is protected by the passivation from Book #32's SiGe steps (an SiOₓBrᵧ layer) and by the near-normal incidence of the ions. Lateral SiGe loss during the 45 s main step is under 1 nm. During a long continuous overetch it grows, and the TE TiN, which etches eight times faster than the ZAZ, is the first to notch (Chapter 11).

---

## 3.6 The TiN-Clear Step

Module 2 begins after Book #32's SiGe soft-landing step has stopped on the TE TiN. A short chlorine step removes the 5 nm TiN and lands on the ZAZ:

```
TiN clear (reference):
  Cl₂ 60 / Ar 60 sccm, 6 mTorr, 600 W source, E ≈ 60 eV, ESC 60 °C
  TiN rate                         ≈ 40 nm/min (no breakthrough needed: the
                                   TE surface never saw air, because the
                                   SiGe was deposited on it)
  ZrO₂ rate                        ≈ 0.5 nm/min (Cl₂ alone at 60 eV;
                                   compare Section 3.3.3)
  Selectivity TiN:ZrO₂             ≈ 80
  Time                             7.5 s nominal + 2.5 s overetch = 10 s
  ZrO₂ consumed                    ≤ 0.1 nm
```

The step has three purposes. It removes the TiN cleanly, so that the main step starts on ZrO₂ everywhere at the same moment. It gives a clean optical transition (Ti emission falls) from which the main step is timed (Chapter 8). And it uses no BCl₃, so the TE TiN at the plate edge is not attacked by the boron-assisted chemistry longer than necessary.

---

## 3.7 Residues and Surface Products

```
Residues after the main step and ALE finish (illustrative):

  Residue                    Where                    Amount             Removed by
  ──────────────────────────────────────────────────────────────────────────────────
  BOₓClᵧ / BNₓClᵧ            periphery SiN            ≈ 3 × 10¹⁴ B/cm²   O₂/H₂O strip
                                                                         and treatment
                                                                         (→ ≤ 5 × 10¹³)
  Cl in the SiN surface      periphery SiN            2–5 at%, top 1 nm  treatment; H₂O
  Cl, B at the ZAZ edge      plate edge               3–8 at% Cl near    treatment
                                                      the edge (Ch. 11)
  ZrClₓ redeposit            resist and plate         a few Zr atoms per resist strip;
                             sidewall                 nm² of sidewall    otherwise a veil
  Zr, Al, B on the wall      chamber                  ≈ 1 mg ZrO₂-equiv. WAC (Chapter 9)
                                                      per wafer leaves
                                                      the wafer
```

BOₓClᵧ is hygroscopic. Left in air, it takes up water and becomes boric acid and HCl; the HCl corrodes the TE TiN and W at the plate edge, and the boric acid forms a haze. The strip and treatment that follow module 2 are therefore part of the dielectric etch, not an afterthought.

The ZrClₓ veil deserves care. During the main step, sputtered ZrClₓ condenses on the nearest cold surface, which is the resist sidewall at the plate edge. When the resist is stripped, a thin zirconium-rich wall can be left standing along the plate edge. Short main steps and low ion energy in the finish reduce it (Chapter 10, Section 10.6).

---

## 3.8 Alternatives to BCl₃

```
Chemistry          O-getter      Advantages                  Problems
──────────────────────────────────────────────────────────────────────────────────────
BCl₃/Cl₂/Ar        B             fast; clean products;       BₓClᵧ deposition below
(reference)                      well understood             E₀; B residue; moisture
CO/Cl₂, CH₄/Cl₂    C             very exothermic; no boron   carbon polymer;
(carbochlorination)                                          micromasking; resist-like
                                                             films on SiN
SiCl₄/Cl₂          Si            no boron                    SiO₂ product deposits;
                                                             etch stops
HBr/Cl₂/BCl₃       B             bromides reduce resist      ZrBr₄ no more volatile than
                                 erosion                     ZrCl₄; little benefit
Pure Ar sputter    —             no chemistry, no residue    ZrO₂ yield ≈ 0.05 at 300 eV;
                                                             redeposition; SiN loss
```

BCl₃ remains the production choice because its products are volatile, its deposition is removable, and its boron residue is understood. The carbon routes are thermodynamically attractive and appear in research; they trade boron residue for carbon residue, which is harder to remove from SiN without oxidizing the plate.

---

## Summary and Key Takeaways

1. **Oxygen must be taken.** Chlorination of ZrO₂, HfO₂, Al₂O₃, and TiO₂ is uphill with Cl₂ alone and downhill with BCl₃ or carbon. Sr, La, and Y chlorides are non-volatile whatever takes the oxygen.

2. **The transition is near 60 eV.** R_net = A(√E − √E_th) − D with E_th ≈ 30 eV and D ≈ 3 nm/min puts the net-zero point at E₀ ≈ 60 eV at 60 °C.

3. **Sensitivity rises near the transition.** 0.9% per eV at 150 eV, 3% at 90 eV, about 10% at 70 eV. The main step runs at 150 eV; the bevel cannot.

4. **A continuous etch makes its own tail.** σ_rem = √((σ_r x)² + σ_t²): 0.35 nm after 4.4 nm removed at 150 eV. Lower energy widens σ_r; heat narrows it.

5. **ZrO₂:SiN is below 1.** Every second of continuous overetch costs 0.13 nm of SiN, which is why the finish is not a continuous overetch.

6. **Residues are part of the process.** Boron and chlorine on SiN and at the ZAZ edge must be removed by the strip and treatment before air does it badly.

---

## Study Questions

1. Compute ΔH for Al₂O₃ + 3 CO + 3 Cl₂ → 2 AlCl₃ + 3 CO₂ from the table in Section 3.2.1. Why is this reaction not used in production despite its driving force?

2. Using the model of Section 3.3.2, compute the net ZrO₂ rate at 120 eV and the sensitivity in % per eV. If the edge ion energy is 8 eV lower than the centre, what is the edge-to-centre rate ratio at 120 eV and at 90 eV?

3. At 150 °C, E_th = 20 eV, A = 1.74 nm/min/√eV, and D = 1.5 nm/min. Find E₀ and the net rate at 100 eV and compare it with the 60 °C rate at 150 eV. How much of the gain comes from the change in A, and how much from E_th and D?

4. Using σ_r = 10% at 100 eV, compute σ_rem after removing 4.4 nm. By how much does this widen the tail compared with the 150 eV reference? What does this imply for running the main step at lower energy to protect the plate edge?

5. During a 31 s continuous overetch at 150 eV, how much SiN is removed? How much TE TiN would be removed laterally at the plate edge if the TiN were exposed at the same rate as on a flat surface? Why is the real lateral TiN loss smaller?

6. A process engineer proposes HBr/BCl₃ to reduce resist erosion. Using the volatility table, explain why the ZrO₂ rate would not improve, and what else would have to change for the proposal to make sense.

---

**Next Chapter:** [Chapter 4: Atomic-Layer & Thermal Etching of High-k](./04-atomic-layer-thermal-etching.md)

---

**Chapter 3 Development Status:** Complete  
**Version:** 1.0
