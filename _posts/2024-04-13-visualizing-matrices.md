---
layout: default
title:  "Visualizing matrices"
date:   2024-04-12 10:00:00 +0100
categories: jekyll update
---

<p>
   <a href="/kamilazdybal.github.io/#blog">
      < Go back
  </a>
</p>

# Visualizing matrices

Ever since I started studying data science, I got into a habit of visualizing matrices, 
either on paper or in my head. Visualizing the shapes of matrices that take part in an algebraic expression 
is a really neat way to debug your operations on matrices! In this note, I show you a couple of examples!

## Multiplying two matrices

Suppose we want to multiply two matrices, <span class="math display">$$\mathbf{A} \in \mathbb{R}^{(p \times q)}$$</span>
and <span class="math display">$$\mathbf{B} \in \mathbb{R}^{(q \times r)}$$</span> and infer the shape of the
resulting matrix, <span class="math display">$$\mathbf{U}$$</span>:

<span class="math display">$$\mathbf{U} = \mathbf{A} \cdot \mathbf{B}$$</span>

The interior dimensions of two multiplied matrices need to match since this is the dimension along which 
the dot products are computed between the rows of <span class="math display">$$\mathbf{A}$$</span> and the columns
of <span class="math display">$$\mathbf{B}$$</span>:

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/visualizing-matrices-A-times-B.png" width="400">
</p>

The remaining dimensions, <span class="math display">$$p$$</span> and <span class="math display">$$r$$</span> are "free",
in a sense that they can be anything and they dictate the dimensions on the resulting matrix, <span class="math display">$$\mathbf{U}$$</span>.

So finally, <span class="math display">$$\mathbf{U} \in \mathbb{R}^{(p \times r)}$$</span>.

## Multiplying three or more matrices

Need to multiply three or more matrices?

<span class="math display">$$\mathbf{U} = \mathbf{C} \cdot \mathbf{B} \cdot \mathbf{A}$$</span>

No problem! Just stack your earlier matrix at the bottom and repeat!

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/visualizing-matrices-A-times-B-times-C.png" width="400">
</p>