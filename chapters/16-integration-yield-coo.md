# Chapter 16: Integration, Yield & Cost of Ownership

## Overview

The dielectric clear is a minute of plasma between a conductor etch and a dielectric deposition. Its cost is a few dollars per wafer. Its yield effect is measured in contact opens at a rate of less than one in 10⁸ contacts, discovered months later. And its choice of route, cold in-situ, hot split, plasma ALE, thermal ALE, or hybrid, changes the plate-etch mainframe, the fab's tool count, the plate edge, and the residue on the periphery all at once.

This chapter assembles the book into production terms. It follows the wafer from the clear to the periphery contacts, lists the yield signatures that point back to the dielectric clear, sizes the equipment for each route, builds the cost of ownership, puts a value on the yield the clear protects, and ends with a route-selection guide and a checklist for new products.

**Learning Objectives:**
- Trace the interactions between the dielectric clear and the ILD, the plate contact, and the periphery contacts
- Map yield and reliability signatures to their dielectric-clear mechanisms
- Size the equipment for 150,000 wafer starts per month on each route
- Build a cost of ownership for each route and compare it with the value of the yield at stake
- Rank the improvement levers by value per dollar
- Choose a route for a given product and list the checks a new product must pass

---

## 16.1 From the Clear to the Contacts

### 16.1.1 The Hand-Off Sequence

```
After the dielectric clear (reference):
  PET (H₂O/N₂ remote) → DI rinse → plasma bevel etch (F then BCl₃) →
  backside TXRF gate → ILD deposition (HDP oxide, ≈ 2 µm) → ILD CMP →
  plate contacts (through ILD and the oxide cap onto W) and periphery
  contacts (through ILD, periphery top SiN, and lower layers)
```

### 16.1.2 What Each Customer Needs From the Clear

```
Customer                    Needs                               From chapter
──────────────────────────────────────────────────────────────────────────────
ILD deposition              B ≤ 2 × 10¹⁴, Cl ≤ 1 at% on SiN;    12
                            no slot at the plate edge (or a
                            sealed one); step 255 nm
ILD CMP                     no blisters or delamination at the  12
                            boron-rich interface
Plate contact               oxide cap ≥ 45 nm remaining, known  12
                            to ± 3 nm; W intact (no cap
                            pinhole craters)
Periphery contacts          no ZrO₂ islands ≥ 1 nm under any    10
                            contact; SiN 118.7 ± 1 nm
Array (reliability)         leakage shift ≤ 10%; damage reach   13
                            ≪ overlap
Shared tools                backside Zr ≤ 1 × 10¹⁰ /cm²         9
```

### 16.1.3 The Periphery Contact Etch

The periphery contacts break through the ILD and then the periphery top SiN. The dielectric clear affects them in three ways. A residual ZrO₂ island stops them. The SiN thickness, 1.3 nm thinner than without the clear, shortens their nitride breakthrough slightly and is fed forward. And boron left on the nitride surface, at 1–2 × 10¹⁴ /cm², has no measurable effect on the fluorocarbon etch, which removes it as BF₃.

---

## 16.2 Yield Signatures

### 16.2.1 Signatures

```
Signature                                   Mechanism                          Ch.
──────────────────────────────────────────────────────────────────────────────────────
Random periphery contact opens, ZrO₂ at     Gaussian tail or non-Gaussian       10
the open (FA)                               residue (C, B glass, F, nodules)
Contact opens clustered near plate edges    ion tilt shadow; worn edge ring     6, 10
at the wafer edge
Ring of contact opens at the wafer edge     edge rate low (ring, edge zone);    6
                                            edge-thick film
Lot-level opens after a strip-chamber       carbon micromasks                   10
event
Opens on 10–100 neighbouring contacts       Zr-containing flake from D1 walls   9, 10
Plate-edge comb leakage up, contacts OK     B or Cl on the cleared SiN; PET     11, 12
                                            or rinse failure
Leakage and retention tail in cells near    edge ingress, oxygen loss, UV       11, 13
the array boundary only
Whole-bank leakage shift, uniform           strip hydrogen; thermal budget      13
ILD blisters or delamination over the       Cl outgassing; B₂O₃ at the          12
periphery                                   interface
Plate resistance outliers, W craters        oxide-cap pinholes                  12
Backside Zr excursion at the litho gate     bevel etch or ALD edge exclusion    9
                                            failure
```

### 16.2.2 The Value of a Fatal Open

Periphery contacts are not covered by the cell-repair redundancy; a die with one open periphery contact in a critical path is lost. With Book #32's wafer value:

```
Wafer value (illustrative): 860 good-die candidates × $3.0 ≈ $2,600 per wafer
1% die yield ≈ $26 per wafer

Reference budget (Chapter 10): ≈ 0.007 fatal opens per die from the clear
  → ≈ 0.7% die yield → ≈ $18 per wafer at risk
```

---

