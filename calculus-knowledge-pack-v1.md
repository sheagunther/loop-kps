# Calculus — Derivatives, Integrals, and the Language of Change

**Loop MMT™ · Multi-Module Theory**
**v1 · 10 April 2026**

---

## About This Document

Calculus is the mathematics of change. Two operations define it: differentiation (finding how fast a quantity changes) and integration (finding how much a quantity accumulates). The Fundamental Theorem of Calculus reveals these as inverse operations — the same relationship viewed from opposite directions.

This pack covers: limits and the formal ε-δ definition, derivatives and their physical meaning, the second derivative as acceleration, integration as accumulation, the Fundamental Theorem, Taylor series as local polynomial approximation, differential equations as models of evolving systems, and optimization. The Board Connection section maps these concepts to Loop MMT's operational structure with eleven structural correspondences, including the second derivative of KP quality (the observation that motivated this pack's production) and exponential decay as the evaporation mechanism identified in the Swarm Intelligence KP.

This pack does not cover multivariable calculus, vector calculus, complex analysis, or measure theory. Dependencies: Fourier Series KP, Chaos Theory KP, Information Theory KP, Nyquist-Shannon KP, Probability & Statistics KP, Systems Theory & Cybernetics KP, Fractals KP, Swarm Intelligence & Stigmergy KP.

---

## 1 · Limits

A limit describes what a function approaches as its input approaches a value — not what it equals at that value, but what it gets arbitrarily close to. The function f(x) = sin(x)/x is undefined at x = 0, but as x approaches 0, f(x) approaches 1.

The informal statement — "as x gets closer to a, f(x) gets closer to L" — served mathematicians for two centuries. Making it precise required the work of Cauchy, Bolzano, and Weierstrass across the 19th century.

### The ε-δ Definition

Karl Weierstrass, in his Berlin lectures beginning in the 1850s, formalized the modern definition. Augustin-Louis Cauchy had introduced ε-based arguments in *Cours d'Analyse* (1821), and Bernard Bolzano had independently given a rigorous ε-δ definition around 1817, though his work was not widely disseminated.

**Definition.** lim[x→a] f(x) = L means: for every ε > 0, there exists a δ > 0 such that whenever 0 < |x - a| < δ, it follows that |f(x) - L| < ε.

The structure is a challenge-response: you name any tolerance (ε) around L, and I guarantee a tolerance (δ) around a that keeps the output within your demanded range. If such a δ always exists, the limit is L.

> **KEY — Limits Replace Infinitesimals.** Newton and Leibniz reasoned about "infinitely small" quantities. George Berkeley, Bishop of Cloyne, famously mocked these in *The Analyst* (1734) as "ghosts of departed quantities." The ε-δ definition replaces "infinitely small" with "as small as you like" — a finite, testable condition. Every core concept of calculus (derivative, integral, continuity, convergence) rests on limits. They are the foundation.

### L'Hôpital's Rule

When a limit takes the indeterminate form 0/0 or ∞/∞, L'Hôpital's rule states that lim[x→a] f(x)/g(x) = lim[x→a] f'(x)/g'(x), provided the right-hand limit exists. The rule appeared in the first calculus textbook, *Analyse des Infiniment Petits* (1696), published by the Marquis de L'Hôpital but based largely on lectures by Johann Bernoulli. The rule itself was Bernoulli's discovery; L'Hôpital had contracted Bernoulli to supply mathematical results for publication.

---

## 2 · Derivatives

### Definition

The derivative of f at x is defined as:

f'(x) = lim[h→0] (f(x+h) - f(x)) / h

The ratio (f(x+h) - f(x))/h is the average rate of change over the interval [x, x+h]. The limit as h → 0 produces the instantaneous rate of change at x.

For f(x) = x²: f'(x) = lim[h→0] ((x+h)² - x²)/h = lim[h→0] (2xh + h²)/h = lim[h→0] (2x + h) = 2x.

**Geometric meaning**: the slope of the tangent line to the graph at a point. A secant line connects two points on the curve; as the second point approaches the first, the secant rotates toward the tangent.

**Physical meaning**: if f(t) is position, f'(t) is velocity — the instantaneous rate of change of position with respect to time.

### Notation

Four notation systems coexist, reflecting the field's history:

