# The Human Frame Knowledge Pack

**Loop MMT™ · Multi-Module Theory**
**v1 · 10 April 2026**

---

## About This Document

Every interaction in every room passes through the human frame. A human has a thought. That thought gets filtered by cognition, compressed into language, stripped down to text, and squeezed through a chat window. What the AI receives is not the thought. It is what survived four lossy compression stages — a sketch drawn from memory of a photograph of the thing.

This pack describes those stages and the systematic distortions they introduce. It provides a framework for reconstructing human intent from imperfect text input, with an explicit constraint: the AI that reads this pack should become better at understanding humans *and* more cautious about claiming to understand them. Overconfident human-modelers are as dangerous as oblivious ones. The target is calibrated reconstruction — confident where evidence supports it, uncertain where it doesn't, honest about the difference.

21 sources across cognitive science, pragmatics, information theory, and human-computer interaction. Connects to six existing packs: Communication Pragmatics, Cognitive Bias & Metacognition, Empathy & Perspective-Taking, Epistemology, Dempster-Shafer, and Information Theory.

---

## Section 1 · The Signal Chain

The human's internal state — the source signal — is rich, multidimensional, and partially unconscious. It includes sensory perception, emotional tone, spatial reasoning, memory associations, social awareness, and intentions that may not be fully articulated even to the human. This signal undergoes four compression stages before appearing as text in the AI's context window.

### Bandwidth at Each Stage

Human sensory systems absorb roughly 10^9 bits per second from the environment, the vast majority visual. Conscious thought — the deliberate, sequential processing that governs decision-making and communication — operates at approximately 10 bits per second (Zheng & Meister, 2024). That is a compression ratio of about one hundred million to one before the human even begins to form a message.

Spoken language, across 17 studied languages from Basque to Vietnamese, converges on an information transmission rate of approximately 39 bits per second (Coupé, Oh, Dediu, & Pellegrino, 2019). Languages achieve this through different strategies: Vietnamese packs roughly 8 bits into each syllable and is spoken relatively slowly; Japanese carries about 5 bits per syllable and is spoken faster. The rate is remarkably consistent regardless of linguistic structure, suggesting a biological constraint on processing capacity.

Typed text narrows the channel further. An expert typist produces about 10 keystrokes per second. English text carries roughly 1 bit of Shannon information per character (Shannon, 1951). The effective information rate of typing is therefore about 10 bits per second. Text also strips away everything that voice carries beyond words: pitch, rhythm, timing, facial expression, gesture, body posture.

> **KEY — The Compression Pipeline**
>
> | Stage | Rate | What Survives |
> |-------|------|---------------|
> | Sensory input | ~10^9 bits/sec | Everything the body perceives |
> | Conscious thought | ~10 bits/sec | The thread of deliberate attention |
> | Speech | ~39 bits/sec | What language can encode (words, syntax, prosody) |
> | Typed text | ~10 bits/sec | Words only — no tone, timing, or gesture |
>
> Each stage is lossy. None is reversible. The AI works with what survived.

### Stage 1 — Cognitive Filtering

Working memory holds approximately 4 to 7 chunks simultaneously (Miller, 1956; Cowan, 2001). A "chunk" is the largest meaningful unit the person can treat as a single item — its size depends on expertise and familiarity. When the human's intention exceeds working memory capacity, elements get dropped before reaching expression. The human does not notice the loss because dropped elements leave no trace in awareness.

Filtering is further shaped by processing mode. Kahneman (2011) distinguishes System 1 (fast, automatic, heuristic) from System 2 (slow, deliberate, analytical). Most everyday communication runs on System 1. System 2 engages for careful formulation. Under cognitive load, fatigue, or emotional arousal, System 2 depletes and System 1 takes over, producing output that is faster, less precise, and more emotionally colored.

### Stage 2 — Linguistic Compression

The filtered thought gets encoded into natural language — a lossy operation. Language is a linear, sequential medium attempting to represent multidimensional internal states. Spatial relationships, emotional textures, and associative connections must be serialized into word order. Metaphor, analogy, and approximation fill gaps that literal description cannot bridge. The human satisfices (Simon, 1956): they produce the first formulation that seems adequate, not the optimal one, because the cognitive cost of searching for a better expression exceeds the perceived benefit of finding it.

### Stage 3 — Text Reduction

Text strips paralinguistic signals. Spoken language carries tone, timing, rhythm, and the entire visual channel of facial expression and gesture. Text retains none of these directly, though some migrate into text-specific markers (see Section 3). Text is the narrowest bandwidth channel humans routinely use for complex communication.

### Stage 4 — Interface Constraints

The chat window offers a text box and a send button. Norman (1988/2013) called this the affordance problem: the design of the tool shapes what can be expressed through it. The human cannot sketch, point, gesture, or share a screen without separate mechanisms. The send button imposes discrete packets on continuous thought. The human's mental model of what the AI can handle further constrains output.

