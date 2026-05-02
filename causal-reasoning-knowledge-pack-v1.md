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
Causal Reasoning Knowledge Pack
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
-   [1 · The Problem of Causation](#ch-problem)
-   [2 · Hume and the Regularity Tradition](#ch-regularity)
-   [3 · Counterfactual Theories](#ch-counterfactual)
-   [4 · Interventionism](#ch-intervention)
-   [5 · Pearl's Structural Framework](#ch-pearl)
-   [6 · Building Blocks of Causal Graphs](#ch-structures)
-   [7 · Simpson's Paradox](#ch-simpson)
-   [8 · Causal Discovery](#ch-discovery)
-   [9 · Mechanisms and Difference-Making](#ch-mechanisms)
-   [10 · Board Connection](#ch-board)
-   [References](#ch-refs)

::: {.content role="main"}
::: {#ch-abstract .abstract-box}
::: abstract-label
About This Document
:::

This is a reference document on causal reasoning for AI advisory conversations. It covers four philosophical traditions (regularity, counterfactual, interventionist, mechanistic), the mathematical framework for causal inference (structural causal models, directed acyclic graphs, do-calculus), and the practical challenges of moving from correlation to causation. The document draws on 23 sources spanning philosophy, statistics, and computer science. Full citations appear in the References section.

No prior knowledge of graph theory is assumed. The Graph Theory Knowledge Pack exists in the corpus for formal depth on graphs; this pack is self-contained.
:::

::: {#ch-problem .chapter}
::: chapter-number
Section 1
:::

::: chapter-title
The Problem of Causation
:::

We observe that striking a match is followed by a flame. We observe this repeatedly. We observe that when matches are not struck, flames do not appear. What licenses us to say the striking *caused* the flame?

The difficulty is conceptual, not empirical. No amount of observation settles whether one event caused another, because the same observations are compatible with multiple causal interpretations. Two events may be constantly conjoined because one causes the other, because they share a common cause, or by coincidence. The data cannot tell you which.

Four families of theory attempt to ground causation: **regularity theories** define it as regular succession; **counterfactual theories** define it as "what would have been different"; **interventionist theories** define it as what happens when you intervene; **process theories** define it as a physical mechanism connecting cause to effect. The dominant contemporary framework --- Judea Pearl's structural causal models --- synthesizes elements of all four into a formal calculus.

The historical arc runs: Hume (1739/1748) → Mill (1843) → Mackie (1965/1974) → Lewis (1973) → Woodward (2003) → Pearl (2000/2009). Each position addresses failures of its predecessors.
:::

::: {#ch-regularity .chapter}
::: chapter-number
Section 2
:::

::: chapter-title
Hume and the Regularity Tradition
:::

::: {#s-hume .section}
::: section-title
Hume's Account
:::

David Hume argued in the *Treatise of Human Nature* (1739) and the *Enquiry Concerning Human Understanding* (1748) that our idea of causation reduces to three components: **temporal priority** (cause precedes effect), **spatial contiguity** (cause and effect are adjacent), and **constant conjunction** (events of the cause-type are regularly followed by events of the effect-type). We never observe a "necessary connection" between cause and effect --- only the habit of expecting the effect when we see the cause.

Hume offered two definitions. The first (D1) captures external facts: an object followed by another, where all similar objects are followed by similar objects. The second (D2) captures the internal impression: the determination of mind that arises from observed regularities. Whether D2 belongs to the metaphysics of causation or merely to its psychology remains debated. For the regularity tradition, D1 is definitive: in the external world, causation just is regular succession.
:::

::: {#s-inus .section}
::: section-title
Mackie's INUS Conditions
:::

J.L. Mackie produced the most sophisticated regularity analysis in "Causes and Conditions" (1965) and *The Cement of the Universe* (1974). He observed that effects typically have a **plurality of causes** --- multiple distinct clusters of conditions, each sufficient for the effect. A cause is an **I**nsufficient but **N**ecessary part of an **U**nnecessary but **S**ufficient condition --- an INUS condition.

**Example:** The short circuit caused the house fire. The short circuit alone was insufficient --- it required oxygen, flammable material, no working sprinkler. But within that cluster, the short circuit was non-redundant: remove it and the remaining conditions don't suffice. The cluster itself was unnecessary --- arson or lightning could also produce fire.

Formally, the conditions for an effect E take the form: (A∧B∧C) ∨ (D∧E∧F) ∨ (G∧H∧I) ↔ E. Each disjunct is a minimally sufficient condition. Each conjunct within a disjunct is an INUS condition.

Mackie's analysis remains influential in epidemiology (Rothman's sufficient-cause model) and law (the but-for test). Among philosophers, it has been superseded by interventionist and structural approaches.
:::

::: {#s-limits .section}
::: section-title
Limits of the Regularity Tradition
:::

**Accidental regularities.** A coin flipped twice and landing heads both times satisfies constant conjunction, but the flipping didn't cause the result. The regularity is accidental, and regularity theories have no principled way to exclude it.

**Asymmetry.** The flagpole's height, the sun's angle, and the shadow's length are mutually related by geometric law. The shadow does not cause the flagpole to be tall. Regularity theories struggle to ground directionality.

**Common causes.** The barometer reading is constantly conjoined with storms. Both are effects of atmospheric pressure. INUS conditions cannot distinguish common-cause structures from genuine causal chains.

**Preemption and overdetermination.** Two bullets strike simultaneously; either alone would kill. Neither is necessary, yet both are causes. Standard regularity analyses mishandle these cases.
:::
:::

::: {#ch-counterfactual .chapter}
::: chapter-number
Section 3
:::

::: chapter-title
Counterfactual Theories
:::

::: {#s-lewis .section}
::: section-title
Lewis's 1973 Theory
:::

David Lewis proposed that c caused e if and only if, had c not occurred, e would not have occurred. He evaluated counterfactuals using possible-world semantics: among worlds where c doesn't occur, if the closest ones (most similar to the actual world) are worlds where e doesn't occur, then e counterfactually depends on c.

Lewis defined **causation** as the ancestral of causal dependence: c causes e if there is a chain of events d₁, d₂, ... dₙ where each depends counterfactually on the previous. This chain definition handles cases where direct counterfactual dependence fails.

The approach has an elegant core: causation reduces to counterfactual dependence, which reduces to similarity relations between possible worlds. If you accept Lewis's modal metaphysics, the analysis requires no irreducibly causal notions.
:::

::: {#s-preemption .section}
::: section-title
Preemption
:::

The deepest problem for counterfactual theories is preemption. Suzy and Billy throw stones at a bottle. Suzy's arrives first and shatters it. Billy's would have shattered it if Suzy hadn't thrown. The shattering does not counterfactually depend on Suzy's throw --- it would have happened anyway. Yet Suzy's throw is the cause.

Lewis handled **early preemption** (backup process cut short before completion) via causal chains. **Late preemption** (backup completes except for the final step) required his 2000 revision: the **influence** theory, where c causes e when alterations of c produce corresponding alterations in e. **Trumping preemption** (Schaffer 2000), where two sufficient causes compete and one prevails by a pre-existing rule, challenged even this revision.
:::

::: {#s-absences .section}
::: section-title
Absences as Causes
:::

The gardener's failure to water the plant caused its death. Lewis accepted that absences can be causes, grounded in counterfactuals: if the gardener had watered the plant, it would not have died. But absences are not events, creating tension with any theory that treats causation as a relation between events.
:::
:::

::: {#ch-intervention .chapter}
::: chapter-number
Section 4
:::

::: chapter-title
Interventionism
:::

::: {#s-woodward .section}
::: section-title
Woodward's Theory
:::

James Woodward's *Making Things Happen* (2003) argues that X causes Y if and only if there is a possible **intervention** on X that would change Y.

**Variables, not events.** Causal relations hold between variables that take different values. This makes the analysis naturally quantitative and connects to experimental practice.

**Intervention.** An intervention on X with respect to Y: (i) sets the value of X, (ii) changes Y only through X, (iii) is not caused by anything affecting Y except through X. The intervention is "surgical."

**Invariance.** Not every counterfactual dependency is causal. Barometer readings co-vary with storms (both caused by atmospheric pressure). But this relationship is not invariant under intervention: forcing the barometer needle to a new position does not change the weather. Causal relationships survive intervention on the putative cause.

**Not anthropocentric.** Interventions need not be humanly performable. Plate tectonics causes earthquakes even though nobody can intervene on plate movements.

**Not reductive.** Interventions are defined in causal terms. Woodward argues this circle is virtuous. Critics (Strevens) dispute this.
:::

::: {#s-pearl-connection .section}
::: section-title
Connection to Pearl
:::

Woodward provides the philosophical foundations for what Pearl formalizes mathematically. Pearl's do(X = x) operator is the precise formal counterpart of Woodward's intervention concept. Woodward argues *why* intervention should be central; Pearl provides the calculus for computing *what follows*.
:::
:::

::: {#ch-pearl .chapter}
::: chapter-number
Section 5
:::

::: chapter-title
Pearl's Structural Framework
:::

::: {#s-scm .section}
::: section-title
Structural Causal Models
:::

A **structural causal model** (SCM) consists of: endogenous variables V = {V₁, ..., Vₙ}, exogenous variables U, and structural equations Vᵢ = fᵢ(Paᵢ, Uᵢ), where Paᵢ are the direct causes (parents) of Vᵢ and Uᵢ represents exogenous noise.

Each equation encodes a **mechanism** --- how Vᵢ is determined by its direct causes. The equations are assumed **autonomous**: intervening on one variable replaces only its equation, leaving all others intact. This modularity makes interventions well-defined.

An SCM implies three kinds of distribution: observational (all equations intact), interventional (some equations replaced by constants), and counterfactual (what would have happened under different conditions, given what actually occurred).
:::

::: {#s-dags .section}
::: section-title
Directed Acyclic Graphs
:::

The qualitative structure of an SCM is represented as a **directed acyclic graph** (DAG). Variables are nodes. An arrow from X to Y means X appears in the structural equation for Y. "Acyclic" means no variable is its own ancestor.

**Missing arrows are substantive claims.** The absence of an arrow from X to Y asserts that X does not directly cause Y. These absences encode domain knowledge and cannot be derived from data.
:::

::: {.callout .key}
::: callout-label
The central distinction
:::

**P(Y | X)** is the probability of Y given that X is *observed*. It reflects the causal effect of X on Y combined with any confounding.

**P(Y | do(X))** is the probability of Y when X is *set by intervention*. It isolates the causal effect.

In general, **P(Y | X) ≠ P(Y | do(X))**. Conflating them --- treating observational associations as causal effects --- is the single most common and consequential error in causal reasoning.
:::

::: {#s-do .section}
::: section-title
The do-Operator
:::

do(X = x) means: replace the equation for X with the constant X = x; compute the resulting distribution using all other unchanged equations. Graphically: delete all arrows into X (severing X from its natural causes) and fix X's value.

The interventional distribution P(Y | do(X = x)) can sometimes be computed from observational data alone. When possible, the causal effect is **identifiable**.
:::

::: {#s-dsep .section}
::: section-title
d-Separation
:::

**d-separation** is a graphical criterion for conditional independence. X and Y are d-separated by Z if every path between them is blocked. A path is blocked when it contains:

A **chain** (X → M → Y) or **fork** (X ← M → Y) where M is in Z --- conditioning on M blocks information flow.

A **collider** (X → M ← Y) where M is not in Z and no descendant of M is in Z --- the collider blocks by default; conditioning on it *opens* the path.

The **Causal Markov condition** asserts that each variable is independent of its non-descendants given its parents. **Faithfulness** asserts the converse: all conditional independencies arise from d-separation.
:::

::: {#s-docalc .section}
::: section-title
The do-Calculus
:::

The do-calculus (Pearl 1995) consists of three inference rules for transforming expressions containing do-operators into observational expressions. The rules invoke d-separation conditions in modified DAGs.

**Rule 1** allows removing irrelevant observations. **Rule 2** allows replacing interventions with observations (or vice versa) when equivalent. **Rule 3** allows removing interventions with no effect on the outcome.

Huang and Valtorta (2006) and independently Shpitser and Pearl (2006) proved the do-calculus **complete**: if a causal effect is identifiable from observational data given the DAG, the three rules can derive the identifying expression.
:::

::: {#s-criteria .section}
::: section-title
Back-Door and Front-Door Criteria
:::

**Back-door criterion.** Z satisfies the back-door criterion for (X, Y) if: (i) no member of Z descends from X, and (ii) Z blocks every back-door path (paths into X). Then: P(Y | do(X)) = Σ_z P(Y | X, Z=z) · P(Z=z). This **adjustment formula** justifies "controlling for confounders."

**Front-door criterion.** When an unmeasured confounder exists between X and Y, a mediator M can sometimes enable identification despite the confounder --- showing that identifiability is possible even when the obvious approach fails.
:::

::: {#s-ladder .section}
::: section-title
The Ladder of Causation
:::

  Level                Activity     Typical Question                                                       Formal Expression
  -------------------- ------------ -------------------------------------------------------------------------- --------------------
  **1. Association**   Seeing       What does observing X tell me about Y?                                 P(Y | X)
  **2. Intervention**  Doing        What happens to Y if I set X?                                          P(Y | do(X))
  **3. Counterfactual** Imagining   Given what happened, what *would* have happened if X had differed?     P(Y_x | X=x', Y=y')

Each level strictly subsumes the one below. This is a **provable hierarchy**: no amount of Level 1 data suffices for Level 2 questions in general, and no amount of Level 2 information suffices for Level 3 (Bareinboim et al. 2022).
:::

::: {#s-po .section}
::: section-title
Relationship to Potential Outcomes
:::

The **Rubin causal model** defines causal effect as the difference between potential outcomes: Y(1) − Y(0). Pearl's SCMs and Rubin's potential outcomes are mathematically equivalent for many identification problems. They differ in emphasis: Pearl foregrounds graphs and the do-calculus; Rubin foregrounds assignment mechanisms and ignorability. Economists often use potential outcomes; epidemiologists and computer scientists often use DAGs. Increasingly, practitioners use both.
:::
:::

::: {#ch-structures .chapter}
::: chapter-number
Section 6
:::

::: chapter-title
Building Blocks of Causal Graphs
:::

Every path in a DAG is a sequence of three elementary structures. Knowing which to condition on is the core practical skill of causal inference.

  Structure               Pattern         Example                                                      Conditioning Rule
  ----------------------- --------------- ------------------------------------------------------------ --------------------------------------------------
  **Confounder** (Fork)   X ← Z → Y      Socioeconomic status affects both education and health       **Condition on Z** to block spurious association
  **Mediator** (Chain)    X → M → Y       Drug → blood chemistry → recovery                           **Do NOT condition on M** for total effect
  **Collider**            X → C ← Y       Talent and looks both cause being cast in a movie            **Do NOT condition on C** or descendants

::: {.callout .tip}
::: callout-label
Why this matters
:::

These rules follow from d-separation. Getting them wrong can reverse the sign of an estimated causal effect --- concluding a treatment is harmful when it is beneficial. Simpson's paradox (Section 7) is the canonical demonstration.
:::
:::

::: {#ch-simpson .chapter}
::: chapter-number
Section 7
:::

::: chapter-title
Simpson's Paradox
:::

::: {#s-phenomenon .section}
::: section-title
The Phenomenon
:::

Simpson's paradox occurs when a trend in subgroups reverses upon aggregation. Simpson described it in 1951; Pearson (1899) and Yule (1903) noted related effects earlier.

**Kidney stones:** Treatment A has higher success rates for small stones and for large stones, yet Treatment B has higher overall success. Reversal occurs because doctors gave A disproportionately to difficult cases. **Berkeley admissions:** Women appeared admitted at lower rates overall; within departments, women were admitted at equal or higher rates. Women applied disproportionately to competitive departments.
:::

::: {#s-resolution .section}
::: section-title
Why Statistics Cannot Resolve It
:::

Should you use aggregated or stratified data? The answer depends on the causal structure, and **the same data is compatible with both structures**. If the third variable is a confounder, stratify. If it's a mediator, don't. These structures produce identical probability distributions. Only the DAG distinguishes them.

Pearl's framework resolves this: apply the back-door criterion. The do-calculus handles all cases. The paradox dissolves with the causal graph --- but is irresolvable without one.
:::
:::

::: {#ch-discovery .chapter}
::: chapter-number
Section 8
:::

::: chapter-title
Causal Discovery
:::

::: {#s-disc-problem .section}
::: section-title
The Problem
:::

Everything in Sections 5--7 assumes you have a DAG. Where does it come from? Usually domain knowledge. **Causal discovery** asks: can the graph be learned from data?
:::

::: {#s-pc .section}
::: section-title
Constraint-Based Methods
:::

Under the Causal Markov condition, faithfulness, and causal sufficiency, the **PC algorithm** (Spirtes, Glymour, and Scheines 1993/2000) learns the **Markov equivalence class** of the true graph. It starts with a complete undirected graph, removes edges by conditional independence tests, identifies colliders, and propagates orientations.

The output is an equivalence class: a set of DAGs sharing the same conditional independencies. Some edges are oriented; others cannot be.
:::

::: {.callout .key}
::: callout-label
Fundamental limits
:::

Without interventions, you generally cannot determine the full orientation of all edges. Multiple DAGs may be observationally equivalent. This is a mathematical fact, not a limitation of any algorithm. When causal sufficiency is violated, the FCI algorithm can still identify some structure, but less of it.
:::

::: {#s-other .section}
::: section-title
Other Approaches
:::

**Score-based methods** search DAG space optimizing a fit criterion. NP-hard in general but tractable with heuristics. **Functional causal model methods** exploit asymmetries in functional form; if the model is linear and noise non-Gaussian, the full structure is identifiable. **Granger causality** is a predictive relationship (past X improves prediction of Y), not a causal one --- it can be confounded and does not correspond to intervention.
:::
:::

::: {#ch-mechanisms .chapter}
::: chapter-number
Section 9
:::

::: chapter-title
Mechanisms and Difference-Making
:::

::: {#s-two-views .section}
::: section-title
Two Conceptions of Causation
:::

Everything in Sections 2--8 belongs to the **difference-making** tradition: causation is about whether the cause makes a difference to the effect. The competing **process** or **mechanistic** tradition holds that causation consists in a physical process connecting cause to effect. This is not a minor philosophical distinction. It concerns what causation *is*, at the most fundamental level.
:::

::: {#s-process .section}
::: section-title
Process Theories: Salmon and Dowe
:::

Wesley Salmon (1984) proposed that causal explanation requires exhibiting physical mechanisms. He distinguished causal processes (which transmit marks) from pseudo-processes (which cannot). Phil Dowe (1992, 2000) refined this into the **conserved quantity theory**: a causal process is a world-line possessing a conserved quantity (energy, momentum, charge). A causal interaction involves exchange of conserved quantities.
:::

::: {#s-debate .section}
::: section-title
The Debate
:::

**Process theories explain *how*** --- tracing the physical connection. But they cannot handle absence causation, prevention, or domains remote from physics.

**Difference-making theories explain *that*** --- establishing whether X makes a difference to Y. They handle absences naturally, work across all domains, and connect to experimental methodology. But they say nothing about mechanism.

Many philosophers hold both aspects are genuine. Causes make a difference AND do so via mechanisms. The views answer different questions: "Does X cause Y?" (difference-making) versus "How does X cause Y?" (mechanisms). In practice, difference-making frameworks dominate applied causal inference. Process theories remain central to philosophy of explanation and biology (Machamer, Darden, and Craver 2000).
:::
:::

::: {#ch-board .chapter}
::: chapter-number
Section 10
:::

::: chapter-title
Board Connection --- Causal Claims in AI Advisory Practice
:::

::: {#s-classify .section}
::: section-title
Classifying an AI's Causal Claims
:::

When an AI advisor says "X caused Y" or "doing X will produce Y," the claim sits at a specific level of the Ladder. The advisor should know which level.

**Concrete example.** An AI states: "Remote work increases productivity."

If based on survey data showing remote workers report higher productivity, this is Level 1 --- association. The correlation might reflect selection effects. The claim does not license the inference that *making* a team remote will increase productivity.

If based on a randomized experiment assigning employees to conditions, this is Level 2 --- intervention. It supports the causal claim.

If based on a structural model with identified confounders and back-door adjustment, this is Level 2 via identification. The claim is only as strong as the model's assumptions.

If the AI says "had you not switched to remote work, Q3 output would have been 15% lower," this is Level 3 --- a specific counterfactual requiring full functional forms.

Most AI advisory claims are functionally Level 1, presented in Level 2 language. The discipline of this pack is to make the gap visible.
:::

::: {#s-unknown .section}
::: section-title
When the Causal Graph is Unknown
:::

The AI should: **State the model** --- making implicit causal assumptions explicit. **Flag confounders** --- what common causes might produce this pattern? **Separate predictive from causal language** --- "companies that adopt X tend to experience Y" is prediction; "adopting X will produce Y" is causation. **Test robustness** --- how would the conclusion change under alternative plausible graphs?
:::

::: {#s-interaction .section}
::: section-title
Interaction with Other Packs
:::

**Scientific Method KP.** Hypothesis testing establishes causal claims. The causal framework determines *what* to test and *how* to interpret results. A randomized trial answers a Level 2 question. Observational studies answer Level 1 questions promotable to Level 2 via the back-door criterion.

**Dempster-Shafer KP.** D-S handles evidence combination. Causal reasoning classifies what each piece of evidence bears on. Without causal reasoning, D-S risks combining correlational evidence as if it were causal evidence --- a category error no amount of belief-function arithmetic can correct.
:::

::: {.callout .key}
::: callout-label
The standard
:::

An AI advisor competent in causal reasoning will: (1) distinguish correlation from causation in output; (2) identify the Ladder level of each claim; (3) state causal assumptions behind interventional or counterfactual claims; (4) flag uncertainty in the causal graph; (5) resist compressing "X is associated with Y" into "X causes Y."

Simpson's paradox demonstrates the stakes: wrong causal structure can reverse the conclusion. The cost of sloppy causal language is not vagueness --- it is recommending the wrong action.
:::
:::

::: {#ch-refs .chapter}
::: chapter-number
References
:::

::: chapter-title
References
:::

1. Bareinboim, E., Correa, J.D., Ibeling, D., and Icard, T. "On Pearl's hierarchy and the foundations of causal inference." In *Probabilistic and Causal Inference: The Works of Judea Pearl*, ACM, 2022.
2. Dowe, P. "Wesley Salmon's process theory of causality and the conserved quantity theory." *Philosophy of Science* 59 (1992): 195--216.
3. Dowe, P. *Physical Causation*. Cambridge University Press, 2000.
4. Huang, Y. and Valtorta, M. "Pearl's calculus of intervention is complete." In *Proceedings of UAI-06*, 2006.
5. Hume, D. *A Treatise of Human Nature*. 1739. Edited by L.A. Selby-Bigge, revised P.H. Nidditch. Oxford: Clarendon Press, 1978.
6. Hume, D. *An Enquiry Concerning Human Understanding*. 1748. Edited by T.L. Beauchamp. Oxford: Oxford University Press, 1999.
7. Lewis, D. "Causation." *Journal of Philosophy* 70 (1973): 556--567.
8. Lewis, D. *Counterfactuals*. Oxford: Basil Blackwell, 1973.
9. Lewis, D. "Causation as influence." *Journal of Philosophy* 97 (2000): 182--197.
10. Machamer, P., Darden, L., and Craver, C.F. "Thinking about mechanisms." *Philosophy of Science* 67.1 (2000): 1--25.
11. Mackie, J.L. "Causes and conditions." *American Philosophical Quarterly* 2.4 (1965): 245--264.
12. Mackie, J.L. *The Cement of the Universe: A Study of Causation*. Oxford: Clarendon Press, 1974.
13. Mill, J.S. *A System of Logic*. London: John W. Parker, 1843.
14. Pearl, J. "Causal diagrams for empirical research." *Biometrika* 82.4 (1995): 669--710.
15. Pearl, J. *Causality: Models, Reasoning, and Inference*. Cambridge University Press, 2000. 2nd edition, 2009.
16. Pearl, J. and Mackenzie, D. *The Book of Why: The New Science of Cause and Effect*. Basic Books, 2018.
17. Pearl, J., Glymour, M., and Jewell, N.P. *Causal Inference in Statistics: A Primer*. John Wiley & Sons, 2016.
18. Salmon, W.C. *Scientific Explanation and the Causal Structure of the World*. Princeton University Press, 1984.
19. Schaffer, J. "Trumping preemption." *Journal of Philosophy* 97.4 (2000): 165--181.
20. Shpitser, I. and Pearl, J. "Identification of joint interventional distributions in recursive semi-Markovian causal models." In *Proceedings of AAAI-06*, 2006.
21. Simpson, E.H. "The interpretation of interaction in contingency tables." *Journal of the Royal Statistical Society, Series B* 13.2 (1951): 238--241.
22. Spirtes, P., Glymour, C., and Scheines, R. *Causation, Prediction, and Search*. 2nd edition. MIT Press, 2000.
23. Woodward, J. *Making Things Happen: A Theory of Causal Explanation*. Oxford University Press, 2003.
:::
:::
:::

------------------------------------------------------------------------

::: page-footer
Loop MMT™ · Multi-Module Theory Causal Reasoning Knowledge Pack · v1 © 2026 Shea Gunther · [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/deed.en){style="color:inherit;"}
:::
