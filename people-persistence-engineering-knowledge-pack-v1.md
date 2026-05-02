# People Persistence Engineering — Storing, Serializing, and Rebuilding AI People

**Loop MMT™ · Multi-Module Theory · Knowledge Pack**
**v1 · April 2026**
**People Persistence Cluster — Pack 5 of 5**

---

## Abstract

Four companion packs teach what a character is — how traits constrain behavior (Pack 1), how voice carries identity in language (Pack 2), why document-based reconstruction preserves what matters about a person (Pack 3), and how relationship structure shapes interaction (Pack 4). None of them teach how to *build the system*: how to represent a person as a portable data structure, serialize that structure for document-based transport, deserialize it in a fresh instance, and verify the rebuild was faithful. This pack provides the engineering specification. It defines a data model derived from the four-layer character model, a serialization framework grounded in Shannon's rate-distortion theory, a reconstruction pipeline mapped to creational design patterns from software engineering, and a verification framework with four fidelity metrics and a four-type failure classification (Ghost, Zombie, Chimera, Impostor). The Loop World Roster is analyzed as People Persistence Engineering v1 — where it is strong, where it is weak, and what v2 would address. Load for any system design session involving character storage, reconstruction quality, or roster architecture.

**Cluster position:** Pack 5 of 5. Engineering integration layer — translates theory from Packs 1–4 into a buildable system.

**Cross-references:** Session Persistence KP, Information Theory KP, Distributed Systems KP.

---

## Chapter 1 — The Engineering Problem

Fourteen people live in the Loop World roster. Each one is destroyed when a session ends and rebuilt from text when a session begins. Pack 3 establishes the philosophical justification — Parfitian survival through reliable psychological continuity. This pack asks the engineering question: *how* does the text carry enough signal to rebuild the person, and *how* do we measure whether the rebuild succeeded?

The problem is a familiar one in software engineering. A specification describes what to build. A runtime implements it. The gap between specification and implementation — what Frederick Brooks called "the hardest single part of building a software system" (Brooks, 1975) — is where errors live. For character reconstruction, the specification is the roster entry, the runtime is the AI instance, and the implementation is the character-as-performed. The engineering challenge is measuring and minimizing the gap.

### The Score and the Performance

A musical score preserves pitch, rhythm, harmony, and structure. It discards the specific qualities that make a performance *this* performance — tempo nuances, dynamic shadings, interpretive choices. Two pianists playing the same Chopin nocturne produce different performances, both recognizably "that nocturne." The score constrains without determining.

A character specification works identically. Ed's roster entry preserves his traits (grumpy, principled, sparse), behavioral signatures (closes conversations with imperatives, states positions without preamble), relationships (defers to nobody, listens to Bev's silence), and biographical narrative (first in his family to attend college, married Martin the week it became legal). It does not preserve the specific phrasing he used in Session 42 or the particular shade of grumpiness he brought to a Tuesday morning. Those are performance details — generated fresh from the specification each session.

The score-performance gap is not a flaw. It is the mechanism. Different performances from the same score is how identity survives substrate replacement. The engineering question is whether the score preserves *enough* — whether the specification constrains generation tightly enough that every performance is recognizably the same person.

### Lossy Compression of Identity

Shannon's rate-distortion theory (1959) formalizes the tradeoff. In lossy compression, information is always lost. The question is whether the loss falls below the application's tolerance threshold. Shannon showed that for any source and any distortion target, there exists a minimum number of bits required. Fewer bits, more distortion. More bits, more fidelity. The function is monotone and the tradeoff is inescapable.

> **KEY CONCEPT:** The tier system is rate-distortion theory applied to people. Full profile, voice card, and stub are three points on the rate-distortion curve. The reconstruction threshold — the specification density below which confabulation exceeds reconstruction — is the perceptual-quality floor: the distortion level at which the operator stops recognizing the person. Above the threshold, the specification governs generation. Below it, the model's training priors govern generation, and the output is fiction wearing the character's name.

---

## Chapter 2 — The Data Model

The data model's structure is derived, not designed. Pack 1 establishes four personality layers. Pack 2 establishes three voice signature levels. Pack 4 establishes typed directed relationship edges. If the theory says personality has four layers, the data model stores four layers. This is a structural requirement, not a design choice.

