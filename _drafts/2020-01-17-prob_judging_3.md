---
layout: post
title:  "Probabilistic Adjudication: Part I (Still under construction)"
date:   2020-01-17 23:01:30 +0200
author:     "Marius Hobbhahn"
category: opinion
---

This post is not yet finished. I am still gathering feedback. You can read it anyway if you like but it will likely change a bit in the near future. 

## What is this mini-series about?

There are many great workshops on different aspects of judging in debating TODO:refs. However, I think one aspect of the adjudication is neither very prominent nor very well illustrated so far - probabilistic judging. The core thesis is that arguments are not just true or false, bought or not bought in their entirety, but they are 'bought to some degree' or the judges are 'convinced to some extend', i.e. arguments are assigned probabilities or probability distributions. What I want to do in this mini series are two things: a) Set up a basic framework of probabilistic judging and b) integrate and illustrates multiple facettes of debating within that framework. Part I deals with the evaluation of one argument in a vacuum, part II deals with extensions and rebuttal and part III attempts to weight different arguments that aim to prove different metrics. To be very clear - I do not say that this is the ultimately correct way to judge a debate, I want to a) further the discourse on how arguments should be evaluated and b) illustrate how I think about probabilistic judging and give other people who have thought less or different about the issue a possibility to learn or improve my view. Additionally, I want to make this post as understandable as possible such that people who are very new to debating also get a chance to understand it. Given that I have a Machine Learning and Probability Theory background I might find concepts intuitive that you are new to. If such a situation occurs I would be grateful for feedback. If you, on the otherhand, understand what I am saying but disagree with regards to content, I would also be interested in your criticism and possible solutions. 

## Part I: evaluating one argument

In this part I want to focus on evaluating one argument in a vacuum. That means we ignore most of the things happening in a usual debate. We ignore all other teams, all extensions, all rebuttal, all framings, etc. We only consider exactly one argument. The two necessary conditions for an argument to persuade anyone are a) the argument is true and b) the argument is relevant. If you are convinced that an argument is true with high probability but not relevant you very likely do not care a lot about it. If you are convinced that something is important but not that it is true you are not convinced by it either. 

### The fundamentals of Probabilistic Inference

A probability distribution denotes the probability $p(h)$ of a variable $h$ taking a certain value, for example the probability of a human to have a certain height. It is more likely that a person is 1.8m than that they are 1m or 3m tall. It is also possible to condition that variable on another variable, i.e. we could look at the probability distribution of height conditioned on the gender $g$ of a person $p(h | g)$. Even though this is not true in reality, assume for simplicity that there are only two genders. The distribution of the height of all people can suddenly be explained by the two conditional distributions $p(h | g=female)$ and $p(h|g=male)$. Distributions can be defined on different domains. A distribution over probabilities, for example, can only range from 0 to 1 since probabilities below 0 or above 1 are just not defined. The distribution over the height of humans could technically be infinitely large but never below 0. The distribution over the measurement error of a clock could in theory be everywhere between minus and plus infinity, i.e. this clock can show a time that is arbitrarily wrong either in the future or past. To understand what probability distributions, conditionals and domains mean, consider the following figure.

TODO illustrate

Distributions can be used to illustrate a fact about the world as shown in the example of height. However, they can also be used to update our believes given new data. Let's say, for example, your current believe is that you currently think that human height is distributed around the two peaks of 1.6 and 1.7 meters as shown in the above figure. Now you receive new information: The data that we have based that believe on are 10 years old and the decrease in human malnourishment has led to an average growth of humans of 5cm. Therefore you update your believe to a new distribution that is centered around the peaks at 1.65m and 1.75m respectively. There could also be other updates that you make about this believe, i.e. it might be found out that the women whose height was measured during the initial measurements were selected from a particular group in society and therefore bias your result. For example only german women were measured because the study was conducted in germany. Since german women on average are slightly taller than the global average your updated distribution would include this fact and change the peak for women from 1.6m to 1.55m. This notion of updating our believes can be expressed via the fundamental rule of probabilistic inference: Bayes rule.

