---
layout:     post
title:      "Does the tax revenue from Cigarettes pay for the Cost of associated Diseases?"
subtitle:   "Or is this just an argument people use to rationalize their addiction?"
date:       2021-03-01 20:28:00
author:     "Marius Hobbhahn"
header-img: "img/header-imgs/cigarettes.jpeg"
category:   opinion
tags:	    [Effective Altruism, Data Analysis]
---

## **What is this post about?**

Whenever I ask people why they smoke I get an answer along the lines of "It sometimes helps with stress. I know I shouldn't do it. I'm trying to stop." But sometimes they then add something along the lines of "But it is actually good for the health care system as a whole because I will die younger and therefore cost the system less" or "The taxes generated through cigarettes are so high that they can easily pay for my lung cancer". Possible these thoughts were inspired by commedy videos such as <a href='https://www.youtube.com/watch?v=WJIMffhpZRw'>Yes Minister - on smoking</a>. I find both answers intuitively absurd but neither they nor I had looked at the data so no minds were changed through the conversation. 

Therefore, I want to do four simple things in this post. First, give a basic overview of the statistics behind smoking, e.g. demographics or magnitude of the global tobacco industry. Secondly, analyze the taxes vs. cost of diseases argument. Thirdly, investigate the question of whether people save the state money by dying younger. And lastly present miscellaneous considerations that are not directly related to the previous ones but are still important such as the costs of passive smoking or possible ways to reduce smoking. 

As always, if you disagree with my approach, with my analysis or with my conclusions, don't hesitate to contact me. If you like it and know other people who you expect to like it too, share it with them. 

TL;DR: 


## Some basic overview Statistics

Most of the overview statistics come from <a href='https://ourworldindata.org/smoking'>Our World in Data</a>. Fortunately they have already compiled a fantastic overview and I merely selected the parts that I found most important. If you want more charts go to Our world in Data. 

#### Prevalence of Smoking

The sale of cigarettes has probably peaked around 1980 in most developed countries. However, the historical data is not available for less developed countries so it's impossible to put their current number into historic perspective.

<figure>
  <img src="/img/Smoking/sales_cigarettes_1875_2015.png"/>
</figure>

Looking at the share of people who smoked everyday from 1980 to 2012 we find that there is a slightly decreasing trend for the entire world. 

<figure>
  <img src="/img/Smoking/sales_cigarettes_1875_2015.png"/>
</figure>

While this is a positive sign it doesn't necessarily imply that the overall number of cigarettes smoked is also decreasing. Theoretically, the number of occasional smokers could have risen. When comparing the proportion of adults who smoke from 2000 with that of 2016 we find that there is a decrease of smokers for the vast majority of countries in the world (above the diagonal means decrease). 

<figure>
  <img src="/img/Smoking/adults_smoke_2000_vs_2016.png"/>
</figure>

Even though the trend is decreasing it should not be forgotten that the absolute numbers are still pretty large. Overall, within all major regions of the world 15%-35% of their population smoke on a daily or non-daily basis. 

#### Influence of Region

Looking at the share of adults who smoke in 2016, I don't think a clear pattern can be established. One could argue that there is a larger number of smokers in Europe and parts of South East Asia but I would be careful not to overinterpret them. 

<figure>
  <img src="/img/Smoking/adults_smoke_2016.png"/>
</figure>

#### Influence of Gender

Nearly universally women smoke much less than men. It also seems like this effect is stronger for less developed countries. 

<figure>
  <img src="/img/Smoking/smoking_men_vs_women.png"/>
</figure>

#### How bad is Smoking?

Smoking is worse than I expected and I already expected it to be quite bad. Looking at the number of deaths by risk factors in 2017, smoking was in second place with 7.1 million deaths. 

<figure>
  <img src="/img/Smoking/death_by_risk_factor_2017.png"/>
</figure>

I will dive deeper into the different diseases that are associated with smoking later in the post, but just to highlight the magnitude of its effect in once example consider the share of cancer deaths attributed to tobacco in 2016.

<figure>
  <img src="/img/Smoking/share_of_cancer_deaths_tobacco.png"/>
</figure>

Given that there are so many different kinds of cancer, I find it remarkable that between 5% and 50% can be traced back to smoking depending on the country. While this sounds pretty bad it needs to be pointed out that the overall number of tobacco deaths is decreasing over time.

<figure>
  <img src="/img/Smoking/smoking_death_1990_vs_2017.png"/>
</figure>

#### The Tobacco Industry

TODO

## 1. Taxes vs. Costs of smoking-related Diseases

TODO: update all numbers for inflation until 2018. 

