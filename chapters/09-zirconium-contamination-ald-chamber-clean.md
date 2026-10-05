# Chapter 9: Zirconium Contamination, Chamber Walls & the ALD-Chamber Clean

## Overview

Zirconium is not a poison in a transistor in the way that iron or copper is. It diffuses slowly, forms stable oxides, and has been part of gate stacks for two decades. It is a contaminant for another reason: it is hard to get rid of. Zirconia is stable in every chamber clean that fabs use, and the fluoride that a fluorine clean makes of it does not leave. A tool that has been contaminated with zirconium stays contaminated, hands its zirconium to every wafer it touches, and hands it onward from the backside to the next chuck and the next furnace. The controls are therefore drawn up in terms of zones, in which the tools that carry zirconium are separated from those that must not, and cleaning rules, in which no step may convert a removable deposit into a permanent one.

This chapter sets out the zones and the transfer arithmetic that justify the edge etch, walks through the wall chemistry of each chamber of this book (including a benefit of the strip-then-clear route that Book #32's integrated chamber cannot have), and treats the one dielectric etch that no wafer ever sees: the clean of the ALD chamber itself, whose walls collect 5.5 nm of zirconia and alumina for every wafer processed.

**Learning Objectives:**
- Assign each tool of the capacitor module to a zirconium zone and state the cleaning rule of each
- Estimate how many wafers one wafer with an unetched backside contaminates
- Explain why the conductor chambers of the strip-then-clear route stay zirconium-free
- Compute the wall deposit per wafer and the clean time and throughput cost of an ALD clean
- Compare fluorine, thermal chlorine/boron, remote-plasma, and wet routes for cleaning zirconia
- Specify monitors and the recovery for a zirconium excursion

---

## 9.1 Zones

### 9.1.1 The Rule

```
High-k zone ("Zr zone"):  tools whose walls, chucks, or exhaust carry zirconium
Clean zone:               tools that must not: furnaces, backend deposition, most etch
Rule: a wafer may move from the high-k zone to the clean zone only if its backside,
      bevel, and edge are at ≤ 1 × 10¹⁰ Zr cm⁻²; a wafer may never move the other way
      carrying a tool's wall deposits.
```

### 9.1.2 The Tools

```
Tool or chamber                         Carries Zr?                       Zone        Cleaning rule
──────────────────────────────────────────────────────────────────────────────────────────────────────────────
ZAZ ALD chamber (Module C)               heavy: 5.5 nm per wafer on walls  high-k      Cl-only (BCl₃/Cl₂); never F
Edge etch (Module E)                     yes: sputtered ZrClₓ              high-k      Cl first; no F
Thermal ALE reactor (Module T)           yes: Zr complexes; F-bearing      high-k      Cl clean; HF-resistant parts
Top-electrode TiN ALD                    front only (ZAZ buried); no       clean*      backside ≤ 10¹⁰ on entry
                                         emission
SiGe LPCVD furnace; W PVD                none                              clean       backside ≤ 10¹⁰ on entry
P1/P2 conductor chambers (R1)            no (ZAZ not sputtered, § 9.3.1)    clean       F cleans allowed
P3 downstream strip                      no                                clean       standard
P4 hot clear chamber                     heavy: ZrClₓ, AlClₓ, BₓClᵧ         high-k      Cl only; hot liner
P5 post-etch treatment, rinse            low: Zr flakes in rinse           high-k      dedicated rinse module
ILD deposition, contact etch             none (ZrO₂ is the contact stop)   clean       backside ≤ 10¹⁰ on entry
```

\* The top-electrode TiN tool sees wafers whose front carries the ZAZ, but the ZAZ is a solid film that sheds nothing in that tool; only the backside touches the pedestal. If the backside has been cleared by the edge etch, the tool stays clean.

The Book #32 integrated plate chamber carries zirconium (it etches ZAZ in its HK step) and is therefore a high-k zone tool that also runs W, SiGe, and TiN steps. The strip-then-clear route separates them, and that separation is the practical benefit of Section 9.3.1.

---

## 9.2 Transfer: What One Dirty Wafer Does

### 9.2.1 A Simple Model

A wafer with an unetched backside ring carries 1.44 × 10¹⁶ Zr cm⁻² in the outer 3.5 mm. Put it on a clean chuck whose contact ring covers the same region, and let a fraction f of the surface zirconium transfer on each contact (illustrative f = 10⁻³ in each direction):

```
Chuck after one dirty wafer:     C_chuck = f × 1.44×10¹⁶ = 1.4 × 10¹³ cm⁻²
Each following clean wafer picks up:    C_w(n) = f × C_chuck × (1 − f)ⁿ
   wafer 1:   1.4 × 10¹⁰ cm⁻²

Wafers above the furnace limit of 10¹⁰:   n = ln(1.44×10¹⁰ / 10¹⁰) / f ≈ 370
Wafers above 10⁹:                          n = ln(14) / f ≈ 2,700
```

One wafer that skips the edge etch contaminates the next 370 wafers on that chuck above the furnace limit, and 2,700 above the VPD-ICPMS floor. Each of those wafers may carry the zirconium onward to a furnace that then holds it for a long time.

After the edge etch the backside is at 10¹⁰ cm⁻². The chuck takes f × 10¹⁰ = 10⁷ cm⁻² and the following wafers pick up 10⁴ cm⁻²: six orders below the limit. The edge etch converts a chain that spreads contamination through the fab into one that does not.

### 9.2.2 Partial Failure

A zone that is only partly cleared is as bad as a missing one for the part of the chuck that meets the uncleared part. If an off-centre wafer leaves 10% of the backside ring uncleared (3.3 cm² at full film), the chuck's contact ring is contaminated at 1.4 × 10¹³ cm⁻² over that 10% of its area, an average of 1.4 × 10¹² cm⁻² over the ring and 10⁵ times the 10⁷ cm⁻² of a chuck that has met only properly etched wafers. The next wafers pick up 1.4 × 10¹⁰ cm⁻² on the same sector, so the failure is local and shows only in a sector reading. The monitor of Chapter 15 reads the backside in azimuthal sectors for this reason.

---

## 9.3 Etch-Chamber Walls

### 9.3.1 The Conductor Chambers Stay Zirconium-Free

In Book #32's integrated route, the plate chamber carries W, SiGe, TiN, and Zr deposits on a single wall. Its waferless clean must go through a four-step sequence in a fixed order (BCl₃/Cl₂ first for the zirconium, NF₃/O₂ after), because fluorine on an unremoved zirconium deposit forms a ZrF₄ skin that is not removed. Every wall memory in that chamber crosses every step (F from the W step into the SiGe step; B and Zr from the HK step into the next wafer's W step).

In the strip-then-clear route the conductor chambers (P1, P2) never sputter zirconium. In P2 the ZAZ is exposed to a Cl₂/Ar plasma at 40 eV, below the 45 and 60 eV thresholds; no Zr leaves it. The chambers therefore need no chlorine-first rule and no BCl₃/Cl₂ zirconium step. They can be cleaned with fluorine as any conductor chamber is, and the memory of the HK step's B and Zr leaves with the HK step into the P4 chamber, where it belongs.

```
Conductor chambers P1/P2 (R1), WAC after every wafer:
  NF₃/O₂ 15 s     removes Si, W, B, C (fluorine is safe: no Zr on the wall)
  Cl₂ 5 s         resets the wall to a chlorinated state for the TiN stop
Compare Book #32 integrated chamber:
  BCl₃/Cl₂ 20 s → O₂ 10 s → NF₃/O₂ 15 s → Cl₂ 5 s    (four steps; order critical)
```

The saving is not only 30 s per wafer. It removes the failure mode in which an operator or a recipe edit reorders the steps and converts a zirconium deposit into ZrF₄, which Book #32 treats as a permanent loss of the chamber.

### 9.3.2 The Hot Clear and Edge Chambers

```
P4 hot clear chamber (BCl₃/Cl₂, 250 °C chuck, 150–180 °C liner):
  Deposits    ZrClₓOᵧ, AlClₓ, a little WOₓClᵧ; BₓClᵧ only on cold parts (< 80 °C)
  WAC         BCl₃/Cl₂ 20–30 s, hot, no bias (removes Zr and Al as chlorides)
              Cl₂ 5 s (resets wall)
  Never       F (NF₃, SF₆, CF₄) in this chamber at any step
  Wet clean   boron and chloride deposits form boric acid and HCl in air: purge cycles,
              ventilated enclosure (Book #32, Chapter 7)

Edge chamber (BCl₃/Cl₂/Ar, wall 100 °C):
  Same rule; the boron film deposits where the wall is below 80 °C, so the wall is held
  at 100 °C and the plate and ring faces are cleaned by an O₂/H₂O step followed by a
  BCl₃/Cl₂ step
```

The reason a fluorine-free WAC is possible in P4 is that the liner is hot. BₓClᵧ deposits only on surfaces below about 80 °C. At 150–180 °C there is little boron to remove, and the one thing that would need fluorine to remove it, boron oxide, does not form in quantity. The cold spots (the gas plate, the pump port) are handled at wet clean.

### 9.3.3 Thermal ALE Reactor Walls

The thermal reactor does not sputter and carries only what the HF/DMAC chemistry volatilizes: Zr complexes that condense on any wall colder than the products' sublimation point, and fluoride films on the aluminium and nickel surfaces. The walls are held at 150–200 °C (Chapter 6), and the foreline is heated. When zirconium-bearing flakes form, they form from the reactor's own deposit on the cold parts; they are removed by a chlorine clean at high temperature or at wet clean.

---

## 9.4 The ALD-Chamber Clean (Module C)

### 9.4.1 What Accumulates

ALD deposits on everything it reaches, and the chamber's walls, showerhead, and pedestal see the same dose per cycle as the wafer. To a good first approximation each wafer adds 5.5 nm to every exposed surface:

```
Wall deposit per wafer:                    5.5 nm
Wafers per micrometre of deposit:          1 µm / 5.5 nm = 182
Typical clean trigger (flake onset):       0.5–1 µm → 91–182 wafers
ALD time per wafer:                        107 cycles × 8 s = 856 s = 14.3 min
```

The pedestal's deposit has a second effect: it raises the surface under the wafer and reduces the gap g of the wrap-around model (Chapter 2). A film of 1 µm reduces g from 12 µm to 11 µm and the backside wrap by 8%, a slow drift of the edge zone's design margin.

### 9.4.2 Why Fluorine Cannot Clean Zirconia

Most deposition chambers are cleaned with NF₃ or ClF₃ remote plasma: fluorine converts silicon and tungsten deposits to volatile fluorides. On a zirconia wall it converts the deposit to ZrF₄, which does not sublime below about 906 °C:

```
ZrO₂ + 4 F → ZrF₄ + O₂         (strongly exothermic; −201 kJ/mol per ZrO₂ for the HF route, Chapter 3)
ZrF₄ remains on the wall at any temperature the chamber can reach.
Volume change on conversion:   ZrF₄ (4.43 g/cm³, 167 g/mol) vs ZrO₂ (5.7 g/cm³, 123 g/mol)
                               (167/4.43) / (123/5.7) = 1.75× in volume
```

The ZrF₄ skin is 75% larger than the film it replaced, brittle, and it does not come off. It flakes. This is the same trap that Book #32 warns of for the conductor chamber, here in a tool that cannot recover from it without a wet clean.

### 9.4.3 Routes Compared

```
Route                                  Rate on ZrO₂ wall   1 µm takes     Overhead per wafer   Notes
─────────────────────────────────────────────────────────────────────────────────────────────────────────────
NF₃/ClF₃ remote plasma                 —                   (never clears)  —                    converts to ZrF₄
Thermal BCl₃/Cl₂ at 280 °C             14.6 nm/min         68 min          23 s (2.6% of ALD)   no thermal cycle;
                                                                                                 slow
Remote-plasma BCl₃/Cl₂ at 350 °C       60 nm/min           17 min          19 s (2.2% of ALD)   + 40 min ramp up and
(including 40 min thermal cycling)                         (+40)                                 down
Wet clean (parts out, 8 h)             —                   480 min         158 s (18.5%) per µm;  parts swap; flake
                                                                           32 s if every 5 µm    risk when reopening
```

(The thermal rate at 280 °C is that at 350 °C scaled by exp(−E_a/kT) with E_a = 0.6 eV: 60 × 0.243 = 14.6 nm/min.) The ZrO₂ + 4/3 BCl₃ → ZrCl₄ + 2/3 B₂O₃ reaction (−191 kJ/mol) forms ZrCl₄, which sublimes at 331 °C and leaves; the boron oxide leaves as the boroxine (BOCl)₃ in excess BCl₃. The reference is the remote-plasma clean at 350 °C every 182 wafers, 19 s per wafer, with the wafer-count trigger tuned to the flake onset of the chamber (0.5–1 µm of deposit) and a wet clean at every 5 µm to remove what the dry clean leaves in cold parts.

### 9.4.4 After the Clean

A freshly cleaned chamber has a different surface from one coated with ZrO₂, and its first ALD wafers differ in growth per cycle (nucleation on a clean wall) and in precursor consumption. The reference seasons the chamber with 2–3 dummy ZAZ depositions after every clean and monitors the first wafer's thickness (± 0.2 nm) before releasing the lot.

---

## 9.5 Monitors

```
Monitor                     What it checks                           Frequency        Limit
───────────────────────────────────────────────────────────────────────────────────────────────
VPD-ICPMS, backside sectors  Zr after Module E and clean             weekly + each PM  ≤ 1 × 10¹⁰ cm⁻²
TXRF, backside               trend of the same                       daily             ≤ 1 × 10¹¹ cm⁻² (trend)
TXRF, front (periphery pad)  Zr residue after Module P               weekly            ≤ 1 × 10¹³ cm⁻²
Zr "canary" wafer            clean-zone chamber: a bare wafer run    weekly; after PM  ≤ 1 × 10¹⁰ cm⁻² front
                             through a dummy recipe, then TXRF                          and back
Particles > 30 nm            flakes after clean, P4, ALD             per wafer / lot   ≤ 10 per wafer
Foreline pressure trend      ZrCl₄/AlCl₃ condensing in the exhaust   continuous        slope alarm
```

---

## 9.6 Excursions and Recovery

```
Event                              First action                          Recovery
───────────────────────────────────────────────────────────────────────────────────────────────────
Backside Zr above 10¹⁰ after E     hold lot; check zone, time, clean     re-clean edge; re-measure
Zr on a canary in a clean tool     quarantine tool; stop wafers          trace by sector; swap chuck;
                                                                         wet clean; re-qualify canary
Fluorine run on a Zr-coated wall   mark chamber; stop                    wet clean; replace liner
(any chamber in the Zr zone)                                              and ring; re-season
Flakes after ALD clean             check trigger vs flake onset          shorten interval; inspect
                                                                         showerhead
Edge ring eroded; wrap wider       VPD sector map                        replace ring; recheck zone
```

The cost of each is dominated by the wafers already processed: with a contamination chain like that of Section 9.2.1, a single missed edge-etch wafer is a 370-wafer problem on that chuck, which is why the VPD-ICPMS monitor and the canary are at a higher frequency than the film specification alone would require.

---

## Summary and Key Takeaways

1. **Two zones, one rule.** Wafers with backsides at ≤ 10¹⁰ Zr cm⁻² may leave the high-k zone; none may leave carrying wall deposits.

2. **One dirty wafer contaminates 370 others.** A chuck takes f × 1.44 × 10¹⁶ = 1.4 × 10¹³ cm⁻² (f = 10⁻³) and hands 1.4 × 10¹⁰ to the next wafer, falling by e⁻ᶠⁿ; after the edge etch the numbers are six orders lower.

3. **The conductor chambers stay clean in the strip-then-clear route.** P1/P2 never sputter zirconium; their WAC can use fluorine, saving 30 s per wafer and a failure mode.

4. **The hot clear chamber needs no fluorine.** Boron deposits only below 80 °C; a 150–180 °C liner leaves little of it.

5. **The ALD chamber gains 5.5 nm per wafer.** 182 wafers per micrometre; fluorine converts the deposit to ZrF₄ (1.75× the volume); a remote-plasma BCl₃/Cl₂ clean at 350 °C takes 17 minutes plus 40 minutes of thermal cycling, 19 s per wafer.

6. **Monitor in sectors.** VPD-ICPMS on the backside, a canary wafer in each clean-zone tool, and the foreline-pressure trend.

---

## Study Questions

1. Recompute the number of wafers contaminated above 10¹⁰ cm⁻² if f is 3 × 10⁻³ per contact in each direction. Compare with 10⁻³.

2. An edge-etch recipe leaves the backside at 2 × 10¹⁰ cm⁻² on one wafer in ten. Compute the chuck inventory after 100 wafers (assume no decay between contacts) and the pick-up of the next wafer. Is the furnace limit met?

3. The ALD chamber is cleaned every 120 wafers by remote-plasma BCl₃/Cl₂ at 350 °C. Compute the deposit thickness at trigger, the clean time, and the overhead per wafer.

4. Compute the clean time per micrometre at 300 °C using E_a = 0.6 eV and the 350 °C rate of 60 nm/min. Is a 300 °C clean competitive with the 350 °C one, given a 40 min thermal-cycling overhead for 350 °C and none for 300 °C?

5. A fluorine-bearing WAC is added to the P4 chamber by mistake and run for a week. Describe the wall chemistry, the particle trend, and the recovery.

6. List the Section 9.1.2 tools that must be added to the zirconium zone if the strip-then-clear route is replaced by Book #32's integrated route.

---

**Next Chapter:** [Chapter 10: Stopping on the Dielectric — Conductor Overetch, Fluorine Skins & Surface Modification](./10-stopping-on-the-dielectric.md)

---

**Chapter 9 Development Status:** Complete  
**Version:** 1.0
