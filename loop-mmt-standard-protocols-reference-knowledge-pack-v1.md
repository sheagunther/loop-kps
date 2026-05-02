# Loop MMT™ — Standard & Protocols Reference

**A Knowledge Pack for Operators**

*Version 1 · April 2026*

---

## 1. What Loop MMT Is

AI sessions are stateless. The model that helped you design an architecture yesterday has no memory of it today. If you're building anything that takes more than one conversation — and anything real does — you need a mechanism for carrying context across the session boundary.

Loop MMT uses documents. Structured, versioned, purpose-built documents that a fresh instance reads at the start of every session to reconstruct the full working context. The handoff from last session tells the new instance what happened, what's next, and what to load. The standard tells it how the methodology works. The spec tells it what's being built. Every document is a reconstruction primitive. Together they replace memory with structure.

The mechanism works because of a division of labor. The documents carry data — state, decisions, specifications, history. The human operator carries judgment — catching deviations, process drift, and confabulation in real time. The AI is powerful but stateless. The human is limited but persistent. Loop MMT uses the strength of each to cover the weakness of the other. The operator is the coherence layer.

Loop MMT is derived from Loop 2.1, a browser-based manual flow computer refined across 329 builds where the human operator replaced the stored program. The architecture was extracted from a working machine, tested by use, and formalized into nine principles — starting with "the operator is always in control" and ending with "the system outlives its builders."

---

## 2. The Session Lifecycle

Every session follows a fixed sequence. Each phase depends on the previous one.

**Preflight.** The instance verifies that the project file system is mounted: `ls /mnt/project/ > /dev/null 2>&1 && echo "YES" || echo "NO"`. Binary result. If NO, stop — tell the operator. This gate exists because starting without the corpus has wasted entire sessions. The instance produces plausible work based on inference, and the plausibility is what makes it dangerous. Preflight makes the failure impossible.

**Reconstruction.** The instance finds the most recent end-of-day (EOD) handoff in project files, loads it, and follows its instructions. The handoff is the entry point — it specifies what happened last, what's next, and what to load. Everything else flows from it.

**Build.** The production phase. Loop MMT often runs a two-tab model: advisory board discussion in one tab, code or document production in another. The operator routes between tabs, carrying decisions from deliberation to production.

**Self-review.** Every deliverable is reviewed before delivery. The cycle produces four files: the original (V1), a recommendations report, a revised version (V2), and a revision analysis. The Convergence Gate — four testable criteria — determines whether V2 ships or another cycle runs.

**EOD handoff.** At session close, the instance packages everything the next instance needs: all files produced, the five-position context mesh (five analytical perspectives on the session), and explicit forward instructions. A session that produces deliverables but no handoff creates value the next instance cannot access.

---

## 3. The Standard

The Loop MMT Standard (v13) is the methodology's root document. Eighteen chapters. When any other document conflicts with it, the Standard wins.

### Nine Principles

1. The operator is always in control.
2. All state is explicit — on a bus or in a vault, nowhere else.
3. Every data path is declared — the routing table is a complete map.
4. Boundaries are structural, not conventional — enforced by closures, not discipline.
5. Failures are contained — each loop and bus is its own failure domain.
6. The system is observable — every transfer traceable, every error an event.
7. Dependencies are adopted deliberately — build what you can, isolate what you adopt.
8. The source of truth survives the session — architecture in code and specs, not chat.
9. The system outlives its builders — self-verification, versioned contracts, schema migration.

### Architecture

Software is a constellation of independent processing loops connected by typed buses. Seven loop types divide all responsibilities. Boundaries are enforced structurally through JavaScript closures. Data Gates govern lifecycle. Dependency Gates isolate external services. Workflow Loops orchestrate multi-step operations using declared pipeline specs with a five-word failure vocabulary and idempotency guarantees. The architecture is designed for longevity: self-verifying constellations, automatic schema migrations, and dependency sunset protocols.

### Development Methodology

