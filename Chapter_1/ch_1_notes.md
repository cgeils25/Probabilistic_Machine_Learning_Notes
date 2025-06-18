# 1 - Introduction

**Machine Learning** (ML) is a broad term that refers to any process where a computer improves its performance (P) on some task or tasks (T) as it gains experience (E).

## Types of ML

ML can be subdivided into 3 major learning paradigms:

1. **Supervised Learning** - the model represents a function ($\hat{f}$) that learns to predict a target (y) using features (X):

$$
\hat{f}(X) = \hat{y}
$$

Where $\hat{y}$ is the model's estimate of the true target y, optimized by minimizing some loss function $L(y, \hat{y})$.

2. **Unsupervised Learning** - There is no clear target. Instead, the model learns how features are distributed in such a way that it can be used to generate new data. 

3. **Reinforcement Learning** - The model serves the role of 'agent' which learns by receiving (possibly sparse) rewards or punishments as it interacts with its environment. 

Some considerations:

- supervised learning can generally be divided into regression (continuous output) and classification (categorical / discrete output)
- reinforcement learning is typically inefficient, since sparse rewards or punishment make th task of learning which 'actions' caused said outcomes difficult 
- collecting labels for supervised learning is expensive. Unsupervised learning is therefore a much more broadly applicable approach 

## Some Types of Data

In addition to the main types of learning, there are some necessary considerations with regard to the data, which form the input and (expected) output of the model.

Most classical ML models assume the input to be a 1-D vector, however certain types of data can't be meaningfully represented this way.

**Images** can be represented as high-dimensional tenors

**Text data** is considerably more complicated, with many possible representations, each with tradeoffs in terms of complexity, amount of information preserved, and size.

- *Bag of words* - essentially just a one-hot encoded vector where each bit is a '1' if that word is present
- *TF-IDF* - a transformed version of bag of words that takes into account relative frequencies of terms in documents while normalizing large counts with a log transform
- *Word Embeddings* - essentially just vectors assigned to each word. Similar words should have vectors pointing in similar directions. 

# Summary

- 3 types of learning: supervised, unsupervised, reinforcement learning
- many models assume a 1-D input, but for special cases some data can be represented with other shapes and passed as input to appropriate architectures
- machine learning is an outgrowth of statistics which focuses more on predictive performance and computation rather than theory
