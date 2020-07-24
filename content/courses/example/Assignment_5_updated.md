---
date: "2019-05-05T00:00:00+01:00"
draft: false
linktitle: A4_314
menu:
  example:
    parent: Assignments STA314
    weight: 4
title: Assignment 4
toc: true
type: docs
weight: 4
---

### Question 1

Here, we want to explore the fact that ridge regression tends to give
similar coefficient values to correlated variables, whereas lasso may
give quite different coefficient values to correlated variables.

In this question, we are provided that *n* = 2, *p* = 2,
*x*<sub>11</sub> = *x*<sub>12</sub> and
*x*<sub>21</sub> = *x*<sub>22</sub>. Furthermore, we are also given that
*y*<sub>1</sub> + *y*<sub>2</sub> = 0,
*x*<sub>11</sub> + *x*<sub>21</sub> = 0 and
*x*<sub>12</sub> + *x*<sub>22</sub> = 0. As a result, the estimate for
the intercept in a least squares, ridge regression or lasso model is
zero: $\\hat{\\beta\_0} = 0$

#### Part a:

Here, we want to write out the ridge regression optimization problem in
this setting.

So, we want to minimize:

(*y*<sub>1</sub> − *β*<sub>1</sub>*x*<sub>11</sub> − *β*<sub>2</sub>*x*<sub>12</sub>)<sup>2</sup> + (*y*<sub>2</sub> − *β*<sub>1</sub>*x*<sub>21</sub> − *β*<sub>2</sub>*x*<sub>22</sub>)<sup>2</sup> + *λ*(*β*<sub>1</sub><sup>2</sup> + *β*<sub>2</sub><sup>2</sup>)

Now, we know that *x*<sub>11</sub> = *x*<sub>12</sub> and
*x*<sub>21</sub> = *x*<sub>22</sub>. So, substituting *x*<sub>12</sub>
as *x*<sub>11</sub> and *x*<sub>22</sub> as *x*<sub>21</sub>, our
function to be minimized becomes,

Now, we know that *y*<sub>1</sub> + *y*<sub>2</sub> = 0. Therefore,
*y*<sub>2</sub> = −*y*<sub>1</sub>. Moreover, we also know that
*x*<sub>11</sub> + *x*<sub>21</sub> = 0. So,
*x*<sub>21</sub> = −*x*<sub>11</sub>. So, substituting this, our problem
becomes,

(*y*<sub>1</sub> − *β*<sub>1</sub>*x*<sub>11</sub> − *β*<sub>2</sub>*x*<sub>11</sub>)<sup>2</sup> + ( − (*y*<sub>1</sub> − *β*<sub>1</sub>*x*<sub>11</sub> − *β*<sub>2</sub>*x*<sub>11</sub>))<sup>2</sup> + *λ*(*β*<sub>1</sub><sup>2</sup> + *β*<sub>2</sub><sup>2</sup>)
 which is,

$$\\boxed{2(y\_1 - ({\\beta\_1} +  {\\beta\_2})x\_{11})^2 + \\lambda ({\\beta\_1}^2 + {\\beta\_2}^2)}$$

#### Part b:

Here, to find the coefficient estimates for ridge regression, we first
differentiate result (A) from part (a) with respect to
$\\hat{\\beta\_1}$ and $\\hat{\\beta\_2}$, set both of them to zero and
then solve for $\\hat{\\beta\_1}$ and $\\hat{\\beta\_2}$

Differentiating with respect to $\\hat{\\beta\_1}$ and setting it to 0,
we have:
$$2(y\_1-\\hat{\\beta\_1}x\_{11} - \\hat{\\beta\_2}x\_{11}) (-x\_{11}) + 2(y\_2-\\hat{\\beta\_1}x\_{21} - \\hat{\\beta\_2}x\_{21}) (-x\_{21}) + 2\\lambda \\hat{\\beta\_1} = 0$$

Therefore,

Similarly, differentiating with respect to $\\hat{\\beta\_2}$ and
setting it to 0, we have:
$$2(y\_1-\\hat{\\beta\_1}x\_{11} - \\hat{\\beta\_2}x\_{11}) (-x\_{11}) + 2(y\_2-\\hat{\\beta\_1}x\_{21} - \\hat{\\beta\_2}x\_{21}) (-x\_{21}) + 2\\lambda \\hat{\\beta\_2} = 0$$

