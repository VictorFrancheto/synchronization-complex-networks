# Synchronization in Complex Networks

<p align="center">
  <img src="https://github.com/VictorFrancheto/Synchronization_Complex_Networks/blob/main/network.jpg">
</p>

> A computational study of how network topology influences synchronization phenomena, using the Kuramoto model as the theoretical framework.

---

## Overview

This repository investigates how the structural properties of complex networks — such as community structure, degree distribution, and rewiring probability — affect the collective synchronization of coupled oscillators. The analysis is grounded in the **Kuramoto model**, one of the most studied models in nonlinear dynamics.

The central question addressed is:

> **How is synchronization influenced by network topology?**

---

## Theoretical Background

### Kuramoto Model

The Kuramoto model, proposed by Yoshiki Kuramoto in the 1970s, describes a population of $N$ coupled oscillators whose dynamics evolve according to:

$$\dot{\theta}_i = \omega_i + \lambda \sum_{j=1}^{N} A_{ij} \sin(\theta_j - \theta_i), \quad i = 1, \ldots, N$$

where:
- $\theta_i$ is the phase of oscillator $i$
- $\omega_i$ is its natural frequency (drawn from a distribution $g(\omega)$)
- $\lambda$ is the global coupling strength
- $A_{ij}$ is the adjacency matrix of the network

### Order Parameter

The degree of synchronization is measured by the **order parameter** $r(t)$:

$$r(t) e^{i\psi(t)} = \frac{1}{N} \sum_{j=1}^{N} e^{i\theta_j(t)}$$

- $r \approx 0$: incoherent (desynchronized) state  
- $r \approx 1$: fully synchronized state  

The **critical coupling** $\lambda_c$ marks the transition between these two regimes.

---

## Network Models Studied

| Network | Model |
|---|---|
| Random with communities | Random Partition Graph |
| Random with communities | Stochastic Block Model (SBM) |
| Random with communities | LFR Benchmark (varying $\mu$) |
| Hierarchical | $k$-regular graph |
| Random | Erdős-Rényi |
| Scale-free | Barabási-Albert |
| Scale-free (nonlinear) | Nonlinear Barabási-Albert (varying $\alpha$) |
| Small-world | Watts-Strogatz |
| Spatial | Waxman |

---

## Key Findings

### Networks with Community Structure
Networks with well-defined communities tend to synchronize at similar critical coupling values $\lambda_c$. Strong intra-community connectivity promotes local synchronization, which then spreads globally through inter-community links.

### Effect of the LFR Mixing Parameter $\mu$
The mixing parameter $\mu$ controls the fraction of inter-community edges. As $\mu$ increases, community boundaries dissolve, and $\lambda_c$ **decreases** — networks with weaker community structure synchronize more easily. This relationship follows a power law on log-log axes.

### Networks without Community Structure
Topology still plays a key role:
- **Erdős-Rényi**: homogeneous degree distribution leads to predictable synchronization
- **Barabási-Albert**: hubs facilitate synchronization at lower $\lambda_c$
- **Nonlinear BA** (varying $\alpha$): preferential attachment nonlinearity tunes the hub effect
- **Watts-Strogatz**: the small-world property (short path lengths + high clustering) strongly reduces $\lambda_c$

---

## Repository Structure

```
├── syncronization-complex-networks.ipynb   # Main notebook with full analysis
├── network.jpg                             # Reference network image
└── README.md
```

---

## References

- Kuramoto, Y. (1984). *Chemical Oscillations, Waves, and Turbulence*. Springer.
- Arenas, A., Díaz-Guilera, A., Kurths, J., Moreno, Y., & Zhou, C. (2008). [Synchronization in complex networks](https://www.sciencedirect.com/science/article/pii/S0370157308003384). *Physics Reports*, 469(3), 93–153.
- Lancichinetti, A., Fortunato, S., & Radicchi, F. (2008). Benchmark graphs for testing community detection algorithms. *Physical Review E*.
- Watts, D. J., & Strogatz, S. H. (1998). Collective dynamics of 'small-world' networks. *Nature*, 393, 440–442.
- Barabási, A.-L., & Albert, R. (1999). Emergence of scaling in random networks. *Science*, 286, 509–512.
- `kuramoto` Python library: [fabridamicelli/kuramoto](https://github.com/fabridamicelli/kuramoto)