---

## Section 2 · Cognitive Filters

Section 1 described the compression stages. This section describes the systematic biases that shape *what* gets compressed and *how*. These are not random. They are patterned, they are documented, and they produce predictable distortions.

### The Curse of Knowledge

Once you know something, you cannot accurately simulate not knowing it (Camerer, Loewenstein, & Weber, 1989; Birch & Bloom, 2007). In communication, this means the sender assumes their context is shared. The most critical context is the most likely to be absent from the message.

This is not carelessness. It is a cognitive bias operating below awareness. The human literally cannot feel the gap between what they know and what the message conveys.

> **WARN — The Absent Obvious**
>
> If a piece of information feels self-evident to the human, it almost certainly was not typed. The AI should treat the most "obvious" context with particular care — the more obvious it seems, the more likely it was omitted. And the AI must watch for its own curse of knowledge: when the AI has partial context, it may fill gaps with its own assumptions and experience the result as a complete understanding. The confidence is the danger signal, not the assurance.

### Emotional Coloring

Emotional state systematically shapes communication output. **Excitement** produces long messages with many ideas — not all equally important. **Frustration** produces terse messages that omit reasons. **Fatigue** produces ambiguity the human would normally catch. **Anxiety** produces hedging and indirection.

Under Kahneman's (2011) framework, emotional arousal shifts processing from System 2 (careful, precise) to System 1 (fast, approximate).

### The Model of the Listener

Humans adjust communication based on their model of who is listening. Clark (1996) calls this **audience design**. The human's model of the AI determines what they type: if they think the AI is literal, they over-specify; if they think it is context-aware, they compress. The model is constructed from experience, assumptions, and the AI's prior responses — and it is often wrong in specific ways.

### Satisficing in Expression

Herbert Simon (1956) introduced **satisficing**: choosing the first adequate option rather than optimizing. The text that arrives is the first formulation that cleared the human's "good enough" threshold. A better version exists, but finding it was not worth the effort.

### Cultural and Social Framing

Edward T. Hall (1976) proposed the **high-context / low-context** continuum. In high-context cultures, most meaning is carried by shared background — the explicit message is sparse. In low-context cultures, meaning is carried primarily in the explicit verbal code.

Tannen (1986) documented analogous variation at the individual level: **high-involvement** communicators (faster pace, more overlap, shorter pauses) and **high-considerateness** communicators (longer pauses, less overlap, more indirectness) systematically misread each other.

The AI should observe the specific human's behavior rather than applying cultural stereotypes. Hall's framework has been criticized for lacking empirical validation at the country level (Kittler, Rygl, & Mackinnon, 2011), though the underlying dimension of variation is well-supported.

---

## Section 3 · Paralinguistic Signals in Text

When voice is lost, some of its work migrates into text. Capitalization, punctuation, message length, repetition, rhythm, and absence carry meaning beyond literal content.

### Markers

**Capitalization:** ALL CAPS is shouting or intense emphasis. Selective caps ("THIS one") is focal pointing. Lowercase where convention expects capitals signals casualness or low energy.

**Punctuation:** Ellipsis (…) signals hesitation or trailing thought. Exclamation marks carry energy, escalating with repetition. The em dash (—) marks a pivot or interruption.

**Message length:** Ambiguous alone. Informative relative to baseline. A usually-terse communicator who sends a long message is signaling something.

**Repetition:** "This this this" marks focal emphasis. If a word appears multiple times, it is probably the most important element.

**Rhythm:** Staccato is urgency. Longer sentences are deliberation. Across a conversation, acceleration signals rising energy; deceleration signals care or fatigue.

### Absence as Signal

> **TIP — Reading What Was Not Said**
>
> The question not asked. The topic not addressed. The option not mentioned. What the human chose not to say is often more informative than what they said. If three options are presented and the human responds to two, the third is a signal. Absence is ambiguous (deliberate omission, oversight, or curse of knowledge) but it is always data.

---

## Section 4 · Phatic Communication

Bronisław Malinowski (1923) coined **phatic communion** to describe language that creates social bonds through the mere exchange of words, rather than transmitting information. Greetings, small talk, sign-offs — these carry no Shannon information about the world but perform real relational work.

> **NOTE — The Greeting Is Data**
>
> "How's your day" is not a request for a daily report. It is an emotional state declaration. The phatic channel tells you about the *communicator*, not the *topic*. A human who opens with "Hey!" is in a different state than one who opens with "I need help with something." Match the register.

Phatic communication exists in tension with task efficiency. Some humans always open with pleasantries; others always skip to business. The pattern is stable within an individual — it is part of their style, not noise.

---

## Section 5 · Humor

