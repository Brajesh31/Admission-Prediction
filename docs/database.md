# 🗃️ Data Storage and Dataset Schema

## 1. Storage status
The project does not currently use a database. The notebook reads a local CSV file, `admission_predict.csv`. This document's filename is retained for continuity. It describes the dataset and tabular schema, not a SQL database.

## 2. Logical structure

| Field | Meaning | Usage |
|---|---|---|
| `Serial No.` | Row identifier | Not a predictive feature |
| `GRE Score` | GRE score | Predictor |
| `TOEFL Score` | TOEFL score | Predictor |
| `University Rating` | University rating | Predictor |
| `SOP` | Statement of purpose rating | Predictor |
| `LOR ` | Letter of recommendation rating | Predictor |
| `CGPA` | Grade-point average | Predictor |
| `Research` | Research experience indicator | Predictor |
| `Chance of Admit ` | Numeric target | Regression label |

The source headers include whitespace inconsistencies. Normalize names explicitly when building a new pipeline and update the notebook and feature contract together.

## 3. Loading the source

Run Jupyter from the repository root:

```python
import pandas as pd
df = pd.read_csv("admission_predict.csv")
```

## 4. Validation recommendations
Validate required columns, normalized names, numeric types, missing values, rating ranges, research encoding, target values, duplicate rows, and duplicate identifiers. Exclude the serial identifier from the predictor matrix. Do not replace zeros with missing values without checking whether zero is valid or an encoding convention in the source.

## 5. Provenance and privacy
The repository license does not necessarily cover the dataset. Verify its original source, provenance, and redistribution terms before reusing it elsewhere. Avoid adding private applicant records or publishing row-level personal data.

## 6. Future storage
If external storage is later required, define a versioned schema and document why a database is needed. Store dataset metadata, source references, checksums, collection dates, and preprocessing versions separately from model artifacts.
