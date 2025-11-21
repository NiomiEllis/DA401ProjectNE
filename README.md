# DA401ProjectNE

1. Early Results – DA401 Project

This repository contains an R Markdown analysis titled EarlyResults.Rmd, which performs a Geographically Weighted Regression (GWR) using county-level socioeconomic and VIIRS light pollution data for five U.S. states (PA, OH, NY, NJ, and MD).

Current Repository Structure
DA401Project/
│--- Experiments
├── EarlyResults.Rmd                     # Main analysis script
├── Data/                          # Folder containing input and output data
│   ├── VIIRS_Region_Only.tif            # Input raster file (light pollution)
│   ├── ACS_County_Data_5states.geojson  # Generated ACS data
│   ├── GWR_Coefficients_Counties.geojson # GWR model output
│   └── GWR_marginalized_coef_raster.tif  # Rasterized GWR coefficients
└── README.md

Setup Instructions:

1. Clone or download this repository to your local computer.
   
3. Download data files and place in Data folder:
   cencus: https://drive.google.com/file/d/1kVebOf6qlQfIuwKRcIbx-KLxvfjqLbhX/view?usp=sharing
   VIIRS: https://drive.google.com/file/d/1OAY3L85oeqqDVBbesq-SDesLYmmoMzrn/view?usp=sharing

5. Open RStudio and set your working directory to the project folder:

6. setwd("path/to/DA401Project")


Next, open the EarlyResults.Rmd file.

The script will automatically install and load the required R packages if they are not already installed:

pkgs <- c("terra", "sf", "sp", "dplyr", "tidycensus", "exactextractr",
          "GWmodel", "tmap", "RColorBrewer", "classInt", "ggplot2",
          "viridis", "ggthemes", "tigris", "spdep", "spgwr")


Make sure the DA401 Data folder is located in the same directory as EarlyResults.Rmd.

The script expects the file DA401 Data/VIIRS_Region_Only.tif to exist. This file is currently too large to push to the repository, can be found in .gitignore

Add your own Census API key in the code chunk that uses:

census_api_key("your_api_key_here", install = FALSE)

Run all code chunks in order, or knit the file to HTML to reproduce the full analysis and visualizations.


Script Overview:
Loads VIIRS night light raster data and ACS county-level demographic data for PA, OH, MD, NJ, and NY.

Constructs a marginalization index using poverty, race, income, and education indicators.

Runs a Geographically Weighted Regression (GWR) to explore spatial variation in relationships between marginalization and light pollution.

Exports processed data and regression outputs for further visualization.

Creates choropleth maps for GWR coefficients and local R² values.

Outputs:
All output files are saved in the DA401 Data folder, including:

GWR_Coefficients_Counties.geojson – County-level GWR coefficients

GWR_marginalized_coef_raster.tif – Rasterized marginalized coefficient surface

ACS_County_Data_5states.geojson – Cleaned ACS data

Notes:

Developed and tested using R version 4.4.0 and RStudio.

Requires a valid U.S. Census API key for data retrieval via tidycensus.

Ensure the VIIRS raster file is properly cropped and aligned with the study area.