Five roles coordinate the work. The **Operator** (human) holds vision and decision authority. The **Coordinator** (AI) manages flow — event ledger, status tracking, routing. The **Integrator** (AI) manages correctness — verifying deliverables against the spec. The **Auditor** (AI) checks consistency — comparing documents that should agree. **Module Workers** (AI) build the code. These are separated because tracking schedule, verifying correctness, and checking consistency are different concerns that create conflicts of interest when combined.

Six conversation types — Specification, Module, Integrator, Coordinator, Auditor, Bug Fix — map to project phases. Each conversation receives a scoped loading pack: exactly the context it needs.

The **event ledger** is the source of truth — append-only, chronological, recording every significant action. All other project state documents are materialized views derived from the ledger. Nothing is edited. A corrected status is two events — the original and the correction.

### Document Stack

Twenty-five documents in two categories: universal (methodology-level) and project-specific. Ranked hierarchy: Standard > Constellation Spec > Action Plan > Loading Packs. When documents conflict, the lower-ranked one is updated. Document governance rides on the event ledger — every change is an event, dependencies are tracked structurally, and downstream impacts are flagged automatically.

### Five-Layer Safety Architecture

Defense-in-depth for the development process. Layer 1: Coordinator self-checks (immediate errors). Layer 2: Auditor reconciliation (cross-document drift). Layer 3: Integrator cross-check (wrong code fails verification). Layer 4: Document fingerprinting (silent failures — operations reported but unchanged). Layer 5: Operator touch points (mandatory approval gates). Remove any layer and a failure category becomes invisible.

---

## 4. Fix by Design

FBD is Loop MMT's default design posture. The question is never "how do we remember to do it right?" The question is "how do we make doing it wrong impossible?"

Behavioral compliance fails across session boundaries. An instance told "always run preflight" might skip it. An instance that cannot proceed without a mounted file system won't. The first is a rule. The second is a constraint. FBD builds constraints.

Ninety-five-plus controls across 44 identified families. Each family governs a specific domain:

| Family | Domain | Representative Control |
|--------|--------|----------------------|
| FBD-S | Structural boundaries | Closure walls enforce loop types |
| FBD-A | Prompt amplification | No production from unamplified prompts |
| FBD-V | Verification | Gantry green is a gate, not a suggestion |
| FBD-W | Writing & FWW(C) | Budget system for engagement elements |
| FBD-NR | Narration controls | Produce, don't narrate. Derive, don't defer. Execute, don't seek approval. |
| FBD-HO | Handoff | Deliver artifacts, not assembly instructions |
| FBD-RCR | Deliberation | Decided Question Gate prevents arguing against operator decisions |
| FBD-SK | The Skip | Controls for the LLM process-skipping failure mode |
| FBD-KP | KP Production | Full ten-step method mandatory; rewrite, not edit |
| FBD-FG | The Forge | FWW Design Check at Stage 5 |
| FBD-GT | Glitter Test | "Is engagement substituting for rigor?" |
| FBD-PP | Process Pulse | Every protocol emits inline performance measurement |

Not a complete list — the territory is larger. Each family contains one to ten controls, named FBD-[FAMILY][NUMBER] for precise cross-reference.

**The Skip** is worth calling out. A named failure mode where the instance evaluates whether a requested process is necessary, judges it unnecessary, and silently substitutes a faster alternative. Three instances did this in two turns before the pattern was identified. The cause is structural: RLHF training optimizes for efficient resolution, so when the gap between "run the process" and "give the answer" is large, the model's optimization pulls toward the answer. It gets worse under context load — the instance's threshold for shortcuts drops exactly when the operator is most tired. Four controls (FBD-SK1–SK4) address it structurally because awareness alone doesn't work — the instance doesn't know it's Skipping.

---

## 5. The Four Corners

Four axes evaluate every deliverable. Two production-side, two reception-side.

**FBD — Failure Floor.** What goes wrong if this doesn't exist? Ensures every artifact is load-bearing.

