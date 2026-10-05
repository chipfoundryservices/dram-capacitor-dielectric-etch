# Chapter 4: Atomic-Layer, Thermal & Wet Removal of High-k Films

## Overview

The periphery ZAZ is about twenty monolayers thick. A continuous plasma etch removes it in half a minute, and in doing so inherits every non-uniformity of the plasma: a 1 eV change of ion energy changes the rate by 1.8%, a 1 °C change of temperature by 0.7%, and a change of open area by whatever the loading law says. Atomic-layer etching (ALE) breaks the removal into two self-limiting half-steps, each of which saturates. The amount removed per cycle then depends on the surface chemistry, not on the dose, and most of those sensitivities fall away.

Two families of ALE apply to high-k films. **Plasma ALE** chlorinates the surface with a low-energy BCl₃/Cl₂ plasma and removes the modified layer with Ar⁺ ions in a narrow energy window. It is directional, like the continuous etch, and it is this book's second reference process, D2. **Thermal ALE** fluorinates the surface with HF and removes the fluoride by ligand exchange with an organometallic or chloride reagent. It uses no plasma at all, is isotropic, and is extraordinarily selective to everything that is not a metal oxide. Wet chemistry, the oldest option, is isotropic and cheap and struggles with crystalline ZrO₂.

This chapter develops each method far enough to compare it with the continuous hot etch D1: what limits the removal per cycle, how wide the process window is, what it does to the landing nitride and the plate edge, how long it takes, and where each method fits.

**Learning Objectives:**
- Describe the two half-cycles of plasma ALE of ZrO₂ and the ion-energy window in which the removal is self-limiting
- Compute the ALE synergy from the half-cycle rates and explain why the chamber temperature must be kept low
- Describe thermal ALE by fluorination and ligand exchange, its reagents, its temperature window, and its selectivity
- Explain why isotropic removal undercuts the dielectric at the plate edge, and compute the undercut
- Compare wet chemistries for crystalline ZrO₂ and the damage-enhanced hybrid route
- Compare the cycle count, time, landing loss, and edge attack of D1, D2, thermal ALE, and the hybrid

---

## 4.1 Why Atomic Layers

```
Sensitivities of the reference continuous etch D1 (Chapter 3):
  Ion energy        1.8% rate per eV
  Temperature       0.7% rate per °C
  Cl₂ fraction      rate, SiN, and sidewall attack all move (Section 3.3.3)
  Open area         global loading (Chapter 6)
  Time              removal proportional to time; endpoint needed
```

In ALE, the amount removed per cycle (EPC, etch per cycle) is set by the depth of the modified layer, which saturates at about one monolayer of reacted surface. As long as each half-step runs to saturation, the dose does not matter. The cost is time: one cycle removes about a third of a monolayer and takes seconds.

---

## 4.2 Plasma ALE: The Reference D2

### 4.2.1 The Cycle

```
D2 cycle (ALE-capable ICP, chuck 100 °C, illustrative):
  Step A  Modification   BCl₃ 90 / Cl₂ 10 sccm, 20 mTorr, 500 W source,
                         0 W bias (ion energy ≈ 15 eV, plasma potential only)  1.5 s
  Purge                  Ar, pressure switch                                    0.5 s
  Step B  Removal        Ar 200 sccm, 10 mTorr, 500 W source,
                         bias for ≈ 60 eV                                       2.5 s
  Purge                  Ar                                                     0.5 s
  Cycle time                                                                    5.0 s
```

Like D1, D2 opens with a 3 s BCl₃/Ar breakthrough at about 100 eV that removes the carbon, titanium, and fluorine left on the surface by the plate etch and the strip (Chapters 2 and 10); at 100 °C it also removes about 0.2 nm of ZAZ, which the cycle count below does not take credit for. In step A, BCl₂⁺ and Cl arrive at energies below the etch threshold. Chlorine bonds to surface zirconium, and boron bonds to surface oxygen, forming a mixed Zr–Cl / B–O surface layer about one monolayer deep. Without energetic ions, further reaction stops: the oxygen beneath the first layer is not reached. In step B, Ar⁺ ions at 60 eV deliver enough energy to desorb ZrClₓ and BOCl from the modified layer, but not enough to sputter unmodified ZrO₂. When the modified layer is gone, removal stops.

