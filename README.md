# Reaching the Boundary: Astral Spaces for Riemannian Optimization over the Probability Simplex

**Federico Pavesi**, **Noémie Jaquier**, **Antonio Candelieri**

## Introduction

Optimizing over probability distributions naturally leads to the probability simplex

$$
\Delta^d = \{\mathbf{p} \in \mathbb R_{\ge 0}^{d+1} | \mathbf{p}^\top \mathbf 1 = 1\},
$$

which appears in Bayesian optimization, robotics, experimental design, and mixture modelling.

Under the $\alpha=-1$ information geometry, optimization becomes unconstrained in the tangent space. However, the standard exponential map approaches the simplex boundary only asymptotically, making boundary solutions practically unreachable.

We address this limitation using the theory of **astral spaces**, extending the geometry continuously to the closed simplex and enabling optimization directly on the boundary.

---

## Main Contributions

- Extension of the $\alpha=-1$ information geometry to the **closed simplex**.
- Proof that the astral compactification of the tangent space is **well-defined and continuous**.
- Construction of an extended exponential map that reaches boundary points.
- Introduction of **Astral Riemannian Optimization** and **Astral $\alpha$-GaBO**.

---

## Information Geometry at $\alpha=-1$

### Probability simplex

$$
\Delta^d
=
\left\{
\mathbf p \in \mathbb R_{\ge 0}^{d+1}
\mid
\mathbf p^\top \mathbf 1 = 1
\right\}.
$$

### Tangent space

$$
T_{\mathbf p}\Delta^d
=
\left\{
\mathbf v \in \mathbb R^{d+1}
\mid
\mathbf v^\top \mathbf p = 0
\right\}
\cong \mathbb R^d.
$$

### Fisher–Rao metric

$$
\langle \mathbf v,\mathbf u\rangle_{\mathbf p}
=
\sum_{i=1}^{d+1}
p_i v_i u_i.
$$

### Natural gradient

$$
\operatorname{grad}_{\mathbf p}F
=
DF(\mathbf p)
-
\mathbf p^\top[DF(\mathbf p)].
$$

### Exponential connection

$$
\nabla^{(-1)}_{\mathbf U}\mathbf V(\mathbf p)
=
\left(
\mathbf p,
D^2_{\mathbf U}\mathbf V(\mathbf p)
+
\mathbf p^\top
\left[
\mathbf U(\mathbf p)\mathbf V(\mathbf p)
\right]
\right).
$$

### Exponential map

$$
\operatorname{Exp}^{(-1)}_{\mathbf p}(\mathbf u)
=
\frac{\exp(\mathbf u)}
{\mathbf p^\top \exp(\mathbf u)}
\,\mathbf p.
$$

---

## Astral Extension of the Tangent Space

The product structure of the exponential family allows a component-wise compactification of the tangent space.

### Interior points

For $\mathbf p \in \operatorname{int}(\Delta^d)$,

$$
\overline{T_{\mathbf p}\Delta^d}
\cong
\prod_{i=1}^{d+1}
\overline{\mathbb R}.
$$

### Boundary points

If $\mathbf p$ lies on a face of dimension $d-k$,

