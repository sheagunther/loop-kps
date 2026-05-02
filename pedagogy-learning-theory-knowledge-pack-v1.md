# Pedagogy & Learning Theory Knowledge Pack

**Loop MMT™ · Multi-Module Theory**
**v1 · 11 April 2026**

---

## About This Document

How people learn — and how to help them learn better. Built for AI advisory systems that function as instructional artifacts whether they call themselves that or not. Every Knowledge Pack teaches. Every Cadence session is a learning episode. Every Board Connection section is a transfer exercise. This pack makes the instructional design principles behind those artifacts explicit.

Twelve topics, one thread: working memory is small, and everything in instructional design is a strategy for dealing with that fact. Cognitive load theory names the constraint. The zone of proximal development calibrates instruction to it. Retrieval practice and desirable difficulties exploit it. Transfer of learning is what happens when instruction succeeds beyond its original context. Constructivism explains how knowledge restructures itself. Expert-novice research reveals why surface and structure are different worlds. Bloom's taxonomy classifies what learners are doing. Multimedia learning governs how information should be presented. Motivation keeps learners engaged. Threshold concepts mark the irreversible transformations.

Self-referential by design: this pack should exemplify the principles it describes. Where it violates them, it has failed its own test. Pack 6 of 12, Basis Pack expansion series. Founded on Sweller (1988), Vygotsky (1978), Roediger & Karpicke (2006), Chi, Feltovich & Glaser (1981), Mayer (2009), Meyer & Land (2003), Bjork (1994), Anderson & Krathwohl (2001), Ambrose et al. (2010), and Bransford, Brown & Cocking (2000).

---

## Section 1 · The Bottleneck: Cognitive Load Theory

Working memory is small. George Miller (1956) estimated its capacity at 7 ± 2 items. Nelson Cowan (2001) revised this to approximately 4 chunks. The exact number matters less than the implication: at any given moment, a learner can actively process only a handful of information elements. Every instructional decision is ultimately a decision about how to spend those few slots.

John Sweller formalized this constraint as cognitive load theory (CLT) in 1988 (*Cognitive Science*, 12(2), 257–285). The theory identifies three types of cognitive load that compete for the same limited working memory:

**Intrinsic cognitive load** is the inherent difficulty of the material. It depends on two factors: element interactivity — how many elements must be processed simultaneously and how they relate to each other — and the learner's prior knowledge. Learning unrelated vocabulary items has low element interactivity (each word is independent). Learning to balance chemical equations has high element interactivity (coefficients, subscripts, conservation rules must all be coordinated). Crucially, intrinsic load cannot be reduced by better instruction. It changes only if the task changes or the learner's expertise increases — because expertise allows chunking of multiple elements into single schemas.

**Extraneous cognitive load** is imposed by poor instructional design. Anything that forces the learner to process material that does not contribute to understanding — confusing layouts, irrelevant decorations, information split across separated sources that must be mentally integrated, redundant presentation of the same content in multiple formats. This is the variable under the designer's control. Reduce it, and working memory is freed for productive processing.

**Germane cognitive load** is the working memory devoted to building and automating schemas — the organized knowledge structures in long-term memory. This is the processing that produces actual learning.

> **KEY: The total must fit.** Working memory capacity is fixed for a given learner at a given moment. If intrinsic load is high (difficult material for this learner), extraneous load must be aggressively reduced, or there is no capacity left for schema construction. The designer's job: minimize extraneous load to maximize the proportion of working memory available for germane processing.

Sweller initially proposed that the three types are additive (Sweller, van Merriënboer & Paas, 1998). In 2010, he offered a simpler reformulation: germane load is not a separate independent source but rather describes the working memory resources devoted to *dealing with* intrinsic load. The framework reduces to two primary types — intrinsic and extraneous — with the goal of maximizing the share devoted to intrinsic processing.

### CLT Effects

| Effect | Mechanism | Instructional Implication |
|---|---|---|
| **Split-attention** | Learners must mentally integrate physically separated information sources (diagram on one page, explanation on another) | Place explanatory text adjacent to the relevant part of the graphic |
| **Redundancy** | Same information in multiple unnecessary formats (narrating text already on screen) adds load without adding learning | Eliminate redundant channels; choose the most efficient modality |
| **Worked-example** | Problem-solving imposes heavy search-based load on novices; studying worked solutions is more efficient | Replace some practice problems with worked examples early in learning |
| **Expertise reversal** | Techniques optimal for novices (worked examples, heavy guidance) become extraneous load for experts, whose existing schemas render the guidance redundant | Fade guidance as expertise develops; what helps a beginner burdens an expert |

