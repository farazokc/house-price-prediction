# House Price Prediction System

## Project Summary
The House Price Prediction System predicts the price of a house based on a provided dataset. The dataset contains a large amount of data with several attributes, which form the basis for model training and prediction. The system is trained to provide predictions based on a test dataset or user input.

## About the Dataset
The dataset is sourced from Kaggle’s ‘[House Prices - Advanced Regression Techniques](https://www.kaggle.com/c/house-prices-advanced-regression-techniques/)’. It includes both numerical and categorical data. The dataset contains the following files:

- `train.csv` - the training set
- `test.csv` - the test set
- `data_description.txt` - full description of each column
- `sample_submission.csv` - a benchmark submission from a linear regression on year and month of sale, lot square footage, and number of bedrooms

### Important Attributes
Some of the key attributes in the dataset are:

- **SalePrice**: The property's sale price in dollars (target variable).
- **OverallQual**: Overall material and finish quality of the house.
- **GrLivArea**: Above ground living area square feet.
- **GarageCars**: Size of garage in car capacity.
- **TotalBsmtSF**: Total square feet of basement area.
- **YearBuilt**: Original construction date.
- **Neighborhood**: Physical locations within Ames city limits.
- **KitchenQual**: Kitchen quality.
- **LotArea**: Lot size in square feet.
- **FullBath** and **HalfBath**: Number of bathrooms.
- **Fireplaces**: Number of fireplaces.
- **GarageArea**: Size of garage in square feet.
- **CentralAir**: Central air conditioning availability.

The full list of attributes along with their descriptions are available [here](https://www.kaggle.com/c/house-prices-advanced-regression-techniques/data).

## Analysis
In our analysis, we performed basic exploratory data analysis (EDA). During EDA, we plotted the target variable, `SalePrice`, to observe its distribution in the data. The following columns were dropped due to more than half of their data being missing, and `Id` was dropped as it was irrelevant to training:

- `Id`
- `Alley`
- `PoolQC`
- `Fence`
- `MiscFeature`

The dataset was divided into numerical and categorical data, and missing values (NA) were filled with appropriate values according to the datatype. One-Hot Encoding was performed for categorical columns.

## Model Training
After processing the data, I trained multiple regression models and calculated the Root Mean Squared Error (RMSE) for each model to measure accuracy. The model with the lowest RMSE, RandomForestRegressor, was selected for further training and testing. The model was then used to make predictions, which were written to an output file with matching IDs.

## Hyperparameter Tuning
During model training, hyperparameter tuning using Optuna was attempted on the following models:

- **XGBRegressor (XGBoost)**
- **BayesianRidge (Bayesian Regression)**
- **RandomForestRegressor (Random Forest Regression)**

Only XGBoost provided positive results, decreasing its RMSE from an estimated 24,000 to 20,000. Tuning on BayesianRidge and RandomForestRegressor was unsuccessful, as the RMSE increased compared to the default configuration of the models.

## Project Dependencies

To run the code and reproduce the analysis, you will need the following dependencies:

- Python
- NumPy 
- pandas
- Matplotlib
- seaborn
- Scikit-Learn
- Optuna
