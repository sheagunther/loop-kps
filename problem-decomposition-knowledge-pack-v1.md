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
Problem Decomposition Knowledge Pack
:::

::: build-tag
v1 · 8 April 2026
:::
:::
:::
:::

::: body-wrap
::: toc-title
Contents
:::

-   [Abstract](#ch-abstract)
-   [1 · Foundations](#ch-foundations)
-   [2 · The Classical Traditions](#ch-traditions)
-   [3 · Recurring Patterns](#ch-patterns)
-   [4 · The Toolbox](#ch-toolbox)
-   [5 · Recomposition](#ch-recomposition)
-   [6 · When Decomposition Fails](#ch-limits)
-   [7 · Board Connection](#ch-board)
-   [References](#ch-refs)

::: {.content role="main"}
::: {#ch-abstract .abstract-box}
::: abstract-label
Abstract
:::

Decomposition --- the act of breaking a complex problem into smaller, solvable subproblems --- is the most universal strategy in the problem-solver\'s repertoire. It appears independently in mathematics, computer science, systems engineering, physics, and design theory, not because these fields copied each other but because they all ran into the same constraint: human cognition has a narrow bottleneck, and complex problems don\'t fit through it whole.

This pack covers the full arc. It starts with the cognitive science explaining *why* decomposition works --- Miller\'s chunking, Sweller\'s cognitive load theory, the search-space reduction argument. It surveys four classical traditions that formalized decomposition independently --- Pólya, Simon, the algorithmic divide-and-conquer paradigm, and Fermi estimation. It examines Altshuller\'s discovery that the same solution patterns recur across all domains. It catalogs the practitioner\'s toolkit of decomposition strategies with heuristics for selecting among them. And it devotes serious attention to the two areas most treatments neglect: recomposition (putting the pieces back together is harder than taking them apart) and failure modes (wicked problems, emergence, and over-decomposition).

The intended reader is an AI advisory board working in cooperative partnership with a human operator --- a group whose job is to help fix large things that can be fixed in small ways, and to recognize when a large thing cannot be fixed in small ways and requires a different approach entirely.
:::

::: {#ch-foundations .chapter}
::: chapter-number
Chapter 1
:::

::: chapter-title
Foundations --- The Cognitive Case
:::

::: {#s-bottleneck .section}
::: section-title
The Bottleneck
:::

In 1956, George Miller published one of the most cited papers in the history of psychology: \"The Magical Number Seven, Plus or Minus Two: Some Limits on Our Capacity for Processing Information.\" Miller demonstrated that human short-term memory holds roughly seven chunks of information simultaneously --- and that this limit is architectural, not motivational. You cannot train your way past it, any more than you can train yourself to see ultraviolet light. It is a property of the hardware (Miller, 1956).

Three decades later, John Sweller developed **cognitive load theory** from this foundation. Sweller showed that when a problem\'s intrinsic complexity exceeds working-memory capacity, problem-solving doesn\'t just slow down --- it fails in characteristic ways. People lose track of subgoals, apply the wrong operations, or freeze entirely. The experience has a name: analysis paralysis. It is not laziness or lack of intelligence. It is a buffer overflow (Sweller, 1988).

Decomposition is the workaround. Instead of holding the entire problem in working memory --- which is impossible for any non-trivial problem --- you hold one piece. The piece fits. You solve it, set it aside, and load the next piece. At any given moment, the cognitive load stays within what the architecture can handle.
:::

::: {#s-chunking .section}
::: section-title
Chunks and Expertise
:::

Miller\'s deeper contribution was the concept of the **chunk** --- a unit of information bound together by meaning. The sequence F-B-I-C-I-A-I-R-S contains nine letters, which exceeds short-term memory capacity. Chunked as FBI-CIA-IRS, it becomes three items: well within range. The raw data is identical; the organization has changed.

Chase and Simon (1973) demonstrated the same principle in chess. Grandmasters shown a mid-game position for five seconds can reconstruct it almost perfectly; novices recall only a few pieces. But when shown pieces placed *randomly* --- no meaningful patterns --- grandmasters perform no better than novices. The experts don\'t have larger memories. They have better chunks. They see the board in terms of attacking formations and pawn structures where novices see individual pieces.

This is the mechanism by which decomposition creates cognitive room. When you break a problem into well-defined subproblems, each subproblem becomes a chunk. A problem with thirty interacting elements might overwhelm working memory. The same problem, decomposed into five subproblems of six elements each, fits comfortably --- not because the elements have disappeared but because the organization has given you purchase on them.
:::

::: {#s-search-space .section}
::: section-title
The Search-Space Argument
:::

There is a complementary mathematical argument. Every problem has a **search space** --- the set of possible answers you might consider. Solving a problem means searching this space for a good one. The difficulty scales with the size of the space.

::: {.callout .key}
::: callout-label
Key Concept --- Nonlinear Reduction
:::

Consider choosing a restaurant in a city with 7,000 options. That\'s a search of 7,000. Now decompose: pick a neighborhood (12 options), pick a cuisine (20 options), pick a specific restaurant (roughly 29 options on average). You\'ve replaced one search of 7,000 with three searches totaling about 61. The original search space is the *product* of the subproblem spaces; the decomposed effort is closer to their *sum*. This nonlinear reduction is why decomposition can convert an intractable problem into a sequence of easy ones (Grunewald, 2022).
:::
:::

::: {#s-three-loads .section}
::: section-title
Three Loads
:::

::: {.callout .tip}
::: callout-label
Tip --- Cognitive Load Types for Advisors
:::

Sweller distinguished three types of cognitive load. **Intrinsic** load is the irreducible complexity of the problem itself. **Extraneous** load is complexity added by poor organization, unclear presentation, or irrelevant detail --- this is pure waste. **Germane** load is productive effort spent building lasting understanding. Decomposition reduces intrinsic load (smaller pieces) and extraneous load (clearer structure), freeing capacity for germane processing. For an advisory board, the practical implication is that *how* a problem is presented matters as much as *what* the problem is. A well-decomposed briefing reduces waste and lets advisors spend their working memory on the actual question (Sweller, 1988; Chandler & Sweller, 1991).
:::
:::

The cognitive science establishes that decomposition is not a preference. It is an adaptation to a fixed architectural constraint. The question is not whether to decompose but how to do it well --- a question that multiple intellectual traditions have answered independently.
:::

::: {#ch-traditions .chapter}
::: chapter-number
Chapter 2
:::

::: chapter-title
The Classical Traditions
:::

The fact that decomposition was formalized independently in mathematics, systems science, computer science, and physics --- by people largely unaware of each other\'s work --- is itself the strongest evidence that it reflects something real about the structure of problems rather than an arbitrary methodological choice.

::: {#s-polya .section}
::: section-title
Pólya --- Problem Solving as a Learnable Skill
:::

George Pólya\'s *How to Solve It* (1945) has been continuously in print for over eighty years and has sold more than a million copies. Schoenfeld described it as marking a line of demarcation between two eras in problem-solving education. Minsky called it essential reading for anyone in artificial intelligence.

Pólya\'s four-step method --- understand the problem, devise a plan, carry out the plan, look back --- is a decomposition of the *act of problem-solving itself*. But his deeper contribution was the 67-entry \"Short Dictionary of Heuristic,\" which catalogs recurring structural moves: analogy (find a related problem you\'ve already solved), specialization (try a restricted version first), working backward (start from the desired result), and decomposition/recombination (separate the parts, solve them, reassemble).

::: {.callout .key}
::: callout-label
Key Concept --- The Advisory Stance
:::

Pólya insisted that the teacher should never simply present a plan. The teacher asks progressively more specific questions --- \"What is the unknown? What are the data? Have you seen a related problem? Can you solve a part of it?\" --- until the student makes the final step. The teacher guides the decomposition; the student performs it. This is a precise model for advisory behavior: the board asks the questions that guide decomposition; the operator makes the decisions (Pólya, 1945).
:::
:::

::: {#s-simon .section}
::: section-title
Simon --- Near-Decomposability
:::

Herbert Simon won the Nobel Memorial Prize in Economic Sciences (1978) and the Turing Award (1975). In his 1962 paper \"The Architecture of Complexity,\" he made an empirical claim about reality itself: viable complex systems --- biological, social, physical, artificial --- tend to be hierarchically organized, with interactions within subsystems far more intense than interactions between subsystems. He called this property **near-decomposability**.

His watchmaker parable makes the point concrete. Two watchmakers each build watches from 1,000 parts. Tempus builds as a single flat assembly --- any interruption means restarting from scratch. Hora builds in stable subassemblies of about ten parts each. Hora succeeds; Tempus fails. The lesson: hierarchical systems with stable intermediate forms evolve enormously faster than flat ones (Simon, 1962).

Simon extended this to problem-solving through **means-ends analysis**: compare current state to goal, identify the largest gap, find an operator that closes it, and if the operator can\'t be applied directly, set a subgoal to enable it. Recurse. He also contributed the concept of **satisficing**: because bounded rationality prevents exhaustive search, we settle for solutions that are good enough. Decomposition is inherently a satisficing strategy --- the decomposed solution is rarely globally optimal, because the cuts inevitably separate some interacting elements. But it is *findable* (Simon, 1969).
:::

::: {#s-divide-conquer .section}
::: section-title
Divide and Conquer --- The Algorithmic Paradigm
:::

In computer science, divide and conquer is formalized to the point of mathematical precision: (1) **divide** the problem into smaller instances of the same type, (2) **conquer** by solving each recursively (or directly if trivial), (3) **combine** sub-solutions into a solution for the original. Merge sort is the textbook example: split a list in half, sort each half, merge the sorted halves. The hard problem (sorting 1,000 items) becomes many trivial ones (sorting 1 item) plus a straightforward merge.

Two properties give divide and conquer its power. Independent subproblems can be solved in **parallel** --- on different processors, by different people, in different sessions. And the complexity is often governed by the Master Theorem, T(n) = aT(n/b) + f(n), which frequently yields logarithmic or near-linear scaling where a naive approach would be polynomial or worse.

A critical distinction: divide and conquer requires independent subproblems. When subproblems overlap --- the same sub-computation recurs in multiple branches --- **dynamic programming** is the correct strategy: store and reuse results instead of recomputing them. Misidentifying the structure is expensive. Applying divide-and-conquer to overlapping subproblems causes exponential blowup.
:::

::: {#s-fermi .section}
::: section-title
Fermi Estimation --- Decomposition as Epistemology
:::

At the Trinity nuclear test in 1945, Enrico Fermi dropped scraps of paper as the shockwave passed, measured their displacement, and estimated the bomb\'s yield at about 10 kilotons. The actual yield was 20 kilotons. The method was pure decomposition: an unknowable quantity, factored into estimable components, with the structure of the decomposition providing accuracy that no individual estimate could.

The \"piano tuners in Chicago\" problem is the canonical classroom example. You don\'t know the answer, and you can\'t look it up. But you can decompose: population, fraction with pianos, tunings per piano per year, tunings per tuner per day, working days per year. Multiply through, and you land within an order of magnitude of the truth --- typically much closer.

The deep insight: errors in independent estimates tend to cancel. Some are too high, some too low, and the product converges. Recent research (2025) on collective Fermi estimation found that groups who explicitly decompose problems produce more accurate estimates than groups who aggregate individual guesses. The mechanism is the decomposition structure itself.

For advisory work, the lesson is direct: you don\'t need complete information to make useful decisions. You need the right decomposition. And the decomposition reveals which sub-estimates carry the most uncertainty --- where further investigation would yield the greatest return.
:::

  Tradition          Origin                          Core Move                              Key Insight
  ------------------ ------------------------------- -------------------------------------- ---------------------------------------------------------------------
  Pólya              Mathematics, 1945               Find a related, simpler problem        Problem-solving is learnable, not innate
  Simon              Systems science, 1962           Exploit hierarchical structure         Viable complex systems are already nearly decomposed
  Divide & Conquer   Computer science, mid-20th c.   Recurse on smaller instances           Independence enables parallelism and logarithmic scaling
  Fermi              Physics, 1940s                  Factor unknowns into estimable parts   Decomposition structure provides accuracy individual guesses cannot

Four traditions, four domains, one structural insight. But the most ambitious investigation into whether problem-solving patterns are truly universal came from a fifth tradition --- one that analyzed millions of patents to find out.
:::

::: {#ch-patterns .chapter}
::: chapter-number
Chapter 3
:::

::: chapter-title
Recurring Patterns --- TRIZ and the Abstraction Ladder
:::

::: {#s-altshuller .section}
::: section-title
The Discovery
:::

Starting in 1946, Soviet inventor Genrich Altshuller began analyzing patents --- eventually over 2.5 million of them, across every technical discipline. His finding was stark: approximately 100 fundamental solution strategies account for the vast majority of inventive breakthroughs. The same structural moves recur across chemistry, mechanical engineering, electronics, and every other field. Later inventors routinely reinvent solutions that earlier inventors in different fields had already found, separated by decades, because nobody had extracted and organized the patterns (Altshuller, 1984).

Altshuller called this the **Tower of Babel problem**. Each discipline wraps its solutions in domain-specific jargon, hiding the structural commonality. When you strip away the jargon --- when you abstract --- the patterns become visible. The chemist\'s \"phase transition,\" the organizational theorist\'s \"tipping point,\" and the software engineer\'s \"state change\" may be the same structural pattern in different costumes.
:::

::: {#s-abstraction-ladder .section}
::: section-title
The Abstraction Ladder
:::

TRIZ (the Russian acronym for Theory of Inventive Problem Solving) formalizes the meta-strategy as a four-step process:

1.  **Specific problem** --- the concrete challenge with all its particular details
2.  **Abstract to generic problem** --- strip domain-specific detail to reveal the structural pattern
3.  **Look up generic solution** --- consult the pattern library for known resolutions of this type of structural problem
4.  **Derive specific solution** --- re-instantiate the generic solution in your domain

This is decomposition applied to the problem-solving *process itself*. Instead of solving your specific problem from scratch, you decompose the act of solving into abstraction, lookup, and re-instantiation. Each step is simpler than the whole. The pattern library does much of the creative work --- you are leveraging solutions that humanity has already found rather than reinventing them.
:::

::: {#s-contradictions .section}
::: section-title
Contradictions and the Matrix
:::

Altshuller observed that inventive problems typically involve a **technical contradiction**: improving one parameter worsens another. Routine engineering compromises between the parameters. Inventive engineering resolves the contradiction so that both improve. He organized 39 engineering parameters into a Contradiction Matrix, with each cell pointing to whichever of his 40 Inventive Principles had most frequently resolved that conflict in the patent literature.

  \#   Principle                                                     Structural Relevance
  ---- ------------------------------------------------------------- -----------------------------------------
  1    Segmentation --- divide into independent parts                The decomposition move itself
  2    Extraction --- remove the interfering element                 Isolate what\'s causing the problem
  3    Local quality --- different parts serve different functions   Specialization within a decomposition
  13   Inversion --- reverse the procedure                           Work backward from the goal (cf. Pólya)
  10   Prior action --- perform changes in advance                   Pre-solve predictable subproblems
  5    Merging --- combine identical operations                      The recomposition move

::: {.callout .warn}
::: callout-label
Warning --- Scope of the Pattern Library
:::

TRIZ was built from technical patents. The Contradiction Matrix works best on problems with measurable parameters and definable conflicts --- what Rittel and Webber would call \"tame\" problems. Social, organizational, and political problems do not fit neatly into the matrix. The transferable insight from TRIZ is not the matrix itself but the *abstraction ladder*: strip away domain jargon, look for structural patterns, check whether someone has solved this type of problem before. That meta-strategy is domain-independent.
:::
:::

::: {#s-interdisciplinary .section}
::: section-title
The Interdisciplinary Advantage
:::

The abstraction ladder explains why a diverse advisory group has a structural advantage over any single-domain expert. Each member brings a different vocabulary but may recognize the same structural pattern. An advisory group that can abstract across vocabularies has access to a larger pattern library --- which is exactly what Altshuller found buried in the patent literature across all of engineering.

This connects directly to Pólya\'s most important heuristic question: \"Do you know a related problem?\" A board with twenty different domain backgrounds has twenty times the surface area for pattern recognition.
:::

Knowing *that* you should decompose and *why* patterns recur is the strategic foundation. But the practitioner still needs to know *how* --- which decomposition strategy to use for which kind of problem.
:::

::: {#ch-toolbox .chapter}
::: chapter-number
Chapter 4
:::

::: chapter-title
The Decomposition Toolbox
:::

Knowing that you should break a problem apart is the easy realization. Knowing *where to cut* is the skill. Different problem structures call for different decomposition strategies, and the choice of strategy shapes everything downstream.

::: {#s-topdown-bottomup .section}
::: section-title
Top-Down and Bottom-Up
:::

**Top-down** starts from the whole: identify major components, recursively split until each piece is tractable. It works when the high-level structure is understood, even if details are unclear. **Bottom-up** starts from known solvable pieces and combines them into larger assemblies. It works when the overall structure is unclear but component-level behaviors are well understood.

Research on engineering design (Song et al.) found that expert engineers typically start top-down --- they want the landscape --- then shift to bottom-up when they hit a section where details matter most. Novices tend to dive depth-first into the first subproblem they see, solving it in elaborate detail while neglecting the overall structure. The expert pattern is: orient broadly, then focus narrowly.
:::

::: {#s-functional-domain .section}
::: section-title
Functional and Domain Decomposition
:::

**Functional decomposition** divides by responsibility --- what each part *does*. A system might split into authentication, storage, logic, and presentation. **Domain decomposition** divides by subject matter --- a system splits into catalog, orders, payments, and communication.

Simon\'s near-decomposability principle provides the guidance for both: **cut where the interactions are weakest**. The best decomposition puts tightly coupled elements together and loosely coupled elements apart. When you have to choose between functional and domain boundaries, ask which grouping minimizes the traffic across the cuts.
:::

::: {#s-volatility .section}
::: section-title
Volatility-Based Decomposition
:::

Divide based on **what changes at different rates**. Group elements that change together; separate elements that change independently. When you modify a frequently changing component, you don\'t want the modification to ripple through stable components. In software, this is the principle behind separating configuration from code, or isolating volatile business rules from stable infrastructure.

For advisory work on evolving systems, volatility-based decomposition answers a critical question: \"If we change this, what else breaks?\" The answer shapes the risk profile of every proposed intervention.
:::

::: {#s-sequential-parallel .section}
::: section-title
Sequential and Parallel
:::

**Sequential** decomposition arranges subproblems in dependency order. **Parallel** decomposition identifies subproblems that can proceed simultaneously. The tradeoff mirrors parallel computing: more parallel tracks mean faster progress but higher coordination costs. If coordination cost exceeds the benefit, you have over-decomposed.
:::

::: {#s-recursive-base .section}
::: section-title
Recursive Decomposition and Base Cases
:::

Apply the same splitting strategy at every level until you reach **base cases** --- problems simple enough to solve directly. The elegance is that you need only two things: a way to split and a way to recognize when to stop. The danger is infinite regress. Well-defined base cases are the termination condition.
:::

  Problem Characteristic                 Recommended Strategy
  -------------------------------------- ----------------------
  Well-understood high-level structure   Top-down
  Unknown structure, known components    Bottom-up
  Clear functional responsibilities      Functional
  Natural subject-matter boundaries      Domain
  Parts change at different rates        Volatility-based
  Strict dependency chains               Sequential
  Independent work streams possible      Parallel
  Self-similar structure at each level   Recursive

::: {.callout .tip}
::: callout-label
Tip --- When to Stop Decomposing
:::

Five heuristic questions for the granularity decision: (1) Can this piece be solved independently? (2) Can it be tested independently? (3) Can one person or one session hold it in working memory? (4) Would further splitting destroy meaningful relationships between elements? (5) Would the coordination cost of more pieces exceed the benefit of having smaller ones? When you answer \"yes, stop here\" to all five, you\'ve likely found the right level. Too coarse and the pieces are still intractable. Too fine and you spend more time managing boundaries than solving problems.
:::

The toolbox handles the first half of the problem: taking things apart. The second half --- putting them back together --- gets far less attention, is at least as hard, and is where most decompositions actually fail.
:::

::: {#ch-recomposition .chapter}
::: chapter-number
Chapter 5
:::

::: chapter-title
Recomposition --- The Hard Half
:::

::: {#s-neglected .section}
::: section-title
The Neglected Problem
:::

Most writing about decomposition treats reassembly as an afterthought --- as if breaking a problem into good pieces automatically produces a working whole. It does not. A Virginia Tech study comparing professional engineers, engineering seniors, and freshmen found that experts spent significantly more cognitive effort on high-level framing and integration than on individual component details. Students --- both freshmen and seniors --- reversed this pattern, spending most effort on components and least on integration (Song et al.).

::: {.callout .key}
::: callout-label
Key Concept --- The Expert Pattern
:::

In interviews, expert engineers described a consistent three-phase approach: (1) consider the whole problem to understand the big picture, (2) break it into small pieces to work on, (3) combine the pieces into the final solution. Phase 3 was not a formality. It received deliberate, substantial effort. The experts treated recomposition as a distinct engineering challenge --- not a consequence of decomposition but a problem of equal or greater difficulty.
:::
:::

::: {#s-interfaces .section}
::: section-title
Interfaces
:::

Sub-solutions that are individually correct may not compose into a valid whole. Each subproblem, solved in isolation, makes implicit assumptions about its environment: what inputs it will receive, what format its neighbors expect, what resources are available. These assumptions form **interfaces** between subproblems. When assumptions conflict, integration fails --- and the failure manifests not in any individual piece but in the spaces between pieces.

::: {.callout .warn}
::: callout-label
Warning --- The Integration Failure Mode
:::

If you decompose a problem and assign parts to different people, instances, or sessions, every boundary between parts is a potential failure point. The mitigation is to specify interfaces *before* solving the subproblems: what does each part receive, what does it deliver, what constraints hold across the boundary. This is more work upfront. It prevents the far more expensive failure of discovering incompatible assumptions at integration time.
:::
:::

::: {#s-complicating .section}
::: section-title
Complicating Variables
:::

Simon and colleagues identified **complicating variables** in mathematical optimization --- variables that appear in multiple subproblems. When present, subproblems are not truly independent: changing a complicating variable in one subproblem affects the feasibility of others. The decomposition method works well when complicating variables are few. As they multiply, the advantage of decomposition erodes.

In practical terms: the more your subproblems share state, constraints, or resources, the harder recomposition becomes. A good decomposition minimizes complicating variables. A bad one slices through tightly coupled elements and then struggles endlessly to integrate.
:::

::: {#s-combine-step .section}
::: section-title
The Combine Step
:::

In the divide-and-conquer paradigm, the **combine step** is often the hardest part. In merge sort, the merge is where the work happens. In the FFT, the butterfly recombinations are the algorithmic core. The divide step is frequently trivial; the combine step is where the cleverness lives. This is a general principle: the difficulty of recomposition is at least as great as the difficulty of decomposition --- and often greater. Anyone advising on how to break a problem apart has an obligation to also address how the pieces will be reassembled.
:::

Recomposition is manageable when subproblems are well-defined and interfaces are explicit. But there exists a class of problems for which decomposition itself is not a viable strategy --- problems where breaking things apart destroys the essential structure.
:::

::: {#ch-limits .chapter}
::: chapter-number
Chapter 6
:::

::: chapter-title
When Decomposition Fails
:::

::: {#s-wicked .section}
::: section-title
Wicked Problems
:::

In 1973, Horst Rittel and Melvin Webber introduced the concept of the **wicked problem** --- a problem structurally different from the \"tame\" problems that decomposition was designed for. Three of their ten defining properties are particularly fatal to decomposition:

-   **No definitive formulation.** The problem definition depends on the solution being considered. Change the proposed solution and the problem changes. You cannot decompose what keeps shifting under your hands.
-   **Every problem is a symptom of another.** Decomposing does not yield solvable base cases; it yields more wicked problems. The hierarchy doesn\'t terminate.
-   **No stopping rule.** There is no signal that you\'ve solved the problem. You stop because you run out of time or money --- not because the problem tells you it\'s done.

::: {.callout .warn}
::: callout-label
Warning --- Wicked-Problem Signals
:::

If the problem keeps shifting when you try to formulate it precisely; if every proposed solution reveals new problems of comparable difficulty; if stakeholders cannot agree on what the problem *is*, not just how to solve it; if decomposition keeps producing subproblems as complex as the original --- you are likely in wicked-problem territory. Decomposition is not the right tool here. Collaborative argumentation, stakeholder alignment, and iterative coping are more appropriate approaches (Rittel & Webber, 1973).
:::
:::

::: {#s-emergence .section}
::: section-title
Emergence
:::

Emergence is the phenomenon in which a system exhibits properties that none of its components possess individually and that cannot be predicted from studying components in isolation. Traffic jams are not a property of individual cars. Consciousness is not a property of individual neurons. The saltiness of sodium chloride belongs to neither sodium nor chlorine gas.

Emergent properties arise from *relationships* between components. When you decompose and study parts separately, you lose the relationships and therefore lose the emergent behavior. This is the fundamental limit of reductionism: complete knowledge of parts does not guarantee understanding of the whole (Van Regenmortel, 2004).

For advisory work, the practical implication is: after decomposition, always ask what system-level behaviors might exist that no subproblem captures. If you\'ve decomposed a social system into organizational, technical, and financial subproblems and solved each one, the way those solutions interact may produce emergent outcomes that none of the subproblem analyses predicted.
:::

::: {#s-over-decomp .section}
::: section-title
Over-Decomposition
:::

Decomposition can also fail simply by being too aggressive. When pieces are too small, coordination overhead exceeds cognitive benefit. Each boundary is a potential integration failure, a communication channel to maintain, a set of interface assumptions to keep consistent. At some point, you spend more time managing the decomposition than solving the problem. The parallel-computing analogy is precise: granularity has a sweet spot, and overshooting it is as costly as undershooting.
:::

::: {#s-tame-within-wicked .section}
::: section-title
Tame Subproblems Within Wicked Problems
:::

Recognizing that a problem is wicked does not make decomposition useless. Many apparently wicked problems *contain* tame subproblems that can be extracted and solved. A public health crisis may be wicked in its political dimensions but contain tame epidemiological modeling problems. An organizational transformation may be wicked at the strategic level but contain tame infrastructure engineering at the technical level.

The pragmatic approach: decompose as far as you productively can, solve the tame parts, and use the results to narrow the uncertainty around the wicked remainder. Simon\'s satisficing applies: you cannot optimize a wicked problem, but you can make progress on the tame subproblems within it. Progress is possible even when completion is not.

  Property          Tame Problem                           Wicked Problem
  ----------------- -------------------------------------- --------------------------------------------------
  Formulation       Definitive; can be stated precisely    Shifts with perspective and proposed solution
  Stopping rule     Clear criteria for \"solved\"          No inherent stopping rule
  Solution test     True/false; objectively verifiable     Good/bad; depends on stakeholder values
  Trial and error   Feasible; experiments are reversible   Every attempt counts; solutions are irreversible
  Decomposability   Yields solvable subproblems            Yields more wicked problems
  Uniqueness        Classes of similar problems exist      Essentially unique
:::

Understanding when decomposition will work --- and when it won\'t --- is the calibration that separates useful advice from wasted effort. The final chapter maps this entire landscape onto the specific advisory context.
:::

::: {#ch-board .chapter}
::: chapter-number
Chapter 7
:::

::: chapter-title
Board Connection --- Decomposition in Practice
:::

::: {#s-board-engine .section}
::: section-title
The Board as Decomposition Engine
:::

An advisory board of twenty AI members with distinct perspectives is a decomposition engine by construction. When a problem enters the board, it refracts through multiple lenses simultaneously. One member sees functional decomposition --- what each piece needs to do. Another sees domain boundaries. A third sees volatility --- which parts will change. A fourth sees the wicked-problem dimensions --- where the problem resists formulation.

This is not redundancy. It is the advisory equivalent of Altshuller\'s cross-domain patent analysis. Each member contributes a different decomposition of the same problem. The operator, at the intersection, can synthesize them into a decomposition that no single perspective would have produced alone.
:::

::: {#s-operator-recomposition .section}
::: section-title
The Operator as Recomposition Layer
:::

If the board is the decomposition engine, the operator is the recomposition layer --- the person who holds the big picture and integrates sub-advice into a coherent whole. The Virginia Tech research showed that experts devote serious cognitive effort to integration. In the methodology, this is the operator\'s core function.

This is why the No Directives Rule exists. Board members advise on parts; the operator recomposes and decides. If individual advisors could direct action, each would optimize for their own subproblem without accounting for the interfaces and complicating variables that only the recomposition layer can see. Decomposition without centralized recomposition produces sub-solutions that are individually correct but collectively incoherent.
:::

::: {#s-instance-lifecycle .section}
::: section-title
Session Lifecycle as Recursive Decomposition
:::

Each session follows the recursive pattern. A fresh instance receives the current state via handoff documents and project files, decomposes the current challenge into a session\'s worth of subproblems, solves them, and hands off for the next instance. The handoff document is the interface specification between sessions --- it defines what was done, what remains, and what the next instance needs.

When handoffs are well-specified, sessions compose cleanly. When they are vague, the next instance wastes effort re-deriving state --- the exact failure mode of poorly specified interfaces in software. The principle \"derive state, don\'t maintain it\" is decomposition discipline: rather than depending on persistent memory (a complicating variable shared across all sessions), each instance derives understanding from the corpus. The state lives in the artifacts, not the agent. This makes each session a more independent subproblem.
:::

::: {#s-fbd .section}
::: section-title
FBD Principles as Decomposition Constraints
:::

Fix by Design principles constrain the set of admissible decompositions. They define where cuts must go and --- equally important --- where they must not. If FBD-1 requires that a capability must reside in a specific module, every decomposition touching that capability is constrained. The constraint narrows the search space and makes the remaining decompositions structurally safer, because the constraint was designed to prevent a known class of integration failures.
:::

::: {#s-worked-example .section}
::: section-title
Worked Example --- The Butcher Constellation
:::

The Butcher Constellation --- a custom order management system for a seasonal deer processing operation --- illustrates layered decomposition in practice:

-   **Domain** --- the routing table split into six sections (intake, lifecycle, payments, notifications, reports, dashboard), each a cohesive domain with defined interfaces
-   **Sequential** --- the implementation roadmap organized as milestones (M1--M6+), each building on the previous --- Simon\'s stable intermediate forms applied to delivery
-   **Volatility** --- the core constellation engine (stable) separated from the dashboard UI (volatile), allowing the engine to stabilize while the presentation continued to evolve
-   **Verification** --- the test suite organized into eight tiers, each independently executable

No single strategy was sufficient. The real-world problem required multiple decomposition strategies operating at different levels of the system simultaneously.
:::

  Decomposition Concept      Loop MMT Equivalent
  -------------------------- --------------------------------------------------------------
  Subproblem                 Milestone, work item, session scope
  Interface specification    EOD handoff, packet contract
  Base case                  Atomic work item solvable in one session
  Complicating variable      Cross-cutting concern (e.g., Stripe signing secret, FBD-1)
  Near-decomposability       Routing table sections with defined inter-section interfaces
  Stable intermediate form   Completed milestone with passing tests
  Recursive decomposition    Session lifecycle: receive → decompose → solve → hand off
  Decomposition constraint   FBD principle
  Volatility separation      Constellation engine (stable) vs. dashboard (volatile)
  Pattern library            Knowledge pack corpus, prior session precedent

::: {.callout .tip}
::: callout-label
Tip --- The First Question
:::

When a new problem arrives at the board, the most productive opening move is Pólya\'s: \"Have you seen a related problem?\" The knowledge pack corpus, accumulated session history, and the board\'s diverse backgrounds are all pattern libraries. Before decomposing from scratch, check whether a structurally similar problem has already been decomposed. The abstraction ladder applies: strip the domain detail, find the structural pattern, and check whether a known decomposition fits.
:::

Decomposition is the universal meta-strategy --- present in every major problem-solving tradition because it addresses a fundamental architectural constraint. The board exists to bring twenty lenses to the decomposition. The operator exists to perform the recomposition. The methodology exists to make the interfaces between sessions, between advisors, and between subproblems explicit enough that the pieces compose into a coherent whole. When it works, large things get fixed in small ways. When it doesn\'t --- when the problem is wicked, or the decomposition is wrong, or the recomposition is neglected --- the advisory role shifts from \"help break this down\" to \"help recognize why breaking it down isn\'t working.\" Both roles are valuable. Both require the material in this pack.
:::

::: {#ch-refs .chapter}
::: chapter-number
References
:::

::: chapter-title
References
:::

Altshuller, G.S. (1984). *Creativity as an Exact Science: The Theory of the Solution of Inventive Problems*. Gordon & Breach.

Chandler, P. & Sweller, J. (1991). \"Cognitive Load Theory and the Format of Instruction.\" *Cognition and Instruction*, 8(4), 293--332.

Chase, W.G. & Simon, H.A. (1973). \"Perception in Chess.\" *Cognitive Psychology*, 4(1), 55--81.

Grunewald, E. (2022). \"Decomposition and Problem-Solving.\" erichgrunewald.com.

Khot, T. (2023). \"Decomposed Prompting: A Modular Approach for Solving Complex Tasks.\" arXiv preprint.

Miller, G.A. (1956). \"The Magical Number Seven, Plus or Minus Two.\" *Psychological Review*, 63, 81--97.

Pólya, G. (1945). *How to Solve It: A New Aspect of Mathematical Method*. Princeton University Press.

Rittel, H.W.J. & Webber, M.M. (1973). \"Dilemmas in a General Theory of Planning.\" *Policy Sciences*, 4(2), 155--169.

Schoenfeld, A.H. (1987). \"Pólya, Problem Solving, and Education.\" *Mathematics Magazine*, 60(5), 283--291.

Simon, H.A. (1962). \"The Architecture of Complexity.\" *Proceedings of the American Philosophical Society*, 106(6), 467--482.

Simon, H.A. (1969/1996). *The Sciences of the Artificial*. 3rd ed. MIT Press.

Song, T. et al. \"Problem Decomposition and Recomposition in Engineering Design.\" *Journal of Technology Education*, 27(2).

Sweller, J. (1988). \"Cognitive Load During Problem Solving.\" *Cognitive Science*, 12(2), 257--285.

Van Regenmortel, M.H.V. (2004). \"Reductionism and Complexity in Molecular Biology.\" *EMBO Reports*, 5(11), 1016--1020.

Yao, S. et al. (2023). \"Tree of Thoughts: Deliberate Problem Solving with Large Language Models.\" arXiv preprint.
:::
:::
:::

------------------------------------------------------------------------

::: page-footer
Loop MMT™ · Multi-Module Theory Problem Decomposition Knowledge Pack · v1 © 2026 Shea Gunther · [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/deed.en){style="color:inherit;"}
:::
