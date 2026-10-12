# ESE 5971 — Milestone 2

## Early Warning and Decision Support for Animal Shelter Overcrowding

### Project Overview

This project explores how historical animal shelter data can support decisions about near-term overcrowding risk. The goal is to help shelter managers anticipate potential capacity pressure and plan interventions earlier.

For Milestone 2, the analysis focuses on data quality, the data-generating process, seasonality, temporal dependence, and preliminary baseline evaluation.

Because reliable historical daily occupancy and capacity measurements are not yet available, the current prediction target is **cumulative net animal flow over the next seven days**, rather than directly observed overcrowding.

## Data Sources

The analysis uses publicly available records from Austin Animal Center:

- [Austin Animal Center Intakes](https://data.austintexas.gov/d/wter-evkm)
- [Austin Animal Center Outcomes](https://data.austintexas.gov/d/9t4d-g238)

The datasets used in this analysis contain 173,812 intake records and 173,775 outcome records, covering approximately October 2013 through May 2025.

The raw CSV files are not included in this repository. To run the analysis, download the datasets and save them locally as:

- `data/raw/intakes.csv`
- `data/raw/outcomes.csv`

The public datasets may change over time, so newly downloaded versions may not reproduce the exact numerical results reported here.

## Repository Structure

- `notebooks/milestone2_analysis.ipynb` — Data cleaning, exploratory analysis, statistical diagnostics, and baseline evaluation.
- `report/` — Milestone 2 Technical Dossier in PDF and LaTeX formats.
- `figures/` — Figures used in the report.
- `data/raw/` — Location for the original CSV files.
- `requirements.txt` — Python dependencies.

## Reproducing the Analysis

1. Download the two datasets and place them in `data/raw/` using the filenames above.
2. Install the required Python packages using `python -m pip install -r requirements.txt`.
3. Open `notebooks/milestone2_analysis.ipynb` in VS Code or Jupyter.
4. Restart the kernel and run all cells in order.

The notebook includes data quality checks, event matching diagnostics, daily data aggregation, seasonal analysis, autocorrelation analysis, and preliminary baseline evaluation.

## Preliminary Results

The analysis identifies seasonal patterns and temporal dependence in recorded daily animal intake activity.

Two simple baselines were evaluated using chronological validation data from 2024:

| Baseline | MAE | RMSE |
|---|---:|---:|
| Zero Net Flow | 34.774 | 46.698 |
| Recent 7-Day Flow | 33.000 | 42.694 |

The Recent 7-Day Flow baseline performs slightly better, suggesting that recent shelter activity contains some useful predictive information.

## Limitations

The current analysis does not directly measure daily on-site occupancy or historical shelter capacity. As a result, net-flow predictions should not be interpreted as confirmed overcrowding predictions.

Other limitations include inconsistent timestamp formats, uncertainty in matching animal intake and outcome events, and possible changes in shelter operations over time.

Future work will focus on improving the connection between predicted shelter activity and actual management decisions.

## AI Use

AI assistance was used for coding support, document organization, and language revision. 