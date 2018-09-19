# Linear Regression

### Assumptions
* Linear: Check by plot
* Mean of residuals should be zero: Just check the mean of residuals.
* Homoscedasticity or equal variance of residuals: Check plot of "residuals vs
independent variables"
* No autocorrelation of residuals (especially for time series): Run-test for
residuals
* Independent variables and residuals uncorrelated: Correlation test between
independent variables and residuals
* No perfect multicollinearity: Variance Inflation Factor (VIF) to check
whether the information of specific variable has been covered by other variables
* Normality of residuals: qq-plot for residuals

### Tests on Coefficients
* Distance between observation and observation mean can be split to distance
between observation and estimated value, and distance between estimated value
and observation mean. This is how r-squared value generated.
* Two classical tests can be used to do the coefficients test.
First one, get the mean and variance of the coefficients, apply the t-test.
Second one, create a F-test by calculating MSR and MSE, this is actually a
variance test.
In simple linear regression, these two tests should give the exactly same p-value.
