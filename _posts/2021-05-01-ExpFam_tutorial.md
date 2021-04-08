---
layout:     post
title:      "A (visual) Tutorial on Exponential Families"
subtitle:   "With special focus on Machine Learning related properties"
date:       2021-03-01 20:28:00
author:     "Marius Hobbhahn"
header-img: "img/img-headers/TODO"
category:   
tags:       [Machine Learning]
---

## **What is this post about?**

Exponential family distributions are important for many classical machine learning application. Their properties form the basis of Expectation Propagation and they are often used in hierarchical probabilistic models. Because of this they are well-documented and many tutorials exist. Most resources on exponential families are rather math-heavy and many people learn best with this approach. However, I personally think and learn primarily by thinking **visually** and others do too. Thus I want to provide a tutorial on exponential families and some of their properties with a focus on visual interpretations whenever possible and refer to other sources for most of the math. 

## The Basics

A probability density function (pdf) that can be written in the form 

$$
\begin{aligned}\label{EF}
p(x) &= h(x)\cdot \exp\left(w^\top \phi(x) - \log Z(w) \right) \\
\qquad\text{where}\qquad Z(w)&:= \int h(x)\exp\left(w^\top \phi(x)\right) \,dx
\end{aligned}
$$

is called an exponential family where $$\phi(x): \mathbb{X} \rightarrow \mathbb{R}^d$$ is called sufficient statistics, $$w \in \mathcal{D} \subseteq \mathbb{R}^d$$: natural parameters where $$\mathcal{D}$$ is the domain of valid parameters, $$\log Z(w): \mathbb{R}^d \rightarrow \mathbb{R}$$: (log) partition function (normalization constant), and $$h(x): \mathbb{X} \rightarrow \mathbb{R}_{+}$$: base measure.

TODO: rephrase, too much where

Many distributions can be written as exponential families (see e.g. <a href='https://en.wikipedia.org/wiki/Exponential_family'>Wikipedia</a>). Some of them most prominent ones are the Normal, Beta and Gamma distribution which are displayed for three sets of parameters respectively in the following figure.

<figure>
  <img src="/img/ExpFam_Vis/normal_beta_gamma.png"/>
</figure>

The **sufficient statistics** are the statistics of the data that tell you everything interesting about them, i.e. if you know the sufficient statistics another person with the same data is unable to tell more about the probability distribution than you are. For the normal distribution, for example, the sufficient statistics are $$Y_1 = \sum_i X_i$$ and $$Y_2 = \sum_i X_i^2$$ for samples $$X_i, i=1,...,N$$. 
With $$Y_1$$ and $$Y_2$$ we can compute 

$$
\begin{aligned}
   M &= 1/n Y_1 \\
   S^2 &= \frac{Y_2 - (Y_1^2/n)}{n-1}  \\
   &= \frac{1}{n-1} \left[\sum_i X_i^2 - n\overline{X}^2\right] 
\end{aligned}
$$

to rediscover the mean and standard deviation which are also sufficient estimators of the normal distribution. 

<figure>
  <img src="/img/ExpFam_Vis/suff_stats_normal.png"/>
</figure>

The **natural parameters** are the set of parameters $$w$$ for which $$p(x)$$ is defined. They are related to (but usually not the same as) the parameters of the probability distribution. The parameters of the normal distribution, for example, are its mean $$\mu$$ and standard deviation $$\sigma$$. Its natural parameters, however, are $$w_1 = \frac{\mu}{\sigma^2}$$ and $$w_2 = -\frac{1}{2\sigma^2}$$. 

The **base measure** is the most fuzzy part of exponential families in my experience. This is because we can arbitrarily shift values between the natural parameters and the base measure. The following three equations, for example, are all possible legitimate definitions of the Beta distribution in exponential family form but they have different base measures and natural parameters.

$$
\begin{aligned}
	\mathcal{B}(x, \alpha, \beta) &= 1 \cdot \exp\left[(\alpha-1)\log(x) + (\beta-1)\log(1-x) - \log B(\alpha, \beta) \right] \\
	&= \frac{1}{x(x-1)} \exp\left[(\alpha)\log(x) + (\beta)\log(1-x) - \log B(\alpha, \beta) \right] \\
	&= \frac{1}{x^2(x-1)^2} \exp\left[(\alpha+1)\log(x) + (\beta+1)\log(1-x) - \log B(\alpha, \beta) \right]
\end{aligned}
$$

