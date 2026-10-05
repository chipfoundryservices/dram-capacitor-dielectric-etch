# Chapter 13: Thinning, Trim & Rework

## Overview

Chapters 1 and 12 priced thickness. A dielectric thinned by 0.2 nm gains 3.8% of capacitance and pays for it with a factor 2.8 in leakage and a factor 3.0 in TDDB life. On those terms, thinning looks like a bad trade, and as a routine knob it is one. It earns its place in two other roles. As a **trim**, it corrects a lot whose ALD ran thick, returning it to the nominal thickness and no further; the leakage of that lot then matches its neighbours' instead of falling below them. As a **rework**, it strips a film that failed its specification entirely so that it can be deposited again.

This chapter builds both on the thermal ALE of Chapters 3 and 6. It shows that the correct policy for the trim is to remove the excess above nominal and to stop there, so that the leakage headroom is spent only by fluorine, carbon, and interface effects, a tenth of the amount that thinning below nominal would cost; it chooses the temperature at which the quantum of removal, one cycle, is smallest without making the process more sensitive to temperature than the chuck can hold; it checks the uniformity of removal along the pillar and across the wafer; it shows how the same reactor serves as the periphery's ALE finish and what that buys; and it counts the cost of a full rework to the electrode.

**Learning Objectives:**
- State the three reasons to etch the dielectric on purpose and the policy that governs each
- Compute the fraction of lots that need a trim from the ALD thickness distribution
- Account for the leakage headroom spent by a trim above and below nominal
- Choose a trim temperature from the granularity and temperature sensitivity of the removal per cycle
- Relate the dose margin to the uniformity of removal along the pillar
- Estimate the benefit of an ALE finish to the periphery clearing tail
- Count the electrode and capacitance cost of a rework

---

## 13.1 Three Reasons to Etch the Dielectric

```
Purpose              What is removed                        Policy
────────────────────────────────────────────────────────────────────────────────────────────
Trim                 0.07–0.22 nm, from over-thick lots      remove the excess above nominal;
                                                              never below nominal without approval
Rework               all of the film (5.5 nm), then redeposit   at most one per wafer
Finish (module P)    the last ≈ 1 nm of the periphery film     R2 only; not a trim (Chapter 6)
```

A fourth, to tune EOT as a product knob in the way that the ALD cycle count is a knob, is not on the list. It is ruled out by Chapter 12: the thinner film's leakage and TDDB cost are not recoverable, and the quantum of 0.073 nm is too coarse a step for tuning.

---

## 13.2 The Trim as an Equalizer

### 13.2.1 Where the Excess Comes From

The ALD thickness has a 3σ spread of ± 0.2 nm across a lot population: σ_lot = 0.067 nm. A lot that is 0.2 nm thick has a capacitance 3.6% below nominal and a leakage 2.8× below nominal. The capacitance is the problem; the lower leakage is a bonus the cell does not need.

```
Lot thickness distribution:  Δt ~ N(0, σ = 0.067 nm)    (3σ = ± 0.2 nm)
Lots with Δt > 0.073 nm (one cycle):   13.7%
Lots with Δt > 0.10 nm:                  6.7%
Mean excess of those above one cycle:    0.107 nm
σ_C / C from thickness alone (1σ):       0.0907 × 0.067 / 0.499 = 1.2%
```

About one lot in seven would be trimmed, by one to three cycles.

### 13.2.2 Trim to Nominal, Not Below

The headroom of Chapter 1 (0.28 nm) is the leakage a lot may add *above the nominal leakage*. A lot that is 0.2 nm thick already has 0.2 nm less leakage than nominal. Removing the excess returns it to nominal and spends nothing:

```
Lot excess    Cycles    Removed     Ends at     Leakage vs nominal    Headroom spent
                         (nm)       (vs nominal)                     (thickness) + F/C + interface (0.05)
─────────────────────────────────────────────────────────────────────────────────────────────────
+0.15 nm        2       0.146       +0.004 nm       0.98×                0.00 + 0.05 = 0.05 nm
+0.20 nm        3       0.219       −0.019 nm       1.10×                0.019 + 0.05 = 0.07 nm
+0.10 nm        1       0.073       +0.027 nm       0.87×                0.00 + 0.05 = 0.05 nm
Trimming a nominal lot by 3 cycles:                                                  0.22 + 0.05 = 0.27 nm
```

