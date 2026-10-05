# Chapter 6: Temperature, Ion Energy & Clearing Uniformity

## Overview

A blanket clear is finished when the last point on the wafer has cleared. Everywhere else, the overetch is spent on the landing film and on the plate edge. The time between the first and the last point to clear is therefore pure cost, and the purpose of uniformity engineering is to shrink it.

In D1, that time comes from three kinds of variation. The film is not the same everywhere: the ALD thickness and phase mix vary radially. The rate is not the same everywhere: ion flux, ion energy, and temperature vary, and at D1's low-energy operating point the rate is steeply sensitive to the last two. And the wafer edge is a region of its own, where the sheath bends, the edge ring wears, and heat escapes. This chapter quantifies each contribution, shows how source tuning, zone heaters, and feed-forward of the incoming film reduce them, and explains what atomic-layer etching does and does not fix.

**Learning Objectives:**
- Write the clearing-time spread in terms of thickness and rate variation
- Compute the contributions of ion flux, ion energy, and temperature to rate non-uniformity at the D1 operating point
- Describe the wafer-edge effects of sheath bending, ring wear, and heat loss, and their compensation
- Explain why D1 shows almost no loading, unlike the TiN etch-back of Book #32
- Use zone temperatures to compensate the radial signature of the incoming ZAZ
- Explain what ALE saturation does to rate non-uniformity and why it does not remove the effect of thickness non-uniformity

---

## 6.1 The Clearing-Time Spread

The local clearing time is the local thickness divided by the local rate:

```
t_c(r) = t(r) / R(r)

σ_tc / t_c ≈ √( (σ_t / t)² + (σ_R / R)² )
```

The overetch must carry the slowest site to clearing and then cover the local, grain-level spread there (Chapter 10). Every percent of wafer-level clearing spread adds about a percent to the required overetch time.

---

## 6.2 Contributions to Rate Non-Uniformity

### 6.2.1 Ion Flux

In the ion-assisted regime, the rate is proportional to the ion flux at fixed energy (the A of Chapter 3 contains Γ_i). An ICP source produces a plasma whose density depends on the coil geometry, pressure, and gas:

```
Radial ion-flux profile (illustrative, 8 mTorr BCl₃/Cl₂/Ar):
  Single planar coil              centre-high, ± 6% (range/2)
  Dual coil, current ratio tuned  ± 2%; 1σ ≈ 0.8%
```

### 6.2.2 Ion Energy

```
Rate sensitivity at the D1 operating point: 1.8% per eV (Chapter 3)

Sources of radial ion-energy variation:
  Bulk of the wafer      sheath voltage nearly uniform (conductive wafer,
                         one self-bias); ± 1 eV from plasma potential
                         variation → ± 1.8%
  Outer 5 mm             sheath bends at the wafer/ring step; energy and
                         angle change; ring wear lowers edge energy
```

### 6.2.3 Temperature

```
Rate sensitivity: 0.7% per °C (Chapter 3)

Chuck and wafer temperature non-uniformity (illustrative):
  Heater zones, steady state        ± 1.5 °C (3σ) → ± 1.0%
  Plasma heat load (centre-high)    centre + 2 °C under plasma unless the
                                    centre zone compensates
  Wafer edge (overhangs the puck)   − 3 to − 5 °C without edge-zone boost
  Backside He pressure variation    ± 3 °C per ± 20% conductance change
```

### 6.2.4 Rate Budget

```
Rate non-uniformity in D1 (1σ, illustrative):
                              Untuned     Tuned
  ───────────────────────────────────────────────
  Ion flux                    3.0%        0.8%
  Ion energy (bulk)           0.6%        0.6%
  Temperature                 1.5%        0.4%
  Total (bulk of the wafer)   3.4%        1.1%
```

---

## 6.3 Incoming Film Non-Uniformity

### 6.3.1 The ALD Signature

```
Periphery ZAZ thickness profile (illustrative):
  Radial signature        centre 5.35 nm → edge 5.48 nm (edge-thick; showerhead
                          and pedestal temperature profile of the ALD chamber)
  Random (die-to-die)     1σ ≈ 0.6%
  Total                   1σ ≈ 1.5%
Monoclinic fraction        higher at the edge (≈ 35%) than the centre (≈ 25%):
                          the plate depositions run hotter at the edge
                          → edge rate ≈ 1% lower
```