There are multiple ways in which states can tax cigarettes. For instance, you can tax the import of tobacco and the sale of cigarettes. But no matter at which stage of the production chain the state taxes cigarettes it will ultimately gain some revenue from the production and sales of cigarettes. This revenue is not at all negligible. According to this <a href='https://www.statista.com/statistics/248964/revenues-from-tobacco-tax-and-forecast-in-the-us/'>Statista report</a> the tobacco tax revenue for the USA was 17$ Billion in 2010 and 12 Billion in 2020. According to a <a href='https://www.who.int/data/gho/data/indicators/indicator-details/GHO/gho-tobacco-control-raise-taxes-rev-excise'>WHO report</a> Germany earned 14 Bllion Euros in taxes in 2018 and the UK earned 8.8 Billion British Pound. However, the WHO count combines specific taxes and ad valorem (e.g. Value-added) taxes whereas the Statista report only reported specific taxes. Thus the WHO report estimates the US tax income due to cigarettes on 30$ Billion in 2018. The same report states that India earned 183.3 Billion rupees in taxes from cigarettes which corresponds to 2.5 Billion US Dollars. While this is a lot of money it needs to be compared to the cost to the public health system in each country respectively. 

According to a <a href='https://www.cdc.gov/tobacco/data_statistics/fact_sheets/economics/econ_facts/index.htm'>report</a> by the Center for Disease Control (CDC) smoking-related Illnesses cost the USA 170$ Billion per year in direct cost. According to the <a href='https://pubmed.ncbi.nlm.nih.gov/25498551/'>original study</a> this translates to 8.7% of the entire annual health spending of the USA in 2010 with a 95% confidence interval between 6.8% (i.e. 133$ Billion) and 11.2% (i.e. 219$ Billion). Accounting for inflation these values become $153.2 billion, $195.9 billion and $252.3 billion in 2018 respectively. On top of the direct cost the report estimates that there are 156$ Billion in lost productivity due to premature inability to work in 2006 or 194.4 in 2018 accounting for inflation. The lost productivity is estimated directly through the present value of future earnings, e.g. taxes, but also from more indirect measurements such as foregone future imputed earnings from unpaid household work that is unrealized as a consequence of early mortality. The exact estimations for indirect costs vary between countries and studies but they broadly include these direct and indirect estimates. 

A further <a href='https://www.hhs.gov/sites/default/files/consequences-smoking-exec-summary.pdf'>report</a> by the surgeon general breaks down the diseases which have been linked to smoking. The diseases in red have been causally linked to smoking while the others have different degrees of correlations with smoking and are thus weighted accordingly in the estimation of costs. 

TODO: where should this section go?

<figure>
  <img src="/img/Smoking/smoking_health_consequences.png"/>
</figure>

Doing similar estimates for the other selected countries yields a direct cost of 16.6 Billion Euro for Germany (see <a href='https://pubmed.ncbi.nlm.nih.gov/11028648/'>study</a>). Importantly, this study uses data from 1996 whereas the tax income is from 2018. Thus, accounting for inflation, this estimate would be €26.6 billion in 2018. Furthermore, this is an underestimate since they only approximated the cost of the four most common illnesses and ignored the less common ones. They also didn't estimate the opportunity costs of lost productivity. A <a href='https://www.ncbi.nlm.nih.gov/pmc/articles/PMC2563685/'>different study</a> estimates that in the year 2003 Germany lost €8.8 billion due to work loss days and early retirement linked to smoking. After accounting for inflation this estimate would yield €12 billion in 2018. However, it is unclear whether this is an over or underestimate of the true costs as hospital costs have risen in general while the number of smokers has slightly decreased. 

A <a href='https://pubmed.ncbi.nlm.nih.gov/32805055/'>WHO study</a> from India concluded that they bear costs of INR 1773.4 billion (US $27.5 billion) per year with estimates from 2017. They split into 22% (i.e. $6 billion) direct and 78% (i.e. $21.5 billion) indirect cost. 

A <a href='https://www.gov.uk/government/publications/health-matters-stopping-smoking-what-works/health-matters-stopping-smoking-what-works'> report by the UK government states that smoking costs the UK approximately 12.6 billion British Pound, which consists of 2.5 billion in direct cost, 1.4 billion from social care and 8.6 billion due to lost productivity. Thus the UK are the only country that makes more money from taxation than it has costs from direct harms. I'm not an expert on the NHS but I would speculate that these lower costs compared to other countries come from the fact that the UK applies cost-benefit calculations much more strictly to health than other countries. If, for example, a treatment costs more than 30,000 pound per <a href='https://en.wikipedia.org/wiki/Quality-adjusted_life_year'>QALY</a> then it is very unlikely to be paid for by the NHS (see section 6.3 <a href='https://www.nice.org.uk/process/pmg9/chapter/the-appraisal-of-the-evidence-and-structured-decision-making'>here</a>).

