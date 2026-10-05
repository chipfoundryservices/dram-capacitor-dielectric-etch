# Chapter 16: Integration, Yield & Cost of Ownership

## Overview

The three dielectric etches are small steps by the measure of chamber time: about three minutes at the bevel, four in the plate chamber, ten in a thermal reactor for the pilot trim. Their influence is out of proportion to their size. The bevel removal decides whether zirconium leaves the capacitor module on every wafer. The periphery clear decides whether thirty million contacts per die open. The trim, where it is used, changes every capacitor on the wafer. This chapter places the three modules in the flow by their hand-offs, lists the yield signature each leaves when it fails, sizes the equipment for a production fab, builds a cost of ownership for each module and its alternatives, weighs that cost against yield, and closes with the decisions an integration team must make and a checklist for a new product.

**Learning Objectives:**
- State the hand-off conditions from each dielectric etch to the next step
- Recognize the yield signature of each module's failure modes
- Size the bevel, plate, and trim equipment for 150,000 wafer starts per month
- Compute the cost of ownership of each module and compare routes
- Weigh the cost of the ALE finish against the yield it protects
- Make the route decisions for a new product

---

## 16.1 Hand-Offs

```
From                  To                     Hand-off conditions (reference)
──────────────────────────────────────────────────────────────────────────────────
ZAZ ALD               Module 3 (pilot) or    thickness 5.5 (6.5) nm ± 1.5%; step
                      TE TiN                 coverage ≥ 96%; particle adders
Module 3 (pilot)      TE TiN                 trim 1.00 ± 0.05 nm (pad); F ≤ 1 at%;
                                             vacuum or ≤ 2 h queue
TE TiN                Module 1 (bevel)       TE continuous (no scratches: the TE
                                             sheet is the module-1 clamp, Ch. 13)
Module 1 (bevel)      Pre-clean, SiGe fill   boundary 148.8 ± 0.1 mm; bevel and
                      (batch furnace)        backside Zr ≤ 1 × 10¹⁰ /cm²; ≤ 24 h
                                             queue (boron ring)
Plate conductor       Module 2               TE TiN exposed in the periphery;
steps (Book #32)                             resist ≥ 330 nm; same chamber
Module 2              Strip and treatment    ≤ 5 min, vacuum transfer
Strip                 ILD deposition         B on SiN ≤ 5 × 10¹³ /cm²; Cl ≤ 0.5 at%;
                                             backside Zr ≤ 5 × 10⁹ /cm²; ≤ 24 h
ILD                   Periphery contacts     no ZrO₂ residue under contacts
                      (Books #6–10)          (verified only at chains and test)
```

Two hand-offs carry the risk of the whole book. The bevel hand-off to the SiGe furnace is where a missed specification spreads zirconium to a hundred wafers per run and to the furnace itself. The ILD-to-contact hand-off is where the periphery clear's tail becomes die yield, weeks after the etch.

---

## 16.2 Yield Signatures

```
Signature                              Module   Mechanism                    Chapter
───────────────────────────────────────────────────────────────────────────────────────
Single periphery contact opens,        2        Gaussian tail: R_slow up      6, 10
edge dies, rising with ring hours               (ring wear), short main step
Single opens, whole wafer              2        EPC drop; BₓClᵧ micromasking  4, 5, 10
Clusters of 3–20 opens                 2        wall or PEZ flakes            9, 10
One large residue blocking a group     ZAZ ALD  ALD flake in the film         9
Opens along plate outlines             2        veil fragments                10
ILD voids / corrosion at plate edges   2        TE notch, queue time          11
Ring of edge-die defects (r ≈ 147 mm)  1        flakes from the boundary      11
                                                staircase; boron ring
Edge dies with plate defects at the    1        boundary too far in (radius   7, 11
outermost array blocks                          error, eccentricity)
Threshold shifts / leakage in other    1        Zr carried to shared tools    9
products in shared furnaces                     (bevel or backside)
Array-wide retention shift             3        trim over-etch, grooves, F    12, 13
Retention tail near array edges        2        edge chemistry, charging      11, 13
(layouts with tight plate overlap)
```

---

## 16.3 Equipment Sizing

```
150,000 wafer starts per month ≈ 210 wafers per hour; availability 85%

Module 1 (bevel):
  225 s per wafer per chamber → 16 wph
  Chambers: 210 / (16 × 0.85) ≈ 15.4 → 16 (4 platforms of 4)

Module 2 (plate chamber with the ALE finish, single-chamber route):
  400 s per wafer → 9.0 wph
  Chambers: 210 / (9.0 × 0.85) ≈ 27.5 → 28
  Continuous route (Book #32), 270 s → 13.3 wph → 19 chambers
  The ALE finish costs 9 additional plate chambers

Module 2, split route (ALE in a second chamber on the same platform):
  Plate chamber: 233 s → 15.5 wph → 16 chambers
  ALE chamber:   192 s → 18.8 wph → 14 chambers (simpler: no high-power
                 bias, no SF₆)
  Total 30 chambers, of which 14 are the cheaper ALE type

Module 3 (trim, if used at full volume):
  Mini-batch reactor, 5 wafers per 745 s → 24 wph
  Reactors: 210 / (24 × 0.85) ≈ 10.3 → 11
```

