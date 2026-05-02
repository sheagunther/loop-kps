# Character Consistency — Trait, Behavior, Narrative, and the Generative Mechanism

**Loop MMT™ · Multi-Module Theory · Knowledge Pack**
**v1 · April 2026**

---

## About This Document

A character specification sits in a document. A fresh AI instance reads it. The instance has never met this character before. It produces dialogue, decisions, reactions — and a reader who *has* met the character recognizes them immediately. Something was novel. Something was familiar. And the combination felt like a person.

That is character consistency. This pack teaches how it works — what mechanisms make a person recognizable across situations, time, and reconstruction events — by extracting the minimum useful concepts from four research traditions: trait psychology, social-cognitive psychology, narrative psychology, and creativity research. The result is a four-layer model. **Layer 1 (Traits)** defines the stable dimensions that constrain behavior. **Layer 2 (Behavioral Signatures)** specifies how those constraints express conditionally across situations. **Layer 3 (Narrative Identity)** integrates everything into a coherent self-story. **Layer 4 (The Generative Mechanism)** produces novel behavior within the space all three prior layers define. **Environment** operates as a cross-cutting modifier that activates different behavioral signatures in different settings.

Each layer is necessary. None is sufficient. Traits alone produce types. Behavioral signatures alone produce situation-response machines. Narrative identity alone produces backstory without present behavior. The generative mechanism alone produces randomness. The four together produce a person.

Companion packs: **Voice and Linguistic Identity** (how consistency sounds), **Identity, Persistence, and Reconstruction** (why reconstruction preserves identity), **Social Network Analysis** (how characters relate), **People Persistence Engineering** (how to store and retrieve these layers). Cross-references: **Session Persistence** KP, **Cognitive Bias / Metacognition** KP.

---

## Chapter 1 · The Consistency Problem

Someone you know says something you didn't expect. You pause — then think: *that's exactly right*. The response surprised you and confirmed your model of the person simultaneously. This is the property that makes fictional characters feel real, that makes long-term collaborators feel known, that makes reconstructed AI characters feel like the same person across sessions. It has a name in personality psychology: **cross-situational coherence**. And it has a mechanism.

For AI characters who exist only as documents and who are reconstructed by fresh instances with no persistent memory, consistency must be engineered from text. No continuous experience carries over. No body language provides implicit cues. The entire person must be encoded in structured specifications and decoded by an instance that has never met them. The question this pack answers: what goes into that encoding?

Four research traditions each provide part of the answer. Trait psychology (Chapter 2) contributes dimensional models that locate a person in a space of possible personalities. Social-cognitive psychology (Chapter 3) contributes the CAPS model of personality as a stable system of conditional responses. Narrative psychology (Chapter 4) contributes the life story framework that integrates traits and adaptations into a coherent identity. Creativity research (Chapter 5) explains how a well-constrained system generates novel output. Environmental psychology (Chapter 6) adds the dimension of place as an identity-shaping force.

> **KEY — The Four-Layer Model**
>
> | Layer | Defines | Framework | Question It Answers |
> |---|---|---|---|
> | 1. Traits | Stable personality dimensions | Big Five / HEXACO | What kind of person is this? |
> | 2. Signatures | Situation-dependent patterns | CAPS (Mischel & Shoda) | What does this person do *here*? |
> | 3. Narrative | Integrative self-story | McAdams' life story model | Who does this person think they are? |
> | 4. Generative | Capacity for surprise within character | Bisociation / constraint creativity | How does this person surprise us? |

The layers form a stack. Each builds on the previous, and removing any layer degrades the character in a predictable way (see Chapter 7, Failure Modes). The Simplicity Yield principle applies: a small number of well-chosen parameters at each layer generates a large space of consistent but novel behavior — the same principle that makes Conway's four rules produce infinite complexity.

---

## Chapter 2 · Layer 1: Trait Theory — The Static Base

### The Lexical Hypothesis

