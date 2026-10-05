# Appendix E: Etch, Trim, Wrap & Charging Calculations

Closed-form models used in this book, with the reference worked example for each. All models are deliberately simple; each lists its main assumptions.

---

## E.1 Capacitance, EOT, and Leakage Headroom (Ch. 1)

```
C_s = ε₀ · 3.9 · A / EOT;   A = π · 28 nm · 1410 nm = 1.24 × 10⁵ nm²
  = 8.854×10⁻¹² × 3.9 × 1.24×10⁻¹³ / 0.50×10⁻⁹ = 8.57 fF
EOT = 3.9 t / k_eff,  k_eff = 5.5 × 3.9 / 0.50 = 43;  dEOT/dt = 0.0907 nm per nm
dC/C = −dEOT/EOT:   thin 0.2 nm → EOT 0.4807 nm, C +3.8%, leakage ×2.8 (10^(0.2/0.45))

J(V) = J₁ exp[(V − 1.0)/0.12 V], J₁ = 8×10⁻⁷ A/cm²;  per cell: 0.023 fA at 0.55 V; 0.99 fA at 1.0 V
Headroom: weakest-cell leakage 100 × 0.023 fA = 2.3 fA against 10 fA → ×4.3 → 0.45 × log₁₀(4.3) = 0.28 nm
```

---

## E.2 Zirconium Inventory and Decades (Ch. 1, 9)

```
n(ZrO₂) = 5.68 g/cm³ / 123.2 g/mol × 6.022×10²³ = 2.78 × 10²² cm⁻³
Zr per cm², 5.2 nm = 2.78×10²² × 5.2×10⁻⁷ = 1.44 × 10¹⁶;  ML (0.3 nm) = 8.3 × 10¹⁴
Limits: 10¹³ (3.2 decades), 10¹¹ (5.2), 10¹⁰ (6.2 decades below as deposited)
Film area / flat area: 1.83×10⁴ cm² / 707 cm² = 26
Edge zone: top 3.0 mm 28.0 cm²; bevel 5.7 cm²; backside 3.5 mm 32.6 cm² → 66 cm², 9.6×10¹⁷ Zr
Dopant limit: 10¹³ / 1.44×10¹⁶ = 0.07% of cation sites (Ch. 14)
```

---

## E.3 Ion-Yield Rates (Ch. 3)

```
ER = K A (√E − √E_th),  K = 3.92 nm/s (per unit yield)
  ZrO₂ tetragonal (E_th 60, A 0.00566):  70 eV → 0.83;  150 eV → 6.0;  250 eV → 10.8 nm/min
  ZrO₂ amorphous  (E_th 45, A 0.00690):  150 eV → 9.0;  250 eV → 14.8 nm/min
  Edge: flux ×0.25: amorphous 250 eV → 3.7 nm/min; Al₂O₃ 2.05 nm/min
  Clear: 2 × 2.6 / 3.7 + 0.3 / 2.05 = 1.551 min = 93 s;  +30% → 121 s
  TiN (E_th 25, A 0.053): 40 eV → 16.5 nm/min
```

---

## E.4 Crystallization (Ch. 2)

```
X(t) = 1 − exp[−(t/τ)²],   τ(T) = τ₀ exp(E_a/kT),  E_a = 3.0 eV
  τ(673 K) = 1430 s (X = 0.41 after 17 min);  τ(698 K) = 221 s;  τ(553 K) = 1.05×10⁸ s
  ALD (280 °C, 14 min): X = 7×10⁻¹¹;  SiGe 425 °C 1 h: X = 1.00;  hot clear 250 °C 38 s: 10⁻¹⁶
R(X) = 9 (1 − X) + 6 X  nm/min
```

---

## E.5 Dosing and Wrap-Around (Ch. 2, 6, 14)

```
Channel: d = 2(p/√3 − r − t) = 2(45/1.732 − 14 − 5.5) = 13.0 nm;  AR = 1410/13 = 109
Tube:  t_sat = 6 N_s AR² / (n₀ v̄)
  Zr precursor: 6 × 1.5×10¹⁸ × 109² / (3.5×10²⁰ × 190) = 1.6 s;  pulse 2.0 s (margin 1.25)
  HF:   6 × 7.7×10¹⁸ × 109² / (1.75×10²¹ × 765) = 0.41 s   (4.1×10⁴ L at 0.1 Torr)
  DMAC: 6 × 3.8×10¹⁸ × 109² / (8.7×10²⁰ × 367) = 0.84 s
Slit:  x_sat = g √(n₀ v̄ t / 3 N_s) = 12×10⁻⁶ × √(3.5×10²⁰×190×2.0 / (3×1.5×10¹⁸)) = 2.06 mm
Zone:  W = 1.5 x_sat + 0.4 mm = 3.5 mm
1d-class (AR 195): pulse ×3.2 (5.2 s min, 6.5 s used), x_sat 3.7 mm, zone 6.0 mm
```

