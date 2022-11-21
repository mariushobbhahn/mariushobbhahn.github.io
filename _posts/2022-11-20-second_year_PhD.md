---
layout:     post
title:      "Reflections on my second year as a Ph.D."
subtitle:   "Scientist or papermaker?"
date:       2022-11-19 20:28:00
author:     "Marius Hobbhahn"
header-img: "img/header-imgs/PhD_second_year_small.png"
category:   opinion
tags:       [Miscellanious, Improve]
---

## **What is this post about?**

I started my Ph.D. a bit more than two years ago. I think it is helpful to reflect on how the journey is going every once in a while and share thoughts that might be helpful for other Ph.D. candidates or people thinking about starting a Ph.D. You can find my first post [here](https://www.mariushobbhahn.com/2021-08-22-PhD_1year/).

## quick overview

To reconnect Ph.D. students who started during the pandemic, we organized the [Ellis doctoral symposium 2021](https://ellis.eu/events/ellis-doctoral-symposium). I was the lead organizer and it required more work than I had anticipated (but it was a big success and has been repeated in 2022 in [Allicante](https://ellisalicante.org/eds2022/)). 

On the content side, I added some new content to my piece on [the Laplace Bridge for BNNs](https://www.mariushobbhahn.com/2022-05-29-LB_for_BNNs/) which then got published at UAI. I spent most of my time working on a big new paper that will hopefully be put on arxiv before 2023. And finally, I made some big changes in my paper on [Laplace Matching](https://www.mariushobbhahn.com/2021-11-10-LM_for_GLMs/) and resubmitted it. I think the reviewers made some really good suggestions and the new version of the paper is genuinely much better than the first one. 

Overall, I think I can be happy with what I have accomplished but it felt slow and unproductive. I’m currently taking a 6-month break from my Ph.D. from November 22 to April 23 to focus full-time on AI safety research because I’m worried about the problems of misaligned AI and feel like I’m in a good position to contribute something valuable. 

## Disclaimers

I have similar disclaimers as last year
1. *I started my Ph.D. right when Covid began*. Therefore, my experience might differ a lot from the usual Ph.D. experience. I have been to only one in-person conference and I didn't like the online versions. So I probably just know fewer people to collaborate with or learn from than other people would at my stage of the Ph.D. 
2. Some of the following bullet points are negative. *My struggles, however, are mostly with academia as a system and not with the people around me*. I like the people in my group and I'm still convinced that Philipp is a great supervisor. He really cares that we are doing well in our Ph.D. both content-wise and mentally (e.g. he sends out feedback forms every year) and he gives us the level of supervision we want to have (e.g. doesn't micromanage unless asked to and lets us explore as long as it's broadly reasonable). 

## I started suboptimally

I started my Ph.D. by extending my Master's thesis and turning it into a paper. Furthermore, Philipp had a very concrete idea in mind for the beginning of my Ph.D. and it fitted neatly with the Master's thesis so my second project was also predetermined. Thus, I started with two relatively structured projects that were both intended to result in a paper. Sounds good, right? It was good but I think it resulted in too little exploration. My third project was more along the lines of "I have an abstract idea, let's play around and see whether I can make it work" and I think I learned more this way. 

Obviously, you should do both exploration and exploitation during your Ph.D., but if I had to do it again, I would probably do more exploration earlier. Just pick some papers that I find interesting, reimplement their method and play around with them. Try to get an intuitive feeling for the method and understand it on a nuts and bolts level. I think I could also have approached my first two projects differently, taking more time to play around and think about the paper later. Obviously, different people have different needs wrt to exploration vs. exploitation. I don't struggle with structure and am eager to get stuff done, so for me, the exploitation part comes naturally and I should bias myself to explore more. For others, it might be exactly the opposite. 

By exploration, I don’t mean doing random things. You can and should do exploration in a structured way. The focus is just much more on understanding the method really deeply without thinking about any presentable result. 

## Scientist or papermaker?

I have an intense love-hate relationship with academia. I love science, the exploration, the truth-seeking and the feeling of improving the world step by step. I hate the politics of academia, parts of the review system and the expectation that you do everything "for science" while getting a bad salary (compared to market rates). I am deeply convinced that the vast majority of scientists I interact with have good intentions. I know that they want to improve the world. On the other hand, there is this nagging voice in my head constantly saying "The incentives of academia are unaligned with truth-seeking, how are we supposed to do science when we are rewarded for so many things that have nothing to do with it?". I find this dilemma emotionally taxing. 

I find the situation additionally hard because it's easy to rationalize both ways. In case your paper gets accepted, the system works because "it saw your genius", in case the paper gets rejected, the system is broken because "reviewers are closed-minded". You always have to select some information to put into the paper, so it's easy to say "I'm just guiding the reviewer's attention" rather than "I'm tricking the reviewer by not showing the negative results". You could also always argue "Everyone presents their results in the best light. It's fine when I'm doing it as well" or "I'll just do grey zone stuff until I'm in the position to change things". 

I'm not really sure how to resolve this struggle to be very honest. Since I'm not dead set on staying in academia, I intend to just write papers when I'm convinced that I have found something important and present them in a more honest light---you know, reporting the limitations, not ignoring the negative results, etc. For now, I'm presenting a more honest version of the paper in my blog posts. When I think something that I found is just a marginal improvement or only applicable in fringe scenarios, I'll say so on my blog even if it might not be feasible to state that in the paper itself. 

## Content is the best motivation

This will sound cheesy but it's still true. Chasing a publication or citations is a bad motivator in my experience. It might keep me motivated for a couple of months but at some point, I started to think "I just want this to be over with and get it done". I felt more motivated for my latest projects (compared to my first paper) because it felt more like "I found something that I want to share with the community". It's just much easier to work on feedback and iterate the paper because my primary goal is to make other people understand the method rather than adding another line to my CV. 

## How we compare methods is broken

How we (ML people) currently compare methods in our papers is broken. It is expected that you compare your new method to a range of other methods. Since most of them require costly fine-tuning and your chance of acceptance decreases if your method isn't better than the others, everyone is incentivized to compare their fine-tuned work with the non-tuned benchmarks. This is clearly bad because it pretends to compare but actually provides a false picture. 

I see multiple paths out of this problem. Either a) you explicitly ask people to fine-tune the baselines and trust them to do it, b) you stop punishing people for not beating the state of the art, or c) you decrease the importance of baselines and increase the importance of other evidence such as case studies, etc. I would argue that a good paper shouldn't solely consist of benchmark comparisons anyway and it would be good to remove the expectation of beating the state of the art in every paper so I'd go for a mix of these suggestions.

