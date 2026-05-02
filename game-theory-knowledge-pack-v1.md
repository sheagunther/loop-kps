# Game Theory — Strategy, Incentives, and Equilibrium

**Loop MMT™ · Multi-Module Theory · Knowledge Pack**
**v1 · 11 April 2026**

---

## About This Document

Decision theory asks what a rational agent should do when outcomes are uncertain. Game theory asks what a rational agent should do when the uncertainty *is another rational agent*. The shift from passive risk to strategic interdependence — from weather to opponents — is the founding move of game theory, and it changes the mathematics, the solution concepts, and the nature of the answers.

This pack covers the field from its foundations through its major extensions: how games are represented, what equilibrium means, why cooperation fails and how it recovers, what happens when players have private information, how to design rules that produce desired outcomes, how evolution replaces rationality, how coalitions divide surplus, and how coordination emerges without communication.

The operational purpose: an AI advisor encounters strategic situations constantly — pricing against competitors, negotiating on behalf of stakeholders, designing incentive structures, evaluating whether a recommendation accounts for how others will respond. This pack provides the formal vocabulary and the core results.

Companion packs: **Decision Theory** (the single-agent foundation this pack extends), **Multi-Objective Optimization / Pareto Theory** (tradeoff analysis without strategic interaction), **Probability & Statistics** (the mathematical substrate). Cross-references: forthcoming **Evolutionary Biology** KP (biological applications), forthcoming **Pricing** KP (mechanism design applied to product pricing).

---

## Section 1 · Representing Games

### The Three Ingredients

Every formal game has three components: **players** (the decision-makers), **strategies** (what each player can do), and **payoffs** (what each player gets for each combination of strategies). The defining feature is interdependence — your best action depends on others' actions, and theirs on yours. This circularity is what distinguishes games from optimization problems and makes the field both harder and more interesting.

### Normal Form

The **normal form** (or strategic form) represents a game as a matrix (for two players) or a multidimensional payoff array. Players choose simultaneously; the matrix entry at each strategy combination specifies each player's payoff. Formally: a game Γ = (N, {Sᵢ}, {uᵢ}), where N is the player set, Sᵢ is player i's strategy set, and uᵢ: S₁ × ... × Sₙ → ℝ is player i's payoff function.

Normal form is compact and makes equilibrium computation tractable. Its limitation: it erases sequence and information flow. A game where Player 1 moves first and Player 2 observes that move looks identical in normal form to a game where they move simultaneously — yet the strategic implications differ profoundly.

### Extensive Form

The **extensive form** represents a game as a decision tree. Nodes represent decision points, branches represent available actions, and terminal nodes carry payoffs. The tree encodes *who moves when* and *what they know*. **Information sets** — groups of nodes a player cannot distinguish — capture situations where a player must decide without knowing what happened previously.

Any extensive-form game can be reduced to normal form by enumerating complete contingent plans (strategies that specify an action at every information set). But the conversion loses structure that matters: subgame perfection, credible threats, and sequential rationality all depend on the tree, not the matrix.

**When to use which:** Normal form for simultaneous games and initial equilibrium analysis. Extensive form when timing matters — sequential decisions, observable actions, credibility of threats, or refinements beyond Nash.

---

## Section 2 · Dominance and Nash Equilibrium

### Eliminating Bad Strategies

A strategy is **strictly dominated** if some alternative is always better regardless of what opponents do. Rational players never play strictly dominated strategies, because there's always something better available. **Iterated elimination of strictly dominated strategies (IESDS)** removes them, simplifies the game, and repeats. When strict dominance is used, the order of elimination doesn't matter — the result is the same regardless. For *weak* dominance (at least as good everywhere, strictly better somewhere), order can matter — a significant and often overlooked asymmetry.

A **strictly dominant strategy** is one that beats all alternatives regardless of opponents' behavior. Having one means you don't need to think about opponents at all. Dominant strategies are powerful and rare.

