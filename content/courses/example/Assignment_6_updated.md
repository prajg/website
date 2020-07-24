---
date: "2019-05-05T00:00:00+01:00"
draft: false
linktitle: Assignment 5
menu:
  example:
    parent: Assignments STA314
    weight: 5
title: Assignment 5
toc: true
type: docs
weight: 5
---

### Question 1:

#### Part a:

Here, for all *x* ≤ *ξ* for the case of one knot, we want to find
*f*<sub>1</sub>(*x*)=*a*<sub>1</sub> + *b*<sub>1</sub>*x* + *c*<sub>1</sub>*x*<sup>2</sup> + *d*<sub>1</sub>*x*<sup>3</sup>
such that *f*<sub>1</sub>(*x*)=*f*(*x*).

Here,
*f*(*x*)=*β*<sub>0</sub> + *β*<sub>1</sub>*x* + *β*<sub>2</sub>*x*<sup>2</sup> + *β*<sub>3</sub>*x*<sup>3</sup> + *β*<sub>4</sub>(*x* − *ξ*)<sub>+</sub><sup>3</sup>.
Because, *x* ≤ *ξ*, we know that (*x* − *ξ*)<sub>+</sub><sup>3</sup> = 0

So, we can transform
*f*<sub>1</sub>(*x*)=*a*<sub>1</sub> + *b*<sub>1</sub>*x* + *c*<sub>1</sub>*x*<sup>2</sup> + *d*<sub>1</sub>*x*<sup>3</sup>
into
*f*(*x*)=*β*<sub>0</sub> + *β*<sub>1</sub>*x* + *β*<sub>2</sub>*x*<sup>2</sup> + *β*<sub>3</sub>*x*<sup>3</sup>
when
$$
{\\boxed{{a\_1} = {\\beta \_0},{b\_1} = {\\beta \_1},{c\_1} = {\\beta \_2},{d\_1} = {\\beta \_3}}}
$$

#### Part b

Here, we want to do the same for all *x* &gt; *ξ*,
$$
\\begin{aligned}{}
f(x) &= {\\beta \_0} + {\\beta \_1}x + {\\beta \_2}{x^2} + {\\beta \_3}{x^3} + {\\beta \_4}{(x - \\xi )^3}(\\because x &gt; \\xi)\\\\
&= {\\beta \_0} + {\\beta \_1}x + {\\beta \_2}{x^2} + {\\beta \_3}{x^3} + {\\beta \_4}({x^3} + 3{\\xi ^2}x - 3\\xi {x^2} - {\\xi ^3})\\\\
&= {\\beta \_0} + {\\beta \_1}x + {\\beta \_2}{x^2} + {\\beta \_3}{x^3} + {\\beta \_4}{x^3} + 3{\\xi ^2}{\\beta \_4}x - 3\\xi {\\beta \_4}{x^2} - {\\xi ^3}{\\beta \_4}\\\\
&= {\\beta \_0} - {\\xi ^3}{\\beta \_4} + ({\\beta \_1} + 3{\\xi ^2}{\\beta \_4})x + ({\\beta \_2} - 3\\xi {\\beta \_4}){x^2} + ({\\beta \_3} + {\\beta \_4}){x^3}
\\end{aligned}
$$
 Therefore, above equation can be written as
*f*<sub>2</sub>(*x*)=*a*<sub>2</sub> + *b*<sub>2</sub>*x* + *c*<sub>2</sub>*x*<sup>2</sup> + *d*<sub>2</sub>*x*<sup>3</sup>,
when
$$
{\\boxed{{a\_2} = {\\beta \_0} - {\\xi ^3}{\\beta \_4},{b\_2} = {\\beta \_1} + 3{\\xi ^2}{\\beta \_4},{c\_2} = {\\beta \_2} - 3\\xi {\\beta \_4},{d\_2} = {\\beta \_3} + {\\beta \_4}}}
$$

#### Part c

Here, we want to show that *f*<sub>1</sub>(*ξ*)=*f*<sub>2</sub>(*ξ*) and
therefore, f is continuous at *ξ*.

