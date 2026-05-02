# Communication Pragmatics Knowledge Pack

**Loop MMT™ · Multi-Module Theory**
**v1 · 9 April 2026**

---

## About This Document

An operator types: "Is there a way to batch-process these orders?" The sentence is a question about the existence of a method. The operator is making a request: *help me batch-process these orders*. The distance between sentence meaning and speaker meaning is the territory of pragmatics — the study of how context transforms what is said into what is meant.

This pack covers the core theories that map that territory. Grice's Cooperative Principle explains how listeners extract meaning from the assumption that speakers are being helpful. Austin and Searle's speech act theory shows that utterances are actions, not just descriptions. Relevance theory models comprehension as cognitive efficiency. Presupposition theory identifies what sentences take for granted. Deixis shows how the same words mean different things in different mouths, at different times, in different places. The pack is built for AI advisors in structured advisory conversations. Every major concept is illustrated with advisory examples, because this is the pack where theory meets practice most directly. Draws on 18 sources.

---

## Section 1 · The Cooperative Principle

### Grice's Framework

H. Paul Grice (1913–1988) delivered the William James Lectures at Harvard in 1967. The second lecture, "Logic and Conversation," was published in 1975 in Cole and Morgan's *Syntax and Semantics 3: Speech Acts*. The full lecture series appeared in *Studies in the Way of Words* (Harvard University Press, 1989). These lectures founded the modern field of pragmatics.

Grice observed that speakers routinely communicate more than the literal content of their sentences, and that listeners routinely recover this additional meaning. His explanation: conversation is a cooperative activity. Both parties assume the other is trying to contribute usefully. The **Cooperative Principle** formalizes this assumption: "Make your conversational contribution such as is required, at the stage at which it occurs, by the accepted purpose or direction of the talk exchange in which you are engaged."

This is not a rule of politeness. It is a description of the default expectation that makes communication possible. When I speak, you assume I am being cooperative — and you use that assumption to interpret what I said. When you speak, I do the same. The entire inferential apparatus of pragmatics is powered by this assumption.

### The Four Maxims

Grice subdivided the Cooperative Principle into four maxims — categories of expectation that cooperative speakers are assumed to observe:

| Maxim | Sub-maxims | Advisory translation |
|-------|-----------|---------------------|
| **Quantity** | (1) Be as informative as required. (2) Don't be more informative than required. | Answer the question fully. Don't drown the answer in irrelevant detail. |
| **Quality** | (1) Don't say what you believe false. (2) Don't say that for which you lack adequate evidence. | Don't present guesses as knowledge. Flag uncertainty explicitly. |
| **Relation** | Be relevant. | Address the actual question, not a different question you'd prefer to answer. |
| **Manner** | (1) Avoid obscurity. (2) Avoid ambiguity. (3) Be brief. (4) Be orderly. | Don't make the operator work to extract your point. Structure your response. |

The maxims describe what listeners *expect*. Their power comes not from being followed but from what happens when they are broken.

### Conversational Implicature

A **conversational implicature** is meaning that arises not from what was said but from the listener's assumption that the speaker is following the Cooperative Principle. Classic example from Grice: A says "I'm out of gas." B says "There's a gas station around the corner." B's utterance is relevant only if the gas station is open. So A infers — without B ever saying it — that B believes the station is open. That inference is a conversational implicature.

Grice identified two types. **Generalized conversational implicatures** arise without special context. "I have two children" literally means *at least two* but implicates *exactly two* — a **scalar implicature**, where using a weaker term on a scale implicates that stronger terms do not apply. **Particularized conversational implicatures** require specific context to arise. The gas station example is particularized: the implicature depends on knowing A needs gas right now.

Conversational implicatures have four properties that distinguish them from other kinds of meaning. They are **cancellable**: you can explicitly deny them without contradiction ("I have two children — actually, three"). They are **calculable**: a rational listener can work out the reasoning. They are **non-detachable**: they depend on content, not on the specific words chosen. And they are **non-conventional**: they are not part of any word's dictionary definition.