### Nash Equilibrium

A strategy profile — one strategy per player — is a **Nash equilibrium (NE)** if no player can improve their payoff by unilaterally changing strategy. Formally: s* is a NE if for every player i and every alternative sᵢ, uᵢ(sᵢ*, s₋ᵢ*) ≥ uᵢ(sᵢ, s₋ᵢ*).

John Nash (1950) proved that every finite game has at least one Nash equilibrium, possibly in mixed strategies. The 1950 PNAS paper used Kakutani's fixed-point theorem (Nash credited David Gale with suggesting the approach). The 1951 *Annals of Mathematics* paper gave an alternative proof using Brouwer's fixed-point theorem.

**What NE captures:** Mutual consistency. At equilibrium, no player has a reason to deviate given what others are doing. It is the only strategy profile that can be *common knowledge* without being self-undermining — if everyone knows everyone's strategy, nobody wants to change.

**What NE does not capture:** How players get to equilibrium. Whether the equilibrium is unique (many games have multiple NE). Whether the equilibrium is efficient (it often isn't — the Prisoner's Dilemma is the canonical example). Whether threats embedded in the equilibrium are credible (motivating subgame perfection and further refinements).

### The Refinement Hierarchy

Multiple equilibria and implausible threats motivated increasingly demanding solution concepts:

| Concept | Added Requirement | Source |
|---|---|---|
| Nash Equilibrium | No unilateral profitable deviation | Nash (1950) |
| Subgame Perfect Equilibrium | NE in every subgame | Selten (1965) |
| Bayesian Nash Equilibrium | NE given type uncertainty | Harsanyi (1967-68) |
| Perfect Bayesian Equilibrium | Sequential rationality + consistent beliefs | Fudenberg & Tirole |
| Trembling Hand Perfect | Robust to small probability mistakes | Selten (1975) |

Each level eliminates equilibria that depend on behavior no one would actually carry out. The hierarchy reflects a core tension in game theory: stronger concepts are more plausible but harder to compute, and may not exist in all games.

---

## Section 3 · Mixed Strategies and the Minimax Theorem

### Why Randomize

Consider Matching Pennies: two players show heads or tails simultaneously. Player 1 wins if they match, Player 2 wins if they differ. No pure strategy is stable — any predictable choice gets exploited. The only equilibrium: both randomize 50-50.

A **mixed strategy** assigns probabilities to pure strategies. The critical insight: in a mixed-strategy NE, each mixing player must be *indifferent* among the strategies in their mix. If one option yielded higher expected payoff, they'd choose it with certainty. To compute a mixed NE, you find the probabilities that make the *opponent* indifferent — the probabilities that make your own mix optimal are determined by the opponent's problem, not yours.

### von Neumann's Minimax Theorem (1928)

The theorem that launched the field. In every finite two-person zero-sum game, the maximin value equals the minimax value: the most Player 1 can guarantee equals the least Player 2 can hold Player 1 to. This common value V is the *value of the game*. Each player has an optimal (possibly mixed) strategy; neither gains by deviating.

Nash's equilibrium concept generalized this to non-zero-sum games with arbitrary numbers of players — but at the cost of uniqueness. Zero-sum games have a clean, unique solution value. General games have equilibria that may be multiple, inefficient, or hard to select among.

---

## Section 4 · Cooperation and Its Failures

### The Prisoner's Dilemma

Two suspects, interrogated separately, each choose to Cooperate (stay silent) or Defect (confess). The payoff ordering: T > R > P > S, where T is the temptation to defect unilaterally, R is the mutual cooperation reward, P is the mutual defection punishment, and S is the sucker's payoff from cooperating while the other defects.

Defect strictly dominates Cooperate — each player does better confessing regardless of what the other does. The unique NE is (Defect, Defect) with payoffs (P, P). But mutual cooperation (R, R) is Pareto superior: both players would prefer it. This is the dilemma — individual rationality produces collective failure.

