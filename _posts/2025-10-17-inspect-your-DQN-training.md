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

Training reinforcement learning (RL) can be difficult. 
Even if you coded the RL algorithm correctly, getting it to train well on a specific environment can take some work.
This mostly stems from a large number of hyper-parameters that we can tweak, which can alter 
(1) the dynamics of the agent navigating this environment and (2) the dynamics of gradient descent.
Hence, it's useful to understand a couple of key indicators that you can look at during training, 
which can guide your hyper-parameter choice.

In this post, we'll use a simple instance of training a deep Q-learning RL agent 
([`DqnAgent`](https://www.tensorflow.org/agents/api_docs/python/tf_agents/agents/DqnAgent) from 
[TF-Agents](https://www.tensorflow.org/agents)). 
We'll use a simple 6-by-4 grid world environment where the agent moves towards the target tile, and once it does,
it receives a +1 reward. Any other transition results in a 0 reward.

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/DQN-env.gif" width="400">
</p>

## Rewards should be higher with a better policy

The first indication that your policy is improving with training is that as it's queried later in the training 
it yields high rewards. To check this, you can implement the exploration probability decay with training time.
For example, you may decay the exploration probability, <span class="math display">$$ \varepsilon $$</span>, from, 
say, 0.5 at the beginning of training to 0.0 at the end of training, 
and even let it stay zero for a couple of final episodes.
As <span class="math display">$$ \varepsilon $$</span> decreases with training time, 
your learned policy is queried more and more frequently and random actions are taken less and less frequently. 
As a result, at the end of training, you should see high (or highest possible) rewards being achieved in the environment.

Below is the result that you'd like to see 
as <span class="math display">$$ \varepsilon \rightarrow 0 $$</span> with training time. With more training, 
the learned policy starts to successfully move the agent towards the target every time, resulting in +1 reward.

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/DQN-rewards-over-episodes-good.png" width="800">
</p>

If, on the other hand, average rewards stagnate at a low value even as your policy is queried more and more frequently,
it is an indication that something isn't setup right in your RL. 
My first go-to hyper-parameter to tweak then would be the learning rate.

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/DQN-rewards-over-episodes-poor.png" width="800">
</p>

Of course, you also don't want the rewards to increase and then come back down again.

## Q-values should be converging and racing each other

The outputs of the deep Q-network are the Q-values. 
They are estimates of the value of taking a given action when in a particular state.
The action selected by the trained policy is the argmax over all Q-values.

### Q-values should converge

Generally, you can expect that the Q-values will converge to within some ballpark from the maximum possible expected reward.



### Q-values for all actions should stick together

The deep Q-learning algorithm relies on taking argmax over all Q-values to determine the right action 
at each state of the environment.
Assuming that all actions are necessary and taken from time to time in the environment, 
we can expect that there shouldn't be too huge numeric differences in the Q-values. If one Q-value persistently drifts
in its numeric value then either it will never be taken (it's the smallest Q-value) or it is the winning action in each state
(it's the largest Q-value). 
For a well-trained policy, the numeric values of Q-values should change *slightly* from state to state to allow 
for the appropriate action being selected in each state. In other words, Q-values should always be racing each other
in various states.



## Looking at training loss



### Why is the loss so noisy?

If you're used to training deep neural networks for simple regression tasks, you may be used to loss functions
(e.g., mean-squared-error losses) to be nicely converging and becoming almost flat at the end of training
when using learning rate decay to an appropriately small learning rate value.

If you're now starting to learn reinforcement learning, you will likely be terrified at the observation that the
mean-squared-error loss for the Q-values is really noisy 
even if the RL training seems to be performing quite well policy-wise! Well, let's discuss the reasons for this!

## The orchestration of hyper-parameters 

There's also the question: How much training is too much training? 
This is where training RL becomes a bit of an art! This small 6-by-4 grid world is a very simple task and I was expecting
the RL agent not needing too many trials to learn. 500 episodes with 20 steps in the environment per episode was
more than enough to learn the perfect policy. A more complicated task would require more training time.