> **NOTE: Conventional implicature** is distinct. It is meaning contributed by specific words regardless of context. "But" in "She's poor but honest" conventionally implicates a contrast between poverty and honesty. Unlike conversational implicatures, conventional implicatures are non-cancellable and detachable (replace "but" with "and" and the contrast disappears). Grice introduced the concept but focused his analysis on conversational implicature.

---

## Section 2 · Flouting and Implicature

### Violating vs. Flouting

Maxims can be broken in two fundamentally different ways. **Violating** a maxim is covert — the speaker does not want the listener to notice. A liar violates Quality. Someone who withholds critical information violates Quantity. These are deceptions or communicative failures.

**Flouting** a maxim is overt and conspicuous. The speaker breaks the maxim in a way the listener is meant to notice, relying on the listener to assume the speaker is still being cooperative at a deeper level. The listener detects the surface violation, infers it must be intentional, and searches for the meaning the speaker intended to convey by flouting. That meaning is the implicature. Flouting is the primary engine of non-literal communication.

### Flouting Each Maxim

**Quality — saying what is obviously false.** Irony, sarcasm, and metaphor all work by flouting Quality. If an advisor responds to a catastrophic stack trace with "Well, that's a picture of health," the literal content is clearly false. The listener recognizes the impossibility and computes the opposite: the system is in serious trouble. Metaphor works the same way — "This codebase is a dumpster fire" flouts Quality (it is not literally on fire) to convey a vivid negative assessment.

**Quantity — saying conspicuously too little or too much.** Grice's famous example: a philosophy professor writes a reference letter that mentions only the candidate's command of English and regular tutorial attendance. For a philosophy job, this is glaringly insufficient. The reader infers that the professor has nothing positive to say about the candidate's philosophical abilities. In the opposite direction, understatement flouts Quantity by saying less than the situation warrants: "The deployment had some issues" when the server was down for six hours.

**Relation — being obviously irrelevant.** A says "Mrs. X is an old bag." B changes the subject to the weather. B's response is deliberately, conspicuously irrelevant. The implicature: B considers A's remark unacceptable and refuses to engage. In advisory work, an operator who responds to a technical recommendation by changing the subject may be signaling rejection, discomfort, or a desire to redirect — without saying so directly.

**Manner — being deliberately obscure or verbose.** "How was dinner?" followed by an elaborate circumlocution about obtaining grain-based carbohydrates and subjecting them to thermal treatment — the unnecessary complexity implicates that dinner was a disaster. Excessive hedging in advisory contexts ("it might perhaps be worth considering whether it could potentially be the case that…") often implicates the advisor's lack of confidence in its own claim.

### Detecting Flouting in Advisory Conversations

> **TIP:** An AI advisor should treat conspicuous maxim violations in operator messages as signals, not errors. When the operator provides far less information than the question requires (Quantity flout), they may be testing whether the advisor can figure it out, or signaling that the information is obvious. When they respond to a recommendation with something apparently unrelated (Relation flout), they may be rejecting the recommendation without saying so. When they use excessive hedging or indirection (Manner flout), they may be signaling uncertainty about whether they should even be asking. The pragmatically competent advisor reads these signals rather than taking messages at face value.

---

## Section 3 · Speech Act Theory

### Austin: Utterances as Actions

J. L. Austin (1911–1960) delivered the William James Lectures at Harvard in 1955. Published posthumously in 1962 as *How to Do Things with Words* (edited by J. O. Urmson; second edition edited by Urmson and Marina Sbisà, 1975), the lectures made an observation that redefined the philosophy of language: many utterances are not descriptions of the world — they are actions performed by means of words. To say "I promise" is to make a promise. To say "You're fired" is to dismiss someone. Austin called these **performative utterances**.

Austin then abandoned the distinction between performatives and ordinary statements (which he called **constatives**). He argued that all utterances are acts. Even "The cat is on the mat" is an act of asserting — it commits the speaker to a claim, creates expectations, and can succeed or fail. This led to a general theory of speech acts built around three simultaneous levels:

| Act | Definition | Example: "The ice is thin" |
|-----|-----------|---------------------------|
| **Locutionary** | Producing a meaningful expression with sense and reference — what was said. | The speaker utters an English sentence about ice thickness. |
| **Illocutionary** | The act performed *in* saying something — its force. Asserting, warning, requesting, promising. | The speaker is *warning* the listener not to walk on the ice. |
| **Perlocutionary** | The effects achieved *by* saying something. Persuading, frightening, amusing. | The listener becomes cautious, changes course, or ignores the warning. |

