# n-Dimensional Hypercube Distance Simulator

Monte Carlo simulation: average Euclidean distance between two random points in [0,1]^n hypercube. Validates E[||P₁-P₂||] ~ √(n/6) asymptotic for n→∞. Plots 1D→1000D.

## Overview
- **1D case**: E[|U₁-U₂|] = 1/3 (uniform [0,1]).
- **n-D case**: E[||P₁-P₂||] where P₁,P₂ ∈ [0,1]^n, ||·|| = L2 norm.
- **Asymptotic**: Distance grows as √(n/6) for large n (theoretical).
- **Output**: Static plot (distance vs. dimensions 1-1000).

## Code Structure
1. `average_absolute_difference_1d(n_samples)`: 1D baseline (mean ~0, |·| mean ~0.33).
2. `average_euclidean_distance_nd(n_dim, n_samples)`: Generate n_samples point pairs in [0,1]^n_dim → compute ||P₁-P₂|| → average.
3. Loop: Dimensions 1→1000 (1000 samples each) → store avg distance.
4. Plot: Blue line (MC estimate), grid overlay.

## Run
```bash
pip install numpy matplotlib
python hypercube_distance.py