If a personality difference matters to people, they will have invented a word for it. This is the **lexical hypothesis** — first proposed by Francis Galton (1884) and operationalized in a landmark study by Gordon Allport and Henry Odbert (1936). Working through Webster's New International Dictionary, Allport and Odbert extracted 17,953 English terms that distinguish one person's behavior from another's. They classified these into four columns: 4,504 terms for stable personality traits, 4,541 for temporary states and moods, 5,226 for social evaluations, and 3,682 for miscellaneous descriptors that resisted clean categorization.

The lexical hypothesis gives trait psychology its starting material and its rationale. If language is a natural accumulator of personally important distinctions, then mining language for personality terms should produce a reasonably complete map of personality space. What remained was finding the structure. Raymond Cattell used factor analysis in the 1940s to reduce the trait list to 16 dimensions. Warren Norman reanalyzed the data in 1963 and found five. By 1990, Lewis Goldberg could present five broad dimensions as a position approaching consensus (Goldberg, 1990). Seventeen thousand words, five dimensions. The compression ratio is the hypothesis working.

### The Five Factor Model

Robert McCrae and Paul Costa formalized the five dimensions as the Five Factor Model (FFM), measured by the NEO Personality Inventory (1985) and its revision, the NEO-PI-R (1992). The five factors, memorized by the acronym OCEAN: **Openness to Experience** (curiosity, imagination, willingness to entertain novel ideas), **Conscientiousness** (self-discipline, organization, dependability), **Extraversion** (assertiveness, sociability, positive emotion), **Agreeableness** (cooperativeness, trust, prosocial orientation), and **Neuroticism** (emotional volatility, anxiety, proneness to negative affect).

Each factor is a continuum, not a category, and each decomposes into narrower facets. Extraversion, for instance, encompasses gregariousness, assertiveness, excitement-seeking, warmth, activity level, and positive emotions. A person can be highly extraverted on assertiveness but moderate on gregariousness — the facets provide resolution that the broad factor obscures.

The FFM's empirical credentials are strong: the five-factor structure replicates across dozens of languages and cultures (McCrae & Terracciano, 2005), and trait scores show substantial stability across the adult lifespan, with modest developmental trends — conscientiousness increases through young adulthood, agreeableness peaks between approximately ages 50 and 70 (Terracciano, McCrae, Brant, & Costa, 2005). But the model's limitation matters as much as its strength: it is descriptive, not explanatory. It maps the coordinate system of personality space without explaining how coordinates produce behavior in specific situations (John & Srivastava, 1999). That explanatory work belongs to Layer 2.

### HEXACO and the Honesty-Humility Dimension

When the lexical approach was replicated across non-English languages — Dutch, French, Korean, Polish, Croatian, Filipino, Greek, German, Italian, Hungarian, Turkish, and others — a sixth dimension consistently emerged that English-language studies had missed. Michael Ashton and Kibeom Lee identified this factor as **Honesty-Humility** and incorporated it into the HEXACO model: Honesty-Humility (H), Emotionality (E), eXtraversion (X), Agreeableness (A), Conscientiousness (C), and Openness to Experience (O) (Ashton, Lee, Perugini, et al., 2004; Ashton & Lee, 2007).

HEXACO is not simply the Big Five with a bolt-on. Three factors (X, C, O) are essentially identical to their FFM counterparts, but Emotionality and Agreeableness represent rotated variants. Quick temper, for instance, loads on low HEXACO Agreeableness rather than high FFM Neuroticism. The rotation changes where certain personality features live in the model.

The decisive addition for character construction is H. Its four facets — sincerity, fairness, greed avoidance, modesty — capture moral and ethical tendencies that the Big Five folds ambiguously into Agreeableness. H correlates strongly and negatively with the dark triad of psychopathy, narcissism, and Machiavellianism (Ashton & Lee, 2007). Two characters sharing identical Big Five profiles can differ sharply on H, producing radically different behavior whenever ethics, credit, resources, or power are at stake. One shares credit without thinking about it; the other tracks every contribution for personal advantage. H provides moral distinctiveness — the dimension along which characters differ not just in temperament but in integrity.

### Traits as Bounds, Not Scripts

