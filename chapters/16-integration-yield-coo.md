# Chapter 16: Integration, Yield & Cost of Ownership

## Overview

Each dielectric etch hands its wafer to a module that depends on what it left. The edge etch hands the top-electrode deposition a dielectric that has not changed, and every furnace and chuck downstream a backside that is clean to 10¹⁰ Zr cm⁻². The trim hands the same deposition a film that is thinner by a known number of cycles and chemically a little different. The periphery clear hands the inter-layer dielectric a plate edge and a periphery free of zirconia, and hands thirty million contacts per die a surface they can land on.

This chapter follows those hand-offs and translates the defects of each module into the yield signatures they produce. It sets out the periphery yield model of Chapter 4 for the five routes of this book, including its extreme sensitivity to the grain-level spread, sizes the equipment for a production fab at the level of the chamber, builds the cost of ownership of each route and each module, and compares the cost of protection with the value of the yield and of the equipment that it protects.

**Learning Objectives:**
- Describe what each module hands to the next and what depends on it
- Identify the yield and electrical signature of each dielectric-etch defect
- Evaluate the periphery open rate against σ_g and overetch for the five routes
- Size the chambers of the strip-then-clear route, the edge etch, and the thermal reactors
- Build per-wafer cost of ownership and compare routes, including the edge etch and the trim
- Compute the break-even for the edge etch and the insurance value of an ALE finish
- Apply the decisions and the new-product checklist

---

## 16.1 Hand-Offs

```
What module E hands on (reference):
  Item                          Value                        What depends on it
  ──────────────────────────────────────────────────────────────────────────────────────────────
  Backside, bevel Zr            ≤ 1 × 10¹⁰ cm⁻²             furnaces, chucks, every clean-zone tool
  ZAZ at r < 146 mm             unchanged (≤ 0.1 nm)         edge-die capacitance and leakage
  B at r = 146 mm               ≤ 2 × 10¹³ cm⁻²             top-electrode interface of the edge dies
  Particles                     ≤ 10 per wafer               top-electrode ALD

What module T hands on (when used):
  ZAZ thickness                 nominal ± 0.04 nm            C_s, leakage, TDDB
  Surface                       F 1–3 at%, C < 1 at%         TiN interface; oxidizing step needed
  State                         amorphous (X ~ 10⁻¹¹)        crystallization at the top electrode

What module P hands to the ILD and the contacts:
  Periphery                     ZAZ-free; SiN 119 nm (loss 0.65 nm); B ≤ 1, Cl ≤ 2 at%
  Plate edge                    W 37.7 nm (R_s 3.8 Ω/□), SiGe foot 2.7–4.2 nm, TiN recess 2.1 nm,
                                shell 0.5 nm; void 5 nm × 2 nm
  Zr residue                    ≤ 1 × 10¹³ cm⁻² average; one grain in 10⁸ at most
```

The last line of each block names a decision that is irreversible downstream. Zirconium on a backside spreads; a grain left under a periphery contact is an open found after the contact module; a trim cannot be undone after the top electrode.

---

## 16.2 Yield Signatures

```
Defect                           Signature                                  Repairable?
────────────────────────────────────────────────────────────────────────────────────────────────
Backside Zr into a furnace       tool excursion: lot-wide contamination;     no (tool and lots lost)
                                 retention tail in affected lots
Edge-die ZAZ loss (boundary in)  C_s and leakage shift, r = 140–146 mm;      partly (edge dies)
                                 radial ring
Edge flakes (bevel)              particles on edge dies; shorts, opens        partly
Periphery contact open (ZrO₂     die-level functional fail; decoder or        mostly no
  grain)                         sense-amp group dead; wafer-edge excess
Fluorine skin (ZrF₄ patch)       same as a grain residue, local to the        mostly no
                                 stop's failing chamber or wafer region
TiN notch > 15 nm / shell breach void along plate edge; corrosion path;       no
                                 plate-edge defects after ILD
W thin (strip long, E high)      plate resistance > 4 Ω/□; plate-bounce        no (bank)
                                 margin failures at speed
Charging in P2 / P4              retention tail in banks; radial ring (phase   no
                                 A); polarity pairs
Trim chemistry (F, C)            leakage and TDDB tail shift of the whole      no (population)
                                 lot; slope in the trim-dose array
Trim over-removal                C_s high, leakage high, TDDB short            no
Rework count > 1                 C_s low by 1.4% per rework                    no
```

Of these, only the first is a tool-level excursion: it cannot be traced to a wafer until several lots have gone through the furnace. For that reason the edge etch has the weakest direct yield signature of the book and the highest cost of failure.

---

## 16.3 The Periphery Yield Model

The model of Book #32, Y = exp(−N_contacts × P_open), with N = 3 × 10⁷ contacts and P_open = 4 × P(grain left) with P = ½ erfc(z/√2) and z = OE/σ_g:

