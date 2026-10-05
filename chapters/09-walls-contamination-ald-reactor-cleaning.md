# Chapter 9: Walls, Boron, Metal Contamination & ALD-Reactor Cleaning

## Overview

Every gram of dielectric the three modules remove goes somewhere. Most leaves through the pump as volatile chlorides. Some stays on the chamber wall, mixed with boron oxychlorides, where it changes the chlorine density of the next wafer's plasma, flakes onto later wafers, and turns into permanent fluorides the first time the chamber runs a fluorine step. Some leaves on the wafer itself, on the backside and on the chuck it touches, and travels to the next tool. And some of the dielectric never reaches a wafer at all: it grows on the walls of the ALD reactor that made it, five and a half nanometres per wafer, until the reactor must be cleaned of the very film this book is about.

This chapter follows the zirconium, aluminium, and boron: onto the etch chamber's walls and how they are cleaned, onto wafer backsides and chucks and how cross-contamination is prevented, into particles and the contact-open clusters they cause, and onto the ALD reactor's parts and how those are cleaned.

**Learning Objectives:**
- Estimate the zirconium deposited on the etch chamber wall per wafer, and why hot walls do not prevent it
- Explain how the wall state changes the main-step rate and why the ALE finish is less sensitive
- State the order of a waferless clean for a chamber that sees Zr, Al, Ti, B, and fluorine, and the reason for each step
- Describe the paths of zirconium cross-contamination and the tool policies that block them
- Estimate the size of the contact-open cluster caused by a flake on the periphery
- Compare ex-situ and in-situ cleaning of a ZrO₂ ALD reactor

---

## 9.1 What Goes on the Etch Chamber Wall

### 9.1.1 Mass Balance

```
Per reference wafer, module 2:
  ZrO₂ removed from the periphery     ≈ 1.0 mg (≈ 0.72 mg Zr)
  Al₂O₃ removed                        ≈ 0.03 mg
  TiN removed (TiN clear)              ≈ 0.8 mg
  BCl₃ consumed (main step + ALE)      ≈ 15 mg
```

### 9.1.2 Why Hot Walls Do Not Keep Zirconium Off

ZrCl₄ is volatile enough at the reference wall temperature:

```
ZrCl₄ vapour pressure (ΔH_sub ≈ 110 kJ/mol, 1 Torr at ≈ 190 °C):
  at 120 °C (wall)          ≈ 6 × 10⁻³ Torr
  at 60 °C (wafer, chuck)   ≈ 1.4 × 10⁻⁵ Torr

ZrCl₄ partial pressure in the chamber during the main step:
  production ≈ 9 × 10¹⁶ molecules/s ≈ 2.8 × 10⁻³ Torr·L/s
  pumping speed ≈ 380 L/s (150 sccm at 5 mTorr)
  p(ZrCl₄) ≈ 7 × 10⁻⁶ Torr
```

Pure ZrCl₄ does not condense on a 120 °C wall. But the zirconium on the wall is not pure ZrCl₄. ZrClₓ fragments react with the oxygen-bearing BOₓClᵧ film the BCl₃ chemistry deposits, and with oxygen released from the Y₂O₃ coating, to form zirconium oxychlorides (ZrOCl₂ and mixed Zr–B–O–Cl solids) that are not volatile at any wall temperature. About 5% of the removed zirconium stays:

```
Zr retained on the wall ≈ 0.05 × 0.72 mg ≈ 36 µg per wafer
Liner and wall area ≈ 4000 cm²  →  ≈ 9 ng/cm² ≈ 6 × 10¹³ Zr/cm² per wafer
                                   (≈ 0.07 monolayer)

Without cleaning:  25 wafers → ≈ 2 monolayers;  1000 wafers → ≈ 70
```

Within one lot, an uncleaned wall would carry more zirconium than the specification allows on the wafer by many orders of magnitude, and some of it would return to the wafers as flakes and as sputtered atoms. The chamber is therefore cleaned after every wafer.

---

