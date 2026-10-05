# Chapter 14: Advanced Dielectrics & Architectures

## Overview

ZAZ has carried DRAM capacitors through several generations, and it is near its limit. Below an EOT of about 0.45 nm, its leakage rises faster than its capacitance, and every remaining nanometre of physical thickness is needed to hold the femtoampere. The industry's answers are of two kinds: **new dielectrics** with higher permittivity, and **new architectures** that change where the capacitor sits and how much periphery surrounds it. Both change the dielectric etches.

A new dielectric changes the chemistry: some of the candidates contain metals whose chlorides volatilize easily (titanium), some whose chlorides never volatilize (strontium, lanthanum, yttrium), and some whose function depends on a crystal phase that an etch can disturb (antiferroelectric and ferroelectric hafnium–zirconium oxide). A new architecture changes the geometry: 4F² cells shrink the channels between pillars; wafer-bonded designs move the periphery to another wafer; 3D DRAM lays the capacitors on their sides and puts the dielectric on surfaces that no directional etch can reach. This chapter takes each in turn and asks what happens to the three modules.

**Learning Objectives:**
- Predict the etch behaviour of HfO₂/ZrO₂ laminates, La- and Y-doped ZrO₂, TiO₂, and SrTiO₃ from the volatility of their halides
- Design a clearing route for a dielectric containing a metal with a non-volatile chloride
- Explain how etch damage interacts with the phase of antiferroelectric and ferroelectric HZO
- Describe how 4F² cells and wafer bonding change the trim and the periphery clear
- Describe the lateral dielectric recess of 3D DRAM and the isotropic etch it requires

---

## 14.1 Why the Dielectric Changes

```
Dielectric roadmap (illustrative):

  Generation   EOT (nm)    Dielectric                       Electrodes
  ─────────────────────────────────────────────────────────────────────────
  1x–1b        0.55–0.50   ZAZ, ZAZA                        TiN / TiN
  1c           0.45–0.48   ZAZ with trim; HZH; doped ZrO₂   TiN / TiN
  1d and       0.35–0.42   TiO₂-based on Ru; AFE HZO;       Ru, Mo, NbN
  beyond                   SrTiO₃ (research)
```

---

## 14.2 HfO₂/ZrO₂ Laminates and Doped ZrO₂

### 14.2.1 Hafnium

Hafnium behaves like zirconium in every chemical respect that matters here. HfCl₄ volatilizes like ZrCl₄; HfF₄ does not. HfO₂ etches about 15% slower than ZrO₂ in the main step and 10% slower in the ALE (Chapters 3 and 4). An HZH stack (HfO₂/ZrO₂/HfO₂) has no Al₂O₃ insertion, so it has no Al marker: the main step must use the Hf/Zr emission ratio, which changes as the etch front passes from the top HfO₂ into the ZrO₂, but much less sharply than the Al line rises (Chapter 8).

### 14.2.2 Dopants With Non-Volatile Chlorides

Lanthanum, yttrium, and similar dopants stabilize the tetragonal or cubic phase and raise permittivity. Their chlorides do not volatilize:

```
La-doped ZrO₂, 3 at% La (of cations), 5.5 nm (illustrative):
  La in the film                       ≈ 0.03 × 1.5 × 10¹⁶ ≈ 4.5 × 10¹⁴ /cm²
  As the Zr leaves as ZrCl₄, La stays as LaClₓ on the receding surface
  La left on the periphery after a      ≈ 1–3 × 10¹⁴ /cm² (0.2–0.4 monolayer)
  BCl₃ main step + ALE
```

A fraction of a monolayer of scattered La does not block contacts: the fluorocarbon contact etch removes the SiN beneath scattered atoms. But a La-rich surface is a contamination source, and at higher doping it forms a continuous crust that does block them. The rescue is simple: **LaCl₃ dissolves in water.** The O₂/H₂O strip and the DIW rinse of Chapter 10 remove most of it; a dilute HCl rinse removes the rest. For dopants whose chlorides do not dissolve readily, the route must be redesigned.

---

## 14.3 TiO₂-Based Dielectrics

### 14.3.1 The Material

Rutile TiO₂, grown on a Ru or RuO₂ electrode that templates the rutile phase, has a permittivity of 80–100. Undoped, it leaks too much; Al-doped TiO₂ and TiO₂/ZrO₂ stacks bring the leakage down while keeping EOT near 0.4 nm.

