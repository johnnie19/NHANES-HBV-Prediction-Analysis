# NHANES HBV Analysis

## Overview

This project analyzes NHANES (National Health and Nutrition Examination Survey) data to predict Hepatitis B Virus (HBV) status using various machine learning models. The analysis focuses on identifying key demographic, socioeconomic, and health-related predictors of HBV positivity.

## Team
Data_Divers

## Key Features

- Comprehensive data preprocessing including standardization and variable transformation
- Multiple machine learning models (Logistic Regression, Random Forest, Gradient Boosting)
- Cross-validation with different resampling techniques
- Feature importance analysis
- Model performance evaluation using multiple metrics (AUC, Accuracy, Sensitivity, Specificity)

## Dataset Information

- **Source**: NHANES dataset
- **Records**: 1,506 individuals
- **Variables**: 16 features including demographics, health insurance status, education level, and health indicators
- **Target Variable**: LBDHBG (Hepatitis B core antibody test result)

## Project Structure

```
NHANES-HBV-Prediction-Analysis/
│
├── README.md                    # Project documentation
│
├── code/                        # Analysis code
│   └── nhanes_final_analysis.Rmd # Main analysis R Markdown file
│
├── data/                        # Data files
│   ├── Nhanes1318.csv           # Raw NHANES dataset
│   └── NhanesFinal2.csv         # Cleaned NHANES dataset
│
└── docs/                        # Documentation
    └── Predictive Model for Chronic Hepatitis B Infection DataDivers.pptx  # Presentation
```

**Note**: The following files mentioned in this README are not currently in the repository:
- `Variables_info.csv`: Metadata describing variables used in the analysis
- `final_resultfinalsun.csv`: Model performance results for all configurations

## Installation

### Required R Packages
```r
install.packages(c("tidyverse", "gbm", "ranger", "caret", "gridExtra", 
                   "DT", "Metrics", "ROCR"))
```

### Load Libraries
```r
library(tidyverse)
library(gbm)
library(ranger)
library(caret)
library(gridExtra)
library(DT)
library(Metrics)
library(ROCR)
```

## Methodology

### 1. Data Preprocessing
- Conversion of categorical variables to factors
- Standardization using centering and scaling
- Removal of near-zero variance predictors
- Train-test split (70-30) with stratified sampling

### 2. Machine Learning Models
Three models were evaluated:
- **Logistic Regression (glm)**
- **Random Forest (ranger)**
- **Gradient Boosting Machine (gbm)**

### 3. Model Validation
Each model was tested with:
- Cross-validation folds: 5 and 10
- Resampling methods: none, up, down, SMOTE, and ROSE
- Total combinations: 30 (3 models × 2 CV folds × 5 resampling methods)

### 4. Performance Metrics
Models were evaluated using:
- AUC (Area Under the Curve)
- Accuracy
- Sensitivity
- Specificity

## Key Findings

### Top Predictors for HBV Status
1. Non-Hispanic Asian ethnicity
2. Weight (pounds)
3. Country of birth (Other)
4. Non-Hispanic Black ethnicity
5. Gender (Female)
6. Insurance status (Not covered)
7. Household size
8. Ever told have HBV
9. Non-Hispanic White ethnicity
10. Education level (College)

## Usage

### Running the Analysis
1. Clone the repository
2. Ensure all required R packages are installed
3. Place any additional dataset files in the `data/` directory
4. Open `code/nhanes_final_analysis.Rmd` in RStudio
5. Knit the document to generate the full analysis report

### Viewing Results
```r
# Load the results (if you have the file)
results <- read.csv("data/final_resultfinalsun.csv")

# View the sortable results table
library(DT)
datatable(results)
```

## Results Summary

The analysis produces a comprehensive table comparing all model configurations, allowing for easy identification of the best-performing model based on various metrics. The feature importance plot helps identify which demographic and health factors are most predictive of HBV status.

## Files Description

- `code/nhanes_final_analysis.Rmd`: Main R Markdown file containing the complete analysis workflow
- `data/Nhanes1318.csv`: Raw NHANES dataset
- `data/NhanesFinal2.csv`: Cleaned and processed NHANES dataset
- `docs/Predictive Model for Chronic Hepatitis B Infection DataDivers.pptx`: Presentation slides

**Missing files (mentioned in documentation but not in repository):**
- `data/Variables_info.csv`: Metadata describing variables used in the analysis
- `data/final_resultfinalsun.csv`: Model performance results for all configurations

## License

This project is intended for educational and research purposes. Please ensure proper citation of the NHANES dataset if using this analysis.

## Contributing

Contributions to improve the analysis are welcome. Please submit pull requests with clear descriptions of the changes made.

## Contact

For questions or collaboration opportunities, please contact the Data_Divers team.

---

**Note**: This analysis is based on NHANES data and is intended for research purposes only. Medical decisions should not be made based solely on these predictive models.
