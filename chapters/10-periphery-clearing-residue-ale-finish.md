# Chapter 10: Periphery Clearing — Residue Statistics, the ALE Finish & SiN Landing

## Overview

Module 2 exists to make one number small: the probability that a grain of ZrO₂ survives under any periphery contact. Chapters 3–9 have provided the pieces: the chemistry that removes the film, the spread the continuous step creates, the self-limited finish that removes the rest with little SiN loss, the clearing-time map that tells the finish how much to remove, and the signals that check it on every wafer. This chapter puts them together.

It begins with where the last dielectric is: at which wafer sites, at which places in the die, and in which part of each grain. It develops the residue model that sets the cycle count, shows how the share of removal between the main step and the finish changes the result (much less than one might hope), and identifies what does change it. It then follows the landing on the periphery SiN, the boron and chlorine left there, and the zirconium veils at the plate edge. It closes with a comparison of the five routes for clearing the periphery and a table of failure modes.

**Learning Objectives:**
- Identify where the last ZAZ on the periphery lies, at wafer, die, and grain scale
- Compute the residue probability and expected contact opens for a given main step and cycle count
- Show why moving removal between the main step and the finish changes the cycle count little, and what lever does change it
- Compute the SiN loss at each wafer site for the continuous and ALE-finished routes
- Explain the origin of zirconium veils and why a short main step and a low-energy finish reduce them
- Compare continuous, ALE-finished, hot, quasi-ALE, and wet-hybrid clearing routes

---

## 10.1 Where the Last Dielectric Is

### 10.1.1 On the Wafer

The slowest sites of the clearing-time map, in the outer 5 mm of dies, carry 1.34 nm after the main step; the fastest, in the 90 mm band, carry 0.79 nm (Chapter 6). Every site receives the same finish. The cycle count is set by the edge.

### 10.1.2 In the Die

```
Periphery locations, ranked by remaining ZAZ after the main step
(same wafer site, illustrative):

  Location                           Effect on clearing        Contacts there?
  ──────────────────────────────────────────────────────────────────────────────
  Plate foot (≤ 50 nm from the       ion shadowing by the       no (design rule:
  plate edge)                        550 nm plate + resist      contacts ≥ 0.5 µm
                                     stack; +10–30% local       from the plate)
                                     thickness-equivalent
  Sidewalls of steps (overlay        vertical ZAZ is not        no (scribe marks)
  marks, scribe structures)          removed by an
                                     anisotropic etch
  Dense periphery (sense-amp         slightly slower main       yes: most of the
  and sub-word-driver regions)       step (local loading)       3 × 10⁷ contacts
  Open periphery                     nominal                    yes
```

The plate foot and the step sidewalls are where the dielectric survives longest, but neither is under a contact. At the plate foot, the surviving ZAZ becomes part of the edge structure of Chapter 11. On mark sidewalls, it remains as a thin vertical stringer, a cosmetic and overlay-signal issue that an isotropic step could remove if it mattered. The contact-bearing regions are flat and clear at the local rate of the map.

### 10.1.3 In the Grain

Grain boundaries etch about 30% faster than grain interiors in the main step (Chapter 2, Section 2.2.3). As the film thins, boundaries reach the bottom first, and the remaining film breaks into islands, each a grain interior. The last material on the periphery is a scatter of grain-centre islands, 10–30 nm across and up to a nanometre thick: exactly the size of a contact bottom.

---

## 10.2 The Residue Model

### 10.2.1 Sites and Targets

```
Grain-sized sites under periphery contacts:
  Contacts per die                     3 × 10⁷
  Contact bottom                       40 × 40 nm = 1600 nm²
  Grains under each contact (≈ 20 nm)  ≈ 4
  Sites per die                        N_s ≈ 1.2 × 10⁸

Target: residue-attributable opens ≤ 0.01 per die
  P(site keeps a grain) ≤ 0.01 / 1.2 × 10⁸ ≈ 8 × 10⁻¹¹  →  z ≥ 6.4
```

