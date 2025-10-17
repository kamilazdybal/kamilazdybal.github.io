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

In this post, I'm using a simple instance of training a deep Q-learning reinforcement learning (RL) agent using 
[TF-Agents](https://www.tensorflow.org/agents)
in order to discuss several key characteristics of good-quality training outcome that can help you adjust your RL.

We use a simple 6-by-4 grid world environment where the agent should move towards the target tile, and once it does,
it receives a +1 reward. Any other transition results in a 0 reward.

```
 _______ _______ _______
|       |       |       |
|    ___|_______|___✨  |
|___|___|_______|_______|
|   |   |       |       |
|   🤖  |       |       |
|_______|_______|_______|
```

### Training reinforcement learning can be difficult

Even if you coded the RL algorithm correctly, getting it to train well on a specific environment can take someg work.
This mostly stems from a large number of hyper-parameters that we can tweak which can alter 
(1) the dynamics of the task being solved in this environment (2) the dynamics of the gradient descent.
Hence, it's useful to understand a couple key indicators that we can look at during training 
which can guide our hyper-parameter choice.

## Rewards should be higher with a better policy

The first indication that your policy is improving with training time is that as it's queried later in the training, 
it yields high rewards. To check this, you can implement an exploration probability decay with training time.
For example, you may decay the exploration probability, <span class="math display">$$ \varepsilon $$</span>, from, say, 0.5 to 0.0 with training time, 
and even let it stay zero for a couple final episodes.
As <span class="math display">$$ \varepsilon $$</span> decreases with training time, 
your learned policy is queried more and more frequently, and random actions are taken less and less frequently. 
As a result, at the end of training, you should see high (or highest possible) rewards being achieved in the environment.

Below is the result that you'd like to see 
as <span class="math display">$$ \varepsilon \rightarrow 0 $$</span> with training time. With training time, the learned
policy starts to successfully move the agent towards the target every time, resulting in +1 reward.

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/DQN-rewards-over-episodes-good.png" width="800">
</p>

If, on the other hand, average rewards stagnate at a low value even as your policy is queried more and more frequently,
it is an indication that something isn't setup right in your RL. 
My first go-to hyper-parameter to tweak would be the learning rate.

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/DQN-rewards-over-episodes-poor.png" width="800">
</p>

Of course, you also don't want the rewards to increase and then come back down again.

There's also the question: How much training is too much training? 
This is where training RL becomes a bit of an art! This small 6-by-4 grid world is a very simple task and I was expecting
the RL agent not needing too many trials to learn. 500 episodes with 20 steps in the environment per episode was
more than enough to learn the perfect policy. A more complicated task would require more training time.

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