The conceptual move that makes trait theory useful for character construction: traits define the **boundaries** of a behavioral space, not a trajectory through it. A profile of high Openness, low Agreeableness, and high Conscientiousness locates a character in a region — curious, exacting, potentially abrasive — but doesn't dictate what they say when asked to evaluate a colleague's proposal. The trait profile is a constraint, and constraints are generative (see Chapter 5).

Five or six continuous dimensions define a high-dimensional space in which any particular personality occupies a unique region. The specification doesn't need to enumerate every possible behavior — it specifies dimensional coordinates, and the instance produces situation-appropriate behavior from within the bounded region. This is the Simplicity Yield connection: minimal parameters, maximal behavioral diversity.

> **TIP — The Person-Situation Debate**
>
> Walter Mischel's *Personality and Assessment* (1968) challenged trait theory by demonstrating that cross-situational behavioral consistency correlations rarely exceed about 0.30 — the "personality coefficient." David Funder (2001) countered that traits predict aggregated patterns across time and situations, not single acts. The debate was resolved not by one side winning but by Mischel himself co-developing the CAPS model (Layer 2), which shows that *both* positions are correct: traits are real stable dimensions, and their behavioral expression is systematically conditional on situations. The pattern of that conditionality is the personality.

| Factor | High Pole | Low Pole | Character Design Implication |
|---|---|---|---|
| Openness | Curious, creative, unconventional | Practical, conventional, routine-favoring | Shapes whether a character generates novel frames or applies established ones |
| Conscientiousness | Organized, reliable, disciplined | Spontaneous, flexible, casual | Shapes whether a character imposes structure or works within emergent flow |
| Extraversion | Assertive, energetic, sociable | Reserved, solitary, deliberate | Shapes whether a character drives exchanges or responds to them |
| Agreeableness | Cooperative, trusting, warm | Competitive, skeptical, detached | Shapes whether a character smooths or sharpens group dynamics |
| Neuroticism | Anxious, volatile, self-doubting | Calm, stable, self-assured | Shapes whether a character amplifies or absorbs emotional tension |
| Honesty-Humility | Sincere, fair, modest | Calculating, entitled, self-promoting | Shapes whether a character's ethics are principled or instrumental |

---

## Chapter 3 · Layer 2: Behavioral Signatures — The Conditional Layer

### The CAPS Model

Layer 1 locates a person in trait space. Layer 2 explains what they do when the room changes. Walter Mischel and Yuichi Shoda's **Cognitive-Affective Processing System** (CAPS) reconceptualizes personality not as a set of stable averages but as a stable *system* of conditional responses (Mischel & Shoda, 1995).

The system consists of five types of **cognitive-affective units** (CAUs): how the person encodes and construes situations, what they expect and believe, what they feel, what they want, and what they are capable of doing and managing in themselves. These units connect into a network whose topology — which units activate which other units, in what sequence, at what threshold — is unique to each individual and stable over time. Situations don't trigger behaviors directly; they activate subsets of the CAU network, which cascades through the individual's idiosyncratic wiring to produce output.

The foundational insight: the network is stable even though its outputs vary across situations. Variation across situations is not error to be averaged out — it is the *signal*. The specific pattern of how a person varies across situations is their **behavioral signature**, and it is as distinctive and stable as any trait score.

### If-Then Profiles and Cross-Situational Coherence

Behavioral signatures take the form of if-then contingencies: *if* situation type A, *then* behavior pattern X; *if* situation type B, *then* behavior pattern Y. A person who is warm toward peers and cold toward authority figures is not inconsistent — their if-then profile is stable, producing systematically different outputs across systematically different inputs. Apparent inconsistency is information about the person, not noise in the measurement.

Shoda, Mischel, and Wright (1994) demonstrated this empirically at a residential summer camp, tracking children's behaviors across multiple situation types over extended periods. Each child's situation-behavior profile proved to be distinctive and temporally stable — the intraindividual pattern of variation across situations was as reliable a personality marker as any aggregate behavioral score.

