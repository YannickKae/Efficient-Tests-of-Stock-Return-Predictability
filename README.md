# Efficient Tests of Stock Return Predictability

<p align="center">
  <img src="Header.png" style="width:100%">
</p>
<p align="center">
  <i>Simulated Returns with highly persistent Reggressor</i>
</p>

Predicting stock returns, especially using financial measures such as the earnings-price ratio (E/P), received considerable academic attention in the 1970s and 1980s. Most research uses ordinary least squares (OLS) regression, with stock returns as the dependent variable against lagged financial predictors. However, their inference based on first-order-asymptotics might be spurious, because the OLS estimator is 2nd order biased, and its t-statistic has a non-normal limit distribution, if the predictor is highly persistent (long-memory) and its innovations are closely correlated with the regression disturbances. The former is a common property of many relevant financial time series.

$$
r_t = \alpha + \beta x_{t-1} + u_t
$$

$$
x_t = \gamma + \sum_{i=1}^{p} \rho_i x_{t-i} + e_t
$$

[Campbell and Yogo (2006)](https://www.sciencedirect.com/science/article/abs/pii/S0304405X05002151) address these limitations by proposing the **Bonferroni Q-test**. This test refines the infeasible uniformly most powerful Q-test by applying the Bonferroni method.

$$
Q\left(\beta_0, \rho\right)=\frac{\sum_{t=1}^T x_{t-1}^\mu\left[r_t-\beta_0 x_{t-1}-\beta_{u e}\left(x_t-\rho x_{t-1}\right)\right]}{\sigma_u\left(1-\delta^2\right)^{1 / 2}\left(\sum_{t=1}^T x_{t-1}^{\mu 2}\right)^{1 / 2}}
$$

## Overview

The R code implements the testing procedure and is divided into several steps:

1. **Bayesian Information Criterion (BIC) calculation**: This block defines the BIC function and uses it to determine the optimal order p of an autoregressive (AR) model by minimizing the BIC on a dataset `ts(m)`. The AR model is then fit using the `dynlm` package.

2. **Intermediate steps for Bonferroni Q-test**: This block performs several intermediate steps in preparation for the Bonferroni Q-test. These steps include estimating the standard error of the slope coefficient, calculating the first-order difference of the predictor variable, setting up a matrix to store lagged differences, and calculating residuals, variances, and covariance, among others.

3. **Bonferroni Q-test**: The final block of code performs the Bonferroni Q-test using the intermediate values calculated in the previous step. The test is used to determine whether the slope coefficient beta of the linear regression is significantly different from 0. This can be used to test the hypothesis that the predictor variable is related to the response variable (stock returns).

## Results Interpretation

<p align="center">
  <img src="Result.png" style="width:100%">
</p>
<p align="center">
  <i>OLS estimator's Bonferroni Confidence Intervals as a Function of Rho</i>
</p>
