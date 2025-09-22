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
<span class="math display">$$ T(x=L) = T_R $$</span>, where <span class="math display">$$ L $$</span> is the rod's length.

## The core idea behind PINNs

In PINNs, you train an artificial neural network (ANN) to approximate the solution, 
<span class="math display">$$ T(x) $$</span>, but such that it obeys the underlying ODE. 
The core concept behind a PINN is quite simple: You write your ODE in a residual form and construct a loss
function which is an error measure of that residual. This residual will be different from zero as long as your solution is not exact. 
The loss essentially contains a contribution from differentiating your current approximation, 
<span class="math display">$$ \tilde{T}(x) $$</span>, according to
how the underlying ODE looks like, and satisfying any boundary conditions.
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
x_grid_torch = torch.linspace(0.0, L, n_points, dtype=dtype, device=device).reshape(-1, 1)
```

(We use PyTorch's linspace instead of Numpy's linspace, because later we'll be querying the PINN model using this grid.)

## The baseline solution, <span class="math display">$$ T_b(x) $$</span>

PINNs often use a neat trick to make the solution obey boundary conditions *exactly*. 

We can do this by first creating a baseline linear function that simply passes through the two boundary conditions. 
We'll call this baseline function <span class="math display">$$ T_b(x) $$</span>.
Let's code the baseline function that passes through 
<span class="math display">$$ T_L $$</span> and <span class="math display">$$ T_R $$</span>
at the end points of our domain:

```python
def baseline_solution(x):
    
    return T_L * (1.0 - x / L) + T_R * (x / L)
```

This is our baseline:

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/PINNs-baseline-solution.png" width="800">
</p>

As you can see, it's just a linear function but one that obeys our boundary conditions!

Next, the trained ANN will only approximate **a correction** to this baseline linear function, <span class="math display">$$ \mathcal{N}(x) $$</span>,
and we will "spread" this correction over the domain using a multiplier <span class="math display">$$ x (L - x) $$</span>, so that 
at <span class="math display">$$ x = 0 $$</span> and <span class="math display">$$ x = L $$</span> we enforce no correction added
(we want to preserve the boundary conditions there exactly).

The final approximated solution that a PINN computes is a superposition of the two:
the baseline linear function (which obeys boundary conditions at the end points of our domain)
and the output of the ANN (with the multiplier which also preserves boundary conditions):

<span class="math display">$$
\tilde{T}(x) = T_b(x) + x \cdot (L - x) \cdot \mathcal{N}(x)
$$</span>

## The ANN correction, <span class="math display">$$ \mathcal{N}(x) $$</span>

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

We can already initialize this ANN that serves as <span class="math display">$$ \mathcal{N}(x) $$</span>:

```python
solution_network = SolutionNetwork(input_dimension=1, 
                                   hidden_dimension=16, 
                                   output_dimension=1, 
                                   network_depth=8).to(device).to(dtype)