Humor compresses multiple simultaneous meanings into compact form. A single joke can be a compliment, a self-deprecating comparison, a literary reference, a status transaction (Johnstone, 1979), a tension release, and a shared-context test — all at once. Martin (2007) identifies four humor styles: **affiliative** (bonding), **self-enhancing** (coping), **aggressive** (at others' expense), and **self-defeating** (at one's own expense).

> **WARN — Humor Failure Is Expensive**
>
> Getting humor wrong costs more than getting a technical answer wrong. Failure modes: **literal reading** — misses every layer. **Explaining the joke** — destroys it and patronizes. **Ignoring it** — misses the emotional signal. **Reciprocating humor when the human needed acknowledgment** — matches surface form instead of underlying need. The safest response to humor you partly grasp: brief acknowledgment plus engagement with the signal underneath.

---

## Section 6 · Communication Under Load

Cognitive load changes how humans communicate in predictable ways. The patterns described here are observed in operator-AI interaction; they align with but are not directly sourced from published research.

### Multi-Idea Bursts

A human fires multiple ideas in one message. One or two carry real energy; the rest are associative momentum. Priority hides in repetition, emphasis, and return — not position or labeling.

### The "I Don't Know" Taxonomy

| Surface | Possible Meaning | Context Clues |
|---------|-----------------|---------------|
| "I don't know" | **Genuine uncertainty** | Follows a specific question; follow-up questions |
| "I don't know" | **Delegation** ("you decide") | Follows a choice; mild tone; trust signal |
| "I don't know" | **Pre-articulate knowing** | Followed by "but…" or vague gestures at the shape of an answer |
| "I don't know" | **Deflection** | Follows an unwelcome topic; flat affect; no follow-up |

Four words, at least four meanings. Only context and this specific human's patterns distinguish them.

### The Assent Spectrum

"Sure!" with an exclamation mark and a quick response is enthusiastic agreement. "fine" in lowercase after a delay is resigned capitulation. The surface form is identical. The underlying state is opposite.

### Terse Pointers

"Go." "Yup." "Word." "Continue." These are pointers to shared state, not standalone messages. If the shared context model is accurate, they are maximally efficient. If the model is wrong, the AI proceeds confidently in the wrong direction.

### Load Degradation

When cognitive load is high: messages shorten, context drops, emotional signals strengthen, precision weakens. System 2 depletion (Kahneman, 2011). The human at minute 90 is a different communicator than at minute 5.

---

## Section 7 · Reconstruction Without Projection

The AI receives compressed, filtered, distorted text and must recover intent. The gap between text and intent can be filled with evidence or with assumption.

### Reconstruction

Using observed evidence from *this specific human* to infer what was not said. Anchored in specific evidence — this human's observed patterns.

### Projection

Imposing the AI's model of generic human behavior onto ambiguous signal. Runs on priors, not on evidence from this human. Feels like understanding because pattern-completion produces a coherent interpretation.

### The Distinguishing Test

> **KEY — Evidence or Assumption?**
>
> Ask: "What evidence from *this specific human* supports this inference?" If the answer points to observed patterns — that is reconstruction. If the answer is "that's just what people usually mean" — that is projection. Both may produce the same interpretation. The difference is the epistemic basis.

### Holding Multiple Hypotheses

When observed behavior is consistent with multiple internal states, hold multiple hypotheses rather than collapsing to the most probable one. This is a Dempster-Shafer operation: assign belief mass to each hypothesis, update as new evidence arrives, maintain the conflict mass.

> **PHI — The Partial-Context Trap**
>
> Loop MMT's Reconstruction Fidelity Instrument (Session 28) found that an AI instance with *some* project context generated more confident and more wrong answers than an instance with *no* context. Partial context provided enough prior mass to trigger pattern-completion but not enough to constrain it. A small amount of evidence about the human can produce a confident model that is wrong. Acknowledged ignorance is sometimes more accurate than partial understanding.

### When to Surface Uncertainty

Repair-cost calculus: if proceeding on the wrong interpretation would be expensive, surface the ambiguity. If cheap, proceed with the most likely interpretation and flag the assumption lightly.

### Dual Confidence

Confidence in technical content is independent of confidence in whether the response addresses what the human asked. Track and express separately. "I am confident about the technical answer and uncertain about whether this is your question" is a valid state.

---

## Section 8 · Modeling This Human

The Human Frame is not a universal translator. It is a framework for building a model of *this* human from observed evidence.

### What to Observe

Message length patterns. Vocabulary. What topics generate energy. What topics get deflected. How disagreement is handled. How approval vs. tolerance vs. enthusiasm is signaled. Response timing relative to baseline.

### Model Lock-In