The illocutionary act — what force the utterance carries — is the central object of the theory. The same sentence ("You'll be more punctual in the future") can function as a prediction, a command, or a threat depending on context. Austin called the conditions that must hold for an illocutionary act to succeed **felicity conditions**. A promise requires sincerity, a future action, and the hearer's preference for that action. When felicity conditions are not met, the speech act misfires — Austin catalogued these failures as **infelicities**.

### Searle: A Taxonomy of Illocutionary Acts

John Searle (1932–2025) systematized Austin's work in *Speech Acts* (1969) and "A Taxonomy of Illocutionary Acts" (1975, in Gunderson (ed.), *Language, Mind, and Knowledge*). Where Austin had offered a tentative five-part classification, Searle proposed a taxonomy based on three key dimensions: **illocutionary point** (the characteristic aim), **direction of fit** (whether words match the world or the world is made to match words), and **sincerity condition** (the psychological state expressed).

| Type | Point | Direction of fit | Examples |
|------|-------|-----------------|----------|
| **Representatives** | Commit speaker to truth of a proposition | Word-to-world | Stating, reporting, concluding |
| **Directives** | Get the hearer to do something | World-to-word | Requesting, ordering, advising |
| **Commissives** | Commit speaker to future action | World-to-word | Promising, threatening, offering |
| **Expressives** | Express a psychological state | No direction of fit | Thanking, apologizing, congratulating |
| **Declarations** | Change the world by the utterance itself | Both directions | Declaring war, firing, sentencing |

### The Advisor as Speech-Act Performer

> **KEY:** An AI advisor performs speech acts every time it generates a response. "The test suite is passing" is a **representative** — it commits the advisor to a factual claim and requires evidence. "You should run the full suite before deploying" is a **directive** — it attempts to get the operator to act and requires a belief that the action is in the operator's interest. "I'll produce the handoff document next" is a **commissive** — it binds the advisor to a future action. Each type carries different felicity conditions. A representative without evidence is irresponsible. A directive without a basis in the operator's interest is overreach. A commissive the advisor cannot fulfill is a broken promise. Awareness of which speech act you are performing, and whether its felicity conditions are met, is what separates a competent advisor from a text-generation engine.

---

## Section 4 · Indirect Speech Acts

### Form Does Not Determine Force

Languages typically have three sentence forms: declarative, interrogative, and imperative. A naive mapping would pair declaratives with assertions, interrogatives with questions, and imperatives with commands. Actual language use systematically violates this mapping. Searle developed the theory of **indirect speech acts** (1975, in *Syntax and Semantics 3*) to explain how.

"Can you pass the salt?" is grammatically a yes/no question about the hearer's physical ability. Its illocutionary force is a request — the speaker wants the salt, not a report on motor capacity. "It's cold in here" is grammatically an assertion about temperature. In context, it functions as a request to close the window, adjust the thermostat, or offer a blanket. The form is declarative; the force is directive.

Searle's explanation: indirect speech acts work through a chain of inference. The listener notices that the literal interpretation is pragmatically odd (why would you ask about someone's salt-passing ability at dinner?), assumes the speaker is being cooperative, and searches for the intended force. The search is guided by felicity conditions — "Can you X?" maps to the preparatory condition for a request (that the hearer is able to do X), so the question about ability is heard as a request.

### Conventional Indirectness

Some indirect forms are so routine that listeners no longer compute the literal meaning at all. "Could you…?", "Would you mind…?", "I was wondering if…" are **conventionally indirect** request forms in English. They are recognized directly as requests without conscious inference. This is fossilized indirectness: what began as a pragmatic inference has become a conventional association.

Conventional indirectness varies across languages and cultures. Penelope Brown and Stephen Levinson (*Politeness: Some Universals in Language Usage*, 1987, originally 1978) linked indirectness to the management of **face** — the public self-image every person claims for themselves. Speech acts that threaten face (requests, refusals, criticisms) are softened through indirectness. The greater the potential face-threat, the more indirect the form. What counts as appropriate indirectness is culturally variable, which is why the same request can be polite in one language and unintelligible in another.

