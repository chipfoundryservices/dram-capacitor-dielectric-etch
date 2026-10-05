# Chapter 10: Clearing the Periphery — Grain Residue, Micromasking & Stringers

## Overview

The dielectric clear is judged by what it leaves, and what it leaves is almost always nothing. The question is how often "almost" fails. A periphery die has about 9 × 10¹⁰ independent clearing domains in its ZAZ, about 1.2 × 10⁸ of them under contacts. If one of those 10⁸ survives under a contact, a contact fails. The process must therefore be designed for a residue probability per domain below 10⁻¹⁰, a level no inline measurement can confirm directly.

This chapter separates the problem into its two parts, as Book #32 did for storage-node separation. The **Gaussian** part is the spread of local clearing times from thickness, phase, and grain structure. Overetch beats it, and the reference D1 overetch beats it by more than six standard deviations even at the slowest site on the wafer. The **non-Gaussian** part is everything that stops the etch locally for reasons the spread does not describe: carbon from the strip, boron glass, fluorinated patches, zirconia nodules from the deposition, and particles. Overetch helps little against these; they must be controlled where they originate. The chapter then turns to the dielectric on vertical walls, which a directional etch cannot reach at all, and ends with the contact-open budget for each route.

**Learning Objectives:**
- Describe the sequence in which a mixed-phase, two-layer ZAZ clears, and define the clearing domain
- Build the local clearing-time spread from its contributions and compute the residue probability for a given overetch
- Compute the expected number of residual domains per die and under contacts for D1, D2, and thermal ALE
- Identify the non-Gaussian residue mechanisms, estimate their densities, and set source controls for each
- Explain why stringers form on vertical faces, when they matter, and what each route can do about them
- Assemble a contact-open budget and set an e-beam inspection limit from it

---

## 10.1 How the Film Clears

### 10.1.1 Sequence

```
Clearing sequence of the periphery ZAZ in D1 (illustrative):
  0–3 s     BT removes Ti, C, F, Cl and ≈ 0.65 nm of the upper ZrO₂
  3–16 s    upper ZrO₂ thins; grain boundaries recess ahead of interiors
  ≈ 15 s    boundaries reach the Al₂O₃ insertion first
  16–19 s   insertion clears, earliest under former boundaries
  19–33 s   lower ZrO₂ thins; its boundaries (offset from the upper ones)
            recess ahead of its interiors
  ≈ 31 s    first SiOₓNᵧ exposed along lower-layer boundaries
  31–41 s   lower-layer grain interiors clear as islands 0.5–1.5 nm thick;
            monoclinic grains last
  ≈ 36 s    mean clearing (t_EP)
  > 41 s    the slowest few domains in 10⁸, 10¹⁰ ... clear during overetch
```

### 10.1.2 The Clearing Domain

Because the upper and lower ZrO₂ layers have independent grain mosaics, each 15–40 nm across, every point of the film sits in one upper grain and one lower grain. A region in which both are the same grains clears as a unit. The average size of such a **clearing domain** is smaller than either grain size, about 20 nm across:

```
Domains (reference, illustrative):
  Domain area                 ≈ (20 nm)² = 4 × 10⁻¹² cm²
  Periphery open area per die ≈ 0.36 cm² (45% of ≈ 0.79 cm² per die site)
  Domains per die             ≈ 9 × 10¹⁰
  Contact bottoms per die     3 × 10⁷ × 1600 nm² = 4.8 × 10⁻⁴ cm²
  Domains under contacts      ≈ 1.2 × 10⁸ per die (≈ 4 per contact)
```

---

## 10.2 The Gaussian Part

### 10.2.1 Contributions to the Local Spread

```
Local (domain-to-domain) clearing-time spread in D1, 1σ (illustrative):
  Phase mix (30% monoclinic, 11% slower)       3.8%
  Local thickness (roughness ≈ 0.3 nm rms)      5.6%
  Grain orientation and boundary density        6.0%
  BT non-uniformity at the scale of grains      3.0%
  Total σ_g = √(3.8² + 5.6² + 6.0² + 3.0²)      ≈ 9.5% → 10% (reference)
```

### 10.2.2 Residue Probability

Treat each domain's clearing time as normally distributed about the local mean with relative spread σ_g. With an overetch OE (as a fraction of the mean clearing time t_EP) at a site whose mean clearing time is s × t_EP:

```
z = ((1 + OE) / s − 1) / σ_g
P(domain left) = ½ erfc(z / √2)
Expected residual domains under contacts per die = 1.2 × 10⁸ × P
Expected residual domains anywhere per die       = 9 × 10¹⁰ × P
```

### 10.2.3 The Reference Overetch

