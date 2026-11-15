# 🛠️ Installation Guide

## 1. Prerequisites
Install Python 3.9 or newer, pip, Git, and a terminal. Jupyter will be installed with project dependencies. The notebook metadata currently records Python 3.11.7. The repository does not include a fully pinned dependency lockfile, so use a virtual environment and record package versions for reproducible work.

```bash
python --version
python -m pip --version
git --version
```

## 2. Clone

```bash
git clone https://github.com/Brajesh31/Admission-Prediction.git
cd Admission-Prediction
```

## 3. Create a virtual environment

### Windows PowerShell

```powershell
py -m venv .venv
.\.venv\Scripts\Activate.ps1
```

If activation is restricted, use the environment's interpreter directly or a shell configured for your machine. Avoid changing system-wide execution policy unnecessarily.

### macOS / Linux

```bash
python3 -m venv .venv
source .venv/bin/activate
```

## 4. Install dependencies

```bash
python -m pip install --upgrade pip
python -m pip install jupyter pandas numpy matplotlib scikit-learn
```

## 5. Verify imports

```bash
python -c "import numpy, pandas, matplotlib, sklearn; print('All required packages imported')"
```

Confirm the notebook kernel uses the same interpreter where packages were installed.

## 6. Launch the notebook

Run from the repository root:

```bash
jupyter notebook Admission_Predict.ipynb
```

Alternatively:

```bash
jupyter lab Admission_Predict.ipynb
```

## 7. Verify the data file
Confirm both `Admission_Predict.ipynb` and `admission_predict.csv` are in the repository root. The notebook uses a relative path, so launching Jupyter elsewhere can cause a file-not-found error.

## 8. Record environment versions

```bash
python --version
python -m pip freeze > requirements-lock.txt
```

Review and test a generated lock file before committing it.

## 9. Shutdown
Save the notebook, stop the Jupyter server from the terminal, and leave the virtual environment with `deactivate`.
