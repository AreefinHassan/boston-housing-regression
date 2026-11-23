# Boston Housing Regression

Predicting median home values in Boston with supervised regression models, comparing linear, penalized, and nearest-neighbour approaches on the classic Boston Housing dataset.

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

The data were checked for missing values, then split into a **75% training set** and a **25% test set**. Four regression models were trained on the training set and evaluated on the test set using RMSE and R².

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

## Project layout

```
├── README.md
├── data/
│   └── BostonHousing.csv          # 506 rows, 13 predictors + MEDV
└── report/
    ├── Boston_Housing_Report.pdf
    └── Boston_Housing_Report.docx
```

The report documents each model's training, test metrics, and interpretation in full.
