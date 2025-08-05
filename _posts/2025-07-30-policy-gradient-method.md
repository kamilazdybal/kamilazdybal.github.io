---
layout: default
title:  "Coding the policy gradient method in PyTorch"
date:   2025-07-30 10:00:00 +0100
categories: jekyll update
---

<script type="text/javascript" async="" src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.4/MathJax.js?config=TeX-MML-AM_CHTML">
</script>

<p>
   <a href="/kamilazdybal.github.io/#blog">
      < Go back
  </a>
</p>

# Coding the policy gradient method in PyTorch

The goal of reinforcement learning (RL) is to learn **the optimal policy**, 
<span class="math display">$$ \pi^* $$</span>, for behaving (acting) in an environment to accomplish a specific task.
Policies are simply functions that return an action to execute when in a given state. When policies are stochastic, 
they become distributions, such that <span class="math display">$$ \pi = \pi(a | s) $$</span>, and 
when they are deterministic they simply compute <span class="math display">$$ a = \pi(s) $$</span>.

There are two main approaches to solving RL tasks, or, to be precise, two ways of thinking about obtaining policies...

RL based on consulting learned optimal *value functions*, <span class="math display">$$ q^*(a, s) $$</span>, 
to determine the next action is commonly used for discrete action spaces. 
This approach to RL first determines the value of being in each state of the environment and executing 
a specific action when in that state. Then, the policy becomes a function that always selects the action 
that maximizes this value function, <span class="math display">$$ \pi: a = \text{argmax}(q^*(a, s)) $$</span>.

But we can also skip the step of getting to know value functions. We can directly learn the parameters, 
<span class="math display">$$ \pmb{\theta} $$</span>, 
of the policy <span class="math display">$$ \pi(a | s, \pmb{\theta}) $$</span>.

Often to navigate real-world systems we would like to be able to take continuous actions.
The latter is a much more powerful approach for practical engineering applications because control variables 
of real-world systems are often continuous—think of velocity, acceleration, torque, direction, temperature, etc.
A single action can then immediately scale to the necessary magnitude, 
instead of requiring several incremental actions to reach the same magnitude.

This concept is visualized in the figure below on the example of spatial navigation 
toward a target—many less steps are required to reach the target if the agent is allowed 
to move in the continuous space of (angle, direction) rather than a discrete space of (up, down, right, left).

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/continuous-action-space.png" width="500">
</p>

In this post, I show you how to code **the policy gradient method** which allows an RL agent to navigate
continuous action spaces by sampling them from learned probability distributions!

## Let's talk about softmax...

We'll start by understanding the **softmax function**.




