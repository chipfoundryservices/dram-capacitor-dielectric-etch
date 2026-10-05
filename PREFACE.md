# Preface: Eighteen Thousand Square Centimetres of Dielectric on a 707 cm² Wafer

## Why This Book Exists

The DRAM capacitor dielectric is usually described by what it gives: a dielectric constant near 43, an equivalent oxide thickness of half a nanometre, a leakage of one femtoampere per cell. Book #32 of this series followed it only as far as the plate etch, where it is the last film to be cleared from the periphery. But a film that is deposited on every surface of the wafer, in the same thickness, and is needed on only one of them, is an etch problem in several places, and each place has its own physics.

The numbers explain why. A 300 mm wafer has 707 cm² of flat area. The dielectric on the pillars of its 860 dies covers 1.8 × 10⁴ cm², twenty-six times more. That film is the product. The film on the flat wafer, on the periphery, the scribe lines, the bevel, and the backside edge, is a waste product, and it has to go without touching the film that matters:

1. **The dielectric is everywhere, and its worst places are the ones nobody looks at.** ALD does not stop at the wafer edge. It wraps into the gap under the wafer and coats the backside out to 2 mm and beyond. The wafer then goes onto chucks, into furnaces, and into other tools, carrying 1.4 × 10¹⁶ zirconium atoms per cm² on its underside.

2. **Away from the array, the dielectric is a contaminant before it is a film.** The periphery specification is 10¹³ Zr cm⁻², the etch-chamber limit 10¹¹, the furnace-entry limit 10¹⁰. The last is six decades below the as-deposited film.

3. **Under the conductor etch, the dielectric is the stop layer.** The plate etch must clear 5 nm of TiN and stop on 5.5 nm of ZAZ, with a loss under 0.3 nm. The required selectivity is 33. Fluorine from the tungsten step can turn the stop layer into a non-volatile ZrF₄ skin that the next step cannot remove.

4. **The dielectric changes with time.** As grown it is amorphous and etches at 9 nm/min with no grain boundaries. After the top electrode and the plate fill it is crystalline and etches at 6 nm/min with a grain tail that sets the yield. Every etch that can happen early is cheaper than the same etch later.

5. **The cut edge of the dielectric is the boundary of an electrical region.** What the etch leaves at that edge, vacancies, chlorine, boron, and a few nanometres of undercut, sits 1.5 µm from the last active cell. The distance is generous. A product that wants to shrink it needs the numbers of Chapter 11.

6. **Etching the dielectric on purpose costs retention.** Thinning the film by 0.2 nm raises the cell capacitance by 3.8% and the leakage by 2.8 times. The trade is not obviously worth making, and Chapter 13 shows when it is.

This book treats dielectric etch as **a set of removals that differ in what they must leave, when in the flow they happen, and what they may touch**, governed by volatility, crystallinity, and the electrical tolerances of the cell, and not as a single high-k clearing step at the end of a plate recipe.

---

## Unique Aspects of DRAM Capacitor Dielectric Etch

### 1. One Film, Four Removals

The edge etch happens before the top electrode, on amorphous film, with no mask. The periphery clear happens after the plate is cut, on crystalline film, with the plate as its mask. The trim happens before the top electrode, in a plasma-free reactor. The chamber clean happens in the deposition tool, on film that was never on a wafer. The film is the same in all four; the chemistry, the temperature, the mask, and the failure modes are not.

### 2. Judged in Decades

A residue specification of 10¹³ Zr cm⁻² means removing 99.93% of the film. A furnace-entry specification of 10¹⁰ means removing all but seven parts in ten million. Metrology changes at each decade: ellipsometry sees the film, XRF sees monolayers, TXRF sees 10¹⁰ on a spot, and VPD-ICPMS sees 10⁸ on the whole surface. The etch is designed to the decade the next tool demands.

### 3. Sharp Boundaries Because Radicals Do Not Etch

Chlorine atoms alone do not etch zirconia: the reaction is endothermic by 120 kJ/mol. The film is removed only where ions arrive. That makes the boundary of an edge etch as sharp as the boundary of the plasma sheath, and it is why a bevel etch can clear the outer 3 mm of a wafer without touching the die 4 mm inside it.

### 4. Plasma-Free Removal That Reaches Into the Forest

Thermal atomic-layer etching, HF followed by a ligand exchange, needs no ions, no mask, and no line of sight. It reaches the dielectric on the pillars inside a 13 nm channel 1.4 µm deep: a dose of under a second saturates the bottom. That makes it possible to thin or strip the film where no plasma could go. It also makes it isotropic, so it undercuts every edge by as much as it etches down.

### 5. Learning the Stop

The least visible etch in this book is the one that removes almost nothing. The conductor overetch lands on the dielectric and must take away less than 0.3 nm of it, in a chamber whose walls remember fluorine from the first step. Whether the stop works decides whether the clear that follows can work.

---

## How to Read This Book

### For Process Engineers
Read Chapters 1–4 for the film, the chemistry, and the selectivity matrix, then Chapters 10–13 for stopping, edge, damage, and trim. Use Appendix D for windows and Appendix G for excursions.

### For Equipment Engineers
Read Chapter 1, then Chapters 5–9 for edge chambers, thermal reactors, clear chambers, monitoring, and contamination control. Chapter 15 covers the metrology that judges your tools.

### For Integration Engineers
Read Chapters 1–2, then Chapters 4, 7, 11, 13, and 16. The route comparison and the cost model in Chapter 16 are written for you.

### For Device Engineers
Read Chapter 1, Chapter 11 for the dielectric edge, Chapter 12 for damage and TDDB, Chapter 13 for the capacitance–leakage trade, and Chapter 16 for yield signatures.

### For Researchers
Read Chapters 3, 6, 12, 13, and 14. The channel-dosing model of Chapter 6, the defect model of Chapter 12, and the volatility map of Chapter 14 are deliberately simple and invite refinement.

---

## A Note on the Reference Process

A single reference process runs through every chapter so that numbers connect. It inherits the array and plate of Books #29, #30, and #32: a 1b-class 6F² cell on a 45 nm hexagonal storage-node pitch, a 1.60 µm mold, solid TiN pillars 32/28/24 nm wide, and a ZAZ dielectric of 5.5 nm (EOT 0.50 nm) under a 5 nm TiN, 150 nm SiGe, and 40 nm W plate. The edge etch removes amorphous ZAZ from the outer 3.0 mm of the top, the bevel, and the outer 3.5 mm of the backside in a BCl₃/Cl₂/Ar edge plasma. The periphery clear strips the resist and clears the ZAZ with the plate as its own mask at 250 °C. The trim thins amorphous ZAZ with HF/DMAC thermal ALE at 280 °C. All values are illustrative; the arithmetic is shown so that readers can replace them with their own.

---

## Acknowledgments

This book draws on decades of published work in high-k deposition and etching, the thermochemistry of metal halides, atomic-layer etching, plasma-induced damage, and contamination control, and on the shared experience of the engineers who have kept zirconium out of the furnaces and the dielectric intact under every plate.

---

**Preface Version:** 1.0  
**Last Updated:** 2026-10-05
