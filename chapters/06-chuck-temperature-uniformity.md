# Chapter 6: Chuck Temperature, Uniformity & the Clearing-Time Map

## Overview

The periphery clear is designed against its slowest site. The main step is timed so that it never clears the film anywhere on the wafer; the ALE finish is given enough cycles to remove the residue tail at the place where the most film remains. Both numbers come from one map: the **clearing-time map**, the time the continuous step would take to clear the ZAZ at each point of the wafer. Its shape comes from the incoming thickness of the dielectric and from the uniformity of the etch rate, and the etch rate's uniformity comes in large part from the chuck: its temperature zones, its edge ring, and the ion energy at the wafer edge.

This chapter builds the clearing-time map for the reference process, shows how it sets the main-step time and the ALE cycle count, describes how chuck temperature and the edge ring shape it, compares the uniformity of the continuous and cyclic steps, and explains how chambers are matched on a 5.5 nm film. It closes with the temperature uniformity needed for the thermal ALE of module 3.

**Learning Objectives:**
- Combine thickness and rate non-uniformity into a clearing-time map
- Compute the remaining thickness after a timed main step at the fastest and slowest sites
- Derive the ALE cycle count from the slowest site, the residue tail, and the target probability
- Estimate the rate sensitivity to chuck temperature and to edge ion energy
- Explain why the ALE finish is more uniform than the main step, and why that does not shorten it
- Set matching criteria between chambers for the periphery clear

---

## 6.1 The Clearing-Time Map

### 6.1.1 Two Contributions

The local clearing time of the continuous step is the local thickness divided by the local rate:

```
t_c(r, θ) = t(r, θ) / R(r, θ)

σ_tc / t_c = √((σ_t / t)² + (σ_R / R)²)

Reference (3σ, within wafer):
  ZAZ thickness (ALD)       ± 1.5%
  Main-step rate            ± 4.7%
  Clearing time             ± 4.9%  ≈ ± 5%
```

### 6.1.2 The Radial Shape

Most of the variation is radial and systematic:

```
Reference clearing-time profile (normalized to the centre, illustrative):

  r (mm)     Thickness    Rate     t_c      Note
  ─────────────────────────────────────────────────────────────────────
     0        1.000       1.000    1.000
    50        0.998       1.012    0.986
    90        0.997       1.020    0.977    fastest band (source coil
                                           maximum)
   120        1.002       1.008    0.994
   135        1.006       0.992    1.014
   142        1.010       0.975    1.036
   146        1.013       0.968    1.046    slowest band (edge ion energy,
                                           edge temperature)
  ─────────────────────────────────────────────────────────────────────
  Systematic range 0.977–1.046; with random and azimuthal terms, the
  3σ extremes are 0.95–1.05.
```

The ALD film is slightly thicker at the edge; the etch is slower there. Both push the same way, and the slowest sites lie in the outermost 5 mm of dies.

### 6.1.3 What the Main Step Leaves

The main step runs a fixed 45 s and removes 4.44 nm at the nominal site (Chapter 3). In nominal-rate nanometres, the film remaining at any site is the local clearing-time equivalent of 5.5 nm minus what was removed:

```
Remaining ≈ 5.5 × (t_c / t̄_c) − 4.44 nm

  Fastest site (0.95):    0.79 nm
  Nominal (1.00):         1.06 nm
  Slowest site (1.05):    1.34 nm
```

The main step must not break through at the fastest site, even at the low end of its grain distribution. With σ_rem = 0.35 nm (Chapter 3, Section 3.4.2), the fastest site's distribution reaches zero at about 2.3σ below its mean: about 1% of the grain sites at the fastest site see SiN for the last few seconds of the main step. That costs at most 0.3 nm of SiN on 1% of the area, which is acceptable. A 50 s main step would push that to about a fifth of the grain sites at the fastest site.

---

## 6.2 From the Map to the Cycle Count

```
N = ⌈ (R_slow + z σ_tot − b) / EPC ⌉

  R_slow   remaining at the slowest site           1.34 nm
  σ_tot    grain spread at the end of the finish   √(0.35² + 0.04²) = 0.352 nm
           (main-step spread + ALE spread, Ch. 4)
  z        residue target (Chapter 10)             6.4  (P ≤ 8 × 10⁻¹¹)
  b        extra removal in the first cycle        0.05 nm
  EPC                                              0.10 nm

  N = ⌈ (1.34 + 6.4 × 0.352 − 0.05) / 0.10 ⌉ = ⌈ 35.4 ⌉ = 36

Achieved z at the slowest site: (36 × 0.10 + 0.05 − 1.34) / 0.352 = 6.56
Achieved z at the nominal site: (3.65 − 1.06) / 0.352 = 7.36
```

Every term in the formula is a lever. The two that the chuck controls are R_slow, through the edge of the map, and σ_tot, through the temperature of the main step (Chapter 3, Section 3.4.1). Each 0.1 nm of R_slow is one cycle, 4.5 seconds.

---

## 6.3 Chuck Temperature

### 6.3.1 Rate Sensitivity

