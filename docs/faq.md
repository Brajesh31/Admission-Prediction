# ❓ Frequently Asked Questions

## Is this a production admissions system?
No. It is an educational regression notebook. It must not be used as the sole basis for admissions, funding, or scholarship decisions.

## Does this repository contain a web app or API?
No. The primary executable artifact is `Admission_Predict.ipynb`. No HTTP API or hosted service is included.

## Does the project use a database?
No. The notebook reads `admission_predict.csv` directly.

## Which features are used?
GRE, TOEFL, University Rating, SOP, LOR, CGPA, and Research, in that order.

## What does the output mean?
The fitted regressor returns a numeric estimate for the dataset target. It is not automatically a calibrated probability or a guarantee of acceptance.

## Why use R² instead of accuracy?
This is a regression task. R² measures explained variance relative to a baseline. It is not classification accuracy and should not be described as an admission success rate.

## Which dependencies are required?
Python, Jupyter, pandas, NumPy, matplotlib, and scikit-learn. See [installation.md](installation.md).

## Why can results differ?
Python and library versions, random seeds, notebook execution order, data split, and preprocessing all affect results.

## Why does the CSV fail to load?
Start Jupyter from the repository root and verify that the CSV sits beside the notebook.

## Can I use the model for a specific university?
The included data does not establish an official university-specific model. The UCLA sample print statement is an illustrative label, not evidence of endorsement or validation.

## Can I redistribute the dataset?
Do not assume the MIT license covers the CSV. Verify its original source and redistribution terms first.

## How can I contribute?
Read [CONTRIBUTING.md](../CONTRIBUTING.md), make a focused change, run the notebook from a clean kernel, and document changes to model evaluation or data preparation.
