# Chapter 4: Atomic-Layer & Thermal Etching of High-k

## Overview

A continuous etch does two things at once: it modifies the surface and it removes the modified layer. When both happen together, the rate depends on every local detail that affects either, and the spread of rates becomes the spread of what is left (Chapter 3, Section 3.4). **Atomic-layer etching** (ALE) separates them in time. In one step, the surface is modified, and the modification stops by itself after about one monolayer. In the next step, the modified layer is removed, and the removal stops by itself when the modified layer is gone. Each cycle removes a fixed amount, set by surface chemistry rather than by flux.

Two kinds of ALE appear in this book. **Plasma ALE**, with a BCl₃ dose and an Ar⁺ removal step, is the finish of module 2: it removes the last nanometres of ZAZ from the periphery with very little SiN loss. **Thermal ALE**, with HF fluorination and ligand exchange by dimethylaluminium chloride (DMAC), is the trim of module 3: it thins the dielectric isotropically inside the array without ions. This chapter develops both: the cycle, its window, its synergy, its saturation, its selectivity, its throughput, and its limits.

**Learning Objectives:**
- Define etch per cycle (EPC), the ALE window, and synergy, and compute synergy from step-alone data
- Describe the BCl₃/Ar⁺ plasma ALE cycle for ZrO₂ and identify what limits each half-step
- Compute EPC from saturation curves and choose dose and removal times for a target saturation
- Describe the HF/DMAC thermal ALE cycle and the temperature dependence of its EPC
- Explain why ALE selectivity to SiN is far higher than that of the continuous BCl₃ step
- State what ALE cannot do, including why it does not narrow a residue distribution created before it

---

## 4.1 The ALE Cycle

### 4.1.1 Two Half-Steps

```
One ALE cycle:

  A. Modification     reactant adsorbs or reacts with the top layer;
                      self-limiting once the surface is saturated
     Purge            removes excess reactant from the gas phase
  B. Removal          energetic ions (plasma ALE) or a second reactant
                      (thermal ALE) remove the modified layer only;
                      self-limiting once it is gone
     Purge            removes products

EPC = thickness removed per cycle (nm/cycle)
```

### 4.1.2 Synergy

The test of an ALE process is that the cycle removes much more than either half-step does alone:

```
S = [EPC − (α + β)] / EPC

  α = removal in step A alone (repeated without step B)
  β = removal in step B alone (repeated without step A)

S → 100%: ideal ALE      S < 50%: closer to a pulsed continuous etch
```

### 4.1.3 The ALE Window

For plasma ALE, the removal step's ion energy must be high enough to remove the modified layer completely and low enough not to sputter the unmodified film beneath:

```
EPC versus Ar⁺ energy in the removal step (tetragonal ZrO₂, illustrative):

  EPC (nm/cycle)
   0.20 ┤                                            ╱  sputtering of the
        │                                          ╱    unmodified film
   0.15 ┤                                        ╱
        │                                      ╱
   0.10 ┤              ●──────●──────●──────●         ← the ALE window
        │            ╱                                  (EPC ≈ 0.10)
   0.05 ┤          ╱   incomplete removal
        │        ╱
   0.00 ┼──────●─────┬──────┬──────┬──────┬──────┬───
               30    45     60     75     90    105   Ar⁺ energy (eV)
```

Below about 45 eV, the ions do not remove all of the chlorinated layer in the time allowed. Above about 75 eV, they begin to sputter ZrO₂ that was not modified, and the process loses its self-limitation. The reference removal step runs at **60 eV**, in the middle of the window. The width of the window, 30 eV, sets how narrow the ion-energy distribution must be (Chapter 5).

---

## 4.2 Plasma ALE of ZrO₂ with BCl₃ and Ar⁺

### 4.2.1 The Reference Cycle

```
Module 2 ALE finish (reference, illustrative):

  Step              Gas (sccm)        Pressure   Source   Bias     Time
  ──────────────────────────────────────────────────────────────────────────
  A. BCl₃ dose      BCl₃ 100, Ar 100  20 mTorr   off      off      1.0 s
     Purge          Ar 300            20 mTorr   off      off      0.75 s
  B. Ar⁺ removal    Ar 200            5 mTorr    500 W    ≈ 60 eV  2.0 s
     Purge          Ar 300            5 mTorr    off      off      0.75 s
  ──────────────────────────────────────────────────────────────────────────
  Cycle time 4.5 s;  EPC 0.10 nm (tetragonal ZrO₂);  ≈ 1.33 nm/min
```

