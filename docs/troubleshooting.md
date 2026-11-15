# 🧯 Troubleshooting Guide

## 1. CSV file not found
**Symptom:** `FileNotFoundError: admission_predict.csv`

Jupyter was likely launched from a directory that does not contain the CSV. Open a terminal in the repository root, verify the CSV is present, and launch:

```bash
jupyter notebook Admission_Predict.ipynb
```

## 2. Missing Python packages
**Symptom:** `ModuleNotFoundError`

Activate the virtual environment and install:

```bash
python -m pip install jupyter pandas numpy matplotlib scikit-learn
```

Check that the notebook kernel is using the same interpreter.

## 3. Notebook cells fail after editing
Variables remain in kernel memory. Running cells out of order can leave stale or missing values. Restart the kernel and run all cells from top to bottom.

## 4. Different evaluation scores
Possible causes include Python or library versions, changed dataset content, row ordering, missing-value treatment, random seed, split strategy, estimator parameters, or execution order. Record settings and compare equivalent protocols.

## 5. Feature-name warning
The stored notebook output includes a warning when a model fitted with named DataFrame columns receives a plain list for prediction. Use a DataFrame with matching names and order:

```python
sample = pd.DataFrame(
    [[337, 118, 4, 4.5, 4.5, 9.65, 1]],
    columns=[
        "GRE", "TOEFL", "University Rating",
        "SOP", "LOR", "CGPA", "Research"
    ],
)
prediction = model.predict(sample)
```

## 6. Unexpected prediction values
Regression can extrapolate beyond the target range. Check input units, feature order, data preparation, and model assumptions. Do not silently clip outputs and describe them as calibrated probabilities.

## 7. Grid search is slow
GridSearchCV fits multiple configurations across multiple folds. Reduce the search grid for quick iteration, but do not report a reduced search as the full evaluation.

## 8. Data cleaning changes row counts
Inspect missing values, duplicates, zero handling, and filters. Keep a record of removed or changed rows. A zero may be valid, so do not automatically convert it to missing data without confirming its meaning.

## 9. Matplotlib plots do not display
Use a Jupyter kernel and enable inline plotting:

```python
%matplotlib inline
```

Rerun the plotting cell after confirming the kernel is active.

## 10. When opening an issue
Include the error message, Python version, package versions, failing cell, and reproduction steps. Remove personal information and private data rows from logs and screenshots.