The Prisoner's Dilemma is not a proof that selfishness is rational. It is a proof that without appropriate structure, individually rational choices aggregate into collectively irrational outcomes. The dilemma diagnoses the problem; the rest of game theory (repeated games, mechanism design, evolutionary dynamics) addresses solutions.

### Tragedy of the Commons and Public Goods

The multi-player generalization. Each herder gains from adding one more animal to shared pasture, but the overgrazing cost falls on all. Each individual's dominant strategy (add more) produces collective ruin (pasture destruction). The same structure appears in climate change, antibiotic resistance, overfishing, and public goods provision — individual incentives systematically misaligned with collective welfare.

---

## Section 5 · Repeated Games and the Shadow of the Future

### Iteration Transforms Incentives

The Prisoner's Dilemma conclusion — defection is the only rational strategy — holds only for single interactions. When the same players meet repeatedly with no known endpoint, future consequences create leverage. Defecting today risks triggering punishment tomorrow. This *shadow of the future* can sustain cooperation as an equilibrium.

### The Folk Theorem

The **folk theorem** (informally known before formal publication) states: in infinitely repeated games with sufficiently patient players (discount factor δ near 1), any feasible payoff vector giving each player more than their minimax value can be sustained as a Nash equilibrium.

Fudenberg and Maskin (1986) proved the subgame-perfect version: these payoffs can be sustained with *credible* punishment strategies — punishing a defector is itself part of an equilibrium, not an empty threat.

The folk theorem is both a vindication and a curse. It says cooperation is possible — but so is a vast range of other outcomes. It answers "can cooperation be sustained?" (yes) while creating the equilibrium selection problem: "which of the infinitely many equilibria will emerge?"

### Tournament Strategies

Robert Axelrod (1984) ran computer tournaments pitting strategies against each other in the iterated Prisoner's Dilemma. Both rounds were won by **Tit-for-Tat (TFT)** — cooperate first, then mirror the opponent's last move. Submitted by Anatol Rapoport, TFT was the simplest entry and never the first to defect.

Axelrod distilled four properties of successful strategies: **nice** (never defect first), **retaliatory** (punish defection immediately), **forgiving** (restore cooperation after punishment), and **clear** (simple enough for opponents to understand and predict).

TFT has a known weakness: it cannot recover from errors. One accidental defection triggers alternating retaliation. **Win-Stay, Lose-Shift (Pavlov)**, analyzed by Nowak and Sigmund (1993), handles noise better — repeat your action if the payoff was satisfactory, switch if it wasn't. In environments with occasional mistakes, Pavlov outperforms TFT.

A technical note: TFT is a Nash equilibrium for sufficiently patient players, but it is *not* subgame-perfect. It prescribes behavior in some off-path subgames that isn't individually rational. **Grim Trigger** — cooperate until any defection, then defect forever — *is* subgame-perfect for high enough δ, but its all-or-nothing punishment is brittle in practice.

Axelrod's primary contribution was not rediscovering the folk theorem (which was already well known) but focusing attention on *evolutionary equilibrium selection* — which strategies survive and spread in populations, not just which are theoretically stable.

---

## Section 6 · Games of Incomplete Information

### Harsanyi's Bayesian Framework

Classical game theory assumes common knowledge of the game itself — all players, strategies, and payoffs are known to everyone. John Harsanyi (1967-68) extended the framework to handle **private information**: situations where players know their own characteristics (preferences, costs, abilities) but not others'.

The modeling device: **nature** moves first, randomly assigning each player a *type* from a probability distribution (the *common prior*). Each player observes their own type, not others'. A strategy now maps types to actions: "if I'm type X, I do Y."

A **Bayesian Nash equilibrium (BNE)** is a strategy profile where each player's type-contingent strategy maximizes expected payoff, given beliefs about others' types and the expectation that others play their equilibrium strategies. Nash's existence theorem extends: BNE exist under the same conditions as standard NE.

