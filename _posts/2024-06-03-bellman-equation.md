---
layout: default
title:  "Solving the Bellman equation with a numerical solver"
date:   2024-06-02 10:00:00 +0100
categories: jekyll update
---

<script type="text/javascript" async="" src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.4/MathJax.js?config=TeX-MML-AM_CHTML">
</script>

<p>
   <a href="/kamilazdybal.github.io/#blog">
      < Go back
  </a>
</p>

# Solving the Bellman equation with a numerical solver

This is a simple example of solving the Bellman equation with a numerical solver for a very small reinforcement learning environment.
For such small environments it is possible to obtain the optimal policy without much effort. So let's do that!

## The Bellman equation

The total pay-off is a sum of discounted rewards:

<span class="math display">$$ 
R(s_0) + \gamma R(s_1) + \gamma^2 R(s_2) + \dots 
$$</span>

where <span class="math display">$$R(s)$$</span> is the reward the agent receives in state <span class="math display">$$s$$</span> and <span class="math display">$$\gamma \in \langle 0,1)$$</span> is the discount factor.

The goal of the optimal policy is to maximize the expected value of the total pay-off.

We'll denote the expected total pay-off under policy <span class="math display">$$\pi$$</span> as <span class="math display">$$v^{\pi}(s)$$</span>. 
The agent starts in a state <span class="math display">$$s$$</span> and executes a policy <span class="math display">$$\pi$$</span>:

<span class="math display">$$
v^{\pi}(s) = \mathbb{E} \big( R(s) + \gamma \sum_{s'} P \cdot v^{\pi} (s') \big)
$$</span>

where <span class="math display">$$P$$</span> is the transition probability and <span class="math display">$$s'$$</span> is the immediate future state.
The summation loops through all possible future states that are achievable directly from the current state <span class="math display">$$s$$</span>.
This will typically be a sum over a small number of elements -- typically much smaller then the total number of states in an environment --
because only a handful of states are immediately adjacent to any current state <span class="math display">$$s$$</span>.

## The environment

Consider a simple environment with only 6 states:

```
 _______ _______ _______
|       |       |       |
| (1,2) | (2,2) | (3,2) |
|_______|_______|_______|
|       |       |       |
| (1,1) | (2,1) | (3,1) |
|_______|_______|_______|
```

with a policy <span class="math display">$$\pi$$</span>:

```
 _______ _______ _______
|       |       |       |
|  ->   |  ->   |  +1   |
|_______|_______|_______|
|       |       |       |
|  ^    |  ^    |  <-   |
|_______|_______|_______|
```

and with all transition probabilities equal to 1. The +1 tile is a terminal state at which the agent receives the +1 reward.

The agent travels the environment according to the policy starting from some initial position. 
The agent's goal is to reach the +1 tile, irrespective of the starting position:

```
 _______ _______ _______
|       |       |       |
|   ____|_______|___✨  |
|___|___|_______|_______|
|   |   |       |       |
|   🤖  |       |       |
|_______|_______|_______|
```

## The system of Bellman equations for this environment

In order to compute the value function for this policy, we solve the following system of six linear equations:

<span class="math display">$$
\begin{cases}
v^{\pi}((1,1)) = R((1, 1)) + \gamma v^{\pi}((1,2)) \\
v^{\pi}((2,1)) = R((2, 1)) + \gamma v^{\pi}((2,2)) \\
v^{\pi}((3,1)) = R((3, 1)) + \gamma v^{\pi}((2,1)) \\
v^{\pi}((1,2)) = R((1, 2)) + \gamma v^{\pi}((2,2)) \\
v^{\pi}((2,2)) = R((2, 2)) + \gamma v^{\pi}((3,2)) \\
v^{\pi}((3,2)) = R((3, 2))
\end{cases}
$$</span>

Of all the immediate rewards present in this set of equations only <span class="math display">$$R((3,2)) \neq 0$$</span>. 
We know that <span class="math display">$$R((3,2)) = 1$$</span>.

This system can easily be solved in your head starting from <span class="math display">$$v^{\pi}((3,2)) = 1$$</span> 
and successively computing the remaining values. 
Assuming <span class="math display">$$\gamma = 0.9$$</span>, this leads to the following value function for each state:

```
 _______ _______ _______
|       |       |       |
| 0.81  | 0.9   |  1    |
|_______|_______|_______|
|       |       |       |
| 0.729 | 0.81  | 0.729 |
|_______|_______|_______|
```

But let's write out the Bellman equation in a matrix form:

<span class="math display">$$
\begin{bmatrix}
1 & 0 & 0 & -\gamma & 0 & 0 \\
0 & 1 & 0 & 0 & -\gamma & 0 \\
0 & -\gamma & 1 & 0 & 0 & 0 \\
0 & 0 & 0 & 1 & -\gamma & 0 \\
0 & 0 & 0 & 0 & 1 & -\gamma \\
0 & 0 & 0 & 0 & 0 & 1
\end{bmatrix}
\begin{bmatrix}
v_{11} \\
v_{21} \\
v_{31} \\
v_{12} \\
v_{22} \\
v_{32}
\end{bmatrix} = 
\begin{bmatrix}
0 \\
0 \\
0 \\
0 \\
0 \\
1
\end{bmatrix}
$$</span>

and let's solve it with ``numpy.linalg.solve()``.

## Python code

```python
import numpy as np
import matplotlib.pyplot as plt

discount = 0.9

A = np.eye(6,6)
discounts_idx = [3, 4, 1, 4, 5]
for i, idx in enumerate(discounts_idx):
    A[i,idx] = -discount

b = np.array([0,0,0,0,0,1])

value_function = np.linalg.solve(A, b)
value_function = np.reshape(value_function, (2,3))

plt.figure(figsize=(4,3))
plt.imshow(value_function, origin='lower', cmap='coolwarm')
plt.xticks([])
plt.yticks([])
for i in range(2):
    for j in range(3):
        text = plt.text(j, i, round(value_function[i, j], 3), fontsize=20, ha="center", va="center", color="w")
plt.savefig('RL-environement-with-value-functions.png', dpi=300, bbox_inches='tight')
```

This results in the following value function:

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/RL-environement-with-value-functions.png" width="300">
</p>

Just like we've computed manually before!