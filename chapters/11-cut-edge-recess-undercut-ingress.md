# Chapter 11: The Cut Edge — Top-Electrode Recess, Undercut & Ingress

## Overview

Everywhere outside the plate, the dielectric clear's job is to remove the ZAZ. At the plate edge, its job is to stop. The ZAZ is cut there, along 147 mm of plate perimeter per die, and the cut face sits directly under the 5 nm TiN top electrode, beneath 150 nm of SiGe, 40 nm of W, and the oxide cap. The conductor sidewall above it is exposed to the plasma for the whole minute of D1. Ions reach it only at grazing incidence; chlorine reaches it freely, and at 250 °C chlorine reacts with TiN, germanium, and tungsten without help.

This chapter follows the plate edge through the dielectric clear: the geometry it starts with, the lateral attack of each conductor and how BₓClᵧ protects against it, the undercut of the dielectric by isotropic routes, the entry of chlorine, boron, and later moisture along the interfaces that the cut exposes, and what all of this means for the plate overlap, the 1.5 µm of plate that lies beyond the last dummy row of the array and that product designers would like to give back.

**Learning Objectives:**
- Describe the plate-edge profile before and after the dielectric clear
- Compute the lateral recess of TE TiN, SiGe, and W in D1 and its dependence on Cl₂ fraction and temperature
- Compare sidewall protection options: BₓClᵧ, nitridation, liners, and lower temperature
- Compute the ZAZ undercut for each route and explain why it forms a slot that the ILD cannot fill
- Estimate chlorine and moisture ingress along the edge and the time scale of edge corrosion
- Build a minimum-overlap budget for the plate edge

---

## 11.1 The Edge Before the Clear

```
Plate edge after the conductor etch and strip (reference, illustrative):

        oxide cap     ┌──────────────── 60 nm, PE-TEOS
        W             │ ╲               40 nm, 84–86°
        SiGe          │  │              150 nm, ≈ 88°; thin SiOₓBrᵧ skin left
                      │  │              by the HBr/O₂ overetch (partly reduced
                      │  │              by the N₂/H₂ strip)
        TE TiN        │  │_             5 nm; vertical face exposed
        ZAZ    ───────┴────────────── 5.4 nm, continuous under and beyond
        top SiN ═══════════════════════
                       ↑
                 plate edge; 1.5 µm beyond the last dummy row
```

Total sidewall height above the ZAZ is about 255 nm, of which 195 nm is conductor. The perimeter of the 32 islands is about 147 mm per die, about 130 m per wafer.

---

## 11.2 Lateral Attack During D1

### 11.2.1 What Reaches the Sidewall

```
Fluxes to the plate sidewall in D1 (illustrative):
  Ions        ≈ 2–5% of the floor flux at grazing incidence (from the ion
              angular spread, ≈ 3–5°), plus reflected ions near the foot
  Cl atoms    ≈ ¼ n v̄ — the same as the floor; isotropic
  BCl₂, BCl   deposit BₓClᵧ where ions do not clean it
```

The sidewall is in the deposition regime for boron and the spontaneous regime for chlorine. Which wins decides the lateral loss.

### 11.2.2 Rates and Recess

```
Lateral attack in D1 (250 °C, 10% Cl₂, 61 s, illustrative):
  Film      Lateral rate    Recess after 61 s    Comment
  ──────────────────────────────────────────────────────────────────────
  W          0.5 nm/min      0.5 nm               W oxide gettered first;
                                                  WClₓ slow below 300 °C
  SiGe       1.0 nm/min      1.0 nm               Ge-rich regions and the
                                                  B-doped foot faster
  TE TiN     1.2 nm/min      1.2 nm               TiCl₄ volatile; thin film,
                                                  fast grain boundaries
  ZAZ edge   ≈ 0.1 nm/min    ≤ 0.3 nm             only after the field clears
                                                  next to the edge (≈ 30 s)
```

