---
date: "2019-05-05T00:00:00+01:00"
draft: false
linktitle: Assignment 4
menu:
  example:
    parent: Example Topic
    weight: 4
title: Example Page 1
toc: true
type: docs
weight: 4
---

### Question 1

Here, *y*<sub>1</sub>, *y*<sub>2</sub>, …, *y*<sub>*n*</sub> is a random
sample from a Bernoulli distribution where *Y* ∼ *B**e**r**n*(*p*) with
pmf of Y:
*f*(*y*<sub>*i*</sub>|*p*)=*p*<sup>*y*<sub>*i*</sub></sup>(1 − *p*)<sup>1 − *y*<sub>*i*</sub></sup>; *y*<sub>*i*</sub> ∈ {0, 1; 1 = *s**u**c**c**e**s**s*}

#### Part a:

Here, we want to find the MLE of p. So, here, the likelihood function
is:
$$ L(p) = \\prod\_{i = 1}^{n} p^{y\_i} (1-p)^{1-y\_i} $$
 So, from this, log-likelihood is:
$$ l(p) = \\log{p} \\sum\_{i = 1}^{n} y\_i + \\log{(1-p)} \\sum\_{i = 1}^{n} (1 - y\_i) $$
 Now, to find the MLE of p, we set the first derivative of *l*(*p*) to
be zero and double check to make sure that the second derivative is
negative.

If we set the first derivative to be zero, we have:
$$ \\frac{dl(p)}{dp} = \\frac{\\sum\_{i = 1}^{n} y\_i}{p}  - \\frac{\\sum\_{i = 1}^{n} (1 - y\_i)}{(1-p)} = 0$$
$$ \\therefore \\sum\_{i = 1}^{n} y\_i - p \\sum\_{i = 1}^{n} y\_i = p \\sum\_{i = 1}^{n} (1-y\_i)$$
$$ \\therefore \\hat{p} = \\frac{\\sum\_{i = 1}^{n} y\_i}{n}$$
 Now, to make sure that this is the maximum likelihood estimator, we
double check that the second derivative is negative.
$$ \\displaystyle \\frac{d^2l(p)}{dp^2}  = - \\frac {\\sum\_{i = 1}^{n} y\_i}{p^2} - \\frac{\\sum\_{i = 1}^{n} (1-y\_i)}{(1-p)^2}$$
 Now, here, *p* ∈ \[0, 1\] and *y* ∈ {0, 1}. Therefore, the second
derivative is negative as both the terms will be negative.

#### Part b:

Here, we are given that in five independent Bernoulli trials from above
Bernoulli process, three successes and two failures were observed.
Calculate the maximum likelihood estimates of p in this situation.

From part a, we know that
$\\hat{p} = \\frac{\\sum\_{i = 1}^{n} y\_i}{n}$.

Here, because we had 3 successes and 2 failures,
$\\sum\_{i = 1}^{n} y\_i = 3$ as in the question, we are given that
1 = *s**u**c**c**e**s**s* and 0 = *f**a**i**l**u**r**e*. Also, because
there are 5 trials, we have *n* = 5.

$$ \\therefore \\hat{p} = \\frac{\\sum\_{i = 1}^{n} y\_i}{n} = \\frac{3}{5}$$
.

#### Part c:

Here, we want to plot the log-likelihood for the data in part(b) by
performing a grid search over a set of possible values of p parameter.
Then, we want to add a vertical line to the plot at the value of p that
maximizes the log-likelihood.

Firstly, we will be creating a log-likelihood function. Then, we define
the possible set of values our parameter *p* can take. Once we have
that, we will find the loglikelihood for all possible parameter values
and then find *p* for which it is the largest.

While doing all of this, we will plot the log-likelihood function and
then add a vertical line to the plot at the value of *p* that maximizes
the log-likelihood.

    # Defining the log-likelihood function
    log_lik_func <- function(x, p = 3, n = 5) { p*log(x) + (n-p)*log(1-x)}

    # Values our parameter can take
    param_values <- seq(0,1, by = 0.2) 

    # Finding log-likelihood for all possible values of parameter
    val <- sapply(param_values , log_lik_func)
    val

    ## [1]      -Inf -5.274601 -3.770523 -3.365058 -3.888306      -Inf

    # Parameter value for which we have maximum log-likelihood
    param_values[which.max(val)]

    ## [1] 0.6

    # plot of log-likelihood
    curve(log_lik_func, from = 0, to = 1)
    points(param_values, val, col = 'blue', pch = 20) 
    points(param_values[which.max(val)], val[which.max(val)], col = 'red', pch = 19) 
    abline(v = param_values[which.max(val)], col = 'red')

