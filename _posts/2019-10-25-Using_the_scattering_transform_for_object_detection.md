---
layout:     post
title:      "Using the Scattering Transform for Object Detection"
subtitle:   "This post is a summary of my second bachelor thesis (Computer Science)"
date:       2019-10-25 20:28:00
author:     "Marius Hobbhahn"
# header-img: "img/Marius2.jpg"
category:   ML_project
tags:       [machine learning]
---

**Abstract:**

In my second bachelor thesis I explored the usefulness of applying static filters, i.e. the Scattering Transform on object detection. I found that the Scattering Transform has desirable properties w.r.t. some equivariances and in the low-data regime. In all other cases no benefitial properties of the Scattering Transform have been found.


## **1. Introduction:**

There are many unknowns in the training of any deep learning architecture. We have no guarantee that it converges to a reasonable optimum, we don't know after how many steps it converges and we can't really predict what features the filters in CNNs will learn. In practice we circumvent these challenges by training with multiple different hyperparameters and using other heuristics to improve training. Additionally, we do want to make sure that a network fulfills some theoretical guarantees after training, i.e. equivariances. Equivariance, in the context of this post, just means that if a transformation is applied on an object in an image we want the network to be able to still detect that object. This is especially important in the context of self-driving cars. If the position, size or orientation of a pedestrian is changed we want to have the guarantee that they are still detected correctly.
In this thesis I tested whether using static filters that are known to have some of these desirable properties in combination with current Deep Learning frameworks yield the desired effects.


## **2. What is the Scattering Transform?**

The paper that introduced the Scattering Transform makes it sound way more complicated than it really is. The scattering transform is just the application of multiple filters on an image in a particular fashion. The filter is a Morlet wavelet (also known as the Gabor filter for people who come from a neuro background like me). This Morlet wavelet/Gabor filter is a product of a sinosoidal wave with a Gaussian and looks like this in 1D:

<figure>
  <img src="/img/Scattering_Bachelor/Morlet_wavelet_1D.png" alt="Morlet_wavelet_1D"/>
  <figcaption>Morlet wavelet/Gabor filter in 1 dimension</figcaption>
</figure>

Even though the theory might look complicated to some I think it is easiest to think of the Morlet wavelet as some kind of 'fancy' edge detector. It comes with some additional properties but from the 1D image alone it is clear that the filter mostly finds gradients along some axis.
The main idea of the Scattering transform is to apply this filter multiple times. That is in different angles and sequentially. The sequential application of two filters can be seen as a layer in a network. For example, we can have a two layer scattering network with four angles. That means we have 4 filters in the first layer and 4*4 in the second. Since the network cannot be though of in a 'pipeline' fashion the output of every filter is relevant. In our example we would have 4 + 16 outputs. These 20 outputs can be interpreted similar to 20 features in the early stages of a CNN. A sketch of a network is shown in the following figure:

<figure>
  <img src="/img/Scattering_Bachelor/scattering_network_overview.png" alt="Figure of a Scattering Network"/>
  <figcaption>Representation of a scattering network. Each filter is described by its path. Every blue arrow describes an output at the particular filter. The m describe the number of iterative applications of the scattering transform. L is the branching factor in the network also known as the number of angles for the filter.</figcaption>
</figure>

To give a better understanding of how the Scattering transform looks at different stages of the network I

<figure>
  <img src="/img/Scattering_Bachelor/cat_example.jpg" width="100"/>
  <img src="/img/Scattering_Bachelor/example_cat_0ord.png" width="100"/>
  <img src="/img/Scattering_Bachelor/example_cat_2ord.png" width="100"/>
  <img src="/img/Scattering_Bachelor/example_cat_2ord.png" width="100"/>
  <figcaption>An image of a cat at different stages of a 2 layer Scattering Network.</figcaption>
</figure>

A scattering network alone is probably pretty useless for detection purposes. We therefore want to combine the theoretical guarantees of the scattering transform with the flexibility of neural network to get the best of both worlds.

## **3. Experiments:**


## **4. Results:**




## **5. Conclusions:**



#### ***One last note:***

If you have any feedback regarding anything (i.e. layout, code or opinions) I would be happy if you told me. But please do it in a constructive manner.
