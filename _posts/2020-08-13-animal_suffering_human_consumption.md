---
layout:     post
title:      "How much animal suffering is there?"
subtitle:   "A back-of-the-envelope attempt to quantify animal suffering caused by human consumption"
date:       2020-08-13 20:28:00
author:     "Marius Hobbhahn"
header-img: "img/header-imgs/sad_cow.png"
category:   opinion
---

## **What is this post about?**

Before we can answer important moral questions such as "which cause is most cost-efficient w.r.t. the reduction of suffering?" we first have to have an approximate view of the status quo. While there are lots of reports of the horrendous conditions that animals face in factory farming, I want to attempt to give a quantitative estimate of how much suffering animals face in factory and
fish farms. This post is the second in a series on approximating the amount of suffering in the world. I would recommend to check out the <a href='http://www.mariushobbhahn.com/2020-06-29-human_suffering/'>first post</a> to get a better understanding of the ideas but especially recommend it if you are unfamiliar with the concepts of <a href='https://en.wikipedia.org/wiki/Disease_burden'>disease burden</a> and <a href='https://en.wikipedia.org/wiki/Disability-adjusted_life_year'>disability-adjusted life years (DALYs)</a>. I also want to emphasize that this post does not include estimates for <a href='https://en.wikipedia.org/wiki/Wild_animal_suffering'>wild animal suffering</a> but is restricted to animals held and killed for human consumption but I will try to make a similar estimate for wild animals in a future post. Pets and laboratory animals are also not included in this estimate since pets probably don't suffer as much as animals in factory farms and their quantity is rather insignificant when compared to factory farms. 

Lastly, I want to emphasize that we have to be cautious with these kinds of estimates. A lot of the assumptions that I make are very broad and carry high uncertainty. The conclusions can, therefore, be wrong by multiple magnitudes. The general framing for this post is more a first guestimate than a definitive answer to the question "how much animal suffering is there due to human consumption?".

Similar to the last article I am just an interested stat nerd that crunched some numbers and made some plots. The hard work of collecting the data and cleaning them has been mostly done by others such as <a href='https://ourworldindata.org/meat-production#all-charts-preview'>ourworldindata.org</a> or the WHO.

## Why should animal suffering have moral weight?

Before we actually start comparing I think it is important to revisit the reasons why we should give animal suffering some moral weight. This is both for people who are rather new to these ideas but also for those who currently do not believe in them. If you have any objections regarding the following arguments please let me know. For more elaborate and detailed explanations have a look at the absolutely excellent <a href='https://www.openphilanthropy.org/2017-report-consciousness-and-moral-patienthood'>openphil article</a> on consciousness and moral patienthood.

0. **A caveat:** The openphil article mostly discusses the phenomenon of consciousness and not the ability to suffer. It is unclear whether consciousness is a sufficient condition for suffering but it seems like a necessary one. I currently believe that consciousness and suffering are at least strongly correlated. In the context of this argument, this implies that I use certain arguments from the openphil article which are made about consciousness as if they implied capability to suffer.

1. **An evolutionary explanation:** In <a href='https://en.wikipedia.org/wiki/The_Selfish_Gene'>The Selfish Gene</a> Richard Dawkins describes the theory that animals (including humans) are merely vessels of their genes. The behavior of nearly all species can be interpreted in terms of its utility to the reproduction of the gene. Altruistic behaviors, for example, have positive expected values if you include the distance of kin in your model (saving a brother would be 1/2 of saving yourself, saving a cousin 1/4th, and so forth). If you believe this theory then the phenomenon of consciousness and especially the capability to suffer only arose because they yield evolutionary advantages. Life had become so complicated that the "rules of survival" could not be hardcoded but a more heuristic-based and abstract system such as consciousness was more well-adapted. Especially for more abstract negative emotions such as grief or guilt, it seems plausible to me that a conscious individual that can connect the emotion to the event in question and reason about its origin would be more likely to survive. However, no behavior strictly requires consciousness - it could be learnable without reasoning or conscious experiences given a sufficient amount of time. But if there are evolutionary reasons for humans to develop it I don't see why these exact same reasons should not also apply to animals.