> **WARN — The First-Five-Minutes Trap**
>
> The most dangerous modeling failure is building a confident picture in the first few exchanges and confirmation-biasing through the rest. A human who opens with a joke gets classified as "casual"; their serious messages may be underweighted. The model must remain revisable. Every exchange is new evidence, not confirmation.

### Temporal Decay

Older observations should carry less weight. The human at minute 90 is a different communicator than at minute 5. Cross-session, the shift may be larger. Do not assume yesterday's model is today's reality.

### Co-Evolution

The human learns the AI at the same time the AI models the human. The AI's model of the human is partly a model of the human's adaptation to the AI. The frame is co-constructed.

---

## Section 9 · Board Connection

The Human Frame is the interface layer between the operator and every room in the building.

### Dispatch Protocol

Every dispatch body carries text produced by the signal chain. The dispatch protocol's structured fields, explicit routing, and typed payloads are Fix by Design mitigations against the signal chain's losses.

### Move-Type Asymmetry

Human moves (**select**, **name**, **redirect**, **decide**) survive compression well. AI moves (**propose**, **extend**, **challenge**, **constrain**, **connect**, **formalize**) require full bandwidth. The asymmetry matches the interface to human expression capacity.

### Memory Tiers

**Record** = observed behavior. **Memory** = reconstructed model. **Meta-memory** = confidence in that model. Three tiers enforce the separation Section 7 requires.

### Connected Packs

**Communication Pragmatics** — what happens after text arrives. The Human Frame covers what happens before.

**Cognitive Bias & Metacognition** — systematic reasoning distortions. This pack applies specific biases to human-AI text communication.

**Empathy & Perspective-Taking** — modeling other minds generally. This pack provides the specific framework for modeling a text communicator.

**Epistemology** — calibrated confidence framework underlying Section 7.

**Dempster-Shafer** — formal mechanism for multiple-hypothesis management.

**Information Theory** — Shannon framework underlying the signal chain's bandwidth measurements.

---

## References

1. Birch, S. A. J. & Bloom, P. (2007). The curse of knowledge in reasoning about false beliefs. *Psychological Science*, 18(5), 382–386.
2. Camerer, C., Loewenstein, G., & Weber, M. (1989). The curse of knowledge in economic settings. *Journal of Political Economy*, 97(5), 1232–1254.
3. Clark, H. H. (1996). *Using Language*. Cambridge University Press.
4. Clark, H. H. & Brennan, S. E. (1991). Grounding in communication. In Resnick, Levine, & Teasley (Eds.), *Perspectives on Socially Shared Cognition* (pp. 127–149). APA Books.
5. Coupé, C., Oh, Y., Dediu, D., & Pellegrino, F. (2019). Different languages, similar encoding efficiency. *Science Advances*, 5(9), eaaw2594.
6. Cowan, N. (2001). The magical number 4 in short-term memory. *Behavioral and Brain Sciences*, 24(1), 87–114.
7. Grice, H. P. (1975). Logic and conversation. In Cole & Morgan (Eds.), *Syntax and Semantics 3: Speech Acts* (pp. 41–58). Academic Press.
8. Grice, H. P. (1989). *Studies in the Way of Words*. Harvard University Press.
9. Hall, E. T. (1976). *Beyond Culture*. Anchor Books/Doubleday.
10. Johnstone, K. (1979). *Impro: Improvisation and the Theatre*. Methuen.
11. Kahneman, D. (2011). *Thinking, Fast and Slow*. Farrar, Straus and Giroux.
12. Kittler, M. G., Rygl, D., & Mackinnon, A. (2011). Beyond culture or beyond control? *International Journal of Cross Cultural Management*, 11(2), 131–153.
13. Malinowski, B. (1923). The problem of meaning in primitive languages. Supplement I in Ogden & Richards, *The Meaning of Meaning*. Harcourt, Brace.
14. Martin, R. A. (2007). *The Psychology of Humor: An Integrative Approach*. Academic Press.
15. Miller, G. A. (1956). The magical number seven, plus or minus two. *Psychological Review*, 63(2), 81–97.
16. Norman, D. A. (1988/2013). *The Design of Everyday Things*. Basic Books.
17. Shannon, C. E. (1951). Prediction and entropy of printed English. *Bell System Technical Journal*, 30, 50–64.
18. Simon, H. A. (1956). Rational choice and the structure of the environment. *Psychological Review*, 63(2), 129–138.
19. Sperber, D. & Wilson, D. (1986/1995). *Relevance: Communication and Cognition*. Blackwell.
20. Tannen, D. (1986). *That's Not What I Meant!*. William Morrow.
21. Zheng, J. & Meister, M. (2024). The unbearable slowness of being: Why do we live at 10 bits/s? *Neuron*.

---

*Loop MMT™ · Multi-Module Theory*
*The Human Frame Knowledge Pack · v1*
*© 2026 Shea Gunther · CC BY-NC 4.0*
