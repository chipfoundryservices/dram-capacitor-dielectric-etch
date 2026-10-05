# Chapter 7: ALE & Thermal-Etch Reactors

## Overview

An ALE recipe is easy to write and hard to run. The reference D2 cycle asks the chamber to replace a BCl₃/Cl₂ plasma with an argon plasma and back again every 2.5 s, to clear the previous gas to below a percent in half a second, to switch the wafer bias on and off without overshooting a 25 eV window, and to do this 73 times per wafer and about five million times a year without the valves, the match, or the walls drifting. Thermal ALE removes the plasma and adds two reagents that are hazardous in different ways: anhydrous hydrogen fluoride and a pyrophoric aluminium alkyl, which must never meet in the gas phase.

This chapter describes the hardware that makes cyclic etching work: gas switching and residence time, RF synchronization and matching, ion-energy control in the removal step, the walls of a cyclic chamber, single-wafer and batch thermal-ALE reactors, and the monitoring and matching that keep the etch per cycle constant across chambers and over time.

**Learning Objectives:**
- Compute the purge time needed to reduce a residual gas to a given fraction, and design a chamber volume and purge flow to meet it
- Describe continuous-plasma and pulsed-plasma ALE and the matching requirements of each
- Explain why a narrow ion energy distribution matters for the ALE window and how tailored bias waveforms provide it
- Describe the hardware of single-wafer and batch thermal-ALE reactors and their safety requirements
- Estimate valve duty cycles and throughput for plasma and thermal ALE
- Set up monitors and matching criteria for cyclic processes

---

## 7.1 What ALE Asks of a Chamber

```
Requirements of the D2 cycle (reference):
  Steps per cycle                4 (A, purge, B, purge)
  Cycle time                     5.0 s
  Residual BCl₃/Cl₂ in step B    ≤ 1% of step A partial pressure
  Residual Ar dilution in step A not critical
  Bias in step B                 60 ± 3 eV mean; distribution inside 45–70 eV
  Bias in step A                 off; no stray bias from coupling
  Cycles per wafer               73
  Cycles per year (one chamber)  ≈ 9 wph × 8760 h × 0.85 × 73 ≈ 4.9 × 10⁶
  Valve actuations per year      ≈ 2 per gas per cycle → ≈ 1 × 10⁷ per valve
```

Ten million actuations per year is at or beyond the life of standard pneumatic process valves (typically 10⁶–10⁷ cycles). ALE chambers use ALD-class diaphragm valves rated for 10⁸ or more, mounted close to the chamber.

---

## 7.2 Gas Switching

### 7.2.1 Residence Time and Purge

A purge dilutes the previous gas exponentially with the residence time:

```
Residual fraction after purge time t:   f = exp(−t / τ),   τ = p V / Q

  Reference conventional chamber: V = 40 L, p = 20 mTorr, Q = 200 sccm
    τ = 0.020 × 40 / 2.53 ≈ 0.32 s
    t for f = 1%: 4.6 τ ≈ 1.5 s   ← too slow for a 0.5 s purge

  ALE chamber with confined volume and purge boost:
    V_eff = 15 L (confinement ring around the wafer), p = 15 mTorr,
    purge Ar 1000 sccm (12.7 Torr·L/s)
    τ = 0.015 × 15 / 12.7 ≈ 0.018 s
    t for f = 1%: ≈ 0.08 s   ← well inside 0.5 s
```

The design levers are a small plasma volume, a high purge flow, high pumping speed, and short gas paths. Dead volume between the switching valve and the chamber, a few cubic centimetres of line at a few torr, empties slowly and can bleed BCl₃ into step B for a second or more. Valves are mounted on the chamber lid, and the step-A gases flow continuously, switching between the chamber and a divert line to the foreline, so the mass-flow controllers never have to settle.

### 7.2.2 Pressure Switching

D2's step A runs at 20 mTorr and step B at 10 mTorr. A throttle valve takes 0.3–1 s to move to a new position and settle. ALE chambers pre-position the valve from a stored table at each step boundary, reaching the target within about 0.2 s. Some processes avoid the problem by running both steps at the same pressure, accepting a less-than-optimal condition for one of them.

### 7.2.3 The Cost of a Dirty Purge

```
Effect of residual BCl₃/Cl₂ during step B (illustrative):
  Residual    Added removal per cycle   EPC     Synergy   SiN EPC
  ──────────────────────────────────────────────────────────────
  0.1%         ≈ 0                       0.100   90%       0.012
  1%           0.002 nm                  0.102   88%       0.014
  5%           0.012 nm                  0.112   79%       0.022
  20%          0.05 nm                   0.15    ≈ 60%     0.05 (not ALE)
```

Chlorine present during the ion step lets the ions etch continuously. The EPC rises a little; what matters more is that the self-limiting property, and with it the selectivity to SiN and the insensitivity to ion energy, erodes.

---

## 7.3 RF Synchronization

### 7.3.1 Pulsed Versus Continuous Plasma

