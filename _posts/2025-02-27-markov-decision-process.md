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

In this post, I provide an illustrative explanation of the transition probabilities involved in executing sequences
of (state, action, reward, next state) tuples by a reinforcement learning agent.
These probabilities define the dynamics of the Markov decision process (MDP) and may seem intimidating at first
(they did to me!), but here I break them down and explain them visually. This note accompanies the first section
in Chapter 3 of the textbook by Barto & Sutton 
and gives an additional visual insight that I was missing when reading this chapter.

We consider a simple 2D grid world environment, where the agent can execute one of the four actions:
go up, go down, go right, go left.

## From deterministic to stochastic environments

### Deterministic environments

In a deterministic reinforcement learning environment, 
executing an action <span class="math display">$$a \in \mathcal{A}$$</span>, results
in state transition from <span class="math display">$$s \rightarrow s'$$</span> with certainty, 
where <span class="math display">$$s \in \mathcal{S}$$</span>. That is, in our simple
2D grid world with four actions, executing the action "go up" is guaranteed
to result in state transition to the state directly above the current state. 
This is presented in the figure below:

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/mdp-deterministic.svg" width="500">
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
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/mdp-stochastic-transition.svg" width="500">
</p>

### Environments with stochastic state transitions and rewards

Even more so, reinforcement learning environments don't have to provide deterministic rewards, 
<span class="math display">$$r \in \mathcal{R}$$</span>, for state transitions!
Suppose that we are indeed transitioning to the state directly above the current state. A deterministic reward for
executing this transition would always provide <span class="math display">$$r = 1$$</span>. But in MDP, 
we want to model the possibility for the rewarding system malfunctioning too! And hence, with 80% probability
we will receive the <span class="math display">$$r = 1$$</span> reward, but with 15% probability we will get
<span class="math display">$$r = 0$$</span> as the reward, and with 5% probability our reward will be
<span class="math display">$$r = -1$$</span>.

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/mdp-stochastic-transition-and-reward.svg" width="500">
</p>

## Understanding the probabilities involved

In a deterministic environment

<span class="math display">$$
p(s' | s, a) = 1 .
$$</span>

You can read <span class="math display">$$p(s' | s, a)$$</span> as the conditional probability of reaching state 
<span class="math display">$$s'$$</span>,
given that the current state is <span class="math display">$$s$$</span> and the action selected is
<span class="math display">$$a$$</span>.

In an environment with stochastic transition probabilities but with deterministic rewards, we can write

<span class="math display">$$
p(s' | s, a) \in [0,1] .
$$</span>

And in the most general case, an environment with stochastic state transitions and stochastic rewards, we can write

<span class="math display">$$
p(s', r | s, a) \in [0,1] ,
$$</span>

where you can read <span class="math display">$$p(s', r | s, a)$$</span> as the *joint* conditional probability
of reaching state <span class="math display">$$s'$$</span> *and* receiving reward 
<span class="math display">$$r$$</span>, 
given that the current state is <span class="math display">$$s$$</span> and the action selected is
<span class="math display">$$a$$</span>.

### Some consequences

In the most general case, an environment with stochastic state transitions and stochastic rewards, we have that

<span class="math display">$$
\sum_{r \in \mathcal{R}} p(s', r | s, a) = p(s' | s, a)
$$</span>

This is easy to show looking at the third figure, where for example, for the transition from the current state
to the state directly above it, we have

<span class="math display">$$
\sum_{r \in \mathcal{R}} p(s', r | s, a) = 0.8 \cdot 0.9 + 0.15 \cdot 0.9 + 0.05 \cdot 0.9 = 0.9 = p(s' | s, a) ,
$$</span>

because the sum of probabilities across all possible stochastic rewards associated
with a particular state transition has to be equal to one.

Of course, a further consequence is that

<span class="math display">$$
\sum_{s \in \mathcal{S}} \sum_{r \in \mathcal{R}} p(s', r | s, a) = 1 ,
$$</span>

which simply pushes the earlier equation further by also summing over probabilities of all state transitions.
Of course, probabilities for all state transitions from any current state have to sum up to one, which is the case
in our simple grid world:

<span class="math display">$$
\sum_{s \in \mathcal{S}} p(s' | s, a) = 0.9 + 0.04 + 0.04 + 0.02 = 1 .
$$</span>