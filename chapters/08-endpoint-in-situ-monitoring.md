# Chapter 8: Endpoint & In-Situ Monitoring of a 5.5 nm Film

## Overview

Endpoint detection for the dielectric clear has to answer a question about a film that is gone in 36 s, that covers less than half the wafer, and whose products are diluted to two parts per thousand in the chamber gas. It has to answer it in time to start a timed overetch, and it has to answer it despite a chamber wall that is releasing the products of the previous wafer and a window that is slowly fogging with boron.

What makes the problem tractable is that the ZAZ is not one material. It has zirconium in it, which disappears from the gas at clearing. It has a 0.3 nm layer of aluminium oxide in the middle, which flashes briefly as the etch passes through it. It sits on silicon nitride, whose silicon and nitrogen appear when the ZAZ is gone. And all of its oxygen ends up bound to boron, whose oxide emission tracks how much oxide is being etched. This chapter describes those signals, how large they are, how an endpoint algorithm combines them, why optical interferometry is of no use here, and how atomic-layer etching is monitored when the process has no natural endpoint.

**Learning Objectives:**
- Estimate the product fluxes of Zr, Al, Si, and O during the clear and the size of each emission change
- Use the Al marker to measure the upper-film rate and predict the clearing time of each wafer
- Relate the width of the landing signal to the local clearing-time spread
- Explain why reflectance-based endpoint fails for ZAZ on SiN and where in-situ ellipsometry can help
- List endpoint failure modes and their fallbacks
- Design a per-cycle emission monitor and a feed-forward cycle count for ALE

---

## 8.1 What Must Be Detected

```
Timeline of D1 on the reference wafer (illustrative):
  0–3 s      BT: surface contaminants, top ≈ 0.65 nm of ZAZ
  3–16 s     upper ZrO₂ (1.95 nm remaining)
  16–19 s    Al₂O₃ insertion (0.3 nm)
  19–36 s    lower ZrO₂ (2.55 nm)
  ≈ 36 s     mean clearing: SiOₓNᵧ / SiN exposed over half the open area
  36–61 s    overetch (70% of 36 s)
```

The endpoint the recipe needs is the **mean clearing time**, t_EP. The overetch is then 0.70 × t_EP, so that a wafer with a thicker film or a slower chamber automatically gets a proportionally longer overetch.

---

## 8.2 Product Fluxes and Emission Signals

### 8.2.1 What Enters the Gas

```
Product generation rates (reference D1, illustrative):
                              During ZrO₂ etch     After clearing
  ────────────────────────────────────────────────────────────────
  Zr (from ZAZ, 318 cm²)       1.4 × 10¹⁷ s⁻¹       ≈ 0 (wall release
                                                    ≈ 2 × 10¹⁵ s⁻¹)
  O  (from ZAZ)                2.8 × 10¹⁷ s⁻¹       0
  O  (from oxide cap, 389 cm²) 5.7 × 10¹⁶ s⁻¹       5.7 × 10¹⁶ s⁻¹
  Si (from oxide cap)          2.8 × 10¹⁶ s⁻¹       2.8 × 10¹⁶ s⁻¹
  Si (from SiN, 318 cm²)       0                    5.6 × 10¹⁶ s⁻¹
  N  (from SiN)                0                    7.5 × 10¹⁶ s⁻¹
```

The oxide cap is a constant background of silicon and oxygen. At clearing, silicon rises threefold, total oxygen falls by about 80%, zirconium falls almost to zero, and nitrogen appears.

### 8.2.2 Emission Lines and Bands