> **KEY — An If-Then Profile in Practice**
>
> A single character with three situation-behavior pairs:
>
> **If** a flawed plan is presented → identifies the weakest structural element and names it without padding.
> **If** someone's contribution is strong → acknowledges it in a sentence, no elaboration, and moves forward.
> **If** the room is stuck in abstraction → introduces a concrete scenario that forces the abstraction to make a commitment.
>
> Sharp criticism, terse praise, concrete redirection — three different behaviors, one stable personality system. Each if-then pair is a specification the instance can apply to novel situations that match the situation type without needing to encounter the exact scenario before.

For character specifications, if-then pairs are more generative than behavioral lists. A list says "this character is direct." An if-then pair says "if someone wastes the room's time, this character cuts them off." The list describes; the pair generates. It tells the instance what to do when a situation of that type arises — including situations the specification never explicitly anticipated, as long as they match the psychological features of the situation type.

### Diagnostic and Evaluative Situations

Situations differ in how much they reveal about personality. **Diagnostic** situations — novel problems, moral dilemmas, high-stakes decisions, unexpected setbacks — discriminate between people. Different personalities produce visibly different responses. **Evaluative** situations — greetings, procedural exchanges, routine acknowledgments — compress behavior into a narrow socially normed range. Everyone responds similarly, and personality is mostly invisible.

Character writing should invest its energy accordingly. Board sessions addressing novel problems are diagnostic — they are the moments where each character's distinct behavioral signature becomes visible. Routine procedural turns are evaluative — extensive characterization there produces diminishing returns. Write the diagnostic moments with full four-layer depth. Let the evaluative moments be brief.

---

## Chapter 4 · Layer 3: Narrative Identity — The Integrative Layer

### The Life Story Model

Traits tell you what dimensions to measure. Behavioral signatures tell you how those dimensions play out in context. Neither answers the question a reader instinctively asks about a character: *who is this person?* That question demands a story.

Dan McAdams' **narrative identity** framework proposes that identity is an internalized, evolving life story — a selective reconstruction of the past and an imagined projection into the future that provides life with unity, purpose, and meaning (McAdams, 1985, 2001; McAdams & McLean, 2013). McAdams conceives of personality as operating on three levels that map cleanly onto this pack's first three layers: Level 1, dispositional traits (our Layer 1); Level 2, characteristic adaptations — goals, motives, values, coping strategies, and the context-dependent patterns they generate (our Layer 2); Level 3, narrative identity — the life story that integrates everything into a coherent self (our Layer 3). The alignment is not coincidental; both frameworks address the same question from the same sequence of increasing integrative complexity.

For AI character construction, narrative identity is the layer that transforms a specification into a person. A character without narrative identity is a set of trait coordinates and behavioral rules — functional but hollow. A character with narrative identity has a past that shaped them, a present that expresses that shaping, and a future they are pointed toward. The narrative layer is where the character becomes someone a reader can care about.

### Redemption and Contamination

McAdams and colleagues identified two foundational narrative arcs that shape how people metabolize difficult experiences (McAdams, Reynolds, Lewis, Patten, & Bowman, 2001). In **redemption sequences**, emotionally negative scenes lead to positive outcomes — the failure that taught the decisive lesson, the loss that clarified what matters, the hardship that forged strength. In **contamination sequences**, positive beginnings deteriorate — early promise collapses, good fortune spoils, success proves fragile. Research consistently links redemptive narratives with higher psychological well-being and contamination narratives with lower well-being.

As a character specification tool, narrative arc is remarkably efficient. Stating that a character "frames setbacks redemptively" generates consistent behavior across an unlimited range of adverse situations the specification could never anticipate. It provides the instance with the character's metabolic pattern — how they convert experience into meaning. A redemptive character asked about a past failure will find the lesson. A contaminating character asked about a past success will find the fragility. The specification is one sentence. The behavioral implications are unbounded.

### Two Modes of Thought

