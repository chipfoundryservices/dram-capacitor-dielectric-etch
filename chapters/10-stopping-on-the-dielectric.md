# Chapter 10: Stopping on the Dielectric — Conductor Overetch, Fluorine Skins & Surface Modification

## Overview

A stop is a selectivity at its limit: the etch is meant to remove the film above and none of the film below. Chapter 4 showed that the arithmetic asks for a TiN-to-ZAZ selectivity of at least 18 and that Cl₂/Ar at 40 eV delivers one of 110–180. This chapter asks what actually happens to the ZAZ in the 19 seconds it spends beneath the plasma at the fastest site, and what the stop leaves behind for the clear that follows.

The answer is that almost nothing is etched, and a good deal is modified. The loss in thickness is 0.03–0.05 nm, most of it a change in the surface layer; the ZAZ surface takes up chlorine; and, if the chamber remembers fluorine from the tungsten step, patches of ZrF₄ form that an ion-assisted etch at 60 °C cannot remove. The chapter quantifies each of these, shows why splitting the fluorine step from the stop step reduces the fluorine dose by two orders of magnitude, accounts for the sidewall of the plate during the stop (the SiGe foot and the TiN edge), and states the condition in which the ZAZ enters the hot clear. It closes with the deposition-mode fallback and the failure modes of the stop.

**Learning Objectives:**
- Decompose the ZAZ loss in the stop into tail-ion sputtering, surface modification, and chemical conversion
- Estimate the fluorine dose from wall memory and the ZrF₄ coverage it produces
- Explain why BCl₃ at 250 °C removes a ZrF₄ skin but a 60 °C ion-assisted step does not
- Account for the SiGe foot and the TiN edge during the stop, through to the end of the clear
- State the surface condition of the ZAZ at the start of P4
- Decide when to switch to the deposition stop

---

## 10.1 The Stop in the Route

```
P2 (reference):  BT BCl₃/Ar 70 eV, 6 s;  Cl₂/Ar 40 eV: TiN clears at 18.2 s ± 1.4 s (3σ)
                 step ends at 36.3 s (100% overetch relative to the measured t_c)

Exposure of the ZAZ to the Cl₂/Ar plasma:
  fastest site clears at 16.7 s → ZAZ exposed 19.6 s
  nominal site             18.2 s →                  18.2 s
  slowest site             19.6 s →                  16.7 s
```

Before the breakthrough the wafer has already been through the SiGe over-etch in HBr/O₂, which left the TiN covered by 1.0–1.5 nm of TiOₓNᵧ. The breakthrough acts on that oxide only, and no ZAZ is exposed until the TiN is gone at a site. After the TiN has cleared, the ZAZ sits under Cl₂/Ar ions at 40 eV for between 16.7 and 19.6 s, depending on the site.

---

## 10.2 What the ZAZ Loses

### 10.2.1 Tail Ions

A nominal ion energy of 40 eV is a peak, not a ceiling. The ion-energy distribution has a high-energy tail; for a collisional, bias-driven sheath, a few percent of the ions arrive above 60 eV. Those ions can etch zirconia:

```
ZrO₂ (tetragonal) in Cl₂ at 70 eV:  0.83 nm/min (BCl₃/Cl₂ model) × 0.3 (no B getter) = 0.24 nm/min
Tail fraction above 60 eV:           3–5%, mean energy about 70 eV
Effective rate:                      0.03–0.05 × 0.24 = 0.007–0.012 nm/min
Over the fastest site's 19.6 s:      0.0024–0.0039 nm
```

Tail-ion etching removes less than 0.004 nm, a tenth of the measured loss.

### 10.2.2 Surface Modification

The 0.03–0.05 nm that the in-situ ellipsometer reports is largely not removal. Ions at 40 eV drive chlorine into the outer nanometre of the film:

```
Modified layer after P2 (illustrative):
  Depth                      ≈ 0.5–1.0 nm
  Composition                ZrOₓCl_y; Cl ≈ 2–5 at% in the layer; O/Zr slightly < 2
  Density                    ≈ 3% lower than tetragonal ZrO₂
  Effect on ellipsometry     the fit reads the layer as slightly thinner or lower-index:
                             "apparent loss" 0.02–0.04 nm
  True removal               ≈ 0.004 nm (tails) + a few hundredths of a nm of oxygen
                             removal as ClO / O₂, i.e., ≈ 0.01 nm
```

The point to take is that the stop measures a modified surface, not a lost film. The modified layer is not a problem for the clear: it etches as ZrO₂ with a slightly higher rate, since chloride bonds are weaker. It is a signal that the stop's ion energy is rising or the chamber's chlorine is changing.

### 10.2.3 The Budget

