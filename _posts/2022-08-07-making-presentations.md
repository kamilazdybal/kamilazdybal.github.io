---
layout: default
title:  "Making effective presentations"
date:   2022-08-07 15:00:00 +0100
categories: jekyll update
---

<p>
   <a href="/kamilazdybal.github.io/#blog">
      < Go back
  </a>
</p>

# Making effective presentations

After a number of talks that I've given during my PhD, I often receive a feedback from the audience that they enjoyed and understood my talk. At the same time, I often struggle to pay attention to conference talks, even those given by senior academics. That altogether made me reflect on what is it that I'm doing that "works" and what doesn't work for me in some presentations that I hear. In this post, I share my workflow of preparing presentation slides, with hopes that our conferences and meetings can start changing for the better, one presentation at a time :) Much of the tips that I present here have been adopted from [this great talk](https://www.youtube.com/watch?v=meBXuTIPJQk).

While preparing your talk is a lot of work and practice, it can also be a lot of fun and can help you clarify your own thoughts about your research!

## Remove distractions

Before adding any results, graphs, etc., your slide should look plain white with nothing on it. There is no need to have decorations, institutional logos, etc. I often find that these act mostly as distractions in getting the message across. Start with a slide that looks like this:

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/slides-01.png" width="600">
</p>

## Reduce, or ideally remove, text

There rarely is any need in putting text on your slides. The audience can only pay attention to one thing at a time: either to listening what you're saying, or to reading the text on your slide. By putting text on your slide, you risk loosing the audience's attention. Prepare your speech well and you will not need much text.

The most lengthy text that I ever use on my slides is the slide "topic sentence", which I put at the top of the slide, left-aligned. While introducing the slide, I will often say that topic sentence, either exactly how it appears on the slide, or paraphrasing it. This creates a redundancy of information, to increase the chances that the audience will "get the message".

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/slides-02.png" width="600">
</p>

My last tip here is to create meaningful line breaks when presenting text. A line break like this:

> Projecting high-dimensional data onto lower dimensions
>
> can introduce non-uniqueness.

reads more naturally than:

> Projecting high-dimensional data onto lower
>
> dimensions can introduce non-uniqueness.

## Reduce, or ideally remove, equations

As with text, the same goes with equations. For every equation that you decide to put on your slide, ask yourself: what story do I plan to convey with this equation? Will I have time to explain the equation and all its terms? (And if not, there's no reason to include the equation.) Equations that pop up on the slide for 30 seconds and you never elaborate on are just distractions. Chances are that your audience, instead of listening to what you have to say, will think: why did they include that equation? what do they want me to see in that equation? will I miss something important if I don't understand this equation?

Sometimes, you might decide that adding an equation is worth it, and that's alright. But be sure to spend a reasonable amount of time elaborating on the equation during your talk. For example, if I decide to include an equation that describes our novel metric, instead of just throwing the equation at the audience like this:

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/slides-03.png" width="600">
</p>

(which I believe would be entirely incomprehensible at first sight), I might describe a step-by-step visual understanding of the metric, and link it with each term in that equation using three consecutive slides:

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/slides-03p1.png" width="600">
</p>

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/slides-03p2.png" width="600">
</p>

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/slides-03p3.png" width="600">
</p>

## Make your slides very visual...

Oftentimes, there's an inspiring and engaging story that you can tell even from one figure. In fact, slides should mostly support you in everything that you can't convey in speech (or that would at least take you a long time to convey in speech). Showing an interesting image or graph based on which you discuss research insights is the best way to utilize slides.

For example, a slide like this, which shows a possible pitfall of a dimensionality reduction technique, does not need any text. While I talk, I can describe in words how the technique left two data points "outside" of the locations where they belong and how that is the result of the objective function that the technique is using under the hood. This can give the audience an intuitive understanding of the technique. A figure like this supported my speech very effectively, so I didn't have to talk too much.

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/slides-04.png" width="600">
</p>

## ...but don't overdo it

Too much graphics popping at the audience all at once can be overwhelming. Chances are the audience will wonder: what should I be paying attention to? What are they trying to show me here?

My approach that I've found to work effectively is to make new graphics appear gradually as you talk. So, instead of showing this slide all at once:

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/slides-05.png" width="600">
</p>

I would show a series of slides that lead to the final figure, each time describing in words what is happening:

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/slides-06.png" width="900">
</p>

## Remove irrelevant information

I've observed that some academics tend to include detailed information on their slides, that they normally would in a scientific paper. Too much information that is not super helpful in understanding the main message is just another distraction. Such irrelevant information can for instance be specific settings with which you ran your simulation, or specific conditions with which you generated your dataset. My advice would be: if it's not absolutely crucial to understanding the message, or if you won't mention or elaborate on that piece of information, remove it.

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/slides-07.png" width="800">
</p>

## Make visual pointers or highlights

If you're presenting close to the projector screen, you might use your hands to point the relevant things on your slides. If you know you'll be presenting in a big room, it might be helpful to anticipate things you'd like to point out and draw visual pointers on your slides early on to direct the audience attention. These can be made in forms of arrows, dots, boxes... I also found that they work most effectively if they appear gradually on your slide and are in synch with what you're currently saying. This is also where I might break the text rule, and add some brief note close to an arrow to help make my point.

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/slides-08.png" width="600">
</p>

## Take-away message

Giving a talk, especially at a conference, is a great opportunity to spread the word about your research or a recently published paper. That does not necessarily mean that you need to include all the information that you would in a scientific paper. In fact, what the audience mostly wants to hear is a more accessible and intuitive overview of your work. If you grab their attention, they will look up and read your paper anyway!

At conferences, people are often stressed, jetlagged, tired from all the scientific conversations they've had with other researchers, grumpy because they didn't have their morning coffee yet, or in any combination of these :) If you can give people an entertaining talk that has as many shortcuts as possible to help them understand what you're talking about, I'm sure that you will succeed! Good luck with your next talk!