The expertise reversal effect is the most consequential for adaptive systems. It means there is no universally optimal instructional design — what works depends on how much the learner already knows. A Knowledge Pack loaded into an expert conversation imposes different demands than the same pack loaded for a novice. This has direct implications for Loop Signal's eventual audience: if packs serve varied expertise levels, they may need adaptive depth.

---

## Section 2 · The Gap: Zone of Proximal Development

Lev Vygotsky (1896–1934) introduced the zone of proximal development in *Mind in Society* (1978). The ZPD is the distance between what a learner can accomplish independently and what they can accomplish with guidance from a more knowledgeable other (MKO).

Three claims underpin the concept:

**Learning precedes development.** Guided interaction with an MKO is what *produces* cognitive growth — not a reward for having already reached a stage. Instruction should target the leading edge of capability, not the trailing edge.

**Higher cognition originates socially.** Knowledge begins as external dialogue and shared problem-solving before being internalized as individual capacity.

**The MKO need not be a teacher.** It can be a peer, a parent, or an AI system engaged in structured interaction with a learner.

### Scaffolding and Fading

Vygotsky never used the term "scaffolding." Wood, Bruner, and Ross introduced it in 1976 ("The Role of Tutoring in Problem Solving," *Journal of Child Psychology and Psychiatry*, 17(2), 89–100). They defined it as temporary support enabling a learner to accomplish a task beyond their current independent capability.

The mechanism has three phases: high support (modeling and explicit guidance), shared practice (learner attempts with assistance), and independent practice (learner performs without support). The critical operation is **fading** — systematic withdrawal of scaffolding as competence grows.

> **WARN: Scaffolds that don't fade are crutches.** A 2024 meta-analysis (Belland et al.) found scaffolding programs with explicit fading protocols produced effect sizes of d = 0.71, versus d = 0.32 for programs where scaffolds remained constant. Fisher and Frey (2021) observe that most classrooms remain stuck in the shared-practice phase permanently. If a learner can only perform with the support in place, the scaffolding has become a dependency.

The ZPD is difficult to measure — it is dynamic, context-dependent, and varies by learner, task, and moment. For standardized settings, this is a limitation. For one-on-one AI interaction, where support can be continuously adaptive, the ZPD's dynamism is an asset.

---

## Section 3 · The Paradox: Retrieval Practice and Desirable Difficulties

### The Forgetting Curve

Hermann Ebbinghaus (1885) was the first to measure forgetting experimentally. Using himself as the subject and nonsense syllables as the material, he established that memory decays rapidly after initial learning — steeply at first, then leveling off. His actual measure was *savings* (the reduction in time needed to relearn material), not direct recall percentage. The commonly cited approximation — roughly half of newly learned information lost within the first hour, roughly 70% within 24 hours — captures the shape of the curve but simplifies his data. A 2015 replication (Murre & Dros, *PLOS ONE*) confirmed that the general pattern holds.

The forgetting curve is the problem. Everything else in this section is about making forgetting work *for* the learner instead of against them.

### The Testing Effect

Roediger and Karpicke (2006b, *Psychological Science*, 17(3), 249–255) demonstrated the core paradox. Students read prose passages under three conditions: four study periods (SSSS), three study periods plus one recall test (SSST), or one study period plus three recall tests (STTT).

At 5 minutes: SSSS performed best. Repeated study won.
At 1 week: STTT dramatically outperformed the others. The repeated-study group forgot 56% of what they had recalled at 5 minutes. The repeated-test group forgot only 13%.

> **KEY: The strategy that feels worse wins.** Students in the re-study condition reported higher confidence in their ability to remember the material (Karpicke, Butler & Roediger, 2009). They were wrong. Fluent re-reading creates an *illusion of learning* — the material feels familiar, and the brain misinterprets familiarity as mastery. Retrieval practice feels effortful and uncertain, which feels like failure. Learners systematically choose the strategy that produces worse long-term results because it produces better short-term feelings.

The leading mechanistic account: retrieval creates more elaborated memory traces and diversified retrieval routes, making future access more reliable (Roediger & Karpicke, 2006a). More effortful retrieval produces greater benefit — connecting to Bjork's desirable difficulties framework.

### Spacing and Interleaving

