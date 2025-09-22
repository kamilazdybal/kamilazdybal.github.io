---
layout: default
title:  "Solving your undergraduate homework with a physics-informed neural network (PINN)"
date:   2025-09-21 10:00:00 +0100
categories: jekyll update
---

<script type="text/javascript" async="" src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.4/MathJax.js?config=TeX-MML-AM_CHTML">
</script>

<p>
   <a href="/kamilazdybal.github.io/#blog">
      < Go back
  </a>
</p>

# Solving your undergraduate homework with a physics-informed neural network (PINN)

Here, I will show you how to approximate a solution to a second-order ODE with physics-informed neural networks (PINNs)!
We will take a simple ODE that you often encounter in your undergrad numerical methods class—the steady-state diffusion 
(in this case, of heat). This particular ODE represents a heating/cooling of a 1D rod:

<span class="math display">$$ \begin{equation}
\frac{d^2 T(x)}{d x^2} = \frac{2h}{\lambda r}(T(x) - T_{\infty})
\end{equation}$$</span>

where 
<span class="math display">$$ h $$</span> is the thermal diffusivity, 
<span class="math display">$$ \lambda $$</span> is the thermal conductivity,
<span class="math display">$$ r $$</span> is the radius of the rod, and
<span class="math display">$$ T_{\infty} $$</span> is the surrounding temperature.

This is a boundary-value problem, where we also impose the Dirichlet boundary conditions as
<span class="math display">$$ T(x=0) = T_L $$</span> and
<span class="math display">$$ T(x=L) = T_R $$</span>.

In PINNs, you train an artificial neural network (ANN) to approximate this solution but such that it obeys the underlying ODE. 
The core concept behind a PINN is quite simple: You write your ODE in a residual form and construct a loss
function which is an error measure of that residual. This residual will be different from zero as long as your solution is not exact. 
The loss essentially contains a contribution from differentiating your current approximation, 
<span class="math display">$$ \tilde{T}(x) $$</span>, according to
how that ODE looks like, and satisfying any boundary conditions.
You then backpropagate this error to train the parameters of the ANN.

Note that, beyond this example, PINNs also work for PDEs!

We'll code everything in PyTorch:

```python
import numpy as np
import torch
import torch.nn as nn
import matplotlib.pyplot as plt

dtype  = torch.float64
device = 'cpu'
torch.set_default_dtype(dtype)
```

## Initialization of parameters

The following are the boundary conditions, <span class="math display">$$ T(x=0) = T_L $$</span>
and <span class="math display">$$ T(x=L)=T_R  $$</span>:

```python
T_L = 900     # K
T_R = 300     # K
```

and the other numeric parameters for this problem:

```python
h = 300       # W/(m^2K)
λ = 237       # W/(mK)
r = 0.01      # m
L = 0.5       # m
T_infty = 700 # K
```

As a shorthand, we'll also already evaluate the constant coefficient from the right-hand-side of this ODE:

```python
k = (2.0 * h) / (λ * r)
```

We also create a grid in the <span class="math display">$$ x $$</span> direction for plotting the final solution:

```python
n_points = 1000
x_grid = np.linspace(0.0, L, n_points)
```

## The baseline solution

PINNs often use a neat trick to make the solution obey boundary conditions *exactly*. 

We can do this by first creating a baseline linear function that simply passes through the two boundary conditions. 
We'll call this baseline function <span class="math display">$$ T_b(x) $$</span>.

Next, the trained ANN will only approximate a correction to this linear function, <span class="math display">$$ \mathcal{N}(x) $$</span>
and we will "spread" this solution over the domain using a vanishing factor <span class="math display">$$ x (L - x) $$</span>, so that 
at <span class="math display">$$ x = 0 $$</span> and <span class="math display">$$ x = L $$</span> we enforce no correction added
(we want to preserve the boundary conditions there exactly).

The final approximated solution is a superposition of the two, the baseline linear function (which obeys the boundary conditions at the end points of our domain)
and the output of the ANN:

<span class="math display">$$
\tilde{T}(x) = T_b(x) + x \cdot (L - x) \cdot \mathcal{N}(x)
$$</span>

Let's code the baseline function that passes through 
<span class="math display">$$ T_L $$</span> and <span class="math display">$$ T_R $$</span>
at the end points of our domain:

```python
def baseline_solution(x):
    
    return T_L * (1.0 - x / L) + T_R * (x / L)
```

Let's visualize this baseline:

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/PINNs-baseline-solution.png" width="600">
</p>

## The ANN correction

Now you're free to define whatever fancy ANN you'd like to serve as <span class="math display">$$ \mathcal{N}(x) $$</span>!

I made a network where the user can steer its depth and size of the hidden units. I use ReLU activations, which 
worked better for me in this example than hyperbolic tangents. Note that to define this ANN you use a standard
way of sublcassing ``nn.Module`` from PyTorch (your new class has to have its ``forward()`` function and all...).

```python
class SolutionNetwork(nn.Module):
    
    def __init__(self, 
                 input_dimension=1, 
                 hidden_dimension=8, 
                 output_dimension=1, 
                 network_depth=4):
        
        super().__init__()
        
        layers = []

        # The first (input) layer:
        layers.append(nn.Linear(input_dimension, hidden_dimension))

        # Hidden layers:
        for _ in range(network_depth - 1):
            layers.append(nn.ReLU())
            layers.append(nn.Linear(hidden_dimension, hidden_dimension))

        # The final (output) layer:
        layers.append(nn.ReLU())
        layers.append(nn.Linear(hidden_dimension, output_dimension))

        # Define a sequential model:
        self.PDE_solution_net = nn.Sequential(*layers)

        # Initialize all trainable parameters with the Xavier initialization:
        for module in self.PDE_solution_net:
            
            if isinstance(module, nn.Linear):
                nn.init.xavier_normal_(module.weight)
                nn.init.zeros_(module.bias)

    def forward(self, x):
        
        return self.PDE_solution_net(x)
```

## The complete PINN module

Now we just complete the picture by defining this PINN module which will take an instance of ``SolutionNetwork``, and will
add it to the baseline function, as we've seen earlier:

```python
class PINN(nn.Module):

    def __init__(self, 
                 solution_network):
        
        super().__init__()
        
        self.solution_network = solution_network

    def forward(self, x):
        
        PINN_correction = self.solution_network(x)

        output = baseline_solution(x) + x * (L - x) * PINN_correction
        
        return output
```

## The residual loss

Now we need to construct the residual loss! When we write our ODE in a residual form, we get:

<span class="math display">$$ \begin{equation}
\frac{d^2 T(x)}{d x^2} - \frac{2h}{\lambda r}(T(x) - T_{\infty}) = 0
\end{equation}$$</span>

We will train the ANN such that this equation gives *almost* zero. Our loss function will simply be 
the mean-squared-error (MSE) over some mini-batch

<span class="math display">$$ \begin{equation}
\mathcal{L} = \text{MSE} \left( \frac{d^2 \tilde{T}(x)}{d x^2} - \frac{2h}{\lambda r}(\tilde{T}(x) - T_{\infty}) \right)
\end{equation}$$</span>

But, as you may rightly wonder, this loss contains a second derivative of <span class="math display">$$ \tilde{T}(x) $$</span>.
How are we going to get that??? Thankfully, PyTorch's automatic differentiation module will help us there!

We can define a function that computes the first derivative, like so:

```python
def dTdx(T, x):
    
    return torch.autograd.grad(T, x, torch.ones_like(T), create_graph=True)[0]
```

and now define a function that computes the second derivative by running the first derivative operation twice internally:

```python
def d2Tdx2(T, x):

    return dTdx(dTdx(T, x), x)
```



## How does a PINN compare to a finite difference method?

Here we check how does the PINN solution compare to a numerical approximation 
using a second-order accurate finite difference stencil.



