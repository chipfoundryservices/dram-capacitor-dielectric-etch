# Chapter 6: Thermal & Vapor-Phase Etch Reactors

## Overview

A plasma cannot go where the dielectric is thinnest to reach. The ZAZ on the pillars of the array lies in channels 13 nm wide and 1.4 µm deep, behind support lattices and a top electrode that has not yet been deposited. Thinning that film, or stripping it for rework, needs a removal that works by gas transport alone: no ions, no sheath, no line of sight. Thermal atomic-layer etching is that process, and it needs a reactor of its own.

This chapter describes the reactor. It starts from what the process demands of temperature and gas, derives the dose that saturates the bottom of a channel of aspect ratio 109 and the number of cycles each task needs, sizes single-wafer, mini-batch, and batch configurations against the throughput each task requires, and sets out the materials, delivery, and effluent practice that HF, DMAC, and zirconium fluoride impose. The reactor serves modules T and R2, and in a form adapted for chlorine, module C (Chapter 9).

**Learning Objectives:**
- State the temperature, uniformity, and gas-switching requirements of HF/DMAC thermal ALE
- Derive the saturation time of a dead-end channel and apply it to HF and DMAC
- Design the cycle: dose, purge, and the check of the purge by residence time
- Compare single-wafer, mini-batch, and batch reactors for trim, finish, strip, and all-thermal clears
- Specify materials, gas delivery, and abatement for HF, DMAC, and metal fluorides
- Explain why a thermal etch leaves the dielectric amorphous

---

## 6.1 What the Process Demands

```
Thermal ALE reactor requirements (reference):
  Wafer temperature        280 °C ± 2 °C (3σ) across the wafer
  Wall / showerhead        150–200 °C (no condensation of ZrF₄ complexes or DMAC)
  Pressure                 0.5–2 Torr
  Gases                    anhydrous HF (0.1 Torr partial), DMAC vapor (0.05 Torr),
                           N₂ purge; no oxidant, no water
  Dose / purge             2 s dose, 3 s purge, each half-cycle; 10 s per cycle
  Gas-switch time          < 0.2 s (valves at the chamber)
  Materials                no quartz, glass, or silicon-based ceramics in contact with HF
```

### 6.1.1 Why ± 2 °C

The removal per cycle depends on temperature. Near 280 °C the logistic EPC(T) of Chapter 3 has a slope of 1.2% per °C:

```
dEPC/dT at 280 °C = 1.2% per °C  (equivalently 6% per 5 °C)

Temperature uniformity ± 2 °C  → removal ± 2.4%
  trim of 3 cycles (0.22 nm):         ± 0.005 nm
  strip of 80 cycles (5.5 nm):        ± 0.13 nm
  all-thermal clear (158 cycles):     ± 0.17 nm of 7.1 nm
```

The trim is limited not by temperature but by quantization: one cycle removes 0.073 nm, an EOT step of 0.0066 nm (1.3% of EOT). The smallest trim is one cycle.

### 6.1.2 Why the Film Stays Amorphous

Thermal ALE runs at 280 °C for minutes. The Avrami model of Chapter 2 gives τ(553 K) = 1.05 × 10⁸ s: a 13-minute strip crystallizes about 6 × 10⁻¹¹ of the film. The thermal etch does not crystallize the dielectric it leaves, and a trimmed film is as amorphous at the top-electrode deposition as an untouched one.

---

## 6.2 Dosing a Dead-End Channel

### 6.2.1 The Model

The ZAZ-coated forest is a network of channels, each a void between three pillars: an inscribed circle of 13 nm diameter and 1.41 µm of exposed height, closed at the bottom (AR = 109). Gas enters from the top. The saturation time derived in Chapter 2 for a closed tube of diameter d, with a front that advances by Knudsen transport and a surface that takes N_s per unit area, is

