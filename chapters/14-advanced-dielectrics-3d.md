# Chapter 14: Advanced Dielectrics & 3D Architectures

## Overview

The ZAZ stack is near the end of its road. At an EOT of 0.4 nm, a ZrO₂-based film no longer has the room: the dielectric constant of the tetragonal phase is about 43, and thinner films leak too much. The next dielectrics are doped or alloyed zirconia and hafnia, rutile titanium dioxide, niobium and tantalum oxides, and perovskites such as SrTiO₃, with dielectric constants from 40 to above 100. Every one of them changes the etch, because the removal of a dielectric is decided by whether its metal halide is volatile. At the same time the arrays get taller and finer (Book #31) and then rotate: in 4F² and 3D DRAM the capacitor lies in tiers and the dielectric lies in lateral cavities.

This chapter follows these changes through the four dielectric etches of the book. It builds the volatility map of the candidate oxides, shows how a few percent of a non-volatile dopant puts a residue tens of times above the limit, treats titanium oxide, where HF alone is volatile and thermal ALE loses its self-limiting character, treats strontium and barium, where no dry route exists, chains the taller-array scaling through the ALD pulse and the edge zone of Chapter 2, and ends with the lateral dielectric recess of a 3D stack.

**Learning Objectives:**
- Classify a candidate dielectric by the volatility of its chlorides and fluorides and choose a removal route
- Compute the residue left by a non-volatile dopant at a given fraction of the cation sites
- Explain why thermal ALE of TiO₂ with HF alone is not self-limiting and what to change
- Describe the wet clear for SrTiO₃ and BaTiO₃ and its undercut
- Chain an increase in aspect ratio through the dosing time, the backside wrap, and the edge-zone width
- Estimate the cycles, time, and area cost of a lateral dielectric recess in a 3D stack

---

## 14.1 What Changes and Why It Matters

```
Candidate dielectric        k (typical)     Electrode             What the etch inherits
────────────────────────────────────────────────────────────────────────────────────────────────────
ZrO₂/Al₂O₃/ZrO₂ (ZAZ)       ≈ 43            TiN                   reference
Doped ZrO₂ (Al, Y, La, Sr)   40–50           TiN                   dopant halides may not volatilize
HfO₂/ZrO₂ nanolaminate, HZO   30–50 (AFE)     TiN, Mo               HfCl₄ ≈ ZrCl₄; phase sensitive
TiO₂ (rutile) / Al₂O₃         80–100          Ru, RuO₂ template     TiF₄ and TiCl₄ volatile
Nb₂O₅, Ta₂O₅ (and doped)      30–60           TiN, NbN              chlorides volatile near 240 °C
SrTiO₃, (Ba,Sr)TiO₃           > 100           noble / oxide         Sr, Ba halides never volatile
```

These are the dielectrics Book #32 (Chapter 14) listed. That chapter asked what they do to the plate etch. This one asks what they do to each of the four dielectric etches.

---

## 14.2 The Volatility Map

Removal by a dry etch needs a volatile product. The practical limit is the highest wafer or chuck temperature a chamber can sustain, about 350 °C; a halide is useful if it sublimes or boils below that.

```
Sublimation / boiling point (°C, handbook values, rounded)
Metal    Chloride          Fluoride         Dry-removable below 350 °C?
────────────────────────────────────────────────────────────────────────────
Zr       ZrCl₄   331       ZrF₄   906       yes (chloride, marginal)
Hf       HfCl₄   317       HfF₄   970       yes (chloride, marginal)
Al       AlCl₃   180       AlF₃  1276       yes (chloride)
Ti       TiCl₄   136       TiF₄   284       yes (either)
Nb       NbCl₅   248       NbF₅   234       yes (either)
Ta       TaCl₅   239       TaF₅   229       yes (either)
Sr       SrCl₂ ≈ 1250      SrF₂  2460       no
Ba       BaCl₂  1560       BaF₂  2260       no
La       LaCl₃  1812       LaF₃ ≈ 2330      no
Y        YCl₃   1507       YF₃  ≈ 2230      no
```

Two classes follow. **Class V**: the metal has a volatile halide below 350 °C (Zr, Hf, Al, Ti, Nb, Ta). Its dielectric can be removed by ion-assisted chlorination, thermal fluorination with ligand exchange, or, for Ti, Nb, and Ta, by a fluoride alone. **Class N**: no halide below 350 °C (Sr, Ba, La, Y). A dielectric with any of these as a *constituent* cannot be removed dry; a dielectric with one as a *dopant* leaves it behind.

---

## 14.3 Dopants: A Few Percent Is Tens of Times the Limit

A film doped at a fraction x of its cation sites with a Class N element leaves that element on the surface after the host has been etched away. For the reference film, with 1.44 × 10¹⁶ cation sites per cm² (5.2 nm of ZrO₂):

```
Residue = x × 1.44 × 10¹⁶ cm⁻²          limit 1 × 10¹³ cm⁻²

Dopant            x        Residue (cm⁻²)     × limit
────────────────────────────────────────────────────
La (Class N)      3%       4.3 × 10¹⁴          43
Y  (Class N)      5%       7.2 × 10¹⁴          72
Y  (Class N)      1%       1.4 × 10¹⁴          14
Sr (Class N)      2%       2.9 × 10¹⁴          29
La (Class N)      0.1%     1.4 × 10¹³          1.4
Al (Class V)      5%       none (AlCl₃ volatile)
```

The tolerable fraction of a non-volatile dopant is 10¹³ / 1.44 × 10¹⁶ = **0.07%** of the cation sites, which is below the doping range in use (1–5%). A film doped with La, Y, or Sr therefore cannot be cleared by any of the dry routes of this book: it needs a wet clear or a physical one, and the contamination zones of Chapter 9 gain a new element. The residue lies on the periphery SiN, where it is a contact etch stop (LaF₃, YF₃, SrF₂ do not volatilize in fluorocarbon) as ZrO₂ is, and it cannot be seen by the Al marker of Chapter 8, since the dopant's emission is weak and its release rate small.

---

## 14.4 Titanium Dioxide: When HF Alone Etches

```
TiO₂ + 4 HF → TiF₄(g) + 2 H₂O       ΔH = −95 kJ/mol;  TiF₄ sublimes at 284 °C
```

At 280 °C TiF₄ is volatile. HF vapor alone removes TiO₂ from the surface, and keeps removing it for as long as HF is supplied: there is no fluoride layer of limited thickness to be volatilized by a second half-cycle, since the product leaves on its own. The thermal ALE of Chapter 3 depends on that second half-cycle for its self-limiting character. For TiO₂ the HF dose alone defines the removal, which then depends on exposure, which depends on position along the channel (Chapter 13). The result is not self-limiting and not uniform along the pillar.

```
Consequences for a TiO₂ dielectric (illustrative):
  HF/DMAC cycle           continuous etch during each HF pulse: ≈ 0.3–1.0 nm per pulse
                          rather than a fixed 0.07 nm; top of the pillar etches more
  Redesign                lower the temperature to 200–220 °C (TiF₄ no longer volatile),
                          so that the fluoride limits itself and the ligand exchange
                          becomes necessary again; EPC then ≈ 0.02 nm; or use a Cl-based
                          ALE (BCl₃ then plasma/thermal) where TiCl₄ (136 °C) is volatile
  Plasma route            BCl₃/Cl₂ etches TiO₂ faster than ZrO₂ (TiCl₄ volatile): selectivity
                          to SiN improves, but a TiO₂/SiN stop is thin
```

Titanium oxide is the easiest of the high-k oxides to remove and the hardest to keep: every step that uses fluorine near it attacks it. In a TiO₂/Al₂O₃ stack the Al₂O₃ layer (AlF₃, non-volatile) is the one that survives HF, and the whole stack may be better cleared by a Cl-based route in which the alumina is volatile as AlCl₃.

Nb₂O₅ and Ta₂O₅ behave like TiO₂ in that both their chlorides and fluorides are volatile near 240 °C and 230 °C: thermal etching by HF alone is possible and equally not self-limiting, and an ion-assisted step in Cl₂/BCl₃ at 250 °C is straightforward.

---

## 14.5 Strontium and Barium: No Dry Route

### 14.5.1 What Happens

SrTiO₃ and (Ba,Sr)TiO₃ have a perovskite lattice in which Sr or Ba is a major constituent (one cation in two). In a halogen plasma the titanium leaves as TiCl₄ and the strontium stays as SrCl₂ or SrF₂. The periphery film etched in BCl₃/Cl₂ leaves a Sr-rich layer of about the film's cation inventory of Sr:

```
SrTiO₃, a = 0.3905 nm: Sr sites = 1/a³ = 1.7 × 10²² cm⁻³ ≈ 1.7 × 10¹⁵ cm⁻² per nm of film
8 nm of film: ≈ 1.3 × 10¹⁶ cm⁻² of Sr, some thirteen hundred times the 10¹³ cm⁻² limit
```

No dry process within the temperature range of a wafer chamber volatilizes it. Book #32 reached the same conclusion for the plate etch: the dielectric must be removed wet.

### 14.5.2 The Wet Clear

```
Wet clear of SrTiO₃ (illustrative):
  Chemistry       dilute HCl/HF mixture, 25 °C; rate ≈ 3–6 nm/min on amorphous or
                  nanocrystalline film
  Time            8 nm × 1.3 / 4 nm/min ≈ 2.6 min
  Lateral undercut   8 nm × 1.3 = 10.4 nm (isotropic; ≈ 13 nm for a 10 nm film)
  Selectivity     SiN etches too: dilute HF at 2 nm/min → 5 nm lost; W and TiN are attacked
                  quickly by peroxide-containing mixtures and only slowly by dilute HCl/HF
```

The wet step has no forest to protect on the periphery, so the capillary problem of Chapter 3 does not arise. Its undercut is the overlap budget's new term: 10–13 nm, a small addition to the sum of Chapter 11 (R1's sum rises from 152 to 165 nm and O_min from 0.23 to 0.25 µm), still far below the reference overlap of 1.5 µm.

