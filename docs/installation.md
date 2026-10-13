# Installation

## Prerequisites

- Python 3.9 or newer
- PowerShell, Command Prompt, or a compatible shell
- Jupyter Notebook or JupyterLab

## Create an environment

```powershell
py -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
python -m pip install jupyter pandas numpy matplotlib scikit-learn
```

On macOS or Linux, use `python3 -m venv .venv` and `source .venv/bin/activate`.

## Verify the installation

```powershell
python -c "import numpy, pandas, matplotlib, sklearn; print('Dependencies loaded')"
```

If the import check fails, verify that the virtual environment is active and install the missing package into that environment.

## Open the project

Run Jupyter from the repository root so the notebook can resolve `admission_predict.csv`:

```powershell
jupyter notebook Admission_Predict.ipynb
```