TODO: summary plot

Looking at the summary plot above, I would argue that the argument is not very convincing in most contexts. In the US, Germany and India already the direct health costs from smoking outweigh the entire tax revenue gained from it. In the UK, I would be more open to the argument of "smoking for your country" but it still seems rather inefficient. The Queen would probably prefer if you just kept working until you died instead of dying early from smoking or became a skydiver at 65 ;) 

## 2. Dying Younger to save the State Costs

As far as I understand the argument correctly the argument goes: "Old people cost the health care system much more than younger people. Additionally, the state pays pensions after a certain age is reached. Both costs would be reduced if people died exactly after they stop working." 

Before looking at the data, I would expect the argument not to hold true. The cost for the healthcare system mainly increases around 2 years before a person dies. Since the smokers just die earlier this cost is probably not reduced just shifted. I would even expect the opposite to hold true, i.e. that smokers cost the health system much more in their last 2 years than non-smokers. While it is true that pensions are costs for the state I would assume that most people are unable to "time their smoking death correctly" and die quickly at age 65 of spontaneous lung cancer. So usually it will be a long process that often means they are unable to work before their pension age. Thus they are not only a burden for the system but additionally create opportunity due to their lost productivity. The direct cost for the healthcare system and the indirect cost for society are already estimated in the previous section. Thus in this section I will only focus on the money saved by the state from pensions.

The <a href='https://iea.org.uk/'>Institute of Economic Affairs (IEA)</a>, a liberal economic thinktank in the UK estimated exactly this number in a <a href='https://iea.org.uk/wp-content/uploads/2017/08/Smoking-and-the-Public-Purse.pdf'>report</a> in 2017. They compute the amount of money saved due to premature deaths from smoking-related illness in great detail. Their calculation includes the deathrates per age-bracket multiplied with the cost of saved pensions and control for many different factors, such as the loss of productivity when people die before their pension or the amount of pensions people would get conditional on their job. They estimate that the UK saves 9.8 billion British Pound annually due to premature deaths related to smoking. While this estimate might be influenced by their ideological affiliation, I think their methodology for estimating the amount saved in pensions is sound. However, their numbers on lost productivity are very conservative estimates and thus much lower than the 8.6 billion estimated by the British Government. For example, they only compare the direct income due to taxes with the cost of education and health care but don't include the indirect savings through unpaid labor such as raising children or taxes paid by the employer of that individual. 

Since the IEA report computes savings from pensions and taxation in the same number instead of seperated from each other, I will do a seperate analysis. I originally wanted to repeat a similar strategy as the IEA report, i.e. combine age-specific population estimates with age-specific death rates from smoking and then compute the resulting saved pensions. However, I encountered two problems. Firstly, the openly available data on age-specific death rates from smoking are insufficiently fine-grained to get an estimate that doesn't have huge uncertainty attached to it. Secondly, I found it very hard to include counterfactual death times in my calculation. I could, for example, imagine that someone who dies very early due to smoking related illness would not have reached the average life expectancy of their country because they have other conditions that potentially interact with each other such as alcoholism or obesity. Since there is no data publically available on the conditional life expectancy for these groups (even though they seem to exist somewhere as the <a href='https://www.ncbi.nlm.nih.gov/books/NBK179276/pdf/Bookshelf_NBK179276.pdf'>US Surgeon General report</a> claims to include them in their estimate), I think my model would have been fancy but probably pretty wrong. 

Thus I decided to use a simpler, more back-of-the-envelope style, calculation. There are multiple sources that claim that smoking reduces your life expectancy by about ten years (see e.g. <a href='https://www.cdc.gov/tobacco/data_statistics/fact_sheets/health_effects/tobacco_related_mortality/index.htm'>here</a> or <a href='https://www.blueprintincome.com/tools/life-expectancy-calculator-how-long-will-i-live/info/smoking'>here</a>). They control for factors such as income, socio-cultural background, nutrition, etc. such that my concerns about the counterfactials are at least reduced. An estimate of the number of smoking-related deaths per year is publicly available for all four countries in question and average pension numbers are public or can be roughly estimated. This strategy has some pathologies as it ignores the age-distribution of people dying 

For the USA it is estimated that 480000 people die per year due to smoking-related illness (TODO: cite), for Germany this number is TODO (TODO:cite), for India it is 10 Million (TODO:cite), and for the UK TODO (TODO:cite). 

