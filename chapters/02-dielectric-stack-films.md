# Chapter 2: The Dielectric Stack — Films, Phases, Interfaces & Wrap

## Overview

An etch inherits everything about the film it removes: its thickness and the variation of that thickness, its composition layer by layer, its crystal phase and grain structure, the interfaces above and below it, and where on the wafer it was deposited. For the capacitor dielectric, each of these is unusual. The film is a laminate of two oxides with very different etch behaviour. It changes phase during the module, from mostly amorphous when the bevel is etched to fully tetragonal when the periphery is cleared. Its grains are as wide as the film is thick times five, and their boundaries etch faster than their interiors. It sits on TiN that it has partly oxidized, under TiN that has partly reduced it. And it covers the bevel and part of the backside, where nobody intended it to be.

This chapter describes the reference ZAZ stack and its relatives, how it is deposited and crystallized, what happens at its interfaces, where it ends up on the wafer edge, and the incoming variations each of the three etches must absorb.

**Learning Objectives:**
- Describe the layers of the ZAZ stack and the purpose of each
- Compute EOT from layer thicknesses and permittivities, and the EOT change from a trim
- Explain how crystallization changes etch rate, grain structure, and leakage, and why it depends on layer thickness
- Describe the bottom and top interfaces and what the top-electrode deposition does to the dielectric
- Sketch the thickness profile of the dielectric over the bevel and backside
- List the incoming variations at each dielectric etch

---

## 2.1 The ZAZ Stack

### 2.1.1 Layers

```
Reference capacitor dielectric (on the TiN pillar, outward):

  TiN storage node (Book #32)
  ── TiOₓNᵧ interfacial layer       ≈ 0.4 nm   formed by O₃ during the first
                                               ZrO₂ cycles; partly conductive
  ── ZrO₂ (bottom)                  2.6 nm     ≈ 29 ALD cycles
  ── Al₂O₃ insertion                0.3 nm     3 ALD cycles
  ── ZrO₂ (top)                     2.6 nm     ≈ 29 ALD cycles
  ── TiN top electrode (TE)         5.0 nm     ALD, TiCl₄/NH₃, 400 °C
  Total dielectric                  5.5 nm     (interfacial layer counted with
                                               the electrode)
```

**ZrO₂** provides the permittivity: about 40–47 in its tetragonal phase, 20–25 in its monoclinic phase, and 20–25 when amorphous. **Al₂O₃** has a permittivity of only about 9, but it does three jobs. It interrupts the columnar grains of the ZrO₂, so that no grain boundary runs straight from one electrode to the other. It raises the conduction-band offset in the middle of the stack. And it slows the growth of monoclinic grains. Three ALD cycles, about one monolayer, are enough; the layer is partly intermixed with the ZrO₂ on either side and behaves more like a sheet of Al dopant than a separate film.

### 2.1.2 Deposition

```
ZrO₂ ALD:   CpZr(NMe₂)₃ / O₃, 300 °C;  ≈ 0.09 nm per cycle
Al₂O₃ ALD:  Al(CH₃)₃ (TMA) / O₃, 300 °C;  ≈ 0.10 nm per cycle
Cycle time: ≈ 10–20 s in a single-wafer chamber with long exposures for the
            1.5 µm-deep forest; ≈ 61 cycles in all, ≈ 15 min per wafer
Impurities: C ≈ 0.5 at%, H ≈ 1–2 at%, N < 0.5 at%
```

The long exposures are set by the array: the oxidant and the precursor must saturate the surface at the bottom of a channel 1.5 µm deep and about 20 nm across before the dielectric is deposited (Chapter 12 develops the same transport for the etch).

### 2.1.3 EOT

The layers add as capacitors in series:

```
EOT = 3.9 Σ tᵢ/kᵢ

Reference (crystallized):
  ZrO₂  5.2 nm / k ≈ 48 (tetragonal, 2.6 nm layers; §2.2.2)     0.42 nm
  Al₂O₃ 0.3 nm / k ≈ 9 (intermixed; effective)                  0.13 nm
                                                         EOT  ≈ 0.55 nm
  Measured from C–V on capacitor arrays:                        0.50 nm
  Equivalent single-film k_eff = 3.9 × 5.5 / 0.50               ≈ 43
```

The measured value is about 10% below the layer sum, which is typical: the "Al₂O₃" is not a pure film but Al-doped ZrO₂ with a higher effective permittivity, and the TiOₓNᵧ interface and electrode screening are not well described by a series of ideal layers. Relative changes in the layer sum track relative changes in the measured EOT well, and that is how this book uses it. This book uses the measured k_eff ≈ 43 and EOT = 0.50 nm throughout.

### 2.1.4 Relatives

```
Dielectric variants in production and development (illustrative):

  Stack                         t (nm)   EOT (nm)   Etch-relevant difference
  ────────────────────────────────────────────────────────────────────────────
  ZAZ (reference)               5.5      0.50       ZrO₂ chlorides, Al marker
  ZAZA / ZAZAZ laminates        5.5–6    0.50–0.55  more Al₂O₃ interfaces; more
                                                    endpoint markers
  HZH (HfO₂/ZrO₂/HfO₂)           5.5      0.55       Hf: heavier, slower in BCl₃
  Al-, La-, or Y-doped ZrO₂     5–6      0.45–0.5   dopant halides (LaCl₃, YCl₃)
                                                    non-volatile at 60 °C
  ZrO₂ on TiO₂ / rutile TiO₂    6–8      0.35–0.45  TiCl₄ very volatile; TiO₂
                                                    etches fast
  SrTiO₃ (STO)                  8–10     0.3–0.4    SrCl₂ non-volatile; Sr is
                                                    the problem
```

Chapter 14 treats the alternatives. The rest of the book uses ZAZ.

---

## 2.2 Phases and Grains

### 2.2.1 Crystallization

As deposited at 300 °C on TiN, ZrO₂ is mostly amorphous with crystalline nuclei. It crystallizes into the tetragonal phase as the stack is heated:

```
Crystalline fraction of the ZAZ through the module (illustrative):

  Step                               T (°C)   Tetragonal fraction   Note
  ───────────────────────────────────────────────────────────────────────────
  ZAZ ALD                            300      ≈ 20%                 nuclei on TiN
  TE TiN ALD                         400      ≈ 60%                 module 1 sees this
  SiGe:B LPCVD (≈ 2 h)               425      ≈ 95%                 module 2 sees this
  Pilot PDA, N₂ (module 3 only)      420      ≈ 90% (6.5 nm stack)  before the trim
```

The tetragonal phase gives the high permittivity. The monoclinic phase, which forms if grains grow large or the film is too thick, does not. Al₂O₃ insertion and the moderate temperatures keep the film tetragonal.

### 2.2.2 Thickness-Dependent Crystallization

The temperature at which a ZrO₂ layer crystallizes rises as the layer gets thinner, because the energy of the interfaces is a larger share of the total. Below about 3 nm per layer, a 425 °C anneal leaves part of the film amorphous:

```
Crystallinity and permittivity of one ZrO₂ layer after 425 °C (illustrative):

  Layer thickness    Tetragonal fraction    k (layer)
  ──────────────────────────────────────────────────────
  2.0 nm             ≈ 70%                  ≈ 38
  2.6 nm             ≈ 90%                  ≈ 48
  3.6 nm             ≈ 98%                  ≈ 55
```

This is the physics behind module 3 (Chapter 12): a top ZrO₂ layer deposited at 3.6 nm, crystallized, and then trimmed to 2.6 nm keeps the crystal structure it formed at 3.6 nm.

### 2.2.3 Grains and Boundaries

