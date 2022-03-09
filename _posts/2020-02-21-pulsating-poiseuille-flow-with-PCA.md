---
layout: default
title:  "PCA approximation to the pulsating Poiseuille flow"
date:   2020-02-21 15:00:00 +0100
categories: jekyll update
---

<p>
   <a href="/science-docs/#blog">
      < Go back
  </a>
</p>

# PCA approximation to the pulsating Poiseuille flow

Poiseuille flow is a flow of fluid between two parallel plates. In the simplest case one can assume that the pressure gradient is constant throughout the channel. In that case, it is easy to solve the Navier-Stokes equations and obtain an analytic solution that results in a parabolic velocity profile. But much more interesting things start to happen when we assume that pressure is a certain function depending on time. In this example, we took: p(t) = pM + pA cos(omega t), where pM, pA and omega are constants. Interestingly, we can find an analytic solution for the velocity profile also in that case, using a method called *asymptotic complex solution*.

By plotting the obtained velocity profile we get a cool animation! Below you can see the exact solution and, just for fun, a PCA approximation of that solution using the first Principal Component.

<p align="center">
  <img src="https://github.com/kamilazdybal/POD-DMD-decompositions/raw/master/python-reproduction/pulsating-poiseuille.gif">
</p>

Code can be accessed [here](https://github.com/kamilazdybal/POD-DMD-decompositions/tree/master/python-reproduction).
