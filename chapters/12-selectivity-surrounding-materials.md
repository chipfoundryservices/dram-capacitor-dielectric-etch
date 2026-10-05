# Chapter 12: Selectivity & the Materials Around the Dielectric

## Overview

The dielectric clear touches five materials besides the ZAZ: the periphery nitride it lands on, the oxide cap that protects the plate, the conductor sidewall at the plate edge, the 0.3 nm aluminium oxide inside the ZAZ, and, through the gas, everything on the walls. Chapter 11 treated the sidewall. This chapter treats the others: how much of each is consumed, what is left on each surface, and how the post-etch treatment and rinse turn those surfaces into something the inter-layer dielectric can be deposited on.

Selectivity in a high-k clear is an unusual quantity. The film is 5.4 nm thick and the landing film is 120 nm thick, so even a selectivity below one would not consume the nitride. What matters more is the state of the surface: a few atomic percent of chlorine and a few times 10¹⁴ boron atoms per square centimetre on the nitride decide whether the ILD adheres, whether it outgasses, and whether the plate edges leak to each other across the periphery.

**Learning Objectives:**
- Compute the SiN landing loss and its local variation for D1 and D2
- Describe the chemical state of the SiN surface after the clear: boron, chlorine, and zirconium
- Design a post-etch treatment and rinse that remove chlorine and boron without oxidizing the plate edge
- Build the oxide-cap budget across the plate conductor etch and the dielectric clear
- Explain the role of the Al₂O₃ insertion and of variant stacks in the clearing sequence
- Compare the surfaces each route hands to the ILD

---

## 12.1 The Landing Nitride

### 12.1.1 Loss

```
SiN landing loss in D1 (reference, illustrative):
  SiOₓNᵧ interlayer (0.5 nm) at 3.5 nm/min          ≈ 8 s
  SiN at 3.0 nm/min for the remaining overetch       ≈ 0.85 nm
  Nominal total (interlayer + SiN)                   ≈ 1.3 nm
```

### 12.1.2 Local Variation

Domains that clear early lose more nitride than domains that clear late. With σ_g = 10%, a domain at −3σ clears at about 25 s and is exposed for about 36 s; one at +3σ clears at about 47 s and is exposed for about 14 s:

```
Local SiN loss (D1, illustrative):
  Early domain (−3σ)       ≈ 1.9 nm
  Mean domain              ≈ 1.3 nm
  Late domain (+3σ)        ≈ 0.7 nm
  Local range              ≈ 1.2 nm over tens of nanometres
```

A nanometre of nitride roughness on a 120 nm film has no effect on the periphery contacts, which etch through the nitride anyway. It is reported because it is the signature of the clearing spread: AFM roughness of the cleared nitride on a monitor pad correlates with σ_g (Chapter 15).

### 12.1.3 By Route

```
SiN loss by route (illustrative):
  R0 cold in-situ (Book #32)     ≈ 4 nm      (selectivity 0.75, 50% OE)
  D1 hot                         ≈ 1.3 nm
  D2 plasma ALE                  ≈ 0.2 nm    (17 over-cycles × 0.012 nm)
  Thermal ALE                    < 0.1 nm
  Hybrid                         ≈ 1 nm      (mostly in the HF step)
  Specification                  ≤ 5 nm
```

Every route meets the loss specification. The landing loss is not what separates them.

---

## 12.2 The Surface Left on the Nitride

### 12.2.1 Composition After D1

```
SiN surface after D1, before PET (illustrative, XPS and TXRF):
  B         3–6 × 10¹⁴ /cm², as B–N and B–O bonding in the top nm,
            plus a BₓClᵧ overlayer ≈ 0.3 nm
  Cl        3–5 at% in the top 1 nm (Si–Cl, B–Cl)
  O         from the SiOₓNᵧ interlayer remnant and BOClₓ
  Zr        1 × 10¹¹ to 1 × 10¹² /cm² average (gas-phase redeposition
            and the tail of clearing), far below the 1 × 10¹³ limit
  F         < 0.5 at% (BT removed the fluorinated skin)
```

### 12.2.2 Why It Matters

```
Effects of surface residues on the cleared nitride (illustrative):
  Residue        Effect                                      Seen as
  ─────────────────────────────────────────────────────────────────────────
  Cl             HCl release in the ILD deposition; corrosion  ILD blisters;
                 of exposed TiN/W at the plate edge          edge oxidation
  BₓClᵧ          hygroscopic; absorbs water in queue; B₂O₃   ILD adhesion loss;
                 glass at the ILD interface                  delamination at CMP
  B (bonded)     surface conduction when wet; dopant source  comb leakage;
                 if the nitride is later thinned             (rarely) Vt shift
  Zr (trace)     none at < 10¹² /cm² unless clustered        contact opens only if
                                                             clustered (Ch. 10)
```

---

## 12.3 Post-Etch Treatment and Rinse

### 12.3.1 The Reference PET

