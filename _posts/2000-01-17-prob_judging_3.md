---
layout: post
title:  "Probabilistic Adjudication: Part III - clashes and metrics (Still under construction)"
date:   2019-01-17 23:01:30 +0200
author:     "Marius Hobbhahn"
header-img: "img/debate.png"
category: opinion
---

This post is not yet finished. I am still gathering feedback. You can read it anyway if you like but it will likely change a bit in the near future. 

## What is this mini-series about?

The overall purpose of these posts is to build a framework to judge debates probabilistically and illustrate how some parts of adjudication work within this framework. Part I (TODO:link) dealt with a single argument made by a team in a vacuum. Part II (TODO:link) dealt with direct interaction between two teams through rebuttal and extensions. This part deals with the comparison between different teams along different metrics. As already emphasized in the first part I want these posts to be as understandable as possible even for people that do not have any background in statistics or math. If you do not understand a certain explanation please let me know. If you have understood the explanation but think it is an incorrect model of debating please let me know as well, such that we can work out a better version.

## Agreement about the metric

If there is agreement about the metric the teams both argue that the motion would change the world along one moral axis. They merely disagree on the sign of the change, i.e. gov says it would change the world to the positive and opp says it would change to the negative. In the motion "THB the US should intervene militarily in Syria" both teams might, for example, agree that the question of the debate should be whether more or less war is the deciding one. This makes the life of the adjudicator easier, since they merely have to compare the distribution of the two teams and whoever has the higher expected value in their respective direction wins. To show illustrate this more clearly we consider the following three scenarios:

- Scenario 1: The oppositions argument is further in the negative than the government is in the positive with their respective arguments. Therefore, the opposition team wins this clash. 
- Scenario 2: The oppositions argument is less in the negative than the government is in the positive with their respective arguments. Therefore, the government team wins this clash. 
- Scenario 3: The oppositions argument is as far in the negative as the government is in the positive with their respective arguments. We cannot resolve this clash on its own but need to include other information such as their other arguments, their POIs, their responsiveness to that team, the order of the teams in the debate, etc. 

<figure>
  <img src="/img/Probabilistic_Judging_3/same_metric.png"/>
  <figcaption><span style="font-family:Papyrus; font-size:1em;">Belief about teams arguments</span></figcaption>
</figure>

If the teams agree on a metric that makes the life of the adjudicators easier - we just compare the sizes of the different effects on the agreed upon metric. Obviously, there still might be disagreement of whether the team actually showed this particular effect but it is still easier compared to a situation where multiple metrics have to be weighed against each other. 

## Disagreement about the metric

In many debates we have a situation where arguments are based on different philosophical principles, e.g. a Utilitarian calculus, fairness, justice, rights, etc. Often those are not easily translatable into each other and therefore we cannot just "count" their difference towards zero and compare. Therefore we have to weight the different metric compared to each other. We could choose to weigh every metric uniformly. However this would introduce the problem that it would be rational to just spam as many different arguments as possible as long as they are based on different metrics. This is clearly not how we want debating to be and I therefore propose to use a "meta distribution" that represents our belief about the strength of the different metrics in the debate. This distribution, similar to the other distributions we have used so far, has a prior and is updated through the arguments made in the debate. The meta distribution is combined with the posteriors of the arguments made in the debate similar to how we combine the truth and relevance distribution, i.e. a high value for your category in the meta distribution implies that the clash that argument is based on is very relevant in the debate and should count a lot. To illustrate the meta distributions and how they interact with the posteriors of the arguments, consider the following examples. The first is based on a scenario in which the debate revolves around two clashes and the second is used to illustrate three clashes. A debate can easily have more than three clashes, it just gets harder to illustrate and I therefore stopped at three. I also want to point out that meta distributions obviously have priors but I decided not to show them in the illustrations because it would make them too messy. So for the illustrations we can assume that the presented meta distributions are the posterior of the meta priors and the arguments that the teams provided during the debate. Arguments to shift our meta distributions are sometimes implicitely done through framing but often explicitely stated by the second speaker of a team. A team might, for example, argue that the metric their argument is based on is more important than an argument by another team that is based on a different metric by explaining why one is a logical necessity for the other (i.e. the right to life is a logical necessity for all other rights) or by a thought experiment that distills the metrics of the debate (i.e. whether a person should be allowed to be bound to your body for 9 months if that was the only way they could survive). There are, of course, many other ways to shift meta distributions but I just wanted to give these two from the abortion debate illustrate the idea.