A trim of an over-thick lot to nominal spends 0.05–0.07 nm of the 0.28 nm headroom, a quarter, almost all of it fluorine, carbon, and interface effects. The same three cycles on a lot already at nominal would spend 0.27 nm, nearly all of it. The policy is therefore a *decision* made from a measurement: the ALD thickness of each lot (ellipsometry or XRF, ± 0.03 nm) sets the number of cycles N = round((t_meas − t_nom) / EPC), and N = 0 for any lot within one cycle of nominal.

### 13.2.3 The Payoff

Trimming the 14% of lots that exceed one cycle truncates the upper tail of the thickness distribution at about +0.04 nm (half a cycle) and reduces the spread of C_s. The gain is modest, the capacitance of the worst 3% of lots rising by up to 3.7%, and it matters at the capacitance specification limit (8.3 fF against a mean of 8.6 fF) where lots on the thick side are the ones near the edge.

---

## 13.3 Granularity and Temperature

### 13.3.1 The Quantum of Removal

The removal per cycle sets the step by which a trim can be adjusted. A smaller step is easier to centre on a target; it also tends to be more sensitive to temperature, because the process is lower on its steep curve:

```
T (°C)    EPC (nm)    EOT per cycle (nm)    d ln EPC/dT     ± 2 °C       Cycles for 0.20 nm
──────────────────────────────────────────────────────────────────────────────────────────────
250        0.041        0.0037               2.7% /°C        ± 5.4%        4.9 → 5
265        0.058        0.0053               1.9% /°C        ± 3.8%        3.4 → 3
280 (ref)  0.073        0.0066               1.2% /°C        ± 2.4%        2.7 → 3
```

At 265 °C the removal per cycle is 0.058 nm, so the spacing between reachable removals is 0.058 nm and any target is within ± 0.029 nm of one of them: three or four cycles (0.174 or 0.232 nm) cover every target from 0.14 to 0.26 nm within ± 0.03 nm. At 280 °C the spacing is 0.073 nm and the worst-case error is ± 0.037 nm, which fails the specification. The temperature sensitivity at 265 °C, ± 3.8% for ± 2 °C (± 0.007 nm on 0.17 nm), is small against the quantum. At 250 °C the quantum is smaller, but ± 5.4% on five cycles gives ± 0.011 nm, and the margin on the temperature controller is smaller. The reference of Chapter 3 is 280 °C for the full strip, where the quantum does not matter. For the trim, **265 °C** is the better choice: a separate recipe on the same reactor, with the pedestal held within ± 2 °C of a different setpoint.

### 13.3.2 Fractional Cycles

A shorter DMAC pulse removes a fraction of the saturated amount. It does not help: the removal is then no longer self-limiting, it depends on the dose, and the dose varies along the pillar (Section 13.4). A fractional cycle gives a finer step and loses the property that makes thermal ALE worth using. The recipe keeps both pulses above saturation.

---

## 13.4 Uniformity

### 13.4.1 Along the Pillar

The saturation front of the DMAC reaches the bottom of the 13 nm channel in 0.84 s at 0.05 Torr (Chapter 6). The pulse is 2 s, a margin of 2.4. In the tube model the saturated length scales as the square root of the margin:

```
Dose margin M = t_pulse / t_sat(bottom):   saturated length fraction = min(1, √M)

  M      saturated fraction     unsaturated bottom of the pillar
 2.37       1.00                    0
 1.5        1.00                    0
 1.0        1.00                    0
 0.8        0.89                    11% (partial removal)
 0.5        0.71                    29% (partial removal)
```