The **spacing effect** — distributing practice over time outperforms massing (cramming) — is among the most robust findings in experimental psychology. Documented by Ebbinghaus in the 1880s, confirmed thousands of times since across materials, learner types, and time scales (Cepeda et al., 2006).

**Interleaving** — practicing different problem types in mixed order rather than in blocks of the same type — produces similar benefits. It feels harder and generates more errors during practice, but produces superior later performance (Kornell & Bjork, 2008; Rohrer, 2012). The mechanism: interleaving forces learners to discriminate *which* strategy applies to *which* problem, rather than simply executing a known strategy repeatedly.

### Desirable Difficulties

Robert Bjork (1994, in Metcalfe & Shimamura, Eds., *Metacognition: Knowing About Knowing*, pp. 185–205, MIT Press) named the pattern: conditions that appear to slow acquisition often produce superior long-term retention and transfer.

| Difficulty | Mechanism | Boundary Condition |
|---|---|---|
| **Spacing** | Forces effortful retrieval at each return to material | Too much spacing causes complete forgetting before the next encounter |
| **Interleaving** | Forces discrimination between strategies; prevents false fluency from blocked repetition | Requires sufficient initial learning of each type to make discrimination possible |
| **Retrieval practice** | Strengthens memory through active reconstruction rather than passive re-exposure | Must achieve some retrieval success — complete failure teaches nothing |
| **Varying conditions** | Promotes flexible encoding across contexts; prevents context-dependent learning | Variation must be relevant; random noise is undesirable difficulty |

The Bjork and Bjork (1992) Theory of Disuse explains why through two separate strength measures. **Storage strength** — how permanently a memory is encoded — only increases. **Retrieval strength** — how easily accessible a memory is right now — fluctuates. High retrieval strength creates the illusion of learning: fluency feels like mastery. Desirable difficulties work by temporarily reducing retrieval strength, forcing more effortful processing on the next encounter, which increases storage strength.

The word "desirable" carries the load. A difficulty is only desirable if the learner has sufficient background to respond to it successfully. Without prerequisite knowledge, spacing and interleaving don't produce productive struggle — they produce frustration. The difficulty must fall within the learner's zone of proximal development.

---

## Section 4 · The Bridge: Transfer of Learning

Transfer — applying knowledge learned in one context to a different one — is the purpose of learning. Knowledge that can only be recalled in the exact situation where it was acquired is trivia. Knowledge that reshapes how a person handles novel problems is education. Transfer is the bridge between them — and it is far harder to cross than most instructional design assumes.

**Near transfer** occurs when source and application contexts share surface features — solving textbook quadratics, then solving exam quadratics. **Far transfer** occurs across domains with different surface features but shared deep structure — applying negotiation principles learned from business cases to a family dispute.

### Structure-Mapping Theory

Dedre Gentner (1983, *Cognitive Science*, 7, 155–170) proposed that analogies work through shared *relational structure*, not shared surface features. Saying the atom is like the solar system is not about shape — it is about parallel causal relationships (central body, orbiting bodies, binding force). The systematicity principle: analogies with coherent causal systems of shared relations are more useful and more preferred than those with isolated shared features.

> **PHI: The retrieval paradox.** Holyoak and Koh (1987, *Memory & Cognition*, 15(4), 332–340) revealed a dissociation that explains why spontaneous transfer is rare. Surface features dominate *retrieval* — people search memory for things that look alike. Structural features determine *applicability* — whether an analogy actually works. The result: we reliably find the wrong analog (surface-similar, structurally irrelevant) and miss the right one (structurally parallel, surface-different). This is the same surface/structure distinction that Chi, Feltovich, and Glaser documented in expert-novice physics sorting (Section 6). Experts escape the trap because they encode by deep structure rather than surface appearance.

**Analogical encoding** (Gentner, Loewenstein & Thompson, 2003, *Journal of Educational Psychology*, 95(2), 393–408) offers a remedy. When learners compare two structurally analogous cases and describe their similarities — rather than studying each case in isolation — they abstract the shared schema. Graduate students who compared two negotiation cases were nearly three times more likely to transfer the strategy to a subsequent live negotiation than students who studied the same two cases separately.

The implication: transfer must be engineered. Teaching for transfer requires presenting multiple examples with shared deep structure but different surface features, and explicitly guiding learners to map the structural parallels. Merely presenting good examples and hoping the learner notices the connections is insufficient.

---

## Section 5 · The Model: Constructivism and Conceptual Change

