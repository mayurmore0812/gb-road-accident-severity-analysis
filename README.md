# Great Britain Road Accident Severity Analysis (2005–2015)

> **Repository status:** README-only preview. The project notebook and supporting files have not been published here yet.

## Project question

Which recorded conditions were associated with a higher share of serious or fatal road accidents in Great Britain between 2005 and 2015? 

This academic project uses exploratory analysis to describe patterns and communicate road-safety questions. It does not train an accident-prediction model.

## Data and approach

The analysis uses accident, vehicle, and casualty tables from a Kaggle collection based on British road-safety records. The saved notebook reports **1,780,653 accident records** for 2005–2015. I prepared dates and coded categories, joined the tables with attention to their different units, and built grouped summaries and visualisations across ten questions.

- **Accident-level measures** count unique accidents.
- **Vehicle-level measures** describe vehicles involved in recorded accidents.
- **Casualty-level measures** describe people recorded as casualties.

Keeping those units separate avoids treating multiple vehicles or casualties from one event as multiple accidents.

## Selected findings from the saved analysis

| Observation | Saved result |
|---|---:|
| Recorded accidents in 2005 and 2015 | 198,735 → 140,056 |
| Share of recorded accidents classified as serious or fatal in 2005 and 2015 | 14.06% → 15.46% |
| Serious or fatal share among recorded rural and urban accidents | 18.37% rural; 12.96% urban |

These are **descriptive shares among recorded accidents**, not the probability of a crash for a road user. The analysis does not adjust for traffic exposure, travel distance, reporting changes, or other factors needed to infer causal effects.

## Release plan

The reviewed notebook contains the full analysis, tables, and charts. Before adding it to this repository, I plan to clean the notebook, document the data source and category definitions, prepare setup instructions, and check what can be redistributed. Large raw data files will be replaced with acquisition instructions where appropriate.

**Tools used:** Python, pandas, NumPy, matplotlib, seaborn.

## Project status

This README describes completed academic analysis reflected in saved notebook outputs. Code, data, and a reproducible environment are **not yet available in this repository**.
