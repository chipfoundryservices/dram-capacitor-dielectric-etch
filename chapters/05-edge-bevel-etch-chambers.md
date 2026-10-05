# Chapter 5: Edge & Bevel Etch Chambers

## Overview

The edge etch is the one dielectric etch that is done on a wafer that looks, to the plasma, almost like a bare silicon disc. Its film is amorphous, its target is a ring at the rim of the wafer, and its mask is geometry: a pair of ceramic parts that leave the outer 3 mm of the top, the bevel, and the outer 3.5 mm of the backside exposed and shield everything else. It must remove 5.5 nm of zirconia and alumina from that ring, and it must not remove 0.1 nm of the same film 1 mm inside it.

This chapter describes the chamber that does this. It follows the geometry that defines the zone, explains why a plasma-free gap protects the interior and why the boundary of an ion-assisted etch is sharp, sets the recipe and the time, builds the boundary budget, and describes the two parts of the process that determine whether the 10¹⁰ cm⁻² limit is met: the sputtered-zirconium residue after the plasma and the edge-limited wet clean that follows it.

**Learning Objectives:**
- Describe the edge-etch chamber geometry and which part defines which boundary
- Explain why a thin gap shields the wafer interior and why the zirconia boundary is sharp
- Compute the ion current, power, clearing time, and throughput of the reference edge etch
- Build the boundary-placement budget from centring, ring position, and plasma blur
- Describe the post-etch edge clean and estimate the removal factor it must provide
- Identify the failure modes of the edge etch and what each does to the die

---

## 5.1 What the Edge Chamber Has to Do

```
Edge etch, reference requirements:
  Film                 amorphous ZAZ, 5.5 nm, on: top ring r > 147.0 mm,
                       bevel (≈ 0.6 mm arc), backside r > 146.5 mm
  Zone area            top 28.0 cm², bevel 5.7 cm², backside 32.6 cm²: 66 cm²
                       (9.4% of the wafer's 707 cm² of flat area)
  Inventory            9.6 × 10¹⁷ Zr atoms per wafer
  Limit after clean    Zr ≤ 1 × 10¹⁰ cm⁻² on bevel and backside
  Boundary             147.0 ± 0.3 mm (top); ZAZ loss ≤ 0.1 nm at r < 146 mm
  Underlayers          periphery SiN or oxide on the top ring; Si on the backside
```

There is no resist and no lithography. The mask is the chamber.

---

## 5.2 Geometry

### 5.2.1 The Parts

```
Cross-section of the edge zone (schematic; not to scale):

          upper electrode / dielectric plate (radius 147.0 mm, powered edge ring outside)
   ───────────────────────────────────┐ ░░░ ← powered ring
        gap g_top = 0.3 mm            │ plasma
   ═══════════════════════════════╗ wafer top (r < 147: shielded; r > 147: exposed)
              wafer (775 µm)      ╚══╗ bevel
   ───────────────────────────────┐  ║
        backside                  │  ╚══ backside ring (r > 146.5: exposed)
   ───────────────────────────────┘     ░░░ ← grounded lower ring
          pedestal (radius 146.5 mm)

   Centre purge: N₂ or Ar flows from the centre of the upper plate outward through
   the top gap, 100–200 sccm
```

```
Part                        Defines                              Tolerance
──────────────────────────────────────────────────────────────────────────────────
Upper dielectric plate      inner boundary of the top zone       radius 147.0 ± 0.05 mm;
                                                                 gap 0.3 ± 0.05 mm
Pedestal (lower)            inner boundary of the backside zone  radius 146.5 ± 0.05 mm
Powered edge ring           where the plasma burns               ceramic-coated; consumable
Grounded lower ring         return path; plasma shape
Centre purge                keeps radicals out of the top gap    flow to ± 2%
Lift pins / centring        wafer position on the pedestal       ± 0.1 mm (3σ)
```

### 5.2.2 Why the Gap Shields the Interior

The top gap g = 0.3 mm is far below the dimension at which a plasma can exist at the chamber pressure:

