# Preface: Removing the Film That Makes the Capacitor

## Why This Book Exists

Most etches remove material that was put down in order to be patterned. The dielectric etch of a DRAM capacitor removes material that was put down for a different purpose entirely. The high-k film exists to sit between two electrodes, 5.5 nm thick, and hold a field of a million volts per centimetre for ten years with a leakage of one femtoampere per cell. It is deposited by atomic-layer deposition because nothing else can coat seventeen billion pillars 1.4 µm tall with the same thickness top to bottom. And atomic-layer deposition coats everything else too.

The previous book of this series, *DRAM Capacitor Electrode Etch*, treated the removal of that excess dielectric as the last step of the plate etch: after tungsten, silicon-germanium, and titanium nitride, a minute and a half of BCl₃ at 150 eV, under resist, in the same chamber. That works, and much of the industry has done it that way. But the treatment there was written from the conductor's side. The dielectric step was the step that ate the resist budget, notched the top electrode, left veils, ran with a selectivity to nitride below one, and set the tightest residue margin in the module. This book is written from the dielectric's side.

Six facts make the dielectric etch a subject of its own:

1. **The film's bonds are as strong as silicon dioxide's.** Zr–O, Hf–O, and Si–O all lie near 770–800 kJ/mol. Only boron, among the atoms a plasma can supply, binds oxygen more strongly.

2. **Fluorine does not work.** ZrF₄, HfF₄, and AlF₃ are involatile solids. The chemistry that etches every other oxide in the fab forms a skin on these and stops. That is why the periphery contacts stop on residual ZrO₂, and why the film must be gone before they are etched.

3. **Chlorine works only with help.** ZrCl₄ and HfCl₄ need about 190 °C to reach 1 Torr of vapor pressure. At 60 °C, ions must sputter them off; at 250 °C, they leave on their own once formed. Temperature is the strongest knob in the process.

4. **The film is granular.** After crystallization, ZrO₂ is a mosaic of tetragonal and monoclinic grains 15–40 nm across. Grain boundaries clear first; grain centres clear last. The overetch is set by the slowest grain among 10⁸ under the periphery contacts of every die.

5. **Anisotropy and isotropy each fail somewhere.** An ion-driven etch clears flat surfaces and leaves the dielectric on every vertical face of the wafer's topography. A thermal or wet etch clears vertical faces and undercuts the dielectric under the top electrode at the edge of every plate.

6. **The etch runs next to the finished capacitor.** At the plate edge, the cut face of the dielectric sits under a 5 nm TiN top electrode that is exposed to the same chlorine. A micrometre and a half away are the first capacitors of the array.

This book treats capacitor dielectric etch as **the complete removal of a refractory, granular, sub-6-nm film from a large open area, without harming the same film at the edge where it must stay**, and not as the final step of a conductor recipe.

---

## Unique Aspects of DRAM Capacitor Dielectric Etch

### 1. The Specification Is an Absence

The film is 5.5 nm thick, and the target is not a thickness but a probability: fewer than one grain in 10¹⁰ left under a contact. Average surface measurements cannot see that tail. The process is designed against statistics that are confirmed only by contact-chain yield months later.

### 2. The Etch Is Thinner Than Its Own Overetch Budget

The whole film clears in about half a minute. The overetch, the breakthrough, and the time it takes the wafer to reach temperature on the chuck are each comparable to it. Endpoint signals come from a film that is gone before most monitoring systems finish averaging.

### 3. Heat Instead of Energy

In a cold chamber, the energy to remove ZrCl₄ comes from ions at 150 eV, and the nitride beneath etches faster than the zirconia. In a chamber at 250 °C, heat does part of that work, the ion energy can fall to 70 eV, and the selectivity rises to three. The cost is a hard mask instead of resist, and a chuck, walls, and windows that must live at temperature in BCl₃.

### 4. Atomic Layers as a Production Option

The film is thin enough that atomic-layer etching, at 0.1 nm per cycle, clears it in a few minutes. The self-limiting steps remove the ion-energy and loading sensitivities of continuous etching, and leave almost no nitride loss. Whether that is worth five times the chamber time is an economic question this book answers with numbers.

### 5. Zirconium Travels

Zirconium is foreign to the front end of the fab. It deposits on chamber walls, wraps around the wafer bevel during deposition, and rides on backsides into tools shared with other layers. The dielectric etch module owns not only the periphery surface but the zirconium budget of the wafer.

---

## How to Read This Book

### For Process Engineers
Read Chapters 1–4 for the films and chemistry, then Chapters 10–12 for clearing, the plate edge, and selectivity. Use Appendix D for windows and Appendix G for excursions.

### For Equipment Engineers
Read Chapter 1, then Chapters 5–9 for heated chambers, uniformity, ALE and thermal reactors, endpoint, and wall and contamination management. Chapter 15 covers the metrology that judges your tools.

### For Integration Engineers
Read Chapters 1–2, then Chapters 10, 11, 14, and 16. The route comparison and cost model in Chapter 16 are written for you.

### For Device Engineers
Read Chapter 1, Chapter 11 for the plate edge, Chapter 13 for damage to the remaining dielectric, and Chapter 16 for yield signatures.

### For Researchers
Read Chapters 3, 4, 10, and 14. The threshold-temperature model of Chapter 3, the ALE window of Chapter 4, the clearing statistics of Chapter 10, and the dielectric-separation problems of 3D DRAM in Chapter 14 are deliberately simple and invite refinement.

---

## A Note on the Reference Process

A single reference process runs through every chapter so that numbers connect. It inherits the array of Books #29, #30, and #32: a 1b-class 6F² cell on a 45 nm hexagonal storage-node pitch, a 1.60 µm mold, and solid TiN pillars coated with 5.5 nm of ZAZ (EOT 0.50 nm). The plate of Book #32 is etched under a 60 nm oxide cap and stopped on the ZAZ. Two dielectric-clear processes follow. **D1** etches the ZAZ continuously in BCl₃/Cl₂/Ar at 70 eV on a 250 °C chuck, in about a minute. **D2** removes it by plasma ALE at 100 °C, 0.1 nm per cycle, in about six. Thermal ALE, wet finishes, and Book #32's cold in-situ step appear as comparisons. All values are illustrative; the arithmetic is shown so that readers can replace them with their own.

---

## Acknowledgments

This book draws on decades of published work in high-k dielectric deposition and etching, the surface chemistry of boron and chlorine plasmas, atomic-layer etching by plasma and by ligand exchange, and plasma-induced damage, and on the shared experience of the engineers who have kept DRAM periphery contacts open and capacitor plates tight through every node.

---

**Preface Version:** 1.0  
**Last Updated:** 2026-10-05
