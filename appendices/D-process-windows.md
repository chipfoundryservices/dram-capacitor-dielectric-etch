# Appendix D: Process Windows

Reference windows for the dielectric etch modules. "Target" is the reference process; "window" is the range within which the specification of Chapter 1 is met with the other parameters at target. All values are illustrative starting points for a design of experiments.

---

## D.1 Edge Etch (Module E)

```
Parameter                 Target              Window             Limited by
─────────────────────────────────────────────────────────────────────────────────────────────
BCl₃ / Cl₂ / Ar           60 / 15 / 100 sccm  Cl₂ 10–30%        BₓClᵧ deposition (low Cl₂) /
                                                                  Si loss (high Cl₂)
Pressure                  200 mTorr           150–300 mTorr      boundary blur / ion energy
RF power (edge ring)      300 W               250–350 W          rate (low) / Si, SiN loss (high)
Self-bias (ion energy)    −250 V (≈ 250 eV)   200–320 eV         etch–dep. transition (low) /
                                                                  Si loss (high)
Overetch                  30% (121 s total)   20–40%             Zr residue (low) / Si loss (high)
Si loss (backside)        5.0 nm              ≤ 10 nm            backside roughness
Plate gap                 0.30 mm             0.25–0.35 mm       p·g (breakdown); blur
Centre purge (N₂)         150 sccm            100–200 sccm       radical ingress (low) /
                                                                  boundary shift (high)
Wall temperature          100 °C              ≥ 90 °C            BₓClᵧ deposition on the plate
Pedestal radius           146.5 mm            ± 0.05 mm          backside zone (3.5 mm)
Upper plate radius        147.0 mm            ± 0.05 mm          top boundary
Wafer centring            ± 0.10 mm (3σ)     ≤ ± 0.15 mm        boundary budget (Chapter 5)
Queue ALD → top TiN       ≤ 4 h               ≤ 4 h incl. T      carbon, hydroxyl on ZAZ
Edge wet clean            0.5% HF, 20 s       15–30 s            removal factor (low) /
                                                                  SiN loss, meniscus (high)
Edge clean nozzle width   3.0 mm at surface   ± 0.3 mm           HF reaching r < 146 mm
```

---

## D.2 Conductor and Stop (P1/P2)

```
Parameter                 Target              Window             Limited by
─────────────────────────────────────────────────────────────────────────────────────────────
P1 steps (BARC, W, SiGe)  Book #32 recipe     —                  —
Chambers                  F (BARC, W);        ≥ 87 s between W   fluorine memory on the ZAZ
                          Cl/Br (SiGe, P2)    and P2 if shared
BT (BCl₃/Ar)              6 s, 70 eV          4–8 s; 60–80 eV    TiOₓ left (low) /
                                                                  ZAZ at pinholes (high)
TiN stop ion energy       40 eV               30–55 eV           rate (low) / ZrO₂ threshold,
                                                                  ion mixing (high)
Cl₂ / Ar                  100 / 100 sccm      Cl₂ 40–70%         foot notch (high Cl₂)
Pressure                  6 mTorr             4–10 mTorr         uniformity
Overetch (re. endpoint)   100% of t_c         60–120%            TiN residue (low) / foot notch,
                                                                  ZAZ loss (high)
Chuck temperature         60 °C               50–70 °C           foot notch (high) / rate (low)
TiN thickness (input)     5.0 nm              4.7–5.3 nm         t_c ± 6%
ZAZ apparent loss         0.03–0.05 nm        ≤ 0.10 nm          stop quality (Chapter 10)
SiGe foot notch (total)   2.7–4.2 nm          ≤ 5 nm             Chapter 10
```

---

## D.3 Strip (P3)

```
Parameter                 Target              Window             Limited by
─────────────────────────────────────────────────────────────────────────────────────────────
Time                      60 s                50–90 s            shell margin ≥ 1.3 (low) /
                                                                  W budget (high)
Temperature               250 °C              230–270 °C         resist rate; oxide growth
O₂ / N₂                   1500 / 150 sccm     —                  resist rate
Pressure                  1 Torr              0.7–1.5 Torr       radical flux
TiOₓ shell                1.8 nm              1.65–2.2 nm        shell life vs P4 step time
WOₓ top                   2.5 nm              2.1–3.1 nm         W consumed ≤ 0.9 nm
W consumed                0.74 nm             ≤ 0.9 nm           plate R_s
Queue strip → P4          ≤ 1 h (vacuum: none) —               water on ZAZ / oxides
```

