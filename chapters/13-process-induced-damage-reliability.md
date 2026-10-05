# Chapter 13: Process-Induced Damage & Dielectric Reliability

## Overview

Each of the three dielectric etches leaves most of the dielectric untouched and some of it changed. Module 1 runs a plasma at the wafer edge while a continuous TiN sheet connects the edge to every capacitor on the wafer. Module 2 runs two plasmas, one of them re-ignited thirty-six times, over a plate that is wired to every capacitor in its island, and leaves chlorine and boron at the plate edge. Module 3 has no plasma at all, but it chemically etches the surface of every capacitor, grooves its grain boundaries, and leaves fluorine, aluminium, and carbon behind. Book #32 (Chapter 13) treated the charging of the capacitor dielectric through the plate during the conductor steps. This chapter takes the dielectric's point of view across all three modules: what each etch can do to the remaining film, how those changes appear in leakage and breakdown, how much of the damage later anneals repair, and how it is measured.

**Learning Objectives:**
- List the damage mechanisms of each dielectric etch and the part of the film each reaches
- Estimate the voltage across the dielectric when a wafer-wide TE sheet is connected to a bevel plasma
- Describe how chlorine, boron, fluorine, hydrogen, and oxygen vacancies change trap-assisted leakage in ZrO₂
- Use Weibull area scaling to translate a test-capacitor breakdown result to a full die
- Identify which damage is recovered by later anneals and which is not
- Design test structures that separate the contributions of each module

---

## 13.1 Inventory

```
Damage mechanisms by module (reference):

  Module   Mechanism                     Reaches                        Severity
  ─────────────────────────────────────────────────────────────────────────────────
  1        Charging through the TE       every capacitor on the         low: clamped by
  bevel    sheet (B1, while TiN is       wafer (TE is continuous        the wafer's own
           present at the edge)          before the SiGe)               leakage (§13.2)
           Halogens, boron at the        the bevel boundary only        none for devices
           boundary
  2        Charging through the plate    every capacitor in the         low to moderate
  periph.  (main step, ALE ignitions)    island                         (§13.3)
           VUV from the Ar ALE plasma    the exposed ZAZ edge face      none for devices
           Cl, B at the ZAZ edge         ≈ 50 nm from the edge          none for devices
                                         (Chapter 11)                   (edge on SiN)
  3        Grain-boundary grooves        every capacitor                moderate (§13.4)
  trim     F, Al, C at the surface       every capacitor, top 0.3 nm    low after O₃
           H from HF                     every capacitor                low; anneal-
                                                                        sensitive
```

Two of the three modules can reach every capacitor on the wafer: module 1 through charging, module 3 through chemistry. Module 2 reaches every capacitor of an island through charging, and reaches the film chemically only at its edge.

---

## 13.2 Module 1: The Wafer-Wide Capacitor as Its Own Clamp

### 13.2.1 The Circuit

At module 1, the TE TiN has just been deposited and is continuous over the whole front of the wafer, across every array, the periphery, and the bevel. Every capacitor on the wafer has the TE as its top electrode and its storage node, through the access transistor's junction, connected to the substrate. During B1, the TE at the bevel touches the plasma:

```
Bevel plasma ── TE TiN (whole wafer) ── ZAZ (2 m² of array + 318 cm² periphery)
                                          │
                              storage nodes ── junctions ── substrate ── chuck
```

The bevel plasma can push current into the TE. The only way out is through the dielectric, the storage nodes, and the substrate. The question is how high the voltage across the dielectric must rise to carry that current.

### 13.2.2 The Clamp

```
Maximum current the bevel plasma can deliver (ion saturation):
  ≈ 1 mA/cm² × 46 cm² ≈ 46 mA (upper bound; net current is smaller)

Leakage of the whole wafer's dielectric at 1.0 V:
  8 × 10⁻⁷ A/cm² × 2 × 10⁴ cm² ≈ 16 mA

Leakage rises exponentially above 1 V (J = J₁ exp((V − 1)/V₀), V₀ ≈ 0.2 V):
  Voltage to carry 46 mA:  V ≈ 1 + 0.2 ln(46/16) ≈ 1.2 V
```