However, the most reasonable definition is one where we push all "left-over" parts from the natural parameters into the base measure, e.g. the $$-1$$ terms in the Beta distribution (see second equation above). The reason why it is called "base-measure" is that if you set your natural parameters $$w$$ to 0, only your base is left. Similarly, you could say that changing your natural parameters $$w$$ can be seen as updating your base measure $$h(x)$$. 

The **log partition function:** is the most underrated part of exponential families in my opinion. In the beginning I perceived it as "just a normalizing constant" to ensure that your distribution integrates to 1. However, the fact that it is available in closed form combined with the structure of exponential families yields very powerful properties. I will discuss them further down in more detail but, in short, the log partition function allows for efficient computation of the moments through derivation instead of integration. This is powerful because derivation is usually much easier than integration. To understand the normalizing effect of the log partition function consider the following figure where the Gamma distribution has been plotted with and without the normalizing constant. 

TODO: naming scheme

<figure>
  <img src="/img/ExpFam_Vis/log_partition_gamma.png"/>
</figure>

If you want to find the natural parameters $$w$$, sufficient statistics $$\phi(x)$$, base-measure $$h(x)$$ or log partition function $$\log Z(w)$$ and don't want to calculate them by hand, you can find a large table of them on <a href='https://en.wikipedia.org/wiki/Exponential_family#Table_of_distributions'>Wikipedia</a>. 

## Important Properties

Exponential Families have a lot of interesting properties. I chose a small selection of those that I find most important. Since I come from a Machine Learning background, my selection is biased towards ML. 

### Multiplication and Division

Due to the properties of the exponential function, the multiplication and division of exponential family PDFs can be done in closed form as long as the resulting natural parameters are valid. If we have an exponential family with two different parameterizations $$w_1$$ and $$w_2$$. Then we can write

