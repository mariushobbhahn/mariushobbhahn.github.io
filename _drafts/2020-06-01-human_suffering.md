---
layout:     post
title:      "How much human suffering is there?"
subtitle:   "A back-of-the-envelope attempt to quantify human suffering"
date:       2020-06-29 20:28:00
author:     "Marius Hobbhahn"
header-img: "img/header-imgs/sisyphus.jpeg"
category:   opinion
---

## **What is this post about?**

As an Effective Altruist with a quantitative mindset, it is plausible that you want to ask questions about the suffering in the world. A very fundamental question that I have asked myself for a long time and could now finally bring myself to crunch the numbers to answer is "How much suffering exists?". Especially when it comes to cause prioritization it would be important to have some approximations, for example, to compare the suffering of animals to that of humans. In this post, I will try to give a rough sketch of the absolute and relative amounts of suffering of humans that exists and existed in the last 30 years. In future articles, I hope to do the same for animals.

The hard work has not been done by me. The data come from <a href='https://ourworldindata.org/'>our world in data</a> and <a href='https://www.prb.org/'>prb.org</a> who themselves have aggregated many many sources - I merely crunched some numbers, plotted and interpreted them.

## QALYs and burden of disease

<a href='https://en.wikipedia.org/wiki/Disease_burden'>Burden of disease</a> quantifies the impact of a health problem by financial cost, mortality, morbidity or other indicators. It is often quantified in terms of <a href='https://en.wikipedia.org/wiki/Quality-adjusted_life_year'>quality-adjusted life years (QALYs)</a> or <a href='https://en.wikipedia.org/wiki/Disability-adjusted_life_year>disability-adjusted life years (DALYs)</a>. Both metrics approximate the number of years lost due to disability (YLDs), sometimes also known as years lost due to disease or years lived with disability/disease.

DALYs are calculated using two components - <a href='https://en.wikipedia.org/wiki/Years_of_potential_life_lost'> years of potential life lost (YLL), i.e. how early did you die compared to your life expectancy, and years of life lost due to disability (YLD), i.e. the number of years of good health that were taken away from you by the disease. The formula is a simple non-weighted sum: DALY = YLL + YLD. The following figure from Wikipedia should make the concept more clear

<figure>
  <img src="/img/Human_suffering/750px-DALY_disability_affected_life_year_infographic.png"/>
</figure>

In my approximations I use DALYs and not QALYs because the data was only available for DALYs and I think the metric is more common when it comes to quantifying public health than QALYs because QALYs operate on a more individual level.

The Wikipedia articles for <a href='https://en.wikipedia.org/wiki/Quality-adjusted_life_year'>QALYs</a>, <a href='https://en.wikipedia.org/wiki/Disability-adjusted_life_year>DALYs</a> and <a href='https://en.wikipedia.org/wiki/Disease_burden'>disease burden</a> are really informative and easy to understand. I would recommend to check them out.

## Shut up and calculate

The <a href='https://ourworldindata.org/burden-of-disease#all-charts-preview'>our world in data on disease burden</a> provides 'DALYs per 100K people' as a measurement for every years since 1990 and nearly every country in the world. We will therefore first have a look at the relative measures and then multiply these with the respective population of the country to account for the global population growth since 1990. There are lots of other interesting facts about disease burden in QALYs that I will not discuss in this post such as an analysis of disease burden by age or cause over time. I would highly recommend to check out ourworldindata.org and have a look at their charts - they are amazing and every data nerd's wet dream.

### Relative suffering - QALYs per 100K people

Let's first look at the seven countries that have the lowest average QALYs over the years from 1990 to 2017.

<figure>
  <img src="/img/Human_suffering/relative_suffering_good_countries.png"/>
</figure>

I found the results a bit surprising. Iceland, Sweden and Switzerland were the ones I expected most. I would have also expected Norway, New Zealand and Canada to be there (they are in the top 20). I was a bit surprised by Japan and Singapores very good results. Further analysis shows that other East Asian countries such as South Korea and Taiwan also perform very well. My hypothesis is that these countries have generally well run health care systems, healthier diets and a more caring mentality towards their elderly than western countries do and therefore have smaller disease burdens. The countries that surprised me the most were Spain and Andorra. I would have, for example, predicted Germany to be above Spain. Further analysis shows that a lot of the mediterranean Countries (Italy, Greece, Cyprus, Malta) have very low disease burdens. My current hypothesis is that the mediterranean diet is very healthy and is less prone to lead to cardiovascular diseases who are by far the largest contributer to disease burden in developed countries. I want to emphasize that I am no health expert and my explanations for East Asia and the mediterranean countries are of very speculative nature.

