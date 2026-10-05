# Chapter 5: ICP Chambers & Ion-Energy Control for Nanometre Removal

## Overview

Module 2 runs in the chamber that has just etched the plate. The wafer arrives under Book #32's W and SiGe steps, and without leaving the chuck it goes through a TiN clear, a 45 s continuous BCl₃ main step at 150 eV, and 36 cycles of plasma ALE in which the chamber alternates every 4.5 seconds between a BCl₃ dose with no plasma and an argon plasma with ions at 60 eV. The chamber must therefore do three things that conductor etch chambers were not originally built for: deliver ions within a 30 eV window centred on 60 eV, switch gases and plasma state seventy times in under three minutes, and survive a chemistry that coats every cold surface with boron.

This chapter describes the inductively coupled plasma (ICP) chamber from the point of view of the dielectric clear: why ICP, how ion flux and energy are set, why the shape of the ion-energy distribution matters more for ALE than its mean, how fast gas switching and plasma re-ignition are achieved, and what all of this does to throughput.

**Learning Objectives:**
- Explain why the periphery clear runs in an ICP chamber with independent source and bias
- Compute ion flux and ion current from plasma density and temperature
- Estimate the width of the ion-energy distribution for sinusoidal and tailored bias, and the fraction of ions outside the ALE window
- Compute gas residence times and choose purge times for an ALE cycle
- Describe the transients of plasma ignition and matching in a cycled process
- Estimate the throughput of the plate chamber with the module 2 finish

---

## 5.1 Why an ICP

```
Requirement of module 2                     ICP                     CCP (dual-frequency)
──────────────────────────────────────────────────────────────────────────────────────
Independent flux and energy                 yes (source / bias)     partly
Ion energy 60 eV with high flux             yes                     low flux at low
                                                                    energy
Low pressure (5 mTorr) for anisotropy       yes                     usually 15–50 mTorr
Plasma off/on every 4.5 s                   re-ignites readily      re-ignites; slower
                                            at 5–20 mTorr           match
Same chamber as the W/SiGe/TiN steps        yes (Book #32)          no (conductor etch
                                                                    is ICP)
```

The decisive reason is the last line: the periphery clear is the end of the plate etch, and the plate etch is a conductor etch in an ICP. Moving the wafer to another chamber between the SiGe soft-landing and the ZAZ would expose a half-etched plate with resist to a vacuum transfer and a second chamber's first-wafer effects. Chapter 16 compares this with a split arrangement.

---

## 5.2 Ion Flux and Ion Energy

### 5.2.1 Flux

```
Γ_i = 0.61 n_e u_B,   u_B = √(kT_e / M_i)

Main step (BCl₃/Cl₂/Ar, 800 W, 5 mTorr):
  n_e ≈ 1.2 × 10¹¹ cm⁻³, T_e ≈ 3.5 eV, mean ion mass ≈ 82 amu (BCl₂⁺)
  u_B = √(3.5 × 1.6 × 10⁻¹⁹ / (82 × 1.66 × 10⁻²⁷)) ≈ 2.0 km/s
  Γ_i ≈ 0.61 × 1.2 × 10¹¹ × 2.0 × 10⁵ ≈ 1.5 × 10¹⁶ cm⁻² s⁻¹
  J_i ≈ 2.4 mA/cm²;  I_i (300 mm) ≈ 1.7 A

ALE removal step (Ar, 500 W, 5 mTorr):
  n_e ≈ 6 × 10¹⁰ cm⁻³, T_e ≈ 3 eV, M = 40 amu
  u_B ≈ 2.7 km/s;  Γ_i ≈ 1.0 × 10¹⁶ cm⁻² s⁻¹;  I_i ≈ 1.1 A
```

### 5.2.2 Mean Energy

The mean ion energy is the plasma potential plus the time-averaged sheath voltage at the wafer, which the bias supply sets:

```
E_i ≈ e(V_p + |V_dc|)       V_p ≈ 12–15 V

Main step:  E_i ≈ 150 eV → |V_dc| ≈ 135 V
ALE step:   E_i ≈ 60 eV  → |V_dc| ≈ 47 V
```

