---
layout:     post
title:      "Inverse Classification using Generative Models"
subtitle:   "This post is a summary of my first bachelor thesis (Cognitive Science)"
date:       2019-10-20 20:28:00
author:     "Marius Hobbhahn"
# header-img: "img/Marius2.jpg"
category:   ML_project
tags:       [machine learning]
---

**Abstract:** 

In my first bachelor thesis I tested whether "inverting" the classification process by using the gradient information of generative models is effective. After many experiments the conclusion is confirming the expected: it depends on the quality of the generative network. The better the generative network the better its ability to classify. 

## **1. Introduction:**

My supervisor for the project Sebastian Otte and the Professor of the research chair have conducted multiple experiments on gradient based methods in general. The motivation for doing comes from two angles: 1. It is more robust against adverserial attacks. If you think of a trained forward network, i.e. a CNN as a very complex lookup table that also often overfit on meaningless features or proxies instead of the best possible features I think it gets more plausible why they are so prone for adverserial attacks in the first place. A generative model has to develop some sort of inner representation of the concept it is generating and might therefore be less prone to these attacks. 2. The chair I was doing this thesis with is the chair of Cognitive Science and therefore has a strong neuroscience background. Most learning systems in the brain are not just a one way forward classification task but rather a very interactive process where information is propagated forward and backward multiple times. A particular framing that is often used (and I personally find very convincing because it explains so many biases or behaviours of humans) is the following: The brain is mostly a generative model that constantly makes predictions about the real world and updates them given input data through the senses. Inverse classification probably is the most basic experiment one can conduct to test a very simplified version of this hypotheses. Given that this work is the first using temporal gradients for classification a lot of exploratory work is done, i.e. analysis of its capabilities and methods to increase its functonality. 

## **2. What is Inverse Classification?** 

Inverse Classification is a two step process. In the first step a generative model is trained on any dataset. This can be any generative model. It could be a generative adverserial network (GAN) or any other. In this thesis we used LSTMs because the dataset I was using constisted of long sequences. The training is done until a good representation of a concept is learned. In my case that ment until the network has learned representations of all classes. I used one-hot encoding for the classes, so inputting a vector that is one at its first entry and otherwise zero would generatve the character 'a'. In the second step the generative model is used to classify previously unseen data by iteratively updating its prediction using the temporal gradient information. This means starting with an arbitrary starting vector and generating a sequence from it. Given that we have no idea what our class is going to be a uniform vector is the most plausible choice. The uniform vector generates some sequence. This sequence is now compared to the actual target to be classified. The error between prediction and target is calculated and backpropagated through the network and a gradient is output. This gradient can now be used to update our initial guess, i.e. the uniform vector. This new vector can now be pushed forward through the network again and produce an output that is a little closer to the actual target. This iterative process can now be done until the error between true target and reconstruction converges. At the point of convergence the input vector is taken as the classification and the class can be detemined by using the biggest entry of this vector. If the vector has not converged to a one-hot it also gives valuable insight about what the network thinks that the target is a combination of. So, for example, the character 'a' might be partly reconstructed using a 'd'. An example of the entire process can be seen in the following figure:

<figure>
  <img src="/img/IC_Bachelor/Gen_IC_figure.jpg" alt="Figure of the Inverse Classification process"/>
  <figcaption>Depiction of the Inverse Classification process. The first step is to train a generative model. The second step is to iteraitvely update the latent vector using the temporal gradient.</figcaption>
</figure>

## **3. Experiments:**

We conducted many different experiments with the aim to increase the accuracy of the Inverse Classification process. If you wanna see them all you will have to check out the full thesis. The short summary is: all but one mechanism that we tested don't work but this one works pretty good. The working mechanism is to add Gaussian noise to the inputs before doing a training iteration and then clipping and normalizing the vector such that it still resembles a vector of probabilities. So a vector with four classes resembling and 'a' would look like this: [1,0,0,0] before this procedure and could look like this: [0.83, 0.06, 0.04, 0.07] after it. The whole idea besides the experiment is to introduce some variability in the latent representations that the network sees during training and is therefore able to use during the Inverse Classification. Simplified, If the network has only seen one-hot vectors during training it does not know how to reconstruct a target using anything else. An additional variable that was checked for within the experiments is the number of available training data points. Conventional forward networks are know for only working well with huge amounts of training data, whereas generative models are known to already perform reasonably well at lower amounts of data.

## **4. Results:**