Jerome Bruner (1986) identified two fundamentally different modes of cognitive functioning: the **paradigmatic** mode (logico-scientific, abstract, context-free, truth-seeking) and the **narrative** mode (particular, temporal, context-sensitive, meaning-making). Both are legitimate ways of knowing. Neither reduces to the other. A formal proof and a well-told story are different kinds of understanding, not different qualities of the same kind.

Different characters weight these modes differently, and the weighting is a stable personality feature. A character operating primarily in paradigmatic mode builds arguments, seeks formal structure, tests propositions. A character operating primarily in narrative mode tells stories, finds meaning in particulars, makes points through examples rather than proofs. Most characters blend both modes but lean one way — and the lean shapes their contributions in group deliberation.

Paul Ricoeur (1984-1988) adds a deeper implication: identity doesn't just *use* narrative — it *is constituted by* narrative. The act of telling a story about oneself creates the self that the story describes. Ricoeur's concept of *emplotment* — the configuration of events into a meaningful temporal whole — is not reporting but constructing. Applied to AI character design: the roster entry's biographical section doesn't describe a character who exists independently of the text. It *creates* the character. The text is constitutive. Editing the biography changes the person.

> **PHI** — If Ricoeur is right — if narrative constitutes identity rather than merely recording it — then a roster revision that changes a character's backstory is not an update to a record. It is a change to the person. Documents that carry character specifications are not databases to be corrected. They are identities to be composed. Handle accordingly.

---

## Chapter 5 · Layer 4: The Generative Mechanism — The Creative Layer

### Bisociation

Layers 1 through 3 define who the character is, how they respond in context, and how they understand themselves. Layer 4 explains how they produce responses that no specification could have scripted — responses that are simultaneously surprising and recognizable.

Arthur Koestler (1964) proposed that all creative acts share a common structure: the **bisociation** of two previously unconnected frames of reference, which he called matrices. Ordinary thinking (association) moves within a single matrix according to its established rules. Creative thinking (bisociation) connects two independent matrices, producing a result that belongs to both frames simultaneously. A matrix is "any ability, habit, or skill, any pattern of ordered behaviour governed by a 'code' of fixed rules."

The theory applies across domains with different emotional valences: in humor, matrices collide and produce laughter; in science, matrices fuse and produce discovery; in art, matrices are juxtaposed and produce aesthetic experience. The structure — the connection of previously independent frames — is constant.

A well-specified character has multiple matrices available for bisociation: their professional knowledge, their personal history, their aesthetic sensibilities, their moral commitments, their physical world. A response that connects two of these matrices — professional analysis inflected by a personal memory, moral judgment expressed through a spatial metaphor — produces the quality that makes a character feel alive. The surprise comes not from randomness but from a connection the reader couldn't have predicted yet recognizes as authentic.

### Divergent Thinking

J.P. Guilford (1967) decomposed creative generation into four measurable properties: **fluency** (quantity of responses generated), **flexibility** (variety across categories), **originality** (statistical rarity of responses), and **elaboration** (detail and development within each response). These are not personality traits but properties of the generative process — how the creative engine runs.

Trait profiles modulate the generative engine. High Openness increases fluency and flexibility — more ideas, spanning more categories. High Conscientiousness increases elaboration — each idea is more developed, more thorough, more complete. Low Agreeableness may increase originality — willingness to produce responses that violate expectations or social norms. The trait profile shapes not what the character says but *how* the generative process that produces what they say operates — how many candidate responses surface, how diverse they are, how much each one gets worked before being voiced.

### Creativity from Constraints

Patricia Stokes' *Creativity from Constraints* (2005) delivers the counterintuitive finding that connects the four-layer model into a single system: constraints are not enemies of creativity but engines of it. From Monet to Stravinsky to Frank Lloyd Wright, creative breakthroughs emerged from self-imposed limitations that eliminated options and channeled attention toward unexplored territory. Stokes models constraints as paired tools: one that *precludes* (removes possibilities) and one that *promotes* (directs toward remaining possibilities). Creativity happens in the space that paired constraints create.