---

## E.6 Stop Requirement (Ch. 4, 8, 10)

```
t_c = 5.0 / 16.5 × 60 = 18.2 s;  σ_tc = √(6.0² + 5.0²) = 7.8% (3σ)
Fastest site clears at 16.7 s; step 36.3 s (100% OE) → exposure 19.6 s → 16.5 × 19.6/60 = 5.4 nm TiN-equivalent
S ≥ 5.4 nm / 0.3 nm = 18  (OE 60% → 11);   measured ZAZ loss 0.03–0.05 nm → S ≈ 110–180
Tail-ion sputter: 0.03–0.05 × 0.24 nm/min × 19.6 s/60 = 0.0024–0.0039 nm
F memory: n_F = 10¹² [0.9 e^(−t/10) + 0.1 e^(−t/200)] cm⁻³;  F dose 1.5×10¹³ cm⁻² → ZrF₄ 3.8×10¹² cm⁻² (0.45% ML)
```

---

## E.7 Strip, Shell, and W Budget (Ch. 4, 7)

```
Shell = 1.8 √(t/60) nm;  WOₓ = 2.5 √(t/60) nm;  W consumed = WOₓ / 3.4
Plate R_s: 1/R = 1/(ρ_W/t_W) + 1/133 + 1/500;  R_s ≤ 4.0 → t_W ≥ 36.1 nm;  loss ≤ 3.9 (2.7 with −3%)
Budget (60 s): strip 0.74 + P4 2.4 × 37.8/60 = 1.51 → 2.25 nm
Shell life = shell / 2.0 nm/min;  margin = life / t_step:   1.8 nm → 54 s / 37.8 s = 1.43
Min shell for 1.3× margin: 1.3 × 37.8 × 2.0 / 60 = 1.64 nm;  E_min = 74 eV
TiN recess: 3.5 nm/min × 18 s = 1.05 nm + shell conversion 1.8/1.7 = 1.06 → 2.1 nm
```

---

## E.8 Charging with the Plate Exposed (Ch. 7)

```
Island top 1.32×10⁻² cm²; island dielectric 5.4×10⁸ × 1.24×10⁻⁹ = 0.667 cm²;  ratio 0.0198
I = 0.5 mA/cm² × 0.0132 cm² = 6.6 µA;  J = 9.9×10⁻⁶ A/cm²
ΔV = 0.12 × ln(J/J₁) = 0.12 × ln 12.4 = 0.30 V → clamp 1.30 V;  pulsed (J ×0.5): 1.22 V
Q(P4) = 9.9×10⁻⁶ × 38 s = 3.8×10⁻⁴ C/cm²;  R1 total ≈ 1.7×10⁻³ vs R0 ≈ 1.0×10⁻³ C/cm²
```

---

## E.9 Grain-Tail Statistics (Ch. 2, 4, 13, 16)

```
P(grain left) = ½ erfc(z/√2),  z = OE/σ;   opens per die = 3×10⁷ × 4 × P;   Y = exp(−opens)
  R0 (50%, σ 8%):    z 6.25, P 2.0×10⁻¹⁰, opens 2.5×10⁻², Y 97.6%
  R1 (35%, σ 5%):    z 7.00, P 1.3×10⁻¹², opens 1.5×10⁻⁴, Y 99.985%
  R1 (40%, σ 6%):    opens 1.6×10⁻³;  R1 (35%, σ 6%): 0.33
  R2 finish (30%, σ_EPC 4%):  z 7.5, P 3.2×10⁻¹⁴, opens 3.8×10⁻⁶
Target: P < 0.01 / 1.2×10⁸ = 8.3×10⁻¹¹ → z ≥ 6.4 → OE ≥ 32% (σ 5%), 51% (σ 8%), 19% (σ 3%)
Contact chains: N = −ln 0.05 / P = 3/P;  P = 3.3×10⁻¹⁰ → 9.0×10⁹ contacts = 45 wafers × 2×10⁸
```

---

## E.10 Thermal ALE (Ch. 3, 6, 13)

