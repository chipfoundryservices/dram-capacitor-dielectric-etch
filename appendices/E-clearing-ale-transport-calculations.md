# Appendix E: Clearing, ALE & Transport Calculations

Closed-form models used in this book, with the reference worked example for each. All models are deliberately simple; each lists its main assumptions.

---

## E.1 Capacitance, EOT, and Leakage (Ch. 1, 2)

```
C_s = ε₀ k A / t = ε₀ · 3.9 · A / EOT;   ε₀ = 8.854 × 10⁻²¹ F/nm
  A = 1.24 × 10⁵ nm², t = 5.5 nm, k = 43 → C_s = 8.6 fF; EOT = 0.50 nm

EOT (layer sum) = 3.9 Σ tᵢ/kᵢ
  Reference: 5.2/48 + 0.3/9 → 0.55 nm (measured 0.50)
  Pilot trimmed: 2.6/48 + 0.3/9 + 2.6/55 → 0.525 → × 0.50/0.552 ≈ 0.475 nm

J(t) ≈ J₀ exp(−t/λ), λ ≈ 0.25 nm:  −0.1 nm → ×1.5;  −1.0 nm → ×55
dC/C = −dt/t:  0.1 nm ≈ 1.8%
```

---

## E.2 Etch–Deposition Model (Ch. 3, 7)

```
R_net(E) = A (√E − √E_th) − D;    E₀ = (√E_th + D/A)²
d ln R / dE = A / (2 √E R_net)

Reference (t-ZrO₂, 60 °C): A = 1.33, E_th = 30 eV, D = 3 → E₀ ≈ 60 eV
  R(150) = 6.0;  sensitivity 0.9%/eV
  R(90) = 2.3;   3.0%/eV
Bevel (60% crystalline): A_mix = 0.6 A_t + 0.4 A_a = 1.60
  R(80) = 2.5 nm/min; 3.6%/eV
```

---

## E.3 Grain-Scale Spread (Ch. 3, 4)

```
σ_rem(x) = √((σ_r x)² + σ_t²)
  σ_r = 7.5%, σ_t = 0.12 nm, x = 4.44 nm → 0.35 nm

ALE added spread: σ_ALE = √((0.03 · EPC · √N)² + (0.01 R)²)
  N = 36, R = 3.6 nm → 0.04 nm
Total at the end of the finish: σ_tot = √(σ_rem² + σ_ALE²) = 0.352 nm
```

---

## E.4 Clearing-Time Map and Remaining Film (Ch. 6)

```
σ_tc / t_c = √((σ_t/t)² + (σ_R/R)²) = √(1.5² + 4.7²) ≈ 4.9% (3σ)
Remaining ≈ 5.5 (t_c / t̄_c) − x
  x = 4.44: fastest 0.79; nominal 1.06; slowest 1.34 nm

Main-step time for a removal x (reference rates):
  t = 26.0 s (2.6 nm ZrO₂) + 3.6 s (0.3 nm Al₂O₃) + (x − 2.9) / 0.1 s
  x = 4.44 → 45.0 s
```

---

## E.5 Residue Probability and Cycle Count (Ch. 6, 10)

```
P = ½ erfc(z / √2),  z = (N · EPC + b − R) / σ_tot
Target: N_s = 1.2 × 10⁸ sites/die, ≤ 0.01 opens/die → P ≤ 8 × 10⁻¹¹ → z ≥ 6.4

N = ⌈ (R_slow + 6.4 σ_tot − b) / EPC ⌉
  = ⌈ (1.34 + 2.25 − 0.05) / 0.10 ⌉ = 36
  Achieved: z = 6.56 (slowest), 7.36 (nominal), 8.1 (fastest)

Useful values of ½ erfc(z/√2):
  z = 4.0: 3.2 × 10⁻⁵    5.0: 2.9 × 10⁻⁷    6.0: 9.9 × 10⁻¹⁰
  z = 6.4: 7.8 × 10⁻¹¹   6.56: 2.7 × 10⁻¹¹  7.0: 1.3 × 10⁻¹²

Main-step share (Ch. 10): N(x) with R_slow = 5.775 − x, σ(x) from E.3
  x = 3.50 → 41;  4.00 → 39;  4.44 → 36;  4.90 → 34

Expected opens per wafer ≈ Σ (dies in band) × N_s × P(band)
  ≈ 0.12 × 950 × 1.2 × 10⁸ × 2.7 × 10⁻¹¹ ≈ 0.35
```

