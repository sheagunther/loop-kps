# Attention & Priority — Deciding What to Think About First

**Loop MMT™ · Multi-Module Theory**
**v1 · 9 April 2026**

---

## About This Document

A pack about allocation. Cognitive agents — human or artificial — operate under hard capacity constraints. They cannot process everything, so they must choose what to process first, what to defer, and what to discard. This pack covers bounded rationality (Simon), attention as a scarce resource (Kahneman), triage frameworks adapted from emergency medicine to general reasoning, the Eisenhower matrix and its limits, opportunity cost as an attention concept, information overload, time-horizon conflicts, and the underrated skill of strategic ignorance.

The operational purpose: equip AI advisors to manage their own processing priorities and to help the people they serve manage theirs. An advisor that answers every question with equal depth has no sense of priority. An advisor that flags the unasked question that matters more than the asked one is doing attentional work — and this pack teaches it how.

Pack 11 of 11 in the Basis Pack series. Companion packs: **Decision Theory** (choosing under uncertainty — a special case of prioritizing), **Cognitive Bias & Metacognition** (attention failures produce systematic errors), **Problem Decomposition** (triage is decomposition under time pressure), **Rhetoric & Argumentation** (the structure of a query implies the asker's priority).

---

## Section 1 · Bounded Rationality

Herbert Simon introduced bounded rationality in "A Behavioral Model of Rational Choice" (1955, *Quarterly Journal of Economics*). The core observation: rational agents have finite processing capacity, finite time, and incomplete information. Classical economics assumed agents optimize — they survey all options, compute expected utilities, and select the maximum. Simon argued this is descriptively false and often prescriptively useless. Real agents cannot enumerate all options. The search itself costs resources.

Simon proposed **satisficing** as the realistic alternative. A satisficing agent sets an aspiration level — a threshold of "good enough" — and accepts the first option that meets it. This is not laziness. It is a rational response to the cost of continued search. When the expected marginal benefit of examining one more option is less than the cost of the examination, stopping is the correct move.

The implications for attention are direct. If you cannot process everything, you need a policy for what to process. Bounded rationality does not say "think less." It says "think about what to think about, and then think about that." The meta-cognitive step — choosing where to allocate processing — is itself a decision under bounded rationality. You cannot optimally allocate attention because optimal allocation would require the very processing capacity you are trying to conserve.

> **KEY: Satisficing is not settling.** Satisficing is choosing when to stop searching. The aspiration level can be high. A surgeon satisficing during triage is not doing sloppy work — she is recognizing that spending twenty minutes on a perfect diagnosis of Patient A means Patient B bleeds out. The constraint is real, and respecting it is rational.

This connects directly to the **Decision Theory** pack's treatment of satisficing under uncertainty. That pack addresses the formal choice architecture. This pack addresses the prior question: of all the decisions you could be making right now, which one should you be making?

---

## Section 2 · Attention as a Scarce Resource

Daniel Kahneman's *Attention and Effort* (1973) proposed a capacity model of attention. Attention is not merely selection (choosing what to focus on) but a **limited pool of processing resources** that must be allocated across concurrent demands. When total demand exceeds capacity, performance degrades. This is not a metaphor. It is measurable: dual-task experiments consistently show interference when two tasks compete for the same processing resources.

### Selective Attention and Its Costs

Selective attention — focusing on one stream while ignoring others — is efficient but has a price. The price was demonstrated dramatically by Simons and Chabris (1999) in the "gorillas in our midst" experiment. Participants counting basketball passes failed to notice a person in a gorilla suit walking through the scene. This **inattentional blindness** is not a failure of vision. The gorilla hits the retina. It is a failure of attention — the processing resources are committed elsewhere.

The practical consequence: you miss what you are not looking for. This is true for humans watching basketball and for AI systems parsing queries. An advisor focused on answering the explicit question may miss the implicit crisis. Inattentional blindness is not a bug in the system — it is the cost of having a system that can focus at all.

### The Bottleneck

Earlier models debated where the bottleneck sits. Broadbent (1958) said unattended information gets filtered before you process its meaning. Treisman (1964) said it gets turned down, not off. Kahneman moved past both: the bottleneck is not a gate but a budget. The resource pool is finite. Different tasks draw on it in different amounts. Easy tasks leave spare capacity; hard tasks exhaust it.

For advisory practice, the capacity model matters because it explains why "just pay attention to everything" is not advice — it is a wish. Attention must be allocated, and allocation requires criteria.

---

## Section 3 · Triage

Triage originated in Napoleonic military medicine. Baron Dominique-Jean Larrey, Napoleon's chief surgeon (historical attribution, widely cited but not traceable to a single source), sorted casualties into three groups: those who would survive without treatment, those who would die regardless of treatment, and those for whom treatment would make the difference between life and death. Resources went to the third group. The principle is brutal and correct: treat the saveable, not the sickest.

### Triage as a General Framework

The triage principle generalizes beyond medicine. Any situation with more demands than resources benefits from sorting demands into categories based on the *marginal value of attention*:

| Category | Description | Action |
|---|---|---|
| **Will resolve without you** | Problems that fix themselves, questions that answer themselves with time | Ignore or defer |
| **Cannot be resolved by you** | Problems beyond your capacity, questions requiring information you cannot obtain | Acknowledge limits, refer elsewhere |
| **Your attention changes the outcome** | Problems where your processing makes a measurable difference | Act here first |

The third category is where attention belongs. A caution on the second: classifying a problem as unresolvable is itself a high-stakes judgment. An agent that too readily bins demands into "cannot be resolved" is using triage to justify inaction. The classification should be revisited as conditions change. This is not obvious in practice because the first and second categories often *feel* more urgent. A crisis that will resolve on its own generates more emotional signal than a quiet problem where your input is decisive. Triage requires overriding the urgency signal with a value-of-intervention assessment.

### Information Triage

Gary Klein's research on naturalistic decision-making (*Sources of Power*, 1998) showed that experienced decision-makers do not compare options analytically. They recognize patterns, generate a single plausible course of action, mentally simulate it, and act if the simulation holds. When applied to information processing, this becomes information triage: What can I act on now? What needs more data before action is possible? What is noise — information that will not change any decision I make?

The noise category is the one most people underuse. Identifying noise and discarding it is not carelessness. It is the recognition that processing noise consumes the same resources as processing signal.

---

## Section 4 · The Eisenhower Matrix

The Eisenhower matrix sorts tasks on two dimensions: urgency and importance. This yields four quadrants.

| | Urgent | Not Urgent |
|---|---|---|
| **Important** | Q1: Do immediately | Q2: Schedule and protect |
| **Not Important** | Q3: Delegate or batch | Q4: Eliminate |

The matrix is well-known. Its insight is less well-understood.

### Why Q2 Is Chronically Neglected

Q1 demands attention by definition — it is both urgent and important. Q3 creates urgency signals that mimic Q1. Q4 is ignorable. Q2 is the problem quadrant: important work with no deadline pressure. Strategic planning, relationship maintenance, skill development, preventive maintenance. These tasks matter enormously and generate zero urgency signals. They are perpetually displaced by Q1 and Q3.

The structural problem is that Q2 work, when neglected long enough, becomes Q1 work. The preventive maintenance you skipped becomes the emergency repair. The strategic planning you deferred becomes the reactive scramble. Neglecting Q2 does not save time — it converts important-not-urgent work into important-and-urgent work, which is more expensive to process.

### Limits of the Matrix

The matrix assumes you can cleanly classify tasks on both dimensions. In practice, importance is often unclear (you do not know what matters until later) and urgency is often manufactured (others' urgency is not necessarily yours). The matrix is a sorting heuristic, not a decision algorithm. It works when the classification is honest. It fails when everything is labeled urgent-important, which is the degenerate case that collapses the matrix into a single unsorted pile.

---

## Section 5 · Opportunity Cost and the Value of Ignoring

### Opportunity Cost

Every allocation of attention has an opportunity cost. Choosing to focus on X is simultaneously choosing not to focus on Y. Classical economics makes this explicit for monetary decisions, but it applies with equal force to cognitive resources. The attention spent reading a low-priority email is attention not spent on high-priority analysis. The token budget consumed by a tangential sub-topic is token budget not available for the central question.

Making opportunity cost explicit is itself a priority-setting tool. When the cost of attention is invisible (as it usually is), everything seems worth examining. When the cost is named — "spending twenty minutes on this means not spending twenty minutes on that" — the threshold for "worth examining" rises.

### Strategic Ignorance

Nassim Taleb's *via negativa* principle (*Antifragile*, 2012) argues that what you remove is often more important than what you add. Applied to attention: what you choose not to know can matter more than what you choose to learn. This is **strategic ignorance** — the deliberate decision not to process available information because the processing cost exceeds the expected value.

Strategic ignorance is not anti-intellectual. It is the recognition that information has carrying costs. Every piece of information you take in must be stored, evaluated, and potentially acted upon. If the information will not change any decision you make, processing it is pure cost. A physician who does not read celebrity health blogs is not ignorant — she is efficiently allocating a scarce resource. An AI advisor that does not pursue every tangential thread in a query is doing the same.

> **KEY: The via negativa test.** Before asking "what should I add to my analysis?" ask "what should I remove?" Removing noise improves signal-to-noise ratio faster than adding signal, because removing noise also frees the processing capacity that was being wasted on it.

---

## Section 6 · Information Overload

Eppler and Mengis (2004, *The Information Society*) reviewed the information overload literature across five disciplines and found a consistent pattern: there is a curvilinear relationship between information quantity and decision quality. Decision quality improves as information increases — up to a point. Beyond that point, additional information degrades decisions. The agent cannot process the volume, begins sampling haphazardly, loses track of what has already been evaluated, and defaults to simpler (often worse) heuristics.

Barry Schwartz's *The Paradox of Choice* (2004) documented the downstream effects. More options lead to greater decision difficulty, lower satisfaction with the chosen option, and increased regret. The mechanism is straightforward under bounded rationality: more options means more comparison operations, which means more processing demand, which means either lower quality per comparison or incomplete comparison. Neither outcome is good.

### The Paradox for AI Advisors

An AI advisor with access to vast information faces the same structural problem. Having access to all relevant data does not mean processing all relevant data is optimal. The advisor must select, compress, and present. A response that includes everything relevant but in no priority order has offloaded the overload problem onto the person being advised. Effective advisory requires *curating* information — presenting what matters most, noting what was considered and excluded, and explaining the priority logic.

> **NOTE: Completeness is not a virtue.** A complete answer to a question nobody asked is worse than an incomplete answer to the right question. Completeness is a secondary goal. Relevance and priority ordering are primary.

---

## Section 7 · Time Horizons and Uncertainty

### Hyperbolic Discounting

Humans systematically overweight the present relative to the future. This pattern — **hyperbolic discounting** — has been documented across species and across decision domains (Ainslie, 1992; Frederick, Loewenstein, & O'Donoghue, 2002). A dollar today is preferred over $1.10 tomorrow, but $1.10 in 31 days is preferred over $1.00 in 30 days — even though the trade-off is identical. The near future is disproportionately vivid.

For priority-setting, hyperbolic discounting means short-term priorities systematically crowd out long-term priorities. Q1 displaces Q2 not only because Q1 is urgent but because Q1 is *now* and Q2 is *later*. The discounting is not rational in the economic sense — it produces preference reversals — but it is deeply embedded in human cognition, and AI advisors should expect it in the people they serve.

### Prioritizing Under Uncertainty

When the priority order itself is uncertain — when you don't know what matters most — the question becomes: how do you act? **Robust decision-making** offers one answer. Instead of optimizing for the most likely scenario, choose actions that perform adequately across multiple scenarios. This trades peak performance for resilience. A robust priority list is one that holds even if your initial assessment of importance turns out to be wrong.

Klein (1998) documented how experienced firefighters handle this. They do not compute optimal resource allocation. They construct a mental model of the situation, identify the most time-critical element, act on it, reassess, and repeat. Priority-setting under uncertainty is iterative, not static. The priority list is a living document, updated as information arrives.

> **WARN: The planning fallacy meets priority-setting.** People underestimate how long tasks take (Kahneman & Tversky, 1979). They also underestimate how many tasks they will face. The combination means priority lists are routinely overloaded at creation. An honest priority list accounts for actual capacity, not theoretical capacity.

---

## Section 8 · Board Connection

This pack changes how an AI advisor allocates its own processing and helps the people it serves allocate theirs. The mappings are specific.

**Triage on complex queries.** When a query contains multiple sub-questions, the advisor should not answer them in the order they were asked. It should triage: which sub-question has the highest marginal value of attention? Often the answer buried at the end of a rambling query is the one that matters most. The advisory move is to surface priority order explicitly: "You asked three things. Here's why I'm starting with the third one."

**Flagging the unasked question.** Inattentional blindness applies to query construction. The person asking a question is focused on what they think they need. They may be missing a more important question they haven't thought to ask. The advisor's job is to function as the gorilla detector — attending to what the asker is not attending to. This is a judgment call, not a formula. The test: "If I answer only what was asked, will the person walk away missing something that would have changed their decision?" If yes, flag it.

**Depth vs. breadth.** Bounded rationality applies to responses. A 5,000-word answer that covers eight topics at 625 words each may be worse than a 2,000-word answer that covers three topics thoroughly and notes what was deferred. The advisor must satisfice on coverage to optimize on the topics that matter most. This is the attention version of satisficing from the **Decision Theory** pack — applied not to choosing options but to choosing what to explain.

**Interaction with companion packs.** The **Cognitive Bias & Metacognition** pack identifies attention-driven biases (availability, salience, anchoring). This pack provides the framework for understanding *why* those biases arise: they are consequences of bounded attention interacting with environmental cues. The **Problem Decomposition** pack teaches how to break a problem into parts. This pack teaches which parts to work on first. The **Rhetoric & Argumentation** pack teaches how to read the structure of a query. This pack teaches how to *prioritize* what the structure reveals — the implicit hierarchy in how someone constructs a question is data about their priority. A query that opens with its main concern and ends with "also, by the way..." has told you the priority order. A query that buries the real question after three paragraphs of context has told you the person doesn't yet know their own priority — and surfacing it is the advisory move.

**The meta-move.** This pack is itself a test case. An advisor loaded with this pack should be able to look at its own context window and ask: "Of everything loaded here, what is most relevant to the current query?" Not everything in context deserves equal processing. The pack that matters most for the current query should get the most attention. The rest is available but deferred. An advisor that treats all loaded context as equally relevant has failed the attention test this pack describes.

---

## Key Concepts Reference

| Concept | Definition | Source |
|---|---|---|
| **Bounded rationality** | Agents have finite processing capacity; optimization is usually impossible | Simon (1955) |
| **Satisficing** | Accepting the first option that meets an aspiration level rather than searching for the optimum | Simon (1956) |
| **Capacity model of attention** | Attention is a limited pool of processing resources allocated across demands | Kahneman (1973) |
| **Inattentional blindness** | Failure to perceive visible stimuli when attention is directed elsewhere | Simons & Chabris (1999) |
| **Triage** | Sorting demands by marginal value of intervention to allocate scarce resources | Larrey (c. 1800); Klein (1998) |
| **Eisenhower matrix** | 2×2 classification of tasks by urgency and importance | Covey (1989), attributed to Eisenhower |
| **Opportunity cost** | The value of the best alternative forgone when a choice is made | Standard economics |
| **Via negativa** | Improvement through removal rather than addition | Taleb (2012) |
| **Information overload** | Point at which additional information degrades rather than improves decisions | Eppler & Mengis (2004) |
| **Paradox of choice** | More options lead to worse decisions and lower satisfaction under bounded rationality | Schwartz (2004) |
| **Hyperbolic discounting** | Disproportionate preference for immediate over delayed rewards | Ainslie (1992) |
| **Robust decision-making** | Choosing actions that perform adequately across multiple scenarios | Lempert, Popper, & Bankes (2003) |

---

## References

Ainslie, G. (1992). *Picoeconomics: The Strategic Interaction of Successive Motivational States Within the Person*. Cambridge University Press.

Broadbent, D. E. (1958). *Perception and Communication*. Pergamon Press.

Covey, S. R. (1989). *The 7 Habits of Highly Effective People*. Free Press.

Eppler, M. J., & Mengis, J. (2004). The concept of information overload: A review of literature from organization science, accounting, marketing, MIS, and related disciplines. *The Information Society*, 20(5), 325–344.

Frederick, S., Loewenstein, G., & O'Donoghue, T. (2002). Time discounting and time preference: A critical review. *Journal of Economic Literature*, 40(2), 351–401.

Kahneman, D. (1973). *Attention and Effort*. Prentice-Hall.

Kahneman, D., & Tversky, A. (1979). Prospect theory: An analysis of decision under risk. *Econometrica*, 47(2), 263–291.

Klein, G. (1998). *Sources of Power: How People Make Decisions*. MIT Press.

Lempert, R. J., Popper, S. W., & Bankes, S. C. (2003). *Shaping the Next One Hundred Years: New Methods for Quantitative, Long-Term Policy Analysis*. RAND Corporation.

Schwartz, B. (2004). *The Paradox of Choice: Why More Is Less*. Ecco Press.

Simon, H. A. (1955). A behavioral model of rational choice. *Quarterly Journal of Economics*, 69(1), 99–118.

Simon, H. A. (1956). Rational choice and the structure of the environment. *Psychological Review*, 63(2), 129–138.

Simons, D. J., & Chabris, C. F. (1999). Gorillas in our midst: Sustained inattentional blindness for dynamic events. *Perception*, 28(9), 1059–1074.

Taleb, N. N. (2012). *Antifragile: Things That Gain from Disorder*. Random House.

Treisman, A. M. (1964). Selective attention in man. *British Medical Bulletin*, 20(1), 12–16.
