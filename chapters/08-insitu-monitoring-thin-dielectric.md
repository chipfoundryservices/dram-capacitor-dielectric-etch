# Chapter 8: In-Situ Monitoring & Etch-Amount Control for a 5 nm Film

## Overview

The dielectric etches of this book remove 5.5 nm of film, or 0.07 nm of it, or fail to remove 0.3 nm of it. An optical emission trace that is reliable for a 150 nm SiGe film is close to its noise floor for a film that is thirty times thinner, and for an etch that acts on a ring one tenth the area of the wafer. Two of the four modules have no plasma at all. Yet the specifications are tight: a ZAZ loss under 0.3 nm in the stop, a trim of 0.22 nm ± 0.03 nm, a clear that leaves no grain in 10⁸.

This chapter sets out what can be measured in situ for each module, and with what resolution. It sizes the optical-emission signal of the edge etch against that of Book #32's high-k step, develops the stop and clear endpoints for the strip-then-clear route, introduces in-situ ellipsometry on a pad as the thickness gauge of the stop and the trim, and describes cycle counting and witness-crystal monitoring for thermal ALE. It ends with the failure modes that a thin-film endpoint shares and the control actions each signal permits.

**Learning Objectives:**
- Compare the zirconium and aluminium emission signals of the edge etch, the integrated high-k step, and the hot clear
- Define an endpoint-relative overetch for the TiN stop and explain why it tracks drift
- Use in-situ ellipsometry to measure ZAZ loss during the stop to 0.01 nm
- Convert a quartz-crystal frequency shift into a removal per ALE cycle and its resolution
- Design cycle-count control of a trim, including quantization
- Identify what each sensor cannot see

---

## 8.1 What Each Module Must Know

```
Module   Quantity to be known                         Needed precision        Sensor
──────────────────────────────────────────────────────────────────────────────────────────
E        film cleared on the ring (end of clear)      ± 10 s of 121 s         time; OES Al marker as drift check
P2       TiN cleared in the open area                 ± 1 s                   OES: Ti I, N₂, Cl
P2       ZAZ lost during the stop                     ± 0.03 nm of 0.3        in-situ ellipsometry on a pad
P4       ZAZ cleared in the open area                 ± 0.6 s of 28 s         OES: Al I marker, Ti I trace
P4       shell and W consumed                         ± 0.2 nm               not in situ (XPS/TEM, Chapter 15)
T        removal per cycle; cycles to target          ± 3% EPC; 1 cycle      witness crystal; cycle counter;
                                                                              ellipsometry on a pad
```

Two of these, the shell and the W consumed, cannot be measured in situ; they are set by the strip time and the ion energy and verified off-line. The rest are the subject of this chapter.

---

## 8.2 Optical Emission

### 8.2.1 The Edge Etch Is a Weak Emitter

The OES signal from a species released by the etch is proportional to its release rate, the number of atoms per second leaving the surface. The edge etch and Book #32's high-k step release the same film, in different amounts:

```
Zr release rate (ZrO₂ at 1.44 × 10¹⁶ Zr cm⁻²):
  Edge etch:   66 cm² × 1.44×10¹⁶ / 93 s            =  1.0 × 10¹⁶ atoms/s
  Book #32 HK: 318 cm² × 1.44×10¹⁶ / 52 s (ZrO₂)   =  8.8 × 10¹⁶ atoms/s     (8.6× larger)

Al release rate (Al₂O₃ at 1.1 × 10¹⁵ Al cm⁻²):
  Edge etch:   66 cm² × 1.1×10¹⁵ / 8.8 s           =  8.3 × 10¹⁵ atoms/s
  Book #32 HK: 318 cm² × 1.1×10¹⁵ / 3.6 s          =  9.7 × 10¹⁶ atoms/s     (11.7× larger)
  Hot clear P4: 318 cm² × 1.1×10¹⁵ / 2.0 s         =  1.7 × 10¹⁷ atoms/s
```

The Al transient of the edge etch is twelve times weaker than the Al marker of Book #32, which was already a transient on a noisy baseline (Zr lines are "weak; rarely usable alone"). It is also confined to a ring at the wafer rim, so a window at the chamber wall sees only part of it, and its azimuthal position matters. Edge-etch endpoint is therefore **time-based**. The Al marker is retained as a drift check: the time of the Al peak, averaged over four azimuthal sensors, compared with its expected 47 s (42 s for the first ZrO₂ layer plus half of the 9 s Al₂O₃ layer); a shift of more than 10% flags a rate drift before the 1 × 10¹⁰ Zr limit does.

