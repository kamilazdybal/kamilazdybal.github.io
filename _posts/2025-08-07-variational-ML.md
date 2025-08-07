---
layout: default
title:  "Variational approaches in machine learning"
date:   2025-08-07 10:00:00 +0100
categories: jekyll update
---

<script type="text/javascript" async="" src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.4/MathJax.js?config=TeX-MML-AM_CHTML">
</script>

<p>
   <a href="/kamilazdybal.github.io/#blog">
      < Go back
  </a>
</p>

# Variational approaches in machine learning



## Gaussian probability density function

The *Gaussian probability density function* (PDF), also known as the *Gaussian normal distribution*,
for a random variable <span class="math display">$$z$$</span> 
is denoted <span class="math display">$$\mathcal{N}(z \mid \mu, \sigma^2)$$</span>, 
where <span class="math display">$$\mu$$</span> is the mean and <span class="math display">$$\sigma$$</span>
is the standard deviation of the distribution (note that <span class="math display">$$\sigma^2$$</span>) is a quantity
known as the variance of the distribution). The Gaussian PDF can be conveniently expressed in analytic form as:

<span class="math display">$$\mathcal{N}(z \mid \mu, \sigma^2) = \frac{1}{\sigma \sqrt{2 \pi}} \exp \left( - \frac{1}{2} \frac{(z - \mu)^2}{\sigma^2} \right)$$</span>

since such form has a total area under the curve equal to unity.

The figure below visualizes a few Gaussian 

The cool part about this distribution is that knowing the values of 
<span class="math display">$$\mu$$</span> and <span class="math display">$$\sigma$$</span> you know everything about it.
What's even cooler, you can now sample a value of the random variable <span class="math display">$$z$$</span> 
from a distribution with a specific values for <span class="math display">$$\mu$$</span> and <span class="math display">$$\sigma$$</span>!





