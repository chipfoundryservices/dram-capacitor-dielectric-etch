# Chapter 13: Damage to the Remaining Dielectric

## Overview

The dielectric clear removes ZAZ that has no job, next to ZAZ that has the most demanding job on the die. Under each plate island lies the dielectric of about half a billion capacitors, each allowed one femtoampere of leakage. The clear cannot reach that dielectric with its ions, which stop in the oxide cap, or its light, which stops in the tungsten. It can reach it in other ways: through charge collected by the plate sidewall, through chlorine and boron entering at the cut edge, through hydrogen from the strip that precedes the clear and the treatment that follows it, through ultraviolet light absorbed in the ZAZ at the edge, and through the heat of a 250 °C chuck.

Book #32 analysed the in-situ cold route, in which the plate etch is still connected across the wafer when the high-k step begins and the plate acts as a large antenna. The split route of this book starts with every plate island already isolated and covered by an oxide cap. This chapter re-examines each damage mechanism for that geometry, estimates its magnitude, describes the test structures that detect it, and compares the routes.

**Learning Objectives:**
- Compute the antenna ratio and charging current of an isolated, capped plate island during D1, and the resulting voltage across the dielectric
- Explain how chlorine, boron-driven oxygen loss, and fluorine affect the ZAZ near the cut edge
- Estimate the hydrogen exposure of the array dielectric in the strip and PET
- Describe the reach of ultraviolet damage from the plate edge
- Design an overlap-ladder test structure and interpret its results
- Compare the damage signatures of the cold, hot, ALE, thermal-ALE, and hybrid routes

---

## 13.1 What Can Be Damaged

```
The dielectric that the clear must not degrade (reference):
  Under each plate island     array capacitors, ≈ 5 × 10⁸ cells per island,
                              dielectric area ≈ 0.67 cm² per island
                              (1.32 mm² × ≈ 50 surface enhancement over
                              the island, including non-array strips)
  At the plate edge           ZAZ under the TE in the 1.5 µm overlap:
                              no storage node beneath, but the path to the
                              first dummy and active capacitors
  Field ZAZ                   being removed; its damage is irrelevant
```

The damage mechanisms divide into those that act on the whole island through the conductor (charging, hydrogen) and those that act through the edge (chlorine, boron, ultraviolet light, fluorine).

---

## 13.2 Charging Through the Plate

### 13.2.1 The Island Antenna

In D1, each plate island is a floating conductor: TE TiN, SiGe, and W, isolated from every other island since the conductor etch, capped by 60 nm of oxide, and capacitively coupled through the ZAZ to its 5 × 10⁸ storage nodes. The only conducting surface exposed to the plasma is the sidewall:

```
Island antenna in D1 (reference, illustrative):
  Exposed conductor     sidewall: perimeter 4.6 mm × conductor height
                        195 nm ≈ 9 × 10⁻⁴ cm²
  Island dielectric     ≈ 0.67 cm²
  Antenna ratio         ≈ 1.3 × 10⁻³
  Oxide cap top         charges itself (insulator); does not reach the
                        plate
```

### 13.2.2 Current and Voltage

```
Net charging current into an island (illustrative):
  Ion current density at the sidewall (grazing, ≈ 3% of floor)
                                          ≈ 0.1 mA/cm²
  Ion current to the sidewall             ≈ 9 × 10⁻⁸ A
  Net imbalance (ion − electron), local   ≈ 10% → ≈ 9 nA per island
  Current density through the dielectric  9 nA / 0.67 cm² ≈ 1.3 × 10⁻⁸ A/cm²

ZAZ conduction (illustrative, 250 °C):
  At 0.5 V   ≈ 2 × 10⁻⁸ A/cm²
  At 1.0 V   ≈ 1 × 10⁻⁶ A/cm²
```

