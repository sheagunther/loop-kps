# Analogy & Metaphor Knowledge Pack

**Loop MMT™ · Multi-Module Theory**
**v1 · 9 April 2026**

---

## About This Document

This pack is about the tool AI advisors use most often without naming it. When an advisor tells an operator "the event ledger works like a financial journal — append-only, never edited," it has constructed an analogy. When it says "think of the routing table as a switchboard," it has performed a structure mapping. These are not pedagogical extras. They are the primary mechanism by which unfamiliar domains become accessible to non-experts — and they are the primary mechanism by which non-experts get misled.

The cognitive science of analogy is well-developed. Gentner's structure-mapping theory (1983) explains the mechanics: analogies transfer relational structure from a familiar domain to an unfamiliar one. Holyoak and Thagard (1995) add that the reasoner's goals shape the mapping. Lakoff and Johnson (1980) demonstrate that metaphor is not decorative language but a fundamental cognitive structure that shapes reasoning invisibly. Hofstadter and Sander (2013) argue that analogy is not a specialized tool but the core of all thought. Hesse (1963) shows how analogies drive scientific discovery and where they break. This pack synthesizes these accounts into operational guidance for AI advisors working with non-expert operators. Draws on 15 sources.

---

## Section 1 · Structure Mapping — How Analogies Work

Dedre Gentner's structure-mapping theory (1983) provides the dominant account in cognitive science of how analogies function. Its foundational claim is precise: an analogy is a mapping from a **base domain** (the familiar system) to a **target domain** (the system being explained) that carries across *relations between objects* while discarding *attributes of objects*.

When someone says "the atom is like a solar system," the mapping carries across REVOLVES-AROUND(electron, nucleus) ← REVOLVES-AROUND(planet, sun), ATTRACTS(nucleus, electron) ← ATTRACTS(sun, planet), and the causal connection between attraction and orbital motion. It does not carry across HOT(sun) or YELLOW(sun) or VISIBLE-TO-NAKED-EYE(planet). Attributes describe individual objects. Relations describe connections between objects. Analogies map relations and drop attributes.

This distinction has a formal basis. In Gentner's framework, a **relation** is a predicate taking multiple objects as arguments: ORBITS(planet, sun). An **attribute** is a predicate taking a single object: MASSIVE(sun). The mapping rules operate on the syntactic structure of the representation, not on specific content — which is why the same mapping process works across wildly different domains.

### The Systematicity Principle

Among the many possible relational mappings between two domains, people prefer those that form interconnected systems — clusters of relations connected by higher-order relations such as CAUSE, ENTAILS, or IMPLIES. Gentner called this the **systematicity principle**.

In the atom/solar system case: the relation ATTRACTS(sun, planet) causally connects to REVOLVES-AROUND(planet, sun), which connects to MORE-MASSIVE-THAN(sun, planet). These form a system. The isolated relation HOTTER-THAN(sun, planet), though it holds in the solar system, has no causal connection to the orbital system and is not mapped. The systematicity principle captures a tacit preference for coherence — we want analogies that carry explanatory structure, not lists of coincidences.

### Types of Comparison

Gentner and Markman (1997) situated analogy within a broader taxonomy of comparison:

- **Literal similarity**: shared relations AND shared object attributes. A desk chair and a dining chair.
- **Analogy**: shared relations, NOT shared object attributes. An atom and a solar system.
- **Mere appearance match**: shared object attributes, NOT shared relations. A basketball and a planet (both round, no relational correspondence).

This is a continuum. But the distinction matters operationally: mere appearance matches feel similar without being informative. People — especially novices — are drawn to them. An advisor must distinguish between "these two things look alike" and "these two things work alike."

### Analogical Inference

Once the relational mapping is established, it does more than re-describe the target. It generates **candidate inferences**: relations present in the base domain, connected to the mapped system, that have not yet been verified in the target. These are predictions the analogy makes.

