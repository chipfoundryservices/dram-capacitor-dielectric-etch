# Appendix E: Clearing, ALE & Edge Calculations

Closed-form models used in this book, with the reference worked example for each. All models are deliberately simple; each lists its main assumptions.

---

## E.1 Capacitance and Leakage Budget (Ch. 1)

```
C_s = ε₀ · 3.9 · A / EOT;   k_eff = 3.9 · t_phys / EOT;   J_max = I_max / A

Reference: A = π × 28 nm × 1410 nm = 1.24 × 10⁻⁹ cm²; EOT = 0.50 nm
  C_s = 8.85 × 10⁻¹² × 3.9 / 0.5 × 10⁻⁹ × 1.24 × 10⁻¹³ m² = 8.6 fF
  k_eff = 3.9 × 5.5 / 0.50 ≈ 43
  I_max = 1 fA → J_max ≈ 8 × 10⁻⁷ A/cm²;  field at 0.55 V: 1.0 MV/cm
```

---

## E.2 Zirconium Inventory and Residue Specification (Ch. 1)

```
n_Zr = ρ N_A / M;   areal density per nm = n_Zr × 10⁻⁷ cm

  ZrO₂ tetragonal: 6.1 / 123.2 × 6.02 × 10²³ = 3.0 × 10²² cm⁻³ → 3.0 × 10¹⁵ cm⁻² per nm
  Monolayer (≈ 0.28 nm) ≈ 8.3 × 10¹⁴ cm⁻²
  Periphery ZrO₂ 5.1 nm → 1.5 × 10¹⁶ cm⁻²
  Spec 1 × 10¹³ → 1.2% of a monolayer → 99.93% removal
```

---

## E.3 Dielectric Accounting (Ch. 1)

```
Area inside the plate ≈ A_wafer × f_plate × f_array × SEF + other surfaces
  707 × 0.55 × 0.70 × 71 ≈ 19,500 cm² (pillars) + ≈ 2,500 (supports etc.)
  ≈ 2.2 m²;  periphery 707 × 0.45 = 318 cm² → ≈ 1.4% of the film
SEF (surface enhancement) = pillar area / cell area = 1.24 × 10⁵ / 1734 ≈ 71
```

---

## E.4 Halide Vapor Pressure (Ch. 3)

```
ln(p / p₀) = −(ΔH_sub / R)(1/T − 1/T₀)

ZrCl₄: ΔH_sub ≈ 110 kJ/mol, T₀ = 604 K, p₀ = 760 Torr → ΔH/R ≈ 13,200 K
  250 °C (523 K): ln(p/760) = −13,200 × (1.912 − 1.656) × 10⁻³ = −3.39 → p ≈ 26 Torr
  60 °C (333 K): ln(p/760) = −17.8 → p ≈ 1.4 × 10⁻⁵ Torr
```

---

## E.5 Reaction Enthalpy (Ch. 3)

```
ΔH = Σ ΔH_f(products) − Σ ΔH_f(reactants)

ZrO₂ + 4/3 BCl₃ → ZrCl₄(s) + 2/3 B₂O₃
  = (−981 + 2/3 × −1274) − (−1101 + 4/3 × −403) = −1830 − (−1638) ≈ −191 kJ/mol
```

---

## E.6 Threshold-Yield Model (Ch. 3, 6)

```
R(E, T) = A(T)(√E − √E_th(T))
d ln R / dE = 1 / (2√E (√E − √E_th))

Reference (250 °C): A = 2.76, E_th = 25 eV
  R(70) = 2.76 × (8.37 − 5.00) = 9.3 nm/min
  d ln R / dE = 1 / (2 × 8.37 × 3.37) = 1.8% per eV
  SiN: 1.05 × (8.37 − 5.48) = 3.0 nm/min → selectivity 3.1
Yield per ion: Y = R n / Γ_i = 1.5 × 10⁻⁸ × 3.0 × 10²² / 2 × 10¹⁶ ≈ 0.022
```

---

## E.7 Ion Flux and Energy (Ch. 5)

```
Γ_i = 0.61 n_e u_B;  u_B = √(kT_e / M);  E_i ≈ e(V_p + P_bias / I_i)

  n_e = 1.5 × 10¹¹ cm⁻³, T_e = 3.5 eV, M = 71 amu → u_B = 2.2 km/s
  Γ_i = 2.0 × 10¹⁶ cm⁻² s⁻¹; I_i (300 mm) = 2.3 A
  ME: 120 W / 2.3 A = 52 V + 15 V → ≈ 67 eV; BT: 200 W → ≈ 102 eV
```