The dielectric conducts the imbalance away at well under half a volt. Over the whole step the charge through the dielectric is about 8 × 10⁻⁷ C/cm², many orders of magnitude below the charge-to-breakdown of ZAZ at operating fields. **Charging is not a damage mechanism in the split route.** It was in the cold in-situ route, where the plate was wafer-continuous at the start of the high-k step and its isolation into islands happened during the plasma (Book #32, Chapter 13).

---

## 13.3 Through the Edge: Chlorine, Boron, and Oxygen

### 13.3.1 Chlorine

Chapter 11 estimated that chlorine travels about 8 nm along the TiN/ZAZ interface during D1. In the ZAZ, chlorine substitutes for oxygen and creates donor-like states in the band gap; at the interface with TiN, it can lower the effective barrier height for electron injection. Both raise leakage locally. The affected band is about 10 nm wide along the edge, 1.5 µm from the first cell.

### 13.3.2 Oxygen Loss to Boron

BCl₃ removes oxygen from oxides; that is its purpose. At the exposed cut face of the ZAZ, it also removes oxygen from the first nanometre or so without removing the zirconium, leaving a sub-stoichiometric ZrOₓ edge with a high density of oxygen vacancies. Oxygen vacancies are the principal leakage-assisting defects in ZrO₂ and HfO₂ films. The PET's water vapor partly re-oxidizes the edge.

### 13.3.3 Fluorine

In the thermal-ALE route, the cut face is fluorinated by HF at 275 °C, and fluorine diffuses into the edge of the ZAZ. Fluorine is ambiguous in high-k films: at low concentrations it passivates oxygen vacancies and can reduce leakage, as it does in HfO₂ gate dielectrics; at higher concentrations it forms ZrF bonds that disrupt the lattice and raise leakage. The slot left by the undercut (Chapter 11) also exposes the TE TiN underside and the ZAZ cut face to every later chemistry until it is sealed.

---

## 13.4 Through the Conductor: Hydrogen

### 13.4.1 Sources

```
Hydrogen exposures around the clear (reference, illustrative):
  N₂/H₂ strip (before D1)      H atoms at 250 °C, ≈ 30 s
  D1 itself                    little hydrogen (from surface OH only)
  H₂O/N₂ PET (after D1)        H and OH at 250 °C, 30 s
  ILD deposition (later)       H from silane/TEOS chemistries at ≈ 400 °C
```

### 13.4.2 Reaching the Dielectric

Atomic hydrogen diffuses through W, SiGe, and TiN, more slowly through TiN and fastest through SiGe. It reaches the ZAZ under the plate from above and at the edge from the side. In ZrO₂, interstitial hydrogen and hydrogen bound at oxygen vacancies form shallow donor states; at the TiN/ZAZ interface, hydrogen can reduce the thin TiOₓNᵧ layer that helps set the barrier. The result is a small, uniform increase in array leakage that partly anneals out in later thermal steps:

```
Array leakage change attributable to hydrogen (illustrative, at ±1 V, 85 °C):
  After N₂/H₂ strip at 250 °C            + 3 to + 5%
  After the ILD deposition anneal        + 1 to + 2% (partial recovery)
```

The strip's hydrogen is a cost of the hard-mask route: the resist must be stripped before the clear, and an oxygen strip is ruled out by the plate edge (Chapter 2). Lower strip temperature and shorter time reduce it; the trade-off is carbon residue (Chapter 10).

---

## 13.5 Ultraviolet Light

### 13.5.1 What the Plasma Emits

```
UV and VUV emission in D1 (illustrative):
  Ar resonance lines          104.8, 106.7 nm (11.6–11.8 eV)
  Cl lines                    134–139 nm (≈ 9 eV)
  BCl band                    ≈ 272 nm (4.6 eV)
  ZrO₂ band gap               ≈ 5.8 eV (λ < 214 nm absorbed strongly)
```

### 13.5.2 Where It Is Absorbed

Photons above the band gap are absorbed in the first 10–30 nm of ZrO₂. Under the plate, they never reach the ZAZ: the oxide cap absorbs the VUV and the W absorbs everything else. At the plate edge, the ZAZ cut face is exposed to light arriving at grazing angles. Absorbed photons create electron–hole pairs and break bonds, and trapped holes and new defects form within a few tens of nanometres of the edge. The ZAZ is a thin slab of higher index than its neighbours (SiN below, TiN above), and some light coupled in at the edge travels farther before it is absorbed, but the TiN above absorbs strongly and limits the guiding. The reach of UV damage from the edge is estimated at 50–100 nm.

---

## 13.6 Heat

```
Thermal exposure of the array dielectric (reference):
  ZAZ ALD                       280 °C, ≈ 40 min
  TE TiN, SiGe, W, cap          400–425 °C, ≈ 60 min total
  D1 (including heat-up)        250 °C, ≈ 1.5 min
  Thermal-ALE batch             275 °C, ≈ 4 h
  ILD deposition                ≈ 400 °C, ≈ 30 min
```

D1's heat is negligible next to the plate depositions. The thermal-ALE batch adds hours at 275 °C, which slowly grows the TiOₓNᵧ interface between the TE TiN and the ZAZ where oxygen is available, and is measurable as a small EOT increase (≈ 0.01 nm) in arrays with thin interface layers. It is within the noise of most processes but is checked when the batch route is qualified.

---

## 13.7 Test Structures

### 13.7.1 Array Capacitor Monitors

```
Capacitor-array monitors (illustrative):
  Block            one full bank's capacitor array with the plate contacted
                   and all storage nodes tied through their transistors
  Measurement      I–V at ±1 V and ±2 V, 85 °C; C–V for EOT
  Limits           leakage shift ≤ 10% at ±1 V against a reference split
                   with the clear done by a non-plasma route
  TDDB             constant-voltage stress at 2.5 V, 125 °C: t₆₃ and Weibull
                   slope; no early-failure population
```

### 13.7.2 The Overlap Ladder

Damage that enters from the edge is invisible in a full bank, whose edge is 1.5 µm from its first cell. An overlap-ladder structure moves the edge toward the cells on purpose:

```
Overlap ladder (illustrative):
  Five small capacitor arrays, each with its plate edge at a different
  distance from the last active row: 0, 0.1, 0.2, 0.4, 0.8 µm (product 1.5 µm)
  Each array: 10⁶ cells; perimeter-to-area ratio high
  Measure: leakage per cell and retention-tail fraction versus overlap
```

```
Typical overlap-ladder result (D1, illustrative):
  Overlap (µm)    Leakage per cell (relative)    Retention-tail cells
  ────────────────────────────────────────────────────────────────────
  0               1.6×                           × 20
  0.1             1.08×                          × 2
  0.2             1.01×                          × 1.1
  0.4             1.00×                          × 1.0
  0.8             1.00×                          × 1.0
  Damage reach                                   ≈ 0.1–0.15 µm
```

The ladder measures the damage reach that Chapter 11's overlap budget assumed. If the reach is 0.15 µm for D1, the 0.4 µm overlap has a comfortable margin for damage; ingress and lithography dominate.

---

## 13.8 Comparing the Routes

```
Damage by route (illustrative):
  Route         Charging          Edge chemistry          Hydrogen     UV at     Reach
                                                                       the edge
  ─────────────────────────────────────────────────────────────────────────────────────
  R0 cold       significant in    Cl at 150 eV; veils     none (resist  yes       ≈ 0.2 µm
  in-situ       the isolation     (Book #32)              route uses   (resist
                phase                                     O₂ ash after) edge)
  D1 hot        negligible        Cl ≈ 8 nm along the     strip H      yes       ≈ 0.1–0.15
                                  interface; O loss                                µm
  D2 ALE        negligible        Cl lower; O loss        strip H      less      ≈ 0.05–0.1
                                  smaller (no bias in                  (60 eV Ar  µm
                                  step A)                              plasma)
  Thermal ALE   none              F into the cut face;    strip H;     none      ≈ 0.1–0.2
                                  open slot until sealed  long 275 °C            µm
  Hybrid        negligible        damaged face, HF        strip H      yes       ≈ 0.1–0.15
                                                                                  µm
```

The split routes remove charging from the list. What remains is edge chemistry, hydrogen from the strip, and ultraviolet light at the edge, all acting within about 0.15 µm of the plate edge, an order of magnitude inside the reference overlap.

---

## Summary and Key Takeaways

1. **The array dielectric is shielded from ions and light** by the oxide cap and the W strap; the clear reaches it through the conductor and through the edge.

2. **Charging is negligible in the split route.** Each island is already isolated; its sidewall antenna ratio is about 10⁻³, and the dielectric conducts the imbalance away below half a volt.

3. **The edge collects chlorine, oxygen loss, and in thermal ALE fluorine**, within about 10 nm of the cut face; UV adds damage within 50–100 nm.

4. **Hydrogen from the strip is the main whole-island exposure:** a few percent of array leakage, partly recovered by later anneals.

5. **The overlap ladder measures the damage reach directly:** about 0.1–0.15 µm for D1, inside the reference 1.5 µm and the proposed 0.4 µm.

6. **Charging was the cold route's problem; the edge and hydrogen are the split route's.**

---

## Study Questions

1. Recompute the charging current density for a plate island one quarter the size (same height) and for an island with a 400 nm-tall conductor stack. Does either reach a voltage that matters?

2. Estimate the number of storage nodes within 0.15 µm of the plate edge in a product with 0.4 µm overlap and one dummy row. What fraction of the bank is that?

3. A strip recipe change raises the wafer temperature from 250 to 280 °C. Which damage mechanism is affected, in which direction, and which test structure would show it first?

4. Explain why fluorine at the cut face might reduce leakage at low concentration and raise it at high concentration. How would you separate the two in an experiment?

5. Design an overlap-ladder experiment to compare D1 and thermal ALE. What sample size per split is needed to detect a 5% leakage difference at the 0.1 µm rung if the wafer-to-wafer variation is 4% (1σ)?

6. Why does the oxide cap prevent VUV from reaching the array, and why does that protection fail at the edge?

---

**Next Chapter:** [Chapter 14: Advanced Schemes — Higher-k Films, Area-Selective Deposition, 4F² & 3D DRAM](./14-advanced-dielectric-schemes.md)

---

**Chapter 13 Development Status:** Complete  
**Version:** 1.0