---

## 16.4 Cost of Ownership

### 16.4.1 Basis

```
Cost basis (illustrative):
                                 Annual cost per chamber    Cost per second
                                 (depreciation, parts,      of chamber time
                                 service, gases, space)     at 85% uptime
  ──────────────────────────────────────────────────────────────────────────
  ICP plate chamber              $1.10 M                    $0.041
  ALE-only ICP chamber           $0.85 M                    $0.032
  Bevel chamber                  $0.80 M                    $0.030
  Strip chamber                  $0.45 M                    $0.017
  Thermal ALE mini-batch         $0.90 M                    $0.034 (per batch-s)
  reactor
```

### 16.4.2 Module 1

```
Bevel chamber time 225 s × $0.030        $6.70
VPD sampling, edge inspection            $0.20
Bevel rinse (fallback, ≈ 10% of lots)    $0.10
────────────────────────────────────────────────
Module 1                                 ≈ $7.00 per wafer
Hot-bevel variant (≈ 130 s; 9 chambers)  ≈ $4.20 per wafer
```

### 16.4.3 Module 2

```
                                   Continuous    Reference      Split route
                                   (Book #32)    (ALE finish)   (ALE chamber)
───────────────────────────────────────────────────────────────────────────────
Dielectric steps in plate chamber  93 s          60 s           60 s
  (TiN clear, main, transition)    $3.80         $2.50          $2.50
ALE finish                         —             162 s          192 s incl.
                                                 $6.60          exchange
                                                                $6.10
Extra wafer exchange                —             —              $0.30
Strip and treatment (60 s)         $1.00         $1.00          $1.00
HF veil dip                        $0.60         —              —
Monitoring (chains, TXRF, ladders) $0.40         $0.50          $0.50
───────────────────────────────────────────────────────────────────────────────
Module 2                           ≈ $5.80       ≈ $10.60       ≈ $10.40
```

The ALE finish adds about $4.80 per wafer, most of it chamber time. The split route saves little in operating cost; its advantage is in capital, because the 14 ALE chambers are simpler than plate chambers.

### 16.4.4 Module 3 (Pilot)

```
Reactor time 149 s per wafer (batch-averaged) × $0.034   $5.10
HF and DMAC (≈ 0.1 g DMAC per wafer, incl. waste)        $0.80
TEM and electrical sampling (pilot level)                $0.60
──────────────────────────────────────────────────────────────
Module 3                                                 ≈ $6.50 per wafer
```

---

## 16.5 The Value of Yield

### 16.5.1 Contact Opens

```
Die yield from periphery contact opens: Y = exp(−λ), λ = opens per die

Module-2-attributable λ (illustrative):
                              Continuous     Reference (ALE finish)
  ─────────────────────────────────────────────────────────────────
  Gaussian tail (avg)         ≈ 0.002        ≈ 0.0004
  Veils                       ≈ 0.003        ≈ 0.0004
  Flakes, ALD flakes, B mask, ≈ 0.007        ≈ 0.007
  abnormal grains
  ─────────────────────────────────────────────────────────────────
  Total λ                     ≈ 0.012        ≈ 0.008

Wafer value (950 dies × $4)   ≈ $3,800
Yield difference              ≈ 0.4%  →  ≈ $15 per wafer
```

On contact yield alone, the ALE finish returns about three times its cost. Its other benefits are harder to price but point the same way: 0.4 nm of SiN loss instead of 2–7 nm makes the periphery contact etch's SiN-open step more uniform; a 1.3 nm TE notch instead of 4 nm removes a site of ILD voids and corrosion; half the high-energy ion time halves the charging dose.

The break-even is low: the finish pays for itself if it lowers λ by more than about 0.0013 opens per die. A team that doubts the veil and tail numbers above should ask whether the finish achieves at least that, not whether it achieves all of them.

### 16.5.2 The Bevel

The bevel removal has no break-even calculation. Its alternative is not a cheaper route but contaminated furnaces and edge flakes. The economic questions within it are the hot-bevel variant (saves ≈ $2.80 per wafer and seven of the sixteen chambers, at the cost of tighter TiN-creep control) and the rinse policy (fallback or every wafer).

### 16.5.3 The Trim

```
What +5% C_s is worth (illustrative):
  Equivalent by mold height:     +80 nm of mold (5% of 1.6 µm)
    Extra hole and mold etch     ≈ $2 per wafer
    Pillar-bending risk at the   yield risk; hard to price
    higher aspect ratio
  Equivalent by sense margin:    +5% signal; retention margin at the
                                 10⁻⁶ point
  Cost of the trim:              ≈ $6.50 per wafer, plus leakage +10–20%
                                 and a whole-array excursion risk
```

