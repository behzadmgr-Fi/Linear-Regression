# Population Prediction from Housing Data — Simple Linear Regression
 
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/)
![Python](https://img.shields.io/badge/Python-3.10%2B-blue)
![scikit--learn](https://img.shields.io/badge/scikit--learn-ML-orange)
 
A simple linear regression model that predicts an area's **population** from its **total number of bedrooms**, using the classic California Housing dataset.
 
## Overview
 
This project walks through a complete (if intentionally minimal) supervised learning workflow: loading and exploring housing data, checking the relationship between two variables, training a single-feature linear regression model, and evaluating its predictive performance.
 
## Dataset
 
The [California Housing dataset](https://www.kaggle.com/datasets/camnugent/california-housing-prices) — 20,640 rows × 10 columns, covering housing attributes for California districts from the 1990 census.
 
| Column | Description |
|---|---|
| `total_bedrooms` | Total number of bedrooms in the district (**input feature**) |
| `population` | Total population of the district (**target**) |
 
## Methodology
 
1. **Load & explore** — Read the dataset into a Pandas DataFrame; inspect structure, dtypes, and missing values with `.info()` / `.describe()`.
2. **Select variables** — Isolate `total_bedrooms` (feature) and `population` (target) into a working DataFrame.
3. **Handle missing values** — `total_bedrooms` had 207 missing values out of 20,640 (~1%); rows with missing values were dropped with `.dropna()`.
4. **Explore the relationship** — Computed the Pearson correlation (**0.878**) and visualized the relationship with a scatter plot, confirming a strong positive, roughly linear trend.
5. **Train/test split** — 80% train / 20% test, with `random_state=42` for reproducibility.
6. **Train the model** — Fit a `LinearRegression()` model from scikit-learn on the training set.
7. **Predict & evaluate** — Generated predictions on the test set and scored them with R², MSE, and RMSE.
## Results
 
| Metric | Value |
|---|---|
| **R²** | 0.8076 |
| **MSE** | 253,605.82 |
| **RMSE** | 503.59 |
| Intercept | 155.68 |
| Coefficient | 2.36 |
 
`total_bedrooms` alone explains **~80.8%** of the variance in `population`, and predictions are typically off by about **504 people**. The fitted line: `population ≈ 155.68 + 2.36 × total_bedrooms`.
 
![Regression fit](docs/regression_plot.png)
*Actual population values (blue) vs. the fitted regression line (red) on the test set.*
 
## Conclusion
 
A single feature (`total_bedrooms`) captures a strong majority of the variance in population, confirming the intuitive link between housing density and population size. Performance is solid for a one-feature baseline, but it leaves ~19% of the variance unexplained. Natural next steps:
 
- Add features such as `households`, `total_rooms`, or `median_income` (multiple linear regression)
- Impute missing `total_bedrooms` values (e.g., median imputation) instead of dropping rows, to retain the full dataset
- Compare against non-linear models (e.g., decision trees, gradient boosting) to check for non-linear effects
## How to Run
 
```bash
git clone <your-repo-url>
cd <repo-folder>
pip install -r requirements.txt
```
 
**requirements.txt**
```
pandas
numpy
scikit-learn
matplotlib
```
 
Then open `notebook.ipynb` in Jupyter or [Google Colab](https://colab.research.google.com/) and run all cells top to bottom. Update the dataset path in the load step to point to your local copy of `housing.csv`.
 
## Example Usage
 
```python
from sklearn.linear_model import LinearRegression
from sklearn.model_selection import train_test_split
 
X = reg_df[["total_bedrooms"]]
y = reg_df["population"]
 
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)
 
model = LinearRegression()
model.fit(X_train, y_train)
 
y_pred = model.predict(X_test)
```
 
## Repository Structure
 
```
.
├── Linear Regression.ipynb         # Full analysis notebook
├── data/
│   └── housing.csv        # California Housing dataset
├── regression_plot.png
│   
├── requirements.txt
└── README.md
```
 
## License
 
MIT
 
