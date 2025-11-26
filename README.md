# cdc-covid-pipeline-vsichula
Project: CDC COVID-19 deaths weekly analysis — Jupyter notebook + figures
# CDC COVID-19 weekly deaths — analysis pipeline

Jupyter notebook that ingests the CDC/NCHS provisional COVID-19 deaths dataset and produces weekly U.S./state/regional visualizations.

## Quick start

1. **Get the data**  
   Download the CSV from the CDC/NCHS portal (dataset: *Provisional COVID-19 death counts, rates, and percent of total deaths, by jurisdiction of residence*).  
   Save it as: `work/data/cdc.csv`

2. **Run the notebook**  
   Open `notebooks/01_cdc_pipeline.ipynb` in JupyterLab (Python 3.x) and **Run All**.  
   Figures will be saved to `outputs/figures/` (or next to the notebook if the folder isn’t writable).

## Repo layout

.
├─ notebooks/
│  └─ 01_cdc_pipeline.ipynb
├─ work/
│  └─ data/
│     └─ cdc.csv        # user-provided; not tracked
├─ outputs/
│  └─ figures/          # generated plots (PNG/SVG)
├─ README.md
├─ .gitignore
└─ LICENSE

## Requirements
- Python 3.9+
- Packages: `pandas`, `matplotlib`
Install (optional):
```bash
pip install pandas matplotlib

## Validation checks
- Weekly cadence after 2020-01-01
- No negative values; flag unusual backfills/spikes
- Sum of states ≈ national total per week (allow small reporting drift)

## Dataset metadata
| Field       | Value                                                                                 |
|-------------|---------------------------------------------------------------------------------------|
| source      | CDC/NCHS provisional COVID-19 deaths by jurisdiction                                  |
| grain       | Weekly; US, HHS regions, states, selected cities                                      |
| time fields | data_as_of, data_period_start, data_period_end                                        |
| measures    | covid_deaths, total_deaths, pct_covid_of_total (derived)                              |
| caveats     | Provisional with revisions; occasional backfills; schema drift                         |
| license     | Public domain (U.S. Government data); code under MIT (see LICENSE)                    |
| retrieved   | 2025-11-19                                                                            |
                                 

**Housekeeping**
- Add `.gitkeep` files in `work/data/` and `outputs/figures/` so those folders exist in Git.
- In `.gitignore`, ensure you don’t commit raw data:

work/data/*
!work/data/.gitkeep

outputs/*
!outputs/figures/.gitkeep

.ipynb_checkpoints/
