---
date: "2019-05-05T00:00:00+01:00"
draft: false
linktitle: A2_314
menu:
  example:
    parent: Assignments STA314
    weight: 2
title: Assignment 2
toc: true
type: docs
weight: 2
---

Question 1:
-----------

### Part a: Write down what is P(X|Dividend = Yes).

P(X|Dividend = Yes), based on the question, follows a normal
distribution with mean = 10 and variance = 36.

So, it's density would look like:
$$
\\begin{aligned}
  f(x) &= \\frac{1}{\\sqrt{2\\pi\\sigma^2}}exp(-\\frac{(x - \\mu)^2}{{2\\sigma^2}}) \\\\
      &= \\frac{1}{\\sqrt{2\\pi\\times 36}}exp(-\\frac{1}{{2\\sigma^2}}(x - 10)^2)
\\end{aligned}
$$

### Part b: Write down what is P(X|Dividend = No).

P(X|Dividend = No), based on the question, also follows a normal
distribution with mean = 0 and variance = 36.

So, it's density would look like:
$$
\\begin{aligned}
  f(x) &= \\frac{1}{\\sqrt{2\\pi\\sigma^2}}exp(-\\frac{(x - \\mu)^2}{{2\\sigma^2}}) \\\\
      &= \\frac{1}{\\sqrt{2\\pi\\times 36}}exp(-\\frac{x^2}{{2\\sigma^2}})
\\end{aligned}
$$

### Part c: Use dnorm() to calculate conditional probabilities in a) and b) when X=4.

Here, we will firstly calculate conditional probability for part(a) when
X=4.

    dnorm(4, mean = 10, sd = 6, log = FALSE)

    ## [1] 0.04032845

Based on this, we see that the conditional probability in (a) when X=4
is **0.04032845**. Now, we will be calculating conditional probability
for part(b) when X=4.

    dnorm(4, mean = 0, sd = 6, log = FALSE)

    ## [1] 0.05324133

Based on this, we see that the conditional probability in (b) when X=4
is **0.05324133**.

### Part d: What is the value of P(Dividend = Yes)

Based on the question, we are given that 80% of the companies issue
dividends. So, P(Dividend = Yes) = 0.8

### Part e: Write down what is P(X|Dividend = No).

Based on the question, we know that 20% of the companies do not issue
dividends. So, P(Dividend = No) = 0.2

### Part f: Predict the probability that a company will issue a dividend this year given its percentage profit was X = 4.

Based on part (c), (d) and (e), we will predict the probability that a
company will issue a dividend this year given its percentage profit was
X = 4. To do this, we will be using Bayes' rule. Based on that, we get
probability = 0.752.

$$
\\begin{aligned}
  p\_{yes}(x) &= \\frac{\\pi\_{yes}exp(-\\frac{(x - \\mu\_{yes})^2}{{2\\sigma^2}})}{\\pi\_{yes}exp(-\\frac{(x - \\mu\_{yes})^2}{{2\\sigma^2}}) + \\pi\_{no}exp(-\\frac{(x - \\mu\_{no})^2}{{2\\sigma^2}})} \\\\
      &= \\frac{0.8 \\times 0.04032845}{0.8 \\times 0.04032845 + 0.2 \\times 0.05324133}\\\\
      &= 0.752
\\end{aligned}
$$

Question 2:
-----------

### Part a:

Here, we want to create a binary variable, mpg01, that contains a 1 if
mpg contains a value above its median, and a 0 if mpg contains a value
below its median.

    # Check the first five entries of the dataset to see if the dataset is loaded properly
    knitr::kable(head(Auto)) 