### 14.5.3 Alternatives

```
Option                              Comment
───────────────────────────────────────────────────────────────────────────────────
Pattern the dielectric as deposited  area-selective ALD or a lift-off before the plate;
                                     needs resist over the forest (Chapter 4: not allowed)
Sputter removal (Ar⁺, 300 eV+)       physical; slow (≈ 1 nm/min); no selectivity; damages SiN
Leave the film in the periphery      high-k film (k > 100) under later metal: capacitive
                                     coupling, and it is a contact-etch stop
Contact etch through it              fluorocarbon forms SrF₂: stops
```

Strontium and barium dielectrics therefore restore the wet step of the hybrid route (R4) as the *only* route, and the dielectric clear becomes a wet process with the plate as its mask.

---

## 14.6 Ferroelectric and Antiferroelectric HZO

Hafnium-zirconium oxide can be crystallized into an orthorhombic (ferroelectric) or tetragonal-like (antiferroelectric) phase with a high k near the phase boundary. The etch is the same as ZrO₂'s, since HfCl₄ and ZrCl₄ are alike (Section 14.2). The new property is phase sensitivity:

```
Phase-sensitive features of HZO capacitors:
  The polar phase depends on stress and on thermal history; a cut edge relaxes the stress
  within a few tens of nm; ion damage (Chapter 12) can stabilise the non-polar phase locally
  Thermal ALE with F incorporation (module T) may shift the phase near the surface
  Consequence: the damage length of Chapter 12 becomes a design parameter; the overlap budget
  of Chapter 11 should use the phase-relaxation length, not the vacancy length
```

