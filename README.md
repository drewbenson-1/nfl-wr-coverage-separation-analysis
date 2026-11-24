# nfl-wr-coverage-separation-analysis
Built a Python (pandas, matplotlib) pipeline joining 2026 NFL wide receiver coverage and situational datasets to evaluate Man Coverage Separation Score against Targets Per Route Run (TPRR) across qualified receivers ($\ge 50$ Man and $\ge 50$ Zone routes).
# NFL Wide Receiver Separation & Target Efficiency by Coverage Shell (2026)

## Overview
This project merges two 2026 NFL wide receiver datasets—**Receiving Separation by Coverage** and **Receiving – Situation**—in Python (`pandas` + `matplotlib`) to evaluate how wide receivers separate against Man vs. Zone coverage relative to their target rate (`TPRR`).

## Methodology
1. **Multi-Header Parsing:** Flattened two-tier CSV headers and removed summary rows (`League Avg`) while preserving `player_id` keys.
2. **Relational Join:** Merged coverage separation scores and situational efficiency metrics on `player_id` (`n = 149` WRs).
3. **Sample Filtering:** Filtered to receivers with **>= 50 Man routes AND >= 50 Zone routes** (`n = 56`) to minimize small-sample variance.
4. **Feature Engineering:**
   - `sep_diff_man_zone`: Man Separation Score minus Zone Separation Score
   - `man_underutilized_gap`: Standardized Man Separation (`z-score`) minus standardized Man `TPRR` (`z-score`)

## Key Findings
- **Man vs. Zone Baseline:** Qualified WRs averaged a `0.113` separation score against Man coverage vs. `0.064` against Zone (`+0.049` mean differential).
- **Top Man-Over-Zone Separators:** DeMario Douglas (`+0.357`), Garrett Wilson (`+0.294`), Jaxon Smith-Njigba (`+0.272`), and Ja'Marr Chase (`+0.263`).
- **Underutilized Man Separation:** Jerry Jeudy, Ja'Marr Chase, and Antonio Williams posted strong Man separation relative to their Man `TPRR`.

## Files
- `NFL_WR_Sep_by_Coverage.ipynb` — Full data cleaning, merging, feature engineering, and visualization notebook
- `wr_coverage_separation_2026_clean.csv` — Qualified WR analytical dataset (`n = 56`)
- `wr_man_sep_vs_tprr.png` — Quadrant scatter plot comparing Man Separation Score vs. Man TPRR