```
Main-step rate versus wafer temperature near 60 °C (from Chapter 3):
  R(60 °C) = 6 nm/min,  R(150 °C) = 12 nm/min
  d ln R / dT ≈ ln 2 / 90 ≈ 0.8% per °C

ALE EPC versus temperature near 60 °C:
  ≈ 0.1% per °C (both half-steps saturated)
```

The main step is eight times more sensitive to temperature than the finish.

### 6.3.2 Heat Load and the Wafer Temperature

```
Heat flux to the wafer (illustrative):
  Main step:   ion power 2.4 mA/cm² × 150 V ≈ 0.36 W/cm²
               + recombination, radiation, electrons ≈ 0.4 W/cm²
               total ≈ 0.8 W/cm²
  ALE removal: ≈ 1.6 mA/cm² × 60 V + ≈ 0.2 W/cm² ≈ 0.3 W/cm², 44% duty
  ALE dose:    ≈ 0

Wafer-to-chuck temperature rise (He backside 10 Torr, h ≈ 0.08 W/cm²/K):
  Main step:   ≈ 10 °C above the chuck surface
  ALE:         ≈ 2 °C average
```

The wafer is about 8 °C cooler during the finish than during the main step. That does not matter to the ALE, whose EPC barely depends on temperature. It matters to the main step's uniformity: if helium pressure varies across the wafer, or the chuck surface wears at the edge, the local temperature rise during the main step varies with it.

### 6.3.3 Zones

```
Reference chuck: four radial heater zones; ESC set point 60 °C

Temperature non-uniformity on the wafer during the main step (3σ):
  Zone-centre regions           ± 0.5 °C   → rate ± 0.4%
  Zone boundaries               ± 1.0 °C   → rate ± 0.8%
  Outer 3 mm (edge seal, ring   ± 2.0 °C   → rate ± 1.6%
  coupling)
```

Temperature contributes about ±1% (3σ) of the ±4.7% rate non-uniformity. The rest comes from ion flux, ion energy, and radical distribution. The temperature zones are nonetheless the most useful **tuning** tool, because they can be adjusted per chamber to flatten a radial rate profile that comes from the plasma.

```
Using the zones to correct the slowest band (illustrative):
  Rate at r = 146 mm is 3.2% low.
  Raising the outer zone by 4 °C:  +3.2% → flat to first order
  Side effect: TiN-clear and conductor steps run in the same chamber; the
  zone offset must be applied only during the main step, or it changes
  Book #32's profile at the plate edge.
```

Production chucks with fast zone response (a few seconds) allow per-step zone offsets. Slow chucks force one compromise setting for the whole recipe.

---

## 6.4 The Edge Ring and Edge Ion Energy

### 6.4.1 How the Ring Shapes the Edge

At the wafer edge, the sheath bends from the wafer to the edge ring. If the ring's top surface is level with the wafer and its electrical coupling matches, ions arrive at the extreme edge at the same energy and angle as at the centre. As the ring erodes, the sheath over the ring thins, the boundary curves, and ions at the wafer's outer few millimetres arrive at lower energy and with a tilt:

```
Edge ion energy versus ring erosion (main step, illustrative):
  ΔE_edge ≈ −1 eV per 50 RF-hours of ring life (at r ≈ 146 mm)

  RF-hours    ΔE_edge    Edge rate change    Slowest t_c    R_slow
  ──────────────────────────────────────────────────────────────────
     0          0           0                 1.046          1.34 nm
   150         −3 eV       −2.7%              1.075          1.47 nm
   300         −6 eV       −5.4%              1.105          1.64 nm
   450         −9 eV       −8.1%              1.137          1.81 nm
```

### 6.4.2 What It Costs

```
Cycles needed (Section 6.2) versus ring life:
     0 h:  36       150 h:  37       300 h:  39       450 h:  41

Without adjustment, at 300 h the reference 36 cycles give at the edge:
  z = (3.65 − 1.64) / 0.352 = 5.7  →  P ≈ 6 × 10⁻⁹ per grain
  ≈ 0.7 contact opens per die at the edge dies
```

An eroding ring turns into contact opens on the edge dies within a few hundred hours. The cure is in the hardware: an edge ring whose height is raised by an actuator as it erodes, or whose bias is tuned by a separate edge electrode, keeps ΔE_edge within ±1 eV over the ring's life. Where neither is available, the cycle count is raised with ring hours by feed-forward (Chapter 15).

### 6.4.3 Why the ALE Is Not Sensitive

The ALE removal step runs inside its window (45–75 eV). A 6 eV sag at the edge moves edge ions from 60 to 54 eV, still inside the window; the EPC changes by less than 1%. The finish is immune to the ring; the main step is not. **The ring's erosion is paid for in ALE cycles because it acts on the main step.**

---

## 6.5 Uniformity of the Two Steps

