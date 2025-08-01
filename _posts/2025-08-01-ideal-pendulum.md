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
a bunch of proof-of-concept research ideas. Below, I show solutions to an **undamped** and **damped** ideal pendulum
coded in Python. 

```python
import numpy as np
from scipy.integrate import solve_ivp
import matplotlib.pyplot as plt
```

The state vector for the ideal pendulum is composed of the angle, <span class="math display">$$ \theta(t) $$</span>, that the pendulum makes
with the vertical direction, and the angular velocity, <span class="math display">$$ \omega(t) $$</span>, 
both being functions of time, <span class="math display">$$ t $$</span>.

## Undamped pendulum

The system of ordinary differential equations (ODEs) that describes motion of an undamped ideal pendulum is as following:

<span class="math display">$$ \begin{equation}\begin{cases} \frac{d \theta(t)}{dt} = \omega(t) \\ \frac{d \omega(t)}{dt} = - \frac{g}{L} \sin(\theta(t)) \end{cases}\end{equation}$$</span>

where <span class="math display">$$ g $$</span> is the gravitational acceleration and <span class="math display">$$ L $$</span>
is the length of the pendulum.

We first define a function that generates the right-hand-side (RHS) vector for this system of ODEs:

```python
def undamped_pendulum(t, 
                      state_vector, 
                      g=9.8, 
                      L=1.0):

    θ, ω = state_vector
    
    return [ω, - g/L * np.sin(θ)]
```

Next, we create a generic function that will solve an initial value problem (IVP) given the time vector, the RHS vector,
the initial condition, <span class="math display">$$ \theta(t=0) = \theta_0 $$</span> and 
<span class="math display">$$ \omega(t=0) = \omega_0 $$</span>, and any other parameters:

```python
def generate_pendulum_trajectory(θ_0, 
                                 ω_0, 
                                 T=10.0, 
                                 n_points=200, 
                                 b=0.1, 
                                 g=9.8, 
                                 L=1.0, 
                                 damped=False,
                                 method='BDF'):

    time_vector = np.linspace(0, T, n_points)

    if damped:
        
        sol = solve_ivp(damped_pendulum,
                        [0, T],
                        [θ_0, ω_0],
                        method=method,
                        t_eval=time_vector,
                        args=(b,),
                        rtol=1e-9,
                        atol=1e-9)

    else:
        
        sol = solve_ivp(undamped_pendulum,
                        [0, T],
                        [θ_0, ω_0],
                        method=method,
                        t_eval=time_vector,
                        args=(g,L,),
                        rtol=1e-9,
                        atol=1e-9)
    
    return sol.t, sol.y.T
```

Now you can simply solve the undamped pendulum for a specific choice of parameters:

```python
time, trajectory = generate_pendulum_trajectory(θ_0=0.1, 
                                                ω_0=0.0, 
                                                T=20.0, 
                                                n_points=500, 
                                                b=0.1, 
                                                g=9.8, 
                                                L=9.8, 
                                                damped=False, 
                                                method='BDF')
```

To test my code, I create the figures below which are my reproductions of figures shown in section 1.2.3 in Prof. Scheinerman's textbook 
[*Invitation to Dynamical Systems*](https://github.com/scheinerman/InvitationToDynamicalSystems).
The parameters' values used in the textbook are <span class="math display">$$ g = 9.8 \frac{m}{s^2} $$</span> and 
<span class="math display">$$ L = 9.8 m $$</span> for simplicity.

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/ideal-pendulum-01.png" width="800">
</p>

> The motion of a pendulum with <span class="math display">$$ \theta_0 = 0.1 $$</span> and <span class="math display">$$ \omega_0 = 0.0 $$</span>.

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/ideal-pendulum-02.png" width="800">
</p>

> The motion of a pendulum with <span class="math display">$$ \theta_0 = 3.0 $$</span> and <span class="math display">$$ \omega_0 = 0.0 $$</span>.

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/ideal-pendulum-03.png" width="800">
</p>

> The motion of a pendulum with <span class="math display">$$ \theta_0 = 0.0 $$</span> and <span class="math display">$$ \omega_0 = 2.0 $$</span>. 
> Interestingly, here I wasn't quite able to get Prof. Scheinerman's figure and the solution strongly depends on the type of solver used (I've used BDF).

## Damped pendulum

The system of ordinary differential equations (ODEs) that describes motion of an undamped ideal pendulum is as following:

<span class="math display">$$ \begin{equation}\begin{cases} \frac{d \theta(t)}{dt} = \omega(t) \\ \frac{d \omega(t)}{dt} = - \frac{g}{L} \sin(\theta(t)) - b \cdot \omega(t) \end{cases}\end{equation}$$</span>

where <span class="math display">$$ b $$</span> is the damping parameter.

We define a function that generates the RHS vector for this system of ODEs:

```python
def damped_pendulum(t, 
                    state_vector, 
                    b=0.1, 
                    g=9.8, 
                    L=1.0):

    θ, ω = state_vector
    
    return [ω, - g/L * np.sin(θ) - b * ω]
```

And we solve it with the same function `generate_pendulum_trajectory()` as before:

```python
time, trajectory = generate_pendulum_trajectory(θ_0=3.0, 
                                                ω_0=0.0, 
                                                T=30.0, 
                                                n_points=500, 
                                                b=0.1, 
                                                g=9.8, 
                                                L=9.8, 
                                                damped=True, 
                                                method='BDF')
```

Here's one example of the trajectory of the damped pendulum, where you can observe the angle of the pendulum decaying with time:

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/ideal-pendulum-damped-01.png" width="800">
</p>

> The motion of a damped pendulum with <span class="math display">$$ \theta_0 = 3.0 $$</span> and <span class="math display">$$ \omega_0 = 0.0 $$</span>.
