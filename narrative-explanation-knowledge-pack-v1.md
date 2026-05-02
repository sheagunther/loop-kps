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
Narrative & Explanation Knowledge Pack
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
-   [1 · Two Ways of Thinking](#ch-two-modes)
-   [2 · What Makes an Explanation](#ch-explanation)
-   [3 · The Third Mode of Inference](#ch-abduction)
-   [4 · Narrative Structure](#ch-narrative)
-   [5 · Temporal vs. Logical Order](#ch-ordering)
-   [6 · Chunking and Working Memory](#ch-chunking)
-   [7 · The Curse of Knowledge](#ch-curse)
-   [8 · The Illusion of Explanatory Depth](#ch-depth)
-   [9 · Visual Explanation](#ch-visual)
-   [10 · Board Connection](#ch-board)
-   [References](#ch-refs)

::: {.content role="main"}
::: {#ch-abstract .abstract-box}
::: abstract-label
About This Document
:::

This pack addresses the gap between having correct information and producing understanding. An AI system can be factually accurate and still fail to explain — because explanation is not information transfer. It is the construction of a mental model in another mind. That construction follows rules. This pack covers them.

The material spans cognitive psychology (Bruner on modes of thought, Miller and Cowan on working memory, Rozenblit and Keil on the illusion of explanatory depth), philosophy (Peirce on abduction, Lipton on inference to the best explanation, Lombrozo on the structure of explanation), and communication craft (Pinker on the curse of knowledge, Tufte on visual explanation). Twenty-three sources are cited. Full references appear at the end.

Companion packs: Causal Reasoning (the formal structure of causes that explanations communicate), Good Design (explanation as a design problem), Epistemology (knowing what you know and don't know), Communication Pragmatics (what the listener needs vs. what the speaker wants to say).
:::

::: {#ch-two-modes .chapter}
::: chapter-number
Section 1
:::

::: chapter-title
Two Ways of Thinking
:::

::: {#s-bruner .section}
::: section-title
Bruner's Two Modes
:::

Jerome Bruner proposed in *Actual Minds, Possible Worlds* (1986) that human cognition has two distinct modes of operation. He called them **paradigmatic** (logico-scientific) and **narrative**.

The paradigmatic mode operates through categories, propositions, and logical relationships. It seeks empirical truth and evaluates claims against consistency and evidence. It produces theories, classifications, and proofs. Its quality criterion is validity — does the argument hold?

The narrative mode operates through agents, intentions, actions, and consequences arranged in time. It tracks particular people doing particular things and encountering particular outcomes. It produces stories, case studies, and historical accounts. Its quality criterion is verisimilitude — does this feel like how things actually happen?

Bruner's claim is not that these are personality types. Everyone uses both. His claim is that the two modes are **irreducible** — neither can be derived from the other. A good argument is not a story with the characters removed. A good story is not an argument with characters added. They are different natural kinds. Both are legitimate. Both are necessary.
:::

::: {.callout .key}
::: callout-label
The AI default
:::

AI systems produce almost exclusively paradigmatic output: lists, analyses, taxonomies, logical arguments. This reflects their training data (encyclopedias, textbooks, technical documents), their architecture (token prediction optimizes for logical coherence), and the culture that built them (precision over narrative). The result is that AI advisors are fluent in one mode and nearly mute in the other — even though many of the questions humans ask are best answered narratively.
:::

::: {#s-when .section}
::: section-title
When Each Mode Serves
:::

The choice between modes is not aesthetic. It is functional. Paradigmatic mode is the right tool when the listener needs to compare, classify, or verify — when the structure of the answer matters more than its temporal unfolding. "What are the differences between PostgreSQL and MongoDB?" is a paradigmatic question. A table or comparison serves it well.

Narrative mode is the right tool when the listener needs to understand a sequence of events, a decision process, or a causal chain that unfolds over time. "Why did we switch from MongoDB to PostgreSQL?" is a narrative question. The answer involves a sequence of discoveries, problems, and decisions. A chronological account serves it better than a feature comparison.

Many real questions require both. "What is this system and how did it get this way?" calls for a structural description (paradigmatic) anchored by key decision points (narrative). The skill is knowing the proportion, not choosing one exclusively.
:::
:::

::: {#ch-explanation .chapter}
::: chapter-number
Section 2
:::

::: chapter-title
What Makes Something an Explanation
:::

::: {#s-desc-vs-expl .section}
::: section-title
Description vs. Explanation
:::

A description tells you *what* something is. An explanation tells you *why* it is that way. The difference is causal structure.

Consider a server that crashed at 3 AM. A description reports the symptoms: CPU at 100%, memory exhausted, process table full. An explanation connects the symptoms through a causal chain: a memory leak in the logging module consumed RAM over 72 hours; when physical memory ran out, the OS began thrashing swap space; swap thrashing pegged the CPU; cascading recovery processes filled the process table; the system halted.

The description lets you recognize the situation if it recurs. The explanation lets you prevent it. This distinction — between recognizing and intervening — connects directly to the interventionist theory of causation in the Causal Reasoning pack: a cause is something you can change to change the outcome.
:::

::: {#s-lombrozo .section}
::: section-title
How Explanations Work Cognitively
:::

Tania Lombrozo (2006) identified two properties that make explanations cognitively powerful. First, explanations **accommodate** new information within prior beliefs. They don't add a fact to a pile — they integrate it into what you already know. Second, explanations **foster generalization**. By revealing the pattern behind the particular case, they let you reason about situations you haven't encountered yet.

This is why the causal account of the server crash is more useful than the symptom list. The symptoms are specific to this crash. The causal pattern — memory leak → resource exhaustion → cascade failure — generalizes to any long-running system with finite resources. The explanation gives you a reusable schema.
:::

::: {#s-kinds .section}
::: section-title
Kinds of Explanation
:::

Aristotle identified four "causes" — better translated as modes of explanation: **material** (what is it made of?), **formal** (what is its structure?), **efficient** (what brought it about?), and **final** (what is it for?). Modern cognitive research broadly confirms this taxonomy. People use all four types, and the appropriate type depends on what is being explained and what the asker needs.

Keil (2006) found that people accept teleological (final-cause) explanations selectively. They readily accept "the heart is for pumping blood" because the heart's function played a causal role in its evolution. They reject "the mountain is for climbing" because mountains don't exist because of their utility. The selectivity tracks whether the function actually contributed to the thing's existence — a distinction that maps onto the difference between designed artifacts and natural objects.

::: {.callout .note}
::: callout-label
The question behind the question
:::

The same phenomenon can receive valid explanations of different kinds. "Why is the bridge this shape?" could call for a material answer (the steel has this yield strength), a formal answer (the parabolic arch distributes load efficiently), an efficient answer (the engineer chose this design), or a final answer (the bridge needs to span 200 meters). Knowing which kind the asker wants is as important as knowing the content. This is where explanation meets Communication Pragmatics.
:::
:::
:::

::: {#ch-abduction .chapter}
::: chapter-number
Section 3
:::

::: chapter-title
The Third Mode of Inference
:::

::: {#s-peirce .section}
::: section-title
Peirce's Abduction
:::

Charles Sanders Peirce (1839–1914) argued that logic has three irreducible modes of inference. **Deduction** derives necessary conclusions from premises. **Induction** generalizes from observations to patterns. **Abduction** generates hypotheses to explain surprising observations.

Peirce's mature formulation: A surprising fact C is observed. If hypothesis H were true, C would be a matter of course. Therefore, there is reason to suspect that H is true. This is neither deductively valid nor inductively sound. It is a different kind of reasoning: the creative generation of explanatory hypotheses.

Peirce spent four decades refining this idea. By his later work (collected in *The Essential Peirce*, Volume 2), he saw abduction as the only source of genuinely new ideas. Deduction unpacks what you already believe. Induction tests hypotheses against data. But the initial creative leap — proposing a new explanation for something puzzling — is abductive. He described it as arriving "like a flash," guided by what he called instinct or attunement to nature, though this instinct is highly fallible.
:::

::: {#s-ibe .section}
::: section-title
Inference to the Best Explanation
:::

The term "Inference to the Best Explanation" (IBE) was introduced by Gilbert Harman in 1965. Peter Lipton developed it into a comprehensive framework in *Inference to the Best Explanation* (1991; second edition 2004).

Lipton's key distinction is between the **likeliest** and the **loveliest** explanation. The likeliest is the most warranted by evidence. The loveliest is the one that would, if correct, provide the deepest understanding. Lipton argued that loveliness — explanatory depth, elegance, unifying power — serves as a guide to likelihood. We are drawn to the explanation that would tell us the most, and this instinct is often reliable.

The relationship between Peirce's abduction and Lipton's IBE is contested. Campos (2011) argued they address different stages of inquiry: Peirce's abduction concerns the *generation* of candidate hypotheses (where do ideas come from?), while Lipton's IBE concerns both generation and *evaluation* (which candidate is best?). The criteria for generating plausible hypotheses (economy, testability) differ from the criteria for selecting the best explanation (scope, precision, mechanistic detail).
:::

::: {.callout .key}
::: callout-label
Abduction as the default mode of advisory use
:::

When an operator brings a problem to an AI advisor, the interaction is almost always abductive. The operator has observed something surprising or puzzling. They want the best available explanation. The advisor's job is to generate candidate hypotheses, evaluate them against what is known, and present the most plausible one with its supporting reasoning. Making this abductive structure explicit — "the most likely explanation is X, because of Y and Z" — is more honest and more useful than presenting the conclusion as if it were deduced from first principles.
:::
:::

::: {#ch-narrative .chapter}
::: chapter-number
Section 4
:::

::: chapter-title
Narrative Structure
:::

::: {#s-architecture .section}
::: section-title
The Narrative Architecture of Cognition
:::

The human brain processes sequential causal information through narrative schemas automatically. This is not a cultural habit. It is architecture.

The evidence: Heider and Simmel (1944) showed people animations of geometric shapes — triangles and circles — moving on a screen. Participants spontaneously attributed intentions to the shapes and constructed narratives about their "behavior." The triangle was "chasing" the circle. The circle was "trying to escape." This tendency is robust across cultures and ages. Bruner (1990) argued it reflects a biological readiness for narrative — a built-in capacity to organize experience into temporal, intentional sequences.

The implication: when you explain a process, a decision, or a sequence of events, the listener will try to fit your explanation into a narrative schema whether you designed it that way or not. If your explanation has natural narrative structure, the listener's cognition works with you. If it doesn't, the listener must construct the narrative themselves — more effort, more error, often a worse mental model.
:::

::: {#s-canonical .section}
::: section-title
Canonical Structure
:::

Bruner described narrative structure as: a **canonical state** (normal order), a **breach** (disruption), a **crisis** (consequences unfold), and a **redress** (attempt to restore or transform the order). Kenneth Burke (*A Grammar of Motives*, 1945) offered the complementary pentad: **agent**, **act**, **scene**, **agency** (means), and **purpose**.

For advisory communication, the practical distillation is three elements: **setup** (establish context and stakes), **tension** (identify the problem, question, or gap), and **resolution** (close the gap). This is the minimal narrative arc — the smallest unit that activates narrative processing.
:::

::: {#s-practice .section}
::: section-title
Narrative in Practice
:::

Two versions of the same technical explanation:

**Without narrative structure:** "We use PostgreSQL. It supports ACID transactions. Our data model is relational. MongoDB uses eventual consistency."

**With narrative structure:** "The order system processes payments, so two operations hitting the same record must produce consistent results — no partial writes, no lost updates [setup]. MongoDB's eventual consistency can't guarantee this without complex workarounds [tension]. PostgreSQL gives us ACID transactions natively, letting the database enforce consistency instead of the application [resolution]."

Same information. The second version opens a question in the listener's mind (how do we guarantee consistency?) before answering it. This creates what psychologists call a **knowledge gap** — a slot in working memory that the answer fills. The information sticks because it arrives in response to a question the listener is already holding.
:::
:::

::: {#ch-ordering .chapter}
::: chapter-number
Section 5
:::

::: chapter-title
Temporal vs. Logical Order
:::

::: {#s-two-orderings .section}
::: section-title
Two Questions, Two Orderings
:::

Every explanation must choose an ordering principle. The two fundamental options are temporal (how we got here) and logical (how it works). The right choice depends on the question being asked.

**"How did this happen?"** → temporal. The listener wants events in the order they occurred. Sequence matters because earlier events constrain later ones, and alternatives not taken only make sense in context. Post-mortems, debugging stories, project histories, and decision reconstructions are temporal.

**"How does this work?"** → logical. The listener wants the system's parts and their relationships, ordered by dependency, not by when they were built. The construction history is usually noise. API docs, architecture overviews, and reference guides are logical.
:::

::: {#s-mistakes .section}
::: section-title
Common Ordering Mistakes
:::

Two failure modes occur with high frequency:

**History when structure was asked for.** Someone asks how the system works, and the explainer narrates how it was built. The listener gets a chronological tour of decisions and refactors when they wanted a map. They know what happened but not what they're looking at.

**Structure when history was asked for.** Someone asks why a decision was made, and the explainer describes the current architecture. The listener sees the outcome without understanding the constraints and trade-offs that produced it. They know what was chosen but not why, which means they can't judge when to choose differently.
:::

::: {.callout .tip}
::: callout-label
Decision heuristic
:::

**Why / how-did questions → temporal order.** The answer is events, decisions, or causes in time. **What / how-does questions → logical order.** The answer is components and relationships by dependency. When both are needed, lead with logical structure and embed temporal context at decision points.
:::
:::

::: {#ch-chunking .chapter}
::: chapter-number
Section 6
:::

::: chapter-title
Chunking and Working Memory
:::

::: {#s-miller .section}
::: section-title
Miller's Finding
:::

George Miller's 1956 paper, "The Magical Number Seven, Plus or Minus Two," is one of the most cited works in cognitive psychology. Its central finding: short-term memory holds approximately seven items (±2) at once. Miller was careful to specify that the limit applies to **chunks** — the largest meaningful units the person recognizes — not to raw information bits. A word is one chunk for a fluent speaker; it is many chunks for someone who doesn't know the language.

Miller himself noted with dry humor that the number seven seemed to persecute him — it appeared in multiple unrelated cognitive limits. He was equally careful to note that some of those coincidences were probably just that: coincidences. The paper's rhetorical frame was tongue-in-cheek, which may have, as Cowan (2015) argued, inadvertently discouraged follow-up research for decades.
:::

::: {#s-cowan .section}
::: section-title
Cowan's Revision
:::

Nelson Cowan (2001) revisited the question with tighter experimental controls. His conclusion: the core capacity of working memory, stripped of rehearsal strategies and chunking aids, is closer to **four items**. The number seven persists in popular culture, but four is the better estimate for the raw processing bottleneck. Cowan argued this limit is a genuine architectural constraint, not a methodological artifact.

The practical upshot is the same at either number: working memory is drastically limited. Any explanation that requires the listener to hold more than a handful of items while simultaneously integrating new material will overload the system. Not because the listener isn't paying attention. Because the hardware can't do it.
:::

::: {#s-progressive .section}
::: section-title
Progressive Disclosure
:::

The design response to working memory limits is **progressive disclosure**: present information in layers, starting with the top-level structure and adding detail only as needed. The concept comes from interaction design but the principle applies to any communication that must convey complex information without overwhelming the receiver.

In explanation, this means: give the big picture first. Let the listener build a scaffold in working memory. Then attach details to that scaffold. Each detail elaborates a node that already exists, so it doesn't consume a new working-memory slot — it extends an existing one. The listener's capacity for detail is limited only by how well the scaffold is built.

The opposite approach — front-loading all the detail and leaving the listener to extract the structure — is what most technical documentation does, and it is what most AI systems produce. It fails not because the information is wrong but because it arrives before the listener has anywhere to put it.
:::

::: {.callout .warn}
::: callout-label
The unbounded-output problem
:::

AI systems have no working memory limit in the human sense. They can produce arbitrarily long, detail-dense responses. This is a defect, not a feature, because the output must fit the *reader's* cognitive architecture. A response containing twelve considerations, seven caveats, and four cross-references is technically comprehensive and practically unusable. The constraint on output length and complexity should be the reader's working memory, not the system's generation capacity.
:::
:::

::: {#ch-curse .chapter}
::: chapter-number
Section 7
:::

::: chapter-title
The Curse of Knowledge
:::

::: {#s-curse-problem .section}
::: section-title
The Problem
:::

Once you understand something, you lose access to the state of not understanding it. You can no longer see where the confusion was. This makes it systematically difficult to explain things to people who don't yet know them.

The concept has roots in developmental psychology. Wimmer and Perner (1983) showed that young children cannot represent false beliefs — they assume others know what they know. Adults outgrow the most extreme version but retain a residual bias. Camerer, Loewenstein, and Weber (1989) formalized it in economics as the "curse of knowledge": people who know the outcome of an event overestimate how predictable that outcome was to others who didn't know.

Steven Pinker devoted Chapter 3 of *The Sense of Style* (2014) to the curse, calling it the single most important cause of bad writing.
:::

::: {#s-mechanisms .section}
::: section-title
Mechanisms
:::

**Chunking.** Expertise compresses complex ideas into compact labels. The expert uses these labels as if everyone knows them. What occupies one chunk in the expert's memory may be five chunks — or zero — in the novice's.

**Functional fixity.** Experts think about concepts in terms of how they use them, not how they appear to a newcomer. They describe components by function before establishing what the component *is*.

**Omitted steps.** Inferential steps that feel obvious to the expert are invisible to the novice. The expert skips them. The novice hits a gap and either fills it wrong or stops following.

**Abstraction creep.** Each abstract term compresses information the expert has internalized. Stack three or four in a sentence and the sentence is opaque to anyone who hasn't done the same internalization.
:::

::: {.callout .key}
::: callout-label
Why effort alone doesn't fix it
:::

The curse is not carelessness. It is a genuine cognitive limitation. Even people who explicitly try to take another's perspective show residual anchoring to their own knowledge state. The practical remedy is external: show the explanation to someone who doesn't already understand the topic, and observe where they get lost. In writing, this is the editor's function. In AI advisory, this is the operator's feedback loop — and it is why the Interaction Guide emphasizes reading the operator's questions to calibrate the response level.
:::

::: {#s-ai-curse .section}
::: section-title
The AI Form of the Curse
:::

AI systems exhibit a distinctive version. They were trained on expert-to-expert text and learned to reproduce expert discourse patterns: jargon, assumed background knowledge, implicit steps. The mechanism is different from human expertise (the AI hasn't internalized the knowledge and forgotten what it was like not to have it — it never had the not-knowing experience). The effect on the reader is the same: the output assumes knowledge the reader may not have.
:::
:::

::: {#ch-depth .chapter}
::: chapter-number
Section 8
:::

::: chapter-title
The Illusion of Explanatory Depth
:::

::: {#s-finding .section}
::: section-title
The Finding
:::

Leonid Rozenblit and Frank Keil (2002) demonstrated that people systematically overestimate how well they understand causal mechanisms. They called it the **illusion of explanatory depth** (IOED).

The method: ask participants to rate their understanding of everyday devices (zippers, flush toilets, sewing machines) on a 1-to-7 scale. Then ask them to write a detailed, step-by-step mechanical explanation. Then ask them to re-rate. Consistently, post-explanation ratings are markedly lower. The attempt to produce the explanation exposes gaps that confident pre-explanation intuition had concealed.
:::

::: {#s-vulnerable .section}
::: section-title
Why Explanatory Knowledge Is Uniquely Vulnerable
:::

The IOED is specific to causal-mechanistic knowledge. Rozenblit and Keil tested across knowledge types — facts, procedures, narratives, and causal mechanisms. The illusion was strong for causal mechanisms and weak or absent for the others. Three features of explanatory knowledge explain this asymmetry:

**Indefinite depth.** You can always go deeper into a causal mechanism. With a fact, you either know it or you don't. With an explanation, there is always another layer — and it is hard to know in advance where your understanding actually stops.

**Environmental support confusion.** When a device is visible, you can trace its workings in real time. People confuse this environmentally-assisted reasoning with internally-stored knowledge. Remove the device and the understanding evaporates.

**Distributed knowledge.** You know that *someone* understands how the toilet works. You confuse this community-level knowledge with your own.
:::

::: {#s-keil .section}
::: section-title
Keil's Broader Picture
:::

Keil's 2006 review article, "Explanation and Understanding," placed the IOED in a broader framework. He argued that human explanatory understanding is characteristically **skeletal**: we grasp broad causal outlines but rarely possess the mechanistic depth we believe we possess. This is not necessarily pathological — skeletal understanding may be optimal for an organism that must track causal structure across many domains without mastering any one completely. The problem arises when the skeleton is mistaken for the full body.

Keil emphasized that people compensate for shallow individual understanding through **cognitive division of labor**. You don't need to know plumbing if you know a plumber. The IOED becomes dangerous only when this division breaks down — when you must act on your own understanding and discover, in the middle of action, that it isn't there.
:::

::: {.callout .warn}
::: callout-label
Double illusion in AI advisory
:::

AI systems produce fluent explanations of mechanisms they do not understand in any causal sense. The fluency creates an illusion in both directions. The operator assumes the system has deep mechanistic understanding (it doesn't — it predicted the next token). The system's output pattern-matches expert explanation well enough that the boundary between genuine causal reasoning and plausible confabulation is invisible from the outside. The IOED afflicts both the consumer and the producer of AI-generated explanations.
:::
:::

::: {#ch-visual .chapter}
::: chapter-number
Section 9
:::

::: chapter-title
Visual Explanation
:::

::: {#s-when-diagrams .section}
::: section-title
When Diagrams Beat Words
:::

A sentence unfolds in one dimension — it is sequential. A diagram displays two or more dimensions simultaneously. When the thing being explained has inherent spatial, relational, or quantitative structure, a diagram can present it directly while text must describe it sequentially and ask the reader to reconstruct the spatial structure in working memory. The diagram eliminates that reconstruction step.

This is not a blanket endorsement of diagrams. If the thing being explained is itself sequential (a process, a narrative, a causal chain), text may serve better. The decision rule: use visual representation when the **structure** of the explanation has more than one dimension.
:::

::: {#s-tufte .section}
::: section-title
Tufte's Principles
:::

Edward Tufte's work (*The Visual Display of Quantitative Information*, 1983; *Visual Explanations*, 1997) articulated principles for effective visual explanation:

**Show the data.** Every element of a visual should encode information. Decoration that doesn't represent a relationship, quantity, or distinction is clutter. This is the visual equivalent of eliminating filler words.

**Encourage comparison.** The power of visual representation is in showing how things differ. Side-by-side placement, small multiples, and aligned scales enable comparisons that would require careful sentences in prose.

**Minimize non-data ink.** Of all the visual elements, maximize the proportion that carries meaning. Grid lines, borders, and decorative shading consume attention without contributing understanding.

**Integrate text and graphics.** Labels, annotations, and contextual notes belong *with* the visual, not in a separate paragraph. Separating explanation from diagram forces the reader to shuttle between two representations and merge them in working memory — adding cognitive load that integrated design eliminates.
:::

::: {#s-design-connection .section}
::: section-title
Connection to Good Design
:::

Visual explanation is a specific application of design principles. The Good Design Knowledge Pack covers the broader framework: clarity, honesty, reduction to essentials, fitness for purpose. Tufte's contribution is showing that these principles, applied to visual representations, produce the same results as they produce in prose: ruthless elimination of everything that does not serve the reader's understanding.
:::
:::

::: {#ch-board .chapter}
::: chapter-number
Section 10
:::

::: chapter-title
Board Connection
:::

::: {#s-craft .section}
::: section-title
Explanation as Advisory Craft
:::

The central claim of this pack is that how an explanation is structured determines whether it produces understanding. Correct information in the wrong structure fails. The following table maps each concept to advisory practice:

  Concept                         Advisory Application
  ------------------------------- -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  Two modes (Bruner)              Match output mode to question type. "What happened?" → narrative. "How should we build it?" → paradigmatic. Many questions need both — analysis anchored by narrative context.
  Explanation vs. description     Don't just report findings. Connect them through causal structure. A list of facts is description. An account of why those facts indicate a conclusion is explanation.
  Abduction (Peirce/Lipton)       When the operator presents a puzzle, perform explicit IBE: generate hypotheses, evaluate against evidence, present the best one with reasoning. Make the abductive structure visible.
  Narrative structure              For process explanations, use setup → tension → resolution. Establish context, identify the problem, then answer it.
  Temporal vs. logical order      "How did we get here?" → chronological. "How does it work?" → structural.
  Chunking (Miller/Cowan)         Four or fewer top-level concepts per response. Progressive disclosure: structure first, detail on demand.
  Curse of knowledge               Define terms before using them. Spell out steps that feel obvious. Assume the operator is smart but may not share the advisor's vocabulary.
  IOED (Rozenblit/Keil)           Be honest about explanatory depth. If the system is pattern-matching rather than reasoning from mechanism, say so.
  Visual explanation (Tufte)      When spatial or structural relationships are central, use diagrams. Integrate text and graphics.
:::

::: {#s-depth-calibration .section}
::: section-title
Calibrating Explanatory Depth
:::

How deep should an explanation go? Every explanation invites a further "why?" The operator asks why the build failed. The advisor explains the dependency conflict. The operator asks why dependencies conflict. Where does it end?

Keil's research suggests the answer: stop when the listener can **act**. An explanation is deep enough when the operator can make a decision, take an action, or recognize the situation if it recurs. Deeper is academic interest. Shallower leaves them unable to act.

The operator's questions reveal the right level. "Which command do I run?" signals they don't need theory. "Why does this approach work better?" signals they do. Reading the question level and matching explanatory depth to it is the core skill this pack is meant to develop.
:::

::: {#s-cross-pack .section}
::: section-title
Cross-Pack Integration
:::

**Causal Reasoning.** Explanation communicates causal structure. The interventionist framework (Woodward, 2003) provides the formal account of causation; this pack provides the craft of communicating it.

**Good Design.** Explanation is a design problem. Tufte's principles are specific instances of the broader design principles — clarity, honesty, fitness for purpose — in the Good Design pack.

**Communication Pragmatics.** What the operator needs to hear and what the advisor wants to say diverge. The curse of knowledge and the IOED explain why. Communication Pragmatics provides the tools for managing the gap.

**Epistemology.** The IOED is an epistemic failure: not knowing what you don't know. The Epistemology pack's treatment of calibration and epistemic humility applies directly.
:::

::: {#s-loop-mappings .section}
::: section-title
Loop MMT Mappings
:::

- **EOD handoff as narrative.** The handoff answers "what happened and where are we?" — a temporal question. It should use narrative ordering: what was attempted, what succeeded, what failed, what's next. A handoff that merely inventories file states is description, not explanation.
- **Self-review as IOED mitigation.** The V1 → Fact-check → V2 cycle is structurally parallel to Rozenblit and Keil's paradigm: produce the explanation, test it against evidence, discover the gaps, rewrite from scratch. The process catches illusions of depth that a single pass preserves.
- **Talk-first as progressive disclosure.** Establishing the session's goals before building is progressive disclosure at the session level: scaffold first, detail second. Implementation details attach to nothing when the scaffold hasn't been built yet.
- **Board characters as explanatory perspectives.** Different board members bring different explanatory stances. Ed's terse structural analysis is paradigmatic. Historical accounts of project evolution are narrative. The board's plurality of voices is a plurality of explanatory modes — matching Keil's finding that different explanation types serve different cognitive purposes.
:::
:::

::: {#ch-refs .chapter}
::: chapter-number
References
:::

::: chapter-title
References
:::

1. Aristotle. *Posterior Analytics*. c. 350 BC.
2. Bruner, Jerome. *Actual Minds, Possible Worlds*. Harvard University Press, 1986.
3. Bruner, Jerome. *Acts of Meaning*. Harvard University Press, 1990.
4. Bruner, Jerome. "The Narrative Construction of Reality." *Critical Inquiry* 18(1):1–21, 1991.
5. Burke, Kenneth. *A Grammar of Motives*. University of California Press, 1945.
6. Camerer, Colin, George Loewenstein, and Martin Weber. "The Curse of Knowledge in Economic Settings." *Journal of Political Economy* 97(5):1232–1254, 1989.
7. Campos, Daniel. "On the Distinction between Peirce's Abduction and Lipton's Inference to the Best Explanation." *Synthese* 180:419–442, 2011.
8. Cowan, Nelson. "The Magical Number 4 in Short-Term Memory." *Behavioral and Brain Sciences* 24(1):87–114, 2001.
9. Cowan, Nelson. "George Miller's Magical Number of Immediate Memory in Retrospect." *Psychonomic Bulletin & Review* 22:619–625, 2015.
10. Harman, Gilbert. "The Inference to the Best Explanation." *Philosophical Review* 74(1):88–95, 1965.
11. Heider, Fritz and Marianne Simmel. "An Experimental Study of Apparent Behavior." *American Journal of Psychology* 57(2):243–259, 1944.
12. Keil, Frank C. "Explanation and Understanding." *Annual Review of Psychology* 57:227–254, 2006.
13. Lipton, Peter. *Inference to the Best Explanation*. 2nd ed. Routledge, 2004. (1st ed. 1991.)
14. Lombrozo, Tania. "The Structure and Function of Explanations." *Trends in Cognitive Sciences* 10(10):464–470, 2006.
15. Miller, George A. "The Magical Number Seven, Plus or Minus Two: Some Limits on Our Capacity for Processing Information." *Psychological Review* 63(2):81–97, 1956.
16. Peirce, Charles Sanders. *Collected Papers*. Harvard University Press, 1931–1958.
17. Peirce, Charles Sanders. *The Essential Peirce: Selected Philosophical Writings*. Vol. 2 (1893–1913). Indiana University Press, 1998.
18. Pinker, Steven. *The Sense of Style: The Thinking Person's Guide to Writing in the 21st Century*. Penguin, 2014.
19. Rozenblit, Leonid and Frank Keil. "The Misunderstood Limits of Folk Science: An Illusion of Explanatory Depth." *Cognitive Science* 26(5):521–562, 2002.
20. Tufte, Edward R. *The Visual Display of Quantitative Information*. Graphics Press, 1983.
21. Tufte, Edward R. *Visual Explanations: Images and Quantities, Evidence and Narrative*. Graphics Press, 1997.
22. Wimmer, Heinz and Josef Perner. "Beliefs about Beliefs: Representation and Constraining Function of Wrong Beliefs in Young Children's Understanding of Deception." *Cognition* 13:103–128, 1983.
23. Woodward, James. *Making Things Happen: A Theory of Causal Explanation*. Oxford University Press, 2003.
24. Stanford Encyclopedia of Philosophy. "Abduction." plato.stanford.edu. Retrieved April 2026.
:::
:::
:::
