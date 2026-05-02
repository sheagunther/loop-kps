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
Dempster-Shafer Evidence Theory & Information Fusion
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

-   [About This Document](#ch-abstract)
-   [1 · Frame of Discernment](#ch-frame)
-   [2 · Mass Functions](#ch-mass)
-   [3 · Belief & Plausibility](#ch-belief)
-   [4 · The Belief Interval](#ch-interval)
-   [5 · Dempster\'s Rule](#ch-combination)
-   [6 · Conflict & the Zadeh Paradox](#ch-conflict)
-   [7 · Alternative Combination Rules](#ch-alternatives)
-   [8 · Relationship to Bayes](#ch-bayesian)
-   [9 · Representing Ignorance](#ch-ignorance)
-   [10 · Applications](#ch-applications)
-   [11 · Board Connection](#ch-board)
-   [References](#ch-refs)

::: {.content role="main"}
::: {#ch-abstract .abstract-box}
::: abstract-label
About This Document
:::

This is a reference document on Dempster-Shafer evidence theory, designed to be loaded into AI advisory conversations. It covers the mathematical framework for reasoning under uncertainty when evidence comes from multiple independent sources of varying reliability. The theory\'s ability to represent ignorance explicitly and to combine conflicting evidence makes it the formal framework for Sable\'s analysis role on the advisory board.

Board member Sable (Analysis Terminal) uses this framework. The document covers the core formalism, combination rules, the Zadeh paradox, alternative rules, and the relationship to Bayesian probability. Full citations appear in the References section.
:::

::: {#ch-frame .chapter}
::: chapter-number
Section 1
:::

::: chapter-title
Frame of Discernment
:::

::: {#s-frame-def .section}
::: section-title
Definition
:::

The **frame of discernment** Ω is a finite set of mutually exclusive and exhaustive hypotheses about the state of the system under consideration. If we are diagnosing a patient, Ω might be {flu, pneumonia, bronchitis}. If we are classifying a sensor reading, Ω might be {target_present, target_absent}. The hypotheses must be mutually exclusive --- exactly one is true --- and exhaustive --- no other possibility exists.

The **power set** 2^Ω^ is the set of all subsets of Ω, including ∅ and Ω itself. For a frame with n elements, the power set has 2^n^ elements. DST assigns belief not just to individual hypotheses (singletons) but to *subsets* of hypotheses. This is the fundamental departure from classical probability, which assigns probabilities only to singletons.
:::

::: {#s-frame-design .section}
::: section-title
Designing the Frame
:::

The choice of frame matters enormously. Too coarse and the theory cannot distinguish states that are actually different. Too fine and the power set grows exponentially --- a frame with 20 elements has over one million subsets, making computation intractable.

The mutual exclusivity requirement is strict. If two hypotheses can both be true simultaneously, they cannot both be elements of the same frame. Instead, the frame must be refined to include compound states, or the problem must be restructured using multi-valued mappings between frames.
:::
:::

::: {#ch-mass .chapter}
::: chapter-number
Section 2
:::

::: chapter-title
Mass Functions
:::

::: {#s-mass-def .section}
::: section-title
Basic Probability Assignment
:::

A **basic probability assignment** (BPA), also called a **mass function**, is a mapping `m: 2`^`Ω`^` → [0, 1]` satisfying two conditions:

1.  `m(∅) = 0` --- no belief is assigned to the impossible event.
2.  `∑`~`A ⊆ Ω`~` m(A) = 1` --- the total mass across all subsets sums to one.

The value `m(A)` represents the portion of belief committed *exactly* to subset A and to nothing more specific. If `m({flu}) = 0.6`, the evidence supports \"flu\" specifically with weight 0.6. If `m({flu, pneumonia}) = 0.3`, the evidence supports \"either flu or pneumonia\" with weight 0.3 but does not specify which --- this is not the same as splitting 0.3 between them.
:::

::: {#s-focal .section}
::: section-title
Focal Elements
:::

A subset A is a **focal element** if `m(A) > 0`. The set of all focal elements is called the **body of evidence**. In practice, most subsets have zero mass and only a small number of focal elements carry information.

  Focal Element Structure             Interpretation                                                                     Special Case
  ----------------------------------- ---------------------------------------------------------------------------------- ----------------------------------------------------------------
  All singletons                      Complete specificity --- each piece of evidence points to exactly one hypothesis   Collapses to classical probability
  Only Ω                              Complete ignorance --- `m(Ω) = 1`                                                  Vacuous belief function
  Mix of singletons and larger sets   Partial knowledge --- some evidence is specific, some is ambiguous                 The general case
  Nested sets                         Hierarchical precision                                                             Consonant belief function; equivalent to a possibility measure
:::
:::

::: {#ch-belief .chapter}
::: chapter-number
Section 3
:::

::: chapter-title
Belief & Plausibility
:::

::: {#s-bel-def .section}
::: section-title
Belief Function
:::

The **belief function** Bel(A) measures the total evidence that *directly supports* A --- it sums the masses of all subsets of A:

`Bel(A) = ∑`~`B ⊆ A`~` m(B)`

Belief is a lower bound on the true probability of A. It counts only evidence entirely committed to A or to something more specific. Evidence assigned to a set that overlaps A but extends beyond it is not counted.
:::

::: {#s-pl-def .section}
::: section-title
Plausibility Function
:::

The **plausibility function** Pl(A) measures total evidence *consistent with* A:

`Pl(A) = ∑`~`B ∩ A ≠ ∅`~` m(B) = 1 − Bel(Ā)`

Plausibility is an upper bound on the true probability of A. It includes all evidence that does not directly contradict A.
:::

::: {#s-bel-properties .section}
::: section-title
Properties
:::

**Bel(A) ≤ Pl(A)** always. The true probability lies somewhere in \[Bel(A), Pl(A)\].

**Bel is superadditive:** `Bel(A ∪ B) ≥ Bel(A) + Bel(B) − Bel(A ∩ B)`. Belief functions do not require `Bel(A) + Bel(Ā) = 1`.

The gap between Bel and Pl represents **uncertainty** --- evidence relevant to A but not specific enough to commit. When Bel(A) = Pl(A), the belief function reduces to a probability assignment for A.

::: {.callout .key}
::: callout-label
The interval is the information
:::

In Bayesian probability, uncertainty about a hypothesis is a single number. In DST, uncertainty is an interval. A narrow interval \[0.8, 0.9\] means the evidence is largely specific. A wide interval \[0.2, 0.9\] means substantial ambiguity remains. The width of the interval is itself informative --- it tells you how much you don\'t know, which a single probability cannot.
:::
:::
:::

::: {#ch-interval .chapter}
::: chapter-number
Section 4
:::

::: chapter-title
The Belief Interval
:::

::: {#s-interval-structure .section}
::: section-title
Structure
:::

For any hypothesis A, the **belief interval** `[Bel(A), Pl(A)]` partitions \[0, 1\] into three regions:

  Region        Range               Meaning
  ------------- ------------------- ----------------------------------------------
  Support       \[0, Bel(A)\]       Evidence committed to A
  Uncertainty   \[Bel(A), Pl(A)\]   Evidence consistent with A but not committed
  Disbelief     \[Pl(A), 1\]        Evidence committed against A (= Bel(Ā))
:::

::: {#s-interval-example .section}
::: section-title
Worked Example
:::

Let Ω = {a, b, c} with `m({a}) = 0.4`, `m({a, b}) = 0.3`, `m(Ω) = 0.3`.

For {a}: `Bel = 0.4`, `Pl = 0.4 + 0.3 + 0.3 = 1.0`. Interval \[0.4, 1.0\] --- strong support but high ambiguity.

For {b}: `Bel = 0`, `Pl = 0.3 + 0.3 = 0.6`. Interval \[0, 0.6\] --- no direct support, not ruled out.

For {c}: `Bel = 0`, `Pl = 0.3`. Interval \[0, 0.3\] --- very little evidence even consistent with c.
:::
:::

::: {#ch-combination .chapter}
::: chapter-number
Section 5
:::

::: chapter-title
Dempster\'s Rule of Combination
:::

::: {#s-rule-def .section}
::: section-title
The Rule
:::

Given two independent mass functions `m₁` and `m₂` over the same frame Ω, **Dempster\'s rule** produces a combined mass `m₁₂ = m₁ ⊕ m₂`:

`m₁₂(A) = (1 / (1 − K)) · ∑`~`B ∩ C = A`~` m₁(B) · m₂(C)`  for A ≠ ∅

where the **conflict coefficient** K is:

`K = ∑`~`B ∩ C = ∅`~` m₁(B) · m₂(C)`

K measures the total mass that the two sources assign to mutually contradictory hypotheses. The normalization factor `1/(1 − K)` redistributes the contradictory mass across the non-empty intersections. The rule is undefined when K = 1 (total conflict).
:::

::: {#s-rule-properties .section}
::: section-title
Properties
:::

**Commutative:** `m₁ ⊕ m₂ = m₂ ⊕ m₁`.

**Associative:** `(m₁ ⊕ m₂) ⊕ m₃ = m₁ ⊕ (m₂ ⊕ m₃)`. Multiple sources can be combined in any order.

**Not idempotent:** `m ⊕ m ≠ m` in general. Combining evidence with itself changes the result.

**Independence required:** The rule assumes `m₁` and `m₂` are based on independent bodies of evidence. Applying it to dependent sources overcounts shared evidence and produces overconfident results.

::: {.callout .warn}
::: callout-label
The independence assumption
:::

Independence is critical and frequently violated. If two doctors base their diagnoses on the same lab results, their mass functions are not independent --- combining them by Dempster\'s rule overweights the shared evidence. Diagnosing and handling dependence between sources is one of the hardest practical problems in applying DST.
:::
:::

::: {#s-rule-mechanics .section}
::: section-title
Grid Visualization
:::

List the focal elements of `m₁` along one axis and `m₂` along the other. Each cell is the product `m₁(B) · m₂(C)`. The intersection `B ∩ C` determines which combined hypothesis receives that mass. Cells where `B ∩ C = ∅` contribute to K. All other cells contribute to the combined mass of their intersection. After filling the grid, normalize by `1/(1 − K)`.
:::
:::

::: {#ch-conflict .chapter}
::: chapter-number
Section 6
:::

::: chapter-title
Conflict & the Zadeh Paradox
:::

::: {#s-zadeh .section}
::: section-title
The Paradox
:::

The most famous critique of Dempster\'s rule is the Zadeh paradox (1986). Two equally reliable doctors examine a patient with Ω = {tumor, meningitis, concussion}:

  Source     m(tumor)   m(meningitis)   m(concussion)
  ---------- ---------- --------------- ---------------
  Doctor 1   0.99       0.01            0
  Doctor 2   0          0.01            0.99

The conflict is K = 0.99 × 0.99 + 0.99 × 0.01 + 0 = 0.99 × (0.99 + 0.01) = 0.99 × 1 = 0.9999\... Working it out precisely: K = (0.99)(0) + (0.99)(0.99) + (0.01)(0.99) = 0 + 0.9801 + 0.0099 = 0.99. The only non-empty intersection is meningitis: m₁(meningitis) · m₂(meningitis) = 0.01 × 0.01 = 0.0001. Normalizing: m₁₂(meningitis) = 0.0001 / (1 − 0.99) = 0.0001 / 0.01 = **1.0**.

The combined result assigns 100% belief to meningitis --- the one diagnosis both doctors considered least likely. Both assigned it only 1% probability, yet the combination gives it certainty.

::: {.callout .warn}
::: callout-label
Why this happens
:::

The normalization by `1/(1 − K)` redistributes all conflicting mass to the non-conflicting intersections. When K is close to 1 (near-total conflict), even tiny areas of agreement get amplified enormously. The meningitis mass is tiny in absolute terms but it is the only non-zero intersection, so all renormalized mass goes there. The paradox reveals that Dempster\'s rule can produce absurd results when sources are highly conflicting.
:::
:::

::: {#s-conflict-interpretation .section}
::: section-title
What Conflict Means
:::

The conflict coefficient K has a direct interpretation: it is the probability that the two sources, if both were correct, would jointly assert something impossible. High K means the sources are fundamentally incompatible --- they cannot both be right. Low K means the sources are largely compatible.

K serves as a diagnostic: if K is high, you should investigate *why* the sources disagree before blindly combining them. Possible explanations include faulty sensors, incorrect frame design, or violated independence assumptions. Combining highly conflicting sources without diagnosis is the root cause of paradoxical results.
:::
:::

::: {#ch-alternatives .chapter}
::: chapter-number
Section 7
:::

::: chapter-title
Alternative Combination Rules
:::

::: {#s-alt-rules .section}
::: section-title
Responses to the Conflict Problem
:::

The Zadeh paradox motivated development of alternative rules that handle high-conflict scenarios differently:

  Rule                              Author(s)               How It Handles Conflict                                                                                                               Trade-Off
  --------------------------------- ----------------------- ------------------------------------------------------------------------------------------------------------------------------------- --------------------------------------------------------------------------------------------------------------------------------
  Yager\'s rule                     Yager (1987)            Assigns conflicting mass to Ω (total ignorance) instead of normalizing it away                                                        Conservative --- conflict increases uncertainty rather than being redistributed. Loses no information but weakens conclusions.
  Murphy\'s averaging               Murphy (2000)           Averages all mass functions first, then combines the average with itself n−1 times                                                    Smooths out outlier sources. Loses source independence information.
  Transferable Belief Model (TBM)   Smets & Kennes (1994)   Uses unnormalized Dempster\'s rule --- allows `m(∅) > 0`, representing the degree to which the evidence is internally contradictory   Philosophically cleaner (conflict is visible, not hidden) but requires different decision-making rules.
  Dubois-Prade disjunctive rule     Dubois & Prade (1988)   Assigns conflicting mass to `B ∪ C` instead of discarding it                                                                          Preserves information by generalizing rather than discarding. More cautious than Dempster.

No rule is universally superior. The choice depends on what conflict means in the specific application. If conflict indicates one source is wrong, Dempster\'s rule (with its implicit \"at least one source is right\" assumption) may be appropriate for low-conflict scenarios. If conflict indicates the problem is harder than expected, Yager\'s rule or TBM preserve the conflict as visible uncertainty.
:::
:::

::: {#ch-bayesian .chapter}
::: chapter-number
Section 8
:::

::: chapter-title
Relationship to Bayesian Theory
:::

::: {#s-bayes-collapse .section}
::: section-title
DST Generalizes Bayes
:::

When every focal element is a singleton --- that is, when every piece of evidence points to exactly one hypothesis --- the mass function becomes a classical probability distribution, Bel(A) = Pl(A) for all A, and the belief interval collapses to a point. In this special case, Dempster\'s rule reduces to Bayes\' rule for combining independent likelihoods.

DST is strictly more general: it allows mass to be assigned to non-singleton subsets, which Bayesian probability cannot represent. The extra generality comes at a cost --- the belief interval is wider (less precise) than a Bayesian posterior --- but it is honest about what the evidence actually supports rather than forcing a precision the evidence doesn\'t warrant.
:::

::: {#s-bayes-comparison .section}
::: section-title
Key Differences
:::

  Feature                  Bayesian Probability                              Dempster-Shafer
  ------------------------ ------------------------------------------------- -------------------------------------------------------------
  Belief assigned to       Singletons only                                   Any subset of Ω
  Prior required?          Yes --- must specify P(H) for all H               No --- can start from total ignorance (m(Ω) = 1)
  Representing ignorance   Uniform distribution (assumes equal likelihood)   m(Ω) = 1 (makes no assumption at all)
  Uncertainty about H      Single number P(H)                                Interval \[Bel(H), Pl(H)\]
  Combination rule         Bayes\' theorem (requires likelihood and prior)   Dempster\'s rule (requires only independent mass functions)
  Additivity               P(A) + P(Ā) = 1 always                            Bel(A) + Bel(Ā) ≤ 1 in general

::: {.callout .key}
::: callout-label
The critical difference
:::

In Bayesian theory, a uniform prior over {a, b, c} assigns P(a) = P(b) = P(c) = 1/3. This *looks like* ignorance but is actually a strong claim: all hypotheses are equally likely. In DST, `m(Ω) = 1` assigns all mass to the entire frame, saying nothing about individual hypotheses. Bel(a) = 0, Pl(a) = 1 --- the interval \[0, 1\] genuinely represents knowing nothing. This distinction matters when the \"ignorance\" prior drives the result, which it frequently does when evidence is sparse.
:::
:::
:::

::: {#ch-ignorance .chapter}
::: chapter-number
Section 9
:::

::: chapter-title
Representing Ignorance
:::

::: {#s-vacuous .section}
::: section-title
The Vacuous Belief Function
:::

The **vacuous belief function** has `m(Ω) = 1` and `m(A) = 0` for all proper subsets A. It represents total ignorance --- the evidence says nothing at all. For every hypothesis H, `Bel(H) = 0` and `Pl(H) = 1`, giving the maximal uncertainty interval \[0, 1\].

The vacuous belief function is the identity element for Dempster\'s rule: combining any mass function m with the vacuous function returns m unchanged. This is the correct behavior --- combining evidence with ignorance should not change the evidence.
:::

::: {#s-partial-ignorance .section}
::: section-title
Partial Ignorance
:::

DST can represent states between total knowledge and total ignorance. Consider `m({a}) = 0.6`, `m(Ω) = 0.4`. This says: 60% of the evidence points specifically to a; the remaining 40% is uninformative. The resulting belief interval for a is \[0.6, 1.0\] --- we know at least 0.6 supports a, but the uncommitted 0.4 could go either way.

This ability to assign mass to Ω --- to say explicitly \"I don\'t know\" with a quantified weight --- is what Bayesian probability cannot do. A Bayesian must either assign prior probabilities (claiming knowledge they don\'t have) or use improper priors (losing mathematical guarantees). DST provides a principled third option.
:::
:::

::: {#ch-applications .chapter}
::: chapter-number
Section 10
:::

::: chapter-title
Applications
:::

::: {#s-app-list .section}
::: section-title
Where DST Is Used
:::

  Domain                      Application                                                                                      Why DST
  --------------------------- ------------------------------------------------------------------------------------------------ --------------------------------------------------------------------------------------------------------------------------------
  Sensor fusion               Combining readings from multiple sensors (radar, infrared, acoustic) for target identification   Sensors have different reliability profiles; DST handles partial information and sensor disagreement
  Fault diagnosis             Combining diagnostic tests to identify equipment failures                                        Individual tests are ambiguous; DST combines partial evidence without requiring priors on failure modes
  Medical diagnosis           Combining results from multiple tests, symptoms, and expert opinions                             Evidence is often partial and sometimes conflicting; DST represents the uncertainty interval explicitly
  Classification              Combining outputs from multiple classifiers (ensemble methods)                                   Each classifier provides partial evidence; DST handles the case where classifiers disagree
  Risk analysis               Combining expert judgments about the likelihood of failure scenarios                             Experts have different knowledge bases; DST allows each to express ignorance about areas outside their expertise
  Multi-source intelligence   Combining HUMINT, SIGINT, IMINT for intelligence assessment                                      Sources have different reliability and coverage; DST provides a formal framework for fusion with explicit conflict measurement
:::
:::

::: {#ch-board .chapter}
::: chapter-number
Section 11
:::

::: chapter-title
Board Connection
:::

::: {#s-board-mapping .section}
::: section-title
Documents as Evidence Sources
:::

The advisory board uses Dempster-Shafer theory as the formal framework for Sable\'s analysis terminal. The mapping is direct:

  DST Concept                   Advisory Board
  ----------------------------- ---------------------------------------------------------------------------------------------------------
  Frame of discernment Ω        The set of possible session states --- what was decided, built, and understood
  Mass function from source i   The evidence a single session document provides about the session state
  Focal elements                The specific claims a document makes --- some precise (singletons), some ambiguous (subsets)
  Belief interval \[Bel, Pl\]   The range from \"definitely established\" to \"possibly true\" for any claim about the session
  Dempster\'s rule              The process of combining evidence from multiple documents to reconstruct session state
  Conflict coefficient K        The degree to which documents contradict each other --- a diagnostic signal, not an error
  m(Ω) --- ignorance mass       The portion of the session that no document captures --- explicitly quantified rather than assumed away
:::

::: {#s-board-implications .section}
::: section-title
Design Implications
:::

**Documents are not equally reliable.** A handoff document written at the end of a session has different reliability characteristics than a routing table produced mid-session. DST allows each to carry its own reliability profile rather than treating all documents as equally authoritative.

**Conflict between documents is informative, not pathological.** When two documents disagree about the session state, the conflict coefficient K quantifies the disagreement. High K means something went wrong --- a document is stale, a decision was reversed, or the documents capture different moments. The conflict should be investigated, not normalized away.

**Ignorance is explicit.** When no document addresses a particular aspect of the session, DST represents this as `m(Ω)` rather than inventing a prior. The belief interval for that aspect will be wide, honestly reflecting what is and isn\'t known. This is better than a Bayesian approach that would assign a uniform prior and produce a falsely precise answer.

**Each new document narrows the interval.** As more documents are loaded, the belief intervals tighten --- Bel increases and Pl decreases. The rate at which intervals tighten depends on how independent and informative each document is. Redundant documents (dependent evidence) tighten intervals less than documents covering new ground.

::: {.callout .key}
::: callout-label
The structural claim
:::

Sable\'s analysis terminal is a DST combination engine operating on session documents as evidence sources. Each document provides a mass function. The terminal combines them, measures conflict, and reports belief intervals. The Zadeh paradox is the formal statement of why blind combination without conflict diagnosis can produce absurd session reconstructions --- and why the terminal checks K before reporting results.
:::
:::
:::

::: {#ch-refs .chapter}
::: chapter-number
References
:::

::: chapter-title
References
:::

::: section
::: section-title
Foundational Works
:::

Dempster, A. P. (1967). Upper and lower probabilities induced by a multivalued mapping. *The Annals of Mathematical Statistics*, 38(2), 325--339.

Dempster, A. P. (1968). A generalization of Bayesian inference. *Journal of the Royal Statistical Society, Series B*, 30(2), 205--247.

Shafer, G. (1976). *A Mathematical Theory of Evidence*. Princeton University Press.
:::

::: section
::: section-title
Conflict and Alternative Rules
:::

Zadeh, L. A. (1986). A simple view of the Dempster-Shafer theory of evidence and its implication for the rule of combination. *AI Magazine*, 7(2), 85--90.

Yager, R. R. (1987). On the Dempster-Shafer framework and new combination rules. *Information Sciences*, 41(2), 93--137.

Smets, P. & Kennes, R. (1994). The transferable belief model. *Artificial Intelligence*, 66(2), 191--234.

Dubois, D. & Prade, H. (1988). Representation and combination of uncertainty with belief functions and possibility measures. *Computational Intelligence*, 4(3), 244--264.

Murphy, C. K. (2000). Combining belief functions when evidence conflicts. *Decision Support Systems*, 29(1), 1--9.
:::

::: section
::: section-title
Surveys and References
:::

Sentz, K. & Ferson, S. (2002). Combination of evidence in Dempster-Shafer theory. *Sandia National Laboratories Report*, SAND 2002-0835.

Jøsang, A. (2016). *Subjective Logic: A Formalism for Reasoning Under Uncertainty*. Springer.

Pearl, J. (1990). Reasoning with belief functions: An analysis of compatibility. *International Journal of Approximate Reasoning*, 4(5--6), 363--389.

Wikipedia contributors. (2025). Dempster--Shafer theory. *Wikipedia, The Free Encyclopedia*.
:::
:::
:::
:::

------------------------------------------------------------------------

::: page-footer
Loop MMT™ · Multi-Module Theory Dempster-Shafer Evidence Theory & Information Fusion Knowledge Pack · v1 © 2026 Shea Gunther · [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/deed.en){style="color:inherit;"}
:::