```
ZAZ loss in P2 (reference, at the fastest site):
  Tail-ion sputtering         0.004 nm
  Oxygen removal              0.01 nm
  Apparent loss from surface modification  0.02–0.03 nm
  Total apparent              0.03–0.05 nm       (specification ≤ 0.3 nm; margin 6–10×)
```

---

## 10.3 Fluorine

### 10.3.1 Why It Is the Worst Contaminant of the Stop

The conductor etch begins with a tungsten step in SF₆. Fluorine adsorbs on the chamber wall and leaves it slowly, over minutes. If the TiN stop runs in the same chamber, F atoms from the wall reach the exposed ZAZ and form ZrF₄ (−201 kJ/mol per ZrO₂ for the HF route; strongly exothermic with atomic F). ZrF₄ sublimes at about 906 °C; at 60 °C and 40 eV it stays.

```
Wall fluorine memory after the W step (illustrative, one chamber for P1 and P2):
  n_F(t) = 10¹² cm⁻³ × [0.9 exp(−t/10 s) + 0.1 exp(−t/200 s)]     t from the end of W

Elapsed time at the start of P2:  SiGe ME 47 s + OE 25 s + transitions + BT 6 s ≈ 87 s
  n_F(87 s) = 10¹² × (0.9 e^(−8.7) + 0.1 e^(−0.435)) = 6.5 × 10¹⁰ cm⁻³ (the slow component)

Arrival flux:  Γ = ¼ n v̄,  v̄(F, 333 K) = 6.1 × 10⁴ cm/s
  Γ = 0.25 × 6.5×10¹⁰ × 6.1×10⁴ = 1.0 × 10¹⁵ cm⁻² s⁻¹

Reaction probability on ZAZ s = 10⁻³ (illustrative)
Dose over the 18 s of overetch at the nominal site (integrating the decay):
  F dose = 1.5 × 10¹³ cm⁻²    → Zr converted (4 F per Zr) = 3.8 × 10¹² cm⁻²
  = 0.45% of a monolayer (8.3 × 10¹⁴ cm⁻² per ML)
```

A coverage of 0.45% of a monolayer is invisible to any average measurement. It is, however, 38% of the periphery residue limit of 10¹³ Zr cm⁻² if it were left in place, and it is not distributed evenly: it forms patches around nucleation sites.

### 10.3.2 Splitting the Chambers

The fluorine reaching the ZAZ falls in proportion to n_F. If the tungsten step runs in a separate chamber, the stop chamber sees fluorine only from the wafer's own outgassing and the memory of any small F-carrying parts:

```
One chamber for P1 and P2:                Zr converted = 3.8 × 10¹² cm⁻²    (0.45% ML)
Separate F chamber (BARC, W) and Cl/Br
chamber (SiGe, P2), n_F × 10⁻²:          Zr converted = 3.8 × 10¹⁰ cm⁻²    (0.005% ML)
If only 40 s elapse between W and P2:     Zr converted = 4.8 × 10¹² cm⁻²    (0.58% ML)
```

The recommended hardware is a mainframe with a fluorine chamber for BARC and W and a chlorine/bromine chamber for SiGe and the TiN stop. It costs a transfer (about 15 s) and one more chamber per mainframe, and it reduces the zirconium fluoride coverage by a factor of 100. The same split removes the SiGe step's F memory (Book #32, Chapter 9: lateral etch up, top-of-sidewall bow).

### 10.3.3 Conversion in the Hot Clear

A ZrF₄ patch is removed in the hot BCl₃/Cl₂ step by conversion to the chloride, which sublimes:

```
ZrF₄ + 4/3 BCl₃ → ZrCl₄ + 4/3 BF₃     ΔH = −45 kJ/mol
  At 250 °C, ZrCl₄ (sublimation 331 °C) desorbs with ion assistance
  Patch: one monolayer of ZrF₄ ≈ 0.4 nm; at the hot clear's ≈ 12 nm/min equivalent:  2 s
```

In the ambient route (R0) the chemistry is the same but the temperature is 60 °C and ZrCl₄ does not desorb thermally; the conversion proceeds only with ion help, at a fraction of the ZrO₂ rate. The patch lifetime rises by about ten times: a 0.4 nm patch costs about 6–10 s of local delay, which is a local increase of the grain-level σ_g of Chapter 4. The hot step absorbs the same patch in under 2 s. AlF₃ is not converted by BCl₃ (+74 kJ/mol), but the Al₂O₃ layer lies under 2.6 nm of ZrO₂ and does not see fluorine in the stop.

---

## 10.4 Chlorine, Bromine, Carbon