The film is thickest and slowest exactly where the plasma tends to be weakest: at the edge. Uncorrected, the edge clears last by a wide margin.

### 6.3.2 Feed-Forward Through Zone Temperatures

The ALD radial signature is stable from wafer to wafer and drifts slowly with the deposition chamber's state. It can be measured on periphery pads (ellipsometry, Chapter 15) and compensated by tilting the D1 zone temperatures:

```
Compensation (illustrative):
  Edge needs + 2.4% thickness + 1% phase = + 3.4% more removal
  At 0.7% per °C → edge zone + 5 °C relative to centre
  Result: radial clearing-time signature reduced from ≈ 3.4% to ≈ 0.5%
```

Temperature is the right actuator: it moves the rate smoothly over a radius of several centimetres, does not change the ion energy at the plate edge, and has no effect on the plasma itself.

---

## 6.4 The Wafer Edge

### 6.4.1 Sheath Bending

At the wafer edge, the sheath follows the step between the wafer and the edge ring. If the ring top is below the wafer surface, the sheath curves down, ions are tilted outward and focused, and the edge sees higher flux at an angle. If the ring is above the wafer, the reverse. The ring height is set so that the sheath is flat over the wafer at the start of the ring's life.

```
Edge effects (outer 3 mm, illustrative):
  Ion tilt at the edge        up to 2–3° with a worn ring
  Ion energy at the edge      falls ≈ 3 eV over the ring life (1500 RF h)
  ZrO₂ rate at the edge       − 5% over the ring life (at 1.8%/eV)
```

### 6.4.2 Tilt and the Plate Sidewalls

A tilted ion flux strikes one sidewall of every plate island at the edge of the wafer more than the other. On the outward-facing plate edges of edge dies, the TE TiN and SiGe see more ions; on the inward-facing ones, the floor next to the plate is partly shadowed. In D1, with a 260 nm-tall plate and a 3° tilt, the shadow on the floor is about 14 nm wide; it delays clearing in a strip 14 nm wide along every inward-facing plate edge at the wafer edge. This matters only if the overetch is short, but it is a reason the slowest sites on the wafer are often next to plate edges near the bevel (Chapter 10).

### 6.4.3 Compensation

```
Edge compensation options:
  Ring height adjustment       motorized ring lifts to restore the sheath;
                               compensates wear without breaking vacuum
  Edge-zone temperature        + 2 to + 5 °C restores rate; does not fix tilt
  Tunable edge electrode       RF applied to an electrode under the ring
                               restores edge ion energy and angle
  Ring replacement             at ≈ 1500 RF h (≈ 90,000 wafers at 61 s)
```

---

## 6.5 Loading

### 6.5.1 Why D1 Has Almost None

Book #32's TiN etch-back showed a 1.76-fold jump in the rate on the pillar tops when the field cleared, because the chlorine consumed by the field was suddenly available to a fifth of the area. D1 shows nothing comparable:

```
Reactant consumption in D1 (Chapter 3):
  Boron consumed as BOCl ≈ 0.5% of the BCl₃ flow
  Cl consumed by ZrCl₄ formation ≈ 0.5–1% of the Cl supply
  Global loading constant k ≈ 0.02 → rate change at clearing ≈ 1%
```

ZrO₂ etching is limited by ion-assisted lattice breaking, not by reactant supply. When the ZAZ clears, the ions go on arriving at the same rate, and the remaining grains etch at the same rate as before.

### 6.5.2 Pattern Loading at the Plate Edge

Near the plate sidewall, BₓClᵧ deposits more heavily (Chapter 3) and some of the deposited boron is resputtered onto the floor within a few tens of nanometres of the edge. The floor there etches 2–4% more slowly. Like the tilt shadow, this concentrates the last-clearing sites along plate edges.

---

## 6.6 The Wafer-Level Result

```
Clearing-time spread for D1 (1σ, illustrative):
                                      Untuned     Tuned + FF
  ─────────────────────────────────────────────────────────────
  Rate, bulk                          3.4%        1.1%
  Thickness and phase (radial)        2.0%        0.3%
  Thickness, random                   0.6%        0.6%
  Total, bulk                         4.0%        1.3%
  Edge, systematic (worn ring)        − 5% rate   compensated to ≈ 1%

Slowest site relative to the mean:   ≈ + 8%      ≈ + 3%
```

