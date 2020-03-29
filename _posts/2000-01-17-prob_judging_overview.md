---
layout: post
title:  "Probabilistic Adjudication: An overview"
date:   2019-01-17 23:01:30 +0200
author:     "Marius Hobbhahn"
header-img: "img/header-imgs/debate.png"
category: opinion
---

This post is not yet finished. I am still gathering feedback. You can read it anyway if you like but it will likely change a bit in the near future. 

## Motivation

I think an aspect of adjudication that is often a bit overlooked is a probabilistic interpretation. Even though arguments are often "bought to some degree" or the judges are "convinced to some degree" we rarely talk about what that means. I have written a three-part mini-series about this topic on my blog where I tried to be as detailed as possible. This post serves as a short motivation for and overview of the basic concepts. If you are unfamiliar with probability distributions you might want to check out the first paragraphs of Part I TODO:link.

We don't think about the world in a binary fashion. Our weather apps usually don't say "It will rain" but "It will rain with a probability of 70 percent". When we say something like "I am probably coming to the party" you express a probabilistic statement, i.e. you don't say "I'm definitely coming" or "I'm definitely not coming" but rather "I am more likely to come than not". Our decision making also works with probabilistic assessments. When the weather app says it will rain with 70 percent probability you might think: "well that is too much of a risk and I therefore do not go outside" or "I'm willing to take the risk". These kind of assessments not only happen on a small level in our daily lives but also in the decision making of governments and companies. If the experts say there is a 5 percent chance of a nuclear attack on the country the government will not reply "We will just round this 5 percent to 0 percent and do nothing". A company that predicts that there will be a 40 percent probability that a part of their supply chain will fail they will likely think of alternative strategies even though it is less likely to happen than not. The reason for these decisions is because the actors in question used an expected value to inform them. The expected damage of a nuclear scenario with 5 percent is still very large and a scenario where your supply chains brake with 40 percent might have catastrophical results for the company. But just assigning probabilities to an even does not tell the entire story. There can be a difference between two scenarios with the same assigned probability. We would, for example say, that around 50 percent of the outcomes of a repeated unbiased coin toss are tail and might also say that the probability of brexit actually happening might have been 50 percent in 2018. The difference is in the uncertainty that we have about these numbers. While we are very confident that a number close to 50 percent is the correct one when it comes to coin tosses we were very uncertain about the actual state of brexit. To include this estimate of uncertainty we can use probability distributions. If that feels a bit overwhelming at first, I can totally understand. The basic message that I want to get out there is that the world is not binary, our decision making is not binary and therefore debating and adjudication should not be either. They should be probabilistic.

### Beliefs are probability distributions

Every belief that we have can be described in terms of a probability distribution. The distribution over the belief that the sun rises tomorrow peaks at probability 1 and has very low uncertainty. The distribution over the believe that the stock market will rise tomorrow is peaked around 0.5 and has very high uncertainty. The distribution about the global effects of CoviD-19 represents some kind of "large but with high uncertainty". These distributions can be assigned to every claim or argument made in a debate and used to evaluate the strength of an argument. The reason why I chose probability distribution over point estimates (e.g. the probability of the sun rising tomorrow is 99.9%) is two-fold: a) Distributions can encode uncertainty which can be relevant in debating. When two judges disagree it might just be because the argument carries large uncertainty and b) A distribution is a nice way to encode that the average informed voter/global citizen (AIV) is not just one person with clearly defined beliefs but rather the combination of many opinions which differ in varying degrees. 

<figure>
  <img src="/img/Probabilistic_Judging_1/priors_overview.png"/>
</figure>

### Beliefs have a prior and can be shifted

About every belief we have a prior distribution, i.e. we already think an argument might be broadly plausible or it is completely unreasonable before a team makes it. However, this prior distribution can be shifted to a large extend via the arguments made in the debate. After all, we do not want our priors to influence the debate too much. Since debating is a sport in which we want to reward people for making convincing arguments rather than letting our priors determine the outcome of the debate we have to establish certain rules. The priors cannot be our personal priors but must roughly approximate the beliefs that the AIV holds. Additionally, these priors should be sceptical rather than naive, i.e. a team needs to provide reasons for an argument to be bought. Furthermore, a judge is able to be persuaded if an argument is made - the stronger the argument the larger the shift in the respective distribution. 
We can say that an argument is the combination of a truth and a relevance distribution, which are answering the questions "How true is this argument?" and "How relevant is this argument?" respectively. The relevance distribution is by no means restricted to any kind of moral metric. Relevance can mean happiness/suffering, freedom, democracy, individual rights, etc. depending on the context and the arguments the teams decide to make. The strength of an argument can be evaluated as the combination of the truth and the relevance distribution as shown in the following figure. 

<figure>
  <img src="/img/Probabilistic_Judging_1/general_notion.png"/>
</figure>

### Debating is more than evaluating a single argument

Other aspects of debating can easily be integrated into the framework:
- Rebuttal can be seen as a negative shift in the distribution of the argument being rebutted. The stronger the rebuttal the larger the shift. An argument can even be diminished to zero if the rebuttal is entirely refuting. Since rebuttal is constructive the rebutting team gets some credit proportional to the shift. This is discussed in Part II. TODO:link
- An extension that is based on the same claim as the opening teams arguments uses the posterior distribution of the opening team as prior. If, for example, the opening team convinces the judges to some degree that their argument is true and the closing team provides additional reasons for the truth of an argument. Whether the closing team beats the opening team can be determined by comparing the shift in the openings distribution with the shift from the openings distribution to the closings posterior distribution. This is also discussed in Part II. TODO:link
- Weighing arguments on different moral metrics, e.g. happiness vs. freedom can be integrated using an additional meta distribution. The more the teams persuade us that their metric is more important than that of the other team(s) the more they shift the meta distribution in their favour. Meta distributions also have priors. The priors reflect the moral beliefs of the AIV. In the debate "THW give more weight to young people's votes" the AIV would presumably give higher weight to the metrics of democracy, fairness and happiness than religious freedom. This is discussed in Part III. TODO:link

## What's the point?

Maybe this seemed entirely obvious to you but I was unable to find any resources on this part of debating and hope that at least some people might learn a thing or two. Besides that there are two aspects that I want to highlight.
1. **Outside** of debates: Having a more of less formal framework of persuasion and adjudication is helpful because it brings people on the same page and forces them to think about inconcistencies in debating when an aspect is not easy to integrate. I, for example, had to realize that my understanding of "rebuttal is constructive" was rather vague and inconsistent. Explaining it through the probabilistic framework forced me to come up with a consistent solution. 
2. **In** a debate, especially when adjudicating: Obviously, I am not asking you to explicitely calculate the distributions over the teams arguments within a debate. This framework is more of a mental assistance for the process of adjudication. When two adjudicators disagree about an argument, we can for example ask whether this disagreement is reasonably explained by the variance of the AIVs view on this argument. We can decide whether something was an extension by trying to identify to which degree the opening's argument convinced us and then compare it to the degree that the closing's argument furthered that belief. The framework is therefore used to unify understanding and language about debating to make adjudication more efficient. 

## Acknowledgements

Julian, Samuel, Bea, Maria, Marion, Anton


***One last note:***

If you have any feedback regarding anything (i.e. layout or opinions) please tell me in a constructive manner via your preferred means of communication.