$$
\underbrace{p(X|Y)}_{\text{posterior}} \propto \underbrace{p(Y|X)}_{\text{likelihood}} \underbrace{p(X)}_{\text{prior}}
$$

We have a certain prior believe about a thing in the world, we get new data (here referred to as likelihood) and update this believe to yield a posterior. The posterior asks: "what is our believe about variable X after having seen data Y", i.e. what is our updated belief? 

I think persuasion can easily be integrated into this model. An adjudicator has the prior believe of the average intelligent globally informed citizen and updates these believes according to the claims made in the debate. As already motivated in the introduction there are two necessary conditions for an argument to be persuasive: it must be true and relevant. I posit that for both, truth and relevance, we have a prior distribution that can be updated through the speakers contributions. The updates should be proportional to the strength of the presented arguments, i.e. a very strong argument must lead to larger updates than a weak one. To illustrate this further consider the following example. 

## Example Motion: UBI

Assume the motion is "THW introduce a universal basic income (UBI)". The model introduced by the goverment is simple: Cut all social benefits, tax the rich and introduce a 1000 dollar per month payment for every person that has citizenship. People without citizenship still get all benefits they have previously gotten. Parents get the money for their children until their 18th birthday. In the following I want to discuss two arguments, a utilitarian calculus and a principle right, that both could be made by a government team. Additionally I want to illustrate how the prior to posterior distribution shift could be viewed for different possible mechanisms and impacts of the respective argument. 

### Argument I: a utilitarian calculus

The statement we assess reads: A UBI improves peoples lives. To evaluate the overall persuasiveness of this argument consider different scenarios. We begin with the update for the distribution of the truth value of this statement. In increasing strength we have

1. An emotional story of a friend that would be helped by this because they could buy themselves a new car. We will call this weak evidence (WE).
2. Someone pointing out that this has been tested in small scales in some countries with some positive results. However, they do not explain why this experimental setting is transferable to larger society. We will call this mediocre evidence (ME).
3. A weak mechanism (WM): money is nice for people since it allows them to buy stuff they like and need. 
4. A strong mechanism (SM): For a large group of people it removes the fear and uncertainty of low and unsteady income, i.e. not knowing whether they will be able to pay the rent or go to college. 
5. The weak and strong mechanism are both explained to support the thesis (WM+SM)

Note, that I do not say mechanism 4 is necessarily stronger than mechanism 3. Let's for the purpose of this example assume that it had been explained more persuasively (e.g. better analysis, more depth, etc.).

<figure>
  <img src="/img/Probabilistic_Judging_1/UBI_truth.png" alt="test"/>
  <figcaption>Different scenarios of the "Truth condition" of an argument</figcaption>
</figure>

![test](/img/Probabilistic_Judging_1/UBI_truth.pdf){width=100%}

Now, let's assume any number of reasons for why the UBI improves peoples lives has been presented and we are now left with the question: "Why should we care about this?". This is the second part of the argument, namely: relevance. In the following we look at the relevance created by different lines of argumentation **under the assumption the mechanism leading to this effect has been shown to be $100\%$ true**. Again in increasing order we have:

1. A small amount of people is helped. For example, with UBI middle class families can afford an additional holiday per year. This is nice for them and increases their happiness marginally. 
2. The individual effect of a UBI is very large. The fear and uncertainty accompanying a low and unsteady income is huge. Not knowing whether you are able to pay the rent for the next month of the tuition for your children is a heavy emotional burden. There is good psychological evidence showing that this "nagging in the back of your head" has an equivalent effect on your psyche as not having slept the last night. Alleviating people of that effect has large individual effects. 
3. A large amount of people is helped. A UBI with accompanying rich tax is essentially a way of redistribution. Therefore around 90 percent of society gain something while only 10 percent lose out. Therefore a large group is helped. 
4. An especially important actor is harmed/helped. The individual effects described in 2) hit the most vulnurable groups escpecially hard. Single parents, low income families, people in disenfranchised communities (i.e. people of color or immigrants) are disproportionally affected by this uncertainty because they on average earn less and have smaller financial safety nets. Since they never chose to be born within these explicit circumstances but rather just through the lottery of birth we should care about these actors more. 
5. Any combination of the above. For example, a large group and a strong individual effect. 