### 4.2.2 Step A: Modification by BCl₃

The BCl₃ dose runs without plasma. BCl₃ reacts with the ZrO₂ surface, particularly at oxygen and hydroxyl sites:

```
Zr–O–(surface) + BCl₃ → Zr–Cl (surface) + O–BCl₂ (surface)
Zr–OH + BCl₃ → Zr–O–BCl₂ + HCl
```

After saturation, the top layer is chlorinated and borated to a depth of about one ZrO₂ unit (≈ 0.1 nm of film). With no plasma, there is no BₓClᵧ deposition: deposition in Chapter 3 came from radicals made by electron impact, and here there are none. This is what makes step A self-limiting where a low-energy BCl₃ *plasma* would not be.

```
Saturation of step A (illustrative):
  θ_A(t) = 1 − exp(−t/τ_A),   τ_A ≈ 0.30 s at 20 mTorr BCl₃ partial ≈ 10 mTorr

  t_A = 0.5 s  → θ = 0.81
  t_A = 1.0 s  → θ = 0.96   (reference)
  t_A = 1.5 s  → θ = 0.99
```

### 4.2.3 Step B: Removal by Ar⁺

In the Ar plasma, ions at 60 eV strike the modified layer and release ZrClₓ, BOClₓ, and Cl. The removal saturates when the modified layer is gone, because 60 eV Ar⁺ sputters unmodified ZrO₂ only very slowly:

```
Removal saturation (illustrative):
  Ion flux Γ_i ≈ 1.0 × 10¹⁶ cm⁻² s⁻¹ (Ar, 500 W, 5 mTorr)
  Modified layer ≈ 2.9 × 10¹⁴ Zr/cm² (0.10 nm of ZrO₂)
  Yield of modified-layer removal at 60 eV ≈ 0.04 Zr per ion (initial)
  τ_B ≈ 2.9 × 10¹⁴ / (0.04 × 1.0 × 10¹⁶) ≈ 0.7 s

  t_B = 1.0 s  → 76% removed
  t_B = 2.0 s  → 94% removed  (reference)
  t_B = 3.0 s  → 99% removed
```

The reference times give a product of saturations of 0.96 × 0.94 ≈ 0.90 of the fully saturated EPC. The EPC quoted, 0.10 nm, is the value at these times; the fully saturated value is about 0.11 nm. Running each step to near-complete saturation would add 1.5 s per cycle for 10% more EPC, a poor trade (Section 4.4).

### 4.2.4 Synergy

```
Measured on blanket tetragonal ZrO₂ (illustrative):
  α: BCl₃ dose alone, 100 cycles               ≈ 0 (no plasma)
  β: Ar⁺ at 60 eV alone, 2.0 s per cycle       ≈ 0.004 nm/cycle
  EPC                                          0.10 nm/cycle

  S = (0.10 − 0.004) / 0.10 = 96%
```

### 4.2.5 EPC by Material

```
Reference ALE cycle, flat surfaces (illustrative):

  Film                          EPC (nm/cycle)    Selectivity to SiN
  ────────────────────────────────────────────────────────────────────
  ZrO₂, tetragonal                 0.10              6.7
  ZrO₂, amorphous                  0.12              8
  Al₂O₃ (insertion)                0.08              5.3
  HfO₂                             0.09              6
  PECVD SiN                        0.015             1
  PE-TEOS SiO₂                     0.03              2
  TiN (flat)                       0.15              10
  TiN (vertical sidewall)          ≈ 0.02            —
  KrF resist                       0.25              17
```

**SiN.** BCl₃ does not take nitrogen as it takes oxygen, so the dose chlorinates the SiN surface only weakly; the 60 eV Ar⁺ removes little of it. ZrO₂:SiN rises from 0.75 in the continuous step to about 6.7 in ALE. That ninefold improvement is the reason for the finish (Chapter 10).