```
Grain structure of the crystallized ZAZ (illustrative):
  Lateral grain size          10–30 nm (median ≈ 20 nm)
  Grain shape                 columnar through each ZrO₂ layer; the Al₂O₃
                              insertion restarts nucleation
  Boundary width              ≈ 0.5 nm; lower density, O-deficient
  Boundary area fraction      ≈ 5% of the surface
```

The grain boundaries matter to every etch in this book. They etch faster than grain interiors in a continuous chlorine-based etch and in wet chemistry, so the last material to clear is grain interiors (Chapter 10). They are the preferred leakage paths, so an etch that thins them more than the grains raises leakage tails (Chapter 12). And they are where halogens and boron diffuse in from an exposed edge (Chapter 11).

---

## 2.3 The Interfaces

### 2.3.1 Bottom: TiN Storage Node

The first ZrO₂ cycles expose the TiN surface to ozone. About 0.4 nm of TiOₓNᵧ forms. It is conductive enough to count as part of the electrode, but it is the source of oxygen vacancies at the bottom of the ZrO₂ and of the asymmetry of leakage with polarity. No etch in this book reaches it, except where a trim or a clearing etch reaches the bottom of the dielectric: at the periphery, where the dielectric lies on SiN and there is no bottom electrode, and at the pillar tops, which are covered by the full stack.

### 2.3.2 Top: TiN Top Electrode

The TE TiN is deposited by ALD from TiCl₄ and NH₃ at 400 °C. Two things happen to the dielectric:

1. **Oxygen scavenging.** Ti at the interface draws oxygen from the top ZrO₂, leaving vacancies within the first nanometre. These raise leakage and are partly healed by later anneals.
2. **Chlorine.** The TE carries about 1 at% Cl; some reaches the ZrO₂ surface.

The TE is the first film over the dielectric everywhere. In module 1, the bevel plasma must remove it before it can reach the ZAZ. In module 2, it is cleared from the periphery by a short Cl₂ step that lands on the ZAZ (Chapter 3, Section 3.6).

### 2.3.3 What the Plate Fill Does

The SiGe:B plate fill (425 °C, about 2 h in a batch furnace) completes the crystallization and introduces hydrogen from the silane and germane. Hydrogen passivates some vacancies and creates others; its net effect on the dielectric is mildly beneficial. More important to this book: the plate fill fixes the dielectric's phase, so module 2 always clears tetragonal ZAZ, and module 1, which precedes it, always etches partly amorphous ZAZ.

---

## 2.4 Where the Dielectric Lies in the Periphery

```
Periphery cross-section at the start of module 2 (not to scale):

         resist (KrF, ≈ 360 nm left)
         ┌──────────────────────┐
         │ W 40 nm              │
         │ SiGe:B 150 nm        │
         ├──────────────────────┤ ← plate edge (Book #32 conductor steps
   ══════╪════ TE TiN 5 nm ═════╪═══════════════════  land on the TE TiN)
   ──────┴─── ZAZ 5.5 nm ───────┴───────────────────
   ▓▓▓▓▓▓▓▓▓▓▓ top SiN, 120 nm ▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓
   ░░░░░░░░░░░ periphery mold oxide ░░░░░░░░░░░░░░░░░
      array side                         periphery side
```

The periphery top SiN stands at the same height as the top support of the array, over the periphery mold oxide that the dip-out of Book #30 did not remove. The ZAZ on it is flat. It is the same film, with the same thickness and phase, as on the pillars, but it lies on SiN rather than on TiN, so it has no TiOₓNᵧ interface and its first ZrO₂ cycles nucleate differently. Grain size on SiN is similar; the bottom 0.5 nm is slightly less crystalline.

The resist that defines the plate has already been thinned by Book #32's W and SiGe steps. About 360 nm remains when module 2 begins.

---

## 2.5 Conformality in the Array

The ALD step coverage in the reference forest is about 97% from the top of the channel to the bottom. The thickness at the bottom of the pillars is about 5.35 nm, at the top 5.5 nm. For module 3, which thins the film inside the same channels by thermal ALE, the deposition step coverage and the etch step coverage multiply (Chapter 12):

