# Boston Housing Regression

![R](https://img.shields.io/badge/language-R-276DC3?style=flat-square&logo=r&logoColor=white)
![Dataset](https://img.shields.io/badge/dataset-Boston%20Housing-506%20rows-blue?style=flat-square)
![License](https://img.shields.io/badge/license-MIT-green?style=flat-square)

Predicting median home values in Boston with supervised regression models, comparing linear, penalized, and nearest-neighbour approaches on the classic Boston Housing dataset.

## Key Results

- **Best model: K-Nearest Neighbours — test RMSE 3.572, R² 0.829.** KNN clearly outperformed the linear and penalized models, explaining about 83% of the variance in median home values.
- **Linear Regression — test RMSE 4.393, R² 0.743.** Ridge (RMSE 4.401, R² 0.743) and Lasso (RMSE 4.397, R² 0.742) performed almost identically to plain linear regression — regularization added little on this dataset.
- **Most influential features** in the linear model: **LSTAT** (lower-status population), **RM** (average rooms per dwelling), and **DIS** (distance to employment centres).

All metrics are on the held-out 25% test set. RMSE is in $1,000s, so the KNN model's predictions are off by about $3,572 on average.

## Dataset

The Boston Housing dataset — 506 observations of Boston-area suburbs, with 13 predictors and one target:

| Variable | Description |
| --- | --- |
| CRIM | Per-capita crime rate by town |
| ZN | Proportion of residential land zoned for lots over 25,000 sq. ft. |
| INDUS | Proportion of non-retail business acres per town |
| CHAS | Charles River dummy variable (1 if tract bounds river, 0 otherwise) |
| NOX | Nitric oxides concentration (parts per 10 million) |
| RM | Average number of rooms per dwelling |
| AGE | Proportion of owner-occupied units built prior to 1940 |
| DIS | Weighted distances to five Boston employment centres |
| RAD | Index of accessibility to radial highways |
| TAX | Full-value property-tax rate per $10,000 |
| PTRATIO | Pupil–teacher ratio by town |
| LSTAT | Percentage of lower-status population |
| **MEDV** | **Median value of owner-occupied homes (in $1,000s) — the target** |

## Method

The data were checked for missing values (none found), then split into a **75% training set** (379 observations) and a **25% test set** (127 observations). Four regression models were trained on the training set and evaluated on the test set using RMSE and R²:

1. **Linear Regression** — ordinary least squares on all 13 predictors.
2. **Ridge Regression** — L2-penalized linear regression.
3. **Lasso Regression** — L1-penalized linear regression.
4. **K-Nearest Neighbours Regression** — distance-based, non-parametric regression.

## Results (test set)

| Model | RMSE | R² |
| --- | --- | --- |
| Linear Regression | 4.393 | 0.743 |
| Ridge Regression | 4.401 | 0.743 |
| Lasso Regression | 4.397 | 0.742 |
| **K-Nearest Neighbours** | **3.572** | **0.829** |

RMSE is in the same units as the target, so an RMSE of 4.393 means the linear model's predictions are off by about $4,393 on average.

## Key findings

- **KNN regression performed best**, with the lowest error (RMSE 3.572) and the highest explained variance (R² 0.829) — clearly ahead of the linear and penalized models.
- The linear and penalized models performed almost identically (RMSE ≈ 4.40, R² ≈ 0.74); regularization added little on this dataset.
- In the linear model, the most influential features were **LSTAT** (lower-status population), **RM** (average rooms per dwelling), and **DIS** (distance to employment centres) — the strongest drivers of median home value.

## How to Run

1. Open R or RStudio.
2. Load the dataset from `data/BostonHousing.csv` (506 rows, 13 predictors + `MEDV`).
3. Check for missing values, then split the data 75% training / 25% test.
4. Fit linear, ridge, lasso, and K-nearest neighbours regression models on the training set.
5. Evaluate each model on the test set with RMSE and R².

The full step-by-step analysis, model outputs, and interpretation are documented in `report/Boston_Housing_Report.pdf`.

## Project layout

```
├── README.md
├── LICENSE
├── data/
│   └── BostonHousing.csv          # 506 rows, 13 predictors + MEDV
└── report/
    ├── Boston_Housing_Report.pdf
    └── Boston_Housing_Report.docx
```

The report documents each model's training, test metrics, and interpretation in full.

## License

MIT License — see [LICENSE](LICENSE).
