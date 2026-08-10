# CDC COVID-19 Weekly Mortality Analysis Pipeline

A reproducible data-analysis pipeline for ingesting, validating, analyzing, and visualizing
CDC/NCHS provisional COVID-19 mortality data across the United States.

The project demonstrates practical skills in **Python, data cleaning, quantitative analysis,
data validation, reproducible research, visualization, and scalable data-processing workflows**.

## Project Overview

Public-health datasets are often large, evolving, and subject to revisions. This project
develops a reproducible workflow for analyzing the CDC/NCHS *Provisional COVID-19 Death
Counts by Jurisdiction of Residence* dataset.

The pipeline:

- ingests and cleans CDC mortality data;
- normalizes changing column names and data types;
- validates weekly reporting cadence and numerical consistency;
- analyzes national, state, and HHS regional mortality patterns;
- calculates rolling averages and cumulative trends;
- produces reproducible visualizations for communicating analytical findings; and
- documents data provenance, assumptions, and limitations.

The workflow was developed in JupyterLab on a Jetstream2 virtual machine using Python,
pandas, matplotlib, and a PySpark-ready architecture.

## Research Questions

The analysis addresses three primary questions:

1. How did weekly U.S. COVID-19 deaths change over time?
2. How did mortality patterns differ among states and HHS regions?
3. How did COVID-19's share of total U.S. deaths change across pandemic waves?

## Key Findings

The analysis identified several important temporal and geographic patterns:

- U.S. mortality data show distinct pandemic waves, including the major winter 2020–21
  surge and subsequent Delta and Omicron waves.
- Weekly mortality declined substantially after 2022, although smaller seasonal increases
  remained visible.
- Large states such as California, Texas, and Florida accounted for substantial absolute
  mortality counts, while the timing and magnitude of peaks differed geographically.
- HHS regional analysis showed that the geographic contribution to national mortality
  changed across pandemic waves.
- COVID-19 represented a much larger share of total deaths during 2020–21 than during
  later years.
- Four-week moving averages helped distinguish underlying mortality trends from weekly
  reporting variability and backfills.

## Data Pipeline

The project follows a reproducible analytical workflow:

CDC/NCHS CSV
    ↓
Data ingestion
    ↓
Schema and type normalization
    ↓
Data-quality validation
    ↓
Transformation and aggregation
    ↓
Quantitative analysis
    ↓
Visualization
    ↓
Reproducible outputs

### Data Processing

The pipeline performs:

- column-name normalization;
- date parsing;
- numeric type conversion;
- duplicate handling;
- jurisdiction filtering;
- weekly aggregation;
- rolling-average calculations;
- state and regional comparisons; and
- cumulative trend analysis.

## Data Validation

Because the CDC dataset is provisional and may contain revisions and reporting backfills,
the workflow includes several validation checks:

- Verify weekly reporting cadence after January 2020.
- Check for negative or invalid mortality counts.
- Compare aggregated state totals with national totals.
- Identify unusual spikes potentially associated with reporting backfills.
- Validate date and numerical data types.
- Account for minor CDC schema changes.

These checks improve the reliability and reproducibility of downstream analysis.

## Analytical Outputs

The notebook generates several types of analyses and visualizations:

- U.S. weekly COVID-19 deaths;
- 4-week moving-average mortality trends;
- state-level mortality comparisons;
- top-state time-series overlays;
- HHS regional mortality comparisons;
- state-by-week mortality heatmaps;
- COVID-19 deaths as a percentage of total deaths; and
- cumulative mortality trajectories.

## Technology Stack

- Python 3
- pandas
- matplotlib
- JupyterLab
- PySpark 4.0.1 / Spark-ready processing
- Jetstream2 virtual computing environment
- Git / GitHub

The dataset used in this project is relatively small enough to process efficiently with
pandas. The workflow was designed so that aggregation and transformation stages can be
migrated to PySpark as dataset size or data-source complexity increases.

## Repository Structure

```text
cdc-covid-pipeline-vsichula/
│
├── README.md
├── notebooks/
│   └── big_data_project_VSICHULA.ipynb
│
├── work/
│   └── data/
│       └── cdc.csv        # User-provided; not tracked
│
├── outputs/
│   └── figures/           # Generated visualizations
│
├── .gitignore
└── LICENSE