$$
\begin{aligned}
p_1(x) \cdot p_2(x) &= \frac{1}{Z} \exp((w_1 + c) \phi(x)) \cdot \frac{1}{Z} \exp((w_2 + c) \phi(x)) \\
	&= \frac{1}{Z'} \exp((w' + c') \phi(x))
\end{aligned}
$$

which is again in the form of the same exponential family. A similar result can be derived for division just that $$w' = w_1 - w_2$$ instead of $$w' = w_1 + w_2$$. Of course, the $$w'$$ have to be valid parameters, e.g. the variance of a Gaussian cannot be negative. To see this property visually for the Beta and Normal distribution consider the following figure.

<figure>
  <img src="/img/ExpFam_Vis/beta_normal_mult_div.png"/>
</figure>

The true distributions have been computed by multiplying/dividing distribution 1 and 2 and re-normalizing the results. The update rule for the Beta distribution is simply $$\alpha' = \alpha_1 + \alpha_2 -1, \beta' = \beta_1 + \beta_2 - 1$$ and for the Gaussian distribution $$\mu' = \frac{\mu_1 \sigma_2^2 - \mu_2 \sigma_1^2}{\sigma_1^2 + \sigma_2^2}$$ and $$\sigma' = \sqrt{\frac{1}{\frac{1}{\sigma_1^2} - \frac{1}{\sigma_2^2}}}$$. 

While this looks like an insignificant property it is actually very important. It implies that we can update the parameters of distributions by simple addition instead of computing costly approximations. This properties is a key component of the Machine Learning technique <a href='https://tminka.github.io/papers/ep/roadmap.html'>Expectation Propagation</a>. 

### Conjugacy

If you have data of a certain type, e.g. Bernoulli, then there often is an exponential family conjugate prior distribution, e.g. the Beta. This means, that you can compute the posterior distribution by updating the parameters of the prior distribution through simple addition $$w' = w_0 + f(x)$$ for data $$x$$ where $$f(x)$$ is a cheap and simple function. This is very powerful, since it enables very fast Bayesian inference with exponential families without the need for costly approximations such as sampling. 

TODO bayes theorem and explanation better.

$$
p(\theta \vert X) = \frac{p(X \vert \theta) \p(\theta)}{p(X)} = \frac{\overbrace{p(X \vert \theta)}_{\text{likelihood}} \overbrace{\p(\theta)}_{\text{prior}}}{\underbrace{\int p(X \vert \theta) \p(\theta)}_{\text{evidence}} 
$$

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

The conjugate prior for the **mean** of a Gaussian (**not** the entire Gaussian distribution) is a Gaussian. In other words, the more data points you have from a Gaussian distribution the more certain you are about its mean. The update equations for this setup are

$$
\begin{aligned}
	v' &= \frac{1}{\frac{1}{\sigma_0^2} + \frac{n}{\sigma^2}} \\
	m' &= v' \cdot \left(\frac{\mu_0}{\sigma_0^2} + \frac{\sum_i x_i}{\sigma^2} \right)
\end{aligned}
$$

![](/img/ExpFam_Vis/Normal_mean.gif)

Our goal is to estimate the mean of the Gaussian distribution on the right, i.e. the red line. In the beginning we have no clue about its position and start with a standard normal prior (blue line on the left). The more samples (black) we see from the true distribution, the more our posterior estimate for the mean (red line on the left) gets closer to the true mean and its variance decreases. 

#### Gamma

The Gamma is a distribution over positive quantities. It is a conjugate prior to the rate parameter of<a href='https://en.wikipedia.org/wiki/Poisson_distribution'>Poisson</a> likelihoods, which are discrete distributions over rare events, e.g. earth quakes. So if you have count data of earth quakes and you assume them to be generated by a Poisson distribution you can get a posterior distribution over its rate parameter with $$\alpha' = \alpha + \sum_i x_i$$ and $$\beta' = beta + n$$

![](/img/ExpFam_Vis/Gamma_Poisson.gif)

We find that with more data the posterior distribution over the $$\lambda$$ rate parameter gets closer to the true value of 0.5 and the uncertainty decreases. 

#### Dirichlet

Similar to how the Beta distribution describes believes about one probability, the Dirichlet describes beliefs about a probability vector. It is a conjugate prior to categorical and multinomial likelihoods. Let's say, for example, we have three categories (or types) of texts: politics, finance and sports and we read a newspaper containing three texts every day. They can contain multiple texts of the same type. Then we might be interested in which kind of focus the publisher has, i.e. what the generating distribution for the texts is. Every individual newspaper can be modelled by a Binomial distribution with $$n=3$$. The generating can be modelled by a Dirichlet and updated with $$\alpha' = \alpha + \sum_i x_i$$.

![](/img/ExpFam_Vis/Dirichlet.gif)

We can see that the mean of the posterior Dirichlet function gets ever closer to the true probabilities generating the Binomial likelihoods and that the uncertainty of our estimate decreases. In our metaphor this means that after seeing 10 individual newspapers we think that the outlet focuses mostly on politics (60%), a bit on finance (25%) and even less on sports (15%). 

#### Inverse Wishart

The inverse Wishart is a distribution over symmetric positive semi-definite matrices. It is a conjugate prior to empirical covariance matrices, e.g. the outer product of vectors drawn from a Gaussian. I always found it hard to get a good grasp of the inverse Wishart distribution and thus first want to introduce it in slightly more detail than the other distributions so far. 

First of all, the inverse Wishart (and the Wishart) distribution is defined on the symmetric positive semi-definite (psd) cone. The psd cone is a subspace of $$\mathbb{R}^d$$ on which all psd matrices lie. A real symmetric matrix $$\begin{pmatrix} a & b \\ b & c \end{pmatrix}$$ is psd iff $$a, c \geq 0$$ and $$ac - b^2 \geq 0$$. following <a href='https://math.stackexchange.com/questions/1875462/how-to-plot-the-psd-cone-in-matlab'>this stackoverflow post</a>, we will represent this by $$(a, b, c) \in \mathbb{R}^3$$. If we set $$a=1$$ then $$c \geq b^2$$ and if we set $$c=1$$ then $$a \geq b^2$$. So if we plot $$(a,b,c) = (1, b, b^2)$$ and $$(a,b,c) = (b^2, b, 1)$$ for $$-1 \leq y \leq 1$$ resptively and join these points with $$(0,0,0)$$ we start to see the cone. 

<figure>
  <img src="/img/ExpFam_Vis/PSD_cone_vis.png"/>	
</figure>

If you want to view the cone from different angles you can do so in the respective jupyter notebook. 

It is very hard to plot the density of a probability distribution on this cone. Thus we have to revert to other strategies to plot the Wishart distribution. I will use three different tools to plot the Wishart distribution. The first requires a bit of math. For off diagonal elements of a symmetric psd matrix $$A$$ it holds $$a_{ij}^2 \leq a_{ii} a_{jj}$$ (see e.g. <a href='https://math.stackexchange.com/questions/3018639/off-diagonal-entries-of-a-symmetric-positive-semi-definite-matrix-prove-a-ij'>here</a>). Thus for our 2-dimensional case we know that $$b = \rho \cdot \sqrt{ac}$$ for $$\rho \in (-1, 1)$$. So one way to visualize the Wishart is to plot marginals for different values of $$\rho$$ with increasing $$a$$ and $$c$$. The resulting plot looks like this

<figure>
  <img src="/img/ExpFam_Vis/Wishart_rhos.png"/>
</figure>

where the values of $$\rho$$ are $$-0.9,-0.8,...,0.8,0.9$$ from the most blue to the most red curve respectively. The $$\Psi$$ chosen for this figure is $$\begin{pmatrix} 5 & 1 \\ 1 & 2 \end{pmatrix}$$, i.e. $$a$$ is larger than $$c$$. This is reflected in the asymmetry of the blue and red curves, i.e. negativ values of $$\rho$$ (blue) yields more compressed curves than positive $$\rho$$s (red).

TODO: understand why!

The second and third tool are simpler. The (inverse-) Wishart distribution has a scale matrix parameter $$\Psi$$ which we can plot as a 2x2 heatmap to show the size of the individual entries. The last method is just plotting histograms over $$a,b$$ and $$c$$ for samples drawn from the (inverse-) Wishart. 

To visualize the likelihood we draw samples from a 2-dimensional Gaussian (top right) and compute their outer products. The update rules for the inverse Wishart are $$\Psi' = \Psi + \sum_i x_i x_i^\top$$ and $$\nu' = \nu + n$$. 

Combining all this we can inspect how the Wishart distribution behaves when updated with Gaussian outer product likelihoods. 

![](/img/ExpFam_Vis/Wishart.gif)

In our first visualization (top left) we find that a) larger values of $$n$$ and $$\Psi$$ imply more probability mass for larger values of $$a$$ and $$c$$. b) The diagonal entries of $$\Psi$$ are equivalent in the beginning, i.e. they are both one and thus $$-\rho$$ and $$+\rho$$ yield the same marginal distribution. After some updates the diagonal values of $$\Psi$$ are different and thus $$\rho$$ and $$+\rho$$ yield different marginal distributions. TODO: is more mass where larger values are?