The TE TiN recesses about 1.2 nm, the specification allows 3 nm (Chapter 1). The ZAZ edge is barely touched: it is exposed laterally only after the field next to it has cleared, and spontaneous chlorination of ZrO₂ is slow.

### 11.2.3 Sensitivity

```
TE TiN lateral recess over the D1 step (illustrative):
  Condition                      Recess (nm)
  ─────────────────────────────────────────────
  Reference (10% Cl₂, 250 °C)     1.2
  20% Cl₂                         2.8
  30% Cl₂                         5.6   ✗
  10% Cl₂, 200 °C                 0.6   (ZrO₂ rate falls ≈ 30%)
  10% Cl₂, 280 °C                 1.7
  OE 70% → 120%                   1.6
  BCl₃ MFC low by 20%             1.9   (less BₓClᵧ, relatively more Cl)
```

The Cl₂ fraction is the strongest lever: it raises Cl and reduces BₓClᵧ at the same time. A thermal activation energy of about 0.3 eV doubles the TiN recess from 200 to 250 °C, the same interval in which the ZrO₂ rate rises by nearly half. The process sits where the floor gains more than the edge loses.

---

## 11.3 Protecting the Sidewall

```
Sidewall protection options (illustrative):

Option                      How                              Effect / cost
─────────────────────────────────────────────────────────────────────────────────────
BₓClᵧ (reference)           BCl₃-rich chemistry; sidewall    TiN 1.2 nm; free; sensitive
                            in deposition regime             to BCl₃ flow and wall state
Lower Cl₂ (0–5%)            less Cl                          TiN 0.4–0.8 nm; ZrO₂ rate
                                                             − 10 to − 15%
N₂ plasma pre-step          5 s N₂ at low bias before BT:    SiGe lateral ÷ 2; TiN
                            nitrides SiGe and W skins        unchanged (already nitride)
Lower temperature           200 °C                           TiN 0.6 nm; ZrO₂ − 30%;
                                                             selectivity 3 → 2.1
Conformal liner             3 nm ALD AlN or Al₂O₃ after the  sidewall fully protected;
(sidewall spacer)           conductor etch; opened on the    + 1 ALD step; liner on the
                            field by the BT                  field adds ≈ 3 nm to clear
                                                             (Al₂O₃) — same chemistry
```

The liner option deserves a comment. An oxide or nitride liner on the field would have to be removed by the D1 breakthrough before the ZAZ, and a fluorocarbon spacer etch is ruled out because it fluorinates the ZAZ (Chapter 3). A 3 nm ALD Al₂O₃ liner, on the other hand, is cleared by the same BCl₃ chemistry as the ZAZ, adds about 25 s to the clear, and stays on the sidewall because the sidewall receives no ions. It is the most robust protection, and the most expensive. The reference does not need it at 1.2 nm of recess; a product with a thinner TE or a tighter edge might.

---

## 11.4 Dielectric Undercut

### 11.4.1 By Route

```
ZAZ undercut under the TE TiN at the plate edge (illustrative):
  Route                       Top of ZAZ     Bottom of ZAZ    Mechanism
  ──────────────────────────────────────────────────────────────────────────
  R0 cold in-situ             ≈ 0            ≈ 0              directional
  D1 hot (reference)          ≤ 0.3 nm       ≈ 0.1 nm         spontaneous Cl,
                                                              reflected ions
  D2 plasma ALE               ≈ 0.1 nm       ≈ 0              self-limited
                                                              surface reaction
  Hybrid (damaged + HF)       1–1.5 nm       ≈ 0.5 nm         wet on damaged face
  Thermal ALE, 139 cycles     7.0 nm         1.6 nm           isotropic
  Thermal ALE, 190 cycles     9.6 nm         4.2 nm           isotropic (Ch. 10)
```

### 11.4.2 The Slot

