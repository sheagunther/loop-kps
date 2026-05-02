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
Session Persistence in Multi-Agent Systems
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
-   [1 · The Disconnected Models Problem](#ch-problem)
-   [2 · Persistence vs. Handoff](#ch-persistence-vs-handoff)
-   [3 · The Protocol Layer](#ch-protocols)
-   [4 · The Framework Landscape](#ch-frameworks)
-   [5 · OpenAI Agents SDK](#ch-openai)
-   [6 · LangGraph](#ch-langgraph)
-   [7 · AutoGen, CrewAI, Strands](#ch-others)
-   [8 · Common Persistence Patterns](#ch-patterns)
-   [9 · Claude\'s Approach](#ch-claude)
-   [10 · The Understanding Gap](#ch-gap)
-   [11 · The Market](#ch-market)
-   [12 · Board Connection](#ch-board)
-   [References](#ch-refs)

::: {.content role="main"}
::: {#ch-abstract .abstract-box}
::: abstract-label
About This Document
:::

This document surveys the landscape of session persistence and handoff in multi-agent AI systems as of early 2026. Its purpose is to know the landscape so the mesh can articulate what it does that others don\'t. It covers communication protocols (MCP, A2A, ACP), orchestration frameworks (OpenAI Agents SDK, LangGraph, AutoGen, CrewAI, Strands), common persistence patterns, and the critical gap that all current approaches share: they persist data and message history but not understanding.

Board member Renata owns this domain. Full citations appear in the References section.
:::

::: {#ch-problem .chapter}
::: chapter-number
Section 1
:::

::: chapter-title
The Disconnected Models Problem
:::

::: {#s-core-problem .section}
::: section-title
The Core Challenge
:::

Large language models are stateless. Each inference call begins from scratch --- the model has no memory of previous interactions unless that history is explicitly provided in the context window. This creates a fundamental problem for autonomous agents: to be autonomous, an agent must carry context through a sequence of actions, but the underlying models are disconnected and lack the continuity that sustained reasoning requires.

The problem intensifies across sessions. Within a single context window, an LLM can maintain a coherent thread of reasoning (up to the window\'s token limit). But when a session ends --- because the window fills up, the user closes the conversation, or the system restarts --- all context is lost. The next session starts from zero unless something external bridges the gap.

::: {.callout .key}
::: callout-label
The fundamental tension
:::

LLMs are powerful reasoners within a single context window but amnesiac across context windows. Every multi-agent framework and persistence protocol is, at bottom, an attempt to solve this discontinuity --- to create the illusion of continuity from a substrate that has none.
:::
:::
:::

::: {#ch-persistence-vs-handoff .chapter}
::: chapter-number
Section 2
:::

::: chapter-title
Persistence vs. Handoff
:::

::: {#s-distinction .section}
::: section-title
Two Different Problems
:::

**Persistence** is storage: saving state to a durable medium so it survives beyond the current session. A database stores facts. A checkpoint stores the state of a computation. Persistence answers the question: \"What was true?\"

**Handoff** is communication: transferring context from one agent (or session) to another in a form that enables the receiver to continue the work. A handoff tells a story --- not just what happened but what it meant, what was decided, and what remains. Handoff answers the question: \"What do you need to know to continue?\"

The distinction matters because persistence is necessary but not sufficient for continuity. You can persist every message in a database and still lose the thread --- because the raw messages don\'t encode the understanding that emerged from them. A handoff must be more than a data dump; it must be a structured transfer of context that enables reconstruction of the mental model.
:::
:::

::: {#ch-protocols .chapter}
::: chapter-number
Section 3
:::

::: chapter-title
The Protocol Layer
:::

::: {#s-mcp .section}
::: section-title
Model Context Protocol (MCP)
:::

**MCP**, announced by Anthropic in November 2024, is an open standard for connecting AI systems to external data sources and tools. It uses JSON-RPC 2.0 and is inspired by the Language Server Protocol. MCP handles **vertical integration** --- connecting a model to the tools and data it needs. By late 2025, MCP had been adopted by OpenAI, Google, Microsoft, and Amazon. In December 2025, Anthropic donated MCP to the Agentic AI Foundation under the Linux Foundation, co-founded by Anthropic, Block, and OpenAI.

MCP enables persistent context across sessions by allowing agents to read from and write to external stores (databases, file systems, APIs) through a standardized interface. An agent can save its state to an MCP server at the end of a session and reload it at the start of the next. But what gets saved is determined by the application, not the protocol --- MCP provides the plumbing, not the structure.
:::

::: {#s-a2a .section}
::: section-title
Agent-to-Agent Protocol (A2A)
:::

**A2A**, developed by Google, handles **horizontal integration** --- communication between agents. Where MCP connects agents to tools, A2A connects agents to each other. Agents publish \"Agent Cards\" describing their capabilities, and other agents can discover and invoke them through a standardized REST interface. In late 2025, IBM\'s Agent Communication Protocol (ACP) merged into A2A under the Linux Foundation, consolidating the inter-agent protocol space.
:::

::: {#s-protocol-summary .section}
::: section-title
Protocol Summary
:::

  Protocol   Origin                 Purpose                                         Integration Direction
  ---------- ---------------------- ----------------------------------------------- ----------------------------------------
  MCP        Anthropic (Nov 2024)   Connect AI to tools and data sources            Vertical (model ↔ tools)
  A2A        Google (2025)          Inter-agent communication and task delegation   Horizontal (agent ↔ agent)
  ACP        IBM BeeAI (2025)       REST-native agent communication                 Horizontal (merged into A2A late 2025)
:::
:::

::: {#ch-frameworks .chapter}
::: chapter-number
Section 4
:::

::: chapter-title
The Framework Landscape
:::

::: {#s-landscape .section}
::: section-title
The Big Picture
:::

As of early 2026, the multi-agent framework landscape has consolidated from the chaos of 2024--25 into recognizable tiers. Provider-native SDKs (OpenAI Agents SDK, Google ADK, Claude Agent SDK) are optimized for their respective model families. Independent frameworks (LangGraph, CrewAI, AutoGen/AG2, Strands) work across providers. Each takes a fundamentally different approach to orchestration, state management, and inter-agent communication.

  Framework           Orchestration Model                     State Persistence                            Handoff Model
  ------------------- --------------------------------------- -------------------------------------------- ---------------------------------
  OpenAI Agents SDK   Explicit handoffs between agents        Context variables (ephemeral by default)     First-class handoff primitive
  LangGraph           Directed graph with conditional edges   Built-in checkpointing with time-travel      Graph edges transfer state
  AutoGen / AG2       Conversational GroupChat                Conversation history (in-memory)             Message passing between agents
  CrewAI              Role-based crews with processes         Task outputs passed sequentially             Task delegation and results
  Strands (AWS)       Tool-use loop with SessionManager       File-based persistence, pluggable backends   Session state serialization
  Google ADK          Hierarchical agent tree                 Session state with pluggable backends        Parent-child delegation via A2A
:::
:::

::: {#ch-openai .chapter}
::: chapter-number
Section 5
:::

::: chapter-title
OpenAI Agents SDK
:::

::: {#s-openai-detail .section}
::: section-title
Architecture
:::

Released March 2025 as the successor to the experimental Swarm framework. Five primitives: **Agents** (with instructions and tools), **Handoffs** (first-class transfer of control between agents), **Guardrails** (input/output validation), **Sessions** (conversation state), and **Tracing** (built-in observability). A multi-agent triage system can be built in roughly 30 lines of Python.

Handoffs are the distinctive feature. When Agent A determines that Agent B should handle the conversation, it executes a handoff --- transferring the full conversation context to Agent B. Version 0.6.0 introduced collapsing message history into a single context message during handoffs to manage token budgets.

**Persistence limitation:** Context variables are ephemeral by default. Cross-session persistence requires external storage --- the SDK provides the handoff mechanism but not the durable state layer.
:::
:::

::: {#ch-langgraph .chapter}
::: chapter-number
Section 6
:::

::: chapter-title
LangGraph
:::

::: {#s-langgraph-detail .section}
::: section-title
Architecture
:::

LangGraph treats agent workflows as stateful directed graphs. Nodes represent agents or tool invocations; edges represent transitions with optional conditions. State is a first-class citizen --- the graph maintains a typed state object that flows through nodes and can be checkpointed at any step.

**Time-travel debugging:** LangGraph\'s checkpointing system allows replaying execution from any previous state. If step 7 fails, you can roll back to step 6, modify the input, and resume. This is the strongest persistence story of any current framework.

**Persistence limitation:** State is persisted at the graph level --- the computation\'s data and control flow. But the *meaning* of that state, the understanding that a human operator would extract from watching the execution, is not captured. You can replay the steps but you cannot extract a narrative summary of what happened and why.
:::
:::

::: {#ch-others .chapter}
::: chapter-number
Section 7
:::

::: chapter-title
AutoGen, CrewAI, Strands
:::

::: {#s-autogen .section}
::: section-title
AutoGen / AG2 (Microsoft)
:::

Asynchronous multi-agent messaging through structured conversations. Agents take turns in a GroupChat, with a centralized transcript serving as short-term memory. Microsoft merged AutoGen with Semantic Kernel into a unified Agent Framework in October 2025. Memory is conversation-based: agents share a transcript but must extract structure from it themselves.
:::

::: {#s-crewai .section}
::: section-title
CrewAI
:::

Role-driven multi-agent orchestration. Agents have defined roles (researcher, writer, critic) and work on tasks within a \"crew.\" Memory uses ChromaDB vectors for short-term recall, SQLite for task results. The coordinator-worker model is intuitive and produces working prototypes quickly, but memory isolation per role means cross-agent understanding requires explicit sharing.
:::

::: {#s-strands .section}
::: section-title
AWS Strands Agents
:::

Released as Strands Agents 1.0 in mid-2025. Notable for the **SessionManager** abstraction --- a pluggable interface for persisting session state to files, DynamoDB, or custom backends. Also provides a `handoff_to_user` tool for explicit human-in-the-loop handoffs. Built around MCP for tool access, model-agnostic in principle but deeply integrated with AWS services.
:::
:::

::: {#ch-patterns .chapter}
::: chapter-number
Section 8
:::

::: chapter-title
Common Persistence Patterns
:::

::: {#s-patterns-list .section}
::: section-title
What the Industry Does
:::

  Pattern                              What It Persists                                         What It Loses
  ------------------------------------ -------------------------------------------------------- -----------------------------------------------------------------------------------------------------------
  Short-term memory (context window)   Recent messages within the current session               Everything before the window; all cross-session state
  Long-term memory (vector store)      Embeddings of past messages, retrievable by similarity   Temporal order; the narrative arc; what was decided vs. what was discussed
  Checkpointing                        Full computation state at specific points                The meaning of the state; why the computation is in this state
  State serialization                  Structured data objects representing current state       The reasoning that produced the state; the alternatives considered and rejected
  Conversation logging                 Complete message transcripts                             Implicit understanding; the mental model; what the messages meant in context
  Handoff networks                     Explicit transfer of context between agents              Depends on handoff format --- raw message passing loses understanding; structured summaries preserve more
:::
:::

::: {#ch-claude .chapter}
::: chapter-number
Section 9
:::

::: chapter-title
Claude\'s Approach
:::

::: {#s-claude-code .section}
::: section-title
Claude Code Engineering Guidance
:::

Anthropic\'s guidance for Claude Code (published November 2025) recommends specific persistence practices for coding agents: progress tracking files that record what has been done and what remains, git integration for state management (using commits as checkpoints), and structured handoff artifacts between sessions. The AGENTS.md convention (adopted by 60,000+ open-source projects by early 2026) provides a standardized way to give agents project-specific instructions across repositories.

This approach is closer to document-based persistence than the conversation-log approach used by most frameworks. A progress tracking file is a structured document that encodes understanding, not just data. But it is still a single-agent, single-document approach --- it does not address the multi-perspective, multi-document reconstruction that complex sessions require.
:::
:::

::: {#ch-gap .chapter}
::: chapter-number
Section 10
:::

::: chapter-title
The Understanding Gap
:::

::: {#s-gap-analysis .section}
::: section-title
What Everyone Misses
:::

Every framework and protocol in the current landscape solves persistence of **data** and **message history**. None of them solve persistence of **understanding**.

Understanding is the reconstructed mental model that emerges from a session --- not just what was said but what it meant, not just what was decided but why, not just the current state but the trajectory that produced it. Understanding is what a skilled human would extract from watching the entire session and then summarize for a colleague who needs to continue the work.

The gap is visible in every handoff approach:

-   **Conversation logs** preserve everything that was said but none of what it meant. Replaying a 200K-token conversation does not reconstruct understanding --- it overwhelms the new context window.
-   **State checkpoints** preserve the computation\'s current position but not the reasoning that got it there. You can resume from a checkpoint but you cannot explain why you are at that checkpoint.
-   **Vector memories** retrieve fragments by similarity but lose temporal structure and causal relationships. You get relevant snippets, not a coherent narrative.
-   **Handoff messages** summarize what happened but collapse the multi-dimensional session into a single perspective, losing the richness that multiple viewpoints would preserve.

::: {.callout .key}
::: callout-label
The structural claim
:::

The handoff collapses to \"here\'s the conversation log\" or \"here\'s the state dump,\" not \"here\'s what we collectively understood.\" No current framework produces structured documents that encode understanding at multiple resolutions from multiple perspectives. This is the gap that Loop MMT\'s document mesh addresses --- not by improving any single persistence mechanism, but by producing a multi-document, multi-perspective encoding of the session that enables holographic reconstruction of understanding, not just replay of data.
:::
:::
:::

::: {#ch-market .chapter}
::: chapter-number
Section 11
:::

::: chapter-title
The Market
:::

::: {#s-market-data .section}
::: section-title
Scale and Trajectory
:::

The AI agent market was valued at approximately \$7.6 billion in 2025, with projections reaching \$196.6 billion by 2034 --- a compound annual growth rate of 43.8%. MCP SDK downloads grew from approximately 100,000 in November 2024 to over 8 million by April 2025. Over 5,800 MCP servers and 300 MCP clients were available by late 2025.

However, the market is immature. Gartner projected that 40% of AI agent projects started in 2025 would be canceled or scaled back by 2027. Only about 2% of organizations had deployed agents at scale. The gap between framework capability and production readiness remains wide --- most frameworks excel at demos and prototypes but struggle with the reliability, observability, and error handling that production systems demand.
:::
:::

::: {#ch-board .chapter}
::: chapter-number
Section 12
:::

::: chapter-title
Board Connection
:::

::: {#s-board-position .section}
::: section-title
Where Loop MMT Sits
:::

Loop MMT operates in the understanding gap identified in Section 10. It is not a competing framework --- it does not provide agent orchestration, tool integration, or runtime management. It provides the **session persistence layer** that existing frameworks lack: structured, multi-perspective documents that encode understanding rather than data.

  What Others Solve                                  What Loop MMT Solves
  -------------------------------------------------- ----------------------------------------------------------------------------------------------
  Connecting models to tools (MCP)                   Encoding session understanding in structured documents
  Agent-to-agent communication (A2A)                 Cross-session state transfer via holographic document sets
  Within-session orchestration (LangGraph, CrewAI)   Cross-session continuity through multi-resolution handoffs
  State checkpointing (LangGraph)                    Understanding checkpointing --- preserving not just state but the reasoning behind it
  Conversation persistence (all)                     Perspective persistence --- encoding the session from multiple vantage points simultaneously

The mesh produces what no framework currently can: a set of documents that, when loaded into a fresh instance, reconstructs not just what happened but what was understood. The EOD handoff, the routing tables, the field tables, the contracts --- each encodes the session from a different angle. Together they form a holographic plate from which a new instance can reconstruct the full 3D session at the resolution supported by the available fragments.

::: {.callout .key}
::: callout-label
Renata\'s position
:::

The landscape is solving persistence of data. Loop MMT solves persistence of understanding. These are complementary, not competing. MCP, A2A, LangGraph, and the rest provide the infrastructure on which understanding-preserving handoffs could eventually run. Loop MMT provides the document architecture that produces those handoffs. The integration point is clear: use MCP to store and retrieve the documents, use A2A to transfer them between agents, use the mesh to produce them.
:::
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
Protocols
:::

Anthropic. (2024). Introducing the Model Context Protocol. *Anthropic Blog*, November 2024.

Wikipedia contributors. (2026). Model Context Protocol. *Wikipedia, The Free Encyclopedia*.

Google. (2025). Agent-to-Agent Protocol (A2A). *Google Cloud Documentation*.

IBM. (2025). Agent Communication Protocol (ACP). *BeeAI Project*. (Merged into A2A, late 2025.)
:::

::: section
::: section-title
Frameworks
:::

OpenAI. (2025). OpenAI Agents SDK. *GitHub*. (Successor to Swarm, March 2025.)

LangChain. (2024--2026). LangGraph documentation. *langchain.com*.

Microsoft. (2023--2025). AutoGen / AG2. *GitHub*. (Merged with Semantic Kernel into Microsoft Agent Framework, October 2025.)

CrewAI. (2024--2026). CrewAI documentation. *crewai.com*.

AWS. (2025). Strands Agents 1.0. *AWS Blog*.

Google. (2025). Agent Development Kit (ADK). *Google Cloud Documentation*.
:::

::: section
::: section-title
Surveys and Analysis
:::

Pento. (2025). A year of MCP: From internal experiment to industry standard. *pento.ai/blog*.

Langfuse. (2025). Comparing open-source AI agent frameworks. *langfuse.com/blog*.

Softmax Data. (2026). Definitive guide to agentic frameworks in 2026. *blog.softmaxdata.com*.

Anthropic. (2025). Code execution with MCP: Building more efficient AI agents. *anthropic.com/engineering*.
:::
:::
:::
:::

------------------------------------------------------------------------

::: page-footer
Loop MMT™ · Multi-Module Theory Session Persistence in Multi-Agent Systems Knowledge Pack · v1 © 2026 Shea Gunther · [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/deed.en){style="color:inherit;"}
:::