```
Two ways to run plasma ALE:
  Pulsed plasma      plasma off during purges; reignite each step
                     + no ion flux during purges
                     − reignition delay 20–100 ms; power and match
                       transients each step; 146 ignitions per wafer
  Continuous plasma  Ar plasma on throughout; BCl₃/Cl₂ added in step A;
                     bias pulsed only in step B (reference)
                     + no ignition; smooth match
                     − Ar plasma during step A and purges dilutes the
                       modification gas and adds low-energy Ar⁺
```

The reference runs a continuous source plasma with Ar flowing throughout. In step A, BCl₃/Cl₂ is added and the bias is off; the Ar⁺ arriving at the plasma potential (about 15 eV) is below every sputter threshold. In step B, the BCl₃/Cl₂ is diverted, the bias turns on, and Ar⁺ arrives at 60 eV.

### 7.3.2 Matching

The plasma impedance changes when the gas changes. A matching network with motor-driven vacuum capacitors needs 0.5–2 s to retune: far too long. ALE chambers use frequency-tuned generators that shift their frequency a few percent around 13.56 MHz to follow the load in about 10 ms, with the mechanical match held at a compromise position. The reflected power during the first 20–50 ms of each step is logged and monitored (Section 7.6).

### 7.3.3 Bias Turn-On

When the bias turns on at the start of step B, the sheath voltage can overshoot before the self-bias settles. An overshoot to 120 eV for 10 ms delivers about 0.4% of the step-B ion dose at an energy where unmodified ZrO₂ and SiN sputter. Bias is ramped up over about 50 ms, and the ramp is part of the recipe.

---

## 7.4 Ion-Energy Control in the Removal Step

### 7.4.1 Distribution Width

```
Ion energy distribution in step B (Ar⁺, 60 eV mean, illustrative):
  Sinusoidal 13.56 MHz bias        bimodal, peaks near 52 and 68 eV;
                                   ≈ 90% of ions inside 45–70 eV
  Tailored waveform (pulsed DC     single peak, 60 ± 3 eV;
  with ramp compensation)          > 99% inside 45–70 eV
```

With a 25 eV window, a bimodal distribution places part of the flux near each edge of the window. The high-energy peak is the one that matters: ions above 70 eV sputter unmodified oxide and nitride. Tailored waveforms, which hold the wafer surface at a nearly constant negative voltage during most of the RF period and neutralize it briefly with electrons, produce a narrow distribution centred where the recipe asks.

### 7.4.2 Qualification

Ion energy at the wafer is measured during qualification with a retarding-field energy analyzer built into a wafer-shaped probe, or inferred from the EPC-versus-bias curve on monitor wafers (Chapter 4, Section 4.2.3). The plateau's edges, measured in bias volts, are the chamber's ALE window; they are rechecked after every major maintenance.

---

## 7.5 Walls in a Cyclic Chamber

The walls see the same cycle as the wafer, at the plasma potential: chlorinated in step A, bombarded by 15 eV Ar⁺ in every step. They do not etch much, but they adsorb chlorine in step A and release it in step B, where it acts like a residual gas (Section 7.2.3).

```
Wall chlorine memory (illustrative):
  Wall 60 °C        Cl released in step B ≈ 2% equivalent residual
  Wall 100 °C       ≈ 0.5%
  Wall 100 °C,      ≈ 0.3%
  Y₂O₃ coating
```

Warm walls and yttria coatings minimize the memory. A chamber that has just been wet-cleaned has bare walls that adsorb more chlorine than a seasoned one; the first wafers after a clean run with slightly higher EPC and lower synergy until the wall saturates (Chapter 9).

---

## 7.6 Thermal-ALE Reactors

### 7.6.1 Reagents

```
Thermal-ALE reagents (reference HF / DMAC):
  HF          anhydrous, from a cylinder at ≈ 1 bar (bp 19.5 °C); highly
              toxic and corrosive; Monel or Hastelloy wetted parts; heated
              lines to prevent condensation
  DMAC        Al(CH₃)₂Cl, liquid, from a bubbler at 25–40 °C; pyrophoric;
              reacts violently with water
  Never mix   HF + DMAC in the gas phase → AlF₃ particles and CVD
```

### 7.6.2 Single-Wafer Reactor

```
Single-wafer thermal ALE (illustrative):
  Pedestal          275 °C, resistive, no RF
  Walls and lid     150 °C (limits HF and DMAC adsorption)
  Gas inlet         separate showerhead channels for HF and DMAC
  Cycle             HF 1 s / purge 5 s / DMAC 1 s / purge 5 s = 12 s
  Throughput        139 cycles ≈ 28 min per wafer → ≈ 2 wph per chamber
```

The long purges are set by HF, which adsorbs strongly on every surface and desorbs slowly. A shorter purge leaves HF to meet DMAC, and the reactor fills with AlF₃.

### 7.6.3 Batch Reactor

