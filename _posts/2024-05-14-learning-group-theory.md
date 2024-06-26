---
layout: default
title:  "My journey through learning group theory"
date:   2024-05-13 15:00:00 +0100
categories: jekyll update
---

<p>
   <a href="/kamilazdybal.github.io/#blog">
      < Go back
  </a>
</p>

# My journey through learning group theory

One of my postdoc study goals is to learn the basics of group theory (GT) to the point that I will:

1. Apply GT in my machine learning research.
2. Deliver a graduate lecture on GT.
3. Be able to fully understand [G-CNN lectures](https://www.youtube.com/playlist?list=PL8FnQMH2k7jzPrxqdYufoiYVHim8PyZWd) by Erik Bekkers.

This note is a record of my study that I put together mostly to hold myself accountable and monitor my progress, 
but also it might help someone else to follow the same study resources and get a sense of how much time it can take.

## Study resources

### 📕 Reading [*Visual group theory* by Nathan Carter](https://github.com/liwei766/visual-group-theory/blob/master/visual%20group%20theory.pdf)

My recommendations to someone reading this textbook:

- This textbook leaves out formalism, and it's helpful to have another resource to fill-in the gaps. I find certain sections lacking rigor and it makes understanding what "X" really is more difficult. It's good to have another rigorous math textbook on the side.
- You absolutely should do all the exercises at the end of each chapter! They are actually pretty quick to do and also fun to think about. Exercises are referred to later in the text, so it helps to have them done before moving forward.

### 🌀 Watching [Visual group theory](https://www.youtube.com/playlist?list=PLwV-9DG53NDxU337smpTwm6sef4x-SCLv)

## Week-by-week self-study

#### Week 1 (13 May - 19 May, 2024)

- 📕 I've read Chapter 1 & finished its exercises.
- 🌀 I've watched [this lecture](https://youtu.be/UwTQdOop-nU).
- 📕 I went back to exercises of Chapter 1 after some things became clearer to me:

> Chapter 1 did not make it clear that:
> (1) There seems to be an assumption that there always exists a "non-action" which is "do nothing". It seems to me that this should have been noted as part of rule 1.5!
> (2) If a sequence of actions lead to a state we have already visited with a generator, or with a different
> sequence of actions, then we do not count that action. In other words, we only count those actions that lead
> to unique states. A consequence of this is that there can be finite set of actions. I initially thought that the
> set of actions will always be infinite, because you can always add one more generator to a sequence.
 
- 📕 I've read Chapter 2 & I'm working on its exercises.
- 🌀 I've watched [this lecture](https://youtu.be/vzEObOzsSKY).

#### Week 2 (20 May - 26 May, 2024)

- 📕 I've finished exercises in Chapter 2.
- 📕 I'm reading Chapter 3...
- I started thinking if GT can be useful for representation learning and I'm reading [this publication](https://proceedings.mlr.press/v206/marchetti23b.html).

#### Week 3 (27 May - 02 June, 2024)

- 📕 I've finished reading Chapter 3 & I'm working on its exercises.
- I've watched [this video by 3Blue1Brown](https://www.youtube.com/watch?v=mH0oCDa74tE). This video indeed mentions that "do-nothing" is always an admissible action!

> At this point, I'm still unsure what the textbook means by an object "occupying the same space" after group action.
> I initially thought that it means that actions that distort the inherent shape of an object are not allowed (e.g., folding the corner of the rectangle puzzle).
> But after reading Chapter 3, I think it's actually even more restrictive: the object literally has to occupy the same space if we were to attach an inherent coordinates to the initial object.
> So, for example, 90 degree rotation of a rectangle puzzle is not allowed. I'm curious what the formalism of this constraint looks like!
> I wonder if group theory introduces a notion of a coordinate system to define the space initially occupied by an object!
> Let's keep reading and we'll see :-)


