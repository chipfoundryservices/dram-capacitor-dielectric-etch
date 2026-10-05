# Appendix D: Process Windows

Reference windows for the dielectric-clear module. "Target" is the reference process; "window" is the range within which the specification of Chapter 1 is met with the other parameters at target. All values are illustrative starting points for a design of experiments.

---

## D.1 D1 — Hot Continuous Clear

```
Parameter                 Target               Window              Limited by
──────────────────────────────────────────────────────────────────────────────────────────
Wafer temperature         250 °C               220–270 °C          rate, selectivity (low) /
(chuck 236 °C + offset)                                            TE recess, Cl ingress (high)
Wall / liner temperature  120 °C               100–140 °C          Zr and B deposits (low) /
                                                                   seals, coating stress (high)
Pressure                  8 mTorr              6–12 mTorr          uniformity, sidewall BₓClᵧ
Source power              900 W                750–1100 W          flux and rate
BT chemistry              BCl₃ 100 / Ar 50     BCl₃ 80–120         —
BT ion energy             ≈ 100 eV             90–120 eV           C, F removal (low) /
                                                                   SiN, cap loss (high)
BT time                   3 s                  2–5 s               non-Gaussian residue (low) /
                                                                   ZAZ consumed before EP (high)
ME Cl₂ fraction           10%                  5–15%               rate (low) /
                                                                   TE recess > 3 nm (high, > 20%)
ME ion energy             ≈ 70 eV              60–80 eV            BₓClᵧ competition, edge
(bias V control)                                                   non-uniformity (low) /
                                                                   selectivity, sidewall ions (high)
Endpoint                  Si rise 50% AND      —                   —
                          BO drop 50%
OE fraction of t_EP       70%                  60–100%             Gaussian tail at slowest site
                                                                   (low) / TE recess, SiN (high)
Backside He               10 Torr              8–12 Torr           wafer offset ± 3 °C
Heat-up before strike     ≥ 10 s clamped       —                   wafer at ± 2 °C of setpoint
```

---

## D.2 D2 — Plasma ALE

```
Parameter                 Target               Window              Limited by
──────────────────────────────────────────────────────────────────────────────────────────
Chuck temperature         100 °C               60–150 °C           EPC (low) / α rises,
                                                                   synergy < 85% (high)
Step A time               1.5 s                ≥ 1.0 s             saturation knee
Step A Cl₂ fraction       10%                  5–20%               modification depth / TE
                                                                   lateral attack
Step A bias               0 W                  0 (no stray)        α
Step B ion energy         60 eV                45–70 eV            incomplete removal (low) /
                                                                   sputtering, SiN EPC (high)
Step B time               2.5 s                ≥ 1.5 s             saturation knee
Purge residual            ≤ 1%                 ≤ 2%                synergy, SiN EPC
Over-cycling              30%                  25–50%              tail at slowest site (low) /
                                                                   time, SiN (high)
BT before cycling         3 s, ≈ 100 eV        2–5 s               carbon, F (low)
```

---

## D.3 Thermal ALE (Comparison Route)

```
Parameter                 Target               Window              Limited by
──────────────────────────────────────────────────────────────────────────────────────────
Temperature               275 °C               250–300 °C          exchange incomplete (low) /
                                                                   DMAC decomposition, CVD (high)
HF dose per cycle         saturating           ≥ 1.5 × knee        EPC
DMAC dose per cycle       saturating           ≥ 1.5 × knee        EPC
Purges                    5 s (single wafer)   ≥ 4 s               AlF₃ particles
Over-cycling              78% (190 cycles)     ≥ 75%               σ_g ≈ 12% tail
Seal after clear          ALD SiN 3 nm         2.7–4 nm            slot fill (low) /
                                                                   contact etch (high)
```

---

## D.4 Post-Etch Treatment and Rinse

```
Parameter                 Target               Window              Limited by
──────────────────────────────────────────────────────────────────────────────────────────
PET chemistry             H₂O 300 / N₂ 700     H₂O 200–400         Cl removal (low) /
                          sccm                                     W oxidation (high)
PET time                  30 s                 20–45 s             same
PET temperature           250 °C               200–280 °C          Cl removal / W, TE oxidation
D1 → PET                  vacuum transfer      —                   edge corrosion
PET → rinse               ≤ 4 h                —                   moisture uptake
Rinse                     DI, 60 s             ≥ 45 s              B(OH)₃ removal
Rinse → ILD               ≤ 24 h               —                   adsorbed moisture
```

---

## D.5 Incoming Conditions

```
Parameter                      Target              Window              Effect outside window
──────────────────────────────────────────────────────────────────────────────────────────────
Periphery ZAZ thickness        5.4 nm              5.1–5.7 nm          FF exceeds zone range
Radial thickness tilt          + 2.4% edge         ± 4%                FF exceeds zone range
Monoclinic fraction            30%                 15–45%              σ_g > 12%: raise OE
Ti residue (after TiN step)    ≤ 3 × 10¹⁴ /cm²     ≤ 5 × 10¹⁴          BT insufficient
Carbon after strip             ≤ 3 × 10¹⁴ /cm²     ≤ 5 × 10¹⁴          micromask budget
Oxide cap                      60 nm               55–66 nm            cap budget
Strip → D1                     vacuum              —                   boron glass, moisture
```

---

## D.6 Interactions to Remember

```
1. Raising the Cl₂ fraction speeds the floor and the edge together; the
   edge gains faster (Chapter 11).
2. Raising the wafer temperature helps the floor more than SiN, but also
   raises TE recess with ≈ 0.3 eV activation.
3. Raising the ion energy in D1 changes the rate 1.8% per eV but the
   selectivity only slightly; it changes cap and ring erosion more.
4. Raising the OE beyond ≈ 70% buys almost nothing against non-Gaussian
   residue.
5. In D2, nothing changes the EPC much except leaving the window; the
   cycle count must follow the incoming thickness.
```

---

**Appendix D Version:** 1.0  
**Last Updated:** 2026-10-05