### 8.2.2 The Stop: Ti and N₂

The TiN clear is the best-behaved signal in the route. The 5 nm TiN film releases 2.4 × 10¹⁶ TiN units per cm²; over 318 cm² of open area clearing in 18 s, the release rate is 4.3 × 10¹⁷ per second, forty times the edge zirconium rate. Ti I (399.9, 453.3, 498.2 nm) and N₂ (337.1 nm), normalized to Ar 750.4 nm, fall when the TiN has cleared, and Cl I (837.6 nm) rises as Cl is no longer consumed (Book #32, Chapter 8).

```
P2 trace (Cl₂/Ar, 40 eV, illustrative):
   0–6 s    breakthrough (BCl₃/Ar): BCl, TiOₓ products; Ti I low
   6–24 s   TiN clearing: Ti I (453)/Ar high, falling from ≈ 16 s
   ≈ 18.2 s inflection of the Ti I fall = nominal clearing time t_c
   ≈ 20–22 s plateau: ZAZ exposed; Ti I at 5% of its high value
```

The wafer-averaged signal traces the cumulative distribution of clearing times, a normal distribution of mean 18.2 s and σ = 0.47 s (7.8%/3 × 18.2 s). Its inflection is at t_c; the plateau is reached at about 20 s.

### 8.2.3 Endpoint-Relative Overetch

The stop's overetch is not a fixed time but a multiple of the measured clearing time:

```
P2 end time = t_EP + OE × t_c,   t_EP ≈ t_c  (inflection),  OE = 100%
  nominal wafer:  18.2 + 18.2 = 36.4 s
  slow chamber (rate −10%):  t_c = 20.2 s → end 40.4 s
  fast chamber (rate +10%):  t_c = 16.5 s → end 33.0 s
```

Because the overetch tracks the clearing, the time that the ZAZ is exposed at the fastest site is the same fraction of the TiN etch whatever the drift: the TiN-equivalent overetch of Section 4.2.2 (5.4 nm) is preserved, and the ZAZ loss budget with it. A fixed-time step would give 36.4 s regardless: on a +10% chamber that is a 121% overetch before the spread; on a −10% chamber 80%. The endpoint-relative overetch removes that drift from the stop.

### 8.2.4 The Clear: Al Marker Without Resist

In P4 there is no resist, hence no CO (483.5 nm), CN, or hydrogen emission, and no resist-derived background. The hot clear's trace is that of a plate on SiN:

```
P4 trace (BCl₃/Cl₂/Ar, 250 °C, illustrative):
   0–13 s    first ZrO₂ layer (2.6 nm / 12 nm/min): BCl, Cl steady; Zr weak
   13–15 s   Al₂O₃ (0.3 nm at 9 nm/min): Al I 396.2 nm transient
   15–28 s   second ZrO₂ layer
   ≈ 26–30 s SiN exposed: N₂ 337 and SiCl 287 rise
```

The marker prediction of Book #32 applies: the Al peak at 14 s predicts a clear at 2 × 14 = 28 s, to which the 35% overetch is applied. The marker's centroid is known to about ± 0.3 s (the transient is ≈ 2 s wide, the sampling 0.1 s), so the predicted clear is good to ± 0.6 s, 2%, against a grain-level σ_g of 5%: the marker is accurate enough that the timing of the clear contributes little to the tail. The Al release rate of the hot clear (1.7 × 10¹⁷ per s) is the highest of the three modules, so the marker is the strongest here.

### 8.2.5 What OES Cannot See

As in Book #32, the signal is a wafer-area average with a noise floor of about 0.5% of the step amplitude. Zirconia grains that remain after the plateau cover 10⁻⁶ of the area and are invisible; the 38 s step ends when the overetch ends, not when a signal says so. The shell and the tungsten loss, which are edge and top features of a few nanometres, have no optical signature at all.

---

## 8.3 In-Situ Ellipsometry on a Pad

### 8.3.1 The Gauge

A spectroscopic ellipsometer with a spot of about 1 mm can be installed in the process chamber through two windows at 70° incidence. It needs a flat, large pad: a 2 × 2 mm monitor pad in the periphery of a central die, where the plate has been removed in the open area and the ZAZ lies on SiN. The ellipsometer measures the thickness of the film stack on the pad:

```
In-situ ellipsometry (illustrative):
  Spot             ≈ 1 mm on a 2 × 2 mm periphery pad
  Wavelengths      250–800 nm, acquisition 1 s
  Precision        ± 0.01 nm on 5.5 nm of ZAZ (1σ); drift-corrected against the SiN/Si
  Temperature      250 °C: n(T) shifts by ≈ 10⁻⁴ per K; ± 3 °C → thickness error 0.001 nm
                   (negligible); recalibrated on the hot chuck
  Not used on      the array (no flat pad), the edge ring (geometry), the plate top
```

### 8.3.2 Measuring the ZAZ Loss in the Stop

In P2 the pad's TiN clears about 18 s into the Cl₂ step and the ZAZ is then seen directly. From that moment the ellipsometer reads its thickness every second:

```
ZAZ thickness on the pad after TiN clears (reference):
  loss rate  ≈ 0.05 nm in 18 s (surface modification; Chapter 10)  → 0.003 nm/s
  precision  0.01 nm per reading; a straight-line fit of the 18 readings gives the loss over
             the 18 s exposure to ± 0.008 nm
  specification 0.3 nm → resolved 37:1; the reference loss of 0.05 nm is resolved at 6:1
```

The stop is therefore the first etch in the capacitor module whose primary quality metric is measured in the chamber, wafer by wafer. A ZAZ loss that grows, from 0.05 to 0.15 nm, flags a fluorine skin or a rising ion energy long before the clear shows it as a residue tail. A step in which the TiN does not clear on the pad at all is a hold.

### 8.3.3 Measuring the Trim

The same gauge, on a flat pad of ZAZ before the TiN deposition, can measure the thickness of the dielectric before and after a trim. Used in a thermal reactor, it reads the removal per cycle directly: the thickness after N cycles falls by N × EPC. The thermal chamber carries an ellipsometer on a 5 mm pad region and reports the actual removal; the cycle counter alone cannot (Section 8.4).

---

## 8.4 Monitoring Thermal ALE

### 8.4.1 No Plasma, No Emission

A thermal ALE chamber has no plasma and no OES. Three other sensors apply.

```
Sensor                    Measures                         Resolution                  Limit
────────────────────────────────────────────────────────────────────────────────────────────────
Cycle counter             cycles completed                 1 cycle (0.073 nm)          not the removal
Witness crystal (QCM)     mass removed per cycle           3.2 Hz per cycle at 6 MHz    drift; crystal temperature
Ellipsometry on a pad     thickness of the pad film        ± 0.01 nm                    pad; needs windows
```

### 8.4.2 The Witness Crystal

A quartz crystal coated with ALD ZrO₂ (20 nm, amorphous) sits at the pedestal edge at the wafer's temperature and is etched alongside the wafer. A removal of one cycle of 0.073 nm of ZrO₂ (5.3 g/cm³) is a mass of 38.7 ng/cm². The Sauerbrey relation for a 6 MHz crystal gives a sensitivity of 0.0815 Hz per ng/cm²:

```
Δf per cycle = 38.7 ng/cm² × 0.0815 Hz/(ng/cm²) = 3.2 Hz
Resolution 0.1 Hz (thermally stable crystal)  → EPC to ± 3% per cycle
```

At 280 °C a quartz crystal is at the edge of its range; a gallium phosphate crystal is the usual choice. The witness is not the wafer: its film is deposited separately and has a different history and surface. It measures the *relative* change in removal per cycle, EPC(t)/EPC(0), and so tracks a pedestal that is drifting cold (6% per 5 °C) or a DMAC pulse that is falling short.

### 8.4.3 Cycle-Count Control of a Trim

The trim target is a removal d_target on the wafer. The controller works from the EPC measured at the last calibration (on the pad, by ellipsometry, per lot) and the witness-crystal drift since:

```
N = round( d_target / EPC_now ),    EPC_now = EPC_cal × (witness EPC now / witness EPC at calibration)

Example: d_target 0.2 nm, EPC_cal 0.073 nm
  nominal:           N = round(2.74) = 3 cycles → 0.219 nm (+0.019 nm)
  pedestal 5 °C cool: EPC_now = 0.069 nm → N = round(2.90) = 3 → 0.207 nm
  pedestal 10 °C cool: EPC_now = 0.063 nm → N = round(3.17) = 3 → 0.189 nm
```

The quantization of one cycle, 0.073 nm, is the dominant uncertainty. A trim of 0.2 nm cannot be better than ± 0.037 nm; the specification of Chapter 1 (0–0.28 nm, ± 0.03 nm) is therefore met only when the target is close to a whole number of cycles, or when the removal per cycle is smaller than about 0.06 nm, for example at 265 °C (EPC 0.058 nm). Chapter 13 weighs these options.

---

## 8.5 Failure Modes of Thin-Film Monitoring

```
Symptom                              Likely cause                       Control action
───────────────────────────────────────────────────────────────────────────────────────────
Ti I does not fall at 18 s           TiN thick; rate low; oxide         hold; extend; check BT
Ti I falls early, plateau high       Ti on chamber wall (memory)        check wall; WAC
ZAZ loss on the pad > 0.15 nm        F skin; E too high; wall F         stop; check WAC; Chapter 10
Al peak shifts > 10%                 ZrO₂ rate drift (chuck T, wall)    adjust time; check chuck
Al marker absent in P4               ZAZ already gone; E very high      hold lot; check P2 loss
Ellipsometer reads thick after P4    BₓClᵧ film on the pad              extend P5; check B₂O₃
QCM EPC down 6%                      pedestal 5 °C cold                 recalibrate; check heater
QCM EPC drifts down per run          crystal coating consumed           replace crystal
Cycle counter OK, pad shows less     DMAC short; HF short; cold         trace pulse; raise p
removal
```

---

## Summary and Key Takeaways

1. **The edge etch is eight to twelve times weaker an emitter than Book #32's high-k step.** Zr release 1.0 × 10¹⁶ atoms/s against 8.8 × 10¹⁶; Al 8.3 × 10¹⁵ against 9.7 × 10¹⁶. Its endpoint is a time, with the Al marker as a drift check.

2. **The stop has the best signal.** TiN releases 4.3 × 10¹⁷ per s; the Ti I fall puts t_c at 18.2 s to ± 0.5 s.

3. **Overetch should follow the endpoint.** An endpoint-relative overetch keeps the TiN-equivalent overetch, and so the ZAZ loss, constant across a ± 10% rate drift.

4. **The Al marker is stronger in the hot clear.** 1.7 × 10¹⁷ Al per s with no resist background; the clear is predicted to ± 0.6 s (2%).

5. **In-situ ellipsometry measures the stop.** ± 0.01 nm per reading and ± 0.008 nm on the fitted loss resolve the 0.3 nm specification better than 30:1 and the 0.05 nm reference loss 6:1, wafer by wafer.

6. **A witness crystal gives EPC to ± 3%.** 3.2 Hz per cycle at 6 MHz; one cycle (0.073 nm) is still the quantum of the trim.

---

## Study Questions

1. Compute the Zr release rate of an edge etch whose zone is 80 cm² and clears in 110 s. By what factor is it below Book #32's 8.8 × 10¹⁶ atoms/s?

2. A chamber's TiN rate falls to 14.8 nm/min. Compute t_c, the endpoint-relative P2 end time, and the TiN-equivalent overetch at the fastest site (7.8% spread). Compare with a fixed 36.4 s step.

3. The Al peak in P4 occurs at 15.4 s. Predict the clear time and the step end time at 35% overetch. By what percentage has the ZrO₂ rate fallen?

4. A 6 MHz witness crystal shows a frequency shift of 2.9 Hz per cycle. Compute the EPC (ZrO₂ 5.3 g/cm³) and the pedestal temperature error (use 1.2%/°C).

5. A trim of 0.15 nm is requested at EPC = 0.073 nm. Find N and the actual removal, and the resulting error. What EPC would make N = 2 give exactly 0.15 nm, and what pedestal temperature does that imply?

6. Explain why OES cannot confirm that the periphery contacts will open, and which measurement can (Chapter 15).

---

**Next Chapter:** [Chapter 9: Zirconium Contamination, Chamber Walls & the ALD-Chamber Clean](./09-zirconium-contamination-ald-chamber-clean.md)

---

**Chapter 8 Development Status:** Complete  
**Version:** 1.0
