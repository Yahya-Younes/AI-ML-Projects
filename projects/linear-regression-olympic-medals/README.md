# Linear Regression – Predicting Olympic Medals

Implementation of multiple linear regression **from scratch with the normal equation**,
validated against scikit-learn's `LinearRegression`.

## Dataset

[`data/teams.csv`](data/teams.csv) – 2,014 rows, one per country per Olympic Games.

| Column | Description |
|---|---|
| `team`, `year` | Country code and Games year |
| `athletes`, `events` | Number of athletes sent / events entered |
| `age`, `height`, `weight` | Average athlete characteristics |
| `prev_medals` | Medals won at the previous Games |
| `medals` | Medals won (**target**) |

## Method

Features: `athletes` and `prev_medals` (+ an intercept column).

1. Solve the normal equation  **B = (XᵀX)⁻¹ Xᵀy**.
2. Predict **ŷ = XB** and compute **R² = 1 − SSR / SST**.
3. Fit `sklearn.linear_model.LinearRegression` on the same features and compare.

## Results

| Parameter | Normal equation | scikit-learn |
|---|---|---|
| Intercept | −1.962 | −1.962 |
| `athletes` | 0.0711 | 0.0711 |
| `prev_medals` | 0.7341 | 0.7341 |

**R² ≈ 0.872** — the two features explain about 87 % of the variance in medal counts.
Both approaches give identical coefficients, confirming that scikit-learn's ordinary
least squares solves the same problem as the normal equation.

## Running

```bash
pip install numpy pandas scikit-learn jupyter
cd projects/linear-regression-olympic-medals
jupyter notebook linear_regression.ipynb
```

The notebook reads `data/teams.csv` relative to its own folder.
