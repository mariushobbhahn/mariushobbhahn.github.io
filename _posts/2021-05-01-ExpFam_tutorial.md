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

Exponential family distributions are important for many classical machine learning application. Their properties form the basis of Expectation Propagation and they are often used in hierarchical probabilistic models. Because of this they are well-documented and many tutorials exist. Most resources on exponential families are rather math-heavy and many people learn best with this approach. However, I personally think and learn primarily by thinking **visually** and others do too. Thus I want to provide a tutorial on exponential families and some of their properties with a focus on visual interpretations whenever possible and refer to other sources for most of the math. 

## The Basics

A probability density function (pdf) that can be written in the form 

\begin{align}\label{EF}
p(x) &= h(x)\cdot \exp\left(w^\top \phi(x) - \log Z(w) \right) \\
\qquad\text{where}\qquad Z(w)&:= \int_{\mathbf{X}} \exp\left(w^\top \phi(x)\right) \,dh(x)
\end{align}

is called an exponential family where $$\phi(x): \mathbb{X} \rightarrow \mathbb{R}^d$$ is called sufficient statistics, $$w \in \mathcal{D} \subseteq \mathbb{R}^d$$: natural parameters where $$\mathcal{D}$$ is the domain of valid parameters, $$\log Z(w): \mathbb{R}^d \rightarrow \mathbb{R}$$: (log) partition function (normalization constant), and $$h(x): \mathbb{X} \rightarrow \mathbb{R}_{+}$$: base measure.

Many distributions can be written as exponential families (see e.g. <a href='https://en.wikipedia.org/wiki/Exponential_family'>Wikipedia</a>). Some of them most prominent ones are the Normal, Beta and Gamma distribution which are displayed for three sets of parameters respectively in the following figure.

<figure>
  <img src="/img/ExpFam_Vis/normal_beta_gamma.png"/>
</figure>

The **sufficient statistics** are the statistics of the data that tell you everything interesting about them, i.e. if you know the sufficient statistics another person with the same data is unable to tell more about the probability distribution than you are. For the normal distribution the sufficient statistics are $$Y_1 = \sum_i X_i$$ and $$Y_2 = \sum_i X_i^2$$ for samples $$X_i, i=1,...,N$$. 
With $$Y_1$$ and $$Y_2$$ we can compute 

\begin{align}
   M &= 1/n Y_1 \\
   S^2 &= \frac{Y_2 - (Y_1^2/n)}{n-1} = \frac{1}{n-1} \left[\sum_i X_i^2 - n\overline{X}^2\right] 
\end{align}

to rediscover the mean and standard deviation which are also sufficient estimators of the normal distribution. 

<figure>
  <img src="/img/ExpFam_Vis/suff_stats_normal.png"/>
</figure>

The **natural parameters** are the set of parameters $$w$$ for which $$p(x)$$ is defined. They are related to but usually not the same as the parameters of the probability distribution. The parameters of the normal distribution, for example, are its mean $$\mu$$ and standard deviation $$\sigma$$. Its natural parameters, however, are $$w_1 = \frac{\mu}{\sigma^2}$$ and $$w_2 = -\frac{1}{2\sigma^2}$$. 

The **base measure** is the most fuzzy part of exponential families in my experience. This is because I can arbitrarily shift values between the natural parameters and the base measure. For example, the following three equations are all possible legitimate definitions of the Beta distribution in exponential family form. 

TODO example of the Beta distribution. 

However, the most reasonable definition is one where we push all "left-over" parts from the natural parameters into the base measure, e.g. the $$-1$$ terms in the Beta distribution. The reason why it is called "base-measure" is that if you set your natural parameters $$w$$ to 0, everything that's left is your base. Similarly, you could say that changing your natural parameters $$w$$ can be seen as updating your base measure $$h(x)$$. 

The **log-partition function:** is the most underrated part of exponential families in my opinion. In the beginning I perceived it as "just a normalizing constant" such that your distribution integrates to 1. However, the fact that it is available in closed form combined with the structure of exponential families yields very powerful properties. I will discuss them further down in more detail but, in short, the log partition function allows for efficient computation of the moments through derivation instead of integration. This is a game changer because derivation is usually much easier than integration. To understand the normalizing effect of the log partition function consider the following figure where the TODO distribution has been plotted with and without the normalizing constant. 
TODO: equations of pdfs with and without Z. 