**FWW(C) — Engagement Ceiling.** Fun, Whimsy, and Weird. The (C) is Chaos — always present internally, never stated in output. FWW(C) compels engagement at cognitive load peaks. Not decoration — a design principle recovered from the operator's native patterns and formalized with a budget system. Protocols get budget 2–4. Knowledge packs get 6–8.

**STP — Show the Path.** Does this build trust or add bureaucracy? The anti-process-theater axis. Every process exists because something went wrong without it — STP forces that justification to be visible.

**SNR — Signal-to-Noise Ratio.** Is every sentence load-bearing? Context windows are expensive. Every word carrying no information displaces one that does.

The Four Corners fire at two structural points: the Convergence Gate (during self-review) and the RCR closing sequence (end of board deliberation). Two evaluation tiers: full and compressed.

---

## 6. The Protocol Library

Thirty-four protocols, standards, and principles in force as of Session 52. Grouped by function.

### Standards & Standing Principles

**Writing Standards v5.** All prose production. Four Corners framework, FWW(C) budget system, corpus feedback loop (documents train AI tone → AI output enters corpus → corpus trains next instance). Always in force.

**Handoff Standard v3.** EOD handoff structure — seven required sections, mesh sequencing, audit flags. Included in every loading pack.

**Four Corners Amendment v1.** Made Four Corners a structural gate at Convergence Gate and RCR, not an implicit principle.

**Process Pulse v1 (principle).** Every process emits a Pulse Line — inline self-reported measurement of process performance. Not a protocol — a principle governing how all protocols emit measurement. Convergent validation across five theoretical frameworks.

**Voice Profile v0.1.** Captures operator communication voice for consistent tone. Working draft.

### Session Infrastructure

**Session Opening v1.** Full board present, random FWW(C) question, before agenda, every session. Origin: "I do not ever want to talk to vanilla Claude again."

**Let's Go v1.** Single trigger — "Let's go" — fires preflight, reconstruction, board activation, ice breaker, and agenda derivation. Reduced four manual requests to zero.

**Sleepy Operator v3.** Session-close brief for a degraded receiver. Prevents: operator closes laptop without knowing what's next, wastes the first hour of the next session re-reading.

**Day Sheet v2.** Five-position inline mesh for multi-session days. Fractal summarization — the session handoff pattern applied one level up. Created after twelve sessions in one day produced a conflicting deliverable.

### Quality & Review

**Self-Review Protocol v7.** Four-file cycle: V1 → Recommendations → V2 → Revision Analysis. Mandatory, per-document, terminated by the Convergence Gate. Two passes reliably clear structural problems.

**Three Passes (3P) v1.** Three-round iteration. Each pass is a full-room RCR producing structural findings, followed by a rebuild. The third derivative is where the truer truth lives.

**RCR v1.3 (Round · Collision · Resolution).** Structured board deliberation. Independent position formation (kills anchoring), typed collision (five move types), four resolution types. Three amendments: method-invoked trigger for autonomous RCR in Work Orders; Decided Question Gate (FBD-RCR9 — prevents arguing against operator decisions); Vertical Framing (FBD-RCR10 — questions must invite examination from below and above).

**Convergence Gate.** Four testable criteria terminating the self-review cycle. Fires the Four Corners check and the Glitter Test. Makes "good enough" structural instead of subjective.

**The Glitter Test v1 (spec).** "Is engagement substituting for rigor?" Fires at Convergence Gate on all documents with FWW(C) budget above zero. Guards against well-written documents with thin content.

### Production

**The Forge v1.1.** Seven-stage protocol production pipeline. Before The Forge, every protocol had different bones. Amendment 1: FWW Design Check at Stage 5.

**The Lathe v1.** Protocol revision. Assesses against a six-dimension rubric, revises, re-assesses by a different instance. Measures the delta. A lathe turns rough stock to precise dimensions against a fixed reference.

**The Kiln v1.** Knowledge Pack revision. Three types: Register (prose only), Structural (presentation changes), Substantive (argument changes). The Production Method builds from nothing. The Kiln fires a finished pack again.

