# Efficient Tests of Stock Return Predictability

<p align="center">
  <img src="Header.jpg" style="width:100%">
</p>
<p align="center">
  <i>Regression Model</i>
</p>

This repository contains an R implementation of the Bonferroni Q test from Yogo and Campbell's (2006) paper "Efficient Tests of Stock Return Predictability." The code tests the predictability of stock returns by analyzing the relationship between a predictor variable and stock returns using advanced econometric methods.

## Overview

The R code in this repository is divided into several blocks that perform different tasks:

1. **Bayesian Information Criterion (BIC) calculation**: This block defines the BIC function and uses it to determine the optimal order p of an autoregressive (AR) model by minimizing the BIC on a dataset `ts(m)`. The AR model is then fit using the `dynlm` package.

2. **Intermediate steps for Bonferroni Q-test**: This block performs several intermediate steps in preparation for the Bonferroni Q-test. These steps include estimating the standard error of the slope coefficient, calculating the first-order difference of the predictor variable, setting up a matrix to store lagged differences, and calculating residuals, variances, and covariance, among others.

3. **Bonferroni Q-test**: The final block of code performs the Bonferroni Q-test using the intermediate values calculated in the previous step. The test is used to determine whether the slope coefficient beta of the linear regression is significantly different from 0. This can be used to test the hypothesis that the predictor variable is related to the response variable (stock returns).

## Getting Started

To use the code in this repository, follow these steps:

1. Ensure you have R installed on your system.
2. Install the necessary R packages: `readxl`, `dynlm`, and `quantmod`.
3. Clone this repository or download the R script.
4. Modify the script to load your dataset by replacing the file name and sheet name in the `read_excel()` function.
5. Run the script in your favorite R environment.

## Results Interpretation

The output of the Bonferroni Q-test will help you determine whether the predictor variable is related to the stock returns. If the test indicates a significant relationship, the variable can be considered predictive. Otherwise, it is not predictive. Additionally, a plot is generated to visualize the relationship between different values of rho and beta.

Happy coding and stock return analysis!