**TiN.** TiN etches readily: its surface oxide is borated in step A, and TiClₓ is volatile. On the vertical sidewall of the plate edge, where Ar⁺ arrives at grazing incidence, the removal step is weak and the EPC is low; the exposed edge of the TE TiN loses about 0.7 nm over 36 cycles (Chapter 11).

**Resist.** Resist loses about 0.25 nm per cycle, mostly by Ar⁺ sputtering. Over 36 cycles that is 9 nm, a small part of the resist budget.

### 4.2.6 Per-Grain Uniformity

Because each cycle removes what one saturated layer contains, the EPC depends much less on grain orientation than the continuous rate does:

```
Grain-to-grain EPC spread σ_EPC/EPC ≈ 3%       (vs σ_r = 7.5% continuous, 150 eV)
```

Over R nm of ALE removal, the ALE adds a spread of 0.03 R to whatever spread was already there. It adds; it does not subtract (Section 4.6).

---

## 4.3 Thermal ALE of ZrO₂ with HF and DMAC

### 4.3.1 The Cycle

Thermal ALE uses no plasma and no ions. The film is fluorinated by HF, and the fluoride is removed by a ligand-exchange reagent that makes a volatile product:

```
Step A (fluorination):
  ZrO₂ + 4 HF → ZrF₄ (surface layer) + 2 H₂O
  Self-limiting: the fluoride layer slows further HF diffusion

Step B (ligand exchange with DMAC, AlCl(CH₃)₂):
  ZrF₄ (surface) + AlCl(CH₃)₂ → ZrClₓ(CH₃)ᵧF_z (volatile) + AlF(CH₃)Cl ...
  The Zr leaves carrying chloride and methyl ligands; the Al leaves
  carrying fluoride. The remaining surface is ZrO₂ with adsorbed Al species.
```

The exchange reagent's chlorine is what makes ZrO₂ etch: zirconium products with chloride ligands are volatile at 250 °C, while those with only methyl or fluoride ligands are not. Chlorine-bearing reagents such as DMAC, SiCl₄, and TiCl₄ have been reported to etch ZrO₂ and HfO₂ in thermal ALE; trimethylaluminium, without chlorine, etches Al₂O₃ and HfO₂ more readily than ZrO₂.

### 4.3.2 The Reference Cycle (Blanket)

```
Thermal ALE, blanket wafer (illustrative):

  Step              Gas                 Partial pressure   Time
  ─────────────────────────────────────────────────────────────────
  A. HF             HF in N₂            0.5 Torr           0.5 s
     Purge          N₂                  —                  2 s
  B. DMAC           DMAC in N₂          0.2 Torr           0.5 s
     Purge          N₂                  —                  2 s
  ─────────────────────────────────────────────────────────────────
  Cycle 5 s (blanket); T_wafer 250 °C; EPC ≈ 0.06 nm (tetragonal ZrO₂)
```

On a flat wafer, each half-step saturates in well under a second. Inside the array, exposures and purges must be much longer, because the reactants reach the bottom of the channels by molecular flow (Chapter 12): the pilot uses about 35 s per cycle.

### 4.3.3 Temperature

```
EPC of tetragonal ZrO₂ versus temperature (HF/DMAC, saturated, illustrative):

  T (°C)      EPC (nm/cycle)     Limiting factor
  ─────────────────────────────────────────────────
   200           0.02             product volatility
   225           0.04
   250           0.06             (reference)
   275           0.08
   300           0.10             ligand-exchange products begin to
                                  decompose; Al deposition
```

The EPC rises with temperature because the fluoride layer grows thicker and the products leave more easily. Above about 300 °C, the exchange reagent begins to decompose on the surface and deposits aluminium, and the process turns into a competition between etch and deposition again. The trim runs at 250 °C: below the ZAZ deposition temperature and well below the 420 °C anneal, so the trim does not change the crystal structure it is meant to preserve.

### 4.3.4 Selectivity and What Else Is Exposed