<figure>
  <img src="/img/ExpFam_Vis/log_partition_gamma.png"/>
</figure>

If you want to find the natural parameters $$w$$, sufficient statistics $$\phi(x)$$, base-measure $$h(x)$$ or log partition function $$\log Z(w)$$ and don't want to calculate them by hand, you can find a large table of them on <a href='https://en.wikipedia.org/wiki/Exponential_family#Table_of_distributions'>Wikipedia</a>. 

## Important Properties

Exponential Families have a lot of interesting properties. I chose a small selection of those that I find most important. Since I come from a Machine Learning background, you will find a biased selection.

### Multiplication and Division

Due to the properties of the exponential function, the multiplication and division of exponential family PDFs can be done in closed form as long as the resulting natural parameters are valid. If we have an exponential family with two different parameterizations $$w_1$$ and $$w_2$$. Then we can write

$$\begin{align}
p_1(x) \cdot p_2(x) &= \frac{1}{Z} \exp((w_1 + c) \phi(x)) \cdot \frac{1}{Z} \exp((w_2 + c) \phi(x)) \\
	&= \frac{1}{Z'} \exp((w' + c') \phi(x))
\end{align}$$

which is again in the form of the same exponential family. A similar result can be derived for division just that $$w' = w_1 - w_2$$ instead of $$w' = w_1 + w_2$$. Of course, the $$w'$$ have to be valid parameters, e.g. the variance of a Gaussian cannot be negative. To see this property visually for the Beta and Normal distribution consider the following figure.

<figure>
  <img src="/img/ExpFam_Vis/beta_normal_mult_div.png"/>
</figure>

The true distributions have been computed by multiplying/dividing distribution 1 and 2 and re-normalizing the results. The update rule for the Beta distribution is simply $$a' = a1 + a2 -1$$ and for the Gaussian distribution $$\mu' = \frac{\mu_1 \sigma_2^2 - \mu_2 \sigma_1^2}{\sigma_1^2 + \sigma_2^2}$$ and $$\sigma' = \sqrt{\frac{1}{\frac{1}{\sigma_1^2} - \frac{1}{\sigma_2^2}}}$$. 

While this looks like a small and irrelevant property it is actually very important. It implies that we can update the parameters of distributions in very little time instead of computing costly approximations. This properties is also the foundation of a the famous Machine Learning technique called <a href='https://tminka.github.io/papers/ep/roadmap.html'>Expectation Propagation</a>. 

### Conjugacy

If you have data of a certain type, e.g. Bernoulli, then there often is an exponential family conjugate prior distribution, e.g. the Beta. This means, that you can compute the posterior distribution by updating the parameters of the prior distribution through simple addition $$w' = w_0 + f(x)$$ for data $$x$$ where $$f(x)$$ is a cheap and simple function. This is very powerful, since it enables very fast Bayesian inference with exponential families without the need for costly approximations such as sampling. 

TODO bayes theorem and explanation better.

I think conjugacy can be easiest understood in visual terms. Thus, in the following, you can see how different data types update their respective conjugate priors. The figures on the left contain the conjugate distribution and the figure on the right is used to generate the data. 

TODO: do EFs always have conjugate priors?

If you find the speed of the GIF to high or low or want to pause it at some point you can always just pull the github repo TODO:link and look at all individual figures. 

#### Beta

The Beta distribution describes beliefs about a probability, thus it is plausibly the conjugate prior to <a href='https://en.wikipedia.org/wiki/Bernoulli_distribution'>Bernoulli</a> and <a href='https://en.wikipedia.org/wiki/Binomial_distribution'>Binomial</a> likelihoods. In both cases we start with a flat Beta prior, i.e. $$\alpha=\beta=1$$. On the right hand side, the distributions of the likelihood are shown in blue and the samples that simulate our data are drawn in black. Per step we draw one sample and update our current Beta distribution accordingly. 

For the Bernoulli likelihood this means we compute $$\alpha' = \alpha + \sum_i x_i$$ and $$\beta' = \beta + n - \sum_i x_i$$, i.e. we add 1 to $$\alpha$$ for every success and 1 to $$\beta$$ for every failure. 

![](/img/ExpFam_Vis/Beta_Bernoulli.gif)

For the Binomial likelihood we compute $$\alpha' = \alpha + \sum_i x_i$$ and $$\beta' = \beta + \sum_i N_i - \sum_i x_i$$. 

![](/img/ExpFam_Vis/Beta_Binomial.gif)

The posterior updates have a very intuitive interpretation. If we have more data the Beta mean gets closer to the true probability and its uncertainty decreases. The more coinflips we see the better we know its bias and the more certain we become. 

#### Mean of a Normal (with known variance)

The conjugate prior for the **mean** of a Gaussian (**not** the entire Gaussian distribution) is a Gaussian. In other words, the more data points you have from a Gaussian distribution the more certain you are about its mean. 

TODO update equation

TODO GIF for normal

Our goal is to estimate the mean of the Gaussian distribution on the right, i.e. the red line. In the beginning we have no clue about its position and start with a standard normal prior (blue line on the left). The more samples (black) we see from the true distribution, the more our posterior estimate for the mean (red line on the left) gets closer to the true mean and its variance decreases. 

#### Gamma

The Gamma is a distribution over positive quantities. It is a conjugate prior to the rate parameter of<a href='https://en.wikipedia.org/wiki/Poisson_distribution'>Poisson</a> likelihoods, which are discrete distributions over rare events, e.g. earth quakes. So if you have count data of earth quakes and you assume them to be generated by a Poisson distribution you can get a posterior distribution over its rate parameter with $$\alpha' = \alpha + \sum_i x_i$$ and $$\beta' = beta + n$$

TODO: GIF for Gamma with Poisson

We find that with more data the posterior distribution over the $$\lambda$$ rate parameter gets closer to the true value of 0.5 and the uncertainty decreases. 

#### Dirichlet

Similar to how the Beta distribution describes believes about one probability, the Dirichlet describes beliefs about a probability vector. It is a conjugate prior to categorical and multinomial likelihoods. Let's say, for example, we have three categories (or types) of texts: politics, finance and sports and we read a newspaper containing three texts every day. They can contain multiple texts of the same type. Then we might be interested in which kind of focus the publisher has, i.e. what the generating distribution for the texts is. Every individual newspaper can be modelled by a Binomial distribution with $$n=3$$. The generating can be modelled by a Dirichlet and updated with $$\alpha' = \alpha + \sum_i x_i$$.

TODO GIF

We can see that the mean of the posterior Dirichlet function gets ever closer to the true probabilities generating the Binomial likelihoods and that the uncertainty of our estimate decreases. In our metaphor this means that after seeing 10 individual newspapers we think that the outlet focuses mostly on politics (60%), a bit on finance (25%) and even less on sports (15%). 

#### Inverse Wishart

The inverse Wishart is a distribution over symmetric positive semi-definite matrices. It is a conjugate prior to empirical covariance matrices, e.g. the outer product of vectors drawn from a Gaussian. I always found it hard to get a good grasp of the inverse Wishart distribution and thus first want to introduce it in slightly more detail than the other distributions so far. 

First of all, the inverse Wishart (and the Wishart) distribution is defined on the symmetric positive semi-definite (psd) cone. The psd cone is a subspace of $$\mathbb{R}^d$$ on which all psd matrices lie. A real symmetric matrix $$\begin{pmatrix} a & b \\ b & c \end{pmatrix}$$ is psd iff $$a, c \geq 0$$ and $$ac - b^2 \geq 0$$. following <a href='https://math.stackexchange.com/questions/1875462/how-to-plot-the-psd-cone-in-matlab'>this stackoverflow post</a>, we will represent this by $$(a, b, c) \in \mathbb{R}^3$$. If we set $$a=1$$ then $$c \geq b^2$$ and if we set $$c=1$$ then $$a \geq b^2$$. So if we plot $$(a,b,c) = (1, b, b^2)$$ and $$(a,b,c) = (b^2, b, 1)$$ for $$-1 \leq y \leq 1$$ resptively and join these points with $$(0,0,0)$$ we start to see the cone. 

TODO: plot psd cone.

It is very hard to plot the density of a probability distribution on this cone. Thus we have to revert to other strategies to plot the Wishart distribution. I will use three different tools to plot the Wishart distribution. The first requires a bit of math. For off diagonal elements of a symmetric psd matrix $$A$$ it holds $$a_{ij}^2 \leq a_{ii} a_{jj}$$ (see e.g. <a href='https://math.stackexchange.com/questions/3018639/off-diagonal-entries-of-a-symmetric-positive-semi-definite-matrix-prove-a-ij'>here</a>). Thus for our 2-dimensional case we know that $$b = \rho \cdot \sqrt{ac}$$ for $$\rho \in (-1, 1)$$. So one way to visualize the Wishart is to plot marginals for different values of $$\rho$$ with increasing $$a$$ and $$c$$. The resulting plot looks like this

TODO image

where TODO: what is red and what is blue? What does it means that they are not the same? 

The second and third tool are simpler. The (inverse-) Wishart distribution has a scale matrix parameter $$\Psi$$ which we can plot as a 2x2 heatmap to show the size of the individual entries. The last method is just plotting histograms over $$a,b$$ and $$c$$ for samples drawn from the (inverse-) Wishart. 

To visualize the likelihood we draw samples from a 2-dimensional Gaussian and compute their outer products. The update rules for the inverse Wishart are $$\Psi' = Psi + \sum_i x_i x_i^\top$$ and $\nu' = \nu + n$$. 

Combining all this we can inspect how the Wishart distribution behaves when updated with Gaussian outer product likelihoods. 

TODO GIF

In our first visualization (top left) we find that a) larger values of $$n$$ and $$\Psi$$ imply more probability mass for larger values of $$a$$ and $$c$$. b) The diagonal entries of $$\Psi$$ are equivalent in the beginning, i.e. they are both one and thus $$-\rho$$ and $$+\rho$$ yield the same marginal distribution. After some updates the diagonal values of $$\Psi$$ are different and thus $$\rho$$ and $$+\rho$$ yield different marginal distributions. TODO: is more mass where larger values are?

