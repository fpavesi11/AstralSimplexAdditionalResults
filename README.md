# Reaching the Boundary: Astral Spaces for Riemannian Optimization over the Probability Simplex

**Federico Pavesi¹, Noémie Jaquier², Antonio Candelieri¹**

¹ Department of Economics, Management and Statistics (DEMS), University of Milano-Bicocca, Milan, Italy

² Department of Robotics, Perception and Learning (RPL), KTH Royal Institute of Technology, Stockholm, Sweden

---

## Introduction & Motivation

Optimizing over probability distributions naturally leads to the probability simplex

[
\Delta^d = \left{\mathbf p \in \mathbb R^{d+1}_{\ge 0} ;\middle|; \mathbf p^\top \mathbf 1 = 1 \right},
]

which appears in numerous applications, including Bayesian optimization, robotics, experimental design, and mixture modelling.

Under the (\alpha=-1) information geometry, optimization can be performed in an unconstrained manner within tangent spaces. However, the corresponding exponential map approaches the boundary of the simplex only asymptotically. Consequently, solutions located on the boundary cannot be reached in finite time, creating practical limitations for optimization algorithms.

To address this issue, we leverage the theory of **astral spaces** and construct a continuous extension of the geometry to the closed simplex, enabling optimization directly on boundary points.

---

## Main Contributions

* Extension of the (\alpha=-1) information geometry from the interior of the probability simplex to the **closed simplex**, including all boundary strata.

* Proof that the astral compactification of the tangent space is **well-defined and continuous**.

* Derivation of an **extended exponential map** that remains valid on the boundary.

* Introduction of **Astral Riemannian Optimization** and **Astral (\alpha)-GaBO**.

---

## Information Geometry at (\alpha=-1)

The main geometric objects associated with the exponential geometry are the following.

### Probability Simplex

[
\Delta^d
========

\left{
\mathbf p \in \mathbb R^{d+1}_{\ge 0}
;\middle|;
\mathbf p^\top \mathbf 1 = 1
\right}.
]

### Tangent Space

[
\mathcal T_{\mathbf p}\Delta^d
==============================

\left{
\mathbf v \in \mathbb R^{d+1}
;\middle|;
\mathbf v^\top \mathbf p = 0
\right}
\cong \mathbb R^d.
]

### Fisher–Rao Metric

[
\langle \mathbf v,\mathbf u\rangle_{\mathbf p}
==============================================

\sum_{i=1}^{d+1}
p_i,v_i,u_i.
]

### Natural Gradient

[
\operatorname{grad}_{\mathbf p}F
================================

## DF(\mathbf p)

\mathbf p^\top [DF(\mathbf p)].
]

### (\alpha=-1) Connection

[
\nabla^{(-1)}_{\mathbf U}\mathbf V(\mathbf p)
=============================================

\Bigl(
\mathbf p,,
D^2_{\mathbf U}\mathbf V(\mathbf p)
+
\mathbf p^\top
\bigl[
\mathbf U(\mathbf p)\mathbf V(\mathbf p)
\bigr]
\Bigr).
]

### Exponential Map

[
\operatorname{Exp}^{(-1)}_{\mathbf p}(\mathbf u)
================================================

\frac{\exp(\mathbf u)}
{\mathbf p^\top \exp(\mathbf u)}
,\mathbf p.
]

---

## Astral Extension of the Tangent Space

The component-wise structure of the exponential family permits a tractable astral compactification of tangent spaces.

### Interior Points

For (\mathbf p \in \operatorname{int}(\Delta^d)),

[
\overline{\mathcal T_{\mathbf p}\Delta^d}
\cong
\prod_{i=1}^{d+1}
\overline{\mathbb R}.
]

### Boundary Points

Suppose (\mathbf p) belongs to a face of dimension (d-k), meaning that (k) coordinates vanish. Then

[
\overline{\mathcal T_{\mathbf p}\Delta^d}
\cong
\left(
\prod_{i=1}^{d-k+1}
\overline{\mathbb R}
\right)
\times
\left(
\prod_{j=1}^{k}
[-\infty,0]
\right).
]

### Extended Exponential Map

The exponential map admits the extension

[
\overline{\operatorname{Exp}}^{(-1)}_{\mathbf p}(\mathbf u)
===========================================================

\frac{\overline{\exp}(\mathbf u)}
{\mathbf p^\top \overline{\exp}(\mathbf u)}
,\mathbf p,
]

where (\overline{\exp}) denotes the astral extension of the exponential function satisfying

[
\overline{\exp}(-\infty)=0.
]

---

## Theoretical Results

### Theorem 1 (Well-definedness of the Compactification)

The compactified tangent space

[
\overline{\mathcal T_{\mathbf p}\Delta^d}
]

is a well-defined astral extension of the tangent space
(\mathcal T_{\mathbf p}\Delta^d).

#### Proof

The tangent space is characterized by the linear constraint

[
\mathcal T_{\mathbf p}\Delta^d
==============================

\left{
\mathbf u \in \mathbb R^{d+1}
;\middle|;
\mathbf p^\top \mathbf u = 0
\right}.
]