Bias power is a poor control variable, because the ion current changes with source power, gas, and wall state. Production chambers control the bias voltage (V_dc or the peak-to-peak voltage at the chuck) and let the power follow. In the reference chamber, the main step needs about 450 W of bias and the ALE step about 60 W.

---

## 5.3 The Ion-Energy Distribution

### 5.3.1 Why the Shape Matters

For the continuous main step, only the mean energy matters much: the rate varies by 0.9% per eV around 150 eV (Chapter 3), and ions at 130 or 170 eV etch at nearly the average rate. For the ALE removal step, the distribution matters a great deal. Ions below about 45 eV leave part of the modified layer; ions above about 75 eV sputter the unmodified ZrO₂ and the SiN beneath it (Chapter 4, Section 4.1.3). What matters is the **fraction of ions outside the window**.

### 5.3.2 Sinusoidal Bias

With a sinusoidal bias, an ion crossing the sheath in less than one RF period sees a sheath voltage that oscillates as it crosses. Light ions at low frequency follow the oscillation and arrive with a bimodal distribution spanning nearly the full voltage swing:

```
IEDF width for sinusoidal bias (illustrative):
  ΔE ≈ (sheath voltage swing) × f(τ_ion / τ_RF)

  Ar⁺ at E = 60 eV, sheath ≈ 0.4 mm:
    τ_ion (sheath transit) ≈ 60 ns
    13.56 MHz: τ_RF = 74 ns → ΔE ≈ 50 eV   (35–85 eV)
    40 MHz:    τ_RF = 25 ns → ΔE ≈ 17 eV   (52–68 eV)

  BCl₂⁺ at E = 150 eV (main step), 13.56 MHz: ΔE ≈ 40 eV (130–170 eV)
```

A bimodal distribution between E − ΔE/2 and E + ΔE/2 is approximated by the arcsine distribution:

```
F(x) = ½ + (1/π) arcsin[(x − E) / (ΔE/2)]

13.56 MHz, Ar⁺, E = 60, ΔE = 50:
  Fraction above 75 eV = ½ − (1/π) arcsin(15/25) = 0.5 − 0.205 = 29.5%
  Fraction below 45 eV = 29.5%
  → 59% of the ions are outside the ALE window

40 MHz, ΔE = 17:  all ions within 52–68 eV
```

### 5.3.3 What the High-Energy Tail Does

```
Effect of the 13.56 MHz Ar⁺ distribution on the reference ALE (illustrative):

                                   Tailored / 40 MHz    13.56 MHz sinusoidal
  ────────────────────────────────────────────────────────────────────────────
  β (Ar⁺ alone, nm/cycle)            0.004                 0.012
  EPC, ZrO₂ (nm/cycle)               0.100                 0.108
  Synergy                            96%                   89%
  SiN EPC (nm/cycle)                 0.015                 0.035
  ZrO₂:SiN                           6.7                   3.1
  Resist EPC (nm/cycle)              0.25                  0.40
```

The ions above 75 eV sputter. The SiN loss more than doubles and the self-limitation weakens. The ions below 45 eV do less harm; they lower the removal efficiency, which a slightly longer removal step recovers.

### 5.3.4 Tailored Waveforms

The reference chamber applies a **tailored bias waveform** in the ALE removal step: a periodic voltage, built from a fundamental and its harmonics or from a pulsed DC train with a short positive pulse to neutralize surface charge, that holds the sheath voltage nearly constant through most of each period:

```
Tailored bias (illustrative):
  Repetition 400 kHz; negative plateau ≈ 90% of the period
  ΔE ≈ 8–10 eV (FWHM) at E = 60 eV
  Fraction of ions outside 45–75 eV < 2%
```

The main step keeps its 13.56 MHz sinusoidal bias: at 150 eV a 40 eV spread is harmless, and the sinusoidal generator delivers the higher power more simply. The bias system therefore switches between two modes within one recipe, and the match must accept both (Section 5.5).

