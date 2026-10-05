# Appendix D: Process Windows

Operating windows for the reference recipes, with the failure at each edge. Values are illustrative starting points for a design of experiments, not qualified limits.

---

## D.1 Module 1: Bevel Removal

```
Parameter                  Low edge (failure)                Reference          High edge (failure)
────────────────────────────────────────────────────────────────────────────────────────────────────
B2 RF power                300 W: backside ≈ 72 eV, rate     400 W              500 W: arcing at the
                           ≈ 1.8 nm/min, residual Zr                            apex; plasma deeper in
                                                                                the PEZ gap
B2 time                    120 s: front shoulder OE 9%       150 s              200 s: throughput;
                                                                                more SiN loss on bevel
B2 pressure                0.5 Torr: plasma spreads into     0.8 Torr           1.2 Torr: lower ion
                           PEZ gap (boundary inward)                            energy; slower
Cl₂ fraction (of halogen)  10%: BₓClᵧ deposits, boron ring   20%                40%: O gettering
                           wider                                                weak; slower ZAZ
Centre purge N₂            1 slm: radical decay 0.3 mm; TiN  2 slm              4 slm: purge disturbs
                           creep                                                the edge plasma
PEZ gap                    0.25 mm: contact risk with bow    0.35 mm            0.5 mm: pd rises;
                                                                                boundary inward
Chuck temperature          40 °C: slower; deposition          60 °C              100 °C: TiN creep
                           heavier                                              under PEZ grows
B3 O₂/N₂ time              10 s: BₓClᵧ left (haze)            20 s               —
```

---

## D.2 Module 2: Periphery Clear

```
Parameter                  Low edge (failure)                Reference          High edge (failure)
────────────────────────────────────────────────────────────────────────────────────────────────────
TiN-clear overetch         0 s: TiN islands at slow sites;   2.5 s              8 s: TE notch grows;
                           main step starts unevenly                            ZrO₂ loss ≈ 0.1 nm
Main-step ion energy       100 eV: σ_r 10%, +7 cycles        150 eV             200 eV: SiN, resist,
                                                                                veil, charging up
Main-step removal          3.5 nm: +5 cycles                 4.44 nm            4.9 nm: 20% of fast-
                                                                                site grains break
                                                                                through
Main-step Cl₂ fraction     10%: BₓClᵧ micromasking           20%                40%: rate −2%; OK
                                                                                to ≈ 40%
Chuck temperature          50 °C: rate −8%                   60 °C              70 °C: rate +8%;
                                                                                resist OK; zones
                                                                                re-tune
ALE dose time              0.5 s: EPC −16%, drift-           1.0 s              1.5 s: +1.5 s/cycle
                           sensitive                                            for +3% EPC
ALE purge time             0.5 s: residual BCl₃ 10%, EPC     0.75 s             1.25 s: throughput
                           0.09
ALE Ar⁺ energy             45 eV: incomplete removal         60 eV              75 eV: sputtering;
                                                                                SiN EPC rises
ALE removal time           1.0 s: EPC −18%                   2.0 s              3.0 s: +1 s/cycle
                                                                                for +5% EPC
ALE cycles                 34: z = 6.0 at the slowest site   36 (ring-hour      40: +18 s; SiN
                                                             compensated)       +0.06 nm
Bias waveform (ALE)        13.56 MHz sinusoidal: 59% of      tailored           —
                           ions outside the window; SiN
                           EPC ×2.3
Queue to strip             —                                 ≤ 5 min (vacuum)   1 h in air: TE notch
                                                                                +0.5 nm; W oxide
Strip H₂O fraction         0%: B on SiN not removed          10%                30%: W edge oxide
Strip temperature          150 °C: H₃BO₃ not volatilized     250 °C             300 °C: resist pop
                                                                                (initial step)
```

---

## D.3 Module 3: In-Array Trim (Pilot)

```
Parameter                  Low edge (failure)                Reference          High edge (failure)
────────────────────────────────────────────────────────────────────────────────────────────────────
Wafer temperature          225 °C: EPC 0.04; 25 cycles       250 °C             275 °C: groove ratio
                                                                                up; Al deposition
                                                                                begins near 300 °C
HF dose                    3 s: supply-limited; bottom-to-   8 s                15 s: ratio no better
                           top 0.70                                             (soft saturation)
DMAC dose                  5 s: under-saturated exchange     12 s               20 s: cost; DMAC use
HF → DMAC purge            2 s: HF left; AlF₃ deposition in  5 s                —
                           channels
DMAC → HF purge            5 s: DMAC left; Al deposition     10 s               —
Cycles                     16: trim 0.96 nm; EOT high        17                 18: trim 1.08 nm;
                                                                                leakage +15%
O₃ post-step               0 s: F 2–4 at%; TDDB −30%         30 s               120 s: TiN-side
                                                                                oxidation risk at
                                                                                exposed edges
Queue to TE                —                                 vacuum / ≤ 2 h     > 8 h: C and H₂O
                                                                                uptake; leakage up
Deposited top ZrO₂         3.3 nm: crystallinity gain        3.6 nm             4.0 nm: needs 1.4 nm
                           partly lost                                          trim; groove, time
```

---

**Appendix D Version:** 1.0
