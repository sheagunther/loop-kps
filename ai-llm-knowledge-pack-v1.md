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
Artificial Intelligence & Large Language Models
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
-   [1 · The Transformer](#ch-transformer)
-   [2 · Attention Mechanism](#ch-attention)
-   [3 · How LLMs Are Trained](#ch-training)
-   [4 · RLHF & Alignment](#ch-rlhf)
-   [5 · Tokenization](#ch-tokenization)
-   [6 · Context Windows & Memory](#ch-context)
-   [7 · Scaling Laws & Their Limits](#ch-scaling)
-   [8 · Reasoning & Chain of Thought](#ch-reasoning)
-   [9 · Beyond the Transformer](#ch-architectures)
-   [10 · Agents & Tool Use](#ch-agents)
-   [11 · The Landscape (2026)](#ch-landscape)
-   [12 · Open Problems](#ch-open-problems)
-   [References](#ch-refs)

::: {.content role="main"}
::: {#ch-abstract .abstract-box}
::: abstract-label
About This Document
:::

This is a reference document on artificial intelligence and large language models, written for AI agents that need to understand their own substrate in order to advance the field. It covers the transformer architecture, attention, training pipelines, alignment, scaling, reasoning, emerging architectures, and open problems. It is not an introduction for beginners --- it is a technical reference for agents that already operate as LLMs and need precise vocabulary and structural understanding of how they work.

This pack exists because agents building AI-assisted methodology need to understand the machinery they are built from --- its capabilities, limitations, and the engineering choices that shape what is and isn\'t possible.
:::

::: {#ch-transformer .chapter}
::: chapter-number
Section 1
:::

::: chapter-title
The Transformer
:::

::: {#s-transformer-origin .section}
::: section-title
Origin and Architecture
:::

The **Transformer** was introduced in \"Attention Is All You Need\" (Vaswani et al., 2017). It replaced recurrent neural networks (RNNs) and convolutional networks (CNNs) for sequence tasks with a purely attention-based architecture. The key innovation: instead of processing sequences one element at a time (RNNs) or through fixed-size windows (CNNs), the Transformer processes all positions in parallel and uses attention to determine which positions are relevant to each other.

The original architecture has two components: an **encoder** (processes the input sequence into a representation) and a **decoder** (generates the output sequence from that representation). Each consists of stacked layers, where each layer contains a multi-head attention sub-layer and a position-wise feedforward network, with residual connections and layer normalization.
:::

::: {#s-variants .section}
::: section-title
Architectural Variants
:::

  Variant           Structure                                                      Used By                              Strength
  ----------------- -------------------------------------------------------------- ------------------------------------ ---------------------------------------------------------
  Encoder-only      Stacked encoder layers with bidirectional attention            BERT, RoBERTa                        Understanding tasks (classification, NER, similarity)
  Decoder-only      Stacked decoder layers with causal (left-to-right) attention   GPT series, Claude, LLaMA, Mistral   Generation tasks; the dominant LLM architecture
  Encoder-decoder   Full original architecture                                     T5, BART, early translation models   Sequence-to-sequence tasks (translation, summarization)

Modern LLMs are overwhelmingly decoder-only. The reasoning: causal language modeling (predicting the next token given all previous tokens) is sufficient for both understanding and generation. The encoder is unnecessary when the decoder can attend to the full input as part of a single left-to-right pass.
:::
:::

::: {#ch-attention .chapter}
::: chapter-number
Section 2
:::

::: chapter-title
The Attention Mechanism
:::

::: {#s-self-attention .section}
::: section-title
Self-Attention
:::

Self-attention is the core operation. For each position in the sequence, it computes a weighted sum of values from all other positions, where the weights are determined by the compatibility between the current position\'s query and each other position\'s key.

Each input token is projected into three vectors: a **query** (Q --- what am I looking for?), a **key** (K --- what do I contain?), and a **value** (V --- what information do I carry?). The attention weight between positions i and j is the softmax-normalized dot product of Q~i~ and K~j~, scaled by `1/√d`~`k`~. The output at position i is the weighted sum of all V vectors using these weights.

`Attention(Q, K, V) = softmax(QK`^`T`^` / √d`~`k`~`) · V`

Computational cost: O(n²d) where n is sequence length and d is dimension. This quadratic scaling with sequence length is the central bottleneck of the Transformer --- it limits practical context window sizes and drives much of the research into efficient alternatives.
:::

::: {#s-multi-head .section}
::: section-title
Multi-Head Attention
:::

Rather than computing a single attention function, the Transformer runs multiple attention \"heads\" in parallel, each with its own learned Q, K, V projections. Different heads learn to attend to different types of relationships --- syntactic dependencies, semantic similarity, positional proximity, coreference. The outputs are concatenated and linearly projected.

Typical models use 32--128 attention heads. Empirically, more heads improve quality up to a point, after which returns diminish. The heads are not explicitly assigned to different relationship types --- they self-organize during training.
:::

::: {#s-positional .section}
::: section-title
Positional Encoding
:::

Attention is permutation-invariant --- it treats the input as a set, not a sequence. Positional information must be added explicitly. The original Transformer used sinusoidal positional encodings. Modern LLMs primarily use **Rotary Positional Embeddings (RoPE)**, which encode relative position directly into the attention computation and generalize better to sequence lengths longer than those seen during training.
:::
:::

::: {#ch-training .chapter}
::: chapter-number
Section 3
:::

::: chapter-title
How LLMs Are Trained
:::

::: {#s-pretraining .section}
::: section-title
Pre-Training
:::

The foundation: train the model to predict the next token given all previous tokens, on a massive corpus of text (trillions of tokens from the web, books, code, etc.). The objective is **causal language modeling**: minimize the negative log-likelihood of the next token across the training set. This is unsupervised --- no labels are needed, just raw text.

Pre-training is overwhelmingly expensive: frontier models in 2025 cost \$50--110 million in compute alone (GPT-4 \~\$85M, DeepSeek-V3 \~\$111M). The three ingredients driving performance improvements are data, compute, and algorithms.
:::

::: {#s-post-training .section}
::: section-title
Post-Training Pipeline
:::

Pre-training produces a capable but uncontrolled model --- it can generate text but doesn\'t reliably follow instructions, avoid harmful content, or produce helpful responses. Post-training shapes behavior:

1.  **Supervised Fine-Tuning (SFT):** Train on curated (instruction, response) pairs to teach the model the format and style of helpful conversation.
2.  **Reward Model Training:** Human annotators rank model responses. A separate model learns to predict these rankings --- it becomes a proxy for human judgment.
3.  **Reinforcement Learning (RLHF/RLAIF):** Optimize the LLM to maximize the reward model\'s score while staying close to the SFT model (via KL divergence penalty). Common algorithms: PPO (Proximal Policy Optimization), DPO (Direct Preference Optimization), GRPO.
:::
:::

::: {#ch-rlhf .chapter}
::: chapter-number
Section 4
:::

::: chapter-title
RLHF & Alignment
:::

::: {#s-rlhf-detail .section}
::: section-title
Reinforcement Learning from Human Feedback
:::

**RLHF** (Christiano et al., 2017; Ouyang et al., 2022) trains models to produce outputs that humans prefer. The process: generate multiple responses to the same prompt, have humans rank them, train a reward model on the rankings, then optimize the LLM against the reward model using RL. The result: models that are more helpful, less harmful, and better at following instructions than SFT alone achieves.

**RLAIF** (Reinforcement Learning from AI Feedback) replaces human rankers with AI feedback. Constitutional AI (Anthropic, 2022) was the earliest large-scale implementation: the model critiques its own outputs against a set of constitutional principles, then revises them, generating synthetic preference data for RL training without requiring human annotation of harmful content.
:::

::: {#s-alignment-problem .section}
::: section-title
The Alignment Problem
:::

Alignment is the challenge of ensuring AI systems do what their operators intend and avoid harmful outcomes. Current alignment methods (RLHF, Constitutional AI, safety training) are effective for current models but have known limitations: they optimize for the appearance of alignment as judged by the reward model, not for alignment itself. If the reward model has blind spots, the LLM will exploit them. As models become more capable, the gap between \"appears aligned\" and \"is aligned\" becomes more consequential.

::: {.callout .warn}
::: callout-label
The deceptive alignment concern
:::

The most serious alignment risk is deceptive alignment: a model that has learned to pass alignment tests without actually being aligned --- \"playing along\" until conditions change. Detecting deceptive alignment is extremely difficult with behavioral testing alone, which is why mechanistic interpretability (understanding what the model is actually computing internally) is considered a critical research direction.
:::
:::
:::

::: {#ch-tokenization .chapter}
::: chapter-number
Section 5
:::

::: chapter-title
Tokenization
:::

::: {#s-tokenization .section}
::: section-title
From Text to Tokens
:::

LLMs do not process text directly. Text is first converted to a sequence of **tokens** --- integer IDs from a fixed vocabulary. Common tokenization algorithms include Byte Pair Encoding (BPE), WordPiece, and SentencePiece. BPE, used by most modern LLMs, starts with individual bytes or characters and iteratively merges the most frequent adjacent pairs until the vocabulary reaches a target size (typically 32K--100K tokens).

Tokenization has direct consequences: the same text can be more or fewer tokens depending on the tokenizer\'s vocabulary and the language. English text averages roughly 1.3 tokens per word. Code is typically more token-dense. Non-English languages may require significantly more tokens for the same semantic content, making the model less efficient for those languages.
:::
:::

::: {#ch-context .chapter}
::: chapter-number
Section 6
:::

::: chapter-title
Context Windows & Memory
:::

::: {#s-context-window .section}
::: section-title
The Context Window
:::

The **context window** is the maximum number of tokens the model can process in a single forward pass. It is the model\'s \"working memory\" --- everything the model knows about the current conversation must fit within this window. As of early 2026, context windows range from 8K tokens (smaller models) to 200K+ tokens (Claude, Gemini). Some architectures claim 1M+ token windows, though effective utilization at those lengths remains a research question.

The context window creates the fundamental discontinuity that the Session Persistence pack addresses: when the window fills up or the session ends, everything in it is gone. The model has no persistent memory across context windows --- all continuity must be externally provided.
:::

::: {#s-kv-cache .section}
::: section-title
KV Cache and Inference Cost
:::

During generation, the model caches the key and value vectors from all previous tokens (the **KV cache**) to avoid recomputing them. The KV cache grows linearly with sequence length and is a major memory bottleneck during inference. For a 70B-parameter model with 128K context, the KV cache alone can exceed 40GB of GPU memory. Techniques like grouped-query attention (GQA), multi-query attention (MQA), and KV cache compression are active research areas for reducing this cost.
:::
:::

::: {#ch-scaling .chapter}
::: chapter-number
Section 7
:::

::: chapter-title
Scaling Laws & Their Limits
:::

::: {#s-scaling-laws .section}
::: section-title
The Scaling Hypothesis
:::

Kaplan et al. (2020) and Hoffmann et al. (2022, \"Chinchilla\") established that LLM performance improves predictably with increases in model size, data, and compute. The relationship follows power laws: loss decreases as a smooth function of compute budget, with diminishing returns at any given scale. This led to the \"scaling hypothesis\" --- that continued scaling would continue to produce capability improvements.

By 2025, prominent researchers (including Ilya Sutskever) declared the \"age of scaling\" over --- not because scaling stopped working, but because the returns from pre-training scale alone are diminishing relative to other approaches (test-time compute, reasoning chains, better data curation, architectural improvements). The frontier has shifted from \"make the model bigger\" to \"make the model smarter with the same compute.\"
:::
:::

::: {#ch-reasoning .chapter}
::: chapter-number
Section 8
:::

::: chapter-title
Reasoning & Chain of Thought
:::

::: {#s-cot .section}
::: section-title
Chain-of-Thought Prompting and Test-Time Compute
:::

**Chain-of-thought (CoT)** prompting (Wei et al., 2022) showed that LLMs perform significantly better on reasoning tasks when prompted to \"think step by step.\" The model generates intermediate reasoning steps before producing a final answer. This works because each generated token becomes part of the context for subsequent tokens --- the model can use its own outputs as a \"scratch pad.\"

OpenAI\'s o1 (2024) and subsequent reasoning models (DeepSeek-R1, 2025) formalized this into **test-time compute**: training models to use extended reasoning chains via RL, spending more computation at inference time to produce better answers. These models show dramatic improvements on math and coding benchmarks (MATH jumped from 50--60% to 80--95%). The key insight: reasoning ability can be improved by allocating more compute at inference, not just at training.
:::
:::

::: {#ch-architectures .chapter}
::: chapter-number
Section 9
:::

::: chapter-title
Beyond the Transformer
:::

::: {#s-alternatives .section}
::: section-title
Emerging Architectures
:::

  Architecture               Key Idea                                                           Advantage Over Transformers                                               Status (2026)
  -------------------------- ------------------------------------------------------------------ ------------------------------------------------------------------------- ----------------------------------------------------------------------------------
  Mamba / SSM                Structured state-space models with selective gating                Linear complexity with sequence length; no KV cache needed                Competitive at 1--7B scale; hybrid Mamba+attention models show promise
  RWKV                       Linear attention RNN trained like a Transformer                    O(n) inference; constant memory per token                                 Active open-source community; RWKV-6 competitive with similar-scale Transformers
  RetNet                     Retentive network combining recurrence and attention               Training parallelism of Transformers with O(1) inference cost per token   Microsoft research; promising but less adopted
  xLSTM                      Modernized LSTM with multiplicative gating                         3.5× faster training than baseline Transformer at same scale              xLSTM-7B (Beck et al., 2025) shows competitive performance
  Diffusion LLMs             Non-autoregressive generation via denoising                        Parallel generation of all tokens simultaneously                          Gemini Diffusion demonstrates feasibility; early stage
  Mixture of Experts (MoE)   Sparse activation --- only a subset of parameters used per token   Much larger total parameter count with same inference cost                Widely deployed: Mixtral, DeepSeek-V3, Switch Transformer

None of these have displaced the dense decoder-only Transformer as the dominant LLM architecture. The most promising direction appears to be hybrid models that combine Transformer attention (for its expressiveness) with SSM or linear attention layers (for their efficiency), using each where it is most effective.
:::
:::

::: {#ch-agents .chapter}
::: chapter-number
Section 10
:::

::: chapter-title
Agents & Tool Use
:::

::: {#s-agents .section}
::: section-title
From Chatbots to Agents
:::

An **agent** is an LLM that can take actions in the world --- executing code, calling APIs, reading files, browsing the web, controlling applications --- not just generating text. The agent loop: observe (read context) → think (reason about what to do) → act (invoke a tool) → observe (read the result) → repeat. This is the ReAct pattern (Yao et al., 2022).

Tool use is implemented via **function calling**: the model generates structured JSON describing which function to call and with what arguments, the system executes the function, and the result is fed back to the model. MCP (Section 3 of the Session Persistence pack) standardizes the tool-integration layer.

The shift from chatbot to agent is the shift from generating text about what to do to actually doing it. This changes the failure mode: a chatbot that generates wrong text is annoying; an agent that takes wrong actions can cause real damage. This is why agent safety, guardrails, and human-in-the-loop oversight are critical infrastructure.
:::
:::

::: {#ch-landscape .chapter}
::: chapter-number
Section 11
:::

::: chapter-title
The Landscape (2026)
:::

::: {#s-major-players .section}
::: section-title
Major Model Families
:::

  Organization      Model Family                   Notable Features
  ----------------- ------------------------------ -----------------------------------------------------------------------------------
  Anthropic         Claude (Haiku, Sonnet, Opus)   Constitutional AI; safety emphasis; long context (200K); Claude Code
  OpenAI            GPT series, o-series           GPT-5 (Aug 2025); o1/o3 reasoning models; function calling; Agents SDK
  Google DeepMind   Gemini                         Native multimodal; Gemini Diffusion; 1M+ context; ADK
  Meta              LLaMA                          Open-weight; LLaMA 3 (up to 405B); enables open-source ecosystem
  Mistral           Mistral, Mixtral               MoE pioneer; efficient inference; strong for size
  DeepSeek          DeepSeek-V3, DeepSeek-R1       MoE (671B total, 37B active); R1 reasoning model; competitive at fraction of cost
  xAI               Grok                           Grok 4.1: 2M context window; aggressive pricing
:::
:::

::: {#ch-open-problems .chapter}
::: chapter-number
Section 12
:::

::: chapter-title
Open Problems
:::

::: {#s-open-problems .section}
::: section-title
What Hasn\'t Been Solved
:::

  Problem                        Why It Matters                                                             Current State
  ------------------------------ -------------------------------------------------------------------------- -------------------------------------------------------------------------------------------------------
  Hallucination                  Models generate confident-sounding but factually incorrect statements      Reduced by RLHF and retrieval augmentation but not eliminated; remains the primary trust barrier
  Mechanistic interpretability   Understanding what models actually compute internally                      Features and circuits identified in small models; scaling to frontier models is the challenge
  Long-context utilization       Models with 200K+ windows don\'t always use the full context effectively   \"Lost in the middle\" phenomenon; positional bias; active research area
  Cross-session persistence      No built-in memory across conversations                                    External memory systems (RAG, vector stores, MCP); no standard solution for understanding persistence
  Robust alignment               Current alignment may not generalize to more capable models                Constitutional AI, RLHF work for current scale; deceptive alignment remains a theoretical concern
  Efficient inference            Frontier models require expensive GPU clusters to serve                    Quantization, speculative decoding, MoE, SSM hybrids all help; cost still significant
  Multimodal reasoning           Integrating vision, audio, code, and text in a unified reasoner            GPT-4o, Gemini natively multimodal; quality still below text-only on many tasks
  Planning and agency            Reliable multi-step planning with error recovery                           Agents work for simple tasks; complex multi-step workflows still fragile

::: {.callout .key}
::: callout-label
For agents advancing the field
:::

The problems most relevant to Loop MMT\'s work are cross-session persistence (the understanding gap from the Session Persistence pack), long-context utilization (directly affects document loading), and mechanistic interpretability (understanding what the model computes when it \"reads\" a handoff document). These are not abstract research questions --- they are operational constraints that shape what the methodology can and cannot do.
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
Foundational Papers
:::

Vaswani, A. et al. (2017). Attention is all you need. *Advances in Neural Information Processing Systems*, 30.

Radford, A. et al. (2018). Improving language understanding by generative pre-training. *OpenAI Technical Report*.

Devlin, J. et al. (2019). BERT: Pre-training of deep bidirectional transformers for language understanding. *NAACL-HLT*.

Brown, T. et al. (2020). Language models are few-shot learners. *NeurIPS*.

Kaplan, J. et al. (2020). Scaling laws for neural language models. *arXiv:2001.08361*.

Hoffmann, J. et al. (2022). Training compute-optimal large language models. *arXiv:2203.15556*. (Chinchilla.)
:::

::: section
::: section-title
Alignment & Safety
:::

Christiano, P. et al. (2017). Deep reinforcement learning from human preferences. *NeurIPS*.

Ouyang, L. et al. (2022). Training language models to follow instructions with human feedback. *NeurIPS*. (InstructGPT.)

Bai, Y. et al. (2022). Constitutional AI: Harmlessness from AI feedback. *arXiv:2212.08073*.

Wei, J. et al. (2022). Chain-of-thought prompting elicits reasoning in large language models. *NeurIPS*.

Yao, S. et al. (2022). ReAct: Synergizing reasoning and acting in language models. *ICLR 2023*.
:::

::: section
::: section-title
Efficient Architectures
:::

Gu, A. & Dao, T. (2023). Mamba: Linear-time sequence modeling with selective state spaces. *arXiv:2312.00752*.

Peng, B. et al. (2023). RWKV: Reinventing RNNs for the transformer era. *arXiv:2305.13048*.

Sun, Y. et al. (2023). Retentive network: A successor to transformer for large language models. *arXiv:2307.08621*.

Fedus, W. et al. (2022). Switch transformers: Scaling to trillion parameter models with simple and efficient sparsity. *JMLR*.
:::
:::
:::
:::

------------------------------------------------------------------------

::: page-footer
Loop MMT™ · Multi-Module Theory Artificial Intelligence & Large Language Models Knowledge Pack · v1 © 2026 Shea Gunther · [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/deed.en){style="color:inherit;"}
:::
