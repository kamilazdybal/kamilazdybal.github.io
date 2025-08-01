---
layout: default
title:  "The ideal pendulum"
date:   2025-08-01 10:00:00 +0100
categories: jekyll update
---

<script type="text/javascript" async="" src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.4/MathJax.js?config=TeX-MML-AM_CHTML">
</script>

<p>
   <a href="/kamilazdybal.github.io/#blog">
      < Go back
  </a>
</p>

# The ideal pendulum

Numerical solutions to motion of an ideal pendulum can generate useful dynamical system datasets for testing 
a bunch of proof-of-concept research ideas. Below, I show solutions to an **undamped** and **damped** ideal pendulum.

 ## Undamped pendulum

Let's start with coding the undamped ideal pendulum in Python.



The figures below are my reproductions of figures shown in section 1.2.3 in Prof. Scheinerman's textbook 
[https://github.com/scheinerman/InvitationToDynamicalSystems](*Invitation to Dynamical Systems*).

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/ideal-pendulum-01.png" width="500">
</p>

> The motion of a pendulum with <span class="math display">$$ \theta_0 = 0.1 $$</span> and <span class="math display">$$ \omega_0 = 0.0 $$</span>.

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/ideal-pendulum-02.png" width="500">
</p>

> The motion of a pendulum with <span class="math display">$$ \theta_0 = 3.0 $$</span> and <span class="math display">$$ \omega_0 = 0.0 $$</span>.

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/ideal-pendulum-03.png" width="500">
</p>

> The motion of a pendulum with <span class="math display">$$ \theta_0 = 0.0 $$</span> and <span class="math display">$$ \omega_0 = 2.0 $$</span>. 
> Interestingly, here I wasn't quite able to get Prof. Scheinerman's figure and the solution strongly depends on the type of solver used (I've used BDF).

## Damped pendulum