<table>
<thead>
<tr class="header">
<th align="right">mpg</th>
<th align="right">cylinders</th>
<th align="right">displacement</th>
<th align="right">horsepower</th>
<th align="right">weight</th>
<th align="right">acceleration</th>
<th align="right">year</th>
<th align="right">origin</th>
<th align="left">name</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="right">18</td>
<td align="right">8</td>
<td align="right">307</td>
<td align="right">130</td>
<td align="right">3504</td>
<td align="right">12.0</td>
<td align="right">70</td>
<td align="right">1</td>
<td align="left">chevrolet chevelle malibu</td>
</tr>
<tr class="even">
<td align="right">15</td>
<td align="right">8</td>
<td align="right">350</td>
<td align="right">165</td>
<td align="right">3693</td>
<td align="right">11.5</td>
<td align="right">70</td>
<td align="right">1</td>
<td align="left">buick skylark 320</td>
</tr>
<tr class="odd">
<td align="right">18</td>
<td align="right">8</td>
<td align="right">318</td>
<td align="right">150</td>
<td align="right">3436</td>
<td align="right">11.0</td>
<td align="right">70</td>
<td align="right">1</td>
<td align="left">plymouth satellite</td>
</tr>
<tr class="even">
<td align="right">16</td>
<td align="right">8</td>
<td align="right">304</td>
<td align="right">150</td>
<td align="right">3433</td>
<td align="right">12.0</td>
<td align="right">70</td>
<td align="right">1</td>
<td align="left">amc rebel sst</td>
</tr>
<tr class="odd">
<td align="right">17</td>
<td align="right">8</td>
<td align="right">302</td>
<td align="right">140</td>
<td align="right">3449</td>
<td align="right">10.5</td>
<td align="right">70</td>
<td align="right">1</td>
<td align="left">ford torino</td>
</tr>
<tr class="even">
<td align="right">15</td>
<td align="right">8</td>
<td align="right">429</td>
<td align="right">198</td>
<td align="right">4341</td>
<td align="right">10.0</td>
<td align="right">70</td>
<td align="right">1</td>
<td align="left">ford galaxie 500</td>
</tr>
</tbody>
</table>

    # Creating a variable "mpg01" whose value is 1 if the corresponding mpg value is greater
    # than median mpg value and 0 if less than the median 
    mpg01 <- rep(0, length(Auto$mpg))
    mpg01[Auto$mpg > median(Auto$mpg)] <- 1

    # Merging the "mpg01" variable with other variables in the Auto dataset
    Auto <- data.frame(Auto, mpg01)

### Part b:

Here, we want to see which continuous features seem most likely to be
useful in predicting the mpg. We are provided in the question that we
should use cor() function here and consider features with correlation
coefficient greater than 0.6 in predicting.

    # Because we can use cor() function only on numeric values, we remove the 9th column, 
    # which is the "Names" of the vehicles/cars
    A <- cor(Auto[,-9])
    A

    ##                     mpg  cylinders displacement horsepower     weight
    ## mpg           1.0000000 -0.7776175   -0.8051269 -0.7784268 -0.8322442
    ## cylinders    -0.7776175  1.0000000    0.9508233  0.8429834  0.8975273
    ## displacement -0.8051269  0.9508233    1.0000000  0.8972570  0.9329944
    ## horsepower   -0.7784268  0.8429834    0.8972570  1.0000000  0.8645377
    ## weight       -0.8322442  0.8975273    0.9329944  0.8645377  1.0000000
    ## acceleration  0.4233285 -0.5046834   -0.5438005 -0.6891955 -0.4168392
    ## year          0.5805410 -0.3456474   -0.3698552 -0.4163615 -0.3091199
    ## origin        0.5652088 -0.5689316   -0.6145351 -0.4551715 -0.5850054
    ## mpg01         0.8369392 -0.7591939   -0.7534766 -0.6670526 -0.7577566
    ##              acceleration       year     origin      mpg01
    ## mpg             0.4233285  0.5805410  0.5652088  0.8369392
    ## cylinders      -0.5046834 -0.3456474 -0.5689316 -0.7591939
    ## displacement   -0.5438005 -0.3698552 -0.6145351 -0.7534766
    ## horsepower     -0.6891955 -0.4163615 -0.4551715 -0.6670526
    ## weight         -0.4168392 -0.3091199 -0.5850054 -0.7577566
    ## acceleration    1.0000000  0.2903161  0.2127458  0.3468215
    ## year            0.2903161  1.0000000  0.1815277  0.4299042
    ## origin          0.2127458  0.1815277  1.0000000  0.5136984
    ## mpg01           0.3468215  0.4299042  0.5136984  1.0000000

    library(corrplot)
    corrplot(A, type="full", method = "color")

<img src="/img/2b-1.png" alt="Correlation plot"  />
<p class="caption">
Correlation plot
</p>

