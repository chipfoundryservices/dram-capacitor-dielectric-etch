# Chapter 9: Walls, Boron Deposits, Zirconium Contamination & the Bevel

## Overview

The zirconium removed from the periphery does not all reach the pump. A small fraction of it, together with boron oxychlorides, silicon from the cap, and aluminium from the insertion layer, deposits on the chamber walls, the window, the edge ring, and the chuck. These deposits change the plasma, flake onto later wafers, and release zirconium back into the gas. They also defeat the usual way of cleaning etch chambers: a fluorine plasma, which turns zirconium deposits into zirconium fluoride and leaves them where they are.

Meanwhile, the wafer carries zirconium of its own to places no etch reaches. ALD wrapped the ZAZ around the bevel and onto the outer backside, under the plate films. From there it reaches robot end effectors, chucks, FOUPs, and the lithography and furnace tools that the wafer shares with other layers.

This chapter covers what deposits on the walls of the dielectric chamber, how to clean and season it, the fluorine trap, the sources and limits of zirconium cross-contamination, the removal of the dielectric from the bevel and backside, and the particles and flakes that come from all of these.

**Learning Objectives:**
- Estimate the deposition of zirconium and boron on the walls per wafer and over a maintenance interval
- Explain why fluorine-based chamber cleans fail for zirconium deposits and design a chlorine-based clean and seasoning sequence
- Describe the consequences of wall deposits for etch rate, endpoint, and particles
- List the sources of zirconium on wafer backsides and the limits for entering shared tools
- Compare plasma bevel etch, wet bevel and backside cleans, ALD edge exclusion, and batch thermal ALE for removing the dielectric from the wafer edge
- Set up wall and contamination monitoring for the dielectric module

---

## 9.1 What Deposits on the Walls

### 9.1.1 Composition

```
Wall deposits in the D1 chamber (illustrative):
  Deposit              Origin                                 Character
  ─────────────────────────────────────────────────────────────────────────────
  BₓClᵧ                BCl₃ plasma, everywhere ions are weak  soft; hygroscopic
  B₂O₃ / BOCl          gettered oxygen from ZAZ and cap;      glassy; hygroscopic
                       (BOCl)₃ on cooler surfaces
  ZrOClₓ → ZrO₂        ZrCl₄ meeting adsorbed O, OH, H₂O      hard; refractory;
                       on the walls                           does not volatilize
                                                              in F chemistry
  AlOClₓ               Al₂O₃ insertion (small)                minor
  SiOₓClᵧ              oxide cap, SiN floor                   minor
  YOCl skin            the Y₂O₃ coating itself                thin, self-limiting
```

### 9.1.2 Rates

```
Zirconium to the walls (reference, illustrative):
  Zr removed per wafer: 1.4 × 10¹⁷ s⁻¹ × 33 s ≈ 4.6 × 10¹⁸ atoms
  Fraction sticking to chamber surfaces ≈ 2% → ≈ 9 × 10¹⁶ atoms
  Wall area ≈ 3000 cm² → ≈ 3 × 10¹³ Zr/cm² per wafer
  ≈ 0.01 nm ZrO₂ equivalent per wafer → ≈ 10 nm per 1000 wafers

Boron-containing deposits: ≈ 0.05 nm per wafer → ≈ 50 nm per 1000 wafers
(without cleaning; strongly dependent on wall temperature)
```

The boron deposits are thicker; the zirconium deposits are harder to remove. Both accumulate fastest where the walls are coolest and the ion flux is lowest: in the pumping plenum, behind the liner, at the window edge.

### 9.1.3 Consequences

```
Effect of wall deposits on the process (illustrative):
  Cl recombination        BₓClᵧ walls recombine Cl less than clean Y₂O₃;
                          Cl density rises ≈ 5% over the first 100 wafers
                          after a clean → ZrO₂ rate + 2%, TiN lateral + 5%
  Zr release              Zr baseline in OES rises; endpoint confirmation
                          (Chapter 8) degrades
  Flakes                  deposits thicker than ≈ 50 nm crack from thermal
                          cycling and shed; a ZrO₂-containing flake on the
                          periphery is a high-k island under a later contact
  Moisture on venting     boron deposits absorb water: HCl, B(OH)₃ crystals,
                          corrosion of exposed metal; long recovery
```

