# Troubleshooting

## `FileNotFoundError` for the CSV

Start Jupyter from the repository root and confirm that `admission_predict.csv` is beside `Admission_Predict.ipynb`. The notebook uses a relative path.

## Import errors

Activate the virtual environment and install the documented dependencies:

```powershell
python -m pip install jupyter pandas numpy matplotlib scikit-learn
```

## Notebook cells behave inconsistently

Restart the kernel and run all cells from top to bottom. Notebook state can hide missing imports or stale variables.

## Different model scores

Check Python and package versions, the random seed, the train/test split, and any changes to data cleaning. Small environment or preprocessing differences can change results.

## Warnings about feature names

Pass a DataFrame with the same column names used during training, or verify that a positional list follows the documented feature order. Do not ignore a warning until its cause is understood.

## Unexpected prediction values

Confirm that inputs use the dataset's units and ranges. A regression estimate outside an expected probability range should be investigated rather than silently clipped.
