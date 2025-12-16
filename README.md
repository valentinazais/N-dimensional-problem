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

Math

1D: ∫₀¹∫₀¹|u-v|dudv = 1/3.
n-D: E[∑ᵢ(Xᵢ-Yᵢ)²] = n·Var(U)·2 = n/6 → E[distance] ≈ √(n/6).
Convergence: MC error ~1/√(1000) per dimension.

Example Output

D=1: ~0.33 (matches theory).
D=100: ~4.08 (vs. √(100/6)≈4.08).
D=1000: ~12.9 (vs. √(1000/6)≈12.9).
Plot: Linear-ish growth √n regime visible.

Use Cases

Curse of dimensionality demo.
Random sampling density (points spread as n↑).
Unit tests for high-D geometry algos.

Extend

Add theoretical √(n/6) overlay (plt.plot(dimensions, np.sqrt(np.array(dimensions)/6), '--', label='Theory')).
Vary distributions (Gaussian, exponential).
Compute variance/percentiles.