---

## 5.4 Gas Switching

### 5.4.1 Residence Time

```
τ = pV / Q

Reference chamber: effective volume V ≈ 40 L
1 sccm ≈ 0.0127 Torr·L/s

BCl₃ dose (20 mTorr, 200 sccm total = 2.5 Torr·L/s):
  τ = 0.020 × 40 / 2.5 = 0.32 s
Ar purge (20 mTorr, 300 sccm = 3.8 Torr·L/s):
  τ = 0.21 s
Ar removal step (5 mTorr, 200 sccm = 2.5 Torr·L/s):
  τ = 0.08 s
```

A purge of 0.75 s at 20 mTorr is about 3.5 residence times and reduces the BCl₃ partial pressure to about 3% of its dose value. The remaining BCl₃ in the removal step is not harmless: with the plasma on, it makes radicals, and a BCl₃ plasma at 60 eV is near the etch–deposition transition (Chapter 3). The removal step then deposits a little BₓClᵧ while it removes, and the EPC falls:

```
Residual BCl₃ fraction in the removal step vs purge time (illustrative):

  Purge (s)    Residual fraction    EPC (nm/cycle)
  ──────────────────────────────────────────────────
   0.25           30%                 0.07
   0.50           10%                 0.09
   0.75 (ref.)     3%                 0.10
   1.25          < 1%                 0.10
```

### 5.4.2 Delivery Hardware

```
Gas delivery for ALE (reference):
  Fast pneumatic valves at the lid, ≤ 20 ms actuation
  Separate injector for BCl₃; dead volume between valve and chamber ≤ 5 cm³
  BCl₃ line heated to 40 °C (vapour pressure ≈ 2.2 atm at 40 °C; avoids
  condensation in the line; Book #32, Ch. 7)
  Divert line: BCl₃ flows continuously to the foreline when not dosed, so
  the mass-flow controller does not restart every cycle
  Pressure control: throttle valve pre-positioned for each step;
  20 → 5 mTorr in ≈ 0.3 s
```

The divert line is what makes a 1.0 s dose reproducible. A mass-flow controller that starts from zero every 4.5 s overshoots and settles over about a second; with a divert, the flow is already stable when the valve to the chamber opens.

---

## 5.5 Plasma Ignition and Matching in a Cycled Process

Every ALE cycle turns the plasma off for the dose and purge, and on again for the removal step. Each re-ignition has a transient:

```
Re-ignition sequence (reference, removal step 2.0 s):
  0–40 ms      source RF on at preset match position; plasma ignites
               (inductive mode at 5 mTorr Ar)
  40–150 ms    density rises to steady state; frequency tuning of the
               source generator corrects the residual mismatch
  150 ms       bias on (tailored waveform), delayed so that ions do not
               arrive with the large energies of an unmatched, low-density
               sheath
  150–2000 ms  steady removal
```

Two rules come from this sequence. **First, the match must be preset, not tuned.** A mechanical match takes 0.3–1 s to find a new position; over 36 cycles that would waste a minute and make every cycle different. Frequency-agile generators with pre-stored match positions reduce the transient to tens of milliseconds. **Second, the bias must wait.** Applying bias to a plasma still forming gives a few milliseconds of high sheath voltage and a burst of energetic ions; over 36 cycles that burst is a measurable addition to SiN loss.

---

## 5.6 Materials for BCl₃ and Cycling

```
Chamber surfaces (reference):
  Walls and liner     anodized Al with Y₂O₃ plasma-spray coating, 120 °C
  Window              Y₂O₃-coated ceramic, heated
  Edge ring           quartz or SiC; Y₂O₃ for BCl₃-rich steps
  Chuck surface       Al₂O₃ ceramic (ESC)
  Gas injector        Y₂O₃-coated or sapphire
```