```
Route     Overetch / σ                          z       P (grain left)   Opens per die   Y
────────────────────────────────────────────────────────────────────────────────────────────────
R0        OE 50%, σ_g 8% (ambient)              6.25    2.0 × 10⁻¹⁰      2.5 × 10⁻²      97.6%
R1        OE 35%, σ_g 5% (hot, resist-free)     7.00    1.3 × 10⁻¹²      1.5 × 10⁻⁴      99.985%
R2/R3     over-cycle 30%, σ_EPC 4%              7.50    3.2 × 10⁻¹⁴      3.8 × 10⁻⁶      99.9996%
R4        OE 40%, σ 5% (assumed; wet finish)    8.00    6.2 × 10⁻¹⁶      7.5 × 10⁻⁸      ≈ 100%
```

### 16.3.1 Sensitivity to σ_g

The tail is the steepest function in the book. For R1 at 35% overetch:

```
σ_g      z       P (grain left)    Opens per die   Y          Loss vs a perfect die ($ per wafer, $26 per 1%)
────────────────────────────────────────────────────────────────────────────────────────────────────────────
5.0%     7.00    1.3 × 10⁻¹²       1.5 × 10⁻⁴      99.985%    ≈ 0
5.5%     6.36    9.9 × 10⁻¹¹       1.2 × 10⁻²      98.8%      31
6.0%     5.83    2.7 × 10⁻⁹        0.33            72%        723
7.0%     5.00    2.9 × 10⁻⁷        34              0%         2,600
8.0%     4.38    6.1 × 10⁻⁶        730             0%         2,600
```

A rise in σ_g from 5% to 6% takes the yield from 99.985% to 72%. The grain-level spread is not controlled by anything in the recipe: it is a property of the film and the chuck temperature. A recipe with 35% overetch has no margin against a σ_g drift of 1 percentage point. At 40% overetch the same drift to 6% costs only 0.16% (opens 1.6 × 10⁻³), and the price of the 5% extra overetch is 1.4 s of a 38 s step, about $0.05 per wafer. The reference of 35% is the hot step of Book #32; **a production recipe should run 40%**, which the shell (margin 1.38) and the tungsten (2.31 nm) tolerate.

### 16.3.2 Value Relative to Book #32

```
R1 vs R0, model:       99.985% − 97.57% = +2.4% → $63 per wafer ($26 per 1%)
Corrected for the fraction of opens that are fatal (÷2 to ÷5, as in Book #32): $13–31 per wafer
R2 vs R1, model:       99.9996% − 99.985% = +0.015% → $0.39 per wafer
```

R1 is worth $13–31 per wafer against R0. R2 at σ_EPC = 4% is worth $0.39: nothing at the reference spread. What R2 buys is the protection of Section 16.3.1: against a σ_g drift to 6% it recovers $723 per wafer.

---

## 16.4 Equipment Sizing

```
Fab assumption: 100,000 wafer starts per month at this layer → 139 wph; availability 85%
Capacity needed: 139 / 0.85 = 163.5 wph per step

Module P, R1 (chamber level):
  Chamber                      Cycle (s)       wph/chamber   Chambers needed (163.5 wph)
  ──────────────────────────────────────────────────────────────────────────────────────────
  F  (BARC 20 s, W 15 s)         68 (incl. handling 30 s)    52.9       3.09 → 4
  C  (SiGe 72 s + P2 42 s + 12 s transitions + handling 30 s)   156     23.1    7.09 → 8
  Strip (60 s + 30 s)            90                          40.0       4.09 → 5
  Hot clear (38 + 5 s heat + 30 s)    73                     49.3       3.32 → 4
  Total                                                                  21 chambers
Book #32 integrated route (R0): 4 mainframes of 4 plate + 2 strip/PET chambers = 24 chambers

Module E:    mainframe of 4 edge chambers: 89 wph → 163.5/89 = 1.8 → 2 mainframes
             edge wet clean modules (100 wph): 1.6 → 2
Module T:    trim on 13.7% of lots ≈ 19 wph: one single-wafer thermal chamber (40 wph)
R2 finish:   batch tools (25 wafers, 29 cycles at 20 s + 20 min): 50.6 wph → 3.2 → 4 tools
R3:          batch tools (158 cycles): 20.6 wph → 7.9 → 8 tools
R4 wet:      wet chambers at 8 wph (6.5 min dip): 20 chambers
```

The strip-then-clear route needs fewer chambers than the integrated route (21 against 24), because each chamber does one step: the C chamber is the bottleneck, at 8, and the splitting of the F step (4 chambers) pays for itself by removing the F memory from it (Chapter 10).

---

## 16.5 Cost of Ownership