In the second visualization (bottom left) we mostly see how the values of the scale matrix $$\Psi$$ get larger over time. 

In the third visualization (bottom right) we find that the histograms of $$a,b$$ and $$c$$ for 1000 samples of the Wishart get narrower over time. This shows how the uncertainty decreases and we get more and more certain about the underlying psd matrix. 

### Moment calculation

I have already stated that the moments of exponential families can be computed by differentiating the log-partition function. In this section I want to show why this is possible and derive the mean and variance for the Gamma distribution. 

In general, the <a href='https://en.wikipedia.org/wiki/Moment-generating_function'>moment-generating function</a> (MGF) of a random variable $$X$$ is

$$M_X(t) := \mathbb{E}\left[e^{tX} \right], \qquad t \in \mathbb{R}$$

wherever this expectation exists. $$M_X(0)$$ always exist and is 1, since probability density functions have to integrate to 1. The <a href='https://en.wikipedia.org/wiki/Cumulant'>cumulant-generating function</a> CGF is defined as the logarithm of the MGF

$$K(t) = \log \mathbb{E} \left[e^{tX} \right], \qquad t \in \mathbb{R}$$

For exponential families this means that the MGF of the sufficient statistics $$\phi(x)$$ is

$$
M_{\phi(x)}(u) = \mathbb{E}[e^{u^\top \phi(x)} | w] = \int_x h(x) \exp((w+u)^\top \phi(x) - Z(w)) dx = \exp(Z(w + u) - Z(w))
$$

which means that the CGF is

$$
K_{\phi(x)}(u) = Z(w + u) - Z(w)
$$

The CGF is a Taylor series and the $$n$$-th cumulant can thus be obtained by differentiating the function $$n$$ times and evaluating the result at $$0$$. For the above expression this is mathematically equivalent to taking the $$n$$-th derivatives of $$Z(w)$$ to get the $$n$$-th cumulant. In general, the cumulants are not similar to the central moments of a probability distribution. However, the mean, variance and third central moment they are identical and for the rest of this tutorial we only care about the first and second central moments. 

To illustrate this further, we derive the mean and variance of the Gamma distribution (the same derivation can also be found on <a href='https://en.wikipedia.org/wiki/Exponential_family#Example_1'>Wikipedia</a>). The pdf of the Gamma distribution is

$$
p(x) = \frac{\beta^\alpha}{\Gamma(\alpha)} x^{\alpha-1} e^{-\beta x}
$$

and its natural parameters are $$w_1 = \alpha-1$$ and $$w_2 = -\beta$$. Their reverse substitutions are $$\alpha = w_1 + 1$$ and $$\beta = -w_2$$. The sufficient statistics are $$(\log x, x)$$ and the log-partition function as a function of the natural parameters is

