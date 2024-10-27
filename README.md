# NACE2COICOP_Translation

This repository provides code to transform a **household expenditures matrix** classified by **19 NACE sectors across 6 macro-regions** (NW, NE, Toscana, Centro, Sud, and Ext) into a **consumption composition matrix** classified by **45 COICOP categories across the same regions**. The transformation process includes data loading, matrix operations, normalization, and adjustments to ensure the final output aligns with predefined target sums for each macro-region.

## Table of Contents
- [Project Overview](#project-overview)
- [Input Files](#input-files)
- [Outputs](#outputs)
- [Installation and Setup](#installation-and-setup)
- [Running the Code](#running-the-code)
- [License](#license)

## Project Overview

The code takes a matrix of household expenditures across NACE economic sectors and allocates these expenditures to COICOP consumption categories, using a concordance matrix for proportional distribution across categories and regions. It outputs a final matrix representing COICOP expenditures across each macro-region.

### Key Steps in the Code

1. **Normalize Concordance Matrix**:  
   The **concordance matrix** (19x45) maps each NACE sector to COICOP categories. Each row is normalized to sum to 1, ensuring full distribution of each NACE sector's expenditures across COICOP categories.

2. **Transform NACE to COICOP**:  
   The **NACE expenditures matrix** (19x6) is multiplied by the normalized **concordance matrix** (45x19) to produce a **45x6 COICOP expenditures matrix**.

3. **Adjust to Target Regional Sums**:  
   For each region, scaling factors are applied to ensure that total COICOP expenditures match target sums, aligning outputs with expected expenditures for each macro-region.

4. **Verification and Export**:  
   The final adjusted COICOP expenditures matrix is verified and exported for analysis or modeling.

## Input Files

1. **Concordance Matrix** (`concordance_matrix.xlsx`):  
   A 19x45 matrix that maps NACE sectors to COICOP categories. The matrix must be clean, with no extra rows or columns.

2. **NACE Expenditures Matrix** (`household_expenditures_NACE_19.xlsx`):  
   A 19x6 matrix of household expenditures by NACE sector and macro-region.

3. **Target Regional Sums**:  
   These are predefined totals for each macro-region:
   - NW: 288344.34
   - NE: 206885.173
   - Toscana: 65495.455
   - Centro: 133510.837
   - Sud: 263920.045
   - Ext: 1433.059

## Outputs

1. **Adjusted COICOP Expenditures Matrix (45x6)**:  
   A matrix with 45 COICOP categories and 6 macro-regions, representing adjusted expenditures by COICOP category in each region.

2. **Adjusted Regional Totals**:  
   A single-row summary of adjusted total expenditures per region, verifying alignment with the target values.

## Installation and Setup

1. Clone this repository to your local machine:
   ```bash
   git clone https://github.com/username/NACE2COICOP_Translation.git
   cd NACE2COICOP_Translation
   
2. Install the required R packages:
   
   install.packages(c("readxl", "dplyr", "writexl"))
   
3. Place your input files (concordance_matrix.xlsx and household_expenditures_NACE_19.xlsx) in the project directory or specify paths as prompted by the code.
   
## Running the Code

1.Open the R script in your R environment (RStudio or another IDE).

2.Follow the prompts to load the concordance matrix and NACE expenditures matrix.

3.Run the script to produce the adjusted COICOP expenditures matrix and adjusted regional totals.

4.The outputs are saved to adjusted_coicop_expenditures_by_region.xlsx:

-Adjusted_COICOP_Sums: A data frame showing adjusted total expenditures per region.
-COICOP_Expenditures: The 45x6 matrix of COICOP expenditures by category and region.

## License

This project is licensed under the GNU General Public License v3.0.
