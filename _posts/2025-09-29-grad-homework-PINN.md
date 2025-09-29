---
layout: default
title:  "Warm-starting finite difference methods with PINNs"
date:   2025-09-29 10:00:00 +0100
categories: jekyll update
---

<script type="text/javascript" async="" src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.4/MathJax.js?config=TeX-MML-AM_CHTML">
</script>

<p>
   <a href="/kamilazdybal.github.io/#blog">
      < Go back
  </a>
</p>

# Warm-starting finite difference methods with PINNs

In this post, we'll modify [the previous example](https://kamilazdybal.github.io/jekyll/update/2025/09/21/undergrad-homework-PINN.html)
and solve a *nonlinear* ordinary differential equation (ODE) with physics-informed neural networks (PINNs).

We'll take the second-order ODE describing the steady-state diffusion of heat due to radiation in a 1D rod:

<span class="math display">$$ \begin{equation}
\frac{d^2 T(x)}{d x^2} = \alpha(T^4(x) - T_{\infty}^4)
\end{equation}$$</span>

where
<span class="math display">$$ \alpha $$</span> is a coefficient that combines the thermal conductivity
and emissivity 
and <span class="math display">$$ T_{\infty} $$</span> is the surrounding temperature.

We'll do something fancy at the end though—we'll pass the pre-computed PINN solution as an initial
guess to a finite difference method solving a linearized version of this ODE and show 
that the convergence can be (two iterations 😉) faster! This shows the potential of a PINN model to
warm-start finite difference methods.

## Modest code modification

The great part of using PINNs to solve ODEs is that not a whole lot needs to change in our previous code to
accommodate a different right-hand-side. 

Except for specifying the new numeric parameters of this problem:

```python
T_L = 300     # K
T_R = 400     # K
L = 1         # m
α = 1e-8      # 1/(K^3m^2)
T_infty = 900 # K
```

everything else that needs to change is how we compute the new residual! This ODE in a residual form looks like this:

<span class="math display">$$ \begin{equation}
\frac{d^2 T(x)}{d x^2} - \alpha(T(x)^4 - T_{\infty}^4) = 0
\end{equation}$$</span>

Hence, we need to replace this part in our training loop:

```python
residual = T_xx - k * (T_pred - T_infty)
```

with this:

```python
residual = T_xx - α * (T_pred**4 - T_infty**4)
```

and we're ready to train the new PINN model!

Here's the PINN approximation along with a finite-difference numerical approximation using a second-order-accurate stencil:

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/PINNs-nonlinear-approximation.png" width="800">
</p>

As before, the PINN approximation is quite significantly different from the finite-difference approximation.
Which begs the question what could PINNs be actually useful for... 🤔

## Warm-starting finite difference methods

Let's try to use this pre-computed PINN solution as an initial guess when we solve this ODE numerically and see if
it can be helpful!

I linearized this ODE to get a set of linear equations of the form:

<span class="math display">$$ \begin{equation}
\frac{T_{i-1} - 2T_i + T_{i - 1}}{\Delta x^2} = \alpha (- 3{T}_{\text{guess}, i}^4 + 4 {T}_{\text{guess}, i}^3 T_i - T_{\infty}^4)
\end{equation}$$</span>

where, in general, <span class="math display">$$ {T}_{\text{guess}}(x)$$</span> is our initial guess for the temperature
distribution in the entire domain.

I solve these in an iterative process of updating the guess with the current numeric solution. 
My own initial guess would be to set 
<span class="math display">$$ T(x) = \frac{T_{\infty}}{2}$$</span>. In this case, my solver gets to the 
<span class="math display">$$ L_2 $$</span> norm between the previous and current guess lower than 
<span class="math display">$$ 10^{-6} $$</span> in 6 iterations:

```
10946.85015189905
2721.2344585582314
442.33582868664246
10.182994079198922
0.005245534201349177
3.8544634728714925e-09

Converged in 6 iterations.
```

When I use the pre-computed PINN solution as the initial guess, I converge in 4 iterations:

```
703.0258369833273
22.588183443400222
0.025565367593299866
1.2049626265198362e-07

Converged in 4 iterations.
```

Maybe PINNs are useful for something after all! 😉