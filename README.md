
#  Project: Real Estate Price Prediction

## Overview
This project focuses on predicting real estate prices using a combination of traditional machine learning models and deep learning approaches. 
The dataset was scrapped by the author (1.0-scrapping-real-estate.ipynb), cleaned, and enriched.
By leveraging Random Forest (RF), XGBoost (XGB), and Neural Networks (NNs), the goal was to find the most effective predictive model.

Several ensemble learning techniques were explored, including weighted averaging, stacking with meta-learners, and feature engineering with model outputs.

## Table of Contents
- [Dataset](#dataset)
- [Data Preprocessing](#Data-Preprocessing)
- [Models Evaluated](#Models-Evaluated)
- [Best Performing Model](#Best-Performing-Model)
- [Key Takeaways](#Key-Takeaways)
- [Next Steps](#Next-Steps)
- [Project Organization](#Project-Organization)
- [Installation & Usage](#Installation-&-Usage)


## Dataset
The dataset consists of flat listings with various attributes such as:
* **Numerical Features:** Area, build year, population density, etc.
* **Categorical Features:** City, district, building type, etc.
* **Target Variable:** Price, price per square meter - depending on the tactics chosen


## Data Preprocessing
**Feature Engineering:**
- Numerical features scaled using MinMaxScaler.
- Categorical variables transformed using encoding.
- Aggregation, Data Enrichment
- Additional features extracted from model outputs (meta-features for stacking).

**Feature Selection:**
- Multicollinearity check
- Feature Importances and BorutaPy

**Data Splitting:**
- Training, validation, and test sets created using stratified sampling.

## Models Evaluated
1. **XGBoost & Random Forest Models** - Hyperparameter-tuned versions.
2. **Weighted Averaging** - Combining RF & XGB.
3. **Stacking with Meta-Learners** - Using Ridge, (XGBoost and LGBM were underperforming).
4. **Feature Engineering with Model Outputs** - Using RF & XGB predictions as NN inputs.

## Best Performing Model
The **Stacked Model with Ridge Meta-Learner** provided the most stable and high-performing results:
- **Test R² Score**: 0.8363
- **Test MAE**: 1.4278

## Key Takeaways
- **XGBoost & RF individually performed well** but stacking improved performance.
- **Neural Networks** did not outperform tree-based models, even with embeddings & feature engineering.
- **Stacking with Ridge Regression worked best** among tested meta-learners.
- **Weighted averaging** of RF & XGB performed best.


## Next Steps
- Experiment with additional feature engineering.
- Explore more sophisticated stacking methods.
- Models have difficulty predicting the price for very expensive housing. A further possible way forward could be to categorize expensive housing and analyze it separately.


## Project Organization

```
├── LICENSE                               <- Open-source license
├── README.md                             <- Project documentation
├── data
│   ├── interim                           <- Data after scrapping - input for price prediction
│   └── processed                         <- The final, canonical data sets for modeling
│
├── models                                <- Trained models, model predictions, or model summaries
│
├── notebooks                             <- Jupyter notebooks
│   ├── 1.0-scrapping-real-estate.ipynb   <- Scrapping code-anonymized, deprived of key variables
│   └── 2.0-price-prediction.ipynb        <- Code with data preprocessing and models
│
├── reports                               <- Generated analysis (Profile Report)
│   └── figures                           <- The most important generated graphics and figures
│
└── requirements.txt                      <- Python dependencies
```
## Installation & Usage
1. Clone the repository:
```bash
https://github.com/Zanyata/Real-estate_REG-ML-NN.git
cd Real-estate_REG-ML-NN
```
2. Install dependencies:
```bash
pip install -r requirements.txt
```
3. Run Jupyter Notebook:
```bash
jupyter notebook
```
Train models & evaluate performance using provided notebooks.


--------