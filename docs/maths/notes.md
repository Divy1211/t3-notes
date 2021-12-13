# Notes

## Definitions
**Probability**: Mathematical method to quantify the chance of something happening by using a # b/n 0-1.

**Statistics**: sci of collecting, analysing and interpreting data in order to extract meaningful info and conclusions

**Population**: collection of all individual items of a particular type

**Sample**: a sub collection of pop chosen by some rule

## Types of statistical studies
1. Comparitive (b/n >= 2 grps), non comparitive (learn more about 1 grp)
2. Observational (no intervention) vs Experimental (control)

**Sampling errors**: every survey suffers from errors called sampling errors because it can't be done over the full pop. (eg. selection bias)

**Systematic errorss**: zero error etc.

**Random errors**: single event effects

## Types of data
1. Categorical (qualitative): repr-ed with freq. tables, bar graphs

    1.1 Nominal (fav. colour: red, green, blue, no ranking)

    1.2 Ordinal (disagree, neutral, agree, ranked)

2. Numerical (quantitative): histograms

    2.1 Discrete (numbers, counting things, ints)

    2.2 Continuous (measurements taken over time, speed, etc.)

## Measures of Centre, Central Tendency

1. Mean $\bar{x}$ (not robust, sensitive to small/large vals)
2. Median $\tilde{x}$ (robust, not sensitive to small/large vals)
3. Mode - Unimodal, Bimodal.

Symmetric unimodal graph => mean, median and mode are all coincident

Skewed bimodal graph => if the tail of the graph is to left, skewed left, if tial to right, skewed right. (skew is opp of peak!)

## Measures of spread

Units are important when calc-ing these.

Variance $\sigma^2 = S^2_x = \cfrac{1}{n-1} \sum\limits_{i=1}^n (x_i - \bar{x})^2$ (unit^2)

Standard deviation $\sigma = \sqrt{S^2_x}$ (unit) (not robust)

Range $x_{max} - x_{min}$ (unit)

Interquartile Range (IQR) $IQR = Q_3 - Q_1$ where $Q_1$ is the median of the lower half and $Q_3$ is the median of the upper half
If the # of entries is odd, discard the overall median before dividing in half. (unit)
There is no generlly accepted definition for IQR, make your own usage and definition clear as per use case


5 Number summary: $x_{min}$, $Q_{1}$, $\tilde{x}$, $Q_3$, $x_{max}$ Used to draw box plot. `QUARTILE.INC(range, 0-4)` in XL

Outliers: values very far from the bulk of the data. There is no set defn for these, just if a value is 1.5*IQR less than $Q_1$ or 1.5*IQR more than $Q_3$ then it is *generally* regarded as an outlier

## Moving average

$m_n = \cfrac{\sum\limits_{i=1}^{k} (y_{n-i})}{k}$

Trendline in XL.

## Bivariate Data

Data involving $(x_i, y_i)$ indep & dep vars. All single series terms can be used on either series

### Covariance and Correlation

For population:
$S_{xy} = \cfrac{1}{n} \sum\limits_{i=1}^n (x_i - \bar{x})(y_i - \bar{y})$ (unit^2)

For sample:
$S_{xy} = \cfrac{1}{n-1} \sum\limits_{i=1}^n (x_i - \bar{x})(y_i - \bar{y})$ (unit^2)

$r_{xy} = \cfrac{S_{xy}}{S_x S_y}$

`COVARIANCE.S` and `CORREL` in XL

## Linear Regression

$x$ - predictor/explanatory/independent variable
$y$ - response/outcome/dependent variable

### Least Squares Method

Assuming that there is a line of best fit for the linear data, $y = \beta_1 x_i + \beta_0$

We compute the signed distance of all the $y_i$ values with the predicted values from the above equation, and minimise it using mvc to find the most apt values of $\beta_0$ and $\beta_1$

$Q = \sum\limits_{i=1}^{n}[ y_i - (\beta_1 x_i + \beta_0)]^2$


#### Derivation Using MVC:

$\cfrac{\partial Q}{ \partial \beta_1} = \sum\limits_{i=1}^{n} - 2 x_i [ y_i - (\beta_1 x_i + \beta_0)]$

$\cfrac{\partial Q}{ \partial \beta_0} = \sum\limits_{i=1}^{n} - 2 [ y_i - (\beta_1 x_i + \beta_0)]$

Equating to 0

$\sum\limits_{i=1}^{n} - 2 x_i [ y_i - (\beta_1 x_i + \beta_0)] = 0$

$\sum\limits_{i=1}^{n} - 2 [ y_i - (\beta_1 x_i + \beta_0)] = 0$

divide by -2 =>

$\sum\limits_{i=1}^{n}x_i[ y_i - (\beta_1 x_i + \beta_0)] = 0$

$\sum\limits_{i=1}^{n}[y_i - (\beta_1 x_i + \beta_0)] = 0$

=>

$\sum\limits_{i=1}^{n} x_i y_i - \sum\limits_{i=1}^{n}x_i(\beta_1 x_i + \beta_0) = 0$

$\sum\limits_{i=1}^{n} y_i - \sum\limits_{i=1}^{n}(\beta_1 x_i + \beta_0) = 0$

=>

$\sum\limits_{i=1}^{n} x_i y_i - \beta_1\sum\limits_{i=1}^{n} x^2_i + \beta_0 \sum\limits_{i=1}^{n} x_i = 0$ ... (i)

