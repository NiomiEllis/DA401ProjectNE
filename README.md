# DA401ProjectNE
# DA401 Project — Light Pollution & Social Marginalization in the Northeastern U.S.

This repository contains the full workflow, code, and outputs for my senior data analytics project:
analyzing how social marginalization relates to light pollution across counties in the Northeastern United States using spatial statistics, GWR (Geographically Weighted Regression), and county-level ACS + VIIRS satellite data.

The project is entirely reproducible, and this README explains:

- the folder structure

- how to access and run main.Rmd

- required installations

- what the code produces (figures, model results, data outputs)

- Project Overview

The main analysis uses:

- Nighttime radiance (VIIRS) data

- County-level ACS indicators, including marginalization index, poverty rate, and percent non-white

- Geographically Weighted Regression (GWR) to detect spatially varying relationships

- OLS and VIF checks for comparison

- Local t-values, coefficient maps, and residual spatial autocorrelation (Moran’s I)

The workflow is designed to show whether environmental inequality patterns (specifically exposure to artificial light) differ across space and which areas show strong marginalization-based effects.

## Folder Structure

Your repository should look like this:

DA401Project/
│
└── DA401ProjectNE/
    │   main.Rmd
    │
    ├── Data/
    │     ├── raw input files (VIIRS, ACS data, GeoJSONs)
    │     ├── any derived spatial datasets created during the workflow
    │     └── *.geojson / *.xlsx outputs saved during analysis
    │
    ├── Experiments/
    │     └── (empty for now) 
    │
    ├── Figures/
    │     ├── all exported PNG visuals
    │     ├── small multiple panels
    │     └── coefficient/t-value maps
    │
    ├── Results/
    │     ├── model outputs (CSV, Excel)
    │     ├── saved GWR coefficient tables
    │     └── local statistics results
    │
    └── Utilities/
          └── EarlyResults.Rmd
Setup Instructions:

1. Clone or download this repository to your local computer.
   
3. Download data files and place in Data folder:
   cencus: https://drive.google.com/file/d/1kVebOf6qlQfIuwKRcIbx-KLxvfjqLbhX/view?usp=sharing
   VIIRS: https://drive.google.com/file/d/1OAY3L85oeqqDVBbesq-SDesLYmmoMzrn/view?usp=sharing
   OR (preferrably)
   Use preprocessed data in Data folder

4. Open RStudio and set your working directory to the project folder:

5. setwd("path/to/DA401Project")


Next, open the Main.Rmd file.

How to Run the Project
1. Install Required R Packages

Before running the R Markdown file, install these packages:

install.packages(c(
  "sf", "dplyr", "ggplot2", "viridis", "tmap", "spdep",
  "readr", "exactextractr", "terra", "GWmodel", "tidyr"
))



2. Open the Analysis File

Navigate to:

DA401Project/DA401ProjectNE/main.Rmd


Open in RStudio.

This file is the master script that:

- loads raw datasets

- preprocesses VIIRS + ACS data

- merges county geometry

- computes marginalization index

- runs OLS, VIF checks, and GWR

- creates all maps and side-by-side comparison panels

- writes output datasets to /Data and /Results

- writes plots to /Figures

- saves coefficient surfaces (GeoJSON) for reuse

  

## Reproducibility Notes

To fully reproduce the analysis:

- Keep the folder structure exactly as shown.

- Place raw datasets inside /Data before running.

- Open RStudio projects from the DA401ProjectNE root folder.

- Knit main.Rmd to HTML to generate all outputs.

  
## General Notes:
- Developed and tested using R version 4.4.0 and RStudio.

- Requires a valid U.S. Census API key for data retrieval via tidycensus.

- Ensure the VIIRS raster file is properly cropped and aligned with the study area.
