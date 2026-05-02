# What Am I Flattening? — Dimensional Reduction, Lossy Compression, and the Cost of Simplification

**Loop MMT™ · Knowledge Pack · v1 · 11 April 2026**

---

## About This Document

Dimensional reduction, lossy compression, and the cost of simplification. This pack is a reference on what happens when high-dimensional things are forced into lower dimensions — in mathematics (PCA, rate-distortion theory), philosophy (Korzybski, Borges, Box), physics (Anderson's emergence), political science (Scott's legibility), and feminist epistemology (Haraway's situated knowledges). The central question, "what am I flattening?", applies to every summary, label, model, diagram, handoff, and abstraction the methodology produces. Fourteen sources across six disciplines. One question throughout: what was lost, and does the consumer know?

---

## 1 · The Central Question

Every representation is a reduction. A meeting summary compresses hours to minutes. A label compresses a person to a category. A diagram compresses a system that operates across dozens of interacting dimensions to marks on a flat surface. An equation compresses the motion of every macroscopic object into three symbols. None of these compressions is optional — the uncompressed version is too large to think with. Borges' fictional cartographers built a 1:1 map and found it useless. We compress because we must.

The question is not whether to compress. It is what you destroy when you do — and whether the destruction matters. This pack follows that question through mathematics, information theory, philosophy, political science, and cognitive science. The structural operation is the same in every domain: project from more dimensions to fewer, and lose whatever falls outside the projection. The pack exists to make that loss visible.

---

## 2 · Projection: The Mathematics of Flattening

**Principal Component Analysis** is the canonical technique for dimensional reduction. Karl Pearson laid the mathematical foundation in 1901; Harold Hotelling formalized PCA as a statistical method in 1933. The idea: given data distributed across many dimensions, find the directions of greatest variance and project the data onto those directions. The first principal component captures the axis of maximum spread. Each subsequent component captures the maximum remaining variance, orthogonal to all previous components. To reduce dimensions, keep the top components and discard the rest.

This is mathematically optimal: PCA minimizes reconstruction error for a given number of retained components. But "optimal" means "loses the least variance." Variance is a specific measure of importance. A feature with low variance but high causal significance — say, a rare but critical failure mode — will be among the first things discarded. The projection looks right and misses what matters.

> **KEY:** The axes you keep are a statement about what matters. PCA's implicit statement: "what matters is what varies the most." This is a reasonable default and nothing more. Different methods — t-SNE (preserves local neighborhoods, destroys global structure), MDS (preserves pairwise distances), factor analysis (assumes latent causes) — make different choices about what to preserve and what to sacrifice. Each applied to the same data produces a different compression. The choice of method is the first act of judgment in any reduction.

PCA as a *thinking tool* (not just a statistical technique): when you call someone "a nurse," you are performing PCA with one component. You have found one axis (occupation) and projected a multidimensional person onto it, discarding everything orthogonal. When a KPI dashboard presents five numbers for a business with thousands of moving parts, it has retained five principal components and thrown away the rest. The question is whether the discarded components were noise — or load-bearing structure. (Cross-reference: *Linear Algebra & Basis Theory KP*.)

---

## 3 · Lossy Compression: Shannon's Framework

Claude Shannon's 1948 paper "A Mathematical Theory of Communication" proved that every information source has an entropy rate — the minimum bits per symbol for lossless compression. You cannot go below entropy without losing information. This is a mathematical limit, not a practical one. (Cross-reference: *Information Theory KP*, Section 4.)

**Lossy compression** accepts distortion in exchange for rates below entropy. Shannon's **rate-distortion theory**, introduced in 1948 and formalized in a 1959 paper, quantifies the tradeoff: the rate-distortion function R(D) gives the minimum bit rate achievable at distortion level D. The function is convex and monotonically decreasing — better fidelity always costs more, and there are no free reductions.

The critical design choice is the **distortion measure**. In signal processing, mean squared error is the default. But Blau and Michaeli (2019) demonstrated a three-way tradeoff between rate, distortion, and perceptual quality: minimizing mathematical error can degrade how the result looks to a human, and vice versa. The "right" distortion measure depends on who consumes the output and what they need from it.

> **NOTE:** Rate-distortion theory applies to signal processing, but its conceptual structure applies everywhere. Every summary has an implicit distortion measure — the summarizer's judgment about what counts as "close enough." Every label chooses which features to preserve and which to discard. The difference: in signal processing, the compressor and consumer typically agree on the distortion measure. In human communication, they usually don't — and neither is aware of the disagreement.

| Concept | Definition | The Flattening Question |
|---|---|---|
| Entropy H(X) | Minimum bits/symbol for lossless representation | The floor below which you must start losing |
| Rate R | Bits per symbol actually used | How much you compressed |
| Distortion D | Measured error between original and reconstruction | What you lost, quantified |
| R(D) | Minimum rate for a given maximum distortion | The cheapest possible cost for a given compression |
| Data processing inequality | Processing cannot increase information | Compressing a compression only loses more |

---

## 4 · The Map and the Territory

Alfred Korzybski (1879–1950), the founder of General Semantics, presented three premises in his 1931 paper to the American Association for the Advancement of Science, later published in *Science and Sanity* (1933). First: the map is not the territory. Second: the map does not represent all of the territory. Third: the map is self-reflexive — maps reference other maps at higher levels of abstraction.

The second premise carries the weight. Every map omits. The London Underground map, designed by Harry Beck in 1931, distorts geographic distance to clarify connections between stations. It serves Tube navigation brilliantly and walking navigation terribly. The distortion is the feature. But the distortion is invisible to anyone who navigates only by the map. **The map's omissions are invisible to anyone who only has the map.**

Jorge Luis Borges' 1946 one-paragraph story "On Exactitude in Science" takes this to the limit. An empire's cartographers, pursuing perfect accuracy, create a map at 1:1 scale — a map the size of the territory. Subsequent generations find it useless and abandon it to decay. Lewis Carroll had the same idea: a map "with the scale of a mile to the mile," whose users resort to "the country itself, as its own map."

> **PHI:** A lossless representation of a thing *is* the thing. It therefore has no function as a representation — no compression, no abstraction, no portability, no utility. Maps are useful precisely because they flatten. Borges proves this by reductio. Box completes the argument from the other direction: "Essentially, all models are wrong, but some are useful" (Box & Draper, 1987). A useful model is wrong in the right ways — it discards what doesn't matter for the purpose at hand. The synthesis: the question is never "is this model wrong?" (it always is). The question is "is it wrong in ways that matter?"

---

## 5 · Emergence: What Reduction Destroys

P.W. Anderson (1923–2020), Nobel laureate in Physics, published "More Is Different" in *Science* in 1972. His target was a specific overreach of reductionism: the assumption that because everything obeys fundamental physical laws, understanding those laws is sufficient to understand everything built from them. Anderson's counter: the reductionist hypothesis does not imply its constructionist inverse. You cannot start from particle physics and derive psychology, not because psychology violates physical law, but because at each level of complexity, entirely new properties emerge through symmetry breaking.

Superconductivity is not a property of individual electrons. Consciousness is not a property of individual neurons. Traffic patterns are not a property of individual cars. Culture is not a property of individual people. These properties exist only at higher levels of organization — they inhabit dimensions that do not exist at the component level.

| Scale | Emerges | Cannot Be Derived From |
|---|---|---|
| Many-body physics | Phase transitions, superconductivity | Single-particle quantum mechanics |
| Chemistry | Molecular structure, reaction kinetics | Atomic physics alone |
| Molecular biology | Self-replication, metabolism | Chemistry alone |
| Neuroscience | Consciousness, perception | Individual neuron behavior |
| Social science | Markets, institutions, culture | Individual psychology |

> **WARN:** Reducing a system to a list of its components destroys the relationships between components — and emergent properties live in those relationships. A city inventoried as buildings, roads, and people is not a city. The city is what happens between them. This is the sharpest limit on dimensional reduction: some properties only exist in the higher dimension and are annihilated by projection. (Cross-reference: *Systems Theory & Cybernetics KP*.)

---

## 6 · The Curse of Dimensionality

Richard Bellman (1920–1984) identified what he called the "curse of dimensionality" while working on dynamic programming — first in his 1957 book *Dynamic Programming* and elaborated in *Adaptive Control Processes* (1961). The curse is a family of phenomena that make high-dimensional spaces behave in ways that violate every intuition trained in two or three dimensions.

**Distance concentration:** as dimensions increase, the ratio of nearest-neighbor distance to farthest-neighbor distance approaches 1. In sufficiently high dimensions, every point is approximately the same distance from every other point. The concept "nearest neighbor" becomes meaningless.

**Volume concentration:** the volume of a hypersphere inscribed in a hypercube shrinks toward zero as dimensions grow. In 100 dimensions, nearly all the volume of the cube is in its "corners."

**Sparsity:** to cover a high-dimensional space with the same density of samples as in low dimensions, you need exponentially more data. A common rule of thumb: at least 5 samples per dimension. At 100 dimensions, that is 500 — but to uniformly sample the space at even modest resolution, you would need data growing as 10^d.

> **KEY:** The curse proves that some high-dimensional structures resist meaningful simplification — distances break, volumes vanish, samples are always inadequate. But it also proves why we *must* simplify: working directly in the high-dimensional space is impossible precisely because our tools fail there. We are forced to project. The projection will lose something. The question — the only question this pack has — is what.

---

## 7 · The Politics of Flattening

### Legibility

James C. Scott (1936–2024) published *Seeing Like a State* in 1998 — an account of what happens when institutions simplify complex realities to make them controllable. Scott's term is **legibility**: states arrange populations into forms that simplify governance. Permanent surnames replace patronymics. Cadastral surveys replace informal land tenure. Grid cities replace organic neighborhoods. Monoculture forests replace diverse ecosystems.

Each simplification projects a high-dimensional social or ecological system onto the axes the state cares about. Everything orthogonal is discarded. The loss is not collateral damage; it is the mechanism. Simplification *is* how the state sees.

Scott's sharpest example: 18th-century Prussian scientific forestry. Diverse forests were replanted as monoculture rows — single species, uniform spacing, legible to measurement and optimized for timber yield. First generation: record yields. Second generation: catastrophic decline. The compression — forest reduced to "board-feet of lumber per hectare" — had discarded the soil organisms, companion species, and mycorrhizal networks that sustained the ecosystem. Everything orthogonal to the state's chosen axis turned out to be load-bearing.

> **KEY:** The person doing the flattening captures the benefit (governance, efficiency, scalability). The thing being flattened bears the cost (loss of diversity, local knowledge, adaptive capacity). Simplification is not neutral. It is an exercise of power — choosing which dimensions survive is choosing whose reality counts.

### The God Trick

Donna Haraway's 1988 essay "Situated Knowledges" provides the epistemological frame. Haraway attacks what she calls **the god trick**: the claim to see everything from nowhere — a disembodied, universal perspective. This perspective is itself a position, she argues, but one that conceals its own situatedness.

All knowledge is partial, embodied, located. "Only partial perspective promises objective vision." Objectivity is not the view from everywhere; it is accountable positioning — knowing where you stand, what you can see, and what you cannot.

Applied to this pack's question: every dimensional reduction is performed from somewhere. The choice of axes, the choice of distortion measure, the choice of what counts as signal and what counts as noise — all are situated. Claiming that a compression is "objective" is the god trick applied to information theory. The honest compression declares its position. (Cross-reference: *Perspectivism & Triangulation KP*.)

---

## 8 · People as Projections

Stereotyping is dimensional reduction applied to persons. When you categorize someone — by occupation, nationality, diagnosis, demographic — you project a high-dimensional individual onto one or a few axes and discard the rest. The operation is cognitively necessary: human working memory cannot maintain a full-dimensional model of every person simultaneously. Categories are lossy compression in service of bounded rationality.

The damage is not in the category. It is in forgetting that the category is a compression. Within-category variation — the way every nurse differs from every other nurse along every axis except the one retained — is erased. If the downstream consumer of the label never encounters the full-dimensional person, the erased variance ceases to exist in their model. The projection has replaced the person.

Institutional systems scale this operation. A **credit score** compresses financial history to three digits and uses those digits to determine access to housing, employment, and credit. A **medical diagnosis** compresses a patient to a condition; treatment follows the label. A **census category** compresses continuous human variation into discrete bins that then determine resource allocation and political representation. In each case, the compression serves the institution that performs it and constrains the person it is performed upon. (Cross-reference: *Cognitive Bias & Metacognition KP*. Cross-reference: *Ethics & Moral Reasoning KP*.)

> **WARN:** The asymmetry is structural: the compressor gains efficiency; the compressed loses dimensions. This is Scott's legibility applied to individuals. The test for whether a categorization has crossed from useful abstraction to harmful flattening: does the compressed party have recourse to restore the discarded dimensions when they matter?

---

## 9 · Productive Flattening

Compression is not inherently harmful. Abstraction — deliberate, purposeful reduction — is how humans build understanding of complex systems. Every useful tool is a productive compression.

> **TIP — Three Questions Before Flattening:**
> 1. **What am I losing?** Name the discarded dimensions. If you cannot name them, you do not understand your own compression.
> 2. **Is the loss acceptable for this purpose?** "Acceptable" is purpose-relative and consumer-relative. Acceptable to whom?
> 3. **Does the consumer know what was discarded?** If not, they will treat the map as the territory — and they will be wrong without knowing it.

**Scientific models** are the paradigm. Newton's F=ma is a catastrophic compression of physical reality — it ignores relativity, quantum mechanics, thermodynamics, and nearly everything else. It is also one of the most useful equations ever written, because it preserves the relationships that matter for mechanical engineering and discards what doesn't. The consumers (engineers) know the boundaries.

**Programming abstractions** hide implementation behind interfaces. A function call compresses hundreds of lines into a name and parameters. An API compresses an entire system into an input-output contract. The value is the compression.

**Edward Tufte's data-ink ratio** formalizes productive compression for visualization: every element of a display should serve the data. Non-data-ink is noise — dimensions that carry no information but create the illusion of content. Good visualization is deliberate dimensional reduction: maximum signal, minimum noise. But Tufte also catalogues how bad compressions deceive: distorted axes, truncated scales, misleading aggregations.

The through-line: productive flattening is not characterized by the absence of loss (there is always loss). It is characterized by three properties: the loss is known, the loss is acceptable for the purpose, and the downstream consumer is informed.

---

## 10 · Board Connection: Loop MMT and the Flattening Problem

Loop MMT is a methodology built on compression. Documents compress sessions. Handoffs compress days. KP abstracts compress packs. The operator's single-word instructions compress multi-step intentions. SNR governs deliverables by demanding that noise be removed — which is to say, by demanding dimensional reduction. The methodology works because these compressions are productive. It fails when they are not. This pack provides the vocabulary to tell the difference.

**SNR is deliberate flattening.** Every SNR-governed decision chooses what to preserve (signal) and what to discard (noise). The distinction between signal and noise is a distortion measure — it defines what counts as "close enough." The operator's values define that measure. FWW(C) exists partly as a check — the engagement ceiling ensures that SNR does not flatten away the dimensions that keep people reading.

**Handoffs are low-dimensional projections.** A session is high-dimensional: it includes decisions, but also energy, tone, false starts, rejected ideas, debates that changed how a problem was framed. A handoff captures decisions, deliverables, status, and next steps. Everything else is lost. The Context Mesh — five observer documents from different positions — is explicitly tomographic: multiple projections from different angles, partially recovering the higher-dimensional session. No single document is the session. The mesh is less wrong. (Cross-reference: *Tomographic Reconstruction KP*. Cross-reference: *Holography KP*.)

**Four Corners is a four-axis projection of quality.** FBD, FWW(C), STP, SNR — four axes along which every deliverable is evaluated. Are these four axes independent? Do they span the quality space? Or is quality a higher-dimensional phenomenon that Four Corners projects onto four components, losing whatever falls outside? The Linear Algebra & Basis Theory KP provides the formal tools to test this. This pack does not answer those questions. It provides the frame for asking them.

**The operator's maximal compression.** When Shea says "Go," he compresses an instruction set into a single syllable. The receiving instance reconstructs full context from that syllable plus everything in memory, history, and project files. What's lost? Nuance, priority weighting, unstated constraints. The Prompt Amplification Protocol exists because this loss is real. (Cross-reference: *Human Frame KP*.)

**KP abstracts are lossy compression of full packs.** Every abstract compresses 5,000+ words to 50. What survives: scope, domain, connection count. What is lost: arguments, examples, callouts, nuance — everything that makes the pack useful. A board member who loads the index but not the pack navigates by the abstract alone. The abstract's omissions are invisible to them. This is Korzybski's second premise operating inside the methodology.

This document is itself a compression. The research behind it is three times longer. The sources behind the research run to thousands of pages. What was lost? Mathematical formalism, historical depth, counterarguments, the texture of individual thinkers' prose. Was the loss acceptable? That depends on whether the document serves its purpose: giving you a framework for asking "what am I flattening?" before you flatten. If it does, the compression was productive. If it doesn't, you should load the sources. Either way, you now know something was lost — and that knowledge is the pack's entire point.

---

## References

| Source | Year | Contribution to This Pack |
|---|---|---|
| Anderson, P.W. "More Is Different." *Science*, 177(4047), 393–396. | 1972 | Emergence; reduction ≠ construction |
| Bellman, R.E. *Dynamic Programming*. Princeton University Press. | 1957 | Curse of dimensionality (coined) |
| Bellman, R.E. *Adaptive Control Processes*. Princeton University Press. | 1961 | Curse of dimensionality (elaborated) |
| Blau, Y. & Michaeli, T. "Rethinking Lossy Compression." *ICML*. | 2019 | Rate-distortion-perception tradeoff |
| Borges, J.L. "On Exactitude in Science." *Los Anales de Buenos Aires*. | 1946 | The 1:1 map parable |
| Box, G.E.P. "Science and Statistics." *JASA*, 71(356), 791–799. | 1976 | "All models are wrong" |
| Box, G.E.P. & Draper, N.R. *Empirical Model-Building and Response Surfaces*. Wiley. | 1987 | "...but some are useful" |
| Haraway, D. "Situated Knowledges." *Feminist Studies*, 14(3), 575–599. | 1988 | Partial perspective; the god trick |
| Hotelling, H. "Analysis of a complex of statistical variables." *J. Ed. Psych.*, 24(6). | 1933 | PCA formalization |
| Jolliffe, I.T. *Principal Component Analysis* (2nd ed.). Springer. | 2002 | PCA standard reference |
| Korzybski, A. *Science and Sanity*. Science Press. | 1933 | Map-territory distinction |
| Pearson, K. "On Lines and Planes of Closest Fit." *Phil. Mag.*, 2(11). | 1901 | PCA mathematical foundations |
| Scott, J.C. *Seeing Like a State*. Yale University Press. | 1998 | Legibility; the cost of state simplification |
| Shannon, C.E. "A Mathematical Theory of Communication." *Bell Sys. Tech. J.*, 27. | 1948 | Information theory; rate-distortion foundations |
| Tufte, E.R. *The Visual Display of Quantitative Information* (2nd ed.). Graphics Press. | 2001 | Data-ink ratio; visual compression principles |

---

*Loop MMT™ · What Am I Flattening? Knowledge Pack · v1 · 11 April 2026*
*© 2026 Shea Gunther · CC BY-NC 4.0*
