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

A bioreactor is a dynamical system that can be modeled as a zero-dimensional, perfectly stirred reactor
where biomass is produced from a substrate.
The substrate is continually added to the bioreactor at the rate <span class="math display">$$ F $$</span> 
(in <span class="math display">$$ L/h $$</span>), and the products 
of the bioreactor are expelled at the same rate, thus maintaining a constant volume, <span class="math display">$$ V $$</span>, in the reactor.

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/bioreactor-control-bioreactor.png" width="300">
</p>

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

The biomass growth rate is often modeled using the Monod's model [[1](https://www.sciencedirect.com/science/article/abs/pii/0923046794870349)]:

<span class="math display">$$ \begin{equation}
\mu(S) = \mu_{\text{max}} \frac{S}{K_S + S}
\end{equation}$$</span>

where
<span class="math display">$$ \mu_{\text{max}} $$</span> is the maximum growth rate in <span class="math display">$$ 1/h $$</span> and
<span class="math display">$$ K_S $$</span> is the half-saturation constant in <span class="math display">$$ g/L $$</span>.

For more realism, we may also model gradual decay of biomass if substrate is not continually provided. With the current
ODE model, <span class="math display">$$ X $$</span> stays constant once <span class="math display">$$ D \rightarrow 0 $$</span> 
and <span class="math display">$$ S \rightarrow 0 $$</span>. Realistically, without new substrate biomass eventually
starves. This can be modeled by an additional decay term, <span class="math display">$$ k_d $$</span>, in 
the first ODE:

<span class="math display">$$
\begin{equation}
\frac{d X}{d t} = \left( \mu(S) - D - k_d \right) X
\end{equation}$$</span>

## Bioreactor parameters

We are going to use the following parameters for the bioreactor:

| Parameter                                                | Value                                                  |
|----------------------------------------------------------|--------------------------------------------------------|
| <span class="math display">$$ \mu_{\text{max}} $$</span> | <span class="math display">$$ 0.4 \,\, 1/h $$</span>   |
| <span class="math display">$$ K_S $$</span>              | <span class="math display">$$ 0.1 \,\, g/L $$</span>   |
| <span class="math display">$$ S_{\text{in}} $$</span>    | <span class="math display">$$ 10.0 \,\, g/L $$</span>  |
| <span class="math display">$$ k_d $$</span>              | <span class="math display">$$ 0.01 \,\, 1/h $$</span>  |
| <span class="math display">$$ Y_d $$</span>              | <span class="math display">$$ 0.5 \,\, gX/gS $$</span> |
| Max. <span class="math display">$$ X $$</span>           | <span class="math display">$$ 10.0 \,\, g/L $$</span>  |
| Max. <span class="math display">$$ S $$</span>           | <span class="math display">$$ 20.0 \,\, g/L $$</span>  |

## Control action

This dynamical system is controlled by establishing the right dilution rate, <span class="math display">$$ D $$</span>,
such that we maximize the rate of biomass expelled from the reactor, <span class="math display">$$ D X $$</span>, also known as the reactor's productivity. 
Note that too low <span class="math display">$$ D $$</span> will hamper the growth of biomass with too little
nutrients provided and equally small biomass output. But too high <span class="math display">$$ D $$</span> can lead
to reactor washout, _i.e._, complete removal of biomass from the reactor with time.

Below, we visualize a couple of scenarios starting from initial condition 

<span class="math display">$$
\begin{equation}
    \begin{cases}
        X(t = 0) = 1.0 \frac{g}{L} \\
        S(t = 0) = 5.0 \frac{g}{L}
    \end{cases}
\end{equation}$$</span>

### Good control

First, a good control case where dilution rate is not too low and not too high. With just
the right amount of substrate continually supplied to the reactor the biomass concentration establishes a steady state at some high value.

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/bioreactor-control-good.png" width="800">
</p>

### Zero dilution rate

Second, zero dilution rate causes the biomass to gradually decay due to starvation.

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/bioreactor-control-zero.png" width="800">
</p>

### High dilution rate

Third, too high dilution rate causes washout, where at some point in time the biomass is completely removed from the bioreactor and
its production cannot be restored.

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/bioreactor-control-washout.png" width="800">
</p>

## Setting up reinforcement learning training

We are going to use the following training parameters:

| Parameter                                                       | Value                                                   |
|-----------------------------------------------------------------|---------------------------------------------------------|
| Optimizer                                                       | Adam                                                    |
| Initial <span class="math display">$$ \alpha $$</span>          | <span class="math display">$$ 1 \cdot 10^{-4} $$</span> |
| Final <span class="math display">$$ \alpha $$</span>            | <span class="math display">$$ 1 \cdot 10^{-5} $$</span> |
| <span class="math display">$$ \alpha $$</span> decay            | Cosine                                                  |
| Discount factor, <span class="math display">$$ \gamma $$</span> | <span class="math display">$$ 0.99 $$</span>            |
| Policy network architecture                                     | in-64-64-out                                            |
| Activation function                                             | ReLU                                                    |
| Number of episodes                                              | 2000                                                    |
| Random seed                                                     | 100                                                     |

The state is determined by five values that are inputs to the policy network:

- The current <span class="math display">$$ X $$</span>
- The current <span class="math display">$$ S $$</span>
- The difference between the current and previous <span class="math display">$$ X $$</span>, <span class="math display">$$ \Delta X $$</span>
- The difference between the current and previous <span class="math display">$$ S $$</span>, <span class="math display">$$ \Delta S $$</span>
- The previous action, <span class="math display">$$ D_{\text{prev}} $$</span>

The continuous action is the value for <span class="math display">$$ D $$</span> which we assume bounded between 
<span class="math display">$$ 0.0 \,\, 1/h $$</span> and <span class="math display">$$ 1.0 \,\, 1/h $$</span>. This
is the output of the policy network.

The reward is computed as <span class="math display">$$ D \cdot X $$</span>.

We assume that washout occurs if <span class="math display">$$ X $$</span> drops below <span class="math display">$$ 10^{-3} g/L $$</span>
and is penalized with an additional <span class="math display">$$ -10.0 $$</span> reward.

## REINFORCE model for bioreactor control

We are using the REINFORCE [[2]()] agent from TF-Agents [[3]()]:

```python
agent = reinforce_agent.ReinforceAgent(time_step_spec=train_env.time_step_spec(),
                                       action_spec=train_env.action_spec(),
                                       actor_network=actor_net,
                                       optimizer=agent_optimizer,
                                       train_step_counter=train_step_counter, 
                                       gamma=discount_factor, 
                                       normalize_returns=True, 
                                       entropy_regularization=None)
```

where the policy network is a fully-connected dense neural network:

```python
actor_net = actor_distribution_network.ActorDistributionNetwork(
    input_tensor_spec=train_env.observation_spec(),
    output_tensor_spec=train_env.action_spec(),
    fc_layer_params=(64, 64),
    activation_fn=tf.keras.activations.relu,
    kernel_initializer=tf.keras.initializers.GlorotUniform(seed=random_seed),
    seed=random_seed,
)
```

Below, we show how the average per-step reward develops during the 2000 training episodes. Note that the 
theoretical maximum instantaneous reward is <span class="math display">$$ D_{\text{max}} \cdot X_{\text{max}} = 1 \,\, 1/h \cdot 10.0 \,\, g/L = 10.0 \frac{g}{Lh} $$</span>,
but in practice, this may not lead to the optimal operating conditions of the bioreactor 
as maintaining the highest possible <span class="math display">$$ D $$</span> may lead to reactor washout.
What the highest optimal <span class="math display">$$ D \cdot X $$</span> is determined by the reactor's parameters.
For example, a higher yield may allow for higher <span class="math display">$$ D $$</span> as more biomass is
produced from the substrate at any instance in time and washout is less likely.

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/bioreactor-control-average-per-step-reward.png" width="800">
</p>

### Comparison with a constant action

Post training, we compare the RL control with a constant action, <span class="math display">$$ D = \text{const} $$</span>.
We find the best possible constant action that leads to the highest cumulative <span class="math display">$$ D \cdot X $$</span>, which
seems to be at <span class="math display">$$ D \approx 0.3 \,\, 1/h $$</span>. 
The nonlinear RL control slightly outperforms this constant action for this initial condition:

<span class="math display">$$
\begin{equation}
    \begin{cases}
        X(t = 0) = 1.0 \frac{g}{L} \\
        S(t = 0) = 2.0 \frac{g}{L}
    \end{cases}
\end{equation}$$</span>

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/bioreactor-control-comparison-with-constant-action.png" width="800">
</p>

Note that if the constant action matched the steady-state value of the RL control action, it would lead to a much worse
outcome:

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/bioreactor-control-comparison-with-constant-action-higher.png" width="800">
</p>

### Challenging initial condition

Let's also start the bioreactor at a challenging initial condition that is close to washout:

<span class="math display">$$
\begin{equation}
    \begin{cases}
        X(t = 0) = 0.002 \frac{g}{L} \\
        S(t = 0) = 0.0 \frac{g}{L}
    \end{cases}
\end{equation}$$</span>

This time, the best constant action has to be decreased to <span class="math display">$$ D \approx 0.15 \,\, 1/h $$</span>.
The RL control first decreases <span class="math display">$$ D $$</span> in order to prevent washout, and
starts to increase <span class="math display">$$ D $$</span> only after sufficient amount of biomass is accumulated in 
the bioreactor.

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/bioreactor-control-comparison-close-to-washout.png" width="800">
</p>

### Response to perturbations

Finally, let's introduce some perturbation in the reactor to see how the RL agent responds. We are going to suddenly
drop <span class="math display">$$ X $$</span> in the reactor by <span class="math display">$$ 3.0 g/L $$</span>.
The RL agent chooses to decrease <span class="math display">$$ D $$</span> for a while after this event most
likely to avoid potential washout. However, there is a better constant action that leads to higher
cumulative productivity at <span class="math display">$$ D \approx 0.3 \,\, 1/h $$</span>. 
There is room to improve the RL training 🙂 

<p align="center">
  <img src="https://github.com/kamilazdybal/kamilazdybal.github.io/raw/main/_posts/bioreactor-control-with-perturbation.png" width="800">
</p>