```
t_sat = 6 N_s AR² / (n₀ v̄)

HF:    M = 20 amu → v̄ = 765 m/s at 553 K
       p = 0.1 Torr = 13.3 Pa → n₀ = 1.75 × 10²¹ m⁻³
       N_s = F needed per cycle = 4 F per Zr × 0.23 ML × 8.3×10¹⁴ cm⁻² = 7.7 × 10¹⁴ cm⁻²
           = 7.7 × 10¹⁸ m⁻²
       t_sat = 6 × 7.7×10¹⁸ × 109² / (1.75×10²¹ × 765) = 0.41 s
       exposure 0.1 Torr × 0.41 s = 0.041 Torr·s = 4.1 × 10⁴ L

DMAC:  M = 87 amu → v̄ = 367 m/s
       p = 0.05 Torr → n₀ = 8.7 × 10²⁰ m⁻³
       N_s = 3.8 × 10¹⁸ m⁻² (assumed half that of F)
       t_sat = 6 × 3.8×10¹⁸ × 109² / (8.7×10²⁰ × 367) = 0.84 s
```

The 2 s pulses are 4.9× and 2.4× longer than these saturation times. The HF pulse is set by the saturation of the flat wafer (10⁵ L, Chapter 3); the DMAC pulse, with its smaller margin, is the one to watch.

### 6.2.2 Sensitivities

```
t_sat ∝ AR² / (p v̄);  at fixed p and M it scales with AR².

Taller mold (Book #31): 2.0 µm pillars, same 45 nm pitch
  AR = 2000 / 13 = 154   (factor 2.0 in AR²)
  HF   t_sat = 0.82 s   (margin 2.4× at 2 s)
  DMAC t_sat = 1.70 s   (margin 1.2× at 2 s)  ← marginal; raise to 0.10 Torr:
  DMAC at 0.10 Torr: t_sat = 0.85 s (margin 2.4×)
```

A narrower throat does not change the result by much. The 6 nm throats between nearest neighbours connect channels; if a whole channel were a tube of that width, AR would be 235 and t_sat for HF 1.9 s, still within a 2 s pulse. The throats are short and the channels are the long path.

### 6.2.3 What the Model Leaves Out

Sticking probability below one does not change the order of magnitude: at s = 10⁻³ the molecules diffuse deeper before reacting and the process is reaction-limited with a flat profile, at the cost of a longer dose. Support lattices with 50 nm openings add resistance in series, and the model's channel (d = 13 nm) is narrower than the lattice openings, so they do not dominate. The model is good to a factor of two; the verification is the uniformity of removal along the pillar, measured in Chapter 13.

---

## 6.3 The Cycle

### 6.3.1 Purge

The purge must remove HF before DMAC arrives; if both are present they react in the gas and deposit. The chamber's residence time sets the purge:

```
Chamber V = 4 L; pressure 1 Torr; N₂ purge 1000 sccm
  τ = pV/Q = 4 L × 1 Torr / (1000 sccm × 0.0127 Torr·L/s per sccm) = 0.315 s
  Purge 3 s = 9.5 τ → residual fraction e^(−9.5) = 7 × 10⁻⁵
```

The Knudsen transit time of the channel, L²/D_K = (1.4 µm)² / (13 nm × 765 m/s / 3) = 0.6 µs, is negligible; what limits the purge in the channel is not diffusion but the adsorption–desorption of HF on the fluoride layer, which is fast at 280 °C. The purge time is set by the chamber, not the forest. A larger chamber (a batch tool) needs longer.

### 6.3.2 The Cycle Count

```
Task                          Film         Cycles                  Time at 10 s
─────────────────────────────────────────────────────────────────────────────────
Trim 0.22 nm                  amorphous    3 × 0.073 nm            30 s
R2 finish, last 1.0 nm        tetragonal   1.0 × 1.3 / 0.045 = 29  4.8 min
Rework strip of ZAZ           amorphous    5.2/0.07 + 0.3/0.05 = 80  13.3 min
R3 all-thermal clear          tetragonal   (5.2/0.045 + 6) × 1.3 = 158  26 min
```