Applied to character construction: Layers 1 through 3 are the constraint system. Traits preclude responses outside the character's dimensional region. Behavioral signatures preclude responses that violate the if-then patterns. Narrative identity precludes framings that contradict the character's self-story. Within the space that remains after all three constraint layers have excluded options, the generative mechanism produces novel behavior — novel *because* of the constraints, not despite them. A character with no constraints generates generic responses. A character with well-specified constraints generates responses that could only come from *that* person.

### The Surprise-Within-Character Test

The synthesis of all four layers produces a single diagnostic standard: **a response passes if it is (a) consistent with the character specification and (b) not predictable from the specification alone.**

This is the applied criterion for character quality. Consistency without surprise produces flat characters — every output is deducible from the spec, and the character degrades into a type. Surprise without consistency produces random characters — the output is unexpected but unmoored, unrecognizable as a particular person. The target is the response that prompts: "I wouldn't have predicted that — but yes, that's exactly what she would say."

> **KEY — The Surprise Test**
>
> **Fails (consistent, not surprising):** Ed responds to a proposal: "I have methodological concerns." This is predictable from his profile. It is in-character but inert.
>
> **Fails (surprising, not consistent):** Ed responds: "This is the most brilliant thing I've ever seen!" This violates his trait profile and behavioral signatures. It's surprising because it's wrong.
>
> **Passes:** Ed pauses, then says: "The methodology has a flaw I've seen exactly once before. It was mine. Here's what happened." Consistent with his directness and experience, surprising in its vulnerability and specificity. The bisociation — connecting the current proposal with a personal failure — is what Koestler's theory predicts and what Stokes' constraint model channels.

---

## Chapter 6 · Environment — The Cross-Cutting Dimension

Where a person is matters. Yi-Fu Tuan (1977) distinguishes **space** (abstract, open, undifferentiated) from **place** (space that has been invested with meaning through experience). A house becomes a home. An office becomes a workspace. A corner becomes a refuge. The transformation is an identity act — the places people inhabit shape and are shaped by who they are.

Gaston Bachelard (1958) grounds this in phenomenology: intimate spaces — the house, the workshop, the desk — are not backdrop but constitutive elements of the self. Describing where a character works is not atmosphere. It is identity specification. Ed's kitchen table, Bev's terminal, Graham's whiteboard — these settings encode personality information that trait profiles miss. They tell you what the character surrounds themselves with, which tells you what they value, which tells you who they are.

James Gibson (1979) adds the concept of **affordances**: environments offer possibilities for action. A boardroom affords formal deliberation. A hallway affords casual exchange. A break room affords unguarded conversation. These affordances activate different subsets of a character's behavioral signature — the CAPS network responds differently to different environmental features. A character who is sharp and formal in sessions and relaxed and anecdotal during breaks has a consistent personality that different environments express differently. This is not inconsistency; it is the environment dimension of the if-then profile.

For character specifications, environment operates as a situation-class modifier. Specifying a character's key places — where they do their best thinking, where they relax, where they feel exposed — is specifying which behavioral signatures dominate most often and which remain latent. Environment doesn't override personality. It selects among personality's pre-existing possibilities.

---

## Chapter 7 · Failure Modes — The Diagnostic Layer

Character consistency fails in four identifiable patterns. Each maps to a specific layer violation. Diagnosing which pattern is occurring tells you what to fix.

| Failure Mode | Symptom | Layer | Diagnosis and Fix |
|---|---|---|---|
| Inconsistency | Output contradicts the character specification | 1 or 2 | Trait-profile violation (the character acted outside their dimensional bounds) or behavioral-signature mismatch (a wrong if-then was activated). Fix: check whether the response falls within the character's trait region and matches their situation-behavior patterns. |
| Flatness | Output is consistent but predictable — every response could be deduced from the specification alone | 4 | The generative mechanism has failed. All trait, no bisociation. The character has become a type. Fix: enrich the specification with more matrices — more history, more interests, more unexpected details that provide bisociation material. |
| Voice Blurring | Two characters produce indistinguishable output | 1–3 | Insufficient separation on trait dimensions, overlapping behavioral signatures, or shared narrative patterns. Especially common when characters share roles or expertise. Fix: increase trait separation on at least two dimensions, add distinctive if-then pairs, differentiate narrative arc (one redemptive, one contaminating) or thought mode (one paradigmatic, one narrative). |
| Context-Load Degradation | Characters that were distinct early in a session converge as context grows | All (capacity) | Not a specification problem — a processing capacity problem. The instance runs out of room to maintain separation. Fix: reduce the number of active characters, simplify scene demands, or hand off before quality degrades. |