The first result is with regards to the addition of noise to the inputs. I have already spoiled in the Experiments section that it was the only experiment with positive results but I want to show this is a more graphical fashion. In the following we consider a model that was trained only on two different character classes, i.e. 'a' and 'b'. To test the influence of the addition of noise on the latent space of the model we did a grid search over a 2D grid with vectors ranging from [0,0] to [1,1] with steps of size 0.1 and plot the mean squared error to a stereotypical 'a'. This means the heatmap is light when the model predicts and 'a' and gets darker the more different the predictions get from an 'a'. If the latent space is perfectly separated our model would always predict the class which has the maximum entry in the vector, e.g. a [0.3, 0.8] would be predicted as 'b' and [1, 0.5] would be 'a'. The results for different models are presented as heat maps in the following figure. A model with perfectly separated latent space has a decision boarder on the diagonal because this is where the maximum entry switches. In the first heatmap a vanilla model is presented, i.e. a model that is trained without the addition of noise to the input. In the following four heatmaps different level of noise were added. Given that we add Gaussian noise the levels are just increasing standard deviations. In our case: 0.1, 0.2, 0.3 and 0.4. The last heatmap shows the mean squared error for the character 'b' of the 0.3 standard deviation model. This is just used to double check that the model not only has a good latent space for both classes but also no zones that create weird artifacts. 


<figure>
  <img src="/img/IC_Bachelor/2D_noise_overview.jpg" alt="2D noise results"/>
  <figcaption>Heatmaps representing MSE distance to the character 'a' for the outcome of the generative model trained on data. First heatmap is the vanilla model, i.e. no addition of noise during training. Heatmap 2 to 5 represent models with increasing amount of input noise. Heatmap 6 shows the distance to the character 'b' to double check that the latent space is completely well defined.</figcaption>
</figure>

The second result concerns the amount of datapoints that was used for training. In the 'sparse1' setting there was only one sample per class for the training while there were 4 samples for the 'sparse4' setting and the full training set, i.e. around 220 samples per class for the 'all data' case. The accuracy of these models are compared to a conventional forward model trained on the entire set and one on 4 data points, namely 'comparison' and 'sparse comparison'. The following figure compares all accuracies and tells a very simply but surprising story: In simple settings, i.e. a problem that has only 2 or 4 classes, it does not really matter what method you choose, and how many training points you use. So even a model that was only trained on one example per class is just as good as one that was trained on multiple hundred training samples. The more complex problems, i.e. 20 dimensions get more interesting. The forward model trained on all data points outperforms every other approach by a strong margin. The Inverse Classification models get better the less training data one uses (This is especially surprising). I think the reason for this behaviour is an intrinsic problem with Inverse Classification, namely that every generative model holds exactly one representation of a class. I hypothesise that a inverse model trained on multiple representatives of a class might hold a weird 'average' of the samples that is a less good representation than just one sample. An inverse model trained on few data points is just as good as a forward model trained on few data points as can be seen with the 'sparse1' and the 'sparse comparison' accuracies. This, at least for me, is good evidence for the fact that Inverse Classification has potential as a technique, especially in the low data regime. 

<figure>
  <img src="/img/IC_Bachelor/results_bar_plot.jpg" alt="Overview of the results"/>
  <figcaption>Comparison of the accuracies for five different models. 'sparse1', 'sparse4' and 'all data' describe accuracies of Inverse Classification models trained on 1, 4 or all data points per class respectively. 'comparison' and 'sparse comparison' describe conventional forward models trained on all data or 4 data points per class.</figcaption>
</figure>

## **5. Conclusions:**

Honestly, I am not yet decided on the Inverse Classification technique. I think this basic research shows that it has some potential, especially in the low data regime. I think the two directions one would have to check to make a more informed decisions are either to improve the generative model or to reduce the problem complexity in some way. For the first I could imagine using GANs to train the model instead of LSTMs. LSTMs are just not the state of the art of generative models and the GAN community has produced some astonishing results over the last few years. For the second option I could think of using a modular approach to Inverse Classification, i.e. using multiple smaller generative models and have them compete against each other to produce classifications. 
However, even if a better generative model might make the technique feasible there is one downside that might kill its practical application entirely. Since every classification process is an optimization in itself, there is a high computational overload attached to each classification step. This might not be much of a problem given that computing is faster and cheaper than ever but is only worth the extra effort if the results clearly outperform other methods. My most reasonable estimation of the technique is that it will probably be relevant for some niche applications but will not revolutionize the way we classify in general. 


#### ***One last note:***

If you have any feedback regarding anything (i.e. layout, code or opinions) I would be happy if you told me. But please do it in a constructive manner.