When *x* = *ξ*, we have:
$$
\\begin{aligned}{}
{f\_2}(\\xi) &= {\\beta \_0} - {\\xi ^3}{\\beta \_4} + ({\\beta \_1} + 3{\\xi ^2}{\\beta \_4})\\xi  + ({\\beta \_2} - 3\\xi {\\beta \_4}){\\xi ^2} + ({\\beta \_3} + {\\beta \_4}){\\xi ^3}\\\\
 &= {\\beta \_0} - {\\xi ^3}{\\beta \_4} + {\\beta \_1}\\xi  + 3{\\xi ^3}{\\beta \_4} + {\\beta \_2}{\\xi ^2} - 3{\\xi ^3}{\\beta \_4} + {\\beta \_3}{\\xi ^3} + {\\beta \_4}{\\xi ^3}\\\\
 &= {\\beta \_0} + {\\beta \_1}\\xi  + {\\beta \_2}{\\xi ^2} + {\\beta \_3}{\\xi ^3}\\\\
 &= {f\_1}(\\xi)
\\end{aligned}
$$

#### Part d

Here, we want to show that *f*′<sub>1</sub>(*ξ*)=*f*′<sub>2</sub>(*ξ*)
and therefore, f' is continuous at *ξ*

When *x* = *ξ*, we have:
$$
\\begin{aligned}{}
{{f'}\_1}(x) &= {\\beta \_1} + 2{\\beta \_2}x + 3{\\beta \_3}{x^2}\\\\
{{f'}\_1}(\\xi ) &= {\\boxed{{\\beta \_1} + 2{\\beta \_2}\\xi  + 3{\\beta \_3}{\\xi ^2}}}
\\end{aligned}
$$
 and similarly, we have:

$$
\\begin{aligned}{}
{{f'}\_2}(x) &= {\\beta \_1} + 3{\\xi ^2}{\\beta \_4} + 2({\\beta \_2} - 3\\xi {\\beta \_4})x + 3({\\beta \_3} + {\\beta \_4}){x^2}\\\\
 &= {\\beta \_1} + 3{\\xi ^2}{\\beta \_4} + 2{\\beta \_2}x - 6\\xi {\\beta \_4}x + 3{\\beta \_3}{x^2} + 3{\\beta \_4}{x^2}\\\\
{{f'}\_2}(\\xi ) &= {\\beta \_1} + 2{\\beta \_2}\\xi  + 3{\\beta \_4}{\\xi ^2} - 6{\\beta \_4}{\\xi ^2} + 3{\\beta \_3}{\\xi ^2} + 3{\\beta \_4}{\\xi ^2}\\\\
 &= {\\beta \_1} + 2{\\beta \_2}\\xi  + (3{\\beta \_4} - 6{\\beta \_4} + 3{\\beta \_3} + 3{\\beta \_4}){\\xi ^2}\\\\
 &= {\\boxed{{\\beta \_1} + 2{\\beta \_2}\\xi  + 3{\\beta \_3}{\\xi ^2}}}
\\end{aligned}
$$
 Therefore, *f*′<sub>1</sub>(*ξ*)=*f*′<sub>2</sub>(*ξ*).

#### Part e

Here, we want to show that *f*″<sub>1</sub>(*ξ*)=*f*″<sub>2</sub>(*ξ*)
and therefore, *f*″ is continuous at *ξ*

Taking derivatives of *f*<sub>1</sub>(*x*), we have:
$$
\\begin{aligned}{}
{f\_1}(x) &= {a\_1} + {b\_1}x + {c\_1}{x^2} + {d\_1}{x^3}\\\\
{{f'}\_1}(x) &= {b\_1} + 2{c\_1}x + 3{d\_1}{x^2}\\\\
{{f''}\_1}(x) &= 2{c\_1} + 6{d\_1}x
\\end{aligned}
$$
 By substituting *c*<sub>1</sub> = *β*<sub>2</sub>and
*d*<sub>1</sub> = *β*<sub>3</sub> into above equation with *x* = *ξ*:
$$
{{f''}\_1}(\\xi) = {\\boxed{2{\\beta \_2} + 6{\\beta \_3}\\xi}}
$$
 Similarily,
*f*″<sub>2</sub>(*x*)=2*c*<sub>2</sub> + 6*d*<sub>2</sub>*x*
 Again, by substituting
*c*<sub>2</sub> = *β*<sub>2</sub> − 3*ξ**β*<sub>4</sub> and
*d*<sub>2</sub> = *β*<sub>3</sub> + *β*<sub>4</sub> into above equation
with *x* = *ξ*, we have:
$$
\\begin{aligned}{}
{{f''}\_2}(\\xi) &= 2{\\beta \_2} - 6\\xi {\\beta \_4} + 6({\\beta \_3} + {\\beta \_4})\\xi\\\\
 &= {\\boxed{2{\\beta \_2} + 6{\\beta \_3}\\xi}}
\\end{aligned}
$$
 Therefore, we have *f*″<sub>1</sub>(*ξ*)=*f*″<sub>2</sub>(*ξ*).

### Question 2:

#### Part a:

Based on the given functions, when *λ* → ∞, $\\hat g\_2$ will have
higher order polynomial because of the order of penalty term. As a
result, it will be more flexible resulting in a smaller bias and smaller
training RSS as compared to $\\hat g\_1$.

#### Part b:

With *λ* → ∞, as $\\hat g\_2$ will have higher order polynomial because
of the order of penalty term, it may overfit the data. That will
probably result in $\\hat g\_1$ having smaller test RSS compared to
$\\hat g\_2$.

This is becuase higher order derivatives bring less information of the
function. So, there exists a certain point where the decrease in bias
cannot compensate the increase in variance. So, when *λ* → ∞, the
increase in variance using higher order of derivative is more than the
decrease in bias, therefore $\\hat g\_1$ will have smaller test RSS
comparing to $\\hat g\_2$.

#### Part c:

When *λ* = 0, both models just fit least squares irrespective of the
order of derivative used in minimizing $\\hat g$. Therefore,
$\\hat g\_1$ will have the same training and test RSS as that of
$\\hat g\_2$.

### Question 3:

#### Part a:

Classification Error: Classification error is the fraction of **training
observations** in the region that do not belong to the most common
class.

It is given by:
$$E = 1 - \\underset{\\boldsymbol{k}}{max} (\\hat{p}\_{mk}) $$

Gini Index: Gini index is the measure of total variance across all
classes.

It is given by:
$$G = \\sum\_{k = 1}^{K} \\hat{p}\_{mk} (1 - \\hat{p}\_{mk})$$

Entropy: Entropy is an alternative to Gini index and is given by:
$$D = - \\sum\_{k = 1}^{K}\\hat{p}\_{mk} log(\\hat{p}\_{mk})$$

#### Part b:

Here, we want to plot the above three measures

    p1 <- seq(0 + 1e-06, 1 - 1e-06, length.out = 100)
    p2 <- 1 - p1

    # error-rate:
    E <- 1 - apply(rbind(p1, p2), 2, max) # here, 2 indicates to apply the function to columns

    # Gini index:
    G <- p1 * (1 - p1) + p2 * (1 - p2)

    # entropy:
    D <- -(p1 * log(p1) + p2 * log(p2))

    plot(p1, E, type = "l", col = "black", xlab = "prob of class 1", ylab = 
           "value of measure", ylim = c(min(c(E, G, D)), max(E, G, D)))
    lines(p1, G, col = "blue")
    lines(p1, D, col = "green")
    legend("topright", c("Classification error", "Gini index", "entropy"), col = 
             c("black", "blue", "green"), lty = c(1, 1), cex  = 0.5)

<img src="/img/3b-1.png"  />

### Question 4:

We are provided 10 estimates of P(Class is red|X) which are:
0.1,0.15,0.2,0.2,0.55,0.6,0.6,0.65,0.7,0.75

So, the respective estimates of P(Class is green|X) will be:
0.9,0.85,0.8,0.8,0.45,0.4,0.4,0.35,0.3,0.25

#### Majority vote approach:

Here, we see that 6 out of 10 observations have P(Class is red|X) &gt;
P(Class is green|X) i.e., P(Class is red|X) &gt; 0.5. So, the
classification would be **Red**.

#### Average probability approach:

Based on these 10 estimates, ${\\hat{P}(R|X)}$ = mean of the estimates
of P(Class is red|X). So, ${\\hat{P}(R|X)} = 0.45$ . Therefore,
${\\hat{P}(G|X)} = 0.55$

So, the classification would be **Green**.