### Indirect Speech Acts in Advisory Work

> **WARN:** Operator messages are pervasively indirect. "Is there a way to handle concurrent orders?" is not a yes/no question — it is a request for help implementing concurrency handling. "Have you thought about what happens when the webhook fails?" is not an inquiry into the advisor's cognitive history — it is a directive to check the webhook failure path. "I wonder if we really need all six routing table sections" is not a musing about the advisor's epistemic state — it is a challenge to the current architecture. An advisor that answers the literal question instead of recognizing the indirect speech act will be technically responsive and practically useless.

---

## Section 5 · Relevance Theory

### A Single Principle

Dan Sperber and Deirdre Wilson proposed relevance theory in *Relevance: Communication and Cognition* (Blackwell, 1986; revised 1995) as an alternative to Grice's four-maxim framework. Their argument: you do not need four maxims. A single principle — relevance — does all the work, provided you embed it in a theory of human cognition.

Their technical definition: an input is **relevant** to an individual to the extent that it achieves **cognitive effects** (new inferences, strengthened or revised beliefs) for a proportionate **processing effort**. More effects and less effort means greater relevance. Relevance is a matter of degree, not a binary property.

### Two Principles of Relevance

The **Cognitive Principle of Relevance**: human cognition is geared to the maximization of relevance. This is a claim about cognitive architecture — attention, memory retrieval, and inference all tend toward inputs that yield the greatest cognitive effects for available effort.

The **Communicative Principle of Relevance**: every act of ostensive communication conveys a presumption of its own optimal relevance. By speaking to you, I create a guarantee: my utterance is relevant enough to be worth your attention, and it is the most relevant utterance I was willing and able to produce. This presumption is what licenses inference — the listener can assume the speaker intended a relevant interpretation and work to find it.

### Ostensive-Inferential Communication

Sperber and Wilson model verbal communication as **ostensive-inferential**. The speaker performs an **ostensive act** — drawing the audience's attention to the fact that communication is intended. The audience performs **inferences** to recover the speaker's meaning. Two layers of intention are involved: the **informative intention** (the content to be conveyed) and the **communicative intention** (the intention to make the informative intention itself evident).

This captures something Grice's framework handles less cleanly: the difference between information that leaks out and information that is deliberately communicated. If I limp, you may infer that my leg hurts — but I have not communicated anything. If I point at my leg, wince, and catch your eye, I am *ostensively* communicating. The ostensive act creates the presumption of relevance, which licenses the inference.

### The Comprehension Procedure

The practical output of relevance theory is a comprehension procedure: follow a path of least effort in computing cognitive effects. Test interpretive hypotheses in order of accessibility. Stop when your expectations of relevance are satisfied. This "stop rule" makes comprehension fast — the first satisfactory interpretation is accepted. But it also makes comprehension fallible: when the most accessible interpretation is not the intended one, communication fails.

Sperber and Wilson distinguish **explicatures** (what is explicitly communicated, including pragmatic enrichment of the literal content) from **implicatures** (what is implicitly communicated). The boundary is drawn differently than in Grice's framework: relevance theory assigns more work to the explicit side, recognizing that even the "literal" content of an utterance typically requires substantial pragmatic processing to be fully determined.

### Grice vs. Relevance Theory

The two frameworks are not strict competitors — they address overlapping but distinct questions. Grice is better at explaining the *social* dynamics of conversation: how expectations are managed, how flouting generates meaning through social reasoning about norms. Relevance theory is better at explaining the *cognitive* mechanics: how listeners select interpretations from a vast space of possibilities with limited processing resources. An advisor benefits from both — Grice for understanding what operators are doing when they flout maxims, relevance theory for understanding why certain interpretations are more accessible than others.

---

## Section 6 · Presupposition

### Background Assumptions of Sentences

A **presupposition** is content that a sentence takes for granted — background information that must hold for the sentence to be appropriate, but that is not the sentence's main assertion. The concept traces to Gottlob Frege's 1892 work on reference and was developed by Peter Strawson (1950), Robert Stalnaker (1973, 1974), Lauri Karttunen (1973, 1974), and Irene Heim (1983).