$\sum\limits_{i=1}^{n} y_i - \beta_1 \sum\limits_{i=1}^{n} x_i + n\beta_0 = 0$ ... (ii)

Multiply (ii) by $\bar{x}$ =>

$\sum\limits_{i=1}^{n} x_i y_i - \beta_1\sum\limits_{i=1}^{n} x^2_i +  n \bar{x} \beta_0 = 0$

$n \bar{y} \bar{x} - \beta_1 n \bar{x}^2 + n \bar{x} \beta_0 = 0$ ... (iii)

subtract (i) from (ii) =>

$n \bar{y} \bar{x} - \sum\limits_{i=1}^{n} x_i y_i + \beta_1 (\sum\limits_{i=1}^{n}x^2_i - n \bar{x}^2) = 0$

=>

$\beta_1 = \cfrac{n \bar{y} \bar{x} - \sum\limits_{i=1}^{n} x_i y_i}{n \bar{x}^2 - \sum\limits_{i=1}^{n}x^2_i}$

#### Final Result
INSERT_ALGEBRA_HERE W2C1S30

$\beta_1 = \cfrac{S_{xy}}{S_{x}^2}$

INSERT_ALGEBRA_HERE

$\beta_0 = \bar{y} - \bar{x}\beta_1$

Since  = $\hat{\beta_1}$ and $\hat{\beta_0}$ are estimaters of their values for the "true" linear relation, they are denoted by the hat notation.

#### Coefficient of Determination

This is a measure of how successful the regression model is.

$r^2 = \cfrac{\sum\limits_{i=1}^{n} (\hat{y}_i - \bar{y})^2}{\sum\limits_{i=1}^{n} (y_i - \bar{y})^2}$

0 implies complete failure and 1 implies complete fit

$r^2 = r_{xy}^2 = \cfrac{S_{xy}^2}{S_x^2 S_y^2}$

### Multiple regression with matricies

$y = X \beta$

Here, $X$ is an $n\times k$ matrix of $k$ independent variables in $n$ rows

$\beta$ is an $k \times 1$ matrix of $k$ coefficients for the $k$ independent variables

$Q = ||y - X\beta||^2$

INSERT_ALGEBRA_FOR_SOLUTION W2C1S30

$\hat{\beta} = (X^T X)^{-1}X^T y$

CoD formula is the same

### Overfitting

increasing the order of regression too much hurts the model in the long run

## Axioms of Probability

1. $\mathbb{P}(E) \geq 0$ The probability of any event is non negative
2. $\mathbb{P}(S) = 1$ or $\mathbb{P}(\phi) = 0$ The probability of an event from the sample space occuring is always one
3. if $E_i \cap E_j = \phi$ then $E_i + E_j = E_i \cup E_j$

## Baye's Theorem, Conditional Probability and Independent events

## Random Variables

A random variable is a function on the sample space of an experiment. It maps each outcome of the experiment to some $\mathbb{R}$ value

Remember for the functions below, $x \in \mathbb{R}$

### Probability Mass Function (pmf)

For a discrete random variable:

$f(x) = \mathbb{P}(X = x)$

### Cumulative Distribution Function (cdf)

For a discrete random variable:

$F(x) = \mathbb{P}(X \leq x_n) =  \sum\limits_{i=1}^{n} f(x_i)$

### Geometric Random Variables
\# of coin tosses till T for the first time

$X \sim geometric(p)$

#### Memorylessness property of geometric Distributions

$\mathbb{P}(X \geq s + t | X \geq t) = \mathbb{P}(X \geq s)$

## Expectation, Mean and variance

### Expectation

$\bar{x} = \sum\limits_{i=1}^{n} x_i \cfrac{|E_i|}{|S|}$

$\bar{x} = \sum\limits_{i=1}^{n} x_i \mathbb{P}(X = x_i)$

This is the expeced value:

$\mathbb{E}(x) = \sum\limits_{i=0}^{n} x_i \mathbb{P}(X = x_i)$

### Variance

$Var(X) = \sum\limits_{i=0}^{n} \mathbb{P}(x)(\mathbb{E}(x) - x_i)^2$

## Distributions of Random Variables

### Binomial Distributions