To compare this, let's have a look at the countries with the highest average relative suffering over the years from 1990 to 2007. Once with Rwanda

<figure>
  <img src="/img/Human_suffering/relative_suffering_bad_countries_w_rwanda.png"/>
</figure>

and once without Rwanda.<

<figure>
  <img src="/img/Human_suffering/relative_suffering_bad_countries_wo_rwanda.png"/>
</figure>

Let's first discuss the elephant in the room - Rwuanda 1994. I knew the genocide was really really bad, I had read the wikipedia article, seen documentaries and knew of the killings, the rapes and torture. But holy shit did I underestimate the suffering that must have been inflicted in the 1994 Rwandan genocide. 700,000 QALYs per 100,000 people means that in just one year, on average, every single person in Rwanda was robbed of 7 years of life. Looking at all of these trends find that all seven countries are located in sub-sahara Africa and that their trajectory is no linear. In fact, all of them seem to have a period of increasing relative disease burden before it decreases again. In all cases this is a longer multi-year span and can therefore not really be attributed to specific coups, civil wars or political events. Even after informing myself on all countries that display this trend I still can't find a coherent, unifying hypothesis for this behaviour. I would be interested in more expert opinions (please contact me if you have one). Lastly, I want to compare the scope between the countries with highest to the ones with the lowest disease burden. The disease burden per 100K for the Central African Republic was around 100,000 while for Singapore it was around 16,000. If we use disease burden as an approximation for suffering, amount of suffering for an average Singaporian would be around 6 times lower than that of the average citizen of the African Central Republic.

Not only the high and low end of the spectrum are interesting and I therefore want to have a last look at a selected group of countries. These are some of the worlds largest and most influential countries.

<figure>
  <img src="/img/Human_suffering/relative_suffering_selected_countries.png"/>
</figure>

We can see that the general trend is a nearly linear decrease in QALYs per 100K per year. This is a good sign, especially since the two most populated countries in the world, China and India, have a steep downward trend. Russia, on the other hand, does not show the same decrease. After the break down of the UdSSR, Russia seemed to have a significant increase in average suffering. Another small but potentially significant detail is the trajectory of the USA. It decreases lower than other developed nations and also shows a slight upward trend in the last couple of years. I guess the effects of systematic wealth inequality, a broken democracy and a terrible health care system slowly catch up at some point.

### Absolute suffering - QALYs aggregate

The relative suffering is interesting but we can look at suffering from a different angle as well. Instead of only looking at the disease burden per 100K we can also account for the increase in population over the last thirty years. The decrease in average relative suffering in the world could, for example, be negated by the increase in the number of people and therefore the aggregate disease burden could have stayed constant.

The sum of QALYs per year for selected countries can be found in the following figure.

<figure>
  <img src="/img/Human_suffering/absolute_suffering_selected_countries.png"/>
</figure>

This seems to indicate that China was able to improve the quality of life faster than their population growth since the aggregate is decreasing. Indias population grew as fast as the quality of life per individual improved. Removing China and India to get a better picture of the other countries we get:

<figure>
  <img src="/img/Human_suffering/absolute_suffering_selected_countries_wo_CN_IN.png"/>
</figure>

We see that Germany, Japan, the UK, and Brazil follow a somewhat similar trend. Their overall disease burden decreases slightly. As we have seen before their relative disease burden decreases more drastically, implying that they are able to keep up with their low to medium population growth. The USA, in contrast, is one of the few developed nations, that has an increased absolute disease burden over this time period. Even in the times in which their relative disease burden decreased the population grew faster than the living standards improved. Russia has had nearly no change in the size of its population and therefore the absolute disease burden shows the same trajectory as its relative estimate.

Lastly, I want to present a holistic comparison of the relative and absolute global disease burden. The relative disease burden is weighted by the countries population.

<figure>
  <img src="/img/Human_suffering/abs_vs_rel_suffering_world.png"/>
</figure>

The positive news is that the relative disease burden seems to decline steadily. The alleviation of poverty and the eradication of diseases seem to work well on average. The absolute disease burden has increased from 1990 to 2000 but has since then decreased even further. This seems to indicate that the progress humanity has made on improving living standards is faster than the growth rate of the global human population. One event that stands out in both metrics is the Rwandan genocide from 1994 which, again, I really did not expect. A country that had around 7.2 Mio inhabitants before the genocide and 5.8 Mio after it has had a significant impact on the global disease burden of 5.7 Billion people.

### Nerd section - Data preparation

Skip this section if you don't care about the data preparation process.

