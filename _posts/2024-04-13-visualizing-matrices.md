---
layout: default
title:  "Visualizing matrices"
date:   2024-04-12 10:00:00 +0100
categories: jekyll update
---

<script type="text/javascript" async="" src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.4/MathJax.js?config=TeX-MML-AM_CHTML">
</script>

<p>
   <a href="/kamilazdybal.github.io/#blog">
      < Go back
  </a>
</p>

# Visualizing matrices

Ever since I started studying data science, I got into a habit of visualizing matrices, 
either on paper or in my head. Visualizing the shapes of matrices that take part in an algebraic expression 
is a really neat way to debug your operations on matrices! This is handy when working with Numpy or Matlab, 
when reading literature, and when writing papers. In this note, I show you a couple of examples!

## Multiplying two matrices

Suppose we want to multiply two matrices, <span class="math display">$$\mathbf{A} \in \mathbb{R}^{p \times q}$$</span>
and <span class="math display">$$\mathbf{B} \in \mathbb{R}^{q \times r}$$</span>, and infer the shape of the
resulting matrix, <span class="math display">$$\mathbf{U}$$</span>:

<span class="math display">$$\mathbf{U} = \mathbf{A} \cdot \mathbf{B}$$</span>

The interior dimensions of two multiplied matrices need to match since this is the dimension along which 
the dot products are computed between the rows of <span class="math display">$$\mathbf{A}$$</span> and the columns
of <span class="math display">$$\mathbf{B}$$</span>:

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/visualizing-matrices-A-times-B.png" width="750">
</p>

The remaining dimensions, <span class="math display">$$p$$</span> and <span class="math display">$$r$$</span>, are "free",
in a sense that they can be anything and they dictate the dimensions of the resulting matrix, <span class="math display">$$\mathbf{U}$$</span>.

So, in this example, <span class="math display">$$\mathbf{U} \in \mathbb{R}^{p \times r}$$</span>.

## Multiplying three or more matrices

Need to multiply three or more matrices? No problem! Just stack your earlier matrix at the bottom and repeat!

Let's take <span class="math display">$$\mathbf{A} \in \mathbb{R}^{p \times q}$$</span>, 
<span class="math display">$$\mathbf{B} \in \mathbb{R}^{q \times r}$$</span> and 
<span class="math display">$$\mathbf{C} \in \mathbb{R}^{r \times s}$$</span>. The matrix multiplication is as follows:

<span class="math display">$$\mathbf{U} = \mathbf{A} \cdot \mathbf{B} \cdot \mathbf{C}$$</span>

Now consider your matrix multiplication equation from right to left and draw it from top to bottom, stacking the consecutive matrices: 

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/visualizing-matrices-A-times-B-times-C.png" width="800">
</p>

Here, <span class="math display">$$p$$</span> and <span class="math display">$$s$$</span> are "free dimensions", _i.e._, they can be anything
and that anything dictates the dimensions of the resulting matrix. 
In this example <span class="math display">$$\mathbf{U} \in \mathbb{R}^{p \times s}$$</span>.

## Multiplying vectors

You can apply the same strategy to perform vector-matrix multiplications or vector-vector multiplications. Let's look
at two more examples where we multiply two vectors, <span class="math display">$$\mathbf{a}$$</span>
and <span class="math display">$$\mathbf{b}$$</span>.

In the first example, we compute a classic dot product between two vectors of the same length. Let's take 
<span class="math display">$$\mathbf{a} \in \mathbb{R}^{p}$$</span>
and <span class="math display">$$\mathbf{b} \in \mathbb{R}^{p}$$</span> and create a vector (dot) product:

<span class="math display">$$u = \mathbf{a} \cdot \mathbf{b}^{\top}$$</span>

This multiplication of vectors results in a single value (a scalar), <span class="math display">$$u$$</span>:

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/visualizing-matrices-a-times-bT.png" width="750">
</p>

Note that from the picture above it becomes clear that we couldn't multiply 
<span class="math display">$$\mathbf{a} \cdot \mathbf{b}^{\top}$$</span> if <span class="math display">$$\mathbf{a}$$</span>
and <span class="math display">$$\mathbf{b}$$</span> had different lengths. There simply wouldn't be enough elements in the
shorter vector to complete the dot product.

On the other hand, we _can_ multiply two vectors of different length, say 
<span class="math display">$$\mathbf{a} \in \mathbb{R}^{p}$$</span> and
<span class="math display">$$\mathbf{b} \in \mathbb{R}^{q}$$</span>,
in the following way:

<span class="math display">$$\mathbf{U} = \mathbf{a}^{\top} \cdot \mathbf{b}$$</span>

simply because it's still the interior dimension of two multiplied vectors that has to match, and in this case this
dimension is equal to 1! The result of such multiplication of two vectors is an entire matrix of shape
<span class="math display">$$\mathbf{U} \in \mathbb{R}^{p \times q}$$</span>:

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/visualizing-matrices-aT-times-b.png" width="750">
</p>

Similarly to the matrix-matrix multiplication examples, <span class="math display">$$p$$</span> and <span class="math display">$$q$$</span> are "free dimensions".
They can be anything and they dictate the dimensions of the resulting matrix.





