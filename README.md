# Replication Package

This folder reproduces all tables and figures in the paper.

This Read Me file describes all the data, code and folders needed to replicate “Populist Ideology, Policy and the Real Economy: Explaining Economic Growth in Populist Regimes” .  Two aspects of the paper can be replicated, both are done in R. First are the simulations. Second are the empirical results and figures. 

We first explain how to replicate all our results, figures, and tables in the paper.  The first section is organized by SIMULATIONS, DATA and EMPIRICAL ANALYSIS.  Then, we identify each figure and table and what data and code are needed to generate them individually. That section is organized by FIGURE and TABLE. 

## Software Requirements

- R (>= 4.2)
- Packages: tidyverse, plm, vars, urca, ggplot2

## Data Sources

- Global Macro Database
- IMF IFS
- World Bank WDI

Due to licensing restrictions, raw data are not redistributed.
See `data/raw/README.md` for instructions.

# SIMULATIONS 

All simulations are done in R. All code is in the “Simulation” folder. 

## Walking Sicks Analysis.R 

First, open and run “Walking Sicks Analysis.R”.  This code is used to generate all the simulations results for all three of our key cases (“all at once”, “fifty-fifty” and “baseline”) those results can be saved as figures (for example, Figures 3, 4, A2 and A3 in the paper) and must be used to generate simulated data into excel that is then used by other R code to create the comparative figure in the Appendix, Figure A1. 

To generate the data and figures from a case, set the policy parameters in the POLICY OPTIONS section from rows 99-109 in the code then the appropriate lines for the graphs and for the data output which saves the output to an excel sheet. 

## “All at once” case,  

un-comment row 106 (policy), 283 (figure: tech and output), 308 (figure: inflation and output), 338 (whole model results) and 343 (save data to excel) 

comment out row 107 & 108 (policy), 284 & 385 (figure: tech and output), 309 & 310 (figure: inflation and output), 339 & 340 (whole model results) and 344 & 345 (save data to excel) 

## “Fifty Fifty” case,  

un-comment row 107 (policy), 284 (figure: tech and output), 309 (figure: inflation and output), 339 (whole model results) and 344 (save data to excel) 

comment out row 106 & 108 (policy), 283 & 385 (figure: tech and output), 308 & 310 (figure: inflation and output), 338 & 340 (whole model results) and 343 & 345 (save data to excel) 

## “Baseline” case,  

un-comment row 108 (policy), 285 (figure: tech and output), 310 (figure: inflation and output), 340 (whole model results) and 345 (save data to excel) 

comment out row 106 & 107 (policy), 283& 284 (figure: tech and output), 308 & 309 (figure: inflation and output), 338 & 339 (whole model results) and 343 & 344 (save data to excel) 

## Walking Sick Comparison Graphs.R 

Run this code in the folder with the excel output from all three Analysis cases (above). This produces three separate graphs comparing TFP, Growth and Inflation for the three regimes.  The paper only includes Figure A1. Inflation Rates Compared. 

# DATA 

All relevant data and data-preparing code are in the “Data” folder. 

Our study covers 62 countries between the years 1970-2019, and the dataset (mainmodelallworld.xlsx) contains the following variables used in the analysis, grouped by their original source: 

## Populism Indicators 

Variables from Freytag_populistbegin to Freytag_populist_1 are from the Populism dataset of Ball, Freytag, and Kautz (2019). 

Variables from Schularick_populistbegin to Schularick_populist_consensus_1 are from Funke, Schularick, and Trebesch (2023). 

## Macroeconomic Data

Variables with “WB” in the beginning of their names (WB_AnnualRGDPGrowth, WB_BroadMoney, WB_Unemployment, WB_RnDexpenditure) are from the World Bank Open Data, whereas WB_AnnualInfl is from Jongrim Ha and Ohnsorge (2023) under World Bank. 

Variables with “pwt” in the beginning of their names (from pwt_PriceLvlImp to pwt_hc) are from the Penn World Table (Feenstra et al., 2015). 

Variables with “GMD” in the beginning of their names (from GMD_M0 to GMD_USDfx) are from the Global Macro Database (Müller et al., 2025). 

Variable BIS_CBassets is from the Bank for International Settlements. 

Variables from Banking.Crisis to Inflation.Crises are from Reinhart et al. (2016) 

## Institutional and Political Data 

Variable Polity5_polity2 is from the Polity5 Project. 

Institutional variables with “vdem” in the beginning of their names (from vdem_polyarchy to vdem_alternativeinfosources) are from the V-Dem Database. 

Variable kof_economic_globalisation_index is from the KOF Swiss Economic Institute. 

Variable gl_gov_change is from Herre (2023). 

Note: Variables ending in _c (e.g., WB_BroadMoneyGrowth_c) denote own calculations (mostly for growth rates) derived from the respective sources. Populism indicator dummies with the term “begin” denote the consideration of only the enterance year of a populist regime, whereas the populist indicator dummies without this term are the ones we have used in our empirical analysis, and they consider every ruling year of a populist regime as “1”. For further information, please check the Metadata sheet of our database, mainmodelallworld.xlsx. 