```
Species on the ZAZ        Source                       After P2        After P3 (strip)   Effect in P4
──────────────────────────────────────────────────────────────────────────────────────────────────────────
Cl                        Cl₂/Ar ions (stop)           ≈ 3 × 10¹⁴      ≈ 6 × 10¹³         etches as ZrOCl; none
                                                        cm⁻² in 1 nm    (O radicals)
Br                        SiGe OE memory; HBr/O₂        ≈ 1 × 10¹³      ≈ 3 × 10¹²         ZrBr₄ sublimes at 357 °C,
                                                                                            26 °C above ZrCl₄:
                                                                                            leaves with ion help
C                         resist, BARC (P1)             ≈ 5 × 10¹³      < 1 × 10¹²         none (stripped)
F (Zr as ZrF₄)            wall memory                   ≈ 4 × 10¹² (1 chamber)  unchanged   converted in P4 (§ 10.3.3)
                                                        ≈ 4 × 10¹⁰ (split)
H₂O / OH                  air queue                     monolayer        monolayer           desorbs at 250 °C
```

None of these changes the clear except fluorine, and only in the ambient route. The strip is the step that clears the rest: oxygen radicals at 250 °C oxidize carbon and reduce chlorine by about 80%.

---

## 10.5 The Plate Sidewall During the Stop

The stop acts for 36 s on a plate whose sidewall is exposed: SiGe with its passivation, a TiN edge, and the W above, under resist. Two features of the sidewall change during P2 and are carried through to the end of the route.

### 10.5.1 The SiGe Foot

