---
layout:     post
title:      "How much animal suffering is there?"
subtitle:   "A back-of-the-envelope attempt to quantify animal suffering caused by human consumption"
date:       2020-07-05 20:28:00
author:     "Marius Hobbhahn"
header-img: "img/header-imgs/sad_cow.png"
category:   opinion
---

## **What is this post about?**

Before we can answer important moral questions such as "which cause is most cost-efficient w.r.t. the reduction of suffering?" we first have to have an approximate view of the status quo. While there are lots of reports of the horrendous conditions that animals face in factory farming, I want to attempt to give a quantitative estimate of how much suffering animals face in factory farms and 
fishfarms. This post is the second in a series on approximating the amount of suffering in the world. I would recommend to check out the <a href='http://www.mariushobbhahn.com/2020-06-29-human_suffering/'>first post</a> to get a better understanding of the ideas but especially recommend it if you are unfamiliar with the concepts of <a href='https://en.wikipedia.org/wiki/Disease_burden'>disease burden</a> and <a href='https://en.wikipedia.org/wiki/Disability-adjusted_life_year'>disability-adjusted life years (DALYs)</a>. I also want to emphasize that this post does not include estimates for <a href='https://en.wikipedia.org/wiki/Wild_animal_suffering'>wild animal suffering</a> but is restricted to animals held and killed for human consumption but I will try to make a similar estimate for wild animals in a future post. 

Lastly, I want to emphasize that we have to be cautious with these kinds of estimates. A lot of the assumptions that I make are very broad and carry high uncertainty. The conclusions can, therefore, be wrong by multiple magnitudes. The general framing for this post is more a first guestimate than a definitive answer to the question "how much animal suffering is there due to human consumption?". 

Similar to last article I am just an interested stat nerd that crunched some numbers and made some plots. The hard work of collecting the data and cleaning them has been mostly done by others such as <a href='https://ourworldindata.org/meat-production#all-charts-preview'>ourworldindata.org</a> or the WHO. 

## Why should animal suffering have moral weight?

Before we actually start comparing I think it is important to revisit the reasons why we should give animal suffering some moral weight. This is both for people who are rather new to these ideas but also for those who currently do not believe in them. If you have any objections regarding the following arguments please let me know. For more elaborate and detailed explanations have a look at the absolutely excellent <a href='https://www.openphilanthropy.org/2017-report-consciousness-and-moral-patienthood'>openphil article</a> on consciousness and moral patienthood.

0. **A caveat:** The openphil article mostly discusses the phenomenon of consciousness and not the ability to suffer. It is unclear whether consciousness is a necessary condition for suffering but I currently believe that they are at least strongly correlated. In the context of this argument this implies that I use certain arguments from the openphil article which are made about consciousness as if they implied capability to suffer. 

1. **An evolutionary explanation:** In <a href='https://en.wikipedia.org/wiki/The_Selfish_Gene'>The Selfish Gene</a> Richard Dawkins describes the theory that animals (including humans) are merely vessels of their genes. The behaviour of nearly all species can be interpreted in terms of its utility to the reproduction of the gene. Altruistic behaviour, for example, have positive expected values if you include the distance of kin in your model (saving a brother would be 1/2 of saving yourself, saving a cousin 1/4th and so forth). If you believe this theory then the phenomenon of consciousness and especially the capability to suffer only arose because they yield evolutionary advantages. Life had become so complicated that the "rules of survival" could not be hard coded but a more heuristic-based and abstract system such as consciousness was more well-adapted. Especially for more abstract negative emotions such as grief or guilt it seems plausible to me that a conscious individual that can connect the emotion to the event in question and reason about its origin would be beneficial for its own survival. However, no behavior strictly requires consciousness - it could be learnable without reasoning or conscious experiences given a sufficient amount of time. But if there are evolutionary reasons for humans to develop it I don't see why these exact same reasons should not also apply to animals. 