The practical import is enormous. Auctions, bargaining, market competition, regulation — nearly every economic interaction involves some private information. Harsanyi's framework makes these tractable while preserving the strategic core.

---

## Section 7 · Signaling and Communication

### Costly Signals

Michael Spence (1973) introduced the canonical signaling model. Workers differ in ability (their private type). Education is costly but doesn't increase productivity — it serves only as a signal. The key mechanism: education costs less for high-ability workers (who learn faster). This *differential cost* enables credible separation.

### Three Types of Equilibrium

**Separating equilibrium:** Different types send different signals. The receiver infers type with certainty. In Spence's model: high-ability workers get degrees, low-ability workers don't, employers correctly decode the signal.

**Pooling equilibrium:** All types send the same signal. The receiver learns nothing new and relies on prior beliefs. Everyone gets a degree (or nobody does), and wages reflect population averages.

**Semi-separating (hybrid) equilibrium:** Partial information revelation. Some types are distinguishable, others pool. These equilibria are theoretically important but empirically underexplored.

Signaling games typically have multiple equilibria. Refinements like the **intuitive criterion** (Cho and Kreps, 1987) narrow the set, often selecting the least-cost separating equilibrium (the Riley equilibrium) — the separating outcome where each type signals just enough to distinguish itself.

### Cheap Talk

When signals are costless, the analysis shifts fundamentally. Crawford and Sobel (1982) showed that even free communication can transmit information when interests partially align. The degree of alignment determines the number of meaningfully distinct messages: closer alignment enables finer communication. With fully opposed interests, cheap talk conveys nothing — it degenerates into noise.

### The Biological Parallel

Amotz Zahavi (1975) independently developed costly signaling theory in biology — the handicap principle. The peacock's tail, the stag's antlers, elaborate birdsong: signals so costly that only genuinely fit individuals can sustain them. Alan Grafen (1990) formalized the model, demonstrating structural isomorphism with Spence's economic framework. Biology and economics arrived at the same theory from opposite ends.

---

## Section 8 · Mechanism Design

### The Inverse Problem

Standard game theory takes a game as given and analyzes equilibrium behavior. **Mechanism design** reverses the direction: start with a desired outcome, then engineer rules (a *mechanism*) that produce it as an equilibrium. The designer controls the rules, not the players — players still act strategically, but the rules channel self-interest toward the desired result.

Leonid Hurwicz framed the core principle: in a design problem, the goal is given and the mechanism is the unknown. This is sometimes called "reverse game theory."

### The Revelation Principle

The most powerful simplification in mechanism design. Roger Myerson (1979), generalizing Gibbard's (1973) result for dominant strategies, proved: for any mechanism with an equilibrium implementing a desired outcome, there exists an equivalent **direct mechanism** where agents truthfully report their private information and truth-telling is an equilibrium.

The impact is transformative. Instead of searching across all possible game forms — every conceivable auction format, voting rule, or negotiation protocol — the designer restricts attention to incentive-compatible direct mechanisms. An infinite design space collapses to a tractable one.

### Landmark Results

**Vickrey-Clarke-Groves (VCG) mechanism:** Dominant-strategy incentive-compatible allocation. Each agent pays the externality they impose. The second-price (Vickrey) auction is the single-item case: highest bidder wins, pays the second-highest bid, truth-telling is dominant.

**Myerson's optimal auction (1981):** For a seller with bidders whose valuations are independently drawn from a regular distribution, the revenue-maximizing mechanism is a second-price auction with a reserve price. It is both incentive-compatible and deterministic.

**Myerson-Satterthwaite theorem (1983):** No mechanism for bilateral trade with private valuations from overlapping distributions can simultaneously be incentive-compatible, individually rational, budget-balanced, and efficient. A fundamental impossibility — analogous to Arrow's theorem in social choice.