```
D1, σ_g = 10%; mean site s = 1.00; slowest site s = 1.03 (Chapter 6):

  OE     Site    z       P(left)       Under contacts   Anywhere
                                       per die          per die
  ───────────────────────────────────────────────────────────────────
  50%    mean    5.00    2.9 × 10⁻⁷    34               2.6 × 10⁴
  50%    slow    4.56    2.5 × 10⁻⁶    300              2.3 × 10⁵
  60%    mean    6.00    9.9 × 10⁻¹⁰   0.12             89
  60%    slow    5.53    1.6 × 10⁻⁸    1.9              1400
  70%    mean    7.00    1.3 × 10⁻¹²   1.5 × 10⁻⁴       0.1
  70%    slow    6.50    3.9 × 10⁻¹¹   0.0047           3.5   ← reference
  80%    slow    7.48    3.8 × 10⁻¹⁴   4.6 × 10⁻⁶       0.003
```

The reference 70% overetch keeps the Gaussian contribution below 0.005 contacts per die even at the slowest site, about half the 0.01 target. Each 10% of overetch moves the tail by about one standard deviation and changes the residue by one to two orders of magnitude. The SiN cost of each 10% is about 0.18 nm (3.6 s at 3 nm/min). In D1, the Gaussian tail is cheap to beat.

### 10.2.4 Not Every Residual Domain Kills a Contact

Of the domains left at the end of the overetch, those still thicker than about 1 nm stop the contact etch; thinner ones are punched through, sometimes with a resistance penalty (Chapter 1). Near the clearing tail, the surviving domains are thin; roughly half exceed 1 nm. The Gaussian contribution to fatal contact opens at the reference is therefore about 0.002 per die.

---

## 10.3 The Non-Gaussian Part

### 10.3.1 Mechanisms

```
Non-Gaussian residue mechanisms (D1, illustrative):

Mechanism                 Origin                         Overetch helps?
─────────────────────────────────────────────────────────────────────────────────
Carbon micromasks         fragments of resist and BARC   a little: BT sputters
                          redeposited during the strip;  thin C; fragments
                          5–30 nm; not removed by        > 2 nm survive the BT
                          BCl₃/Cl₂ without oxygen        and shield the ZAZ
Boron glass islands       B₂O₃ from BₓClᵧ meeting        a little
                          moisture (queue, vent
                          recovery); hard in BCl₃
Fluorinated patches       ZrF₄ skin from wall memory     yes, if the BT is
                          (conductor chamber, F clean)   sufficient
Ti-rich islands           TE TiN clearing last in the    yes (TiOₓ etches fast
                          plate etch                     in BCl₃ at 250 °C)
ZrO₂ nodules              gas-phase or wall particles    no: 10–50 nm thick
                          in the ALD, embedded in the
                          film
Particles and flakes      walls, chuck, transfer (Ch. 9) no
Shadowed strips           ion tilt next to plate edges   yes
                          at the wafer edge (Ch. 6)
```

### 10.3.2 How Much Is Allowed

A residual island in the periphery kills a contact only if a contact lands on it. The fraction of the periphery covered by contact bottoms sets the conversion:

```
Fraction of periphery under contact bottoms: f_c = 4.8 × 10⁻⁴ / 0.36 ≈ 1.3 × 10⁻³

Allowed fatal islands per die for 0.01 opened contacts per die:
  N_islands ≤ 0.01 / 1.3 × 10⁻³ ≈ 8 per die ≈ 20 per cm² of periphery
  (for islands no larger than a contact; larger islands count with their area)
```

That is the inspection specification: fewer than about 20 residual islands per cm² of periphery, of a size that can stop a contact. It is a strict but measurable number for e-beam inspection, unlike the 10⁻¹⁰ domain probability (Chapter 15). The Gaussian contribution at the reference uses about 3.5 of the 8 per die at the slowest site, mostly sub-contact-sized domains; the non-Gaussian mechanisms must fit in the rest.

### 10.3.3 Carbon From the Strip

```
Carbon micromask budget (illustrative):
  Carbon after N₂/H₂ strip           2–5 × 10¹⁴ C/cm² (Chapter 2)
  Fraction in fragments > 2 nm       ≈ 10⁻⁶ of the carbon area
  Fragment density                   ≈ 10–100 per cm²
  Survival of the BT + 25 s OE       ≈ 20%
  Islands                            2–20 per cm² → up to the whole budget
```

Carbon is the largest non-Gaussian source in the hard-mask route, and it comes from a step that is not the dielectric clear. Controls: strip completion (time, temperature, and an endpoint on the strip itself), a downstream strip chamber with no line of sight from resist to wafer surface during the burn, and a BT energy high enough to sputter thin carbon. Adding a little O₂ to the BT would remove carbon but would also oxidize the plate sidewall and create B₂O₃; the reference does not.

### 10.3.4 Boron Glass

