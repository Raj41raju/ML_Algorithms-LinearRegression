
# Regrassion

Regression is a **Supervised Machine Learning** algorithm used for predcting continious values. It established a linear mathematical relationship between a **dependent variable** and one or more **independent variables**.

## Regrassion model equation
For single variable X(CGP of students)

**Y = mX + C**

Where:

Y → Dependent variable (e.g., package)

X → Independent variable (e.g., CGP of students)

m → Slope (rate of change)

c → Intercept (starting value when X is 0)


# Simple Linear Regression
This is the simplest type of regression. Here we assume a **linear** (straight-line) relationship between dependent variable and independent variables.

**Example:**
Predcting House price based on area (square footage) and number of bedrooms.
Predcting Weight of Persion based on height
Predcting sales of ice cream based on temperature

## Assumptions of Linear Regression
1. **Linearity:** The relationship between the independent variable(X) and the dependent variable(Y) must be linear.
        **Example:** House price increases with increase in house size (sqaure footage)
2. **Indepedence:** Observations should not be correlated With each other.
**Example:** The Price of one house should not depend on the price of a neighbouring house.

3. **Homoscedasticity:** The variance of residuals(errors= actual - predected) should be constant accross all values of X.

**Example:** 
- **For small houses:** Residuals ≈ Rs. ±10,000  
- **For medium houses:** Residuals ≈ Rs. ±10,000  
- **For large houses:** Residuals ≈ Rs. ±10,000  

if variance of residuals(errors) is not constant then predictions can be **biased** and **inefficient**.

4. **No Multicollinearity:** In multple regression(having more then one independent variable), independent variables should not be highly correlated.
**Example:** since scuare footage and no. of rooms are highly correlated, so it can distort the model accuracy.





# NOTE:
### In scikit-learn 
- Calculation of best fit line in class **LinearRegression** the Ordinary Least Squares (OLS) method is used which is part of **Closed form Solution**
-  Calculation of best fit line in class **SGDRegressor** is calculated by **Gradient Decent** method is used which is part of non closed form solution.

# SUPPORT TOPICS

# Homoscedasticity and Hetroscedasticity in details:

## Homoscedasticity:
Homoscedasticity means that the variance of Residuals(errors = actual - predected) remains constant accross all value of indepemdent variable (X).

 - If the variance of Residuals (error) is constant, the regression model makes reliable predictions across all values of X
- If the variance of Residuals (error) changes(i.e heteroscedasticity) then predictions can be **biased** and **inefficient**.

### Let's Understand with Example
**Example 1: Predicting House Prices (Homoscedasticity)**
- let us suppose we have build a regression model to predict the house price based on **area** of house (square footage).
- if the variance of residuals (errors actual - predected) remains constant different sizes of house (i.e small house, medium house, large house), then model satisfies the Homoscedasticity.
- A scatter plot of residuals vs predicted values can show the visualization, If the residuals are evenly spread across all house sizes, then data is Homoscedastic.

**Example 2: Income Vs Expanses (Hetroscedasticity)**
- Let us suppose we have build a regression model to predict the monthly expance of the presion based on their income.
- For low-income individuals, expenses are fairly predictable.
- But for high-income individuals, some spend a little, while others spend a lot—causing increasing variance in errors.
- This results in heteroscedasticity, where the spread of errors increases as income rises.
- In a residuals vs. predicted values plot, errors increase as predicted values increase, forming a funnel shape (wider spread for higher values).

### How to Detect Homoscedasticity?
1. Residual Plot
- Plot residuals (errors) against predicted values.
If errors are randomly scattered, homoscedasticity holds.
- If errors show a pattern (funnel shape or increasing spread), heteroscedasticity exists.
2. Breusch-Pagan Test (Statistical Test)
- A statistical test to check whether error variance is constant.
- If the test result is significant (p-value < 0.05), heteroscedasticity is present.

### How to Fix Heteroscedasticity?
If heteroscedasticity is detected, we can:
- Use Log Transformation → Convert Y values using logrithmic Transformation.
- Weighted Least Squares (WLS) → Assign different weights to handle varying error variance.
- Use Robust Standard Errors → Adjust for heteroscedasticity in regression models.

![image alt](https://github.com/Raj41raju/ML_Algorithms-LinearRegression/blob/main/Heteroscedasticity.jpg?raw=true)

## Summary
## Homoscedasticity vs. Heteroscedasticity  

| **Feature**            | **Homoscedasticity ✅** | **Heteroscedasticity ❌** |
|------------------------|----------------------|----------------------|
| **Error Variance**     | Constant             | Changes with \(X\)  |
| **Residuals Pattern**  | Random spread        | Funnel shape (wider for higher \(X\)) |
| **Impact on Model**    | Reliable Predictions | Biased & inefficient model |
| **Detection Method**   | Residual Plot, Breusch-Pagan Test | Same methods |
| **Fixing Method**      | No fixing needed        | Log transformation, WLS, Robust Errors |