<figure>
  <img src="/img/Probabilistic_Judging_1/UBI_impact.png" alt="test"/>
  <figcaption>Different scenarios of the "Relevance condition" of an argument</figcaption>
</figure>

Now we have to combine the two posterior distributions over an arguments truth and relevance. If we only considered one of the two it would be rational to either only argue claims that are uncontroversial, such as "this motion helps at least one individual a little bit" or claims that have gigantic effects, such as "This motion will lead to a nuclear world war". To illustrate how different distributions over truth and relevance interact I have chosen three distributions over the truth part and three over the relevance part and show all possible combinations of them. 

<figure>
  <img src="/img/Probabilistic_Judging_1/UBI_combined.png" alt="test"/>
  <figcaption>Different combinations of 3 truth and 3 relevance distributions</figcaption>
</figure>


### Argument II: a principle right

TODO

## But what about the priors?

The most used criticism of Bayesian inference is: "Your posterior depends on the prior and if you choose the prior in dumb ways you can produce whatever results you want. Therefore Bayesian Inference does not work." And while it is true in some (but not most) real life applications that it is hard to choose a prior that makes sense we could also choose a prior that just says "I actually really don't know. It could be anything." However, in debating, there is a simple way to choose the priors that we already all agree on. In every judging manual you will find that the "Average Informed Global Citizen" or "Average Informed Voter" (AIV) is the basis of adjudication. And the AIV surely has prior knowledge. For example if I asked you what your belief about the statement "Donald Trump is currently (January 2020) the president of the united states", then you would be very sure that this is a true and not a false statement. Maybe there would be some lingering uncertainty because he could have been impeached while you were asleep or something but you would be very sure. For the statement "Putin is 20 years old in 2020" your distribution would very much lean to the untrue end. If you were to assess the statement "Brexit will happen" in 2018 the past AIV would have very high uncertainty over the truth of statement probably including all possibilities from false to true. This is also true for the relevance of a given statement. For example, the prior distribution over "the harms of human made climate change" is definitely above zero or the prior distribution over "the wrongness of torturing people for fun without additional reason" is definitely at the high end of badness. 

TODO illustrations

All the knowledge that the AIV has should be seen as prior knowledge in this model of debating. There is obviously not a list of things that the AIV knows and therefore this question can not be answered for good but at least we have a clear way of solving disagreements during adjudication. 

However, I must point out that debating is a game that implies rules for how the prior distributions are distributed. First, prior knowledge must align with the reality of the AIV, i.e. they know basic facts about the world but are not specialists in any particular field. They know the presidents of most major countries of the world, some basic economics and politics, etc. They do not know the finance minister of the Kongo, the exact melting point of all metals or the exact wording of the law of every country in the world. Even if a particular adjudicator knows these facts, for the purpose of the debate, they must assume not to know any of them. Second, prior knowledge distributions must be easily shiftable, i.e. the adjudicator is easily persuaded by arguments when good reasons are presented. This level of persuadability is probably a lot higher than for the average person that you meet on the street but is part of the game we are playing. 

## prior shift vs. absolute value:

TODO

Why talk so much about priors when you don't care about them anyways?

## Limitations of the model:

human communication is weird, we don't talk in logic.

overlap between truth and effect. 

## Nerd section: some statistical explanations 

- Bayes rule not bayes theorem:
- Distributions are beta, gamma and normal.
- combination: not sampling, multiplied with expected value.


***One last note:***

If you have any feedback regarding anything (i.e. layout or opinions) please tell me in a constructive manner via your preferred means of communication.