Therefore,

Now, to solve for $\\hat{\\beta\_1}$ and $\\hat{\\beta\_2}$, we compare
equation (B) and equation (C). Comparing that, we get:
$$\\hat{\\beta\_1} = \\hat{\\beta\_2}$$

#### Part c:

Here, we want to write out the lasso optimization problem in this
setting.

So, we want to minimize:

(*y*<sub>1</sub> − *β*<sub>1</sub>*x*<sub>11</sub> − *β*<sub>2</sub>*x*<sub>12</sub>)<sup>2</sup> + (*y*<sub>2</sub> − *β*<sub>1</sub>*x*<sub>21</sub> − *β*<sub>2</sub>*x*<sub>22</sub>)<sup>2</sup> + *λ*(|*β*<sub>1</sub>|+|*β*<sub>2</sub>|)

Now, we know that *x*<sub>11</sub> = *x*<sub>12</sub> and
*x*<sub>21</sub> = *x*<sub>22</sub>. So, substituting *x*<sub>12</sub>
as *x*<sub>11</sub> and *x*<sub>22</sub> as *x*<sub>21</sub>, our
function to be minimized becomes,

Now, we know that *y*<sub>1</sub> + *y*<sub>2</sub> = 0. Therefore,
*y*<sub>2</sub> = −*y*<sub>1</sub>. Moreover, we also know that
*x*<sub>11</sub> + *x*<sub>21</sub> = 0. So,
*x*<sub>21</sub> = −*x*<sub>11</sub>. So, substituting this, our problem
becomes,

(*y*<sub>1</sub> − *β*<sub>1</sub>*x*<sub>11</sub> − *β*<sub>2</sub>*x*<sub>11</sub>)<sup>2</sup> + ( − (*y*<sub>1</sub> − *β*<sub>1</sub>*x*<sub>11</sub> − *β*<sub>2</sub>*x*<sub>11</sub>))<sup>2</sup> + *λ*(|*β*<sub>1</sub>|+|*β*<sub>2</sub>|)
 which is,

$$\\boxed{2(y\_1 - ({\\beta\_1} +  {\\beta\_2})x\_{11})^2 + \\lambda (|{\\beta\_1}| + |{\\beta\_2}|)}$$

#### Part d:

Here, we want to show that for the optimization problem in part (c), the
Lasso coefficients are not unique and then show the solutions. Now, in
part (c), we see that the optimization problem has absolute values. So,
understanding how to differentiate them is the first important step.

From basic calculus, we know that:

