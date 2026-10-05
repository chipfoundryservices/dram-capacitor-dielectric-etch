# Preface: Removing the Film That Is the Capacitor

## Why This Book Exists

Books #29 to #32 of this series followed the DRAM capacitor through its hole, its mold, its height, and its electrodes. Each of those books mentions the dielectric, because every one of them has to protect it or prepare for it. None of them is about it. This book is.

The capacitor dielectric is 5.5 nm of zirconium oxide with a few ångströms of aluminium oxide in the middle. It is made by atomic-layer deposition, one self-limiting reaction at a time, so that it has the same thickness at the top of a pillar 1.6 µm tall as at the bottom of a gap 6 nm wide beside it. That conformality is why it works. It is also why it is everywhere: on the periphery, on the scribe lines, on the alignment marks, on the bevel, around the apex, and a few millimetres onto the back of the wafer. The capacitor needs only the part on the pillars.

Every other part must be removed, and removing it is harder than its thickness suggests:

1. **The film was chosen for its stability.** Zr–O bonds are as strong as Si–O bonds. Zirconium fluoride does not volatilize below about 600 °C. The fluorine chemistry that etches every other dielectric in the fab forms a skin on ZrO₂ and stops. Only chlorine works, and only with boron to take the oxygen and ions to take the chloride.

2. **The specification is absence.** A ZrO₂ grain 20 nm across and one nanometre thick, left at the bottom of one of thirty million periphery contacts, stops that contact's fluorocarbon etch. The average residue can be a hundredth of a monolayer and the die can still fail. Clearing is judged by its tail.

3. **The etch makes its own tail.** A continuous ion-assisted etch of a crystalline film removes some grains faster than others. The faster it goes, the wider the spread of what it leaves. The last grain to clear is the one the main step left behind.

4. **The film wraps the wafer edge.** On the bevel and the backside, nothing patterns the dielectric and nothing removes it unless a dedicated etch does. Left there, it contaminates every tool the wafer touches afterwards and anchors a stack of later films that flakes.

5. **The film is the device.** Where the dielectric is removed, an edge of the capacitor dielectric is left exposed: at the plate edge in every die, and at the bevel boundary. Where it is thinned, every capacitor in the array is touched. Halogens, boron, hydrogen, fluorine, ultraviolet light, and charge all reach the film that must hold a femtoampere.

This book treats capacitor dielectric etch as **the removal and thinning of a refractory, granular, conformal film whose remaining part is the capacitor itself**, governed by clearing statistics, edge chemistry, reactant transport, and the electrical tolerance of the cell, and not as the last few seconds of a conductor etch.

---

## Unique Aspects of DRAM Capacitor Dielectric Etch

### 1. Three Etches in Three Places

The bevel removal happens once the top-electrode TiN has capped the dielectric and before the plate fill. The periphery clear is the last step of the plate etch. The in-array trim, where it is used, happens before the top electrode. They use different tools, different chemistries, and different control strategies, and they fail in different ways.

### 2. Thinner Than the Noise

The film is 5.5 nm thick. Its thickness non-uniformity across the wafer is a few tenths of a nanometre. A residue that fails a contact is a fraction of a nanometre thick and covers a fraction of a percent of the area. Endpoint signals, surface analysis, and electrical tests all work at the edge of their sensitivity, and the metrology that matters is often the contact chain on the finished wafer.

### 3. Etching Near the Etch–Deposition Transition

BCl₃ plasmas deposit boron-chlorine films on any surface their ions do not clean fast enough. On ZrO₂ the transition lies near 60 eV. The periphery clear runs well above it; the ALE finish uses it, adsorbing below and removing above; the bevel etch, where the plasma is confined at high pressure, runs barely above it and fails first wherever the edge ion energy sags.

### 4. Cyclic Etches in Production

The ALE finish and the thermal trim are cyclic. Their rates are set by steps that each saturate, not by fluxes, and they are measured in nanometres per cycle, not per minute. Their uniformity is excellent and their throughput is poor. Where they belong in production, and for how many cycles, is an economic question as much as a physical one.

### 5. The Gap as a Reactor

Inside the array, the open channel left between three neighbouring pillars after a thick dielectric is only 7 to 13 nm across and 1.5 µm deep. A thermal etch that must thin the dielectric uniformly from top to bottom of that channel is limited by the molecular flow of HF and DMAC down a passage two hundred times deeper than it is wide. The physics is the same as in the high-aspect-ratio etches of Book #31, with the roles of deposition and etch exchanged.

---

## How to Read This Book

### For Process Engineers
Read Chapters 1–4 for the film and its chemistry, then Chapters 10–12 for clearing, edges, and the trim. Use Appendix D for windows and Appendix G for excursions.

### For Equipment Engineers
Read Chapter 1, then Chapters 5–9 for ICP chambers, chuck uniformity, bevel systems, endpoint, and wall and reactor cleaning. Chapter 15 covers the metrology that judges your tools.

### For Integration Engineers
Read Chapters 1–2, then Chapters 10, 11, 12, 14, and 16. The route comparison in Chapter 10 and the cost model in Chapter 16 are written for you.

### For Device Engineers
Read Chapter 1, Chapter 11 for the dielectric edges, Chapter 12 for what a trim does to grain boundaries, Chapter 13 for damage and reliability, and Chapter 16 for yield signatures.

### For Researchers
Read Chapters 3, 4, 10, 12, and 14. The tail model of Chapter 10, the ALE window of Chapter 4, and the transport model of Chapter 12 are deliberately simple and invite refinement.

---

## A Note on the Reference Process

A single reference process runs through every chapter so that numbers connect. It inherits the array of Books #29–32: a 1b-class 6F² cell on a 45 nm hexagonal storage-node pitch, a 1.60 µm mold, and solid TiN pillars 32/28/24 nm wide, coated with ZAZ (2.6/0.3/2.6 nm, EOT 0.50 nm) and a 5 nm TiN top electrode. In module 1, a confined bevel plasma removes the TiN and the ZAZ from the outer 1.2 mm of the front, the apex, and the backside edge. In module 2, at the end of Book #32's plate etch, a 45 s BCl₃/Cl₂/Ar main step at 150 eV removes 4.4 nm of the exposed ZAZ, and 36 cycles of plasma ALE remove the rest and its tail, landing on the periphery SiN with about 0.4 nm loss. In module 3, a pilot flow for the 1c generation trims 1.0 nm from a 6.5 nm ZAZ inside the array by thermal ALE. All values are illustrative; the arithmetic is shown so that readers can replace them with their own.

---

## Acknowledgments

This book draws on decades of published work on the plasma chemistry of refractory oxides, on high-k gate-dielectric etching, on plasma and thermal atomic-layer etching, on bevel processing and contamination control, and on the reliability of high-k capacitors, and on the shared experience of the engineers who have kept DRAM periphery contacts open and wafer edges clean through every node.

---

**Preface Version:** 1.0  
**Last Updated:** 2026-10-05