An isotropic undercut leaves a slot between the TE TiN and the top SiN, 5.4 nm tall and as deep as the undercut, running along the entire plate perimeter:

```
Plate edge after thermal ALE (190 cycles), not to scale:

        SiGe     │
        TE TiN   │___________                5 nm, now overhanging
                  ← 9.6 nm →  ZAZ ────────   cut face recessed
        slot     ░░░░░░░░░░                  5.4 nm tall
        top SiN  ═══════════════════════
```

No ILD deposition fills a slot 5 nm tall and 10 nm deep: high-density-plasma oxide pinches at the opening, flowable oxide wets it partly and shrinks on curing. The slot stays as a void along 147 mm per die. By itself it is electrically harmless: there is no storage node under the plate edge, and the void is in the dielectric between the TE and the nitride. It matters as a path: moisture and chemistry that reach it travel along the perimeter and toward the interface between the TE and the ZAZ (Section 11.5).

### 11.4.3 Sealing

```
Slot sealing after an isotropic clear (illustrative):
  ALD Al₂O₃ or SiN, 3 nm     fills a 5.4 nm slot from both faces (2.7 nm
                             each); seals the TE edge and the cut face;
                             adds a deposition step; Al₂O₃ also lies on the
                             periphery and must not be thick enough to stop
                             the contact etch (3 nm is a problem: see below)
  ALD SiN, 3 nm              seals; is removed by the contact etch with the
                             top SiN; preferred
```

An Al₂O₃ seal would recreate the problem the clear just solved: a refractory film on the periphery under the contacts. The seal must be a material the contact etch removes. SiN is the natural choice.

---

## 11.5 Ingress

### 11.5.1 Chlorine and Boron During the Clear

```
Chlorine uptake at the plate edge (illustrative):
  Into the TE TiN sidewall      ≈ 2–4 at% in the outer 1–2 nm (TiClₓ, TiOClₓ)
  Along the TiN/ZAZ interface   interfacial diffusion D_i ≈ 10⁻¹⁴ cm²/s at
                                250 °C → √(D_i t) over 61 s ≈ 8 nm
  Into the ZAZ cut face         ≈ 1 nm (ZrClₓ, ZrOClₓ)
  Boron                         BₓClᵧ film on the sidewall, ≈ 0.3–0.5 nm
```

The PET (H₂O/N₂ remote plasma) converts most surface chlorine to HCl and boron to oxide that the rinse removes (Chapter 12). The chlorine that has diffused 8 nm along the interface is not reached by a 30 s surface treatment; it remains.

### 11.5.2 Later: Moisture and Corrosion

The chlorine left at the edge becomes a problem only when water arrives. Water can arrive during the rinse after the PET, during queue time in a humid FOUP, and during the early stages of ILD deposition before the edge is sealed:

```
Edge corrosion sequence (illustrative):
  1. H₂O adsorbs at the cut edge and in any slot
  2. Residual Cl forms HCl locally; TiN oxidizes to TiO₂ at the edge
     (molar volume × 1.6: stress, possible delamination of the TE edge)
  3. Oxidation front moves along the TiN/ZAZ interface, faster where Cl is
  4. In the ILD deposition (≈ 400 °C) the front grows by thermal oxidation
     until the edge is sealed

Lateral extent (illustrative, reference D1 + PET + rinse + ILD):
  Typical                 10–30 nm of TE oxidation from the edge
  With a slot and a       50–100 nm
  long humid queue
```

Against a 1.5 µm overlap, 100 nm is a small fraction. The first dummy row is untouched, and the first real capacitor is farther still.

### 11.5.3 The Plate-Edge Comb

```
Plate-edge comb (monitor structure, illustrative):
  Two plate islands with interdigitated edges, 1 µm apart, total facing
  edge length 10 mm, on periphery SiN; measured after the first metal
  Test            plate A to plate B at 1.1 V, 85 °C
  Limit           ≤ 1 pA per mm of facing edge (≤ 10 pA total)
  Sensitive to    B and Cl residues on the cleared SiN (surface conduction
                  between the edges), TE edge oxidation, edge damage
```