Based on the correlation table and the figure, we can say that
"cylinders", "displacement", "horsepower" and "weight" are four features
that we will be using for prediction as their absolute correlation
coefficient is greater than 0.6.

Just to confirm the impact of the features above, we plot individual box
plots which confirm the same.

    par(mfrow=c(2,2))
    boxplot(Auto$cylinders ~ Auto$mpg01, main = "Cylinders vs mpg01")
    boxplot(Auto$displacement ~ Auto$mpg01, main = "Displacement vs mpg01")
    boxplot(Auto$horsepower ~ Auto$mpg01, main = "Horsepower vs mpg01")
    boxplot(Auto$weight ~ Auto$mpg01, main = "Weight vs mpg01")

<img src="/img/2bs-1.png" alt="Box-plots of features to be used in prediction" /> 
<p class="caption">
Box-plots of features to be used in prediction
</p>


### Part c:

Here, we want to split the data into training and test set, holding 30%
for the test set. So, for that, we use the sample.split function and
then store them in Auto.train and Auto.test respectively.

    set.seed(101)
    temp  <- sample.split(Auto, SplitRatio = 0.7)
    Auto.train <- Auto[temp,]
    Auto.test <- Auto[!temp,]

### Part d:

Here, we want to perform LDA using the variables that seemed most
associated in part b and then want to find the test error.

    set.seed(101)
    # Fitting the LDA model
    mod_lda <- lda(mpg01 ~ cylinders + weight + displacement + horsepower, data = Auto.train)
    mod_lda

    ## Call:
    ## lda(mpg01 ~ cylinders + weight + displacement + horsepower, data = Auto.train)
    ## 
    ## Prior probabilities of groups:
    ##         0         1 
    ## 0.4981818 0.5018182 
    ## 
    ## Group means:
    ##   cylinders   weight displacement horsepower
    ## 0  6.678832 3605.263     269.2482  129.30657
    ## 1  4.224638 2357.543     118.4312   79.65217
    ## 
    ## Coefficients of linear discriminants:
    ##                       LD1
    ## cylinders    -0.289911365
    ## weight       -0.001216868
    ## displacement -0.002048940
    ## horsepower    0.004664771

    # Predicting based on the fitted LDA model
    pred.lda <- predict(mod_lda, Auto.test)

    # Generating the confusion matrix to check the error rate.
    table(pred.lda$class, Auto.test[,"mpg01"])

    ##    
    ##      0  1
    ##   0 51  1
    ##   1  8 57

    mean(pred.lda$class != Auto.test[,"mpg01"])

    ## [1] 0.07692308

Based on this, we can say that the test error is **7.69%** in the case
of using LDA on features selected in part b.

### Part e:

Here, we want to perform QDA using the variables that seemed most
associated in part b and then want to find the test error.

    set.seed(101)
    # Fitting the LDA model
    mod_qda <- qda(mpg01 ~ cylinders + weight + displacement + horsepower, data = Auto.train)
    mod_qda

    ## Call:
    ## qda(mpg01 ~ cylinders + weight + displacement + horsepower, data = Auto.train)
    ## 
    ## Prior probabilities of groups:
    ##         0         1 
    ## 0.4981818 0.5018182 
    ## 
    ## Group means:
    ##   cylinders   weight displacement horsepower
    ## 0  6.678832 3605.263     269.2482  129.30657
    ## 1  4.224638 2357.543     118.4312   79.65217

    # Predicting based on the fitted LDA model
    pred.qda <- predict(mod_qda, Auto.test)

    # Generating the confusion matrix to check the error rate.
    table(pred.qda$class, Auto.test[,"mpg01"])

    ##    
    ##      0  1
    ##   0 54  1
    ##   1  5 57

    mean(pred.qda$class != Auto.test[,"mpg01"])

    ## [1] 0.05128205

Based on this, we can say that the test error is **5.12%** in the case
of using QDA on features selected in part b.

