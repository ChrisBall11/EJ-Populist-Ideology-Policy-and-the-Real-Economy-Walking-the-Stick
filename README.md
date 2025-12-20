# Replication Package

This folder reproduces all tables and figures in the paper.

## Software Requirements

- R (>= 4.2)
- Packages: tidyverse, plm, vars, urca, ggplot2

## Execution Order

1. `01_clean_data.R`
2. `02_construct_variables.R`
3. `03_estimations.R`
4. `04_figures_tables.R`

Running all scripts sequentially will reproduce the results in the paper.

## Data Sources

- Global Macro Database
- IMF IFS
- World Bank WDI

Due to licensing restrictions, raw data are not redistributed.
See `data/raw/README.md` for instructions.