The trim is not cheaper than a taller mold at the 1c generation. It becomes the only option when the mold cannot grow further and the channel cannot afford a thicker film, which is where the 4F² arithmetic of Chapter 14 places it.

---

## 16.6 Decisions

```
Decision                         Options                       Reference choice and reason
───────────────────────────────────────────────────────────────────────────────────────────
Bevel timing                     after TE / after SiGe / after after TE, before the SiGe
                                 W                             furnace (Ch. 1, 7)
Bevel chemistry and              60 °C dry / hot dry /         60 °C dry with rinse
temperature                      dry + rinse                   fallback; evaluate hot
Periphery-clear route            continuous / ALE finish /     ALE finish (Ch. 10, 16.5)
                                 hot / quasi-ALE / wet hybrid
Main-step temperature            60 / 120 °C                   60 °C; 120 °C would save six
                                                               cycles if the plate edge and
                                                               resist allow (Ch. 10)
ALE arrangement                  same chamber / split          same chamber at pilot volume;
                                                               split at high volume for
                                                               capital
Bias waveform in ALE             13.56 MHz / 40 MHz / tailored tailored (Ch. 5)
Cycle-count policy               fixed / ring-hour / adaptive  ring-hour compensated; never
                                                               below 36 (Ch. 15)
Trim                             none / pilot / production     pilot at 1c; production at
                                                               4F² pitches (Ch. 12, 14)
```

### 16.6.1 New-Product Checklist

```
□ Dielectric stack and thickness; Al marker present? (Ch. 2, 8)
□ Crystalline fraction at module 1 and at module 2 (Ch. 2)
□ Backside wrap extent in the ALD tool; bevel clearing radius (Ch. 2, 7)
□ Bevel ion energies on the new edge profile; boundary radius vs last die
□ Periphery open area and contact count; grain-site count (Ch. 10)
□ Clearing-time map; R_slow; σ_r of the main step (Ch. 3, 6)
□ Cycle count from N = ⌈(R_slow + 6.4σ − b)/EPC⌉; ladder to verify (Ch. 6, 15)
□ ALE window and IEDF in the qualified chamber (Ch. 4, 5)
□ SiN EPC and loss at the fastest site (Ch. 10)
□ Plate-edge distance to active capacitors; edge-intensive arrays (Ch. 11, 13)
□ Strip water fraction and temperature; B and Cl on SiN (Ch. 10)
□ Wall clean order with the conductor steps' fluorine (Ch. 9)
□ Zr cross-contamination plan: cover-wafer WAC, backside scrub, tool
  dedication (Ch. 9)
□ If a trim: channel radius, reactant demand, bottom-to-top ratio, groove
  depth, F after O₃ (Ch. 12)
□ For non-volatile dopants or Sr: water rinse in the route (Ch. 14)
□ Equipment count and cost per wafer for the chosen routes (Ch. 16)
```

---

## Summary and Key Takeaways

1. **Two hand-offs carry the risk.** Bevel to the SiGe furnace (zirconium spread) and ILD to the periphery contacts (residue becomes yield).

2. **Each module fails with its own signature.** Edge-weighted single opens for the tail, clusters for flakes, outlines for veils, edge rings for the bevel, array-wide shifts for the trim.

3. **The ALE finish costs chambers.** Nine more plate chambers at 150,000 wafers per month, or a split route with fourteen simpler ones.

4. **It pays through yield.** About $4.80 per wafer buys about $15 of contact yield; it breaks even at a λ reduction of 0.0013 per die.

5. **The bevel is mandatory; its variant is the choice.** A hot bevel would save $2.80 per wafer and seven of sixteen chambers.

6. **The trim is a tool for the end of scaling.** At 1c it costs more than a taller mold; at 4F² pitches it may be the only way to keep both capacitance and the top electrode.

---

## Study Questions

1. Recompute the number of plate chambers needed for the reference route if the ALE cycle is shortened from 4.5 s to 3.5 s with no loss of EPC. What is the new module-2 cost per wafer?

2. Using the cost basis of Section 16.4.1, compute the module-2 cost for a quasi-ALE finish of 70 s. If its λ is 0.010, which route gives the lowest total cost (operating cost plus yield loss) per wafer?

3. A fab runs at 80,000 wafer starts per month. Size the bevel chambers and the plate chambers for the reference routes. Does the split route still make sense?

4. The hot-bevel variant raises the TE TiN creep under the PEZ by 0.2 mm, so the boundary staircase widens. What specification would you have to relax, and what would you check on the edge dies?

5. A product's die is worth $6 and has 4.5 × 10⁷ periphery contacts. Recompute the break-even λ reduction for the ALE finish and the value of the reference reduction (scale the Gaussian and veil terms with the contact count).

6. Using Section 16.5.3, under what conditions would the trim be preferred to a taller mold at the 1c generation? List the measurements that would decide it.

---

**Chapter 16 Development Status:** Complete  
**Version:** 1.0

---

**End of Main Text.** Continue to the [Appendices](../appendices/A-material-properties.md), the [Glossary](../GLOSSARY.md), and the [Index](../INDEX.md).
