# Chapter 1: The Capacitor Dielectric & Why It Is Etched

## Overview

A DRAM storage capacitor is two conductors and an insulator, and the insulator does the work. A 5.5 nm film of zirconia and alumina separates the TiN pillar of each cell from the shared plate, and it must carry a field of about 1 MV/cm for ten years without leaking a charge that the cell cannot spare. The film is grown by atomic-layer deposition, which is conformal by design: it coats every surface the precursor reaches, in the same thickness. The pillars need it. The periphery does not, the scribe lines do not, the bevel does not, and the backside certainly does not. None of those surfaces is protected from the deposition, and every one of them must be cleared.

This chapter explains what the dielectric does in the cell and how much thickness the cell can spare, counts how much film lies where, and lists the reasons it must be removed from each place that is not the array. It then introduces the four dielectric etches of this book, places them in the capacitor module flow beside the electrode etches of Book #32, and gives the specification sheet against which the rest of the book is written.

**Learning Objectives:**
- Compute the cell capacitance from the dielectric geometry and the sensitivity of capacitance and leakage to thickness
- Estimate the headroom in the retention budget that a thinning etch may consume
- Count the film on the array, the periphery, the edge zone, and the backside, and the zirconium atoms to be removed from each
- State the contamination limits that apply at each stage and the number of decades between them
- Name the four dielectric etches and place each in the capacitor module flow
- List the specification of each etch and the failure each line protects against

---

## 1.1 What the Dielectric Does

### 1.1.1 The Capacitance

The storage node is a TiN pillar 28 nm wide on average and exposed over 1410 nm of height. The dielectric wraps its outer surface:

```
Dielectric area per cell:  A = π × 28 nm × 1410 nm = 1.24 × 10⁵ nm² = 1.24 × 10⁻⁹ cm²

C_s = ε₀ · 3.9 · A / EOT
    = 8.854×10⁻¹² F/m × 3.9 × 1.24×10⁻¹³ m² / 0.50×10⁻⁹ m
    = 8.57 fF                                     (reference: 8.6 fF)

Stack:  ZrO₂ 2.6 nm / Al₂O₃ 0.3 nm / ZrO₂ 2.6 nm = 5.5 nm physical
        EOT = 0.50 nm → k_eff = 5.5 × 3.9 / 0.50 = 43
```

