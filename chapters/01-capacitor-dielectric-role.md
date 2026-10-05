# Chapter 1: The Capacitor Dielectric & Why It Is Etched

## Overview

A DRAM storage capacitor is two conductors and the film between them. Books #29–32 of this series made the conductors: the hole, the TiN pillar inside it, the mold removed from around it, the plate wrapped over it. This book is about the film. It is 5.5 nm of zirconium and aluminium oxide, deposited by atomic-layer deposition (ALD) over the whole wafer, and it is the part of the capacitor that sets how much charge the cell holds and how long it holds it.

ALD does not know where the capacitors are. It coats the pillars, and it coats everything else: the periphery, the scribe lines, the wafer bevel, the apex, and a few millimetres of the backside. Most of that coating must be removed, and in the newest flows the part that stays must sometimes be thinned. These are the **capacitor dielectric etches**. This chapter explains what the dielectric does, where ALD puts it, why each unwanted part must go, where the three etches of this book sit in the process flow, and the specification sheet that the rest of the book works against.

**Learning Objectives:**
- Compute the storage capacitance and leakage of the reference cell from the dielectric's thickness, permittivity, and area
- Explain why ALD deposits the dielectric over the whole wafer and list the five places it meets an etch
- Explain why a ZrO₂ grain at a periphery contact, a dielectric film on the bevel, and a nanometre of thickness in the array each matter
- Place the bevel removal, the periphery clear, and the in-array trim in the capacitor module flow
- State the specification of each etch and the failure that each line protects against

---

## 1.1 What the Dielectric Does

### 1.1.1 Capacitance

The storage capacitance of a cell is set by three numbers: the area of the electrode surface the dielectric covers, the dielectric's permittivity, and its thickness:

```
C_s = ε₀ k A / t = ε₀ · 3.9 · A / EOT

Reference cell:
  A   = 1.24 × 10⁵ nm²     effective area (outer pillar surface below the top
                            support, less support contacts; Book #30, Ch. 1)
  t   = 5.5 nm             ZrO₂ 2.6 / Al₂O₃ 0.3 / ZrO₂ 2.6 (ZAZ)
  k   ≈ 43                 effective, after crystallization (Chapter 2)
  EOT = 3.9 t / k = 0.50 nm

  C_s = 8.854 × 10⁻²¹ F/nm × 43 × 1.24 × 10⁵ nm² / 5.5 nm = 8.6 fF
```

The electrode area is enormous compared with the cell. Each cell occupies 1734 nm² of the wafer surface and wraps 1.24 × 10⁵ nm² of dielectric around its pillar, a ratio of about 72. Over one wafer, with about 40% of its area in cell arrays, the capacitor dielectric covers **about 2 m²**, nearly thirty times the wafer's own area. The parts this book removes, from the periphery and the edge, are about 2% of that.

### 1.1.2 Sensitivity to Thickness

Because C_s scales as 1/t, every 0.1 nm of dielectric is worth about 1.8% of capacitance:

```
dC_s / C_s = −dt / t = −0.1 / 5.5 = −1.8% per 0.1 nm added
```

Leakage moves the other way and much faster. Conduction through crystallized ZAZ at 1 V is dominated by trap-assisted tunnelling, which falls roughly exponentially with thickness:

```
J(t) ≈ J₀ exp(−t/λ),   λ ≈ 0.25 nm (illustrative, ZAZ at 1.0 V, 85 °C)

  Thinner by 0.1 nm:  J × 1.5
  Thinner by 0.5 nm:  J × 7.4
  Thinner by 1.0 nm:  J × 55
```

A uniform loss of a few tenths of a nanometre is a capacitance gain and a leakage loss of comparable importance. A *local* loss, at a grain boundary or an edge, is only a leakage loss. This asymmetry runs through Chapters 11–13: an etch that touches the remaining dielectric is judged by its worst nanometre, not its average.

### 1.1.3 Leakage and Retention

The cell holds its charge for the refresh interval of 64 ms:

```
Q = C_s V_core = 8.6 fF × 1.10 V = 9.5 fC
Retention budget (Book #32, Ch. 1):  I_max ≈ 30 fA for all leakage paths
Dielectric allocation:              ≈ 1 fA per cell at 1.0 V, 85 °C
                                    (8 × 10⁻⁷ A/cm² over 1.24 × 10⁵ nm²)
```