```
Final thickness at depth z = t_dep(z) − Δt_trim(z)

Pilot, bottom of the channel:
  t_dep = 6.5 × 0.97 = 6.31 nm;  Δt_trim = 1.0 × 0.92 = 0.92 nm  →  5.39 nm
Top:
  t_dep = 6.50 nm;               Δt_trim = 1.00 nm               →  5.50 nm
```

An etch that is less conformal than the deposition partly cancels the deposition's top-heavy profile; one that is more top-heavy than the deposition makes the profile worse.

---

## 2.6 The Wafer Edge: Where the Film Wraps

### 2.6.1 The Edge Profile

```
300 mm wafer edge (SEMI-standard profile, simplified):

     front surface ─────────────────────────────┐ r = 149.6 mm (front shoulder)
                                                  \  front bevel facet
                                                   │ apex, r = 150.0 mm
                                                  /  back bevel facet
     back surface  ─────────────────────────────┘ r = 149.6 mm (back shoulder)

  Wafer thickness 775 µm; bevel facets ≈ 22°; apex radius ≈ 200 µm
  Die exclusion: last full die ends at r ≈ 147 mm
```

### 2.6.2 Thickness of the Dielectric Around the Edge

ALD reaches every surface the gases reach. In a single-wafer ALD chamber, the wafer sits on a heated susceptor with a recess or pins; an edge purge of inert gas under the wafer limits how far precursor diffuses onto the backside, and a sealing ring stops it:

```
ZAZ thickness around the edge (reference ALD chamber, illustrative):

  Location                          r (mm)          ZAZ (nm)    TE TiN (nm)
  ──────────────────────────────────────────────────────────────────────────
  Front, inside the last die        < 147           5.5         5.0
  Front ring                        148.8–149.6     5.5         5.0
  Front bevel facet                 149.6–150       5.4         4.8
  Apex                              150             5.2         4.5
  Back bevel facet                  150–149.6       4.5         3.5
  Backside ring                     149.6 → 147.6   4.0 → 0.3   3.0 → 0.2
  Backside, inside the seal         < 147.5         ≈ 10⁻⁵ nm   trace
                                                    (10⁹–10¹⁰ Zr/cm²
                                                    by leakage past the
                                                    seal)
```

The backside film tapers over about 2 mm and ends at the seal. Module 1 must therefore clear the dielectric from the front ring, the facets, the apex, and the backside ring out to r = 147.0 mm, a little inside the seal, so that the full taper is removed.

### 2.6.3 What Lies Under the Dielectric at the Edge

```
Under the ZAZ at the edge (reference):
  Front ring       top SiN of the support (the storage-node TiN was removed
                   from the bevel after the fill; Book #32, Ch. 9)
  Bevel facets     mixed: SiN, oxide, and bare Si where earlier bevel etches
                   cleared everything
  Backside ring    LPCVD SiN and oxide left from earlier furnace steps
```

These films matter to module 1 in two ways. They set what the bevel plasma lands on, and they set the adhesion of the dielectric: ZAZ on bare silicon at the apex adheres well; ZAZ on a rough, partly etched SiN facet adheres less well and is where peeling begins if the bevel film is left (Chapter 11).

---

## 2.7 Incoming Variation at Each Etch

