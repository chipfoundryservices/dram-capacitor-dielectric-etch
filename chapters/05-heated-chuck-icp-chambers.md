# Chapter 5: Heated-Chuck ICP Chambers for Dielectric Clearing

## Overview

The reference dielectric clear D1 asks for a combination that conductor etch chambers are not built for: a wafer at 250 °C, ions at a well-controlled 70 eV with a flux of 2 × 10¹⁶ cm⁻² s⁻¹, a BCl₃-rich chemistry, and walls that neither release fluorine from earlier steps nor collect zirconium for later wafers. The inductively coupled plasma (ICP) source supplies the flux and the low energy independently. The rest of the chamber, the chuck, the walls, the window, the edge ring, the gas lines, and the exhaust, must be designed around temperature and around boron trichloride, which attacks most of the ceramics etch chambers are made of.

This chapter explains why the dielectric clear gets its own chamber, how an ICP source sets ion energy and flux, how a chuck holds a wafer at 250 °C while the plasma heats it, what the chamber surfaces must be made of, how BCl₃ is delivered and exhausted, and how the hot chamber fits on the plate-etch mainframe.

**Learning Objectives:**
- Give the reasons for separating the dielectric clear from the plate conductor etch
- Compute ion current, ion energy, and bias power for the D1 operating point
- Describe a Johnsen–Rahbek chuck for 250 °C, its heat balance, and the wafer heat-up sequence
- Choose wall, window, liner, and edge-ring materials for BCl₃/Cl₂ at elevated temperature
- Describe BCl₃ delivery, moisture control, and exhaust handling
- Lay out a split-route mainframe and identify its throughput bottleneck

---

## 5.1 Why a Separate Chamber

```
Reasons to move the high-k step out of the plate conductor chamber:

1. Temperature    The conductor steps run at 60 °C (SiGe lateral etch and resist
                  limits). The dielectric clear wants 250 °C. A chuck cannot
                  swing 190 °C per wafer: its thermal time constant is minutes.
2. Mask           Resist does not survive 250 °C. The hot route needs the
                  oxide cap and a strip before the clear.
3. Chemistry      The conductor chamber carries fluorine from the W step on its
                  walls (Chapter 2); a dedicated chamber starts the ZAZ clear
                  on a fluorine-free wall.
4. Zirconium      Zr deposits only where ZrO₂ is etched. Confining that to one
                  chamber type confines the Zr cleaning problem.
5. Time           The cold in-situ high-k step took 93 s of a 212 s plate recipe.
                  Moving it out rebalances the mainframe.
```

The cost is a strip step and a transfer between chambers, both under vacuum, and a mainframe position for each hot chamber.

---

## 5.2 The ICP Source

### 5.2.1 Why ICP

An inductively coupled source produces its plasma with a coil outside a dielectric window; the wafer bias is supplied separately. Ion flux is set mainly by source power, ion energy mainly by bias power. For an etch that needs a high flux at a low and well-controlled energy, that independence is essential. A capacitively coupled chamber could reach 70 eV only at low power and low flux, or would need a dual-frequency arrangement to separate the two.

### 5.2.2 Ion Flux and Energy

```
Ion flux (reference D1, illustrative):
  n_e ≈ 1.5 × 10¹¹ cm⁻³ at the sheath edge, T_e ≈ 3.5 eV, mean ion mass ≈ 71 amu
  Bohm velocity u_B = √(kT_e/M) ≈ 2.2 km/s
  Γ_i = 0.61 n_e u_B ≈ 2.0 × 10¹⁶ cm⁻² s⁻¹
  Ion current density J_i ≈ 3.2 mA/cm²; total on 300 mm: I_i ≈ 2.3 A

Ion energy:
  E_i ≈ e (V_p + P_bias / I_i)
  ME/OE:  V_p ≈ 15 V; P_bias = 120 W → 52 V → E_i ≈ 67 ≈ 70 eV
  BT:     P_bias = 200 W → 87 V → E_i ≈ 102 ≈ 100 eV
```

The relation is approximate (the bias waveform, the sheath capacitance, and the ion mass mix all enter), but it shows the main sensitivity: at fixed bias power, the ion energy varies inversely with ion current. If the source power or the gas mix drifts so that I_i falls by 10%, the ion energy rises by about 6 eV. The yield per ion rises by about 10%, which roughly offsets the lower flux, so the ZrO₂ rate barely moves and the drift goes unnoticed by endpoint. Everything that depends on energy rather than rate, sputtering of the cap and the edge ring, the ion energy window of the plate edge, and damage, moves with it. Production chambers therefore control the bias voltage (V_pp or V_dc measured at the chuck) rather than the bias power.