### Two metrics

For this example we consider three debates where the teams agree on two different metrics but found no way to translate them into each other meaningfully. 

- Scenario 1: The government team in the debate argues with an argument regarding fairness. The opposition argues with an argument using a utilitarian calculus. The teams justify their arguments in such a way that our meta distribution after the debate favours the fairness argument by ca. 60:40 as shown in the left subfigures. After combining the posterior distribution we conclude that even though the meta distribution favours the fairness argument the posterior of the utility argument is more persuasive than the posterior of the fairness argument and the opposition team using the utility argument slightly wins the debate. 
- Scenario 2: The government team argues a rights metric, i.e. humans should have the right for something independent of the consequences. The opposition argues that due to that measure many people would die. The government team provides a very powerful argument for their case leading to a very high posterior. However, the opposition gives a lot of good reasons why we should consider the number of deaths more than the violation of rights and the government fails to respond to any of them. Therefore the meta distribution very heavily shifts in favour of the number of deaths. The combination of the respecive posterior distributions and the meta distribution yields the distribution shown in the middle subfigures. So even though the government team has a potentially more powerful argument they fail to respond w.r.t the metrics and lose the debate. 
- Scenario 3: The government argues using a utilitarian argument. The opposition responds on the utilitarian calculus but is unable to win this clash on its own. The opposition additionally argues on a rights based metric. They both do not argue at all for why any of the clashes is more important and we therefore have a very uncertain meta distribution over the two metrics. However, our prior does not favour any of the two given the motion and therefore we weigh them equally as shown in the right subfigures. After combining the posteriors with the meta prior we reach a situation in which the opposition is not able to beat the government on any of the two metrics but the combination of both is able to beat the contribution of the government. Therefore, opposition wins. 

<figure>
  <img src="/img/Probabilistic_Judging_3/2D_meta_priors.png"/>
  <figcaption><span style="font-family:Papyrus; font-size:1em;">Meta distributions</span></figcaption>
</figure>

<figure>
  <img src="/img/Probabilistic_Judging_3/different_metric2D.png"/>
  <figcaption><span style="font-family:Papyrus; font-size:1em;">Beliefs over the contributions of the teams after considering the meta distributions</span></figcaption>
</figure>

### Three metrics

The following scenarios can be seen as the same debate taking place in three different rooms. For simplicity we assume the teams make the exact same argument in every debate only differing in their argumentation w.r.t the metric, i.e. shifting the meta distribution. To simplify even further we also assume that the government team always runs a utilitarian case and the opposition a fairness and a rights case. 

- Scenario 1: The teams provide equal justifications for all respective metrics and our meta distribution is therefore agnostic. After combining meta distribution and posteriors we end up with a situation in which the combined arguments from opposition beat the contribution from government and therefore opposition wins. 
- Scenario 2: 

<figure>
  <img src="/img/Probabilistic_Judging_3/3D_meta_priors.png"/>
  <figcaption><span style="font-family:Papyrus; font-size:1em;">Meta distributions. Red implies high probability mass.</span></figcaption>
</figure>

<figure>
  <img src="/img/Probabilistic_Judging_3/different_metric3D.png"/>
  <figcaption><span style="font-family:Papyrus; font-size:1em;">Beliefs over the contributions of the teams after considering the meta distributions</span></figcaption>
</figure>

## What about the priors?

http://trolleyproblem.blogspot.com/2012/11/what-does-good-judge-believe.html

## Limitations of the model:

burdens? 
meeting the right comparative?
doing a weighing better than other teams

## Conclusion

debating is very inconsistent

## Nerd section: some statistical explanations 

- N-dimensional probability simplex
- similar to other prob, expected value

## Acknowledgements


***One last note:***

If you have any feedback regarding anything (i.e. layout or opinions) please tell me in a constructive manner via your preferred means of communication.