```
Post-etch treatment (reference, strip/PET chamber, illustrative):
  Chemistry       remote (downstream) plasma of H₂O 300 / N₂ 700 sccm,
                  1 Torr, 2 kW, wafer 250 °C, 30 s
  Reactions       Cl + H → HCl↑ (surface Cl removed)
                  BₓClᵧ + H₂O → B(OH)₃ / B₂O₃ + HCl↑
                  Ti–Cl at the TE edge → Ti–O (thin TiOₓ passivation)
  Not wanted      W oxidation: limited to < 1 nm WOₓ by the short time and
                  the low oxygen potential of H₂O compared with O₂
Then              DI-water rinse (single wafer, 60 s, 25 °C): dissolves
                  B(OH)₃ (solubility ≈ 50 g/L) and HCl; spin dry
```

### 12.3.2 Results

```
SiN surface after PET + rinse (illustrative):
                         After D1       After PET     After rinse    Spec
  ────────────────────────────────────────────────────────────────────────
  Cl (at%)               3–5            ≈ 1.5         ≤ 0.8          ≤ 1
  B (10¹⁴ /cm²)          3–6            3–6 (as       1–2            ≤ 2
                                        oxide)
  Zr (10¹¹ /cm²)         1–10           1–10          1–10           ≤ 100
```

The PET does not remove boron; it converts it to a water-soluble form. The rinse removes it. Boron that is bonded into the nitride as B–N survives both and sets the floor at about 1 × 10¹⁴ /cm².

### 12.3.3 Alternatives

```
PET options (illustrative):
  Option                    Cl removal   B removal        Plate edge
  ──────────────────────────────────────────────────────────────────────
  H₂O/N₂ remote + rinse     good         good (rinse)     TiOₓ skin; W < 1 nm
  (reference)
  H₂/N₂ remote              good         poor (B stays    benign
                                         as BₓHᵧ/BN)
  O₂ remote                 good         converts to     W oxidized several nm;
                                         B₂O₃            TE edge oxidized
  Rinse only                partial      partial          Cl + water at the edge
                                                         before passivation ✗
```

A rinse without a PET puts water on a chlorinated plate edge, which is exactly the corrosion sequence of Chapter 11. The PET comes first, under vacuum, and the rinse follows.

### 12.3.4 Queue Times

```
Queue-time limits (reference):
  Strip → D1          vacuum transfer (no air)
  D1 → PET            vacuum transfer
  PET → rinse         ≤ 4 h (in N₂-purged FOUP)
  Rinse → ILD         ≤ 24 h
```

---

## 12.4 The Oxide Cap

### 12.4.1 Budget

The 60 nm PE-TEOS cap is the hard mask for the dielectric clear, but it is also exposed during the whole plate conductor etch:

```
Oxide cap budget (reference, illustrative):
  Step                          Oxide rate          Time     Loss
  ────────────────────────────────────────────────────────────────
  Cap open (under resist)       —                   —        0
  W (SF₆/N₂/Cl₂), cap now       ≈ 30 nm/min         15 s     ≈ 7.5 nm
  under resist; resist edge
  pull-back exposes the corner
  SiGe (HBr/Cl₂/O₂, HBr/O₂)     ≈ 3 nm/min          72 s     ≈ 1 nm
  (corner only)                 (corner)
  TiN (Cl₂/Ar, 50 eV)           ≈ 2 nm/min          10 s     ≈ 0.3 nm
  N₂/H₂ strip                   ≈ 0                 —        0
  D1 (BCl₃/Cl₂, 70 eV, 250 °C)  2.0 nm/min          61 s     ≈ 2 nm
                                (full top area)
  Total at the top                                           ≈ 2–3 nm
  Total at the corner (facet)                                ≈ 12 nm
  Remaining                                                  ≥ 48 nm
```

The cap is protected by resist through the conductor steps; only its corner, exposed by resist pull-back, sees them. In D1 the whole cap top is exposed. The loss is small. The cap's thickness is set less by the etch than by what it must do afterwards: it remains under the ILD, and the plate contact must etch through it.

### 12.4.2 If the Cap Fails

W under BCl₃/Cl₂ at 250 °C and 70 eV etches at tens of nanometres per minute. A pinhole in the cap, or a corner eroded through, exposes W to the D1 chemistry: a 61 s step can remove the entire 40 nm of W under the pinhole and start on the SiGe. The resulting crater is a plate-resistance defect and a particle source. Cap pinholes are inspected after the cap deposition, and the corner facet is checked by cross-section when the conductor recipe changes.

---

## 12.5 Inside the Dielectric

### 12.5.1 The Al₂O₃ Insertion

```
The insertion in each route (illustrative):
  Route    Insertion rate          Time to clear 0.3 nm      Relative to ZrO₂
  ──────────────────────────────────────────────────────────────────────────
  D1       7.0 nm/min              2.6 s                     0.78×
  D2       0.08 nm/cycle           3.75 cycles               0.80×
  T        0.06 nm/cycle           5 cycles                  1.2× (tetragonal)
```

The insertion is a speed bump in D1 and D2 and is slightly faster than crystalline ZrO₂ in thermal ALE. In every route, its main role in the clear is as an endpoint marker (Chapter 8).