```
Useful emission features (illustrative):
  Species     Wavelength (nm)            Behaviour at clearing
  ─────────────────────────────────────────────────────────────────────────
  Zr I        360.1, 351.9, 349.6        falls to wall baseline
  Al I        394.4, 396.2               brief peak at the insertion
  Si I        288.2; SiCl band 280–290   rises ≈ 3×
  BO (α band) ≈ 420–600 (several heads)  falls ≈ 80% (oxygen gettering ends
                                         on the open area)
  N₂ (2nd     337.1, 357.7               appears; weak in BCl₃/Ar
  positive)
  B I         249.7, 249.8               little change (BCl₃ is abundant)
  Cl I        837.6                      little change (loading ≈ 1%)
  Ar I        750.4, 811.5               actinometer reference
```

All signals are normalized to Ar I 750.4 nm (actinometry) to remove changes in electron density and temperature. Zr I 360.1 nm lies close to N₂ 357.7 nm, which rises at clearing; spectrometers with resolution better than 0.5 nm separate them.

### 8.2.3 Signal Size

```
Relative change at clearing (normalized, reference, illustrative):
  Zr I 360.1 / Ar       − 95% (from a weak baseline; S/N ≈ 10 at 0.2 s)
  Si I 288.2 / Ar       + 200% (S/N ≈ 30)
  BO band / Ar          − 75% (S/N ≈ 40; broad band, high counts)
  N₂ 337.1 / Ar         from ≈ 0 to detectable (S/N ≈ 8)
```

The Zr line is the most specific and the weakest: ZrCl₄ is the dominant product and only a fraction of it is dissociated to emitting Zr atoms. The BO band is the strongest: every oxygen atom removed from the film passes through boron. The Si line is the cleanest landing signal.

---

## 8.3 The Al Marker

### 8.3.1 The Signal

When the etch front reaches the 0.3 nm Al₂O₃ insertion, aluminium enters the gas for about 2.6 s at the mean, spread by the local clearing-time distribution. The Al I doublet at 394.4/396.2 nm rises from zero, peaks, and falls back.

```
Al marker (reference, illustrative):
  Peak centre       t_Al ≈ 17.3 s (3 s BT + 13.0 s upper ZrO₂ + half of 2.6 s)
  Width (FWHM)      ≈ 4 s (2.6 s intrinsic, broadened by the spread of the
                    upper-film clearing, σ ≈ 1.3 s at this depth)
  S/N               ≈ 15
```

### 8.3.2 Using It

The Al peak tells the controller how fast the upper ZrO₂ etched on this wafer, in this chamber, today:

```
Upper ZrO₂ rate:   R_u = t_upper / (t_Al − 3 s − 1.3 s)
                       = 1.95 nm / 13.0 s = 0.15 nm/s = 9.0 nm/min

Predicted mean clearing time:
  t_EP,pred = t_Al + 1.3 s + t_lower / R_u
            = 17.3 + 1.3 + 2.55 / 0.15 = 35.6 s
```

The prediction arrives 18 s before the event. It is used two ways. First, it sets a window for the landing-signal algorithm: an endpoint called far from the prediction is suspect. Second, it is a per-wafer measurement of the etch rate, which drifts with chamber state, and a feed-forward of what the clearing-time spread should be (Chapter 15).

### 8.3.3 The Width Is Information

The width of the Al peak above its intrinsic 2.6 s comes from the spread of local clearing times at mid-film. A peak that broadens from 4 s to 6 s, with the same centre, means the local spread has grown, from a higher monoclinic fraction, coarser grains, or a non-uniform BT, even though the mean rate has not changed. That is exactly the case in which the tail of the clearing-time distribution grows and the fixed 70% overetch may become insufficient.

---

## 8.4 The Landing Signal

### 8.4.1 Shape

As the ZAZ clears, the fraction of the open area exposing SiN rises from 0 to 1. The Si signal follows the cumulative distribution of local clearing times:

```
Fraction cleared F(t) = Φ((t − t_EP) / σ_tc)
  t_EP ≈ 36 s, σ_tc ≈ 0.10 × 36 ≈ 3.6 s (local spread, Chapter 10)
  10% → 90% rise: 2.56 σ_tc ≈ 9 s, from ≈ 31 to ≈ 41 s
```

