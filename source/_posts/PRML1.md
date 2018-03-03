---
title: PRML阅读笔记1
date: 2014-01-27 21:09:34
tags:
- 阅读
- 技术
- Machine Learning
---
最近刚刚看完Ng的machine learning，想再加一点料，于是拿起PRML，开始啃。。。

第一章：

Polynomial Curve Fitting:

-   regression, error function, RMS(root-mean-square),overfitting

Probability Theory:

-   many distribution.....
-   frequentist: think parameter exist, we just need to find it
-   Bayesian: think paremter is random variable, we need to take its distribution into account
-   frequentist and Bayesian diff in prior of parameter
-   curve fitting(probability aspect): model P(x|w) --> error function, model P(w|x) by Bayesian --> RMS
-   Bayesian curve fitting: integrate all w

Model selection:(pass)

Curse of Dimensionality:(pass)

Decision Theory:

-   Minimize misclassification rate, minimize expected loss, reject option(set threshold)
-   three type:generative model(model p(x|y)), discriminative model, no probability

Information Theory:(pass)

  

import views:

1\. frequentist and Bayesian

2\. regulation

3\. regression on probability view and non-probability view

4\. generative model, discriminative model, no probability