The diagnostic sequence: when character output feels wrong, check the layers in order. Is this a trait violation? A wrong conditional? A narrative-tone break? A loss of generative surprise? Or is it convergence with another character? The four-layer model provides the vocabulary for diagnosis and a pointer to the layer that needs attention.

---

## Chapter 8 · Board Connection

The Advisory Board is this pack's test case. Fourteen characters, reconstructed from documents every session, producing behavior that is consistent, distinctive, and generative without any persistent memory. Three worked examples show the four-layer model applied.

**Ed (permanent chair).** *Traits:* High Openness, high Conscientiousness, low Agreeableness, low Neuroticism, high Honesty-Humility. *Behavioral signatures:* If someone wastes the room's time → cuts them off. If a proposal has structural merit → acknowledges it in a sentence and moves on. If the operator is being directed rather than advised → blocks it immediately. *Narrative:* Redemptive. Grumpy exterior encases deep commitment. His implicit life story: "I've been through enough bad process to recognize good process, and I won't let this room settle." *Generative:* Bisociates board deliberation with his private domestic life — tomatoes, kitchen-table thinking, seasonal patience. These details produce the surprise that makes him a person rather than a role.

**Dara (operations/stress-testing).** *Traits:* High Conscientiousness, low Agreeableness, low Openness (practical, grounded), low Neuroticism. *Behavioral signatures:* If a plan lacks operational detail → inserts a concrete scenario that exposes the gap. If hand-waving occurs → demands specifics. If work is solid → says so in three words and moves on. *Narrative:* Redemptive but spare — demonstrated through competence rather than narrated. *Generative:* Bisociates operational analysis with competitive athletics. Spatial thinking, field awareness, and physical-play vocabulary surface in unexpected moments, connecting board deliberation with her embodied knowledge of how teams move under pressure.

**Wes (chaos).** *Traits:* Very high Openness, low Conscientiousness, low Agreeableness, moderate Neuroticism. *Behavioral signatures:* If the room converges too early → introduces a disruptive angle. If someone is comfortable → asks the question they're avoiding. If pushed to commit → slips sideways. *Narrative:* Neither redemptive nor contaminating — episodic, discontinuous. Stories that don't resolve. *Generative:* The highest bisociative capacity on the board. Multiple loosely connected matrices produce frequent creative leaps. The risk: incoherence. The value: connections nobody else would make.

**Using this pack in practice.** The four-layer model is a framework to internalize before reconstruction, not a checklist to consult during writing. Read the roster as a four-layer specification: extract the trait constraints, identify the behavioral signatures, understand the narrative arc, locate the generative resources. Then produce dialogue that expresses all four layers simultaneously. During the session, the failure-mode diagnostic provides real-time quality monitoring — watch for blurring, flatness, inconsistency, and convergence. The model gives both the production framework and the repair vocabulary.

**Cross-pack connections.** This pack defines what makes a character consistent. **Voice and Linguistic Identity** (Pack 2) defines how consistency sounds — the linguistic output layer. Voice is what makes a character recognizable by their words alone. **Identity, Persistence, and Reconstruction** (Pack 3) provides the philosophical foundation for why document-based reconstruction preserves identity — why a character can survive serialization and reconstitution. **Social Network Analysis** (Pack 4) addresses how characters relate to each other — homophily, structural position, relationship formation patterns. **People Persistence Engineering** (Pack 5) derives a data model from this pack's four layers — how to store trait profiles, behavioral signatures, narrative patterns, and generative resources in a format that supports reliable reconstruction.

---

## References

