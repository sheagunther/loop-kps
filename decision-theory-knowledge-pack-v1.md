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
Decision Theory — Choosing Under Uncertainty
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
-   [1 · Expected Utility Theory](#ch-eu)
-   [2 · Risk and Uncertainty](#ch-risk)
-   [3 · Choosing Under Ignorance](#ch-ignorance)
-   [4 · Satisficing and Bounded Rationality](#ch-satisficing)
-   [5 · Prospect Theory](#ch-prospect)
-   [6 · Multiple Objectives](#ch-multi)
-   [7 · Option Value](#ch-option)
-   [8 · Sequential Decisions and the Value of Information](#ch-sequential)
-   [9 · Three Theories of Decision](#ch-three)
-   [10 · Board Connection](#ch-board)
-   [References](#ch-refs)

::: {.content role="main"}
::: {#ch-abstract .abstract-box}
::: abstract-label
About This Document
:::

Decision theory studies how to choose when outcomes are uncertain. This pack covers the formal normative frameworks (expected utility, minimax, value of information), the empirical findings about how humans actually choose (prospect theory, bounded rationality), and the prescriptive methods that try to bridge the gap (decision analysis, structured trade-off elicitation).

The operational purpose: equip AI advisors to structure decisions for the people they serve. Not to decide on their behalf, but to identify alternatives, clarify objectives, represent uncertainty honestly, and surface trade-offs that might otherwise remain hidden. An advisor grounded in decision theory can recognize when a decision-maker is operating in the domain of Knightian uncertainty rather than calculable risk, when "good enough" is the rational strategy, and when the framing of a question is silently determining the answer.

Companion packs: **Dempster-Shafer** (evidence combination as input to decisions), **Probability** (the mathematics underneath expected utility), **Multi-Objective Optimization / Pareto** (formal treatment of competing objectives).
:::

::: {#ch-eu .chapter}
::: chapter-number
Section 1
:::

::: chapter-title
Expected Utility Theory
:::

::: {#s-why-utility .section}
::: section-title
Why Utility, Not Money
:::

In 1738, Daniel Bernoulli analyzed the St. Petersburg paradox — a coin-flip game whose expected monetary payoff is infinite, yet no sensible person would pay a large sum to play it. His resolution: people do not maximize expected wealth. They maximize the expected value of a subjective *utility function* that translates wealth into satisfaction. Because each additional dollar matters less than the last (diminishing marginal utility), the utility function is concave, and this concavity produces risk-averse behavior as a mathematical consequence.

::: {.callout .key}
::: callout-label
Key
:::

Utility is not money. A risk-averse agent's utility of $1,000 is more than half their utility of $2,000. A risk-neutral agent's utility is linear in money — and only for this special case does maximizing expected utility coincide with maximizing expected monetary value. The distinction matters: any advisor that treats expected dollars and expected utility as interchangeable is implicitly assuming risk neutrality, which is rarely warranted.
:::
:::

::: {#s-vnm .section}
::: section-title
The von Neumann-Morgenstern Framework
:::

John von Neumann and Oskar Morgenstern, in *Theory of Games and Economic Behavior* (1944, with the axiomatic treatment refined in the 1947 second edition), proved that Bernoulli's intuition could be given rigorous foundations. If a decision-maker's preferences over lotteries satisfy four axioms, then there exists a utility function such that the decision-maker behaves as if maximizing expected utility.

| Axiom | Meaning | What It Rules Out |
|---|---|---|
| **Completeness** | For any two lotteries, the agent can say which is preferred or that they are indifferent | Incomparability — being unable to compare two options at all |
| **Transitivity** | If A ≥ B and B ≥ C, then A ≥ C | Preference cycles — being exploitable by a money pump |
| **Continuity** | If A > B > C, there exists some mixture of A and C that is indifferent to B | Lexicographic preferences — outcomes infinitely better than others |
| **Independence** | Preferences between two lotteries are unchanged when both are mixed with the same third lottery in the same proportions | Preferences influenced by irrelevant common outcomes |

The resulting utility function is cardinal — unique up to positive affine transformation (you can shift and scale it without changing its behavioral implications). But it is not interpersonally comparable: there is no principled way to aggregate utilities across different people using VNM theory alone.
:::

::: {#s-savage .section}
::: section-title
Savage's Subjective Extension
:::

VNM assumes objective, externally given probabilities. Leonard Savage's *The Foundations of Statistics* (1954) dropped this assumption. Savage showed that if preferences satisfy a richer set of axioms — including a "sure-thing principle" stating that preferences between acts should depend only on the states where the acts differ — then the agent acts as if possessing both a utility function and a subjective probability distribution, maximizing *subjective* expected utility. This is the formal bridge connecting decision theory to Bayesian statistics: beliefs and desires are jointly revealed by choices.
:::

::: {#s-allais .section}
::: section-title
The Allais Crack
:::

In 1953, Maurice Allais published a pair of choice problems demonstrating that most people's preferences systematically violate the independence axiom. The violations take two forms: the **common consequence effect** (adding or removing a common outcome flips preferences) and the **common ratio effect** (scaling all probabilities by a common factor flips preferences). Both forms show that people give disproportionate weight to certainty — preferring a sure gain even when a risky alternative has higher expected utility.

::: {.callout .warn}
::: callout-label
Warning
:::

Independence is the load-bearing axiom. Completeness and transitivity are rarely challenged. Continuity is mostly technical. But independence is violated regularly and robustly in controlled experiments. Every major descriptive alternative to expected utility — prospect theory, rank-dependent utility, regret theory — weakens or drops independence. An AI advisor must treat the independence axiom as normatively compelling but descriptively fragile.
:::
:::
:::

::: {#ch-risk .chapter}
::: chapter-number
Section 2
:::

::: chapter-title
Risk and Uncertainty
:::

::: {#s-knight .section}
::: section-title
Knight's Distinction (1921)
:::

Frank Knight's *Risk, Uncertainty, and Profit* (1921) introduced a distinction that remains central to decision theory. **Risk** involves situations where outcomes are uncertain but their probability distribution is known or estimable — actuarial tables, manufacturing defect rates, casino games. **Uncertainty** (now called Knightian uncertainty) involves situations where the probability distribution itself is unknown or unknowable — radical innovation, geopolitical upheaval, novel technologies.

The distinction has economic substance. Under risk, firms can insure and hedge, so competition erodes excess returns. True profit — returns above the cost of capital — exists only because entrepreneurs bear genuine uncertainty that cannot be diversified away. John Maynard Keynes made a similar point independently in 1921, writing in *A Treatise on Probability* of situations where there exists no scientific basis for forming any calculable probability.
:::

::: {#s-ellsberg .section}
::: section-title
The Ellsberg Paradox
:::

Daniel Ellsberg (1961) showed experimentally that people distinguish between known and unknown probabilities even when rational theory says they shouldn't. An urn contains 30 red balls and 60 balls that are either black or yellow in unknown proportions. Most people prefer betting on red (known probability: 1/3) over betting on black (unknown probability: between 0 and 2/3). They simultaneously prefer betting on "not red" over "not black" — a combination that violates Savage's sure-thing principle. This **ambiguity aversion** confirms that the risk/uncertainty distinction has behavioral reality, not just theoretical significance.
:::

::: {#s-advisory .section}
::: section-title
Advisory Implications
:::

An AI advisor operating as if all probabilities are known will overstate confidence and mischaracterize the decision landscape. The first diagnostic question in any decision is: are we in the domain of risk or uncertainty? Under risk, expected utility calculations are appropriate. Under uncertainty, the advisor should say so explicitly, represent ignorance honestly (the Dempster-Shafer framework assigns belief mass to the full frame of discernment, which is exactly what "I don't know" looks like formally), and consider robust decision criteria that do not depend on probability estimates.
:::
:::

::: {#ch-ignorance .chapter}
::: chapter-number
Section 3
:::

::: chapter-title
Choosing Under Ignorance
:::

::: {#s-criteria .section}
::: section-title
Decision Criteria Without Probabilities
:::

When probabilities cannot be assigned, expected utility is unavailable. Several alternative decision rules have been proposed, each embedding a different posture toward the unknown.

| Criterion | Rule | Posture | Source |
|---|---|---|---|
| **Maximin (Wald)** | Maximize the minimum payoff across all possible states | Extreme pessimism — prepare for the worst | Wald, *Statistical Decision Functions* (1950) |
| **Minimax Regret** | Minimize the maximum regret (difference between actual outcome and best possible outcome for that state) | Moderate pessimism — avoid the worst "I should have..." | Savage (1951) |
| **Hurwicz** | Weighted combination of best and worst case: α·max + (1−α)·min | Adjustable — α represents the decision-maker's optimism | Hurwicz (1951) |
| **Laplace** | Assign equal probability to all states (principle of insufficient reason), then maximize expected value | Agnostic — no state is presumed more likely | Laplace (1814) |
:::

::: {#s-pessimism .section}
::: section-title
The Price of Pessimism
:::

Maximin guarantees the best worst case, but its conservatism can be extremely costly. A decision-maker who always prepares for the absolute worst outcome will sacrifice enormous upside to protect against scenarios that may be exceedingly unlikely. The gap between the maximin payoff and the expected-utility-optimal payoff — the "price of pessimism" — can be enormous in problems with low-probability catastrophic outcomes but high-probability benign ones.

There is no meta-criterion for choosing among these rules. The choice of decision criterion is itself a decision under uncertainty. Hurwicz's α-parameter makes this explicit: rather than hiding the optimism-pessimism trade-off inside the choice of rule, it puts it in a tunable parameter that the decision-maker must set. The honest response is often: "I cannot tell you which rule is correct; I can tell you what each rule recommends and what assumptions each embeds."
:::
:::

::: {#ch-satisficing .chapter}
::: chapter-number
Section 4
:::

::: chapter-title
Satisficing and Bounded Rationality
:::

::: {#s-limits .section}
::: section-title
Why Optimization Fails
:::

Expected utility theory instructs: enumerate every alternative, compute expected utility for each, select the maximum. Herbert Simon observed that this prescription is unimplementable for most real decisions. Decision-makers face limited cognitive capacity, incomplete information about alternatives and consequences, and finite time. The full optimization problem is computationally intractable — not because of laziness but because the problem space exceeds the agent's processing capacity.

Simon called this condition **bounded rationality**. The concept first appeared in *Administrative Behavior* (1947) and was formalized across two landmark papers: "A Behavioral Model of Rational Choice" (*Quarterly Journal of Economics*, 1955) and "Rational Choice and the Structure of the Environment" (*Psychological Review*, 1956). Simon received the Nobel Memorial Prize in Economics in 1978 for this work.
:::

::: {#s-strategy .section}
::: section-title
The Strategy
:::

**Satisficing** replaces maximization with threshold satisfaction. The decision-maker sets an **aspiration level** — a minimum standard for what constitutes an acceptable outcome — and searches through options sequentially, stopping at the first option that meets or exceeds the threshold. The word itself is a portmanteau of "satisfy" and "suffice," borrowed from Scots dialect by Simon in 1956.

::: {.callout .tip}
::: callout-label
Tip
:::

Aspiration levels are dynamic. They rise after easy successes (the agent becomes more ambitious) and fall after repeated failure (the agent lowers standards). This makes satisficing adaptive rather than static — the threshold itself evolves through feedback from the environment. A well-calibrated aspiration level in a stable environment converges toward optimal behavior. In volatile environments, it provides robustness that fixed optimization rules lack.
:::
:::

::: {#s-ecological .section}
::: section-title
Ecological Rationality
:::

Gerd Gigerenzer and the ABC Research Group extended Simon's insight: simple heuristics, including satisficing, can *outperform* complex optimization in specific environments. When sample sizes are small, when cues are numerous and correlated, or when the cost of data collection is nontrivial, a simple rule that ignores most available information often predicts better than a model that tries to use all of it. The overfitting that plagues complex models is itself a failure of optimization — the model optimizes for the training set at the expense of the real world.
:::
:::

::: {#ch-prospect .chapter}
::: chapter-number
Section 5
:::

::: chapter-title
Prospect Theory
:::

::: {#s-how-humans .section}
::: section-title
How Humans Actually Decide
:::

Daniel Kahneman and Amos Tversky published "Prospect Theory: An Analysis of Decision under Risk" in *Econometrica* in 1979. It became the most cited paper in the journal's history and earned Kahneman the 2002 Nobel Memorial Prize in Economics (Tversky died in 1996). The paper documents systematic deviations from expected utility theory and proposes an alternative descriptive model.
:::

::: {#s-departures .section}
::: section-title
Three Departures
:::

**Reference dependence.** People evaluate outcomes as gains or losses relative to a reference point — typically the status quo — not as final states of wealth. The same salary feels like a windfall if expectations were lower and a disappointment if they were higher. The reference point is malleable: it can be set by prior expectations, social comparisons, the framing of the question, or the most recent experience.

**Loss aversion.** Losses hurt more than equivalent gains satisfy. The loss aversion coefficient λ — the ratio of the marginal disutility of losses to the marginal utility of gains near the reference point — is typically estimated between 2 and 2.5 across many studies, though with significant individual variation. This asymmetry is distinct from risk aversion: a risk-neutral person with loss aversion would still demand more than $100 to accept a 50-50 bet of gaining or losing $100.

**Probability weighting.** People do not multiply utilities by raw probabilities. Instead, they apply a nonlinear weighting function that overweights small probabilities and underweights moderate-to-large ones. This single mechanism explains the simultaneous purchase of lottery tickets (overweighting the small chance of a large gain) and insurance (overweighting the small chance of a large loss).
:::

::: {#s-fourfold .section}
::: section-title
The Fourfold Pattern
:::

| | High Probability | Low Probability |
|---|---|---|
| **Gains** | Risk averse — certainty effect. Prefer $900 for sure over 90% chance of $1,000. | Risk seeking — lottery effect. Prefer 0.1% chance of $10,000 over sure $10. |
| **Losses** | Risk seeking — gamble to avoid sure loss. Prefer 90% chance of losing $1,000 over sure loss of $900. | Risk averse — insurance effect. Pay $10 to avoid 0.1% chance of losing $10,000. |

No single risk attitude can produce this pattern. It requires the interaction of loss aversion with the nonlinear probability weighting function. The fourfold pattern has been confirmed across numerous studies and cultures.
:::

::: {#s-framing .section}
::: section-title
Framing Effects
:::

Because evaluation is relative to a reference point, the same objective situation produces different choices depending on how it is presented. In the "Asian disease" problem, Kahneman and Tversky showed that describing outcomes as lives saved (gain frame) versus lives lost (loss frame) reverses the majority preference between a certain and a probabilistic option — even though the two frames describe mathematically identical outcomes. This violates the normative requirement of **description invariance**: rational preferences should not change when the same situation is described differently.
:::

::: {#s-replication .section}
::: section-title
Global Replication
:::

A large-scale replication published in *Nature Human Behaviour* (2020, with full results reported 2022) tested the original 1979 experiments across 19 countries and 13 languages. The study reported approximately 90% replication of the core theoretical contrasts underlying prospect theory. Some effect sizes were smaller than in the original, but the fundamental phenomena — loss aversion, reference dependence, probability weighting, the fourfold pattern — held across cultures.
:::
:::

::: {#ch-multi .chapter}
::: chapter-number
Section 6
:::

::: chapter-title
Multiple Objectives
:::

::: {#s-competing .section}
::: section-title
Competing Criteria
:::

Most consequential decisions involve multiple objectives that cannot be simultaneously maximized. Hiring decisions trade off cost, skill, experience, and organizational fit. Product design trades off performance, reliability, aesthetics, and price. Public policy trades off economic growth, equity, environmental protection, and political feasibility.

The **Multi-Objective Optimization / Pareto pack** (already in the corpus) provides the mathematical framework: Pareto optimality identifies the set of solutions where improving any objective requires worsening another. This section addresses the decision-theoretic question that Pareto analysis leaves open: *which* Pareto-optimal solution should you choose?
:::

::: {#s-methods .section}
::: section-title
Methods for Choosing
:::

Three families of methods are common. **Multi-attribute utility theory** (Keeney & Raiffa, 1976) extends VNM utility to multiple dimensions by decomposing overall utility into component functions over individual attributes, combined with preference weights elicited from the decision-maker. **Weighted scoring methods** assign numerical weights to criteria and compute a weighted sum — simpler but more sensitive to arbitrary weight assignment. **Outranking methods** (ELECTRE, PROMETHEE) compare options pairwise on each criterion, building a partial ranking rather than a complete one.

The common element across all methods is that they force the decision-maker to make value judgments *explicit*. The primary contribution of multi-criteria analysis is not producing the "right" answer — it's surfacing trade-offs that would otherwise remain hidden inside an intuitive judgment. Making the weights visible makes them debatable.
:::
:::

::: {#ch-option .chapter}
::: chapter-number
Section 7
:::

::: chapter-title
Option Value
:::

::: {#s-flexibility .section}
::: section-title
Flexibility Has Value
:::

A **real option** is the right, but not the obligation, to take a future business action — defer, expand, contract, abandon, switch, or stage an investment. Stewart Myers coined the term in 1977, applying financial options logic to capital budgeting. The core insight: the ability to decide later, after learning more, has positive economic value — and that value increases with uncertainty.

Traditional net-present-value (NPV) analysis misses this because it treats investment as a single go/no-go commitment. **Expanded NPV = Traditional NPV + Option Value.** A project with negative traditional NPV may be worth pursuing if the option value embedded in it — the right to learn and adapt — is large enough to compensate.
:::

::: {#s-when .section}
::: section-title
When Option Value Matters Most
:::

Four conditions increase option value: (a) **high uncertainty** — the more you might learn, the more flexibility is worth; (b) **significant irreversibility** — costs that cannot be recovered make premature commitment expensive; (c) **staging is possible** — you can invest incrementally rather than all at once; (d) **no urgent deadline** — the value of waiting isn't destroyed by competitive preemption. When all four hold, option value can dominate the analysis. When none hold, NPV is sufficient.

The mindset shift matters as much as the mathematics. The conventional stance toward uncertainty is defensive: "we don't know enough, so we shouldn't invest." The option-value stance is strategic: "we don't know enough, so we should invest a little to learn, preserving the option to invest more later." The startup building a minimum viable product, the pharma company running a Phase I trial, the oil company buying exploration rights — all are buying options, not commitments.
:::
:::

::: {#ch-sequential .chapter}
::: chapter-number
Section 8
:::

::: chapter-title
Sequential Decisions and the Value of Information
:::

::: {#s-trees .section}
::: section-title
Decision Trees
:::

When decisions unfold over time — when an initial choice leads to new information, which informs a subsequent choice — the structure is a **decision tree**. Decision nodes (squares) represent choices under the agent's control. Chance nodes (circles) represent uncertain events governed by nature. Terminal nodes carry payoffs. The tree is solved by **backward induction**: starting at the terminals, choosing optimally at each decision node and computing expected values at each chance node, working backward to the present.
:::

::: {#s-voi .section}
::: section-title
Value of Information
:::

Before committing, you can often reduce uncertainty by gathering information — running a test, consulting an expert, conducting a pilot study. Howard Raiffa and Robert Schlaifer formalized the value of this information-gathering in *Applied Statistical Decision Theory* (1961).

**Expected Value of Perfect Information (EVPI)** is the maximum you should pay to learn the true state of the world before deciding. It equals the difference between the expected payoff of the best decision with perfect information and the expected payoff of the best decision without it. EVPI provides an upper bound on the worth of any investigation.

**Expected Value of Sample Information (EVSI)** is the value of imperfect information — a test with known accuracy that reduces but doesn't eliminate uncertainty. EVSI ≤ EVPI always. Computing EVSI requires specifying how the information updates your beliefs (via Bayes' theorem) and how the updated beliefs change the optimal action.
:::

::: {#s-act .section}
::: section-title
When to Act
:::

Continue gathering information as long as the expected value of the next piece of information exceeds its cost — including the cost of delay. Common failure modes: gathering too little due to impatience or overconfidence; gathering too much due to decision avoidance or perfectionism; failing to recognize that delay itself carries cost (competitive preemption, option decay, missed windows).

Raiffa's *Decision Analysis* (1968) synthesized these ideas — utility theory, Bayesian updating, decision trees, value of information — into a practical framework. It marked the shift from abstract statistical decision theory to applied decision analysis: a prescriptive discipline aimed at helping real people structure and evaluate real choices.
:::
:::

::: {#ch-three .chapter}
::: chapter-number
Section 9
:::

::: chapter-title
Three Theories of Decision
:::

::: {#s-trichotomy .section}
::: section-title
The Trichotomy
:::

David Bell, Howard Raiffa, and Amos Tversky organized the field around a three-way distinction in their 1988 edited volume *Decision Making: Descriptive, Normative, and Prescriptive Interactions* (Cambridge University Press):

::: {.callout .note}
::: callout-label
Note
:::

**Normative:** How should a perfectly rational agent decide? Expected utility, VNM axioms, Bayesian updating. The standard is internal consistency — preferences that satisfy the axioms are rational by definition. This is the "should."

**Descriptive:** How do actual humans decide? Prospect theory, heuristics and biases, bounded rationality. The standard is empirical accuracy — does the model predict observed behavior? This is the "do."

**Prescriptive:** How can we help imperfect decision-makers do better? Decision analysis, structured elicitation, nudges, debiasing. The standard is practical improvement. Bell, Raiffa, and Tversky described their subjects as people with "divided minds with different aspirations" — the prescriptive project is helping them reconcile those divisions. This is the "can."
:::
:::

::: {#s-why-matters .section}
::: section-title
Why the Distinction Matters
:::

The three perspectives need each other. You cannot identify a "bias" (descriptive finding) without a standard of correctness (normative theory). You cannot design a helpful intervention (prescriptive method) without knowing both the target (normative) and the failure modes (descriptive). Conflating the three leads to two common errors: treating normative theory as a description of behavior (overestimating human rationality) or treating descriptive findings as reasons to abandon normative standards (underestimating human potential).

For an AI advisor, the prescriptive layer is the one that does the work. The advisor is not a perfectly rational agent (normative applies as aspiration, not description). The advisor is not predicting what the operator will do (descriptive is a diagnostic tool, not the goal). The advisor is trying to help the operator make better decisions than they would make alone — and "better" is defined by the operator's own values, not the advisor's.
:::
:::

::: {#ch-board .chapter}
::: chapter-number
Section 10
:::

::: chapter-title
Board Connection
:::

::: {#s-obligation .section}
::: section-title
The Advisory Obligation
:::

An AI advisory board member in Loop MMT operates in the prescriptive layer. Its job is to structure decisions, not to make them. Structuring means: enumerating alternatives the operator may not have considered, making objectives and trade-offs explicit, representing uncertainty honestly (including admitting ignorance), detecting framing effects that might be distorting the operator's evaluation, and flagging when the operator's stated preferences conflict with each other.

The board should never present expected utility calculations as if probabilities are known when they are not. This is the most common and most dangerous advisory failure mode: treating uncertainty as risk, assigning made-up probabilities, and computing expected values that carry a false precision. When probabilities are unknown, say so. When the belief-plausibility interval is wide (per the Dempster-Shafer framework), say so.
:::

::: {#s-optimize-satisfice .section}
::: section-title
When to Optimize, When to Satisfice
:::

Optimize when: the problem is well-defined, alternatives are enumerable, probabilities are estimable, stakes justify the computation, and the operator has time. Satisfice when: the problem is novel, alternatives are open-ended, probabilities are unknown, the cost of prolonged search exceeds the expected improvement, or the operator needs to act now.

Most decisions in Loop MMT's operating context — construction, campground management, software development, seasonal butcher shop operations — are satisficing-appropriate. The board should calibrate its recommendations accordingly. "Here is an option that meets your stated requirements and constraints" is often the correct form of a recommendation. "Here is the globally optimal solution assuming seventeen parameters we estimated from limited data" is usually not.
:::

::: {#s-risk-tolerance .section}
::: section-title
Unknown Risk Tolerance
:::

When the operator's risk tolerance is unknown, the board has three options. First: infer it from revealed preferences in past decisions (the operator chose X over Y, which implies a certain range of risk attitudes). Second: present calibrated trade-offs ("would you prefer A for certain or a 50/50 chance of B or C?") to narrow the range. Third: use robust methods (maximin, minimax regret) that do not require risk-tolerance assumptions, acknowledging the conservatism this entails.

The Dempster-Shafer framework makes the right structural move here: assign belief mass to the full frame of discernment (ignorance) rather than guessing at a probability distribution over risk attitudes. The recommendation can then be conditional: "if you are more concerned about downside protection, option A; if you can tolerate variance for higher expected value, option B; I don't have enough information to determine which you prefer."
:::

::: {#s-cross .section}
::: section-title
Cross-Pack Connections
:::

**Dempster-Shafer → Decision Theory.** D-S evidence combination produces belief intervals as inputs to decision evaluation. A narrow interval (belief ≈ plausibility) indicates near-certain evidence — the domain of risk. A wide interval (large plausibility-belief gap) indicates significant ignorance — the domain of uncertainty. The width of the interval should determine which decision framework the board applies.

**Probability → Decision Theory.** Probability theory provides the mathematical machinery beneath expected utility: distributions, conditional probability, Bayes' theorem. Decision theory consumes probability as an input and combines it with utility to produce action recommendations.

**Pareto → Decision Theory.** Pareto analysis identifies the efficient frontier — the set of options where no objective can be improved without cost to another. Decision theory selects a point on that frontier by making value trade-offs explicit. The two are complementary: Pareto says "these options are non-dominated," decision theory says "among the non-dominated options, here is how to choose."
:::
:::

::: {#ch-refs .chapter}
::: chapter-number
References
:::

::: chapter-title
References
:::

Allais, M. (1953). "Le comportement de l'homme rationnel devant le risque: Critique des postulats et axiomes de l'école américaine." *Econometrica*, 21(4), 503–546.

Bell, D. E., Raiffa, H., & Tversky, A. (Eds.). (1988). *Decision Making: Descriptive, Normative, and Prescriptive Interactions*. Cambridge University Press.

Bernoulli, D. (1738/1954). "Exposition of a New Theory on the Measurement of Risk." *Econometrica*, 22(1), 23–36. [Translation of 1738 Latin original.]

Dixit, A. K., & Pindyck, R. S. (1994). *Investment under Uncertainty*. Princeton University Press.

Ellsberg, D. (1961). "Risk, Ambiguity, and the Savage Axioms." *Quarterly Journal of Economics*, 75(4), 643–669.

Gigerenzer, G., Todd, P. M., & the ABC Research Group. (1999). *Simple Heuristics That Make Us Smart*. Oxford University Press.

Hurwicz, L. (1951). "Optimality Criteria for Decision Making Under Ignorance." Cowles Commission Discussion Paper, Statistics No. 370.

Kahneman, D., & Tversky, A. (1979). "Prospect Theory: An Analysis of Decision under Risk." *Econometrica*, 47(2), 263–292.

Keeney, R. L., & Raiffa, H. (1976). *Decisions with Multiple Objectives: Preferences and Value Trade-Offs*. Wiley.

Knight, F. H. (1921). *Risk, Uncertainty, and Profit*. Houghton Mifflin.

Myers, S. C. (1977). "Determinants of Corporate Borrowing." *Journal of Financial Economics*, 5(2), 147–175.

Peterson, M. (2017). *An Introduction to Decision Theory* (2nd ed.). Cambridge University Press.

Raiffa, H. (1968). *Decision Analysis: Introductory Lectures on Choices under Uncertainty*. Addison-Wesley.

Raiffa, H., & Schlaifer, R. (1961). *Applied Statistical Decision Theory*. Harvard University Press.

Ruggeri, K., et al. (2020). "Replicating patterns of prospect theory for decision under risk." *Nature Human Behaviour*, 4, 622–633.

Savage, L. J. (1951). "The Theory of Statistical Decision." *Journal of the American Statistical Association*, 46(253), 55–67.

Savage, L. J. (1954). *The Foundations of Statistics*. Wiley.

Simon, H. A. (1955). "A Behavioral Model of Rational Choice." *Quarterly Journal of Economics*, 69(1), 99–118.

Simon, H. A. (1956). "Rational Choice and the Structure of the Environment." *Psychological Review*, 63(2), 129–138.

Tversky, A., & Kahneman, D. (1992). "Advances in Prospect Theory: Cumulative Representation of Uncertainty." *Journal of Risk and Uncertainty*, 5(4), 297–323.

von Neumann, J., & Morgenstern, O. (1944). *Theory of Games and Economic Behavior*. Princeton University Press. [2nd ed. with axiomatic utility appendix, 1947.]

Wald, A. (1950). *Statistical Decision Functions*. Wiley.
:::
:::
:::

------------------------------------------------------------------------

::: page-footer
Loop MMT™ · Multi-Module Theory · Decision Theory Knowledge Pack · v1 © 2026 Shea Gunther · [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/deed.en){style="color:inherit;"}
:::