```
HF/DMAC at 250 °C, materials exposed inside the array (illustrative):

  Film                      EPC (nm/cycle)    Note
  ───────────────────────────────────────────────────────────────────────
  ZrO₂, tetragonal             0.06          the target
  ZrO₂ grain boundaries        0.08–0.09     faster; see Chapter 12
  Al₂O₃                        0.05          etched if exposed
  SiN (support)                ≈ 0.005       HF reacts slowly without water;
                                             ≤ 0.1 nm in 17 cycles
  TiN (storage node)           not exposed   covered by the dielectric
  SiO₂                         ≈ 0.01        if any; HF with H₂O product
                                             can catalyse
```

The reference trim stops within the top ZrO₂ by cycle count. It never reaches the Al₂O₃ insertion, which lies 2.6 nm below the trimmed surface.

### 4.3.5 Fluorine Left Behind

The last fluorination of a trim leaves a fluorinated surface unless the cycle ends with a DMAC half-step. Even then, fluorine diffuses into the top few tenths of a nanometre during the cycles:

```
F in the trimmed ZrO₂ (illustrative):
  After 17 cycles, ending on DMAC     ≈ 2–4 at% in the top 0.3 nm
  After an O₃ or H₂O exposure at 250 °C   ≈ 0.5–1 at%
  Specification                        ≤ 1 at% (Chapter 1)
```

Fluorine in ZrO₂ can passivate oxygen vacancies or create fixed charge, depending on how much and where (Chapter 13). The pilot adds a short ozone exposure at the end of the trim.

---

## 4.4 Throughput

```
                            Plasma ALE (module 2)   Thermal ALE (module 3)
──────────────────────────────────────────────────────────────────────────────
EPC                         0.10 nm                 0.06 nm
Cycle time                  4.5 s                   5 s (blanket); 35 s (array)
Rate                        1.33 nm/min             0.72 nm/min (blanket);
                                                    0.10 nm/min (array)
Removal needed              3.6 nm                  1.0 nm
Cycles                      36                      17
Time                        162 s                   ≈ 10 min (array)
```

ALE is slow. The two levers are the EPC and the cycle time, and they pull in opposite directions: longer half-steps saturate more fully and raise the EPC, but lengthen the cycle. For saturation curves of the form 1 − exp(−t/τ), the removal rate per unit time is maximized when each step runs about 1.5–2 time constants, short of full saturation, which is why the reference plasma cycle uses 1.0 s and 2.0 s rather than 1.5 s and 3.0 s.

```
Rate = EPC_sat (1 − e^(−t_A/τ_A)) (1 − e^(−t_B/τ_B)) / (t_A + t_B + t_purge)

τ_A = 0.30 s, τ_B = 0.7 s, t_purge = 1.5 s, EPC_sat = 0.107 nm:
  t_A = 1.0, t_B = 2.0:  EPC = 0.096 nm, cycle 4.5 s → 1.28 nm/min
  t_A = 1.5, t_B = 3.0:  EPC = 0.105 nm, cycle 6.0 s → 1.05 nm/min
  t_A = 0.5, t_B = 1.0:  EPC = 0.065 nm, cycle 3.0 s → 1.30 nm/min
                                                     (but less self-limited:
                                                      EPC sensitive to drift)
```

The reference stays at 1.0 s and 2.0 s: nearly the maximum rate, with each step far enough along its saturation curve that a 10% drift in flux changes the EPC by only about 2%.

---

## 4.5 Quasi-ALE

Between continuous etch and ideal ALE is a family of **quasi-ALE** or **mixed-mode pulsing** processes, in which a BCl₃ plasma step with low bias (some deposition and some chlorination) alternates with a higher-energy Ar or Ar/Cl₂ step. EPC is larger (0.2–0.4 nm), synergy lower (50–80%), and SiN selectivity intermediate:

```
                       Continuous    Quasi-ALE       ALE (reference)
───────────────────────────────────────────────────────────────────
ZrO₂ rate (nm/min)       6.0          3–4             1.33
ZrO₂:SiN                 0.75         ≈ 3             6.7
Grain spread added       7.5% of x    ≈ 5% of x       3% of x
Self-limited             no           partly          yes
```

Quasi-ALE is a reasonable compromise where throughput dominates (Chapter 10, Section 10.7). The reference uses true ALE because the finish exists to protect SiN, the plate edge, and the remaining dielectric, and that protection comes from self-limitation.

---

## 4.6 What ALE Cannot Do