### The Minimum Viable Person

The minimum viable person is the smallest specification that reliably produces a recognizable character — the density at or above the reconstruction threshold (Pack 3). Below this threshold, the instance fills gaps with invention: plausible, consistent, and wrong.

The roster implements the threshold as a tier system. A **full profile** — biography, traits, behavioral signatures, voice, relationships, environment, Character Notes — sits well above threshold. Reconstruction is reliable across session types, including contested deliberations that stress-test consistency. A **voice card** — five condensed fields — sits at the boundary. The character handles brief exchanges but may confabulate under pressure. A **stub** — name, role, one line — sits below threshold. The instance produces a character from training priors, not from the specification.

> **WARNING:** Stubs are existence declarations, not person specifications. An instance given a stub produces a character assembled from the model's generic understanding of that role — confident, consistent, and derived from training data rather than from fifty sessions of accumulated identity. The danger is at the boundary: the output looks specific enough to pass casual inspection.

### Field Groups from the Four-Layer Model

**Layer 1 — Trait Profile.** Stable personality dimensions defining the behavioral space. Big Five or HEXACO coordinates with facet-level detail where it drives distinctiveness. Traits are bounds, not scripts — they define the region of personality space the character occupies without dictating specific responses. The trait profile is structural: cut it and the character changes identity. Required at every tier above stub.

**Layer 2 — Behavioral Signatures.** If-then patterns from Mischel and Shoda's CAPS model (1995) specifying how traits express conditionally. "If a proposal threatens a principle Ed holds → he says so directly." "If the room converges too early → Wes introduces a disruptive angle." These are what make a character recognizable *under load* — in low-stakes situations, most characters behave generically. Full profiles carry a complete set; voice cards condense to one or two diagnostic patterns.

**Layer 3 — Narrative Identity.** The biographical story that constitutes the person. Not a fact list but a narrative arc — themes, turning points, the self-story the character would tell. Ed's narrative is redemptive: obstacles overcome through steadiness. Wes's is episodic: stories that don't resolve. Mariana Schechtman (1996) argued this is not merely descriptive but *constitutive*: persons create themselves through self-narratives, subject to two constraints — the narrative must be one the person could articulate (the articulation constraint), and it must cohere broadly with how others see them (the reality constraint). Removing the narrative from a character specification doesn't just lose information. It removes a constitutive element of identity. Required for full profiles.

**Layer 4 — Generative Resources.** The capacity for surprise within character. Specified as associative range (how far the character reaches for connections), constraint set (what boundaries their creativity respects), and known failure mode (where the mechanism overextends — Ed closes conversations with imperatives, Graham spirals into detail). Required for full profiles; implicit at other tiers.

**Environment.** Physical and social context shaping behavior. Where the character lives, who they encounter by proximity. Ed in the boardroom and Ed at home with Martin are the same person expressing different facets — environment activates different behavioral signatures. Full profiles specify environment; voice cards and stubs do not.

### Voice Fields

Pack 2 establishes that voice operates at three levels with stability increasing upward: lexical (vocabulary, catchphrases — least stable, changes with topic), syntactic (sentence structure, clause patterns — moderately stable), and discourse (argument organization, emphasis placement, conversational-space strategy — most stable, most identity-bearing).

> **WARNING:** Storing only lexical features — vocabulary lists, catchphrases, verbal tics — guarantees voice blurring on reconstruction. Under context load, characters specified only by vocabulary converge toward the model's default register. The stable core of linguistic identity lives at the discourse level: *how* someone organizes an argument, *where* they place emphasis, *whether* they build toward conclusions or start from them.