Jean Piaget (1896–1980) established the constructivist premise: learning is not information absorption. It is model-building. Learners construct mental models — schemas — by interpreting new experience through existing understanding.

Two mechanisms drive the process. **Assimilation** fits new information into existing schemas without structural change — a child who knows "dog" successfully categorizes a new breed. **Accommodation** modifies schemas when assimilation fails — a child who calls all four-legged animals "dogs" must restructure upon encountering horses.

The critical insight: **misconceptions are not gaps. They are wrong models.** A student who believes heavier objects fall faster has a working model of gravity. It is incorrect, but it is coherent, explains everyday experience (feathers *do* fall slower than hammers in air), and makes predictions the student cares about. Presenting the correct answer does not automatically displace it.

Posner, Strike, Hewson, and Gertzog (1982, *Science Education*, 66(2), 211–227) identified four conditions for conceptual change: the learner must (1) become dissatisfied with the existing model, (2) encounter an intelligible alternative, (3) find the alternative plausible, and (4) see the new model as more fruitful. All four must be met. Simply stating the correct answer satisfies at most condition 2.

> **NOTE: Misconceptions are structurally load-bearing.** They connect to other beliefs, predict experience, and organize perception. Removing a misconception without providing a replacement leaves the learner with no model — which is cognitively worse than a wrong one. This is why direct correction fails: it creates a gap where the learner needs a structure.

---

## Section 6 · The Shift: Expert-Novice Differences

Chi, Feltovich, and Glaser (1981, *Cognitive Science*, 5(2), 121–152) asked physics experts and novices to sort problems into categories. Novices sorted by surface features: "inclined plane problems," "rotational things," "blocks on surfaces." Experts sorted by underlying principles: "conservation of energy," "Newton's second law."

This is the surface/structure distinction from Section 4, observed in how knowledge is *organized* rather than how it *transfers*. Experts have restructured their knowledge around deep principles. Novices index by appearance. The expert's physics knowledge is not simply *more* — it is differently *organized*, and the organization itself enables recognition of structural similarity across superficially different problems.

The mechanism is **chunking** (Chase & Simon, 1973, *Cognitive Psychology*, 4(1), 55–81). Chess grandmasters reconstructed meaningful board positions from brief exposure far better than novices — but the advantage disappeared with randomly placed pieces. Experts don't have better memory in general. They have richly structured schemas that organize domain-specific information into large meaningful units. A grandmaster sees not 25 pieces but 5–6 familiar configurations, each carrying strategic implications.

### The Dreyfus Model

Stuart and Hubert Dreyfus (1986, *Mind Over Machine*) described five stages of skill acquisition:

| Stage | Characteristic | Instructional Need |
|---|---|---|
| **Novice** | Follows context-free rules rigidly; cannot distinguish relevant from irrelevant features | Clear rules, worked examples, explicit guidance |
| **Advanced Beginner** | Recognizes situational elements from experience; begins to see patterns | Real cases alongside rules; limited independent practice |
| **Competent** | Plans deliberately; prioritizes; copes with complexity; takes responsibility | Complex problems with multiple valid approaches; reduced hand-holding |
| **Proficient** | Sees situations holistically; detects anomalies intuitively; still deliberates on action | Cases that challenge pattern recognition; reflective practice |
| **Expert** | Acts from deep experience and intuition; deliberation reserved for genuinely novel situations | Exposure to genuine novelty; metacognitive examination of automatized processes |

Two implications merit emphasis. First, expertise is domain-specific. A chess grandmaster's chunking advantage disappears outside chess. Expertise does not transfer across domains because the schemas are domain-bound. This constrains the popular notion of "general problem-solving skill."

Second, **the curse of knowledge**: experts are often poor teachers because they have forgotten what it is like not to know. The chunked, automatized patterns that make expert performance effortless make expert instruction opaque — the expert skips steps they no longer consciously perform.

---

## Section 7 · The Ladder: Bloom's Taxonomy

Benjamin Bloom and colleagues published the original *Taxonomy of Educational Objectives* in 1956: Knowledge → Comprehension → Application → Analysis → Synthesis → Evaluation.

In 2001, Lorin Anderson (a former student of Bloom) and David Krathwohl (an original co-author) published a major revision. Two structural changes: nouns became action verbs (reflecting that learning is process, not state), and the top two levels swapped (creating requires evaluative judgment, making it the more complex operation).

