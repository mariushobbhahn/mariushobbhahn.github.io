---
layout:     post
title:      "A reproducibility ML journal"
date:       2020-03-22 18:28:00
author:     "Marius Hobbhahn"
header-img: "img/header-imgs/reproducible4.png"
category:   opinion
---

## What is the purpose of this post

In this post TODO:link I have argued that there are structural reasons why some published architectures or ideas within ML are not reproducible. I also outlined and estimated some of the harms that come with this problem. There are, of course, different strategies to solve it. <a href='https://www.wired.com/story/artificial-intelligence-confronts-reproducibility-crisis/'>This article</a> further describes the problem and argues that conferences such as NeurIPS should have a mandatory reproducibility checklist. Determined.ai give a good <a href='https://determined.ai/blog/reproducibility-in-ml/'>overview post</a> to keep yourself in check as a researcher and therefore provide reproducible code. However, while these are valid and important efforts, they are not sufficient to target the true problem of misaligned incentives within current academia. While changing this problem, if at all achievable, will take a long time, I suggest a simpler solution. Instead of changing incentives to stop the bad behaviour we should reward people who point out problems or become victims of unreproducible claims by bad luck. Therefore I want to outline a journal that only focuses on reproducibility. 

## What is a reproducible ML journal?

The idea is pretty simple: an online journal where people can submit work that is a reproduction of already published papers. The journal would likely be somewhat of a merger between <a href='https://osf.io/ezcuj/wiki/home/'>The reproducibility project</a> in Psychology and <a href='https://distill.pub/'>distill.pub</a>. To give you an idea of what this could look like consider the following
1. A submission to this journal can be one of the following: a) A first clean provision of the code for the paper. This is only legitimate when the original paper was released without code. b) Code for the paper using a different framework or programming language, i.e. Pytorch, Tensorflow, Keras or C++. c) A meaningful extension of the original paper, e.g. results for new datasets, additional experiments (e.g. using different accents in speech recognition), etc. The bar for publication would likely be lower than on a top tier conference but so is the effort. 
2. If a paper is not reproducible on the original dataset or fails to generalise to other datasets an author can publish their code and a description of their setup and thereby "flag" the paper as not reproducible. This option should only be used when you are very sure that you have exhausted a reasonable range of failure options. Since this is a critique of their work, the original authors will likely spent some time looking at the challenging code. If there are too many cases of people uploading buggy code and hoping someone will help them fix it this would ruin the journal. Whether this reasonable range of failure options was sufficiently exhausted has to be determined through peer review. 
3. For every ML paper that exists and was attempted to be reproduced there exists an entry on the website. This entry contains a link to the original paper and original code (if it exists), a link to all other implementations of this code and all extensions. If an architecture or method becomes so important that it is implemented in the ML libraries such as Pytorch, Tensorflow or scikit-learn the method will just be branded as "working" and links to the libraries will be provided. 
4. Importantly, the journal is not a dump for projects that failed. There should be a reviewing process that checks whether the code is clean and commented, whether it runs with the hardware requirements that are given in the description and if the report is understandable and complete. 

## What are the benefits of this journal?

1. **Open access** The journal would be non-profit and open access. Everyone can use it any time.
2. **Gives credit to valuable work** Reproducing another paper or method is valuable work but does not get a lot of credit currently. If it works, the method is more likely to be actually useful. Providing code in a different framework opens up this method to other parts of the community. Surely, I can currently already upload my code on github and hope that either someone searches for "'some paper' PyTorch implementation github", forks my repo and credits me with a comment in their code or a future employer looks at my Github repository. However, I think these are insufficient rewards for the effort put in and the uncertainty attached to them is too high. Having a publication in a real journal is more valuable for that individual.
3. **Institutionalises knowledge** By googling for a bit, reading 20 obscure forum posts and forking Github repos one can probably already get 90 percent of the things that this journal would do. Having all relevant information and links in one place would clearly be more efficient and save countless hours. Additionally, not all of this knowledge can even be found online. Some of it might be shared orally in larger labs or big companies and never even make it on the internet. Therefore having one institution to collect it all would increase access for less privileged parts of the community. 

## What now?

I currently transition from my Master's to a PhD programm and therefore do neither have the time, the resources nor the social status to stem such a project by myself. If you think that this is a good idea and can provide either time, resources or social standing you can just contact me via your prefered means of communication. 

#### ***One last note***

If you have any feedback regarding anything (i.e. layout or opinions) please tell me in a constructive manner via your preferred means of communication.