In operation the dielectric sees at most ±0.55 V, because the plate sits at V_core/2; at that bias its leakage is about two orders of magnitude lower. The specification at 1.0 V is the margin for the tail: the one cell in 10⁸ whose dielectric has a thin spot, a damaged edge, or a trap-rich grain boundary. **Retention tails, not mean leakage, are what the dielectric etches can harm.**

---

## 1.2 Why ALD Puts It Everywhere

### 1.2.1 Self-Limiting Growth

ALD grows a film by alternating exposures to a metal precursor and an oxidant, each of which reacts only with the surface left by the other. Each cycle adds about 0.08–0.1 nm, the same amount on every surface the gases can reach. That is why the film has the same thickness at the bottom of the pillar forest as at its top; it is also why there is no way to make it stop at the edge of the array.

```
Where the ZAZ deposition puts the dielectric (reference wafer):

  Surface                              Area (cm²)    Fate
  ──────────────────────────────────────────────────────────────────────────
  Pillar walls and supports in the     ≈ 20,000      the capacitor; kept
  arrays (effective)                                 (thinned in module 3)
  Array-block tops and plate overlap   ≈ 390         under the plate; kept
  (55% of the front)
  Periphery and scribe lines           ≈ 318         removed by module 2
  (45% of the front)
  Front bevel ring, r ≥ 148.8 mm       ≈ 11          removed by module 1
  Apex                                 ≈ 7           removed by module 1
  Backside ring, r ≥ 147.0 mm          ≈ 28          removed by module 1
```

How far the film reaches onto the backside depends on how the wafer sits in the ALD chamber. On a susceptor with edge clearance, precursor diffuses under the wafer edge, and the film thins over 2–3 mm from the apex inward (Chapter 2, Section 2.6).

### 1.2.2 The Five Places the Dielectric Meets an Etch

```
Plan view of one die and the wafer edge (not to scale):

  ┌─────────────────────────── die ───────────────────────────┐
  │  ┌───────── plate island ─────────┐                        │
  │  │  array: ZAZ on pillars    (5) │  periphery: ZAZ on SiN │
  │  │  thinned by module 3          │  removed by module 2 (1)│
  │  └────────────────(2)────────────┘                        │
  │          plate edge: cut edge of the ZAZ                  │
  └────────────────────────────────────────────────────────────┘
                                          wafer edge ─────────┐
       front ring (3) ── apex ── backside ring (4)            │
       removed by module 1                                     │
```

1. **Periphery and scribe lines**: the dielectric lies flat on the periphery top SiN and must be cleared completely at the end of the plate etch.
2. **Plate edge**: where the plate etch stops, the remaining dielectric has a cut edge, exposed to the plasma, the strip, and the next deposition.
3. **Front bevel ring**: outside the last full die, between the edge exclusion and the shoulder of the bevel.
4. **Apex and backside**: places the plate etch never reaches, because they face away from the plasma or are shadowed by the chuck.
5. **The channels between pillars**: inside the array, where the dielectric is the capacitor and is touched only by a trim.

---

## 1.3 Why Each Place Matters

### 1.3.1 The Periphery: Grains That Stop Contacts