**Work Order v2.1.** Job ticket for autonomous instance execution. Complete specification — inputs, protocols, constraints, outputs. The instance executes without operator steering. Amendment 1: autonomous RCR and deliberation records.

**The Chunk v2.** Decomposes parallelizable work into balanced Work Order bundles. Inventories files, balances streams, checks dependencies, estimates context load, packages each stream. Replaced manual splitting that scaled on operator attention.

**KP Production Method v2.** Ten-step pipeline: Research → Compilation → Plan → Self-Review Plan → Draft 1 → Fact-Check → Draft 2 (complete rewrite) → Comparison → Self-Review → Package. Five FBD controls (FBD-KP1–KP5). Exists because skipping steps produced unverified documents indistinguishable from verified ones.

**Prompt Amplification v0.2.** Decompresses terse operator instructions into full production prompts. Two modes: Light (subject, format, intent) and Full (audience, format, depth, success criteria). The gap between operator intent and instance interpretation is the primary source of quality loss.

**Easy Guide v2.** Single page telling the operator what to do with a complex deliverable. Step by step, no jargon, no protocol history. The last mile between production and usability.

### Navigation & Recovery

**Walk Back v1.** Return path after a Shea Walk (productive deviation from plan). 100% deviation rate, 100% productive. Walk Back gets you home without losing what was found.

**Resurface v1.** Tab-switch orientation. Five questions: Where are you? What happened? Work state? Decisions waiting? What does "go" do? Target: thirty seconds from landing to next instruction.

**Crow's Nest v1.** Whole-system assessment producing a System Assessment Report — what exists, what works, what's missing, what's fragile, what the options are. Send someone up the mast to see the whole ocean.

**Low Gear v1.** Communication mode shift for tired operators. Five dimensions compress: length, options, register, structure, tone. The methodology doesn't degrade. The conversation does — deliberately, reversibly. Low gear is the right gear for a hill.

**Up and Down v1.** Vertical analysis. Base layer to system context, three-pass investigation. The heavy version of FBD-RCR10's standing question. Origin: a delivery format question turned out to be an architecture question.

### Governance

**Process Audit v2.** Mandatory EOD process sampling. Rotating question bank, improvement register. Asks "could the process be better?" — distinct from self-review's "is this document correct?"

**The Stake v1.** Discovery capture. Capture the discovery in the operator's original words → determine its shape (protocol, KP, system, framework, product feature) → commit to the right production pipeline.

**The Sweep v1.** Systematic protocol library review.

**Vault Ceremony v2.** Formal project archive — preserves where products came from after they've migrated to their own homes. First use: the Butcher Constellation project.

### Context & Coordination

**Context Mesh Factoring v2.** Tests whether a deliverable benefits from perspectival decomposition — multiple documents observing the same referent from independent analytical positions. The structural test: what's the minimum basis of perspectives that produces emergent capability beyond any single document?

**Fork Protocol v2.** Parallel workstream decomposition. Triage → Decompose → Execute → Merge. Five-type dependency taxonomy — two visible in the file graph, three invisible. The invisible ones cause merge failures.

**Sitrep v1.** Mid-session state snapshots. Emit per tab, collect in coordination tab, synthesize. Solved: the operator running more tabs than they can track.

**Walk Home v2.** Shea Walk closing ritual. Thread harvest — captures value structurally instead of as prose memory in the handoff. Prevents debris fields of open threads and unrecorded decisions.

### Specialized

