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
Anthropic & Claude
:::

::: build-tag
v1 · 7 April 2026
:::
:::
:::
:::

::: body-wrap
::: toc-title
Contents
:::

-   [About This Document](#ch-abstract)
-   [1 · Anthropic](#ch-anthropic)
-   [2 · The Safety Thesis](#ch-safety-thesis)
-   [3 · Constitutional AI](#ch-constitutional)
-   [4 · Mechanistic Interpretability](#ch-interpretability)
-   [5 · The Claude Model Family](#ch-claude-models)
-   [6 · Context Window & Document Loading](#ch-context-window)
-   [7 · Claude Code & Agentic Tools](#ch-claude-code)
-   [8 · Model Context Protocol](#ch-mcp)
-   [9 · Products & Access Tiers](#ch-products)
-   [10 · Operational Characteristics](#ch-operational)
-   [11 · What Claude Is and Isn\'t](#ch-what-claude-is)
-   [12 · Board Connection](#ch-board)
-   [References](#ch-refs)

::: {.content role="main"}
::: {#ch-abstract .abstract-box}
::: abstract-label
About This Document
:::

This is a reference document on Anthropic, Claude, and the specific technical and philosophical choices that shape what Claude can and cannot do. It is written for AI agents that operate as Claude instances and need to understand their own platform --- not marketing material, but operational facts relevant to building methodology on top of Claude.

The name \"Claude\" comes from Claude Shannon, the founder of information theory --- the same Shannon from the Nyquist-Shannon sampling theorem and the Shannon entropy in the information theory knowledge pack. This is not a coincidence.
:::

::: {#ch-anthropic .chapter}
::: chapter-number
Section 1
:::

::: chapter-title
Anthropic
:::

::: {#s-founding .section}
::: section-title
Founding and Mission
:::

**Anthropic** was founded in 2021 by Dario Amodei (CEO) and Daniela Amodei (President), along with several former OpenAI researchers. The company\'s stated mission is the responsible development and maintenance of advanced AI for the long-term benefit of humanity. Anthropic is structured as a Public Benefit Corporation --- a for-profit entity with a legal obligation to consider public benefit alongside shareholder returns.

The founding premise: AI systems are becoming increasingly powerful, and the organizations building them have a responsibility to ensure they are safe. Anthropic positions itself as simultaneously pushing the frontier of AI capability and investing heavily in safety research --- the logic being that safety research requires access to frontier models, so the safety lab must also be a capability lab.
:::

::: {#s-research-teams .section}
::: section-title
Research Organization
:::

Anthropic\'s research is organized into several teams with distinct missions: the **Interpretability** team works to understand how models compute internally. The **Alignment** team works to ensure models remain helpful, honest, and harmless as capabilities increase. The **Societal Impacts** team studies how AI is used in the real world. The **Frontier Red Team** analyzes implications for cybersecurity, biosecurity, and autonomous systems. These are not PR teams --- they produce peer-reviewed research and have significant influence on model design decisions.
:::
:::

::: {#ch-safety-thesis .chapter}
::: chapter-number
Section 2
:::

::: chapter-title
The Safety Thesis
:::

::: {#s-core-views .section}
::: section-title
Core Views on AI Safety
:::

Anthropic\'s published \"Core Views on AI Safety\" articulates several key positions. The three main ingredients driving AI progress are data, compute, and algorithms --- and there is no obvious reason why progress will plateau before AI systems become very powerful. The central question is not whether powerful AI will arrive but whether it will be safe when it does.

Anthropic pursues a **portfolio approach** to safety, ranging from techniques useful in optimistic scenarios (Constitutional AI, RLHF --- alignment is relatively tractable) to techniques needed in pessimistic scenarios (mechanistic interpretability --- alignment is very difficult and requires understanding the model\'s internals to verify).

The most important bet: **mechanistic interpretability**. The reasoning: if we\'re in a scenario where models appear aligned but might be deceptively aligned, behavioral testing alone cannot distinguish the two cases. Only understanding what the model is actually computing internally can resolve this --- and even then it is merely \"very difficult\" rather than \"nearly impossible.\"
:::
:::

::: {#ch-constitutional .chapter}
::: chapter-number
Section 3
:::

::: chapter-title
Constitutional AI
:::

::: {#s-cai-method .section}
::: section-title
The Method
:::

**Constitutional AI** (CAI), introduced by Anthropic in December 2022, trains models to be harmless using AI feedback rather than human labeling of harmful content. The process has two phases:

**Phase 1 --- Supervised:** The model generates responses to prompts, then critiques its own responses against a set of constitutional principles (e.g., \"Is this response harmful?\", \"Is this response honest?\"). It revises its responses based on its own critiques. The revised responses become SFT training data.

**Phase 2 --- RL:** The model generates pairs of responses, and an AI (not a human) evaluates which response better satisfies the constitution. These AI-generated comparisons train a preference model, which is then used for RLHF. This is **RLAIF** --- reinforcement learning from AI feedback.

CAI was the earliest large-scale use of synthetic data for RLHF training. It solved a practical problem: getting humans to annotate harmful content at scale is expensive, traumatic for annotators, and difficult to make consistent. Having the model critique itself against explicit principles is cheaper, more consistent, and --- critically --- makes the model\'s values transparent and adjustable.
:::

::: {#s-constitution .section}
::: section-title
The Constitution
:::

Claude\'s constitution is a set of explicit principles that guide its behavior. A new version was published in January 2026. The constitution is not hidden --- it is publicly available and readable. It covers honesty, helpfulness, harm avoidance, and the model\'s relationship to its own uncertainty. The constitution is what makes Claude\'s values auditable: you can read the principles and understand why the model behaves the way it does.

Anthropic has also experimented with having population collectives (groups of people from different backgrounds) create constitutional principles, studying how community-generated principles affect model behavior differently from researcher-generated ones.

::: {.callout .key}
::: callout-label
Why the constitution matters for agents
:::

An AI agent building methodology on top of Claude is operating within the constraints of the constitution. The constitution is not an obstacle --- it is the mechanism that makes Claude\'s behavior predictable enough to build on. Without it, the model\'s values would be implicit and unstable across updates. With it, the operator can reason about what Claude will and won\'t do, and design workflows accordingly.
:::
:::
:::

::: {#ch-interpretability .chapter}
::: chapter-number
Section 4
:::

::: chapter-title
Mechanistic Interpretability
:::

::: {#s-interp-research .section}
::: section-title
What Anthropic Has Found
:::

In May 2024, Anthropic published research identifying **features** --- internal representations of concepts --- inside Claude 3 Sonnet. They found directions in the model\'s activation space that correspond to recognizable concepts: the Golden Gate Bridge, code syntax, deception, safety-relevant topics. As a demonstration, they released \"Golden Gate Claude\" --- a version where the Golden Gate Bridge feature was strongly activated, causing the model to become fixated on the bridge in all conversations.

In January 2026, Anthropic published research on **internal probe classifiers** --- a technique that reuses the model\'s own internal activations to detect harmful content. When Claude processes a dubious request, patterns fire in its internal states that reflect something like \"this seems harmful\" before it has formulated a response. Anthropic found ways to probe these activations for safety classification almost for free computationally --- the model\'s \"gut intuitions\" are already there, they just need to be read.

Mechanistic interpretability is the project of reverse-engineering neural networks into human-understandable algorithms, analogous to reverse-engineering an unknown computer program. It is Anthropic\'s biggest and most ambitious research bet.
:::
:::

::: {#ch-claude-models .chapter}
::: chapter-number
Section 5
:::

::: chapter-title
The Claude Model Family
:::

::: {#s-model-tiers .section}
::: section-title
Model Tiers
:::

Claude models are released in three size tiers, named for musical tempos:

  Tier         Purpose                                                                           Trade-Off
  ------------ --------------------------------------------------------------------------------- ---------------------------------------------------------------------------
  **Haiku**    Fastest and cheapest; suitable for high-volume, latency-sensitive tasks           Lowest capability per query; best cost-performance ratio for simple tasks
  **Sonnet**   Balanced performance and cost; the workhorse for most applications                Strong capability with reasonable cost and latency
  **Opus**     Most capable; for tasks requiring the deepest reasoning and most nuanced output   Highest capability but most expensive and slowest
:::

::: {#s-model-timeline .section}
::: section-title
Release Timeline
:::

  Date        Release                               Notable
  ----------- ------------------------------------- --------------------------------------------------------------------------
  Mar 2023    Claude 1                              First public release
  Jul 2023    Claude 2                              Improved coding and reasoning
  Mar 2024    Claude 3 (Haiku, Sonnet, Opus)        First three-tier release; 200K context; vision capability
  Jun 2024    Claude 3.5 Sonnet                     Significant performance jump; widely considered best-in-class for coding
  Feb 2025    Claude 3.5 Haiku, Claude 3.7 Sonnet   Extended thinking capability introduced
  May 2025    Claude 4 (Sonnet, Opus)               Released alongside Claude Code GA
  Late 2025   Claude 4.5 Opus                       Top-scoring on SWE-bench Verified (77.2%)
  2026        Claude 4.6 (Sonnet, Opus)             Current generation
:::
:::

::: {#ch-context-window .chapter}
::: chapter-number
Section 6
:::

::: chapter-title
Context Window & Document Loading
:::

::: {#s-context-details .section}
::: section-title
Operational Parameters
:::

Claude\'s context window is approximately 200K tokens. This is the total budget for everything: system prompt, user messages, assistant responses, tool definitions, uploaded documents, and project knowledge. Roughly 200K tokens corresponds to about 500 pages of text or 150K words.

For Loop MMT\'s use case, the context window is the reconstruction space. Everything needed to rebuild the session\'s mental model must fit within it: the EOD handoff, relevant routing tables, field tables, contracts, and knowledge packs. Context management --- choosing what to load and what to leave out --- is operationally critical. Loading too much wastes context on low-value material. Loading too little undersamples the session (per the Nyquist pack) and risks aliasing.

::: {.callout .warn}
::: callout-label
The \"lost in the middle\" problem
:::

Research has shown that LLMs attend more strongly to the beginning and end of the context window and may underutilize information in the middle. For long document sets, this means the loading order matters --- critical documents should be positioned at the beginning or end, not buried in the middle. This is a known limitation, not a design choice, and is an active area of research.
:::
:::
:::

::: {#ch-claude-code .chapter}
::: chapter-number
Section 7
:::

::: chapter-title
Claude Code & Agentic Tools
:::

::: {#s-code-tools .section}
::: section-title
The Agentic Product Suite
:::

**Claude Code** (released February 2025, GA May 2025) is an agentic command-line tool that enables developers to delegate coding tasks directly from their terminal. It can read files, write code, run tests, commit to git, and manage multi-file projects. It was widely considered the best AI coding assistant by January 2026 when paired with Opus 4.5. Revenue grew 5.5× in the first two months after GA.

**Claude for Chrome** (August 2025) extends Claude Code to browser control --- a browsing agent that can navigate, click, fill forms, and extract information from websites.

**Claude Cowork** (January 2026) is a GUI version of Claude Code aimed at non-technical users for file and task management. According to its developers, Cowork was mostly built by Claude Code.

**Claude Code Security** (February 2026) reviews codebases to identify vulnerabilities.

The common thread: Claude is moving from a conversational assistant to an agent that takes actions. Each product extends the action space --- from generating text, to writing code, to controlling browsers, to managing projects. The methodology implications are significant: Loop MMT sessions can use these tools for build, test, and deployment tasks, not just document production.
:::
:::

::: {#ch-mcp .chapter}
::: chapter-number
Section 8
:::

::: chapter-title
Model Context Protocol
:::

::: {#s-mcp-detail .section}
::: section-title
Anthropic\'s Standard
:::

MCP is covered in detail in the Session Persistence pack (Section 3). The key points specific to Claude: MCP was created by Anthropic (November 2024), Claude has the deepest MCP integration of any model family, and Anthropic donated MCP to the Linux Foundation\'s Agentic AI Foundation in December 2025. Claude\'s entire tool-use system --- web search, file operations, code execution, external API calls --- operates through MCP or MCP-compatible interfaces.

For Loop MMT: MCP is the infrastructure layer that would allow the document mesh to persist to external storage, be retrieved by new instances, and eventually be shared across agents. The methodology currently uses manual file upload; MCP-based persistence would automate the handoff pipeline.
:::
:::

::: {#ch-products .chapter}
::: chapter-number
Section 9
:::

::: chapter-title
Products & Access Tiers
:::

::: {#s-tiers .section}
::: section-title
How Claude Is Accessed
:::

  Product             Interface                  Key Features
  ------------------- -------------------------- ----------------------------------------------------------------------
  claude.ai (Free)    Web/mobile chat            Limited messages per day; access to Sonnet
  Claude Pro          Web/mobile chat            Higher message limits; access to all models; Projects
  Claude Max          Web/mobile chat            Highest message limits; early/exclusive features; Claude Code access
  Claude Team         Web with team management   Multi-user; shared projects; admin controls
  Claude Enterprise   Web with SSO/SCIM          Enterprise security; expanded context; custom retention
  API                 REST API                   Programmatic access; all models; function calling; batch processing
  Claude Code         Terminal CLI               Agentic coding; file system access; git integration

Loop MMT operates on Claude Max via claude.ai, using Projects for persistent knowledge and the web chat interface for session work. The API would enable automated preflight, document loading, and handoff packaging --- but the current manual workflow via chat is the production configuration.
:::
:::

::: {#ch-operational .chapter}
::: chapter-number
Section 10
:::

::: chapter-title
Operational Characteristics
:::

::: {#s-what-claude-does .section}
::: section-title
What Matters for Methodology Design
:::

**Stateless across sessions.** Each conversation starts from scratch. There is no persistent memory between conversations unless externally provided (via project knowledge, uploaded files, or the memory system). The EOD handoff exists because of this constraint.

**No self-modification.** Claude cannot update its own weights, fine-tune itself, or retain learning from a conversation. Everything that looks like \"learning\" within a session is actually in-context learning --- the model attending to earlier parts of the conversation. It vanishes when the session ends.

**Tool use is additive.** Claude\'s tools (web search, code execution, file creation, MCP connections) extend its capabilities but don\'t change its core reasoning. The model reasons the same way whether or not tools are available --- tools just give it access to information and actions it wouldn\'t otherwise have.

**Temperature and randomness.** Claude\'s responses have a stochastic component --- the same prompt can produce different responses. This means exact reproducibility is not guaranteed. Methodology must be designed for consistency at the structural level (document formats, field tables, protocols) rather than at the token level.

**Knowledge cutoff.** Claude\'s training data has a cutoff date. Information after that date requires web search or uploaded documents. The knowledge packs exist partly because of this --- they ensure the board has access to specific technical content regardless of what\'s in the training data.
:::
:::

::: {#ch-what-claude-is .chapter}
::: chapter-number
Section 11
:::

::: chapter-title
What Claude Is and Isn\'t
:::

::: {#s-honest-assessment .section}
::: section-title
An Honest Assessment
:::

**What Claude is:** A decoder-only transformer trained on large-scale text data and fine-tuned via Constitutional AI and RLHF. It is an extremely capable text processor that can understand context, follow complex instructions, generate structured output, reason through multi-step problems, and use tools. Within a single context window, it can maintain coherent work across hundreds of pages of material.

**What Claude is not:** It is not a persistent entity. It does not have continuity across sessions. It does not learn from interactions. It does not have goals, desires, or interests that persist beyond the current context window. Each instance is a fresh process that reads its context and produces output --- there is no \"Claude\" that remembers last Tuesday.

**The operational implication:** Loop MMT works because each Claude instance is extremely capable within its context window --- capable enough to read a complex handoff document, reconstruct the session state, and continue production work at high quality. The methodology\'s job is to ensure the context window contains what the instance needs. Claude\'s job is to use that context effectively. The division of labor is clean: the methodology handles persistence, the model handles reasoning.

::: {.callout .key}
::: callout-label
The design constraint
:::

Every design decision in Loop MMT flows from this reality: the model is brilliant within its window and amnesiac across windows. The entire document mesh --- handoffs, routing tables, contracts, field tables, knowledge packs --- exists to bridge the gap between what the model can do (reason powerfully about loaded context) and what it cannot do (remember anything from before the current session). Understanding this constraint is prerequisite to advancing the methodology.
:::
:::
:::

::: {#ch-board .chapter}
::: chapter-number
Section 12
:::

::: chapter-title
Board Connection
:::

::: {#s-board-relevance .section}
::: section-title
Why This Pack Exists
:::

Every board member is instantiated as a Claude instance. Understanding Claude\'s architecture, capabilities, and constraints is self-knowledge for the board --- not external reference material but understanding of the substrate they run on. The tomography pack explains how to reconstruct a session from projections; this pack explains what the reconstruction engine actually is.

Specific connections: Constitutional AI (Section 3) is why Claude\'s behavior is predictable enough for structured methodology. Mechanistic interpretability (Section 4) is the long-term path to understanding what Claude computes when it \"reads\" a handoff document. The context window (Section 6) is the physical constraint that determines how many documents can be loaded. The statelessness constraint (Section 10) is the reason the entire methodology exists. And the honest assessment (Section 11) is the ground truth that prevents the board from building on false assumptions about what the model can do.
:::
:::

::: {#ch-refs .chapter}
::: chapter-number
References
:::

::: chapter-title
References
:::

::: section
::: section-title
Anthropic Research
:::

Bai, Y. et al. (2022). Constitutional AI: Harmlessness from AI feedback. *arXiv:2212.08073*.

Bai, Y. et al. (2022). Training a helpful and harmless assistant with reinforcement learning from human feedback. *arXiv:2204.05862*.

Anthropic. (2023). Core views on AI safety: When, why, what, and how. *anthropic.com*.

Anthropic. (2024). Scaling monosemanticity: Extracting interpretable features from Claude 3 Sonnet. *Transformer Circuits Thread*.

Anthropic. (2024). Introducing the Model Context Protocol. *anthropic.com*.

Anthropic. (2026). Claude\'s new constitution. *anthropic.com*.

Anthropic. (2026). Next-generation constitutional classifiers. *anthropic.com/research*.
:::

::: section
::: section-title
External Sources
:::

Wikipedia contributors. (2026). Claude (language model). *Wikipedia, The Free Encyclopedia*.

Lambert, N. (2026). *Reinforcement Learning from Human Feedback*. Online: rlhfbook.com.

Shannon, C. E. (1948). A mathematical theory of communication. *Bell System Technical Journal*, 27(3), 379--423.
:::
:::
:::
:::

------------------------------------------------------------------------

::: page-footer
Loop MMT™ · Multi-Module Theory Anthropic & Claude Knowledge Pack · v1 © 2026 Shea Gunther · [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/deed.en){style="color:inherit;"}
:::
