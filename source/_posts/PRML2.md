---
title: PRML阅读笔记2
date: 2014-01-29 10:09:34
tags:
- 阅读
- 技术
- Machine Learning
---

继续PRML  

第二章：

Binary Variables:

-   Bernouli Distribution, binomial distribution
-   conjugate prior --> beta distribution

<!--more-->
Multinomial Variables:

-   multinomial distribution
-   conjugate prior --> Dirichlet distribution

The Gaussian Distribution:

-   univariate, multivariate, shape, limit
-   conditional Gaussian, Marginal Gaussian, Bayes' theorem
-   Maximum likelihood, sequential estimation
-   conjugate prior --> unknown mean, unknown variance, and both
-   Mixtures of Gaussians

The exponential Family:

-   Bernoulli distribution --> logistic sigmoid function
-   Multinomilal distribution --> softmax function
-   conjugate priors

Nonparametric Methods:

-   histogram approach: p(i) = n(i) / (N * width of bin)
-   p(x) = K/NV: fix V and find K --> Kernel Estimator . fix K and find V --> K-nearest-nerghbour estimator
-   Kernel Estimator: estimate new data x according to old datas in V
-   K-nearest-nerghbour estimator: estimate new data x according to neighbors within K

  

import views:

1\. posterior = prior * ML

2\. conjugate prior

3\. sequential model to deal with large dataset(update data with disgarding the old data)

4\. Gaussian Distribution and its variation

5\. nonparametic method

6\. hyperparameter: to model the distribution of parameter