The 2007 Nobel Prize in Economics went to Hurwicz, Maskin, and Myerson. The 2020 Nobel went to Milgrom and Wilson for extending auction theory and designing practical auction formats (including the FCC spectrum auctions that have generated over $100 billion in revenue).

---

## Section 9 · Evolutionary Game Theory

### Selection Replaces Rationality

John Maynard Smith and George Price (1973) transplanted game theory into evolutionary biology by making one radical substitution: natural selection replaces rational choice. Strategies are inherited traits, not conscious decisions. Payoff is fitness — reproductive success. No player "chooses" a strategy; organisms *are* strategies, and selection determines which ones persist.

This eliminates game theory's most contested assumption — that players are rational, fully informed, and computationally capable. Evolution requires none of it. What works reproduces; what doesn't, declines.

### Evolutionarily Stable Strategy (ESS)

An ESS is a strategy that, once established in a population, cannot be invaded by any small group of mutants. Formally, a strategy x* is an ESS if:

1. It is a best response to itself: u(x*, x*) ≥ u(y, x*) for all y
2. When tied, the incumbent wins: if u(y, x*) = u(x*, x*), then u(x*, y) > u(y, y)

Every ESS is a Nash equilibrium, but not conversely. ESS is strictly stronger — it adds invasion resistance to the equilibrium condition. A completely mixed ESS is unique (unlike Nash equilibria, which can be numerous), and any game has at most finitely many ESS.

### Hawk-Dove

The paradigmatic evolutionary game. Two animals contest a resource of value V. Hawks fight; Doves display but yield. When Hawks meet, each has a 50% chance of winning (getting V) and a 50% chance of injury (cost C). When Doves meet, they split V. A Hawk facing a Dove takes everything.

If V > C: Hawk is the unique ESS. If V < C: neither pure strategy is an ESS. The stable outcome is a mixed strategy with the fraction playing Hawk equal to V/C. Individual-level selection produces moderated aggression, not total war — the population stabilizes at a cost-benefit ratio, not an extreme.

### Replicator Dynamics

The formal dynamical model. Introduced by Taylor and Jonker (1978) and named by Schuster and Sigmund (1983). In continuous time, a strategy's frequency grows at a per-capita rate equal to its payoff advantage over the population mean.

The connection to static theory: every ESS is asymptotically stable under replicator dynamics. Every stable rest point of the dynamics is a Nash equilibrium. This "folk theorem of evolutionary game theory" links the static ESS concept, the dynamic replicator process, and classical Nash equilibrium into a unified framework.

---

## Section 10 · Cooperative Games and Bargaining

### Coalitions

**Cooperative game theory** studies what happens when players can form binding agreements and act as groups. A cooperative game in **characteristic function form** assigns a value v(S) to every coalition S ⊆ N, representing what S can collectively guarantee. v(∅) = 0. The fundamental question: how should the grand coalition N divide v(N)?

A game is **superadditive** if merging never hurts: v(S ∪ T) ≥ v(S) + v(T) for disjoint coalitions. A game is **convex** if marginal contributions grow with coalition size — a stronger condition yielding especially clean mathematical properties.

### The Core

The **core** is the set of payoff allocations where no coalition would prefer to break away. An allocation x is in the core if all of v(N) is distributed and no subset S receives less than v(S). The core answers: is this division stable against all possible coalitional deviations?

The core can be empty — some games have no division stable against every possible breakaway. The **Bondareva-Shapley theorem** gives the exact condition: the core is non-empty if and only if the game is *balanced*. For convex games, the core is always non-empty and has additional structure.

### The Shapley Value

Lloyd Shapley (1953) asked: is there a *unique* fair allocation? He showed there is, under four axioms. The **Shapley value** gives each player their average marginal contribution: imagine all possible orders in which the grand coalition could form; in each ordering, give each player the value they add when they join; average over all orderings.