Not every surviving grain opens its contact: a grain covering a quarter of the bottom raises the resistance, and one at the edge of the bottom may be undercut by the contact's own overetch. Treating every surviving grain as an open is conservative by a factor of perhaps two to four. The conservatism is kept, because the distribution has non-Gaussian tails (Section 10.2.4).

### 10.2.2 The Gaussian Tail

At a wafer site where the mean remaining thickness after the main step is R and the grain-scale spread at the end of the finish is σ, a finish that removes A = N × EPC + b leaves a grain with probability:

```
P = ½ erfc(z / √2),   z = (A − R) / σ

Reference: A = 36 × 0.10 + 0.05 = 3.65 nm, σ = 0.352 nm

  Site       R (nm)    z       P             Opens per die
  ─────────────────────────────────────────────────────────
  Fastest    0.79      8.1     ≈ 2 × 10⁻¹⁶    ≈ 0
  Nominal    1.06      7.4     ≈ 9 × 10⁻¹⁴    ≈ 1 × 10⁻⁵
  Slowest    1.34      6.6     ≈ 3 × 10⁻¹¹    ≈ 0.003
```

### 10.2.3 Expected Opens per Wafer

Integrating over the clearing-time map, almost all of the expected residue comes from the slowest band:

```
Dies per wafer ≈ 950; fraction in the slowest band (r > 140 mm) ≈ 12%

Expected residue opens per wafer ≈ 0.12 × 950 × 0.003 + (rest ≈ 0)
                                 ≈ 0.35
Expected per die (wafer average) ≈ 4 × 10⁻⁴
```

The Gaussian residue tail of the reference process is negligible for the wafer as a whole and small at the edge. That is how it should be: the Gaussian tail is the part of the problem the engineer controls by design. The rest of the opens come from mechanisms that are not Gaussian.

### 10.2.4 Non-Gaussian Mechanisms

```
Contact opens attributable to module 2 (reference, illustrative Pareto):

  Mechanism                                 Share     Signature
  ──────────────────────────────────────────────────────────────────────────
  Particles and wall flakes (Chapter 9)     ≈ 45%     clusters of 3–20 opens
  ALD flakes embedded in the ZAZ            ≈ 20%     single large residue;
                                                       TEM shows ZrO₂ > 6 nm
  BₓClᵧ micromasking in the main step       ≈ 15%     random singles; boron
                                                       under the residue
  Monoclinic or Al-rich grains (low EPC     ≈ 10%     singles at the slowest
  in both steps)                                       sites
  Gaussian tail (this section)              ≈ 5%      singles at the edge
  Veil fragments (Section 10.6)             ≈ 5%      near plate edges in the
                                                       periphery
```

**BₓClᵧ micromasking** deserves explanation. In the main step, the boron-chlorine deposit forms everywhere and is cleaned continuously by ions. Where a small region receives a little less ion flux or a little more radical flux, an island of BₓClᵧ survives long enough to shadow the ZrO₂ beneath it. The ZrO₂ under the island etches later than its neighbours. The fix is in the main-step chemistry (Cl₂ fraction, Chapter 3, Section 3.3.3), not in the finish, whose BCl₃ dose without plasma forms no BₓClᵧ film.

---

## 10.3 Dividing the Work Between Main Step and Finish

### 10.3.1 The Cycle Count as a Function of the Main Step

If the main step removes x nm, the slowest site carries R_slow = 5.5 × 1.05 − x, the spread is σ(x) = √((σ_r x)² + σ_t² + σ_ALE²), and the finish needs:

```
N(x) = ⌈ (R_slow(x) + 6.4 σ(x) − b) / EPC ⌉

σ_r = 7.5%, σ_t = 0.12 nm, σ_ALE = 0.04 nm, b = 0.05 nm, EPC = 0.10 nm

  x (nm)    Main time   R_slow   σ(x)    N     Finish   Total    Fast site
            (s)                                time (s)  (s)     breaks
                                                                  through
  ──────────────────────────────────────────────────────────────────────────
  3.50       35.6        2.28    0.291   41     185      221      0%
  4.00       40.6        1.78    0.326   39     176      217      0.1%
  4.44       45.0        1.34    0.356   36     162      207      1%
  4.90       49.6        0.88    0.389   34     153      203      20%
```

Moving a nanometre of removal from the finish to the main step saves about five cycles, not ten, because the main step widens the tail as it goes. Past about 4.5 nm, the fast sites begin to clear in the main step and lose SiN at 0.13 nm per second. The reference sits at the knee.

### 10.3.2 The Lever That Works

The term that dominates the cycle count is 6.4 σ(x), and σ(x) is dominated by σ_r x. **Reducing σ_r** is worth far more than any redistribution of removal:

```
Effect of the main-step grain spread σ_r at x = 4.44 nm:

  σ_r       How                                   σ(x)     N
  ────────────────────────────────────────────────────────────
  10%       main step at 100 eV                   0.46     43
  7.5%      reference (150 eV, 60 °C)             0.36     36
  5%        150 eV, 120 °C (resist limit)         0.26     30
  3.5%      250 °C, hard-mask route               0.20     26
```

A main step at 100 eV, chosen to protect the plate edge, would cost seven more cycles. A main step at 120 °C, the most a resist mask allows, saves six. Chapter 16 prices these options.

---

## 10.4 Landing on the Periphery SiN

### 10.4.1 SiN Loss by Site

```
SiN EPC in the finish: 0.015 nm/cycle; first exposure when the local
grain distribution's mean clears.

  Site       Cycle at which the     Cycles on SiN    SiN loss (nm)
             mean clears
  ─────────────────────────────────────────────────────────────────
  Fastest     8                      28               0.42
  Nominal    11                      25               0.38
  Slowest    13                      23               0.35
  Main-step breakthroughs (1% of grains at the fastest site): ≤ 0.3 nm
  on 1% of the area
```

```
Comparison with a continuous 50% overetch (Book #32):
  SiN loss, fastest / slowest site       ≈ 6–7 nm / 2–3 nm
  ALE-finished (reference)               0.42 / 0.35 nm
```

### 10.4.2 Why It Matters

The periphery contacts must open the 120 nm SiN after the oxide etch. A SiN whose thickness varies by 4 nm across the wafer forces the SiN-open step to overetch the thinnest sites by the time it takes to clear the thickest; on landing pads that are themselves thin, that overetch is a gouge. An SiN that lost 0.35–0.42 nm everywhere is, for practical purposes, the SiN that was deposited. The ALE finish's benefit is not only the 3.7 nm of SiN it saves on average, but the 4 nm of non-uniformity it never creates.

---

## 10.5 Boron and Chlorine on the Landing Film

```
Surface of the periphery SiN at the end of the finish (illustrative):
  B     ≈ 3 × 10¹⁴ atoms/cm² (most from the main step; ALE dose adds little
        to SiN, where it adsorbs weakly)
  Cl    2–5 at% in the top 1 nm
  Zr    ≈ 5 × 10¹² atoms/cm² (re-adsorbed ZrClₓ; scattered atoms, not
        grains)
```

The strip that follows removes the resist and treats the surface:

```
Strip and treatment (reference, downstream chamber on the same platform):
  O₂ / H₂O (10%), 1.5 Torr, 250 °C, remote plasma, 60 s
    Resist (≈ 310 nm) removed
    B:  3 × 10¹⁴ → ≤ 5 × 10¹³ atoms/cm² (B₂O₃ hydrated, H₃BO₃ volatilizes
        partly at 250 °C)
    Cl: 2–5 at% → < 0.5 at%
Post-strip wet clean:
  DIW rinse with dissolved O₃, then backside scrub
  (no SC1: it would attack the TE TiN and the W at the plate edge)
```

