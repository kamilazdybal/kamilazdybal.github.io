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
This mostly stems from a large number of hyper-parameters that we can tweak, which can alter:

**(1)** the dynamics of the agent navigating this environment,

**(2)** the dynamics of gradient descent.

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
The action selected by the trained policy is the argmax over all Q-values. In this environment, I allow four actions:
go up, do down, go left, go right. Hence, I have four Q-values.

During training, we can inspect a selection of Q-values for fixed state transitions in the environment in order to see
if the Q-values behave the way they should. 
Let's monitor the Q-values for the following arrangement of the agent (blue) and target (red):

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/DQN-fixed-transition.png" width="400">
</p>

We know that for such arrangement the best action to take is "go right". Here are the Q-values for that state once the
policy has been trained:

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/DQN-Q-values-for-fixed-transition.png" width="800">
</p>

There's a couple of items that I wanted to point out in the figure above. 

### The best action should always result in the maximum Q-value

First, once we take argmax over the Q-values (_i.e._, we execute the policy in that state) 
at the end of training (episode 500), the action selected 
is indeed to go right because the maximum Q-value for that state is the fourth Q-value, 
<span class="math display">$$ Q_4 $$</span>.

Second, notice that it wasn't necessarily so at the beginning of training. If we zoom in at the Q-values at the early episodes,
the action "go up" wouldn't always be the winning one:

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/DQN-Q-values-for-fixed-transition-zoom-too-early.png" width="450">
</p>

### Q-values should converge

Third, notice that the Q-values converge. 
They plateau at the end of training and become much less noisy than at the beginning of training:

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/DQN-Q-values-for-fixed-transition-zoom-end-of-training.png" width="450">
</p>

### Q-values for all actions should stick together

Fourth, notice that the numerical values of the final Q-values are within some ballpark of 1.0, which, 
not incidentally, is the maximum achievable reward over one full episode in this environment. This is what one should
generally expect in deep Q-learning, even though we may not always know a priori what that maximum possible reward 
(the expected reward) is.
This is the direct aftermath of how the Q-values are updated at each training step 
(see [the Bellman equation](https://kamilazdybal.github.io/jekyll/update/2024/06/02/bellman-equation.html)):

<span class="math display">$$ Q_{\pi}(s, a) = R(s, a) + \gamma \sum_{s'} P(s, a, s') \cdot \text{max} \big( Q_{\pi}(s',a') \big)$$</span>

In the equation above, you can see that the Q-values are constructed from the instantaneous reward plus the sum of discounted future rewards.
Generally, you can expect that the Q-values will converge to within some ballpark from the 
maximum possible expected reward which also depends on the discount factor, <span class="math display">$$ \gamma $$</span>.

### Q-values should race each other

The deep Q-learning algorithm relies on taking argmax over all Q-values to determine the right action 
at each state of the environment.
Assuming that all actions are necessary and taken from time to time in the environment, 
we can expect that there shouldn't be too huge numeric differences in the Q-values. If one Q-value persistently drifts
in its numeric value then either it will never be taken (it's the smallest Q-value) or it is the winning action in each state
(it's the largest Q-value). 
For a well-trained policy, the numeric values of Q-values should change *slightly* from state to state to allow 
for the appropriate action being selected in each state. In other words, Q-values should always be racing each other
in various states.

This is an indication of something not going well during training:

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/DQN-Q-values-drift.png" width="800">
</p>

The reason why you do not want large differences between Q-values is that in the relatively nearby states 
the best action selected should still have the option to change rapidly. 
For example, if the agent is in any of the four tiles directly around the target, 
the best action would change from "go up", to "go down", to "go left", to "go right", but the state value 
(which is the input to the deep Q-network) does not change that much. 
The best course of action is for the network to learn to make tiny adjustment in the Q-values that allow for action switching. 
Otherwise, if there are huge differences in Q-values in one state, 
the network outputs might have a hard time switching back to a different action in a similar state.
In other words, you do not want the deep Q-network become too stiff.

## Looking at training loss

As the Q-values converge to fixed values, the loss should converge too:

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/DQN-MSE.png" width="800">
</p>

### Why is the loss so noisy?

If you're used to training deep neural networks for simple regression tasks, you may be used to loss functions
(e.g., mean-squared-error losses) to be nicely converging and becoming almost flat at the end of training
when using learning rate decay to an appropriately small learning rate value.

If you're now starting to learn RL, you will likely be terrified at the observation that the
mean-squared-error loss for the Q-values is really noisy 
even if the RL training seems to be performing quite well policy-wise! Well, let's discuss the reasons for this!

## The orchestration of hyper-parameters 

Here's the quirky bit of RL: The same exploration probability (<span class="math display">$$ \varepsilon $$</span>) decay 
and learning rate (<span class="math display">$$ \alpha $$</span>) decay spread over 
various durations of training can lead to different training outcomes! In other words, there seems to be the right
orchestration between how we position the decay of <span class="math display">$$ \varepsilon $$</span> and 
<span class="math display">$$ \alpha $$</span> over the duration of training, all other hyper-parameters
being equal. Below is a small schematic where I locate the same decays either over 500 or 1000 episodes.
The exploration probability decays linearly from 0.1 at the first episode to 0.0 at the last episode 
(being either 500 or 1000). In the same way, the cosine learning rate decay is spread over the episodes 
from <span class="math display">$$ 10^{-2} $$</span> at the first episode 
to <span class="math display">$$ 10^{-5} $$</span> at the last episode.

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/DQN-decay-over-episodes.png" width="800">
</p>

Take a look at the outcomes of these two trainings, the first ran for 500 episodes, the second for 1000 episodes: 

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/DQN-rewards-over-episodes-good-short.png" width="800">
</p>

> This first figure shows us that learning the policy perfectly in this environment is possible with just 500 episodes.

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/DQN-rewards-over-episodes-good-long.png" width="800">
</p>

> But if all we had ever tried was 1000 episodes, we would have also learned the policy perfectly,
> but we would not have known that a much shorter training period could have already accomplished the task!
> Notice that here, at episode 500, we're still not solving the task correctly even half the time even though
> <span class="math display">$$ \varepsilon = 0.05 $$</span> at episode 500
> (*i.e.*, random actions are taken only 5% of the time–a reasonably small number 
> that a well-trained policy should be able to correct for by taking on-policy actions the remaining 95% of the time).

So there's always the two questions: How much training is too much training? 
Or, with how little training can we get away with?
This is where training RL becomes a bit of an art! This small 6-by-4 grid world is a very simple task and I was expecting
the RL agent not needing too many trials to learn. 500 episodes with 20 steps in the environment per episode was
more than enough to learn the perfect policy. A more complicated task would require more training time.
With more experience of training across environments with varying complexity 
you will start to be able to take good guesses for the training time.
