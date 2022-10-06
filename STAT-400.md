# STAT 400

## Chapter 4

### Continuous Bivariate Distributions

If X and Y are two continuous random variables, their joint probability density function, f(x,y) represents the density at the point(x,y).

Marginal PDF: $\int_{-\infty}^{\infty}f(x,y)dy$

Probability for joint pdfs: $P[(X,Y)\in A]=\int\int_{A}f(x,y)dxdy$

Independence: $f(x,y) = f_x(x)f_y(y), x\in S_x,y\in Sy$

### Bivariate Discrete DIstribution

Independence: $P[X=x,Y=y] = P[X=x]P[Y=y]$

### Covariance

Note: $\mu_x = E(X)$ $\mu_y=E(Y)$ $\sigma^2_x=E[(X-\mu_x)]$	$\sigma^2_y=E[(Y-\mu_y)]$

Then, the covariance of X and Y is defined as follows:
$$
Cov[X,Y] = E[(X-\mu_x)(Y-\mu_y)] = \sigma_{xy}
$$
, or
$$
Cov[X,Y] = E(XY) - \mu_x\mu_y
$$
The correlation coefficient, $\rho$, is defined as:
$$
\rho = \frac{Cov(X,Y)}{\sigma_x\sigma_y}
$$
If it is independent, the covariance is 0.

### Conditional Distributions

Conditional Distributions:
$$
P(A|B) = \frac{P(A\cap B)}{P(B)} = \frac{f(x,y)}{f_y(y)}
$$
Conditional Mean and Variance:
$$
\mu_{Y|x}= E(Y|x) = \Sigma_yyf(y|x)
$$

$$
\sigma_{Y|x}^2=\Sigma_y[y-E(Y|x)]^2f(y|x)
$$

, or
$$
=E(Y^2|x)-[E(Y|x)]^2
$$

$$
E(Y|x)=\mu_y + \rho\frac{\sigma_Y}{\sigma_X}(x-\mu_X)
$$

Bivariate Normal follows the distribution:
$$
N(\mu_Y+\rho\frac{\sigma_Y}{\sigma_X}(x-\mu_x),(1-\rho^2)\sigma^2_Y)
$$