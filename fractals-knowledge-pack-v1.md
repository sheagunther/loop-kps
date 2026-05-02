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
Fractals Knowledge Pack
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
-   [1 · What Are Fractals](#ch-what)
-   [2 · Fractal Dimension](#ch-dimension)
-   [3 · Classic Fractals](#ch-classic)
-   [4 · Iterated Function Systems](#ch-ifs)
-   [5 · Complex Dynamics Fractals](#ch-complex)
-   [6 · Random & Natural Fractals](#ch-random)
-   [7 · Multifractals](#ch-multifractals)
-   [8 · Applications](#ch-applications)
-   [9 · Fractal Catalog](#ch-catalog)
-   [References](#ch-refs)

::: {.content role="main"}
::: {#ch-abstract .abstract-box}
::: abstract-label
About This Document
:::

A comprehensive reference on fractal geometry --- self-similar structures, dimension theory, construction methods, and applications. Covers classic geometric fractals, complex dynamics fractals (Mandelbrot/Julia), iterated function systems, random fractals, and multifractal analysis. Draws on 10 sources.
:::

::: {#ch-what .chapter}
::: chapter-number
Section 1
:::

::: chapter-title
What Are Fractals
:::

A **fractal** is a geometric object exhibiting **self-similarity** (or statistical self-similarity) at different scales, typically with a non-integer (fractional) dimension. The term was coined by Benoit Mandelbrot in 1975 from the Latin *fractus* (\"broken\"). No single formal definition encompasses all objects called fractals, but key properties include: (1) fine structure at arbitrarily small scales, (2) too irregular to be described by classical geometry, (3) some form of self-similarity (exact, quasi, or statistical), (4) fractal dimension exceeding topological dimension.

::: {.callout .key}
::: callout-label
Self-similarity types
:::

**Exact self-similarity:** The object is identical at every scale (Cantor set, Sierpiński triangle). **Quasi-self-similarity:** Small-scale copies are approximately but not exactly the same as the whole (Mandelbrot set boundary). **Statistical self-similarity:** Statistical properties are preserved across scales (coastlines, turbulence, Brownian motion). Natural fractals are statistically self-similar; mathematical fractals can be exactly self-similar.
:::
:::

::: {#ch-dimension .chapter}
::: chapter-number
Section 2
:::

::: chapter-title
Fractal Dimension
:::

The **topological dimension** of a point is 0, a line is 1, a surface is 2. Fractals have dimensions between these integers. Several measures exist:

  Dimension          Definition                                                                         Computation
  ------------------ ---------------------------------------------------------------------------------- ---------------------------------------------------------
  **Hausdorff**      d_H = inf{d : H\^d(F) = 0} where H\^d is the d-dimensional Hausdorff measure       Mathematically rigorous; often hard to compute exactly
  **Box-counting**   d_B = lim\_{ε→0} log N(ε) / log(1/ε) where N(ε) = min boxes of side ε to cover F   Practical approximation; use log-log regression
  **Similarity**     For exactly self-similar sets: d = log N / log (1/r) where N copies at scale r     Only for exactly self-similar IFS attractors
  **Correlation**    Based on scaling of correlation integral C(ε) \~ ε\^{d_2}                          Estimated from time series data (Grassberger-Procaccia)
  **Kaplan-Yorke**   D_KY = j + (∑\_{i=1}\^j λ_i)/\|λ\_{j+1}\| from Lyapunov spectrum                   Estimated from dynamical system Lyapunov exponents

For \"nice\" fractals (exactly self-similar with the open set condition), all these dimensions agree. For more complex fractals, they can differ, with Hausdorff ≤ box-counting in general.

::: {.callout .tip}
::: callout-label
Quick dimension formula
:::

For a self-similar fractal made of N copies scaled by factor r: d = log(N) / log(1/r). Example: Sierpiński triangle = 3 copies at scale 1/2 → d = log 3 / log 2 ≈ 1.585. Koch curve = 4 copies at scale 1/3 → d = log 4 / log 3 ≈ 1.262.
:::
:::

::: {#ch-classic .chapter}
::: chapter-number
Section 3
:::

::: chapter-title
Classic Geometric Fractals
:::

  Fractal                   Construction                                                          Dimension              Key Property
  ------------------------- --------------------------------------------------------------------- ---------------------- ---------------------------------------------------------------------------------
  **Cantor set**            Remove middle third of \[0,1\], repeat on each remaining segment      log 2/log 3 ≈ 0.631    Uncountable, zero length, totally disconnected
  **Sierpiński triangle**   Remove central inverted triangle from equilateral triangle, repeat    log 3/log 2 ≈ 1.585    Zero area, infinite perimeter
  **Sierpiński carpet**     Remove center square from 3×3 grid, repeat on remaining 8             log 8/log 3 ≈ 1.893    Universal: contains homeomorphic image of every 1D compact metric space
  **Koch snowflake**        Replace middle third of each side with equilateral bump, repeat       log 4/log 3 ≈ 1.262    Finite area, infinite perimeter; continuous but nowhere differentiable boundary
  **Menger sponge**         3D analog of Sierpiński carpet; remove center and face-center cubes   log 20/log 3 ≈ 2.727   Zero volume, infinite surface area
  **Dragon curve**          Repeatedly fold a strip of paper in half, unfold to 90°               2                      Space-filling; tiles the plane
  **Hilbert curve**         Space-filling curve visiting every point in a square                  2                      Continuous surjection \[0,1\] → \[0,1\]²
:::

::: {#ch-ifs .chapter}
::: chapter-number
Section 4
:::

::: chapter-title
Iterated Function Systems (IFS)
:::

An **IFS** is a finite collection of contraction mappings {f₁, \..., f_N} on a complete metric space. By the **Banach contraction principle**, there exists a unique nonempty compact set A (the **attractor**) satisfying A = f₁(A) ∪ f₂(A) ∪ \... ∪ f_N(A). This is **Hutchinson\'s theorem** (1981).

If each f_i is a similarity (rotation + scaling) with ratio r_i, and the **open set condition** holds (the images f_i(U) are disjoint for some open set U), then the Hausdorff dimension of the attractor is the unique d satisfying ∑ r_i\^d = 1 (the **Moran equation**).

The **Chaos Game** (random IFS algorithm): repeatedly pick a random f_i and apply it to the current point. The orbit converges to the attractor. This provides a simple probabilistic method for rendering IFS fractals.

**Barnsley\'s fern** is a famous IFS with 4 affine maps that produces a remarkably realistic fern --- demonstrating that complex natural forms can emerge from simple affine rules.
:::

::: {#ch-complex .chapter}
::: chapter-number
Section 5
:::

::: chapter-title
Complex Dynamics Fractals
:::

The **Mandelbrot set** and **Julia sets** arise from iterating z~n+1~ = z~n~² + c in the complex plane. See the dedicated Mandelbrot Set Knowledge Pack for full treatment. Key facts: the Mandelbrot set is connected (Douady-Hubbard), its boundary has Hausdorff dimension 2 (Shishikura), and it encodes the dynamics of all quadratic polynomials. Julia sets range from smooth curves (for c in the interior of M) to intricate fractals (for c near the boundary of M) to Cantor dusts (for c outside M).

**Newton fractals** arise from applying Newton\'s method z~n+1~ = z_n − f(z_n)/f\'(z_n) to complex polynomials. The basins of attraction of different roots form fractal boundaries.
:::

::: {#ch-random .chapter}
::: chapter-number
Section 6
:::

::: chapter-title
Random and Natural Fractals
:::

**Brownian motion** has a sample path with Hausdorff dimension 2 (almost surely) in ℝ^d^ for d ≥ 2, and the graph of 1D Brownian motion has dimension 3/2. **Fractional Brownian motion** B_H(t) with Hurst parameter H ∈ (0,1) has graph dimension 2 − H.

**Percolation clusters** at criticality are random fractals with dimension 91/48 ≈ 1.896 in 2D (Smirnov, 2001, proved conformal invariance for site percolation on the triangular lattice).

**Natural fractals** exhibit statistical self-similarity over limited scale ranges: coastlines (Richardson, d ≈ 1.25 for Britain), mountain surfaces, river networks, blood vessel branching, lung bronchial trees, galaxy distributions, turbulent fluid flows. Mandelbrot\'s original motivation was to study such irregular natural forms that Euclidean geometry cannot describe.
:::

::: {#ch-multifractals .chapter}
::: chapter-number
Section 7
:::

::: chapter-title
Multifractal Analysis
:::

A **multifractal** is an object requiring a spectrum of dimensions to characterize, not just a single number. The **singularity spectrum** f(α) describes the fractal dimension of the set of points with local scaling exponent (Hölder exponent) α. For a simple fractal, f(α) is a single point; for a multifractal, it is a curve. The **Rényi dimensions** D_q provide an equivalent characterization: D₀ = box-counting dimension, D₁ = information dimension, D₂ = correlation dimension. For a monofractal, all D_q are equal; for a multifractal, they differ.

Multifractal analysis is used in turbulence modeling (the energy dissipation field is multifractal), financial time series, and network traffic analysis.
:::

::: {#ch-applications .chapter}
::: chapter-number
Section 8
:::

::: chapter-title
Applications
:::

  Domain              Application
  ------------------- --------------------------------------------------------------------------------------------------------------------
  Computer graphics   Terrain generation (midpoint displacement, diamond-square), procedural textures, L-systems for plants
  Image compression   Fractal compression (Barnsley, Jacquin): encode image as IFS; high compression ratios at the cost of encoding time
  Antenna design      Fractal antennas (Koch, Sierpiński): multi-band, compact, self-similar geometry enables wideband performance
  Medicine            Fractal dimension of blood vessel networks, retinal vasculature, tumor boundaries; diagnostic biomarker
  Geology             Coastline measurement (Richardson), earthquake fault networks, mineral distribution
  Finance             Fractal market hypothesis; multifractal models of returns (Mandelbrot); fat-tailed distributions
  Physics             Phase transitions (percolation), turbulence (multifractal energy dissipation), diffusion-limited aggregation
:::

::: {#ch-catalog .chapter}
::: chapter-number
Section 9
:::

::: chapter-title
Fractal Catalog
:::

  Fractal                             Type                Dimension
  ----------------------------------- ------------------- -----------
  Cantor set                          Geometric (IFS)     0.631
  Koch curve                          Geometric (IFS)     1.262
  Sierpiński triangle                 Geometric (IFS)     1.585
  Sierpiński carpet                   Geometric (IFS)     1.893
  Menger sponge                       Geometric (IFS)     2.727
  Mandelbrot set boundary             Complex dynamics    2.000
  Lorenz attractor                    Strange attractor   2.063
  Hénon attractor                     Strange attractor   1.261
  Brownian motion path (2D)           Random              2.000
  Brownian motion graph (1D)          Random              1.500
  Percolation cluster (2D critical)   Random              1.896
  Britain coastline                   Natural             ≈ 1.25
  Barnsley fern                       IFS (affine)        ≈ 1.45
:::

::: {#ch-refs .chapter}
::: chapter-number
References
:::

::: chapter-title
References
:::

1.  Barnsley, M.F. *Fractals Everywhere*, 2nd ed. Academic Press, 1993.
2.  Falconer, K. *Fractal Geometry: Mathematical Foundations and Applications*, 3rd ed. Wiley, 2014.
3.  Hutchinson, J.E. \"Fractals and self-similarity.\" *Indiana University Mathematics Journal* 30 (1981): 713--747.
4.  Mandelbrot, B. *The Fractal Geometry of Nature*. W.H. Freeman, 1982.
5.  Mandelbrot, B. \"How long is the coast of Britain? Statistical self-similarity and fractional dimension.\" *Science* 156 (1967): 636--638.
6.  Peitgen, H.-O., Jürgens, H. & Saupe, D. *Chaos and Fractals: New Frontiers of Science*, 2nd ed. Springer, 2004.
7.  Schroeder, M. *Fractals, Chaos, Power Laws*. W.H. Freeman, 1991.
8.  Shishikura, M. \"The Hausdorff dimension of the boundary of the Mandelbrot set and Julia sets.\" *Annals of Mathematics* 147 (1998): 225--267.
9.  Smirnov, S. \"Critical percolation in the plane: conformal invariance, Cardy\'s formula, scaling limits.\" *C. R. Acad. Sci. Paris* 333 (2001): 239--244.
10. Edgar, G.A. *Measure, Topology, and Fractal Geometry*, 2nd ed. Springer, 2008.
:::
:::
:::

------------------------------------------------------------------------

::: page-footer
Loop MMT™ · Multi-Module Theory Fractals Knowledge Pack · v1 © 2026 Shea Gunther · [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/deed.en){style="color:inherit;"}
:::
