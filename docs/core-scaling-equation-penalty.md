# The Core Scaling Equation Penalty

When one resource axis is held completely constant (e.g., dataset size $D$ is fixed), scaling the other axes yields severely diminishing returns, asymptotically bounded by a scaling penalty.

## Concept Overview
The joint scaling law equation modeling parameters ($N$) and dataset size ($D$) is:

$$L(N, D) \approx \left(\frac{N_c}{N}\right)^{\alpha_N} + \left(\frac{D_c}{D}\right)^{\alpha_D}$$

Where:
- $N_c, D_c$ are constant scaling factors.
- $\alpha_N, \alpha_D$ are scaling exponents.

If dataset size $D$ is fixed, even if parameters $N \to \infty$, the loss is bounded by:

$$\lim_{N \to \infty} L(N, D) = \left(\frac{D_c}{D}\right)^{\alpha_D}$$

This is the scaling penalty ceiling. You cannot bypass dataset limitations purely by making the model larger.

```mermaid
graph TD
    subgraph Data Constraint Asymptote
        FixedD[Fixed Dataset Size D] -->|Loss Bound| Limit[L_min = (D_c/D)^alpha_D]
        N[Scale Parameters N -> Infinity] -->|Approaches| Limit
    end
```

## Key Paper Citations
- **Original Foundation:**
  - [Jared Kaplan et al., 2020: "Scaling Laws for Neural Language Models"](https://arxiv.org/abs/2001.08361) — Formulated the joint scaling law equations and the concept of fixed-dataset performance limits.
- **Refinement:**
  - [Jordan Hoffmann et al., 2022: "Training Compute-Optimal Large Language Models"](https://arxiv.org/abs/2203.15556) — Refined the joint loss formulation to $L(N,D) = E + \frac{A}{N^\alpha} + \frac{B}{D^\beta}$ where $E$ represents the irreducible entropy of natural language.

---
[← Back to README](../README.md)