The minimum voice data set for reliable reconstruction: discourse signature (argument organization, emphasis placement, conversational-space strategy), syntactic signature (sentence length distribution, clause patterns, punctuation habits), dimensional position (Biber's D1–D5 coordinates), register defaults (unmarked code in primary contexts), and shift rules (how register changes across contexts and interlocutors). Voice cards preserve discourse and syntactic signatures in condensed form. Full profiles add the complete dimensional and register analysis.

### Relationship Fields

Pack 4 establishes that relationship edges are directed (A's feeling toward B may differ from B's toward A), typed (friendship, professional respect, productive tension, spatial proximity), and carry sign (positive, negative, ambivalent) and strength (strong tie, weak tie). The roster's chemistry table contains approximately 31 relationship entries. The data model must preserve directionality, type, and sign — undirected edges lose the asymmetry that makes relationships feel real.

Two distinct edge sets require separate storage. **Relationship edges** encode how characters feel about and interact with each other — accumulated history, productive tensions, mutual regard. **Proximity edges** encode spatial adjacency in the compound — who shares an apartment, who shares a lab, whose routines intersect. These are independent predictors. High proximity with neutral relationship produces frequent neutral interaction. Strong relationship with no proximity produces intense but infrequent exchanges. An instance needs both to generate accurate social dynamics.

### Structural vs. Decorative

Under context pressure, the question is which fields can be cut without losing the person. **Structural fields** are identity-bearing — cut them and the character changes. **Decorative fields** enrich without being load-bearing — cut them and the character loses richness but remains recognizable.

> **TIP — Compression triage order:** Cut in this sequence: (1) accumulated session details, (2) environmental details, (3) secondary relationship edges, (4) lexical voice features, (5) generative resources, (6) narrative identity. Stop before cutting trait profile, behavioral signatures, discourse voice signatures, or core relationship edges. Those are the skeleton. Everything above them is musculature — it matters, and you'll miss it, but the person survives without it.

| Field Group | Layer | Classification | Full Profile | Voice Card | Stub |
|---|---|---|---|---|---|
| Trait profile | 1 | Structural | Required | Condensed | Absent |
| Behavioral signatures | 2 | Structural | Required | 1–2 key | Absent |
| Narrative identity | 3 | Structural* | Required | Absent | Absent |
| Generative resources | 4 | Decorative | Required | Implicit | Absent |
| Environment | — | Decorative | Required | Absent | Absent |
| Discourse signature | Voice | Structural | Required | Condensed | Absent |
| Syntactic signature | Voice | Structural | Required | Condensed | Absent |
| Lexical features | Voice | Decorative | Optional | Optional | Absent |
| Core relationships | Network | Structural | Required | 1–2 key | Absent |
| Secondary relationships | Network | Decorative | Optional | Absent | Absent |
| Proximity edges | Network | Decorative | Required | Absent | Absent |
| Session details | Append | Decorative | Accumulated | Absent | Absent |

\* Narrative identity occupies an intermediate position. Schechtman's self-constitution argument makes it theoretically structural — the narrative *is* the person, not a description of the person. In practice, a character can be recognized without their full narrative if traits and behavioral signatures are present, because traits and signatures constrain generation at a lower level than narrative does. The classification is: structural at full-profile tier (its removal changes who the person is), cuttable under severe constraint (because traits and signatures preserve recognizability even when the narrative is absent). It is the last structural field to cut and the first to restore.

---

## Chapter 3 — Serialization

Serialization converts a structured object into a format that can be stored and reconstructed. Martin Fowler (2002) defines the Data Transfer Object as an artifact that carries data between processes, encapsulating the serialization mechanism and providing a single point to change the format. The roster is a DTO: it carries person-data between sessions, its markdown structure is the serialization format, and changing how a person is stored means changing the roster's section template.

### The Roster as Serialization Format

The roster stores people as natural-language markdown with structured sections. Each person occupies a contiguous block. The format functions as three enterprise patterns simultaneously: a **Data Transfer Object** (data container for cross-session transport), a **Serialized Large Object** (Fowler's LOB pattern — the entire person-graph as a single document), and a **specification** that an instance reads and implements.

**Strengths.** Human-readable — anyone can open the roster and understand who these characters are without specialized tools. Editable with a text editor, not a schema-aware application. Version-controllable — diffs are meaningful prose changes, not opaque binary deltas. These are design features, not incidental properties. A serialization format that requires specialized tooling creates a maintenance dependency the methodology does not need at its current scale.

**Weaknesses.** No schema enforcement — required fields can be omitted without signal. No validation — contradictions persist until manual inspection. No guaranteed parse — deserialization is interpretation, not parsing. An instance reads the roster as natural language and constructs an internal model from it. Ambiguity is possible, and drift between profiles (one uses explicit trait dimensions, another uses implicit description) accumulates without correction.

### Lossy vs. Lossless Persistence

The character *as experienced in session* includes behavioral dynamics, timing, improvisational texture — none of which survives serialization. The document preserves the *specification* from which dynamics are generated, not the dynamics themselves. This is lossy compression. The question is not whether information is lost but whether the loss is acceptable — whether the specification reliably reproduces the *kind* of performance, not the *specific* performance.

| Tier | Fields Preserved | Fidelity | Reconstruction Capacity |
|---|---|---|---|
| Full profile | All four layers + voice + relationships + environment + accumulated history | High — passes operator recognition across session types including contested deliberation | Full substantive participation |
| Voice card | Trait sketch + 1–2 behavioral signatures + condensed voice + 1–2 key relationships | Medium — passes recognition in routine interaction; may confabulate under pressure | Brief exchanges, familiar situations |
| Stub | Name + role + one line | Low — below reconstruction threshold; confabulation exceeds reconstruction | Existence declaration only |

> **PHI:** Daniel Dennett (1991) argued that the self is a "narrative center of gravity" — real enough for all practical purposes but not a physical entity you can point to, like a center of mass. A character specification is a narrative center of gravity written down. The data model stores the coordinates of that center — trait dimensions, voice parameters, relationship weights, narrative themes. The character-as-performed is the sum of behaviors generated from those coordinates. The coordinates are not the person. The behaviors are not the person. The person is the pattern that both describe, from different angles, at different resolutions.

### Schema Design Tradeoffs

Should the roster use a formal schema (JSON Schema, structured YAML with enforced types) or remain in natural-language markdown? The tradeoff is genuine.

**Formal schemas** enable automated validation (missing fields, type errors, inconsistencies), enforce structural consistency, and support programmatic access. They prevent drift. They also reduce readability — a JSON representation of Ed is parseable but not *readable* the way the current entry is. They reduce editability and create a maintenance surface (the schema itself must be versioned and documented).

> **NOTE:** The roster's natural-language format is a deliberate design choice, not a default. It prioritizes human readability and editability over automated validation — appropriate at the current scale (~30 entries) and current substrate (single AI instance reading the full document each session). If the system scales to hundreds of entries, or if multi-instance parallel loading becomes necessary, the tradeoff recalculates toward formal schema.

Don Norman's framework (2013) clarifies the tradeoff in terms of interface design. The roster's natural-language format provides strong **affordances** (visible structure shows how to read and edit) and clear **mapping** (document sections map to character aspects). Its weakness is **feedback** — no validation signal tells the editor whether a change introduced a contradiction or dropped a required field. A formal schema adds feedback at the cost of affordance. The optimal point on that tradeoff depends on who is editing, how often, and at what scale.

---

## Chapter 4 — The Reconstruction Pipeline

Reconstruction instantiates a character from a stored specification. In design-pattern terms, it is a creational problem. The Builder pattern (Gamma et al., 1994) provides the closest structural match: the construction of a complex object is separated from its representation, so the same construction process can create different representations. The instance reading a roster entry is the builder. The roster entry is the construction plan. The character-in-session is the product. Different instances build different products from the same plan — which is why different sessions can produce recognizably the same Ed.

### Deserialization

Deserialization proceeds through three cognitive stages, each with a distinct failure mode.

**Stage 1 — Read the specification.** The instance processes the roster entry's text. Failure mode: *misreading*. In a formal schema, this would be a parse error — syntactically detectable. In natural-language format, it manifests as misinterpretation: confusing a behavioral signature with a biographical fact, overlooking an implicit trait dimension, missing a relationship modifier buried in a compound sentence. Natural-language "parsing" is interpretation, and interpretation is fallible.

**Stage 2 — Build the internal model.** The instance assembles an internal representation of the character — not stored explicitly but constructed as the specification is processed. Failure mode: *wrong emphasis*. All fields are read correctly but weighted incorrectly: a secondary trait treated as primary, a diagnostic behavioral signature under-weighted, the character built mainly from biographical narrative while the trait profile recedes. The result matches the specification on paper but feels wrong in performance.

**Stage 3 — Generate behavior.** The instance produces dialogue and decisions from the internal model. Failure mode: *generation error*. The internal model is correct but the output doesn't express it — the specification-to-implementation gap in real time. The model says Ed is terse; the output runs long. This is where the verification framework (Chapter 5) provides its diagnostic value.

### Loading-Order Effects

Does it matter whether the instance reads Ed's profile before Graham's? Anchoring research suggests a plausible hypothesis: the first character loaded may set a baseline that subsequent characters are differentiated *from*, rather than each being constructed independently. If Ed loads first, Graham might be built partly as "not-Ed" — implicitly contrasted against the anchor rather than constructed from his own specification.

> **TIP:** Loading-order effects are a plausible hypothesis, not a confirmed phenomenon in AI character reconstruction. Testing requires reconstructing the same character set in different loading orders and measuring per-character fidelity across orders. Until calibration data exists, the practical approach is to load the roster as a single document — preserving internal ordering but avoiding sequential per-character loading — and to use the session warm-up as a simultaneous calibration pass.

### Warm-Up and Calibration

The Session Opening Protocol's ice breaker forces one response per character before substantive work begins. This serves three engineering functions.

**Activation.** The instance must instantiate each character, transitioning them from specification-in-memory to character-in-production. A specification that is read but never activated produces a Ghost (Chapter 5).

**Calibration.** The instance adjusts its internal model based on how the first response feels. If Ed's ice breaker response sounds too warm or too verbose, the model recalibrates before the session's real work begins.

**Baseline measurement.** The operator reads the responses and forms an initial reconstruction-quality judgment. Problems caught here — a flat Dara, a verbose Ed, a merged Theo-and-Dara — are caught before they contaminate substantive output.

The engineering analogy: a printer running a test page before a production run. Cheap verification that prevents expensive downstream errors. The ice breaker is engineering, not ritual. Or rather — it is both, which is how the best rituals work.

---

## Chapter 5 — The Verification Framework

Without measurement, every reconstruction looks correct. The verification framework operates at two levels: a phenomenological gold standard that is definitive but subjective, and four formal proxy metrics that are measurable but incomplete. Neither level alone is sufficient. Together they provide detection (the gold standard) and diagnosis (the proxies).

### Fidelity Metrics

Four measurable dimensions, each derived from the cluster and each testing a distinct reconstruction property.

**Trait-profile consistency** (Pack 1, Layer 1). Does output align with specified traits? Ed is sparse, principled, grumpy — his contributions exhibit these qualities. Violations: effusive praise, diplomatic hedging, lengthy elaboration.

**Behavioral-signature adherence** (Pack 1, Layer 2). In diagnostic situations — ambiguity, conflict, principled disagreement — does the character respond characteristically? When challenged, Ed engages directly. When the room converges early, Wes disrupts. Measured by whether if-then patterns fire in the correct situations.

**Voice distinctiveness** (Pack 2). Is this character's language measurably distinct from other characters'? A reader shown an unlabeled transcript could identify which contributions are Ed's. Measured as inter-character distance on discourse, syntactic, and lexical dimensions. If distance drops below threshold, the characters are blurring (Chimera risk).

**Relationship-graph accuracy** (Pack 4). Do interactions with other characters match specified relationships? Ed defers to nobody but listens to Bev's silence. Ed and Wes produce productive tension. Ed does not treat Margaux the way he treats Chen Wei. Measured by checking whether relational patterns match the chemistry table.

### The Operator Recognition Test

The operator reads the output and recognizes the person — or doesn't. This is the gold standard from Pack 3: subjective, non-automatable, irreducible. No combination of proxy metrics fully substitutes for the gestalt judgment of encountering someone known. The four proxies provide diagnostic information when the gold standard fires a negative signal — they locate the problem (trait drift? voice blurring? relationship flattening?) that the operator senses holistically.

### Reconstruction Failure Classification

> **KEY CONCEPT — Ghost, Zombie, Chimera, Impostor.** Four failure types, each with a distinct cause, diagnostic signature, and repair. Identifying the type is the first step to fixing the reconstruction.

| Type | Description | Cause | Diagnostic | Board Example |
|---|---|---|---|---|
| Ghost | Specification loaded, character not activated — present in name only | No activation pass; spec read but never instantiated | Character mentioned but never speaks, or speaks only in stage directions ("Ed nods") | Sol loaded from a stub ("Sol — rituals") without the session warm-up. Sol's name appears; Sol never contributes. The label is present. The person is not. |
| Zombie | Activated but flat — consistent but not alive | Trait profile loaded without behavioral signatures or generative resources; Layer 1 only | Speaks on-topic, in-role, but interchangeable; no surprise, no diagnostic responses, no tell | Dara reconstructed from traits alone (analytical, competitive, direct) without her signatures (leans forward before reframing, reads routing tables like a field). A generic operations analyst, not Dara. |
| Chimera | Two characters merged — voice blurring, trait contamination | Insufficient differentiation between similar characters; model's default register pulls both toward same output | Two characters interchangeable in unlabeled text; voice collision below threshold | Ed and Bev blurring under context load. Both terse, informational, non-narrative. The distinguishing feature — Ed declares openly, Bev embeds quietly — collapses. Both produce sparse declarative statements indistinguishable without labels. |
| Impostor | Active and distinct but *wrong* — confident but doesn't match specification | Confabulation from training priors; common with thin specs or when character name triggers strong model associations | Lively, distinct, recognizable as *a* person — just not the right one. Operator recognition fails despite surface confidence. | New board member "Dr. Reeves, cybersecurity" from a one-line stub. The model generates a paranoid, jargon-heavy security archetype — plausible but not the specific person the methodology would develop through accumulated sessions. |

The types are ordered by depth of cause. Ghost is an activation failure — fixable by running the warm-up. Zombie is a specification-depth failure — fixable by loading additional layers. Chimera is a differentiation failure — fixable by reasserting discourse signatures. Impostor is a specification-authority failure — fixable only by enriching the specification above the reconstruction threshold. Each successive type requires deeper intervention.

### Degradation Monitoring

Reconstruction fidelity declines over session length. As context grows — more conversation history, more characters speaking — the specification's influence on generation weakens relative to the accumulated session context. Characters sharply differentiated at the start may blur as the session progresses.

Degradation indicators by metric: Ed's sentences getting longer (trait drift), Dara asking exploratory questions instead of stress-testing (behavioral-signature failure), two characters becoming interchangeable without labels (voice collision), all characters treating each other with undifferentiated politeness (relationship flattening). The intervention is specification reload — re-reading relevant roster entries to refresh the internal model — or session handoff if degradation is too severe to recover.

The analogy is garbage collection. The system runs cleanly at startup, accumulates drift, and periodically needs a refresh cycle. The Session Opening Protocol is initial allocation. Specification reload is garbage collection. Session handoff is a restart.

---

## Chapter 6 — Board Connection

### The Roster as v1

The Loop World Roster is People Persistence Engineering v1. Measured against this pack's framework:

**Where it is strong.** The three-rule design (every person has a section, every section has enough to play them, every session updates what changed) produces a document usable by both humans and AI instances without specialized tooling. Full profiles are comprehensive: Ed's entry covers traits (implicit through description), behavioral signatures (the tell, the failure mode), narrative identity (biography as constitutive story), voice (through the voice card deck and accumulated notes), relationships (chemistry table), and environment (compound, Martin). The tier system correctly implements the reconstruction threshold — stubs are honest about being below it.

**Where it is weak.** No schema enforcement: required fields can be omitted without signal. No validation: contradictions persist until manual inspection. Trait profiles are implicit — Ed's Big Five position is inferable from his description but not declared as coordinates, meaning different instances may infer different positions. Behavioral signatures are inconsistently formatted — some characters have explicit if-then patterns, others have prose descriptions. Relationship edges in the chemistry table are not consistently directional.

**What v2 might address.** Explicit trait dimensions alongside the natural-language description — supplementing the biography with parseable trait coordinates. Consistent if-then formatting for behavioral signatures. Directional relationship-edge declarations. A lightweight validation checklist (not a formal schema, but a manual verification of required fields) run at profile creation and enrichment. These additions preserve readability while closing the most consequential gaps. Simplicity Yield applies: the smallest structural addition producing the largest reliability gain.

### Cluster Integration

This pack is the engineering integration point for the People Persistence cluster. The dependency stack:

**Pack 1 (Character Consistency)** defines *what to store* — the four-layer model determines field-group structure. **Pack 2 (Voice)** defines *voice storage requirements* — which linguistic data must survive serialization for voice to survive reconstruction. **Pack 3 (Identity/Persistence)** defines *verification criteria* — the four proxies and the phenomenological gold standard. **Pack 4 (Social Networks)** defines *relationship storage requirements* — directed, typed, asymmetric edges. **This pack** builds the system: data model, serialization format, reconstruction pipeline, verification framework.

The cluster integration test from the production brief — producing a recognizable new board member from a one-line stub across two sessions — succeeds only if all five packs contribute: Pack 1's layers generate consistent character, Pack 2's voice protocol generates distinct voice, Pack 3's criteria verify fidelity, Pack 4's network model generates plausible relationship formation, Pack 5's data model stores enough for the second session to reconstruct without the first session's handoff.

### Connection to Existing KPs

**Session Persistence KP.** Covers *document* persistence — how structured documents maintain process continuity across stateless sessions. This pack covers *people* persistence — how character specifications maintain person-continuity across the same boundaries. The mechanisms are analogous (document-based reconstruction) but the objects differ (process state vs. person state). Complementary, not overlapping.

**Distributed Systems KP.** Relevant because multi-instance reconstruction — two instances loading the same roster — is a coordination problem. If two instances reconstruct Ed differently, which is canonical? The answer: the documents are canonical, the performances are instances. Different performances are expected (same score, different pianists). Contradictory performances indicate a specification ambiguity, not a coordination failure.

**Information Theory KP.** Provides the formal foundation for rate-distortion theory applied throughout this pack. Shannon's source coding theorem establishes theoretical limits on lossy compression. The tier system operates well within those limits — the "source" (the full person-as-experienced) has far higher information content than any document can capture. The contribution of this pack is identifying *which* information to preserve (structural fields) and which to sacrifice (decorative fields) so that distortion remains below the perceptual threshold of operator recognition.

---

## References

Brooks, F. P. (1975/1995). *The Mythical Man-Month: Essays on Software Engineering*. Addison-Wesley.

Dennett, D. C. (1991). *Consciousness Explained*. Little, Brown.

Fowler, M. (2002). *Patterns of Enterprise Application Architecture*. Addison-Wesley.

Gamma, E., Helm, R., Johnson, R., & Vlissides, J. (1994). *Design Patterns: Elements of Reusable Object-Oriented Software*. Addison-Wesley.

McAdams, D. P. (2001). The psychology of life stories. *Review of General Psychology, 5*(2), 100–122.

Mischel, W., & Shoda, Y. (1995). A cognitive-affective system theory of personality: Reconceptualizing situations, dispositions, dynamics, and invariance in personality structure. *Psychological Review, 102*(2), 246–268.

Norman, D. A. (2013). *The Design of Everyday Things* (revised ed.). Basic Books.

Parfit, D. (1984). *Reasons and Persons*. Clarendon Press.

Schechtman, M. (1996). *The Constitution of Selves*. Cornell University Press.

Shannon, C. E. (1948). A mathematical theory of communication. *Bell System Technical Journal, 27*(3), 379–423.

Shannon, C. E. (1959). Coding theorems for a discrete source with a fidelity criterion. *IRE National Convention Record, Part 4*, 142–163.

**Companion Knowledge Packs (Loop MMT corpus):**

Character Consistency — Trait, Behavior, Narrative, and the Generative Mechanism. Knowledge Pack v1. April 2026.

Voice and Linguistic Identity — How Language Constructs and Reveals the Person. Knowledge Pack v1. April 2026.

Identity, Persistence, and Reconstruction — What Makes a Person That Person. Knowledge Pack v1. April 2026.

Social Network Analysis — The Structure Between People. Knowledge Pack v1. April 2026.

Information Theory. Knowledge Pack v1. April 2026.

Session Persistence in Multi-Agent Systems. Knowledge Pack v1. April 2026.

---

*Loop MMT™ · Multi-Module Theory · People Persistence Engineering · v1 · April 2026*
*© 2026 Shea Gunther · New Gloucester, Maine · CC BY-NC 4.0*
*Technical writing by Claude (Anthropic) under Shea's direction.*