1. **It cannot narrow a distribution created before it.** If the main step leaves a remaining thickness distribution of width σ, the ALE must remove the thickest tail of that distribution, cycle by cycle. A thicker spot needs more cycles; ALE does not know it is thicker. (Smoothing of roughness by ALE occurs at the scale of a few tenths of a nanometre and does not change this conclusion for grain-scale residue.)

2. **It cannot be fast.** At 1.33 nm/min, the 5.5 nm ZAZ would take more than four minutes on its own; the main step does most of the removal.

3. **It cannot etch what has no volatile product.** Sr, La, and Y halides do not leave in either plasma or thermal ALE (Chapter 14).

4. **It cannot ignore the first cycle.** The first cycle on a surface left by a different step (a BₓClᵧ-coated surface after the main step, an OH-terminated surface after an anneal) can remove more or less than the steady EPC. The module 2 finish begins on a surface the main step has already chlorinated and borated; its first cycle removes about 0.15 nm.

5. **It cannot be measured directly in production.** EPC is measured on blanket monitors and inferred on product; Chapter 8 describes cycle-resolved emission signals that help.

---

## 4.7 Where ALE Appears in This Book

```
Module   ALE type          Job                            Chapters
──────────────────────────────────────────────────────────────────────────
2        Plasma            remove the main-step residue   4, 5, 8, 10, 11
                           tail with low SiN loss and
                           low ion energy at the edge
3        Thermal           thin the dielectric isotrop-   4, 12, 13
                           ically inside the array
1        —                 not used: the bevel needs a    7
                           fast, unmasked removal
```

---

## Summary and Key Takeaways

1. **ALE separates modification from removal.** Each half-step self-limits; the cycle removes a fixed EPC set by surface chemistry.

2. **The plasma ALE window is 45–75 eV.** BCl₃ dose without plasma (self-limiting chlorination), then Ar⁺ at 60 eV; EPC 0.10 nm, synergy 96%.

3. **ALE selectivity to SiN is nine times better.** ZrO₂:SiN ≈ 6.7 in ALE versus 0.75 in the continuous step; that is the finish's purpose.

4. **Thermal ALE is isotropic and slow.** HF fluorination and DMAC ligand exchange at 250 °C remove 0.06 nm per cycle with no ions, and leave fluorine that an ozone exposure reduces.

5. **Run each half-step to about two time constants.** That nearly maximizes throughput while keeping EPC insensitive to drift.

6. **ALE adds spread; it does not remove it.** The finish must remove the whole tail left by the main step.

---

## Study Questions

1. A plasma ALE process gives EPC = 0.12 nm/cycle; BCl₃ dosing alone removes nothing measurable, and Ar⁺ alone at 70 eV removes 0.02 nm/cycle. Compute the synergy. What would you expect to happen to synergy if the Ar⁺ energy were raised to 90 eV?

2. With τ_A = 0.30 s and τ_B = 0.7 s, compute the EPC (as a fraction of saturation) and the removal rate for t_A = 0.75 s and t_B = 1.5 s, with 1.5 s of purges per cycle. Compare with the reference.

3. The SiN EPC in the ALE finish rises from 0.015 to 0.04 nm/cycle after a chamber change. How much SiN does the 36-cycle finish now remove at the fastest-clearing site, where SiN is exposed for 28 cycles? Does this break the specification?

4. A thermal ALE trim at 275 °C has EPC 0.08 nm. How many cycles are needed for a 1.0 nm trim? Why might the process engineer still prefer 250 °C?

5. A main step leaves a remaining-thickness distribution with σ = 0.35 nm. The ALE finish removes 3.6 nm with σ_EPC/EPC = 3%. What is the total spread at the end of the finish, before any material reaches SiN? Explain why it is larger, not smaller, than 0.35 nm.

6. Explain why a BCl₃ dose with the plasma source on at 300 W (no bias) would not be a self-limiting step A. What would you observe in EPC versus dose time?

---

**Next Chapter:** [Chapter 5: ICP Chambers & Ion-Energy Control for Nanometre Removal](./05-icp-chambers-ion-energy-control.md)

---

**Chapter 4 Development Status:** Complete  
**Version:** 1.0
