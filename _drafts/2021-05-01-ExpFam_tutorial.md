---
layout:     post
title:      "(Visual) Tutorial on Exponential Families"
subtitle:   "With special focus on Conjugacy and Moments"
date:       2021-03-01 20:28:00
author:     "Marius Hobbhahn"
header-img: "img/img-headers/TODO"
category:   opinion
tags:       [Machine Learning]
---

## **What is this post about?**

Exponential family distributions are important for many classical machine learning application. Their properties form the basis of Expectation Propagation and they are often used in hierarchical probabilistic models. Because of this they are well-documented and many tutorials exist. Most resources on exponential families are rather math-heavy and many people learn best with this approach. However, I personally think and learn primarily by thinking **visually** and others do too. Thus I want to provide a tutorial on exponential families and some of their properties with a focus on visual interpretations. 

TODO: examples: Beta, Gamma, Normal

## The Basics

A probability density function (pdf) that can be written in the form 
\begin{align}\label{EF}
p(x) &= h(x)\cdot \exp\left(w^\top \phi(x) - \log Z(w) \right) \\
\qquad\text{where}\qquad Z(w)&:= \int_{\mathbf{X}} \exp\left(w^\top \phi(x)\right) \,dh(x)
\end{align}
is called an exponential family where $\phi(x): \mathbb{X} \rightarrow \mathbb{R}^d$ is called sufficient statistics, $w \in \mathcal{D} \subseteq \mathbb{R}^d$: natural parameters where $\mathcal{D}$ is the domain of valid parameters, $\log Z(w): \mathbb{R}^d \rightarrow \mathbb{R}$: (log) partition function (normalization constant), and $h(x): \mathbb{X} \rightarrow \mathbb{R}_{+}$: base measure.

The **sufficient statistics** are the set of statistics of the data that tell you everything you are interested in. TODO
sufficient statistic: show normal samples -> need mean and std and know everything else about the data

The **natural parameters** are the set of values for which $$p(x)$$ is defined. They are related to but usually not the same as the parameters of the probability distribution. The parameters of the normal distribution are its mean $$\mu$$ and standard deviation $$\sigma$$. Its natural parameters, however, are $$w_1 = \frac{\mu}{\sigma^2}$$ and $$w_2 = -\frac{1}{2\sigma^2}$$. 

base measure: most optional part; depend on your parameterisation but can be thought of as left-overs

log-partition function: actually pretty important because known integral. 

TODO: figure of functions with and without their log-partition function


See Wikipedia table for more. 

## Important Properties

With a focus on relevance for ML.

### Multiplication and Division

TODO: closed under either

The foundation of EP

### Conjugacy

This is really nice. 

TODO make lots of nice GIFs showing conjugacy

#### Beta


#### Mean of a Normal (with known variance)

#### Gamma

Chi2 and inv-wishart are similar in nature

#### Dirichlet


#### Inverse Wishart

Wishart is similar in nature

Defined on the psd cone: make a GIF or plot of it. 

### Moment calculation

TODO: how to visualize this? <- just plot mean and variance? & also log exp. and variance?

Useful for Max. LLH & Fisher Information <- TODO understand

## Conclusion

Exp Fams are very powerful 

#### ***One last note***

If you want to get informed about new posts you can <a href='http://www.mariushobbhahn.com/subscribe/'>subscribe to my mailing list</a> or <a href='https://twitter.com/MariusHobbhahn'>follow me on Twitter</a>.

If you have any feedback regarding anything (i.e. layout or opinions) please tell me in a constructive manner via your preferred means of communication.