```
EPC(T) = 0.10 / [1 + exp(−(T − 258)/22)] nm;  d ln EPC/dT = (1 − p)/22,  p = EPC/0.10
  280 °C: 0.073, 1.2%/°C;  265 °C: 0.058, 1.9%/°C;  250 °C: 0.041, 2.7%/°C
Cycles: strip 5.2/0.07 + 0.3/0.05 = 80 (+10% = 88);  R2 finish 1.0 × 1.3/0.045 = 29;  R3 (5.2/0.045 + 6) × 1.3 = 158
Time at 10 s per cycle: 13.3 min, 4.8 min, 26 min
Trim: N = round(Δt/EPC) for Δt > one cycle; ends within ½ cycle of nominal
Lot excess σ = 0.067 nm: P(Δt > 0.073) = 13.7%;  headroom spent: 0.05–0.07 nm (over-thick lot) vs 0.27 nm (nominal lot)
Dose margin M = t_pulse / t_sat; saturated fraction of the pillar = min(1, √M)
Witness: Δf = 0.0815 Hz/(ng/cm²) × 38.7 ng/cm² = 3.2 Hz per cycle (6 MHz)
```

---

## E.11 Damage, Leakage, and TDDB (Ch. 12)

```
Energy transfer γ = 4 m₁m₂/(m₁ + m₂)²;  O: Ar 0.82, Cl 0.86;  E to displace O = E_d/γ = 24 eV (E_d 20 eV)
Equivalent thickness ΔT_eq = w (1 − η);  leakage factor 10^(ΔT_eq/0.45);  10% leakage = 0.019 nm
TDDB: F(t) = 1 − exp[−A (t/η₁)^β],  β = 1.2;  η ∝ (E/E₀)^(−n), n = 30
  A = 21.3 cm²;  P(10 yr) = 10⁻⁵ → η₁ = 1.9×10⁶ yr/cm²
  trim 0.2 nm: field ×1.038, k = 3.04, M = k^β = 3.79 → P = 3.8×10⁻⁵
M_edge = 1 + f_d (k^β − 1):  (10⁻³, 10) → 1.01;  (10⁻², 10) → 1.15;  (10⁻³, 100) → 1.25
```

---

## E.12 Edge Overlap and Redeposition (Ch. 11)

```
O_min = 1.5 × (placement + undercut + damage + notch)
  R1: 1.5 × (100 + 0 + 50 + 2.1) = 0.23 µm;  R3: 1.5 × (100 + 21 + 50 + 2.1) = 0.26 µm;  reference 1.5 µm
Undercut: d_lat = d_v × (1 + OE);  boundary enhancement ≤ 3×:  R3 7.1 → 21 nm
Field at a corner: E_edge/E_flat = t / (r ln(1 + t/r)):  t = 5.5 nm; r = 2 → 2.08; r = 5 → 1.48
Redeposition: C(x) = C₀ exp(−x/λ), C₀ = 10¹⁵ B cm⁻², λ = 0.4 mm → 8.2×10¹³ at 1 mm; with strip ÷10: 8×10¹²
```

---

## E.13 Contamination Transfer and ALD Clean (Ch. 9)

```
Chuck after one dirty wafer: C_c = f × 1.44×10¹⁶ = 1.4×10¹³ cm⁻² (f = 10⁻³)
Pick-up of wafer n: f C_c (1 − f)ⁿ;  above 10¹⁰: n = ln(1.44)/f ≈ 370;  above 10⁹: n ≈ 2,700
After the edge etch (10¹⁰ backside): chuck 10⁷, pick-up 10⁴ cm⁻²
Wall deposit: 5.5 nm per wafer → 182 wafers per µm;  clean 1 µm: 17 min at 60 nm/min (+ 40 min ramp) = 19 s/wafer
Rate at 280 °C: 60 × exp[−0.6/k (1/553 − 1/623)] = 60 × 0.243 = 14.6 nm/min
ZrO₂ → ZrF₄ volume ×1.75
```

---

## E.14 Control and Cost (Ch. 15, 16)

```
EWMA: EPC_{n+1} = λ EPC_meas + (1 − λ) EPC_n,  λ = 0.3:  0.0730, meas 0.0690 → 0.0718 → N = 3 for Δt = 0.20
P(wrong N) = 2[1 − Φ(0.0365/σ_meas)]:  σ 0.010 → 0.03%;  0.015 → 1.5%;  0.030 → 22%
Depreciation per wafer = (capex/5 yr) / (wph × 8760 × 0.85)
  F $2.3 M @ 52.9 wph = $1.17;  C $2.3 M @ 23.1 = $2.68;  strip $1.5 M @ 40 = $1.01;  hot $2.8 M @ 49.3 = $1.53
  R1 etch total $10.53;  edge module $3.44;  trim average $0.53
Break-even for module E: $3.44 × 1.2×10⁶ = $4.1 M/yr ÷ $3 M per event = 1.4 events/yr
Value of 1% die yield ≈ 0.01 × 860 × $3 = $26 per wafer
```

---

**Appendix E Version:** 1.0
