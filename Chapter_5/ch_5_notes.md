# 5 - Decision Theory

Decision theory encompasses approaches by which we use our models of the world which we form from observation (aka data), to select optimal actions from an action space. 

$\mathcal{A}$ - action space
$a$ - action ($a \in \mathcal{A}$)
$\mathcal{H}$ - state space of nature
$h$ - observed state of nature ($h \in \mathcal{H}$)
$l(h, a)$ - loss function for taking action $a$ in nature state $h$
$x$ - observed data
$p(H | x)$ - posterior belief about the state of nature given observed data $x$
 
## Bayesian Decision Theory

Under the bayesian approach to decision theory, we can assign different costs (to our liking) associated actions given different states of nature. Then, given our observed data, we can compute the posterior probability of each state of nature. Finally, we can determine the optimal action given our data by computing the expected cost of each action:

$$
a^* = \argmin_{a \in \mathcal{A}}{\mathbb{E}_{p(h \mid x)}[l(a, h)]}
$$

where 

$$
\mathbb{E}_{p(h \mid x)}[l(a, h)] = \sum_{h_i \in \mathcal{H}}{p(h_i \mid x) \cdot l(a, h_i)}
$$

As an example, say we have a patient who tests positive for some kind of cancer, and we want to know whether a particular treatment should be administered. Our action space $\mathcal{A}$ is $\{\text{treatment}, \text{no treatment}\}$.

In order to make an optimal decision here, we logically would want to consider a couple things:

- the probability that the test was wrong (p(false positive))
- the costs of administering vs. not administering the treatment in two contexts:
    - they actually have cancer
    - they don't have cancer

Perhaps the treatment has severe side effects and moderate efficacy. Under what conditions, then, does it make sense to administer it? We could also imagine incorporating more information into this equation like the patient's age, gender, comorbidities (other conditions), perhaps the stage of cancer, etc.

Moreover, we can potentially make a better decision in the global sense by making our assessment of the state of the patient more accurate - perhaps by repeating the same test or performing a different one.


## Frequentist Decision Theory

The frequentist approach arrives at a similar result as the bayesian, though without explicitly defining a prior distribution over the unknown state of nature and, consequently, without computing a posterior.

The risk of some estimator $\pi$, which for an unknown state of nature $\theta$ and observed data $x$ gives action $\pi(x)$, is defined as:

$$
R(\theta, \pi) = \mathbb{E}_{p(x \mid \theta)}{l(x, \pi(x))}
$$

Where $p(x \mid \theta)$ implies that we compute the expected value in effectively the same way as the bayesian case, only with this *likelihood function* rather than a posterior.


## Bayesian vs Frequentist Hypothesis Testing

A key difference in bayesian and frequentist decision theory is how they approach the problem of **hypothesis testing**, which is where we aim to use our observed data to make an optimal conclusion with regard to some hypothesis about the unknown state of nature. 

In both cases, we consider a **null ($H_0$)** and **alternate ($H_1$) hypothesis**, which together span the full state space of nature (ex. for some unknown $\mu$, we form the following hypotheses: $H_0: \mu \geq 5$, $H_1: \mu < 5$) 

When we observe some data $\mathcal{D}$, under the **Bayesian** approach we compute the **bayes factor**:

$$
B_{1, 0} \equiv \frac{p(\mathcal{D} \mid H_1)}{p(\mathcal{D} \mid H_0)}
$$

Where we use Bayes rule to compute $p(\mathcal{D} \mid H)$:

$$
p(\mathcal{D} \mid H) = \frac{p(\mathcal{D}) p(H \mid D)}{p(H)}
$$

If the $B_{1, 0}$ > 1, then we favor $H_1$. 

However, computing $p(H)$  necessarily requires integrating over all possible $\mathcal{D}$: 

$$\int{p(\mathcal{D}) \cdot p(H \mid D)d\mathcal{D}}$$

which may be expensive or otherwise infeasible.

Thus, we can instead use the **Frequentist** approach, which focuses on p-values. 

P-values are defined as the probability of observing a test statistic, computed by $\tau(\mathcal{D})$, is as or more extreme than the one observed given that the null hypothesis is true:

$$
\text{pval}(\tau(\mathcal{D})) = p(\tau(\tilde{D}) \geq \tau(\mathcal{D}) \mid H_0)
$$

We then "reject" $H_0$ based on whether $p$ is below some predefined threshold $\alpha$, which is most commonly 0.05.

One problem with the frequentist approach and p-values in their omission of a prior and a comparison of the relative $p(\mathcal{D} \mid H)$. To understand why this is problematic, consider the following reasoning:

> If a person is a Professor, then they probably graduated from high school. This person is not a Professor. Therefore they did not graduate from high school.

Clearly this is fallacious, but how do we express exactly why in terms of probabilities? In this case, our $H_0$ is that someone graduated from high school, and $H_1$ is that they didn't. $\mathcal{D}$ is sampled from $\{\text{professor}, \text{not professor}\}$.

The problem here is that, at least in the US, $p(H_0 \mid \mathcal{D})$ is high in both cases. 

In other words, we can't simply rely on the fact that our observation is extreme given our null, since it might be even more extreme given our alternate. 


## Empirical Risk Minimization (ERM)

Essentially just a formal probabilistic argument for how we can obtain good estimators by minimizing a risk (loss) function.

This extends to the issue of overfitting vs underfitting, as well as arguing for the tradeoffs of model complexity and consequently for the benefit of regularization.


## Summary
- decision theory attempts to produce optimal decisions given models of the state of nature and the risks associated with potential actions
- the bayesian and frequentist approach differ in that the bayesian focuses on the use of a prior
- bayesian and frequentist hypothesis testing are similar, with the key difference being (again) the use of a prior 
- ERM gives a formal probabilistic argument for optimal loss functions in supervised learning