---

## E.6 Ring Wear (Ch. 6, 15)

```
ΔE_edge ≈ −1 eV per 50 RF-hours; edge rate −0.9% per eV
t_c,slow(h) = 1.046 / (1 − 0.009 ΔE)
N(h): 0 h → 36;  150 h → 37;  300 h → 39;  450 h → 41
Fit: N(h) = 36 + ⌈max(0, h − 50) / 100⌉
```

---

## E.7 ALE Saturation and Throughput (Ch. 4)

```
EPC = EPC_sat (1 − e^(−t_A/τ_A)) (1 − e^(−t_B/τ_B))
Rate = EPC / (t_A + t_B + t_purge)

τ_A = 0.30 s, τ_B = 0.7 s, EPC_sat = 0.107 nm, t_purge = 1.5 s:
  (1.0, 2.0): EPC 0.097, 4.5 s → 1.3 nm/min (reference)
  (1.5, 3.0): EPC 0.105, 6.0 s → 1.05 nm/min
  (0.5, 1.0): EPC 0.066, 3.0 s → 1.3 nm/min (drift-sensitive)

Synergy S = (EPC − α − β) / EPC = (0.10 − 0 − 0.004) / 0.10 = 96%
Removal time constant: τ_B = n_layer / (Y Γ_i) = 2.9 × 10¹⁴ / (0.04 × 1.0 × 10¹⁶) ≈ 0.7 s
```

---

## E.8 Ion Flux, Energy, and IEDF (Ch. 5)

```
Γ_i = 0.61 n_e u_B,  u_B = √(kT_e / M_i)
  Main step: n_e 1.2 × 10¹¹, T_e 3.5 eV, 82 amu → Γ_i 1.5 × 10¹⁶ cm⁻²s⁻¹
  ALE step:  n_e 6 × 10¹⁰, T_e 3 eV, 40 amu    → Γ_i 1.0 × 10¹⁶ cm⁻²s⁻¹
E_i ≈ e(V_p + |V_dc|)

Arcsine (bimodal) IEDF between E − ΔE/2 and E + ΔE/2:
  F(x) = ½ + (1/π) arcsin[(x − E)/(ΔE/2)]
  E = 60, ΔE = 50: fraction > 75 eV = ½ − (1/π) arcsin(0.6) = 29.5%
```

---

## E.9 Gas Residence and Purge (Ch. 5)

```
τ = pV / Q;  1 sccm ≈ 0.0127 Torr·L/s ≈ 7.5 × 10¹⁵ molecules/s
  V = 40 L, p = 20 mTorr, Q = 300 sccm → τ = 0.21 s
Residual after a purge of time t: exp(−t/τ)  (0.75 s → ≈ 3%)
```

---

## E.10 Bevel Confinement (Ch. 7)

```
Paschen: breakdown requires p·d near ≈ 1 Torr·cm (Ar, N₂)
  PEZ gap: 0.8 Torr × 0.035 cm = 0.028 Torr·cm → no plasma in the gap

Radical decay against the purge: n(x) = n₀ exp(−x/L), L = D / v
  D(Cl in N₂, 0.8 Torr) ≈ 0.15 × 760/0.8 ≈ 140 cm²/s
  v = Q(760/p) / (60 A_gap);  A_gap = 2π r × gap ≈ 3.3 cm²
  2 slm → v ≈ 9600 cm/s → L ≈ 0.15 mm; 90% → 10% over 2.2 L ≈ 0.3 mm
```

---

## E.11 Vapour Pressure (Ch. 9)