## 16.3 Equipment Sizing

```
Fab assumptions (illustrative, as in Book #32):
  Wafer starts      150,000 per month → ≈ 139 wafers per hour
  Availability      85%
```

```
Equipment per route (illustrative):

Route        Etch tools                                         Other tools
─────────────────────────────────────────────────────────────────────────────────────────
R0 cold      plate mainframes (4 plate + 2 strip/PET), 50 wph:  —
             139 / (50 × 0.85) = 3.3 → 4
D1 hot       split mainframes (3 C + 2 S + 2 D1), 60 wph:       oxide-cap PECVD;
(reference)  139 / (60 × 0.85) = 2.7 → 3                         BCl₃ step on bevel tool
D2 ALE       conductor mainframes (3 C + 2 S), 60 wph → 3;      oxide-cap PECVD
             ALE chambers at ≈ 9.2 wph:
             139 / (9.2 × 0.85) = 17.8 → 18 (3 mainframes of 6)
T thermal    conductor mainframes → 3;                          oxide-cap PECVD;
ALE (batch)  batch reactors at ≈ 24 wph (190 cycles):           ALD SiN seal;
             139 / (24 × 0.85) = 6.8 → 7                         no backside wet clean
Hybrid       split mainframes → 3                                single-wafer wet (HF)
                                                                 shared with the rinse
```

Moving the high-k step out of the conductor chambers reduces the plate mainframes from four to three. The two hot chambers per mainframe more than pay for themselves in conductor-chamber time. Plasma ALE needs eighteen chambers of its own; thermal ALE needs seven batch reactors.

---

## 16.4 Cost of Ownership

### 16.4.1 The Reference D1 Route

```
Plate module, D1 split route, per wafer (illustrative, full loading):
  Depreciation   mainframe $15 M over 5 years, 60 wph × 8760 × 0.85
                 = 4.5 × 10⁵ wafers/yr → $3.0 M/yr ÷ 4.5 × 10⁵      $6.70
  Consumables    rings, Y₂O₃ kits, window, hot-chamber parts         $1.40
  Gases, power   BCl₃, HBr, SF₆, Cl₂; RF, heaters                    $0.70
  Maintenance    including chlorine-first cleans and kit refurbish   $0.70
  Metrology      ellipsometry, TXRF, e-beam, edge OCD (allocated)    $1.00
  Total etch                                                         ≈ $10.50
  Oxide cap deposition (PECVD)                                       ≈ $1.00
  BCl₃ bevel step, extra strip/PET                                   ≈ $0.40
  Module etch-related total                                          ≈ $11.90

Book #32 cold route (R0), etch total for comparison                  ≈ $10.70
Difference                                                           ≈ + $1.20
```

Book #32 estimated the hot hard-mask route at + $2 to + $3 per wafer when hot chambers were added without rebalancing. Counting the conductor chambers freed by moving the high-k step out, the difference falls to about + $1.2.

### 16.4.2 The Alternatives

```
Route cost relative to D1 (illustrative, per wafer):
  Route                          Δ cost      Main benefit
  ─────────────────────────────────────────────────────────────────────────────
  R0 cold in-situ                − $1.2      no cap, no strip before the clear;
                                             but SiN loss 4 nm, charging phase,
                                             veils, carbon, and 4 plate mainframes
  D2 plasma ALE                  + $7 to $8  Gaussian spread 4%; SiN loss 0.2 nm;
                                             edge recess ≈ 0.4 nm; ring-wear
                                             immunity
  T thermal ALE (batch)          + $6 to $8  clears walls, bevel, and backside;
                                             infinite selectivity; but undercut,
                                             seal step, 4 h batches
  Hybrid (D1 + HF)               + $1        shorter dry overetch; but the tail
                                             is not fully removed
  D1 with OE 70% → 90%           + $0.25     Gaussian tail × 10⁻³; SiN + 0.4 nm
  Al₂O₃ sidewall liner           + $1.5      TE recess → ≈ 0; for thin-TE products
```

---

## 16.5 The Value of Each Lever

```
Value of improvements against the reference (illustrative):

Lever                          Δ fatal opens    Δ yield     Value      Cost       Net
                               per die                      per wafer  per wafer
────────────────────────────────────────────────────────────────────────────────────────
Halve carbon micromasks        − 0.0015         + 0.15%     + $3.9     ≈ $0.2     + $3.7
(strip endpoint, chamber)
Halve wall flakes (clean       − 0.0004         + 0.04%     + $1.0     ≈ $0.3     + $0.7
interval)
OE 70% → 90%                   − 0.002          + 0.2%      + $5.2     $0.25      + $5.0
(Gaussian slowest site)
D1 → D2                        − 0.001          + 0.1%      + $2.6     $7.5       − $4.9
(Gaussian only; non-Gaussian
unchanged)
D1 → T (with seal)             ≈ 0 (tail        ≈ 0         ≈ 0        $7         − $7
                               same at 190
                               cycles)
Overlap 1.5 → 0.4 µm           —                + 0.2%      + $5       qualification
(die area)                                      die area
```