If an experiment has two outcomes with probabilities $\mathbb{P}(A) = p$ and $\mathbb{P}(A') = 1 - p$

If X is the number of times the outcome was A, then X is a **binomial distribution** denoted by $X \sim binomial(n, p)$

pmf: $\mathbb{P}(X = k) = f(x) = \displaystyle\binom{n}{k}p^k(1-p)^{n-k}$

#### Mean & Variance of a Binomial Distribution

$\mathbb{E}(x) = np$

$Var(x) = np(1-p)$

### Poisson Distribution

A random variable $X$ satisfies a Poisson distribution if its pmf is a function of a value $\lambda > 0$ such that:

$\mathbb{P}(X = k) =  e^{-\lambda}\cfrac{\lambda^k}{k!}, k \in 0, 1, 2 ...$

$\mathbb{E}(x) = \lambda$

$Var(x) = \lambda$

when $\lambda = np$, it approximates a binomial distribution with parameters $n$, $p$

## Properties of Expectation and Variance

$\mathbb{E}(g(X)) = \sum\limits_{i=1}^{n}g(x_i)\mathbb{P}(X = x_i)$

$Var(X) = \mathbb{E}(X^2) - \mathbb{E}(X)^2$

$Var(aX + b) = a^2 Var(X)$

$\mathbb{E}(\sum\limits_{i=1}^{m}X_i) = \sum\limits_{i=1}^{m}\mathbb{E}(X_i)$

### Bernoulli Distributions

A random variable is a Bernoulli random variable if it can only take on values 1 (success) and 0 (faliure)

$\mathbb{P}(X = 1) = p \;\;\;\; \mathbb{P}(X = 0) = 1 - p$

$\mathbb{E}(X) = p \;\;\;\; Var(X) = p(1 - p)$

Usually, a complex random variable may be represented as a sum of suitably chosen bernoulli variables

## Probability with Continuous Random Variables

$f : \mathbb{R} \rightarrow [0, \infty)$ is called the probability density function (pdf) of X if for any $A \in \mathbb{R}$

\[\mathbb{P}(X \in A) = \int_{A}f(x)dx\]

The cumulative density function (cdf) of X is defined as:

\[F(x) = \mathbb{P}(X \leq x) = \int\limits_{-\infty}^{x}f(t)dt\]

$F'(x) = f(x)$ It is often easier to find the cdf and then differentiate for the pdf.

### Properties of the CDF

1. $F(x)$ is a non decreasing function
2. $0 \leq F(x) \leq 1$; $\lim\limits_{x \rightarrow -\infty} F(x) = 0$; $\lim\limits_{x \rightarrow \infty} F(x) = 1$
3. $F(x)$ represents a probability
4. For $a \leq b$, $\mathbb{P}(a \leq X \leq b) = F(b) - F(a)$

### Properties of the PDF

$f(x)$ does **not** represent a probability by itself, only for a small $\delta x$

$f(x)\delta x \approx \mathbb{P}(x \leq X \leq x + \delta x)$

1. $\mathbb{P}(a \leq X \leq b) = \int\limits_a^b f(x)dx = F(b) - F(a)$
2. $\mathbb{P}(X \in \mathbb{R}) = \int\limits_{-\infty}^{\infty} f(x)dx = 1$
3. $\mathbb{P}(X = a) = \int\limits_{a}^{a} f(x)dx = 0$

This is why $\leq$ and $<$ are interchange-able

### Expectation of Continuous Distribution

\[ \mu = \mathbb{E}(X) = \int\limits_{-\infty}^{\infty} x f(x) dx \]

All properties for expectation hold Here

$\mathbb{E}(g(X)) = \int\limits_{-\infty}^{\infty}g(x_i)f(x)dx$

$Var(X) = \mathbb{E}(X^2) - \mathbb{E}(X)^2$

$Var(aX + b) = a^2 Var(X)$

$\mathbb{E}(\sum\limits_{i=1}^{m}X_i) = \sum\limits_{i=1}^{m}\mathbb{E}(X_i)$

### Uniform Distribution

A cont. rand. dist. X is uniform if

\[  f(x) = 
    \begin{cases}
        0 & x < a \\
        \cfrac{1}{b-a} & a \leq x \leq b \\
        0 & b < x
    \end{cases}
\]

\[  F(x) = 
    \begin{cases}
        0 & x < a \\
        \cfrac{x-a}{b-a} & a \leq x \leq b \\
        1 & b < x
    \end{cases}
\]

$X \sim uniform(a, b)$

### Expectation of Uniform Distribution

$\mathbb{E}(X) = \cfrac{a+b}{2}$

### Variance of Distribution

$Var(X) = \cfrac{(b-a)^2}{12}$

### Exponential Distribution

\[  f(x) = 
    \begin{cases}
        \lambda e^{-\lambda x} & x \geq 0 \\
        0 & x < 0
    \end{cases}
\]

$X \sim exponential(\lambda)$

\[  F(x) = 
    \begin{cases}
        1 - e^{-\lambda x} & x \geq 0 \\
        0 & x < 0
    \end{cases}
\]

$\lambda$ - Rate of average occurrance

#### Memorylessness property of exp Distributions

$\mathbb{P}(X \geq s + t | X \geq t) = \mathbb{P}(X \geq s)$

#### Expectation of exp distribution

$\mathbb{E}(X) = \cfrac{1}{\lambda}$

#### Variance of exp distribution

$Var(X) = \cfrac{1}{\lambda^2}$

### Expectation of a CRV Whoes PDF = 0 for X < 0

\[\mathbb{E}(X) = \int\limits_{0}^{\infty}(1-F(x))dx\]

### Standard Normal Distribution (aka Gaussian Distribution)

A rand. var. $Z$ is said to satisfy standard normal dist. if its pdf is given by:

\[ \phi(x) = \cfrac{1}{\sqrt{2\pi}} e^{-x^2/2}, x \in \mathbb{R} \]

Using double integration it can be shown that this is a valid cdf

SND is so common $Z$ is used to denote it. its cdf is given by the following integral which does not have an elementary anti-derivative

\[ \Phi(x) = \cfrac{1}{\sqrt{2\pi}} \int\limits_{-\infty}^{x} e^{-t^2/2} dt \]

$\mathbb{E}(Z) = 0$ and $Var(Z) = 1$

### General Normal Distribution

if $X = aZ + b$, we can find the cdf as follows

\[ F(x) = \mathbb{P}(aZ + b \leq x) = \mathbb{P}(Z \leq \cfrac{x - b}{a}) = \Phi(\cfrac{x - b}{a}) \]

On differentiating, we find that

\[ f(x) = \cfrac{1}{\sqrt{2a^2\pi}} e^{-(x-b)^2/(2a^2)} \]

The expectation and variance of the pdf are as follows:

$\mathbb{E}(X) = b$

$Var(X) = a^2$

replacing $b$ with $\mu$ and $a$ with $\sigma$

\[ f(x) = \cfrac{1}{\sqrt{2\sigma^2\pi}} e^{-(x-\mu)^2/(2\sigma^2)} \]

This is formally known as a normal distribution $X \sim \mathcal{N}(\mu, \sigma^2)$. Here, $\mathbb{E}(X) = \mu$ and $Var(X) = \sigma^2$

$Z ~ \mathcal{N}(0, 1) is the SND$

#### Properties of GND

1. The probability of a value being within $k$ standard deviations of the mean is the same for every GND

$\color{cyan}\mathbb{P}(\mu - k\sigma \leq X \leq \mu + k\sigma) \color{white}= \color{lime}\mathbb{P}(-k\leq \cfrac{X - \mu}{\sigma} \leq k) \color{white}= \color{yellow}\mathbb{P}(-k\leq Z \leq k)$

$\color{cyan}\mathbb{P}(-k \leq Z \leq k) \color{white}= \color{lime}\Phi(k) - \Phi(-k) \color{white}= \color{yellow}2\Phi(k) - 1 \color{white}= 1 - 2\Phi(-k)$

#### Approximating Binomial Dist with GN Dist

$X \sim binomial(n, p)$ has an $\mathbb{E}(X) = np$ and $Var(X) = np(1-p)$.

Note that the value $\mathbb{P}(X = K)$ is the area of the rectangle from $k - 0.5$ to $k + 0.5$ on the binomial dist.

This can be thus be approximated by $\mathbb{P}(k+0.5 \leq Y \leq k+0.5)$ on a normal dist., where $Y \sim \mathcal{N}(np, np(1-p))$.

Hence, $\mathbb{P}(X \leq k) = \mathbb{P}(Y \leq k + 0.5) = \approx \Phi(\cfrac{k+0.5-np}{\sqrt{np(1-p)}})$

The value $0.5$ is known as the continuity correction. 

Try act 3, 4 and 5 from W8C1

## Q-Q (Quantile-Quantile) Plot

This plot is a graphical way to check which type of distribution some collected data best fits

The $p$th quantile (aka percentile) of $X$ is an $x$-value $Q_p$ such that $\mathbb{P}(X = Q_p) = F(Q_p) = p$

If $p = 1/2$ then $Q_p$ is the median.

If the CDF is a strictly increasing function (normal and exp), then $Q_p = F^{-1}(p)$

If we plot the $p$th quantile of any normal distribution against the $p$th quantiles of the standard normal for various values of $p$, then the plot forms a straight line. (A similar result is true for exponential distribution)

In general, if the data comes from a random variable $X$ then $x_i$ should be close to the $\cfrac{i}{n+1}$th quantile of $X$

### To construct a Q-Q plot

The above observation leads to the following procedure for constructing a Q-Q plot:

1. Order the data values as $x_1 \leq x_2 \leq x_3 \leq ... \leq x_n$.
2. If you suspect that the data comes from a certain distribution, then construct a scatter plot of $x_i$ against the $\cfrac{i}{n+1}$ th quantiles of such a distribution.
3. Special case: if you suspect the data to be normal, then plot $x_i$ against $\Phi^{-1}(\cfrac{i}{n+1})$ this is known as a normal probability plot.
4. If the scatter plot is close to a straight line, then the data could be modelled by said distribution

## Functions of Random Variables

if we have some $Y = g(X)$ and the CDF/PDF of $X$ is known, then we can find the $CDF/PDF$ of $Y$. $Y \in range(g)$

$F_y(y) = \mathbb{P}(Y \leq y)$

$F_y(y) = \mathbb{P}(g(X) \leq y)$

$F_y(y) = \mathbb{P}(X \leq g^{-1}(y))$ (note that the inequality might change when solving for g^{-1}, square roots, or flips)

$F_y(y) = F_x(g^{-1}(y))$ here, $y \in domain(g^{-1})$

differentiating:

$f_y(y) = f_x(g^{-1}(y))(g^{-1}(y))'$

## Discrete Joint Random Variables

### Joint PMF

let $X$ and $Y$ be some discrete random variables. The joint pmf is defined as:

\[ f(x, y) = \mathbb{P}(X = x \cap Y = y)\]

$f(x, y)$ must satisfy that $\sum\limits_{\forall x}\sum\limits_{\forall y} f(x, y) = 1$

### Marginal PMF

Marginal pmf of $X$, denoted as $f_X$ is defined as:

\[ f_X(x) = \mathbb{P}(X = x) = \sum\limits_{\forall y} f(x, y) \]

Similarly, marginal pmf of $Y$, denoted as $f_Y$ is defined as:

\[ f_Y(y) = \mathbb{P}(Y = y) = \sum\limits_{\forall x} f(x, y) \]

The marginal pmfs are the row/column sums of the joint pmf table, and since they're usually written in the margins of the joint pmf table, they're called marginal pmfs.

can ask: $\mathbb{P}(X + Y = n)$

### Independence of RV

Two random variables $X$ and $Y$ are independent

iff $X \in A$ and $Y \in B$ are independent $\forall A, B \subseteq \mathbb{R}$

iff $\mathbb{P}(X \in A \cap Y \in B) = \mathbb{P}(X \in A)\mathbb{P}(Y \in B) \forall A, B \subseteq \mathbb{R}$

iff $f(x, y) = f_X(x) f_Y(y) \forall x, y \subseteq \mathbb{R}$

### Expected Value of functions over Joint random variables

\[ \mathbb{E}(g(X, Y)) = \sum\limits_{\forall x} \sum\limits_{\forall y} g(x, y) f(x, y) \]

Theorem: 

\[ \mathbb{E}(X + Y) = E(X) + E(Y) \]

## Continuous Joint Random Variables

### Joint PDF

\[ \mathbb{P}((X, Y) \in C) = \int\int_{(x, y) \in C} f(x, y)dx dy \]

specifically, if the region is rectangular $[a, b] \times [c, d]$ then

\[ \mathbb{P}((X, Y) \in C) = \int\limits_c^d\int\limits_a^b f(x, y)dx dy \]

\[ \int\limits_{-\infty}^{\infty}\int\limits_{-\infty}^{\infty} f(x, y)dx dy = 1\]

Once again, $f(x, y)$ is not a probability on its own. But for small $\delta x$ and $\delta y$, $f(x, y)\delta x \delta y = \mathbb{P}(X \in [x, x + \delta x], Y \in [y, y + \delta y])$

### Marginal pdf

\[ \mathbb{P}(X = x) = \int\limits_{-\infty}^{\infty} f(x, y) dy\]

\[ \mathbb{P}(Y = y) = \int\limits_{-\infty}^{\infty} f(x, y) dx\]

### Expected Value

\[ \mathbb{E}(g(X, Y)) = \int\limits_{-\infty}^{\infty}\int\limits_{-\infty}^{\infty} g(x, y) f(x, y)dx dy \]

### Independence of Continuous RV

exactly the same as discrete

iff $\mathbb{P}(X \in A \cap Y \in B) = \mathbb{P}(X \in A)\mathbb{P}(Y \in B) \forall A, B \subseteq \mathbb{R}$

iff $f(x, y) = f_X(x) f_Y(y) \forall x, y \subseteq \mathbb{R}$

the two conditions are equivalent

### Joint CDF

$F(x, y) = \mathbb{P}(X \leq x, Y \leq y)$

$\lim\limits_{y \to \infty} F(x, y) = F_X(x)$

$\lim\limits_{x \to \infty} F(x, y) = F_Y(y)$

$\mathbb{P}(X > x, Y > y) = 1 - F_X(x) - F_Y(y) + F(x, y)$

## Sum of Independent RVs

If $X \sim binomial(n, p)$ and $Y \sim binomial(m, p)$ then $X + Y \sim binomial(n + m, p)$. This is intuitive: $n$ trials followed by $m$ trials is equivalent to $m + n$ trials.

If $X \sim poisson(\lambda)$ and $Y \sim poisson(\mu)$ then $X + Y \sim poisson(\lambda + \mu)$. This is intuitive as well, $X$ occurs $\lambda$ times on avg, $Y$ occurs $\mu$ times on avg, This means that $X + Y$ will occur $\lambda + \mu$ times on average.

### Expectation

$\mathbb{E}(X+Y) = \mathbb{E}(X) + \mathbb{E}(Y)$

$\mathbb{E}(aX+bY+c) = a\mathbb{E}(X) + b\mathbb{E}(Y) + c$

### Variance

$Var(X+Y) = \mathbb{E}((X + Y)^2) - \mathbb{E}((X + Y))^2$

$Var(X+Y) = \mathbb{E}(X^2) + \mathbb{E}(Y^2) + 2\mathbb{E}(XY) - \mathbb{E}(X)^2 - \mathbb{E}(Y)^2 - 2\mathbb{E}(X)\mathbb{E}(Y)$

$Var(X+Y) = \mathbb{E}(X^2) - \mathbb{E}(X)^2 + \mathbb{E}(Y^2) - \mathbb{E}(Y)^2 + 2(\mathbb{E}(XY) - \mathbb{E}(X)\mathbb{E}(Y))$

$Cov(X, Y) = \mathbb{E}(XY) - \mathbb{E}(X)\mathbb{E}(Y)$ which is $ = 0$ when X and Y are independent

$Var(X+Y) = Var(X) + Var(Y) + 2Cov(X, Y)$

$Var(X+Y) = Var(X) + Var(Y)$

$Var(aX+bY+c) = a^2Var(X) + b^2Var(Y) + 2abCov(X, Y)$

#### Covariance of Independent Variables

\[ \mathbb{E}(XY) = \int\limits_{-\infty}^{\infty} \int\limits_{-\infty}^{\infty} xy f(x, y) dx dy \]

\[ \mathbb{E}(XY) = \int\limits_{-\infty}^{\infty} \int\limits_{-\infty}^{\infty} xy f_X(x) f_Y(y) dx dy \]

\[ \mathbb{E}(XY) = \int\limits_{-\infty}^{\infty} x f_X(x)dx \int\limits_{-\infty}^{\infty} y f_Y(y) dy \]

\[ \mathbb{E}(XY) = \mathbb{E}(X) \mathbb{E}(Y) \]

If $X \sim uniform(0, 1)$ and $Y \sim uniform(0, 1)$ are independent RV, we can find $\mathbb{P}(X + Y \leq t) = \int\int_{x+y \leq t} f(x, y) dx dy$ and then differentiate to find the pdf

We thus find that:

\[  \mathbb{P}(X + Y \leq t) = 
    \begin{cases}
        \cfrac{t^2}{2}  & 0 < t < 1 \\
        1 - \cfrac{(2- t)^2}{2} & 1 \leq t \leq 2 \\
        0 & otherwise
    \end{cases}
\] 

and on differentiating:

\[  \mathbb{P}(X + Y = t) = 
    \begin{cases}
        t & 0 < t < 1 \\
        2-t & 1 \leq t \leq 2 \\
        0 & otherwise
    \end{cases}
\]

If $X \sim \mathcal{N}(\mu_1, \sigma_1^2)$ and $Y \sim \mathcal{N}(\mu_2, \sigma_2^2)$ are independent normal RV. $X + Y \sim \mathcal{N}(\mu_1 + \mu_2, \sigma_1^2 + \sigma_2^2)$

## Independent and Identitcally Distributed RV

A collection of RV is said to be IID if they are all independent and have the same distribution

\[ \bar{X}_n = \cfrac{1}{n}\sum\limits_{i = 1}^{n} X_i \]

$\bar{X}_n$ itself is an RV

if Each individual dist has $\mu$ and $\sigma^2$ then $\bar{X}_n$ has $\mu$ and $\cfrac{\sigma^2}{n}$

### Law of large numbers

for any $\epsilon > 0$

\[ \lim_{n \to \infty} \mathbb{P}(|\bar{X}_n - \mu| < \epsilon) = 1 \]

LLN shows that the emperical frequency of any repeatable event converges to its theoretical Probability. To see this, let A be the event of interest, and $p = \mathbb{P}(A)$. $X_i = 1$ if A occurs on the $i$th (independent) trial, and $0$ otherwise. Then $\bar{X}_n$ is the empirical frequency of A, and by the LLN, it converges to $\mu = \mathbb{E}(X_i) = p$.

Likewise, the LLN shows that histograms constructed from data approximate the true pdf or pmf of the underlying RV. To see this, consider a bin in a histogram given by the interval $[a, b)$. $Y_i = 1$ if the $i$th data point $X_i$ falls into the bin, and $0$ otherwise. Then $\bar{Y}_n$ is the proportion of data points in that bin, and it converges to $\mu = \mathbb{E}(Y_i) = \mathbb{P}(a \leq X_i < b)$

### Central Limit Theorem (CLT)

If we have $n$ IID RV with $\mu$ and $\sigma^2 < \infty$, Then for any $x \in \mathbb{R}$

\[ \lim_{n \to \infty} \mathbb{P} (\cfrac{{\bar{X}_n - \mu}}{\sigma/\sqrt{n}} \leq x) = \Phi(x) \]

\[ \cfrac{\bar{X}_n - \mu}{\sigma/\sqrt{n}} \approx \mathcal{N}(0, 1) = Z\]

\[ \bar{X}_n \approx \mathcal{N}(\mu, \sigma^2/n) \]

\[ \sum\limits_{i=1}^{n} X_i \approx \mathcal{N}(n\mu, n\sigma^2) \]

The limiting behaviour of this sum depends solely on the mean and variance of the dist. and not on their type

Typically, $n \geq 30$ (if pdf or pmf symmetric/skewed $n$ may be smaller/larger)

## Point Estimators

Parameters such as $\mu$ or $\sigma^2$ of the distribution are often unknown in practise. Given a dataset, $x_1$, $x_2$, ... $x_i$ we would like to estimate them. If some unknown parameter $\theta$ is estimated using computations on the dataset, it is known as a point estimator and denoted as $\hat{\theta}$

for the true mean $\mu$, we use $\hat{\mu} = \bar{x}$

for the true variance $\sigma^2$ we use $\hat{\sigma}^2 = S_x^2$

## Confidence Intervals

A point estimator is unlikely to give a value that actually agrees with the true parameter

It would be more useful to give a range of possible values for the value being estimated. This would allow us to make statements like "most of the time, $\mu$ lies in some interval A"

A confidence interval is an interval $A$ for the estimate of a parameter $\theta$ such that

\[\mathbb{P}(\theta \in A) = 1-\alpha\]

### Two sided CIs

if $A = [L, U]$

\[\mathbb{P}(L \leq \theta \leq U) = 1-\alpha\]

Here, $\alpha \in (0, 1)$ and $L, U$ are computed from a sample

$[L, U]$ is called a $100(1-\alpha)\%$ (two sided) confidence interval for $\theta$

$(1-\alpha)$ is called the confidence level. Using $\alpha = 0.05$ is very common, resulting in a $95\%$ confidence level

Consider that a random sample $x_1$, $x_2$, ... $x_n$ is drawn from a distribution $X$ with $\mu$ and $\sigma^2$. Suppose that $n$ is large and $\mu$ is unknown but $\sigma^2$ is known.

We can then construct a $95\%$ confidence interval for $\mu$ by noting that $\cfrac{\bar{X}_n - \mu}{\sigma/\sqrt{n}}$ is approximately standard normal by the central limit theorem. Hence,

$\mathbb{P}(-1.96 \leq \cfrac{\bar{X}_n - \mu}{\sigma/\sqrt{n}} \leq 1.96) = 0.95$

$\mathbb{P}(-1.96 \cfrac{\sigma}{\sqrt{n}} \leq \bar{X}_n - \mu \leq 1.96 \cfrac{\sigma}{\sqrt{n}}) = 0.95$

$\mathbb{P}(1.96 \cfrac{\sigma}{\sqrt{n}} + \bar{X}_n \geq \mu \geq - 1.96 \cfrac{\sigma}{\sqrt{n}} + \bar{X}_n) = 0.95$

Generally, let $z_{\alpha/2} = \Phi^{-1}(1-\cfrac{\alpha}{2})$

Then we have that $100(1-\alpha)\%$ two-sided confidence interval for $\mu$ is given by

\[ \left[ \bar{x} - z_{\alpha/2} \cfrac{\sigma}{\sqrt{n}}, \bar{x} + z_{\alpha/2} \cfrac{\sigma}{\sqrt{n}} \right] \]

**If the distribution is known to be normal, then we don't need $n$ to be very large, it works for any $n \in \mathbb{N}$**

Once a confidence interval has been calculated, the true mean $\mu$ either lies inside it, or it does not. So, technically speaking, it is incorrect to say that µ lies inside the $95\%$ CI with probability = $95\%$.

A better interpretation for the $95\%$ CI is: if we repeatedly draw samples of size $n$ from the same distribution, and calculate the CI using the same method each time, then the proportion of CI’s that contains $\mu$ will approach $95\%$

### One sided CI

**Lower** $100(1-\alpha)\%$ confidence interval: $\left[ \bar{x} - z_{\alpha} \cfrac{\sigma}{\sqrt{n}}, \infty \right)$

**Upper** $100(1-\alpha)\%$ confidence interval: $\left( -\infty, \bar{x} + z_{\alpha} \cfrac{\sigma}{\sqrt{n}} \right]$

### Unknown Variance

In most applications, $\sigma^2$ is also unknown, and is estimated using $S_x^2$. In general there is no limit theorem for $cfrac{\bar{X}_n - \mu}{S/\sqrt{n}}$

In the special case where $X_i \sim \mathcal{N}(\mu, \sigma^2)$ for all $1 \leq i \leq n$ the distribution of $cfrac{\bar{X}_n - \mu}{S/\sqrt{n}}$ can be found using the *Student's $t$-distribution with $n-1$ degrees of freedom*

When $\sigma^2$ is unknown but $X_i$ are IID normal RVs, the $100(1-\alpha)\%$ two sided CI is given by

\[ \left[ \bar{x} - t_{n-1, \alpha/2} \cfrac{\sigma}{\sqrt{n}}, \bar{x} + t_{n-1, \alpha/2} \cfrac{\sigma}{\sqrt{n}} \right] \]

$t_{n-1, \alpha/2}$ comes from the inverse CDF of a $t$-distribution. Its values are also tabulated like $\Phi$. `T.INV(1-\alpha/2, n-1)` may be used in Excel

The one sided CIs are given by:

**Lower** $100(1-\alpha)\%$ confidence interval: $\left[ \bar{x} - t_{n-1, \alpha/2} \cfrac{\sigma}{\sqrt{n}}, \infty \right)$

**Upper** $100(1-\alpha)\%$ confidence interval: $\left( -\infty, \bar{x} + t_{n-1, \alpha/2} \cfrac{\sigma}{\sqrt{n}} \right]$

### $t$-distributions

$t$-distribution is a family of continuous distributions that depend on $n$. It converges to the standard normal as $n \to \infty$

Each $t$-distribution is a symmetric bell shaped curve symmetric around $0$, but has heavier tails than the SND. Using it thus gives wider CIs (in)

## Hypothesis Testing

To answer questions such as: is A better than B?

In hypothesis testing, we try to infer some information about the population from a sample; more specifically, we attempt to answer this: given a sample, does it provide statistically significant evidence to prove beyond reasonable doubt a hypothesis about the population?

To do so, we use data to test the validity of a claim about the population, against a counter claim. We set up the two competing claims as follows:

The null hypothesis, $H_0$. Usually, $H_0$ is the claim of no difference or no effect; the status quo / conservative stance.

The alternative hypothesis, $H_1$, which is the logical negation of $H_0$. Usually, $H_1$ is the claim that there is a difference or effect; a
change from a well-accepted current practice.

### Computing Intervals

A random IID sample of $n$ values $X_i$ drawn from a distribution with unknown $\mu$ but known $\sigma^2$. If $n$ is sufficiently large, we can use CLT to test $H_0 : \mu = \mu_0$ vs $H_1 : \mu \neq \mu_0$

**Assuming** that $H_0$ is true, we have that $\cfrac{\bar{X}_n - \mu_0}{\sigma / \sqrt{n}} \sim \mathcal{N}(0, 1)$. Thus:

\[ \mathbb{P}(-z_{\alpha/2} \leq \cfrac{\bar{X}_n - \mu_0}{\sigma / \sqrt{n}} \leq z_{\alpha/2}) = 1 - \alpha \]

Hence, we $\color{red}\text{reject H0 in favour of H1}$ iff $\bar{x}$ lies outside the above interval for a given $\alpha$ (probability of type I error, aka significance level, usually small, ~ $0.1$, $0.05$, $0.01$)

2. $H_1 : \mu > \mu_0$: we $\color{red}\text{reject H0 in favour of H1}$ iff $\bar{x}$ lies outside the upper bound one sided interval

3. $H_1 : \mu < \mu_0$: we $\color{red}\text{reject H0 in favour of H1}$ iff $\bar{x}$ lies outside the lower bound one sided interval

### p-value

Another approach to hypothesis testing: assuming $H_0$ is true, whats the probability of observing an outcome at least as extreme as the one observed? If this probability is less than $\alpha$ (the significance level) we reject $H_0$. This probability is thus known as the p-value

It is the smallest value of $\alpha$ for which $H_0$ can be rejected.

**Note: Definition of at least as extreme depends on context! It could be deviation on either side of the mean, it depends on the question and its context!**

Note that this is actually equivalent to the first method, because the p-value is less than $\alpha$ iff the $\bar{x}$ lies outside of our computed CI for that $\alpha$ .

### Power

The probability of correctly rejecting $H_0 : \mu = \mu_0$ in favour of $H_1 : \mu = \mu_1 > \mu_0$ is known as the power of the test. This probability is dependent on the true mean $\mu_1$ of the distribution. Basically, its the probability that our observed sample mean is higher than $\mu_0 + z_{\alpha} \cfrac{\sigma}{\sqrt{n}}$, because that is when we reject the null hypothesis.

Thus:

\[ 1-\beta = \mathbb{P}(\bar{X}_n > \mu_0 + z_{\alpha} \cfrac{\sigma}{\sqrt{n}}) \]

\[ 1-\beta = \mathbb{P}(Z > \cfrac{\mu_0 - \mu_1}{\cfrac{\sigma}{\sqrt{n}}} + z_{\alpha}) \]

\[ \text{power} = 1-\beta = \mathbb{P}(Z < \cfrac{\mu_1 - \mu_0}{\cfrac{\sigma}{\sqrt{n}}} - z_{\alpha}) \]

\[ \beta = 1 - \mathbb{P}(Z < \cfrac{\mu_1 - \mu_0}{\cfrac{\sigma}{\sqrt{n}}} - z_{\alpha}) \]

$\beta$ is the probability of committing a type II error. (failing to reject $H_0$ when it is false)

## Residuals

If we have some data $(x_i, y_i)$ and we draw the regression line for it using the equation $\hat{y} = \beta_0+ + \beta_1x$ then for each $y_i$, we have a residual defined as $e_i = y_i - \hat{y}_i$

If the data is actually linear in reality, then the residual values are IID normal random variables (assuming that the errors are measurement errors)

Hence, an $(x_i, e_i)$ plot (known as a **residual plot**) should hold the following properties:

1. It should be randomly distributed
2. The vertical spread of residuals (standard deviation of the $\epsilon_i$) should remain constant
3. The Q-Q plot of the residuals can be used to test for normality as well.

If the residual plot is a parabola, the regression may need an $x^2$ term

The variance of the residuals can be estimated by the mean squared error:

$s^2 = \cfrac{1}{n-2} \sum\limits^n_{i=1}e_i^2$

generally, any $e_i > 2s$ implies outlier 

### Distribution of $\beta_1$

$\hat{\beta}_1 \sim \mathcal{N}(\beta_1, \cfrac{\sigma^2}{(n-1) s_x^2})$ (w13c1 for proof)

plug this into the confidence interval formula for an SND $\sim \mathcal{N}(\mu, \sigma^2)$ with $n$ observations

\[ \mathbb{P}(-z_{\alpha/2} \leq \cfrac{\hat{\beta}_1 - \beta_1}{\sigma/(s_x\sqrt{n-1})} \leq z_{\alpha/2}) = 1 - \alpha \]

since $\sigma^2$ is unknown in practise, it is replaced with $s^2$ (MSE) and then the t-distribution is utilised to find the CI.

### Hypothesis Testing

if we have $H_0 : \beta_1 = b_1$ vs $H_1 : \beta_1 \neq b_1$

We can reject $H_0$ in favour of $H_1$ at significance level $\alpha$ if $b_1$ lies outside the CI constructed using the given $\alpha$

## Maximum likelyhood estimation

We can use the sample mean and sample variance to approximate the mean and variance of a dist.

In general, a distribution may contain parameters that are different from its mean and var. To find/estimate such parameters, the goal is to pick such a value for them that maximises the probability of seeing the given data.

For instance, if we know that a biased coin has some probability $p$ to give $T$, and we observe $T T T H T$, then intuitively the value of $p$ that maximises this outcome is $p = 4/5$. This can be shown by maximising $\mathbb{P} = p^4 (1-p)$

In general, if we have a pdf with a parameter: $f(x | t)$ and $n$ IID observations $x_i$, then we can write the probability of obserivng the outcome as:

\[ L(t) = \prod\limits_{i = 1}^{n} f(x | t)\]

This function is known as the likelyhood function (probability) of observing the given outcome. Now we can maximise this to find the parameter $t$.