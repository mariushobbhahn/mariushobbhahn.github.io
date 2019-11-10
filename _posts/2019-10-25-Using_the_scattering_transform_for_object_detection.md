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

There are many unknowns in the training of any deep learning architecture. We have no guarantee that it converges to a reasonable optimum, we don't know after how many steps it converges and we can't really predict what features the filters in CNNs will learn. In practice we circumvent these challenges by training with multiple different hyperparameters and using other heuristics to improve training. Additionally we do want to make sure that a network fulfills some theoretical guarantees after training, i.e. equivariances. Equivariance, in the context of this post, just means that if a transformation is applied on an object in an image we want the network to be able to still detect that object. This is especially important in the context of self-driving cars. If the position, size or orientation of a pedestrian is changed we want to have the guarantee that they are still detected correctly. 
In this thesis I tested whether using static filters that are known to have some of these desirable properties in combination with current Deep Learning frameworks yield the desired effects. 


## **2. What is the Scattering Transform?** 


<figure>
  <img src="/img/IC_Bachelor/Gen_IC_figure.jpg" alt="Figure of the Inverse Classification process"/>
  <figcaption>Depiction of the Inverse Classification process. The first step is to train a generative model. The second step is to iteraitvely update the latent vector using the temporal gradient.</figcaption>
</figure>

## **3. Experiments:**


## **4. Results:**




## **5. Conclusions:**



#### ***One last note:***

If you have any feedback regarding anything (i.e. layout, code or opinions) I would be happy if you told me. But please do it in a constructive manner.