```
Paschen product:  p·g = 0.2 Torr × 0.03 cm = 0.006 Torr·cm
(the breakdown minimum for Ar-based gases is near 0.5–1 Torr·cm)
```

At this product the gap cannot break down: electrons leave the gap by diffusion faster than they can multiply. No plasma, no ions, and no sheath exist over the wafer interior. The centre purge flows outward through the gap and carries any neutral radicals that diffuse in back out toward the ring. The exposed zone is defined by where the gap ends and the open ring begins.

### 5.2.3 Why the Boundary Is Sharp

Even where the geometry is imperfect, the etch boundary is set by the ions. Chlorine and BCl₂ radicals that leak into the gap meet a surface on which, by Chapter 3, they do nothing: Cl alone does not etch zirconia (ΔH = +120 kJ/mol). The rate falls from its full value to under 1% over a transition width Δ of about one gap, 0.3 mm (10–90%), set by where the sheath collapses at the plate edge. A thermal etch or a wet etch would creep under a mask edge by diffusion and reaction; the ion-assisted etch does not.

---

## 5.3 The Recipe

```
Edge etch (reference, illustrative):
  Gas             BCl₃ 60 / Cl₂ 15 / Ar 100 sccm;  centre purge N₂ 150 sccm
  Pressure        200 mTorr
  Power           13.56 MHz, 300 W on the edge ring; self-bias about −250 V
  Wafer temp      60–80 °C (heated by the plasma; no backside gas in the zone)
  Ion flux        ≈ 0.8 mA/cm² (0.25 × the 3.2 mA/cm² of the ICP chambers)
  Ion energy      250 eV (effective, peak of a collisional distribution)

Rates (amorphous film, Chapter 4):
  ZrO₂ 3.7 nm/min    Al₂O₃ 2.1 nm/min    SiN 3.3    SiO₂ 2.1    Si (backside) 10.7
```

### 5.3.1 Currents and Power

```
Zone area                              66 cm²
Ion current   0.8 mA/cm² × 66 cm²   =  53 mA
Ion power     0.8 mA × 250 V × 66   =  13 W   (0.2 W/cm²)
```

The ion power into the wafer is small, so the wafer stays close to the plasma-chamber temperature, and the edge zone does not thermally anneal the ZAZ. Power into the plasma is a few hundred watts, almost all dissipated in the ring and the gas.

### 5.3.2 Time and Throughput

```
Clearing time (centre of the zone):
  ZrO₂   2 × 2.6 nm / 3.7 nm/min = 1.405 min
  Al₂O₃  0.3 nm / 2.05 nm/min    = 0.146 min
  Total                          = 1.551 min = 93 s
Overetch 30%                      28 s  → step 121 s

Overetch consumption (backside, top ring):
  Si loss    10.7 nm/min × 28 s  =  5.0 nm       (limit 10 nm)
  SiN loss   3.3 nm/min × 28 s   =  1.5 nm       (top ring; no specification)

Throughput:
  Step 121 s + handling 40 s (transfer, pump, purge, centre) = 161 s
  → 22.4 wph per chamber; 4 chambers per mainframe → 89 wph
  Mainframes for 139 wph at 85% availability:  139 / (89 × 0.85) = 1.8 → 2
```

The overetch of 30% is not driven by the clearing statistics. With σ = 3% on an amorphous film, z = 30%/3% = 10 and the grain-tail problem does not exist. It is driven by the zirconium limit: the last atoms of the film are sputtered and redeposited, and a longer plasma step lowers the residue the wet clean has to remove (Section 5.6).

---

## 5.4 The Boundary Budget

The top boundary at r = 147.0 mm must hold to ± 0.3 mm. Four contributions, combined in quadrature:

```
Contribution                        3σ (mm)
──────────────────────────────────────────────
Wafer centring on the pedestal       0.10
Ring and plate position (machining)  0.10
Plasma boundary blur (Δ/2)           0.15       (Δ = 0.3 mm 10–90%)
Wafer edge shape (round, bow)        0.05
Root-sum-square                      0.21 mm
Specification                        0.30 mm        margin 1.4×
```