When the word line opens, the stored charge is shared with the bit line (Book #32, Chapter 1):

```
ΔV_BL = (V_core/2) · C_s / (C_s + C_BL) = 0.55 × 8.6 / (8.6 + 40) = 97 mV
```

### 1.1.2 Thickness Sensitivity

To first order, capacitance varies as the inverse of EOT, and EOT varies in proportion to physical thickness:

```
EOT = 3.9 t / k_eff         dEOT/dt = 3.9 / 43 = 0.0907 nm per nm of physical film
dC/C = −dEOT/EOT

Thin the ZAZ by       EOT (nm)    C_s (fF)    ΔC       Leakage (× median)*
─────────────────────────────────────────────────────────────────────────
0.0 nm (reference)    0.4988      8.60        —        1.0
0.1 nm                0.4898      8.76       +1.9%     1.7
0.2 nm                0.4807      8.92       +3.8%     2.8
0.3 nm                0.4716      9.10       +5.8%     4.6
0.5 nm                0.4535      9.46      +10.0%    12.9

* assuming one decade of leakage per 0.45 nm of physical thickness (illustrative);
  C_s scaled to the reference 8.6 fF
```

A 0.2 nm thinner film would add 3.8% to C_s and raise the sense signal from 97.3 mV to 100.3 mV. It would also nearly triple the leakage. Section 1.1.3 shows how much leakage the cell can afford.

The same arithmetic runs the other way. A dielectric etch that removes 0.3 nm of film by accident, in the conductor-etch overetch or in a damaged edge, changes the capacitance by 6% and the leakage by a factor of 4.6. A cell cannot be repaired by a second ALD pass, because the TiN beneath is already covered by the top electrode.

### 1.1.3 Leakage and the Retention Budget

The leakage of the reference dielectric follows (Book #32, Chapter 13):

```
J(V) = J₁ exp[(V − 1.0 V)/0.12 V],  J₁ = 8 × 10⁻⁷ A/cm² → 1 fA per cell at 1.0 V
(one decade per 0.28 V)

V (volts)    J (A/cm²)        Per cell (fA)
────────────────────────────────────────────
0.55         1.9 × 10⁻⁸          0.023       ← operating bias
0.80         1.5 × 10⁻⁷          0.19
1.00         8.0 × 10⁻⁷          0.99        ← screening bias
1.30         9.7 × 10⁻⁶         12.1
```

The specification of "1 fA at 1.0 V" is a screening condition. At the operating bias of 0.55 V the median cell leaks 0.023 fA. The retention budget (Book #32, Chapter 1) allows about 30 fA in the weakest cell from all paths, of which a third, 10 fA, may be dielectric leakage. The tail of a real population lies above its median; if the weakest cell of a die leaks 100 times the median:

```
Weakest-cell dielectric leakage at 0.55 V:   0.023 fA × 100 = 2.3 fA
Budget:                                      10 fA
Headroom:                                    10 / 2.3 = 4.3×

Thickness that consumes the headroom:        0.45 nm × log₁₀(4.3) = 0.28 nm
```

The dielectric can lose about 0.28 nm before the weakest cells of a die cross the retention budget, if nothing else in the cell degrades. That is the most that a dielectric etch may remove from the array, and it is the budget against which every trim, every accidental loss, and every edge effect in this book is measured. It is generous in thickness (5% of the film) and tight in practice, because the other contributors to leakage also draw on the same 10 fA.

---

## 1.2 Why It Must Go From Everywhere Else

### 1.2.1 The Inventory

The film that the wafer carries is large in the array and small elsewhere:

```
Per 300 mm wafer (860 dies, 1.72 × 10¹⁰ cells each):
  Dielectric on pillars (the product)     14.8 × 10¹² cells × 1.24×10⁻⁹ cm² = 1.83 × 10⁴ cm²
  Flat wafer area                         707 cm²           (film area is 26× larger)

Film to be removed (flat, top side):
  Periphery, scribe, and edge ring        45% of 707 cm²  = 318 cm²
    of which the top edge ring (r > 147 mm)                    28 cm²
Film to be removed (outside the plate's reach):
  Bevel (0.6 mm arc × 942 mm)                                 5.7 cm²
  Backside, outer 3.5 mm                                      32.6 cm²

Zirconium per cm² in 5.2 nm of ZrO₂:
  n(ZrO₂) = 5.68 g/cm³ / 123.2 g/mol × 6.022×10²³ = 2.78 × 10²² cm⁻³
  × 5.2×10⁻⁷ cm = 1.44 × 10¹⁶ Zr cm⁻²

Atoms to remove per wafer:
  Periphery and scribe (318 cm²)          4.6 × 10¹⁸
  Edge zone (28 + 5.7 + 32.6 = 66 cm²)    9.6 × 10¹⁷
```

The array holds 98% of the film on the wafer by area. The other 2% is the subject of this book, and it has to be removed completely, because zirconium at the surface is judged by limits that are thousands of times smaller than the film.

### 1.2.2 The Contamination Zones

```
Limit                                   Zr (cm⁻²)     Fraction of     Decades below
                                                       as-deposited    as-deposited
────────────────────────────────────────────────────────────────────────────────────
As deposited (5.2 nm ZrO₂)              1.4 × 10¹⁶     1                0
Periphery specification (contacts)      1 × 10¹³       6.9 × 10⁻⁴       3.2
Etch-chamber monitor limit (Book #32)   1 × 10¹¹       6.9 × 10⁻⁶       5.2
Furnace-entry / chuck-contact limit     1 × 10¹⁰       6.9 × 10⁻⁷       6.2
```

The periphery limit protects contacts. It is judged on the front side, on average, by TXRF, and in the tail by contact chains (Book #32, Chapter 15). The two lower limits protect equipment. A wafer that enters a SiGe LPCVD furnace at 425 °C with zirconium on its backside deposits that zirconium on the quartz, from which it can reach every wafer that follows. The same wafer on an etch-chamber chuck leaves zirconium on the chuck, and the chuck hands it to the next wafer's backside (Book #32, Chapter 9). Because the transfer is from the backside, the edge and the backside are held to the lowest limit, and they are the surfaces on which the wafer's own plate etch cannot act.

### 1.2.3 Periphery Contacts

The periphery contacts of a later module are etched through about 1.8–2.0 µm of oxide and nitride with a fluorocarbon plasma. Zirconium fluoride does not volatilize below about 900 °C, so a ZrO₂ island under a contact is an open (Book #32, Chapter 1). With 3 × 10⁷ contacts per die and about four grains under each, the probability that a grain survives the plate etch must be below 8 × 10⁻¹¹. That requirement, from Book #32's grain-tail model, is the reason the periphery clear is the hardest clearing problem in the capacitor module, and it is the reason this book treats it in detail (Chapters 4, 7, and 10).

### 1.2.4 Flakes, Bevel, and Scribe

Two lesser reasons also apply. At the bevel, the plate stack of W, SiGe, TiN, and ZAZ is deposited over a surface with poor adhesion and subsequently experiences thermal cycling. Material at the bevel that comes loose lands on a die as a particle containing tungsten and zirconium. And in the scribe, a ZAZ film of k = 43 over an alignment mark or a test structure changes its optical signal, which shows up as an overlay shift or a monitor offset in the next critical layer (Book #32, Chapter 12).

---

## 1.3 The Four Dielectric Etches

```
Module                      Where                     Film state     Mask        Ions?      Removes
─────────────────────────────────────────────────────────────────────────────────────────────────────
E  Edge etch                after ZAZ ALD, before     amorphous      none        yes        ZAZ on top edge
                            top-electrode TiN                        (edge       (edge      ring, bevel, and
                                                                      plasma)     plasma)    backside edge
P  Periphery clear          after plate deposition    tetragonal     plate       yes        ZAZ on periphery
                            (replaces Book #32's                     itself      (hot ICP)  and scribe
                            high-k step)
T  Trim and rework          after ZAZ ALD, before     amorphous      none        no         0–0.3 nm over the
                            top-electrode TiN                                    (thermal    whole wafer, or
                                                                                 ALE)        all of it (rework)
C  ALD-chamber clean        in the ALD tool, every    as-grown on    none        no         ZrO₂ on walls and
                            few hundred wafers        tool surfaces              (thermal)  showerhead
```

The modules differ in every column. The edge etch works on a film that has not yet crystallized and can use a resistless plasma confined to a ring. The periphery clear works on crystallized film under the plate, and must stop a conductor etch on the way. The trim works without ions and acts on the dielectric in the array, where no plasma could go. The clean acts on no wafer at all.

---

## 1.4 Where the Dielectric Etches Sit

### 1.4.1 The Capacitor Module

```
Capacitor module flow (reference; steps 1–8 as in Book #32):
   1–8. Mold, holes, TiN fill, storage-node separation, support open, dip-out   (Books #29–#32)
   9. ZAZ ALD, 5.5 nm, amorphous                              [Module C acts on this tool]
  ─────────────────────── this book, modules E and T ─────────────────────────
   9a. Edge etch: amorphous ZAZ off the top edge ring, bevel, backside edge
   9b. Trim or rework (optional): thermal ALE, 0–0.3 nm, or full strip and re-ALD
  ───────────────────────────────────────────────────────────────────────────
  10. Top electrode TiN ALD, 5 nm (400 °C; ZAZ partly crystallizes)
  11. Plate fill: B-doped SiGe, 150 nm (425 °C; ZAZ fully tetragonal)
  12. Plate strap: W, 40 nm
  13. Plate mask: BARC + KrF resist
  ─────────────────────── this book, module P (replaces Book #32 step 14) ─────
  14a. P1: conductor etch: BARC, W, SiGe main, SiGe over-etch   (as Book #32)
  14b. P2: TiN breakthrough and stop, landing on the ZAZ
  14c. P3: resist strip (downstream O₂/N₂, 250 °C)
  14d. P4: ZAZ clear with the plate as its own mask (hot BCl₃/Cl₂/Ar)
  ───────────────────────────────────────────────────────────────────────────
  15. Post-etch treatment and clean
  16. Inter-layer dielectric; periphery contacts; plate contact
```

### 1.4.2 Why Edge and Trim Come Before the Top Electrode

The ZAZ is amorphous from its deposition until the top electrode is deposited at 400 °C. In that state it etches 1.5× faster than after crystallization (9 against 6 nm/min), and it has no grain boundaries, so no grain tail. It is also exposed: nothing covers it, so a resistless edge plasma or a plasma-free vapor can reach it. After step 10 it is buried under TiN, SiGe, and W, and the only way to reach it is through the conductor etch of module P. Every dielectric etch that can be done at step 9 is cheaper and cleaner than the same etch at step 14.

The order of 9a and 9b is also deliberate. The edge etch comes first so that the backside, which would otherwise rest on the thermal reactor's pedestal, no longer carries zirconium into the trim tool. The cost is a queue: the exposed ZAZ surface must reach the top-electrode deposition within a limit set by carbon and hydroxyl uptake (4 h in the reference, illustrative), and both steps spend part of it. Chapter 16 compares a vacuum-integrated cluster with a stand-alone sequence.

### 1.4.3 What Module P Changes in Book #32's Flow

Book #32 clears the ZAZ in a single BCl₃/Cl₂ step at 60 °C and 150 eV, under the plate resist, as the last of five steps. This book splits that step. The conductor etch stops on the ZAZ (P2), the resist is removed (P3), and the ZAZ is cleared (P4) with the plate itself as the mask. The reasons, and the costs, occupy Chapters 4, 7, 10, and 16.

---

## 1.5 The Specification Sheet

```
Module E — edge etch (reference, illustrative):
  Zr on backside and bevel after etch and clean     ≤ 1 × 10¹⁰ cm⁻² (VPD-ICPMS)
  Top-edge exclusion boundary                       r = 147.0 ± 0.3 mm
  ZAZ loss inside r < 146 mm                        ≤ 0.1 nm
  Si loss on the backside                           ≤ 10 nm
  Particles added (> 30 nm)                         ≤ 10 per wafer
  Queue, ZAZ to top-electrode TiN (incl. E and T)   ≤ 4 h

Module P — periphery clear:
  ZAZ loss in the conductor stop (P2)               ≤ 0.3 nm
  Zr residue on periphery pads                      ≤ 1 × 10¹³ cm⁻² (TXRF)
  Periphery contacts opened by residue              ≤ 0.01 per die (contact chains)
  W loss from strip and clear                       ≤ 2.7 nm (plate R_s ≤ 4.0 Ω/□)
  TiN notch at the plate edge                       ≤ 15 nm lateral
  SiN loss in the periphery                         ≤ 15 nm
  Charging voltage across the dielectric            ≤ 1.5 V (antenna structures)
  Cell leakage after module P                       ≤ 10% above unetched reference at 1.0 V

Module T — trim and rework:
  Removal per wafer                                 0–0.28 nm, ± 0.03 nm (3σ)
  Non-uniformity along the pillar                   ≤ 10% of the removal
  Median leakage after trim                         within the headroom of Section 1.1.3
  Rework: electrode loss                            ≤ 0.2 nm per side; ≤ 1 rework per wafer

Module C — ALD-chamber clean:
  Zr flakes / particles added to the next wafers    ≤ 10 per wafer (> 30 nm)
  Fluorine used on a zirconia-coated wall           none

Electrical (end of capacitor module):
  C_s                                               ≥ 8.3 fF (mean 8.6 fF)
  Plate-to-node leakage at 1.0 V                    ≤ 1 fA per cell (median)
  Periphery contact opens from high-k               0 per die
```

Three of the lines are absolute: zirconium at the edge, high-k residue under contacts, and fluorine on zirconia. The first two are judged by the absence of a film; the third is a rule whose violation shows up weeks later as a flake. The remaining lines are budgets, spent on one side by etch and on the other by retention.

---

## 1.6 What Makes Dielectric Etch Different

1. **It removes the product's own film.** The same 5.5 nm ZAZ is the active insulator in 1.5 × 10¹³ cells per wafer and a contaminant on the backside. The etch must tell them apart by position and by sequence, not by chemistry.

2. **It is judged in decades.** The film is 10¹⁶ cm⁻², the limits are 10¹³, 10¹¹, and 10¹⁰, and each limit has a metrology and a failure of its own (Section 1.2.2).

3. **The film changes between etches.** Amorphous at step 9, partly crystalline at step 10, tetragonal at step 14. Rates, selectivities, and the clearing tail all depend on when the etch occurs (Chapters 2 and 4).

4. **Chlorine, boron, and heat; never fluorine.** ZrCl₄ sublimes at 331 °C and ZrF₄ at 906 °C. Fluorine is allowed only as the first half-cycle of a ligand-exchange etch, where the second half follows (Chapter 3).

5. **The finished capacitor is in the circuit.** Module P exposes the plate to a plasma while the dielectric is connected to it; modules E and T act before the capacitor is complete but on the same dielectric that will carry it (Chapters 7 and 12).

---

## Summary and Key Takeaways

1. **The dielectric sets the cell.** C_s = 8.57 fF at EOT 0.50 nm; each 0.1 nm of thickness is 1.9% of capacitance and a factor 1.7 in leakage.

2. **The retention budget lets the film lose about 0.28 nm.** That is the most any dielectric etch may remove from the array.

3. **The array holds 98% of the film.** 1.8 × 10⁴ cm² on pillars against 318 cm² of periphery and 66 cm² of edge zone, but the 2% must be cleared to six decades below its as-deposited zirconium content.

4. **Four removals, four places in the flow.** Edge (E) and trim (T) before the top electrode on amorphous film; periphery clear (P) after the plate on tetragonal film; chamber clean (C) in the deposition tool.

5. **Do what can be done early.** Amorphous ZAZ etches 1.5× faster with no grain tail; after step 10 it is buried.

6. **The specification has absolutes and budgets.** Zr at the edge, residue under contacts, and fluorine on zirconia are absolute; trim, loss, and notch are spent against retention and yield.

---

## Study Questions

1. Compute the cell capacitance and the sense signal ΔV_BL for a ZAZ thinned by 0.15 nm, with k_eff = 43 unchanged. By what factor does the leakage rise if it falls by one decade per 0.45 nm?

2. At what voltage does the median cell leak 0.1 fA, using the model of Section 1.1.3? If the weakest cell of a die leaks 300 times the median at 0.55 V and the dielectric budget is 10 fA, how much thickness can be removed?

3. Recompute the edge-zone inventory (area and Zr atoms) if the backside zone is 2.0 mm instead of 3.5 mm. How many decades of removal does each zone need to reach the furnace-entry limit of 10¹⁰ cm⁻²?

4. A 1d-class product has 26 nm average pillars 1.9 µm tall. Compute the dielectric area per cell and the ratio of film area to flat wafer area for 860 dies of 1.72 × 10¹⁰ cells.

5. Explain why the edge etch is placed before the trim in Section 1.4.2, and what would happen to a thermal reactor that trimmed wafers with untreated backsides.

6. A periphery contact chain shows opens at the wafer edge but TXRF on periphery pads reads 3 × 10¹² Zr cm⁻². Which of the limits in Section 1.2.2 does the TXRF result satisfy, and why does it not rule out a residue problem?

---

**Next Chapter:** [Chapter 2: The ZAZ Film as the Etch Sees It — Growth, Crystallization, Wrap-Around & Stress](./02-zaz-film-as-etch-sees-it.md)

---

**Chapter 1 Development Status:** Complete  
**Version:** 1.0
