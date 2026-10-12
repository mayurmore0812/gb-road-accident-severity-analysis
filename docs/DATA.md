# Data and provenance

## Download and layout

1. Download [UK Car Accidents 2005–2015](https://www.kaggle.com/datasets/silicon99/dft-accident-data) from Kaggle user `silicon99`. Kaggle may require an account and acceptance of its terms.
2. Extract `Accidents0515.csv`, `Vehicles0515.csv` and `Casualties0515.csv` directly into the repository root or keep the archive.zip in the root folder.
3. Open Jupyter from the repository root.

| Table | Rows independently counted | Unit |
|---|---:|---:|
| Accidents0515.csv | 1,780,653 | Accident |
| Vehicles0515.csv | 3,262,270 | Involved vehicle |
| Casualties0515.csv | 2,402,909 | Casualty |

Local accident dates span 2005-01-01 through 2015-12-31. The historical Kaggle version/download date and raw-file checksums are not established in this release. Matching filenames alone do not prove identical content. Current Department for Transport downloads may use newer schemas or revisions and are not automatic substitutes for these exact historical files.

## Fields used

Accidents: `Accident_Index`, `Accident_Severity`, `Number_of_Vehicles`, `Number_of_Casualties`, `Date`, `Day_of_Week`, `Time`, `Police_Force`, `Road_Type`, `Speed_limit`, `Junction_Detail`, `Light_Conditions`, `Weather_Conditions`, `Road_Surface_Conditions`, `Urban_or_Rural_Area`, `Longitude`, `Latitude`.

Vehicles: `Accident_Index`, `Vehicle_Reference`, `Vehicle_Type`.

Casualties: `Accident_Index`, `Vehicle_Reference`, `Casualty_Reference`, `Casualty_Severity`, `Casualty_Type`, `Casualty_Class`.

`Accident_Index` links the tables. Accident severity and casualty severity are distinct. Fatal/Serious/Slight map to 1/2/3. `Severe` and `KSI` select 1 or 2 at their respective row levels. `Year` comes from day-first dates; `Hour` comes from time, with invalid/missing values coerced to missing. `Junction_Group` separates code 0, positive codes and unknowns. User groups identify pedestrians, cyclists and motorcyclists from casualty type.

Lookups: Accident_Severity, Casualty_Severity, Casualty_Type, Day_of_Week, Junction_Detail, Light_Conditions, Police_Force, Road_Type, Urban_Rural, Vehicle_Type. Weather and road-surface labels are defined in notebook code. Unmapped codes become `Not mapped`. `-1` is a coded missing/out-of-range value for relevant categories; it is not a universal indicator of missing numeric measurements such as longitude.

## Source and coverage

The [Department for Transport open-data page](https://www.gov.uk/government/statistical-data-sets/road-safety-open-data) describes the official source. The [official catalogue](https://www.data.gov.uk/dataset/cb7ae6f0-4be6-4935-9277-47e5ce24a11f/road-accidents-safety-data) identifies the publisher and Open Government Licence. These cover reported personal-injury road records, not every crash or every injury. Review [official coverage guidance](https://www.gov.uk/government/publications/road-accidents-and-safety-statistics-notes-and-definitions/road-casualty-statistics-overview-and-coverage) before generalizing.

Source links checked 12 October 2026. Kaggle's exact redistribution licence and the provenance of its supplementary lookup files were not independently established. Official-source OGL metadata should not be treated as proof of every Kaggle addition's licence.