Tuned and fed forward, the slowest site on the wafer clears about 3% after the mean. That number enters the overetch calculation of Chapter 10: the reference 70% overetch, measured from the endpoint at the mean, leaves 1.70 / 1.03 − 1 = 65% for the slowest site.

---

## 6.7 Uniformity in Atomic-Layer Etching

### 6.7.1 What Saturation Fixes

In D2, every point on the wafer receives enough radicals in step A and enough ions in step B to saturate, so the EPC does not follow the flux or the dose:

```
EPC sensitivity in D2 (illustrative):
  Radical flux ± 30%                 EPC ± 0.5% (step A at 1.5 × knee)
  Ion flux ± 30%                     EPC ± 0.5% (step B at 2.5 × knee)
  Ion energy ± 5 eV (in window)      EPC ± 2%
  Temperature ± 3 °C (at 100 °C)     EPC ± 0.3%
  Wafer-level EPC uniformity         1σ ≈ 0.5%
```

### 6.7.2 What Saturation Does Not Fix

The number of cycles needed at each point is the local thickness divided by the EPC. A uniform EPC removes the rate term; the thickness term remains:

```
σ_N / N ≈ √( (σ_t / t)² + (σ_EPC / EPC)² ) = √(1.5² + 0.5²) ≈ 1.6%
```

Feed-forward of the thickness cannot be applied radially in ALE, because the EPC has been made insensitive to every actuator. Instead, the over-cycling covers it: 30% over-cycling is about nineteen times the wafer-level 1σ, and the remainder of the margin is spent on the grain-level spread (Chapter 10).

### 6.7.3 ALE at the Edge

At the wafer edge, the ion energy in step B falls a few electronvolts as the ring wears, but stays inside the 45–70 eV window. The EPC at the edge drops by about 1%, against 5% for D1. A worn ring that would require compensation in D1 is harmless in D2.

---

## Summary and Key Takeaways

1. **Clearing spread is thickness over rate.** Both terms matter; the overetch pays for both.

2. **At 70 eV, ion energy and temperature are steep levers.** 1.8% per eV and 0.7% per °C; flux tuning, zone heaters, and voltage control bring the bulk rate spread to about 1% (1σ).

3. **The incoming film is thickest and slowest at the edge.** Feed-forward through zone temperatures removes most of the radial signature.

4. **The wafer edge is its own process.** Ring wear lowers the edge energy and tilts the ions; movable rings or edge electrodes restore it.

5. **D1 has almost no loading.** The etch is ion-limited; the rate does not jump at clearing.

6. **ALE fixes rate non-uniformity, not thickness non-uniformity.** Over-cycling covers the thickness spread; the edge is nearly immune to ring wear.

---

## Study Questions

1. A new ALD chamber produces a centre-thick ZAZ (centre 5.48 nm, edge 5.35 nm). Compute the zone-temperature tilt needed to compensate it in D1. Does this conflict with the edge heat loss of Section 6.2.3?

2. The ring has run 1200 RF hours and the edge ion energy is 2.5 eV low. Compute the edge rate loss in D1 and in D2. For D1, how much edge-zone temperature boost compensates it?

3. Estimate the width of the shadowed floor strip next to a 260 nm plate edge for ion tilts of 1°, 2°, and 4°. At what tilt does the shadowed strip become wider than a periphery contact?

4. Explain why Book #32's TiN etch-back has a large loading jump at clearing and D1 does not. What would have to be true for D1 to show one?

5. Compute the slowest-site overetch for D1 with the untuned spread of Section 6.6. Is the reference 70% overetch still sufficient for the grain statistics of Chapter 10 (σ_g = 10%, z ≥ 6.4)?

6. The backside helium pressure drops 25% on one chuck. Using Chapter 5, estimate the wafer temperature change and the D1 rate change. Would endpoint detect it? Would anything else?

---

**Next Chapter:** [Chapter 7: ALE & Thermal-Etch Reactors](./07-ale-thermal-etch-reactors.md)

---

**Chapter 6 Development Status:** Complete  
**Version:** 1.0