The Ge-rich foot of the SiGe (Book #32, Chapter 12) is exposed at the sidewall. In Cl₂/Ar without HBr or O₂ the SiOₓBrᵧ passivation of the sidewall is the only protection; at 40 eV the ions do not sputter it. A lateral rate of about 2 nm/min through the passivation (illustrative) over 36.3 s adds

```
Foot notch added in P2:     2 nm/min × 36.3 s / 60 = 1.2 nm
Foot notch from P1 (Book #32):  1.5–3 nm
Total foot notch:           2.7–4.2 nm       (failure threshold 5 nm)
```

The margin is 0.8 nm at the worst case. It is the reason a fallback exists (Section 10.7).

### 10.5.2 The TiN Edge

The TiN is cut vertically in P2; its edge is exposed thereafter. The TiN edge sees the stop's Cl₂ for the remaining overetch (about 18 s) and is then oxidized by the strip:

```
Lateral TiN etch in Cl₂ at 60 °C:            ≈ 3.5 nm/min × 18 s / 60 = 1.05 nm
Shell conversion in the strip:               1.8 nm TiOₓ from TiN, Pilling–Bedworth 1.7 → 1.06 nm of TiN
TiN recess before P4:                        2.1 nm
In P4 (hot):                                 shell etched at 2.0 nm/min × 37.8 s = 1.26 nm of 1.8 nm
                                              0.54 nm of shell remains; TiN not exposed
Final TiN recess                             ≈ 2.1 nm   (vs 4.2 nm in Book #32's integrated route)

Shell of 1.0 nm instead of 1.8:
  conversion 0.6 nm; recess before P4 1.6 nm; shell breached at 30 s;
  TiN etched at 70 nm/min for the remaining 7.8 s: 9.1 nm
  Final TiN recess ≈ 1.6 + 9.1 = 10.7 nm        (specification 15 nm)
```

The shell is a safety margin, not a measurement. A shell of 1.0 nm still meets the 15 nm specification, with 4 nm of margin; a thinner shell, or a P4 longer than 45 s, does not.

---

## 10.6 The ZAZ at the Start of P4

```
ZAZ entering the hot clear (reference):
  Thickness                        5.45 nm (apparent loss 0.05 nm)
  Outer 0.5–1.0 nm                 ZrOₓCl_y; Cl ≈ 6 × 10¹³ cm⁻² after strip
  Fluorine (as ZrF₄)               ≈ 4 × 10¹⁰ cm⁻² (split chambers); ≈ 4 × 10¹² (one chamber)
  Carbon                           < 1 × 10¹² cm⁻²
  State                            tetragonal; clean; hydroxylated if in air > 1 h
  Under the ZAZ                    120 nm SiN, flat
```

The clearing time of P4 is set from the ZAZ thickness. A loss in P2 of 0.05 nm changes it by 0.5% (0.1 s of 28 s). A loss of 0.3 nm would change it by 5.5% (1.5 s), which is within the Al-marker correction of Chapter 8 but has consumed the whole specification.

---

## 10.7 The Deposition-Mode Fallback

If the foot notch exceeds 5 nm, or if the ZAZ loss exceeds 0.15 nm, the stop can be run in BCl₃/Cl₂ below the transition (Chapter 4): boron passivates the SiGe foot and the ZAZ gains a BₓClᵧ film.

```
Deposition-mode P2 (illustrative):
  BCl₃ 40 / Cl₂ 20 / Ar 100;  40 eV;  TiN clears at ≈ 10 nm/min (lower rate: B film competes)
  ZAZ:   gains BₓClᵧ ≈ 0.3–0.7 nm in 20 s;  loss 0
  SiGe foot: passivated by B; added notch ≈ 0.2 nm (instead of 1.2 nm)
  Cost:   TiN step 30 s instead of 18 s; the boron film must be removed:
          strip converts it to B₂O₃ (hygroscopic); hot clear removes it in ≈ 3 s more
```

The deposition stop is more conservative for the ZAZ and for the foot, and more demanding on the strip (the B₂O₃ must not be left, because it is hygroscopic) and on the vacuum transfer to P4 (Chapter 7). It is held as a fallback because the film it leaves depends on the BCl₃ fraction and on the wall condition, which makes it harder to control than a threshold.

---

## 10.8 Failure Modes

```
Symptom                                Likely cause                          Control action
─────────────────────────────────────────────────────────────────────────────────────────────────
ZAZ apparent loss > 0.15 nm            ion energy up; F skin; wall F          check E; WAC; split chambers
Zr residue patches at the edge         F skin; slow clear at edge             hot clear with BCl₃; edge ring
                                                                              check
SiGe foot notch > 5 nm                 Cl₂ too long; passivation thin         shorten OE; HBr in P2; fallback
TiN notch > 15 nm                      shell thin; P4 long                    strip longer; E ≥ 74 eV
Stop does not stop: ZAZ thin           E high; BT energy hits ZAZ at          lower E; check BT; pinholes
at a site                              pinholes
Cl on SiN high after P4                strip short; no P5                    extend strip; P5
```

---

## Summary and Key Takeaways

1. **The stop loses 0.03–0.05 nm, and most of that is modification.** Tail-ion sputtering is under 0.004 nm; the rest is a chlorine-bearing outer nanometre that the ellipsometer reads as a thinner film.

2. **Fluorine is the contaminant that matters.** Wall memory over 18 s gives a dose of 1.5 × 10¹³ F cm⁻² and 3.8 × 10¹² Zr cm⁻² as ZrF₄ in a shared chamber: 0.45% of a monolayer and 38% of the periphery limit.

3. **Splitting the chambers reduces it by 100.** A separate fluorine chamber for BARC and W puts 3.8 × 10¹⁰ Zr cm⁻² of ZrF₄ on the ZAZ at the stop.

4. **Hot BCl₃ removes what ambient BCl₃ cannot.** ZrF₄ + 4/3 BCl₃ → ZrCl₄ is −45 kJ/mol; at 250 °C the chloride leaves in under 2 s, at 60 °C it takes ten times longer.

5. **The sidewall changes in the stop.** The SiGe foot gains 1.2 nm (total 2.7–4.2 nm against a threshold of 5 nm); the TiN edge ends at ≈ 2.1 nm if the shell holds and ≈ 10.7 nm if the shell is 1.0 nm.

6. **A deposition stop is the fallback.** BCl₃ below the transition passivates the foot and protects the ZAZ at the price of a boron film that the strip and the clear must remove.

---

## Study Questions

1. A chamber's ion distribution has a 10% tail above 60 eV, mean 75 eV. Using the Cl₂ model of Section 10.2.1 (ZrO₂ at 75 eV = 0.3 × the BCl₃/Cl₂ yield-model rate, K = 3.9 nm/s), compute the tail-ion removal at the fastest site.

2. The wall fluorine memory is 3× higher (n₀ = 3 × 10¹² cm⁻³). Recompute the F dose, the ZrF₄ coverage, and the fraction of the 10¹³ cm⁻² limit. Is the split-chamber fix still sufficient?

3. A line is changed so that P2 starts 40 s after the end of the W step. Compute the F dose and ZrF₄ coverage with the memory function of Section 10.3.1.

4. The strip is shortened to 42 s, giving a 1.5 nm shell. Recompute the TiN recess before P4, the shell life at 2.0 nm/min, the shell remaining at the end of a 37.8 s P4, and the final recess.

5. The SiGe foot has 3 nm from P1 and a lateral rate of 3.5 nm/min through the passivation in P2. Compute the total foot notch. Does it pass the 5 nm threshold, and what do you change?

6. Explain why a ZrF₄ patch and an AlF₃ patch behave differently in the hot clear, and why the Al₂O₃ layer is not exposed to fluorine in P2.

---

**Next Chapter:** [Chapter 11: The Dielectric Edge — Profile, Undercut, Overlap & Seal](./11-dielectric-edge-undercut-seal.md)

---

**Chapter 10 Development Status:** Complete  
**Version:** 1.0
