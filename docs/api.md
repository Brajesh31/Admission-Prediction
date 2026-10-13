# API and prediction interface

The current project has no HTTP or Python package API. Its practical interface is the notebook cell that calls the fitted scikit-learn model.

## Feature contract

Predictions use a seven-value row in this order:

| Position | Feature |
| --- | --- |
| 1 | GRE score |
| 2 | TOEFL score |
| 3 | University rating |
| 4 | Statement of purpose rating |
| 5 | Letter of recommendation rating |
| 6 | CGPA |
| 7 | Research experience |

The values must use the same units and ranges as the training dataset.

## Example

```python
model.predict([[337, 118, 4, 4.5, 4.5, 9.65, 1]])
```

The returned value is a regression estimate. It must not be presented as a guaranteed admission outcome or an automatically authoritative decision.

## Future API requirements

Any future service should validate types and ranges, reject missing or unexpected fields, version the feature contract, avoid logging raw applicant data, and document model version and uncertainty with every response.