The enormous area of the dielectric clamps the voltage near 1.2 V, close to the operating range and far below the 2–2.5 V at which charge injection begins to create traps. The wafer-wide capacitor is its own protection. Two conditions would break it: a TE sheet broken into islands before B1 (an island of small area has no clamp), and a bevel plasma with arcing (Chapter 7), whose current is not limited by ion saturation.

---

## 13.3 Module 2: The Plate, Revisited

### 13.3.1 What Book #32 Established

During the plate etch, each plate island is connected to every capacitor beneath it and exposed to the plasma at its edge. Book #32 (Chapter 13) estimated an antenna ratio of about 0.017 for the wafer-continuous plate, a clamp voltage of about 1.3 V, and an injected charge of about 10⁻³ C/cm², small compared with the charge to breakdown. Once the plate is separated into islands at the end of the TE clear, each island charges independently.

### 13.3.2 What Changes in This Book's Module 2

```
                                  Continuous HK step     Reference (main + ALE)
                                  (Book #32)
───────────────────────────────────────────────────────────────────────────────
Time with 150 eV bias, islands    93 s                    45 s
separated
Plasma ignitions after separation 1                       37 (main + 36 ALE)
Bias during ALE removal           —                       ≈ 60 eV, tailored
                                                          waveform
Plasma off (dose, purges)         —                       ≈ 90 s of the 162 s
```

Shorter time at high bias halves the steady charging dose. The new element is the **ignition transient**: each time the Ar plasma ignites, the density rises over tens of milliseconds, and until it is uniform, different plate islands float to different potentials:

```
Ignition transient charging (illustrative, per ignition):
  Duration                   ≈ 40–150 ms (Chapter 5)
  Peak voltage across ZAZ    ≈ 1.5 V (before the bias is applied)
  Injected charge            ≈ 10⁻⁷ C/cm² per ignition
  36 ignitions               ≈ 4 × 10⁻⁶ C/cm²

Compare: steady charging of the main step ≈ 5 × 10⁻⁴ C/cm²
         charge to breakdown of ZAZ      ≈ 1–10 C/cm²
```

The transients add less than 1% to the main step's dose, provided the bias waits until the plasma is formed (Chapter 5, Section 5.5). Applied early, into a forming plasma, the bias would raise each transient's peak to several volts and its injected charge by orders of magnitude.

### 13.3.3 VUV at the Edge

Argon plasmas emit strongly at 104.8 and 106.7 nm, photons of about 12 eV, far above the 5.8 eV band gap of ZrO₂. The ALE removal steps expose the ZAZ to them for 72 s in total:

```
VUV at the exposed ZAZ (illustrative):
  Ar resonance photon flux at the wafer      ≈ 10¹⁵ photons/cm²/s
  Exposure over 36 removal steps             ≈ 7 × 10¹⁶ photons/cm²
  Absorption depth in ZrO₂                   ≈ 10–20 nm (entire film)
  Reaches                                    exposed ZAZ only: the periphery
                                             (removed) and the edge face
                                             (on SiN, unbiased)
```

The plate (W and SiGe) is opaque to VUV. Under it, the capacitors receive none. The VUV dose matters only in edge-intensive test structures and in any layout where the plate leaves capacitor dielectric uncovered.

---

## 13.4 Module 3: Chemistry on Every Capacitor

### 13.4.1 Traps and Leakage

Leakage through crystallized ZAZ at 1 V is mostly trap-assisted tunnelling: electrons hop through defect states in the band gap. The current scales with the density of traps near the energy at which the electrons enter:

```
J_TAT ∝ N_t × exp(−(trap-related barrier terms))

Dominant traps in ZrO₂:   oxygen vacancies (V_O), especially at grain
                          boundaries and at the TiN interfaces
```

### 13.4.2 What Each Species Does

