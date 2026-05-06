# Python ML Foundations

Pure-Python implementations and derivations of core building blocks behind machine
learning — written without NumPy, scikit-learn, or any other numerical framework.
Every module relies only on the Python standard library (and `matplotlib` for plots),
so every linear algebra step, derivative, and probabilistic sample is visible in code.

## Modules

| Module | Topic |
|---|---|
| [`forward_pass/`](forward_pass/) | Two-layer MLP forward pass with ReLU activation, derived step by step |
| [`gradient_optimization/`](gradient_optimization/) | Partial derivatives and a closed-form minimum of a quadratic objective |
| [`hyperplane_distance/`](hyperplane_distance/) | Distance from a point to a hyperplane via Lagrangian projection |
| [`convexity/`](convexity/) | Convexity proofs for `x^2`, the negative log, and an LSE-style function |
| [`biased_coin/`](biased_coin/) | Monte Carlo simulation of a biased Bernoulli process and longest-run statistics |
| [`uniform_sum_clt/`](uniform_sum_clt/) | Empirical demonstration of the central limit theorem on sums of uniform RVs |

## Running the notebooks

```bash
pip install matplotlib jupyter
jupyter notebook
```

The simulation modules (`biased_coin/`, `uniform_sum_clt/`) ship as Jupyter notebooks
with the produced figures committed alongside. The four math modules
(`forward_pass/`, `gradient_optimization/`, `hyperplane_distance/`, `convexity/`)
are written-out derivations in `solution.md`.

## Why no NumPy?

The point is to keep the math in plain sight. Matrix-vector products are spelled
out as nested loops, gradient steps are written as scalar arithmetic, and
sampling is done with `random.random()`. Once the mechanics are clear, swapping
in a numerical library is the small step.
