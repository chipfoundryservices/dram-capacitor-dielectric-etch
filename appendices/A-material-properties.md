# Appendix A: Material Properties

Properties of the dielectrics, electrodes, and landing films that the three dielectric etches remove, stop on, or leave behind, as used in this book. Values are representative of thin films deposited as described in Chapter 2; bulk values are given where the film value is not well defined. All values are illustrative.

---

## A.1 Capacitor Dielectrics

```
Property                    ZrO₂            ZrO₂            Al₂O₃ (ALD)     HfO₂
                            (tetragonal)    (amorphous)
───────────────────────────────────────────────────────────────────────────────────────
Thickness (reference)       2 × 2.6 nm      as deposited    0.3 nm          —
Deposition                  ALD, CpZr(NMe₂)₃ / O₃, 300 °C   TMA / O₃, 300 °C  —
Growth per cycle            ≈ 0.09 nm       ≈ 0.09 nm       ≈ 0.10 nm       ≈ 0.09 nm
Dielectric constant         ≈ 40–55         ≈ 20–25         ≈ 9             ≈ 20–25
                            (layer-
                            thickness
                            dependent)
Band gap (eV)               ≈ 5.8           ≈ 5.5           ≈ 8.8           ≈ 5.8
Density (g/cm³)             5.9–6.1         ≈ 5.3           ≈ 3.0–3.2       ≈ 9.7
Molar mass (g/mol)          123.2           123.2           102.0           210.5
Metal density per nm        2.9 × 10¹⁵      2.6 × 10¹⁵      3.7 × 10¹⁵ Al   2.8 × 10¹⁵
of film (atoms/cm²)                                         per nm
Refractive index (633 nm)   ≈ 2.15          ≈ 2.05          ≈ 1.64          ≈ 2.05
Crystallization             350–425 °C,     —               > 800 °C        ≈ 450 °C
                            thickness-
                            dependent
Grain size                  10–30 nm        —               amorphous       10–30 nm
                            (median ≈ 20)
```

```
ZAZ reference stack:
  Layers                     ZrO₂ 2.6 / Al₂O₃ 0.3 / ZrO₂ 2.6 nm = 5.5 nm
  k_eff                      ≈ 43 (from measured EOT)
  EOT                        0.50 nm (C–V); layer sum ≈ 0.55 nm
  Leakage at 1.0 V, 85 °C    ≈ 8 × 10⁻⁷ A/cm² ≈ 1 fA per cell
  Leakage thickness scale    λ ≈ 0.25 nm (J ∝ exp(−t/λ))
  Breakdown (TDDB) Weibull   β ≈ 2.0
  Zr areal density           ≈ 1.5 × 10¹⁶ atoms/cm²
  Al areal density           ≈ 1.1 × 10¹⁵ atoms/cm²

ZAZ pilot (module 3):        ZrO₂ 2.6 / Al₂O₃ 0.3 / ZrO₂ 3.6 nm = 6.5 nm,
                             trimmed to 5.5 nm; EOT 0.475 nm
```

---

## A.2 Alternative Dielectrics (Chapter 14)

```
Property                    TiO₂ (rutile)    SrTiO₃           Hf₀.₅Zr₀.₅O₂      La-doped ZrO₂
───────────────────────────────────────────────────────────────────────────────────────────
Dielectric constant         80–100           100–300          ≈ 30–40 (AFE      ≈ 40–50
                                             (thickness-      boost near the
                                             dependent)       transition)
Band gap (eV)               ≈ 3.0–3.3        ≈ 3.2            ≈ 5.6             ≈ 5.7
Electrode                   Ru / RuO₂        Ru, Pt           TiN               TiN
Problem halide              —                SrCl₂ (bp        —                 LaCl₃ (non-
                                             1250 °C)                           volatile)
Water-soluble residue       —                SrCl₂: yes       —                 LaCl₃: yes
```

---

## A.3 Electrodes

```
Property                    TiN (storage node,  TiN (top electrode,   SiGe:B (plate)    W (strap)
                            CVD fill)           ALD)
───────────────────────────────────────────────────────────────────────────────────────────
Thickness (reference)       pillar 32/28/24 nm  5.0 nm                150 nm            40 nm
                            wide
Deposition                  pulsed CVD, 580 °C  TiCl₄ / NH₃, 400 °C   LPCVD, 425 °C     PVD
Resistivity                 150–200 µΩ·cm       ≈ 250 µΩ·cm           ≈ 2 mΩ·cm         ≈ 15 µΩ·cm
Cl content                  ≈ 0.5 at%           ≈ 1 at%               —                 —
Interface with ZAZ          TiOₓNᵧ ≈ 0.4 nm     O-scavenging of the   —                 —
                                                top ZrO₂
Etch in the TiN clear       —                   ≈ 40 nm/min (Cl₂/Ar,  —                 —
                                                60 eV)
```

---

## A.4 Landing and Edge Films

```
Property                    PECVD SiN (periphery   PE-TEOS SiO₂     LPCVD SiN          Si (apex)
                            top)                                    (backside)
─────────────────────────────────────────────────────────────────────────────────────────────
Thickness (reference)       120 nm                 —                ≈ 100 nm           bulk
Refractive index (633 nm)   ≈ 1.95                 ≈ 1.46           ≈ 2.01             3.88
Main-step rate (150 eV)     8 nm/min               5 nm/min         ≈ 6 nm/min         —
ALE EPC (60 eV)             0.015 nm/cycle         0.03 nm/cycle    ≈ 0.012            —
Thermal ALE EPC (250 °C)    ≈ 0.005 nm/cycle       ≈ 0.01           ≈ 0.004            —
```

---

## A.5 Geometry of the Reference Array and Wafer

```
Array (Books #29–32):
  Cell                       1b-class 6F², F = 17 nm, 1734 nm² per cell
  Storage-node pitch         45 nm hexagonal
  Mold                       1.60 µm; top SiN support 122 → 120 nm
  Pillars                    TiN, 32 / 28 / 24 nm (top / average / bottom)
  Effective capacitor area   1.24 × 10⁵ nm² per cell
  C_s                        8.6 fF
  Channel radius after ZAZ   4.8 nm (top) / 6.5 / 8.5 nm (bottom)

1c pilot (Chapter 12):
  Pitch 41 nm; pillars 27 / 24 / 21 nm below the support
  Effective area 1.05 × 10⁵ nm²; channel depth ≈ 1.48 µm
  Channel radius before the dielectric 10.2 / 11.7 / 13.2 nm

Die and wafer:
  16 Gb die, ≈ 1.7 × 10¹⁰ cells, ≈ 0.66 cm²; ≈ 950 dies per wafer
  Plate coverage 55%; periphery and scribe 45% (≈ 318 cm²)
  Array dielectric area per wafer ≈ 2 m²; per die ≈ 21 cm²
  Periphery contacts ≈ 3 × 10⁷ per die, 40 × 40 nm bottoms
  Grain sites under contacts ≈ 1.2 × 10⁸ per die

Wafer edge:
  Front ring removed by module 1        r ≥ 148.8 mm (≈ 11 cm²)
  Apex                                   ≈ 7 cm²
  Backside ring removed                  r ≥ 147.0 mm (≈ 28 cm²)
  ALD seal (backside wrap stops)         r ≈ 147.5 mm
```

---

**Appendix A Version:** 1.0