```
MODULE 1 (bevel)
──────────────────────────────────────────────────────────────────────────────
Variable                        Typical range           Consequence
──────────────────────────────────────────────────────────────────────────────
ZAZ on backside ring            4.0 ± 0.6 nm at the     backside clearing time
                                shoulder                 (Chapter 7)
Wrap extent (seal position,     ± 0.3 mm                 residual ring if it reaches
edge purge)                                              past r = 147.0 mm
Wafer centring in the ALD tool  ± 0.2 mm                 eccentric wrap
Crystalline fraction            50–70%                   rate ± 10%
TE TiN on the bevel             3–5 nm                   TiN step time

MODULE 2 (periphery clear)
──────────────────────────────────────────────────────────────────────────────
ZAZ thickness, within wafer     5.5 nm ± 1.5% (3σ)       clearing-time map (Ch. 6)
ZAZ thickness, lot to lot       ± 0.05 nm                feed-forward (Ch. 15)
Al₂O₃ position and amount       3 cycles ± 0            Al marker timing (Ch. 8)
Tetragonal fraction             93–97%                   rate ± 3%
TE TiN thickness                5.0 ± 0.3 nm             TiN clear time
Resist remaining                360 ± 25 nm              resist budget (Ch. 10)
Plate-edge profile              85–89° (Book #32)        TE foot, ZAZ edge exposure
Periphery top SiN               120 ± 3 nm               landing margin

MODULE 3 (in-array trim, pilot)
──────────────────────────────────────────────────────────────────────────────
Deposited ZAZ                   6.5 nm ± 1.5% (3σ)       final thickness spread
Step coverage, deposition       96–98%                   bottom thickness
Tetragonal fraction, top ZrO₂   95–99%                   trim rate, boundary attack
Channel radius at the top       3.7 ± 0.5 nm             reactant transport (Ch. 12)
(after deposition)
Surface state after PDA         OH coverage, C          first-cycle etch amount
                                contamination
```

---

## Summary and Key Takeaways

1. **ZAZ is a laminate.** Two ZrO₂ layers give the permittivity; a monolayer of Al₂O₃ breaks the columns and the leakage paths, and gives the endpoint a marker.

2. **The phase changes during the module.** Module 1 etches ZAZ that is about 60% crystalline; module 2 etches ZAZ that is fully tetragonal; module 3 trims a film crystallized at its deposited thickness.

3. **Thin layers crystallize poorly.** Below about 3 nm per layer, the tetragonal fraction and the permittivity fall. Deposit thick and trim is the pilot's answer.

4. **Grain boundaries are fast, leaky, and permeable.** They etch first, leak most, and carry halogens and boron in from exposed edges.

5. **The dielectric wraps the edge.** It covers the apex and tapers over 2 mm onto the backside to the ALD seal. Module 1 must remove it out to r = 147.0 mm.

6. **Each etch inherits a different set of variables.** Backside wrap for module 1; thickness, phase, and resist for module 2; step coverage and channel radius for module 3.

---

## Study Questions

1. Compute the EOT of a ZAZ stack with ZrO₂ 2 × 2.6 nm at k = 48 and Al₂O₃ 0.3 nm at k = 9. Compare it with the measured 0.50 nm and suggest two physical reasons for the difference.

2. The pilot flow deposits ZrO₂ 2.6 / Al₂O₃ 0.3 / ZrO₂ 3.6 nm and trims 1.0 nm from the top layer. Using the permittivities in Section 2.2.2, compute the EOT before and after the trim, assuming the trimmed top layer keeps k = 55. What is the capacitance gain over the reference at equal physical thickness?

3. The ALD seal moves outward by 0.5 mm so that the backside taper ends at r = 148.1 mm. How does that change the radius to which module 1 must clear the backside? What happens if the seal moves inward by 0.5 mm instead?

4. Grain boundaries cover 5% of the surface and etch 30% faster than grain interiors in a continuous chlorine etch. When the average film has 1 nm left, how much thinner is the film at the boundaries, assuming 4.4 nm has been removed? Where is the last material?

5. Using the step coverages in Section 2.5, compute the final thickness at the bottom of the channel if the trim's step coverage falls to 0.80. By how much does the capacitance per unit area differ between top and bottom?

6. Explain why module 1 always etches a partly amorphous film and module 2 a tetragonal one. What would change in module 1's recipe if the bevel removal were moved after the SiGe fill?

---

**Next Chapter:** [Chapter 3: Halide Plasma Chemistry of High-k Oxides](./03-high-k-halide-plasma-chemistry.md)

---

**Chapter 2 Development Status:** Complete  
**Version:** 1.0