```

The PINN solution is a superposition of these two:

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/PINNs-superposition.png" width="800">
</p>

## The complete PINN module

Now we just complete the picture by defining this PINN module which will take an instance of `SolutionNetwork` and will
add it to the baseline function, as we've seen earlier:

<span class="math display">$$
\tilde{T}(x) = T_b(x) + x \cdot (L - x) \cdot \mathcal{N}(x)
$$</span>

This class's `forward()` does this superposition:

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

We initialize the complete PINN module which uses the ANN that we just initialized:

```python
PINN_model = PINN(solution_network).to(device).to(dtype)
```

## The residual loss

Now we need to construct the residual loss! When we write our ODE in a residual form, we get:

<span class="math display">$$ \begin{equation}
\frac{d^2 T(x)}{d x^2} - \frac{2h}{\lambda r}(T(x) - T_{\infty}) = 0
\end{equation}$$</span>

We will train the ANN such that this equation gives *almost* zero. Our loss function will simply be 
the mean-squared-error (MSE) over some mini-batch of <span class="math display">$$ n $$</span> points:

<span class="math display">$$ \begin{equation}
\mathcal{L} = \text{MSE}_{i=0}^{n} \left( \frac{d^2 \tilde{T}(x)}{d x^2} - \frac{2h}{\lambda r}(\tilde{T}(x) - T_{\infty}) \right)
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

Now the training plan is the following. We'll sample <span class="math display">$$ n $$</span> random locations 
from our domain, let's store them in a vector called `x_grid_random`. This will be our mini-batch of points at each epoch.

We'll evaluate the current PINN prediction on those points:

```python
T_pred = PINN_model(x_grid_random)
```

We'll compute the second derivative of the current prediction at those grid points:

```python
T_xx = d2Tdx2(T_pred, x_grid_random)
```

We'll assemble the residual (second derivative minus that whole linear term):

```python
residual = T_xx - k * (T_pred - T_infty)
```

And the loss will be the MSE between that residual and a vector of zeros (because we know it should be exactly zero):

```python
loss = mse(residual, torch.zeros_like(residual))
```

So let's follow this procedure and train our PINN model!

## Training

We define a function that, at each epoch, will sample <span class="math display">$$ n $$</span> locations on our rod where we will evaluate 
how good the current approximation to the ODE solution is. This essentially defines a randomized grid in <span class="math display">$$ x $$</span>. 
Notice that we use samples from a random uniform distribution (each location in <span class="math display">$$ x $$</span> is equally likely), 
between <span class="math display">$$ x=0 $$</span> and <span class="math display">$$ x=L $$</span>.

```python
def sample_x_grid(n_points):
    
    x = torch.rand(n_points, 1, dtype=dtype, device=device) * L
    x.requires_grad_(True)
    
    return x
```

We can specify how many random points from <span class="math display">$$ x $$</span> we will sample at each epoch:

```python
n_points_for_random_sample = 256
```

We specify a bunch of training parameters:

```python
epochs = 5000
print_every = 100
initial_learning_rate = 0.001
final_learning_rate = 0.0001
```

We specify the MSE loss function that will compare how far off we are from the zero residual:

```python
mse = nn.MSELoss()
```

We use the RMSprop optimizer:

```python
optimizer = torch.optim.RMSprop(PINN_model.parameters(), lr=initial_learning_rate)
```

Usually it's a good idea to decay the learning rate with training, so we define a learning rate decay scheduler:

```python
scheduler = torch.optim.lr_scheduler.CosineAnnealingLR(optimizer, 
                                                       T_max=epochs, 
                                                       eta_min=final_learning_rate)
```

And here's our training loop that follows the procedure I mentioned earlier!

```python
loss_across_epochs = []

for i in range(1, epochs + 1):

    optimizer.zero_grad()
    
    # We sample some points on the x-grid:
    x_grid_random = sample_x_grid(n_points_for_random_sample)
    
    # Current approximation to T(x):
    T_pred = PINN_model(x_grid_random)

    # Second derivative of T(x):
    T_xx = d2Tdx2(T_pred, x_grid_random)

    # Now we compute the residual form of the ODE, in an ideal case this should be exactly zero:
    residual = T_xx - k * (T_pred - T_infty)

    # We compare this residual with a tensor of zeros:
    loss = mse(residual, torch.zeros_like(residual))
    loss.backward()
    optimizer.step()
    scheduler.step()

    loss_across_epochs.append(loss.item())

    # Here, we check how well we're doing on all the constraints:
    if i % print_every == 0:
        
        with torch.no_grad():

            # Check the boundary values:
            x0 = torch.zeros(1, 1, dtype=dtype, device=device)
            xL = torch.full((1, 1), L, dtype=dtype, device=device)
            TL_hat = PINN_model(x0).item()
            TR_hat = PINN_model(xL).item()
            
        print(f"iter {i:5d} | per-sample residual loss {loss.item()/n_points_for_random_sample:.3e} | T(0)~{TL_hat:.3f} K, T(L)~{TR_hat:.3f} K")
```

## How did the PINN do compared to an analytic solution or a finite-difference method?

I computed an analytic solution to this ODE using Sympy 
and a finite-difference numerical solution using a second-order-accurate stencil.
Here's how the PINN approximation compares with those two:

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/PINNs-approximation.png" width="800">
</p>

It catches the trend but actually still leaves a lot to be improved! 🙂
Certainly a second-order-accurate finite difference stencil does much better than this!
But training parameters can still be tweaked. Feel free to play with the training parameters to see if you can do better than me!