Estimating the pensions per country is slightly more complicated as most pension schemes are complex and depend on a lot of different factors such as whether you worked for the state or private industry, whether you have children, whether you are married, etc. 



TODO: additional layer of saved health care costs or discuss why not. 

TODO: discussion, still ineffective way to get rid of old people. There have to be better ways. 

## 3. Other considerations

While the purpose of my post was to primarily answer the two questions above, I stumbled over some other interesting considerations along the way. 

### Jobs

There are some people who claim that the jobs within the tobacco industry, e.g. in production, advertisement and distribution, should not be forgotten in my calculations. I personally don't like this argument for two reasons. Firstly, I think that people usually find other jobs if their company goes bankrupt and especially in an industry like cigarettes there are few jobs that require a very unique skillset that wouldn't be applicable to other jobs. Secondly, and more importantly, I don't think jobs should be an argument for an industry that is net negative to society. If there was an industry whose workers would run around murdering people, nobody would argue that the industry should exist because of the jobs it provides. Cigarettes aren't as direct - the death is much later and the link is more probabilistic and thus less salient - but the underlying argument still holds true in my opinion. If an industry is net negative for society and it is rather directly responsible for a lot of deaths and suffering, the state should probably try to reduce its influence as much as possible. Especially when the people who are affected aren't always the ones who chose to smoke in the first place. This is what I will discuss further in the next two sections. 

### Indirect Harms - passive smoking



### Moral Considerations

Opportunity costs in hospitals & Children

### Which Legistlation works?

The rest of the article might sound like I would be in favor of banning cigarettes entirely. But that's not necessarily the case. I support all measures that reduce the number of cigarettes smoked in an effective manner and making them illegal might not be the most effective route to achieve that since people might switch to the black market. 

## Conclusions

If you are a smoker and feel attacked by this article, I'm sorry. While I can understand how people started smoking, I don't think there is a good justification for it. There are better ways for stress aleviation with less risk and there are better ways to belong to a peer group. If you already agree that smoking is bad for you, there are ways to stop and you can get help at TODO:links. Remember that it's never too late to try to stop smoking and your future self will only thank you for it. 




#### ***One last note***

If you want to get informed about new posts you can <a href='http://www.mariushobbhahn.com/subscribe/'>subscribe to my mailing list</a> or <a href='https://twitter.com/MariusHobbhahn'>follow me on Twitter</a>.

If you want to support me financially, you can send me a donation via my <a href='https://www.paypal.me/mariushobbhahn'>PayPal</a>. 

If you have any feedback regarding anything (i.e. layout or opinions) please tell me in a constructive manner via your preferred means of communication.

%%%overview & misc:
https://www.who.int/news/item/19-12-2019-who-launches-new-report-on-global-tobacco-use-trends

%%%links for tax:
https://www.destatis.de/EN/Press/2020/01/PE20_016_799.html
https://chronicdata.cdc.gov/Policy/Table-of-Gross-Cigarette-Tax-Revenue-Per-State-Orz/rkpp-igza
https://www.taxpolicycenter.org/statistics/tobacco-tax-revenue
https://www.who.int/tobacco/publications/en_tfi_tob_tax_chapter4.pdf
https://www.statista.com/statistics/248964/revenues-from-tobacco-tax-and-forecast-in-the-us/
https://tobaccoatlas.org/topic/taxes/
https://www.google.com/search?channel=fs&client=ubuntu&q=cigarette+tax+revenue <- see table-8 of who report
https://www.who.int/data/gho/data/indicators/indicator-details/GHO/gho-tobacco-control-raise-taxes-rev-excise

https://ourworldindata.org/grapher/death-rates-smoking-age?country=~USA <--- Age distribution of smoker deaths

https://ourworldindata.org/smoking

%%%link for cost
https://iea.org.uk/wp-content/uploads/2017/08/Smoking-and-the-Public-Purse.pdf
https://www.ncbi.nlm.nih.gov/pmc/articles/PMC2563564/
https://www.cancer.org/latest-news/diseases-linked-to-smoking-cost-the-world-422-billion-in-health-related-expenses.html
https://www.cdc.gov/tobacco/data_statistics/fact_sheets/economics/econ_facts/index.htm
https://tobaccocontrol.bmj.com/content/27/1/58
https://www.swedish.org/classes-and-resources/smoking-cessation/financial-physical-and-social-costs-of-smoking
https://www.erswhitebook.org/chapters/tobacco-smoking/societal-costs-of-smoking/
https://www.cdc.gov/tobacco/data_statistics/fact_sheets/fast_facts/index.htm

https://jamanetwork.com/journals/jamanetworkopen/fullarticle/2769102  <---- health care spending in some rich countries