## Organising Academic events

I have organized events for the debate club and for Effective Altruism in the past. Some of them were large events with more than 100 attendants and they obviously required some effort. So I expected to be well-prepared for lead-organizing the 2021 Ellis doctoral symposium, a new event we created to get new PhDs together during covid. But I was very wrong! I easily spent hundreds of hours organizing and I was only one of ~10 Ph.D. organizers. And we even had help from more senior university and ELLIS staff. 

There are a ton of rules that make it harder to spend public money and it really feels like the system puts spokes in your wheel at every step. For every major spending point, you need to make a public bidding and find at least 3 competitors. For every cent you spend, you have to fill out a form and provide detailed reasoning. In theory, this system is in place to prevent fraud. In practice, people know how to circumvent and bend the rules to get the desired results anyway and thus it feels mostly like a waste of time. 

We, as the PhDs, would have been completely lost without the help of multiple admins who knew how to navigate the system. I feel bad for them since they have to spend so much time filling out forms and creating documents for small spending points even if they probably have better things to do with their time. But what can they do? Don’t hate the players, hate the game.

I guess that these rules are in place because there was rampant misuse in the past. But it still sucks that the 95% of people who just want to organize a good event have to pay the price for the 5% who abused the system. I think there are some ways to improve the system but it feels like a very sticky problem. 