2. **Potentially consciousness indicating features:** In the openphil report there is a section on <a href='https://www.openphilanthropy.org/2017-report-consciousness-and-moral-patienthood#PCIFsWork'>potentially consciousness indicating features (PCIFs)</a>. There you can find a large table that lists PCIFs and which animals fulfull them. For most of the high-level, abstract features such as "has a theory of mind" or "Long-term alteration in behavior to avoid noxious stimuli" we essentially don't have conclusive answers. For the low-level, physiological features like "Has a central nervous system", "Has neural nociceptors" or "Physiological responses to nociception or handling" we know that most animals (that are as developed as fish and higher) have them. So while we can't conclude that animals clearly have a phenomenal experience (i.e. they feel suffering) when there is an averse stimuli, we do know that they show direct physical responses and that they have the physiological conditions (i.e. nociception) to do so. While this behaviour could also be expressed without consciousness (e.g. In the automata chicken: "If harm, then run") I would not rule out that there is a phenomenal experience of pain attached to it. 

3. **Err on the side of caution:** I'm generally not a big fan of the ``Err on the side of caution'' argument because people often use it to justify risk-averse behaviour which does not maximize expected value. However, the question of whether animals can suffer is one of few exceptions because of two reasons. First, our understanding of consciousness as a phenomenon is very limited. We can't even be certain that other people than ourselfes are conscious or have good explanations for its necessary or sufficient conditions. Given that our uncertainty is so high it is very unclear what the expected value actually is and how much credit we should assign to it. Second, the trade-off is in favor of not killing animals. Even if you would assign a very small probability to animals being capable of suffering the expected absolute amount of suffering would still be massive due to the large amounts of animals in factory farms. Additionally, the harm for us is really not that large. We have to stop eating meat and treat animals better. Both of these seem to have very low cost attached compared to the potential harm done to animals if they can suffer. 


## Shut up and calculate

Before we get into the actual computations it is important to get a more accurate picture of factory farming. Then I attempt to answer the two hardest questions of this article: a) "How bad is the situation for animals in factory farms?" and b) "what is the suffering exchange rate between humans and animals?". After giving estimates for the answers to these questions we will compare animal suffering to human suffering. 

### Animals killed for production

The number of animals we kill for human consumption has drastically increased over the last 70 years. 

<figure>
  <img src="/img/Human_suffering/animals_killed_over_time.png"/>
</figure>

The first observation is that we see mostly chickens. While humanity slaughtered around 6.5 billion Chicken a year it has grown to a collective 68.8 billion in 2018. To see what has happened to other animals we remove chickens from the graph.

<figure>
  <img src="/img/Human_suffering/animals_killed_over_time_wo_chicken.png"/>
</figure>

We find that the number of other animals has increased as well but none of them at the same rate as chickens. While chickens had a 10-fold increase from 1961 to 2018 pigs increased 4-fold, turkeys 3.5-fold, sheep 1.5-fold, Goats 3.5-fold, and cattle 1.3-fold. While the relative increases are interesting I think the absolute numbers give a more interesting perspective. The current world population (summer 2020) is around 7.6 billion people. Humanity kills 68.8 billion chicken every year which means 9 chickens on average per person and year. If you account for the fact that some people don't eat meat for religious or ethical reasons this means over 10 per person and year. Doing the same calculation you get 4 percent of a cow, 9 percent of a Turkey, 20 percent of a pig, 6 percent of a goat, and 8 percent of a sheep per person and year. That's a lot of meat. 

TODO: distribution by country & kilo per person & year.

Humans not only kill land-animals but also fish in large scale for their consumption. 

<figure>
  <img src="/img/Human_suffering/seafood_production_over_time.png"/>
</figure>

As we can see both the number of fish that is captured but also the amount of seafood that is produced in aquacultures increases over time. However, the graph for aquaculture might be a bit misleading since it includes not only fish but also aquatic plants such as seaweed and smaller species such as Molluscs and Crustaceans. According to <a href='http://www.fao.org/3/ca5224en/ca5224en.pdf'>this UN report</a> the top ten species groups (measured in tons) in global aquaculture are as follows. 

<figure>
  <img src="/img/Human_suffering/top_ten_aquaculture_composition.png"/>
</figure>

Only four of these ten species are actually fishes and the rest is either aquatic plans or smaller animals where I am really uncertain whether they can suffer. For simplicity I will not account for them in my computations but I would be interested in expert opinions on the matter. 

To summarize what we know about the current situation of factory farming and aquaculture consider the following two tables. The first shows the number of animals killed for human consumption in 2018 and the second shows the number of fishes killed in aquaculture (computed by their weight in relation to the tons of production from above). 