## 9.2 Wall State and the Plasma

### 9.2.1 Chlorine Recombination

The density of chlorine atoms depends on how fast they recombine on the wall:

```
n_Cl ∝ (production) / (γ_wall × wall area + pumping)

Recombination probability γ (illustrative):
  Fresh Y₂O₃, oxidized (after O₂ clean)        ≈ 0.04
  Y₂O₃ coated with BOₓClᵧ                       ≈ 0.01
  Wall coated with TiClₓ / metal chlorides     ≈ 0.10
```

A wall that has just been cleaned in oxygen recombines chlorine four times faster than one seasoned with a boron-chlorine film. The main step, partly limited by the supply of chlorine and by the deposition D, sees it:

```
Main-step rate versus wall state (illustrative):
  Seasoned (BOₓClᵧ)                       6.0 nm/min (reference)
  Just after an O₂-final clean (unseasoned) 5.6 nm/min (−7%)
  Metal-chloride-coated (no clean)         5.3 nm/min (−12%)

ALE EPC versus wall state:
  Seasoned / unseasoned / metal-coated      0.100 / 0.099 / 0.097
```

The ALE's BCl₃ dose is a neutral gas with no plasma; its Ar⁺ step involves no chlorine radicals. It hardly notices the wall. The main step does, and a −7% first-wafer effect is 0.31 nm of extra residue at every site, three more ALE cycles than the statistics allowed for.

### 9.2.2 First-Wafer Effect and Seasoning

The cure is to end every clean with a seasoning step in the process chemistry, so that each wafer meets the same wall:

```
Season step (end of every WAC): BCl₃/Cl₂/Ar plasma, no wafer, 5 s
First-wafer effect after season: < 1%
After an idle > 2 h: run a 60 s season before the first wafer
```

---

## 9.3 The Waferless Auto-Clean

### 9.3.1 The Order

The plate chamber runs Book #32's W step in SF₆/N₂/Cl₂ at the start of every wafer, and this book's ZAZ steps at the end. Fluorine and zirconium meet on the wall unless the clean between wafers removes the zirconium first:

```
ZrO₂/ZrOCl₂ + F → ZrF₄ (sublimes only near 600 °C): permanent
Al deposits + F  → AlF₃: permanent
B deposits + F   → BF₃ (volatile): harmless
Ti deposits + F  → TiF₄ (volatile at wall temperature): harmless
```

```
Reference WAC (between every wafer, ≈ 30 s):

  Step   Chemistry              Removes                        Why this order
  ──────────────────────────────────────────────────────────────────────────────
  1      Cl₂/BCl₃, 1200 W,      Zr, Al, Ti as chlorides;       before any F reaches
         15 s                   B as BCl₃ and (BOCl)₃          Zr or Al
  2      O₂, 1200 W, 10 s       carbon from resist;            after Cl: O₂ first
                                residual Cl                    would fix B as B₂O₃
                                                               and Zr as ZrO₂
  3      BCl₃/Cl₂/Ar season,    —                              uniform wall for the
         5 s                                                   next wafer (§ 9.2.2)
```

The rule of Book #32 (Chapter 7) holds here with one addition: **oxygen after chlorine, not before**. An oxygen clean on a boron-bearing wall converts the boron to B₂O₃, which neither oxygen nor chlorine removes quickly at 120 °C.

### 9.3.2 Wet Clean

Over hundreds of RF-hours, what the WAC misses accumulates on the coolest parts (window edges, the gap behind the edge ring) and on parts that see little ion flux. The chamber is opened and its liner, ring, and window replaced:

```
Wet-clean interval (reference): ≈ 400 RF-hours
Triggers: particle adders > 10 per wafer at ≥ 45 nm; Zr on the
          monitor-wafer backside > 1 × 10¹¹ atoms/cm²; WAC end-point
          (Cl₂-step Zr emission) not reaching baseline
Parts cleaning: HCl/HNO₃ mixtures remove Zr–B–O–Cl deposits from Y₂O₃;
                HF is avoided because it attacks the coating
Recovery: season 20 wafer-equivalents; qualify main-step rate,
          ALE EPC, particles, Zr on backside
```

