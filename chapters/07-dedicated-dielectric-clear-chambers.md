# Chapter 7: Dedicated Dielectric-Clear Chambers & the Strip-Then-Clear Route

## Overview

Book #32 clears the ZAZ in the same chamber, under the same resist, as the conductors above it. That keeps the module simple and puts every constraint on one step: the resist must survive 93 s of BCl₃/Cl₂ at 150 eV, the TiN must not notch, the veil must not form, and the ZrO₂ grains must clear to a probability of 10⁻¹⁰. This book takes the clear out of the plate recipe. The conductor etch stops on the ZAZ, the resist is stripped, and the plate itself becomes the mask for a hot, low-energy clear in a chamber that is built for nothing else.

This chapter describes that route and its hardware. It lays out the five steps and the chambers that run them, shows that the strip, which exists to remove resist, also sets the TiOₓ shell and the WOₓ top that the clear depends on, derives the ion-energy window of the hot clear from the shell and the tungsten budgets, builds the charging budget of a route in which the plate top is exposed, and ends with the hot-chuck hardware, the transfer, and the post-clear treatment.

**Learning Objectives:**
- Lay out the five steps P1–P5, their chambers, and their times
- Relate strip time to the TiOₓ shell, the WOₓ top, and the tungsten consumed
- Derive the ion-energy window of the hot clear from the shell lifetime and the W budget
- Compare the charging budget of the strip-then-clear route with the integrated route of Book #32
- Specify the hot-chuck chamber, transfer, and post-clear treatment
- List the failure modes of the route and their signatures

---

## 7.1 The Route in One Page

```
Step   Chamber                    Chemistry / action                            Time
────────────────────────────────────────────────────────────────────────────────────────────
P1     ambient ICP, 60 °C         BARC (CF₄/O₂/Ar) → W (SF₆/N₂/Cl₂/Ar) →        107 s
       (as Book #32)              SiGe ME (HBr/Cl₂/O₂) → SiGe OE (HBr/O₂/He)
P2     ambient ICP, 60 °C         BT: BCl₃/Ar, 70 eV, 6 s                        42 s
                                  TiN stop: Cl₂/Ar, 40 eV, 18 s + 100% OE
P3     downstream strip, 250 °C   O₂/N₂ radicals: resist off; TiOₓ shell and     60 s
                                  WOₓ top grown
P4     hot ICP, 250 °C            BCl₃/Cl₂/Ar, 80 eV, plate as mask:             38 s
                                  ZAZ clear 28 s + 35% OE
P5     post-etch treatment        remove BₓClᵧ, Cl; passivate W and TiN edges   30–60 s
────────────────────────────────────────────────────────────────────────────────────────────
Plasma time P1–P4                                                               ≈ 247 s
(Book #32 integrated plate etch, for comparison)                                ≈ 212 s
```

The route takes 35 s more plasma time than the integrated recipe, spread over three chamber types. In return it removes the HK step from the resist budget (resist ends at ≈ 348 nm, then is stripped), removes the veil mechanism (there is no resist wall to coat), and allows the hot chuck that Book #32 reserves for a hard-mask route, without the hard mask.

---

## 7.2 The Strip: Shell and Oxide as By-Products

### 7.2.1 What the Strip Does

After P2 about 348 nm of KrF resist remains (500 − 143 nm through P1, − 9 nm in P2) over a plate whose sides are exposed: W, SiGe, and the TiN edge. A downstream plasma of O₂ and N₂ at 250 °C removes the resist at about 1 µm/min, which clears the 348 nm in 21 s. The step runs 60 s, for three reasons: to remove the sidewall polymer and the BARC remnant at the foot of the 3 µm spaces, to remove carbon from the ZAZ surface, and to grow the shell.

```
Strip (reference, illustrative):
  Plasma          remote (downstream); O₂ 1500 / N₂ 150 sccm; 1 Torr; 250 °C pedestal
  Ions on wafer   none (no bias, remote source): no charging, no sputtering
  Time            60 s
  Results         resist and BARC removed
                  TiN sidewall oxidized to a TiOₓ shell, 1.8 nm
                  W top and sidewall oxidized to WOₓ, 2.5 nm (consumes 0.74 nm of W)
                  SiGe sidewall: passivation of Book #32 (SiOₓBrᵧ) thickened by ≈ 0.3 nm
                  ZAZ: carbon and adsorbed halogens oxidized; stoichiometric surface
```

