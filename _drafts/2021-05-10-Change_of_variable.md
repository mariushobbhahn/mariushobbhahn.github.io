---
layout:     post
title:      "Change of variable for PDFs"
subtitle:   "A simple visual tutorial"
date:       2021-04-29 20:28:00
author:     "Marius Hobbhahn"
header-img: "img/header-imgs/change_of_variable.png"
category:   ML_project
tags:       [Machine Learning]
---

## **What is this post about?**

The change of variable for probability density functions (pdfs) is a simple yet powerful fact about probability distributions. It is the foundation for some of my research, which is why I feel comfortable writing this tutorial, but it is also the main component of other ML techniques such as normalizing flows. TODO:link

In this post I introduce the change of variable with increasingly complex examples while primarily focusing on visual interpretations.

If you have constructive feedback don't hesitate to write me. If you like it, share it with others. 

## Change of variable for pdfs

If we apply a transformation $$g(x): \mathbb{R} \rightarrow \mathbb{R}$$ to a random variable $$X$$ then its pdf $$p_X(x)$$ also changes. If $$g(x)$$ is a monotonic function then the pdf $$p_Y(y)$$ of the transformed random variable $$Y$$ is

$$\begin{aligned}
p_Y(y) &= f_X(g^{-1}(y)) p_Y(y) &= f_X(g^{-1}(y)) \left\vert \frac{d}{dy}(g^{-1}(y)) \right\vert
\end{aligned}$$

where $$g^{-1}$$ describes the inverse function of $$g$$. 

The first part of the equation, $$f_X(g^{-1}(y))$$, simply means that all occurences of $$x$$ in your original pdf $$p(x)$$ are replaced with the inverse function of your desired transformation $$g^{-1}(y)$$. I like to think of $$p_X(x)$$ as a wire and the transformation is simply a shift, stretch or compression of the wire and then describes the new pdf $$p_Y(y)$$. 

The second part, $$\left\vert \frac{d}{dy}(g^{-1}(y)) \right\vert$$, makes sure that the new pdf $$p_Y(y)$$ still integrates to 1. The change of variable might increase or decrease the area under the function which would imply that the resulting function is not a valid pdf. The determinant of the Jacobian of the inverse transformation can be seen as the inverse of the volume of the transformation. Thus this second part can be interpreted as a normalizing factor. 

In the following, we will look at different transformations of increasing difficulty. Later examples elaborate on more complex properties of the change of variable such as their concatenations or how to deal with non-monotonic transformations. For more properties or high-dimensional transformations I recommend the <a href='https://en.wikipedia.org/wiki/Probability_density_function#Function_of_random_variables_and_change_of_variables_in_the_probability_density_function' target='_blank'>Wikipedia article</a>.

### Adding a constant: y = x+c

If we want to add a constant to our variable $$y = x + c$$, we can interpret this as a shift of the distribution. With the change of variable formula we get 

$$\begin{aligned}
g^{-1}(y) &= y-c \\
p_Y(y) &= f_X(g^{-1}(y)) \cdot 1 
\end{aligned}$$
where $$p_Y(y) &= f_X(g^{-1}(y)) \left\vert \frac{d}{dy}(g^{-1}(y)) \right\vert = 1 $$ because the transformation doesn't change the volume of the pdf. 

In the specific case of the Gaussian distribution with $$c=1$$ we can visualize the transformation like this:

TODO:gif

TODO description

### Multiplying with a constant: y = c*x

If we want to multiply our random variable with a constant $$y=c*x$$, we can interpret this as compressing or stretching the pdf. We have 

$$\begin{aligned}
g^{-1}(y) &= c * y \\
p_Y(y) &= f_X(g^{-1}(y)) \cdot 1/c
\end{aligned}$$
where $$p_Y(y) &= f_X(g^{-1}(y)) \left\vert \frac{d}{dy}(g^{-1}(y)) \right\vert = 1/c$$.

For a Gaussian random variable with $$c=2$$ we get a visual interpretation of 

TODO gif

TODO description

### Non-linear transformation: y = log(x)

If we want to apply a non-linear transformation to our random variable such as $$y = log(x)$$, we can think of a non-linear stretch or compression of the wire. In the case of the logarithm we map small values $$(0 < x < 1)$$ to larger negative numbers, i.e. we stretch the wire. Larger values $$(x > 1)$$ will be mapped to smaller numbers since $$\log(x)$$ < x$$ when $$x > 1$$, i.e. we compress the wire. 

For a Gamma random variable we can visualize the log-transformation like this:

TODO: gif

TODO description

### Non-monotonic transformations: y = sqrt(x)

Non-monotonic transformations such as the squareroot are not invertible in their entirety. Thus we have to adapt the general change of variable equation by splitting the function into monotonic intervals. 

$$\begin{aligned}
f_Y(y) &= \sum_{k=1}^{n(y)} f_X(g_k^{-1}(y)) \left\vert \frac{d}{dy}(g_k^{-1}(y)) \right\vert
\end{aligned}$$

where $$n(y)$$ is the number of invertible intervals and $$g_k^{-1}(y)$$ is the inverse transformation on interval $$k$$. 

To illustrate this fact, consider the example of transforming a Chi-square random variable $$X$$ with one degree of freedom ($$k=1$$) by the square root, i.e. $$Y = \sqrt{X}$$. Then

TODO: math for transformation

TODO: GIF

TODO: interpret GIF

Note: more complicated cases like Wishart and matrix squareroot

### Concatenating transformations

Assume we have two transformations $$g(x)$$ and $$f(x)$$. Then we can apply them sequentially, e.g. $$Y = g(X)$$ and $$Z=f(Y)$$, and can compute the resulting pdf either by applying the change of variable once for $$f$$ and then for $$g$$ or by computing the concatenation $$f \circ g$$. 
In general, $$f \circ g \neq g \circ f$$. 

In Machine Learning, <a href='TODO' target='_blank'>normalizing flows</a> make use of this concatenation by assuming that an unknown probability distribution, e.g. images, are a complicated transformation of a simple distribution, e.g. a Gaussian. Normalizing flows then parameterize the complicated e, transformation.g. by a neural network, and learn it from data. The result is a map from samples of a simple distribution to a complicated distribution, which can be used to generate new samples, e.g. images. 

#### ***One last note***

If you want to get informed about new posts you can <a href='http://www.mariushobbhahn.com/subscribe/'>subscribe to my mailing list</a> or <a href='https://twitter.com/MariusHobbhahn'>follow me on Twitter</a>.

If you have any feedback regarding anything (i.e. layout or opinions) please tell me in a constructive manner via your preferred means of communication.