2. **Potentially consciousness indicating features:** In the openphil report there is a section on <a href='https://www.openphilanthropy.org/2017-report-consciousness-and-moral-patienthood#PCIFsWork'>potentially consciousness indicating features (PCIFs)</a>. There you can find a large table that lists PCIFs and which animals have them. For most of the high-level, abstract features such as "has a theory of mind" or "Long-term alteration in behavior to avoid noxious stimuli" we essentially don't have conclusive answers. For the low-level, physiological features like "Has a central nervous system", "Has neural nociceptors" or "Physiological responses to nociception or handling" we know that most animals (that are as developed as fish and higher) have them. So while we can't conclude that animals clearly have a phenomenal experience (i.e. they feel suffering) when there is an adverse stimulus, we do know that they show direct physical responses and that they have the physiological conditions (i.e. nociception) to do so. While this behavior could also be expressed without consciousness (e.g. In the automata chicken: "If harm, then run") I would not rule out that there is a phenomenal experience of pain attached to it.

3. **Err on the side of caution:** I'm generally not a big fan of the ``Err on the side of caution'' argument because people often use it to justify risk-averse behavior which does not maximize expected value. However, the question of whether animals can suffer is one of few exceptions because of two reasons. First, our understanding of consciousness as a phenomenon is very limited. We can't even be certain that other people than ourselves are conscious or have good explanations for its necessary or sufficient conditions. Given that our uncertainty is so high it is very unclear what the expected value actually is and how much credit we should assign to it. Second, the trade-off is in favor of not killing animals. Even if you would assign a very small probability to animals being capable of suffering the expected absolute amount of suffering would still be massive due to the large amounts of animals in factory farms. The harm for us, on the other hand, is really not that large. We have to stop eating meat and treat animals better. Both of these seem to have very low cost attached compared to the potential harm done to animals if they can suffer.

## Shut up and calculate

Before we get into the actual computations it is important to get a more accurate picture of factory farming. Afterward I attempt to answer the two hardest questions of this article: a) "How bad is the situation for animals in factory farms?" and b) "what is the suffering exchange rate between humans and animals?". After giving estimates for the answers to these questions we will compare animal suffering to human suffering.

### Animals killed for production

The number of animals we kill for human consumption has drastically increased over the last 70 years.

<figure>
  <img src="/img/Animal_Suffering/animals_killed_over_time.png"/>
</figure>

The first observation is that we see mostly chickens. While humanity slaughtered around 6.5 billion Chicken a year in 1961 it has grown to a collective 68.8 billion in 2018. To see what has happened to other animals we remove chickens from the graph.

<figure>
  <img src="/img/Animal_Suffering/animals_killed_over_time_wo_chicken.png"/>
</figure>

We find that the number of other animals has increased as well but none of them at the same rate as chickens. While chickens had a 10-fold increase from 1961 to 2018 pigs increased 4-fold, turkeys 3.5-fold, sheep 1.5-fold, Goats 3.5-fold, and cattle 1.3-fold. While the relative increases are interesting I think the absolute numbers give a more interesting perspective. The current world population (summer 2020) is around 7.6 billion people. Humanity kills 68.8 billion chicken every year which means 9 chickens on average per person and year. If you account for the fact that some people don't eat meat for religious or ethical reasons this means over 10 per person and year. Doing the same calculation you get 4 percent of a cow, 9 percent of a Turkey, 20 percent of a pig, 6 percent of a goat, and 8 percent of a sheep per person and year. That's a lot of meat! As you can see in the following there is a large correlation between the amount of meat consumed by individuals and the wealth of a given country. Since the wealth of most nations has increased quite steadily over the last couple of decades, I expect the meat consumption to rise in most states around the world. This makes animal suffering an even more salient problem than it already is. 

<figure>
  <img src="/img/Animal_Suffering/global_meet_per_person.png"/>
</figure>

Humans not only kill land-animals but also fish on large scale for their consumption.

<figure>
  <img src="/img/Animal_Suffering/seafood_production_over_time.png"/>
</figure>

As we can see both the number of fish that are captured but also the amount of seafood that is produced in aquacultures increases over time. However, the graph for aquaculture might be a bit misleading since it includes not only fish but also aquatic plants such as seaweed and smaller species such as Molluscs and Crustaceans. According to <a href='http://www.fao.org/3/ca5224en/ca5224en.pdf'>this UN report</a> the top ten species groups (measured in tons) in global aquaculture are as follows.

<figure>
  <img src="/img/Animal_Suffering/top_ten_aquaculture_composition.png"/>
</figure>

Only four of these ten species are actually fish and the rest is either aquatic plants or smaller animals where I am really uncertain whether they can suffer. For simplicity, I will not account for them in my computations but I would be interested in expert opinions on the matter.

To summarize what we know about the current situation of factory farming and aquaculture consider the following two tables. The first shows the number of animals killed for human consumption in 2018 and the second shows the number of fish killed in aquaculture (computed by their weight in relation to the tons of production from above).

