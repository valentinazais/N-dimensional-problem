# Curse of Dimensionality: Hypercube Distances

Monte Carlo: Average Euclidean distance E[||P1-P2||_2] between uniform [0,1]^n points. Explodes ~√(n/6) → distances saturate hypercube diameter despite "volume normalization".

## Overview
- **1D**: E[|U1-U2|]=1/3 (analytic baseline).
- **nD**: Sample pairs → np.linalg.norm → mean (1000 samples/dim).
- **Dims**: 1-1000 → plot shows linear √n growth.
- Reveals: High-D points "far apart" → sparsity/curse.

## Code
```python
def average_euclidean_distance_nd(n_dim, n_samples=1000):
    point1 = np.random.uniform(0, 1, (n_samples, n_dim))
    point2 = np.random.uniform(0, 1, (n_samples, n_dim))
    return np.mean(np.linalg.norm(point1 - point2, axis=1))
Loop dims → plot.
Fast: ~1s for 1000 dims.
Parametric: Tweak n_samples, dimensions.

Files

curse_dim.ipynb: Self-contained Jupyter (np/matplotlib).

Run
pip install numpy matplotlib jupyter
jupyter notebook curse_dim.ipynb
→ Interactive plot.
Output
1D: {'avg_abs_diff': ~0.333, ...}
Plot: Rising curve (MC), grid/log optional.
![Plot](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAkkAAAHFCAYAAADmGm0K... [from notebook])
(Avg dist vs dim: flat low-D → √n explosion)