With a margin of 2.4 the model gives a flat removal, and because the model is good only to a factor of two, the reference keeps the margin above 1.5. A taller mold (AR 154) at the same pressure has a margin of 1.2 (Chapter 6), which is above 1 but under the 1.5 rule: the DMAC pressure is raised to 0.10 Torr, giving a margin of 2.4 again. The verification is a measurement of the dielectric thickness at the top, middle, and bottom of a pillar by cross-section TEM on a trimmed monitor: the removal at the three heights should agree within 10%.

### 13.4.2 Across the Wafer and Between Wafers

```
Source                          Variation of removal       Control
────────────────────────────────────────────────────────────────────────────────
Wafer temperature (centre-edge)  ± 2 °C → ± 3.8% at 265 °C   multizone pedestal; edge ring
Gas supply (showerhead)          ± 2%                         flow split; pulse timing
Slot to slot (batch)             ± 3–5% (depletion)           gas direction; slot-dependent dose
Wafer to wafer (pedestal drift)  witness-crystal EPC (Ch. 8)  recalibrate per lot
Total (3σ)                       ± 5–6% of the removal
```

On a removal of 0.17 nm, ± 6% is ± 0.010 nm, one sixth of the cycle quantum at 265 °C. Uniformity is not the limit of the trim; the quantum is.

---

## 13.5 The ALE Finish of the Periphery (R2)

The same reactor serves module P in the R2 route. After the hot clear leaves about 1 nm of ZrO₂ as islands, 29 cycles at 0.045 nm per cycle (tetragonal) with 30% over-cycling complete the clear. The relevant statistic is the relative spread of the removal per cycle, σ_EPC:

```
Clearing probability after the ALE finish, over-cycling 30%:   z = 0.30 / σ_EPC

 σ_EPC    z      P (grain left)      Opens per die (3×10⁷ contacts × 4 grains)
 3%       10.0   7.6 × 10⁻²⁴         ≈ 10⁻¹⁵
 4%        7.5   3.2 × 10⁻¹⁴         3.8 × 10⁻⁶
 5%        6.0   9.9 × 10⁻¹⁰         0.12
R1, hot clear alone (σ_g 5%, OE 35%):  z = 7.0   1.3 × 10⁻¹²   1.5 × 10⁻⁴
```

If the removal per cycle is uniform to 4% (the witness crystal measures it to ± 3%, Chapter 8), the finish reduces the die-level opens from 1.5 × 10⁻⁴ to 3.8 × 10⁻⁶, a factor of 40. If it is uniform to 5% it is worse than the hot step alone. The benefit exists only if σ_EPC is measured and held below the grain-level spread of the dry step, and the cost is 4.8 minutes of reactor time per wafer (Chapter 6) and 1.3 nm of lateral undercut at the plate edge (Chapter 11).

---

## 13.6 Rework

### 13.6.1 The Strip

```
Rework strip (amorphous ZAZ, 280 °C, 10 s cycle):
  Cycles to clear:   5.2 nm / 0.07 + 0.3 nm / 0.05 = 74 + 6 = 80
  Over-cycle 10%:    88 cycles → 14.7 min        (no grain tail: the film is amorphous)
  Cycles with TiN exposed:   about 8
```

### 13.6.2 What It Costs the Electrode

After the ZAZ is gone the TiN pillar is exposed to HF/DMAC for the remaining cycles, and it is then covered by a fresh ALD film that re-oxidizes its surface. The loss per side of the pillar from one strip-and-redeposit sequence:

```
TiN etched in the over-cycle:          8 cycles × 0.003 nm = 0.02 nm per side (assumed)
TiOₓNᵧ interface removed and regrown:  consumed TiN of the new interface layer ≈ 0.15 nm per side
Total per rework:                      ≈ 0.2 nm per side
```

```
Pillar radius 14 nm → 13.8 nm:   dielectric area −1.43%   C_s 8.6 → 8.48 fF
After two reworks:                                       8.35 fF
After three reworks:                                     8.23 fF   (< 8.3 fF specification)
```

The limit of one rework per wafer in Chapter 1 follows: two reworks put C_s at 8.35 fF, 0.05 fF above the specification, with nothing in hand for the thickness spread. The rework also repeats the queue limit before the top electrode and doubles the ALD cost for that lot.

