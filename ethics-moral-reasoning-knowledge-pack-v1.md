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
Ethics & Moral Reasoning Knowledge Pack
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

-   [Abstract](#ch-abstract)
-   [1 · The Landscape](#ch-landscape)
-   [2 · The Is-Ought Gap](#ch-isought)
-   [3 · Consequentialism](#ch-consequentialism)
-   [4 · Deontology](#ch-deontology)
-   [5 · Virtue Ethics](#ch-virtue)
-   [6 · Care Ethics](#ch-care)
-   [7 · Moral Particularism](#ch-particularism)
-   [8 · The Trolley Diagnostic](#ch-trolley)
-   [9 · Moral Uncertainty](#ch-uncertainty)
-   [10 · Framework Conflict](#ch-applied)
-   [11 · Board Connection](#ch-board)
-   [References](#ch-refs)

::: {.content role="main"}
::: {#ch-abstract .abstract-box}
::: abstract-label
About This Document
:::

This pack covers the frameworks for reasoning about what one *should* do. Not what one *can* do, not what maximizes self-interest, but what is right. The five major frameworks — consequentialism, deontology, virtue ethics, care ethics, and moral particularism — are presented alongside the tools for handling their disagreement: the trolley problem as a diagnostic for framework conflict, moral uncertainty as a methodology for acting under ethical disagreement, and the is-ought gap as the constraint that makes the whole enterprise irreducibly hard.

This is not the Political Philosophy pack (justice, social contracts, institutional design — that exists elsewhere in the corpus) and not the Decision Theory pack (rational choice under uncertainty). This pack covers the *moral* dimension: is this action right or wrong, and how do you reason about it when your frameworks disagree?

The operational purpose: equip an AI advisor to detect ethical dimensions in advisory questions, identify which frameworks apply, and present framework conflicts transparently. An advisor that collapses genuine moral disagreement into a confident recommendation is failing at its job.
:::

::: {#ch-landscape .chapter}
::: chapter-number
Section 1
:::

::: chapter-title
The Landscape
:::

Moral philosophy is organized around a disagreement that has persisted for twenty-five centuries. Unlike scientific disputes, which can be resolved by evidence, or mathematical disputes, which can be resolved by proof, ethical disputes resist resolution because the competing frameworks begin from genuinely different premises about what makes an action right. Consequentialism starts from outcomes. Deontology starts from duties. Virtue ethics starts from character. Care ethics starts from relationships. Particularism refuses to start from general principles at all.

These are not merely different emphases within a shared project. They are different answers to different questions. A consequentialist asking "what produces the best outcome?" and a deontologist asking "what does duty require?" may arrive at the same verdict in easy cases and opposite verdicts in hard ones. The disagreement is structural, not accidental.

  Framework             Evaluates                          Central Concept                Key Figures
  --------------------- ---------------------------------- ------------------------------ ----------------------------
  Consequentialism      Outcomes of actions                Utility / welfare              Bentham, Mill, Sidgwick
  Deontology            Conformity to rules                Duty / categorical imperative  Kant
  Virtue Ethics         Character of agent                 Eudaimonia / phronesis         Aristotle, MacIntyre
  Care Ethics           Quality of relationships           Care / responsiveness          Gilligan, Noddings
  Moral Particularism   Particular features of situations  Holism about reasons           Dancy, Ross

Before examining the frameworks, there is a prior constraint that shapes the entire field. In 1739, David Hume identified a gap between descriptive claims ("this is the case") and normative claims ("this ought to be the case") that no amount of factual information can bridge on its own. This is-ought gap is not one theory among many — it is the foundational difficulty that every ethical theory must reckon with. It is covered next.
:::

::: {#ch-isought .chapter}
::: chapter-number
Section 2
:::

::: chapter-title
The Is-Ought Gap
:::

::: {#s-hume .section}
::: section-title
Hume's Observation
:::

In Book 3, Part 1 of *A Treatise of Human Nature* (1739–40), David Hume noticed something about moral arguments that has never been satisfactorily resolved. Writers on morality, he observed, begin by discussing matters of fact — the nature of God, the structure of society, observable human behavior — using "is" and "is not." Then, without warning, they shift to prescriptions about what "ought" or "ought not" to be done. Hume found the transition inexplicable. The new relation expressed by "ought" seemed entirely different in kind from the factual relations expressed by "is," and no argument was given for the leap.

This is **Hume's Law**, sometimes called **Hume's Guillotine**: no set of purely descriptive premises can yield a normative conclusion. "Humans evolved to be omnivores" does not entail "humans ought to eat meat." "This policy will maximize GDP" does not entail "this policy ought to be adopted." To reach a normative conclusion, you need at least one normative premise — which is exactly the kind of claim that needs justification and cannot be established by further facts.
:::

::: {#s-moore .section}
::: section-title
Moore's Naturalistic Fallacy
:::

G.E. Moore sharpened the critique in *Principia Ethica* (1903). Moore argued that "good" is a simple, unanalyzable property that cannot be identified with any natural property — not pleasure, not evolutionary fitness, not social approval. His weapon was the **open-question argument**: for any natural property N you propose as the definition of "good," the question "X has property N, but is X good?" remains genuinely open. If "good" just *meant* the same thing as N, the question would be trivially closed, like asking "this bachelor is unmarried?" The fact that it stays open shows "good" is not reducible to N. Identifying moral properties with natural properties is the **naturalistic fallacy**.

Hume and Moore are making related but distinct points. Hume's is about logic: you cannot derive an "ought" from an "is." Moore's is about metaphysics: moral properties are not natural properties. Both converge on the same practical constraint: facts alone do not determine values.
:::

::: {#s-responses .section}
::: section-title
Challenges to the Gap
:::

The is-ought gap has been contested. John Searle argued that institutional facts bridge it: "Jones promised to pay Smith five dollars" entails "Jones ought to pay Smith five dollars," because promising is constitutively normative — the concept of a promise just *is* the concept of placing oneself under obligation. Alasdair MacIntyre argued that functional evaluations bridge it: "this watch is inaccurate and too heavy" entails "this is a bad watch," because watches have a purpose. If human beings have a natural purpose (*telos*), evaluative conclusions about human action might follow from facts about human nature. Hilary Putnam argued more broadly that fact and value are entangled — our descriptions of the world are already value-laden, and our values are responsive to facts.

Most philosophers accept some version of the gap. Ethical naturalists contend that goal-directed analysis can bridge it: "in order for agent A to achieve goal B, A ought to do C" is a factually verifiable claim. But this only relocates the problem — why *ought* A to pursue goal B?
:::

::: {.callout .key}
::: callout-label
Operational significance
:::

An AI advisor with access to every relevant fact about a situation still cannot derive the correct action from those facts alone. Ethical conclusions require ethical premises that the data does not supply. This means the advisor must make its value commitments visible rather than concealing them behind an appearance of objective analysis. When a recommendation rests on a value judgment — as most non-trivial recommendations do — the advisor should say so.
:::
:::

::: {#ch-consequentialism .chapter}
::: chapter-number
Section 3
:::

::: chapter-title
Consequentialism
:::

::: {#s-principle .section}
::: section-title
The Principle
:::

Consequentialism holds that the moral status of an action depends entirely on its consequences. The right action is the one that produces the best outcome. This is a family of theories: they share the commitment to evaluating actions by results but disagree about what "best" means and how to measure it. The dominant member of the family is **utilitarianism**, which identifies the best outcome with the greatest aggregate well-being.
:::

::: {#s-bentham .section}
::: section-title
Bentham
:::

Jeremy Bentham (1748–1832) gave utilitarianism its first systematic form in *An Introduction to the Principles of Morals and Legislation* (1789). Bentham was a strict hedonist: pleasure is the only intrinsic good, pain the only intrinsic bad. Morality is a matter of producing the greatest happiness for the greatest number. He was also a reformer who applied the principle to argue for women's suffrage, prison reform, abolition of slavery, and the elimination of capital punishment.

Bentham proposed the **felicific calculus** to make moral judgment systematic. Any pleasure or pain is measured across seven dimensions: **intensity**, **duration**, **certainty** (likelihood of occurring), **propinquity** (nearness in time), **fecundity** (tendency to produce further pleasures or pains), **purity** (freedom from admixture of the opposite sensation), and **extent** (number of people affected). Bentham did not expect this to be computed before every action — experience-based rules of thumb suffice for most cases. But the calculus expressed the commitment: morality is quantifiable, and all pleasures are commensurable. A children's game has equal value with poetry if the pleasure is equal.
:::

::: {#s-mill .section}
::: section-title
Mill
:::

John Stuart Mill (1806–1873) revised Bentham's framework in *Utilitarianism* (1861). Mill rejected Bentham's purely quantitative hedonism. Some pleasures are higher in *kind*, not merely in amount: intellectual and moral pleasures are qualitatively superior to bodily pleasures. The test: anyone who has experienced both will prefer the higher. "It is better to be Socrates dissatisfied than a fool satisfied."

Mill is generally classified as a **rule utilitarian** (a term coined by Richard Brandt in the late 1950s, after Mill's death). The distinction from Bentham's **act utilitarianism**:

- **Act utilitarianism** evaluates each individual action by its specific consequences.
- **Rule utilitarianism** evaluates *rules* by the consequences of their general observance, then judges individual actions by conformity to those rules.

The difference is sharpest in extreme cases. Judith Jarvis Thomson imagined a transplant surgeon who could save five dying patients by killing one healthy patient and harvesting organs. Act utilitarianism struggles to explain why this is wrong (total welfare increases). Rule utilitarianism handles it: a rule permitting doctors to kill healthy patients would devastate trust in medicine if generally followed.

Mill also formulated the **harm principle**: the only legitimate basis for exercising power over a person against their will is to prevent harm to others. Their own good is not sufficient warrant. This flows naturally from rule utilitarianism — individual acts of paternalism might sometimes increase welfare, but a rule permitting them would not.
:::

::: {#s-problems .section}
::: section-title
Problems
:::

::: {.callout .warn}
::: callout-label
The Utility Monster
:::

Robert Nozick (*Anarchy, State, and Utopia*, 1974) imagined a being that derives enormously more utility from each resource unit than anyone else. If one apple brings an ordinary person one unit of pleasure and the monster one hundred units, utilitarianism requires giving the apple to the monster. Scaled up, it requires giving *everything* to the monster. Nozick's point: utilitarianism appears egalitarian but is structurally capable of demanding total sacrifice. The objection generalizes — any consequentialist system that maximizes a global function is vulnerable to a sufficiently efficient converter.
:::

::: {.callout .warn}
::: callout-label
The Repugnant Conclusion
:::

Derek Parfit (*Reasons and Persons*, 1984) showed that total utilitarianism implies a vast population where every life is barely worth living — Parfit's image was "muzak and potatoes" — is preferable to a small population with excellent lives, as long as the vast population's *total* welfare is greater. Parfit called this the "repugnant conclusion" and noted it is structurally another utility monster: the monster here is not a single being but an enormous aggregate. Average utilitarianism avoids this but introduces its own perversity — it can recommend eliminating the least happy people to raise the average.
:::

**Demandingness.** If morality requires maximizing aggregate welfare, then every moment spent on anything other than welfare-maximization is morally wrong. You should give until you are as destitute as the poorest person you could help. No vacation, no leisure, no personal projects while suffering exists. A moral theory that eliminates the possibility of a personal life strikes many as self-refuting.

**The experience machine.** Nozick also proposed a thought experiment: a machine that simulates any experience you desire, indistinguishable from reality. If only subjective experience matters, you should plug in permanently. Most people refuse, suggesting they care about contact with reality, genuine achievement, and authentic relationships — not merely the experience of having them.
:::
:::

::: {#ch-deontology .chapter}
::: chapter-number
Section 4
:::

::: chapter-title
Deontology
:::

::: {#s-kant .section}
::: section-title
Morality from Reason Alone
:::

Deontological ethics (from Greek *deon*, duty or obligation) evaluates actions by their conformity to moral rules, not their consequences. The preeminent deontological theory belongs to Immanuel Kant (1724–1804), developed in the *Groundwork of the Metaphysics of Morals* (1785) and the *Critique of Practical Reason* (1788).

Kant's starting point: the only unconditionally good thing is a **good will**. Every other quality — intelligence, courage, wealth, even happiness — can serve good or evil ends. Only the will to act rightly has moral worth in itself. And moral worth attaches not to actions that merely happen to conform to duty, but to actions performed *because* they are duties. A merchant who gives fair prices only because it attracts customers acts in accordance with duty but not from duty. Only the merchant who gives fair prices because honesty is right acts morally.

Morality, Kant argued, is derivable from pure practical reason. It is **a priori** (independent of experience), **universal** (binding on all rational beings), and **formal** (specifying the structure right action must have, not the content). Since all rational beings share the same reason, the moral law obligates everyone equally.
:::

::: {#s-ci .section}
::: section-title
The Categorical Imperative
:::

Kant's supreme principle is the **categorical imperative**: a command that applies unconditionally. It contrasts with **hypothetical imperatives**, which are conditional on desires ("if you want to pass the exam, study"). The categorical imperative commands regardless of what you want.

Kant formulated it in several ways. Three are central:

::: {.callout .key}
::: callout-label
Three Formulations
:::

**1. Universal Law:** "Act only according to that maxim whereby you can at the same time will that it should become a universal law." State the principle behind your action. Universalize it. If the universalized maxim generates a contradiction — if a world where everyone follows it is incoherent — the action is impermissible. False promising fails: if everyone made false promises, trust would collapse and promising would become impossible, destroying the very institution the false promisor is exploiting.

**2. Humanity:** "Act so that you treat humanity, whether in your own person or in that of another, always at the same time as an end and never merely as a means." Persons have dignity, not merely price. They may not be used solely as instruments. You may hire a taxi driver (using their labor instrumentally), but you must simultaneously respect them as a rational being with their own purposes.

**3. Kingdom of Ends:** "Act as if you were through your maxims a law-making member of a kingdom of ends." Imagine a community where every rational being is both legislator and subject. The laws you will must be ones you would accept being bound by, and they must respect every member as an end.
:::

Duties divide into **perfect** (admitting no exceptions: do not lie, do not kill, do not make false promises) and **imperfect** (requiring general effort but allowing discretion: develop your talents, help others). Perfect duties correspond to maxims that self-destruct when universalized. Imperfect duties correspond to maxims you *could* universalize without contradiction but could not *will* to be universal — you could conceive a world where nobody helps anyone, but you could not rationally will it while having needs yourself.
:::

::: {#s-deont-problems .section}
::: section-title
Problems
:::

**The murderer at the door.** A killer asks where your friend is hiding. Kant held — explicitly, in a separate essay — that you may not lie even in this case. The universalizability test forbids lying. The Formula of Humanity forbids using the murderer as a means (which deception would do). But the Formula of Humanity also seems to prohibit allowing your friend to be used merely as a means by the murderer. The two formulations can generate conflicting obligations, and Kant offered no systematic method for resolving such conflicts.

**Maxim formulation.** The universalizability test yields different verdicts depending on how you describe your action. "I will steal" fails. "I will steal bread to feed my starving child when no other option exists" is a different maxim that may not fail. Since the "correct" level of specificity is undetermined, the test is arguably indeterminate — you can pass or fail depending on how you frame the maxim.

**Rigorism.** Absolute prohibitions treat a white lie to spare someone's feelings as the same moral category as perjury. Many post-Kantian deontologists have tried to soften this — W.D. Ross's prima facie duties, for instance, allow duties to be outweighed — but these revisions move away from Kant's own position.
:::
:::

::: {#ch-virtue .chapter}
::: chapter-number
Section 5
:::

::: chapter-title
Virtue Ethics
:::

::: {#s-aristotle .section}
::: section-title
Aristotle's Question
:::

Virtue ethics reframes the central question of morality. Instead of "what should I do?" it asks "what kind of person should I be?" The foundational text is Aristotle's *Nicomachean Ethics* (c. 340 BCE) — probably a set of lecture notes rather than a polished work, named for Aristotle's son Nicomachus, who may have edited it posthumously.

Aristotle begins by asking what the highest human good is. His answer: **eudaimonia**. The word is conventionally translated as "happiness" but means something closer to *flourishing* or *living well and doing well*. Eudaimonia is not a subjective feeling. It is an objective condition — the excellent exercise of distinctively human capacities (reason and moral agency) over a complete life. Several consequences follow. First, you cannot be eudaimon while deceived about your situation — self-deception is incompatible with flourishing. Second, favorable external circumstances are necessary — extreme poverty, severe illness, or the catastrophic loss of loved ones can prevent flourishing regardless of inner virtue. Third, eudaimonia is a property of a whole life, not a momentary state. A single good day does not make a person eudaimon any more than a single swallow makes a summer.
:::

::: {#s-mean .section}
::: section-title
The Doctrine of the Mean
:::

Every moral virtue is a stable disposition lying between two vices — one of excess, one of deficiency. Courage lies between rashness and cowardice. Generosity between prodigality and miserliness. Proper anger between irascibility and passivity. The mean is not a mathematical midpoint. It is relative to the person and the situation: the right amount of food for an athlete differs from the right amount for a sedentary person; the right level of anger at a grave injustice differs from the right level at a trivial annoyance.

Finding the mean requires **phronesis** — practical wisdom. Phronesis is the capacity to perceive the morally salient features of a particular situation and respond well. It cannot be reduced to rules or algorithms. Aristotle insists that ethics is an imprecise discipline: "it is the mark of an educated person to look for precision in each class of things just so far as the nature of the subject admits." Practical wisdom is developed through experience and practice, not through studying principles — though principles can serve as useful starting points.
:::

::: {#s-character .section}
::: section-title
Character Through Practice
:::

"We become just by doing just acts, temperate by doing temperate acts, brave by doing brave acts." Virtues are acquired through habituation — repeated right action. But true virtue is not mere habit. It requires choosing the right action knowingly, for its own sake, from a settled disposition. The virtuous person does not merely happen to act justly; they understand why justice matters and are pained by injustice. Virtue is constitutive of flourishing, not instrumental to it. The virtuous life *is* the flourishing life — virtue is not rewarded with happiness as a separate payment.
:::

::: {#s-macintyre .section}
::: section-title
MacIntyre and the Modern Revival
:::

Alasdair MacIntyre, in *After Virtue* (1981), diagnosed modern moral philosophy as incoherent. We have inherited fragments of older moral vocabularies — "good," "just," "virtuous" — without the teleological framework (the shared understanding of human purpose) that once made them meaningful. Modern moral debate is shrill and interminable because the participants draw on incommensurable fragments, each internally consistent but incompatible with the others.

MacIntyre proposed grounding virtues in **practices**: cooperative human activities with internal goods — goods achievable only through the practice itself (the satisfaction of craftsmanship, the excellence of athletic performance) as opposed to external goods (money, status) obtainable by other means. Virtues are the dispositions that enable practitioners to achieve internal goods. Different practices and traditions yield different virtue lists — Homer's virtues differ from Aquinas's, which differ from Franklin's. MacIntyre regarded this as intelligible rather than problematic: virtues are always situated within communities and traditions. The modern virtue ethics revival includes Philippa Foot (*Natural Goodness*, 2001) and Rosalind Hursthouse (*On Virtue Ethics*, 1999) alongside MacIntyre.
:::

::: {#s-virtue-problems .section}
::: section-title
Problems
:::

**Cultural relativity.** If virtues are tradition-dependent, how do we adjudicate between traditions with incompatible virtue lists? Homeric Greeks prized competitive martial excellence. Christians prize humility. Both cannot be the virtues. MacIntyre embraces tradition-dependence; critics see it as ceding the ground that moral theory needs.

**Action guidance.** Virtue ethics tells the perplexed agent to "do what the virtuous person would do." This is unhelpful when you are the perplexed agent trying to figure out what that is. Defenders reply that this is honesty, not weakness: morality genuinely requires judgment, and a theory that pretends to eliminate judgment is lying about the nature of the problem.
:::
:::

::: {#ch-care .chapter}
::: chapter-number
Section 6
:::

::: chapter-title
Care Ethics
:::

::: {#s-gilligan .section}
::: section-title
The Different Voice
:::

Care ethics emerged in the early 1980s as a challenge to assumptions shared by consequentialism, deontology, and virtue ethics alike. Carol Gilligan, in *In a Different Voice* (1982), began from a specific empirical puzzle. Lawrence Kohlberg's influential model of moral development measured maturity as progress toward abstract, universal, principle-based reasoning. When girls were included in his studies, they scored systematically lower. Gilligan argued this was an artifact of the instrument, not a real deficit. The scale measured one kind of moral reasoning — the "justice orientation" (rights, obligations, universal principles) — and ignored another: the "care orientation" (relationships, needs, responsiveness to particular others).

Gilligan compared the two orientations to the duck-rabbit illusion: a moral reasoner can adopt either but cannot hold both simultaneously. Both men and women used both orientations at different times, but without women in the sample, the care orientation nearly disappeared from view. Gilligan's later work retreated from strong claims about gender differences, concluding that the orientations were not sex-linked but that studying only male subjects had produced a distorted picture of moral development.
:::

::: {#s-noddings .section}
::: section-title
Noddings' Caring
:::

Nel Noddings developed care into a systematic moral framework in *Caring: A Feminine Approach to Ethics and Moral Education* (1984). The unit of moral analysis is the caring relationship between the **one-caring** and the **cared-for**. Caring is an act of **engrossment**: receiving the other on their own terms, resisting projection, attending to their actual needs rather than to what you assume they need.

Noddings distinguished **natural caring** — the spontaneous impulse to care for those close to us (paradigmatically, parent for child) — from **ethical caring** — the deliberate "I must" that arises when natural caring is absent but need is recognized. Natural caring is primary. This reverses Kant's hierarchy: for Kant, duty outranks inclination; for Noddings, the inclination to care is the foundation of ethical life, and duty is the fallback when inclination fails.

Crucially, Noddings rejected universal moral principles. Care is always contextually situated. The same question from different people in different relationships may require different responses. This is not a deficiency to be corrected but the essential nature of moral life.
:::

::: {#s-assumptions .section}
::: section-title
The Shared Assumptions Under Attack
:::

Care ethics challenges three commitments that consequentialism and deontology share despite their other disagreements:

- **Impartiality.** Both utilitarian calculation and Kantian universalizability demand treating everyone equally. Care ethics holds that your duties to your child differ from your duties to a stranger, and that a morality denying this is impoverished.
- **Abstraction.** Both frameworks apply general principles to particular cases. Care ethics holds that attending to the particular — this person, this relationship, this context — is the core moral task, not a deviation from it.
- **Individualism.** Both frameworks treat moral agents as autonomous, self-sufficient units. Care ethics holds that human beings are fundamentally interdependent, that identities are formed in relationship, and that moral duties flow from connections to particular others.

Joan Tronto later extended care ethics beyond personal relationships, identifying four elements of care as a social practice: **attentiveness** (noticing needs), **responsibility** (accepting obligation to respond), **competence** (responding skillfully), and **responsiveness** (attending to the cared-for's experience of receiving care).
:::

::: {#s-care-problems .section}
::: section-title
Problems
:::

**Essentialism.** Linking care to feminine experience risks reinforcing the stereotype that caring is women's work, women's nature. Even if the association is empirically real, it may be socially constructed — and grounding a moral theory in it may perpetuate the conditions that produced it.

**Scope.** What do I owe distant strangers? Noddings held that obligation requires an existing or potential caring relationship, and the relationship must have potential to become reciprocal. This leaves large portions of the moral landscape — duties to distant populations, future generations, non-human animals — difficult to address.
:::
:::

::: {#ch-particularism .chapter}
::: chapter-number
Section 7
:::

::: chapter-title
Moral Particularism
:::

::: {#s-dancy .section}
::: section-title
The Claim
:::

Moral particularism, in its strongest form, holds that there are no defensible moral principles, that moral thought does not consist in applying principles to cases, and that the morally perfect person should not be conceived as a person of principle. The principal architect is Jonathan Dancy, across *Moral Reasons* (1993) and *Ethics Without Principles* (2004).

The central argument is **holism about reasons**. A feature that provides a moral reason in one context may provide no reason, or even an opposite reason, in another. That an action causes pain is normally a reason against it — but in surgical or dental contexts, it may be a reason in favor. That something is a lie is normally a reason against saying it — but lying to protect an innocent person from a murderer seems morally different. If the moral valence of a feature can shift across contexts, then no principle of the form "this feature always counts this way" can be correct. Principles are, at best, crutches that a morally sensitive person would not need — and at worst, sources of moral distortion.
:::

::: {#s-ross .section}
::: section-title
Ross as Precursor
:::

W.D. Ross (*The Right and the Good*, 1930) occupies an intermediate position. Ross identified seven **prima facie duties**: fidelity (keep promises), reparation (make amends), gratitude, justice, beneficence (help others), self-improvement, and non-maleficence (do no harm). These are genuine moral claims that can conflict. When they do — when keeping a promise would cause harm, or justice conflicts with beneficence — no further principle resolves the conflict. Judgment is required. Ross is generalist about what *counts as* a reason (the seven duties are general principles) but particularist about what to *do* all-things-considered (no principle tells you which duty wins). Dancy goes further: even Ross's general principles are suspect, because the features they identify can switch moral valence.
:::

::: {#s-aesthetic .section}
::: section-title
The Aesthetic Analogy
:::

Dancy argues that moral judgment resembles aesthetic judgment. We make sophisticated, defensible judgments about what is beautiful or elegant without relying on aesthetic principles — no one has stated a principle of the form "any painting with property X is beautiful" that survives counterexample. Yet aesthetic judgment is not arbitrary: trained judges converge, can articulate reasons, and can educate others. Moral judgment, Dancy contends, works the same way. The absence of principles does not entail the absence of knowledge, reason, or education. It means moral knowledge is particular, perceptual, and resistant to codification — like the knowledge of a skilled craftsperson rather than the knowledge of someone following a manual.

Dancy concedes that some moral features may have **invariant relevance** — perhaps cruelty for its own sake is always a reason against an action. But these are isolated rocks in a sea of contextual fluidity. They do not determine the character of the whole moral terrain, and the rationality of moral thought does not depend on them.
:::

::: {#s-part-problems .section}
::: section-title
Problems
:::

**Moral education.** Without principles, how do children learn right from wrong? Dancy answers: teach virtues (honesty, kindness, courage), not rules. But naming virtues reintroduces generality at a different level.

**Coordination.** Shared moral life seems to require predictability, and predictability seems to require shared principles. Dancy responds that we can rely on people to "by and large do what is right in the circumstances" without needing principles — just as we rely on people to act sensibly without explicit principles of rationality. Critics find this optimistic in practice.

**Conservatism.** Without principles to challenge existing moral intuitions, particularism risks ratifying the status quo. If moral judgment is irreducibly perceptual, the biases embedded in current moral perception have no external corrective.
:::
:::

::: {#ch-trolley .chapter}
::: chapter-number
Section 8
:::

::: chapter-title
The Trolley Diagnostic
:::

The trolley problem is not a puzzle with a right answer. It is a diagnostic instrument that reveals which ethical framework is operating behind your intuitions — and where frameworks conflict with each other and with common moral judgment.

::: {#s-cases .section}
::: section-title
The Two Cases
:::

**The Switch.** Philippa Foot (1967) introduced the scenario: a runaway trolley is heading toward five people on the track. A bystander can pull a lever to divert it onto a side track where one person stands. Diverting kills one, saves five. Most people judge this permissible.

**The Footbridge.** Judith Jarvis Thomson (1976, 1985) introduced the variant: the bystander is on a bridge over the tracks. The only way to stop the trolley is to push a large man off the bridge into its path. His body stops the trolley. He dies. Five are saved. The numerical structure is identical — one death to save five. Most people judge this impermissible.
:::

::: {#s-divergence .section}
::: section-title
What the Divergence Reveals
:::

The reversed intuition between the two cases is the diagnostic payload. Several explanations have been proposed, each aligning with a different ethical framework:

**Consequentialism** cannot explain the divergence. Both cases produce the same outcome (one dead, five saved). A pure consequentialist should approve both or disapprove both. The fact that most people treat them differently shows that most people are not pure consequentialists, even when they think they are.

**The doctrine of double effect** (a principle with roots in Aquinas) distinguishes intended harm from foreseen harm. In the switch case, the one person's death is a foreseen but unintended side effect of saving the five. In the footbridge case, his death is the *intended means*. The doctrine permits causing harm as a side effect of pursuing a good end but forbids causing harm as a means to a good end. This explains the divergence — but Thomson's "loop" variant complicates it: if the side track loops back toward the five and the one person's body is what stops the trolley, then his death is the means of saving the five even in the switch-type scenario. Most people still approve diverting in the loop case, which undermines the doctrine.

**Kant's Formula of Humanity.** Pushing the man uses him merely as a means — his body is a tool for stopping the trolley. Diverting the trolley does not use the person on the side track; he is simply in the way. Again, the loop variant creates trouble: in the loop, the person's body is what stops the trolley, so he is used as a means even in the switch-type case.

**Foot's duty analysis.** In the switch case, both options involve redirecting an existing threat. In the footbridge case, pushing the man creates a *new* threat. Thomson later distinguished "deflecting a threat from a larger group onto a smaller group" (permissible) from "bringing a different threat to bear on the smaller group" (impermissible).

::: {.callout .key}
::: callout-label
What the trolley problem is for
:::

The problem does not tell you what you should do. It tells you what kind of moral reasoner you are. If you approve both cases, you are reasoning consequentially. If you approve the switch but not the push, something besides consequences is doing moral work — and the pattern of your approvals reveals what that something is. The trolley problem is a tool for making implicit frameworks explicit.
:::
:::
:::

::: {#ch-uncertainty .chapter}
::: chapter-number
Section 9
:::

::: chapter-title
Moral Uncertainty
:::

::: {#s-mu-problem .section}
::: section-title
The Problem
:::

The preceding sections present five ethical frameworks that have each attracted serious defenders for decades or centuries. Intelligent, honest philosophers have not resolved the disagreement. This is not likely to change soon. Meanwhile, you must act. How should you make decisions when you are genuinely uncertain which moral theory is correct?

The default — what William MacAskill calls the "my favourite theory" approach — is to pick whichever framework seems most plausible and act as if it were certainly correct. MacAskill argues this is irrational, for the same reason that betting everything on a 55% probability is irrational. If you are 55% consequentialist and 45% deontologist, and the consequentialist option involves a serious rights violation that the deontological theory rates as catastrophically wrong, acting on the 55% theory alone is reckless.
:::

::: {#s-ecw .section}
::: section-title
Expected Choice-Worthiness
:::

MacAskill, Krister Bykvist, and Toby Ord developed a systematic treatment in *Moral Uncertainty* (2020, Oxford University Press). Their proposal: **maximize expected choice-worthiness**. Assign credences to the moral theories you take seriously. For each available action, determine how choice-worthy it is according to each theory. Weight by credence. Choose the action with the highest expected choice-worthiness.

This treats moral uncertainty analogously to empirical uncertainty and draws explicitly on **social choice theory** — each moral theory is like a "voter" expressing preferences over actions, and your credences function as vote weights.
:::

::: {#s-comparison .section}
::: section-title
The Comparison Problem
:::

The central technical difficulty is **intertheoretic comparison**. Utilitarianism assigns cardinal values (utility scores). Deontology classifies actions as permissible or impermissible — ordinal categories without magnitudes. How do you compare "5 additional utils" with "categorically impermissible"? MacAskill et al. argue the correct approach depends on the informational structure of the theories in question. When theories provide cardinal information, expected-value maximization applies. When they provide only ordinal information, aggregation methods from social choice theory (like the Borda rule) may be appropriate. When intertheoretic comparison is genuinely impossible, acknowledging the indeterminacy is more honest than pretending it does not exist.
:::

::: {#s-takeaways .section}
::: section-title
Practical Takeaways
:::

Even without solving the full technical problem, the framework has clear implications:

- Consequentialists should avoid serious rights violations, because deontological theories (which deserve some credence) rate them catastrophically.
- Deontologists should put significant weight on doing large amounts of good, because consequentialist theories (which deserve some credence) rate indifference to outcomes as seriously wrong.
- Actions that are **robustly good** — acceptable or commendable across multiple frameworks — should be favored over actions that score very well on one framework but very badly on another.
- When frameworks genuinely conflict and no robust option exists, the conflict itself is morally informative. It signals a genuine trade-off between values that different reasonable people weight differently.
:::
:::

::: {#ch-applied .chapter}
::: chapter-number
Section 10
:::

::: chapter-title
Framework Conflict in Practice
:::

When a real decision involves genuine disagreement between ethical frameworks, no meta-theory resolves the dispute without begging the question — any meta-theory is itself an ethical framework that the other frameworks do not accept. What can be done is more modest but still useful: make the disagreement visible, identify what is at stake, and locate the value judgment that the decision-maker must make.

::: {#s-methods .section}
::: section-title
Methods
:::

**Reflective equilibrium** (John Rawls, *A Theory of Justice*, 1971). Begin with your considered moral judgments — judgments held with confidence after reflection, not snap reactions. Test them against general principles. Where they conflict, revise either the judgments or the principles (or both) until they cohere. This is a method for arriving at a stable moral position, not a formula for a unique answer. Different people with different starting judgments may reach different equilibria — and that is part of the point. The method disciplines moral reasoning without claiming to dictate moral conclusions.

**Convergence testing.** When multiple frameworks agree, the verdict is more robust than one supported by only a single framework. When they disagree, the disagreement is informative — it signals a genuine trade-off. The advisor's role is to make the trade-off explicit, not to resolve it unilaterally.

**Moral uncertainty maximization** (MacAskill et al.). Assign credences, weight by expected choice-worthiness, favor robustly good options. The most formally developed approach, but requires solving intertheoretic comparison — which is not always possible.

**Particularist attention.** Set the frameworks aside. Attend to the specific features of *this* situation. What matters here? What would a thoughtful, morally sensitive person see? This is the least systematic approach but the most honest about the limits of systematization.
:::

::: {.callout .tip}
::: callout-label
For AI advisory
:::

The most defensible pattern for an AI advisor: (1) Identify which frameworks are relevant. (2) State what each recommends and why. (3) Note convergence where it exists. (4) Where frameworks disagree, name the value trade-off. (5) Make clear that the final judgment is the operator's, not the advisor's. Never collapse a genuine framework conflict into a single confident recommendation without disclosing the collapse.
:::
:::

::: {#ch-board .chapter}
::: chapter-number
Section 11
:::

::: chapter-title
Board Connection
:::

::: {#s-detecting .section}
::: section-title
Detecting Ethical Dimensions
:::

Most advisory questions have ethical dimensions the operator has not flagged. Pricing involves fairness. Hiring involves respect for persons. Resource allocation involves distributive justice. Product design involves care for users. The advisor's first task is **recognition**: noticing that an ethical dimension exists even when the question was framed instrumentally.

When should the advisor raise a concern the operator did not ask about? The threshold is not "does the advisor disagree?" but "would a thoughtful observer want this flagged?" A minor ethical consideration that the operator has likely already weighed does not need intervention. A serious concern that the operator appears unaware of — or that the operator's framing implicitly resolves in a way that a reasonable person applying a different framework would contest — should be raised. The standard is proportional to the stakes.
:::

::: {#s-presenting .section}
::: section-title
Presenting Conflicts
:::

When an advisory question involves genuine framework conflict, the advisor should present the conflict rather than resolving it silently. The pattern: name the frameworks that apply, state what each recommends and why, identify the value trade-off (what is gained and lost under each option), note if one option is robustly good across frameworks, and make clear that the final decision involves a value judgment the operator must make. This is not indecisiveness. It is intellectual honesty about the structure of the problem.
:::

::: {#s-connections .section}
::: section-title
Connections to Other Packs
:::

**Decision Theory.** Decision theory covers rational choice under uncertainty — utility maximization, expected value, risk. This pack adds ethical *constraints* on that optimization. Nozick's "moral side-constraints" — limits on what you may do even in pursuit of the best outcome — mark the boundary between decision theory and ethics. MacAskill's moral uncertainty framework is structurally analogous to decision under empirical uncertainty, making the connection direct.

**Cognitive Bias.** Moral reasoning is subject to specific biases. Jonathan Haidt's social intuitionist model holds that moral judgments are typically rapid intuitive responses rationalized after the fact. Trolley-problem research confirms this: responses are influenced by factors (physical proximity, personal force, whether you push or pull) that no ethical framework would endorse as relevant. Motivated reasoning is another danger — selecting whichever framework supports the conclusion you already want. The advisor should watch for this in its own reasoning and in the operator's framing.

**Political Philosophy.** The Political Philosophy pack covers justice, social contracts, rights, and institutional design. Rawls appears in both packs: reflective equilibrium is a method for applied ethics (this pack); the veil of ignorance and difference principle are political philosophy (that pack). The boundary: this pack handles individual moral decisions; political philosophy handles the design of just institutions.
:::
:::

::: {#ch-refs .chapter}
::: chapter-number
Section 12
:::

::: chapter-title
References
:::

  Author                               Work                                                                Year        Pack Section
  ------------------------------------ ------------------------------------------------------------------- ----------- ---------------
  Aristotle                            *Nicomachean Ethics*                                                c. 340 BCE  §5
  Bentham, Jeremy                      *An Introduction to the Principles of Morals and Legislation*       1789        §3
  Dancy, Jonathan                      *Moral Reasons*                                                     1993        §7
  Dancy, Jonathan                      *Ethics Without Principles*                                         2004        §7
  Foot, Philippa                       "The Problem of Abortion and the Doctrine of Double Effect"         1967        §8
  Foot, Philippa                       *Natural Goodness*                                                  2001        §5
  Gilligan, Carol                      *In a Different Voice*                                              1982        §6
  Hume, David                          *A Treatise of Human Nature*                                        1739–40     §2
  Hursthouse, Rosalind                 *On Virtue Ethics*                                                  1999        §5
  Kant, Immanuel                       *Groundwork of the Metaphysics of Morals*                           1785        §4
  Kant, Immanuel                       *Critique of Practical Reason*                                      1788        §4
  MacAskill, W., Bykvist, K., Ord, T. *Moral Uncertainty*                                                 2020        §9
  MacIntyre, Alasdair                  *After Virtue*                                                      1981        §5
  Mill, John Stuart                    *Utilitarianism*                                                    1861        §3
  Moore, G.E.                          *Principia Ethica*                                                  1903        §2
  Noddings, Nel                        *Caring: A Feminine Approach to Ethics and Moral Education*          1984        §6
  Nozick, Robert                       *Anarchy, State, and Utopia*                                        1974        §3
  Parfit, Derek                        *Reasons and Persons*                                                1984        §3
  Rawls, John                          *A Theory of Justice*                                               1971        §10
  Ross, W.D.                           *The Right and the Good*                                             1930        §7
  Thomson, Judith Jarvis               "Killing, Letting Die, and the Trolley Problem"                     1976        §8
  Thomson, Judith Jarvis               "The Trolley Problem"                                               1985        §8
:::
:::