```
Species introduced by the trim and the etches (illustrative):

  Species  Site                     Effect                          Net, reference
  ───────────────────────────────────────────────────────────────────────────────
  F        replaces O near V_O      passivates vacancy traps at     slight benefit at
           (F_O); excess F          < 1 at%; fixed positive charge  ≤ 1 at%; harm
           interstitial             and new traps at several at%    above ≈ 2 at%
  Cl       Cl_O; at boundaries      donor-like; traps; does not     harm; kept at the
                                    leave below ≈ 600 °C            plate edge only
  B        at boundaries, surfaces  acceptor-like; mobile along     harm if in the
                                    boundaries                      array; kept out
  H        OH, V_O–H complexes      passivates some traps;          mixed; released
                                    releases under stress           by later anneals
  Al       surface dopant           slightly raises local k;        neutral to slight
           (≈ 10¹⁴ /cm²)            no new traps                    benefit
  C        interstitial,            traps near mid-gap              harm above
           carbonates                                               ≈ 0.5 at%
```

### 13.4.3 The Groove, Again

The 0.25 nm grooves along grain boundaries of Chapter 12 combine two effects: the film is thinner there, and boundaries already have the highest trap density. In the pilot, the median leakage rises by about 10% and the 10⁻⁶ tail by about 20%. The groove is the main reason the trim's leakage cost is in the tail rather than the median.

---

## 13.5 Breakdown and Area Scaling

### 13.5.1 Weibull Statistics

Time-dependent dielectric breakdown (TDDB) is measured on test capacitors and extrapolated to the product with Weibull statistics:

```
F(t) = 1 − exp[ −(A / A₀) (t / η)^β ]

Scaling the characteristic life from area A₀ to area A:
  η(A) = η(A₀) × (A₀ / A)^(1/β)

Reference ZAZ: β ≈ 2.0
  Test capacitor array   A₀ = 1 × 10⁻³ cm²
  One die: 1.7 × 10¹⁰ cells × 1.24 × 10⁵ nm² ≈ 21 cm² of dielectric
  η(die) / η(test) = (10⁻³ / 21)^(1/2) ≈ 7 × 10⁻³
```

A die has about twenty thousand times the dielectric area of the test structure; its characteristic life is about 150 times shorter. That is why the qualification of a dielectric etch is judged by changes in β and in the low tail of the Weibull plot, not only by η.

### 13.5.2 What Each Module Does to the Weibull Plot

```
TDDB at 2.0 V, 125 °C, test arrays (illustrative, normalized):

  Split                          η        β       Comment
  ─────────────────────────────────────────────────────────────────────────
  Reference (no trim)            1.00     2.0
  Module 2 continuous route      0.97     2.0     longer charging; no change
  (Book #32), centre arrays                       in β
  Edge-intensive arrays (0.2 µm  0.80     1.7     edge chemistry reaches the
  from the plate edge)                            outer cells; β falls
  Trim pilot (module 3)          0.90     1.9     grooves; slight β loss
  Trim without O₃ step           0.70     1.6     fluorine and carbon traps
  (F ≈ 3 at%)
```

A fall in β is more serious than a fall in η: a smaller β means a wider distribution, and after area scaling the early failures of the die come from the low tail. The trim's β of 1.9 instead of 2.0 costs, after scaling to the die, about as much as its 10% loss of η.

---

## 13.6 Recovery

```
Recovery by later process steps (illustrative):

  Damage                       Step that repairs it          Fraction recovered
  ───────────────────────────────────────────────────────────────────────────────
  Charge-trapping traps from   SiGe fill (425 °C, 2 h);       ≈ 70–90%
  plasma charging (module 1)   later anneals
  Charge-trapping traps        ILD and back-end anneals,      ≈ 50–70%
  (module 2 main step)         forming-gas alloy (420 °C)
  Interface states, V_O        forming gas (H₂ passivation)   partial; H released
                                                              again under stress
  F excess (module 3)          O₃ step; TE deposition at      F above ≈ 1 at% partly
                               400 °C (F gettered to the TE   remains
                               interface)
  Cl at the plate edge         none below ≈ 600 °C            stays (harmless where
                                                              unbiased)
  Grain-boundary grooves       none (geometric)               stays
```