---

## 9.2 Cleaning the Chamber

### 9.2.1 The Fluorine Trap

Most etch chambers are cleaned between wafers by a waferless plasma of NF₃, SF₆, or O₂. In the dielectric chamber, a fluorine clean meets ZrOClₓ deposits and converts them to ZrF₄:

```
ZrO₂ + 2 NF₃(plasma) → ZrF₄ + ...     ZrF₄ subl. ≈ 905 °C: stays on the wall
```

The zirconium is not removed; it is converted into a passivating fluoride skin. Worse, the skin and the adsorbed fluorine are released slowly in later BCl₃ plasmas, fluorinating the top of the next wafer's ZAZ and delaying its start (Chapter 2). An O₂ clean has a related problem: it converts BₓClᵧ into B₂O₃, a glass that BCl₃ removes slowly.

### 9.2.2 Chlorine-First Waferless Clean

The dielectric chamber cleans its walls with the same chemistry that clears the wafer, at conditions that favour the walls:

```
Waferless clean (reference, every wafer, illustrative):
  Cover         chuck protected by a cover wafer (AlN chuck surface is
                attacked by BCl₃/Cl₂ at high source power)
  Step 1        BCl₃ 50 / Cl₂ 150 sccm, 30 mTorr, 1500 W source, no bias,
                10 s: removes ZrOClₓ and BₓClᵧ at wall-sheath energies,
                helped by 120 °C walls
  Step 2        Ar / Cl₂, 5 s: removes loose boron; leaves a light, steady
                chlorinated wall
  Total         ≈ 15 s, interleaved with wafer exchange
```

Running the clean after every wafer keeps the wall in the same state for every wafer, which matters more than keeping it perfectly clean. The clean removes most but not all of the deposit; the residue grows slowly until the wet clean.

### 9.2.3 Wet Clean and Recovery

```
Wet clean (reference, illustrative):
  Interval       ≈ 1500 RF h (coincides with edge-ring replacement)
  Procedure      cool walls; vent with dry N₂ (moisture would hydrolyse
                 boron deposits); remove liner, window, and ring kit;
                 install a refurbished kit; leak check; pump and bake
                 (120 °C walls, 4 h)
  Kit refurbish  offline: mechanical and mild chemical removal of deposits
                 (Y₂O₃ coatings are attacked by strong acids); recoat when
                 the coating is thinner than specification
  Seasoning      20–50 conditioning wafers (blanket ZrO₂ on SiN) to build
                 the steady-state wall; the first-wafer effect is gone when
                 the Al-marker time and ZrO₂ rate are within 1% of the
                 pre-clean baseline
  Qualification  particle wafer; ZrO₂ and SiN rate wafers; Zr-contamination
                 wafer (backside TXRF)
```

---

## 9.3 Zirconium Cross-Contamination

### 9.3.1 Why It Matters

Zirconium is not a fast-diffusing lifetime killer in silicon. It matters because it does not belong in most of the fab: a furnace tube or a lithography chuck that picks up zirconium transfers it to gate oxides, implant masks, and other layers where it was never qualified. Fabs treat it, like other non-standard metals, by limits and tool dedication.

```
Zirconium limits (illustrative):
  Wafers entering shared tools (litho, furnaces, metrology)
    backside Zr                   ≤ 1 × 10¹⁰ atoms/cm²
    bevel Zr                      ≤ 1 × 10¹¹ atoms/cm² (bevel-specific scan)
  Dedicated "high-k" tool set     ALD, plate etch, D1, strip, plate wet clean
                                  (no limit within the set; monitored)
```

### 9.3.2 Sources