### 14.3.2 Etch Chemistry

```
TiO₂ versus ZrO₂ (illustrative, BCl₃/Cl₂/Ar, 60 °C):

                          ZrO₂ (tetragonal)    TiO₂ (rutile)
  ─────────────────────────────────────────────────────────
  Chloride volatility     1 Torr at 190 °C     1 Torr at −14 °C
  ΔH with BCl₃            −191 kJ/mol          −130 kJ/mol
  E₀ (net-zero energy)    ≈ 60 eV              ≈ 25 eV
  Main-step rate, 150 eV  6 nm/min             ≈ 25 nm/min
  ALE EPC                 0.10 nm              ≈ 0.25 nm (less self-limited)
  Selectivity to SiN      0.75                 ≈ 3
```

TiO₂ is easy to remove, because its chloride leaves on its own. The periphery clear becomes shorter and its tail narrower. The difficulties move elsewhere: the Ru top electrode must be etched in O₂/Cl₂ (RuO₄ is volatile) in the conductor steps, and that oxygen-rich chemistry oxidizes the edge of the TiO₂ and the Ru bottom electrode where they are exposed; and Ti from the dielectric is now indistinguishable, in the emission spectrum, from Ti from any TiN electrode or liner.

### 14.3.3 The Bevel

TiO₂ on the bevel is removed in seconds. Ru on the bevel is not: Ru is a contamination concern of its own, and its bevel removal (O₂/Cl₂, or wet ceric-ammonium-nitrate edge rinse) becomes the hard part of module 1.

---

## 14.4 SrTiO₃

SrTiO₃ (STO) has a permittivity of 100–300 in films thick enough to be crystalline, and has long been the high-k dielectric of research DRAM capacitors. It is the hardest material in this book to etch:

```
SrTiO₃ in BCl₃/Cl₂ (illustrative):
  Ti leaves as TiCl₄
  Sr stays: SrCl₂ (boils at 1250 °C)
  Result: an SrCl₂-rich crust grows as the etch proceeds and stops it

Removal of the Sr:
  Physical sputtering   Ar⁺ yield of SrCl₂ at 150 eV ≈ 0.1; slow, and the
                        sputtered Sr redeposits
  Water                 SrCl₂ is very soluble: a DIW or dilute HCl rinse
                        dissolves the crust in seconds
```

The natural route is a **cyclic dry–wet clear**: a BCl₃/Cl₂ step removes titanium and converts the surface to SrCl₂; a water rinse dissolves it; repeat. Each cycle removes about 2 nm. In a single-wafer tool that combines a dry chamber and a wet module, a 10 nm STO film clears in about five cycles. The bevel needs the same treatment, and Sr contamination limits (Sr is an alkaline-earth metal and a fast surface migrant on oxides) make a wet bevel rinse mandatory, not a fallback.

---

## 14.5 Antiferroelectric and Ferroelectric HZO

### 14.5.1 Why Phase Matters

Hafnium–zirconium oxide (Hf₁₋ₓZrₓO₂) can be paraelectric, antiferroelectric (AFE), or ferroelectric (FE), depending on composition, thickness, stress, electrodes, and defects. ZrO₂-rich AFE films show a field-induced transition that raises the effective permittivity near the operating voltage; FE films store charge in their polarization and are candidates for non-volatile DRAM-like memories. In both, the useful property depends on a metastable crystal phase.

### 14.5.2 What the Etches Can Do

```
Etch effect on AFE/FE HZO (illustrative):

  Effect                          Cause                             Consequence
  ──────────────────────────────────────────────────────────────────────────────
  Oxygen vacancies at exposed     BCl₃ getters oxygen at the        domain pinning;
  edges                           surface (the same chemistry       wake-up and
                                  that etches it)                   imprint
  Hydrogen and fluorine           strip water; thermal ALE HF       phase shift towards
                                                                    the monoclinic or
                                                                    tetragonal phase
  Trapped charge from             plasma charging through the       imprint (shifted
  charging                        plate                             hysteresis)
  Thinning by a trim              module 3                          phase depends on
                                                                    thickness: a trim
                                                                    can change it
```