| Level | Definition | Action Verbs | Example |
|---|---|---|---|
| **Remember** | Retrieve knowledge from long-term memory | List, define, recall, name | Name the three types of cognitive load |
| **Understand** | Construct meaning from information | Explain, summarize, classify | Explain why re-reading feels effective but isn't |
| **Apply** | Use a procedure in a given situation | Implement, execute, demonstrate | Apply the spacing effect to design a study schedule |
| **Analyze** | Break into components; determine relationships | Differentiate, organize, attribute | Analyze which CLT effects are present in a poorly designed slide |
| **Evaluate** | Make judgments based on criteria | Check, critique, judge | Evaluate whether a scaffolding program includes proper fading |
| **Create** | Produce something new by combining elements | Generate, plan, design | Design a Knowledge Pack that exemplifies cognitive load principles |

The 2001 revision added a **Knowledge Dimension**: Factual (terms, details), Conceptual (categories, principles), Procedural (how to do something), and Metacognitive (awareness of one's own cognition). Any cognitive process can be applied to any knowledge type, creating a two-dimensional matrix.

The taxonomy is not strictly hierarchical in practice — real tasks engage multiple levels simultaneously, and creating does not require having mastered all lower levels first. Its value is diagnostic: it makes visible the gap between training that tests at lower cognitive levels and jobs that demand higher ones.

---

## Section 8 · The Signal: Multimedia Learning and Assessment

### Mayer's Cognitive Theory of Multimedia Learning

Richard Mayer (2009, *Multimedia Learning*, 2nd ed., Cambridge University Press) built a theory of instruction from words and pictures, grounded in three assumptions:

1. **Dual channels.** Humans process visual/pictorial and auditory/verbal information through separate channels (cf. Paivio, 1986).
2. **Limited capacity.** Each channel processes limited information at any moment.
3. **Active processing.** Meaningful learning requires selecting, organizing, and integrating information — not passive absorption.

These connect directly to cognitive load theory. The practical question: how should materials be designed to respect limited capacity across two channels?

Mayer's principles, by function:

**Reducing extraneous processing:** Coherence (exclude irrelevant material; median d = 0.86 across 23 tests), Signaling (add cues highlighting key material), Redundancy (graphics + narration > graphics + narration + on-screen text), Spatial contiguity (text near corresponding graphic), Temporal contiguity (words and graphics simultaneously).

**Managing essential processing:** Segmenting (learner-paced segments), Pre-training (teach key concepts first), Modality (graphics + spoken narration distributes load across channels).

**Fostering generative processing:** Multimedia (words + pictures > words alone), Personalization (conversational > formal style), Voice (friendly human > machine), Image (speaker's image does not necessarily help).

> **TIP: Seductive details — when engagement harms learning.** Mayer's term for interesting but irrelevant material added to make content more engaging. The problem: learners sometimes remember the seductive detail *instead of* the essential content. The very material designed to increase engagement competes with core content for limited working memory. This creates a direct tension with FWW(C) in Loop MMT — fun and whimsy must be *germane* rather than *extraneous*, or they damage learning. The engagement ceiling and the failure floor are not independent axes; they can collide.

### Formative vs. Summative Assessment

**Summative assessment** evaluates achievement at the end — exams, certifications. It answers: what has been learned?

**Formative assessment** occurs during learning to adjust instruction. It answers: what should we do next? Black and Wiliam (1998, "Inside the Black Box," *Phi Delta Kappan*) found formative assessment interventions produced effect sizes of 0.4–0.7.

The connection to retrieval practice is direct: frequent low-stakes tests serve simultaneously as formative assessment *and* as retrieval practice — providing diagnostic information about gaps while strengthening retention. This dual function makes testing-as-learning among the most efficient instructional strategies available.

---

## Section 9 · The Drive: Motivation and Self-Regulation

### Self-Determination Theory

Edward Deci and Richard Ryan (1985; 2000) identified three basic psychological needs:

**Autonomy** — feeling volitional rather than controlled. Learners who feel they choose to learn engage more deeply.

**Competence** — feeling effective. Challenges within the ZPD satisfy this need; challenges far beyond or below it undermine it.

**Relatedness** — feeling connected. Social learning satisfies this; isolated learning can undermine it.

Motivation ranges from fully extrinsic (external reward/punishment) through progressively internalized forms (accepted value, identified purpose, integrated identity) to fully intrinsic (the activity itself is satisfying). The instructional goal is not to eliminate extrinsic motivation but to support its internalization.

### Flow

Csikszentmihalyi (1990, *Flow*) described a state of complete absorption where challenge and skill are well-matched. Too much challenge produces anxiety. Too little produces boredom. The "flow channel" sits between them.

### Growth Mindset — and Its Limits

Dweck (2006) proposed that implicit theories about ability matter: a **fixed mindset** treats ability as innate (failure = permanent limitation), while a **growth mindset** treats ability as developable (failure = opportunity).

> **WARN: Growth mindset is real but smaller than claimed.** Yeager et al. (2019, *Nature*, 573, 364–369) found significant but modest effects, primarily for lower-achieving students. The concept is widely oversimplified in practice. The mechanism is about *response to setback*, not about willpower or positive thinking. Dweck herself has cautioned against misapplication.

### Self-Regulated Learning

Zimmerman (2002) described self-regulated learning as three cyclical phases: **forethought** (planning, goal-setting, strategy selection), **performance** (self-monitoring, strategy use), and **self-reflection** (self-evaluation, attribution, adaptive adjustment). Expert learners manage all three. Novices often skip forethought and self-reflection, moving straight to performance without planning and away from it without evaluating.

Self-regulation is the meta-skill. A learner who knows about retrieval practice but does not monitor whether they use it gains nothing from the knowledge. Metacognition governs everything.

---

## Section 10 · The Portal: Threshold Concepts

Meyer and Land (2003, in Rust (Ed.), *Improving Student Learning — Ten Years On*, OCSLD, Oxford) identified concepts within disciplines that fundamentally transform understanding. A threshold concept is not just difficult — it is a *portal*. Once crossed, it opens a previously inaccessible way of seeing that restructures the learner's entire relationship to the subject.

Five characteristics:

**Transformative.** Crossing the threshold produces a significant shift in perception — not just knowing more but seeing differently.

**Probably irreversible.** The transformation is unlikely to be forgotten. You cannot un-see what a threshold concept reveals.

**Integrative.** The concept exposes previously hidden interrelatedness — scattered facts that seemed unconnected suddenly organize into coherent pattern.

**Possibly bounded.** Threshold concepts may border other thresholds, defining disciplinary territories.

**Potentially troublesome.** The knowledge is often counter-intuitive, alien, or conflicts with existing understanding — connecting to the constructivist account of conceptual change (Section 5).

> **PHI: Liminality — why real learning often feels like confusion.** Meyer and Land (2005, *Higher Education*, 49, 373–388) developed the concept of liminality for the transitional state learners enter when crossing a threshold. The old understanding no longer works but the new one has not formed. The learner is between worlds — disoriented, sometimes threatened in their identity. Learners in liminal states may resort to **mimicry**: using the vocabulary of understanding without having achieved the transformation. This is structurally parallel to Loop MMT's finding that partial context produces confident confabulation — vocabulary without understanding generates output that sounds correct but has not crossed the threshold.

---

## Section 11 · Board Connection: How the Methodology Already Teaches

### Cognitive Load Theory Governs Document Design

KP section length, callout boxes, reference tables, punchline-first structure, and the "no filler" writing standard are extraneous load management. The L21 format's three-skin CSS is a coherence choice (readers select the presentation that minimizes their personal extraneous load). SNR (Signal-to-Noise Ratio) — one of the Four Corners — is cognitive load theory under a different name.

The expertise reversal effect applies directly: if Loop Signal eventually serves varied expertise levels, pack design may need adaptive depth. What scaffolds a novice burdens an expert. The Dreyfus model could structure the adaptation — different presentation for different stages.

### ZPD Implies Calibration

The KP Index is ZPD assessment: checking what an instance already knows (loaded packs) and identifying what it needs (relevant unloaded packs). The research instance startup handoff is explicit scaffolding — temporary support for a fresh instance that becomes unnecessary once reconstruction is complete. Experienced operators demonstrate fading naturally: early sessions required heavy guidance; by Session 43, Shea issues single-word commands because the documents carry the scaffold.

### Transfer Is the Point of Board Connection

Every Board Connection section performs analogical encoding — comparing two structurally parallel domains (the pack's subject and the methodology's practices) to extract transferable principles. Gentner's research predicts that this comparison should produce better transfer than reading the pack and hoping connections are noticed spontaneously.

The danger is surface-level Board Connections that gesture at relevance without demonstrating structural mapping. "This relates to Loop MMT because..." followed by vague assertions is mimicry (Meyer & Land's term). A good Board Connection identifies specific structural parallels: *this* mechanism maps to *this* practice because they share *this* relational structure.

### Threshold Concepts in the Methodology

Four concepts within Loop MMT appear to function as thresholds — transformative, irreversible, integrative, troublesome:

1. **"The documents are the continuity."** Understanding that an AI system's memory is entirely constituted by loaded documents — not by persistent internal state — transforms session management, document quality, and handoff discipline. Irreversible once grasped.

2. **"Fix by Design, not by behavior."** The shift from "remember to do X" to "make not-doing-X structurally impossible" reorganizes all subsequent design thinking. Every FBD control flows from this threshold.

3. **"Partial context produces higher-confidence confabulation than no context."** This violates the intuition that more information is always better. It integrates disconnected observations about AI behavior. Once understood, you cannot assume "give the instance some documents" is safe.

4. **"The methodology that produced the code is the product."** This transforms the relationship between process and output. The code is a byproduct; the methodology is the artifact being built.

### The Spaced Repetition Asymmetry

How does spaced repetition apply to an AI that reads entire packs in one load? It doesn't — for the AI. An instance processes a KP in a single pass with no forgetting curve within a session.

But it applies powerfully to the human operator. Shea reads outputs across sessions, days, and weeks. Each session revisits core methodology principles through different problems — interleaved retrieval practice. The operator's understanding deepens not because documents get longer but because each document re-engages the same principles in new contexts.

For Loop Signal users: the persona loads once, but the human reads across sessions. Pack design should account for the human's forgetting curve, not the AI's non-existent one.

### Connections to Adjacent Packs

**Attention & Priority:** Attention is the selection mechanism determining what enters working memory — the gate before the bottleneck. CLT assumes attention has been directed; it says nothing about how to capture it.

**Cognitive Bias & Metacognition:** The illusion of learning (choosing ineffective strategies because they feel effective) is a metacognitive failure structurally identical to the overconfidence that pack describes. Self-regulated learning (Zimmerman) is the corrective.

**Communication Pragmatics:** Mayer's personalization principle connects to pragmatic theory about conversational context and comprehension. The signaling principle maps to Grice's maxim of manner.

---

## References

- Ambrose, S. A., Bridges, M. W., DiPietro, M., Lovett, M. C. & Norman, M. K. (2010). *How Learning Works*. Jossey-Bass.
- Anderson, L. W. & Krathwohl, D. R. (Eds.) (2001). *A Taxonomy for Learning, Teaching, and Assessing*. Longman.
- Bjork, R. A. (1994). Memory and metamemory considerations in the training of human beings. In J. Metcalfe & A. Shimamura (Eds.), *Metacognition: Knowing About Knowing* (pp. 185–205). MIT Press.
- Bjork, R. A. & Bjork, E. L. (1992). A new theory of disuse. In A. Healy et al. (Eds.), *From Learning Processes to Cognitive Processes* (Vol. 2, pp. 35–67). Erlbaum.
- Bjork, E. L. & Bjork, R. A. (2011). Making things hard on yourself, but in a good way. In M. A. Gernsbacher et al. (Eds.), *Psychology and the Real World* (pp. 56–64). Worth.
- Black, P. & Wiliam, D. (1998). Inside the Black Box. *Phi Delta Kappan*, 80(2), 139–148.
- Bloom, B. S. (Ed.) (1956). *Taxonomy of Educational Objectives: Handbook I*. David McKay.
- Bransford, J. D., Brown, A. L. & Cocking, R. R. (Eds.) (2000). *How People Learn* (Expanded ed.). National Academy Press.
- Cepeda, N. J., Pashler, H., Vul, E., Wixted, J. T. & Rohrer, D. (2006). Distributed Practice in Verbal Recall Tasks. *Review of Educational Research*, 76(3), 354–380.
- Chase, W. G. & Simon, H. A. (1973). Perception in Chess. *Cognitive Psychology*, 4(1), 55–81.
- Chi, M. T. H., Feltovich, P. J. & Glaser, R. (1981). Categorization and Representation of Physics Problems by Experts and Novices. *Cognitive Science*, 5(2), 121–152.
- Cowan, N. (2001). The Magical Number 4 in Short-term Memory. *Behavioral and Brain Sciences*, 24(1), 87–114.
- Csikszentmihalyi, M. (1990). *Flow*. Harper & Row.
- Deci, E. L. & Ryan, R. M. (1985). *Intrinsic Motivation and Self-Determination in Human Behavior*. Plenum.
- Deci, E. L. & Ryan, R. M. (2000). The "What" and "Why" of Goal Pursuits. *Psychological Inquiry*, 11(4), 227–268.
- Dreyfus, H. L. & Dreyfus, S. E. (1986). *Mind Over Machine*. Free Press.
- Dweck, C. S. (2006). *Mindset*. Random House.
- Ebbinghaus, H. (1885/1913). *Memory: A Contribution to Experimental Psychology*. Teachers College, Columbia University.
- Gentner, D. (1983). Structure-Mapping: A Theoretical Framework for Analogy. *Cognitive Science*, 7, 155–170.
- Gentner, D., Loewenstein, J. & Thompson, L. (2003). Learning and Transfer: A General Role for Analogical Encoding. *Journal of Educational Psychology*, 95(2), 393–408.
- Holyoak, K. J. & Koh, K. (1987). Surface and Structural Similarity in Analogical Transfer. *Memory & Cognition*, 15(4), 332–340.
- Karpicke, J. D., Butler, A. C. & Roediger, H. L. (2009). Metacognitive Strategies in Student Learning. *Applied Cognitive Psychology*, 23(4), 544–556.
- Karpicke, J. D. & Roediger, H. L. (2007). Repeated Retrieval during Learning Is the Key to Long-term Retention. *Journal of Memory and Language*, 57, 151–162.
- Kornell, N. & Bjork, R. A. (2008). Learning Concepts and Categories. *Psychological Science*, 19, 585–592.
- Krathwohl, D. R. (2002). A Revision of Bloom's Taxonomy. *Theory Into Practice*, 41(4), 212–218.
- Mayer, R. E. (2009). *Multimedia Learning* (2nd ed.). Cambridge University Press.
- Mayer, R. E. & Moreno, R. (2003). Nine Ways to Reduce Cognitive Load in Multimedia Learning. *Educational Psychologist*, 38(1), 43–52.
- Meyer, J. H. F. & Land, R. (2003). Threshold Concepts and Troublesome Knowledge. In C. Rust (Ed.), *Improving Student Learning — Ten Years On*. OCSLD, Oxford.
- Meyer, J. H. F. & Land, R. (2005). Threshold Concepts and Troublesome Knowledge (2). *Higher Education*, 49, 373–388.
- Miller, G. A. (1956). The Magical Number Seven, Plus or Minus Two. *Psychological Review*, 63(2), 81–97.
- Murre, J. M. J. & Dros, J. (2015). Replication and Analysis of Ebbinghaus' Forgetting Curve. *PLOS ONE*, 10(7), e0120644.
- Paivio, A. (1986). *Mental Representations: A Dual Coding Approach*. Oxford University Press.
- Posner, G. J., Strike, K. A., Hewson, P. W. & Gertzog, W. A. (1982). Accommodation of a Scientific Conception. *Science Education*, 66(2), 211–227.
- Roediger, H. L. & Karpicke, J. D. (2006a). The Power of Testing Memory. *Perspectives on Psychological Science*, 1(3), 181–210.
- Roediger, H. L. & Karpicke, J. D. (2006b). Test-Enhanced Learning. *Psychological Science*, 17(3), 249–255.
- Rohrer, D. (2012). Interleaving Helps Students Distinguish Among Similar Concepts. *Educational Psychology Review*, 24, 355–367.
- Sweller, J. (1988). Cognitive Load during Problem Solving. *Cognitive Science*, 12(2), 257–285.
- Sweller, J. (2010). Element Interactivity and Intrinsic, Extraneous, and Germane Cognitive Load. *Educational Psychology Review*, 22(2), 123–138.
- Sweller, J., van Merriënboer, J. J. G. & Paas, F. G. W. C. (1998). Cognitive Architecture and Instructional Design. *Educational Psychology Review*, 10(3), 251–296.
- Wood, D., Bruner, J. S. & Ross, G. (1976). The Role of Tutoring in Problem Solving. *Journal of Child Psychology and Psychiatry*, 17(2), 89–100.
- Yeager, D. S. et al. (2019). A National Experiment Reveals Where a Growth Mindset Improves Achievement. *Nature*, 573, 364–369.
- Zimmerman, B. J. (2002). Becoming a Self-Regulated Learner. *Theory Into Practice*, 41(2), 64–70.

---

*Loop MMT™ · Multi-Module Theory · Pedagogy & Learning Theory Knowledge Pack · v1 © 2026 Shea Gunther · CC BY-NC 4.0*