```
Vertical batch thermal ALE (illustrative):
  Load              100 product wafers + dummies, 6 mm pitch
  Temperature       275 °C, ± 1.5 °C over the load
  Cycle             HF 10 s / purge 20 s / DMAC 10 s / purge 20 s = 60 s
  Process           139 cycles ≈ 2.3 h; load, heat, cool, unload ≈ 1 h
  Throughput        100 wafers / 3.3 h ≈ 30 wph per reactor
  Uniformity        each pulse must saturate ≈ 14 m² of wafer surface (both faces);
                    dose at the top and bottom of the boat checked with
                    monitors
```

A batch reactor makes thermal ALE economically possible. It also etches both faces of every wafer, so the ZAZ on the bevel and on the outer backside, which no front-side plasma process reaches, comes off in the same step (Chapter 9). And it removes stringers from scribe topography. Against those advantages stands the isotropic undercut at the plate edge (Chapter 11), and a three-hour cycle with 100 wafers at risk in each load.

### 7.6.4 Spatial ALE

A third design separates the reagents in space rather than time: wafers on a rotating platen pass under zones of HF, inert curtain, DMAC, and inert curtain in turn. Each revolution is a cycle, and there are no purges in the time domain. Spatial reactors reach several cycles per second of rotation time per wafer, but the gas curtains must hold HF and DMAC apart to below 0.1% at 275 °C, and they are less mature for etching than for deposition.

---

## 7.7 Monitoring and Matching Cyclic Processes

### 7.7.1 Per-Cycle Traces

```
Fault-detection signals logged for every cycle (plasma ALE):
  Chamber pressure trace       purge depth; valve response time
  Source reflected power       match transients at each step boundary
  Bias V_pp in step B          ion energy
  OES Cl 837.6 nm in step B    residual chlorine (should be near zero)
  OES Ar 750.4 nm              plasma stability
```

A valve that slows by 50 ms, or a purge that leaves 3% chlorine, shows up in the per-cycle traces long before it shows up in the etch result.

### 7.7.2 Monitor Wafers

```
Monitors (illustrative):
  Daily        blanket crystallized ZrO₂ (20 nm, on SiN): EPC over 50 cycles,
               by ellipsometry; target 0.100 ± 0.003 nm
  Weekly       blanket SiN: EPC (selectivity check); target 0.012 ± 0.003
  After PM     saturation curves (step A and B times); ion-energy window
               (EPC vs bias); synergy (α and β runs)
```

### 7.7.3 Matching

```
Chamber matching criteria (plasma ALE):
  EPC ZrO₂                  ± 2% between chambers
  EPC SiN                   ± 0.003 nm
  Window edges (bias V)     ± 5 V
  Synergy                   ≥ 85%
```

Matched EPC means the same cycle count clears every chamber's wafers; the recipe does not need a per-chamber cycle count. Chambers that fall outside the EPC match get their cycle count adjusted only as a last resort, because a different count hides the cause.

---

## Summary and Key Takeaways

1. **ALE is a gas-switching problem.** A 0.5 s purge to 1% residual needs a small confined volume, a high purge flow, valves on the lid, and continuous flow with divert lines.

2. **Residual chlorine in the ion step erodes self-limitation.** A 5% residual cuts synergy from 90 to 79% and nearly doubles SiN loss.

3. **Continuous plasma with pulsed bias avoids reignition.** Frequency-tuned generators follow the impedance; bias ramps avoid overshoot.

4. **The ion energy distribution must fit the window.** Tailored-waveform bias keeps more than 99% of ions between 45 and 70 eV.

5. **Thermal ALE needs HF and a pyrophoric reagent kept apart.** Single-wafer reactors are too slow for production; batch reactors reach about 30 wph and clean bevels and backsides at the same time.

6. **Cyclic processes are monitored per cycle and matched on EPC.** Valve response, purge depth, and step-B chlorine catch drift before the etch result does.

---

## Study Questions

1. A chamber has V_eff = 25 L and a purge flow of 500 sccm at 15 mTorr. How long must the purge be for a 1% residual? For 0.1%? What cycle time results?

2. Using the table in Section 7.2.3, estimate the SiN loss over 73 cycles for residuals of 1% and 5%. Compare with the D1 landing loss.

3. A bias overshoot to 150 eV lasting 20 ms occurs at each step-B start. Estimate the fraction of the step-B ion dose delivered above 70 eV. If ions above 70 eV remove unmodified ZrO₂ at an EPC-equivalent of 0.3 nm per second of full flux, what is the added removal per cycle?

4. A batch thermal-ALE reactor runs 139 cycles at 60 s each with 1 h of overhead. How many reactors are needed for 139 wafers per hour at 85% availability? What is the work-in-process inside the reactors at any time?

5. Why are thermal-ALE purges limited by HF rather than by DMAC? What would change at a wall temperature of 200 °C?

6. Design a daily monitor for D1 (continuous etch) analogous to the D2 monitor of Section 7.7.2. What does it measure that the D2 monitor does not need to?

---

**Next Chapter:** [Chapter 8: Endpoint & In-Situ Monitoring of a 5.5 nm Film](./08-endpoint-in-situ-monitoring.md)

---

**Chapter 7 Development Status:** Complete  
**Version:** 1.0