```
Zirconium on wafer backsides (illustrative, before any edge clean):
  Source                          Typical level           Area
  ───────────────────────────────────────────────────────────────────────
  ALD wrap onto backside edge     10¹⁵–10¹⁶ /cm²          outer 1–3 mm
  ALD chamber: pedestal contact,  10¹¹–10¹² /cm²          lift-pin marks,
  lift pins                                               chuck pattern
  D1 chuck contact (Zr migrates   10¹⁰–10¹¹ /cm²          whole backside
  from bevel to chuck surface)
  Robot end effectors, FOUP       10⁹–10¹⁰ /cm²           contact points
```

The edge wrap dominates by four to five orders of magnitude. Everything else is a slow transfer of that same zirconium from one tool to the next. Control the edge and the rest follows.

---

## 9.4 Removing the Dielectric From the Bevel and Backside

### 9.4.1 Prevent It: ALD Edge Exclusion

The cheapest bevel zirconium is the zirconium that was never deposited. ALD chambers can confine their precursors to the front surface with an edge purge: an inert gas flow out of a ring around the pedestal, and a shadow ring that sits over the wafer edge.

```
ALD edge exclusion (illustrative):
  Without edge purge     ZAZ on bevel, apex, and 1–3 mm of backside
  With edge purge        ZAZ ends within ≈ 0.5 mm of the apex on the front;
                         backside < 1 × 10¹² /cm²
  Cost                   ≈ 0.5 mm of usable radius; possible partial-die
                         effects at the extreme edge; particles from the ring
```

### 9.4.2 Plasma Bevel Etch

A bevel etcher confines a plasma to an annulus around the wafer edge, with the centre of the wafer protected by a closely spaced insulating plate. It typically uses F/O₂ chemistry to remove polymers, oxides, nitrides, and metals from the bevel. For the dielectric module, it must also remove ZrO₂, which requires BCl₃/Cl₂:

```
Bevel sequence for the plate module (illustrative):
  Step 1   F-based: W, SiGe, TiN, oxide cap on the bevel (Book #32)
  Step 2   BCl₃/Cl₂, 100 °C: ZAZ on the top bevel, apex, bottom bevel
           and backside to ≈ 1 mm
  Caution  F before Cl leaves a fluorinated ZAZ on the bevel; a short BCl₃
           breakthrough (as in D1) must come first in step 2
  Reach    ≈ 1–1.5 mm onto the backside
```

### 9.4.3 Wet Backside Clean

Beyond the reach of the bevel etcher, a single-wafer wet tool cleans the backside with the front protected by a nitrogen curtain:

```
Wet backside clean (illustrative):
  Chemistry      HF / H₂SO₄ at 80 °C (crystalline ZrO₂ ≈ 2 nm/min);
                 then dilute HF; DI rinse
  Time           ≈ 3 min for 5 nm on the outer backside
  Front          N₂ curtain; the front-side edge exclusion of the wet
                 tool (≈ 1 mm) must not overlap live dies
```

### 9.4.4 Batch Thermal ALE

A batch thermal-ALE reactor (Chapter 7) etches every exposed metal oxide on every face of every wafer. If the dielectric clear itself is done by thermal ALE, the bevel and backside ZAZ come off in the same step, without a bevel etcher or a backside wet clean, provided the plate films on the bevel do not cover it. The plate films usually do cover part of it, so the bevel etch of the conductors (step 1 above) must come first.

### 9.4.5 Choosing

```
Route                     Removes                   Cost and risk
───────────────────────────────────────────────────────────────────────────────
ALD edge exclusion        prevents deposition       edge-die area; ALD hardware
Plasma bevel (F + Cl)     bevel, ≈ 1 mm backside    extra tool; Cl-capable bevel
                                                    chamber
Wet backside clean        outer backside            extra tool; front protection
Batch thermal ALE         everything exposed        only with the T route
```

The reference module uses ALD edge exclusion, a plasma bevel etch with a BCl₃ step after the plate etch, and a backside TXRF gate before the wafer leaves the dedicated tool set.