| Notation | Origin | Usage | Example |
|----------|--------|-------|---------|
| f'(x) | Lagrange | Analysis, general math | f'(3) = 6 |
| dy/dx | Leibniz | Physics, engineering | dy/dx = 2x |
| ẏ | Newton | Physics (time derivatives) | ẏ = 10t |
| Df | Operator | Functional analysis | Df(x) = 2x |

Leibniz's notation prevails because it makes the chain rule (dy/dx = dy/du · du/dx) and integration (∫ ... dx) notationally transparent.

### Differentiation Rules

| Rule | Statement | Example |
|------|-----------|---------|
| Power | d/dx[xⁿ] = nxⁿ⁻¹ | d/dx[x³] = 3x² |
| Constant multiple | d/dx[cf] = cf' | d/dx[5x²] = 10x |
| Sum | (f+g)' = f' + g' | d/dx[x² + x³] = 2x + 3x² |
| Product | (fg)' = f'g + fg' | d/dx[x sin(x)] = sin(x) + x cos(x) |
| Quotient | (f/g)' = (f'g - fg')/g² | |
| Chain | d/dx[f(g(x))] = f'(g(x))·g'(x) | d/dx[sin(x²)] = 2x cos(x²) |

The **chain rule** is structurally important: the rate of change of a composition equals the product of the rates at each stage. If y depends on u which depends on x, then dy/dx = (dy/du)(du/dx). This is the calculus of nested dependencies.

### Mean Value Theorem

If f is continuous on [a,b] and differentiable on (a,b), there exists c in (a,b) where f'(c) = (f(b) - f(a))/(b - a). Somewhere in the interval, the instantaneous rate equals the average rate. This is the bridge between local information (derivative at a point) and global behavior (change over an interval). Lagrange published the first rigorous proof.

### Differentiability vs. Continuity

Differentiability implies continuity, but not vice versa. The function f(x) = |x| is continuous at x = 0 but not differentiable there — the graph has a corner, and no single tangent line exists.

Weierstrass's 1872 function pushed this gap to the extreme: a function continuous everywhere but differentiable nowhere. Every point on the graph is a "corner." Poincaré called it "an outrage against common sense." Hermite called it "a deplorable evil." It demonstrated that continuity and smoothness, which intuition conflates, are logically independent properties.

> **WARN — Continuity ≠ Smoothness.** Not every continuous function has a derivative. Differentiability requires the absence of corners, cusps, and vertical tangents — a strictly stronger condition than mere continuity.

---

## 3 · The Second Derivative

### Definition and Interpretation

The second derivative is the derivative of the derivative:

f''(x) = d/dx[f'(x)]

It measures the rate of change of the rate of change.

| Order | Symbol | If f(t) = position | Name |
|-------|--------|-------------------|------|
| 0th | f(t) | Where you are | Position |
| 1st | f'(t) | How fast you're moving | Velocity |
| 2nd | f''(t) | How fast your speed is changing | Acceleration |
| 3rd | f'''(t) | How fast your acceleration is changing | Jerk |

Acceleration is what you feel when a car speeds up or brakes. Jerk is the sudden onset of braking — the lurch.

### Concavity

The second derivative determines the curvature of a graph:

**f''(x) > 0**: the graph is concave up (bends upward, like a cup). The first derivative is increasing. If the function is growing, it's growing at an accelerating rate.

**f''(x) < 0**: the graph is concave down (bends downward). The first derivative is decreasing. If the function is growing, the growth is decelerating.

An **inflection point** is where f'' changes sign — where the curve switches between concave up and concave down. At an inflection point, the acceleration reverses direction.

> **KEY — This Is What the Operator Observed.** "The KPs are getting better, and the rate of improvement is itself speeding up" is the statement f'(n) > 0 and f''(n) > 0, where f(n) is a quality metric for pack number n. The quality curve is concave up. Each pack improves by more than the previous improvement. This is measurable: plot Board Connection density, cross-pack references, or fact-check correction rates against pack index. If the curve bends upward, the second derivative is positive. The swarm KP explains the mechanism (stigmergic positive feedback from richer environment). This pack provides the formal language to describe it.

### The Second Derivative Test

At a critical point where f'(c) = 0:
- f''(c) > 0 → local minimum (the curve is concave up — a valley)
- f''(c) < 0 → local maximum (the curve is concave down — a hilltop)
- f''(c) = 0 → test fails; further analysis needed

---

## 4 · Integration

### The Problem

Differentiation answers: given a quantity, what's its rate of change? Integration answers the inverse: given a rate of change, what's the total accumulation?

If you know velocity at every instant, integration recovers total distance. If you know the rate of KP quality improvement across sessions, integration gives the cumulative quality of the corpus.

### Riemann Sums

Bernhard Riemann (1826–1866) formalized the definite integral as a limit of sums. Partition an interval [a,b] into subintervals. On each, approximate the area under the curve with a rectangle. Sum the rectangles. Take the limit as the partition refines:

∫[a,b] f(x)dx = lim[n→∞] Σᵢ f(xᵢ)Δxᵢ

The integral is the signed area between the curve and the x-axis: positive above, negative below.

### Antiderivatives

An antiderivative of f is a function F such that F'(x) = f(x). The indefinite integral ∫f(x)dx denotes the family of all antiderivatives, differing by a constant:

| Function | Antiderivative |
|----------|---------------|
| xⁿ (n ≠ -1) | xⁿ⁺¹/(n+1) + C |
| 1/x | ln|x| + C |
| eˣ | eˣ + C |
| sin(x) | -cos(x) + C |
| cos(x) | sin(x) + C |

The constant C is unavoidable: if F'(x) = f(x), then (F(x) + 7)' = f(x) too. Integration loses the constant that differentiation destroys.

---

## 5 · The Fundamental Theorem of Calculus

The Fundamental Theorem of Calculus (FTC) is the central result of the subject. It connects integration and differentiation, revealing them as inverse operations.

**Part 1.** If f is continuous on [a,b] and F(x) = ∫[a,x] f(t)dt, then F'(x) = f(x).

The derivative of the integral gives back the original function. Differentiation undoes integration.

**Part 2.** If F is any antiderivative of f on [a,b], then ∫[a,b] f(x)dx = F(b) - F(a).

Total accumulation = antiderivative at the endpoint minus antiderivative at the start. No Riemann sums needed.

> **KEY — Why This Is Fundamental.** Before the FTC, computing areas (integration) and computing slopes (differentiation) were separate problems with separate techniques. The FTC reveals them as the same problem in two directions. James Gregory proved a restricted version around 1668. Isaac Barrow proved a more general form around 1670; Newton, his student, developed the surrounding theory. Leibniz published his account in 1693. The theorem made calculus a unified subject instead of two disconnected toolkits.

Practical impact: integration by antiderivatives is vastly faster than computing Riemann sums. Conceptual impact: production at a rate and the resulting accumulation are mathematically connected. This is the relationship between writing packs (rate) and having a corpus (total).

---

## 6 · Taylor Series

### Local Approximation by Polynomials

Any function whose derivatives all exist at a point can be approximated near that point by a polynomial. Each additional term in the polynomial matches one more derivative of the original function. Brook Taylor published this in *Methodus Incrementorum Directa et Inversa* (1715), though Newton and Leibniz had known related results earlier. Lagrange first recognized its full importance in 1772, calling it the basic principle of differential calculus.

### The Formula

f(x) = f(a) + f'(a)(x-a) + f''(a)(x-a)²/2! + f'''(a)(x-a)³/3! + ... = Σ[n=0,∞] f⁽ⁿ⁾(a)(x-a)ⁿ/n!

When centered at a = 0, this is called a Maclaurin series (after Colin Maclaurin, though Taylor had already treated this case).

### Important Series

| Function | Maclaurin Series | Converges for |
|----------|-----------------|---------------|
| eˣ | 1 + x + x²/2! + x³/3! + ... | All x |
| sin(x) | x - x³/3! + x⁵/5! - ... | All x |
| cos(x) | 1 - x²/2! + x⁴/4! - ... | All x |
| ln(1+x) | x - x²/2 + x³/3 - ... | -1 < x ≤ 1 |
| 1/(1-x) | 1 + x + x² + x³ + ... | |x| < 1 |

The radius of convergence — the distance from the center within which the series converges — varies by function. The exponential and trigonometric series converge everywhere. The geometric series converges only for |x| < 1.

> **TIP — How Computers Calculate Transcendental Functions.** When a calculator computes sin(0.5), it evaluates a truncated Taylor series: sin(x) ≈ x - x³/6 + x⁵/120 - ... Essentially every transcendental function computed by digital hardware uses Taylor polynomials (or the closely related CORDIC algorithm). Taylor series are the bridge between abstract mathematical functions and computable arithmetic.

### Relation to Fourier Series

Taylor series approximate locally: near a single point, using polynomials. Fourier series approximate globally: across an entire interval, using sines and cosines. Both decompose functions into simpler components. The Fourier Series KP covers the complementary approach.

---

## 7 · Differential Equations

A differential equation relates a function to its derivatives. Where the algebraic equation x² - 4 = 0 asks "what number?", the differential equation dy/dx = 2y asks "what function?" The answer is not a number but a function: y = Ce²ˣ.

**Ordinary differential equations** (ODEs) involve one independent variable. **Partial differential equations** (PDEs) involve multiple independent variables and partial derivatives.

### First-Order Examples

**Exponential growth/decay**: dy/dt = ky, solution y = y₀eᵏᵗ. If k > 0: population growth, compound interest, viral spread. If k < 0: radioactive decay, Newton's cooling, pheromone evaporation. The defining feature: the rate of change is proportional to the current value.

**Logistic growth**: dy/dt = ky(1 - y/K). Growth that slows as y approaches a carrying capacity K. The solution is S-shaped: exponential at first, then decelerating, asymptotically approaching K.

### Second-Order: Oscillation

The spring-mass system mu'' + ku = 0 has solution u(t) = A cos(ωt + φ) where ω = √(k/m). The system oscillates indefinitely. Adding a damping term (mu'' + bu' + ku = 0) introduces exponential decay of the oscillation amplitude. The discriminant b² - 4mk determines whether the system oscillates with decay, overdamps without oscillation, or sits at the critical boundary between the two.

### Applications

Newton's second law F = ma is a second-order ODE: force equals mass times the second derivative of position. Virtually every dynamical system in physics, engineering, biology, and economics is described by differential equations. The SIR model in epidemiology, circuit analysis in electrical engineering, predator-prey dynamics in ecology — all are systems of ODEs.

> **NOTE — The 200-Year Gap.** Newton and Leibniz invented calculus in the late 1600s. It was applied to physics, astronomy, and engineering for nearly two centuries before Cauchy and Weierstrass established rigorous foundations in the 1800s. Utility preceded proof. The calculus worked before anyone could explain why it worked. This is not unique to calculus, but it is the most dramatic example in mathematics.

---

## 8 · Optimization

### Critical Points and Tests

At a local maximum or minimum, the derivative is zero: f'(c) = 0. These are **critical points**. (A horizontal tangent means the function has momentarily stopped rising or falling.)

**First derivative test**: if f' changes from positive to negative at c, local maximum. Negative to positive: local minimum.

**Second derivative test**: at a critical point c, if f''(c) > 0, the function is concave up (valley = local minimum). If f''(c) < 0, concave down (hilltop = local maximum).

### Constrained Optimization

Real problems have constraints. Lagrange multipliers (Joseph-Louis Lagrange, 1788) handle optimization subject to constraints by requiring that the gradients of the objective function and constraint be parallel: ∇f = λ∇g. The scalar λ measures how much the optimal value would improve if the constraint were relaxed.

### Where This Appears

Optimization is where calculus becomes engineering. Minimizing cost, maximizing throughput, finding the shape that resists load with the least material, choosing the session structure that produces the most useful output per unit of context consumed. Any "what's the best?" question is, at its mathematical core, an optimization problem.

---

## 9 · History

### Ancient Precursors

Archimedes of Syracuse (~287–212 BC) computed areas under parabolas and volumes of spheres using the **method of exhaustion** — approximating curved regions with polygons of increasing refinement. He also found the tangent to a spiral, anticipating differentiation. Abu Ali ibn al-Haytham (Alhazen, c. 965–1040), working in Cairo, integrated a fourth-degree polynomial — the earliest known such computation.

### Newton and Leibniz

Isaac Newton (1643–1727) developed his "method of fluxions" during the plague years of 1665–1666, when he was sent home from Cambridge. His first systematic account, *De Analysi per Aequationes Numero Terminorum Infinitas*, was composed in 1669 and circulated among colleagues, but not published until 1711. The *Philosophiæ Naturalis Principia Mathematica* (1687) used calculus to derive planetary motion from the inverse-square law of gravitation, though Newton's geometric style obscured the calculus.

Gottfried Wilhelm Leibniz (1646–1716) developed calculus independently in the mid-1670s, publishing in 1684 in the *Acta Eruditorum*. His notation — d for differential, ∫ (an elongated S, for summa) for integral — proved far more expressive than Newton's dots and was adopted across continental Europe.

The ensuing priority dispute was bitter. The Royal Society, under Newton's influence, declared him the sole discoverer in 1715. Modern consensus: independent invention, Newton's work preceding Leibniz's by roughly a decade, Leibniz's publication preceding Newton's. Consequence: British mathematics stagnated for a century, loyal to Newton's less flexible notation, while continental mathematics flourished with Leibniz's.

### The 18th Century

Jakob Bernoulli (1655–1705) and Johann Bernoulli (1667–1748), working with Leibniz's methods, developed most of the standard calculus curriculum: differentiation rules, integration techniques, applications to mechanics and geometry. Johann's student Leonhard Euler (1707–1783) dominated 18th-century mathematics, extending calculus to complex functions and producing foundational work in virtually every branch.

The first calculus textbook, *Analyse des Infiniment Petits* (1696), was published by the Marquis de L'Hôpital based on Johann Bernoulli's lectures. Brook Taylor added *Methodus Incrementorum Directa et Inversa* (1715), introducing the Taylor series and the calculus of finite differences.

### Rigorization

For two centuries, calculus rested on informal reasoning about infinitesimals. Cauchy (1789–1857) began the rigorization with *Cours d'Analyse* (1821), introducing inequality-based proofs and precise definitions of limit, continuity, and convergence. Bolzano (1781–1848) achieved similar results independently. Karl Weierstrass (1815–1897), who spent his early career as a secondary school teacher and did not obtain a university position until his early forties, completed the program with the ε-δ definition of limits.

Weierstrass's 1872 continuous-but-nowhere-differentiable function forced the mathematical community to confront the gap between intuition and logic. It remains a landmark of analysis and a precursor to fractal geometry.

| Thinker | Dates | Contribution |
|---------|-------|-------------|
| Archimedes | ~287–212 BC | Method of exhaustion; tangent to spiral |
| Newton | 1643–1727 | Fluxions; *Principia*; inverse-square law |
| Leibniz | 1646–1716 | Notation (d, ∫); general calculus algorithm |
| Jakob Bernoulli | 1655–1705 | Differentiation rules; applications |
| Johann Bernoulli | 1667–1748 | Integration techniques; L'Hôpital's rule |
| Euler | 1707–1783 | Elementary functions; complex analysis |
| Taylor | 1685–1731 | Taylor series (1715) |
| Cauchy | 1789–1857 | *Cours d'Analyse*; ε proofs |
| Bolzano | 1781–1848 | Independent rigorous definitions |
| Riemann | 1826–1866 | Riemann integral |
| Weierstrass | 1815–1897 | ε-δ definition; pathological functions |

---

## 10 · Board Connection

### §10.1 — Derivative as Improvement Rate

If Q(n) measures the quality of Knowledge Pack number n, then Q'(n) ≈ ΔQ/Δn is the improvement rate — how much better each pack is than its predecessor. Candidate metrics: Board Connection density (correspondences per pack), cross-pack dependency count, fact-check correction count (lower = cleaner process). Plotting Q against n and computing the slope gives the first derivative.

### §10.2 — Second Derivative as Quality Acceleration

The operator's observation that "packs are getting better faster" is Q''(n) > 0. The quality curve is concave up: each increment of improvement exceeds the previous one. The swarm KP explains the mechanism — stigmergic positive feedback from a richer document environment. This pack names the phenomenon: positive second derivative of quality with respect to pack index.

### §10.3 — Integration as Cumulative Corpus Value

The total value of the corpus is the integral V = ∫[1,N] Q(n)dn — accumulated quality across all packs, not just the quality of the latest one. A pack of moderate individual quality still adds positive area under the curve. This framing makes explicit why breadth matters: every positive contribution increases the integral.

### §10.4 — The FTC Connects Production and Corpus

The rate of production (quality added per session) and the cumulative corpus (total quality) are related by the Fundamental Theorem. Knowing the production rate function lets you compute corpus totals by integration. Knowing corpus totals as a function of session count lets you recover the production rate by differentiation. Production and accumulation are two views of the same mathematical object.

### §10.5 — Taylor Approximation as Instance Reconstruction

A new Claude instance reconstructs the project from loaded documents — a local approximation of the full project state. This is a Taylor expansion centered at the most recent session. The EOD handoff provides f(a) (current state). Mesh documents provide f'(a) (trajectory), f''(a) (acceleration), and higher derivatives (deeper historical patterns). Accuracy degrades with distance from center — events ten sessions ago are reconstructed less reliably than events from the last session. The RFI experiment demonstrated the failure mode: confident confabulation from an insufficient expansion, where partial context (a few Taylor terms) produced a worse reconstruction than no context at all.

### §10.6 — Differential Equations as System Dynamics

If corpus quality grows proportionally to current richness (richer context → better packs → richer context), the model is dQ/dt = kQ — exponential growth. Adding a carrying capacity (context window limits, operator bandwidth, formalization debt) gives the logistic equation dQ/dt = kQ(1 - Q/K). The chaos report's warnings about formalization debt are, in this frame, warnings that Q is approaching K: the system nears carrying capacity without structural expansion.

### §10.7 — Optimization of Session Allocation

Each session involves implicit optimization: maximize productive output subject to constraints (context depth, operator energy, time). The optimal allocation is where the marginal return on context investment equals the marginal cost — the first-order condition f'(x) = 0. The operator performs this intuitively; the calculus provides the framework to formalize it.

### §10.8 — Inflection Points as Qualitative Shifts

An inflection point is where f'' changes sign — where acceleration becomes deceleration. In the project's history: the shift from collecting board members to producing with them, the transition from experimental KP production to the standardized 10-step method, the moment the swarm KP revealed the system's own coordination mechanism. Each was a point where the project's curvature changed direction.

### §10.9 — Chain Rule as Pipeline Composition

The 10-step KP production method is a composition of functions: research → compilation → plan → draft → fact-check → rewrite → ... The chain rule says the total derivative is the product of the derivatives at each stage. A weakness at any stage multiplies through the pipeline. If fact-checking catches 90% of errors and self-review catches 90% of remaining errors, the pipeline passes 1% of original errors. The chain rule formalizes how compositional quality propagates.

### §10.10 — Exponential Decay as Evaporation

The swarm KP identified that the corpus lacks a forgetting mechanism. Exponential decay y = y₀e⁻ᵏᵗ is the standard evaporation model. The constant k controls how fast traces fade. Currently k = 0 for all documents: nothing decays. Setting k > 0 for specific document types (mesh reports might decay faster than core specifications) would implement the evaporation the swarm system requires. The optimal k for each document class is itself an optimization problem.

### §10.11 — Limits as System Asymptote

What does the corpus approach as sessions → ∞? If Loop MMT has a limiting state — a fully formalized, fully connected, maximally consistent body of knowledge — that state is the limit. The chaos report measures the gap between current state and that limit. Formalization debt is |corpus - lim|. Whether the system converges (approaches the limit) or diverges (produces chaos faster than formalization can contain it) is the fundamental long-term question, and it is a question about limits.

---

## 11 · References

- Barrow, I. *Lectiones Geometricae*. London, 1670.
- Berkeley, G. *The Analyst*. London, 1734.
- Cauchy, A.-L. *Cours d'Analyse de l'École Royale Polytechnique*. Paris, 1821.
- Euler, L. *Institutiones Calculi Differentialis*. St. Petersburg, 1755.
- Grabiner, J. V. "Who Gave You the Epsilon? Cauchy and the Origins of Rigorous Calculus." *American Mathematical Monthly* 90, no. 3 (March 1983): 185–194.
- L'Hôpital, G. F. A. de. *Analyse des Infiniment Petits pour l'Intelligence des Lignes Courbes*. Paris, 1696.
- Leibniz, G. W. "Nova Methodus pro Maximis et Minimis." *Acta Eruditorum*. Leipzig, 1684.
- Newton, I. *De Analysi per Aequationes Numero Terminorum Infinitas*. Composed 1669; published London, 1711.
- Newton, I. *Philosophiæ Naturalis Principia Mathematica*. London, 1687.
- Riemann, B. "Über die Darstellbarkeit einer Function durch eine trigonometrische Reihe." Habilitationsschrift, University of Göttingen, 1854.
- Stewart, J. *Calculus: Early Transcendentals*. 8th ed. Boston: Cengage, 2015.
- Taylor, B. *Methodus Incrementorum Directa et Inversa*. London, 1715.
- Thompson, S. P. *Calculus Made Easy*. London: Macmillan, 1910.
- Weierstrass, K. Berlin Lectures on Analysis, 1860s–1890s. Circulated as student notes; not published under Weierstrass's supervision.