---

## D.4 Hot Clear (P4)

```
Parameter                 Target              Window             Limited by
─────────────────────────────────────────────────────────────────────────────────────────────
Chuck temperature         250 °C              235–260 °C         rate −15% at 235 °C; shell
                                                                  margin (low) / resist-free: none
Ion energy (peak)         80 eV               74–110 eV          shell margin ≥ 1.3 (low) /
                                                                  damage, notch (high)
BCl₃ / Cl₂ / Ar           80 / 20 / 50 sccm   Cl₂ 15–30%         BₓClᵧ (low) / TiOₓ shell etch (high)
Pressure                  5 mTorr             3–8 mTorr          uniformity
Source / bias             800 W / 200 W       bias 150–260 W     ion energy window
Bias pulsing              10 kHz, 50%         —                  charging (Chapter 7)
Clearing time (nominal)   28 s                —                  Al-marker prediction
Overetch                  35% reference;      35–45%             residue tail (low) /
                          40% production                         shell margin ≥ 1.3 (45% = 1.33)
Step time                 38 s (35%); 39 s (40%) ≤ 41.5 s        shell life 54 s ÷ 1.3
SiN loss                  0.65 nm             ≤ 15 nm            —
W loss in P4              1.5 nm              ≤ 1.96 nm          total W budget 2.7 nm
Liner / window / lid      150–180 / ≥ 120 / 120 °C  —            condensation; B deposition
Foreline                  150 °C              ≥ 130 °C           AlCl₃, ZrCl₄ condensation
Post-etch treatment (P5)  H₂O/O₂ 30 s + rinse —                  Cl ≤ 2 at%, B ≤ 1 at% on SiN
```

---

## D.5 Thermal ALE (Module T and R2)

```
Parameter                 Target              Window             Limited by
─────────────────────────────────────────────────────────────────────────────────────────────
Pedestal temperature      265 °C (trim);      ± 2 °C            ± 3.8% (265) / ± 2.4% (280)
                          280 °C (strip)                          removal
HF                        0.1 Torr, 2 s       ≥ 1 s              flat saturation (10⁵ L)
DMAC                      0.05 Torr, 2 s      ≥ 1.3 s (margin 1.5)  pillar bottom saturation
                                              (AR 154: 0.10 Torr, 3 s)
Purge                     3 s                 ≥ 2.8 s (9τ)       gas-phase CVD (HF + DMAC)
Cycles (trim)             N = round(Δt/EPC)   ≤ 4 at 265 °C      headroom (Chapter 12)
Cycles (rework strip)     88 (80 + 10%)       —                  TiN exposure ≤ 8 cycles
Cycles (R2 finish)        29                  25–35              grain tail (low) / undercut (high)
Oxidizing step after trim O₃ or O₂ plasma, 250 °C, 3 min   —     F, C, vacancies (Chapter 12)
Foreline / walls          150 °C / 150–200 °C —                  ZrF₄ / ligand condensation
EPC (witness, amorphous)  0.073 nm (280 °C)   ± 8%              loop stops at −8% (Chapter 15)
```

---

## D.6 ALD-Chamber Clean (Module C)

```
Parameter                 Target              Window             Limited by
─────────────────────────────────────────────────────────────────────────────────────────────
Clean trigger             120–180 wafers      ≤ flake onset      flakes (0.5–1 µm deposit)
Chemistry                 BCl₃/Cl₂ remote plasma, 350 °C        —   fluorine NEVER
Rate (ZrO₂)               60 nm/min           ≥ 40               time per wafer
Time                      17 min per µm (+ 40 min thermal cycling)  overhead 19 s per wafer
Wet clean                 every 5 µm          —                  cold parts, residue
Season after clean        2–3 dummy ZAZ       —                  first-wafer thickness ± 0.2 nm
```

---

**Appendix D Version:** 1.0