### 7.2.2 Shell and Oxide Against Strip Time

Oxide growth at these temperatures is parabolic: x² = k t. The reference values are 1.8 nm of TiOₓ and 2.5 nm of WOₓ after 60 s. Then:

```
Strip time (s)   TiOₓ shell   WOₓ     W consumed    P4 W loss   Total W    Budget margin   Shell life   Shell margin
                 (nm)         (nm)    (nm)          (nm)        (nm)       (2.7 nm)        (s)          (× 37.8 s)
──────────────────────────────────────────────────────────────────────────────────────────────────────────────────
   42             1.51         2.09     0.62          1.51        2.13       +0.57           45           1.20
   50             1.64         2.28     0.67          1.51        2.18       +0.52           49           1.30
   60 (ref)       1.80         2.50     0.74          1.51        2.25       +0.45           54           1.43
   75             2.01         2.80     0.82          1.51        2.33       +0.37           60           1.60
   90             2.20         3.06     0.90          1.51        2.41       +0.29           66           1.75
```

A longer strip thickens the shell and protects the TiN edge for longer, at the price of tungsten. The two limits leave a wide window. A shell margin of 1.3× is reached at 50 s, which sets the lower edge; the upper edge is the tungsten budget, whose margin shrinks by about 0.08 nm for every 10 s of strip and is still 0.29 nm at 90 s. The reference of 60 s sits at a shell margin of 1.43 and keeps 0.45 nm of tungsten budget in hand.

### 7.2.3 What the Strip Does Not Do

It does not remove the sidewall passivation of the SiGe, whose SiOₓBrᵧ is not volatile in oxygen. It does not remove zirconium from the ZAZ surface, but there is none to remove: nothing has yet sputtered the ZAZ. It also does not reach into the plate: with no ions there is no line of sight, and the 150 nm SiGe is protected at its sidewall by an oxide that will be removed or buried at P5.

---

## 7.3 The Hot Clear

### 7.3.1 The Recipe

```
P4, hot clear (reference; hot recipe of Book #32, Chapter 7):
  Chamber       ICP, heated AlN chuck 250 ± 3 °C, liner 150–180 °C
  Gas           BCl₃ 80 / Cl₂ 20 / Ar 50 sccm;  5 mTorr
  Power         800 W source; bias 200 W (peak ion energy ≈ 80 eV), pulsed 10 kHz, 50% duty
  Rates         ZrO₂ 12, Al₂O₃ 9, SiN 4, SiO₂ 2 nm/min; W 2.4 nm/min; TiOₓ shell 2.0 nm/min
  Time          clear 28 s (5.2/12 + 0.3/9 = 0.467 min);  35% overetch → 38 s
  SiN loss      (38 − 28) s × 4 nm/min = 0.65 nm
  W loss        2.4 nm/min × 38 s = 1.5 nm
```

Wafer heat-up on the hot chuck is quick: a silicon wafer of 0.7 J/(g·K) × 128 g = 90 J/K, coupled through He backside gas at 0.1 W/(cm²·K) over 707 cm², has τ = 1.3 s and reaches 250 °C in about 5 s. The chuck is never cooled; the plasma starts when the wafer is within 5 °C.

### 7.3.2 The Ion-Energy Window

Three films limit the energy. The ZrO₂ rate sets the step time; the shell sets the maximum step time; and the W rate sets the loss per second. With the yield model of Chapter 3 (E_th = 25 eV for ZrO₂ at 250 °C, 30 eV for SiN, 40 eV for W; each calibrated at 80 eV to the rates above):

