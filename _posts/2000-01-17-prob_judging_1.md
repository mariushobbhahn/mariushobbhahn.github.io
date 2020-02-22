---
layout: post
title:  "Probabilistic Adjudication: Part I - one argument (Still under construction)"
date:   2019-01-17 23:01:30 +0200
author:     "Marius Hobbhahn"
header-img: "img/debate.png"
category: opinion
---

This post is not yet finished. I am still gathering feedback. You can read it anyway if you like but it will likely change a bit in the near future. 

## What is this mini-series about?

There are many great workshops on different aspects of judging in debating (E.g. the ones given by <a href='https://www.youtube.com/watch?v=B3gLCTOxFDY'>Olivia Sundberg</a>, <a href='https://www.youtube.com/watch?v=4-pz11ECDyk&list=PLJQFY9AV_gZTZddiuaqay-Xj9tLYk9xuW&index=13'>Yair Har-Oz</a>, <a href='https://www.youtube.com/watch?v=4Mvn6m2YPd0'>Daan Welling</a> and <a href='https://www.youtube.com/watch?v=hS-8nxPbDJM'>Omer Nevo</a>). However, I think one aspect of the adjudication is neither very prominent nor very well illustrated so far and that is probabilistic judging. The core thesis is that arguments are not just true or false, bought or not bought in their entirety, but they are 'bought to some degree' or the judges are 'convinced to some extend', i.e. arguments are assigned probabilities or probability distributions. What I want to do in this mini series are two things: a) Set up a basic framework of probabilistic judging and b) integrate and illustrates multiple facettes of debating within that framework. Part I deals with the evaluation of one argument in a vacuum, part II deals with direct interaction, i.e. extensions and rebuttal, and part III attempts to weight different arguments that aim to prove different metrics. To be very clear - I do not say that this is the ultimately correct way to judge a debate, I want to a) further the discourse on how arguments should be evaluated and b) illustrate how I think about probabilistic judging and give other people, who have thought less or different about the issue, a possibility to learn or improve my view. Additionally, I want to make this post as understandable as possible such that people who are very new to debating also get a chance to understand it. Given that I have a Machine Learning and Probability Theory background I might find concepts intuitive that you are new to. If such a situation occurs I would be grateful for feedback. If you, on the otherhand, understand what I am saying but disagree with the content, I would also be interested in your criticism and possible solutions. 

## Part I: evaluating one argument

In this part I want to focus on evaluating one argument in a vacuum. That means we ignore most of the things happening in a usual debate. We ignore all other teams, all extensions, all rebuttal, all framings, etc. We only consider exactly one argument. The two necessary conditions for an argument to persuade anyone are a) the argument is true and b) the argument is relevant. If you are convinced that an argument is true with high probability but not relevant you very likely do not care a lot about it. If you are convinced that something is important but not that it is true you are not convinced by it either. 

### The fundamentals of Probabilistic Inference

A probability distribution denotes the probability \(p(h)\) of a variable \(h\) taking a certain value, for example the probability of a human to have a certain height. It is more likely that a person is 1.8m than that they are 1m or 3m tall. It is also possible to condition that variable on another variable, i.e. we could look at the probability distribution of height conditioned on the gender \(g\) of a person \(p(h | g)\). Even though this is not true in reality, assume for simplicity that there are only two genders. The distribution of the height of all people can suddenly be explained by the two conditional distributions \(p(h | g=female)\) and \(p(h|g=male)\). Distributions can be defined on different domains. A distribution over probabilities, for example, can only range from 0 to 1 since probabilities below 0 or above 1 are just not defined. The distribution over the height of humans could technically be infinitely large but never below 0. The distribution over the measurement error of a clock could in theory be everywhere between minus and plus infinity, i.e. this clock can show a time that is arbitrarily wrong either in the future or past. To understand what probability distributions, conditionals and domains mean, consider the following figure.

<figure>
  <img src="/img/Probabilistic_Judging_1/dist_examples.png" alt="test"/>
  <figcaption>Illustration of a probability distribution, conditional probabilities and different domains</figcaption>
</figure>

Distributions can be used to illustrate a fact about the world as shown in the example of height. However, they can also be used to update our believes given new data. Let's say, for example, your current believe is that human height is distributed around the two peaks of 1.6 and 1.7 meters as shown in the above figure. Now you receive new information: The data that we have based that believe on are 10 years old and the decrease in human malnourishment has led to an average growth of humans of 5cm. Therefore you update your believe to a new distribution that is centered around the peaks at 1.65m and 1.75m respectively. There could also be other updates that you make about this believe, i.e. it might be found that the women whose height was measured during the initial measurements were selected from a particular group in society and therefore bias your result. For example only german women were measured because the study was conducted in germany. Since german women on average are slightly taller than the global average your updated distribution would include this fact and change the peak for women from 1.6m to 1.55m. This notion of updating our believes can be expressed via the fundamental rule of probabilistic inference: **Bayes rule**.

