# Appendix G: Troubleshooting Guide

Symptom-driven guide for DRAM capacitor dielectric etch excursions. For each symptom: likely causes ranked from most to least common, checks to separate them, and corrective actions. Chapter references point to the underlying physics.

---

## G.1 Periphery Contact Opens Up, Single, Edge Dies

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. Edge-ring wear: edge ion energy down,   Ring RF-hours; edge-band rate on    Raise / replace ring;
   R_slow up (Ch. 6.4)                     blanket monitor; ladder intercept   apply ring-hour N(h)
2. Main step short: Al-marker bias from    Al baseline before the main step;   Remove Al source
   Al parts (Ch. 8.8)                      t_Al vs ALD thickness               (Y₂O₃ parts); limit
                                                                               adaptation
3. ZAZ thicker at the edge (ALD change)    ALD radial profile (SE pads)        Feed-forward x_w and
   (Ch. 6.1)                                                                   N_w; fix ALD
4. Chamber not matched (rate −2%)          Fleet comparison of n₅₀             Per-chamber main-step
   (Ch. 6.6)                                                                   time
```

## G.2 Periphery Contact Opens Up, Single, Whole Wafer

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. ALE EPC drop: purge short or valve      S₁ per wafer; purge-end pressure    Restore purge; fix
   slow (residual BCl₃) (Ch. 5.4)          per cycle (FDC)                     valve
2. Dose under-delivered (MFC, divert)      Dose pressure rise; B I line        Fix MFC/divert
   (Ch. 5.4.2)
3. BₓClᵧ micromasking: Cl₂ low in the      Cl₂ MFC log; TEM for B under        Restore Cl₂ fraction
   main step (Ch. 10.2.4)                  residue islands
4. Unseasoned wall after an O₂-final       WAC log; first-wafer rate           Restore season step
   clean (Ch. 9.2)
```

## G.3 Clusters of Contact Opens

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. Wall flakes (late in wet-clean          RF-hours since wet clean; flake     Wet clean; shorten
   interval) (Ch. 9.5)                     composition (Zr, B)                 interval
2. ALD flakes embedded in the ZAZ          TEM: ZrO₂ > 6 nm at the cluster;    ALD reactor clean
   (Ch. 9.5.3)                             ALD particle wafers                 (App. C.7)
3. BCl₃ hydrolysis particles               B(OH)₃ composition; cylinder        Purge, leak check
   (Ch. 9.5.1)                             change log                          (App. C.6)
```

## G.4 Opens Along Plate Outlines

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. Veil fragments: main step lengthened    Main-step time log; SEM of the      Restore main-step time;
   or energy raised (Ch. 10.6)             plate edge after strip              add 0.1% HF dip as a
                                                                               containment
2. Resist sidewall changed (litho)         Resist profile; Zr on sidewall      Litho fix
```

## G.5 Periphery SiN Loss High

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
Uniformly high:
1. ALE bias in sinusoidal mode (IEDF       Bias mode log; N₂ plateau per       Restore tailored
   tail) (Ch. 5.3)                         cycle                               waveform
2. Ar⁺ energy set high (> 75 eV)           V_dc log                            Restore 60 eV
High at fast sites only:
1. Main step too long (adaptation          t_main vs t_Al; ALD thickness       Clip adaptation;
   clipped wrong way) (Ch. 6.1.3)                                              check marker
```

## G.6 ILD Lifting or Haze in the Periphery

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. Boron left on SiN: strip H₂O off or     TOF-SIMS B on SiN; strip log        Restore H₂O and
   temperature low (Ch. 10.5)                                                  250 °C
2. Queue between strip and ILD > 24 h      Queue log                           Enforce queue
```

## G.7 Corrosion or Voids at the Plate Edge

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. Queue to strip in air (platform         Transfer log; TEM notch             Hold affected lots;
   fault) (Ch. 11.3)                                                           vacuum transfer
2. TE notch large: TiN-clear OE long,      Recipe log; TEM notch               Restore 2.5 s OE;
   main step long (Ch. 11.1)                                                   main step
3. SC1 in the post-strip clean              Wet-bench recipe                    Remove SC1
```

## G.8 Bevel Zr Above Limit

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. Lower PEZ ring wear: backside ion       V_pp trend; backside clearing on    Replace ring; RF trim
   energy down (Ch. 7.3.3)                 monitor wafer                       within ± 5%
2. ALD wrap extends past r = 147.0 mm      ALD seal and edge purge; backside   Fix ALD; widen backside
   (Ch. 2.6)                               thickness profile                   removal
3. Bevel chamber Zr loading (PEZ           Chamber clean log; Zr on a bare     Clean; parts swap
   deposits)                               wafer run
4. Zr picked up later (chuck, robot)       Backside VPD before and after       Clean handler; cover-
   (Ch. 9.4)                               each tool                           wafer WAC
Containment: bevel rinse for the affected lots (Ch. 7.5)
```

## G.9 Bevel Boundary Out of Specification

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
Too far in (< 148.7 mm):
1. PEZ gap opened (part wear, deposits)    Gap sensors; PEZ part hours         Adjust / replace
2. Pressure low; plasma deeper in gap      Pressure log                        Restore 0.8 Torr
Eccentric:
1. Centring offset drift                   Edge inspection 360° map            Re-teach centring
Wide staircase / haze ring:
1. Centre purge low (TiN creep)            Purge MFC                           Restore 2 slm
2. Cl₂ fraction low (boron ring)           Gas log; haze width                 Restore 20%
3. Queue to pre-clean > 24 h               Queue log                           Enforce; rework clean
```

## G.10 Edge-Die Defect Ring at r ≈ 147–149 mm

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. Flakes from the bevel staircase         SEM/EDX of flakes (SiGe on ZrO₂,    Pre-clean; narrow
   (boron-contaminated interface)          B)                                  transition; Cl₂
   (Ch. 11.4)                                                                  fraction
2. PEZ flakes from the bevel tool          Flake composition (Zr–B–O–Cl)       Bevel chamber clean
```

## G.11 Trim Out of Specification (Module 3)

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
Over-trim:
1. Temperature high                        Heater log; QCM EPC                 Restore 250 °C
2. Extra cycles                            Recipe log; interlock               Interlock
Bottom-to-top ratio low:
1. DMAC supply low (bubbler level, T)      Pressure rise per dose               Refill; temperature
2. Doses shortened                         Recipe log                          Restore 8 / 12 s
AlF₃ deposits in channels:
1. HF → DMAC purge short                   HF partial pressure at DMAC start   Restore purge
Leakage high after trim:
1. O₃ step skipped (F, C high)             XPS F, C on pads                    Interlock O₃ step
2. Groove deeper (reagent change)          TEM tomography                      Requalify reagent
```

## G.12 Main-Step Rate Drifting

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. Wall state (WAC order, season)          Cl/Ar ratio; WAC log                Restore WAC (App. C.5)
   (Ch. 9.2)
2. Chuck zone drift                        Zone temperatures; radial rate      Re-tune zones
3. Bias voltage control fault              V_dc log                            Fix bias control
4. ZAZ crystallinity change (SiGe          Al-marker timing vs thickness;      Feed-forward; notify
   furnace thermal budget)                 XRD on monitors                     furnace owner
```

---

**Appendix G Version:** 1.0
