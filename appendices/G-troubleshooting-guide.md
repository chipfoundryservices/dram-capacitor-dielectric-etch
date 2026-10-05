# Appendix G: Troubleshooting Guide

Symptom-driven guide for DRAM capacitor dielectric-clear excursions. For each symptom: likely causes ranked from most to least common, checks to separate them, and corrective actions. Chapter references point to the underlying physics.

---

## G.1 Periphery Contact Opens Up (Random, Whole Wafer)

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. Carbon micromasks: strip incomplete     Strip endpoint log; XPS C on        Restore strip; verify
   (Ch. 10.3.3)                            monitor pad; FA shows C under ZrO₂  BT energy
2. Wider clearing spread (monoclinic       Al-marker width; GIXRD on plate-    Raise OE per FF rule
   fraction, grain size) (Ch. 8.3.3)       dep monitor; AFM SiN roughness      (Ch. 15.5.1)
3. BT weakened (bias, BCl₃ flow)           BT V_pp and MFC logs; Ti, F on      Restore BT; check
   (Ch. 2.4.3)                             post-clear XPS                      fluorine source
4. ALD nodules (deposition chamber)        Islands thicker than 5 nm on        Hold ALD chamber;
   (Ch. 10.3.5)                            e-beam review; ALD particle trend   clean and requalify
```

## G.2 Contact Opens at the Wafer Edge (Ring or Clusters Near Plate Edges)

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. Edge-ring wear: edge energy low, ion    RF hours; edge rate on daily        Raise ring / edge
   tilt (Ch. 6.4)                          monitor; opens next to inward-      electrode; replace ring
                                           facing plate edges
2. Edge-thick ZAZ not compensated          Incoming radial profile; zone FF    Restore FF; update
   (Ch. 6.3)                               log                                 zone model
3. Edge zone heater fault                  Zone thermocouples; wafer offset    Repair; requalify
                                           map
```

## G.3 Clustered Opens (10–100 Neighbouring Contacts)

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. Zr-containing wall flakes (RF hours     Defect review EDX (Zr, B, Y);       Wet clean; shorten
   since wet clean) (Ch. 9.5)              particle monitor trend              interval
2. Boric acid particles (BCl₃ line         Boron-rich particles; cylinder      Purge per App. C.5;
   moisture) (Ch. 5.5.1)                   change log                          leak check
3. Chuck scraping (cold clamp)             Al/N particles at the edge; heat-   Restore preheat
   (Ch. 5.3.3)                             up sequence log                     sequence
```

## G.4 t_EP Drifting Long (Rate Falling)

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. Wafer temperature low: He leak,         Wafer offset; He flow; zone         Fix leak; requalify
   chuck change (Ch. 5.3.2)                temperatures                        offset
2. Ion energy low at constant power        V_pp trend; source power and        Switch to V control;
   (Ch. 5.2.2)                             reflected power                     check match
3. Wall state after clean (first wafers)   Wafers since clean; Cl/Ar ratio     Complete seasoning
   (Ch. 9.1.3)
4. Thicker or more monoclinic incoming     Incoming ellipsometry; GIXRD        None if OE scales;
   film                                                                        verify FF
```

## G.5 SiN Loss High

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. Ion energy high (bias drift)            V_pp; SiN monitor rate              Restore V setpoint
2. Cl₂ fraction high (MFC)                 MFC log; TE recess on edge grating  Restore 10%
   (Ch. 3.3.3)
3. Endpoint late → OE long                 Endpoint trace; fallback flag       Check viewport,
   (Ch. 8.6)                                                                   thresholds
```

## G.6 TE TiN Recess High (Edge Grating OCD or TEM)

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. Cl₂ fraction high or BCl₃ low           MFC logs; BCl₃ cylinder pressure    Restore flows
   (Ch. 11.2.3)
2. Wafer temperature high                  Offset; zone setpoints              Restore
3. OE extended (FF rule triggered          OE log per wafer                    Review FF limits
   repeatedly)
4. Wall state: low BₓClᵧ on walls after    Wafers since clean                  Season further
   clean → more free Cl
```

## G.7 Plate-Edge Comb Leakage Up, Contacts Normal

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. PET failed (H₂O flow, temperature)      PET logs; XPS Cl and B on pad       Repair; re-PET held
   (Ch. 12.3)                                                                  lots if within queue
2. Rinse skipped or short                  Wet-tool log; XPS B                 Re-rinse
3. Queue PET → rinse exceeded              Lot history                         Enforce ≤ 4 h
4. TE edge oxidation (moisture before      TEM/EELS at edge                    Enforce vacuum D1 →
   PET)                                                                        PET
```

## G.8 Array Leakage Shift (Whole Bank, Uniform)

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. Strip hydrogen dose up (temperature,    Strip logs; split with lower-       Restore strip
   time) (Ch. 13.4)                        temperature strip
2. Thermal budget change (ILD, anneals)    Process history                     Integration review
3. Not the clear: deposition change        ALD and TE logs; arrays from        Escalate to module
                                           split routes
```

## G.9 Retention Tail at the Array Boundary Only

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. Overlap reduced below damage reach      Overlap-ladder data; layout         Restore overlap or
   (Ch. 13.7.2)                            revision                            change route
2. Edge ingress after slot (thermal ALE    TEM for slot; seal thickness        Restore SiN seal
   without seal) (Ch. 11.4)
3. Plate placement shift (overlay)         Overlay data                        Litho correction
```

## G.10 TXRF Zr High (Average)

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. Under-etch: endpoint fallback, recipe   Endpoint traces; recipe audit       Rework if possible
   error                                                                       (D1 OE-only rerun);
                                                                               scrap otherwise
2. Redeposition from walls (Zr release)    Zr I baseline; RF hours             Clean; season
3. Measurement: VPD used on crystalline    Method audit                        Use TXRF (App. F.2)
   ZrO₂ (reads low, not high)
```

## G.11 Backside Zr Above Gate

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. ALD edge purge failure                  Backside Zr radial profile (outer   Repair ALD edge
   (Ch. 9.4.1)                             1–3 mm high)                        hardware
2. Bevel etch BCl₃ step skipped or weak    Bevel tool logs; bevel scan         Rerun bevel etch
3. Chuck transfer (D1 or ALD chuck)        Uniform backside level; chuck       Clean chuck; check
                                           contact pattern                     wafer-handling path
```

## G.12 ALE (D2) EPC Drift

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. Purge residual up (valve slow)          Per-cycle pressure trace; Cl in     Replace valve; check
   (Ch. 7.2.3)                             step B                              divert timing
2. Step-B energy out of window             V_pp; IED wafer                     Restore bias
3. Chamber temperature up (synergy         Chuck and wall temperatures; α      Restore; requalify
   falls) (Ch. 4.2.5)                      run
4. Wall chlorine memory after clean        Wafers since clean                  Season
   (Ch. 7.5)
```

---

**Appendix G Version:** 1.0  
**Last Updated:** 2026-10-05