### 8.4.2 Algorithm

```
Reference endpoint algorithm (illustrative):
  Signals       S1 = Si 288.2 / Ar 750.4;  S2 = BO band / Ar;  S3 = Zr 360.1 / Ar
  Window        open from t_EP,pred − 8 s to t_EP,pred + 10 s
  Trigger       S1 crosses 50% of its rise (baseline before the window,
                plateau estimated by fitting the rising edge)
                AND S2 has fallen past 50% of its drop
  Confirm       S3 below 30% of its pre-window level
  Then          OE = 0.70 × t_EP (≈ 25 s)
  Fallback      if no trigger by t_EP,pred + 10 s: t_EP = t_EP,pred, flag wafer
  Hard limit    t_EP ≤ 50 s; beyond it, abort to an engineering hold
```

Triggering at 50% of the rise, rather than at the end of the rise, places the endpoint at the mean clearing time regardless of how wide the spread is. The overetch is then sized against the spread separately (Chapter 10).

---

## 8.5 Optical Thickness Methods

### 8.5.1 Interferometry and Reflectometry

Endpoint by reflectance works when the etched film and the layer beneath differ in refractive index. ZAZ (n ≈ 2.15 at 633 nm, crystalline) on SiN (n ≈ 2.02) on oxide does not:

```
Reflectance change on removing 5.4 nm of ZAZ from the periphery stack
(illustrative, normal incidence, 633 nm):    ΔR/R ≈ 0.1%
Plasma emission noise at the detector:       ≈ 0.5%
```

The film is optically nearly the same as a few nanometres of extra nitride. Reflectometry cannot see it go.

### 8.5.2 In-Situ Ellipsometry

Ellipsometry measures the change of polarization on reflection at oblique incidence, and it is sensitive to 0.05 nm on a well-characterized stack. A spectroscopic ellipsometer mounted on a chamber at about 70° incidence, focused on a large open pad, can follow the ZAZ thickness in real time:

```
In-situ ellipsometry limits (illustrative):
  Spot             ≈ 50 × 150 µm (elongated at 70°); needs an open pad
  Precision        ≈ 0.05 nm per second of averaging
  Problems         two windows that fog with BₓClᵧ (must be heated and
                   shielded); plasma light; wafer temperature changes n;
                   the pad is one point, not the wafer
```

It is a development and qualification tool. It measures the rate and the shape of the clearing on one pad with a precision no emission signal can match, and it is how the calibration curves of Chapters 3 and 4 are best obtained. In production, it adds cost and maintenance for a measurement at one point, and emission is preferred.

---

## 8.6 Endpoint Failure Modes

```
Failure mode                          Symptom                      Fallback / fix
──────────────────────────────────────────────────────────────────────────────────────
Viewport fogging (BₓClᵧ, ZrOClₓ)      all signals fall with time;  heated, recessed,
                                      S/N drops                    purged viewport;
                                                                   intensity normalization
Zr wall release (after many wafers    Zr baseline high; S3 never   confirm on S1/S2 only;
or after a wet clean)                 confirms                     season (Ch. 9)
Wide clearing spread (grain size,     slow S1 rise; trigger at     Al-peak width alarm;
monoclinic fraction)                  correct mean, OE short for   raise OE (Ch. 10)
                                      the tail
Pattern change (test wafers,          different background from    product-specific
different open area)                  cap; S1 step smaller         thresholds
Weak BT (Ti, C, F surface)            delayed start; Al peak late  predicted EP follows;
                                      and broad                    BT check (Ch. 2)
No Al insertion (variant stacks)      no marker                    timed prediction from
                                                                   upstream thickness
```

The most dangerous of these is the third: the endpoint is called correctly, at the mean, and the wafer is under-etched in its tail because the spread grew. Nothing in the landing signal itself is wrong. Only the width of the Al peak, or the slope of the Si rise, carries the warning.