The cheapest gains are not in the choice of route. They are in the overetch, which is nearly free in D1 up to the point where the Gaussian tail vanishes, and in the strip, which sets the largest non-Gaussian source. A route change to ALE pays only when something other than residue limits the process: a thin top electrode that cannot tolerate 1.2 nm of recess, an overlap pushed below 0.4 µm, a damage-sensitive dielectric, or a nitride landing budget much tighter than 5 nm.

The overetch row needs one qualification. Going from 70% to 90% removes the Gaussian contribution almost entirely, but it lengthens the exposure of the plate edge by 7 s (+0.15 nm of TE recess) and the landing nitride by 0.4 nm. Both are within specification at the reference; neither would be at a thinner TE or a tighter landing budget.

---

## 16.6 Decisions

### 16.6.1 Route Selection

```
Choosing a route (illustrative):

Product condition                               Route
─────────────────────────────────────────────────────────────────────────────
Mature 6F², 1.5 µm overlap, cost-driven         R0 (cold in-situ) acceptable;
                                                D1 if a mainframe is saved
Standard 6F², overlap ≤ 1 µm, residue-driven    D1 (reference)
TE ≤ 3 nm, or edge recess must be < 0.5 nm      D2, or D1 with a sidewall liner
Overlap < 0.3 µm (4F²)                          D2; overlap ladder qualification
Topography that must be cleared (marks, 3D)     T, with an ALD SiN seal
Sr- or rare-earth-containing dielectric         chlorinate-and-rinse hybrid
```

### 16.6.2 New-Product Checklist

```
Before a new product or stack is released on the dielectric clear:
  1. Incoming    periphery ZAZ thickness, radial profile, phase mix;
                 surface after the conductor etch and strip (Ti, C, F)
  2. Chemistry   rates of each dielectric layer and the landing film at the
                 operating point; endpoint markers for the stack
  3. Clearing    σ_g from the Al-marker width and AFM; overetch for z ≥ 6.4
                 at the slowest site; e-beam island density ≤ 20 /cm²
  4. Edge        TE, SiGe, W recess on the edge grating; undercut by TEM;
                 Cl ingress by EELS/ToF-SIMS
  5. Surface     B, Cl after PET and rinse; ILD adhesion test
  6. Damage      array leakage and TDDB; overlap-ladder reach ≪ overlap
  7. Electrical  contact chains ≥ 10⁸ contacts with no Zr-related opens;
                 plate-edge comb ≤ 1 pA/mm
  8. Contamination  backside and bevel Zr at the shared-tool gate
  9. Control     FF and EWMA loops set; FDC limits; VM model retrained
```

---

## Summary and Key Takeaways

1. **The clear's customers are the ILD, the plate contact, the periphery contacts, the array, and the shared tools.** Each needs something different from the same minute of plasma.

2. **Yield signatures point back to specific mechanisms:** random opens to the tail, edge clusters to tilt and ring wear, comb leakage to surface residues, array-boundary leakage to the edge.

3. **The split route saves a plate mainframe.** Three split mainframes replace four cold-route mainframes at 150,000 wafer starts per month.

4. **D1 costs about $1.2 per wafer more than the cold route;** ALE routes cost $6–8 more.

5. **The cheapest yield is in the overetch and the strip.** A route change to ALE pays only when the edge, the landing film, the overlap, or damage limits the process.

6. **A new product passes nine checks,** from incoming film to shared-tool contamination, before it runs on the clear.

---

## Study Questions

1. Recompute the equipment count for D1 if the conductor recipe shortens to 150 s per wafer and the D1 chamber time stays at 102 s. Is the third mainframe still needed?

2. A fab at 100,000 wafer starts per month runs the cold route on three mainframes. Is converting to D1 worth it? Include the cap deposition and the freed mainframe in your estimate.

3. The carbon micromask density doubles after a strip-chamber change. Using Chapter 10 and Section 16.5, estimate the yield loss and its value per wafer. How long can the fab run before the loss exceeds the cost of a dedicated strip chamber ($3 M)?

4. A product with a 3 nm TE cannot tolerate more than 0.5 nm of recess. Compare the cost per wafer of D2 and of D1 with an Al₂O₃ sidewall liner. Which other differences would decide the choice?

5. Using Section 16.5, rank the levers by net value per wafer for a product whose wafer value is $4,000 instead of $2,600.

6. Write the yield-signature table entry for a failure mode not listed in Section 16.2.1, for example a PET chamber that runs at 150 °C instead of 250 °C, with its mechanism and detecting measurement.

---

**Back to:** [README](../README.md) | [INDEX](../INDEX.md)

---

**Chapter 16 Development Status:** Complete  
**Version:** 1.0
