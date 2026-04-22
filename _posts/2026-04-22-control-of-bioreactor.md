---
layout: default
title:  "Control of a bioreactor using reinforcement learning"
date:   2026-04-22 10:00:00 +0100
categories: jekyll update
---

<script type="text/javascript" async="" src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.4/MathJax.js?config=TeX-MML-AM_CHTML">
</script>

<p>
   <a href="/kamilazdybal.github.io/#blog">
      < Go back
  </a>
</p>

# Control of a bioreactor using reinforcement learning

## Zero-dimensional model of a bioreactor

A bioreactor is a dynamical system that can be modeled as a zero-dimensional reactor of volume <span class="math display">$$ V $$</span> 
where biomass is produced from a substrate.
The substrate is continually added to the bioreactor at the rate <span class="math display">$$ F $$</span>, and the products 
of the bioreactor are expelled at the same rate, thus maintaining a constant volume in the reactor.

The system of initial value ordinary differential equations (ODEs) that describes this process can be written as:

<span class="math display">$$
\begin{equation}
    \begin{cases}
      \frac{d X}{d t} = \left( \mu(S) - D \right) X \\
      \frac{d S}{d t} = D \left( S_{\text{in}} - S \right) - \frac{\mu(S)}{Y_d} X
    \end{cases}
\end{equation}$$</span>

with the initial conditions

<span class="math display">$$
\begin{equation}
    \begin{cases}
        X(t = 0) = X_0 \\
        S(t = 0) = S_0
    \end{cases}
\end{equation}$$</span>

and where
<span class="math display">$$ X $$</span> is the biomass concentration in <span class="math display">$$ g/L $$</span>,
<span class="math display">$$ S $$</span> is the substrate concentration in <span class="math display">$$ g/L $$</span>,
<span class="math display">$$ S_{\text{in}} $$</span> is the substrate concentration in the feed in <span class="math display">$$ g/L $$</span>,
<span class="math display">$$ D = F / V $$</span> is the dilution rate in <span class="math display">$$ 1/h $$</span>,
<span class="math display">$$ \mu(S) $$</span> is the biomass growth rate in <span class="math display">$$ 1/h $$</span>,
and 
<span class="math display">$$ Y_d $$</span> is the yield coefficient specifying how much biomass can be obtained 
from the unit mass of substrate.

The biomass growth rate is often modeled using Monod kinetics:

<span class="math display">$$ \begin{equation}
\mu(S) = \mu_{\text{max}} \frac{S}{K_S + S}
\end{equation}$$</span>

where
<span class="math display">$$ \mu_{\text{max}} $$</span> is the maximum growth rate in <span class="math display">$$ 1/h $$</span> and
<span class="math display">$$ K_S $$</span> is the half-saturation constant in <span class="math display">$$ g/L $$</span>.

For more realism, we may also model gradual decay of biomass if substrate is not continuously provided. With the current
ODE model, <span class="math display">$$ X $$</span> stays constant once <span class="math display">$$ D \rightarrow 0 $$</span> 
and <span class="math display">$$ S \rightarrow 0 $$</span>. Realistically, without new substrate, biomass eventually
starves. This can be modeled by adding an additional decay term, <span class="math display">$$ k_d $$</span>, in 
the first ODE:

<span class="math display">$$
\begin{equation}
\frac{d X}{d t} = \left( \mu(S) - D - k_d \right) X
\end{equation}$$</span>

## Control of a bioreactor

This dynamical system is controlled by establishing the right inflow rate, <span class="math display">$$ F $$</span>,
such that we maximize the rate of biomass expelled from the reactor <span class="math display">$$ D X $$</span>, also known as the reactor's productivity. 
Note that too low <span class="math display">$$ F $$</span> will hamper the growth of biomass with too little
nutrients provided and equally small biomass output. But too high <span class="math display">$$ F $$</span> can lead
to reactor washout, _i.e._, too fast removal of biomass from the reactor.

## REINFORCE model for bioreactor control










## Response to random perturbations