---

## 9.4 Zirconium Cross-Contamination

### 9.4.1 Why Zirconium Is Controlled

Zirconium is not a fast diffuser in silicon like copper, nickel, or iron, and at low levels it does not create deep-level traps the way they do. It is controlled because it is a **foreign high-k metal** in tools that also process the gate stack and other dielectrics, where unintended Zr changes threshold voltages, interface charge, and etch behaviour, and because Zr-bearing particles are hard to remove once present.

```
Typical limits (illustrative):
  Wafer front entering FEOL-shared tools     ≤ 5 × 10⁹ atoms/cm²
  Wafer backside / bevel                     ≤ 1 × 10¹⁰ atoms/cm²
  Monitor wafer through a shared tool        ≤ 1 × 10⁹ atoms/cm² added
```

### 9.4.2 Paths

```
How Zr leaves the capacitor module (before controls):

  Carrier                 Path                                 Blocked by
  ──────────────────────────────────────────────────────────────────────────
  Wafer bevel/backside    film wraps the edge (Ch. 2)          module 1
  Wafer backside          picked up from a Zr-loaded chuck     cover-wafer
                          in module 2                          WAC; backside
                                                               scrub after
                                                               strip
  Robot end effectors     contact with backside/bevel          module 1;
                                                               end-effector
                                                               cleaning
  Furnace boats           SiGe fill: 100 wafers per run,       module 1 before
                          quartz retains Zr                    the furnace
  FOUPs                   wafer edge contact                   FOUP dedication
                                                               and washing
  Shared metrology        stage contact                        Zr-dedicated
                                                               metrology
```

### 9.4.3 The Bevel's Share

```
Zr on the edge of a wafer before module 1:
  Front ring   11 cm² × 1.5 × 10¹⁶                    ≈ 1.7 × 10¹⁷
  Apex          7 cm² × 1.4 × 10¹⁶                    ≈ 1.0 × 10¹⁷
  Backside     28 cm² × ≈ 5 × 10¹⁵ (tapered)          ≈ 1.4 × 10¹⁷
  Total                                               ≈ 4 × 10¹⁷ atoms

If 10⁻⁷ of this transfers to a furnace boat per wafer, a 100-wafer
run leaves ≈ 4 × 10¹² Zr atoms on ≈ 5000 cm² of quartz: ≈ 10⁹/cm²
per run, accumulating run after run, and returning to wafers.

After module 1 (≤ 1 × 10¹⁰/cm² over the edge and backside):
  Total ≤ 7 × 10¹² atoms per wafer: five orders of magnitude less.
```

### 9.4.4 Module 2 Must Not Undo Module 1

During a waferless clean, the chuck surface is exposed to the plasma and to zirconium sputtered from the wall. It picks up zirconium and passes it to the backside of the next wafer:

```
Backside Zr after module 2 (illustrative):
  WAC without cover wafer           3 × 10¹⁰ – 1 × 10¹¹ atoms/cm²
  WAC with cover wafer (dummy       ≤ 5 × 10⁹
  wafer on the chuck during WAC)
  After post-strip backside scrub   ≤ 3 × 10⁹
```

The reference uses a cover wafer during WAC and a backside scrub in the wet clean after the strip. The wafer leaves module 2 cleaner on its backside than the specification requires, so that the ILD deposition and the contact module see no zirconium.

---

## 9.5 Particles and Clusters

### 9.5.1 Sources

```
Particle sources in the dielectric modules (illustrative):
  Wall flakes (Zr–B–O–Cl)         etch chamber, worse late in the
                                  wet-clean interval
  BCl₃ hydrolysis (B(OH)₃ / B₂O₃) moisture in the gas line or chamber
  PEZ deposits (bevel tool)        flakes onto the front near the boundary
  ALD reactor flakes               ZrO₂ flakes from the showerhead,
                                   embedded in the dielectric itself
```