In the second visualization (bottom left) we mostly see how the values of the scale matrix $$\Psi$$ get larger over time. 

In the third visualization (bottom right) we find that the histograms of $$a,b$$ and $$c$$ for 1000 samples of the Wishart get narrower over time. This shows how the uncertainty decreases and we get more and more certain about the underlying psd matrix. 

### Moment calculation

TODO: how to visualize this? <- just plot mean and variance? & also log exp. and variance?

what about moment matching and EP?

Useful for Max. LLH & Fisher Information <- TODO understand

### Moment Matching

TODO: KL divergence is minimized for matching moments. 

## Conclusion

When I first learned of exponential families I thought "It's just a different way to write probability densities, why does it matter?". But after working on and reading about their properties for about a year now, I learned that they are much more powerful. Exponential families have conjugate priors and thus we can compute posteriors in closed form. If you have ever approximated distributions by sampling from the posterior you know how large the difference in speed is. Furthermore, exponential families are "closed" under multiplication and division which - once again - implies fast computations. Their normalizing constants (the log-partition function) is available in closed-form. Therefore we can compute their moments through differentiation instead of integration saving us a lot of pain. On a related note, we can show that the KL-divergence between two exponential families is minimized by matching their moments. Overall, a seemingly simply way to write different probability density functions has pretty large implications and yield the foundations of different algorithms for Bayesian generalized linear models (GLMs), Expectation Propagation and many more. 

TODO rest

My own research is closely linked to exponential families. Maybe you are interested in
1. A cool trick in Bayesian neural networks TODO link blog and arxiv
2. TODO the GLM stuff
3. TBA

#### ***One last note***

If you want to get informed about new posts you can <a href='http://www.mariushobbhahn.com/subscribe/'>subscribe to my mailing list</a> or <a href='https://twitter.com/MariusHobbhahn'>follow me on Twitter</a>.

If you have any feedback regarding anything (i.e. layout or opinions) please tell me in a constructive manner via your preferred means of communication.