We build a binary index of populist regimes by combining the lists from Ball et al. (2019) and Funke et al. (2023). Funke et al. (2023) provides a robust list based on the consensus of other scholars and other lists. Ball et al. (2019) provide a deeper look at Latin American countries specifically (and justify the selections on the “Liste_Populisten_vl.xlsx) and essentially add Guatemala and Nicaragua to the Funke et al. (2023) list.  The final list is printed in the Appendix as Table A2. Populist Leaders Mix of Funke et al. (2023) and Ball et al. (2019). 

## Cleaning the data: WS Data Prep.R and merged_dataset.xlsx 

This dataset, mainmodelallworld.xlsx, is the output of cleaning R code, Database_Merge.R.  The R code takes as input of all of the sources of variables listed above, which are provided in the “Data” folder.  It harmonizes country names across the data sets and outputs the final data set, mainmodelallworld.xlsx, which is then used in all R code for subsequent empirical analysis. 

# EMPIRICAL ANALYSIS 

All codes and necessary merged data are in the “Empirical” folder. 

## Walking Stick Patterns 

This folder contains the necessary data and code to generate Figure 1 

Figure 1. Populist Walking Stick Episodes (Start Date = 100) is generated by Country Graphs Walking Sticks.R code which takes merged_dataset.xlsx  as an input and plots the data in Figure 1 in the paper. 

## FIGURES 

Figure 1. Populist Walking Stick Episodes (Start Date = 100) 

Figure 1. Populist Walking Stick Episodes (Start Date = 100) presents some example walking stick episodes  and is generated by Country Graphs Walking Sticks.R .  The R code takes merged_dataset.xlsx  as an input and pulls and plots the data in Figure 1 in the paper as various examples of walking sticks during populist regimes. 

Figure 2. Output and Technology Time Paths 

Run Walking Sicks Analysis.R set to the “Baseline case” (see above) 

Figure 3. Baseline Case: Inflation and Output 

Run Walking Sicks Analysis.R set to the “Baseline case” (see above) 

Figure 4. Baseline Case: Main Variables  

Run Walking Sicks Analysis.R set to the “Baseline case” (see above) 

Figure 5. IRFs: Non-Populists 

Run Figure-5_Non-Populists_IRF.R (uses mainmodelallworld.xlsx) 

Figure 6. IRFs: All Populists 

Run Figure-6_All-Populists_IRF.R (uses mainmodelallworld.xlsx) 

Figure 7. IRFs: Low-M2 Populists 

Run Figure-5_LowM2-Populists_IRF.R (uses mainmodelallworld.xlsx) 

Figure 8. IRFs: High-M2 Populists 

Run Figure-5_HighM2-Populists_IRF.R (uses mainmodelallworld.xlsx) 

Figure A1. Inflation Rates Compared 

Run Walking Sicks Analysis.R set for each of the three cases (see above). Then run Walking Sick Comparison Graphs.R. 

Figure A2. All At Once: Main Variables 

Run Walking Sicks Analysis.R set to the “all at once” (see above) 

Figure A3. 50-50: Main Variables in the Appendix 

Run Walking Sicks Analysis.R set to the “fifty fifty” (see above) 

# TABLES 

Table 1. GDP, Inflation & TFP dynamics by M2-growth intensity 

Run Table-1_Descriptive_All.R (uses mainmodelallworld.xlsx) 

Table 2. Share of years with positive TFP growth 

Run Table-2_Descriptive_TFP.R (uses mainmodelallworld.xlsx) 

Table 3. TWFE Walking Stick Effects on GDP and TFP Growth 

Run Table-3_TWFE-rGDP.R and Table-3_TWFE-TFP.R (both use mainmodelallworld.xlsx) 

Table 4. ECM coefficients: Populist level and TFP interaction by M2-growth regime 

Run Table-4_FECM-HighM2.R and Table-4_FECM-LowM2.R (uses mainmodelallworld.xlsx) 

Table A1. Policy: Baseline 

Run Walking Sicks Analysis.R set to the “Baseline case” (see above). This data is in the Excel output for this case. 

Table A2. Populist Leaders Mix of Funke et al. (2023) and Ball et al. (2019) 

# Robustness Checks 

On Empirical --> Robustness folder, R-Codes are available to reproduce the following robustness checks: 

Exclusion of populist governments with lower than 3 years in office 

Run TWFE_No-Regimes-Lower-than-3yrs-rGDP.R and TWFE_No-Regimes-Lower-than-3yrs-TFP.R (both use mainmodelallworld.xlsx) 

Different measure of TFP (at constant national prices with 2017 = 1 for each country) from World Bank 

Run the four different PVAR_..._TFP-Different-Measure.R and the TWFE_TFP-Different-Measure.R (each use mainmodelallworld.xlsx) 

Pre-trend checks for rGDP and TFP 

Run TWFE_Pretrend-rGDP.R and TWFE_Pretrend-TFP.R (both use mainmodelallworld.xlsx) 

Driscoll-Kraay Standard Errors 

Run TWFE_Driscoll-Kraay-SEs-rGDP.R and TWFE_Driscoll-Kraay-SEs-TFP.R (both use mainmodelallworld.xlsx) 