Water is the active ingredient. It hydrolyses BOₓClᵧ to boric acid and HCl under controlled conditions, at temperature, in the strip chamber, rather than in the fab air, where HCl would corrode the plate edge (Chapter 11).

```
Queue time: from the end of the finish to the strip: ≤ 5 min (same
platform, vacuum transfer). From the strip to the ILD: ≤ 24 h.
```

---

## 10.6 Zirconium Veils

### 10.6.1 How a Veil Forms

During the main step, ions sputter ZrClₓ and BOₓClᵧ fragments from the periphery near the plate edge. A small fraction strike the resist sidewall and stick. When the resist is stripped, the deposit is left as a thin free-standing film along the plate's outline: a **veil**.

```
Veil thickness (on the resist sidewall at mid-height, illustrative):
  Continuous route (93 s at 150 eV)      ≈ 1.0 nm Zr–B–O–Cl
  Reference (45 s at 150 eV + ALE)       ≈ 0.4 nm
  (ALE removal products at 60 eV leave mostly as volatile species
   with little sputtered fragment flux)
```

### 10.6.2 Why a Thin Veil Is Harmless

A film needs a minimum thickness to stand after its support is removed. Below about 1 nm, an oxychloride deposit has no continuous network; when the resist goes, it collapses onto the surface as scattered atoms (contributing to the 5 × 10¹² Zr/cm² of Section 10.5) rather than standing as a fence. At 1 nm and above, segments survive, fall over, and lie on the periphery as flakes up to a micrometre long, which block contacts (Section 10.2.4).

### 10.6.3 Removal

Any veil that survives is amorphous and soluble in dilute HF. A 10 s dip in 0.1% HF after the strip removes it, at the cost of about 0.2 nm of SiN and a small attack on the exposed ZAZ edge at the plate foot (Chapter 11). The reference does not use the dip; the continuous route needs it.

---

## 10.7 Five Routes Compared

```
Per reference wafer (illustrative):

                      Continuous     ALE-finished    Hot main     Quasi-ALE      Wet hybrid
                      (Book #32)     (reference)     (250 °C,     finish         (dry + HF)
                                                     hard mask)
───────────────────────────────────────────────────────────────────────────────────────────────
Main step             to clear +     45 s, 4.44 nm   ≈ 36 s at    45 s, 4.44 nm  45 s
                      50% OE                         80 eV, to
                                                     clear + 26%
Finish                —              36 ALE, 162 s   —            ≈ 70 s         0.5% HF, ≈ 17 min
                                                                  (EPC 0.3)      (t-ZrO₂ 0.2 nm/min)
z at slowest site     6.25           6.6             6.4          ≈ 6.4          high
SiN loss (range)      2–7 nm         0.35–0.42 nm    ≈ 1 nm       ≈ 1.2 nm       ≈ 30 nm (HF on SiN)
Resist / mask used    78 nm resist   52 nm resist    oxide HM     ≈ 60 nm        52 nm
High-energy ion time  93 s           45 s            0 (80 eV)    45 s + pulsed  45 s
Veil                  ≈ 1 nm         ≈ 0.4 nm        ≈ 0.3 nm     ≈ 0.6 nm       removed
Plate-edge TE notch   ≈ 4 nm         ≈ 1 nm          large unless ≈ 2 nm         wet undercut of
(Chapter 11)                                         protected                   ZAZ edge
Chamber time for HK   93 s           217 s           ≈ 50 s       ≈ 125 s        dry 55 s + wet
Extra steps           HF veil dip    none            HM dep,      none           wet bench
                                                     HM etch
───────────────────────────────────────────────────────────────────────────────────────────────
Verdict               baseline;      reference:      best tail;   compromise     impractical for
                      SiN and edge   gentle, slow    costly       for          tetragonal ZAZ
                      cost                           integration  throughput
```