The nearest die edge lies at r = 146 mm. The distance from the nominal boundary is 1.0 mm; from the worst-case boundary (147.0 − 0.3 = 146.7 mm) it is 0.7 mm. The ZAZ at r < 146 mm must lose no more than 0.1 nm (Chapter 1). A boundary 0.7 mm beyond the specified position still leaves a margin of 0.7 mm to the die.

The backside boundary at r = 146.5 mm is not critical for devices, since nothing on the backside is a cell. It is set by the ALD wrap model of Chapter 2: x_sat = 2.1 mm, tail to 3.1 mm, zone 3.5 mm.

---

## 5.5 Edge-Zone Failure Modes

```
Symptom                           Likely cause                      Effect on the die
────────────────────────────────────────────────────────────────────────────────────────────
ZAZ loss at r = 140–146 mm        plate gap too large; purge low;   edge-die C_s and leakage shift
                                  centring error                    (110 dies between 140 and 150 mm)
Zr on the backside above 10¹⁰     zone too narrow; time short;      Zr to chucks and furnaces
                                  wrap wider than model             (Chapter 9)
Zr on the bevel apex only         plasma shadowed at the apex       flakes from the bevel
Rim of the ZAZ lifts at r = 147   edge cut over a weak interface    particles; edge-die defects
Si backside roughened             overetch too long; Cl on Si       particles on the next chuck
B residue (hygroscopic film)      no O₂ strip; no wet clean         boric acid particles
Etch non-uniform around the ring  powered ring worn; wafer off-     one side of the wafer still
                                  centre; purge asymmetry           has Zr: found by VPD sectors
```

Two of these are central. An error that moves the boundary inward touches the ZAZ of the edge die, which carry active cells; it is detected by a ZAZ thickness line-scan across r = 140–150 mm at every PM. An error that leaves the backside zone incomplete does no harm at all in the chamber and does a great deal later, in the furnace; it is caught only by VPD-ICPMS on a sacrificial wafer (Chapter 15).

---

## 5.6 After the Plasma: Zirconium That Is Not a Film

### 5.6.1 Redeposition

At the end of the plasma the film is gone but zirconium is not. Sputtered ZrClₓ, only partly volatile at 60–80 °C (ZrCl₄ sublimes at 331 °C), lands on the nearest surface, which is the cooled gap above the zone, the lower ring, and the wafer itself outside the sputtering site. A backside measurement after the plasma and an O₂ plasma strip of the boron film reads:

```
Zr after plasma + O₂/H₂O strip (TXRF, backside):    ≈ 4 × 10¹³ cm⁻²
Limit:                                               1 × 10¹⁰ cm⁻²
Required removal factor:                             4×10¹³ / 1×10¹⁰ = 4,000 (3.6 decades)
```

### 5.6.2 The Edge Wet Clean

Because there is no forest in the zone (the top ring at r > 147 mm is outside the array and the backside has no pillars), a dilute HF clean is safe at the edge where it would be impossible at the centre. A spin-and-nozzle module dispenses 0.5% HF onto the bevel and backside edge with an N₂ shield over the top interior:

```
Edge clean (reference, illustrative):
  Chemistry      0.5% HF, 25 °C, 20 s;  then DI rinse, spin dry
  Etch of residue and film remnants:  amorphous ZrOₓ ≈ 2 nm/min → removes 0.7 nm
  Si, SiN, SiO₂ loss:    < 1 nm (SiN 2 nm/min × 20 s = 0.7 nm)
  Zr after clean (VPD-ICPMS):    ≈ 6 × 10⁹ cm⁻²      removal factor 6,700
```

The clean must not reach the top interior. The nozzle is 3.0 mm wide at the wafer surface, the meniscus is held by the N₂ shield, and the same boundary budget of Section 5.4 applies. An HF meniscus that creeps to r = 140 mm wets the ZAZ-covered forest at the edge die; the capillary collapse risk of Chapter 3 then applies to the edge die only, and a partly collapsed forest there is a defect of that die.

