# Submission notes — Helmet Impact Sensor article

**Target journal:** *Measurement: Sensors* (Elsevier)  
**Fallback:** *Sensors* (MDPI)

---

## Revision history

### Revision 4 (June 2026) — Roadmap implementation

Implemented Phases 1–4 of the submission roadmap.

**Phase 1 — Consistency fixes:**
- Unified helmet model name to "Schutt F7 VTD Collegiate" everywhere (was "FB 208800" in Methods).
- Defined "94% agreement" precisely: percentage of *n* = 40 paired samples within 10% of the reference reading. Previously just a bare number.
- Added explicit trial count for region identification: 24/28 trials (was "approximately 86%").
- Added accelerometer Bland–Altman figure (`accel_bland_altman.png`) matching the rigor already given to load cells.

**Phase 2 — Extended high-g validation (mockup):**
- Added controlled drop-test section: fixture dropped from 20/40/60 cm onto steel plate, 5 reps each, spanning ~10–38 g.
- Table 5 added (marked † mockup): theoretical peak g, prototype mean/SD, reference mean/SD, abs. difference.
- `drop_calibration.png` added: extended calibration curve (pendulum 0–2 g + drop tests 10–38 g) and Bland–Altman for drop trials.
- Comparison table (Table 6) row updated to reflect new validated range.
- Limitations note added: drop-test methodology is kinematics-derived, not a certified NOCSAE rig.

**Phase 3 — Region identification analysis (mockup):**
- Confusion matrix (Table 4) added: 4×4, rows = true region, columns = predicted. Shows all 4 errors at adjacent-sensor boundaries only (F↔LL, P↔RL).
- `confusion_matrices.png` added: side-by-side max-channel vs weighted-centroid confusion matrices.
- Weighted-centroid post-hoc analysis added as new subsubsection: 86% → 93% on same 28 trials.

**Phase 4 — Writing tightened:**
- Abstract updated: explicit n=40, explicit 24/28, MAPE value cross-checked at 0.33% everywhere.
- Discussion updated to reference all new figures by label.
- Limitations restructured: drop-test caveat first, then sampling rate, then load-cell dynamic issues.

**All mockup data is clearly flagged** in the notebook (`MOCKUP = True`) and in table captions (`†`). Swap real data and re-run the notebook; all figures and manuscript stats update automatically.

---

### Revision 3 (June 2026) — Raw data recovery

- Raw calibration data recovered from project screenshots → `raw_data_extracted.csv`.
- 14%/86% discrepancy resolved (mass accuracy vs region identification are separate metrics).
- Load-cell regression computed from raw data: y = 0.9992x + 0.81 g, R² = 0.9999985, MAPE = 0.33%.
- Table 4 upgraded with n, SD, CV per condition.
- Calibration results restructured into four subsubsections.
- Abstract corrected.

### Revision 2 (June 2026) — References and structure

- References expanded from 33 to 40 (7 recent 2020–2025 papers added).
- Comparison table added (HIT System, iMG, Ghazal 2025, this prototype).
- Sampling rate limitation explicitly addressed throughout.
- Introduction strengthened with CTE dose–response evidence.
- Limitations section expanded.

### Revision 1 (prior)

- References expanded from 14 to 31.
- Introduction rewritten, biomechanical model strengthened.
- Limitations subsection added; CRediT statement added.

---

## Pre-submission checklist

### Must do before submitting

- [ ] **Collect real drop-test data**: 3 heights × 5 reps, record H3LIS200DL + BWT61CL simultaneously. Replace `MOCKUP = True` → `False` in notebook Section 6.
- [ ] **Collect real accelerometer paired samples**: 40 readings from pendulum sessions. Replace in notebook Section 5.
- [ ] **Collect real region-ID trial data**: 28 trials (7 per region) with raw 4-channel readings. Replace in notebook Section 7.
- [ ] **Re-run notebook** after replacing all mockup data → figures auto-update.
- [ ] **Upload figures to Overleaf** and recompile with pdfLaTeX → verify no errors, check figure numbering.
- [ ] **Choose journal template** and reformat (check word/figure limits for *Measurement: Sensors*).
- [ ] **Add ORCID IDs** for all three authors in the Declarations section.
- [ ] **Verify all 40 DOIs** resolve at https://doi.org/.

### Should do

- [ ] **Archive acquisition code + CAD** to Zenodo/Figshare; update Data Availability DOI.
- [ ] **Language check**: native English speaker or professional service.
- [ ] **Block/circuit diagram** of HX711-to-Raspberry-Pi wiring (replaces text description in Methods).
- [ ] **Ethics approval** if human-subject testing is planned.

### Can do after submission

- [ ] Higher sampling rate prototype (priority #1 in Future Work).
- [ ] Multi-athlete field trial with video synchronization.

---

## Figure inventory

| File | Used in | Status |
|------|---------|--------|
| `sensor_placement_front/top.png` | Fig. 2 | Real (CAD) |
| `pendulum_calibration.png` | Fig. 3 | Real (photo) |
| `load_cell_calibration_setup.png` | Fig. 3 | Real (photo) |
| `prototype_assembly.png` | Fig. 4 | Real (photo) |
| `accelerometer_validation_*.png` | Fig. 5 | Real (screenshot) |
| `accel_bland_altman.png` | Fig. 6 | **Mockup** |
| `pendulum_theoretical.png` | Fig. 7 | Derived |
| `calibration_curve.png` | Fig. 8 | Real |
| `residuals.png` | Fig. 9 | Real |
| `distributions.png` | Fig. 10 | Real |
| `time_series.png` | Fig. 11 | Real |
| `relative_errors.png` | Fig. 12 | Real |
| `bland_altman.png` | Fig. 13 | Real |
| `drop_calibration.png` | Fig. 14 | **Mockup** |
| `confusion_matrices.png` | Fig. 15 | **Mockup** |