### 5.2.3 Bias Frequency and Ion Energy Spread

```
Ion energy distribution width at the wafer (illustrative):
  Bias 13.56 MHz, BCl₂⁺ (81 amu), sheath ≈ 0.3 mm   ΔE ≈ 15–20 eV (bimodal)
  Bias 2 MHz                                          ΔE ≈ 60–80 eV
```

At 70 eV mean energy, a bimodal distribution 15–20 eV wide places part of the ion flux near 55 eV and part near 80 eV. Higher-frequency bias narrows the spread and keeps the low-energy peak above the threshold region where BₓClᵧ deposition competes (Chapter 3). The reference uses 13.56 MHz bias.

---

## 5.3 The Heated Chuck

### 5.3.1 Chuck Type

```
Electrostatic chuck options at 250 °C (illustrative):
  Type                  Dielectric       Behaviour at 250 °C
  ──────────────────────────────────────────────────────────────────────────
  Coulombic             high-ρ Al₂O₃     resistivity falls; leakage current
                                         rises; clamping becomes erratic
  Johnsen–Rahbek (J-R)  doped AlN        designed for 10⁹–10¹¹ Ω·cm at
                                         operating T; strong clamping at low
                                         voltage; reference choice
```

AlN has high thermal conductivity (about 100 W/m·K for chuck grades), resists chlorine better than Al₂O₃, and can be doped to the moderate resistivity a J-R chuck needs at 250 °C. Resistive heater elements embedded in the AlN, in four radial zones, set the temperature.

### 5.3.2 Heat Balance

At 250 °C the chuck must be heated, and the plasma also heats the wafer. The chuck balances the two:

```
Heat into the wafer during D1 (illustrative):
  Ion power: I_i × E_i ≈ 2.3 A × 67 V                         ≈ 155 W
  Electron and recombination heating, radiation from source   ≈ 150 W
  Total plasma heat load                                      ≈ 300 W
  Heat flux                                                   ≈ 0.43 W/cm²

Chuck construction:
  AlN puck with heaters (up to ≈ 2 kW) ─ thermal break ─ cooled base (≈ 50 °C)
  Heater power at idle ≈ 1.2 kW; during plasma ≈ 0.9 kW
  Backside He: 10 Torr; wafer-to-puck conductance ≈ 0.03 W/cm²·K
  Wafer above puck under plasma: ΔT ≈ 0.43 / 0.03 ≈ 14 °C
```

The wafer runs about 14 °C hotter than the puck while the plasma is on. The puck setpoint is about 236 °C for a 250 °C wafer, and the controller reduces heater power when the plasma strikes. The 14 °C offset is a calibration quantity: if the backside helium pressure changes by 20%, the offset changes by about 3 °C, and the ZrO₂ rate by about 2% (Chapter 6).

### 5.3.3 Heat-Up

A wafer arrives from the strip chamber at about 200 °C, or from a cooler station near 25 °C. It must not be clamped cold:

```
Thermal expansion of a 300 mm wafer from 25 to 250 °C:
  ΔL = α ΔT r = 2.6 × 10⁻⁶ × 225 × 150 mm ≈ 88 µm at the edge
```

A wafer clamped cold and then heated slides 88 µm across the chuck surface at its edge, scraping particles from both. The sequence is therefore:

```
Heat-up sequence (reference):
  1. Wafer placed on lift pins 1 mm above the chuck, Ar at 2 Torr      8 s
     (gas conduction and radiation preheat; wafer from strip at ≈ 200 °C)
  2. Lower onto chuck, clamp at low voltage, He backside on            3 s
  3. Stabilize to ±2 °C of setpoint                                    10 s
  4. Strike and run D1                                                 61 s
  5. Dechuck (J-R residual-charge discharge), lift                     5 s
Chamber time per wafer, including transfer and pump (≈ 15 s)          ≈ 102 s
```

About 40% of the chamber time is spent on thermal and transfer overhead. A wafer arriving cold instead of from the strip chamber adds about 15 s. Mainframes that place the strip immediately before the hot chamber, and keep the wafer under vacuum between them, save that time.