### 16.5.1 Module P, R1

```
Per wafer (illustrative, full loading; depreciation = capex / 5 yr / (wph × 8760 × 0.85)):
  Chamber        Capex     wph    Depreciation
  F              $2.3 M    52.9   $1.17
  C              $2.3 M    23.1   $2.68
  Strip          $1.5 M    40.0   $1.01
  Hot clear      $2.8 M    49.3   $1.53
  Depreciation                                    $6.38
  Consumables    rings, liners, hot-chuck parts, HK-coated parts           $1.55
  Gases, power   CF₄, SF₆, HBr, Cl₂, BCl₃, O₂, N₂; RF; heater power         $0.80
  Maintenance    PM labour and parts (Zr zone only for the hot chamber)   $0.70
  Metrology      in-situ ellipsometry, OCD, XRF, TXRF, chains (allocated)  $1.10
  Total R1 etch                                                           ≈ $10.53
  (Book #32 integrated plate etch: ≈ $10.70; lithography ≈ $8 is common to all routes)
```

The cost is the same as the integrated route's, to within 2%. The extra chambers of the hot clear and the strip are offset by the shorter, simpler conductor chambers.

### 16.5.2 Module E

```
Edge etch, per wafer (illustrative):
  Edge etch mainframe   $6 M, 89 wph:  $6M / 5 / (89 × 8760 × 0.85)        $1.80
  Edge wet clean        $2 M, 100 wph                                      $0.54
  Consumables (powered ring, plate, lower ring)                            $0.35
  Gases, power                                                             $0.15
  Maintenance                                                              $0.25
  Metrology (VPD-ICPMS weekly, line scans, TXRF daily)                      $0.35
  Total module E                                                          ≈ $3.44
```

### 16.5.3 Module T and the Alternatives

```
Module T, per trimmed wafer:  single-wafer thermal chamber $2.5 M, 40 wph      $1.68
                              consumables $0.20; HF/DMAC $0.15; metrology $0.40
                              total                                           ≈ $2.43 per trimmed wafer
                              × 13.7% of lots = $0.33; + ALD thickness metrology on every lot $0.20
                              → ≈ $0.53 per wafer, averaged

Route alternatives (added to R1's etch):
  R2  ALE finish (batch, $5 M/tool, 50.6 wph): depreciation $2.66 + gas, consumables, maintenance $1.10   + $3.76
  R3  all-thermal (8 batch tools, 20.6 wph): $6.51 + $1.10 − hot clear chamber costs saved ($2.58)          + $5.03
  R4  hybrid wet (20 chambers at 8 wph, $1.5 M): $5.04 + chemicals $0.50                                      + $5.54
```

```
Route totals per wafer (etch only; add E and T for the module):
  Route    Etch     + E ($3.44) + T avg ($0.53)
  ─────────────────────────────────────────────
  R0       10.70        14.67
  R1       10.53        14.50
  R2       14.29        18.26
  R3       15.56        19.53
  R4       16.07        20.04
```

---

## 16.6 What Protection Is Worth

### 16.6.1 The Edge Etch

```
Annual cost of module E: $3.44 × 1.2 × 10⁶ wafers/yr = $4.1 M
Break-even: the module pays if it prevents more than 4.1 / (event cost) events per year
  at $3 M per furnace-contamination event (tube replacement, qualification, lots lost):
  4.1 / 3.0 = 1.4 events per year
```

If an event costs $3 M, the edge etch pays for itself when it prevents one and a half contamination events a year. A fab without it expects them regularly: Section 9.2.1 showed one dirty wafer on a chuck contaminating the next 370.

### 16.6.2 The ALE Finish

```
R2 costs +$3.76 per wafer; R2 vs R1 at the reference σ_g: +$0.39 per wafer
  → at the reference, a loss of $3.37 per wafer
Insurance: R1 at σ_g = 5.5%  loses $31 per wafer;  at 6.0%  $723 per wafer
  The break-even probability of σ_g drift to 5.5% for the finish to pay: 3.37/31 = 11%;
  to 6.0%: 3.37/723 = 0.5%
```

The same protection is bought more cheaply by raising the hot clear's overetch from 35% to 40% (≈ $0.05 per wafer, Section 16.3.1), which at a σ_g of 6% brings the loss from $723 to $4. The ALE finish is therefore an option for a product whose σ_g cannot be bounded below 6% even at 40% overetch, or for a film whose grain statistics are unknown.

### 16.6.3 The Trim

The trim costs $0.53 per wafer averaged and corrects the capacitance of the 14% of lots that run thick. Its value is the recovered C_s of lots that would otherwise sit near the 8.3 fF limit (Chapter 13): at the tail of the distribution, each percent of C_s that moves a lot above the specification is a lot that is sold instead of scrapped or sorted down.

