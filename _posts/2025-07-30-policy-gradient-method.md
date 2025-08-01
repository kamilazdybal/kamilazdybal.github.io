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

In this post, I show you how to code the policy gradient method which allows a reinforcement learning agent to navigate
continuous action spaces!



<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/continuous-action-space.png" width="500">
</p>




<span class="math display">$$
p(s', r | s, a) \in [0,1] ,
$$</span>

<span class="math display">$$
\sum_{s \in \mathcal{S}} p(s' | s, a) = 0.9 + 0.04 + 0.04 + 0.02 = 1 .
$$</span>