The trim of Chapter 12 relies on the top layer keeping the phase it formed at its deposited thickness. For ZAZ that is a safe assumption; for HZO, whose phase balance shifts with thickness and stress, a trimmed film may relax into a different phase on the next anneal. AFE and FE capacitors are therefore the least suited to a trim and the most sensitive to edge and charging damage.

---

## 14.6 4F² and Wafer-Bonded DRAM

### 14.6.1 Smaller Channels

A 4F² vertical-channel cell places the capacitor directly above a vertical transistor. The capacitor array is still a forest of pillars, at a smaller pitch:

```
Illustrative 4F² capacitor array:
  Pitch ≈ 36 nm (square or hexagonal); pillar CD ≈ 22 nm at the top
  Channel radius before the dielectric ≈ 9 nm (hexagonal) at the top
  ZAZ 5.5 nm → channel radius 3.5 nm → TE TiN at the bottom ≈ 3.5 nm
```

At this pitch, even the reference ZAZ leaves too little room for the top electrode. The options are a thinner dielectric of higher permittivity (Sections 14.3–14.5), a thinner top electrode of a better metal, or a trim that recovers the channel. The arithmetic of Chapter 12 becomes a necessity rather than an option.

### 14.6.2 Less Periphery

In wafer-bonded designs, the periphery circuits are built on a separate wafer and bonded to the cell-array wafer. The cell wafer has only array blocks, their edges, scribe lines, and bonding-pad regions. The periphery clear then removes the dielectric from perhaps 10% of the wafer rather than 45%:

```
Effects of a 10% exposed area (illustrative):
  ZrO₂ products per second           ≈ 1/4.5 of the reference
  Al-marker and ALE-curve signals    ≈ 1/4.5; nearer the detection floor
  Main-step rate                     slightly higher (less loading)
  Contacts that must land cleanly    plate contacts, through-array vias,
                                     bonding-pad vias: far fewer than 3 × 10⁷,
                                     but each larger
```

Fewer contacts lower the number of grain-sized sites, and the cycle count needed for the same open rate falls. Weaker signals make the main step harder to adapt. On balance, the periphery clear becomes easier to specify and harder to monitor.

---

## 14.7 3D DRAM: Dielectric on Surfaces No Ion Can See

### 14.7.1 The Structure