For a cell array whose dielectric is the product, a trim by thermal ALE needs a phase check; the trim-dose array of Chapter 12 is read on polarization (P–V loops), not only on leakage.

---

## 14.7 Taller and Finer Arrays

Book #31 carries the capacitor to a 1d-class array on a 37 nm pitch, 26 nm top CD, and a 2.1 µm mold. The chain of Chapter 2 and Chapter 6 then runs as follows (average pillar CD 22 nm and exposed height 1.9 µm assumed):

```
                                           1b reference      1d-class
Pitch                                      45 nm             37 nm
Inscribed channel (with 5.5 nm ZAZ)        d = 13.0 nm       d = 37/√3 × 2 − 2(11 + 5.5) = 9.7 nm
Exposed height                             1.41 µm           1.9 µm
Aspect ratio of the channel                109               195
Cell area (hexagonal)                      1734 nm²          1186 nm²

ALD forest pulse, min (6N_sAR²/n₀v̄)       1.6 s             5.2 s    (× AR²: 3.2)
Pulse at 25% margin                        2.0 s             6.5 s
Backside wrap x_sat = g√(n₀v̄t/3N_s)       2.1 mm            3.7 mm   (× √3.2 = 1.8)
Edge zone, backside (1.5 x_sat + 0.4)      3.5 mm            6.0 mm
Thermal ALE: HF  t_sat (0.1 Torr)          0.41 s            1.31 s
Thermal ALE: DMAC t_sat (0.05 Torr)        0.84 s            2.72 s   → 0.10 Torr and a 3 s pulse
```

