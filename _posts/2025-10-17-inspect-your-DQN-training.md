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
in order to discuss several key characteristics of good-quality training outcome that can help you adjust your RL.

We use a simple 2D grid world environment where the agent should move towards the target tile, and once it does,
it receives a +1 reward. Any other transition results in a 0 reward.

## Training reinforcement learning can be difficult

Even if you coded the RL algorithm correctly, getting it to train well on a specific environment can be a lot of work.
This mostly stems from a large number of hyper-parameters that we can tweak which can alter 
(1) the dynamics of the task being solved in this environment (2) the dynamics of the gradient descent.
Hence, it's useful to understand a couple of key measures that we can look at during training 
which can guide our hyper-parameter choice.

## Looking at rewards over time

The first indication that your policy is improving with training time is that as it's queried later in the training, 
it yields high rewards. To check this, you can implement an exploration probability decay with training time.
As the exploration probability, <span class="math display">$$ \varepsilon $$</span>, decreases with training time, 
your learned policy is queried more and more frequently, and random actions are taken less and less frequently. 
You may want to decay the exploration probability to zero with training time. As a result, at the end of training,
you should see high (or highest possible) rewards being achieved in the environment.

Below is the result that you'd like to see 
as <span class="math display">$$ \varepsilon \rightarrow 0 $$</span> with training time. With training time, the learned
policy starts to successfully move the agent towards the target (early) every time, resulting in +1 reward.

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/DQN-rewards-over-episodes-good.png" width="800">
</p>

If, on the other hand, average rewards stagnate at a low value even as your policy is queried more and more frequently,
it is an indication that something isn't setup right in your RL. 
My first go-to hyper-parameter to tweak would be the learning rate.

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/DQN-rewards-over-episodes-poor.png" width="800">
</p>

Of course, there's also the question: How much training is too much training? 
This is where training RL becomes a bit of an art! This small 6-by-4 grid world is a very simple task and I was expecting
the RL agent not needing too many trials to learn. 500 episodes with 20 steps in the environment per episode was
more than enough to learn the perfect policy. A more complicated task would require more training time.

## Looking at Q-values





## Looking at training loss