### 9.5.2 What a Particle Does to the Periphery Clear

A particle that lands on the periphery ZAZ before or during the main step shadows the film beneath it. When the particle is later removed by the strip or the wet clean, a ZrO₂ island the size of its footprint remains:

```
Periphery contact density ≈ 3 × 10⁷ contacts / 0.27 cm² ≈ 1.1 per µm²

Particle footprint     Area (µm²)     Contacts blocked (expected)
───────────────────────────────────────────────────────────────────
0.1 µm                 0.008          0.01
0.5 µm                 0.2            0.2
2 µm flake             3.1            3–4
5 µm flake             20             ≈ 20
```

Small particles rarely hit a contact. Wall flakes of micrometre size cause **clusters** of contact opens, a signature distinct from the random single opens of the grain tail (Chapter 16). A particle that arrives during the ALE finish shadows less, because the film under it is already thin, but the finish has no extra cycles to clear around it.

### 9.5.3 Particles in the Dielectric Itself

A ZrO₂ flake from the ALD reactor that lands on the pillars during deposition is overgrown by the rest of the film. In the array, it is a local thick spot: a few cells with lower capacitance. In the periphery, it is a lump of ZrO₂ several nanometres thicker than the film, which no part of module 2 was designed to remove. It survives as a large residue and blocks every contact beneath it.

---

## 9.6 Cleaning the ALD Reactor

### 9.6.1 What Accumulates

ALD grows the film on every surface inside its temperature window:

```
ZAZ ALD reactor (illustrative):
  Susceptor 300 °C, showerhead ≈ 200 °C, walls ≈ 150 °C
  Growth on all hot surfaces ≈ the wafer's: 5.5 nm per wafer
  After 800 wafers:   ≈ 4.4 µm on the showerhead face
  Flaking threshold:  ≈ 4–6 µm (stress, thermal cycling, adhesion to
                      the showerhead metal)
  Clean interval:     ≈ 800 wafers
```

### 9.6.2 Ex-Situ: Parts Swap

```
Ex-situ cleaning (common practice):
  Vent, cool, remove showerhead and liners; install clean set
  Chemical strip of ZrO₂/Al₂O₃ from parts (hot acid mixtures; crystalline
  ZrO₂ resists dilute HF)
  Pump-down, bake, season (≈ 100 nm of ZrO₂ on the new parts), qualify
  Downtime ≈ 10 h every 800 wafers
  At ≈ 4 wafers/h per chamber (≈ 15 min per wafer), 800 wafers ≈ 200 h
  → availability loss ≈ 5%
```

### 9.6.3 In-Situ: Chlorine at the Deposition Temperature

Fluorine-based remote-plasma cleans, which work for SiO₂ and TiN reactors, do not work here: they convert ZrO₂ to ZrF₄, which stays. But the reactor's own surfaces are hot, and at 150–300 °C ZrCl₄ is volatile at Torr pressures. A remote-plasma or thermal chlorine clean can therefore etch the deposits in place:

```
In-situ BCl₃/Cl₂ remote-plasma clean (illustrative):
  Chamber at deposition temperature; 1–2 Torr BCl₃/Cl₂/Ar; remote source
  Rate on the 300 °C susceptor        ≈ 60 nm/min
  Rate on the 200 °C showerhead       ≈ 40 nm/min
  Rate on the 150 °C walls            ≈ 15 nm/min (ZrCl₄ near its
                                      condensation limit)
  Time to remove 4.4 µm (showerhead)  ≈ 110 min
  Recovery: purge, O₃ treatment, season 30 nm of ZrO₂ on the parts,
            first-wafer check for B and Cl in the film (SIMS)
  Downtime ≈ 3 h every 800 wafers   → availability loss ≈ 1.5%
```

