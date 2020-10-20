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

<figure>
  <img src="/img/LB_for_BNNs/TODO"/>
</figure>

The paper can be found here: TODO arxiv link

The accompanying code is available here: TODO git repo link

## Motivation

Neural Networks usually yield point estimates as outputs. In an image classification task the network could say, for example, that the test image shows a dog with 75 percent probability. However, it does not give us an estimate of the uncertainty which is attached to this estimate. The network could either be very certain that this is an image that warrants a 75 percent probability for the class dog or it could be like "meh, I don't know, probably a dog" or anything in between. Especially in safety-critical applications this notion of uncertainty becomes more relevant. If you want a network to detect cancer through images you might also be interested in its uncertainty. If for example the network estimates the probability for skin cancer lower than for no skin cancer but has high uncertainty you might want a human to double-check the images to make sure the detection worked correctly. Similarly, in a self-driving car, you might want to have certain safety mechanisms when the classification for pedestrian has high uncertainty even when the mode of the estimate is high. 

Unfortunately though getting these distributions is usually associated with high computational costs. Either expensive operations have to be performed such as the computation of the Hessian or any of its many approximations or samples have to be drawn from different parts of the network. The Laplace Bridge (LB) for Bayesian Neural Networks (BNN) avoids the sampling process by providing a closed-form approximation of the posterior distribution and thereby speeds up a relevant part of the prediction process.

## Theory

Before we get into the details of its application to BNNs we first have to understand the Laplace Bridge

### The Laplace Bridge

Two pieces of background information are very important to understand the LB. 

**Change of Variable for PDFs:** Every probability distribution $p(x)$ can be represented in a different base $y$ by transforming its variable with $g(x)$ and multiplying it with the Jacobian of the inverse transformation to ensure that the distribution still integrates to 1. In equations this means
$$p_y(y) = p_x(g^{-1}(x)) \det\left(\frac{\partial g^{-1}(x)}{\partial y}\right)$$
For a simplified intuition you can think of the change of variable as stretching or shrinking the distribution in a potentially non-linear way. 

**Laplace Approximation:** A common way to approximate a function with a normal distribution is by using a Laplace approximation. This is done by using the mode of the function as the mean of the Normal $\mu = \argmax_x p(x)$ and the covariance matrix as the invere Hessian $\Sigma = \frac{\partial^2 f(x)}{\partial^2 x}$. The approximation comes from 

TODO: derivation

TODO: more text for Laplace Bridge & Dirichlet in math terms

The last observation on our way to the Laplace Bridge is that a Dirichlet Distribution looks very much like a Gaussian when you change its variable via the softmax transformation $$\pi(x) = \frac{\exp(x_i)}{\sum_j \exp(x_j)}$$. This can be seen visually in the following figure which contains the one-dimensional special case of the Dirichlet, the Beta distribution. We compare the Dirichlet in the standard base (left) and in the softmax base after applying the change of variable (right). 

<figure>
  <img src="/img/LB_for_BNNs/TODO"/>
</figure>

Now, we can apply a Laplace approximation in both bases to fit a Gaussian to the distribution. We can additionally transform the Gaussian from the Laplace approximation in the softmax basis back to the standard basis and find that it is a better fit than the Laplace Approximation in the standard base. 

<figure>
  <img src="/img/LB_for_BNNs/TODO"/>
</figure>

Furthermore the Laplace approximation in the standard base is not always possible. When the Beta distribution encounters parameters that are smaller or equal to 1 it doesn't have a well-defined mode anymore and a Gaussian can't be fit (see the red line in the left figure). However, the same function with the same parameters can be fit in the softmax basis and this fit can also be transformed back to the original base (see red line in middle and right figure). 

Lastly, I want to present a sanity check for the Laplace Bridge and its application to Bayesian Neural Networks. In the following figure you can see five different scenarios of 3-dimensional Gaussians mapped through the Laplace Bridge. In the upper row are samples drawn from the Gaussian to which the softmax was applied. In the bottom row they values of the original Gaussian are mapped by the Laplace Bridge.

TODO: figure with 5 3D comparisons

We firstly find that the LB is an imperfect but sufficiently good map, i.e. we can see small differences but the two rows look mostly similar. Secondly, the parameters of the Gaussian have been chosen to stress important ideas. Case a) and b) have the same mean but different covariance matrices. This further emphasizes the need for a Bayesian interpretation of Machine Learning. Using the mode or mean as point estimate would treat a) and b) similarly even though the respective uncertainties are clearly different. Szenarios c), d) and e) show similar means with increasing uncertainty. This case was chosen to show that this change of uncertainty in the original Gaussian is successfully mapped through the Laplace Bridge to further convince us that it is worth considering for practical applications. 

TODO: summary figure(?)

### LB applied to BNNs

In the context of Bayesian Neural Networks, one possibility to generate your distribution of the outputs is to estimate a Gaussian of the logits, then draw samples from it and apply the softmax to each samples individually. There are other possibilities to estimate an output distribution but sampling is commonly used as it's a cheap and easy to use method. Applying a softmax to a Gaussian does not yield a closed-form solution and drawing samples is therefore the only possible way to estimate the true posterior. However, since we want a to transform a distribution in logit-space $\mathbb{R}^D$ to a distribution in probability space $\mathbb{P}^{D}$ using the Laplace Bridge seems like a good option to get rid of the expensive sampling step. To get a visual intuition where exactly we apply the LB consider the following figure.

