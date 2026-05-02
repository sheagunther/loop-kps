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
Linear Algebra & Basis Function Theory
:::

::: build-tag
v1 · 9 April 2026
:::
:::
:::
:::

::: body-wrap
::: toc-title
Contents
:::

-   [About This Document](#ch-abstract)
-   [1 · Vector Spaces](#ch-vector-spaces)
-   [2 · Linear Independence](#ch-independence)
-   [3 · Span](#ch-span)
-   [4 · Basis and Dimension](#ch-basis)
-   [5 · Inner Product and Orthogonality](#ch-orthogonality)
-   [6 · Projection](#ch-projection)
-   [7 · Completeness](#ch-completeness)
-   [8 · Gram-Schmidt](#ch-gram-schmidt)
-   [9 · Testing Axes Empirically](#ch-empirical)
-   [10 · The Basis Checklist](#ch-checklist)
-   [11 · Board Connections](#ch-board)
-   [References](#ch-refs)

::: {.content role="main"}
::: {#ch-abstract .abstract-box}
::: abstract-label
About This Document
:::

Reference on the linear algebra needed to evaluate whether a proposed set of axes constitutes a genuine basis. Covers independence, span, completeness, orthogonality, projection, and the Gram-Schmidt process, then bridges to empirical methods (PCA, factor analysis) for testing these properties against data. A multi-axis model is either a metaphor or a testable structure. The difference is whether its axes satisfy the formal properties of a basis. This pack provides the tools to make that determination. Founded on standard references (Strang, Axler, Lay) and 10 consulted sources.
:::

::: {#ch-vector-spaces .chapter}
::: chapter-number
Section 1
:::

::: chapter-title
Vector Spaces — The Container
:::

A **vector space** V over a field F is a set with two operations — vector addition and scalar multiplication — satisfying eight axioms: closure under both operations, associativity of addition, commutativity of addition, existence of an additive identity (zero vector), existence of additive inverses, compatibility of scalar multiplication (a(bv) = (ab)v), identity element of scalar multiplication (1·v = v), and distributivity (of scalars over vectors and of vectors over scalars). The canonical examples are ℝⁿ for various n: ℝ² (the plane), ℝ³ (ordinary space), ℝⁿ (n-dimensional coordinate space).

A **subspace** W of V is a nonempty subset that is itself a vector space under the inherited operations. The practical test: W contains the zero vector and is closed under addition and scalar multiplication. Every vector space contains at least the trivial subspace {0} and the whole space V as subspaces.

::: {.callout .key}
::: callout-label
Why this matters for multi-axis models
:::
Proposing n axes for a problem domain is implicitly claiming that a vector space of dimension n models that domain. If the space is never defined — what its elements represent, what addition and scaling mean in context — then the axes are labels, not coordinates. The space must be specified before the basis can be evaluated.
:::
:::

::: {#ch-independence .chapter}
::: chapter-number
Section 2
:::

::: chapter-title
Linear Independence — No Redundancy
:::

Vectors v₁, v₂, ..., vₖ in a vector space V are **linearly independent** if the equation c₁v₁ + c₂v₂ + ... + cₖvₖ = 0 has only the trivial solution c₁ = c₂ = ... = cₖ = 0. If any nontrivial solution exists, the vectors are **linearly dependent** — at least one is a weighted sum of the others and contributes no new information.

**Geometric reading.** Two vectors in ℝ² are dependent iff they're parallel. Three vectors in ℝ³ are dependent iff they all lie in the same plane. Each independent vector opens a direction that the others cannot reach.

**Computational test.** Arrange the vectors as columns of a matrix A. Row-reduce to echelon form. The set is independent iff there is a pivot in every column. For n vectors in ℝⁿ, equivalently: det(A) ≠ 0.

**The cost of dependence.** Dependent axes produce non-unique coordinates — the same point in the space admits multiple descriptions. This isn't merely inelegant; it means the axes don't cleanly separate the phenomena they're supposed to distinguish.

::: {.callout .note}
::: callout-label
Gram-Schmidt as independence detector
:::
The Gram-Schmidt process (Section 8) outputs the zero vector when it encounters a vector dependent on its predecessors. Attempting to orthogonalize a set therefore serves as a constructive independence test.
:::
:::

::: {#ch-span .chapter}
::: chapter-number
Section 3
:::

::: chapter-title
Span — Coverage
:::

The **span** of a set S = {v₁, ..., vₖ} is the set of all linear combinations of vectors in S: span(S) = {c₁v₁ + ... + cₖvₖ : cᵢ ∈ F}. The span is always a subspace — in fact, the smallest subspace containing S. When span(S) = V, we say S **spans** V: every vector in V is reachable.

A set can span without being independent (redundant vectors — more than needed), or be independent without spanning (not enough vectors to cover the full space). Two independent vectors in ℝ³ span a plane, not the whole space. Five vectors in ℝ³ span the whole space but carry at least two redundant vectors.

Span answers the question: *what can these axes describe?* If something in the problem space cannot be written as a combination of the axes, that thing is outside the span — invisible to the model.
:::

::: {#ch-basis .chapter}
::: chapter-number
Section 4
:::

::: chapter-title
Basis and Dimension
:::

A **basis** for a vector space V is a set B = {b₁, ..., bₙ} that is linearly independent and spans V. This is the minimal complete description: no vector is redundant, and no direction is missing.

**Unique Representation.** If B is a basis, every v ∈ V has exactly one expression v = c₁b₁ + ... + cₙbₙ. The scalars c₁, ..., cₙ are v's **coordinates** in basis B. Uniqueness is the property that makes coordinates meaningful — without it, a coordinate system is ambiguous.

**Dimension.** All bases of a finite-dimensional vector space have the same size. That size is the **dimension**, dim(V). Dimension is a property of the space, not of any particular basis. ℝ³ has dimension 3 regardless of which three independent spanning vectors you choose.

**The Basis Theorem.** For a space of dimension n: (a) any n independent vectors form a basis; (b) any n spanning vectors form a basis; (c) any independent set can be extended to a basis; (d) any spanning set can be reduced to one.

**Change of basis.** Multiple bases exist for any space. The standard basis for ℝ³ is {(1,0,0), (0,1,0), (0,0,1)}, but {(1,1,0), (0,1,1), (1,0,1)} works equally well. A **change-of-basis matrix** converts coordinates between bases. Choosing a basis is a design decision — different bases highlight different structure in the same space.

::: {.callout .key}
::: callout-label
The two-part test
:::
A set of axes forms a basis iff it satisfies both conditions: **independent** (no axis is derivable from the others) and **spanning** (every phenomenon in the space is expressible using these axes). If either fails, the model is either redundant or incomplete.
:::
:::

::: {#ch-orthogonality .chapter}
::: chapter-number
Section 5
:::

::: chapter-title
Inner Product and Orthogonality
:::

An **inner product** on a real vector space V is a function ⟨·,·⟩ : V × V → ℝ that is symmetric (⟨u,v⟩ = ⟨v,u⟩), linear in the first argument (⟨au + bw, v⟩ = a⟨u,v⟩ + b⟨w,v⟩), and positive definite (⟨v,v⟩ > 0 for v ≠ 0, and ⟨0,0⟩ = 0). The standard inner product on ℝⁿ is the dot product.

From the inner product come **norm** (‖v‖ = √⟨v,v⟩), **distance** (‖u − v‖), and **angle** (cos θ = ⟨u,v⟩/(‖u‖‖v‖)). The Cauchy-Schwarz inequality |⟨u,v⟩| ≤ ‖u‖·‖v‖ guarantees that this cosine is always between −1 and 1.

Two vectors are **orthogonal** (written u ⊥ v) if ⟨u,v⟩ = 0. An **orthogonal set** has pairwise orthogonal elements; an **orthonormal set** adds the requirement that each vector has unit norm.

**Orthogonality implies independence.** Any orthogonal set of nonzero vectors is linearly independent. Proof: suppose c₁u₁ + ... + cₖuₖ = 0. Take the inner product of both sides with uⱼ. By orthogonality all cross-terms vanish: cⱼ⟨uⱼ,uⱼ⟩ = 0. Since uⱼ ≠ 0, ⟨uⱼ,uⱼ⟩ > 0, so cⱼ = 0. This holds for all j. QED. Orthogonality therefore provides independence as a structural guarantee.

The deeper advantage is computational. With an orthogonal basis, coordinates are computed by individual inner products: cⱼ = ⟨v, bⱼ⟩/⟨bⱼ, bⱼ⟩. With a non-orthogonal basis, finding coordinates means solving a coupled system. Orthogonal axes don't interfere — each axis's contribution is measurable in isolation.

::: {.callout .key}
::: callout-label
Orthogonality is desirable, not required
:::
A basis need not be orthogonal. {(1,0), (1,1)} is a valid basis for ℝ² with non-orthogonal vectors. The axes exhibit crosstalk — the measured contribution of one axis depends on the other's value. Non-orthogonal bases are legitimate but analytically more expensive.
:::

**ε-orthogonality.** Perfect orthogonality is a mathematical idealization. In practice, axes measured from data are approximately orthogonal at best. The standard of ε-orthogonality — |⟨u,v⟩|/(‖u‖‖v‖) < ε for some small ε — defines when crosstalk is negligible enough to treat the axes as effectively independent.

::: {.callout .note}
::: callout-label
Orthogonality ≠ statistical independence
:::
Mathematical orthogonality (zero inner product, equivalently zero correlation for centered data) and statistical independence (P(A∩B) = P(A)P(B)) are related but not equivalent. For jointly Gaussian random variables, zero correlation does imply independence. For non-Gaussian variables, it does not — uncorrelated variables can still be dependent through higher-order relationships. When evaluating real-world axes, test both correlation structure and distributional independence.
:::
:::

::: {#ch-projection .chapter}
::: chapter-number
Section 6
:::

::: chapter-title
Projection — Decomposing Into Components
:::

Given a subspace W of an inner product space V, the **orthogonal projection** of v onto W is the vector in W closest to v. If {u₁, ..., uₖ} is an orthogonal basis for W:

proj_W(v) = Σᵢ₌₁ᵏ (⟨v, uᵢ⟩ / ⟨uᵢ, uᵢ⟩) uᵢ

For an orthonormal basis: proj_W(v) = Σᵢ₌₁ᵏ ⟨v, uᵢ⟩ uᵢ.

**Best Approximation Theorem.** proj_W(v) is the unique closest point in W to v. For any w ∈ W with w ≠ proj_W(v): ‖v − proj_W(v)‖ < ‖v − w‖.

*Proof.* Write v − w = (v − proj_W(v)) + (proj_W(v) − w). The first vector lies in W⊥ (by the definition of projection); the second lies in W. They are orthogonal. The Pythagorean theorem gives ‖v − w‖² = ‖v − proj_W(v)‖² + ‖proj_W(v) − w‖² ≥ ‖v − proj_W(v)‖², with equality only when proj_W(v) − w = 0.

**Residual.** The vector r = v − proj_W(v) is the part of v not captured by W. Its norm ‖r‖ measures approximation error. If ‖r‖ = 0, v lies entirely in W.

**Projection matrices.** For a matrix U whose columns form an orthonormal basis for W: P = UUᵀ. For a general full-rank matrix U: P = U(UᵀU)⁻¹Uᵀ. Properties: P² = P (idempotent — projecting twice does nothing new) and Pᵀ = P (symmetric).

**Least squares.** When Ax = b has no exact solution, the least-squares solution x̂ minimizes ‖Ax − b‖. Geometrically: project b onto Col(A), then solve. Algebraically: the **normal equations** AᵀAx̂ = Aᵀb. If A has linearly independent columns: x̂ = (AᵀA)⁻¹Aᵀb. Least-squares regression is orthogonal projection onto the column space of the design matrix. Every regression coefficient is, at bottom, an inner product.
:::

::: {#ch-completeness .chapter}
::: chapter-number
Section 7
:::

::: chapter-title
Completeness — Nothing Left Over
:::

The **orthogonal complement** of a subspace W is W⊥ = {v ∈ V : ⟨v, w⟩ = 0 for all w ∈ W}. This is everything W cannot reach — everything perpendicular to the entire subspace.

**Dimension Theorem.** dim(W) + dim(W⊥) = dim(V). A 3-dimensional subspace of ℝ⁵ has a 2-dimensional orthogonal complement. Those 2 missing dimensions are precisely what the subspace cannot describe.

**Orthogonal Decomposition.** V = W ⊕ W⊥. Every vector v decomposes uniquely as v = w + w⊥ with w ∈ W, w⊥ ∈ W⊥. This decomposition is the mathematical statement of "what the axes explain" + "what they don't."

**Completeness test.** A set of axes is complete for V iff its span equals V, which holds iff the orthogonal complement of that span is {0}. Equivalently: if ⟨v, bᵢ⟩ = 0 for every axis bᵢ forces v = 0, the axes are complete. Any nonzero vector orthogonal to all axes represents a direction the model cannot see.

**Parseval's identity.** For an orthonormal basis {e₁, ..., eₙ}: ‖v‖² = Σᵢ |⟨v, eᵢ⟩|² for all v ∈ V. The total squared norm equals the sum of squared components. In a finite-dimensional space, every orthonormal basis satisfies Parseval automatically. The identity becomes a genuine test of completeness in infinite-dimensional settings (Hilbert spaces), where an orthonormal set may fail to span the whole space. For finite-dimensional applications, Parseval's value is interpretive: it says the axes account for 100% of the signal, with nothing left over.

**The Four Fundamental Subspaces.** For an m × n matrix A of rank r: the row space (dim r in ℝⁿ), null space (dim n − r in ℝⁿ), column space (dim r in ℝᵐ), and left null space (dim m − r in ℝᵐ). Row space ⊥ null space; column space ⊥ left null space. This framework (due to Strang) is a complete accounting of a linear map's structure: what it sends, what it kills, what it reaches, and what it misses.

::: {.callout .key}
::: callout-label
The residual test
:::
Project data onto the span of proposed axes and measure the residual. Large residual relative to total signal indicates incompleteness — structure the model doesn't capture. Residual at noise level indicates near-completeness. This is the empirical version of checking whether W⊥ contains only noise.
:::
:::

::: {#ch-gram-schmidt .chapter}
::: chapter-number
Section 8
:::

::: chapter-title
Gram-Schmidt — From Messy to Clean
:::

The **Gram-Schmidt process** converts a linearly independent set {v₁, ..., vₖ} into an orthogonal set {u₁, ..., uₖ} spanning the same subspace.

**Algorithm:**

u₁ = v₁

uᵢ = vᵢ − Σⱼ₌₁ⁱ⁻¹ (⟨vᵢ, uⱼ⟩ / ⟨uⱼ, uⱼ⟩) uⱼ    for i = 2, ..., k

To normalize: eᵢ = uᵢ / ‖uᵢ‖.

**Mechanism.** Each step subtracts the projections of vᵢ onto all previously computed orthogonal vectors. The remainder is the component of vᵢ genuinely new — orthogonal to everything before it. If that remainder is zero, vᵢ was dependent on its predecessors.

**QR decomposition.** Gram-Schmidt applied to the columns of a matrix A with independent columns yields A = QR, where Q has orthonormal columns and R is upper triangular with positive diagonal entries. QR is the numerically preferred method for least-squares computation, avoiding the condition-number squaring that occurs when forming AᵀA.

**Existence of orthonormal bases.** Every nonzero finite-dimensional inner product space has an orthonormal basis. Proof: take any basis, apply Gram-Schmidt. This is constructive — it produces the basis, not just an existence guarantee.
:::

::: {#ch-empirical .chapter}
::: chapter-number
Section 9
:::

::: chapter-title
Testing Axes Empirically
:::

The theory of Sections 1–8 defines what a basis is. To determine whether proposed axes actually form one, you need data and statistical methods.

**Principal Component Analysis (PCA).** PCA computes the eigendecomposition of the data's covariance matrix. The eigenvectors are the directions of maximum variance; the eigenvalues quantify how much variance each direction captures. PCA is purely descriptive — it finds the orthogonal axes that best summarize variance, without assuming any model. It answers: *if we had to choose k orthogonal axes to explain this data, which would they be?*

PCA assesses completeness through variance explained. If k components capture 95%+ of total variance, a k-dimensional model is nearly complete for that dataset. The scree plot (eigenvalue magnitude vs. component number) shows where signal fades into noise.

**Factor Analysis (FA).** FA goes further: it models observed variables as linear functions of latent factors plus unique noise. This is testable — the model imposes restrictions on the covariance matrix that can be checked against data. Factor loadings reveal how observed variables relate to hypothesized factors. If the model fits, the factors are empirically supported as the generative structure behind the data.

**Confirmatory Factor Analysis (CFA).** When you have a specific hypothesis ("these four axes, loading on these variables"), CFA tests it directly. You specify the structure and ask: does the data support it? Fit indices (chi-square, RMSEA, CFI, SRMR) quantify the answer.

**Testing the four properties:**

*Independence.* Compute correlations between axes or factor scores. Near-zero off-diagonal elements suggest approximate orthogonality. The determinant of the correlation matrix near zero flags near-dependence. In FA, compare orthogonal rotation (varimax, which forces independence) against oblique rotation (promax, which allows correlation) — the difference reveals how much the axes naturally lean on each other.

*Completeness.* Total variance explained by the retained factors. Residual correlations after factoring — patterns in residuals suggest missing dimensions. Horn's parallel analysis compares observed eigenvalues against eigenvalues from random data; components above the random baseline are signal, those below are noise.

*Dimensionality.* How many real axes does the data support? Kaiser's rule (eigenvalue > 1), the scree test, and parallel analysis give estimates. If the data supports 3 dimensions but you proposed 4, one proposed axis is either redundant or not present in the data.

::: {.callout .note}
::: callout-label
Data requirements
:::
These methods require observations scored on each axis. Factor analysis rules of thumb vary by source but generally recommend at least 5–10 observations per variable, with absolute minimums around 100–200 total cases. Without data, basis properties can only be evaluated by argument and thought experiment — which has value but is not the same as measurement.
:::
:::

::: {#ch-checklist .chapter}
::: chapter-number
Section 10
:::

::: chapter-title
The Basis Checklist
:::

For any proposed set of axes in a multi-axis model:

**1. Independence — "Are the axes genuinely distinct?"**

*Question:* Can any axis be expressed as a weighted combination of the others?
*Abstract test:* Form the matrix of axes; check that rank equals the number of axes.
*Empirical test:* Correlation matrix between axis scores; factor cross-loadings.
*Failure mode:* Two apparently different axes measuring the same underlying construct. The model claims more dimensions than it has.

**2. Span — "Can the axes reach everything in the target space?"**

*Question:* Is every phenomenon in the domain expressible as a combination of these axes?
*Abstract test:* Does span({axes}) = V?
*Empirical test:* Total variance explained; check for systematic patterns in residuals.
*Failure mode:* A real phenomenon that no combination of axes can represent. A structural blind spot.

**3. Completeness — "Is there signal the axes miss?"**

*Question:* Does the orthogonal complement contain anything other than noise?
*Abstract test:* W⊥ = {0}?
*Empirical test:* Residual analysis; parallel analysis for additional factors beyond those proposed.
*Failure mode:* An entire unmeasured dimension. Not one blind spot — a category of blind spots.
*Note:* In finite dimensions, span and completeness are mathematically equivalent. The distinction is operationally useful because completeness is directly testable through residuals.

**4. Orthogonality — "Do the axes interfere with each other?"**

*Question:* Does each axis contribute independently, or are adjustments coupled?
*Abstract test:* Pairwise inner products zero? Off-diagonal Gram matrix entries zero?
*Empirical test:* Correlation matrix; compare varimax vs. oblique rotation.
*Failure mode:* Correlated axes. The model works but decomposition is non-unique — the same variance can be attributed to different axes depending on the order of analysis. Not fatal, but makes interpretation harder and the system less robust.
*Note:* Orthogonality is a feature, not a requirement. Non-orthogonal bases are mathematically valid. Orthogonal bases are analytically cleaner.
:::

::: {#ch-board .chapter}
::: chapter-number
Section 11
:::

::: chapter-title
Board Connections
:::

**Basis theory as validation framework.** Any architecture that decomposes a domain into named axes — personality models, management quadrants, advisory frameworks — implicitly claims those axes form a basis for some space. Basis theory converts "these feel like the right categories" into a testable mathematical claim with specific falsification criteria.

**Independence as non-redundancy.** If one module's output can be predicted from the others, it is linearly dependent — it adds no dimension to the system's coverage. The effective dimensionality is lower than the apparent dimensionality. Testing: attempt to express each module as a linear combination of the rest.

**Span as coverage.** If a class of problems exists that cannot be decomposed into the system's axes, the architecture has a structural gap. The gap isn't in execution — it's in the design. The system literally lacks the dimensions to represent those problems.

**Projection as the decomposition operation.** When a problem arrives and is "broken down along the axes," that operation is orthogonal projection. The quality of the breakdown depends on the basis. Orthogonal axes allow each component to be computed independently. Non-orthogonal axes couple the computation — changing one component's value changes what the others mean.

**The residual as diagnostic.** After decomposing a problem along all axes, the residual measures what was missed. Systematically large residuals on a class of problems indicate a missing axis. Random residuals at noise level indicate the basis is adequate.

**Gram-Schmidt as remediation.** If axes are found to be non-orthogonal but independent, Gram-Schmidt provides the procedure for constructing an equivalent orthogonal set spanning the same subspace. The new axes are linear combinations of the originals, preserving coverage while eliminating crosstalk.

**Factor analysis as the empirical gate.** To move from "we believe these are the right axes" to "the data confirms these are the right axes": define measurable indicators for each axis, collect observations, run confirmatory factor analysis, and evaluate fit. Good fit validates the proposed basis. Poor fit indicates dependence, incompleteness, or wrong dimensionality — each a specific, addressable structural problem.
:::

::: {#ch-refs .chapter}
::: chapter-number
References
:::

::: chapter-title
References
:::

1. Axler, S. (2015). *Linear Algebra Done Right.* 3rd ed. Springer. Chapters on inner product spaces, orthogonal projection, and the spectral theorem.
2. Strang, G. (2016). *Introduction to Linear Algebra.* 5th ed. Wellesley-Cambridge Press. The Four Fundamental Subspaces framework; MIT OCW 18.06, Lecture 14.
3. Lay, D. C., Lay, S. R., & McDonald, J. J. (2016). *Linear Algebra and Its Applications.* 5th ed. Pearson. The Best Approximation Theorem and orthogonal projection.
4. Wikipedia contributors. "Basis (linear algebra)," "Linear span," "Orthogonal complement," "Gram-Schmidt process," "Hilbert space," "Principal component analysis," "Factor analysis." English Wikipedia. Accessed April 2026.
5. Margalit, D. & Rabinoff, J. *Interactive Linear Algebra.* Georgia Institute of Technology. https://textbooks.math.gatech.edu/ila/. Chapters on dimension, orthogonal complements, and least squares.
6. Schilling, K., Nachtergaele, B., & Lankham, I. *Linear Algebra.* Mathematics LibreTexts. Inner product spaces and Gram-Schmidt orthogonalization.
7. Sanderson, G. (3Blue1Brown). "Linear combinations, span, and basis vectors." *Essence of Linear Algebra* video series.
8. UCLA Statistical Methods and Data Analytics. "Principal Components (PCA) and Exploratory Factor Analysis (EFA) with SPSS."
9. Shalizi, C. R. (2009). "The Truth about Principal Components and Factor Analysis." CMU 36-350 lecture notes. Distinguishing PCA as decomposition from FA as model.
10. The Analysis Factor. "The Fundamental Difference Between Principal Component Analysis and Factor Analysis." Explanation of PCA as linear combination vs. FA as measurement model.
:::
:::
:::

------------------------------------------------------------------------

::: page-footer
Loop MMT™ · Multi-Module Theory · Linear Algebra & Basis Function Theory Knowledge Pack · v1 © 2026 Shea Gunther · [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/deed.en){style="color:inherit;"}
:::
