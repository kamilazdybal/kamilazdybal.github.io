---
layout: default
title:  "Bioreactor control"
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

A bioreactor can be modeled as a zero-dimensional reactor of volume <span class="math display">$$ V $$</span> 
where biomass is produced from a substrate.
The substrate is continually added to the bioreactor at the rate <span class="math display">$$ F $$</span>, and the products 
of the bioreactor are expelled at the same rate.

The system of initial value ordinary differential equations that describes this process can be written like so:

<span class="math display">$$ \begin{equation}
\frac{d X}{d t} = (\mu(S) - D) X
\end{equation}$$</span>

<span class="math display">$$ \begin{equation}
\frac{d S}{d t} = D (S_{\text{in}} - S) - \frac{\mu(S)}{Y_d} X
\end{equation}$$</span>

where
<span class="math display">$$ X $$</span> is the biomass concentration in <span class="math display">$$ g/L $$</span>,
<span class="math display">$$ S $$</span> is the substrate concentration in <span class="math display">$$ g/L $$</span>,
<span class="math display">$$ S_{\text{in}} $$</span> is the substrate concentration in the feed <span class="math display">$$ g/L $$</span>,
<span class="math display">$$ D = F / V $$</span> is the dilution rate in <span class="math display">$$ 1/h $$</span>,
<span class="math display">$$ \mu(S) $$</span> is the biomass growth rate in <span class="math display">$$ 1/h $$</span>,
and 
<span class="math display">$$ Y_d $$</span> is the yield coefficient specifying how many <span class="math display">$$ g $$</span>
of biomass can be obtained from the unity mass of substrate.

The biomass growth rate is often modeled using Monod kinetics:

<span class="math display">$$ \begin{equation}
\mu(S) = \mu_{\text{max}} \frac{S}{K_S + S}
\end{equation}$$</span>

where
<span class="math display">$$ \mu_{\text{max}} $$</span> is the maximum growth rate and
<span class="math display">$$ K_S $$</span> is the half-saturation constant in <span class="math display">$$ g/L $$</span>.

## REINFORCE model for bioreactor control













