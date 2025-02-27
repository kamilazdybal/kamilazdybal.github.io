---
layout: default
title:  "Understanding the dynamics of the Markov decision process"
date:   2025-02-27 10:00:00 +0100
categories: jekyll update
---

<script type="text/javascript" async="" src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.4/MathJax.js?config=TeX-MML-AM_CHTML">
</script>

<p>
   <a href="/kamilazdybal.github.io/#blog">
      < Go back
  </a>
</p>

# Understanding the dynamics of the Markov decision process

In this post, I provide illustrative explanation of the transition probabilities involved in executing sequences
of state, action, reward tuples by a reinforcement learning agent.
These probabilities define the dynamics of the Markov decision process (MDP) and may seem intimidating at first
(they did to me!), but here I break them down and explain them visually!

We consider a simple 2D grid world environment, where the agent can execute one of the four actions:
go up, go down, go right, go left.

## From deterministic to stochastic environments

### Deterministic environments

In a deterministic reinforcement learning environment, 
executing an action <span class="math display">$$a \in \mathcal{A}$$</span>, results
in state transition from <span class="math display">$$s \rightarrow s'$$</span> with certainty, 
where <span class="math display">$$s \in \mathcal{S}$$</span>. That is, in a simple
2D grid world with four actions, executing the action "go up" is guaranteed
to result in state transition to the state directly above the current state. 
This is presented in the figure below:

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/mdp-deterministic.svg" width="600">
</p>

### Environments with stochastic state transitions

But reinforcement learning environments don't have to behave deterministically! The beauty of the MDP is that
we can implement stochastic environments. In other words, we can assign probabilities of transitioning to other
nearby states, even if the action selected was to "go up"! 
This can, for example, model malfunctioning of an electronic robot. The figure below presents an environment
with stochastic state transitions. The action "go up" will only be correctly executed with 90% probability.
But with 8% probability the next state, <span class="math display">$$s'$$</span>, will be either
the one to the right or to the left of the current state. With 2% probability, the next state will be the state below
the current state.

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/mdp-stochastic-transition.svg" width="600">
</p>

### Environments with stochastic state transitions and rewards

Even more so, reinforcement learning environments don't have to provide deterministic rewards for state transitions!
Suppose that we are transitioning to the state directly above the current state. A deterministic reward for
executing this transition could always provide <span class="math display">$$r = 1$$</span>. But in MDP, 
we want to model the possibility for the rewards system malfunctioning too! And hence, with 80% probability
we will receive the <span class="math display">$$r = 1$$</span> reward, but with 15% probability we will get
<span class="math display">$$r = 0$$</span> as the reward, and with 5% probability, our reward will be
<span class="math display">$$r = -1$$</span>.

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/mdp-stochastic-transition-and-reward.svg" width="600">
</p>

## Understanding the probabilities involved