<img src="Assignment_4_updated_files/figure-markdown_strict/1c-1.png" style="display: block; margin: auto;" />

### Question 2:

Here, we have a case of simple logistic regression where Y is a binary
dependent variable and X is the predictor variable with sample data
(*x*<sub>1</sub>, *y*<sub>1</sub>),(*x*<sub>2</sub>, *y*<sub>2</sub>),…,(*x*<sub>*n*</sub>, *y*<sub>*n*</sub>).
Binary outcomes are modelled as Bernoulli trials as in Question 1 above.
Moreover,
*f*(*y*<sub>*i*</sub>|*p*<sub>*i*</sub>)=*p*<sub>*i*</sub><sup>*y*<sub>*i*</sub></sup>(1 − *p*<sub>*i*</sub>)<sup>1 − *y*<sub>*i*</sub></sup>; *y*<sub>*i*</sub> ∈ {0, 1; 1 = *Y**e**s*}
$$ p\_i = \\frac{e^{{\\beta\_0}+{\\beta\_1x\_i}}}{1+e^{{\\beta\_0}+{\\beta\_1x\_i}}} $$

#### Part a:

Here, we want to derive the log-likelihood function *l*(*β*), where
*β* = (*β*<sub>0</sub>, *β*<sub>1</sub>).

So, here, firstly our likelihood function is as follows:
$$ L(\\beta) = \\prod\_{i=1}^{n}p\_i^{y\_i} (1-p\_i)^{1-y\_i}  $$
 So, from this, our log-likelihood function is as follows:
$$
\\begin{aligned}
  l(\\beta\_0,\\beta\_1) &= \\sum\_{i=1}^{n} y\_i \\log(p\_i) +  \\sum\_{i=1}^{n} (1-y\_i) \\log(1 - p\_i)  \\\\
      &= \\sum\_{i=1}^{n} \\log(1-p\_i) +  \\sum\_{i=1}^{n} y\_i \\log\\frac{p\_i}{(1 - p\_i)} \\\\
      &= \\sum\_{i=1}^{n} \\log(1-p\_i) +  \\sum\_{i=1}^{n} y\_i (\\beta\_0 + \\beta\_1 x\_i) \\\\
      &= \\sum\_{i=1}^{n} \\log(1-(\\frac{e^{{\\beta\_0}+{\\beta\_1x\_i}}}{1+e^{{\\beta\_0}+{\\beta\_1x\_i}}})) +  \\sum\_{i=1}^{n} y\_i (\\beta\_0 + \\beta\_1 x\_i) \\\\
      &= \\sum\_{i=1}^{n} \\log(\\frac{1}{1+e^{{\\beta\_0}+{\\beta\_1x\_i}}}) +  \\sum\_{i=1}^{n} y\_i (\\beta\_0 + \\beta\_1 x\_i) \\\\
      &= \\sum\_{i=1}^{n} \\log{1} - \\log{(1+e^{{\\beta\_0}+{\\beta\_1x\_i}}}) +  \\sum\_{i=1}^{n} y\_i (\\beta\_0 + \\beta\_1 x\_i) \\\\
\\end{aligned}
$$

Now, log1 = 0. So, our log-likelihood function is:
$$ l(\\beta\_0,\\beta\_1) = -\\sum\_{i=1}^{n}\\log{(1+e^{{\\beta\_0}+{\\beta\_1x\_i}}}) +  \\sum\_{i=1}^{n} y\_i (\\beta\_0 + \\beta\_1 x\_i) $$

#### Part b:

Here, we want to write function ll() which calculates the
log-likelihood. For this, we will be using our result from part a.

Here, in the output, we add a negative sign to the function we get from
part a. This is because we will be using this function in optim()
function. Now, optim() minimizes the function by default. But we want
parameters that maximize it.