TODO: table for animals in 2018

TODO table for fish in 2017

### How do we approximate animal suffering?

There are many qualitative reports (TODO:list) on the bad conditions in factory farms. TODO: make a long list to get the vibe across. 
However there are only very few large scale reports on quantative statistics on diseases and other sources of suffering in these institutions. Therefore, I want to choose a slightly different approach. 
To estimate how much suffering animals have we should first ask a simplifying question: "How bad is life on a factory farm if animals had the same capability to suffer as humans?". Since we have high uncertainty about the answer I first want to find upper and lower bounds (think of them as my 95% or more credibility interval). As a hard lower bound I chose the DALY values for Singapore in 2017. It is a well run society with the lowest relative disease burden on the planet and I am pretty confident that factory farms are worse. Singapore had around 16K DALYs per 100K citizens in 2017. After discussion with multiple friends that are all well informed on the conditions of factory farms I came to the conclusion that factory farms are probably not worse than the worst events in human history such as the concentration camps run by the nazis or the Rwandan genocide. Since there is a DALY estimate of the Rwandan genocide in 1994 we will use it (724K DALYs per 100K citizens) as an upper bound. 

Since there are some quantitative numbers for certain species we can estimate a more soft lower bound for them. According to this website TODO: link more than 80 percent of pigs have pneumonia upon slaughter and genetic manipulation has left 90 percent of broiler chickens unable to walk properly. Comparin this to the DALYs that these respective diseases would induce for humans through this WHO report TODO: link and multiplying it with the percentage of animals that are affected we get to a soft lower bound of 49K DALYs for pigs and 33K DALYs per 100K for chickens. Since the original sources for these numbers seem to be unavailable I would be a bit cautious with their validity but we still have the hard lower bound just in case. 
Lastly, I added my personal expected value for the suffering in factory farms. My intuitions were that it is better than the Rwandan genocide but probably worse than living in Haiti after the 2010 earth quake which was estimated around 181K DALYs per 100K people. While it was definitely a catastrophe of large scale my intuition is that factory farms are worse. While many houses are destroyed and most parts of civilisation are disfunctional, there are NGOs who treat the wounded and provide water, food and shelter to those in need. While diseases spread faster than normal they are fought and contained. In comparison, factory farms do not treat diseases once they break out because it is too expensive. However, factory farms with their multiple thousand animals in tight space are a perfect breading ground for diseases and therefore many can be found. The physical pain of many of the conditions that are frequently reported such as the broken bones of broilers felt intuitively high. Additionally, I estimated the psychological damage for the animals to be unable to move at all because their cages are exactly as large as their bodies to be high. My personal estimate is, therefore, in the ballpark of 350K DALYs per 100K individuals but I would be interested in more calibrated people's opinions. I also did not distinguish between different species of animals because I don't know how different the conditions in the factory farm are depending on the species. 

To recap: As a hard upper bound I chose Rwanda in 1994 (724K DALYs), as a hard lower bound I chose Singapore in 2017 (16K DALYs) and as a personal guesstimate I chose 350K DALYs. For some animals such as pigs and chickens we can find a more soft lower bound by looking at some of their most common diseases. 

### What's the suffering exchange rate?

This question seems to be by far the hardest but is probably the holy grail of animal welfare. Because of the fuzziness of questions about consciousness in general but especially because what the experiences of other species are. The <a href='https://en.wikipedia.org/wiki/Qualia'>Qualia</a> problem is already hard enough for humans, how are we even supposed to start with animals? So to get rough estimates I used the numbers and justifications presented in TODO:consciousness and moral patienthood which is by far the most comprehensive and detailed article I know on the subject. From the article we get three important pieces of information. First, we get a "Probability of consciousness of a sort I intuitively morally care about" that is given by the original author. Since they have spend more time on the subject and I find them broadly plausible I will just copy these probabilities. Secondly, we get information about the brain weight of different species and lastly they estimate the number of neurons that different species have in their brain. 