### 13.6.3 What Triggers a Rework

```
Trigger                                   Action
──────────────────────────────────────────────────────────────────────────────────
ALD thickness out of ± 0.5 nm              rework (too far for a trim)
ALD composition wrong (Al layer missing)   rework
Particles / flakes from the ALD chamber    rework if > limit on the pillar; else scrap
Surface contamination before TiN           rework only if the contamination is on the ZAZ
Queue limit exceeded                       oxidizing treatment first; rework if that fails
```

---

## 13.7 Rules

```
Trim rules (reference):
  1. Measure each lot's ALD thickness (± 0.03 nm); compute N = round((t_meas − t_nom)/EPC)
  2. N = 0 within one cycle of nominal; N ≤ 3 at 265 °C or ≤ 2 at 280 °C
  3. Never trim below nominal without written approval; the headroom is 0.28 nm
  4. Run the oxidizing step after any trim (Chapter 12.6)
  5. Check EPC from the witness crystal every lot; trim-dose arrays every month
Rework rules:
  1. At most one rework per wafer; record it
  2. Measure C_s on the monitor after top-electrode deposition for reworked lots
  3. Rework before the top electrode only; after it the film is buried
```

---

## Summary and Key Takeaways

1. **Thinning is a recovery, not a knob.** A trim of 0.2 nm gains 3.8% C_s and costs 2.8× in leakage and 3.0× in TDDB life; used on lots that are already thick it costs almost none of that.

2. **Trim to nominal, not below.** About 14% of lots exceed one cycle; trimming them to nominal spends 0.05–0.07 nm of the 0.28 nm headroom, against 0.27 nm for the same trim on a nominal lot.

3. **265 °C is the trim temperature.** 0.058 nm per cycle and ± 3.8% for ± 2 °C: a finer quantum than 280 °C (0.073 nm, ± 2.4%) without the 5.4% sensitivity of 250 °C.

4. **Keep both pulses above saturation.** A fractional cycle gives a finer step and loses the self-limiting uniformity; the DMAC margin along the pillar must be ≥ 1.5.

5. **The ALE finish helps only if σ_EPC is below 5%.** At 4% it cuts the die-level opens 40× (1.5 × 10⁻⁴ to 3.8 × 10⁻⁶); at 5% it makes them worse.

6. **One rework per wafer.** Each costs about 0.2 nm of pillar radius per side and 1.4% of C_s; the third would take C_s below 8.3 fF.

---

## Study Questions

1. A lot's ALD thickness is 0.17 nm above nominal. Compute the number of cycles at 280 °C and at 265 °C, the thickness after each trim relative to nominal, and the headroom spent in each case (add 0.05 nm for F, C, and interface).

2. From the lot distribution of Section 13.2.1 (σ = 0.067 nm), compute the fraction of lots that need N = 1, N = 2, and N = 3 cycles at 280 °C, using N = round(Δt/EPC) for lots whose excess exceeds one cycle (0.073 nm).

3. The DMAC partial pressure is 0.03 Torr and the pulse is 2 s on AR = 109. Compute the dose margin and the unsaturated fraction at the bottom of the pillar. What pulse restores a margin of 1.5?

4. The witness crystal shows σ_EPC = 4.5% on the R2 finish with 25% over-cycling. Compute z, the opens per die, and the die yield loss. Is the finish worth using over the hot clear alone?

5. A rework strip is run on a wafer whose ZAZ is X = 0.1 crystalline (a queue too long at an elevated temperature). Estimate the extra cycles needed if the crystalline fraction etches at 0.65× (use a linear mixture of EPC) and say whether a longer over-cycle is needed.

6. A product allows a minimum C_s of 8.2 fF and a pillar radius loss of 0.25 nm per rework per side. How many reworks are allowed? Recompute the allowed number for a pillar radius of 12 nm.

---

**Next Chapter:** [Chapter 14: Advanced Dielectrics & 3D Architectures](./14-advanced-dielectrics-3d.md)

---

**Chapter 13 Development Status:** Complete  
**Version:** 1.0