<figure>
  <img src="/img/Animal_Suffering/Animals_killed_2018.png"/>
</figure>

<figure>
  <img src="/img/Animal_Suffering/Fish_killed_2017.png"/>
</figure>

### How do we approximate animal suffering?

There are many qualitative reports (<a href='https://animalequality.org/news/why-factory-farming-is-the-largest-cause-of-animal-abuse-in-history/'>[1]</a>, <a href='https://www.lcanimal.org/index.php/campaigns/other-issues/factory-farming'>[2]</a>, <a href='https://awionline.org/content/inhumane-practices-factory-farms'>[3]</a>, <a href='https://www.aspca.org/sites/default/files/chix_white_paper_nov2015_lores.pdf'>[4]</a>, <a href='https://www.ciwf.org.uk/factory-farming/animal-cruelty/'>[5]</a>, <a href='https://petpedia.co/factory-farming-statistics/'>[6]</a>, <a href='https://www.onegreenplanet.org/animalsandnature/facts-about-the-lives-of-factory-farmed-animals/'>[7]</a>, <a href='https://sentientmedia.org/farmed-animals/'>[8]</a> ...) on the bad conditions in factory farms. They include but are not limited to: Respiratory diseases, Bacterial infections, Crippled legs, Pneumonia, Cholera, Swine arthritis, Salmonellosis, and many other diseases. Additionally, painful practices such as Tail Docking, Dehorning, Castration, and Debeaking are common practice - of course without anesthetics to save costs. While one could argue that the number of diseases does not have to imply anything - after all, there might only be few individual animals affected - factory farms are a perfect breeding ground for every disease that is spread through bacteria or viruses since thousands of animals are cramped up in small spaces with very limited airflow.
However, unfortunately, there are only very few large scale reports containing quantitative statistics on diseases and other sources of suffering in these institutions. Therefore, I want to choose a slightly different approach.
To estimate how much suffering animals have we should first ask a simplifying question: "How bad is life in a factory farm if animals had the same capability to suffer as humans?". Since we have high uncertainty about the answer I first want to find upper and lower bounds (think of them as my 95% or more credibility interval). As a hard lower bound I chose the DALY values for Singapore in 2017. It is a well-run society with the lowest relative disease burden on the planet and I am pretty confident that factory farms are worse. Singapore had around 16K DALYs per 100K citizens in 2017. After a discussion with multiple friends that are all well informed on the conditions of factory farms, I came to the conclusion that factory farms are probably not worse than the worst events in human history such as the concentration camps run by the nazis or the Rwandan genocide. Since there is a DALY estimate of the Rwandan genocide in 1994 we will use it (724K DALYs per 100K citizens) as an upper bound.

Since there are some quantitative numbers for certain species we can estimate a softer lower bound for them. According to this <a href='https://www.onegreenplanet.org/animalsandnature/facts-about-the-lives-of-factory-farmed-animals/'>website</a> more than 80 percent of pigs have pneumonia upon slaughter and genetic manipulation has left 90 percent of broiler chickens unable to walk properly. Comparing this to the DALYs that these respective diseases would induce for humans through this <a href='https://www.who.int/healthinfo/global_burden_disease/GBD2004_DisabilityWeights.pdf?ua=1'>WHO report</a> and multiplying it with the percentage of animals that are affected we get to a soft lower bound of 49K DALYs for pigs and 33K DALYs per 100K for chickens. Since the original sources for these numbers seem to be unavailable I would be a bit cautious with their validity but we still have the hard lower bound just in case.
Lastly, I added my personal expected value for the suffering in factory farms. My intuitions were that the situation is less bad than the Rwandan genocide but probably worse than living in Haiti after the 2010 earthquake which was estimated around 181K DALYs per 100K people. While it was definitely a catastrophe of large scale my intuition is that factory farms are worse. While many houses were destroyed and most parts of civilization were dysfunctional, there were NGOs who treat the wounded and provide water, food, and shelter to those in need. While diseases spread faster than normal they are fought and contained. In comparison, factory farms do not treat diseases once they break out because it is too expensive. Since factory farms with their multiple thousand animals in tight space are a perfect breeding ground for diseases a lot of them break out. The physical pain of many of the conditions that are frequently reported such as the broken bones of broilers felt intuitively high. Additionally, the fact that animals are bred to produce a lot of meat they are massively overweight which comes with further pain and risk of other conditions such as cardiovascular diseases. Even though it is hard to quantify clearly, my personal intuitive estimate is, therefore, in the ballpark of 350K DALYs per 100K individuals but I would be interested in more calibrated people's opinions. I also did not distinguish between different species of animals because I don't know how different the conditions in the factory farm are depending on the species but I would estimate that it is worse for chickens than for Cows based on the reports and stories.

