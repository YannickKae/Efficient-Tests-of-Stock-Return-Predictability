# Efficient-Tests-of-Stock-Return-Predictability
This R code implements the Bonferroni Q test from Yogo and Campbell's (2006) paper "Efficient Tests of Stock Return Predictability.



In the first block of code, the function BIC is defined and used to determine the optimal order p of an autoregressive (AR) model by minimizing the Bayesian information criterion (BIC) on a dataset ts(m). The AR model is then fit using the dynlm package.

In the second block of code, several intermediate steps are performed in preparation for performing a Bonferroni Q-test. These steps include:

Estimating the standard error of the slope coefficient (se_beta) from a linear regression of y[-c(1:p)] on m[(p+1):(length(m)-1)].

Calculating the first-order difference of the predictor variable m and assigning the result to y_3.

Assigning the values of m without the last element to a new variable x_3_1.

Setting up a matrix lagged_differences_matrix_2 to store lagged differences of m and the variables x_3_1 and y_3.

Regressing y on the lagged differences and x_3_1 using lm and storing the coefficients in a variable psi_coeffcients.

Calculating the residuals u and e from the two linear regressions performed in this step and their variances and covariance.

Calculating the correlations cor and cor_new between u and e and y[-c(1:p)] and e, respectively.

The Bonferroni Q-test is then performed in the third block of code using these intermediate values. The test is used to determine whether the slope coefficient beta of the linear regression of y[-c(1:p)] on m[(p+1):(length(m)-1)] is significantly different from 0. This can be used to test the hypothesis that the predictor variable m is related to the response variable y.