To get the expected suffering exchange rate I multiply the probability that I find moraly relevant with the relative difference in brain weight to get a first metric and multiply it with the relative difference in neurons to get a second one. These metrics are imperfect for suffering for multiple reasons: a) brain weight would have unintuitive implications such as "women are less capable of suffering than men on average" and b) it is very unclear how the relationship between weight and capability to suffer ist. Maybe it is linear, maybe it is exponential, maybe the ability to suffer requires a certain threshold or maybe it is a combination of the previous ideas. I could easily come up with reasons for and against all of these hypotheses and this merely shows that we have little to know idea, especially because it is hard or impossible to find evidence for or against them other than our intuitions. However, one of the intuitions that seems very strong is that the ability to suffer somehow scales with the complexity of your brain. We don't know exactly how it is linked but we would probably agree that a cows ability to suffer is lower than that of a human but higher than a chicken. Since the brainweight and the number of neurons are the only available data points I used them as proxies. In the following table you can find a summary of the just described facts and rates. 

TODO: table of rates.

### What are the results?

In the following we will have a look at the results coming from the different metrics. First, we will have a short overview of the suffering over time. 

TODO: over time.

TODO: interpretation. This is only a very mediocre approximation since I don't have any actual data of how conditions in factory farms changed over time. The more interesting interpretations come from the snapshots we have from the most recent data (2017/2018) which we will dive in now. 

Let's first check out the disease burden on animals that is weighed by the weight of each species' brain. 

TODO: image






### Nerd section - Data preparation


## Conclusions



## What could be improved in my modeling

As emphasized multiple times already, the questions I try to find answers for are very hard questions with high uncertainty attached to them. Therefore, there are many ways in which my model could be improved but I am not sure how realistic some of these suggestions are

1. A more accurate image of the conditions in factory farms. More data and better calibrated expert opinion would definitely make this estimate more accurate (please contact me if you are e.g. working with an animal organisation and have ideas for quantification). 

2. What is the suffering exchange rate between different species? This seems to be the hardest yet most important question of the entire endeavor. If you have any ideas that are better than using brain weight as a proxy please contact me. 

3. DALYs are still not a perfect representation of suffering. A longer discussion can be found in part I (TODO:link). If you have a better metric that is also applicable to animals I would be very interested. 


#### ***One last note***

If you have any feedback regarding anything (i.e. layout or opinions) please tell me in a constructive manner via your preferred means of communication.


https://www.openphilanthropy.org/2017-report-consciousness-and-moral-patienthood

https://www.effectivealtruism.org/articles/cause-profile-animal-welfare/

https://butcantheysuffer.wordpress.com/tag/centre-for-effective-altruism/

%%% further evidence for animal cruelty in factory farming
https://animalequality.org/news/why-factory-farming-is-the-largest-cause-of-animal-abuse-in-history/

%%% disability weights
https://www.who.int/healthinfo/global_burden_disease/GBD2004_DisabilityWeights.pdf?ua=1

%%% list of diseases (no quantification)
https://www.lcanimal.org/index.php/campaigns/other-issues/factory-farming

%%% list of painful practices
https://awionline.org/content/inhumane-practices-factory-farms

%%% description of diseases for chicken
https://www.aspca.org/sites/default/files/chix_white_paper_nov2015_lores.pdf

%%% 25% of chicken have painful lameness
https://www.ciwf.org.uk/factory-farming/animal-cruelty/

%%% list of cattle diseases
https://www.tractorsupply.com/tsc/cms/life-out-here/the-barn/livestock/common-cattle-diseases

%%% general best practice for animal farming
https://vikaspedia.in/agriculture/livestock/general-management-practices-of-livestock/common-animal-diseases-and-their-prevention-and-treatments

%%% further evidence for animals have bad lifes
https://petpedia.co/factory-farming-statistics/

%%% fish statistics
https://www.sentienceinstitute.org/us-factory-farming-estimates

%%% finally some numbers about chicken and pigs
https://www.onegreenplanet.org/animalsandnature/facts-about-the-lives-of-factory-farmed-animals/

%%% even more animal cruelty
https://sentientmedia.org/farmed-animals/

%%% this is supposed to say that fish become suicidal?
https://royalsocietypublishing.org/doi/full/10.1098/rsos.160030

%%% fish diseases from fish farms
https://www.animal-ethics.org/diseases-suffered-fish-farms/

%%% brain weights
https://mste.illinois.edu/malcz/DATA/BIOLOGY/Animals.html