TODO: figure with explanation where the LB is applied

## Experiments

From the framing of the paper so far, I think three questions arise quite naturally: a) How good is the approximation in the context of BNNs?, b) How much faster is it compared to sampling?, and c) Are there use-cases for a Dirichlet distribution that do not exist for a distribution of samples. The experiments aim to answer these questions in chronological order.

### Out-of-Distribution Experiments

Naturally, when we have a new approximation, we want to know how good its quality is. Since one of the main use-cases of output distributions is out-of-distribution (OOD) detection we tested it first. We use a Laplace approximation of the network to generate our Gaussians over the logits. This becomes computationally expensive very quickly for larger networks and we therefore apply a last-layer Laplace approximation for all but the (F-, K-, not-)MNIST experiments. The last-layer Laplace approximation has been shown to yield pretty good uncertainty estimates (TODO:references) but is also very much in the spirit of this paper as we want to get a reasonably good uncertainty estimate very quickly. We compare the mean of the Dirichlet from the LB on a standard benchmark suite for OOD detection comparing two scenarios. In the first one the Hessian of the Gaussian to yield the covariance matrix is computed via a diagonal approximation and in the second scenario via a Kronecker factorized approximation which usually yields slightly better OOD detection results. Additionally we measure the time it takes to draw 1000 samples from the Gaussian and apply the softmax vs. the Laplace Bridge. Even though the 1000 samples are unusually high they are motivated by the results from the second experiments. 

TODO: figure with results. 

We find multiple interesting results: a) The LB seems to beat diagonal sampling and draw even with KFAC sampling on average as indicated by the number of black numbers in the respective columns. b) The LB is much faster than sampling methods. More specifically, it takes around 400 times as much to sample than to apply the LB. c) The results for the LB are pretty similar between the two conditions. This is likely due to the fact that it is an imperfect transformation and therefore only uses the diagonal entries of the Gaussian which is probably its biggest weakness. Overall though, it is clear that the LB is a really fast and pretty high quality substition for sampling based methods of predictive uncertainty. 

We are not the first to apply a fast method to approximate the integral of a softmax-Gaussian. There are two other approaches that we want to compare the LB to in the following. 

TODO: compare to other approaches. 

TODO: conclusion of first experiment.

### Timing Experiments

As our main priority is achieving fast predictive uncertainty in BNNs there we want to firstly find out what the trade-off between accuracy and speed of the LB is. For that we consider the KL divergence between the Dirichlet resulting from the LB with the true distribution to the KL diverence from samples to the true distribution where the true distribution is approximated by MCMC with 100k samples. We compare the KL divergences for three different samples of Gaussian dists depending on the number of samples (left) and the actual wall-clock time needed for the computations (right)

TODO: figure. 

We find that it takes between 750 and 10k samples to achieve the same KL divergence to the true distribution as the LB (which is the motivation for taking 1000 samples for the OOD experiments) and around TODO:timings much longer to get the same accuracy. This further indicates that we should use the LB if our goal is to maximize speed while accepting a small but fixed drop in quality. 

Another question is how much this speed-up does in the grand scheme of things. After all, if the last step would only make one percent of the entire costs there would be no large benefit in improving it. To test these timings we measure the time it takes to do one forward pass and compare it with the time for the final prediction for sampling and the LB. We use a ResNet-18 with last-layer Laplace approximation for the CIFAR10 dataset. We compare the times it takes to draw 10, 100, or 1000 samples from the Gaussian. 

TODO: figure.

We find that TODO: results

Lastly, one could assume that computing the mean and covariance matrix for the Laplace approximation is too costly and this approach is therefore overall not applicable. However, with fast computational tools such as BACKpack (TODO:cite), which is a fast automatic differentiation tool on top of PyTorch, we can compute the uncertainties at the cost of one backward pass. TODO: describe rest of the training with times, etc.

### Uncertainty-aware top-k

The performance of image classification networks in the context of ImageNet which is a large dataset with 1000 classes is often measure along a top-1 and a top-5 metric. While it seems plausible to not only look at the highest rated estimate but also the following ones the specific number of five seems both arbitrary and pretty inflexible. We can, for example, easily think of situations where this is either too large or too small of a number. Imagine a scenario in which your network receives the image of a fish and decides it is one of the ten possible fish species available in the training data but can't decide between them. Then it is a coin flip if the correct class is in your top-5. If, on the other hand, the network is pretty sure that the image either belongs to the class "eagle" or "hawk" then the three remaining classes within the top-5 don't add any value to the classification. What we would want is a more flexible solution that includes the networks own uncertainty estimates to create a border between possible candidates and unlikely estimates. We use the Dirichlet resulting from the LB to construct an uncertainty-aware top-k metric. Marginal distributions of the Dirichlet are Dirichlets again and can be computed in closed-form by TODO:equation. Importantly, this means we can estimate a marginal Beta distribution (the 1D special case of the Dirichlet) for every single class in a given prediction. We can use the overlap between sortet estimates to decide whether they are in the or outside of the top-k estimate similar to T-tests or their Bayesian equivalents. For example, we could say that all classes that have a five percent overlap to the next class are inside the estimate. This concept is illustrated with the following figure.

TODO: figure

TODO: findings. 



## Conclusions

It's not a revolution but it makes sense in some or many cases. 

#### ***One last note***

If you have any feedback regarding anything (i.e. layout, code, or opinions) please tell me in a constructive manner via your preferred means of communication.

