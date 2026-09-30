# Data-driven Identification of a Nonlinear Resonator

Jupyter notebooks for processing experimental data and discovering governing equations for a nonlinear resonator using least-squares fitting, sparse regression (PySINDy), and symbolic regression (PySR).

## Setup

From the project root, run in PowerShell:

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install -r requirements.txt
jupyter lab
```

Use the virtual environment as the notebook kernel. PySR sets up its Julia
environment on first use, which requires internet access and may take a few minutes.

## Run the analysis

Open `notebooks/pipeline/` and run all cells in each notebook in this order:

1. `1_data_reading_EDA.ipynb`: load the raw MAT files and explore the data.
2. `2_data_processing_and_integration.ipynb`: filter and integrate the signals.
3. `3_least_squares_velocity_model.ipynb`: fit the baseline least-squares model.
4. `3_least_squares_velocity_model_selection.ipynb`: select model terms.
5. `4_pysindy.ipynb`: fit sparse models with STLSQ, FROLS and SSR.
6. `4_pysr.ipynb`: run symbolic regression using the library selected by PySINDy.
7. `6_pysindy_pysr_comparison.ipynb`: compare the saved models.

Later notebooks load results saved by earlier steps. Rerun the following steps after changing upstream data or settings.

## Files

- `data/raw/`: experimental MAT files (frequency responses and time series).
- `notebooks/pipeline/`: main analysis workflow.
- `notebooks/studies/`: additional PySINDy examples.
- `results/`: generated data, fitted models and comparison results.
- `figures/`: generated PDF figures.
- `references/`: supporting literature.
