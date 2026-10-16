A data cleaning project on real hospital records: handling missing values, standardizing text, and preparing the data for analysis using **Microsoft Excel (Power Query)**.

**Dataset:** [Diabetes 130-US Hospitals for Years 1999–2008](https://archive.ics.uci.edu/dataset/296/diabetes-130-us-hospitals-for-years-1999-2008) – UCI Machine Learning Repository (CC BY 4.0). Records are de-identified (no patient names).

## Results

| | Before | After |
|---|---|---|
| Rows (hospital encounters) | 101,766 | **101,763** |
| Columns | 50 | **48** |
| `?` placeholders for missing values | 192,849 | **0** |
| Blank cells | – | **0** |
| Duplicate rows | 0 | **0** |

## Problems found and how they were fixed

| Problem | Fix |
|---|---|
| Missing values written as `?` in 7 columns | Replaced with real empty values, then labeled `Unknown` |
| `weight` column: 97% missing (98,569 rows) | Column removed (too sparse to be useful) |
| `payer_code` column: 40% missing (40,256 rows) | Column removed |
| 3 rows with gender `Unknown/Invalid` | Removed |
| Age stored as text ranges like `[70-80)` | Cleaned to `70-80` |
| Lab results (`Max_Glu_Serum`, `A1C_Result`) showing `None` | Renamed to `Not Tested` (the test was not done, not a missing value) |
| Missing `Race` (2,271), `Medical_Specialty` (49,947), `Diag_1/2/3` | Labeled `Unknown` instead of deleting the rows |
| Inconsistent column names | Standardized (e.g. `A1C_Result`, `Diabetes_Med`) |

**Decision worth noting:** 30,248 rows belong to patients who were admitted more than once (71,515 unique patients). These are real separate hospital stays, not duplicates, so they were kept.

ID columns (`Admission_Type_Id`, `Discharge_Disposition_Id`, `Admission_Source_Id`) were kept as codes. Their meanings are in the cleaned lookup file `IDS_mapping_Clean.xlsx`.

## Files

- `diabetic_data.csv` – raw data
- `diabetic_data_Clean.xlsx` – cleaned data
- `IDS_mapping.csv` – raw lookup table for ID codes
- `IDS_mapping_Clean.xlsx` – cleaned lookup table (3 sheets: admission type, discharge disposition, admission source)

## Tools

Microsoft Excel · Power Query (M language)

## Author

**Basmala Amgad** – Data Entry & Data Cleaning
