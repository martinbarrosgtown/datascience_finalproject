# Final-Data-Science-Project

Intro to Data Science Final Group Project. Composed of team members: Martin Barros, Gabriella Cova, Eva Langbehn, and Miguel Villa December 2025

This repository includes relevant content for our final group project, titled: A Machine Learning Approach to Predicting Global Remittances.

This project analyzes the determinants of international remittances as a percentage of GDP across 150+ countries over the period 1994-2024. Using machine learning techniques, we construct a prediction model for remittance flows based on economic, demographic, and policy factors.

## Project File Directory


-   [Motivating the Problem](https://martinbarrosgtown.github.io/datascience_finalproject.github.io/analysis/motivation.html)

-   [Proposing the Solution](https://martinbarrosgtown.github.io/datascience_finalproject.github.io/analysis/proposal.html)

-   [Data Set Construction](https://martinbarrosgtown.github.io/datascience_finalproject.github.io/data/dataset_construction.html)

-   [Data Visualization and Initial Model Set Up](https://martinbarrosgtown.github.io/datascience_finalproject.github.io/analysis/dataviz.html)

-   [Model Construction/ Implementation/ Evaluation](https://martinbarrosgtown.github.io/datascience_finalproject.github.io/analysis/model.html)


## Research Question

What factors best predict remittances as a share of GDP, and how do these relationships vary across different modeling approaches?

## Relevant Repository Contents

-   consolidated.qmd - Main project Quarto file with detailed overview of process and justification
    -   **Found in Results Folder**
-   consolidated.html - Rendered output of the Quarto
    -   **Found in Results Folder**
-   remittances.csv - Main dataset that we built
    -   **Found in Data Folder**

## Libraries Used for this project

-   tidyverse
-   tidymodels
-   ggplot2
-   janitor
-   naniar
-   assertr
-   corrplot
-   gridExtra
-   glmnet
-   dplyr
-   vip
-   reshape2
-   ...

## Data

Data was pulled from various sources to build this dataset: *include names/links of sources*

Countries covered: 158 Time period: 1994-2024 (30 years) Number of observations: 3,918 (in training dataset)

Key outcome: Remittances as a % of GDP Predictors used: Migrant stock, GDP per capita, unemployment, deportations, internet accss, inflation, terrorism index, distance between capital cities, poverty rate

There are some issues with missing data, especially for Poverty and Migrant stock. We corrected for this via imputation of the median for numeric variables.

## Methods and Process

## Step 1: Data Overview Preparation

-   Loaded remittances data
-   Removed missing observations
-   Split data 80-20

## Step 2: Exploratory Data Analysis

-   Examined distribution of variables
-   Identified skewed variables (remittances, GDP)
-   Applied log transformations to normalize distributions
-   Analyzed correlations between predctors

## Step 3: Feature Engineering

-   Created lagged variables
-   Log-transformed GDP per capita
-   Normalized numeric predictors

## Step 4: Missing Data

-   Imputed missing values using median for numeric predictors

## Step 5: Cross-validation Setup

-   Created 10-fold cross-validation with 5 repetitions, ensuring no data leakage

## Step 6: Model Training & Tuning

-   Looked at 5 models:
    -   Linear regression (no tuning)
    -   Ridge: turned penalty parameter via grid search (30 levels)
    -   LASSO: tuned penalty parameter via grid search (30 levels)
    -   Random Forest: 20 combinations
    -   KNN: turned number of neighbors from 1-99

## Step 7: Model Evaluation and Selection

-   Calculated RMSE for each model in order to select the best one
-   Fit final model on full training data

## Step 8: Final Model

-   Fit final model on testing data

## Key Findings

1.  The Random Forest model achieved the lowest prediction error (RMSE = 2.53) and explains 86% of variation in remittances
2.  X, Y, and Z were the strongest predictors
3.  Remittances represent a larger share of GDP in lower-income countries, displaying a negative correlation with GDP per capita
4.  Utilizing lagged effects for GDP and deportations improves model performance, suggesting there is a delayed impact of these variables on remittance flows


## How to Reproduce This Analysis

1.  Clone this repository to RStudio
2.  Ensure data file (remittances.csv) is in the project directory
3.  Open consolidated.qmd
4.  Render to generate HTML output

## Notes

-   ⁠Seed set to 20251211 for reproducibility
-   ⁠Repository URL submitted via Canvas
-   Private repository