\(\underbrace{p(X\vert Y)}_{\text{posterior}} \propto \underbrace{p(Y\vert X)}_{\text{likelihood}} \underbrace{p(X)}_{\text{prior}}\)

We have a certain prior believe about a thing in the world, we get new data (here referred to as likelihood) and update this believe to yield a posterior. The posterior asks: "what is our believe about variable X after having seen data Y", i.e. what is our updated belief? 

I think persuasion can easily be integrated into this model. An adjudicator has the prior believe of the average intelligent globally informed citizen and updates these believes according to the claims made in the debate. As already motivated in the introduction there are two necessary conditions for an argument to be persuasive: it must be true and relevant. I posit that for both, truth and relevance, we have a prior distribution that can be updated through the speakers contributions. The updates should be proportional to the strength of the presented arguments, i.e. a very strong argument must lead to larger updates than a weak one. The final weighing of an argument can either be done by considering the entire distribution or by its expected value (the vertical line in the figures). To summarize: I posit that for every argument there is a distribution over the truth of the argument \(p_\text{truth}\) and a distribution over its relevance \(p_\text{relevance}\). Both of these distributions follow Bayes rule, i.e. the adjudicator has a prior believe about them and updates them according to the arguments made in the debate. To illustrate this further consider the following example. 

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

TODO: Im actually confused about principles right now.

## But what about the priors?

The most used criticism of Bayesian inference is: "Your posterior depends on the prior and if you choose the prior in dumb ways you can produce whatever results you want. Therefore Bayesian Inference does not work." And while it is true in some (but not most) real life applications that it is hard to choose a prior that makes sense we could also choose a prior that just says "I actually really don't know. It could be anything." However, in debating, there is a simple way to choose the priors that we already all agree on. In every judging manual you will find that the "Average intelligent globally informed Citizen" or "Average Informed Voter" (AIV) is the basis of adjudication. And the AIV surely has prior knowledge. For example if I asked you what your belief about the statement "Donald Trump is currently (January 2020) the president of the United States", then you would be very sure that this is a true and not a false statement. Maybe there would be some lingering uncertainty because he could have been impeached while you were asleep but you would be very certain. For the statement "Putin is 20 years old in 2020" your distribution would very much lean to the false end. If you were to assess the statement "Brexit will happen" in 2018 the past AIV would have very high uncertainty over the truth of statement probably including all possibilities from false to true. This is also true for the relevance of a given statement. For example, the prior distribution over "the harms of human made climate change" is definitely rather large (possibly with a wider range of options) or the prior distribution over "the wrongness of torturing many children for fun without additional reason" is definitely at the high end of badness. The negative effects of one minor insult are rather small and so is the AIVs respective prior. 

<figure>
  <img src="/img/Probabilistic_Judging_1/priors.png" alt="test"/>
  <figcaption>Three priors over the truth and relevance distributions</figcaption>
</figure>

All the knowledge that the AIV has should be seen as prior knowledge in this model of debating. There is obviously not a list of things that the AIV knows and therefore this question can not be answered for good but at least we have a clear way of solving disagreements during adjudication. 

However, I must point out that debating is a game that implies rules for how the priors are distributed. First, prior knowledge must align with the reality of the AIV, i.e. they know basic facts about the world but are not specialists in any particular field. They know the presidents of most major countries of the world, some basic economics and politics, etc. They do not know the finance minister of the Kongo, the exact melting point of all metals or the exact wording of the law of every country in the world. Even if a particular adjudicator knows these facts, for the purpose of the debate, they must assume not to know any of them. Second, prior knowledge distributions must be easily shiftable, i.e. the adjudicator is easily persuaded by arguments when good reasons are presented. This level of persuadability is probably a lot higher than for the average person that you meet on the street but is part of the game we are playing. Obviously this does not solve the issue of priors entirely but merely shifts it. It is for example unclear whether the AIV intuitively agrees with the statement: "Quantitative Easing hurts the economy in the long term" or if they are even supposed to know what Quantitative Easing is. This is a problem that we cannot solve independent of the probabilistic framework but I think forcing the adjudicators to explicitely think about the priors of the AIV decreases the difference in perception of arguments at least a bit and gives a framework to solve disagreements. Now we can more easily ask: "What are the AIVs priors and how does this change our perception of the argument?". 

## prior shift vs. absolute value