### 5.3.4 Dechucking

J-R chucks hold residual charge at high temperature, and a wafer can stick or jump when the lift pins rise. The dechuck uses a reverse-polarity pulse and a low-power Ar plasma to neutralize the surface, and the lift-pin force is monitored. A wafer that sticks is a broken wafer and an hours-long recovery.

---

## 5.4 Materials That BCl₃ Does Not Consume

### 5.4.1 The Problem

BCl₃ was chosen because it takes oxygen from metal oxides. Etch chambers are lined with metal oxides: anodized aluminium (amorphous Al₂O₃), sintered Al₂O₃ windows and rings, quartz. All of them are etched to some degree by the same chemistry that clears the ZAZ:

```
Erosion of chamber materials in BCl₃/Cl₂ at wall-sheath energies
(≈ 15–25 eV, 120 °C, illustrative relative rates):
  Material                    Relative erosion   Product / contaminant
  ────────────────────────────────────────────────────────────────────
  Anodized Al (Al₂O₃)         1.0 (reference)    AlCl₃; Al particles
  Sintered Al₂O₃              0.6                AlCl₃
  Quartz (SiO₂)               0.8                SiCl₄; window thinning
  SiC                         0.5                SiCl₄; C
  AlN                         0.3                AlCl₃; N₂
  Y₂O₃ (plasma spray)         0.05               YCl₃ (low volatility,
                                                 stays as a skin)
  YOF / Y₂O₃ (aerosol dep.)   0.03               denser; fewer particles
```

Yttria resists because YCl₃ is not volatile (it melts at 721 °C) and Y–O is among the strongest metal–oxygen bonds. Its surface chlorinates to a thin YOCl skin that slows further attack. The reference chamber lines every plasma-facing surface with yttria-based coatings.

### 5.4.2 The Window

The ICP coil couples through a dielectric window. The coil's capacitive coupling raises the window potential, and ions sputter it at energies higher than the walls see. A bare Al₂O₃ or quartz window erodes measurably in BCl₃ and becomes a source of Al or Si contamination and of particles. The reference window is Al₂O₃ with a dense Y₂O₃ coating on the plasma side, heated to 120 °C, with a Faraday shield between the coil and the window to reduce capacitive coupling.

### 5.4.3 The Edge Ring

```
Edge-ring materials (illustrative):
  Quartz          eroded by BCl₃; edge ion energy drifts quickly
  Si              etched by Cl (fast); not used
  SiC             slower; C contamination
  Y₂O₃ (bulk)     slow erosion; brittle; reference choice
```

The edge ring sets the sheath shape and ion energy at the wafer edge. At D1's 1.8% per eV rate sensitivity, a ring that erodes and lowers the edge ion energy by 3 eV over its life shifts the edge rate by 5%. The ring material and its replacement interval are part of the uniformity budget (Chapter 6).

### 5.4.4 Wall Temperature

```
Wall and liner temperature (reference 120 °C), reasons:
  Higher is better for:    less BₓClᵧ and ZrOClₓ adsorption; faster
                           outgassing of HCl and moisture after cleans;
                           more stable wall state wafer to wafer
  Higher is worse for:     elastomer seals (perfluoroelastomer ≤ 200 °C,
                           with margin ≈ 150 °C); coating stress from CTE
                           mismatch; heated-line and valve costs
```

---

## 5.5 Gas Delivery and Exhaust

### 5.5.1 BCl₃

```
BCl₃ properties relevant to delivery:
  Boiling point 12.5 °C; vapor pressure ≈ 1.3 bar at 20 °C
  Reacts with moisture: BCl₃ + 3 H₂O → B(OH)₃ + 3 HCl
```

BCl₃ is delivered from a liquid cylinder at its own vapor pressure, which is barely above atmospheric. Lines and mass-flow controllers are heated to about 40 °C to prevent recondensation where pressure drops. Any moisture in the line makes boric acid particles and HCl, which corrode stainless steel and release iron and nickel. Cylinder changes are followed by long purge-and-pump cycles (Appendix C).

### 5.5.2 Residence Time

```
Chamber volume ≈ 40 L; pressure 8 mTorr; flow 150 sccm (≈ 1.9 Torr·L/s)
Residence time τ = pV / Q ≈ 8 × 10⁻³ × 40 / 1.9 ≈ 0.17 s
```