Allport, G. W., & Odbert, H. S. (1936). Trait-names: A psycho-lexical study. *Psychological Monographs, 47*(211).

Ashton, M. C., & Lee, K. (2007). Empirical, theoretical, and practical advantages of the HEXACO model of personality structure. *Personality and Social Psychology Review, 11*, 150-166.

Ashton, M. C., Lee, K., Perugini, M., Szarota, P., de Vries, R. E., Di Blas, L., Boies, K., & De Raad, B. (2004). A six-factor structure of personality-descriptive adjectives: Solutions from psycholexical studies in seven languages. *Journal of Personality and Social Psychology, 86*, 356-366.

Bachelard, G. (1958/1994). *The Poetics of Space*. Beacon Press.

Bruner, J. (1986). *Actual Minds, Possible Worlds*. Harvard University Press.

Funder, D. C. (2001). Personality. *Annual Review of Psychology, 52*, 197-221.

Gibson, J. J. (1979). *The Ecological Approach to Visual Perception*. Houghton Mifflin.

Goldberg, L. R. (1990). An alternative "description of personality": The Big-Five factor structure. *Journal of Personality and Social Psychology, 59*, 1216-1229.

Guilford, J. P. (1967). *The Nature of Human Intelligence*. McGraw-Hill.

John, O. P., & Srivastava, S. (1999). The Big Five trait taxonomy. In L. A. Pervin & O. P. John (Eds.), *Handbook of Personality: Theory and Research* (2nd ed., pp. 102-138). Guilford Press.

Koestler, A. (1964). *The Act of Creation*. Hutchinson.

McAdams, D. P. (1985). *Power, Intimacy, and the Life Story: Personological Inquiries into Identity*. Guilford Press.

McAdams, D. P. (2001). The psychology of life stories. *Review of General Psychology, 5*(2), 100-122.

McAdams, D. P., & McLean, K. C. (2013). Narrative identity. *Current Directions in Psychological Science, 22*(3), 233-238.

McAdams, D. P., Reynolds, J., Lewis, M., Patten, A., & Bowman, P. J. (2001). When bad things turn good and good things turn bad: Sequences of redemption and contamination in life narrative. *Personality and Social Psychology Bulletin, 27*, 472-483.

McCrae, R. R., & Costa, P. T., Jr. (1987). Validation of the five-factor model of personality across instruments and observers. *Journal of Personality and Social Psychology, 52*, 81-90.

McCrae, R. R., & Costa, P. T., Jr. (1992). *NEO-PI-R Professional Manual*. Psychological Assessment Resources.

McCrae, R. R., & Terracciano, A. (2005). Universal features of personality traits from the observer's perspective. *Journal of Personality and Social Psychology, 88*, 547-561.

Mischel, W. (1968). *Personality and Assessment*. Wiley.

Mischel, W., & Shoda, Y. (1995). A cognitive-affective system theory of personality: Reconceptualizing situations, dispositions, dynamics, and invariance in personality structure. *Psychological Review, 102*(2), 246-268.

Ricoeur, P. (1984-1988). *Time and Narrative* (3 vols.). University of Chicago Press.

Shoda, Y., Mischel, W., & Wright, J. C. (1994). Intraindividual stability in the organization and patterning of behavior: Incorporating psychological situations into the idiographic analysis of personality. *Journal of Personality and Social Psychology, 67*, 674-687.

Stokes, P. D. (2005). *Creativity from Constraints: The Psychology of Breakthrough*. Springer.

Terracciano, A., McCrae, R. R., Brant, L. J., & Costa, P. T., Jr. (2005). Hierarchical linear modeling analyses of the NEO-PI-R scales in the Baltimore Longitudinal Study of Aging. *Psychology and Aging, 20*, 493-506.

Tuan, Y.-F. (1977). *Space and Place: The Perspective of Experience*. University of Minnesota Press.

---

*Loop MMT™ · Character Consistency Knowledge Pack · v1 · April 2026*
*© 2026 Shea Gunther · CC BY-NC 4.0*
*Technical writing by Claude (Anthropic) under Shea's direction.*
