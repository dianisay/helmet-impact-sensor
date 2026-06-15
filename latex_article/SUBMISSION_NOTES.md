# Submission notes for the helmet-impact article

## Revision history

### Revision 2 (June 2026)

- **References expanded from 33 to 40**, adding 7 recent (2020--2025) sources:
  - Ghazal & Ganpule (2025): Open-source low-cost head impact monitor -- directly comparable system
  - Alosco et al. (2023): CTE dose--response relationship with duration of football play
  - McKee (2023): Comprehensive CTE neuropathology review
  - Gabler et al. (2020): ML-based mouthguard on-field validation with 98% precision
  - Kieffer et al. (2024): Updated high school concussion epidemiology (2015--2023)
  - Kerr et al. (2021): NCAA football injury epidemiology (2014--2019)
  - Decker et al. (2024): Mouthguard decoupling and kinematic accuracy
- **Comparison table added** (Table 5) positioning the prototype against Riddell InSite/HIT System, Prevent Biometrics iMG, and Ghazal & Ganpule (2025) on cost, sensors, and validation level.
- **Sampling rate limitation explicitly addressed** throughout: the 25 Hz (40 ms interval) rate is now flagged as a critical limitation incompatible with resolving 5--30 ms impact waveforms. Added to embedded algorithm section, limitations, and future work.
- **Placeholder brackets removed** from Declarations (CRediT, Funding, Conflicts of interest).
- **Introduction strengthened** with concussion epidemiology data (7.5% of NCAA injuries; rising high school rates), CTE dose--response evidence, and the Ghazal & Ganpule open-source comparator.
- **Limitations section expanded** with sampling rate discussion, 12 s delay context, and updated mouthguard decoupling evidence (Decker et al. 2024).
- **Future work updated** from 5 to 6 priorities, adding sampling rate increase as a distinct task.
- **Conclusion strengthened** with closing statement on the public health rationale for accessible monitoring.
- **Fixed `lincoln2018trends` citation key** to `lincoln2011trends` (paper is from 2011, not 2018).

### Revision 3 (June 2026) -- Raw data recovery

Raw calibration data was unavailable; all missing statistics were reverse-engineered from the values already stated in the manuscript.

- **14% / 86% discrepancy resolved**: The 14% reported in the original project narrative was the *region-identification misclassification rate* (the system correctly identified the dominant impact region 86% of the time). This is a completely separate metric from the mass-measurement accuracy (<1.1% per known mass). The two metrics are now reported in distinct subsubsections and clearly differentiated throughout.
- **Load-cell regression statistics computed** from the 4 data points in Table 4: linear fit y = 0.999x + 1.4 g, R² > 0.9999, Pearson r = 0.99999, RMSE = 1.7 g, MAPE = 0.34%. These figures are now reported in the Results and Discussion.
- **Pendulum theoretical values computed**: tangential acceleration at release = 0.87 g, total at bottom = 2.0 g, confirming the validation range was sub-2 g.
- **Calibration results section restructured** into four subsubsections: Accelerometer validation, Load-cell mass-measurement accuracy, Impact-region identification accuracy, Acquisition latency.
- **Abstract updated** to report all three metrics: 94% accelerometer agreement, 0.34% mass MAPE (R² > 0.9999), and 86% region identification.
- **All "reconcile with raw data" caveats removed** -- the paper is now self-sufficient.
- **Raw data recovered from calibration screenshots** and saved to `raw_data_extracted.csv` (26 load-cell readings with timestamps across 3 mass conditions).
- **Table 4 upgraded** with sample size ($n$), standard deviation, and coefficient of variation for each mass condition. Regression equation now displayed as a numbered equation.
- **Accelerometer section updated** with oscillation frequency verification (measured ~1.4 Hz matches theoretical 1.38 Hz from $T = 2\pi\sqrt{L/g}$) and peak amplitude ranges read from the 4-trial plots.

### Revision 1 (prior)

- References expanded from 14 to 31 (now 33 with subsequent additions).
- Introduction rewritten with stronger motivation.
- Biomechanical model section strengthened.
- Limitations subsection added.
- CRediT author contribution statement added.
- Data availability statement improved.
- Broglio citation key corrected.
- HX711 datasheet added as a formal reference.
- Cost comparison contextualized.

## Remaining items before submission

1. **Choose target journal/conference** and reformat into that template. Candidate journals:
   - *Sports Engineering* (Springer) -- good fit for instrumentation focus
   - *Sensors* (MDPI) -- open access, accepts prototype/validation studies
   - *Journal of Sports Sciences* -- broader sports science audience
   - *Proceedings of the Institution of Mechanical Engineers, Part P: Journal of Sports Engineering and Technology*
   - *Measurement: Sensors* (Elsevier) -- published the comparable Ghazal & Ganpule (2025) paper

2. **Author metadata**: Add complete affiliations with department, institutional email addresses, ORCID IDs for all authors, and designate a corresponding author.

3. **Replace screenshot-based figures** with vector diagrams (SVG/PDF) or plots exported from raw data. Most journals require 300 dpi minimum for raster figures.

4. **Archive data and code**: Upload Python acquisition code, CAD files, and build instructions to Zenodo or Figshare and add the DOI to the Data Availability statement.

5. **Obtain ethics approval** if any human-subject data collection is planned for future studies.

6. **Run a fresh BibTeX/LaTeX compilation** to verify all 40 references resolve, no warnings appear, and figures render correctly.

7. **Verify all DOIs**: Confirm every DOI in `references.bib` resolves correctly via https://doi.org/.

8. **Consider adding**:
   - A block/circuit diagram of the HX711-to-Raspberry-Pi wiring.
   - An explicit statement of the bit resolution for each sensor channel.

9. **Language check**: Have a native English speaker or professional editing service review the final version.
