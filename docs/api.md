# 🔌 Prediction Interface

## Current status
The repository does **not** expose an HTTP API, REST endpoint, hosted inference service, or installed Python package interface. The practical prediction interface is the fitted scikit-learn estimator inside `Admission_Predict.ipynb`.

## Feature contract

| Position | Feature | Meaning |
|---:|---|---|
| 1 | GRE | GRE score |
| 2 | TOEFL | TOEFL score |
| 3 | University Rating | University rating value in the dataset |
| 4 | SOP | Statement of purpose rating |
| 5 | LOR | Letter of recommendation rating |
| 6 | CGPA | Academic grade-point average |
| 7 | Research | Research experience indicator |

Use the same feature definitions, units, and expected ranges as the training data.

## Notebook example

```python
model.predict([[337, 118, 4, 4.5, 4.5, 9.65, 1]])
```

A named-column approach is clearer:

```python
import pandas as pd

feature_columns = [
    "GRE", "TOEFL", "University Rating",
    "SOP", "LOR", "CGPA", "Research",
]

sample = pd.DataFrame(
    [[337, 118, 4, 4.5, 4.5, 9.65, 1]],
    columns=feature_columns,
)

estimate = model.predict(sample)[0]
print(estimate)
```

The estimator must be fitted before this code runs.

## Output interpretation
The return value is a regression estimate for the target represented in the training data. It is not automatically a calibrated probability, a guarantee of acceptance, or an official university assessment. Do not silently clip outputs to [0, 1] and then present them as reliable probabilities.

## Requirements for a future API
Any future API should validate all seven values, define a versioned schema, check units and ranges, return model version and limitations, avoid logging raw applicant data, apply rate limits and access controls, include inference tests, and never automate high-impact admission decisions.