So, we will be returning "-log-likelihood" which on minimizing will give
the values of parameter which maximize log-likelihood.

    ll <- function(x, y, beta) {
      # parameter 1
      b_0 = beta[1]
      
      # parameter 2
      b_1 = beta[2]
      
      n = length(x)
      t <- replicate(length(x), 0)
      t2 <- replicate(length(x), 0)
      
      # term 1 from the log-likelihood function from part a:
      term_1 = 0
      
      # term 2 from the log-likelihood function from part a:
      term_2 = 0
      
        for(i in 1:n){
          t[i] = -log(1 + exp(b_0 + ((b_1)*x[i])))
          term_1 = term_1 + t[i]
          t2[i] = y[i]*(b_0 + (b_1*x[i]))
          term_2 = term_2 + t2[i]
        }
      
      # This is our log-likelihood function
      log_likelihood <- (term_1 + term_2)
      
      # Later, we will be using this function in optim() function. Now, optim() minimizes the 
      # function by default. So, we will be returning "-log-likelihood" which on minimizing  
      # will give the values of parameter which maximize log-likelihood
      -(term_1 + term_2)
      
    }

#### Part c:

Here, using the default dataset in the book, we want to fit a logistic
regression model to predict default given balance as a predictor using
glm().

    # model generation
    glm_mod <- glm(default ~ balance, data = Default, family = binomial)
    summary(glm_mod)

    ## 
    ## Call:
    ## glm(formula = default ~ balance, family = binomial, data = Default)
    ## 
    ## Deviance Residuals: 
    ##     Min       1Q   Median       3Q      Max  
    ## -2.2697  -0.1465  -0.0589  -0.0221   3.7589  
    ## 
    ## Coefficients:
    ##               Estimate Std. Error z value Pr(>|z|)    
    ## (Intercept) -1.065e+01  3.612e-01  -29.49   <2e-16 ***
    ## balance      5.499e-03  2.204e-04   24.95   <2e-16 ***
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## (Dispersion parameter for binomial family taken to be 1)
    ## 
    ##     Null deviance: 2920.6  on 9999  degrees of freedom
    ## Residual deviance: 1596.5  on 9998  degrees of freedom
    ## AIC: 1600.5
    ## 
    ## Number of Fisher Scoring iterations: 8

#### Part d:

Here, we want to use optim() function together with ll() and initial
parameter estimates as zero to calculate maximum likelihood estimates of
regression coefficients in part c.

In our data, the response variable "default" is of datatype factor. As a
result, we will first convert that to 0's and 1's with 1 being default
and 0 being non-default.

Following that, we will convert this to a vector as manipulating factors
is a bit tricky.

Finally, we use optim function to find the parameter values which
maximize log-likelihood function starting from (0,0) as the parameter
values. By default, optim function minimizes the function but we wanted
to find parameter values which maximize the log-likelihood. As a result,
we earlier added a negative sign in the output of log-likelihood so that
the result given by optim function fits our requirement.

    # Convert factor levels to 0 and 1
    output_default <- Default$default
    levels(output_default)[1]<-"0"
    levels(output_default)[2]<-"1"

    # Change to a vector
    output_default <- as.numeric(as.character(output_default))

    # Using optim function on log-likelihood to find parameters, starting from (0,0)
    optim(c(0,0), ll,x = Default$balance, y = output_default)

    ## $par
    ## [1] -10.652058220   0.005499188
    ## 
    ## $value
    ## [1] 798.2259
    ## 
    ## $counts
    ## function gradient 
    ##      107       NA 
    ## 
    ## $convergence
    ## [1] 0
    ## 
    ## $message
    ## NULL

#### Part e:

Based on our outputs from part (c) and part (d), we can say that maximum
likelihood estimates obtained using optim() function are very similar to
the ones obtained using glm() function.

#### Part f:

Here, we want to calculate the standard errors of our estimates. As
provided in the question, we can include parameter option 'hessian =
TRUE' in the function optim() when we call the function optim() in part
d.

But here, , we see that if we invert the Hessian matrix using the
default method in optim, we get negative numbers on the diagonal. So,
taking their square roots will not be possible.

As a result, we will use Quasi Newton method, specifically the 'BFGS'
method as those methods are used when Hessian is unavailable.

    Hessian_mat <- optim(c(0,0), ll,x = Default$balance, y = output_default, hessian = TRUE, 
                           method = 'BFGS')$hessian

    # Now, we find the inverse of this and then we take the square root of the diagonal.
    std_err_est <- sqrt(diag(solve(Hessian_mat)))
    std_err_est

    ## [1] 0.3378529809 0.0002296589