Consider the linear functional

[
L(\mathbf u)=\mathbf p^\top \mathbf u.
]

Since (L) is linear, it is convex and continuous. By Theorem 7.4 of Dudík, Schapire, and Telgarsky (2025), every continuous convex function admits a unique continuous astral extension. Consequently, the defining constraint of the tangent space extends uniquely to the astral compactification, yielding a well-defined compactified tangent space

[
\overline{\mathcal T_{\mathbf p}\Delta^d}.
]

Therefore, the astral compactification exists and is continuous. (\square)

---

### Theorem 2 (Extension of the Exponential Map)

The map

[
\overline{\operatorname{Exp}}^{(-1)}_{\mathbf p}(\mathbf u)
===========================================================

\frac{\overline{\exp}(\mathbf u)}
{\mathbf p^\top \overline{\exp}(\mathbf u)}
,\mathbf p
]

is the unique continuous extension of the (\alpha=-1) exponential map to the closed probability simplex.

#### Proof

For each coordinate (i),

[
\Bigl(
\overline{\operatorname{Exp}}^{(-1)}_{\mathbf p}(\mathbf u)
\Bigr)_i
========

\frac{
\overline{\exp}(u_i),p_i
}{
\mathbf p^\top
\overline{\exp}(\mathbf u)
}.
]

The astral exponential function (\overline{\exp}) is continuous, convex, and non-decreasing on (\overline{\mathbb R}). The denominator

[
\mathbf p^\top \overline{\exp}(\mathbf u)
]

is a positive continuous function whenever (\mathbf p\in\Delta^d), ensuring that each coordinate function is well defined.

Moreover, each component is obtained through composition and normalization of continuous convex monotone functions. By Proposition 10.14 of Dudík, Schapire, and Telgarsky (2025), such functions admit continuous astral extensions. Hence every coordinate of the exponential map extends continuously to the compactified tangent space.

Since continuity holds component-wise and the extension coincides with the classical exponential map on the interior, the resulting map is the unique continuous extension to the closed simplex. (\square)

---

## Astral Riemannian Optimization

The proposed optimization procedure consists of the following steps:

1. Start from the current iterate (x_t).
2. Compute the Riemannian gradient in the astral tangent space.
3. Retract using the extended exponential map.
4. Obtain the next iterate (x_{t+1}).
5. Repeat until convergence.

The key difference from standard Riemannian optimization is the replacement of the classical retraction by the extended exponential map, allowing iterates to reach boundary points.

---

## Astral (\alpha)-GaBO

Astral (\alpha)-GaBO integrates the astral optimization procedure into the (\alpha)-GaBO Bayesian optimization framework.

The iterative procedure is:

1. Fit a Gaussian process surrogate.
2. Construct the acquisition function.
3. Optimize the acquisition function using Astral Riemannian Optimization.
4. Evaluate the objective.
5. Update the dataset and repeat.

This modification enables Bayesian optimization to identify optima located on the boundary of the simplex.

---

## Experimental Results

The proposed framework was evaluated on optimization problems whose global optimum lies on the boundary of the simplex.

### Convex Optimization

Differentiable convex functions defined on (\Delta^d) were optimized using Astral Riemannian Gradient Descent.

Astral optimization converged substantially faster than the constrained Euclidean baseline based on projected gradient descent.

**Figure:** `all_dimensions.png`

*Riemannian Astral vs. Euclidean constrained optimization. Objective: Euclidean distance raised to the power (3/10). Dimensions (d=5,10,20). Lower values are better.*

---

### Black-Box Optimization: Astral (\alpha)-GaBO

Non-convex benchmark functions were optimized using Bayesian optimization.

Astral (\alpha)-GaBO consistently identified boundary optima and outperformed the Euclidean baseline.

**Figures**

* `Ackley_all_dims.png`
* `Rosenbrock_all_dims.png`

*Convergence curves (median, 25th percentile, and 75th percentile over 25 independent runs) comparing Astral (\alpha)-GaBO with a standard Euclidean baseline on Ackley and Rosenbrock benchmark functions. Lower values are better.*

---

## Additional Results and Contact

### Federico Pavesi

[f.pavesi11@campus.unimib.it](mailto:f.pavesi11@campus.unimib.it)

### Noémie Jaquier

[jaquier@kth.se](mailto:jaquier@kth.se)

### Antonio Candelieri

[antonio.candelieri@unimib.it](mailto:antonio.candelieri@unimib.it)

Additional experimental results are available through the QR code distributed with the poster.

---

## References

1. Dudík, M., Schapire, R. E., and Telgarsky, M. (2025). *Astral Space: Convex Analysis at Infinity*. arXiv:2205.03260.

2. Pavesi, F., Candelieri, A., and Jaquier, N. (2026). *Information Theoretic Bayesian Optimization over the Probability Simplex*. Proceedings of the 42nd Conference on Uncertainty in Artificial Intelligence (UAI 2026), available as arXiv:2603.09793.