After the plate etch, the periphery is covered by an inter-layer dielectric about 1.8 µm thick, and about 3 × 10⁷ contacts per die are etched through it to the transistors and the bit lines below. The contact etch is a fluorocarbon etch (Books #6–10). On SiO₂ and SiN it etches hundreds of nanometres per minute. On ZrO₂ it forms a ZrF₄ skin, which does not volatilize, and stops:

```
Contact etch on a ZrO₂ grain (illustrative):
  Oxide rate (C₄F₆/O₂/Ar, 1.8 µm, 40 nm contact)    ≈ 500 nm/min
  ZrO₂ rate (sputtering of ZrF₄ only)                ≈ 0.2 nm/min
  Selectivity                                         > 2000
  Contact overetch                                    ≈ 30%, ≈ 1 min
  ZrO₂ removed by the overetch                        ≈ 0.2 nm

A grain 1 nm thick survives the contact etch.
  Covering the whole 40 × 40 nm bottom:   open contact
  Covering a quarter of the bottom:       resistance roughly × 4; marginal
```

The residue does not short anything and is not visible at the plate etch. It is found weeks later, at the contact-chain test, as opens that cluster in the periphery of particular wafers. Chapter 10 works out how small the probability of leaving a grain must be: with about 1.2 × 10⁸ grain-sized sites under the contacts of each die, the probability that any one site keeps a grain must be below about 10⁻¹⁰.

Residual dielectric also matters elsewhere in the periphery. On the overlay and alignment marks in the scribe lines, an uneven film changes the mark signal. On SiN under the inter-layer dielectric, a boron-rich residue degrades adhesion and outgasses (Chapter 10, Section 10.5).

### 1.3.2 The Bevel and Backside: Zirconium That Travels

The dielectric on the bevel and backside never sees a plasma in the plate etch. Unless it is removed, it leaves the capacitor module on every wafer:

```
Zr areal density in the ZAZ:          ≈ 1.5 × 10¹⁶ atoms/cm²
Backside/bevel Zr limit (typical):     ≤ 1 × 10¹⁰ atoms/cm²
Required removal factor:               1.5 × 10⁶
```

Zirconium on the backside transfers to vacuum chucks, end effectors, furnace boats, and lithography wafer tables. From there it reaches the front of other wafers, including wafers at the gate-oxide and implant steps, where transition-metal contamination at 10¹⁰ atoms/cm² degrades leakage and lifetime. The first batch furnace after the dielectric, the LPCVD SiGe plate fill, is where an uncontrolled bevel would do most harm: one boat carries a hundred wafers, and its quartzware keeps what it collects.

The bevel film also anchors a stack. Over the ZAZ on the apex and backside, the plate fill adds 150 nm of SiGe and the strap 40 nm of W, each with its own stress, on surfaces that were never prepared for adhesion. Such stacks peel in sheets at later thermal steps and drop flakes on the edge dies of the same wafer and on other wafers in the same carrier. Chapter 11 follows the flakes.

### 1.3.3 The Channels Between Pillars: Thickness the Gap Cannot Afford

Inside the array, the dielectric is the capacitor and is never removed. But at the 1c generation and beyond, the open channel between three neighbouring pillars becomes too narrow for the dielectric to be deposited at the thickness at which it crystallizes best. A ZrO₂ layer thinner than about 3 nm crystallizes less completely into its high-k tetragonal phase. The pilot flow of Chapter 12 deposits ZAZ at 6.5 nm, crystallizes it, and trims 1.0 nm from the top ZrO₂ by thermal ALE, so that the top electrode still has room to coat every pillar:

```
Open channel between three pillars, just below the top support (radius):

                         Before dielectric   After 5.5 nm   After 6.5 nm   After trim
  1b reference (45 nm)   10.3 nm             4.8 nm         —              —
  1c pilot (41 nm)       10.2 nm             —              3.7 nm         4.7 nm

Top electrode TiN reaches the bottom of the forest at a thickness equal to
the channel radius at the top, where the channel closes first.
```

The trim is the only etch in this book that touches the dielectric that stays. It is a pilot module, used only where the gain in capacitance and leakage outweighs the risk of touching every capacitor in the array.

---

## 1.4 Where the Dielectric Etches Sit

### 1.4.1 The Capacitor Module

```
Capacitor module flow (reference, from the TiN fill onward):

  1.  TiN storage-node fill, 18 nm                    Book #32, Ch. 2
  2.  Storage-node separation (etch-back)             Book #32, module 1
  3.  Support open and mold dip-out                    Book #30
  4.  Pre-clean; ZAZ ALD, 300 °C                       Chapter 2
  4a. [Pilot: post-deposition anneal 420 °C;
       in-array trim by thermal ALE]                   MODULE 3 (Chapter 12)
  5.  Top-electrode TiN ALD, 5 nm, 400 °C              Chapter 2
  6.  Bevel and backside removal of TiN and ZAZ        MODULE 1 (Chapters 7, 11)
  7.  SiGe:B plate fill, LPCVD 425 °C (batch)          ZAZ fully tetragonal
  8.  W strap, PVD 40 nm
  9.  Plate lithography, KrF, 500 nm resist
  10. Plate etch, conductor steps (W, SiGe, landing    Book #32, module 2
      on the top-electrode TiN)
  11. Periphery clear: TiN clear, ZAZ main step,       MODULE 2 (Chapters 3, 4,
      ALE finish; strip and treatment                    10, 11)
  12. Inter-layer dielectric; periphery contacts       Books #6–10
```

The order of steps 5–7 is not arbitrary. The bevel removal must come **after** the top-electrode TiN, because the TiN also wraps the bevel and must be removed with the ZAZ, and because the TiN caps the dielectric everywhere else while the bevel plasma runs. It must come **before** the SiGe fill, because that is the first batch furnace the wafer enters after the dielectric, and because the SiGe would otherwise bury the bevel dielectric under 150 nm of a second film.

### 1.4.2 What Each Etch Sees

```
                        Module 1 (bevel)     Module 2 (periphery)   Module 3 (trim)
──────────────────────────────────────────────────────────────────────────────────────
Films to remove         TiN 5 nm +           TiN 5 nm + ZAZ 5.5 nm  ZrO₂ 1.0 nm of the
                        ZAZ 5.5 nm           (after Book #32's W    top layer
                        (backside ≤ 4 nm)    and SiGe steps)
ZAZ phase               partly crystalline   tetragonal             tetragonal (after
                        (after TE at 400 °C) (after SiGe at 425 °C) the 420 °C PDA)
Mask                    none; plasma         500 nm KrF resist      none; the whole
                        confined to the edge (≈ 300 nm left)        wafer is etched
Lands on                SiN, oxide, bare Si  periphery top SiN,     nothing: stops within
                        (edge and backside)  120 nm                 the top ZrO₂ by cycle
                                                                    count
Area exposed            ≈ 46 cm² (6.6% of    ≈ 318 cm² (45%)        ≈ 2 m² (inside the
                        the front area)                             arrays)
Etch type               continuous plasma    continuous + plasma    thermal ALE
                                             ALE                    (isotropic)
Plasma time             ≈ 3 min              ≈ 4 min                ≈ 10 min (thermal)
```

---

## 1.5 The Specification Sheet

```
MODULE 1 — BEVEL AND BACKSIDE REMOVAL
──────────────────────────────────────────────────────────────────────────────
Parameter                         Specification          Protects against
──────────────────────────────────────────────────────────────────────────────
Front boundary radius             148.8 ± 0.1 mm         die loss (too far in);
                                                         residual ring (too far out)
Boundary concentricity            ≤ 50 µm                one-sided loss of edge dies
Transition width (90% → 10%)      ≤ 300 µm               partial-film flakes
Zr on apex and backside           ≤ 1 × 10¹⁰ atoms/cm²   cross-contamination
(r ≥ 147.0 mm, VPD-ICP-MS)
Ti on apex and backside           ≤ 5 × 10¹⁰ atoms/cm²   cross-contamination
B on bevel after treatment        ≤ 1 × 10¹⁴ atoms/cm²   hygroscopic residue, haze
Added particles (≥ 45 nm, front)  ≤ 10 per wafer         edge-die defects
TiN loss inside r = 148.6 mm      none detectable        plate continuity at
                                                         edge dies

MODULE 2 — PERIPHERY CLEAR
──────────────────────────────────────────────────────────────────────────────
Zr residue, periphery pads        ≤ 1 × 10¹³ atoms/cm²   (average; necessary, not
(TXRF)                                                   sufficient)
Residue-attributable contact      ≤ 0.01 per die         contact opens
opens
Grain-residue probability at      ≤ 8 × 10⁻¹¹            contact opens (Chapter 10)
the slowest site
Periphery SiN loss                ≤ 2 nm (ref. 0.4 nm)   periphery contact landing,
                                                         later nitride budget
Lateral ZAZ etch at plate edge    ≤ 1 nm                 edge leakage
Cl at the ZAZ edge                ≤ 3 at% after          edge leakage, corrosion
                                  treatment
B on the periphery SiN            ≤ 5 × 10¹³ atoms/cm²   ILD adhesion, outgassing
(after treatment)
Resist remaining at end of step   ≥ 150 nm               plate-edge erosion
Plate-edge leakage monitor        ≤ 1.1 × array-centre   edge damage (Chapter 13)
                                  monitor

MODULE 3 — IN-ARRAY TRIM (PILOT)
──────────────────────────────────────────────────────────────────────────────
Trim amount                       1.00 ± 0.10 nm (3σ)    EOT and leakage spread
Bottom-to-top trim ratio in the   ≥ 0.90                 capacitance spread along
channel                                                  the pillar
Excess thinning at grain          ≤ 0.3 nm               leakage tails
boundaries
F incorporated in ZrO₂            ≤ 1 at%                leakage, reliability
SiN support loss                  ≤ 0.5 nm               support strength
EOT after trim                    0.47 ± 0.01 nm         capacitance
Leakage at 1.0 V (median, tail)   ≤ untrimmed 5.5 nm     retention
                                  baseline
```

---

## 1.6 What Makes Dielectric Etch Different

1. **The film is refractory.** Fluorine chemistry, the workhorse of dielectric etch, does not etch it. Chlorine etches it only with boron and ions (Chapter 3).
2. **The specification is a tail.** A clearing that is perfect on average and leaves one grain in 10⁹ fails; one that leaves a hundredth of a monolayer evenly but no grains passes (Chapter 10).
3. **The film is thinner than its metrology.** Most signals that would tell the process where it is are smaller than their own noise at the moment that matters (Chapters 8 and 15).
4. **The film is everywhere.** ALD's virtue is that no surface escapes it; that includes the surfaces nobody patterns (Chapters 7 and 11).
5. **The film that stays is the device.** Edges, grain boundaries, halogens, and charge left in it appear as leakage and retention tails months later (Chapters 11–13).

---

## Summary and Key Takeaways

1. **The dielectric sets C_s and leakage.** ZAZ 5.5 nm with k_eff ≈ 43 gives EOT 0.50 nm and 8.6 fF over 1.24 × 10⁵ nm² per cell; every 0.1 nm is worth 1.8% of capacitance and about 1.5× in leakage.

2. **ALD coats everything.** About 2 m² of dielectric per wafer forms the capacitors; the 318 cm² on the periphery and 46 cm² on the edge must be removed.

3. **A grain stops a contact.** ZrF₄ does not volatilize, so a nanometre of ZrO₂ survives the periphery contact etch. The clearing must be designed against the tail.

4. **The bevel carries zirconium out of the module.** A removal factor of 10⁶ is needed before the first batch furnace, and the bevel stack must not be left to peel.

5. **The trim is the only etch that touches the capacitor itself.** It buys crystallinity and room for the top electrode at the risk of every cell.

6. **Three modules, three tools.** A confined bevel plasma, an ICP with an ALE finish, and a thermal ALE reactor.

---

## Study Questions

1. Compute C_s for the reference cell if the ZAZ is 5.3 nm thick with the same k_eff. Using λ = 0.25 nm, by what factor does the leakage at 1.0 V change?

2. A 1c-class cell has an effective area of 1.05 × 10⁵ nm². What EOT is needed to keep C_s = 8.6 fF? If k_eff rises from 43 to 47 by better crystallization, what physical thickness gives that EOT?

3. Using the areas in Section 1.2.1, compute the mass of ZrO₂ removed per wafer by module 2 (ZrO₂ density 5.9 g/cm³, 5.2 nm of ZrO₂ per wafer area). How many grams of zirconium reach the chamber and exhaust per 10,000 wafers?

4. A bevel etch leaves 0.01% of the original ZAZ on the backside ring. Does the backside meet the Zr specification? What residual fraction is allowed?

5. Explain why the bevel removal must follow the top-electrode TiN and precede the SiGe fill. What would change if the SiGe were deposited in a single-wafer chamber?

6. A contact bottom 40 × 40 nm is a quarter covered by a ZrO₂ grain. Estimate the rise in contact resistance, assuming the resistance is dominated by the interface area. Why is such a contact more dangerous to the product than an open one?

---

**Next Chapter:** [Chapter 2: The Dielectric Stack — Films, Phases, Interfaces & Wrap](./02-dielectric-stack-films.md)

---

**Chapter 1 Development Status:** Complete  
**Version:** 1.0
