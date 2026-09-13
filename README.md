# Linear-Regression
# Population Prediction Using Linear Regression

## Project Overview

This project uses simple linear regression to predict an area's population based on its total number of bedrooms.

## Steps

1. **Load the dataset**
   The housing dataset was loaded into a Pandas DataFrame.

2. **Select the variables**
   `total_bedrooms` was selected as the input feature, and `population` was selected as the target variable.

3. **Handle missing values**
   Rows containing missing values were removed using `dropna()`.

4. **Explore the data**
   The dataset structure, column types, and missing values were examined using `info()`.

5. **Analyze the relationship**
   Correlation and scatter plots were used to examine the relationship between total bedrooms and population.

6. **Split the dataset**
   The data was divided into 80% training data and 20% testing data.

7. **Train the model**
   A linear regression model was trained using the training dataset.

8. **Make predictions**
   The trained model predicted population values for the test dataset.

9. **Evaluate the model**
   The model was evaluated using R², MSE, and RMSE.

## Results

* **R²:** 0.8076
* **MSE:** 253,605.82
* **RMSE:** 503.59

The R² score indicates that total bedrooms explain approximately 80.8% of the variation in population. The RMSE indicates a typical prediction error of approximately 504 people.

## Conclusion

The model demonstrates a strong positive relationship between total bedrooms and population. Although its performance is relatively good for a single-feature model, additional housing features could improve prediction accuracy.

