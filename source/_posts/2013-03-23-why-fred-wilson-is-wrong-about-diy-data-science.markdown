---
layout: post
title: "Why Fred Wilson is wrong about \"DIY data science\""
date: 2013-03-23 00:47
comments: true
categories: ["Analytics"]
---

Fred Wilson, in a recent [blog post on "DIY data science"](http://www.avc.com/a_vc/2013/03/diy-data-science.html), said this:

> I think data science and machine learning (I know they are not the same thing) are going to be a very big part of tech innovation in the coming years. And I also know that putting powerful tools in the hands of "everyman" produces more innovation than can happen when the tools are limited to mathematicians and scientists.

This is one of those pithy expressions that sound great when rolling off the idea-train. Indeed, imagine the possibilities of insightful output that could be enabled by "democratising" data science and machine learning.

However, this is also an idea that just appears unworkable at best.

True "data science" is a process. It's not just about a pretty visualisation or a "ka-ching!" epiphanic insight. It requires:

1. Articulating the objective
2. Identifying the inputs
3. Organising the source data into the required form of input
4. Identifying the input transformation or process
5. Implementing the transformation/process
6. Identifying the required output (see Step 1)
7. Making sense of the output (see Step 1)

*(Note: an underlying assumption is that the source data is clean and readily available -- which is quite the joke for most data domains today)*

The current state of data analysis technology has come admirably far from 10 years back, thanks to phenomenal technological efforts like [D3.js](http://d3js.org/) and [the R ecosystem](http://www.r-bloggers.com/) (with an emphasis on [anything by Hadley Wickham](https://github.com/hadley)), and some other innovations in [analysis](http://continuum.io/wakari.html) and [visualisation](http://www.creativebloq.com/design-tools/data-visualisation-712402). However, one common factor in all of these tools is that they all only address *Step 5* in the above process.

Fred goes on to say:

> So what is the Tumblr or Blogger or Wordpress of data science? When will my son and his friends be able to take the NBA dataset and start running algorithms against it to produce better fantasy picks? When will my daugther *\[sic\]* and her friends be able to take the TV viewing dataset to decide what TV shows to go back and watch that they missed last year?

Well, there can be none. The blogging (or more specifically -- publishing on the Web) revolution solved a problem of cost. It used to be too expensive for talented amateurs or hobbyists to publish (physical costs) and reach a wide audience (distribution costs). The lack of an equivalent for data science just means that there aren't similar hurdles to overcome. Potential data scientists are NOT being held back by such artificial constraints. What **is** preventing the layperson right now from becoming data wizards is, quite simply, the lack of knowledge.

Defining a problem domain is not something that a tool can magically do. That skill comes with a healthy mix of rigorous education and experience.

The world of data science is quite exciting, and [tools](http://gigaom.com/2012/12/18/a-programmers-guide-to-big-data-12-tools-to-know/), [techniques](http://conductrics.com/data-science-resources/) and [education](http://schoolofdata.org/handbook/courses/) will only continue to improve and wow us, but "DIY data science" will never be a thing. At least in the way Fred Wilson envisions it.
