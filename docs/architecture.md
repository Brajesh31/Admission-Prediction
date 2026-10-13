# Architecture

## Overview

Admission-Prediction is a notebook-centered data-science project. It has no web server, database, background worker, or deployed runtime. The notebook is the executable workflow and the CSV is its local data source.

## Components

```text
admission_predict.csv
        |
        v
Admission_Predict.ipynb
  |-- pandas / NumPy data preparation
  |-- matplotlib exploration
  |-- scikit-learn model comparison
  `-- evaluation and sample prediction
```

## Data flow

1. The notebook reads `admission_predict.csv` using a relative path.
2. Applicant features are selected and separated from the admission-chance target.
3. Candidate regression models are evaluated with cross-validation and a train/test split.
4. A final model produces an estimate for a sample feature vector.

## Boundaries

The repository intentionally keeps data loading, analysis, training, and demonstration in one notebook. Future packaging should preserve the same feature order and target semantics while moving reusable logic into tested Python modules.

## Risks and constraints

- Notebook execution depends on the local Python environment.
- The CSV provenance and license must be verified before redistribution.
- Regression estimates should not be treated as institutional admissions decisions.
- Data leakage must be avoided when adding transformations or derived features.