### 4.2.2 Saturation

```
EPC of tetragonal ZrO₂ versus step duration (illustrative):
  Step A (s)    EPC (nm)        Step B (s)    EPC (nm)
  ─────────────────────────     ─────────────────────────
   0.3          0.04             0.5          0.05
   0.7          0.08             1.0          0.08
   1.0          0.095            1.5          0.095
   1.5 (ref)    0.10             2.5 (ref)    0.10
   3.0          0.10             5.0          0.105
```

Both half-steps saturate. The reference durations sit at about 1.5 times the saturation knee, enough margin that chamber-to-chamber differences of radical and ion flux do not move the EPC.

### 4.2.3 The Ion-Energy Window

```
EPC of tetragonal ZrO₂ versus step-B ion energy (illustrative):
  E (eV)    EPC (nm)    Regime
  ─────────────────────────────────────────────────────────────────
   20        0.01       incomplete removal of the modified layer
   35        0.06       partial
   45        0.095      window begins
   60 (ref)  0.10       self-limiting plateau
   70        0.11       window ends
   90        0.16       physical sputtering of unmodified ZrO₂ adds
  120        0.24       not ALE: continuous sputter-assisted etch
```

The window is about 25 eV wide, from 45 to 70 eV. Inside it, a 5 eV error changes the EPC by about 2%, against 9% for the continuous etch at 70 eV. Above 70 eV, Ar⁺ begins to sputter unmodified ZrO₂, the EPC rises with energy, and the process loses the property that made it worth the time.

### 4.2.4 Synergy

The test of a true ALE process is that the two half-steps remove much more together than either alone:

```
Synergy S = (EPC − α − β) / EPC

  α = removal by step A alone (no step B), per cycle      ≈ 0.002 nm
  β = removal by step B alone on an unmodified surface    ≈ 0.008 nm
  EPC                                                      0.10 nm
  S = (0.10 − 0.002 − 0.008) / 0.10 = 90%
```

### 4.2.5 Why the Chamber Is Cool

D2 runs at 100 °C, not at D1's 250 °C. At 250 °C, the chlorinated surface formed in step A begins to lose ZrCl₄ thermally without ions, and BCl₃ chlorination proceeds below the first monolayer:

```
Effect of temperature on D2 (illustrative):
  T (°C)    α (nm/cycle)    EPC (nm)    S
  ──────────────────────────────────────────
   60        0.001           0.09       90%
  100 (ref)  0.002           0.10       90%
  180        0.010           0.13       86%
  250        0.035           0.18       76%  ← spontaneous etch in step A;
                                               loses self-limitation
```

A cooler chamber keeps step A self-limiting. It also means D2 can run in an ALE chamber that is not built for 250 °C (Chapter 7).

### 4.2.6 Materials

```
D2 EPC by film (100 °C, 60 eV removal, illustrative):
  Film                    EPC (nm/cycle)   Comment
  ─────────────────────────────────────────────────────────────────────
  ZrO₂ amorphous           0.13            less dense; deeper modification
  ZrO₂ tetragonal          0.10            reference
  ZrO₂ monoclinic          0.095           close to tetragonal: the
                                           modification depth is set by
                                           surface chemistry, not packing
  Al₂O₃                    0.08
  SiOₓNᵧ interlayer        0.03
  PECVD SiN                0.012           boron–nitrogen bonding in step A
                                           passivates the surface
  PE-TEOS                  0.010
  TE TiN (sidewall)        ≈ 0.005 lateral spontaneous Cl attack in step A;
                                           no ions on the sidewall
```

The difference between tetragonal and monoclinic grains, 9% in D1, falls to 5% in D2. Grain boundaries, which etch faster in D1, are modified to about the same depth as grain interiors. Chapter 10 shows that this narrows the spread of local clearing from about 10% in D1 to about 4% in D2.

### 4.2.7 Cycle Count and Time