$$
\\frac{d}{{dx}}|u| = \\frac{d}{{dx}}\\sqrt {{{{u}}^2}}  = \\frac {u \\times u'}{|u|},  u \\neq 0
$$

So, from part (c), we differentiate equation D with respect to
$\\hat{\\beta\_1}$ and $\\hat{\\beta\_2}$ and set them to 0.
Differentiating with respect to $\\hat{\\beta\_1}$ and setting it to 0,
we have:
$$2(y\_1-\\hat{\\beta\_1}x\_{11} - \\hat{\\beta\_2}x\_{11}) (-x\_{11}) + 2(y\_2-\\hat{\\beta\_1}x\_{21} - \\hat{\\beta\_2}x\_{21}) (-x\_{21}) + \\frac{\\lambda \\hat{\\beta\_1}}{|\\hat{\\beta\_1|}} = 0$$

Similarly, differentiating with respect to $\\hat{\\beta\_2}$ and
setting it to 0, we have:
$$2(y\_1-\\hat{\\beta\_1}x\_{11} - \\hat{\\beta\_2}x\_{11}) (-x\_{11}) + 2(y\_2-\\hat{\\beta\_1}x\_{21} - \\hat{\\beta\_2}x\_{21}) (-x\_{21}) + \\frac{\\lambda \\hat{\\beta\_2}}{|\\hat{\\beta\_2}|} = 0$$

Now, equating the above two equations, we get:
$$ \\frac{\\lambda \\hat{\\beta\_1}}{|\\hat{\\beta\_1}|} = \\frac{\\lambda \\hat{\\beta\_2}}{|\\hat{\\beta\_2}|} $$
 which implies,
$$ \\frac{\\hat{\\beta\_1}}{|\\hat{\\beta\_1}|} = \\frac{\\hat{\\beta\_2}}{|\\hat{\\beta\_2}|} $$

from which we can see that both $\\hat{\\beta}\_1$, $\\hat{\\beta}\_2$
take the same sign and that there are many possible solutions to this
optimization problem.

Now, we know an alternative form of Lasso regression which is:
$$ \\underset{\\boldsymbol{\\beta}}{\\mathrm{argmin}} ((y\_1 - \\hat{\\beta\_1}x\_{11} -  \\hat{\\beta\_2}x\_{12})^2 + (y\_2 - \\hat{\\beta\_1}x\_{21} -  \\hat{\\beta\_2}x\_{22})^2) $$
 subject to
$$| \\hat{\\beta}\_1 | + | \\hat{\\beta}\_2 | \\le s $$

The above form says that the lasso coefficients are the ones that have
the smallest RSS out of all points that lie within the diamond defined
by $| \\hat{\\beta}\_1 | + | \\hat{\\beta}\_2 | \\le s$.

And the point with smallest RSS will be the first point at which the
contours of RSS intersects the diamond defined by
$| \\hat{\\beta}\_1 | + | \\hat{\\beta}\_2 | \\le s$.

As it is first point of intersection, it will be a point on diamond and
so, our solution is: $| \\hat{\\beta}\_1 | + | \\hat{\\beta}\_2 | = s$,
which can be furthur expanded to:
$$\\hat{\\beta}\_1 + \\hat{\\beta}\_2 = s; \\hat{\\beta}\_1 \\geq 0; \\hat{\\beta}\_2 \\geq 0$$
 and
$$\\hat{\\beta}\_1 + \\hat{\\beta}\_2 = -s; \\hat{\\beta}\_1 \\leq 0; \\hat{\\beta}\_2 \\leq 0$$

### Question 2

Here, in this exercise, we will generate simulated data and then will
use this data to perform best model selection. Firstly, we generate a
predictor X of length n=100, as well as a noise vector *ϵ* of length
n=100 such that *ϵ* = 0.1 \* rnorm()

    set.seed(19)

    #  Generating X vector
    X <- rnorm(100)

    # Generating noise vector
    noise_vec <- 0.1 * rnorm(100)

#### Part a:

Here, we want to generate Y of length n = 100 according to the model:
*Y* = *β*<sub>0</sub> + *β*<sub>1</sub>*X* + *β*<sub>2</sub>*X*<sup>2</sup> + *β*<sub>3</sub>*X*<sup>3</sup> + *ϵ*

In the question we are provided that *β*<sub>0</sub>, *β*<sub>1</sub>,
*β*<sub>2</sub> and *β*<sub>3</sub> are constants such that
*β*<sub>0</sub> = 1.0, *β*<sub>1</sub> = −0.1, *β*<sub>2</sub> = 0.05
and *β*<sub>3</sub> = 0.75

    # Setting  the coefficients
    b_0 <- 1
    b_1 <- -0.1
    b_2 <- 0.05
    b_3 <- 0.75

    # Generating the response vector Y
    Y <- b_0 + b_1*(X) + b_2*(X^2) + b_3*(X^3) + noise_vec

    # We will just have a look at the first five elements of Y to make sure things are in place
    head(Y)

    ## [1] 0.006657125 1.258462915 1.133378061 0.960502028 1.704702553 1.107916455

#### Part b:

Here, we want to use regsubsets() function to perform best subset
selection in order to choose the best model containing the predictors
*X*, *X*<sup>2</sup>,...,*X*<sup>8</sup> using the measures
*C*<sub>*p*</sub>, *B**I**C* and Adjusted *R*<sup>2</sup>.

    mod <- regsubsets(Y~poly(X,8,raw = TRUE), data = data.frame(X,Y), nvmax = 8)

    # summary of the regsubsets() gives us the best model for each number of predictor
    # and its respective characteristics including Cp, BIC, RSS, Adjusted R-squared
    reg.summary <- summary(mod)

    par(mfrow=c(2,2))

    # Finding the index for which we have minimum Cp as for determining best model, 
    # we select the one with lowest Cp
    cp_min <- which.min(reg.summary$cp)  

    # Plotting Cp vs number of predictors
    plot(reg.summary$cp, xlab="Number of Predictors", ylab="Best Subset Cp", type="l")

    # Highlighting the point for which we have minimum Cp
    points(cp_min, reg.summary$cp[cp_min], col="red", pch=16)

    # Finding the index for which we have minimum BIC as for determining the best model,
    # we select the one with lowest BIC
    bic_min <- which.min(reg.summary$bic)  

    # Plotting BIC vs number of predictors
    plot(reg.summary$bic, xlab="Number of Predictors", ylab="Best Subset BIC", type="l")

    # Highlighting the point for which we have minimum BIC
    points(bic_min, reg.summary$bic[bic_min], col="red", pch=16)

    # Finding the index for which we have maximum Adjusted R-squared as for determining 
    # the best model, we select the one with maximum Adjusted R-squared
    adjr2_max <- which.max(reg.summary$adjr2) 

    # Plotting Adjusted R-squared vs number of predictors
    plot(reg.summary$adjr2, xlab="Number of Predictors", ylab="Best Subset 
         Adjusted R^2", type="l")

    # Highlighting the point for which we have maximum adjusted R-squared
    points(adjr2_max, reg.summary$adjr2[adjr2_max], col="red", pch=16)

<img src="/img/2b-1 2.png"  />


Now that we have this, we want to know model coefficients from each of
*C*<sub>*p*</sub>, *B**I**C* and Adjusted *R*<sup>2</sup>.

    knitr::kable(coef(mod, cp_min), caption = "Coefficients for model based on Cp")

<table>
<caption>Coefficients for model based on Cp</caption>
<thead>
<tr class="header">
<th></th>
<th align="right">x</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>(Intercept)</td>
<td align="right">1.0066155</td>
</tr>
<tr class="even">
<td>poly(X, 8, raw = TRUE)1</td>
<td align="right">-0.0839368</td>
</tr>
<tr class="odd">
<td>poly(X, 8, raw = TRUE)2</td>
<td align="right">0.0576914</td>
</tr>
<tr class="even">
<td>poly(X, 8, raw = TRUE)3</td>
<td align="right">0.7496948</td>
</tr>
</tbody>
</table>

    knitr::kable(coef(mod, bic_min), caption = "Coefficients for model based on BIC")

<table>
<caption>Coefficients for model based on BIC</caption>
<thead>
<tr class="header">
<th></th>
<th align="right">x</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>(Intercept)</td>
<td align="right">1.0066155</td>
</tr>
<tr class="even">
<td>poly(X, 8, raw = TRUE)1</td>
<td align="right">-0.0839368</td>
</tr>
<tr class="odd">
<td>poly(X, 8, raw = TRUE)2</td>
<td align="right">0.0576914</td>
</tr>
<tr class="even">
<td>poly(X, 8, raw = TRUE)3</td>
<td align="right">0.7496948</td>
</tr>
</tbody>
</table>

    knitr::kable(coef(mod, adjr2_max), caption = "Coefficients for model based on Adjusted R-squared")

<table>
<caption>Coefficients for model based on Adjusted R-squared</caption>
<thead>
<tr class="header">
<th></th>
<th align="right">x</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>(Intercept)</td>
<td align="right">1.0039223</td>
</tr>
<tr class="even">
<td>poly(X, 8, raw = TRUE)1</td>
<td align="right">-0.1087415</td>
</tr>
<tr class="odd">
<td>poly(X, 8, raw = TRUE)2</td>
<td align="right">0.0618556</td>
</tr>
<tr class="even">
<td>poly(X, 8, raw = TRUE)3</td>
<td align="right">0.7696595</td>
</tr>
<tr class="odd">
<td>poly(X, 8, raw = TRUE)5</td>
<td align="right">-0.0026123</td>
</tr>
</tbody>
</table>

Based on the above table, we observe that if we select our model based
on *C*<sub>*p*</sub>, our intercept will be 1.0066, coefficient of *X*
will be -0.0839, that of *X*<sup>2</sup> will be 0.0577 and that of
*X*<sup>3</sup> will be 0.7498.

If we select our model based on *B**I**C*, our intercept will be 1.0066,
coefficient of *X* will be -0.0839, that of *X*<sup>2</sup> will be
0.0577 and that of *X*<sup>3</sup> will be 0.7498.

Finally, if we select our model based on Adjusted R-squared, our
intercept will be 1.0039, coefficient of *X* will be -0.1087, that of
*X*<sup>2</sup> will be 0.0619, that of *X*<sup>3</sup> will be 0.7697
and that of *X*<sup>5</sup> will be -0.0026.

Now, here, it may seem a bit strange to see Adjusted R-squared selecting
4 predictors. However, if we see at its plot, we can see that after you
select 3 predictors, there is not a substantial improvement in adjusted
R-squared as you add another predictor. So, we can potentially have
model with 4 predictors as well.

#### Part c:

Here, we want to fit a ridge regression model to the simulated data,
again using X, *X*<sup>2</sup>, ... , *X*<sup>8</sup> as predictors.

Firstly, we want to plot the extracted coefficients as a function of
*l**o**g*(*λ*) with a legend containing each curve color and its
predictor name in the top right corner.

Here, in the plot, the numbers on the top scale are the number of
coefficients at that weight that are not zero.

In the legend "poly(x, 8, raw = T)i" refers to *X*<sup>*i*</sup>. So,
the corresponding lines represent the coefficients of *X*<sup>*i*</sup>
for that particular value of log(lambda).

    # Getting data into a data frame
    data_final = data.frame(y = Y, x = X)

    # Now, we use model.matrix() to create x. It will generate a matrix corresponding to our 
    # 8 predictors. Also, if there are any qualitative variables, it will transform them 
    # into dummy variables as glmnet() can only take numerical, quantitative inputs
    xmat = model.matrix(y ~ poly(x, 8, raw = T), data = data_final)[, -1]

    # Applying ridge regression
    mod.ridge = glmnet(xmat, Y, alpha = 0)

    # We specify "xvar = lambda" as by default, it plots coefficients against l1 norm
    plot(mod.ridge, xvar = "lambda", label = TRUE)
    legend("topright", lwd = 1, col = 1:8, legend = colnames(xmat), cex = .5)

<img src="/img/2d3-1.png"  />

Now that we have the plot, we want to plot the cross-validation error as
a function of *l**o**g*(*λ*) to find optimal *λ*. Following that, we
also want coefficient estimates for that particular value of *λ*.

    # Setting the seed
    set.seed(20)

    # Running the cross validation model with 10 folds by default.
    mod_cv_2 = cv.glmnet(xmat, Y, alpha = 0)

    # Plotting Cross Validation model automatically plots cross-validation error as 
    # a function of log(lambda). Here, there are two lambda's indicated by vertical line. 
    # One is minimum mean cross validation error. Other one gives most regularized model 
    # such that error is within one standard error of minimum
    plot(mod_cv_2, xvar = "lambda", label = TRUE)

<img src="/img/2d4-1.png"  />


    # To find the optimal lambda, we extract the one with minimum mean cross validation error.
    mod_cv_2$lambda.min

    ## [1] 2.563188

    # Getting the coefficient estimates for optimal lambda
    x <- (predict(mod.ridge,s = mod_cv_2$lambda.min, type = "coefficients"))
    knitr::kable(as.data.frame(as.matrix(x)), caption = "Coefficient for Ridge 
                 Regression model with optimal lambda")

<table>
<caption>Coefficient for Ridge Regression model with optimal lambda</caption>
<thead>
<tr class="header">
<th></th>
<th align="right">1</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>(Intercept)</td>
<td align="right">1.0123824</td>
</tr>
<tr class="even">
<td>poly(x, 8, raw = T)1</td>
<td align="right">0.5445252</td>
</tr>
<tr class="odd">
<td>poly(x, 8, raw = T)2</td>
<td align="right">-0.0050818</td>
</tr>
<tr class="even">
<td>poly(x, 8, raw = T)3</td>
<td align="right">0.1891529</td>
</tr>
<tr class="odd">
<td>poly(x, 8, raw = T)4</td>
<td align="right">0.0031130</td>
</tr>
<tr class="even">
<td>poly(x, 8, raw = T)5</td>
<td align="right">0.0241447</td>
</tr>
<tr class="odd">
<td>poly(x, 8, raw = T)6</td>
<td align="right">0.0011441</td>
</tr>
<tr class="even">
<td>poly(x, 8, raw = T)7</td>
<td align="right">0.0023368</td>
</tr>
<tr class="odd">
<td>poly(x, 8, raw = T)8</td>
<td align="right">0.0002151</td>
</tr>
</tbody>
</table>

#### Part d:

Here, we want to fit a lasso regression model to the simulated data,
again using X, *X*<sup>2</sup>, ... , *X*<sup>8</sup> as predictors.

Firstly, we want to plot the extracted coefficients as a function of
*l**o**g*(*λ*) with a legend containing each curve color and its
predictor name in the top right corner.

Here, in the plot, the numbers on the top scale are the number of
coefficients at that weight that are not zero.

In the legend "poly(x, 8, raw = T)i" refers to *X*<sup>*i*</sup>. So,
the corresponding lines represent the coefficients of *X*<sup>*i*</sup>
for that particular value of log(lambda).

    # Getting data into a data frame
    data_final = data.frame(y = Y, x = X)

    # Now, we use model.matrix() to create x. It will generate a matrix corresponding to our
    # 8 predictors. Also, if there are any qualitative variables, it will transform them 
    # into dummy variables as glmnet() can only take numerical, quantitative inputs.
    x_mat = model.matrix(y ~ poly(x, 8, raw = T), data = data_final)[, -1]

    # Applying lasso regression
    mod.lasso = glmnet(x_mat, Y, alpha = 1)

    # We specify "xvar = lambda" as by default, it plots coefficients against l1 norm.
    plot(mod.lasso, xvar = "lambda", ylim = c(0,1), label = TRUE) 
    legend("topright", lwd = 1, col = 1:8, legend = colnames(x_mat), cex = 0.4)

<img src="/img/2d1-1.png"  />

Now that we have the plot, we want to plot the cross-validation error as
a function of *l**o**g*(*λ*) to find optimal *λ*. Following that, we
also want coefficient estimates for that particular value of *λ*.

    # Setting the seed
    set.seed(21)

    # Running the cross validation model with 10 folds by default
    mod_cv_L = cv.glmnet(xmat, Y, alpha = 1)

    # Plotting cross-validation model automatically plots cross-validation error as
    # a function of log(lambda). Here, there are two lambda's indicated by vertical line.
    # One is minimum mean cross validation  error. Other  one gives most regularized model
    # such that error is within one standard error of minimum.
    plot(mod_cv_L, xvar = "lambda", label = TRUE)

<img src="/img/2d2-1.png"  />

    # To find the optimal lambda, we extract the one with minimum mean cross validation error
    mod_cv_L$lambda.min

    ## [1] 0.02178078

    # Getting the coefficient estimates for optimal lambda
    y <- predict(mod.lasso,s = mod_cv_L$lambda.min, type = "coefficients")
    knitr::kable(as.data.frame(as.matrix(y)), caption = "Coefficient for Lasso 
                 Regression model with optimal lambda")

<table>
<caption>Coefficient for Lasso Regression model with optimal lambda</caption>
<thead>
<tr class="header">
<th></th>
<th align="right">1</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>(Intercept)</td>
<td align="right">1.0200232</td>
</tr>
<tr class="even">
<td>poly(x, 8, raw = T)1</td>
<td align="right">0.0000000</td>
</tr>
<tr class="odd">
<td>poly(x, 8, raw = T)2</td>
<td align="right">0.0433211</td>
</tr>
<tr class="even">
<td>poly(x, 8, raw = T)3</td>
<td align="right">0.7055455</td>
</tr>
<tr class="odd">
<td>poly(x, 8, raw = T)4</td>
<td align="right">0.0000000</td>
</tr>
<tr class="even">
<td>poly(x, 8, raw = T)5</td>
<td align="right">0.0036491</td>
</tr>
<tr class="odd">
<td>poly(x, 8, raw = T)6</td>
<td align="right">0.0000000</td>
</tr>
<tr class="even">
<td>poly(x, 8, raw = T)7</td>
<td align="right">0.0000000</td>
</tr>
<tr class="odd">
<td>poly(x, 8, raw = T)8</td>
<td align="right">0.0000000</td>
</tr>
</tbody>
</table>