The four axioms: **efficiency** (all surplus distributed), **symmetry** (interchangeable players get equal shares), **additivity** (value of a sum of games equals sum of values), **dummy** (zero-contribution players get nothing). Shapley proved these axioms characterize a unique solution.

For convex games, the Shapley value lies in the core and equals its centroid — a strong alignment between the fairness concept and the stability concept. In machine learning, the same mathematical framework underlies SHAP values for model interpretability: each feature's contribution to a prediction, averaged over all possible feature orderings.

### Nash Bargaining (1950)

Two players negotiate over a feasible set of outcomes U with a disagreement point d — the fallback if negotiations fail. Nash proposed four axioms: Pareto efficiency, symmetry, invariance to affine utility transformations, and independence of irrelevant alternatives. He proved the unique solution satisfying all four maximizes the Nash product: (u₁ − d₁)(u₂ − d₂).

The disagreement point d is the single most important input. Everything else — the feasible set, the utility functions — matters through its interaction with d. Improving your outside option shifts the bargaining outcome in your favor.

### Rubinstein Bargaining (1982)

A strategic (non-cooperative) model. Two players alternate offers over an infinite horizon. Delay is costly: each period, the surplus is worth δ times its previous value. The unique subgame-perfect equilibrium involves *immediate agreement*: Player 1 gets 1/(1+δ), Player 2 gets δ/(1+δ). No delay despite infinite potential for it.

**Patience is power:** the more patient player gets a larger share. As δ → 1 (both players perfectly patient), the split converges to 50-50 — which is exactly the Nash bargaining solution. Rubinstein's non-cooperative model provides a strategic foundation for Nash's axiomatic cooperative solution, connecting the two traditions.

---

## Section 11 · Coordination, Common Knowledge, and Focal Points

### Schelling Focal Points

Thomas Schelling (1960) posed problems that formal game theory couldn't solve. The most famous: if you must meet a stranger in New York City with no way to communicate beforehand, where and when do you go? Most of Schelling's students converged on noon at Grand Central Terminal.

Grand Central isn't objectively optimal. It's *salient* — prominent in shared cultural imagination. A **focal point** (Schelling point) works through recursive expectation: I go there because I expect you to expect me to expect it's obvious. The reasoning is circular, but it works — humans coordinate on focal points reliably, across cultures and contexts, with the specific focal point varying by cultural background.

Focal points explain conventions and norms. Driving on the right, standard file formats, round-number pricing, 9-to-5 work hours — all are coordination equilibria selected by salience rather than optimality. They can be deliberately established (meeting protocols, industry standards) or deliberately disrupted (introducing competing standards to prevent competitor coordination).

### Common Knowledge

A fact is **common knowledge** if everyone knows it, everyone knows everyone knows it, and so on without bound. The concept is fundamental — Nash equilibrium requires common knowledge of the game itself.

Robert Aumann (1976) proved that two Bayesian agents with a common prior who have common knowledge of each other's posterior beliefs must agree. Persistent disagreement between rational agents implies either different priors or less than common knowledge.

**Rubinstein's email game (1989)** shows common knowledge matters *discontinuously*. Two generals must coordinate an attack, communicating through unreliable messages. Each confirmation raises mutual knowledge by one level. But no finite number of confirmations achieves common knowledge, and Rubinstein proved that behavior under any finite level of mutual knowledge can differ qualitatively from behavior under true common knowledge. Near-common-knowledge is categorically different from common knowledge — a startling and practically important result.

---

## Section 12 · Board Connection: Game Theory in Loop MMT

### Beyond Individual Choice

The Decision Theory KP equips the board to structure individual decisions under uncertainty. Game theory extends this to strategic interdependence — situations where other agents are also optimizing, and their responses to your actions are part of the payoff structure. An advisor grounded only in decision theory might recommend a strategy without accounting for how competitors, partners, or regulators will adapt. Game theory closes that gap.