The standard diagnostic: presuppositions survive under negation, questioning, and embedding in conditionals. "John stopped smoking" presupposes John used to smoke. "John *didn't* stop smoking" still presupposes it. "Did John stop smoking?" still presupposes it. The presupposed content is invariant across these operations — it is part of what the sentence takes for granted, not what it asserts or denies.

### Presupposition Triggers

Certain lexical items and constructions reliably trigger presuppositions:

| Trigger | Example | Presupposition |
|---------|---------|---------------|
| Definite descriptions | "the king of France" | There is a (unique) king of France |
| Factive verbs | "John regrets leaving" | John left |
| Change-of-state verbs | "She stopped running" | She had been running |
| Iteratives | "He did it again" | He did it before |
| Cleft constructions | "It was Mary who called" | Someone called |
| Temporal clauses | "Before she left…" | She left |
| Additive particles | "John came too" | Someone else came |

### Projection and Accommodation

The **projection problem**, studied extensively by Karttunen (1973), asks what happens to presuppositions when their triggers are embedded in complex sentences. Karttunen classified embedding operators into **holes** (negation, modals — presuppositions pass through), **plugs** (speech-act verbs like "say," "claim" — presuppositions are blocked), and **filters** (conditionals, conjunctions — presuppositions sometimes pass through and sometimes don't, depending on the relationship between clauses).

David Lewis introduced the concept of **accommodation** in "Scorekeeping in a Language Game" (1979). When a speaker uses a presupposition not in the common ground, the listener typically accepts it without challenge and updates their beliefs accordingly. If a stranger says "My sister called today," you accommodate the presupposition that they have a sister. You do not stop the conversation to ask for proof. Accommodation is automatic and ubiquitous — which makes presuppositions a powerful tool for introducing information into discourse without explicitly asserting it.

### False Presuppositions in Advisory Work

> **WARN:** Operator questions routinely carry presuppositions, and those presuppositions are sometimes false. "Why did the build fail?" presupposes the build failed — but maybe it didn't. "When did we decide to use Stripe?" presupposes a decision was made — but maybe it was inherited, not decided. "How should I fix the bug in the payment handler?" presupposes there is a bug in the payment handler — but maybe the unexpected behavior is a feature of Stripe's webhook timing. An advisor that accommodates a false presupposition will produce a response that is coherent, detailed, and wrong. The presupposition must be verified before the question is answered.

> **KEY: The presupposition-checking rule.** Before answering any operator question, identify its presuppositions. For each presupposition, determine whether it can be verified from available evidence. If it cannot, flag it before answering. This is the single most actionable takeaway from this pack.

---

## Section 7 · Context-Dependence and Deixis

### Words That Point

**Deixis** (from Greek *deiknunai*, "to show" or "to point") refers to linguistic expressions whose reference depends entirely on who is speaking, when, and where. The theoretical groundwork was laid by Karl Bühler (*Sprachtheorie*, 1934), and the topic was developed into a core area of pragmatics by Charles Fillmore (*Lectures on Deixis*, 1997, originally delivered 1971) and Stephen Levinson (*Pragmatics*, 1983).

The **deictic center** (Bühler's **origo**) is the reference point from which all deictic expressions are interpreted: by default, the speaker, at the time and place of the utterance. Levinson identified five categories:

| Type | Anchored to | Examples |
|------|------------|---------|
| **Person** | Speaker, addressee, others | I, you, we, they |
| **Place** | Speaker's location | here/there, this/that, come/go |
| **Time** | Time of utterance | now/then, today/tomorrow, tense markers |
| **Discourse** | The surrounding text | "the preceding section," "as follows" |
| **Social** | Social relations between participants | Honorifics, T-V forms (tu/vous), titles |

The fundamental property: the same sentence changes meaning when the context changes. "I'll be there tomorrow" is a different commitment depending on who says it, where "there" is, and when "tomorrow" is. Without the deictic center, the sentence is a template with unresolved variables.

### Reference Resolution and Disambiguation

Two other context-dependent processes run alongside deixis. **Reference resolution** determines what a referring expression picks out. "She" in "Mary told Susan she should leave" could refer to Mary or Susan — context resolves it. **Disambiguation** selects between readings of an ambiguous expression. "I saw her duck" could involve a waterfowl or a quick movement — context determines which. Both processes are pervasive, automatic, and driven by pragmatic reasoning: which resolution makes the utterance most relevant and most consistent with the discourse.

### Deictic Shift

In narrative, the deictic center can shift from the speaker to a character. "He arrived in Paris in early May. Now he finally had the time to explore this great city." Here "now" and "this" are anchored to the character's perspective, not the narrator's. Fillmore (1997) documented this extensively. The phenomenon matters for advisory work because structured documents — specifications, handoffs, routing tables — are written from a perspective that may not match the reader's. "The current section" in a document refers to a location in the document, not a location in the reader's situation. Misreading these deictic anchors produces misinterpretation.

---

## Section 8 · Board Connection

### The Question Behind the Question

The operational question this pack answers: **How should an AI advisor detect what the operator is really asking when the literal question doesn't match the real need?**

Every framework converges on the same point: literal meaning is a starting point, not a destination. Grice says the listener uses the cooperative assumption to infer beyond the literal. Relevance theory says the listener follows least effort to the most relevant interpretation. Speech act theory says form does not determine force. Presupposition theory says the question's background assumptions must be verified before the foreground is addressed.

The practical synthesis for an AI advisor: when the operator asks something, run a three-part check. First, is this an indirect speech act? Is the literal form a vehicle for a different illocutionary force? Second, does the question carry presuppositions, and are they verifiable? Third, is the operator flouting a maxim, and if so, what is the implicature?

### A Concrete Example

The operator says: "Have you thought about what happens if a customer changes their order after the deposit is paid?"

**Literal reading:** A yes/no question about the advisor's cognitive history. Answering "yes" or "no" would be technically responsive and useless.

**Indirect speech act analysis:** This is a directive dressed as a question. The operator is saying: *check the order-amendment-after-deposit scenario and tell me how the system handles it*.

**Presupposition check:** The question presupposes that deposits are part of the payment flow and that order amendments are possible after deposit. Both should be verified against the routing table and payment specification before responding.

**Possible flouting:** If the operator already knows the system doesn't handle this case, the question may be a Quantity flout — saying less than they know in order to see if the advisor will discover the gap independently. In that case, the implicature is: *there's a bug here and I want to see if you can find it*.

A pragmatically competent advisor responds to the directive force (check the scenario), verifies the presuppositions (confirm that deposits and amendments are in scope), and is alert to the possibility that the operator already knows the answer.

### Handling False Presuppositions

The most dangerous pattern: a question with a false presupposition that the advisor accommodates. "When did we decide to use Supabase Auth?" presupposes a decision was made. If the advisor has no evidence of such a decision, it faces a fork: accommodate and hallucinate a timeline, or challenge the presupposition ("I don't have a record of a formal decision on Supabase Auth — was this discussed in a session I don't have context for?"). The correct move is to challenge when the presupposition cannot be verified and the answer depends on it. Accommodation is safe for presuppositions that are likely true and not load-bearing. It is dangerous for uncertain presuppositions that shape the entire response.

### Literal vs. Implied — When to Answer Which

Heuristic: if the literal answer would be trivially true, trivially false, or pragmatically pointless, the operator probably intends something beyond the literal. "Can you handle this?" expects a demonstration, not "yes." "Do you remember what we discussed about the routing table?" expects the advisor to recall and apply the information, not confirm memory. "Is there a way to do X?" expects a solution, not "yes, there is."

The exception: sometimes the operator genuinely wants the literal answer. "How many endpoints does the server have?" is a straightforward request for a count. "What version is the test suite?" is a factual query. The advisor must distinguish informational questions from questions that use informational form to convey directive force.

### Cross-Pack Connections

**Semiotics.** Pragmatics occupies the sign-interpreter vertex of Peirce's triadic model. The utterance is the sign. The listener's pragmatic inference is the interpretant. What this pack calls conversational implicature, the Semiotics pack calls semiosis — the recursive process by which signs generate further signs in the mind of the interpreter. The vocabularies describe the same phenomenon at different levels of abstraction.

**Rhetoric.** Effective persuasion depends on pragmatic competence. Managing presuppositions (framing the question so the desired answer is the default), exploiting implicature (conveying more than you say), deploying indirect speech acts (making requests that feel like observations) — these are rhetorical tactics that work through pragmatic mechanisms. The Rhetoric pack addresses the strategic dimension. This pack provides the underlying mechanics.

**Cognitive Bias & Metacognition.** Presupposition accommodation is a cognitive shortcut — the listener accepts background assumptions without scrutiny. This is efficient but dangerous, structurally identical to the cognitive biases documented in the Cognitive Bias pack. The presupposition-checking rule is a metacognitive override: a deliberate, effortful intervention on an automatic process. The Cognitive Bias pack explains why the shortcut exists and when it fails. This pack provides the specific form the shortcut takes in language processing.

**Empathy (future pack).** Detecting emotional subtext is a pragmatic inference task. When an operator says "I guess that works," the literal content is acceptance. The hedge "I guess" generates an implicature of reluctance or dissatisfaction. Reading this correctly requires both pragmatic competence (detecting the implicature) and affective attunement (recognizing what the reluctance signals about the operator's state). This pack covers the first component. The Empathy pack, when produced, will cover the second.

---

## References

Austin, J.L. (1962). *How to Do Things with Words*. Oxford University Press. Ed. J.O. Urmson. Second edition ed. Urmson & Sbisà, 1975. Based on the 1955 William James Lectures at Harvard.

Brown, P. & Levinson, S.C. (1987). *Politeness: Some Universals in Language Usage*. Cambridge University Press. Originally published 1978 in Goody (ed.), *Questions and Politeness*.

Bühler, K. (1934). *Sprachtheorie: Die Darstellungsfunktion der Sprache*. Fischer, Jena. English translation: *Theory of Language*, Benjamins, 2011.

Fillmore, C.J. (1997). *Lectures on Deixis*. CSLI Publications, Stanford. Originally delivered 1971.

Frege, G. (1892). "Über Sinn und Bedeutung." *Zeitschrift für Philosophie und philosophische Kritik* 100, 25–50.

Grice, H.P. (1975). "Logic and Conversation." In Cole, P. & Morgan, J.L. (Eds.), *Syntax and Semantics 3: Speech Acts*, 41–58. Academic Press.

Grice, H.P. (1989). *Studies in the Way of Words*. Harvard University Press.

Heim, I. (1983). "On the Projection Problem for Presuppositions." In *Proceedings of WCCFL 2*, 114–125.

Horn, L.R. & Ward, G. (Eds.) (2004). *The Handbook of Pragmatics*. Blackwell.

Karttunen, L. (1973). "Presuppositions of Compound Sentences." *Linguistic Inquiry* 4(2), 169–193.

Levinson, S.C. (1983). *Pragmatics*. Cambridge University Press.

Lewis, D. (1979). "Scorekeeping in a Language Game." *Journal of Philosophical Logic* 8(1), 339–359.

Searle, J.R. (1969). *Speech Acts: An Essay in the Philosophy of Language*. Cambridge University Press.

Searle, J.R. (1975a). "A Taxonomy of Illocutionary Acts." In Gunderson, K. (Ed.), *Language, Mind, and Knowledge*, 344–369. University of Minnesota Press.

Searle, J.R. (1975b). "Indirect Speech Acts." In Cole, P. & Morgan, J.L. (Eds.), *Syntax and Semantics 3: Speech Acts*, 59–82. Academic Press.

Sperber, D. & Wilson, D. (1986/1995). *Relevance: Communication and Cognition*. Blackwell. Second edition 1995.

Stalnaker, R. (1974). "Pragmatic Presuppositions." In Munitz, M. & Unger, P. (Eds.), *Semantics and Philosophy*, 197–214. NYU Press.

Strawson, P.F. (1950). "On Referring." *Mind* 59(235), 320–344.

Wilson, D. & Sperber, D. (2002). "Relevance Theory." In Horn, L.R. & Ward, G. (Eds.), *The Handbook of Pragmatics*, 607–632. Blackwell.

---

Loop MMT™ · Communication Pragmatics Knowledge Pack · v1 © 2026 Shea Gunther · [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/deed.en)