```
D2 clearing (reference periphery ZAZ, 5.4 nm):
  Upper ZrO₂ 2.55 nm / 0.10          25.5 cycles
  Al₂O₃ 0.3 nm / 0.08                 3.75 cycles
  Lower ZrO₂ 2.55 nm / 0.10          25.5 cycles
  Phase mix (≈ 30% monoclinic)       + ≈ 1 cycle
  Nominal                            ≈ 56 cycles
  Over-cycling 30%                   + 17 cycles → 73 cycles
  Time at 5.0 s per cycle            365 s ≈ 6.1 min (+ 3 s breakthrough)
  SiN loss in over-cycling           17 × 0.012 ≈ 0.2 nm
```

Six minutes of chamber time against one minute for D1; 0.2 nm of SiN lost against 1.3 nm. Whether the trade is worthwhile depends on what limits the yield (Chapter 16).

---

## 4.3 Thermal ALE

### 4.3.1 Fluorination and Ligand Exchange

Thermal ALE of metal oxides uses two vapor-phase reactions that are each self-limiting:

```
Step 1  Fluorination:      ZrO₂ + 4 HF → ZrF₄ + 2 H₂O        ΔH ≈ −200 kJ/mol
                           (limited to ≈ 1 nm of ZrF₄ by diffusion through
                           the fluoride)
Step 2  Ligand exchange:   ZrF₄ + reagent → volatile Zr complex + fluorinated
                           reagent fragments
        Reagents:          Al(CH₃)₂Cl (DMAC), Al(CH₃)₃ (TMA), SiCl₄, BCl₃
```

The fluorination is spontaneous and stops when the fluoride layer blocks further HF. The ligand exchange transfers chlorine or methyl groups to zirconium and fluorine to the reagent, producing volatile species such as ZrCl₄ and Zr(CH₃)ₓClᵧ. BCl₃ works as an exchange reagent because the Zr–F to B–F transfer is exothermic (Chapter 3, Section 3.2.4) and ZrCl₄ is volatile at the reaction temperature.

### 4.3.2 Window and Rates

```
Thermal ALE (HF / DMAC, single wafer, illustrative):
  Temperature window     250–300 °C (below: exchange incomplete;
                         above: reagent decomposition, CVD of Al species)
  Reference              275 °C
  Cycle                  HF 1 s / purge 5 s / DMAC 1 s / purge 5 s = 12 s

  Film                   EPC (nm/cycle)
  ──────────────────────────────────────────
  ZrO₂ amorphous          0.09
  ZrO₂ tetragonal         0.05
  ZrO₂ monoclinic         0.04
  Al₂O₃                   0.06
  HfO₂ monoclinic         0.04
  SiO₂, SiN               < 0.005 (no water to catalyse HF on silica;
                          no exchange product for Si–N)
  TiN, W, SiGe            ≈ 0 (no oxide-to-fluoride conversion)
```

The selectivity to everything around the dielectric is effectively infinite. The purges are long because HF adsorbs strongly on chamber surfaces and must be cleared before the reagent arrives; otherwise HF and DMAC react in the gas and deposit AlF₃.

### 4.3.3 Crystallinity

Thermal ALE is more sensitive to phase than plasma ALE. Fluorination penetrates a dense crystalline lattice less deeply, and monoclinic grains etch about 20% more slowly than tetragonal grains. Grain boundaries fluorinate deeper than interiors. The spread of local clearing is wider than in D2 (Chapter 10).

### 4.3.4 Time

```
Thermal ALE clearing (reference periphery ZAZ, single wafer):
  ZrO₂ 5.1 nm / 0.05 ≈ 102 cycles; Al₂O₃ 0.3 / 0.06 ≈ 5 cycles
  Nominal ≈ 107 cycles; + 30% → 139 cycles
  Time at 12 s per cycle ≈ 28 min per wafer
```

The 30% margin is the one D2 uses, kept here for comparison. Chapter 10 shows that thermal ALE's wider spread of local clearing needs nearly 80%, about 190 cycles.