```
                                  Main step (continuous)     ALE finish
─────────────────────────────────────────────────────────────────────────────
Rate / EPC non-uniformity (3σ)    ± 4.7%                     ± 1.2%
  ion flux (± 5%)                 ± 3.5%                     ± 1.0% (94%
                                                              saturated)
  ion energy (± 3 eV)             ± 2.7%                     ≈ 0 (in window)
  temperature (± 1 °C)            ± 0.8%                     ± 0.1%
  BCl₃ / Cl distribution          ± 1.5%                     ± 0.4% (dose 96%
                                                              saturated)
Thickness removed                 4.44 nm                    3.6 nm
Removal non-uniformity (3σ)       ± 0.21 nm                  ± 0.04 nm
```

The finish is four times more uniform than the main step. It removes almost the same amount everywhere. That is exactly why it cannot shorten itself to suit the fast sites: it removes 3.6 nm at the slowest site because it must, and 3.6 nm at the fastest site because it cannot do otherwise, where it lands on SiN after about 8 cycles and etches SiN for the remaining 28 (Chapter 10).

---

## 6.6 Matching Chambers

A fab runs the plate etch in tens of chambers. A wafer's periphery clear must not depend on which chamber it went to:

```
Matching criteria for the periphery clear (reference):

  Parameter                              Match within        Why
  ──────────────────────────────────────────────────────────────────────────
  Main-step rate, blanket t-ZrO₂         ± 2%                R_slow ± 0.09 nm
  Main-step radial profile (edge band)   ± 1.5%              slowest site
  Main-step σ_r (grain spread proxy:     ± 10% relative      tail width
  roughness after partial etch)
  ALE EPC, blanket t-ZrO₂                ± 3%                removal capacity
  ALE EPC, SiN                           ± 0.005 nm/cycle    SiN loss
  Al-marker time (Chapter 8)             ± 0.5 s             main-step adaptation
  Edge ring RF-hours at qualification    < 100 h             edge ion energy
```

A chamber whose main-step rate is 2% slower than the fleet leaves 0.09 nm more at every site, about one ALE cycle. Rather than tune every chamber to identical rates, production adjusts the main-step time per chamber so that the removed thickness, not the time, is matched (Chapter 15).

---

## 6.7 Temperature for the Thermal ALE (Module 3)

The pilot trim runs in a thermal reactor at 250 °C. There is no plasma and no heat load; uniformity comes entirely from the heater:

```
EPC sensitivity (Chapter 4, Section 4.3.3):
  dEPC/dT ≈ 0.0008 nm/cycle per °C near 250 °C (≈ 1.3% per °C)

Heater uniformity ± 2 °C (3σ):  EPC ± 2.7%
Trim of 1.0 nm (17 cycles):     ± 0.027 nm from temperature
```

For a trim of 1.0 nm, temperature is a small contributor. The dominant non-uniformity inside the array is not radial at all: it is the variation of the trim from the top to the bottom of the channels between pillars, which depends on reactant transport (Chapter 12).

---

## Summary and Key Takeaways

1. **One map sets two numbers.** The clearing-time map (±5%, slowest at the edge) fixes the main-step time (fastest site must not clear) and the ALE cycle count (slowest site must clear its tail).

2. **N = ⌈(R_slow + zσ − b)/EPC⌉.** For the reference: 36 cycles, z = 6.56 at the slowest site.

3. **Temperature is a tuning tool, not the main cause.** 0.8% per °C on the main step; zones flatten a plasma-driven profile if they can be offset per step.

4. **The edge ring is paid for in cycles.** Each eV of edge ion energy is 0.9% of edge rate; 300 RF-hours of erosion costs three cycles or causes edge-die contact opens.

5. **The finish is uniform and inflexible.** ±1.2% EPC, immune to edge energy sag, but it removes the same 3.6 nm at the fastest site as at the slowest.

6. **Match removed thickness, not time.** Per-chamber main-step times keep R_slow common across the fleet.

---

## Study Questions

1. The ZAZ thickness non-uniformity rises to ±2.5% (3σ) after an ALD chamber change, with the rate unchanged. Compute the new clearing-time range and R_slow. How many ALE cycles are needed?

2. Using the profile in Section 6.1.2, at which radius would you place a monitor site to track R_slow? Why might a site at r = 146 mm on product not be representative of the very slowest grains?

3. A 4 °C offset in the outer zone flattens the main step. Compute the change in TiN-clear rate if that offset were left on during the TiN-clear step, assuming TiN in Cl₂ has an activation that gives 1.5% per °C. Would it matter?

4. An edge ring has 220 RF-hours. Compute ΔE_edge, R_slow, and the cycle count needed. If the fab uses fixed 36 cycles, estimate the contact-open rate per die at the edge dies.

5. Explain why the ALE finish's ±1.2% EPC uniformity cannot be used to reduce the number of cycles at the fast sites. What hardware or process change would let the fast sites stop earlier?

6. Two chambers have main-step rates of 6.0 and 5.85 nm/min. What main-step times give equal removal? If both run 45 s and 36 cycles, compute R_slow and z in the slower chamber.

---

**Next Chapter:** [Chapter 7: Bevel Etch Systems for High-k Removal](./07-bevel-etch-systems.md)

---

**Chapter 6 Development Status:** Complete  
**Version:** 1.0
