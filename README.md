# Agricultural Performance and Seasonal Analysis Using Data Analytics

## Overview
This project analyzes 24 years (1997–2020) of Indian state-wise crop data to understand production and
yield trends, crop and regional performance, seasonal cropping patterns, and the relationship between
environmental/input factors (rainfall, fertilizer, pesticide) and yield. The analysis follows a
**Raw Data → Information → Insights → Decision → Action** framework and concludes with risks, opportunities,
and concrete recommendations rather than exploratory code alone.

## Problem Statement
Agricultural stakeholders (policy planners, agribusinesses, researchers) need a clear, evidence-based view of
how crop production and yield have evolved across crops, states, and seasons in India, and whether commonly
assumed drivers of yield (rainfall, fertilizer, pesticide) show a measurable statistical relationship with
outcomes — in order to prioritize where to invest and what risks to monitor.

## Objectives
1. Identify overall national production and yield trends (1997–2019).
2. Evaluate crop-wise performance (production and yield).
3. Evaluate state/regional performance.
4. Analyze seasonal (cropping-season) patterns.
5. Examine relationships between rainfall, fertilizer, pesticide usage, and yield.
6. Surface risks, opportunities, and actionable recommendations for agricultural decision-making.

## Dataset
- **Source:** [Crop Yield in Indian States Dataset — Kaggle](https://www.kaggle.com/datasets/akshatgupta7/crop-yield-in-indian-states-dataset/versions/1)
- **File:** `crop_yield.csv`
- **Rows / Columns:** 19,689 rows × 10 columns
- **Years covered:** 1997–2020 (2020 has only 37 records and is treated as a partial year, excluded from
  annual trend charts and growth-rate calculations)
- **Crops:** 55 | **States:** 30 | **Seasons:** 6 (Whole Year, Kharif, Rabi, Autumn, Summer, Winter)
- **Missing values:** none | **Duplicate rows:** none
- **Known quality note:** categorical columns (`Crop`, `Season`, `State`) contain trailing whitespace in the
  raw file and are stripped during cleaning.

### Data Dictionary
| Column | Description |
|---|---|
| Crop | Name of the crop |
| Crop_Year | Year the crop was harvested |
| Season | Cropping season (Kharif, Rabi, Whole Year, Autumn, Summer, Winter) |
| State | Indian state |
| Area | Cultivated area (hectares) |
| Production | Total production (units vary by crop — most crops in tonnes; coconut in nut-count) |
| Annual_Rainfall | Annual rainfall recorded for that state (mm) |
| Fertilizer | Total fertilizer used (kg) |
| Pesticide | Total pesticide used (kg) |
| Yield | Production per unit area (Production / Area) |

## Technologies / Libraries
- Python 3
- pandas, numpy — data manipulation
- matplotlib, seaborn — visualization
- scipy — statistical calculations
- Jupyter Notebook — analysis environment

## Project Structure
```
.
├── Agricultural_Performance_Analysis.ipynb   # Main analysis notebook (run this)
├── crop_yield.csv                            # Dataset (place in same folder as notebook)
├── requirements.txt                          # Python dependencies
├── Agricultural_Performance_Analysis_Report.pdf   # Full written project report
└── README.md                                 # This file
```

## How to Install Requirements
```bash
pip install -r requirements.txt
```

## How to Run the Notebook
1. Ensure `crop_yield.csv` is in the same folder as the notebook.
2. Install dependencies (see above).
3. Launch Jupyter and run all cells top to bottom:
```bash
jupyter notebook Agricultural_Performance_Analysis.ipynb
```
The notebook has been executed end-to-end without errors prior to submission.

## Key Analytical Areas
- Data quality checks and cleaning (whitespace, zero-production investigation, extreme-value investigation)
- KPI analysis (production, yield, area, rainfall, fertilizer, pesticide, crop/state counts)
- Yearly production and yield trend analysis (1997–2019)
- Crop-wise performance (top production, top yield, lowest yield)
- State/regional performance (top production, top/bottom yield states)
- Seasonal analysis (production and yield by cropping season)
- Rainfall vs yield and fertilizer/pesticide (per-hectare) vs yield correlation analysis
- Risk identification (rainfall variability, zero-production incidents) and actionable recommendations

## Important Findings (Summary)
- Reported national production grew substantially (1997→2019) while cultivated area stayed nearly flat,
  indicating **yield/productivity-led growth**, not land expansion.
- **Coconut dominates raw production and yield totals**, but this is largely a unit-of-measurement effect
  (nut-count vs. tonnes for other crops) rather than genuine cross-crop superiority.
- `Kharif` (monsoon) is the largest cropping season by cultivated area; `Whole Year` (perennial crops) shows
  the highest average yield.
- Rainfall, fertilizer-per-hectare, and pesticide-per-hectare each show **near-zero linear correlation with
  yield at the pooled, all-crop level** — correlation is not causation, and this pooled result should not be
  read as evidence these inputs don't matter; it reflects the need for crop-specific analysis.
- `Area`, `Fertilizer`, and `Pesticide` totals are very strongly correlated with each other (r ≈ 0.95–0.97),
  since larger farms mechanically use more total input — this is why per-hectare (intensity) figures, not
  raw totals, are used when relating inputs to yield.
- 112 records (≈0.57% of rows) report zero production despite non-zero cultivated area, concentrated in a
  small set of states and crops — treated as legitimate harvest-failure signals, not deleted.

## Limitations
- Descriptive/correlational analysis of secondary, state-reported data; does not control for soil quality,
  irrigation access, farm size, market prices, or crop variety.
- 2020 is a partial year in this dataset (37 records) and is excluded from annual trend/growth calculations.
- Correlation coefficients must not be interpreted as causal relationships.
- Aggregated, all-crop correlation analysis can mask genuine crop-specific relationships; a follow-up
  crop-specific or regional regression study is recommended.

## Submission Files
1. **Agricultural_Performance_Analysis.ipynb** — complete, executed analysis notebook
2. **requirements.txt** — Python dependencies
3. **Agricultural_Performance_Analysis_Report.pdf** — detailed project report with embedded charts
4. **README.md** — this file