A short residence time keeps the dilute ZrCl₄ and boron oxychloride products moving toward the pump rather than back toward the wafer and walls.

### 5.5.3 Exhaust

The products are ZrCl₄, AlCl₃, (BOCl)₃, BCl₃, HCl (from hydrogen on the surfaces), and SiCl₄. In the foreline they cool and can condense or react with moisture to form boron and zirconium oxides. Forelines are heated to about 100 °C up to the dry pump, and the exhaust passes through a wet or burn-wet scrubber that converts BCl₃ and HCl to borates and chlorides.

---

## 5.6 The Hot Chamber on the Mainframe

```
Split-route plate mainframe (reference, illustrative):

          ┌──────────── vacuum transfer module ────────────┐
          │                                                │
   [ C1 ] [ C2 ] [ C3 ]   [ S1 ] [ S2 ]   [ D1-a ] [ D1-b ]
   conductor etch, 60 °C  strip/PET,      hot dielectric
   cap open → W → SiGe    250 °C           clear, 250 °C
   → TiN (stop on ZAZ)

Wafer path:  C (≈ 180 s) → S (strip, ≈ 50 s) → D1 (≈ 102 s) → S (PET, ≈ 50 s)
                                                                → load lock
```

```
Throughput by chamber group (illustrative):
  Group     Chambers   Time per wafer   Capacity (wph)
  ────────────────────────────────────────────────────
  C         3          180 s            60
  S         2          100 s (2 visits) 72
  D1        2          102 s            71
  Mainframe                             ≈ 60 (limited by C)
```

The two hot chambers have spare capacity; the conductor chambers set the pace. Moving the dielectric step out of them is what raised their throughput, from about 50 wafers per hour on Book #32's in-situ route to about 60 here. Chapter 16 sizes the fab and compares the cost.

For the ALE route D2, each wafer occupies an ALE chamber for about 6.5 min including overhead, about 9 wafers per hour per chamber. Matching the 60-wafer-per-hour conductor group would need seven ALE chambers, more positions than a mainframe has. D2 therefore runs on its own ALE mainframe, or as a short finishing step after a shortened D1 (Chapter 14).

---

## Summary and Key Takeaways

1. **The dielectric clear gets its own chamber** because of temperature, mask, chemistry isolation, zirconium confinement, and throughput balance.

2. **ICP separates flux from energy.** D1 runs at 2 × 10¹⁶ cm⁻² s⁻¹ and about 70 eV; bias voltage, not power, should be controlled because energy varies inversely with ion current.

3. **A J-R AlN chuck holds 250 °C.** The plasma adds about 14 °C on top; backside helium sets that offset.

4. **Never clamp a cold wafer on a hot chuck.** Expansion of 88 µm at the edge scrapes particles; preheat on pins, then clamp.

5. **BCl₃ eats oxide chamber parts.** Yttria coatings, a coated and shielded window, and a yttria edge ring keep Al, Si, and particles out.

6. **The conductor chambers set the mainframe pace.** Two hot chambers serve three conductor chambers at about 60 wafers per hour; ALE needs a mainframe of its own.

---

## Study Questions

1. The source power is reduced so that n_e falls by 15%. At constant bias power, estimate the new ion energy, the yield per ion, and the net change in ZrO₂ rate in D1. What would happen with bias-voltage control instead?

2. Compute the wafer-to-chuck temperature offset if the backside helium leaks and the conductance falls to 0.02 W/cm²·K. What is the effect on the ZrO₂ rate?

3. Estimate the time constant for a 300 mm wafer (775 µm, c = 0.75 J/g·K) to approach chuck temperature with a conductance of 0.03 W/cm²·K. How many time constants are needed to get within 2 °C from 200 °C?

4. A quartz window erodes at 2 nm per wafer in the reference chemistry. How many wafers until 1 mm is gone? What contaminant reaches the wafers, and why is erosion of the window worse than erosion of the walls?

5. Rebalance the mainframe of Section 5.6 if the conductor recipe is shortened to 150 s. How many hot chambers are now needed, and what is the new bottleneck?

6. Explain why BCl₃ lines are heated even though BCl₃ is a gas at room temperature.

---

**Next Chapter:** [Chapter 6: Temperature, Ion Energy & Clearing Uniformity](./06-temperature-ion-energy-uniformity.md)

---

**Chapter 5 Development Status:** Complete  
**Version:** 1.0
