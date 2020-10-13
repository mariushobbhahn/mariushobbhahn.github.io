---
layout:     post
title:      "The Laplace Bridge for Bayesian Neural Networks"
subtitle:   "Easy-to-understand summary of our paper: Fast Predictive Uncertainty for Classification with Bayesian Deep Networks"
date:       2020-09-06 20:28:00
author:     "Marius Hobbhahn"
# header-img: "img/Marius2.jpg"
category:   ML_project
tags:       [Machine Learning, Laplace Bridge]
---
## **What is the paper about?**

Bayesian inference in Neural Networks is usually very costly. However it is often desirable because it yields distributions as outputs instead of just point estimates. This paper is one step in the right direction to make Bayesian inference faster by improving one part of the pipeline significantly. In the following figure you can see that we approximate the output distribution with a Dirichlet via the Laplace Bridge instead of sampling from the distribution of logits and applying the softmax function. While this might look like a small change it turns out to be a pretty drastic speed up for this step of the inference and has a non-negligble effect on the overall prediction time while providing similar quality estimates. Additionally it yields a fully parameterized distribution instead of just samples. 

TODO: summary figure

The paper can be found here: TODO arxiv link

The accompanying code is available here: TODO git repo link

## Motivation

Neural Networks usually yield point estimates as outputs. In an image classification task the network could say, for example, that the test image shows a dog with 75 percent probability. However, it does not give us an estimate of the uncertainty which is attached to this estimate. The network could either be very certain that this is an image that warrants a 75 percent probability for the class dog or it could be like "meh, I don't know, probably a dog" or anything in between. Especially in safety-critical applications this notion of uncertainty becomes more relevant. If you want a network to detect cancer through images you might also be interested in its uncertainty. If for example the network estimates the probability for skin cancer lower than for no skin cancer but has high uncertainty you might want a human to double-check the images to make sure the detection worked correctly. Similarly, in a self-driving car, you might want to have certain safety mechanisms when the classification for pedestrian has high uncertainty even when the mode of the estimate is high. 

Unfortunately though getting these distributions is usually associated with high computational costs. Either expensive operations have to be performed such as the computation of the Hessian or any of its many approximations or samples have to be drawn from different parts of the network. The Laplace Bridge (LB) for Bayesian Neural Networks (BNN) avoids the sampling process by providing a closed-form approximation of the posterior distribution and thereby speeds up a relevant part of the prediction process.

## Theory

Before we get into the details of its application to BNNs we first have to understand the Laplace Bridge

### The Laplace Bridge

Two pieces of background information are very important to understand the LB. 

**Change of Variable for PDFs:** TODO

**Laplace Approximation:** TODO

The last observation on our way to the Laplace Bridge is that a Dirichlet Distribution looks very much like a Gaussian when you change its variable via the softmax transformation $$\pi(x) = \frac{\exp(x_i)}{\sum_j \exp(x_j)}$$. This can be seen visually in the following figure which contains the one-dimensional special case of the Dirichlet, the Beta distribution. We compare the Dirichlet in the standard base (left) and in the softmax base after applying the change of variable (right). 

TODO:figure

Now, we can apply a Laplace approximation in both bases to fit a Gaussian to the distribution. We can additionally transform the Gaussian from the Laplace approximation in the softmax basis back to the standard basis and find that it is a better fit than the Laplace Approximation in the standard base. 

TODO:figure

Furthermore the Laplace approximation in the standard base is not always possible. When the Beta distribution encounters parameters that are smaller or equal to 1 it doesn't have a well-defined mode anymore and a Gaussian can't be fit (see the red line in the left figure). However, the same function with the same parameters can be fit in the softmax basis and this fit can also be transformed back to the original base (see red line in middle and right figure). 


### LB applied to BNNs

## Experiments


## Conclusions

#### ***One last note***

If you have any feedback regarding anything (i.e. layout, code, or opinions) please tell me in a constructive manner via your preferred means of communication.

