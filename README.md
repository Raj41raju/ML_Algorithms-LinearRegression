
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

5. Errors or resudal is normally distributed with mean = 0 and std. deviation sigma square

## Calculation of Best Fit Line 


![image alt](https://github.com/Raj41raju/ML_Algorithms-LinearRegression/blob/main/best%20fit%20line.png?raw=true)

To Calculate the best fit line the error between the actual value and the predicted value should be minimum.

**Calculate the error** 

if d is the difference between actual value and predected value then

error = d1 + d2 + _ _ _ _ + dn 

since the difference b/w actual and predected value can be +ve or -ve, so if we directlly add all -ve and +ve errors then they will cencle out each other. Thus we take the **square of errors**

**Q. Why are we taking square of errors (
𝑦
−
𝑦^
)
2 
not taking abs(|y-y^|) ?**

The reason we square the errors instead of taking the absolute value (modulus) is mainly due to three key reasons:

a. Differentiability of Error Functions  

- The squared error function (y - y^)2 is **differentiable everywhere**, making it easier to compute gradients and apply **gradient descent**.  
- The absolute error function (|y - y^|) has a **sharp corner at 0**, making its derivative **undefined** at that point.  
- This creates problems for optimization algorithms like **gradient descent**, which rely on smooth updates.  

b. Penalizing Larger Errors More  

- Squaring the errors **magnifies larger errors** more than smaller ones.  
- This means the model focuses more on **correcting large mistakes**, leading to better data fitting.  

c. Mathematical Convenience
- The squared error function results in a convex function, meaning it has a single global minimum. This ensures gradient descent will converge effectively.
- Absolute error leads to a piecewise linear function, which is harder to optimize using gradient descent.

Now, error = d1²  + d2²  +d3²  + _ _ _ + dn² 

error = ∑ (y_i -y^)² for i = 1 to n 

where y_i = actual value 
y^ = predected value 
 so, y^ = mx_i + c 

error  = ∑ (y_i -mX_i - c)² for i = 1 to n 

in the above equation m and c are the only unknown values

so, error(m,c) = ∑ (y_i -mX_i - c)² for i = 1 to n 

Thus find the value of m & c for minimum error
To find the value of m & c, corrosponding to minimum error, take the partital differentation of error w. r. t. m and c and equate to 0 and find m & c 

![image alt](https://github.com/Raj41raju/ML_Algorithms-LinearRegression/blob/main/mean%20square%20error%201.jpg?raw=true)

![image alt](https://github.com/Raj41raju/ML_Algorithms-LinearRegression/blob/main/mean%20square%20error%202.jpg?raw=true)

























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



