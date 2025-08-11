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

Variational approaches in machine learning (ML) shift the perspective away from explicitly dealing with data samples 
to dealing with probability distributions that describe those data samples. This can provide a powerful data modeling
approach, recently standing behind the many successes of generative models.

Since the core concepts of variational approaches are rooted in probability distributions, we need to first
talk about one of the simplest ones...

## The Gaussian normal distribution

For a random variable <span class="math display">$$z$$</span>—for example, star dates from *Star Trek Original Series*—the 
*Gaussian probability density function* (PDF), also known as the *Gaussian normal distribution*,
is denoted <span class="math display">$$\mathcal{N}(z \mid \mu, \sigma)$$</span>, 
where <span class="math display">$$\mu$$</span> is the mean and <span class="math display">$$\sigma$$</span>
is the standard deviation of the distribution (note that <span class="math display">$$\sigma^2$$</span> is a quantity
known as the variance of the distribution). The symbol "<span class="math display">$$\mid$$</span>" denotes a conditional
probability. The Gaussian PDF can be conveniently expressed in analytic form as:

<span class="math display">$$\mathcal{N}(z \mid \mu, \sigma) = \frac{1}{\sigma \sqrt{2 \pi}} \exp \left( - \frac{1}{2} \frac{(z - \mu)^2}{\sigma^2} \right)$$</span>

since such a function always has the total area under the curve equal to unity.

Python implementation of the above equation is quite straightforward:

```python
import numpy as np

def gaussian_PDF(x, 
                 μ=0.0, 
                 σ=1.0):

    return 1.0 / (σ * np.sqrt(2.0 * np.pi)) * np.exp(- 1.0 / 2.0 * (x - μ)**2 / (σ**2))
```

The figure below visualizes a few Gaussian PDFs for a couple of choices for 
<span class="math display">$$\mu$$</span> and <span class="math display">$$\sigma$$</span>.

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/variational-gaussian-PDFs.png" width="800">
</p>

The cool part about this distribution is that knowing the values of 
<span class="math display">$$\mu$$</span> and <span class="math display">$$\sigma$$</span> you know everything about it.
What's even cooler, you can now sample a value of the random variable <span class="math display">$$z$$</span> 
from a distribution given a specific value for <span class="math display">$$\mu$$</span> and <span class="math display">$$\sigma$$</span>!
The way to do that is to first draw a sample, <span class="math display">$$\varepsilon$$</span>, 
from <span class="math display">$$\mathcal{N}(z \mid \mu = 0.0, \sigma = 1.0)$$</span>
and re-scale that sample to the desired <span class="math display">$$\mu$$</span> and <span class="math display">$$\sigma$$</span> values, like so:

<span class="math display">$$z = \varepsilon \cdot \sigma + \mu$$</span>

Take a look at how I have now drawn 1000 samples from each distribution and plotted histograms for those samples.
They indeed fit the given PDF!

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/variational-gaussian-PDFs-histograms.png" width="800">
</p>

## Working with log-distributions

Working with probabilities or PDFs can be tricky to ML algorithms, because those can get
arbitrarily close to zero. Take a look at the Gaussian PDFs from the figure before, for the most part
(stretching to plus/minus infinity) the Gaussian PDF is very near zero. ML approaches may not work that well
when they have to discern between 
<span class="math display">$$10^{-6}$$</span> and <span class="math display">$$10^{-7}$$</span>
and, at the same time, also work well in the regime between
<span class="math display">$$10^{0}$$</span> and <span class="math display">$$10^{-1}$$</span>.
This is why you will often encounter log-transformations of probabilities, or of PDFs, in ML.
In the figure below, I've transformed the earlier Gaussian PDFs with a natural logarithm.
There is now much more variability in values that we would have previously deemed as essentially zero.

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/variational-log-gaussian-PDFs.png" width="800">
</p>

Let's compute the natural logarithm of the Gaussian normal distribution—this will come in handy later:

<span class="math display">
$$\ln \left( \mathcal{N}(z \mid \mu, \sigma) \right) = \ln \left( \frac{1}{\sigma} \right) + \ln \left( \frac{1}{\sqrt{2\pi}} \right) + -\frac{1}{2} \frac{(z - \mu)^2}{\sigma^2} = -\frac{1}{2} \left( \ln \sigma^2 + \ln(2\pi) + \frac{(z - \mu)^2}{\sigma^2} \right)$$
</span>
