# 4 - Statistics

## Maximum Likelihood Estimation

**Maximum Likelihood Estimation (MLE)** is a popular theoretical approach to the problem of model parameter estimation where we wish to estimate some "true" parameters $\theta$ with $\hat{\theta}$, where $\hat{\theta}_{\text{mle}}$ is the set of parameters that maximizes the probability of observing our data $D$.

$$
\hat{\theta}_{\text{mle}} \equiv \argmax_{\theta} p(D \mid \theta)
$$

In many cases, this approach allows us to formulate our estimation problem as a straightforward "*maximize this function by finding the zero of the derivative*" approach.

For example, in the case of **linear regression**, if we assume the following structure:

$$
y = f(x) + \epsilon
$$

$$
\epsilon \sim N(0, \sigma^2)
$$

where $f(x)$ is a linear function of the vector x, then we can reformulate this as

$$
p(y \mid x, \theta) = N(y \mid w^Tx, \sigma^2) 
$$

which essentially says the same thing, with the main difference being that we can now think about how we can estimate $w$, or the vector of weights, such that the joint probability of having observed our y values is maximized. 

If we do this, then our optimization problem resolves to the familiar **Residual Sum of Squares** objective, namely 

$$
\text{RSS} = \sum_{i=1}^N{(y_i - w^Tx_i)^2}
$$

This is why statisticians will emphasize the importance of residuals being normally distributed about mean 0 with constant variance for linear regression - because those conditions are required for MLE. Of course in practice this is rarely satisfied, which is why linear regression is often used without regard to this assumption.

## Bayesian Statistics

When estimating model parameters, MLE and related methods give useful point estimates. However, this estimate is necessarily sensitive to changes in our data, so there is some inherent uncertainty about what those parameters should even be.

**Bayesian statistics** attempts to model that uncertainty by *assigning a probability distribution rather than a point estimate* to model parameters. In other words, it treats parameters as random variables with an associated distribution, rather than as unknown constants. 

This can be represented as 

$$
P(\theta \mid D) = \frac{P(\theta)P(D \mid \theta)}{P(D)}
$$

We can think of the left-hand posterior as "the probability of some parameter(s) $\theta$ being the true parameters given we observed some data $D$". 

## Frequentist Statistics

The frequentist approach to representing uncertainty in model parameters is to use a sampling distribution, which describes how our estimate might vary over **repeated trials**. 

The main difference between the bayesian and frequentist approach is that the former handles randomness in the parameters, while the latter deals with randomness in the sample.

## Summary
- MLE is a powerful approach for deriving concise, theoretically well-founded solutions to parameter estimation problems
- bayesian and frequentist statisticians approach the problem of modeling uncertainty about model parameters in different ways