The comb is the electrical check that the edge and the surface between edges are clean. A rise in comb leakage with no rise in contact opens points to surface residues (boron, chlorine) rather than to dielectric residue (Chapter 12).

---

## 11.6 How Small Can the Overlap Be?

The plate extends 1.5 µm beyond the last dummy row. Every micrometre of overlap on 147 mm of perimeter is about 0.15 mm² per die, roughly 0.2% of the die. Designers would like to reduce it to about 0.4 µm:

```
Minimum overlap budget (illustrative, 3σ where applicable):
  Item                                        Allowance (nm)
  ───────────────────────────────────────────────────────────
  Plate-to-array overlay                       30
  Plate CD and edge placement                  40
  Edge profile (W taper, SiGe foot)            20
  TE TiN recess (D1)                           3
  ZAZ undercut (D1 / thermal ALE)              0.3 / 10
  Edge oxidation and Cl ingress                100
  Edge damage reach (Chapter 13)               100
  Dummy-row region to protect                  ≈ 1 dummy pitch (45)
  Sum, linear                                  ≈ 340 / 350
  Proposed overlap                             400
```

A 0.4 µm overlap appears feasible for D1 and D2 with today's ingress and damage reach. For thermal ALE, the undercut itself is small against the budget, but the slot raises the ingress term, so the route needs the SiN seal of Section 11.4.3 to qualify. The two largest items are ingress and damage reach, and both are uncertain at the factor-of-two level. The overlap reduction is approved on electrical data from the comb, the array-edge capacitors, and retention at the array boundary, not on this budget.

---

## Summary and Key Takeaways

1. **The plate sidewall sees chlorine, not ions.** In D1 it loses about 1.2 nm of TE TiN, 1.0 nm of SiGe, and 0.5 nm of W, held down by BₓClᵧ and a 10% Cl₂ fraction.

2. **The Cl₂ fraction is the strongest edge lever.** 20% more than doubles the TiN recess; 30% violates the specification.

3. **The cut face of the ZAZ is barely touched in directional routes** (≤ 0.3 nm) and undercut by 7–10 nm in thermal ALE, leaving a slot no ILD fills.

4. **Seal slots with a material the contact etch removes.** ALD SiN, not Al₂O₃.

5. **Chlorine goes 8 nm along the TiN/ZAZ interface during D1** and enables 10–100 nm of edge oxidation when moisture arrives.

6. **A 0.4 µm overlap appears feasible.** Ingress and damage reach dominate the budget; electrical data decide.

---

## Study Questions

1. Compute the TE TiN recess for D1 with a 90% overetch and 15% Cl₂. Does it meet the specification?

2. An ALD Al₂O₃ liner 3 nm thick is added for sidewall protection. Compute the added clearing time in D1 and the added SiN loss with the same 70% overetch on the longer clear. Is the liner removed from the plate cap top?

3. Derive the undercut at the top and bottom of the ZAZ for an isotropic process that removes a total thickness 1.5 × t_f. Why is the undercut at the bottom smaller?

4. Estimate the total slot volume per die for a 9.6 nm × 5.4 nm slot along 147 mm. If it filled with water at the rinse, how many Cl atoms (at 1 × 10¹⁴ /cm² on the slot walls) could it dissolve, and at what concentration?

5. The product team proposes 0.25 µm of overlap. Which items of the budget in Section 11.6 must shrink, and what experiments would show that they have?

6. Explain why a rise in plate-edge comb leakage without a rise in contact opens points to the cleared SiN surface rather than to the ZAZ edge.

---

**Next Chapter:** [Chapter 12: Selectivity & the Materials Around the Dielectric](./12-selectivity-surrounding-materials.md)

---

**Chapter 11 Development Status:** Complete  
**Version:** 1.0