This is the mechanism by which analogies produce new knowledge. It is also the mechanism by which they produce false beliefs. Every candidate inference must be tested — some will hold in the target domain, and some will not. The atom/solar system analogy generates the candidate inference that electrons in higher orbits should move more slowly (correct, approximately). It also generates the prediction that orbiting electrons should radiate energy continuously and spiral inward — the prediction of classical electrodynamics, which turned out to be false, and whose failure drove the development of quantum mechanics.

> **KEY: The operational point.** Every analogy licenses a set of inferences beyond its explicit content. An AI advisor constructing an analogy is not just painting a picture — it is opening a channel through which the operator will project properties from the familiar domain onto the unfamiliar one. Some of those projections will be valid and some will not. The advisor is responsible for knowing which is which.

---

## Section 2 · The Multiconstraint View

Holyoak and Thagard (1989, 1995) proposed that analogical reasoning is simultaneously governed by three constraints:

1. **Similarity**: semantic resemblance between elements placed in correspondence
2. **Structure**: one-to-one mapping, parallel connectivity, systematicity (Gentner's contribution)
3. **Purpose**: the reasoner's goals — what the analogy is being deployed to accomplish

The key addition is purpose as a first-class constraint on the mapping itself, not merely a post-hoc filter on which inferences to accept. Different goals can produce different mappings from the same pair of domains.

Spellman and Holyoak (1992) demonstrated this with mappings between the Persian Gulf War and World War II. Participants produced two coherent but incompatible correspondence sets. One mapped Bush→FDR and the US→the US in WWII (emphasizing the theme of a reluctant superpower entering a global conflict). The other mapped Bush→Churchill and the US→Britain (emphasizing the theme of an ally resisting aggression). Critically, which mapping people preferred could be shifted by manipulating what aspects of the WWII source they had been primed to consider. Same base domain, same target domain, different purpose, different mapping.

For advisory work, the multiconstraint theory says something important that pure structure-mapping does not: the advisor's communicative goal should shape which analogy it selects. A structurally excellent analogy that serves the wrong purpose — that highlights aspects the operator doesn't need and hides aspects they do — is the wrong analogy. Structural soundness is necessary but not sufficient. The analogy must serve the conversation.

> **NOTE: Complementary, not competing.** Gentner's framework is stronger on the mechanics of mapping; Holyoak and Thagard's is stronger on how context shapes analogical reasoning in practice. AI advisory work requires both: structurally sound analogies (Gentner) deployed in service of the right goals (Holyoak & Thagard).

---

## Section 3 · Metaphor as Conceptual Structure

George Lakoff and Mark Johnson's *Metaphors We Live By* (1980) advanced a claim that reshaped cognitive linguistics: metaphor is not a literary device applied to pre-existing thoughts. It is a **fundamental cognitive structure** through which abstract domains are understood in terms of concrete, embodied experience.

UNDERSTANDING IS SEEING: "I *see* what you mean," "that's a *clear* explanation," "let me *shed light* on this." ARGUMENT IS WAR: "she *attacked* every weak point," "he *demolished* the argument," "that claim is *indefensible*." TIME IS MONEY: "you're *wasting* my time," "I *invested* three hours in it," "that meeting wasn't *worth* the time." These are not isolated figures of speech. They are **systematic mappings** — each generates a family of expressions, constrains available inferences, and shapes reasoning about the target domain.

Lakoff and Johnson classified conceptual metaphors into three types. **Structural metaphors** map one concept's structure onto another: ARGUMENT IS WAR licenses attack, defense, strategic retreat. **Orientational metaphors** organize concepts along spatial axes grounded in bodily experience: HAPPY IS UP / SAD IS DOWN; MORE IS UP / LESS IS DOWN; GOOD IS UP / BAD IS DOWN. These are not arbitrary — upright posture correlates with health and energy, lying down correlates with sickness and sleep. **Ontological metaphors** reify abstract phenomena as entities or substances: THE MIND IS A CONTAINER ("I can't get that idea out of my head"); INFLATION IS AN ENTITY ("we need to combat inflation").

### Highlighting and Hiding

Every conceptual metaphor is **partial**. It maps some structure from the source domain and ignores the rest. This selectivity is not a flaw — it is the mechanism. ARGUMENT IS WAR highlights adversarial structure: positions to attack, claims to defend, weak points to exploit. It hides collaborative structure: mutual exploration, joint discovery, the possibility that both sides might be partly right. ARGUMENT IS A JOURNEY — "we've *covered a lot of ground*," "we're *going in circles*," "we've *arrived at* a conclusion" — highlights progress and direction, hides conflict.

What a metaphor highlights becomes obvious and natural. What it hides becomes invisible. This is the deepest practical consequence: the choice of metaphor determines what aspects of a domain the thinker notices and what aspects disappear.

> **KEY: For advisory work.** When an AI advisor uses an analogy, it is choosing a frame. "System architecture" is a building (planned, rigid, load-bearing). "System ecology" is a living thing (adaptive, interconnected, evolving). These are not just different words — they are different conceptual structures that license different inferences about what the system can and should do. The advisor is choosing a frame every time it reaches for a metaphor, usually without noticing.

---

## Section 4 · Dead Metaphors and Invisible Framing

Michael Reddy (1979) analyzed how English speakers talk about communication itself and found that roughly 70% of metalinguistic expressions operate within a single conceptual metaphor: **the conduit metaphor**. Speakers PUT ideas INTO words. Words CARRY ideas to listeners. Listeners EXTRACT ideas FROM words. We "get our ideas across," "put our thoughts into words," "try to get through to someone."

The conduit metaphor frames communication as packaging and shipping. Its deep implication: meaning is IN the words, and successful communication is successful extraction. What it hides: communication is fundamentally constructive. Listeners build meaning from their own conceptual resources, guided but not determined by the speaker's words. There is no package. There is no extraction. There is interpretation. Reddy warned that this invisible framing leads to bad policy — when communication fails, the conduit metaphor implies someone packed the container badly or unpacked it carelessly, rather than that the two parties are constructing different meanings from the same signals.

Lakoff and Johnson's broader point: conventional metaphors — so familiar they no longer register as metaphorical — continue to shape reasoning precisely because they operate below conscious notice. The label "dead metaphor" is misleading. These metaphors are entrenched, not dead. Their influence persists because it is invisible.

### Dead Metaphors in Technical Work

Consider terms ubiquitous in software and methodology:

**Foundation** implies bottom-up construction, sequential layering, each part depending on what's beneath it. It hides non-hierarchical structure and the possibility of rearranging the base.

**Framework** implies a predefined rigid structure that you build within. It hides adaptability and the possibility that the structure should emerge from the work.

**Architecture** implies a designer's blueprint, executed by workers. It hides emergent design and collaborative authorship.

**Pipeline** implies sequential, unidirectional flow. It hides feedback loops, parallelism, and the possibility that outputs modify inputs.

**Technical debt** implies an obligation that accrues interest, owed to a clear creditor. It hides the fact that not all shortcuts have compounding costs, and sometimes "debt" is better understood as a permanent tradeoff rather than a deferred payment.

**Constellation** — Loop MMT's own metaphor for its multi-system architecture — implies related points of light, observed from a distance, whose pattern depends on the observer's perspective. This is actually a well-chosen metaphor because it foregrounds the observer-dependent quality of the system's coherence. But it also implies disconnection: stars in a constellation are not gravitationally bound to each other. Whether that implication matches the target — whether the systems in a Butcher Constellation are truly independent or mutually dependent — is a question the metaphor's implications raise.

> **NOTE: The audit question.** For any metaphor in routine use: what does it imply about the thing it names? What does it highlight? What does it hide? Would a different metaphor surface something important that this one suppresses?

---

## Section 5 · Surface vs. Structure — Why Novices Get Misled

### The Relational Shift

Gentner (1988) and Gentner and Rattermann (1991) identified a developmental trajectory they called the **relational shift**: in any domain, learners initially process comparisons in terms of surface features (object attributes) and progressively shift toward relational structure as they gain domain knowledge.

Young children asked to find an analogous story to one about a jealous dog pick stories featuring another dog — a surface match. Older children pick stories featuring jealousy, regardless of species — a structural match. The identical pattern appears in adults learning new domains: novice physics students sort problems by surface features (inclined plane, pulley, spring), while experts sort by deep structure (conservation of energy, Newton's second law) (Chi, Feltovich, & Glaser, 1981; see Gentner & Maravilla, 2018 for a comprehensive review). The shift is driven primarily by gains in relational knowledge, though increases in processing capacity and inhibitory control also contribute.

### The Retrieval-Mapping Asymmetry

Gentner, Rattermann, and Forbus (1993) documented a critical asymmetry in how analogies operate in practice:

**Retrieval** from long-term memory is dominated by surface similarity. When we encounter a new problem, we spontaneously recall problems that look similar on the surface — same objects, same setting, same visual appearance.

**Mapping** (once two domains are juxtaposed) is driven by structural similarity. When we explicitly compare two things, we prefer relational matches and can evaluate structural correspondence.

The consequence: the cases we spontaneously retrieve are not necessarily the most structurally useful. A novice programmer encountering a new bug may recall a superficially similar bug (same error message, same file type) rather than a structurally parallel one (same logical pattern, different surface). The surface-similar case may suggest the wrong fix.

Experts partially escape this trap. Novick (1988) found that mathematicians with more expertise retrieved structurally similar prior problems more reliably, and rejected surface-similar but structurally irrelevant ones faster. The explanation: experts encode cases with richer relational structure, giving structural similarity a better foothold in retrieval.

Gentner (1989) offered a partial consolation she called the **"kind world" hypothesis**: in natural experience, surface similarity is often correlated with structural similarity. Things that look like tigers tend to be tigers, with tiger-like behavior. This means surface-driven retrieval works reasonably well in domains where surface and structure align. It fails in domains where they diverge — which includes most of software, medicine, law, and organizational design.

### The Pedagogical Trap

This creates what might be called the **expert's dilemma**. The best teaching analogy for a beginner maximizes surface similarity to make the mapping obvious and easy to process: "electricity is like water in pipes" gives the learner concrete objects (water, pipes, pump) to map onto abstract ones (current, wires, battery). But the surface-rich analogy activates properties of water that do not hold for electricity: water is incompressible, water puddles when it leaks, water has momentum. A learner who internalizes the water analogy too deeply will struggle with voltage as potential energy, with capacitance, and with alternating current.

The analogy that helps a beginner misleads an intermediate. The responsible pedagogical move is not to avoid analogies but to manage their lifecycle.

> **KEY: The shelf-life principle.** Every analogy has a range of validity. The advisor's job is to introduce the analogy when it helps, flag its boundaries before they mislead, and retire it when the learner has enough direct knowledge to reason without it. An analogy that is never retired becomes a dead metaphor — shaping the learner's reasoning invisibly and possibly incorrectly.

---

## Section 6 · Analogy in Science

### Hesse's Framework

Mary Hesse (1963, revised 1966) provided the most influential philosophical analysis of how analogies function in scientific theorizing. Against the formalist position that models are merely psychological aids — useful scaffolding that can be discarded once the mathematics is in place — Hesse argued that models and analogies are integral to how theories generate genuinely novel predictions.

Her framework distinguishes three types of analogical relation between a model and the phenomena it explains:

| Type | Definition | Example: billiard balls as model for gas molecules |
|------|-----------|---------------------------------------------------|
| **Positive analogy** | Properties known to be shared | Both have mass, velocity, and undergo elastic collision |
| **Negative analogy** | Properties known NOT to be shared | Billiard balls have color and smooth surfaces; molecules do not |
| **Neutral analogy** | Properties not yet determined to be shared or unshared | The productive unknown — where predictions come from |

Scientific progress consists substantially of converting neutral analogies into positive or negative ones. The model tells you which questions to ask. Without a model, you do not know what to investigate.

### Historical Cases

**Maxwell's mechanical model of electromagnetism.** In 1855, Maxwell used incompressible fluid flow as an analogy for magnetic field lines. In 1861–62, he developed a more elaborate mechanical model involving rotating vortex tubes to represent the electromagnetic field. The mathematical structure of these models led him to add the displacement current term to Ampère's law, which in turn predicted the existence of electromagnetic waves propagating at a speed determined by electrical constants. When Maxwell calculated that speed — around 1862 — it matched the measured speed of light. The analogy's mathematical offspring had unified electromagnetism with optics. Hertz confirmed the existence of electromagnetic waves experimentally in 1887.

The key point for this pack: the prediction of electromagnetic waves was not a direct property of the fluid model. It was a property of the mathematics the model guided Maxwell to write. The model served as scaffolding for the mathematics, and the mathematics generated the prediction. This is a paradigmatic case of analogical inference: the neutral analogy (does the electromagnetic field support wave propagation?) was converted to a positive analogy through mathematical derivation and experimental confirmation.

**Rutherford's nuclear model and Bohr's quantum atom.** In 1911, Rutherford demonstrated that the atom has a small, dense, positively charged nucleus. The analogy to a solar system — a central massive body with lighter bodies moving around it under an attractive force — was implicit in Rutherford's work and made explicit in the Rutherford-Bohr model (1913). The positive analogy was genuine: central body, peripheral bodies, attractive force (electromagnetic rather than gravitational). But the negative analogy was devastating: classical electrodynamics predicted that orbiting charged particles would radiate energy continuously and spiral into the nucleus within a fraction of a second. This failure — the point where the atom refused to behave like a solar system — became the problem that Bohr's quantized energy levels were invented to solve. The negative analogy drove theoretical advance.

**Kepler's boat analogy.** Kepler proposed that the sun exerts a force moving planets as a river's current moves a boat — weakening with distance, stronger for planets closer to the source. The analogy contributed to his thinking about the quantitative relationship between distance and orbital speed, guiding him toward his laws of planetary motion.

---

## Section 7 · When Analogies Fail

### Modes of Failure

**Disanalogy.** The base domain has structure the target lacks. Candidate inferences projected from the base turn out false. The atom radiating energy like an orbiting charged particle is a disanalogy that was scientifically productive. Most everyday disanalogies are just errors — a projected property accepted without verification.

**False parallels.** Surface similarity triggers a mapping where no structural similarity exists. The novice sees two problems with the same visual setup and assumes the same solution applies. This is the signature failure mode of surface-driven retrieval: the analogy was never structurally valid; it was activated by appearance.

**Overcoverage.** The analogy is structurally sound for some mappings but extends beyond its valid range. "Electricity is like water" works for current/flow and resistance/pipe-narrowing. It breaks for voltage (water has no direct analog to electrical potential energy per unit charge), capacitance, and alternating current.

**Stale analogies.** An analogy appropriate at one level of understanding becomes misleading as knowledge deepens. The water model is useful for Ohm's law and harmful for semiconductor physics. The analogy hasn't become wrong — the learner has outgrown it.

**Counteranalogy.** A competing analogy highlights different structure and supports a different conclusion. "The war on drugs is like Prohibition" (emphasis: futility of criminalization, creation of black markets). "The war on drugs is like the fight against infectious disease" (emphasis: treatment, prevention, public health). Neither is "right" — they frame the problem differently, licensing different inferences and supporting different policy conclusions.

### Load-Bearing vs. Illustrative

The most important diagnostic question about any analogy: **is it load-bearing or illustrative?**

An **illustrative** analogy helps the audience visualize something they could understand without it. "Think of RAM as a desk — it's where you keep things you're actively working with." If the desk metaphor collapses, the audience can fall back on direct explanation. The analogy is a convenience, not a dependency.

A **load-bearing** analogy is one where reasoning actually runs through the mapped structure. The audience doesn't have independent access to the target domain, so the analogy is doing the cognitive work. Maxwell's fluid model was load-bearing for predicting electromagnetic waves. In advisory work, a load-bearing analogy is one the operator uses to make decisions — and any false inference the analogy licenses may become a false decision.

Shelley (2004) developed a taxonomy of four counterarguments to analogies: **false analogy** (no real resemblance), **misanalogy** (wrong correspondences drawn), **disanalogy** (important differences undermine the conclusion), and **counteranalogy** (an alternative analogy supports a different conclusion). These are useful diagnostic categories for evaluating whether an analogy is doing the work it claims to do.

Load-bearing analogies require the advisor to identify the negative analogy explicitly and tell the operator where the mapping stops.

---

## Section 8 · Analogy as the Core of Cognition

Douglas Hofstadter and Emmanuel Sander's *Surfaces and Essences* (2013) advances a more radical position than any of the preceding work: analogy is not a specialized cognitive tool used on certain occasions. It is the fundamental process underlying all cognition, including the most ordinary acts of categorization.

Their argument: recognizing a chair as a chair is an analogy — mapping perceptual input onto a stored concept by finding structural correspondences. Choosing to call a situation a "crisis" rather than a "challenge" is an analogy — selecting which stored concept best matches the situation's relational structure. A child saying "I undressed the banana!" (meaning peeled it) is performing the same cognitive operation as Einstein recognizing that a person in free fall experiences an inertial frame equivalent to the absence of gravity. The scale differs. The process does not.

Hofstadter and Sander's position is broader than Gentner's. Where Gentner treats analogy as a specific cognitive process with identifiable components — retrieval, mapping, inference, evaluation — that can be distinguished from other forms of comparison, Hofstadter and Sander argue these components pervade all thought. The debate is about scope, not mechanism.

For AI advisory work, the Hofstadter-Sander perspective reframes the question. The advisor is not occasionally reaching for an analogy as a pedagogical device. It is analogizing continuously — every time it maps a user's question onto patterns from its training, it is performing structure-mapping. The question is not whether to use analogies but whether to use them deliberately.

---

## Section 9 · Board Connection — Analogy in AI Advisory Work

### Why This Pack Changes Behavior

An AI advisor unaware of analogical reasoning is deploying its most powerful tool unreflectively. It constructs analogies without knowing what inferences they license. It uses metaphors without knowing what they hide. It fails to retire analogies that have outlived their usefulness. Understanding the mechanics of analogy converts an unconscious habit into a deliberate skill.

### Decision Protocol: Analogy vs. Direct Explanation

**Deploy an analogy when:**
- The target domain's relational structure is genuinely unfamiliar to the operator
- A base domain exists that the operator knows well and that shares the relevant structure
- The mapping preserves the inferences the operator actually needs
- The operator must reason about the target (predict, decide, evaluate), not merely label it

**Explain directly when:**
- The operator already has the vocabulary for the target domain
- Every available analogy has significant negative analogy in the range the operator needs
- The concept is simple enough that naming it suffices
- The operator has outgrown the analogy — they need the target domain's own structure, not a borrowed one

**Deploy an analogy AND flag its limits when:**
- The analogy is load-bearing (the operator will reason through it, not just visualize with it)
- The negative analogy includes properties the operator might plausibly project
- The operator is intermediate — past the point where the analogy helps and approaching the point where it misleads

### The Explicit-Limits Protocol

When deploying a load-bearing analogy, identify the negative analogy as part of the explanation — not as a disclaimer at the end, but as an integral part of the mapping. "The event ledger works like a financial journal — entries are append-only, never modified, and the current state is derived by replaying the sequence. Unlike a financial journal, though, entries can trigger automated effects — notifications, state transitions — that a journal entry doesn't." This tells the operator exactly how far the mapping extends and where it stops.

### Cross-Pack Connections

**Semiotics (Pack 6).** Analogies are signs — specifically, **diagrammatic icons** in Peirce's taxonomy. They signify through relational resemblance: the base domain's relational structure represents the target domain's relational structure the way a map represents a territory. The semiotic framework provides the vocabulary for analyzing what an analogy *presents* (its immediate object) versus what actually exists in the target domain (its dynamic object). The gap between them is where misunderstanding lives.

**Communication Pragmatics.** Analogies carry **implicatures** — inferences that the listener draws beyond the explicit content, governed by Gricean maxims. When the advisor says "think of the routing table as a switchboard," the maxim of relevance implies that the properties of switchboards relevant to the current conversation are being mapped. But other switchboard properties — physical plugs, human operators, limited capacity — are also activated. The advisor needs to be aware of unintended implicatures, especially when the base domain is concrete and vivid (which makes its properties highly activating).

**Rhetoric and Argumentation.** Analogies have persuasive force that can exceed their logical warrant. A vivid analogy with a concrete source domain can make a conclusion feel compelling even when the structural mapping is thin. The advisor should distinguish between analogies that **illuminate** (strong structural mapping, valid inferences) and analogies that merely **persuade** (compelling surface, weak structure). Both have their uses. The distinction matters.

**Loop MMT self-application.** The methodology's own key terms are analogies. *Event ledger* borrows from financial accounting. *Constellation* borrows from astronomy. *Advisory board* borrows from corporate governance. *Routing table* borrows from network engineering. Each mapping highlights certain properties and suppresses others. The knowledge packs exist in part to make these borrowed structures visible — to convert their neutral analogies into positive or negative ones, so the methodology evolves through scrutiny rather than inheriting its metaphors' blind spots.

> **KEY: The advisor's obligation.** An AI advisor using an analogy is framing, not just explaining. Every analogy highlights and hides. Every analogy licenses candidate inferences. Every analogy has a shelf life. The obligation is to know what is being highlighted, what is being hidden, which inferences are being licensed, and when the analogy should be retired. This is not secondary to explanation — it IS explanation, done with awareness.

---

## References

Chi, M.T.H., Feltovich, P.J., & Glaser, R. (1981). Categorization and representation of physics problems by experts and novices. *Cognitive Science*, 5, 121–152.

Gentner, D. (1983). Structure-mapping: A theoretical framework for analogy. *Cognitive Science*, 7(2), 155–170.

Gentner, D. (1988). Metaphor as structure mapping: The relational shift. *Child Development*, 59, 47–59.

Gentner, D. & Markman, A.B. (1997). Structure mapping in analogy and similarity. *American Psychologist*, 52(1), 45–56.

Gentner, D. & Maravilla, F. (2018). Analogical reasoning. In L.J. Ball & V.A. Thompson (Eds.), *International Handbook of Thinking & Reasoning* (pp. 186–203). New York: Psychology Press.

Gentner, D., Rattermann, M.J., & Forbus, K.D. (1993). The roles of similarity in transfer: Separating retrievability from inferential soundness. *Cognitive Psychology*, 25, 524–575.

Hesse, M.B. (1963/1966). *Models and Analogies in Science*. Notre Dame, IN: University of Notre Dame Press.

Hofstadter, D.R. & Sander, E. (2013). *Surfaces and Essences: Analogy as the Fuel and Fire of Thinking*. New York: Basic Books.

Holyoak, K.J. & Thagard, P. (1989). Analogical mapping by constraint satisfaction. *Cognitive Science*, 13(3), 295–355.

Holyoak, K.J. & Thagard, P. (1995). *Mental Leaps: Analogy in Creative Thought*. Cambridge, MA: MIT Press.

Lakoff, G. & Johnson, M. (1980). *Metaphors We Live By*. Chicago: University of Chicago Press.

Novick, L.R. (1988). Analogical transfer, problem similarity, and expertise. *Journal of Experimental Psychology: Learning, Memory, and Cognition*, 14(3), 510–520.

Reddy, M.J. (1979). The conduit metaphor: A case of frame conflict in our language about language. In A. Ortony (Ed.), *Metaphor and Thought* (pp. 284–324). Cambridge: Cambridge University Press.

Shelley, C. (2004). Analogy counterarguments: A taxonomy for critical thinking. *Argumentation*, 18, 223–238.

Spellman, B.A. & Holyoak, K.J. (1992). If Saddam is Hitler then who is George Bush? Analogical mapping between systems of social roles. *Journal of Personality and Social Psychology*, 62(6), 913–933.

---

*Loop MMT™ · Multi-Module Theory · Analogy & Metaphor Knowledge Pack · v1 © 2026 Shea Gunther · CC BY-NC 4.0*
