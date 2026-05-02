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
Probability & Statistics — The Mathematics of Uncertainty
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
-   [1 · Probability Axioms](#ch-axioms)
-   [2 · Conditional Probability & Bayes' Theorem](#ch-bayes)
-   [3 · Interpretations of Probability](#ch-interpretations)
-   [4 · Random Variables & Distributions](#ch-distributions)
-   [5 · Limit Theorems](#ch-limits)
-   [6 · Hypothesis Testing](#ch-testing)
-   [7 · P-Values & the Replication Crisis](#ch-pvalues)
-   [8 · Regression & Prediction](#ch-regression)
-   [9 · Statistical Fallacies](#ch-fallacies)
-   [10 · Board Connection](#ch-board)
-   [References](#ch-refs)

::: {.content role="main"}
::: {#ch-abstract .abstract-box}
::: abstract-label
About This Document
:::

This is a reference document on probability theory and mathematical statistics, designed to be loaded into AI advisory conversations. It covers the axiomatic foundations of probability, Bayes' theorem and belief updating, the major interpretations of what probability *is*, core distributions and their properties, the limit theorems that make statistics work, hypothesis testing and its failure modes, regression basics, and the most consequential statistical fallacies.

The operational purpose is to provide the mathematical floor under several other packs in the corpus. The Dempster-Shafer pack (belief functions and evidence combination) assumes this material. The Information Theory pack (entropy, mutual information) is built on probability distributions. The Causal Reasoning pack (Simpson's paradox, confounding) requires the statistical concepts here. The Cognitive Bias pack (base rate neglect, anchoring) connects to the fallacies section. Without this pack, those packs are floating — they use the vocabulary and machinery of probability without grounding it.

This pack is written as interpretive framework and failure-mode reference, not as a textbook. The AI already has the mathematical training. What it needs is the interpretive context: what these tools mean, when they break, what the common mistakes are, and how to communicate uncertainty honestly to non-technical operators.
:::

::: {#ch-axioms .chapter}
::: chapter-number
Section 1
:::

::: chapter-title
Probability Axioms
:::

::: {#s-before-kolmogorov .section}
::: section-title
Before the Axioms
:::

Probability theory existed for centuries before anyone formalized it. Pascal and Fermat worked out gambling problems in the 1650s. Laplace systematized the "classical" approach in 1812: the probability of an event equals the number of favorable outcomes divided by the total number of equally likely outcomes. This works for coins and cards but fails immediately when outcomes are not equally likely — which is most of reality.

By the early twentieth century, probability was a collection of useful calculations lacking a rigorous mathematical foundation. Multiple formalizations competed. Richard von Mises proposed in 1919 a frequentist foundation based on "collectives" — infinite sequences of trials with limiting relative frequencies. The approach was conceptually appealing but mathematically awkward, and it could not handle events that do not admit repetition.
:::

::: {#s-kolmogorov .section}
::: section-title
Kolmogorov's Axioms (1933)
:::

Andrey Kolmogorov published *Grundbegriffe der Wahrscheinlichkeitsrechnung* (Foundations of the Theory of Probability) in 1933. The monograph was roughly sixty pages long and permanently settled the mathematical foundations of the field. Kolmogorov's insight was to ground probability in Lebesgue measure theory, which had been developed two decades earlier. The analogy is direct: probability of an event corresponds to measure of a set; mathematical expectation corresponds to Lebesgue integration.

A **probability space** is a triple (Ω, F, P) where:

- **Ω** (the sample space) is the set of all possible outcomes of the random experiment.
- **F** (the event space) is a σ-algebra of subsets of Ω — the collection of events to which we can assign probabilities. The σ-algebra requirement ensures closure under complementation and countable union.
- **P** (the probability measure) is a function from F to [0, 1] satisfying the axioms.

The three axioms:

1. **Non-negativity.** For any event A ∈ F, P(A) ≥ 0.
2. **Normalization.** P(Ω) = 1. Something happens.
3. **σ-additivity (countable additivity).** For any countable sequence of mutually exclusive events A₁, A₂, A₃, ..., we have P(A₁ ∪ A₂ ∪ A₃ ∪ ...) = P(A₁) + P(A₂) + P(A₃) + ...

That is the entire foundation. Everything else — Bayes' theorem, the law of large numbers, the central limit theorem, all of modern statistics — is derived from these three axioms plus standard measure-theoretic machinery.
:::

::: {#s-consequences .section}
::: section-title
Immediate Consequences
:::

From the axioms alone:

- P(∅) = 0. The impossible event has probability zero.
- P(Aᶜ) = 1 − P(A). Complementation.
- If A ⊆ B, then P(A) ≤ P(B). Monotonicity.
- P(A ∪ B) = P(A) + P(B) − P(A ∩ B). Inclusion-exclusion.
- For any event A, 0 ≤ P(A) ≤ 1. Probability is bounded.

These are not additional axioms. They are theorems — necessary consequences of Kolmogorov's three axioms.

::: {.callout .key}
::: callout-label
What the axioms do not say
:::
The axioms define how probabilities must behave. They say nothing about what probability *means* — whether it represents long-run frequency, degree of belief, or propensity. The interpretation question is separate from the mathematical formalism, and it matters enormously for practice. That question is addressed in Section 3.
:::
:::

::: {#s-sigma .section}
::: section-title
Why σ-Additivity Matters
:::

Finite additivity (the rule works for finitely many disjoint events) is weaker than σ-additivity (works for countably many). Some authors — notably Bruno de Finetti — rejected σ-additivity as an unnecessary constraint on subjective probability. In practice, σ-additivity is what allows the machinery of modern probability to work: it connects probability to measure theory, enables limit theorems, and makes conditional expectations well-defined. Without it, the mathematical infrastructure collapses. Almost all working probability and statistics assumes σ-additivity.
:::
:::

::: {#ch-bayes .chapter}
::: chapter-number
Section 2
:::

::: chapter-title
Conditional Probability & Bayes' Theorem
:::

::: {#s-conditional .section}
::: section-title
Conditional Probability
:::

The conditional probability of A given B is:

**P(A | B) = P(A ∩ B) / P(B)**, provided P(B) > 0.

This is a definition, not a theorem. It says: to compute the probability of A given that B has occurred, restrict attention to the part of the sample space where B is true, then ask how much of that space also contains A.

Conditional probability is the single most important concept in applied probability. Nearly every interesting probability question is conditional: What is the probability of disease given a positive test? What is the probability of guilt given the evidence? What is the probability of the hypothesis given the data?
:::

::: {#s-product-rule .section}
::: section-title
The Product Rule and the Chain Rule
:::

Rearranging the definition: **P(A ∩ B) = P(A | B) · P(B)**. This is the **product rule**. It generalizes to any finite number of events:

P(A₁ ∩ A₂ ∩ ... ∩ Aₙ) = P(A₁) · P(A₂ | A₁) · P(A₃ | A₁ ∩ A₂) · ... · P(Aₙ | A₁ ∩ ... ∩ Aₙ₋₁)

This is the **chain rule of probability**, and it is exact — no approximation involved.
:::

::: {#s-independence .section}
::: section-title
Independence
:::

Events A and B are **independent** if P(A ∩ B) = P(A) · P(B), or equivalently, if P(A | B) = P(A). Knowing B happened gives no information about A. Independence is a property of the model, not a property of the world. Two events that are physically unrelated may still be dependent in a particular probability model, and vice versa.

**Conditional independence** is different from independence. A and B can be conditionally independent given C (P(A ∩ B | C) = P(A | C) · P(B | C)) while being marginally dependent, or vice versa. This distinction is critical for causal reasoning — see the Causal Reasoning pack.
:::

::: {#s-bayes .section}
::: section-title
Bayes' Theorem
:::

Bayes' theorem follows from the product rule applied in two directions. Since P(A ∩ B) = P(A | B) · P(B) and also P(A ∩ B) = P(B | A) · P(A), we can set them equal and solve:

**P(A | B) = P(B | A) · P(A) / P(B)**

The denominator P(B) is often computed via the law of total probability: P(B) = Σᵢ P(B | Aᵢ) · P(Aᵢ), summing over a partition {A₁, A₂, ...} of the sample space.

The derivation is trivial. The implications are not. In the language of inference:

- **P(A)** is the **prior** — the probability of hypothesis A before seeing the data.
- **P(B | A)** is the **likelihood** — the probability of observing data B if hypothesis A is true.
- **P(A | B)** is the **posterior** — the updated probability of A after seeing B.
- **P(B)** is the **evidence** (or marginal likelihood) — a normalizing constant ensuring the posterior sums to 1.

The core equation of belief updating: **posterior ∝ likelihood × prior**. The posterior is proportional to the product of what you believed before (prior) and how well the hypothesis predicts the data (likelihood).
:::

::: {#s-bayes-example .section}
::: section-title
Worked Example: Medical Testing
:::

A disease has prevalence 1 in 1,000. A test for the disease has 99% sensitivity (true positive rate) and 5% false positive rate. You test positive. What is the probability you have the disease?

Let D = has disease, T = tests positive.

- Prior: P(D) = 0.001
- Likelihood: P(T | D) = 0.99
- False positive rate: P(T | ¬D) = 0.05
- P(T) = P(T | D)·P(D) + P(T | ¬D)·P(¬D) = 0.99 × 0.001 + 0.05 × 0.999 = 0.00099 + 0.04995 = 0.05094
- Posterior: P(D | T) = 0.00099 / 0.05094 ≈ 0.019 — roughly 2%.

A positive test result, despite the test's high accuracy, gives you only a 2% chance of actually having the disease. The low base rate dominates. This is the single most important example in applied probability, and it is the example most consistently misunderstood by both professionals and the public.
:::

::: {#s-sequential .section}
::: section-title
Sequential Updating
:::

Bayesian updating is sequential and commutative. The posterior from one piece of evidence becomes the prior for the next. The order in which evidence arrives does not matter — the final posterior is the same regardless of sequence. This follows from the commutativity of multiplication.

This property is not shared by all inference procedures. Frequentist methods that depend on the experimental design (the stopping rule, the number of tests planned) can give different answers depending on the order and manner of data collection. Bayesian updating depends only on what data were actually observed, not on what data might have been observed but weren't.
:::

::: {#s-odds .section}
::: section-title
The Odds Form
:::

Bayes' theorem can be expressed in odds:

**Posterior odds = Prior odds × Likelihood ratio**

where the likelihood ratio (or Bayes factor) is P(B | A) / P(B | ¬A). This form is often more intuitive for communication: it separates the contribution of the data (the likelihood ratio) from the contribution of background knowledge (the prior odds). A likelihood ratio of 10 means the data are 10 times more likely under the hypothesis than under the alternative — the data shift the odds by a factor of 10, regardless of where the prior odds started.
:::
:::

::: {#ch-interpretations .chapter}
::: chapter-number
Section 3
:::

::: chapter-title
Interpretations of Probability
:::

::: {#s-what-is .section}
::: section-title
The Question
:::

Kolmogorov's axioms tell us how probabilities must behave. They do not tell us what probability *is*. This is not a merely philosophical question — different interpretations lead to different statistical practices, different answers to the same question, and different notions of what constitutes a valid inference.
:::

::: {#s-frequentist .section}
::: section-title
The Frequentist Interpretation
:::

Probability is the long-run relative frequency of an event in repeated trials. P(heads) = 0.5 means that if you flip the coin many times, the proportion of heads converges to 0.5. This interpretation is clean for repeatable experiments but breaks down for singular events. What is the probability that it rained on the day Caesar crossed the Rubicon? That a specific defendant is guilty? That a particular asteroid will hit Earth? These are one-off events with no long-run frequency to appeal to.

In frequentist statistics, probability attaches to data, not to hypotheses. Parameters are fixed but unknown. A 95% confidence interval does not mean there is a 95% probability the parameter lies inside it — it means that the procedure that generated the interval will cover the true parameter 95% of the time across many repetitions of the experiment. The probability is about the procedure, not about this particular interval.
:::

::: {#s-bayesian .section}
::: section-title
The Bayesian Interpretation
:::

Probability is a degree of belief — a quantification of how confident a rational agent is in a proposition. P(A) = 0.7 means the agent considers A to be 70% plausible given available information. This interpretation handles singular events naturally: you can have a degree of belief about anything.

There are subdivisions within Bayesianism. **Subjective Bayesians** (de Finetti, Savage) treat probability as personal belief — different agents with different information or different starting beliefs will have different probabilities, and that is fine. **Objective Bayesians** (Jaynes, Jeffreys) seek prior distributions that formally express ignorance, hoping the resulting posteriors are in some sense objective. **Empirical Bayesians** estimate the prior from the data itself.

The Bayesian interpretation allows direct probability statements about hypotheses: "There is a 92% probability that the treatment is effective" is a meaningful Bayesian statement. This is what most non-statisticians think statistical results mean. It is what frequentist results explicitly do not mean.
:::

::: {#s-jaynes .section}
::: section-title
Jaynes and Probability as Logic
:::

E. T. Jaynes, in *Probability Theory: The Logic of Science* (published posthumously in 2003), argued that probability theory is not merely a tool but the uniquely correct extension of Boolean logic to reasoning under uncertainty. His argument rests on Cox's theorem (1946): if you want to assign real-valued plausibilities to propositions such that (1) plausibilities are represented by real numbers, (2) the system agrees qualitatively with common sense, and (3) the system is consistent, then those plausibilities must obey the rules of probability theory. There is no alternative consistent system.

Jaynes called this "probability as extended logic." Under this view, Bayesian inference is not a philosophical preference — it is a logical necessity. Any other system of plausible reasoning either reduces to probability theory under a monotonic transformation or is internally inconsistent.

This is a strong claim, and it has been debated. Halpern showed that relaxing certain mathematical assumptions in Cox's theorem permits alternatives. Arnborg and Sjödin responded with additional common-sense postulates that rule out those alternatives. The debate continues, but the practical upshot is widely accepted: probability theory, properly applied, is the normative standard for reasoning under uncertainty. Deviations from it are either reducible to it or produce absurdities.
:::

::: {#s-when-matters .section}
::: section-title
When the Distinction Matters
:::

For most routine data analysis, the Bayesian-frequentist distinction produces negligible practical differences. With large samples and weak priors, Bayesian posteriors and frequentist confidence intervals converge numerically. The distinction matters when:

- **Small samples.** Priors have a large effect. Bayesian methods can incorporate prior knowledge; frequentist methods cannot.
- **Multiple comparisons.** Bayesian methods handle them naturally through the prior; frequentist methods require ad hoc corrections (Bonferroni, etc.).
- **Stopping rules.** Whether you stop data collection at a fixed sample size or stop when a threshold is reached affects frequentist inference (because it changes the sampling distribution) but not Bayesian inference (because the likelihood is the same).
- **Communication.** People want to know "What is the probability the treatment works?" That is a Bayesian question. Frequentist methods answer a different question: "How surprising is this data if the treatment doesn't work?"
- **Interpretation of intervals.** A 95% credible interval (Bayesian) means there is 95% probability the parameter is inside it. A 95% confidence interval (frequentist) means the procedure captures the parameter 95% of the time. These sound similar but are logically different statements.
:::
:::

::: {#ch-distributions .chapter}
::: chapter-number
Section 4
:::

::: chapter-title
Random Variables & Distributions
:::

::: {#s-rv .section}
::: section-title
Random Variables
:::

A **random variable** is a measurable function from the sample space Ω to the real numbers. It is not a variable in the algebraic sense and it is not random in any mystical sense — it is a function that maps outcomes to numbers so we can do mathematics with them. If you roll a die, the random variable X might map each face to its number: X(⚀) = 1, X(⚁) = 2, etc.

A random variable is **discrete** if it takes countably many values, **continuous** if its distribution is described by a density function. The **cumulative distribution function** (CDF) F(x) = P(X ≤ x) completely specifies the distribution of any random variable.
:::

::: {#s-expectation .section}
::: section-title
Expectation and Variance
:::

The **expectation** (mean) of a random variable X is E[X] = Σ x·P(X = x) for discrete X, or ∫ x·f(x) dx for continuous X with density f. Expectation is linear: E[aX + bY] = aE[X] + bE[Y], always, regardless of dependence between X and Y.

The **variance** is Var(X) = E[(X − E[X])²] = E[X²] − (E[X])². It measures spread — how far values typically fall from the mean. The **standard deviation** σ = √Var(X) has the same units as X. For independent random variables, Var(X + Y) = Var(X) + Var(Y). Dependence breaks this: for correlated variables, Var(X + Y) = Var(X) + Var(Y) + 2·Cov(X, Y).
:::

::: {#s-workhorses .section}
::: section-title
The Workhorse Distributions
:::

**Bernoulli(p).** A single binary trial with success probability p. Takes values 0 or 1. Mean = p, Variance = p(1 − p). The atom of discrete probability.

**Binomial(n, p).** The number of successes in n independent Bernoulli trials. Mean = np, Variance = np(1 − p). The distribution behind polling, A/B testing, quality control — anything that counts successes out of fixed trials.

**Poisson(λ).** The number of events in a fixed interval when events occur independently at rate λ. Mean = λ, Variance = λ. The distribution of rare events: radioactive decay, typos per page, goals per match, server requests per second. The Poisson is the limit of the binomial when n is large and p is small with np = λ.

**Normal (Gaussian) N(μ, σ²).** The bell curve. Parameterized by mean μ and variance σ². The normal distribution owes its dominance not to any empirical law about how things are distributed in nature but to the central limit theorem (Section 5): averages of many independent contributions converge to normality regardless of the underlying distribution. This is why it appears everywhere — not because things are inherently normal, but because many measured quantities are sums or averages.

**Exponential(λ).** The time between events in a Poisson process. Mean = 1/λ. It has the memoryless property: P(X > s + t | X > s) = P(X > t). If you've already waited s time units, the remaining wait time has the same distribution as if you just started. This is the only continuous distribution with this property.

**Uniform(a, b).** Equal probability everywhere on [a, b]. Often used as a model of ignorance — if you have no reason to favor any value over another.
:::

::: {#s-conjugate .section}
::: section-title
Conjugate Priors
:::

In Bayesian analysis, if the prior and the posterior belong to the same distributional family, the prior is called **conjugate** to the likelihood. The Beta distribution is conjugate to the binomial likelihood (Beta prior + binomial data → Beta posterior). The Gamma is conjugate to the Poisson. The Normal is conjugate to itself. Conjugate priors make computation tractable — the posterior has a known closed form and its parameters can be read directly as "prior successes" and "prior failures" updated with observed data.
:::
:::

::: {#ch-limits .chapter}
::: chapter-number
Section 5
:::

::: chapter-title
Limit Theorems
:::

::: {#s-lln .section}
::: section-title
The Law of Large Numbers
:::

The **weak law of large numbers** (Khintchine, 1929): For i.i.d. random variables X₁, X₂, ... with finite mean μ, the sample mean X̄ₙ = (X₁ + ... + Xₙ)/n converges in probability to μ. That is, for any ε > 0, P(|X̄ₙ − μ| > ε) → 0 as n → ∞.

The **strong law** (Kolmogorov, 1933): Under the same conditions, X̄ₙ → μ almost surely — the sample mean converges to the true mean with probability 1.

This is why sampling works. If you want to know the average height of a population, measure enough people and the sample average will be close to the population average. The law does not say how fast convergence happens (that depends on the variance), and it says nothing about any finite sample — it is a statement about the limit.

::: {.callout .warn}
::: callout-label
The Gambler's Fallacy
:::
The law of large numbers says the *proportion* of heads converges to 0.5. It does not say a run of heads must be "balanced" by a run of tails. Each flip is independent. After 10 heads in a row, the probability of heads on the next flip is still 0.5. The universe does not keep a ledger.
:::
:::

::: {#s-clt .section}
::: section-title
The Central Limit Theorem
:::

The **central limit theorem** (CLT): For i.i.d. random variables X₁, X₂, ... with finite mean μ and finite variance σ², the standardized sum (X̄ₙ − μ)/(σ/√n) converges in distribution to a standard normal N(0, 1) as n → ∞.

This is the most important theorem in statistics. It explains why the normal distribution appears everywhere: whenever you are measuring something that is the sum or average of many small independent contributions, the distribution of that measurement will be approximately normal, regardless of the shape of the underlying distribution.

The CLT requires finite variance. Distributions with infinite variance (heavy-tailed distributions like the Cauchy) do not obey the CLT — their sample means do not converge to normality. This is not a technicality. Financial returns are often heavy-tailed, which is why models that assume normality (like early versions of Value at Risk) underestimate extreme events.

The rate of convergence to normality depends on the skewness of the underlying distribution. For symmetric distributions, the CLT kicks in quickly (n ≈ 20–30 is often sufficient). For highly skewed distributions, much larger samples are needed.
:::
:::

::: {#ch-testing .chapter}
::: chapter-number
Section 6
:::

::: chapter-title
Hypothesis Testing
:::

::: {#s-np .section}
::: section-title
The Neyman-Pearson Framework
:::

Jerzy Neyman and Egon Pearson formalized hypothesis testing in the 1930s as a decision procedure with controlled error rates:

- **Null hypothesis (H₀):** The default assumption, typically "no effect" or "no difference."
- **Alternative hypothesis (H₁):** What you suspect is true.
- **Type I error (false positive):** Rejecting H₀ when it is true. The probability of this is α, the **significance level**.
- **Type II error (false negative):** Failing to reject H₀ when H₁ is true. The probability of this is β.
- **Power:** 1 − β. The probability of correctly rejecting H₀ when H₁ is true.
- **Effect size:** The magnitude of the difference you are trying to detect. Power depends on effect size, sample size, and α.

The framework is explicitly a decision procedure, not a measure of evidence. Neyman and Pearson designed it for repeated decision-making contexts (accept/reject batches in quality control) where long-run error rates matter. It was never intended to quantify the evidence in a single study.

::: {.callout .key}
::: callout-label
The Fisherian Confusion
:::
R. A. Fisher developed a different approach to testing, using p-values as continuous measures of evidence against the null. Fisher rejected the Neyman-Pearson framework's fixed α and pre-specified alternative hypothesis. In practice, the two frameworks were conflated into a hybrid that neither Fisher nor Neyman-Pearson would have endorsed: compute a p-value (Fisher), compare it to a fixed α (Neyman-Pearson), and interpret the result as evidence (Fisher) about a specific alternative (Neyman-Pearson). This hybrid is what most researchers actually do, and it is the source of much confusion.
:::
:::

::: {#s-power .section}
::: section-title
Power and Effect Size
:::

Most published studies are underpowered — they have insufficient sample size to detect the effects they claim to be looking for. Jacob Cohen estimated in 1962 that the median power of studies in psychology was about 0.48, meaning that even if a real effect existed, the studies had less than a coin-flip chance of detecting it. Subsequent analyses have found similar results across disciplines.

Low power has a devastating consequence beyond missed effects: when an underpowered study does find a statistically significant result, the probability that it is a true positive (the positive predictive value) drops dramatically. This is Ioannidis's central argument (see Section 7). Low power combined with publication bias (only significant results get published) means the published literature is enriched for false positives.

Effect size — the magnitude of the phenomenon — is at least as important as statistical significance. A treatment can be statistically significant with a trivially small effect (just increase the sample size) or statistically non-significant with a practically important effect (the study was too small).
:::
:::

::: {#ch-pvalues .chapter}
::: chapter-number
Section 7
:::

::: chapter-title
P-Values & the Replication Crisis
:::

::: {#s-pvalue-def .section}
::: section-title
What a P-Value Is
:::

A **p-value** is the probability of obtaining a test statistic at least as extreme as the one observed, assuming the null hypothesis is true. It is a property of the data relative to a model, not a property of the hypothesis.
:::

::: {#s-pvalue-not .section}
::: section-title
What a P-Value Is Not
:::

The following are all false but widely believed:

- **Not the probability that the null is true.** P(data | H₀) ≠ P(H₀ | data). Confusing these is the prosecutor's fallacy applied to science.
- **Not the probability that the result occurred by chance.** This is a restatement of the same error.
- **Not the probability of a false positive.** The false positive rate depends on the base rate (prevalence) of true effects — something the p-value does not incorporate.
- **Not a measure of effect size.** A tiny, meaningless effect can produce a tiny p-value with a large enough sample.
- **Not comparable across studies.** Two studies with p = 0.04 are not "equally significant" — they may differ in power, design, multiple comparisons, and the plausibility of their hypotheses.
- **Not evidence for the alternative.** A small p-value says the data are unlikely under the null. It says nothing about how likely they are under any specific alternative.

The ASA issued a formal statement on p-values in 2016 — the first time a major statistical association felt it necessary to explain to the scientific community what its most widely used tool actually means. The statement articulated six principles, of which the most important is: "Scientific conclusions and business or policy decisions should not be based only on whether a p-value passes a specific threshold."
:::

::: {#s-replication .section}
::: section-title
The Replication Crisis
:::

In 2005, John Ioannidis published "Why Most Published Research Findings Are False" in PLoS Medicine. The paper used a simple probabilistic model to show that under realistic assumptions about statistical power, prior probability of effects, bias, and the number of teams testing similar hypotheses, the positive predictive value of published findings can drop below 50%. The argument is essentially a Bayesian calculation: if most hypotheses tested are false (low prior), studies are underpowered (low sensitivity), and there is publication bias toward positive results, then a significant p-value is more likely to be a false positive than a true positive.

The paper has been criticized — Goodman and Greenland identified circularities in the model, Jager and Leek estimated empirically that the false positive rate in medicine is closer to 14% — but its broader argument has been vindicated by large-scale replication efforts. The Open Science Collaboration's 2015 attempt to replicate 100 psychology studies found that only about 36% replicated. Similar concerns have been raised in medicine, economics, and genetics.

The structural causes of the replication crisis include:

- **P-hacking.** Running many analyses and reporting only those with p < 0.05.
- **Publication bias.** Journals preferentially publish significant results, creating a literature enriched for false positives.
- **Underpowered studies.** Low power inflates the false discovery rate among published positive findings.
- **Flexible analysis ("researcher degrees of freedom").** Decisions about outlier exclusion, variable selection, subgroup analysis, etc. are made after seeing the data in ways that inflate the apparent significance.
- **HARKing.** Hypothesizing After Results are Known — presenting post hoc findings as if they were pre-specified.

::: {.callout .tip}
::: callout-label
The Corrective Movement
:::
The response has included pre-registration of studies and analysis plans, registered reports (where journals commit to publish based on the methods alone), open data and code sharing, and increased emphasis on effect sizes and confidence intervals over binary significance declarations. These are structural fixes — not fixes that depend on individual virtue.
:::
:::
:::

::: {#ch-regression .chapter}
::: chapter-number
Section 8
:::

::: chapter-title
Regression & Prediction
:::

::: {#s-correlation .section}
::: section-title
Correlation
:::

The **Pearson correlation coefficient** r measures the linear association between two variables, ranging from −1 (perfect negative linear relationship) to +1 (perfect positive). r = 0 means no *linear* association — but there can still be a strong nonlinear relationship. Correlation is symmetric (r(X, Y) = r(Y, X)) and unitless.

Correlation is not causation. This is so well known as to be a cliché, but the reverse error is less recognized: *causation does imply correlation* (in the absence of confounding), so the absence of correlation is (weak) evidence against a causal relationship.
:::

::: {#s-ols .section}
::: section-title
Ordinary Least Squares
:::

**Linear regression** fits Y = β₀ + β₁X + ε, where β₀ is the intercept, β₁ is the slope, and ε is the error term. The OLS method chooses β₀ and β₁ to minimize the sum of squared residuals Σ(Yᵢ − β₀ − β₁Xᵢ)². The resulting estimates have desirable properties (unbiased, minimum variance among linear unbiased estimators) under the Gauss-Markov assumptions.

R² — the coefficient of determination — measures the fraction of variance in Y explained by the model. R² = 0.6 means the model explains 60% of the variance. R² always increases when you add predictors, even useless ones, which is why adjusted R² (penalizing for the number of predictors) exists.
:::

::: {#s-fit-vs-explain .section}
::: section-title
Fit vs. Explanation
:::

A model can fit data well without explaining anything. Overfitting — capturing noise rather than signal — produces high R² on the training data and poor prediction on new data. The fundamental tension:

- **Prediction** asks: given new inputs, how accurately can we forecast outputs? It does not require understanding why.
- **Explanation** asks: what is the causal mechanism? It requires identifying which variables genuinely affect the outcome and how.

A model with 15 polynomial terms might predict beautifully within the range of the training data and catastrophically outside it. A simple linear model with the right causal variable might predict less precisely but generalize correctly.

::: {.callout .warn}
::: callout-label
Regression to the Mean
:::
Extreme observations on one measurement tend to be less extreme on a second measurement — not because of any causal mechanism, but because extreme observations are partly the result of luck (random error), and luck does not persist. This is a statistical phenomenon, not a causal one. Attributing regression to the mean to a causal intervention ("the treatment brought their scores down") is the **regression fallacy**. Galton discovered this in the 1880s studying the heights of parents and children, and it remains one of the most commonly misidentified patterns in data.
:::
:::
:::

::: {#ch-fallacies .chapter}
::: chapter-number
Section 9
:::

::: chapter-title
Statistical Fallacies
:::

::: {#s-prosecutor .section}
::: section-title
The Prosecutor's Fallacy
:::

Confusing P(evidence | innocent) with P(innocent | evidence). A forensic match probability of 1 in 10,000 does not mean there is a 1 in 10,000 chance the defendant is innocent. If the suspect was drawn from a city of 10 million, there are roughly 1,000 other people who would also match. The probability of innocence given the match depends on the prior probability of guilt (was there other evidence pointing to this person?) — which is Bayes' theorem.

The Sally Clark case is the most devastating real-world example. Expert witness Roy Meadow testified that the probability of two children dying of SIDS in one family was about 1 in 73 million, computed by squaring the single-SIDS rate — an assumption of independence that was unjustified (SIDS deaths within families are correlated). Clark was wrongly convicted; the conviction was later overturned. The case illustrates both the prosecutor's fallacy and the danger of treating dependent events as independent.

*Connection: this fallacy is the forensic application of base rate neglect — see below and the Cognitive Bias pack.*
:::

::: {#s-base-rate .section}
::: section-title
Base Rate Neglect
:::

Ignoring prior probabilities when evaluating conditional evidence. The medical test example in Section 2 is the canonical case: a 99%-accurate test with a 0.1% disease prevalence yields a positive predictive value of only 2%. People consistently overestimate the probability of disease after a positive test because they attend to the test accuracy (the likelihood) and ignore the disease rarity (the base rate).

Kahneman and Tversky attributed this to the **representativeness heuristic** — people judge probability by how representative an observation is of a category rather than by how prevalent the category is. A description of someone who "reads poetry, is quiet, and wears glasses" is judged more likely to be a librarian than a farmer, despite farmers vastly outnumbering librarians.

*Connection: this is the same underlying error as the prosecutor's fallacy, and it is the primary failure mode the Cognitive Bias pack addresses under "base rate neglect."*
:::

::: {#s-simpson .section}
::: section-title
Simpson's Paradox
:::

A trend that appears in several groups of data reverses or disappears when the groups are combined. The Berkeley admissions case (1973) is the textbook example: overall admission rates showed a bias against women, but department-by-department analysis showed a slight bias *in favor of* women. The paradox arose because women applied disproportionately to more competitive departments with lower acceptance rates.

Simpson's paradox is not a paradox in the logical sense — it is a consequence of confounding. The pooled data fails to account for a variable (department choice) that is correlated with both the group variable (gender) and the outcome (admission). Resolving it requires causal reasoning: you must determine which conditioning is correct, and that is a causal question, not a statistical one.

*Connection: Simpson's paradox is treated in detail in the Causal Reasoning pack, where it is shown that the correct resolution depends on the causal structure (the DAG), not on the data alone. Pearl (2009) has argued that Simpson's paradox is proof that causal reasoning cannot be reduced to statistical reasoning.*
:::

::: {#s-survivorship .section}
::: section-title
Survivorship Bias
:::

Analyzing only cases that survived a selection process and ignoring those that did not. The World War II aircraft armor example (due to Abraham Wald) is canonical: engineers wanted to add armor where returning planes showed the most bullet holes. Wald pointed out that the holes on returning planes showed where planes could *survive* being hit. The planes that didn't return were hit in the places with no visible holes. The armor should go where the holes *aren't*.

Survivorship bias produces systematic overestimation of success rates (we only see the survivors), underestimation of risk (the failures are invisible), and distorted attribution of causes (we attribute the survivors' traits to their success rather than recognizing that many who shared those traits failed).
:::

::: {#s-multiple .section}
::: section-title
The Multiple Comparisons Problem
:::

If you test 20 independent hypotheses at α = 0.05, you expect one false positive even if nothing is real. The probability of at least one false positive is 1 − (0.95)²⁰ ≈ 0.64. Candidate gene studies in genetics performed hundreds of tests and reported only the significant ones, producing a literature full of false discoveries. Genome-wide association studies corrected this by requiring p < 5 × 10⁻⁸, effectively a Bonferroni correction for roughly one million independent tests.

The multiple comparisons problem is a structural problem: it cannot be solved by individual caution. It requires either pre-registration of analyses (so the number of tests is known) or formal correction methods (Bonferroni, Benjamini-Hochberg, or Bayesian shrinkage).
:::

::: {#s-ecological .section}
::: section-title
The Ecological Fallacy
:::

Inferring individual-level relationships from group-level data. Countries with higher chocolate consumption per capita have more Nobel laureates per capita (a real published correlation). This does not mean that eating chocolate makes you smarter. The group-level correlation may reflect national wealth, educational investment, or any number of confounders that operate at the aggregate level.

The ecological fallacy is particularly insidious because aggregate data is often easier to obtain than individual data, and the temptation to draw individual conclusions from it is strong.
:::
:::

::: {#ch-board .chapter}
::: chapter-number
Section 10
:::

::: chapter-title
Board Connection
:::

::: {#s-board-statistical-claims .section}
::: section-title
Handling Statistical Claims in Source Material
:::

An AI advisor encountering statistical claims in source material must apply the following checks:

**Sample size and power.** Is the study large enough to detect the claimed effect? A study with 30 participants claiming to detect a small effect should be treated with skepticism — it almost certainly lacks the power to do so reliably.

**Base rates.** What is the prior probability that this claim is true? A study claiming to confirm a well-established finding in a large, well-powered replication is very different from a novel finding from a single small study in a field with low pre-study odds.

**Multiple comparisons.** Was this the primary analysis or one of many? If a study reports 40 outcomes and highlights the three significant ones, the effective evidence is near zero.

**Effect size vs. significance.** A "highly significant" result (p = 0.001) tells you the null is unlikely, but it does not tell you the effect is large or important. Always ask: how big is the effect, and does it matter?

**The Ioannidis checklist.** For any claimed finding, consider: (1) Was the study pre-registered? (2) Has it been replicated? (3) Is the field known for replication problems? (4) Are the researchers conflicted? (5) Was the analysis plan flexible? Any "yes" to questions 3–5 without "yes" to 1–2 should reduce confidence substantially.
:::

::: {#s-board-pvalue-trust .section}
::: section-title
When to Trust a Reported P-Value
:::

A reported p-value is trustworthy to the degree that the analysis that produced it was pre-specified, the multiple comparisons burden is accounted for, and the study has adequate power. A p-value from a pre-registered, adequately powered study with a single primary outcome is strong evidence. A p-value from a post hoc subgroup analysis in an underpowered study is essentially meaningless.

The advisor should never take a p-value at face value without context. The relevant questions are: What was the hypothesis? Was it pre-specified? How many tests were conducted? What is the power? What is the effect size? Without answers to these, the p-value is uninterpretable.
:::

::: {#s-board-uncertainty .section}
::: section-title
Communicating Uncertainty to Non-Technical Operators
:::

The operator (Shea, Rick, Christine — anyone who must act on the advisor's conclusions) is not a statistician. Communicating uncertainty honestly requires:

1. **Natural frequencies over percentages.** "3 out of 100" is processed more accurately than "3%." Gigerenzer's research has shown consistently that natural frequency formats reduce base rate neglect.

2. **Confidence as a range, not a point.** Never report a single number without a range. "We expect 85–110 orders" is honest. "We expect 97 orders" implies false precision.

3. **Explicit unknowns.** Name what you don't know. "This estimate assumes last year's customer return rate holds, but we haven't checked whether it has changed" is more useful than a confident-sounding number.

4. **Likelihood ratios for evidence strength.** When presenting evidence that updates a belief, express the strength of the evidence as a multiplier: "This test result makes the hypothesis 8 times more likely" is clearer than presenting raw probabilities.

5. **Refuse false precision.** If the uncertainty is genuinely large, say so. An honest "I don't know, and the data doesn't tell us" is more valuable than a precise-sounding answer that obscures ignorance.
:::

::: {#s-board-connections .section}
::: section-title
Connections to Other Packs
:::

**Dempster-Shafer pack.** Belief functions generalize probability by allowing explicit representation of ignorance. Where probability requires P(A) + P(¬A) = 1 (forcing you to commit your uncertainty), Dempster-Shafer allows Bel(A) + Bel(¬A) < 1 — the gap represents genuine ignorance. The relationship to Bayesian probability: when a Dempster-Shafer mass function is focused (all mass on singletons), it reduces to a standard probability distribution. The Dempster-Shafer pack handles evidence *combination*; this pack handles the underlying probability machinery that makes those combinations meaningful.

**Information Theory pack.** Shannon entropy H = −Σ p log p is defined in terms of a probability distribution. Mutual information, KL divergence, channel capacity — all of information theory is built on probability distributions. The Information Theory pack tells you how much information a message carries; this pack provides the probability framework that makes "information" a well-defined quantity.

**Causal Reasoning pack.** Simpson's paradox (Section 9) demonstrates that statistical association alone cannot resolve causal questions. Pearl's do-calculus extends probability theory to handle interventions, distinguishing P(Y | X) (observational) from P(Y | do(X)) (interventional). The Causal Reasoning pack provides the machinery for this distinction; this pack provides the probability foundation on which it operates.

**Cognitive Bias pack.** Base rate neglect, anchoring on p-values, the representativeness heuristic, and the gambler's fallacy are all failures of probabilistic reasoning. The Cognitive Bias pack catalogs the errors; this pack provides the normative standard — the correct calculation that the biases deviate from.
:::
:::

::: {#ch-refs .chapter}
::: chapter-number
References
:::

::: chapter-title
References
:::

::: {#s-refs .section}

Kolmogorov, A. N. *Grundbegriffe der Wahrscheinlichkeitsrechnung* (Foundations of the Theory of Probability). Berlin: Springer, 1933. English translation: New York: Chelsea Publishing, 1956. Second English edition with bibliography by A. T. Bharucha-Reid, 2018. The founding document. Sixty pages that put probability theory on a rigorous measure-theoretic foundation.

Jaynes, E. T. *Probability Theory: The Logic of Science*. Edited by G. Larry Bretthorst. Cambridge: Cambridge University Press, 2003. The case for probability as extended logic. Contains the Cox-Jaynes desiderata, the derivation of probability rules from consistency requirements, and extensive applications. Published posthumously; Jaynes died in 1998.

Cox, R. T. "Probability, Frequency and Reasonable Expectation." *American Journal of Physics* 14, no. 1 (1946): 1–13. The original derivation showing that any consistent system of plausible reasoning must reduce to probability theory.

Wasserman, Larry. *All of Statistics: A Concise Course in Statistical Inference*. New York: Springer, 2004. A compact graduate-level text covering both frequentist and Bayesian methods. The reference treatment for the mathematical machinery.

Gigerenzer, Gerd, Zeno Swijtink, Theodore Porter, Lorraine Daston, John Beatty, and Lorenz Krüger. *The Empire of Chance: How Probability Changed Science and Everyday Life*. Cambridge: Cambridge University Press, 1989. The historical development of probabilistic thinking and its penetration into science, medicine, and social policy.

Ioannidis, John P. A. "Why Most Published Research Findings Are False." *PLoS Medicine* 2, no. 8 (2005): e124. The paper that catalyzed the replication crisis conversation. Uses a probabilistic model to show that under realistic assumptions, published findings are enriched for false positives.

Goodman, Steven N. "A Dirty Dozen: Twelve P-Value Misconceptions." *Seminars in Hematology* 45, no. 3 (2008): 135–140. A systematic catalog of what p-values do not mean.

Wasserstein, Ronald L., and Nicole A. Lazar. "The ASA's Statement on p-Values: Context, Process, and Purpose." *The American Statistician* 70, no. 2 (2016): 129–133. The American Statistical Association's formal statement clarifying the interpretation of p-values.

Neyman, J., and E. S. Pearson. "On the Problem of the Most Efficient Tests of Statistical Hypotheses." *Philosophical Transactions of the Royal Society A* 231 (1933): 289–337. The formalization of hypothesis testing as a decision procedure with Type I and Type II error rates.

Cohen, Jacob. "The Earth Is Round (p < .05)." *American Psychologist* 49, no. 12 (1994): 997–1003. A classic critique of null hypothesis significance testing and its misuse in psychology.

Open Science Collaboration. "Estimating the Reproducibility of Psychological Science." *Science* 349, no. 6251 (2015): aac4716. The landmark replication study finding that only about 36% of psychology results replicated.

Bayes, Thomas. "An Essay Towards Solving a Problem in the Doctrine of Chances." *Philosophical Transactions of the Royal Society of London* 53 (1763): 370–418. Communicated posthumously by Richard Price. The original statement of what we now call Bayes' theorem.

de Finetti, Bruno. *Theory of Probability*. 2 vols. New York: Wiley, 1974–1975. The subjective Bayesian position. De Finetti's representation theorem and the rejection of σ-additivity.

Pearl, Judea. *Causality: Models, Reasoning, and Inference*. 2nd ed. Cambridge: Cambridge University Press, 2009. The formal treatment of Simpson's paradox, confounding, and the do-calculus. Demonstrates that causal questions cannot be answered by probability alone.

Gigerenzer, Gerd. "Mindless Statistics." *Journal of Socio-Economics* 33, no. 5 (2004): 587–606. A critique of the ritualistic use of null hypothesis significance testing.

Wald, Abraham. *Statistical Decision Functions*. New York: Wiley, 1950. The decision-theoretic foundation of statistics, including the survivorship bias analysis of WWII aircraft armor.
:::
:::
:::