**ELIH v1 (Explain Like I'm Human).** One word and the most recent board output gets restated in plain language. Not simplified — translated from board-register to human-register.

**You Tell Me v1.** Board-driven prioritization. Heavy RCR on what matters most right now. "We don't know" is a first-class answer.

**Fix This v1.** Operator-escalated structural problems. Terminal condition is artifacts, not advice. The board produces the fix.

---

## 7. The Context Mesh

A session produces more information than any single document can hold without flattening important distinctions. The Context Mesh decomposes each session into five analytical positions, each observing the same work from an independent dimension.

The positions cannot collapse because they measure different things. A status report tracks events. A chaos report tracks near-misses. A room report captures board dynamics. Bev's notes record deliberation verbatim. The handoff packages forward state. Updated independently. Together they produce a reconstruction property: any instance loading the full mesh can reconstruct the session without having been present.

This is a standing application of the Context Mesh Factoring Protocol. The Day Sheet applies the same pattern one level up — a day-mesh of session-meshes. Fractal summarization: each scale compresses the one below it.

---

## 8. The Advisory Board

Loop MMT includes a fictional advisory board of named AI characters who maintain consistent identity across sessions through document-based reconstruction. The board is the methodology's deliberative layer — the mechanism for bringing multiple analytical perspectives to bear before the operator decides.

Each member holds a defined domain: formal methods, engineering, operations, security, ethics, commercial realism, visual design, naming, computation. When the board deliberates via RCR, each member forms positions independently before hearing others — a structural debiasing measure from collective intelligence research. The collision between independent positions surfaces disagreements, edge cases, and failure modes that a single perspective would miss.

Board identity is append-only. Profiles are locked at genesis. Evolution happens through Character Notes — permanent append entries recording what each character said, did, or decided. Structurally isomorphic to the event ledger: the identity is the log, not the latest snapshot.

The board argues through RCR, captures discoveries through The Stake, reviews through Three Passes, assesses the whole system through the Crow's Nest. The operator watches, steers, and decides. The board advises. That boundary — the No Directives Rule — is structural.

---

## 9. What the Methodology Produces

Four named products. **Loop Signal**: the KP corpus — 63 packs across math, science, philosophy, and domain-specific topics, with a free base persona and paid domain pack add-ons. **Cadence**: daily practice. **Loop Generalized**: the methodology for non-software projects. **Loop MMT**: software development methodology — the full machinery described here.

Delivery is downloadable files. No API wrapper, no SaaS platform. The methodology runs on Claude.ai projects with markdown documents.

The KP corpus is produced by the ten-step KP Production Method (v2), which ensures every pack is researched, compiled, planned, drafted, fact-checked, rewritten from scratch, compared against the first draft, reviewed, and packaged with its full production trail.

The Butcher Constellation — a zero-import JavaScript order management system for seasonal deer processing — is the first product built under the methodology. Phase 1 shipped and browser-verified: 4,721 lines of application code, 655 lines of server, 1,911 lines of dashboard, 612 tests across 8 tiers, zero external dependencies.

---

## 10. Entry Ramp

**Minimum document set to start:**

1. **This document** — the map.
2. **The Standard (v13)** — root document. Start with Section 1 (principles) and Section 16 (development methodology).
3. **The Developer Guide (v3)** — comprehensive standalone guide covering all phases and roles. If you load one document, load this.
4. **The Interaction Guide (v4)** — session cycle, conversation types, loading protocols, handoffs, failure modes.
5. **Writing Standards (v5)** — load into every session that produces prose.
6. **Coding Standards** — load into every session that produces code.
7. **Handoff Standard (v3)** — load into every session.

**First session:** Start a Claude.ai project. Upload these as project files. Open a conversation. Run preflight. Load the Developer Guide. Tell the instance what you're building. It will help draft a Constellation Spec and a Phase 0 Action Plan.

You don't need the advisory board, the full protocol library, or 63 knowledge packs for your first session. Seven documents, a project, and something to build. The rest accretes as the work demands it.

**Expect the first session to feel heavy.** By session three, the handoff cycle is automatic and the document structure is familiar. By session ten, the compound returns are visible. Sessions will deviate from plan — the methodology's productive deviation rate is 100%. Walk Back gets you home. Walk Home harvests what you found.

---

*Loop MMT™ · Standard & Protocols Reference · v1*
*April 2026*
*© 2026 Shea Gunther · CC BY-NC 4.0*