Charging damage is the most recoverable, because traps created by injected charge are mostly shallow and anneal out. Chemistry and geometry are not recovered: chlorine stays where it is, and a groove is a groove. This is the deeper reason the reference process keeps chlorine and boron at the plate edge, away from the capacitors, and limits the trim's groove by design rather than by anneal.

---

## 13.7 Test Structures

```
Structure                               Separates                       Used for
─────────────────────────────────────────────────────────────────────────────────────
Array-centre capacitor array            baseline dielectric             every lot
(plate edge ≥ 10 µm away)               (deposition, trim)
Edge-intensive arrays (plate edge at    module 2 edge chemistry and     weekly; route
0.2, 0.5, 1.5 µm)                       charging at the edge            changes
Antenna arrays (small plate islands     module 2 charging per island    qualification
with long perimeters)
Bevel-proximity arrays (dies at         module 1 effects at the edge    qualification
r = 145–147 mm vs centre)               dies
Trim / no-trim split arrays             module 3                        pilot
C–V hysteresis and flat-band shift      trapped charge (charging,       qualification
                                        F fixed charge)
Retention-time distribution on          everything, as the product      per product
product arrays                          sees it
```

The final arbiter is the retention-time distribution of real arrays, measured on product dies at elevated temperature. A dielectric etch that shifts the 10⁻⁶ point of that distribution is a problem whatever its test structures say.

---

## Summary and Key Takeaways

1. **Two modules reach every capacitor.** Module 1 through charging of the wafer-wide TE sheet; module 3 through chemistry on the whole array. Module 2 reaches every capacitor of an island through charging, and the film itself only at the plate edge.

2. **The wafer clamps itself.** 2 m² of dielectric leaks 16 mA at 1 V; the bevel plasma cannot push the voltage across it much above 1.2 V unless the TE is broken or the bevel arcs.

3. **Ignitions are cheap if the bias waits.** 36 ALE ignitions add about 1% to the main step's charging dose.

4. **The trim's species are mixed blessings.** Fluorine below 1 at% helps; above 2 at% it harms. Carbon and boron harm; aluminium is neutral.

5. **Area scaling magnifies tails.** A die has ≈ 21 cm² of dielectric; its life is ≈ 150× shorter than a 10⁻³ cm² test array's, and changes in β matter as much as changes in η.

6. **Charging recovers; chemistry and geometry do not.** Anneals repair most charge-induced traps; chlorine and grooves stay, so they are controlled by where and how much the etch creates.

---

## Study Questions

1. The TE TiN is accidentally broken into four quarter-wafer islands before module 1 by a particle scratch. Recompute the clamp voltage for one island if the bevel plasma delivers 12 mA to it. What if the island were 1 cm² of periphery TE with no array beneath it?

2. The bias in the ALE removal step is applied 10 ms after ignition instead of 150 ms, raising the injected charge per ignition to 10⁻⁵ C/cm². Compare the total with the main step's steady dose.

3. Using Weibull area scaling with β = 1.6 and β = 2.0, compute η(die)/η(test) for a 21 cm² die and a 10⁻³ cm² test array. Explain why the trim-without-O₃ split is unacceptable even though its η is 70% of the reference.

4. List the species of Section 13.4.2 that would be present in the array if the periphery clear's strip were skipped and the ILD deposited directly. Which would reach the capacitors, and how?

5. A device engineer reports a shift of the 10⁻⁶ retention point after a change to module 2, but array-centre leakage is unchanged. Which test structures would you check, and what would each tell you?

6. Explain why chlorine at the plate edge is tolerated, while fluorine in the trimmed array is held below 1 at%.

---

**Next Chapter:** [Chapter 14: Advanced Dielectrics & Architectures](./14-advanced-dielectrics-architectures.md)

---

**Chapter 13 Development Status:** Complete  
**Version:** 1.0