The in-situ clean has three costs. **Chlorine attacks metal parts** (nickel alloys and stainless steel at 200–300 °C); the reactor must be built of chlorine-tolerant materials. **Boron and chlorine stay on the walls** after the clean, and the first wafers deposited after it can carry boron at the dielectric's bottom interface, where it raises leakage; the seasoning deposition buries them. And **the coolest surfaces clean slowest**, so the walls set the clean time even though the showerhead sets the interval.

### 9.6.4 The Top-Electrode Reactor, for Contrast

The TE TiN ALD reactor is cleaned with NF₃ remote plasma: TiF₄ is volatile at the reactor's temperature. The contrast is the whole of Chapter 3 in one line: titanium leaves as a fluoride, zirconium only as a chloride.

---

## 9.7 Monitors

```
Monitor                                      Frequency        Limit / action
───────────────────────────────────────────────────────────────────────────────
Cl/Ar actinometric ratio in the main step    every wafer      ± 5% → season,
                                                              check WAC
Zr emission at the end of WAC step 1         every WAC        must reach baseline
                                                              → wet-clean trigger
Particle wafer, etch chamber                 daily            ≤ 10 adders ≥ 45 nm
Backside VPD, module 2 (with cover-wafer     weekly           ≤ 5 × 10⁹ Zr/cm²
WAC)
Bevel VPD, module 1                          per lot sample   ≤ 1 × 10¹⁰ Zr/cm²
                                                              (rinse at 5 × 10⁹)
Furnace-boat witness wafer (SiGe fill)       weekly           ≤ 1 × 10⁹ Zr/cm²
                                                              added
ALD reactor particle wafer                   daily            flake count; clean
                                                              interval
```

---

## Summary and Key Takeaways

1. **Hot walls do not keep zirconium off.** Pure ZrCl₄ would not condense at 120 °C, but Zr–B–O–Cl solids do: about 5% of the removed zirconium, 6 × 10¹³ atoms/cm² of wall per wafer.

2. **The main step feels the wall; the finish does not.** An unseasoned wall costs 7% of main-step rate, three ALE cycles of margin. End every clean with a season.

3. **Chlorine first, oxygen second, fluorine never on zirconium.** ZrF₄ and AlF₃ are permanent; B₂O₃ formed by an early O₂ step is nearly so.

4. **The wafer carries zirconium unless every module stops it.** Module 1 removes 4 × 10¹⁷ atoms from the edge; module 2 must not put 10¹¹/cm² back on the backside from its chuck.

5. **Flakes make clusters.** A 2 µm flake on the periphery blocks three or four contacts; grain residue blocks single ones.

6. **The ALD reactor needs the same chemistry.** Fluorine cannot clean ZrO₂ deposits; chlorine at the reactor's own temperature can, at the price of chlorine-tolerant hardware and a boron-burying season.

---

## Study Questions

1. Compute the vapour pressure of ZrCl₄ at 90 °C from the parameters in Section 9.1.2. Would pure ZrCl₄ condense on a 90 °C window during the main step?

2. If 10% instead of 5% of the removed zirconium stays on the wall, how many monolayers accumulate on a 4000 cm² wall in one 25-wafer lot without cleaning?

3. A WAC is changed to run O₂ first and Cl₂ second to shorten it. Describe what happens to the boron and zirconium on the wall over a week, and how you would detect it from the main-step data of Chapter 8.

4. Estimate the number of contact opens per die caused by wall flakes if the chamber adds 0.3 flakes of 2 µm per wafer to the periphery, with 950 dies per wafer.

5. Compare the availability loss of ex-situ and in-situ ALD reactor cleaning for a reactor that runs 5 wafers per hour. What other cost of the in-situ clean must be weighed?

6. Explain why the TE TiN reactor can be cleaned with NF₃ and the ZAZ reactor cannot, using the volatility table of Chapter 3.

---

**Next Chapter:** [Chapter 10: Periphery Clearing — Residue Statistics, the ALE Finish & SiN Landing](./10-periphery-clearing-residue-ale-finish.md)

---

**Chapter 9 Development Status:** Complete  
**Version:** 1.0