I used three datasets in total. The burden of disease dataset (see <a href=https://ourworldindata.org/burden-of-disease#all-charts-preview'>here</a>) to get the DALYs per 100k people numbers, the <a href='https://ourworldindata.org/grapher/population-by-country'>population by country</a> dataset from our world in data (which includes data from 1500-2000) and a population by country <a href='https://www.prb.org/international/indicator/population/snapshot/'>snapshot</a> by prb for the year 2019. Since the burden of disease dataset only includes the years from 1990 to 2017 I removed all data prior to 1990 from the population by country dataset which then included data points for 1990 and 2000. All three datasets included some countries that are not in the other two so I removed all countries that are not in the burden of disease dataset and used estimates to fill gaps in the 1990 and 2000 data points for missing countries. This means that there are some countries for which I don't have any data points but most of them are very small like Saint Kitts and Nevis and Micronesia and therefore should not be a large source of error.
To get the population estimates for the years from 1991 to 1999 and 2001 to 2018 I used a linear interpolation. I then cut the years 2018 and 2019 from the population data and merged it with the burden of disease dataset. This linear interpolation is definitely inaccurate but it is a sufficient approximation to start with.

## Conclusions

Some conclusions I reached during the entire process of researching and writing this post.
1. **The world seems to get better:** especially the relative burden of disease steadily decreased from 0.46 DALYs per Person to 0.32 as a global average.
2. **New unanswered questions:** Some of the trends I don't understand. Why does the absolute disease burden increase until around 2000 and then turn back down? What explains the trend in relative suffering for Sub-Saharan countries discussed in the "relative suffering" section? Why is the burden for east Asian countries and Mediterranean countries so low compared to their wealth? If you have some hypothesis please share them with me.
3. **Rwanda 1994:** I knew it was crazy and I still underestimated the suffering by a factor of 2 or 3. No other event of the last 30 years is that visible in the DALY measurement. Not the financial crisis of 2008, not the earthquakes in Haiti or Nepal or the massive tsunami in 2004 that flooded large parts of Indonesia and Sri Lanka, and not even the wars and conflicts in the middle east. These catastrophes meant that entire countries had to be rebuild and yet the estimate of 181K DALYs per 100K people for Haiti in 2010 comes second by a large margin to the incomprehensible 724K DALYs per 100K people for Rwanda in 1994. Just WTF.

## Why should we care?

While this was an interesting and partly disturbing mental exercise for me, I think that it also yields some benefits.
1. We can compare the absolute and relative human suffering in world over time. This means we can test whether the world is becoming a better place on average and at which rate as I have just done. It should be seen as foundational work that can be used as a baseline measure for humanity’s progress.
2. We can compare the absolute and relative human suffering to the suffering of other species. I would for example be interested in how much suffering is inflicted on animals due to factory farming or wild animal suffering. I will, therefore, extend this question to animals in a future blog post (will be linked when ready).

## What could be improved in my modeling

My approximations make a couple of crucial assumptions, all of which could be improved with more effort and research.
1. DALYs are an accurate measure of human suffering. Especially because it measures years of life lost which, strictly speaking, should not contribute to suffering since the person is dead. However, you could also argue that some of the suffering comes from losses in human capital due to lost workers and family members. Even though it's an imperfect approximation, DALYs are the most accurate measure we currently have data of.
2. All suffering is already captured by current measurements. This is a big problem, especially for mental health issues in the developing world. While more developed nations slowly realized that mental health is important and that depression is something that often requires therapy or medication, large parts of the developing world still lag behind. Depression is often frowned upon and seen as a sign of weakness and the mentally ill are often ostracize instead of helped. This means that the data we have about mental health is probably very inaccurate but I would estimate that they play a large role in the net suffering of humanity. Overall this leads me to believe that I drastically underestimate the actual amount of suffering.
3. "Small and daily suffering" such as having a bad day or lovesickness is not part of the DALY estimation and therefore not part of my model. I am not sure to which extent they would play a role but it is surely non-negligible if aggregated over the entire world.
4. For some reason, I could not find a publically available dataset for the population sizes per country that includes all years from 1990 to 2017. I, therefore, had to merge and linearly interpolate datasets from 1990, 2000, and 2019. This is clearly suboptimal and better modeling and data would give more accurate estimates.

I could not answer a lot of interesting questions that could be asked about global suffering such as "which causes have become more prominent over time?" or "Can we extrapolate from the last 30 years to the future in a meaningful way?". While I intend to model some of these questions in future blog posts you might be interested in trying to improve the model by using better data or incorporating more features or just ask other interesting questions. If you want to build on my work don't hesitate to pull the respective github repo (TODO:link) and contact me to coordinate the research.

#### ***One last note***

If you have any feedback regarding anything (e.g. layout, code or opinions) please tell me in a constructive manner via your preferred means of communication.

