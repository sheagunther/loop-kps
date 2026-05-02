::: page-header
<div>

::: logo
LOOP MMT™
:::

::: logo-sub
Multi-Module Theory
:::

</div>

::: header-right
::: skin-group
[Skin]{style="font-family:var(--font);font-size:9px;letter-spacing:2px;color:var(--fg-dim);text-transform:uppercase;margin-right:4px;"}

OG

Winamp

Sunrise
:::

::: doc-title
::: title-main
Mandelbrot Set Knowledge Pack
:::

::: build-tag
v1 · 7 April 2026
:::
:::
:::
:::

::: body-wrap
::: toc-title
Contents
:::

-   [About](#ch-abstract)
-   [1 · Definition](#ch-definition)
-   [2 · Geometry](#ch-geometry)
-   [3 · Julia Sets](#ch-julia)
-   [4 · The Boundary](#ch-boundary)
-   [5 · Dynamics](#ch-dynamics)
-   [6 · Computation](#ch-computation)
-   [7 · Generalizations](#ch-generalizations)
-   [8 · Key Results](#ch-results)
-   [References](#ch-refs)

::: {.content role="main"}
::: {#ch-abstract .abstract-box}
::: abstract-label
About This Document
:::

A focused reference on the Mandelbrot set --- the parameter space of the quadratic family z² + c. Covers the definition, geometric structure, relationship to Julia sets, boundary properties, computational methods, and key theorems. Draws on 8 sources.
:::

::: {#ch-definition .chapter}
::: chapter-number
Section 1
:::

::: chapter-title
Definition
:::

The **Mandelbrot set** M is the set of complex numbers c for which the iteration z~n+1~ = z~n~² + c, starting from z₀ = 0, produces a bounded sequence. Equivalently, c ∈ M if and only if \|z_n\| does not tend to infinity. The set is named after Benoit Mandelbrot, who produced the first computer visualizations in 1980, though the iteration was studied earlier by Pierre Fatou and Gaston Julia in the 1910s--1920s.

**Escape criterion:** If \|z_n\| \> 2 for any n, the sequence diverges and c ∉ M. This follows because once \|z\| \> max(\|c\|, 2), the iteration escapes to infinity. In practice, computation stops and declares c ∉ M when \|z_n\| exceeds 2 (the **bailout radius**).

::: {.callout .key}
::: callout-label
Parameter space vs dynamical space
:::

The Mandelbrot set lives in the *parameter space* --- each point c represents a different dynamical system z² + c. Julia sets live in the *dynamical space* --- for a fixed c, the Julia set J_c describes the dynamics of z² + c as z varies. The Mandelbrot set is a map of which parameter values produce connected Julia sets and which produce disconnected ones.
:::
:::

::: {#ch-geometry .chapter}
::: chapter-number
Section 2
:::

::: chapter-title
Geometric Structure
:::

::: section
::: section-title
Main Cardioid and Period-n Bulbs
:::

The largest component of M is the **main cardioid**, consisting of all c for which z² + c has an attracting fixed point. Its boundary is parametrized by c = (e^iθ^/2)(1 − e^iθ^/2) for θ ∈ \[0, 2π). Attached to the cardioid are **period-n bulbs**: the period-2 bulb (the large circle to the left), the period-3 bulbs (smaller), and so on. Each period-n bulb contains c values for which z² + c has an attracting cycle of period n.
:::

::: section
::: section-title
Self-Similarity
:::

The Mandelbrot set exhibits **quasi-self-similarity**: zooming into the boundary reveals miniature copies of the entire set (called **Mandelbrot copies** or **baby Mandelbrots**), connected to the main body by thin filaments. These copies are not exact --- they are distorted and decorated --- but their structural resemblance to the whole is one of the most striking features of the set. The set is connected (proved by Douady and Hubbard, 1982), meaning all these copies are joined.
:::

::: section
::: section-title
Connectedness and the Mandelbrot Set as a Parameter Space Map
:::

**Douady-Hubbard theorem (1982):** The Mandelbrot set M is connected. Equivalently, c ∈ M if and only if the Julia set J_c is connected; c ∉ M if and only if J_c is totally disconnected (a Cantor set). M is therefore a \"dictionary\" --- it tells you exactly which quadratic polynomials have connected Julia sets.
:::
:::

::: {#ch-julia .chapter}
::: chapter-number
Section 3
:::

::: chapter-title
Julia Sets
:::

For a fixed c, the **filled Julia set** K_c is the set of z₀ values for which z~n+1~ = z~n~² + c remains bounded. The **Julia set** J_c = ∂K_c is its boundary. Three cases:

  c Location                           Julia Set J_c                        Dynamics
  ------------------------------------ ------------------------------------ ----------------------------
  c in interior of M (main cardioid)   Simple closed curve                  Attracting fixed point
  c in interior of period-n bulb       Connected, more complex              Attracting n-cycle
  c on boundary of M                   Connected, often fractal             Neutral (parabolic/Siegel)
  c outside M                          Cantor dust (totally disconnected)   All orbits escape

The **Fatou set** F_c is the complement of J_c where dynamics are \"tame\" (converging to attracting cycles). The Julia set is where dynamics are chaotic --- J_c is the closure of the set of repelling periodic points.
:::

::: {#ch-boundary .chapter}
::: chapter-number
Section 4
:::

::: chapter-title
The Boundary
:::

**Shishikura\'s theorem (1998):** The boundary ∂M has Hausdorff dimension exactly 2. This means the boundary is so intricate that it fills the plane in a measure-theoretic sense --- it is as complex as a 2-dimensional object, despite being a curve.

The boundary of M contains all the mathematical complexity. The interior consists of the main cardioid and the bulbs (where the iteration has attracting cycles). The boundary is where the transition from bounded to unbounded behavior occurs, and it is this transition that generates the fractal structure.

**MLC Conjecture:** The Mandelbrot set is **locally connected** --- for every point on the boundary and every neighborhood, the intersection of M with the neighborhood is connected. This remains one of the most important open problems in complex dynamics. If true, it would imply that the topological model of M given by Douady and Hubbard (via external angles and the Böttcher coordinate) is complete.
:::

::: {#ch-dynamics .chapter}
::: chapter-number
Section 5
:::

::: chapter-title
Dynamics of z² + c
:::

::: section
::: section-title
Fixed Points
:::

The quadratic map f_c(z) = z² + c has two fixed points: z = (1 ± √(1−4c))/2. A fixed point z\* is **attracting** if \|f\'\_c(z\*)\| = \|2z\*\| \< 1, **repelling** if \|2z\*\| \> 1, and **neutral** if \|2z\*\| = 1. The main cardioid of M consists exactly of those c for which one fixed point is attracting.
:::

::: section
::: section-title
Period Doubling
:::

As c moves along the real axis from c = 0 leftward, the system undergoes period-doubling bifurcations at c ≈ −0.75, −1.25, −1.3681, \... converging to the Feigenbaum point c\_∞ ≈ −1.4012. The Feigenbaum constant δ ≈ 4.669 governs the rate of convergence, just as in the logistic map (the two systems are topologically conjugate along the real axis).
:::

::: section
::: section-title
External Rays and Angles
:::

The **Böttcher coordinate** Φ_M: ℂ \\ M → ℂ \\ D̄ is a conformal isomorphism mapping the complement of M to the complement of the closed unit disk. **External rays** R(θ) are the preimages of radial lines under Φ_M. They \"land\" on points of ∂M and provide a combinatorial framework for understanding the structure of M. The **external angle** of a point on ∂M encodes the dynamics of the corresponding Julia set in binary.
:::
:::

::: {#ch-computation .chapter}
::: chapter-number
Section 6
:::

::: chapter-title
Computational Methods
:::

  Method                      Description
  --------------------------- -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **Escape-time algorithm**   Iterate z² + c from z₀ = 0; count iterations until \|z\| \> 2 (bailout). Color by iteration count. Simple, parallelizable.
  **Smooth coloring**         Use fractional escape count: n + 1 − log₂(log₂\|z_n\|) to eliminate color banding.
  **Distance estimation**     Simultaneously iterate the derivative dz/dc to compute distance from c to ∂M. Used for anti-aliased rendering.
  **Perturbation theory**     Compute one reference orbit at high precision; approximate nearby orbits with perturbation. Enables deep zooms (10¹⁰⁰⁰+ magnification) without computing every pixel at full precision.
  **Period detection**        Detect when the iteration enters a cycle (the point is interior to M). Avoids wasting iterations on convergent points.
:::

::: {#ch-generalizations .chapter}
::: chapter-number
Section 7
:::

::: chapter-title
Generalizations
:::

**Multibrot sets:** Parameter spaces of z^d^ + c for integer d \> 2. The d-th Multibrot set has (d−1)-fold rotational symmetry. All are connected.

**Burning Ship fractal:** Uses \|Re(z)\| and \|Im(z)\| in the iteration, producing a non-analytic variant with ship-shaped features.

**Higher-dimensional analogs:** The Mandelbulb and Mandelbox are 3D objects constructed by extending the Mandelbrot iteration to three dimensions using various algebraic generalizations (not true complex analogs, since there is no 3D division algebra).
:::

::: {#ch-results .chapter}
::: chapter-number
Section 8
:::

::: chapter-title
Key Results Reference
:::

  Result               Statement                                                                Source
  -------------------- ------------------------------------------------------------------------ -------------------------
  Definition           M = {c ∈ ℂ : z\_{n+1} = z_n² + c from z₀=0 remains bounded}              Mandelbrot (1980)
  Escape criterion     \|z_n\| \> 2 ⇒ c ∉ M                                                     Standard
  Connectedness        M is connected; c ∈ M ↔ J_c connected                                    Douady & Hubbard (1982)
  Boundary dimension   dim_H(∂M) = 2                                                            Shishikura (1998)
  Area                 Area of M ≈ 1.5065918\...; exact value unknown                           Numerical estimates
  MLC conjecture       M is locally connected (open problem)                                    Douady & Hubbard
  Universality         M contains homeomorphic copies of itself at every scale near boundary    Standard
  Period-doubling      Feigenbaum constant δ ≈ 4.669 governs bifurcation spacing on real axis   Feigenbaum (1978)
:::

::: {#ch-refs .chapter}
::: chapter-number
References
:::

::: chapter-title
References
:::

1.  Branner, B. \"The Mandelbrot set.\" In *Chaos and Fractals*, AMS, 1989.
2.  Devaney, R.L. & Keen, L. (eds.) *Chaos and Fractals: The Mathematics Behind the Computer Graphics*. AMS, 1989.
3.  Douady, A. & Hubbard, J.H. \"Itération des polynômes quadratiques complexes.\" *C. R. Acad. Sci. Paris* 294 (1982): 123--126.
4.  Mandelbrot, B. *The Fractal Geometry of Nature*. W.H. Freeman, 1982.
5.  Milnor, J. *Dynamics in One Complex Variable*, 3rd ed. Princeton University Press, 2006.
6.  Peitgen, H.-O. & Richter, P.H. *The Beauty of Fractals*. Springer, 1986.
7.  Shishikura, M. \"The Hausdorff dimension of the boundary of the Mandelbrot set and Julia sets.\" *Annals of Mathematics* 147 (1998): 225--267.
8.  Schleicher, D. \"On fibers and local connectivity of Mandelbrot and Multibrot sets.\" In *Fractal Geometry and Applications*, AMS, 2004.
:::
:::
:::

------------------------------------------------------------------------

::: page-footer
Loop MMT™ · Multi-Module Theory Mandelbrot Set Knowledge Pack · v1 © 2026 Shea Gunther · [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/deed.en){style="color:inherit;"}
:::
