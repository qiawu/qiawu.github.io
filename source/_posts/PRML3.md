---
title: PRML阅读笔记3
date: 2014-02-03 19:09:34
tags:
- 阅读
- 技术
- Machine Learning
---
继续啃PRML
第八章：
Basic notation:
node --> random variable or group of random variables
link --> probabilistic relation ship
notation of random var and non-random var, observed and unobserved var
Conditional Independence:
three example: block means independent conditionally
     1. tail-tail, observed(block), unobserved(unblock)
     2. head-tail, observed(block), unobserved(unblock)
     3. head-head, observed(unblock), unobserved(block)
D-separation theorm: regrard graph as filter for distribution p(x)
Markov blanket/Markov boundary
Directed graphical model --> Bayesian Networks:
Discrete variables: three ways to control number of parameters
     1. chain nodes
     2. sharing parameters
     3. model with latent parameter
Continues variables: Linear-Gaussian model
Undirected graphical model --> Markov random field：
conditional independence property in undirected graph
factorization property in directed graph
potential function and energy function
how to convert directed graph to undirected and vice versa
I map, D map, perfect map
Inference:
chain: using potential function, local messages pass to get an efficient algorithm
trees: undirected tree, directed tree, polytree, use efficient algorithm in a broader situation
factor graph:
translate directed and undirected graph to factor graph to become tree
sum-product algorithm: read it later
max-sum algorithm: read it later

important view:
1. Basic notation
2. Conditional property and factorization property
3. Directed graphical model --> Bayesian Networks, Undirected graphical model --> Markov random field
4. Inference in graphical model