---

## 16.7 Decisions

```
Decision                    Choose                                  When
──────────────────────────────────────────────────────────────────────────────────────────────────────────
Edge etch                   always; amorphous, before TiN           any wafer that enters a furnace or a clean
                                                                    chuck with a ZAZ-coated backside
Periphery clear route       R1 strip-then-clear, OE 40%             default; plate edge, resist budget,
                                                                    veils, and Zr zone favour it
                            R0 integrated                           low volume; no hot-chuck capacity;
                                                                    accept the 218 nm resist budget and
                                                                    tighter tail
                            R2 (R1 + ALE finish)                    σ_g not bounded below 6%; unknown film
                            R3 all-thermal                          products that cannot tolerate ions at the
                                                                    plate; low volume
                            R4 wet finish                           Sr/Ba dielectrics only
Charging control            bias pulsing; or a 5 nm cap on the W    when polarity pairs show a leakage shift
Trim                        N = round(Δt/EPC) for Δt > one cycle   C_s near the lower limit; never below nominal
Rework                      ≤ 1 per wafer; before the top electrode ALD out of ± 0.5 nm; composition wrong
ALD chamber clean           remote-plasma BCl₃/Cl₂ at 350 °C       every 120–180 wafers (flake onset); never F
```

### 16.7.1 New-Product Checklist

```
For a new array, dielectric, or mold height, re-derive:
  □ Channel diameter and AR; ALD pulse; wrap x_sat; backside zone width       (Ch. 2, 14)
  □ Crystallization history; rates at each etch; amorphous before the top electrode  (Ch. 2)
  □ Volatility of every constituent and dopant: Class V or N                 (Ch. 3, 14)
  □ Stop selectivity: TiN thickness, spread, overetch; S ≥ OE × t / loss      (Ch. 4, 10)
  □ Fluorine budget; split the F and Cl chambers                              (Ch. 10)
  □ Shell lifetime vs step time; ion-energy window                            (Ch. 7)
  □ W loss vs the plate R_s budget                                            (Ch. 4, 7)
  □ Overlap budget: placement, undercut, damage, notch; × 1.5                  (Ch. 11)
  □ Damage as equivalent thickness; headroom; TDDB multiplier                  (Ch. 12)
  □ Dose margin ≥ 1.5 along the pillar; DMAC pressure                          (Ch. 6, 13)
  □ Zirconium zones; transfer chain; clean-zone entry limit                    (Ch. 9)
  □ Test structures: trim-dose, edge-proximity, polarity, chains               (Ch. 12, 15)
```

---

## Summary and Key Takeaways

1. **Each hand-off is irreversible.** Zirconium on a backside spreads, a grain under a contact is an open found weeks later, and a trim cannot be undone after the top electrode.

2. **The periphery tail is steep.** R1's opens per die rise from 1.5 × 10⁻⁴ to 0.33 when σ_g goes from 5% to 6%; 40% overetch brings the 6% case back to 1.6 × 10⁻³ for about $0.05 per wafer.

3. **R1 costs the same as R0 and yields more.** $10.53 against $10.70, with 21 chambers against 24; +2.4% by the model (+$13–31 per wafer after correction).

4. **The edge etch costs $3.44 per wafer.** It pays for itself if it prevents 1.4 furnace-contamination events of $3 M per year.

5. **The ALE finish is insurance, not a gain.** It adds $3.76 per wafer and is worth $0.39 at the reference spread, $31 at σ_g = 5.5%, and $723 at 6%.

6. **Do the cheap things first.** Overetch, then split chambers, then pulse the bias; only then pay for the thermal finish.

---

## Study Questions

1. Recompute the R1 opens per die and yield for OE = 45% and σ_g = 6%. What step time and shell margin does 45% give, and how much W is lost?

2. A fab runs at 150,000 wafer starts per month. Recompute the number of chambers of each type for R1 and the number of edge mainframes.

3. The edge-etch mainframe is $8 M instead of $6 M and runs at 80 wph. Recompute its depreciation per wafer and module E's total. What does the break-even become for a $2 M event?

4. A furnace contamination event costs $1.5 M instead of $3 M. How many events per year must the edge etch prevent to break even, and what does that imply for a fab with two furnace bays?

5. Compute the cost of ownership of R2 if the batch tool is $4 M with 20 s cycles and 15 min overhead (29 cycles per batch). Is the insurance premium of Section 16.6.2 changed?

6. Using the checklist of Section 16.7.1, list the changes to the process for a 1d-class product with AR 195 and a DMAC pulse of 2 s, and say which hand-off in Section 16.1 is most at risk.

---

**Back to:** [README](../README.md) | [INDEX](../INDEX.md)

---

**Chapter 16 Development Status:** Complete  
**Version:** 1.0