```
E (eV)   ZrO₂    SiN    W     ZrO₂:SiN  ZrO₂:W   Clear   Step    SiN loss   W loss   Total W   Shell margin
         nm/min  nm/min nm/min                    (s)     +35%    (nm)       (nm)     (nm)      (54 s / step)
─────────────────────────────────────────────────────────────────────────────────────────────────────────────
 50       6.3    1.8    0.7    3.4       9.2     53.3     72.0    0.57       0.82     1.56      0.75  ✗
 65       9.3    3.0    1.6    3.1       5.9     36.1     48.7    0.63       1.29     2.03      1.11
 73      10.8    3.5    2.0    3.0       5.3     31.2     42.1    0.64       1.43     2.17      1.28
 80 ref  12.0    4.0    2.4    3.0       5.0     28.0     37.8    0.65       1.51     2.25      1.43
100      15.2    5.2    3.4    2.9       4.5     22.1     29.8    0.67       1.67     2.41      1.81
120      18.1    6.3    4.2    2.9       4.3     18.5     25.0    0.68       1.77     2.51      2.16
150      22.0    7.8    5.4    2.8       4.1     15.2     20.6    0.69       1.86     2.60      2.62
```

(The Al₂O₃ rate is taken as 0.75 of the ZrO₂ rate, matching 9 against 12 nm/min.) The nitride loss is nearly constant, because a higher SiN rate is offset by a shorter overetch, and the tungsten loss rises only slowly with energy, because the step also shortens. The binding limit is the shell: a margin of 1.3× requires a step of 41.5 s or less, hence a clearing time of 30.8 s or less, hence a peak ion energy of at least **74 eV**. The reference of 80 eV is 6 eV above it. The upper limit is not in this table; it is the ion damage and the edge-notching of Chapters 11 and 12, which set it near 100–120 eV. The usable window is therefore about 74–110 eV, and bias pulsing and a tailored waveform keep the ion distribution inside it (Section 7.5.2).

---

## 7.4 Charging With the Plate Exposed

### 7.4.1 The Island as an Antenna

In Book #32 the resist covers the plate top through the whole of the high-k step, and after the islands separate their antenna is only their sidewall (ratio 1.4 × 10⁻³). In the strip-then-clear route the W top is bare during P4. Each island, isolated from its neighbours since P2, collects plasma current on its top:

```
Island top area        1.1 mm × 1.2 mm = 1.32 × 10⁻² cm²
Island dielectric      5.4 × 10⁸ cells × 1.24 × 10⁻⁹ cm² = 0.667 cm²
Antenna ratio          0.0132 / 0.667 = 0.0198      (vs 1.4 × 10⁻³ in Book #32's phase C)

Net plasma imbalance current density (Book #32): 0.5 mA/cm²
  I = 0.5 mA/cm² × 0.0132 cm² = 6.6 µA
  J through the dielectric = 6.6 µA / 0.667 cm² = 9.9 × 10⁻⁶ A/cm²
  J / J₁ = 9.9×10⁻⁶ / 8×10⁻⁷ = 12.4 → ΔV above 1.0 V = 0.12 × ln 12.4 = 0.30 V
  Clamp voltage                                      1.30 V
```