In 3D DRAM, the cell is laid on its side and the array is stacked in tiers, like 3D NAND. Each capacitor is a horizontal cavity, opened from a vertical slit or hole, lined with a laterally recessed bottom electrode (Book #32, Chapter 14), then the dielectric, then the top electrode, which fills the cavity and joins the shared plate in the slit.

```
3D DRAM capacitor tiers (illustrative, cross-section through the slit):

        slit (≈ 100 nm wide, ≈ 5 µm deep)
           │ │
   ════════╡ ╞════════   tier separator (SiO₂/SiN)
   ▓▓▓▓░░░░│ │░░░░▓▓▓▓   ← horizontal capacitor cavity: BE TiN (▓), ZAZ, TE
   ════════╡ ╞════════
   ▓▓▓▓░░░░│ │░░░░▓▓▓▓
   ════════╡ ╞════════
           ...  ×100 tiers
```

ALD puts the dielectric on every surface reachable from the slit: inside the cavities, where it belongs; on the slit walls, where the TE and plate will cover it; and, in some designs, on the access-transistor side of each cavity, where it must not stay.

### 14.7.2 A Lateral Recess

Where the dielectric must be removed from inside a cavity, to a depth of tens of nanometres from the slit, no directional etch can reach it. The etch must be isotropic and must remove the same depth on the top tier as on the hundredth:

```
Lateral dielectric recess (illustrative):
  Target: remove ZAZ to 20 nm from the slit wall, inside 100 tiers of
          30 nm-tall cavities, slit 5 µm deep

  Thermal ALE (HF/DMAC, 0.06 nm/cycle):   ≈ 330 cycles → hours; too slow
  Hot isotropic radical etch:
    BCl₃/Cl₂ remote plasma, wafer 300 °C (ZrCl₄ volatile; E_th → ≈ 0)
    Lateral rate ≈ 3–5 nm/min at the top tier
    Radical loss along the slit (recombination on the walls) → the
    bottom tier sees fewer radicals:
      Bottom-to-top recess ratio ≈ 0.8 without correction
    Corrections: pulsed delivery, higher pressure (more diffusion per
    wall collision), alternating etch and passivation
```

The physics is that of Chapter 12 in a new geometry: transport down a high-aspect-ratio slit, then sideways into a cavity, with every wall collision a chance to react or recombine. The tier-to-tier uniformity of the recess becomes the uniformity of the capacitors, the same role the bottom-to-top trim ratio plays in the pillar array.

### 14.7.3 The Staircase

The periphery-type clear of 3D DRAM is on the staircase, where contacts land on each tier's word line or plate. The staircase has vertical faces at every step, and ALD coats them. A directional periphery clear removes the dielectric from the treads but not the risers, leaving vertical ZAZ stringers between tiers. Like the mark sidewalls of Chapter 10, they are harmless if no contact lands on them, but staircases are built for contacts. An isotropic finish, thermal ALE or a hot radical step, joins the ALE finish in the clearing sequence.

---

## 14.8 Summary Table

```
                      Periphery clear          Bevel removal            Trim / recess
──────────────────────────────────────────────────────────────────────────────────────
HZH, HfO₂-rich        slightly slower; no Al   as ZAZ                   as ZAZ
                      marker
La/Y-doped ZrO₂       La/Y residue; water      La/Y on the bevel;       dopant enrichment
                      rinse removes it         rinse                    at the surface
TiO₂ on Ru            fast, narrow tail; Ru    Ru removal is the hard   TiO₂ EPC less
                      etch oxidizes edges      part                     self-limited
SrTiO₃                cyclic dry–wet           wet rinse mandatory      not practical by
                                                                        thermal ALE (Sr)
AFE / FE HZO          edge V_O, imprint;       as ZAZ                   risky: phase shifts
                      low-damage finish                                 with thickness
4F²                   as reference             as reference             trim needed
Wafer-bonded          10% open area; weak      as reference             as reference
                      signals; fewer contacts
3D DRAM               staircase risers need    as reference (taller     lateral recess by
                      an isotropic finish      stack at the edge)       hot radical etch
```

---

## Summary and Key Takeaways

1. **Volatility predicts the route.** Hf behaves like Zr; Ti leaves on its own; Sr, La, and Y do not leave at all as chlorides and need water.

2. **Water rescues non-volatile chlorides.** LaCl₃ and SrCl₂ dissolve; the strip's water and a rinse remove them, and for SrTiO₃ a cyclic dry–wet clear is the natural route.

3. **Phase-sensitive films resent etches.** AFE and FE HZO respond to oxygen vacancies, hydrogen, fluorine, charge, and thinning; they are poor candidates for a trim.

4. **Smaller pitches make the trim a necessity.** At 4F² pitches, the reference ZAZ leaves only 3.5 nm of channel for the top electrode.

5. **Bonding shrinks the periphery.** A 10% open area weakens every endpoint signal and lowers the number of contacts at risk.

6. **3D DRAM needs isotropic removal.** Lateral recesses and staircase risers are invisible to ions; hot radical etches and thermal ALE carry the job, and their uniformity is a transport problem.

---

## Study Questions

1. Estimate the La left on the periphery from a 5.5 nm ZrO₂ film with 5 at% La if 60% of the La remains on the surface as LaClₓ. Is it above a monolayer? What would you add to the process?

2. Using the TiO₂ numbers in Section 14.3.2, design a periphery clear for an 8 nm Al-doped TiO₂ film with the same residue target as the reference. Do you still need an ALE finish?

3. An STO film of 10 nm loses 2 nm per dry–wet cycle. If each cycle takes 40 s (dry 15 s, rinse and dry 25 s), how long is the clear? Compare it with module 2.

4. For the 4F² array of Section 14.6.1, compute the trim needed to give the TE TiN 4.7 nm at the channel bottom, starting from a 5.5 nm ZAZ. What EOT would the trimmed film have if its permittivity were unchanged?

5. In a wafer-bonded design with 10% open area, the Al-marker signal falls to a quarter of the reference. If the marker's timing noise scales inversely with the signal, how much less precisely is the main step adapted?

6. For the 3D DRAM lateral recess, the bottom-to-top ratio is 0.8 for a 20 nm target. What recess does the bottom tier get? Propose two ways to raise the ratio and the cost of each.

---

**Next Chapter:** [Chapter 15: Metrology, Inspection & Advanced Process Control](./15-metrology-inspection-apc.md)

---

**Chapter 14 Development Status:** Complete  
**Version:** 1.0