There are two different philosophies that could follow from the proposed framework. Either you could say the degree to which the person changed my belief from the prior to the posterior is the correct way to judge their contribution or the absolute value of the posterior, i.e. the difference between zero and the posterior. While you might say that debating is about changing opinions and therefore the difference between prior and posterior should be the right metric I would argue it has to be the difference between zero and the posterior. If someone for example sets the motion: DHB the USA should randomly nuke europe and OO points out that this is a very bad idea because it kills many people and probably leads to chaos and destruction then OO's statement is not controversial. The AIVs prior is already that this is a bad idea. It is therefore hard for an opposition team to further shift that prior to make it sound even more stupid. However, since I think that debating should resemble reality in some way, OO should win this argument even if OG gives more reasons or mechanisms because it is just nearly impossible to make plausible from gov. The fault in this setup is clearly with the CAs who have set such a terrible motion. However, most of the time CAs actually try to set balanced motions, thereby reducing this problem. Assuming that the motion is fair, I think the absolute value captures better what we should evaluate. If someone makes the argument that a motion reduced poverty by creating more jobs the average person would be less interested in the difference between their priors and posteriors, i.e. how much more jobs would be created than they expected but rather by the absolute number of jobs. This can be extended further to all other metrics such as the amount of suffering, the degree of unfairness or the number of people that would die. 

You might ask: Why do you talk so much about priors when you don't care about them anyways? To which the answer is two-fold: a) The prior anchors the argument and links it with reality. If there was no prior the rational strategy would just be to spam as many reasons and mechanisms as possible. b) The posteriors of one team are the priors for the following teams. If a closing team, for example, wants to run an analysis extension on an opening team, the openings posterior is the closings prior. Part II will deal extensively with this idea.

## Limitations of the model

This framework/illustration is obviously not perfect and I want to point out some of its limitations. If somebody finds a way to integrate them reasonably into this model I will be very grateful.

1. **Human communication is weird, we don't talk in logic:** Most of the time, teams do not make an argument in strictly logical terms. Instead of showing why a claim is true and relevant we often just concatenate sentences and convey some sort of argument without actually following the logic. However, similarly to temporary debating, it is the judges task to distill the logic from the speeches and compare it with each other. If the logic is too hard to extract because the speech was hard to follow (in a logic not language sence) then it is impossible for the judge with or without the probabilistic framework to make an informed decision.

2. **Overlap between truth and effect:** As you can already see in the first example for UBI, there sometimes is an  overlap between the truth and relevance part of an argument. Explaining why it is true that someone is negatively influenced already to some extend shows to what degree that influence is negative. Even though this might make the model "less distinctive" or "less clean" I do not think it is a big problem. In the end truth and relevance are combined anyways and it therefore does not matter whether the influence on the combined believe comes from the truth or relevance part as long as you do not count it twice. 

3. **Relevance sometimes lower priority:** In some debates the goal of the argument is undisputed, i.e. all teams agree that a certain things is either desirable or undesirable. Therefore the relevance part of an argument becomes less important. This might include claims such as "climate change is bad", "more jobs are good", "democracy is desirable" or "undeserved suffering is bad". The more important question in these debates becomes whether the claim the teams are making is actually leading to the desired outcome, i.e. to which degree it is true. Therefore the truth and relevance framework cannot be forced on all situations.

4. **Hierarchical models:** Theoretically, we could add infinite layers of priors to all of our believes. The prior of the AIV could have a meta prior about what the AIV is able to understand and think. This prior could have another prior, etc. The same can be done for every argument, since you can model all assumptions about reality in a hierarchy of priors. However, the model would become so complicated and confusing that I have decided to exclude all of these parts and focus on the basic understanding first. Since the purpose of this post is illustration and not building a computational model that seems reasonable.

## Nerd section: some statistical explanations 

- Bayes Rule not bayes theorem: Some of you might have seen Bayes formula already and therefore know it with the evidence term $\int p(y|x)p(x) dx$. This is the difference between Bayes rule and Bayes theorem, where the theorem uses the evidence term (i.e. the integral) to normalize the distribution to 1 such that it truely is a probability distribution. 
$$
\underbrace{p(X|Y)}_{\text{posterior}} = \frac{\underbrace{p(Y|X)}_{\text{likelihood}} \underbrace{p(X)}_{\text{prior}}}{\int \underbrace{p(y|x)p(x) dx}_{\text{evidence}}}
\propto \underbrace{p(Y|X)}_{\text{likelihood}} \underbrace{p(X)}_{\text{prior}}
$$
However, since we do not model Debating in a computational sense but rather to clarify and understand some of its peculiarities I have chosen Bayes rule to keep it simpler.

- The distributions I have chosen for the models of truth and relevance are the Beta and Gamma distribution. All other distributions that are on the correct domains would also be fine. For the illustration of probabilities in the beginning I chose the Normal distribution since is the most known distribution and also fits best to model height. 

- To combine two random values by multiplying them you usually have to sample from both and multiply the samples to get a histogramm over the new variable if they are not conjugate to each other. This would also have been possible but introduces another level of complexity. Therefore I have decided to just multiply the Gamma (relevance) distribution with the expected value of the Beta (truth). Even though this means that the variance of the truth distribution is not modeled perfectly I chose to trade this off for understandability. 

## Acknowledgements

Julian, Samuel, Bea, Maria, Marion.


***One last note:***

If you have any feedback regarding anything (i.e. layout or opinions) please tell me in a constructive manner via your preferred means of communication.

