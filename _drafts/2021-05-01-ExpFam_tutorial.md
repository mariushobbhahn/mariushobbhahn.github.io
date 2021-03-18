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

Exponential family distributions are important

Many people have written about them

Everyone else focuses on the math but the best way IMO is visually. 

TODO: examples: Beta, Gamma, Normal

## The Basics

Definition

4 subparts with plots if possible

sufficient statistic: show normal samples -> need mean and std and know everything else about the data

natural parameters: set of values for which p(x) is defined. Have to be positive

...: most optional part; depend on your parameterisation but can be though of as left-overs

log-partition function: actually pretty important because known integral. 

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