---

## 6.4 Reactor Configurations

### 6.4.1 Three Configurations

```
Configuration     Wafers    Cycle    Overhead per run    Notes
──────────────────────────────────────────────────────────────────────────────────
Single-wafer       1        10 s     60 s                heated pedestal, showerhead
Mini-batch         5        14 s     5 min               stacked pedestals; two-sided
Batch             25        20 s     20 min              vertical hot-wall, injectors
```

### 6.4.2 Throughput by Task

```
                                   Single-wafer   Mini-batch (5)   Batch (25)
Throughput per chamber or tool, wph:
  Trim, 3 cycles                      40             53              71
  R2 finish, 29 cycles                10             26              51
  Rework strip, 80 cycles              4             13              32
  R3 all-thermal, 158 cycles           2              7              21

Units needed for 139 wph at 85% availability:
  Trim (every wafer)                  4.1            3.1             2.3
  R2 finish                          15.9            6.4             3.2
  Rework strip                       39              12.9            5.1
  R3 all-thermal                     74.5            22.8            7.9
```

A single-wafer chamber is the right choice for the trim, which takes 30 s, and for rework, which is rare. For R2 the finish needs 16 single-wafer chambers or 3 batch tools: batch configuration is the only economical home for a thermal finish applied to every wafer. For R3 even the batch tool needs 8 units for the whole line; the route is practical for low volumes or for products whose dielectric cannot tolerate ions. The uniformity price of a batch is a slot-to-slot variation of removal, to be held at ± 3% (Chapter 15).

---

## 6.5 Hardware

### 6.5.1 Materials

HF at 280 °C attacks quartz, glass, and anything silicon-based. The reactor is built from nickel-plated or alumina-coated aluminium and stainless steel, with Y₂O₃ and AlF₃-passivated Al₂O₃ in places that see the gas. Fluorine converts alumina to a thin AlF₃ film, which is stable and protective; it will not convert zirconia that is coated on a wall (the ZrF₄ trap, Chapter 3), so zirconium-coated parts are cleaned with a chlorine process (Chapter 9) and not with the reactor's own HF.

```
Reactor materials (reference):
  Chamber / pedestal body     Al, Ni-plated; AlN pedestal with embedded heater
  Showerhead                  Ni or Al₂O₃-coated Al; temperature controlled to 180 °C
  Seals                       perfluoroelastomer or metal gaskets
  Valves, lines               heated to 120–150 °C (DMAC, HF); stainless, electropolished
  Windows                     sapphire (no quartz)
```

### 6.5.2 Delivery

```
Anhydrous HF         bp 19.5 °C; liquefied; delivered from a heated cylinder like BCl₃
                     (Book #32, Chapter 7); lines heated above the cylinder; low-ppm H₂O
DMAC                 liquid, bp 165 °C, vapor pressure ≈ 1.3 Torr at 25 °C; vapor draw from a
                     heated ampoule or direct liquid injection; lines ≥ 120 °C
N₂ purge             dry; point-of-use purifier
TMA alternative      pyrophoric; used only with the full hazard controls it requires
```

A line that is cooler than its source condenses the donor: the flow controller reads correctly and the chamber receives a pulse, as with BCl₃ in Book #32.

### 6.5.3 Exhaust and Abatement

The exhaust carries HF, DMAC, and sublimed metal complexes. The foreline is heated to 150 °C to keep the products in the gas phase to the abatement; a cold foreline fills with ZrF₄-containing solids and ligand residues. Abatement is a caustic wet scrubber for HF (forming KF) followed by thermal oxidation of the organic vapors. HF has a permissible exposure limit of 3 ppm and an immediately dangerous concentration of 30 ppm; the cabinet, the lines, and the reactor enclosure carry HF sensors with 1 ppm alarms, double containment, and interlocks that close the supply.

---

## 6.6 Remote-Plasma Variants