```
ln(p₂/p₁) = −(ΔH/R)(1/T₂ − 1/T₁)
ZrCl₄: p₁ = 1 Torr at 463 K, ΔH = 110 kJ/mol
  333 K (60 °C): 1.4 × 10⁻⁵ Torr;  393 K (120 °C): 6 × 10⁻³ Torr

Partial pressure in the chamber: p = (production rate) / (pumping speed)
  9 × 10¹⁶ s⁻¹ ≈ 2.8 × 10⁻³ Torr·L/s;  S = 380 L/s → 7 × 10⁻⁶ Torr
```

---

## E.12 Reactant Demand and Conformality (Ch. 12)

```
Demand per cycle = S × A_array:  HF 10¹⁵ cm⁻² × 2 × 10⁴ cm² = 2 × 10¹⁹
Reactor content: n = pV/kT = 66.7 Pa × 2 × 10⁻³ m³ / 7.2 × 10⁻²¹ J ≈ 1.9 × 10¹⁹
Minimum dose time = demand / (flow × utilization)
  HF 500 sccm (3.7 × 10¹⁸ s⁻¹), 70% → ≈ 8 s

Knudsen: D_K = d v̄ / 3;  v̄ = √(8kT/πm)
  HF at 523 K: v̄ ≈ 740 m/s; d = 7.4 nm → D_K = 1.8 × 10⁻⁶ m²/s

Exposure to saturate a hole of aspect ratio a:
  (P t)_req ≈ S √(2π m k T) (1 + 19a/4 + 3a²/2)
  a = 200, HF: ≈ 24 Pa·s ≈ 0.18 Torr·s; reference dose 4 Torr·s

Soft saturation: EPC = EPC₀ [1 + β ln X];  β = 0.035, X_top/X_bottom = 10
  ratio bottom/top = 1 / (1 + 0.035 ln 10) ≈ 0.92
```

---

## E.13 Grain-Boundary Groove and Leakage (Ch. 12)

```
Groove excess saturates when depth ≈ ½ × boundary width (≈ 0.25 nm)
Leakage factor at the groove: exp(Δt/λ) = exp(0.25/0.25) ≈ 2.7
Area-weighted mean: (1 − f_gb) + f_gb × 2.7 = 0.95 + 0.135 ≈ 1.09
```

---

## E.14 Charging Clamp (Ch. 13)

```
J(V) = J₁ exp((V − 1)/V₀),  J₁ = 8 × 10⁻⁷ A/cm², V₀ ≈ 0.2 V
I_leak(V) = J(V) × A_dielectric
Module 1: A = 2 × 10⁴ cm² → I(1 V) = 16 mA
  Bevel current 46 mA → V = 1 + 0.2 ln(46/16) ≈ 1.2 V
```

---

## E.15 Weibull Area Scaling (Ch. 13)

```
F(t) = 1 − exp[−(A/A₀)(t/η)^β];   η(A) = η(A₀)(A₀/A)^(1/β)
  A₀ = 10⁻³ cm², A = 21 cm², β = 2.0 → η ratio ≈ 6.9 × 10⁻³
  β = 1.6 → η ratio ≈ 2.0 × 10⁻³
```

---

## E.16 Diffusion and Adhesion (Ch. 11)

```
L = √(D t):  D_gb = 10⁻¹⁵ cm²/s, t = 6.5 h → L ≈ 48 nm
G = σ² h / (2 E'):  SiGe 150 nm, 100 MPa, 150 GPa → 0.005 J/m²
                     W 40 nm, 1.0 GPa, 410 GPa   → 0.05 J/m²
```

---

## E.17 Yield and Cost (Ch. 16)

```
Y = exp(−λ);  ΔY ≈ Δλ for small λ
  Δλ = 0.004 → ΔY ≈ 0.4% → × $3,800 ≈ $15 per wafer
Cost per second of chamber time = annual cost / (8760 × 3600 × availability)
  $1.10 M / (3.15 × 10⁷ × 0.85) ≈ $0.041/s
Chambers = wph_required / (wph_per_chamber × availability)
  210 / (9.0 × 0.85) ≈ 27.5 → 28
Break-even Δλ = Δcost / wafer value = 4.80 / 3800 ≈ 0.0013
```

---

**Appendix E Version:** 1.0