---

## 8.7 Monitoring ALE

### 8.7.1 Per-Cycle Emission

In D2, each cycle's step B removes about 0.1 nm, and the zirconium leaves during step B. Integrating the Zr emission over step B of each cycle gives a per-cycle removal signal:

```
Per-cycle signals (D2, illustrative):
  Zr I 360.1, integrated over step B     flat for ≈ 20 cycles; dips at the
                                         Al insertion (cycles ≈ 25–29);
                                         falls to baseline by cycle ≈ 60
  Al I 396.2, integrated over step B     peak at cycles ≈ 25–29
  Si I 288.2, integrated over step B     rises from cycle ≈ 50
```

The per-cycle signal is weaker than D1's continuous signal, because 0.1 nm leaves in 2.5 s (0.04 nm/s against 0.15 nm/s). Integrating over each step B restores the counts.

### 8.7.2 Endpoint Cycle Versus Fixed Count

```
Two ways to end D2:
  Fixed count       N = 73 (56 nominal + 30%), adjusted per lot by
                    feed-forward: N = 1.3 × ((t_in − 0.3) / EPC + 3.75),
                    the 3.75 cycles being the 0.3 nm Al₂O₃ insertion
  Detected          N_EP = cycle at which the Si per-cycle signal reaches 50%
                    of its rise; then over-cycle 0.30 × N_EP
```

Because the EPC is stable, the fixed count with thickness feed-forward is the reference method. The per-cycle emission confirms it: a wafer whose Si rise comes five cycles late is flagged, because in ALE that can only mean a thicker film or a weaker cycle, and both need attention.

---

## Summary and Key Takeaways

1. **The endpoint is the mean clearing time.** Overetch is a fixed fraction of it, so thickness and rate variations scale the overetch automatically.

2. **Four signals carry the information:** Zr falls, Si rises, BO falls, and Al flashes at mid-film. The cap's constant Si and O are the background.

3. **The Al marker predicts the endpoint 18 s early** and its width measures the local clearing spread, the quantity the overetch must cover.

4. **Reflectometry cannot see ZAZ on SiN.** Their refractive indices differ by about 6%; in-situ ellipsometry can, but on one pad and with fogging windows.

5. **The most dangerous failure is a correct endpoint with a wider tail.** Watch the Al-peak width and the slope of the Si rise.

6. **ALE is counted, not detected.** A feed-forward cycle count is the reference; per-cycle emission confirms it.

---

## Study Questions

1. The plate coverage rises to 60% on a new product. Recompute the Si and O fluxes before and after clearing in Section 8.2.1. Which signal loses the most contrast?

2. On one wafer the Al peak centre is at 19.0 s instead of 17.3 s. Compute the upper-film rate and the predicted t_EP. Which incoming or chamber causes could explain it?

3. The Al peak FWHM grows from 4 s to 6 s. Estimate the new local clearing-time spread at mid-film and at full clearing (assume the spread scales with depth). What overetch would keep z ≥ 6.4 for σ_g at full clearing?

4. Show that ΔR/R for removing 5.4 nm of a film with n = 2.15 from a substrate of n = 2.02 is of order 0.1% at 633 nm. (Use the thin-film approximation.)

5. Design the per-cycle Zr signal integration for D2: how many cycles of baseline are needed to estimate the plateau, and how quickly after the Si rise begins can the endpoint cycle be called with S/N ≥ 5 if each cycle's integrated Si signal has S/N = 2?

6. The viewport transmission falls 30% over 500 wafers. Which normalization keeps the endpoint working, and which signal fails first if the fogging is wavelength-dependent (stronger in the UV)?

---

**Next Chapter:** [Chapter 9: Walls, Boron Deposits, Zirconium Contamination & the Bevel](./09-walls-boron-zirconium-bevel.md)

---

**Chapter 8 Development Status:** Complete  
**Version:** 1.0