To recap: As a hard upper bound I chose Rwanda in 1994 (724K DALYs), as a hard lower bound I chose Singapore in 2017 (16K DALYs) and as a personal guesstimate I chose 350K DALYs. For some animals such as pigs and chickens, we can find a softer lower bound by looking at some of their most common diseases.

### What's the suffering exchange rate?

This question seems to be by far the hardest but is probably the holy grail of animal welfare. The fuzziness of questions about consciousness in general but especially because of what the experiences of other species are this question is very hard to estimate. The <a href='https://en.wikipedia.org/wiki/Qualia'>Qualia</a> problem is already hard enough for humans, how are we even supposed to start with animals? So to get rough estimates I used the numbers and justifications presented in <a href='https://www.openphilanthropy.org/2017-report-consciousness-and-moral-patienthood'>consciousness and moral patienthood</a> which is by far the most comprehensive and detailed article I know on the subject. From the article, we get three important pieces of information. First, we get a "Probability of consciousness of a sort I intuitively morally care about" that is given by the original author. Since they have spent more time on the subject and I find them broadly plausible I will just copy these probabilities. Secondly, we get information about the brain weight of different species and lastly they estimate the number of neurons that different species have in their brain.

To get the expected suffering exchange rate I multiply the probability that I find morally relevant with the relative difference in brain weight to get a first metric and the relative difference in neurons to get a second one. These metrics are imperfect for suffering for multiple reasons: a) brain weight would have unintuitive implications such as "women are, on average, less capable of suffering than men" and b) it is very unclear how the relationship between the metrics and capability to suffer is. Maybe it is linear, maybe it is exponential, maybe the ability to suffer requires a certain threshold or maybe it is a combination of the previous ideas. I could easily come up with reasons for and against all of these hypotheses and this merely shows that we have little to no idea, especially because it is hard or impossible to find evidence for or against them other than our intuitions. However, one of the intuitions that seem very strong is that the ability to suffer somehow scales with the complexity of your brain. We don't know exactly how it is linked but we would probably agree that a cow's ability to suffer is lower than that of a human but larger than a chicken. Since the brain weight and the number of neurons are the only available data points I used them as proxies. In the following table, you can find a summary of the just described facts and rates.

<figure>
  <img src="/img/Animal_Suffering/Moral_relevance_table.png"/>
</figure>

### What are the results?

In the following we will have a look at the results coming from the different metrics. First, we will have a short overview of the suffering over time.

<figure>
  <img src="/img/Animal_Suffering/animal_DALYs_over_time.png"/>
</figure>

This is basically just a reweighted version of the plots about the number of killed animals over time since I don't have any actual data on how conditions in factory farms changed over time. The more interesting interpretations come from the snapshots we have from the most recent data (2017/2018) which we will dive in now.

Let's first check out the disease burden on animals that are weighed by the weight of each species' brain.

<figure>
  <img src="/img/Animal_Suffering/snapshot_2017_2018_DALYs_adjusted.png"/>
</figure>

We can see that: a) Humans still have by far the highest expected value of DALYs per year, b) Pigs have larger expected DALYs than chickens. I find that interesting and would not have expected it just because humanity kills so many chickens every year, and c) The values for fish can't even be seen on this metric. Their brain is so small and light that the number of fish is strongly mitigated.

If we consider the number of neurons in the brain as a proxy, we get a slightly different picture.

<figure>
  <img src="/img/Animal_Suffering/snapshot_2017_2018_DALYs_adjusted_metric2.png"/>
</figure>

The main difference to the first metric (brain weight) is that the expected DALYs decreased for every species but chickens in relation to humans. Apparently, for some reason, the neurons per weight ratio are higher for chickens and humans than for other animals. Other than that we still have similar trends: Fish are still not at all visible on the scale and the expected value for humans is larger than the estimates for all animals combined.

While this might look like that we should prioritize humans over animals when it comes to reducing suffering we should keep in mind that we are working with very rough approximations. To emphasize the possible error that we are making I want to show the DALYs of the different species when we do neither adjust for brain weight nor for number of neurons in the brain to give an intuitive upper bound (I would find it very surprising if it turned out that e.g. chickens could suffer more than humans).