A remote plasma can supply radicals without ions to a chamber that has none of the geometry of a plasma reactor. Two uses relate to this book. A remote NF₃/H₂ plasma can generate HF in situ for the first half-cycle where handling cylinders of anhydrous HF is undesirable; the second half-cycle is unchanged. And a remote Cl₂/BCl₃ plasma can volatilize zirconia from the walls of an ALD chamber at 300–400 °C in a clean (Chapter 9). Neither puts ions on the wafer, and neither changes the dielectric's microstructure.

---

## 6.7 Failure Modes

```
Symptom                           Likely cause                       Effect
────────────────────────────────────────────────────────────────────────────────────────
Removal per cycle falls 6%        pedestal 5 °C low; heater zone     trim under-removes; strip leaves
                                  failed                             islands
Removal falls at the wafer edge   edge ring cool; showerhead         centre-to-edge gradient in EOT
                                  gradient
Removal falls with pillar depth   DMAC pulse short (margin < 1)      bottom of pillars untrimmed;
                                                                     non-uniformity along the pillar
Carbon in the film (> 1 at%)      DMAC decomposition at high T       leakage, instability
Particles after the reactor       cold foreline; ZrF₄/ligand flakes  particles on next chuck
Haze on the backside              HF with moisture on Si             surface roughness
Slot-to-slot variation (batch)    gas depletion down the stack       ± 5% removal slot to slot
```

---

## Summary and Key Takeaways

1. **Thermal ALE needs ± 2 °C and a tight valve.** The removal rises 1.2% per °C near 280 °C; ± 2 °C is ± 2.4%, and one cycle is a quantum of 0.073 nm.

2. **It leaves the film amorphous.** 13 minutes at 280 °C crystallizes 6 × 10⁻¹¹ of the film.

3. **A channel of AR 109 saturates in under a second.** HF 0.41 s at 0.1 Torr (4.1 × 10⁴ L), DMAC 0.84 s at 0.05 Torr; 2 s pulses give margins of 4.9 and 2.4.

4. **AR² sets the dose.** A taller mold (AR 154) pushes DMAC to 1.70 s, a margin of 1.2; doubling its pressure restores 2.4.

5. **Batch tools carry the thermal finish.** The R2 finish needs 16 single-wafer chambers but 3 batch tools for 139 wph; the all-thermal clear needs 8 batch tools.

6. **Materials and abatement are set by HF.** No quartz, heated lines, a heated foreline, a caustic scrubber, and HF sensors at 1 ppm.

---

## Study Questions

1. A 2.0 µm tall forest has AR = 154. Compute the saturation times for HF at 0.1 Torr and DMAC at 0.05 Torr. What pulse length restores a 2× margin on each?

2. A purge of 3 s must reduce HF by at least 10⁻⁵ in a chamber of 6 L at 1 Torr with N₂ at 800 sccm. Compute τ and the residual. How long a purge does the batch tool of Section 6.4.1 need at 20 L and 1500 sccm?

3. The pedestal runs 4 °C below its 280 °C setpoint. Compute the percentage change in EPC and the resulting change in the removal of a 3-cycle trim and of an 80-cycle strip.

4. Compute the number of single-wafer chambers needed for a thermal-ALE rework of 3% of 139 wph (4.2 wph of wafers), using the 14.3 min per wafer of Section 6.4.2.

5. A thermal reactor is to run the R2 finish for 139 wph of wafers with batch tools of 25 wafers and 24 cycles of 25 s each, plus 25 minutes of overhead. How many batch tools are needed?

6. Explain why a quartz window cannot be used on a thermal-ALE reactor, and what a sapphire window does and does not protect against.

---

**Next Chapter:** [Chapter 7: Dedicated Dielectric-Clear Chambers & the Strip-Then-Clear Route](./07-dedicated-dielectric-clear-chambers.md)

---

**Chapter 6 Development Status:** Complete  
**Version:** 1.0