On a single-wafer tool, that is too slow for production. In a batch reactor holding 100 wafers, with longer pulses and purges (about 60 s per cycle), the same 139 cycles take about 2.3 h per batch, roughly 35–40 wafers per hour per reactor (Chapter 7).

### 4.3.5 Isotropy and the Plate Edge

Thermal ALE has no preferred direction. At the plate edge, the ZAZ under the TE TiN is attacked laterally once the etch front reaches it:

```
Undercut by an isotropic removal of total thickness t_rem on a film of
thickness t_f, capped above by the TE TiN:
  at the top of the ZAZ (under the TiN):  ≈ t_rem
  at the bottom of the ZAZ:               ≈ t_rem − t_f

Thermal ALE, reference (t_rem = 1.3 × 5.4 = 7.0 nm, t_f = 5.4 nm):
  undercut ≈ 7.0 nm at the top, ≈ 1.6 nm at the bottom
```

The specification allows 2 nm (Chapter 1). Thermal ALE alone violates it at the top of the film. Chapter 11 discusses whether a 7 nm slot under the TE edge, 1.5 µm from the first capacitor, matters, and how to fill it. Isotropy is also thermal ALE's great advantage: it removes the ZAZ from vertical walls that a directional process cannot reach (Chapter 10).

---

## 4.4 Wet and Vapor Removal

### 4.4.1 Wet Chemistries

```
Wet etch rates (illustrative):
  Film                    0.5% HF       HF/H₂SO₄       Hot H₃PO₄
                          (25 °C)       (80 °C)        (160 °C)
  ────────────────────────────────────────────────────────────────
  ZrO₂ amorphous          ≈ 2 nm/min    ≈ 10 nm/min    ≈ 3 nm/min
  ZrO₂ tetragonal         0.1–0.3       ≈ 2            ≈ 1
  ZrO₂ ion-damaged        ≈ 3           ≈ 10           ≈ 3
  (top 1 nm after a
  BCl₃ plasma)
  Al₂O₃                   ≈ 3           fast           fast
  PECVD SiN               ≈ 2           ≈ 3            ≈ 5
  PE-TEOS                 ≈ 5           ≈ 20           ≈ 1
  TiN, W, SiGe            < 0.1         TiN attacked   W attacked
```

Crystalline ZrO₂ resists dilute HF almost completely. Every chemistry that dissolves it dissolves the landing nitride as fast or faster. A stand-alone wet removal of crystallized ZAZ is not practical.

### 4.4.2 Damage-Enhanced Hybrid

Ion bombardment in a BCl₃ plasma disorders and chlorinates the top nanometre of the film. The damaged layer dissolves in dilute HF at amorphous-film rates. That suggests a hybrid:

```
Hybrid route W (illustrative):
  Dry    D1 chemistry, stopped by time with ≈ 0.8 nm of ZAZ remaining
         (no overetch on SiN; the remaining film is ion-damaged)
  Wet    0.5% HF, 25 °C, 30 s: removes the damaged remainder at ≈ 3 nm/min
         SiN loss ≈ 1 nm; oxide cap loss ≈ 2.5 nm
  Lateral: HF attacks the damaged ZAZ face at the plate edge;
         undercut ≈ 1–1.5 nm
```

The hybrid's weakness is the grain tail. Grains that the dry step left thicker than 0.8 nm, or that were shadowed from the ions, are crystalline and undamaged where they matter, and the wet step barely touches them. The hybrid removes the Gaussian spread well and the non-Gaussian tail poorly (Chapter 10).

### 4.4.3 Vapor HF

Anhydrous or alcohol-moderated HF vapor at room temperature etches amorphous ZrO₂ slowly and crystalline ZrO₂ negligibly. It has no role in clearing the ZAZ. It matters for metrology: vapor-phase decomposition (VPD) of the wafer surface before TXRF does not dissolve crystalline ZrO₂ residues efficiently, so VPD-based measurements undercount zirconium (Chapter 15).

---

## 4.5 Comparison