#### Part g:

Bases on the outputs we have from part (c) and (f), we can say that
standard errors of the MLE obtained using optim() and glm() are very
similar.

### Question 3

#### Part a:

Here, using the summary and glm functions, we want to determine the
estimated standard errors for the coefficients associated with income
and balance in a multiple logistic regression model.

    set.seed(100)
    fit1 <- glm(default ~ income + balance, data=Default, family=binomial)
    summary(fit1)

    ## 
    ## Call:
    ## glm(formula = default ~ income + balance, family = binomial, 
    ##     data = Default)
    ## 
    ## Deviance Residuals: 
    ##     Min       1Q   Median       3Q      Max  
    ## -2.4725  -0.1444  -0.0574  -0.0211   3.7245  
    ## 
    ## Coefficients:
    ##               Estimate Std. Error z value Pr(>|z|)    
    ## (Intercept) -1.154e+01  4.348e-01 -26.545  < 2e-16 ***
    ## income       2.081e-05  4.985e-06   4.174 2.99e-05 ***
    ## balance      5.647e-03  2.274e-04  24.836  < 2e-16 ***
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## (Dispersion parameter for binomial family taken to be 1)
    ## 
    ##     Null deviance: 2920.6  on 9999  degrees of freedom
    ## Residual deviance: 1579.0  on 9997  degrees of freedom
    ## AIC: 1585
    ## 
    ## Number of Fisher Scoring iterations: 8

    sum_coef <- rbind(summary(fit1)$coef[1:3,1:2])
    knitr::kable(sum_coef, caption = "Estimate and Standard Error of the model")

<table>
<caption>Estimate and Standard Error of the model</caption>
<thead>
<tr class="header">
<th></th>
<th align="right">Estimate</th>
<th align="right">Std. Error</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>(Intercept)</td>
<td align="right">-11.5404684</td>
<td align="right">0.4347564</td>
</tr>
<tr class="even">
<td>income</td>
<td align="right">0.0000208</td>
<td align="right">0.0000050</td>
</tr>
<tr class="odd">
<td>balance</td>
<td align="right">0.0056471</td>
<td align="right">0.0002274</td>
</tr>
</tbody>
</table>

Therefore, the estimated standard errors for *β*<sub>0</sub> is
**4.347564e-01**, for *β*<sub>1</sub>, which is the coefficient
associated with income, is **4.985167e-06** and that for
*β*<sub>2</sub>, which is the coefficient associated with balance, is
**2.273731e-04**

#### Part b:

Here, we want to write a function that takes as input the Default data
set as well as index of observations and then outputs the coefficient
estimates for income and balance in the multiple logistic regression
model.

    set.seed(100)
    boot.fn <- function(data_set, index){
      fit2 <- glm(default ~ income + balance, data=data_set, subset = index, family=binomial)
      return(coef(fit2))
    }

#### Part c:

Here, we want to use the boot() function together with our boot.fn() to
estimate the standard errors of the logistic regression coefficients for
income and balance.

For R = 1000 replications

    par(mfrow = c(3,2))
    set.seed(100)
    results <- boot(Default, boot.fn, 1000)
    results

    ## 
    ## ORDINARY NONPARAMETRIC BOOTSTRAP
    ## 
    ## 
    ## Call:
    ## boot(data = Default, statistic = boot.fn, R = 1000)
    ## 
    ## 
    ## Bootstrap Statistics :
    ##          original        bias     std. error
    ## t1* -1.154047e+01 -2.927307e-02 4.446538e-01
    ## t2*  2.080898e-05 -3.481513e-08 4.916633e-06
    ## t3*  5.647103e-03  1.665079e-05 2.318937e-04

So, here, standard error for *β*<sub>0</sub> is **4.276469e-01**, for
*β*<sub>1</sub>, which is the coefficient associated with income, is
**4.890019e-06** and that for *β*<sub>2</sub>, which is the coefficient
associated with balance, is **2.250900e-04**

#### Part d:

Here, we want to comment on the estimated standard errors obtained using
the glm() function and using bootstrap function.

So, based on the results we have, the estimated standard errors obtained
by the two methods are pretty close.