### Part f:

    set.seed(101)
    glm_mod <- glm(mpg01 ~ cylinders + weight + displacement + horsepower, 
                   data = Auto.train, family = binomial)
    summary(glm_mod)

    ## 
    ## Call:
    ## glm(formula = mpg01 ~ cylinders + weight + displacement + horsepower, 
    ##     family = binomial, data = Auto.train)
    ## 
    ## Deviance Residuals: 
    ##     Min       1Q   Median       3Q      Max  
    ## -2.3047  -0.2763   0.1173   0.3913   3.1478  
    ## 
    ## Coefficients:
    ##                Estimate Std. Error z value Pr(>|z|)    
    ## (Intercept)  10.6027057  1.8659851   5.682 1.33e-08 ***
    ## cylinders     0.2606786  0.3991895   0.653  0.51374    
    ## weight       -0.0020693  0.0007444  -2.780  0.00544 ** 
    ## displacement -0.0136283  0.0092348  -1.476  0.14001    
    ## horsepower   -0.0383627  0.0156556  -2.450  0.01427 *  
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## (Dispersion parameter for binomial family taken to be 1)
    ## 
    ##     Null deviance: 381.23  on 274  degrees of freedom
    ## Residual deviance: 162.40  on 270  degrees of freedom
    ## AIC: 172.4
    ## 
    ## Number of Fisher Scoring iterations: 7

    set.seed(101)
    # getting the predicted probabilities
    probs <- predict(glm_mod, Auto.test, type = "response") 

    # creating the confusion matrix
    pred.glm <- rep(0, length(probs))
    pred.glm[probs > 0.5] <- 1
    table(pred.glm, Auto.test$mpg01)

    ##         
    ## pred.glm  0  1
    ##        0 53  2
    ##        1  6 56

    mean(pred.glm != Auto.test$mpg01)

    ## [1] 0.06837607

Based on this, we can say that the test error is **6.84%** in the case
of using Logistic Regression on features selected in part b.

    set.seed(101)
    library(class)
    train.X = cbind(Auto.train$cylinders, Auto.train$weight, 
                    Auto.train$displacement, Auto.train$horsepower)
    test.X = cbind(Auto.test$cylinders, Auto.test$weight, 
                   Auto.test$displacement, Auto.test$horsepower)
    train.Y = Auto.train$mpg01
    test.Y = Auto.test$mpg01
    knn_test_error = c();
    for ( i in 1:200 ) {
      knn.pred = knn(train.X, test.X, train.Y, k = i)
      knn_test_error[i] = mean(knn.pred != test.Y)*100
    }
    plot(1:200, knn_test_error, xlab = "K", ylab = "Test Error Rate (%)")

<img src="/img/2g-1.png" /> 


    df <- data.frame(matrix(ncol = 2, nrow = 10))
    x <- c("K", "Error")
    colnames(df) <- x

    temp_vec <- c(1,5,10,15,20,30,50,100,150,200)
    for(i in 1:10){
       df[i,1] <- temp_vec[i]
    }

    for(j in 1:10){
      df[j,2] <- knn_test_error[temp_vec[j]]
    }

    knitr::kable(df, digits = 3)

<table>
<thead>
<tr class="header">
<th align="right">K</th>
<th align="right">Error</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="right">1</td>
<td align="right">11.111</td>
</tr>
<tr class="even">
<td align="right">5</td>
<td align="right">9.402</td>
</tr>
<tr class="odd">
<td align="right">10</td>
<td align="right">10.256</td>
</tr>
<tr class="even">
<td align="right">15</td>
<td align="right">10.256</td>
</tr>
<tr class="odd">
<td align="right">20</td>
<td align="right">10.256</td>
</tr>
<tr class="even">
<td align="right">30</td>
<td align="right">8.547</td>
</tr>
<tr class="odd">
<td align="right">50</td>
<td align="right">9.402</td>
</tr>
<tr class="even">
<td align="right">100</td>
<td align="right">9.402</td>
</tr>
<tr class="odd">
<td align="right">150</td>
<td align="right">9.402</td>
</tr>
<tr class="even">
<td align="right">200</td>
<td align="right">11.966</td>
</tr>
</tbody>
</table>

    which.min(knn_test_error)

    ## [1] 7

    min(knn_test_error)

    ## [1] 7.692308

So, from the values provided in question, based on the above table, we
see that KNN performs best for K=30 with test error rate of **8.547%**.

However, if we take all values from 1 to 200, when K = 7, KNN classifier
performs the best with the test error rate = **7.69%**.