---

## E.8 Chuck Heat Balance and Heat-Up (Ch. 5)

```
ΔT_wafer–puck = q / h;   τ = (ρ c d) / h;   ΔL = α ΔT r

  q = 300 W / 707 cm² = 0.43 W/cm²; h = 0.03 W/cm²·K → ΔT ≈ 14 °C
  ρ c d = 2.33 × 0.75 × 0.0775 ≈ 0.135 J/cm²·K → τ ≈ 4.5 s
  From 200 °C to within 2 °C of 250 °C: ln(50/2) ≈ 3.2 τ ≈ 14 s
  ΔL = 2.6 × 10⁻⁶ × 225 × 150 mm ≈ 88 µm
```

---

## E.9 Clearing-Time Spread and Zone Feed-Forward (Ch. 6)

```
σ_tc / t_c = √((σ_t/t)² + (σ_R/R)²)
Zone tilt ΔT_zone = (Δt/t + Δphase) / (d ln R / dT)

  Edge +2.4% thickness, +1% phase → +3.4% / 0.7% per °C ≈ +5 °C at the edge
  Tuned bulk spread: √(1.1² + 0.3² + 0.6²) ≈ 1.3% (1σ); slowest site ≈ +3%
```

---

## E.10 Endpoint Prediction From the Al Marker (Ch. 8)

```
R_u = t_upper / (t_Al − t_BT − t_Al₂O₃/2)
t_EP,pred = t_Al + t_Al₂O₃/2 + t_lower / R_u

  t_Al = 17.3 s, t_BT = 3 s, t_Al₂O₃ = 2.6 s, t_upper = 1.95 nm, t_lower = 2.55 nm
  R_u = 1.95 / 13.0 = 0.15 nm/s;  t_EP,pred = 17.3 + 1.3 + 17.0 = 35.6 s
Landing-signal width (10–90%) = 2.56 σ_tc ≈ 2.56 × 3.6 s ≈ 9 s
```

---

## E.11 Product Fluxes (Ch. 3, 8)

```
Φ = A_open × R × n

  Zr: 318 cm² × 1.5 × 10⁻⁸ cm/s × 3.0 × 10²² cm⁻³ = 1.4 × 10¹⁷ s⁻¹
  Mole fraction in 150 sccm (6.7 × 10¹⁹ s⁻¹): 2 × 10⁻³ → 2 × 10⁻⁵ Torr at 8 mTorr
  Si from SiN after clearing: 318 × 5 × 10⁻⁹ × 3.5 × 10²² = 5.6 × 10¹⁶ s⁻¹
  Si from cap: 389 × 3.3 × 10⁻⁹ × 2.2 × 10²² = 2.8 × 10¹⁶ s⁻¹
```

---

## E.12 Domain Clearing Statistics (Ch. 10)

```
z = ((1 + OE)/s − 1) / σ_g;   P = ½ erfc(z/√2)
N_contacts = 1.2 × 10⁸ P;   N_anywhere = 9 × 10¹⁰ P   (per die)

  D1: σ_g = 0.10, OE = 0.70, s = 1.03 → z = 6.50, P = 3.9 × 10⁻¹¹
      → 0.0047 domains under contacts per die (≈ 0.002 fatal)
  D2: σ_g = 0.04, 73/56 cycles, s = 1.03 → z = 6.6, P = 1.6 × 10⁻¹¹ → 0.0019
  T:  σ_g = 0.12, 190/107 cycles → z = 6.5, P = 5 × 10⁻¹¹ → 0.006
Required OE for z: OE = s(1 + z σ_g) − 1;  z = 6.4, σ_g = 0.10, s = 1.03 → 69%
```

---

## E.13 Island Budget (Ch. 10)

```
f_c = (N_c × a_c) / A_periphery;   N_islands,max = target / f_c

  f_c = 3 × 10⁷ × 1600 nm² / 0.36 cm² = 4.8 × 10⁻⁴ / 0.36 ≈ 1.3 × 10⁻³
  N_islands,max = 0.01 / 1.3 × 10⁻³ ≈ 8 per die ≈ 20 per cm² of periphery
```

---

## E.14 ALE Cycle Count, Synergy, and Purge (Ch. 4, 7)

