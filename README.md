
# Real Estate Valuation Using Support Vector Regression (SVR) 

This project aims to predict real estate property prices using Support Vector Regression (SVR).
## Tech Stack

![Python](https://img.shields.io/badge/Python-3.10-blue)
![scikit-learn](https://img.shields.io/badge/scikit--learn-ML-yellow)
![Pandas](https://img.shields.io/badge/Pandas-EDA-lightgrey)
![NumPy](https://img.shields.io/badge/NumPy-Math-orange)
![Matplotlib](https://img.shields.io/badge/Matplotlib-Plotting-blueviolet)
![Seaborn](https://img.shields.io/badge/Seaborn-Visualization-teal)
![Tableau](https://img.shields.io/badge/Tableau-Visualization-E97627?logo=tableau&logoColor=white)


## Exploratory Data Analysis (EDA)
The Real Estate Valuation dataset contains historical market data from Sindian District, New Taipei City, Taiwan. 
It is a regression dataset with 414 observations, where each row represents a real estate transaction. The dataset includes only numerical features and contains no missing values.
You can access the dataset here: [Real Estate Valuation Data Set](https://archive.ics.uci.edu/dataset/477/real+estate+valuation+data+set)

* The dataset is split into training and testing sets
* Numerical features are standarized using `StandardScaler`

### Correlation Heatmap

A correlation heatmap is used to examine linear relationships between input features and the target variable (house price). This visualization helps identify the most influential features and supports feature selection decisions.

![correlation_heatmap](https://github.com/gopletzzz/Real-Estate-Valuation-SVR/blob/main/images/correlation_heatmap.png)

### House Price Distribution
The distribution plot illustrates how house prices are spread across the dataset.

![house_price_distribution](https://github.com/gopletzzz/Real-Estate-Valuation-SVR/blob/main/images/house_price_distribution.png)

### Price Distribution by The Number of Convenience Store
The distribution plot illustrates how house prices are spread across the dataset by the number of covenience store.

![house_price_distribution](https://github.com/gopletzzz/Real-Estate-Valuation-SVR/blob/main/images/convenience_store.jpeg)

### Dashboard 
![house_price_distribution](https://github.com/gopletzzz/Real-Estate-Valuation-SVR/blob/main/images/dashboard.png)

For full interactive exploration and the complete dashboard, access the Tableau Public link:

[Interactive Dashboard](https://public.tableau.com/views/Book1_17700462283560/RealEstateValuationAnalysisSindianDistrictNewTaipeiCity?:language=en-US&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link)


## Model
### Baseline Model Performance

The baseline SVR model was evaluated using normalized target values.  
The following metrics represent the initial model performance before hyperparameter tuning:

| Metric | Value |
|------|-------|
| RMSE (Normalized) | 0.0714 |
| MAE (Normalized)  | 0.0572 |
| MSE (Normalized)  | 0.0051 |
| R² Score          | 0.6325 |

## Model Exploration

### Hyperparameter Grid

| Hyperparameter | Values                | Description                                   |
|----------------|-----------------------|-----------------------------------------------|
| kernel         | linear, rbf, poly     | Kernel function used by the SVR model          |
| C              | 0.1, 1, 10             | Regularization parameter controlling complexity |
| epsilon        | 0.1, 0.2, 0.5          | Width of the epsilon-insensitive loss margin  |


### Model Performance Comparison

| Model / Kernel        | RMSE (Normalized) | MAE (Normalized) | MSE (Normalized) | R² Score |
|-----------------------|------------------|------------------|------------------|----------|
| Baseline              | 0.07             | 0.06             | 0.01             | 0.63     |
| Best Model (RBF)           | 0.07             | 0.06             | 0.01             | 0.63     |
| RBF Kernel            | 0.07             | 0.06             | 0.01             | 0.63     |
| Linear Kernel         | 0.09             | 0.07             | 0.01             | 0.44     |
| Polynomial Kernel     | 0.10             | 0.07             | 0.01             | 0.31     |


![prediction_test](https://github.com/gopletzzz/Real-Estate-Valuation-SVR/blob/main/images/prediction_test.png)


## Model Evaluation Summary

- The baseline model achieved a normalized R² score of approximately 0.63 and serves as a reference point for comparison.
- The best-performing model uses an RBF kernel with parameters C = 1 and epsilon = 0.1, achieving the highest performance with RMSE (normalized) of 0.071, MAE (normalized) of 0.057, and an R² score of 0.633.
- The RBF kernel consistently outperformed other kernels, indicating strong nonlinear relationships within the dataset.
- The linear kernel showed weaker performance with an R² score of approximately 0.44, suggesting that a linear model is insufficient for this task.
- The polynomial kernel performed the worst with an R² score of approximately 0.31, indicating poor suitability for this dataset.