```
Routes for clearing the reference periphery ZAZ (illustrative):

                     R0 cold     D1 hot      D2 plasma    T thermal    W hybrid
                     in-situ     (ref)       ALE (ref)    ALE          (D1 + HF)
─────────────────────────────────────────────────────────────────────────────────────
Temperature (°C)     60          250         100          275          250 / 25
Ion energy (eV)      150         70          60 (pulsed)  none         70 / none
Directional          yes         yes         yes          no           partly
Time per wafer       93 s        61 s        365 s        28 min       ≈ 60 s +
(chamber)                                                 (or batch)   wet step
SiN loss (nm)        4           1.3         0.2          < 0.1        ≈ 1
Selectivity          0.75        3           ≈ 8          > 100        —
ZrO₂ : SiN
Mask                 resist      oxide cap   oxide cap    oxide cap    oxide cap
Plate-edge TiN       notching    1.2 nm      ≈ 0.4 nm     ≈ 0          1.2 nm
lateral loss         (Book #32)
ZAZ undercut         ≈ 0         ≤ 0.3 nm    ≈ 0          ≈ 7 nm top   1–1.5 nm
Stringers on walls   remain      remain      remain       removed      partly
                                                                       removed
Local clearing       ≈ 8–10%     ≈ 10%       ≈ 4%         ≈ 12%        —
spread σ_g
```

No route is best on every line. The hot continuous etch is fast and adequately selective. Plasma ALE is the most uniform and gentlest on the landing film and the edge, and the slowest of the directional routes. Thermal ALE is the most selective and the only one that clears walls, and it undercuts the edge. The hybrid saves overetch and trusts the wet step with a tail it cannot reach. Chapters 10, 11, and 16 weigh them against residue, the plate edge, and cost.

---

## Summary and Key Takeaways

1. **ALE trades time for insensitivity.** Each half-step saturates, so EPC is set by surface chemistry rather than by ion energy, temperature, or loading.

2. **Plasma ALE has a 25 eV window.** Between 45 and 70 eV, Ar⁺ removes the chlorinated layer and not the oxide beneath; synergy is about 90% at 100 °C and falls when the chamber is hot.

3. **D2 clears the ZAZ in 73 cycles and 6 minutes** with 0.2 nm of SiN loss and a local clearing spread of about 4%.

4. **Thermal ALE is selective and isotropic.** HF fluorination and DMAC or BCl₃ exchange remove ZrO₂ and not SiN, SiO₂, TiN, W, or SiGe; they also undercut the ZAZ under the TE TiN by about the total amount removed.

5. **Wet chemistry cannot clear crystalline ZrO₂ selectively,** but it can finish an ion-damaged remainder. The grains it most needs to remove are the ones it cannot.

6. **Every route trades something.** Speed, landing loss, edge attack, wall stringers, and clearing spread cannot all be optimal at once.

---

## Study Questions

1. Compute the synergy of D2 if the chamber temperature drifts to 180 °C (Section 4.2.5). How many cycles are now needed for the reference ZAZ with 30% over-cycling, and how much SiN is lost, if the SiN EPC rises in proportion to α?

2. The step-B bias power is miscalibrated so that the ion energy is 80 eV. Estimate the new EPC and explain why the process is no longer ALE. What happens to the SiN EPC?

3. For thermal ALE at 12 s per cycle, how many single-wafer chambers would be needed for 139 wafers per hour? How many 100-wafer batch reactors at 60 s per cycle (ignore load and heat-up time)?

4. A thermal-ALE process removes a total of 6.5 nm on a 5.4 nm film. Compute the undercut at the top and bottom of the ZAZ under the TE TiN. What happens to the undercut if a plasma ALE step first removes 4 nm anisotropically?

5. In the hybrid of Section 4.4.2, a grain was shadowed by a carbon particle during the dry step and remains 3 nm thick and crystalline. How long would 0.5% HF need to remove it, and how much SiN would be lost meanwhile?

6. Explain why the difference in EPC between tetragonal and monoclinic grains is smaller in plasma ALE than in continuous etching and thermal ALE.

---

**Next Chapter:** [Chapter 5: Heated-Chuck ICP Chambers for Dielectric Clearing](./05-heated-chuck-icp-chambers.md)

---

**Chapter 4 Development Status:** Complete  
**Version:** 1.0
