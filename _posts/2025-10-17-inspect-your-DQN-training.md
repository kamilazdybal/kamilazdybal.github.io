---
layout: default
title:  "How to inspect your deep Q-learning?"
date:   2025-10-17 10:00:00 +0100
categories: jekyll update
---

<script type="text/javascript" async="" src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.4/MathJax.js?config=TeX-MML-AM_CHTML">
</script>

<p>
   <a href="/kamilazdybal.github.io/#blog">
      < Go back
  </a>
</p>

# How to inspect your deep Q-learning?

In this post, we'll code a simple instance of training a deep Q-learning reinforcement learning (RL) agent using 
[TF-Agents](https://www.tensorflow.org/agents)
in order to discuss several key characteristics of a poor-quality and good-quality training outcome.

## Training reinforcement learning can be difficult

Even if you coded the RL algorithm correctly, getting it to train well on a specific environment can be a lot of work.
That work mostly stems from a large number of hyper-parameters that we can tweak which can alter 
(1) the dynamics of the task (2) the dynamics of the gradient descent when solving that task.
Hence, it's useful to understand a couple of key measures that we can look at during training 
which can guide our hyper-parameter choice.

## Looking at rewards over time






## Looking at Q-values





## Looking at training loss


