# Low-Cost Helmet-Integrated Head Impact Monitoring System

A low-cost, helmet-integrated prototype for measuring head impacts in American football, developed at Tecnológico de Monterrey, Campus Ciudad de México.

## Overview

The system combines an H3LIS200DL triaxial accelerometer, four SEN-10245 load cells with HX711 conditioning modules, and a Raspberry Pi Zero 2 W to:

1. Detect head-impact events above a configurable acceleration threshold (default: 14.4 g)
2. Estimate the dominant impact region from four load-cell channels
3. Display color-coded sideline alerts for coaching staff

Total hardware cost: **~US$96** (vs. US$1,000–3,000 for commercial alternatives).

## Repository structure

```
├── latex_article/          # Manuscript (LaTeX)
│   ├── main.tex            # Main article source
│   ├── references.bib      # Bibliography (40 references)
│   ├── main.bbl            # Compiled bibliography
│   ├── raw_data_extracted.csv  # Calibration data extracted from project screenshots
│   ├── figures/            # Manuscript figures (CAD, calibration photos, plots)
│   └── SUBMISSION_NOTES.md # Journal submission checklist
├── analysis/               # Data analysis
│   ├── calibration_analysis.ipynb  # Jupyter notebook with full statistical analysis
│   └── figures/            # Publication-quality plots (PDF + PNG)
└── README.md
```

## Analysis notebook

The Jupyter notebook `analysis/calibration_analysis.ipynb` reproduces all calibration statistics and generates 6 publication-quality figures:

- **Calibration curve** — measured vs expected mass with linear regression
- **Residual plot** — regression residuals by mass condition
- **Distributions** — box-and-strip plots of individual readings per condition
- **Time series** — consecutive load-cell readings over time
- **Relative errors** — horizontal bar chart of per-condition measurement error
- **Bland–Altman plot** — difference vs mean agreement analysis
- **Pendulum simulation** — theoretical acceleration waveforms

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
```

## Key results

| Metric | Value |
|--------|-------|
| Accelerometer agreement with commercial reference | ~94% |
| Load-cell mass-measurement MAPE | 0.33% |
| Load-cell R² (linear fit) | > 0.9999 |
| Impact-region identification accuracy | 86% |
| Hardware cost per helmet | US$95.90 |

## Disclaimer

This prototype is a **screening and research device only**. It does not diagnose concussion and must not determine return-to-play status. See the manuscript for full limitations and clinical context.

## Authors

- Juan Ramón Lara Mora
- Montserrat Sánchez Chávez
- Mariel Alfaro Ponce
- Gerardo Julián Ramírez-Nava

Tecnológico de Monterrey, Campus Ciudad de México, School of Engineering and Sciences
