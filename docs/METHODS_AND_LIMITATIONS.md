# Methods and limitations

## Analytical workflow

```text
Raw Kaggle data files
  Accidents0515.csv      one row per accident
  Vehicles0515.csv       one row per vehicle involved
  Casualties0515.csv     one row per casualty
  contextCSVs/           lookup tables for coded categories
        |
        v
1. Load only required columns
   Keep the notebook focused and reduce memory use.
        |
        v
2. Check data quality
   Check true NaN values with isna().
   Check coded missing/unknown values using coded_minus1.
   Confirm Accident_Index has no duplicate accident rows.
        |
        v
3. Handle missing and unknown values
   Leave rare true NaN values as missing.
   Keep coded unknown values and label them where possible.
   Do not fill missing values with guessed values.
        |
        v
4. Create analysis features
   Year from Date, Hour from Time.
   Readable labels from numeric codes.
   Severe flag for Fatal or Serious accidents.
   Junction_Group for junction vs non-junction accidents.
   User_Group and KSI for vulnerable-road-user analysis.
        |
        v
5. Analyse at the correct level
   Accident questions use unique Accident_Index counts.
   Vehicle questions avoid repeated vehicle-type counts.
   Casualty questions use casualty rows and KSI rates.
        |
        v
6. Produce EDA outputs
   Tables, charts, severe_rate_pct, ksi_rate_pct, and business interpretation.
        |
        v
7. Final recommendations
   Translate the strongest patterns into road-safety actions.
```

The notebook reads selected columns, checks missing values and accident-key duplicates, maps categories, derives temporal and severity fields, and answers ten EDA questions. No train/test split, fitted estimator or predictive accuracy is involved.

`accidents` counts unique accident keys; `severe_accidents` sums the severe flag. This denominator is valid when an accident occurs only once in each grouped input. The vehicle analysis joins on accident key and deduplicates accident/type combinations before grouping. Casualty KSI counts casualty rows after an accident-level join.

## Limits to interpretation

- No mileage, trip, traffic-volume, population or road-length denominator. Severity percentages concern recorded cases only.
- No causal adjustment, confidence intervals, formal significance tests or intervention evaluation.
- Vehicle categories overlap across a multi-vehicle accident. Accident severity does not measure each vehicle occupant's outcome.
- Weather/surface results are joint categories; lighting, rural location and speed limit are correlated factors.
- Speed limit is not actual travel speed. Police-force geography and reporting can differ.
- Minimum groups are 1,000 accidents for weather/surface, 500 accidents for vehicle types, 500 casualties for vulnerable users, and 10,000 accidents for police-force severe-share rankings.
- Date/time missingness affects temporal groups. Unknown/unmapped categories remain where the code permits.
- Historical 2005–2015 data should not be framed as current conditions. Official severity/reporting methods may change over time.
- Some charts use `lakhs`: one lakh is 100,000. Dual-axis annual charts can exaggerate apparent relationships if interpreted carelessly.