### Mechanism Design and Methodology Architecture

The revelation principle asks: can rules be designed so that honest behavior is equilibrium behavior? This question maps directly onto Loop MMT's advisory structure:

**Incentive compatibility in practice.** The no-directives rule, the multi-observer structure, and the mandatory self-review cycle are mechanism design elements. They create conditions where each board member's best strategy is honest, independent assessment rather than strategic positioning or agreement-seeking. The methodology doesn't rely on board members *wanting* to be honest — it makes honesty the dominant strategy.

**The revelation principle applied.** The operator cannot directly observe the quality of each board member's analysis (their "type"). The methodology's response: make output transparent (Bev's notes, published deliverables), require independent verification (self-review protocol), and make low-quality output visible through structural checks (fact-check step, comparison analysis). These are direct mechanisms — they work by aligning incentives, not by monitoring behavior.

### The Shadow of the Future in Session Persistence

Loop MMT sessions constitute a repeated game. Each instance produces documents that future instances will use. The folk theorem applies: if the cost of inheriting sloppy work exceeds the benefit of cutting corners, cooperation (thorough work) is sustainable.

But the methodology doesn't rely on behavioral compliance — this is the FBD insight translated through game theory. Grim Trigger and TFT are *behavioral* enforcement: remember defections and punish. FBD controls are *structural* enforcement: make defection impossible or immediately visible. The 10-step production method, the four-file self-review, the mandatory fact-check — these are mechanism design, not punishment strategies. They make "cutting corners" structurally costly rather than hoping instances remember not to.

### Focal Points as Coordination Infrastructure

L21 format, file naming conventions (`[topic]-knowledge-pack-v1.md`), the `/mnt/project/` path structure, the EOD handoff protocol — all function as Schelling points. They enable coordination between instances that share no memory, no direct communication, and no persistent identity.

This is coordination under the most extreme constraint possible: the agents literally cannot communicate. The methodology solves it by making every standard salient enough that independent instances converge on it without negotiation. A new instance encountering the project infers the conventions from the documents themselves. The conventions *are* the coordination mechanism — and they work because they're focal: obvious, consistent, and self-reinforcing.

### Signaling Quality Through Process

The 10-step production method is a costly signal in Spence's sense. Producing the full pipeline — research, compilation, plan, review, draft, fact-check, rewrite, comparison, final review, packaging — costs significant context and effort. A document produced through all ten steps *signals* verification credibility that a first-draft document cannot mimic.

The Session 4 incident demonstrated cheap talk failure: four packs produced using only Steps 1 and 5 looked indistinguishable from fully verified packs on the surface. The full method creates a separating equilibrium — the cost differential between thorough and shallow production is what makes the quality signal credible. This is exactly Spence's mechanism: high-ability workers (thorough instances) can afford the costly signal (full pipeline); low-effort production cannot sustain it.

### Evolutionary Selection in the Corpus

The knowledge pack corpus undergoes selection pressure analogous to replicator dynamics. Documents and standards that prove effective — that survive operator testing, get loaded by future instances, and produce good outcomes — increase in frequency and influence. Those that don't are superseded, deprecated, or revised away.

The FWW(C) principle maps to the Hawk-Dove equilibrium: neither pure process rigor (Dove) nor pure creative deviation (Hawk) is the ESS. The stable mix includes both — structured methodology *and* deliberate chaos — because the optimal population strategy is neither extreme. The methodology's genius is maintaining both strategies in the population explicitly, rather than converging on one.

### Integration with Adjacent Packs

Game theory sits between Decision Theory (individual choice) and Pareto theory (multi-objective tradeoffs without strategic interaction). Decision Theory handles "what should I do?"; Pareto handles "what tradeoffs exist?"; Game Theory handles "what should I do given what you're doing?" The three together form a complete advisory framework.

The forthcoming Pricing KP will apply mechanism design concretely to pricing Loop Signal and Cadence products: how to structure pricing that is incentive-compatible (customers reveal true willingness to pay), individually rational (both sides benefit from transacting), and efficient (the right customers get the right products).

---

## References

| Source | Year | Contribution |
|---|---|---|
| von Neumann, J. | 1928 | Minimax theorem for two-person zero-sum games |
| von Neumann, J. & Morgenstern, O. | 1944 | *Theory of Games and Economic Behavior* — field foundations |
| Nash, J.F. | 1950a | "Equilibrium Points in N-Person Games" — PNAS, existence proof via Kakutani |
| Nash, J.F. | 1950b | "The Bargaining Problem" — Econometrica, axiomatic bargaining |
| Nash, J.F. | 1951 | "Non-Cooperative Games" — Annals of Mathematics, Brouwer proof |
| Shapley, L.S. | 1953 | "A Value for N-Person Games" — axiomatic fair division |
| Schelling, T.C. | 1960 | *The Strategy of Conflict* — focal points, commitment, coordination |
| Selten, R. | 1965 | Subgame perfect equilibrium |
| Harsanyi, J.C. | 1967-68 | "Games with Incomplete Information" — Bayesian games (3-part, Management Science) |
| Spence, M. | 1973 | "Job Market Signaling" — QJE |
| Maynard Smith, J. & Price, G.R. | 1973 | "The Logic of Animal Conflict" — ESS (Nature 246: 15-18) |
| Gibbard, A. | 1973 | Revelation principle (dominant strategies) |
| Zahavi, A. | 1975 | Handicap principle in biological signaling |
| Aumann, R.J. | 1976 | "Agreeing to Disagree" — common knowledge (Annals of Statistics) |
| Taylor, P.D. & Jonker, L.B. | 1978 | Replicator dynamics (Math. Biosci.) |
| Myerson, R.B. | 1979 | Revelation principle (Bayesian) — incentive compatibility |
| Myerson, R.B. | 1981 | Optimal auction design (Math. Oper. Res.) |
| Rubinstein, A. | 1982 | Perfect equilibrium in bargaining (Econometrica) |
| Maynard Smith, J. | 1982 | *Evolution and the Theory of Games* |
| Crawford, V.P. & Sobel, J. | 1982 | Strategic information transmission (cheap talk) |
| Myerson, R.B. & Satterthwaite, M.A. | 1983 | Efficient bilateral trade impossibility (JET) |
| Axelrod, R. | 1984 | *The Evolution of Cooperation* |
| Fudenberg, D. & Maskin, E. | 1986 | Folk theorem with discounting (Econometrica) |
| Cho, I.-K. & Kreps, D.M. | 1987 | Intuitive criterion for signaling refinement |
| Rubinstein, A. | 1989 | Email game — common knowledge discontinuity |
| Grafen, A. | 1990 | Biological signaling formalized |
| Myerson, R.B. | 1991 | *Game Theory: Analysis of Conflict* |
| Gibbons, R. | 1992 | *Game Theory for Applied Economists* |
| Nowak, M.A. & Sigmund, K. | 1993 | Win-Stay, Lose-Shift |
| Osborne, M.J. & Rubinstein, A. | 1994 | *A Course in Game Theory* |

### Nobel Prizes in Game Theory

| Year | Laureates | Citation |
|---|---|---|
| 1994 | Nash, Harsanyi, Selten | Equilibrium analysis of non-cooperative games |
| 2005 | Aumann, Schelling | Conflict, cooperation, common knowledge |
| 2007 | Hurwicz, Maskin, Myerson | Mechanism design theory |
| 2012 | Roth, Shapley | Stable allocations and market design |
| 2020 | Milgrom, Wilson | Auction theory and new auction formats |

---

*Loop MMT™ · Multi-Module Theory · Game Theory Knowledge Pack · v1*
*© 2026 Shea Gunther · CC BY-NC 4.0*