$$
\overline{T_{\mathbf p}\Delta^d}
\cong
\left(
# Reaching the Boundary: Astral Spaces for Riemannian Optimization over the Probability Simplex

**Federico Pavesi¹ · Noémie Jaquier² · Antonio Candelieri¹**

¹ Department of Economics, Management and Statistics (DEMS), University of Milano-Bicocca, Milan, Italy  
² Department of Robotics, Perception and Learning (RPL), KTH Royal Institute of Technology, Stockholm, Sweden

---

## Introduction & Motivation

Optimizing over probability distributions naturally leads to the **probability simplex**

$$\Delta^d = \left\{ \mathbf{p} \in \mathbb{R}^{d+1}_{\geq 0} \mid \mathbf{p}^\top \mathbf{1} = 1 \right\},$$

which appears in Bayesian optimization, robotics, experimental design, and mixture modelling.

Under the $\alpha = -1$ information geometry, optimization becomes unconstrained in tangent space. However, the standard exponential map approaches the simplex boundary only asymptotically, making boundary solutions practically unreachable.

We resolve this issue using the theory of **astral spaces**, extending the geometry and optimization dynamics continuously to the closed simplex.

---

## Main Contributions

- We extend the $\alpha = -1$ information geometry of the probability simplex to the **closed simplex**, including its boundary.
- We prove that the astral compactification of the tangent space is **well-defined and continuous**.
- We derive an extended exponential map enabling **Riemannian optimization directly on the boundary**.
- We introduce **Astral Riemannian Optimization** and **Astral $\alpha$-GaBO**.

---

## Information Geometry at $\alpha = -1$

Key geometric objects for the exponential geometry:

| Object | Definition |
|---|---|
| **Simplex** | $\Delta^d = \left\\{ \mathbf{p} \in \mathbb{R}^{d+1}_{\geq 0} \mid \mathbf{p}^\top \mathbf{1} = 1 \right\\}$ |
| **Tangent space** | $\mathcal{T}_{\mathbf{p}} \Delta^d = \left\\{ \mathbf{v} \in \mathbb{R}^{d+1} \mid \mathbf{v}^\top \mathbf{p} = 0 \right\\} \cong \mathbb{R}^d$ |
| **Fisher–Rao metric** | $\langle \mathbf{v}, \mathbf{u} \rangle_{\mathbf{p}} = \sum_{i=1}^{d+1} p_i\, v_i\, u_i$ |
| **Natural gradient** | $\operatorname{grad}_{\mathbf{p}} F = DF(\mathbf{p}) - \mathbf{p}^\top [DF(\mathbf{p})]$ |
| **Connection** | $\nabla^{(-1)}_{\mathbf{U}} \mathbf{V}(\mathbf{p}) = \left( \mathbf{p},\; D^2_{\mathbf{U}} \mathbf{V}(\mathbf{p}) + \mathbf{p}^\top \left[ \mathbf{U}(\mathbf{p})\, \mathbf{V}(\mathbf{p}) \right] \right)$ |
| **Exponential map** | $\operatorname{Exp}^{(-1)}_{\mathbf{p}}(\mathbf{u}) = \dfrac{\exp(\mathbf{u})}{\mathbf{p}^\top \exp(\mathbf{u})}\, \mathbf{p}$ |

---

## Astral Extension of the Tangent Space

The product structure of the exponential family allows us to compactify each component of the tangent space independently, yielding a tractable extension.

**Interior** ($\mathbf{p} \in \operatorname{int}\,\Delta^d$):

$$\overline{\mathcal{T}_{\mathbf{p}}\Delta^d} \;\cong\; \bigtimes_{i=1}^{d+1} \overline{\mathbb{R}}$$

**Face of dimension $d - k$** (i.e., $k$ coordinates vanish):

$$\overline{\mathcal{T}_{\mathbf{p}}\Delta^d} \;\cong\; \bigtimes_{i=1}^{d-k+1} \overline{\mathbb{R}} \;\times\; \bigtimes_{j=1}^{k} [-\infty, 0]$$

**Extended exponential map:**

$$\overline{\operatorname{Exp}}^{(-1)}_{\mathbf{p}}(\mathbf{u}) = \frac{\overline{\exp}(\mathbf{u})}{\mathbf{p}^\top \overline{\exp}(\mathbf{u})}\,\mathbf{p}$$

Here $\overline{\exp}$ denotes the extension of the exponential function to $\overline{\mathbb{R}}$, with $\overline{\exp}(-\infty) = 0$.

---

## Theoretical Results

### Theorem 1 (Well-definedness of the compactification)

> **Theorem.** *The compactified tangent space $\overline{\mathcal{T}_{\mathbf{p}}\Delta^d}$ is well-defined as an astral extension.*

**Proof.**
We must show that the astral extension of $\mathcal{T}_{\mathbf{p}}\Delta^d$ exists and is unique.
Recall that

$$\mathcal{T}_{\mathbf{p}}\Delta^d = \ker(\ell_{\mathbf{p}}),$$

where $\ell_{\mathbf{p}} : \mathbb{R}^{d+1} \to \mathbb{R}$ is the linear functional $\ell_{\mathbf{p}}(\mathbf{v}) = \mathbf{p}^\top \mathbf{v}$.
Since $\ell_{\mathbf{p}}$ is linear (in particular, convex), Theorem 7.4 of [1] guarantees that the astral extension of $\ell_{\mathbf{p}}$ to $\overline{\mathbb{R}}^{d+1}$ is **unique and continuous**.
The compactified tangent space is then defined component-wise as

$$\overline{\mathcal{T}_{\mathbf{p}}\Delta^d} = \left\{ \mathbf{u} \in \overline{\mathbb{R}}^{d+1} \mid \bar{\ell}_{\mathbf{p}}(\mathbf{u}) = 0 \right\},$$

where $\bar{\ell}_{\mathbf{p}}$ denotes the astral extension of $\ell_{\mathbf{p}}$.
The product structure of $\overline{\mathbb{R}}^{d+1}$ then yields the identification stated in the theorem. $\blacksquare$

---

### Theorem 2 (Extension of the exponential map)

> **Theorem.** *The map*
> $$\overline{\operatorname{Exp}}^{(-1)}_{\mathbf{p}}(\mathbf{u}) = \frac{\overline{\exp}(\mathbf{u})}{\mathbf{p}^\top \overline{\exp}(\mathbf{u})}\,\mathbf{p}$$
> *is the well-defined continuous extension of the $\alpha = -1$ exponential map to the closed simplex.*

**Proof.**
It suffices to show that the extended geodesics $t \mapsto \overline{\operatorname{Exp}}^{(-1)}_{\mathbf{p}}(t\mathbf{u})$ are continuous for all $\mathbf{p} \in \overline{\Delta^d}$ and all $\mathbf{u} \in \overline{\mathcal{T}_{\mathbf{p}}\Delta^d}$, including directions $\mathbf{u}$ with infinite components.

Decomposing component-wise, the $i$-th component of the extended map reads

$$\left( \overline{\operatorname{Exp}}^{(-1)}_{\mathbf{p}}(\mathbf{u}) \right)_i = \frac{\overline{\exp}(u_i)\, p_i}{\mathbf{p}^\top \overline{\exp}(\mathbf{u})}.$$

Each function $u_i \mapsto \overline{\exp}(u_i)$ is convex and non-decreasing on $\overline{\mathbb{R}}$.
The denominator

$$\mathbf{p}^\top \overline{\exp}(\mathbf{u}) = \sum_{j=1}^{d+1} p_j\, \overline{\exp}(u_j)$$

is a finite positive sum, since $\mathbf{p} \in \Delta^d$ ensures the existence of at least one index $j$ with $p_j > 0$ and $u_j > -\infty$, so the sum is bounded away from zero.
Hence each component is continuous on $\overline{\mathcal{T}_{\mathbf{p}}\Delta^d}$, and by Proposition 10.14 of [1] the full map is continuous in the astral topology.
Well-definedness on boundary faces follows from the convention $\overline{\exp}(-\infty) = 0$, which correctly maps vanishing coordinates to zero probability mass. $\blacksquare$

---

## Algorithms

### Astral Riemannian Optimization

```
Repeat until convergence:
  1. Compute the Riemannian gradient of the objective at x_t
     using the Fisher-Rao metric.
  2. Determine the descent direction in the astral tangent space.
  3. Retract via the extended exponential map:
       x_{t+1} = Exp_bar^{(-1)}_{x_t}( -eta * grad F(x_t) )
  4. Set x_t <- x_{t+1}.
```

The retraction step naturally reaches the boundary whenever the gradient direction has an infinite astral component, making boundary solutions reachable in finite steps.

### Astral $\alpha$-GaBO

Astral $\alpha$-GaBO integrates the extended exponential map into the $\alpha$-GaBO Bayesian optimization framework [2]. The key modification replaces the standard retraction with $\overline{\operatorname{Exp}}^{(-1)}$, allowing gradient-based acquisition optimization to naturally converge to boundary solutions.

```
Repeat until budget exhausted:
  1. Fit a Riemannian GP surrogate on current observations.
  2. Optimize the acquisition function via natural-gradient descent
     using Exp_bar^{(-1)} as the retraction (Astral Riemannian Optimization).
  3. Evaluate the objective at the returned point
     (possibly on the boundary of Delta^d).
  4. Update the observation set and iterate.
```

---

## Experimental Results

We validate the proposed approach on two complementary settings, in both cases placing the global optimum on the **boundary** of $\Delta^d$.

### Convex Optimization

Differentiable convex functions on $\Delta^d$ are optimized with Astral Riemannian gradient descent.
The method converges to the optimum significantly faster than the constrained Euclidean counterpart (projected gradient descent).

- **Objective:** Euclidean distance raised to $3/10$
- **Dimensions:** $d = 5, 10, 20$
- **Metric:** lower is better

### Black-Box Optimization (Astral $\alpha$-GaBO)

Non-convex benchmark functions are optimized with Bayesian Optimization.
Astral $\alpha$-GaBO consistently identifies boundary optima, outperforming the Euclidean baseline.

Benchmarks: **Ackley** and **Rosenbrock** functions in dimensions $d = 5, 10, 20$.

Convergence curves report median, $q_{25}$, and $q_{75}$ over 25 independent runs.
**Astral $\alpha$-GaBO** vs. **Euclidean baseline** — lower is better.

---

## References

[1] Dudík, M., Schapire, R. E., Telgarsky, M.: *Astral space: Convex analysis at infinity*. arXiv:2205.03260 (2025).

[2] Pavesi, F., Candelieri, A., Jaquier, N.: *Information theoretic Bayesian optimization over the probability simplex*. The 42nd Conference on Uncertainty in Artificial Intelligence, arXiv:2603.09793 (2026).

---

## Contact

| Name | Email |
|---|---|
| Federico Pavesi | f.pavesi11@campus.unimib.it |
| Noémie Jaquier | jaquier@kth.se |
| Antonio Candelieri | antonio.candelieri@unimib.it |