### 5.6.3 Checking the Result

VPD-ICPMS collects the surface onto a droplet and reads it by mass spectrometry, with a detection floor of 10⁸–10⁹ cm⁻²: it can resolve 10¹⁰ with a factor-ten margin. TXRF does not (floor 10⁹–10¹¹ on a spot), so it is used as a daily trend and VPD-ICPMS as the weekly proof (Chapter 15).

---

## 5.7 Chamber Materials and Matching

```
Edge-etch chamber (reference):
  Plate, rings        Y₂O₃ / Al₂O₃ ceramics; no quartz in the plasma (B and Cl attack)
  Wall                anodized Al or Y₂O₃-coated; wall temperature 80 °C (above BₓClᵧ
                      deposition on the plate side)
  Consumables         powered ring, upper plate, lower ring; life set by erosion
                      and by Zr wall loading (Chapter 9)
  Contamination zone  "high-k" (Zr): wafers that enter must not go to a clean tool
  Matching            chamber-to-chamber boundary position ± 0.1 mm; rate ± 3%
```

The chamber lives in the zirconium zone of the fab (Chapter 9). It is cleaned chlorine first (Chapter 9); a fluorine clean would convert the zirconium deposits on the plate and ring into ZrF₄, which is permanent.

---

## Summary and Key Takeaways

1. **The mask is the chamber.** A 0.3 mm plate gap above the wafer, a pedestal of radius 146.5 mm, and a powered ring leave a 66 cm² ring exposed and everything else shielded.

2. **The gap cannot light.** p·g = 0.006 Torr·cm is far below the Paschen minimum, so the interior has no plasma, and the centre purge removes radicals.

3. **The boundary is sharp because radicals do not etch zirconia.** The rate falls to under 1% over about one gap (0.3 mm).

4. **121 s, 89 wph per four-chamber mainframe.** 93 s to clear 5.5 nm of amorphous ZAZ at 3.7 nm/min, plus 30% overetch, plus 40 s of handling.

5. **The boundary budget is 0.21 mm against 0.30 mm.** The nearest die edge is 0.7 mm beyond the worst-case boundary.

6. **The plasma leaves 4 × 10¹³ Zr cm⁻² and the wet clean removes it.** A 20 s dilute-HF edge clean gives a removal factor of 6,700, the only way to the 10¹⁰ limit.

---

## Study Questions

1. Compute the ion current and ion power into a zone of 80 cm² if the ion flux is 0.6 mA/cm² at 300 eV. By how much does the wafer's temperature rise over a 121 s step if all the ion power heats the wafer and none is lost? (Silicon wafer, 128 g, 0.7 J/(g·K).)

2. A 0.4 mm gap is used with a pressure of 0.5 Torr. Compute p·g and compare it with the Paschen minimum. At what gap does the interior become able to break down at that pressure? (Take 0.5 Torr·cm as the minimum.)

3. Recompute the clearing time, overetch, and throughput of the edge etch if the ion flux is 0.35 of the ICP value (rather than 0.25) and the ion energy is unchanged. How many mainframes are needed for 139 wph?

4. The wafer centring on the pedestal degrades to ± 0.25 mm (3σ). Recompute the boundary budget. Does the specification still hold? Which die are exposed?

5. A VPD-ICPMS reading of the backside is 3 × 10¹⁰ cm⁻² after the edge clean. List the possible causes in order of likelihood and the checks that separate them.

6. The edge wet clean is changed from 0.5% HF for 20 s to 0.1% HF for 60 s. Estimate the film and nitride removal, and say whether the removal factor is expected to rise or fall.

---

**Next Chapter:** [Chapter 6: Thermal & Vapor-Phase Etch Reactors](./06-thermal-vapor-etch-reactors.md)

---

**Chapter 5 Development Status:** Complete  
**Version:** 1.0