$$
Z(w_1, w_2) = \log \Gamma(w_1 + 1) - (w_1 + 1) \log(-w_2)
$$

To compute the mean we need to differentiate the log-partition function w.r.t. $$w_2$$ since the second sufficient statistic is $$x$$. Thus

$$
\begin{aligned}
\mathbb{E}[x] &= \frac{\partial Z(w_1, w_2)}{\partial w_2} \\
	&= -(w_1 + 1)\frac{1}{-w_2}(-1) = \frac{w_1 + 1}{-w_2} \\
	&= \frac{\alpha}{\beta}
\end{aligned}
$$

To compute the variance we differentiate twice and get 

$$
\begin{aligned}
\mathrm{Var}(x) &= \frac{\partial^2 Z(w_1, w_2)}{\partial w_2} \\
	&= \frac{\partial}{\partial w_2} \frac{w_1 + 1}{-w_2} \\
	&= \frac{\alpha}{\beta^2}
\end{aligned}
$$

We can visually confirm, that these approximations are correct by comparing sampling-based and closed-form solutions.

<figure>
  <img src="/img/ExpFam_Vis/gamma_expectations.png"/>
</figure>

Similar to above we can also compute the moments for the other sufficient statistics, e.g. $$\mathbb{E}[\log x]$$ and $$\mathrm{Var}(\log x)$$. 

All of the moments above could have also be computed using integration but it is significantly more complicated than simple differentiation. 

### Moment Matching

Let's say we have two distributions $$p(x)$$ and $$q(x)$$ where $$p$$ is any fixed distribution and $$q$$ is a member of an exponential family. Then we can show that the <a href='https://en.wikipedia.org/wiki/Kullback%E2%80%93Leibler_divergence'>KL-divergence</a> $$KL(p\vert\vert q)$$ between the two distributions is minimized by matching their moments, e.g. setting the mean and variance of $$p(x)$$ to that of $$q(x)$$. We write

$$\begin{aligned}
KL(p||q) &= \int p(x) \log\frac{p(x)}{q(x)} dx \\
	&= \int p(x) \log p(x) dx - \int p(x) \log q(x) dx \\
	&= \mathbb{E}_{p(x)}[\log p(x)] - \int p(x) \log\exp(w \phi(x) + \log h(x) - \log Z(w)) dx \\
	&= \mathbb{E}_{p(x)}[\log p(x)] - \mathbb{E}_{p(x)}[\log h(x)] - \mathbb{E}_{p(x)}[w \phi(x)] + \mathbb{E}_{p(x)}[\log Z(w)]
\end{aligned}
$$

which as a function of $$w$$ is

$$
KL_w(p||q) = - \mathbb{E}_{p(x)}[w \phi(x)] + \log Z(w)
$$

where the expectation around $$\log Z(w)$$ vanishes as it is independent of $$x$$. To get the optimal values for $$w$$ we compute the first derivative w.r.t. $$w$$ and set it to zero. 

$$\begin{aligned}
\nabla_w KL_w(p||q) &= - \mathbb{E}_{p(x)}[\phi(x)] + \nabla_w \log Z(w) \overset{!}{=} 0 \\
	\Leftrightarrow \nabla_w \log Z(w) &= \mathbb{E}_{p(x)}[\phi(x)] \\
	\Leftrightarrow \mathbb{E}_{q(x)}[\phi(x)]  &= \mathbb{E}_{p(x)}[\phi(x)] 
\end{aligned}
$$

where we use the knowledge that the derivatives of the log-partition function yield the moments of the distribution which we derived in the previous section. The visual intuition behind this fact can be found in the following figure. Our static distribution $$p(x)$$ is a normal with $$\mu=4$$ and $$\sigma=1$$ and we want to fit a Gamma distribution $$q(x)$$ such that $$KL(p\vert\vert q)$$ is minimized. To match the moments we compute

$$\begin{aligned}
	\mu &= \frac{\alpha}{\beta} \\
	\sigma^2 &= \frac{\alpha}{\beta^2} \\
	\Rightarrow \alpha &= \frac{\mu^2}{\sigma^2} = 16\\
	\Rightarrow \beta &= \frac{\mu}{\sigma^2} = 4
\end{aligned}$$

We can then compare the empirical KL divergences for different pairs of parameters around the theoretically optimal solution to convince ourselves that we have the best fit. 

<figure>
  <img src="/img/ExpFam_Vis/moment_matching_gamma.png"/>
</figure>

This property of matching the moments (or expectations) gives name to Expectation Propagation since one of its central steps is to fit an exponential family by moment matching. 

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


