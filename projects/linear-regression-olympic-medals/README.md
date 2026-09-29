# Linear Regression Project
This project is an implementation of Linear Regression in Python using the normal equation to find the parameters
and then using scikit-learn library to compare the results. The purpose of this project is to demonstrate how to build 
a linear regression model and how to use it for making predictions.

# Prerequisites
Before running this project, you need to have the following software installed:

Python 3.6 or higher
scikit-learn library
NumPy library
pandas library
matplotlib library


# Dataset
The dataset used in this project is given below: [`teams.csv`](teams.csv) – 2,014 rows, one per country per Olympic Games.

| Column | Description |
|---|---|
| `team`, `year` | Country code and Games year |
| `athletes`, `events` | Number of athletes sent / events entered |
| `age`, `height`, `weight` | Average athlete characteristics |
| `prev_medals` | Medals won at the previous Games |
| `medals` | Medals won (**target**) |

Features used: `athletes` and `prev_medals` (+ an intercept column).

# Running the project
This project can run on a jupyter notebook

```bash
pip install numpy pandas scikit-learn jupyter
jupyter notebook linear_regression.ipynb
```

Keep `teams.csv` in the same folder as the notebook. Two cells need a small fix before the
scikit-learn comparison runs: `lr.fit(...)` is missing its closing parenthesis, and
`lr.intercept` should be `lr.intercept_`.



# Results
Normal equation **B = (XᵀX)⁻¹ Xᵀy** vs. scikit-learn:

| Parameter | Normal equation | scikit-learn |
|---|---|---|
| Intercept | −1.962 | −1.962 |
| `athletes` | 0.0711 | 0.0711 |
| `prev_medals` | 0.7341 | 0.7341 |

**R² = 1 − SSR/SST ≈ 0.872.**

The scikit-learn library provides a convenient way to implement linear regression in Python, using the Ordinary Least Squares (OLS) method.
This method is equivalent to solving the normal equation, which is a mathematical formula that gives us the optimal values of the coefficients
in the linear regression model. Implementing linear regression using the normal equation is also a common approach, and both methods should give
the same results. The advantage of using the scikit-learn library is that it provides a simple interface for fitting linear regression models
and making predictions, as well as tools for evaluating the model's performance. Additionally, scikit-learn also supports more advanced linear
regression methods, such as Ridge Regression and Lasso Regression, which can be useful in certain scenarios where there is high multicollinearity
between the independent variables or when there are too many features in the dataset.

# Conclusion
Linear Regression is a simple but powerful algorithm that can be used for making predictions. In this project, we demonstrated how to implement
linear regression in Python using scikit-learn library. The results of the linear regression algorithm showed that it is able to make accurate predictions
on the teams dataset.