BₓClᵧ left on the surface after the clear is converted to B₂O₃ by the PET and removed by the rinse (Chapter 12). Before the clear, any boron deposit that meets moisture becomes glass. That happens when the vacuum transfer is broken, when wafers are held in a load lock that has seen a vent, or when the chamber has just recovered from a wet clean. Queue-time control and wall seasoning keep it rare.

### 10.3.5 Nodules and Particles

ZrO₂ nodules 10–50 nm thick come from ALD precursor decomposition or from flakes in the deposition chamber. No dielectric clear removes 50 nm of crystalline ZrO₂ with 25 s of overetch. They are controlled in the ALD module by particle monitoring and chamber cleaning, and caught by inspection after the clear. The same is true of zirconium-containing flakes from the D1 walls (Chapter 9).

### 10.3.6 Overetch Beats the Gaussian, Not the Rest

```
Effect of overetch on each residue source (D1, illustrative):
  Source               OE 50% → 70%            OE 70% → 100%
  ───────────────────────────────────────────────────────────────
  Gaussian tail        × 10⁻⁴                   × 10⁻⁹
  Carbon micromasks    × 0.6                    × 0.5
  Boron glass          × 0.8                    × 0.7
  F patches            × 0.3                    × 0.5
  Nodules, particles   × 1                      × 1
  SiN loss             + 0.4 nm                 + 0.5 nm
  TE TiN recess        + 0.15 nm                + 0.2 nm
```

Above about 70%, more overetch buys nothing measurable in contact yield and costs landing film, edge recess, and time. The non-Gaussian sources set the yield, and they are fixed at their source.

---

## 10.4 The Other Routes

### 10.4.1 D2 (Plasma ALE)

```
D2, σ_g ≈ 4% (Chapter 4), over-cycling 30% (73 / 56 cycles):
  Site     z       P(left)          Under contacts per die
  ──────────────────────────────────────────────────────────
  mean     7.6     1.6 × 10⁻¹⁴      2 × 10⁻⁶
  slow     6.6     1.6 × 10⁻¹¹      0.0019   (edge: +3% thickness,
                                             not compensable in ALE)
```

D2 beats the Gaussian tail with a smaller margin in percent and a larger one in standard deviations, because its spread is narrower. Its non-Gaussian behaviour is different: Ar⁺ at 60 eV and BCl₃ without bias remove carbon even less effectively than D1's main etch, so D2 depends on its opening BT for carbon, exactly as D1 does. Ti-rich islands chlorinate readily in step A and clear. Particles and nodules are unaffected.

### 10.4.2 Thermal ALE

```
Thermal ALE, σ_g ≈ 12% (Chapter 4), nominal 107 cycles:
  Cycles   Over-cycling   z       P(left)         Under contacts per die
  ───────────────────────────────────────────────────────────────────────
  139      30%            2.5     6 × 10⁻³        ≈ 7.6 × 10⁵   ✗
  170      59%            4.9     4.6 × 10⁻⁷      ≈ 56          ✗
  190      78%            6.5     5 × 10⁻¹¹       0.006         ✓
```

Thermal ALE's wider spread, from its sensitivity to phase and to boundary fluorination, requires nearly 80% over-cycling: about 190 cycles. That lengthens the batch time to about 3.2 h of cycling per load, and increases the undercut at the plate edge to about 1.78 × 5.4 ≈ 9.6 nm at the top of the ZAZ (Chapter 11). Against that, thermal ALE has no ion-shadowing, no carbon sputtering (and no carbon removal either), and it clears vertical walls.

### 10.4.3 The Hybrid

The hybrid route's dry step leaves about 0.8 nm, damaged by ions; the wet step removes the damaged layer. Any domain that was more than about 0.8 nm thicker than the mean when the dry step stopped, about 2σ of the local spread at that point, is left with undamaged crystalline ZrO₂ under its damaged skin, which the wet step barely etches. The hybrid needs either a longer dry step (which defeats its purpose) or acceptance of a Gaussian tail it does not fully remove. It is attractive when non-Gaussian sources dominate and the dry overetch is limited by something else, such as damage (Chapter 13).

---

## 10.5 Stringers on Vertical Faces

### 10.5.1 Formation

Where topography lies outside the plate, the ZAZ on its vertical walls is 5.4 nm thick horizontally and up to 1.6 µm tall (Chapter 2). A directional etch removes it only by spontaneous lateral attack and by ions reflected off the floor:

```
Lateral removal of wall ZAZ in D1 (illustrative):
  Spontaneous lateral ZrO₂ etch at 250 °C (no ions)   ≈ 0.1 nm/min
  Reflected and scattered ions near the floor          ≈ 1 nm/min in the
                                                       bottom ≈ 50 nm
  After 61 s: wall ZAZ thinned by ≈ 0.1 nm over most of its height,
  ≈ 1 nm near the foot
```

