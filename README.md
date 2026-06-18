# Low-Cost Helmet-Integrated Head Impact Monitoring System

A low-cost, helmet-integrated prototype for measuring head impacts in American football,
developed at Tecnológico de Monterrey, Campus Ciudad de México.

## Overview

The system combines an H3LIS200DL triaxial accelerometer, four SEN-10245 load cells with
HX711 conditioning modules, and a Raspberry Pi Zero 2 W to:

1. Detect head-impact events above a configurable acceleration threshold (default: 14.4 g)
2. Estimate the dominant impact region from four load-cell channels
3. Display color-coded sideline alerts for coaching staff

Total hardware cost: **~US$96** (vs. US$1,000–3,000 for commercial alternatives).

## Repository structure

```
├── latex_article/
│   ├── main.tex                    # Article source (LaTeX)
│   ├── references.bib              # Bibliography (40 references)
│   ├── main.bbl                    # Compiled bibliography (Overleaf)
│   ├── raw_data_extracted.csv      # Raw load-cell calibration readings
│   ├── figures/                    # All manuscript figures (PNG + PDF)
│   └── SUBMISSION_NOTES.md         # Revision history & submission checklist
├── analysis/
│   ├── calibration_analysis.ipynb  # Full analysis notebook (10 figure sections)
│   └── figures/                    # Publication-quality plots (PNG + PDF)
├── Proyecto_Casco_ITESM (1).pdf    # Original project report
└── README.md
```

## Analysis notebook — sections

The notebook generates **10 publication-quality figure sets** and prints a manuscript
summary. Mockup data is clearly flagged with `MOCKUP = True`; swap in real arrays and
re-run to update all figures automatically.

| Section | Figure(s) | Status |
|---------|-----------|--------|
| 3 | Descriptive stats table | Real data |
| 4.1 | Calibration curve (load cell) | Real data |
| 4.2 | Regression residuals | Real data |
| 4.3 | Per-condition distributions | Real data |
| 4.4 | Time-series stability | Real data |
| 4.5 | Relative error bar chart | Real data |
| 4.6 | Bland–Altman (load cell) | Real data |
| 5 | Bland–Altman (accelerometer, pendulum) | **Mockup** — replace `accel_proto` / `accel_ref` |
| 6 | Extended calibration + Bland–Altman (drop tests) | **Mockup** — replace `proto_readings` / `ref_readings` |
| 7 | Confusion matrices + weighted-centroid | **Mockup** — replace `region_true` / `channel_readings` |
| 8 | Theoretical pendulum simulation | Derived (no raw data needed) |

### Requirements

```
numpy >= 2.0
pandas >= 2.0
matplotlib >= 3.8
scipy >= 1.12
```

### Running

```bash
pip install numpy pandas matplotlib scipy
jupyter lab analysis/calibration_analysis.ipynb
# Kernel → Restart & Run All
```

## Key results (current manuscript)

| Metric | Value | Data source |
|--------|-------|-------------|
| Accelerometer pendulum agreement (within 10%) | 94% (n=40) | Mockup |
| Accelerometer MAPE vs reference | 3.5% | Mockup |
| Drop-test extended range | 10–38 g, R² > 0.998 | Mockup |
| Load-cell mass MAPE | 0.33% | **Real** |
| Load-cell R² | > 0.9999 | **Real** |
| Region ID accuracy (max-channel) | 86% (24/28) | Mockup |
| Region ID accuracy (weighted-centroid) | 93% (26/28) | Mockup |
| Hardware cost | US$95.90 | **Real** |

## Target venue

**Primary:** *Measurement: Sensors* (Elsevier) — published the closest comparator
(Ghazal & Ganpule 2025) and explicitly welcomes benchtop-validation sensor papers.  
**Fallback:** *Sensors* (MDPI).

## Disclaimer

This prototype is a **screening and research device only**. It does not diagnose
concussion and must not determine return-to-play status.

## Authors

- Juan Ramón Lara Mora
- Diana Paola Ayala Roldán *(corresponding — A01365809@tec.mx)*
- Mariel Alfaro Ponce *(supervisor)*

Tecnológico de Monterrey, Campus Ciudad de México, School of Engineering and Sciences
