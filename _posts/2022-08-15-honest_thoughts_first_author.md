---
layout:     post
title:      "Honest thoughts of the first author"
subtitle:   "Brief summary of my takeaways from my little social experiment"
date:       2022-08-15 20:28:00
author:     "Marius Hobbhahn"
header-img: "img/header-imgs/honest_thoughts_first_author.jpeg"
category:   opinion, ML_project
tags:       [Miscellanious]
---

## What is this post about?

I recently presented a poster at UAI22, my first in-person conference. The paper was [Fast Predictive Uncertainty for Classification with Bayesian Deep Networks](https://www.mariushobbhahn.com/2022-05-29-LB_for_BNNs/). I think the paper presents a nice idea, it is easy to understand and the experiments are good--overall, it’s a technically solid paper. However, I feel like I was not sufficiently explicit about what the method can and cannot do. In short, I think the concept presented in the paper is only useful when your method needs to be very very fast. In most other circumstances, other approaches are probably just better. 

Therefore, on my poster, I added a section called “Honest thoughts of the first author” to make my thoughts more explicit. I was very curious how people at the conference and on Twitter would react. In this post, I want to briefly describe the outcome of my [little social experiment](https://twitter.com/MariusHobbhahn/status/1554856125513736194). 

<figure>
  <img src="/img/header-imgs/honest_thoughts_first_author.jpeg"/>
</figure>

**Reasoning:** When I ask other academics in person about the limitations of their papers, they are happy to chat about them. Usually, they are much more humble and honest about their approach than their paper suggests and they are happy to help me wherever they can. However, this kind of informal knowledge is often not made explicit in the paper. I have wasted weeks or months trying to reproduce a paper until I came to the conclusion that it probably just doesn’t work as well as presented in the paper. Therefore, I thought it makes sense to be proactive about all of the strengths and weaknesses of the paper so other academics can actually make an informed decision when they engage with it. 

## Reactions

Here are some of the reactions and my takeaways. 


### Most reactions were positive

All reactions that reached me were positive and encouraging. I guess there were also people who didn’t like it but none of them has communicated that with me yet. In case you are such a person feel free to [reach out anonymously](admonymous.co/mariushobbhahn), I’d be interested in counterarguments. 

I think my main takeaway is that people actually liked it and found it helpful. I intend to do something like this again. I guess for my current project the honest thoughts will be pretty positive because I actually think we have found something pretty exciting. 


### Some people thought I was reducing my chances in academia 

The reasoning was that I’m underselling my work and thus would have worse chances with prestigious supervisors. I think this could be true and my overall pool of possible future supervisors and collaborators might be smaller as a consequence. However, I think it’s still net beneficial for me. 

Firstly, I might have attracted some new attention from people who care more about truthfulness than impressiveness and who wouldn’t otherwise have known me. Secondly, while the pool might be smaller it serves as a good filter. Why would I want to work with someone who wants me to write fancy but untruthful papers when I could work with someone who wants me to write fancy AND truthful papers? 


### Some people wanted to compare their work with mine

Some people who also worked on Bayesian Neural Networks wanted to compare their work with mine. This section made it easier for them to judge whether this was a useful comparison or not. If their method is intended to be very fast, they should compare it. Otherwise, they shouldn’t. Luckily one can call my method with two lines of code, so there are no big downsides of just trying. 

My takeaway is that I might get fewer citations from people who would have otherwise used this paper as a benchmark. While this might be bad for my google scholar profile, it’s probably good for science if people use the correct comparisons. 


### Some people were trying to frame my paper more positively

Multiple people made comments along the lines “you don’t need to be so negative, your paper is actually good”. And they are partly correct. The paper is technically sound, it introduces some new ideas, it has some nice figures, etc. It’s just much more limited than it looks at first glance. I guess people equated the fact that I said the method was limited with the fact that the paper wasn’t good/helpful. I don’t think these things should be equivalent. For example, papers that provide negative results, e.g. that explain why something doesn’t work, are good/helpful while not providing improvements on previous results. 

Firstly, this convinced me further that most academics are much nicer and more empathetic in person than when you tell them to write five unpaid reviews on topics outside of their expertise. Secondly, I think these interactions showed that people still equate the quality of a paper with its improvement over the state of the art (at least in ML) rather than the information gain provided to the rest of the community. Obviously, this doesn’t mean all papers are good, just that I weigh truthfulness/accuracy/helpfulness higher than performance gains in many cases. 


## Final thoughts

There are many possible explanations for why people are more honest in person than in their papers and I don’t want to accuse other academics of misbehavior. One possible explanation is that people play two different games in academia (at least I observed these patterns in myself). The first game is the research game. During the research game, you find out new things about the world or develop a new approach. Your opponent is some uncertain fact of the world, e.g. because you haven’t understood something important yet, and other academics are your allies. While playing the research game, you are happy to talk very honestly and directly about your research. The second game is the publishing game. In the publishing game, you try to get the stamp of approval from other academics. Your opponent is an imaginary reviewer 2 who will misinterpret everything you say and be very narrow-minded. Because reviewer 2 acts as an adversary, you feel like you are justified to break the rules just a bit. You select only the experiments where the method worked or slightly overstate its impact because reviewer 2 “wouldn’t get it” otherwise. Also, it’s not that big of a deal--you just want to publish the goddamn paper and be able to focus on your other projects. The fact that someone else assumes you have played the research game all along and wastes their time trying to reproduce your results never reaches your attention because they assume it was their fault and thus you rarely ever notice the downsides of playing the publishing game. 

Of course, I’m exaggerating here but I still notice that I sometimes started playing the publishing game and it made me deeply uncomfortable. I guess I’ll just try to be unapologetically honest and direct in my future work and see what happens. 

#### One last note

If you want to get informed about new posts, you can [follow me on Twitter](https://twitter.com/MariusHobbhahn).