---

## 9.5 Particles and Flakes

### 9.5.1 Sources

```
Particle sources in the dielectric module (illustrative):
  Source                         Composition       Effect on the wafer
  ──────────────────────────────────────────────────────────────────────────
  Wall flakes (deposit > 50 nm)  Zr, B, Y, O, Cl   high-k islands: contact opens
  Chuck scraping (cold clamp)    Al, N, Si         adders on the periphery
  Lift pins, ring contact        Y, Al             edge adders
  BCl₃ hydrolysis (line          B, O              boric acid particles;
  moisture)                                        micromasks
  Boric acid after venting       B, O, H           heavy adders until recovered
```

### 9.5.2 A Flake Is a Grain

A particle that lands on the periphery during the clear masks the ZAZ beneath it. A particle that lands after the clear, if it contains zirconium, is itself a residue. Either way, if it lies under a periphery contact, the contact stops on it. Particle specifications in this module are therefore tighter than their size alone suggests (Chapter 10).

---

## 9.6 Monitoring the Wall

```
Wall-state monitors (illustrative):
  Signal                          Indicates                  Action limit
  ─────────────────────────────────────────────────────────────────────────
  Zr I baseline between wafers    Zr release from walls      + 50% of post-
                                                             clean baseline
  Cl / Ar ratio in the ME         wall recombination state   ± 5%
  Al-marker time                  ZrO₂ rate (wall-coupled)   ± 3%
  RF hours since wet clean        deposit thickness          1500 h
  Particle monitor (weekly)       flaking                    > 10 adders
                                                             ≥ 30 nm
  Backside TXRF (sampled lots)    Zr transfer                > 1 × 10¹⁰ /cm²
```

---

## Summary and Key Takeaways

1. **Zirconium and boron deposit on the walls.** About 0.01 nm of ZrO₂-equivalent and 0.05 nm of boron deposit per wafer without cleaning.

2. **Fluorine cleans make it worse.** ZrF₄ stays on the wall and fluorinates the next wafer; O₂ turns boron deposits into glass. Clean with chlorine.

3. **Clean every wafer for a steady wall.** A short BCl₃/Cl₂ waferless clean, a cover wafer for the chuck, and wet cleans at about 1500 RF hours.

4. **The bevel wrap is the zirconium source.** It exceeds all other backside sources by four orders of magnitude; ALD edge exclusion prevents most of it.

5. **Bevel and backside removal needs chlorine or strong wet chemistry.** A plasma bevel etch with a BCl₃ step, a hot HF/H₂SO₄ backside clean, or batch thermal ALE.

6. **A zirconium flake is a high-k island.** Particles in this module are judged by what they do under a contact, not only by their size.

---

## Study Questions

1. Using Section 9.1.2, how many wafers can run before the zirconium deposit on the coolest wall area (where deposition is three times the average) reaches the 50 nm flaking threshold, if the per-wafer clean removes 90% of each wafer's Zr deposit?

2. A technician runs an NF₃ waferless clean in the D1 chamber by mistake. Predict the effect on the next 20 wafers: endpoint, Al-marker time, clearing, and residue. What recovery sequence would you run?

3. Estimate the Zr dose on the outer 2 mm of the backside for 5 nm of ZAZ with no edge exclusion. How many orders of magnitude must the backside clean remove to meet 1 × 10¹⁰ /cm²?

4. Why must the BCl₃ step of the bevel etch begin with a breakthrough when it follows an F-based step? What would happen without it?

5. Compare the reference edge-clean sequence with batch thermal ALE for a fab running 139 wafers per hour. Which tools are eliminated, and which risks are added?

6. Write the checklist for returning the D1 chamber to production after a wet clean, with the measurement and limit for each step.

---

**Next Chapter:** [Chapter 10: Clearing the Periphery — Grain Residue, Micromasking & Stringers](./10-periphery-clearing-residue-stringers.md)

---

**Chapter 9 Development Status:** Complete  
**Version:** 1.0