```
N = (1 + f_over) × Σ t_i / EPC_i;   S = (EPC − α − β) / EPC;   f_res = exp(−t/τ), τ = pV/Q

  D2: (2.55/0.10 + 0.3/0.08 + 2.55/0.10) ≈ 54.75 → ≈ 56 with phase mix; × 1.3 → 73
      time = 73 × 5.0 s = 365 s; SiN loss = 17 × 0.012 = 0.2 nm
  S = (0.10 − 0.002 − 0.008) / 0.10 = 90%
  Purge: V = 15 L, p = 15 mTorr, Q = 12.7 Torr·L/s → τ = 0.018 s; 1% in 0.08 s
```

---

## E.15 Isotropic Undercut (Ch. 4, 11)

```
u_top ≈ t_rem;   u_bottom ≈ t_rem − t_f   (film capped above, isotropic removal)

  Thermal ALE, 139 cycles: t_rem = 1.3 × 5.4 = 7.0 nm → u_top 7.0, u_bottom 1.6 nm
  Thermal ALE, 190 cycles: t_rem = 1.78 × 5.4 = 9.6 nm → u_top 9.6, u_bottom 4.2 nm
```

---

## E.16 Lateral Recess and Interface Diffusion (Ch. 11)

```
Recess = R_lat × t;   R_lat(T₂) = R_lat(T₁) exp[(E_a/k)(1/T₁ − 1/T₂)];   L_d = √(D t)

  TE TiN: 1.2 nm/min × 61 s = 1.2 nm;  E_a ≈ 0.3 eV → × 2.0 from 200 to 250 °C
  Cl along TiN/ZAZ: D_i ≈ 10⁻¹⁴ cm²/s, t = 61 s → L_d ≈ 8 nm
```

---

## E.17 Island Charging (Ch. 13)

```
J_diel = f_imb × J_i,side × A_side / A_diel

  J_i,side ≈ 0.1 mA/cm²; A_side = 4.6 mm × 195 nm = 9 × 10⁻⁴ cm²
  f_imb ≈ 0.1 → I ≈ 9 nA; A_diel ≈ 0.67 cm² → J ≈ 1.3 × 10⁻⁸ A/cm²
  ZAZ conducts 2 × 10⁻⁸ A/cm² at ≈ 0.5 V → V_diel < 0.5 V
  Charge over 61 s ≈ 8 × 10⁻⁷ C/cm²
```

---

## E.18 Inspection Sampling (Ch. 15)

```
λ = ρ A;   P(k) = λᵏ e^(−λ) / k!;   zero found → 95% bound λ ≤ 3

  A = 20 mm² = 0.2 cm²: ρ = 20 /cm² → λ = 4; P(k ≥ 10) ≈ 0.8%
  ρ = 60 /cm² → λ = 12; P(k ≥ 10) ≈ 76%
  Zero in 0.2 cm² → ρ ≤ 15 /cm² (95%)
```

---

## E.19 EWMA Rate Control (Ch. 15)

```
ŷ_k = λ y_k + (1 − λ) ŷ_{k−1};   ΔE_total = (ŷ_k / t_target − 1) / (d ln R / dE)

  λ = 0.3; t_EP lots 36.0, 36.9, 37.4 s → ŷ = 36.00, 36.27, 36.61
  ΔE = 0, +0.4, +0.9 eV
D2 cycle count: N = 1.3 × ((t_in − 0.3)/EPC + 3.75)
  t_in = 5.45, EPC = 0.098 → 1.3 × (52.6 + 3.75) ≈ 73.3 → 74
```

---

## E.20 Equipment Sizing and Cost (Ch. 16)

```
N_tools = WPH_required / (WPH_tool × availability)
Cost per wafer (depreciation) = (Price / years) / (WPH × 8760 × availability)

  139 wph; D1 split mainframe 60 wph: 139 / (60 × 0.85) = 2.7 → 3
  D2 ALE chambers 9.2 wph: 139 / (9.2 × 0.85) = 17.8 → 18
  T batch 24 wph: 139 / (24 × 0.85) = 6.8 → 7
  D1 mainframe $15 M / 5 yr ÷ (60 × 8760 × 0.85 = 4.5 × 10⁵) ≈ $6.70 per wafer
```

---

## E.21 Value of Yield (Ch. 16)

```
Value = Δ(fatal opens per die) × wafer value

  Wafer value ≈ 860 × $3.0 ≈ $2,600; 1% ≈ $26
  Reference clear budget ≈ 0.007 per die → ≈ 0.7% → ≈ $18 per wafer at risk
  Halving carbon micromasks: −0.0015 → + $3.9 per wafer
```

---

**Appendix E Version:** 1.0  
**Last Updated:** 2026-10-05
