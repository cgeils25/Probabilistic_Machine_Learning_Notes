# 6 - Information Theory

This chapter covers some basic principles of information theory.

## Entropy 

**Entropy** is a measure of the level of uncertainty, or the amount of *information* in a collection of data samples. 

For discrete RVs with some distribution over a set of K classes, it is defined as 

$$
\mathbb{H}(X) = -\sum_{k = 1}^K{p(X = k)\log_2(p(X = k))}
$$

which can also be rewritten as $-\mathbb{E}[\log_2(p(X))]$ (just by the definition of expected values). For a bernoulli, this quantity is maximized at $\theta = .5$, which makes sense since at that point there would be the most uncertainty about whether the event will be a success or failure (by contrast, there is *no* uncertainty and $\mathbb{H} = 0$ when $\theta = 1 \; \text{or} \; 0$)


**Cross Entropy** is effectively a measure of how different two distributions. For dists. p and q:

$$
\mathbb(p, q) = -\sum_{k=1}^K{p_k \log_2(q_k)}
$$

The **Joint Entropy** of distributions for RVs X and Y is just the entropy of their joint distribution, and is upper-bounded by the total of their entropies.

The **Conditional Entropy** describes how our uncertainty about some distribution is affected by observing some other RV. The main takeaway is that conditioning on some new data never decreases our uncertainty - aka looking at the data is always a good thing.

**Perplexity** measures how predictable the data sampled from a distribution is, and is defined as:

$$
\text{perplexity}(p) = 2^{\mathbb{H}(p)}
$$

where logically it will be maximized for $\mathbb{H} = 0$, and will decrease as $\mathbb{H}$ increases.

## Kullback-Leibler (KL) Divergence

KL divergence serves a similar purpose to cross entropy in that it measures how different two distributions are, although it is a formal distance metric. It is defined as:

$$
\mathbb{KL}(p || q) \equiv \sum_{k=1}^K{p_k \log_2\frac{p_k}{q_k}}
$$

for discrete distributions and 

$$
\mathbb{KL}(p || q) \equiv \int{p(x) \log_2\frac{p(x)}{q(x)}}dx
$$

## Mutual Information (MI)

MI measures how dependent two distributions are. Naturally, we need to know their joint in order to compute this:

$$
\mathbb{I}(X; Y) \equiv \mathbb{KL}(p(x, y) \; || \; p(x)p(y))
$$

It intuitively makes sense that a measure of dependence would involve computing how different the joint and multiplied marginals are. For independent distributions, there will be no difference, since the two are equal by definition.

## Summary

- information theory attempts to understand data distributions in terms of how much "information" they contain
- entropy is a measure of uncertainty in a distribution
- KL divergence measures how different two distributions are
- mutual information measures how dependent two distributions are
