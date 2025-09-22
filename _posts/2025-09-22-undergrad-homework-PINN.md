---
layout: default
title:  "Solving your undergraduate homework with PINNs"
date:   2025-09-22 10:00:00 +0100
categories: jekyll update
---

<script type="text/javascript" async="" src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.4/MathJax.js?config=TeX-MML-AM_CHTML">
</script>

<p>
   <a href="/kamilazdybal.github.io/#blog">
      < Go back
  </a>
</p>

# Solving your undergraduate homework with physics-informed neural networks (PINNs)

Here, I will show you how to approximate a solution to a second-order ODE with physics-informed neural networks (PINNs)!
In PINNs, you train an artificial neural network to approximate this solution. 
The core concept behind a PINN is quite simple: You write your ODE (or PDE) in the residual form, and construct a loss
function as that residual, which will be different from zero as long as your solution is not exact. 
This loss will essentially contain a contribution from differentiating your current approximation, according to
how that ODE (or PDE) looks like, and a contribution from satisfying boundary conditions.

Here, we will take a simple ODE that you often encounter in your undergrad, which is the steady-state diffusion 
(in this case, of heat). This particular ODE represents a heating/cooling of a 1D rod:

<span class="math display">$$ \begin{equation}
\frac{d^2 T}{d x^2} = \frac{2h}{\lambda r}(T - T_{\infty})
\end{equation}$$</span>

where 
<span class="math display">$$ h $$</span> is the thermal diffusivity, 
<span class="math display">$$ \lambda $$</span> is the thermal conductivity,

```python
import numpy as np
import torch
import torch.nn as nn
import matplotlib.pyplot as plt
```








## How does a PINN compare to a finite difference method?

Here we check how does the PINN solution compare to a numerical approximation 
using a second-order accurate finite difference stencil.