## I changed my mind a bit about specialization

In [the previous post](https://www.mariushobbhahn.com/2021-08-22-PhD_1year/), I recommended broadly sticking to the same topic in your Ph.D. since benefits accumulate and you build more expertise. I still think this is true but I want to emphasize more that it is a trade-off. 

If you realize that your original research is not as useful as predicted, something else is much more important, someone else has already solved your problem or even if you are just bored with it, you should switch. In my personal case, I have come to the conclusion that AI alignment is very important and therefore took the 6-month break to explore it further. I’m not exactly sure what will happen afterward but I intend to work mostly on AI safety and alignment in the near future.

## Every paper is two papers in one

Broadly speaking, there are two types of readers for your paper. Firstly, there are people who just want to understand the big picture. They don't care about the exact setup of your experiments and just want to see some nice figures and high-level explanations. For them, speed of understanding is more important than accuracy. Secondly, there are people who really want to understand the paper and potentially reproduce it. They care a lot about the exact setup of your experiments and what every single symbol means. For them, accuracy is much more important than speed. 

It's easy to fall into the trap of writing a paper for either of these two groups while forgetting the other. Most of the time, since your reviewers care about the details, we tend to forget that most people will just skim the abstract, look at one or two figures and leave. If your paper can't be understood this way, you'll lose 80% of your audience without ever knowing. I think papers that manage this split well usually care about conceptual figures, put a lot of the details in the appendix and provide their code publicly. Thus, the reader is not forced to care about the details but could check them if they wanted to. 

## It's very tough to know how well you are doing

During school, Bachelor's and Master's you regularly get some feedback. You get grades, you see how well your friends are doing, etc. During the Ph.D., I found this much harder. The review process is very stochastic, so using it as feedback is very noisy. You could write lots of papers but they might all be bad or you could write “only one paper” but it is very good. This struggle seems to be very common among PhDs. 

I think the main takeaways for me are a) talk about your struggles and especially your solutions with other PhDs (most people struggle in some way even if it's not the exact same way as yours) and b) have high-level meetings with your supervisor from time to time, e.g. every half year. In this meeting, you should not talk about content at all but just about how you're doing, what went well/badly, and exchange constructive feedback. Supervisors usually want to see you do well, so the bottleneck is mostly them not knowing in which specific ways you struggle. Once they know, they usually have good feedback. Supervisors probably have the best overview of what you are doing and how it compares to the reference class, so their opinion should be very valuable to you.

## Who is responsible for feedback and when?

I have come across the following situation in multiple scenarios. "A student works on their paper and sends it to the supervisor for feedback. The supervisor looks at the paper, realizes that it feels unfinished from their perspective and sends it back with a constructive version of 'you can do better. Iterate a bit more’”. The student thinks they already did their best and it's the responsibility of the supervisor to help them out and the supervisor thinks it's the student's responsibility to provide them with a better first draft. Another situation I have witnessed (this time as the supervisor) was "A student sends me their draft and I send it back with detailed comments. They work in the comments, hand in the thesis, and I and my professor grade it. Their grade is not perfect and they are confused. They expected that my feedback was a list of all the possible things they needed to do to get the best grade rather than just the most important comments on their current version. 

I think the conclusion from this is mostly that there is a lot of miscommunication around feedback and responsibilities. Thus, the most important thing is to be clearer no matter if you are the student or supervisor. As the supervisor, it helps to clarify that the feedback should not be seen as a list of *all possible* feedback and as a student it helps tol clarify at what stage the paper is and which kind of feedback you want, e.g. by adding comments like "Is this section clear?" or “this is not yet polished but does the math make sense to you?”, in the text.

#### ***One last note***

If you want to get informed about new posts you can [follow me on Twitter](https://twitter.com/MariusHobbhahn).

If you have any feedback regarding anything (i.e. layout or opinions) please tell me in a constructive manner via your preferred means of communication.