The wet hybrid fails for a simple reason: crystalline ZrO₂ barely dissolves in dilute HF, while the SiN it lands on dissolves ten times faster. The hot route has the narrowest tail and fastest clear, but needs a hard mask over the plate and protection of the TE TiN at the plate edge, which reacts with chlorine at 250 °C (Book #32, Chapter 7). The reference ALE finish is the gentlest; the quasi-ALE finish is the cheapest step towards it.

---

## 10.8 Failure Modes

```
Symptom                         Likely cause                       First check
──────────────────────────────────────────────────────────────────────────────
Single contact opens at the     ring wear (R_slow up); main step   ring RF-hours; Al
edge dies                       short (Al-marker bias)             marker vs ALD
                                                                   thickness (Ch. 6, 8)
Single opens, whole wafer       EPC drop (purge, IEDF); BₓClᵧ      n₅₀, S₁ (Ch. 8); Cl₂
                                micromasking                       flow; TEM for B
Clusters of opens               wall flakes; PEZ flakes; ALD        particle monitors;
                                flakes                              flake composition
Opens near plate edges          veil fragments                      main-step time;
                                                                    resist sidewall
SiN loss high, uniform          SiN EPC up (13.56 MHz mode in       N₂ plateau per cycle
                                the ALE step, Ch. 5)
SiN loss high at fast sites     main step too long (marker          main-step time log
                                adaptation clipped)
ILD lifting in the periphery    B left on SiN (strip water off,      SIMS/TOF-SIMS B;
                                temperature low)                    strip log
```

---

## Summary and Key Takeaways

1. **The last dielectric is at the edge, at the plate foot, on step sidewalls, and in grain centres.** Only the first and the last matter for contacts.

2. **The Gaussian tail is designed small.** With 36 cycles, z ≈ 6.6 at the slowest site and about 0.35 residue opens per wafer, nearly all at the edge.

3. **Most module-2 opens are not Gaussian.** Particles, ALD flakes, BₓClᵧ micromasking, abnormal grains, and veils account for about 95%.

4. **Moving removal between steps barely helps.** A nanometre moved to the main step saves about five cycles and starts breaking through at the fast sites. Reducing σ_r is the real lever: 120 °C saves six cycles.

5. **The finish lands softly.** 0.35–0.42 nm of SiN loss everywhere, against 2–7 nm for a continuous overetch.

6. **Water finishes the job.** An O₂/H₂O strip at 250 °C removes the boron and chlorine before air can, and the short main step leaves veils too thin to stand.

---

## Study Questions

1. Compute z and P at the slowest site if the reference finish runs 34 cycles. How many residue opens per wafer would you expect from the slowest band?

2. Using Section 10.3.1, compute N for x = 4.2 nm. Plot N against x for the four values in the table and your new point. Where is the knee, and why?

3. A process change raises σ_r from 7.5% to 9% (for example a change in the crystalline texture of the ZAZ). How many extra cycles are needed at x = 4.44 nm? What is the throughput cost in the plate chamber?

4. The SiN EPC rises to 0.03 nm/cycle. Recompute the SiN loss at the fastest and slowest sites. Does the uniformity benefit over the continuous route survive?

5. Explain why a veil of 0.4 nm collapses while a veil of 1.0 nm stands. Estimate how much zirconium per centimetre of plate edge each represents (veil height 300 nm, ZrO₂-equivalent density).

6. A team proposes to drop the ALE finish and run a 120 °C continuous step with 30% overetch instead. Using the σ_r values of Section 10.3.2 and the selectivities of Chapter 3, estimate z, SiN loss, and step time. What would you check about the plate edge?

---

**Next Chapter:** [Chapter 11: The Two Edges — Plate Edge & Wafer Bevel](./11-dielectric-edges-plate-bevel.md)

---

**Chapter 10 Development Status:** Complete  
**Version:** 1.0