Three things follow. The ALD precursor pulse that the forest needs grows with AR², and the wrap-around grows with its square root, so the backside zone of the edge etch widens from 3.5 to 6.0 mm: the edge zone is a design variable that follows the mold height. The thermal ALE doses rise together with AR², and the DMAC pulse of 2 s no longer saturates the bottom (margin 0.74) unless the pressure is raised or the pulse lengthened (Chapter 6). And the trim and rework times grow, because the longer pulses add to the cycle. In a 4F² vertical-channel array the lattice is square and the interstitial channel wider, so the dosing is easier, while the finer pitch narrows the film's lateral margin everywhere.

---

## 14.8 3D DRAM: Lateral Dielectric Recess

### 14.8.1 The Structure

In 3D DRAM the capacitors lie in tiers (Book #32, Chapter 14: 100 tiers, an opening about 6 µm deep, AR ≈ 50). The electrode, dielectric, and plate are deposited into the lateral cavities from a vertical opening, and coat the opening's sidewall as well. To isolate the tiers the films on that sidewall must be removed, and each tier's films recessed into its cavity. The electrode is recessed 10–20 nm (Book #32); the dielectric must be recessed at least as far, or a free-standing lip of ZAZ is left standing between tiers, brittle and flaking.

### 14.8.2 Dosing the Stack

```
Vertical opening: 120 nm diameter, 6 µm deep, AR = 50
  HF   t_sat = 6 × 7.7×10¹⁸ × 50² / (1.75×10²¹ × 765) = 0.086 s   (0.1 Torr)
  DMAC t_sat = 0.18 s   (0.05 Torr)
```

The opening saturates in under a fifth of a second; each tier cavity, 150–300 nm deep and 30 nm high, is a shallow side channel (AR 5–10) and saturates faster still. Thermal ALE is well suited to the stack: it is isotropic, self-limiting, and the same removal per cycle is delivered to the top tier and the bottom tier.

### 14.8.3 Cycles, Time, and Area

```
Dielectric recess d_r (equal to the electrode recess, plus margin)
  d_r (nm)    Cycles (0.073 nm)    Single-wafer (10 s)    Batch (25 wafers, 20 s + 20 min)
  ───────────────────────────────────────────────────────────────────────────────────────
  10             137                 23 min                 66 min → 23 wph
  15             205                 34 min                 88 min → 17 wph
  20             274                 46 min               111 min → 13.5 wph

Area lost: each nanometre of dielectric recess beyond the electrode's costs 1/L of the
cavity's dielectric area:  L = 200 nm → 0.5% of C_s per nm of excess
```

A recess of 15 nm takes 205 cycles and half an hour. It is not a trim: it is a main etch of the module, and its economics are those of a batch process, in which every tier is cut back by the same amount. The over-cycling allowance (30% in the periphery of Chapter 6) is replaced by the uniformity of removal between tiers (± 5%, Chapter 13): 15 nm ± 0.75 nm, costing at most 0.4% of C_s per tier.

---

## 14.9 Summary Table

```
Change                      Gets harder                            Gets easier
──────────────────────────────────────────────────────────────────────────────────────────────
Doped ZrO₂ (La, Y, Sr)       residue at 14–72× the limit             —
TiO₂, Nb₂O₅, Ta₂O₅           HF alone is not self-limiting          volatile chlorides and fluorides
SrTiO₃, BaTiO₃               no dry route: wet clear, undercut       —
HZO (AFE/FE)                 phase sensitivity of cut edge and trim same chlorides as ZrO₂
1d-class (AR 195)            ALD pulse 3.2×, wrap 1.8×, zone 6 mm;   —
                             DMAC dose
3D DRAM                      205-cycle lateral recess; tier-to-tier   thermal ALE suits the stack
                             uniformity
```

---

## Summary and Key Takeaways

1. **Volatility decides.** Zr, Hf, Al, Ti, Nb, and Ta have a halide that is volatile below 350 °C (Class V); Sr, Ba, La, and Y do not (Class N).

2. **A Class N dopant is a residue.** 10¹³ cm⁻² is 0.07% of the cation sites; 1–5% dopants leave 14–72 times the limit.

3. **TiO₂ breaks thermal ALE's self-limit.** TiF₄ sublimes at 284 °C, so HF alone etches continuously; lower the temperature, or use a Cl route.

4. **SrTiO₃ and BaTiO₃ need a wet clear.** About 2.6 min for 8 nm, with 10–13 nm of undercut: small against the 1.5 µm overlap.

5. **Taller arrays widen the edge zone.** AR 109 → 195 raises the ALD pulse 3.2×, the wrap 1.8×, and the backside zone from 3.5 to 6.0 mm; the DMAC pulse no longer saturates at 2 s.

6. **3D DRAM turns the trim into a main etch.** A 15 nm lateral recess takes 205 cycles, about 34 minutes per wafer, or 17 wph in a batch tool.

---

## Study Questions

1. A film of Hf₀.₅Zr₀.₅O₂ is doped with 2% Sr on the cation sites and is 8 nm thick (density of cations 2.8 × 10²² cm⁻³). Compute the Sr areal density of the film and the residue as a multiple of the 10¹³ limit. What would the dopant fraction have to be to meet the limit?

2. In a HF/DMAC cycle on a TiO₂ film at 280 °C each HF pulse etches 0.6 nm and the top of a 1.4 µm pillar sees the full pulse while the bottom sees a dose margin of 0.5. Estimate the removal at the top and bottom after 3 cycles, using the saturated-fraction model of Chapter 13 for the bottom, and describe the non-uniformity.

3. A SrTiO₃ film of 10 nm is cleared wet at 4 nm/min with 30% overetch. Compute the time, the undercut, and the SiN loss at 2 nm/min. Add the undercut to the Chapter 11 sum for R1 and recompute O_min.

4. For a 1d array with a 2.1 µm mold and 1.9 µm exposed pillar height, recompute AR, the minimum ALD pulse and the 25% pulse, the wrap x_sat at g = 12 µm, and the backside zone, if the pillar average CD is 24 nm instead of 22.

5. A 3D stack requires a dielectric recess of 18 nm into cavities 250 nm deep, at 0.073 nm per cycle. Compute the cycles, single-wafer time at a 10 s cycle, and the area cost if the electrode recess is 15 nm.

6. Decide, with reasons, which of the four dielectric etches of this book are available for a (Ba,Sr)TiO₃ dielectric and which are not.

---

**Next Chapter:** [Chapter 15: Metrology, Inspection & Advanced Process Control](./15-metrology-inspection-apc.md)

---

**Chapter 14 Development Status:** Complete  
**Version:** 1.0