### 12.5.2 Variant Stacks

```
Variant stacks and their clearing differences (illustrative):
  Stack                              Change in D1 clear
  ──────────────────────────────────────────────────────────────────────
  ZAZ with 0.6 nm Al₂O₃              + 2.6 s; Al marker stronger
  HfO₂/ZrO₂ laminate (HZO)           HfO₂ ≈ 7.5 nm/min: + 10% time
  ZrO₂ with Nb₂O₅ insertion          Nb₂O₅ etches fast (NbCl₅ volatile);
                                     no Al marker; use Nb I lines
  TiO₂ interface layer (0.5 nm)      TiO₂ fast in BCl₃; no change
```

Chapter 14 returns to dielectrics that change the clear more fundamentally.

---

## 12.6 Surfaces Handed to the ILD

```
Surfaces at the start of ILD deposition (reference D1 + PET + rinse):

Surface                Area              State
──────────────────────────────────────────────────────────────────────────────
Periphery SiN          45% of wafer      ≈ 118.7 nm SiN; B 1–2 × 10¹⁴ /cm²;
                                         Cl ≤ 0.8 at%; Zr ≤ 10¹² /cm²;
                                         roughness ≈ 0.4 nm rms
Oxide cap top          55% of wafer      ≈ 48–58 nm PE-TEOS; B and Cl traces
Plate sidewall         147 mm/die        W with < 1 nm WOₓ; SiGe with a thin
                       × 255 nm          oxidized skin; TE TiN with TiOₓ skin,
                                         recessed 1.2 nm; B traces
ZAZ cut face           147 mm/die        Cl in the outer ≈ 1 nm; interface Cl
                       × 5.4 nm          ≈ 8 nm deep along TiN/ZAZ
Bevel                  —                 cleaned separately (Chapter 9)
```

```
Comparison of the surfaces each route leaves (after its own PET, illustrative):
  Route        Periphery residues                     Plate edge
  ──────────────────────────────────────────────────────────────────────────
  R0 cold      C from resist, B, Cl; Zr veils at       ion notching (Book #32)
               the former resist edge
  D1           B, Cl (removed to spec)                 TiN − 1.2 nm, Cl ingress
  D2           B, Cl lower (end on step B: Ar⁺        TiN − 0.4 nm
               leaves a Cl-poor surface)
  Thermal ALE  F (2–5 at%) and Al (AlFₓ, ≈ 10¹⁴ /cm²)  slot; F at the cut face
               from HF and DMAC; PET must remove F
  Hybrid       F from HF; low B, Cl                    1–1.5 nm undercut
```

Thermal ALE trades boron and chlorine for fluorine and aluminium. Fluorine at the SiN surface is removed by the same H₂O-based PET; aluminium fluoride is not water-soluble and stays at about 10¹⁴ /cm², harmless to adhesion but counted in the periphery's metal budget.

---

## Summary and Key Takeaways

1. **Landing loss does not separate the routes.** From 4 nm (cold) to under 0.1 nm (thermal ALE), every route meets the 5 nm specification.

2. **The surface does.** After D1, the nitride carries 3–6 × 10¹⁴ B/cm² and 3–5 at% Cl; untreated, they cause blistering, poor adhesion, edge corrosion, and comb leakage.

3. **PET first, rinse second.** A remote H₂O/N₂ plasma removes chlorine and makes boron soluble; the rinse removes it. Water on a chlorinated edge before the PET starts corrosion.

4. **The cap loses about 2 nm in D1** and about 12 nm at its corner over the whole plate module; a pinhole lets D1 remove the W beneath.

5. **The Al₂O₃ insertion is a speed bump and a marker.** Variant stacks change the clear by seconds and change the endpoint signals.

6. **Each route leaves its own residue signature:** carbon and veils (cold), boron and chlorine (D1, D2), fluorine and aluminium (thermal ALE).

---

## Study Questions

1. Compute the local SiN loss range for D2 (σ_g = 4%, 30% over-cycling, SiN EPC 0.012 nm). Compare with D1.

2. The PET chamber's H₂O flow fails and the PET runs as pure N₂. Predict the surface composition after the rinse and the effect on the plate-edge comb and ILD adhesion.

3. Why is an O₂ PET unacceptable for the reference plate edge? Estimate the W oxidation in 30 s of O₂ downstream plasma at 250 °C if WO₃ grows parabolically with k_p ≈ 1 nm²/s.

4. A cap pinhole 100 nm across exposes W in D1. If W etches at 40 nm/min vertically and 20 nm/min laterally under those conditions, describe the crater after 61 s.

5. The stack changes to an HZO laminate with 0.6 nm Al₂O₃. Recompute the D1 clear time and the overetch time at 70%.

6. List the measurements you would make to qualify a new PET recipe, with the limit for each.

---

**Next Chapter:** [Chapter 13: Damage to the Remaining Dielectric](./13-damage-remaining-dielectric.md)

---

**Chapter 12 Development Status:** Complete  
**Version:** 1.0