The dielectric clamps the island at 1.30 V (negative-plate polarity is the dangerous one; Book #32, Chapter 13), the same figure as the wafer-continuous phase A of the integrated route, but reached by a different circuit.

### 7.4.2 The Charge Budget

```
Phase                          Duration   J (A/cm²)    Q (C/cm²)   Notes
─────────────────────────────────────────────────────────────────────────────────────────────
R0 (Book #32)
  A: wafer-continuous           ≈ 100 s    ≈ 1 × 10⁻⁵   1.0 × 10⁻³
  B: separation                 ≈ 1–2 s    brief 1.6–1.8 V, bank-level
  C: isolated, resist-covered   ≈ 85 s     ≪             ≈ 0
  Total                                                  ≈ 1.0 × 10⁻³
R1 (this book)
  A: P1 + P2 TiN clear          ≈ 131 s    ≈ 1 × 10⁻⁵   1.3 × 10⁻³
  B: separation in P2           ≈ 2.8 s    brief 1.6–1.8 V; at 40 eV and lower flux
  P4: top exposed               38 s       9.9 × 10⁻⁶   3.8 × 10⁻⁴
  Total                                                  ≈ 1.7 × 10⁻³
  Pulsed P4 (J × 0.5)           38 s                    1.9 × 10⁻⁴  → total 1.5 × 10⁻³
  Q / Q_bd (0.5–5 C/cm²)                                 0.03–0.3%
```

The route injects about 1.7 times the charge of the integrated route (1.5 times with pulsing), at a Q/Q_bd of 0.03–0.3%. Breakdown is not a risk; stress-induced leakage is, and the specification (cell leakage within 10% of the unetched reference) must be demonstrated on antenna and polarity structures (Chapter 12). The separation in P2 lasts 2.8 s because the TiN clearing time spreads by ± 7.8% about 18.2 s (± 1.4 s); it occurs at 40 eV and a lower ion flux than Book #32's 150 eV, which compensates for its length.

### 7.4.3 Mitigations

```
Lever                                   Effect in P4
──────────────────────────────────────────────────────────────────────────
Bias pulsing, 50% duty                  J × 0.5; clamp 1.30 → 1.22 V
Leave a cap on the W (5 nm SiN)         antenna → sidewall only; costs a deposition
Lower source power in the last seconds  smaller imbalance current
Short step (higher E, within window)    less time at stress: 25 s at 120 eV
Polarity check (n⁺/p and p⁺/n arrays)   confirms the mechanism
```

The cap is the clean fix and is a route of its own: it is Book #32's oxide hard mask, kept in place of the resist.

---

## 7.5 Hot-Chuck Hardware

### 7.5.1 Chuck, Walls, and Delivery

```
P4 chamber (reference):
  Chuck        AlN, Coulombic; embedded 2–3 zone heater; 250 ± 2 °C with plasma; He backside
               10 Torr; thermal break to the cooled base (Book #32, Chapter 7)
  Liner        150–180 °C; window ≥ 120 °C; lid 120 °C
  BCl₃         heated cylinder (25–30 °C); lines warmer than the cylinder; < 1 ppm H₂O
  Exhaust      heated foreline (≈ 150 °C) to the abatement, to keep AlCl₃ and ZrCl₄ gaseous
  Cleaning     WAC chlorine first, never fluorine first (Book #32; Chapter 9)
```

With no resist in the chamber the deposits are cleaner than in an integrated plate chamber: no carbon, no CₓFᵧ. The wall carries BₓClᵧ, ZrClₓ, AlClₓ, and a little WOₓClᵧ from the exposed W top. The wall loading per wafer is the same as Book #32's HK step; the chamber is cleaned on the same schedule.

### 7.5.2 Ion-Energy Control

```
Window 74–110 eV; reference 80 eV peak; target distribution: FWHM ≤ 15 eV
  Pulsed bias, 10 kHz, 50% duty: narrows the distribution, halves the charging
  Tailored waveform: flattens the distribution; removes the high-energy tail that
  reaches W and the low-energy tail below 74 eV that lets the shell win
```

The ion-energy distribution function matters more here than in the integrated route: a 20% low-energy tail below 65 eV slows the clear locally (the shell clock runs on average step time, not on the fastest ions); a high-energy tail raises the W and SiN loss and the damage depth.

---

## 7.6 Transfer, Queue, and Post-Clear Treatment

### 7.6.1 Vacuum Between Strip and Clear

The strip leaves a clean, oxygen-terminated ZAZ surface and a plate with a TiOₓ shell and a WOₓ top. Exposure to air adds water to the ZAZ and to the oxides. In the hot BCl₃ step, water forms boric acid and HCl locally (Book #32, Chapter 7). The reference holds the strip and the clear on one mainframe with vacuum transfer; where they must be separated, the queue limit between P3 and P4 is 1 h (illustrative) and the P4 chamber runs a short H₂ or Ar pre-treatment at 250 °C to desorb water.

### 7.6.2 Post-Clear Treatment (P5)

After P4 the surfaces carry BₓClᵧ, chlorine on the ZAZ-free SiN, and chlorine at the exposed ends of the W and TiN edges:

```
P5 (reference, illustrative):
  Downstream H₂O/O₂ plasma, 250 °C, 30 s: converts BₓClᵧ to B₂O₃, desorbs HCl
  DI water rinse (spin), 30 s: dissolves B₂O₃ (soluble); megasonic to dislodge particles
  Anneal / dry: 200 °C, 60 s, N₂
Targets:  Cl on SiN ≤ 2 at%;  B ≤ 1 at%;  W corrosion: none at 24 h queue
```

The corrosion rule of Book #32 (Chapter 11) applies unchanged: chlorine at a W edge plus moisture is HCl, and W corrodes in it. The route puts the plasma step ahead of the water rinse, in that order, in a vacuum-integrated sequence.

---

## 7.7 Failure Modes

```
Symptom                             Likely cause                          Chapter
──────────────────────────────────────────────────────────────────────────────────────────────
TiN notch > 15 nm                   shell breached (strip short, step      4, 7.2
                                    long, E low, wall temp drift)
W thin; plate R_s > 4 Ω/□           strip long; WOₓ thick; E high          4.4, 7.2
Zr residue on the periphery         step short; E < 74 eV; chuck cold;     4, 10
                                    ZrF₄ skin not converted
Resist left on the plate edge       strip short; BARC residue at foot      7.2
Cell leakage tail in banks          phase B; P4 charging; polarity         7.4, 12
Particles after P4                  cold foreline; B₂O₃; wall flakes       9
Haze on the SiN                     BₓClᵧ not removed (P5 skipped)         7.6
```

---

## Summary and Key Takeaways

1. **Five steps, three chamber types.** Ambient ICP for P1 and P2 (149 s), a downstream strip for P3 (60 s), and a hot ICP for P4 (38 s): 247 s against 212 s for the integrated recipe.

2. **The strip sets the shell.** TiOₓ 1.8 nm and WOₓ 2.5 nm after 60 s (parabolic in time); 50–90 s keeps the shell margin at 1.3–1.75 with the tungsten inside its 2.7 nm budget.

3. **The shell binds the hot clear's energy.** A margin of 1.3× requires E ≥ 74 eV; the reference of 80 eV sits 6 eV above it and the damage limits cap it near 110 eV.

4. **W loss is 2.25 nm of a 2.7 nm budget.** 0.74 nm from the strip and 1.51 nm from the clear; it varies only weakly with ion energy.

5. **Exposed W raises the charge by 1.7×.** The island antenna ratio is 0.0198; the clamp is 1.30 V and the charge in P4 is 3.8 × 10⁻⁴ C/cm² (1.9 × 10⁻⁴ with pulsing); a 5 nm cap removes it.

6. **Keep the route in vacuum.** Water between the strip and the clear makes boric acid and HCl; chlorine at the W edge corrodes it.

---

## Study Questions

1. A lot's strip runs 70 s instead of 60 s. Compute the shell, WOₓ, W consumed, total W loss, and shell margin with P4 at 80 eV.

2. Using the window table, find the ion energy at which the total W loss reaches 2.7 nm if the strip is 90 s (W consumed 0.90 nm). Is the answer inside the usable window?

3. The product's plate island is 1.4 × 1.4 mm (island dielectric 0.9 cm²). Recompute the antenna ratio, the clamp voltage, and the P4 charge for the unpulsed hot clear.

4. A 5 nm SiN cap is left on the W top in place of the resist. Which of Sections 7.2–7.4 change? What does the cap do to the W budget, to the shell, and to the charge?

5. P4 runs at 250 °C and the chuck heater drifts to 235 °C. The ZrO₂ rate falls roughly in proportion to exp(−E_a/kT) with E_a = 0.25 eV. Compute the rate, the step time at fixed overetch, and the shell margin.

6. Compare R0 and R1 on resist budget, SiN loss, W loss, TiN notch, charge, and plasma time. For which product constraints would you choose each?

---

**Next Chapter:** [Chapter 8: In-Situ Monitoring & Etch-Amount Control for a 5 nm Film](./08-insitu-monitoring-thin-dielectric.md)

---

**Chapter 7 Development Status:** Complete  
**Version:** 1.0