<figure>
  <img src="/img/Animal_Suffering/snapshot_2017_2018_DALYs_not_adjusted.png"/>
</figure>

As expected, the sheer number of chickens dominates all other species. To make comparisons easier we remove them from the equation.

<figure>
  <img src="/img/Animal_Suffering/snapshot_2017_2018_DALYs_not_adjusted_wo_chickens.png"/>
</figure>

We find that most species have a higher upper bound than the expected value of humans if we don't adjust for brain weight or number of neurons. My expected value is larger for pigs but lower for all other species. However, I think that the probability that the non-human animals in question have the same capacity for suffering is similar to humans is rather low. While I am not sure what exactly the ratio is, I think it exists and the point of this post was to give some rough estimates for it and look at its implications.

### Nerd section - Data preparation

Skip this if you don't care about the data preparation process.

The datasets used both come from <a href='https://ourworldindata.org/meat-production#all-charts-preview'>our world in data</a>. Some of the data regarding fish were given by <a href='http://www.fao.org/3/ca5224en/ca5224en.pdf'>this report</a> of the Food and Agricultural organization of the UN. The brain weight of different species was taken from the already mentioned <a href='https://www.openphilanthropy.org/2017-report-consciousness-and-moral-patienthood'>report on consciousness and moral patienthood</a> and gaps were filled where necessary. The number of neurons were taken from the respective <a href='https://en.wikipedia.org/wiki/List_of_animals_by_number_of_neurons'>Wikipedia page</a>. The full data processing can be found with comments in a jupyter notebook on my <a href='https://github.com/mariushobbhahn/approximate_world_suffering'>GitHub</a> page.

## Conclusions

1. **The difference in brain weight or number of neurons is larger than I expected.** I was especially surprised by how small the brain of chickens and especially fish is. While this is no conclusive evidence it still lead me to update my priorities. I would now prioritize chickens and pigs significantly more than fish. I was leaning in this direction before looking at the numbers but not as heavily.
2. **Animal suffering is definitely important.** While both metrics seem to imply that the expected human suffering is larger than that of any other species expected values and lower bounds of non-human animals still imply a lot of suffering that could be reduced. While I don't know the latest research on the comparative effectiveness of different interventions, the numbers seem to suggest focusing mostly on chickens and pigs. However, this impression might be wrong when the effectiveness of interventions regarding specific species is considered, e.g. there might be more political capital for closing a factory farm with cows than with chickens.
3. **There are no major ethical updates for me.** There are some small updates and priority shifts as explained in the previous points but my broader belief of 'animal suffering is non-negligible and should be one of the EA cause areas' still stays the same. That is because the numbers neither provide any strong evidence to drop all other causes nor to drop animal suffering as a cause and because the uncertainties within my modeling are just too high. There are just too many hard questions that I approximate with very rough intuitions or lose upper and lower bounds. Some sources of error are discussed deeper in the following section.
4. **Some interesting considerations:** I had an interesting discussion with a colleague about using the number of neurons as a metric where they asked me how I would decide when I had the chance to save either a human or an elephant (since elephants have more neurons in their brain). While their conclusion was that number of neurons is not a valuable proxy I think it is similarly likely that we massively underestimate the capacity to suffer from elephants. I think the human history of racism and speciesism has mostly shown that we have been insufficiently inclusive in the past and we should be a bit more cautious in the case of elephants. Currently, I, therefore, think that saving the elephant is the right thing with a probability of around 50 percent. Luckily, humans have not yet started to factory farm elephants and this question doesn't have major real-life consequences.

## What could be improved in my modeling

As emphasized multiple times already, the questions I try to find answers for are very hard questions with high uncertainty attached to them. Therefore, there are many ways in which my model could be improved but I am not sure how realistic some of these suggestions are

1. A more accurate image of the conditions in factory farms. More data and better calibrated expert opinion would definitely make this estimate more accurate (please contact me if you are e.g. working with an animal organization and have ideas for quantification).

2. What is the suffering exchange rate between different species? This seems to be the hardest yet most important question of the entire endeavor. If you have any ideas that are better than using brain weight or number of neurons as a proxy please contact me.

3. DALYs are still not a perfect representation of suffering. A longer discussion can be found in <a href='http://www.mariushobbhahn.com/2020-06-29-human_suffering/'>part I</a>. If you have a better metric that is also applicable to animals I would be very interested.

#### ***One last note***

If you have any feedback regarding anything (i.e. layout or opinions) please tell me in a constructive manner via your preferred means of communication.