Two properties matter. **Al-containing surfaces exposed to the plasma emit Al**, which appears in the emission spectrum at the same lines as the Al₂O₃ marker used for endpoint (Chapter 8); Y₂O₃ coatings keep that background low. **Temperature** matters for deposits: walls below about 100 °C collect ZrCl₄ and BOₓClᵧ, which flake (Chapter 9). The reference keeps walls at 120 °C and the window above it.

---

## 5.7 Throughput

```
Plate chamber with module 2 (reference, single chamber):

  Step                                  Time (s)
  ─────────────────────────────────────────────────
  Waferless auto-clean (Ch. 9), wafer     40
  exchange, chuck, stabilize
  Book #32 conductor steps (W, SiGe,      123
  SiGe soft landing), incl. transitions
  TiN clear                               10
  Main step                               45
  Transition to ALE                        5
  ALE finish, 36 × 4.5 s                 162
  Dechuck, transfer to strip               15
  ─────────────────────────────────────────────────
  Total per wafer                        ≈ 400 s  →  9.0 wph per chamber

Without the ALE finish (continuous overetch, Book #32): ≈ 270 s → 13.3 wph
```

The ALE finish costs about a third of the plate chamber's throughput. Two hardware changes recover part of it: a shorter cycle (gas-switching and re-ignition times are about 1.5 s of the 4.5 s), and a split arrangement in which the ALE runs in a second chamber on the same platform while the first chamber etches the next plate. Chapter 16 compares the costs.

---

## Summary and Key Takeaways

1. **The clear runs where the plate is etched.** An ICP with independent source and bias serves the conductor steps, the 150 eV main step, and the 60 eV ALE without moving the wafer.

2. **Flux and energy are separate knobs.** Γ_i ≈ 1.5 × 10¹⁶ cm⁻² s⁻¹ in the main step and 1.0 × 10¹⁶ in the ALE step; energy is set by bias voltage, not power.

3. **ALE needs a narrow distribution.** A 13.56 MHz sinusoidal bias puts 59% of 60 eV Ar⁺ outside the 45–75 eV window and more than doubles SiN loss; a tailored waveform keeps the spread to about 10 eV.

4. **Purges set the residual BCl₃.** 0.75 s at 20 mTorr leaves 3%; shorter purges turn the removal step into a weak BCl₃ plasma and cut the EPC.

5. **Preset the match; delay the bias.** Re-ignition transients, repeated 36 times, must be milliseconds long and free of energetic bursts.

6. **The finish costs a third of the chamber.** About 400 s per wafer with ALE versus 270 s without; Chapter 16 prices the difference.

---

## Study Questions

1. Compute Γ_i and the ion current to a 300 mm wafer for an argon plasma with n_e = 8 × 10¹⁰ cm⁻³ and T_e = 2.8 eV. What bias power is needed for a mean ion energy of 60 eV if V_p = 12 V?

2. With a 13.56 MHz sinusoidal bias, the Ar⁺ distribution spans 35–85 eV. Using the arcsine distribution, compute the fraction of ions above 75 eV if the mean is lowered to 55 eV with the same width. Does lowering the mean solve the problem?

3. The BCl₃ purge is shortened from 0.75 s to 0.5 s to save time. Using the table in Section 5.4.1, compute the new rate in nm/min (cycle time 4.25 s) and the number of cycles needed for 3.6 nm. Is the change worthwhile?

4. Explain why a mass-flow controller with a divert line gives a more reproducible dose than one that starts from zero every cycle. Estimate the error in dose for a 1.0 s step if the controller overshoots by 30% for its first 0.3 s.

5. A chamber uses mechanical matching, taking 0.5 s to retune at each ignition. How much time does this add to the 36-cycle finish, and how would the plasma during that half-second differ from the steady removal step?

6. An alumina gas injector erodes in the BCl₃ steps. Explain how this would affect the Al-marker endpoint of Chapter 8 and the Al contamination of the periphery SiN.

---

**Next Chapter:** [Chapter 6: Chuck Temperature, Uniformity & the Clearing-Time Map](./06-chuck-temperature-uniformity.md)

---

**Chapter 5 Development Status:** Complete  
**Version:** 1.0