The wall ZAZ remains. It is a 5 nm liner on the wall of a mark trench or a monitor array.

### 10.5.2 When It Matters

```
Consequences of wall ZAZ (illustrative):
  Case                                       Consequence
  ─────────────────────────────────────────────────────────────────────────
  Liner on a permanent oxide or SiN wall     inert; buried by the ILD
  Liner on a wall later removed (sacrificial frames, monitor structures)
                                             free-standing fence; breaks into
                                             ZrO₂ flakes → high-k islands
  Overlay and alignment marks                edge signal changes; mark-
                                             dependent overlay offsets
  Later contacts or vias crossing the wall   etch stops on the liner
  (scribe test structures)
```

Most stringers are harmless. The dangerous ones are those that become free-standing, and those on marks that later layers read.

### 10.5.3 What Each Route Can Do

```
Route                Wall ZAZ                     Side effects
───────────────────────────────────────────────────────────────────────────────
Layout               cover topography with        plate dummy islands over
                     plate islands; no ZAZ        marks and monitor arrays;
                     reaches the D1 plasma        mark designs reworked
D1, D2               remains                      none
Thermal ALE          removed                      edge undercut (Chapter 11)
Wet finish           removed only with ≈ 3 min    ≈ 9 nm SiN loss ✗
(HF/H₂SO₄, 80 °C)    on crystalline ZrO₂
```

The reference resolves stringers by layout: marks and monitor arrays that carry capacitor-module topography are placed under plate dummy islands, so their ZAZ is protected rather than exposed, and mark designs read by later layers avoid mold topography altogether. Routes that must clear vertical faces, as in the 3D DRAM schemes of Chapter 14, need an isotropic step and must solve the edge undercut instead.

---

## 10.6 The Contact-Open Budget

```
Opened periphery contacts per die attributable to the dielectric clear
(reference D1, illustrative):

  Source                                  Islands      Fatal contacts
                                          per die      per die
  ────────────────────────────────────────────────────────────────────
  Gaussian tail (slowest site)            3.5          0.002
  Carbon micromasks                       2            0.003
  Boron glass                             0.5          0.0007
  F patches, Ti islands                   0.3          0.0004
  Nodules and flakes                      0.5          0.0007
  Total                                   ≈ 7          ≈ 0.007
  Target                                  ≤ 8          < 0.01
```

The budget is nearly full. A modest rise in any one source, carbon from a weakened strip or flakes from a chamber running past its clean interval, pushes the module over the line. That is why the non-Gaussian sources each carry their own monitors and action limits (Chapter 15).

---

## Summary and Key Takeaways

1. **Clearing happens domain by domain.** About 9 × 10¹⁰ domains per die, 1.2 × 10⁸ under contacts; each clears on its own time.

2. **Overetch beats the Gaussian tail cheaply in D1.** σ_g ≈ 10%; 70% overetch gives z ≈ 6.5 at the slowest site and about 0.002 fatal contacts per die.

3. **Non-Gaussian residue sets the yield.** Carbon from the strip, boron glass, fluorinated patches, nodules, and particles are reduced little by overetch and are controlled at their source.

4. **The inspection limit is about 20 islands per cm² of periphery.** It follows from the contact-open target and the fraction of periphery under contacts.

5. **Thermal ALE needs nearly 80% over-cycling;** D2 needs 30% because its spread is about 4%.

6. **Stringers are mostly harmless and are best avoided by layout.** Only isotropic routes clear vertical walls, at the price of the plate edge.

---

## Study Questions

1. Recompute the table of Section 10.2.3 for σ_g = 12% (a coarser-grained periphery film). What overetch is needed to keep the slowest site below 0.005 contacts per die?

2. A product has 4.5 × 10⁷ periphery contacts per die with 30 × 30 nm bottoms. Recompute the domains under contacts, the allowed island density, and the required overetch for D1.

3. The strip chamber's endpoint fails and the carbon fragment density doubles. Using Section 10.3.3, does the module still meet its budget? What would you change first: the strip, the BT, or the overetch? Why?

4. Show that a 10% increase in overetch moves z by about one standard deviation in D1, and compute the SiN and TE TiN cost of going from 70% to 90%.

5. For thermal ALE, compute the cycles needed for z = 6.5 at the slowest site if the edge is 3% thicker. What is the undercut at the top of the ZAZ?

6. A mark design for a later layer must sit in the periphery outside any plate and must use a mold trench. Propose two ways to keep its wall ZAZ from affecting the mark, and the cost of each.

---

**Next Chapter:** [Chapter 11: The Cut Edge — Top-Electrode Recess, Undercut & Ingress](./11-cut-edge-recess-undercut-ingress.md)

---

**Chapter 10 Development Status:** Complete  
**Version:** 1.0
