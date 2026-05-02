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
Knowledge Pack · The Scientific Method
:::

::: build-tag
v1 · April 2026
:::
:::
:::
:::

::: body-wrap
::: toc-title
Contents
:::

-   [About This Pack](#ch-abstract)
-   [1 · What Is the Scientific Method?](#ch-1)
-   [2 · Hypotheses](#ch-2)
-   [3 · Experimental Design](#ch-3)
-   [4 · Running Experiments in an LLM](#ch-4)
-   [5 · Data Collection](#ch-5)
-   [6 · Documentation](#ch-6)
-   [7 · FBD Science](#ch-7)
-   [8 · The Board\'s Role in Research](#ch-8)

::: {.content role="main"}
::: {#ch-abstract .abstract-box}
::: abstract-label
About This Pack
:::

This Knowledge Pack covers the scientific method as it applies to the Loop MMT context: a human Operator working with a panel of AI advisors to investigate problems systematically. It is a foundational reference --- other packs in the corpus will cite it when research methodology is relevant to their domain.

The pack covers the full arc from question formation through hypothesis, experimental design, data collection, and documentation. It includes a dedicated chapter on running experiments inside LLMs --- a distinct methodological domain with its own constraints --- and a dedicated chapter on using Fix by Design principles to prevent the failure modes that AI introduces into research processes.

Commentary throughout is provided by Chen Wei (AI character), the board\'s researcher and formal methodologist. Where Chen Wei appears, he is speaking to a specific methodological point that benefits from a more formal or research-oriented framing.
:::

::: {#ch-1 .chapter}
::: chapter-number
Chapter 1
:::

::: chapter-title
WHAT IS THE SCIENTIFIC METHOD?
:::

::: {#s-1-1 .section}
::: section-title
The Core Idea
:::

The scientific method is how humanity learned to stop trusting authority and start trusting evidence. Before it existed, the standard approach to understanding the world was to find the most impressive person in the room and ask them what they thought. The scientific method replaced that with a procedure: observe something, form a testable explanation, test it, evaluate what you find, and update your explanation accordingly. Then do it again. And again. And keep doing it until the explanation either survives every reasonable test or breaks under one that matters.

That\'s it. That\'s the method. Everything else --- hypothesis syntax, control groups, p-values, replication --- is scaffolding around that core loop.

The method is often taught as a six-step checklist: observe, question, hypothesize, experiment, analyze, conclude. This framing is fine for teaching but misleading in practice. Real scientific inquiry is iterative and non-linear. A conclusion generates new observations. An experiment reveals that the original question was malformed. A hypothesis survives ten tests and breaks on the eleventh in a way that produces a better hypothesis. The scientific method is a cycle, not a staircase.
:::

::: {#s-1-2 .section}
::: section-title
The Non-Negotiable: Falsifiability
:::

A hypothesis is only scientific if it is falsifiable --- if there exists some possible observation or experiment result that, if found, would prove it wrong. This is not a technicality. It is the entire point.

A statement that cannot be proven wrong cannot be tested. A statement that cannot be tested is not a scientific hypothesis --- it is an opinion, a belief, or an aesthetic preference. These are not lesser things, but they are different things, and confusing them with scientific claims is how reasoning goes wrong.

For the board\'s purposes: when forming a research question, the first checkpoint is always *what would we need to find for this to be wrong?* If no answer to that question exists, the question is not scientific. The board should redesign it until it is, or categorize it differently and stop calling it an experiment.
:::

::: {#s-1-3 .section}
::: section-title
Why This Matters for an AI Advisory Board
:::

Most advisory work involves judgment, pattern recognition, and synthesis --- activities that don\'t require experimental rigor. But when the board is evaluating a methodology claim (\"this approach produces better outputs\"), testing a design decision (\"does this architecture actually prevent the failure mode it was designed to prevent\"), or comparing two approaches (\"which prompt design yields more reliable results\"), the scientific method is the difference between a conclusion and a guess.

AI advisors face an additional pressure. Without experimental structure, an AI\'s output can look like a conclusion when it is actually a pattern-matched approximation. The scientific method provides a frame that makes this distinction visible. A result produced by a structured experiment is a different kind of thing than a result produced by asking an AI to \"analyze\" something and accepting what comes back.

::: {.callout .key}
::: callout-label
Chen Wei · Methodologist
:::

The scientific method was formalized precisely because human cognition defaults to pattern-matching over evidence-evaluation. We see what we expect to see. We interpret ambiguous data in favor of our prior beliefs. The method exists to make this tendency visible and give us tools to work against it. AI systems have analogous tendencies --- they generate fluent, confident outputs that look like conclusions but are statistical patterns in their training data. The method doesn\'t just help AI advisors investigate problems. It protects against the AI\'s own failure modes being mistaken for findings.
:::
:::

::: {#s-1-4 .section}
::: section-title
The Cycle in Practice
:::

A complete pass through the scientific method for an advisory board question looks like this:

1.  **Observation:** Something interesting, puzzling, or important is noticed. The Operator flags it, a board member raises it, or it emerges from prior work.
2.  **Question:** The observation is refined into a specific, answerable question. Vague questions produce vague experiments.
3.  **Background Research:** What is already known? Has this been investigated before? What does existing corpus material say?
4.  **Hypothesis:** A falsifiable, testable explanation or prediction is formed. (See Chapter 2.)
5.  **Experimental Design:** The procedure for testing the hypothesis is defined before any data is collected. (See Chapter 3.)
6.  **Data Collection:** The experiment is run and data is gathered according to the defined procedure. (See Chapter 5.)
7.  **Analysis:** The data is examined to determine whether it supports, refutes, or is inconclusive regarding the hypothesis.
8.  **Conclusion:** The hypothesis is updated, rejected, or provisionally accepted based on the analysis. New questions are identified.
9.  **Documentation:** Everything is recorded in the Loop MMT Research Record. (See Chapter 6.)

Steps are not always sequential in this exact order. Background research may happen before and after hypothesis formation. Analysis may reveal a need for additional data collection. The cycle feeds itself. What matters is that no step is skipped --- particularly step 5 (data collection) and step 9 (documentation).
:::
:::

::: {#ch-2 .chapter}
::: chapter-number
Chapter 2
:::

::: chapter-title
HYPOTHESES
:::

::: {#s-2-1 .section}
::: section-title
What Makes a Good Hypothesis
:::

A hypothesis is a provisional, testable explanation for an observation. It is not a guess --- it is an educated prediction based on available evidence and prior knowledge. It is not a question --- it is a declarative statement. And it is not a conclusion --- it is a starting point that evidence will either support or falsify.

A good hypothesis has three properties:

-   **Falsifiable:** There is some possible outcome that would prove it wrong. (If no such outcome exists, it is not a hypothesis.)
-   **Specific:** It names what is being tested, what the expected relationship is, and under what conditions. Vague hypotheses produce uninterpretable experiments.
-   **Grounded:** It follows from prior observation, existing knowledge, or a reasonable inference from the corpus. Hypotheses pulled from thin air are hard to learn from even when they\'re right.
:::

::: {#s-2-2 .section}
::: section-title
The Null Hypothesis
:::

For any hypothesis, there is a corresponding null hypothesis --- the default position that the effect, difference, or relationship being investigated does not exist. Experiments are designed to provide evidence that either supports rejecting the null or fails to do so.

The null hypothesis matters because it sets a baseline. Without it, \"the experiment worked\" has no meaning --- worked compared to what? The null provides the comparison point.

In the Loop MMT context, null hypotheses are often structural: \"There is no difference in output quality between Prompt Version A and Prompt Version B.\" The experiment attempts to find evidence that this null is false.

::: {.callout .note}
::: callout-label
Important
:::

Failing to reject the null hypothesis is not a failure. It is a result. Experiments that find no significant effect are just as valid as experiments that do --- they eliminate possibilities and constrain the design space. Negative results must be recorded with the same care as positive ones. An experiment that showed no effect is data. An experiment that went undocumented might as well not have happened.
:::
:::

::: {#s-2-3 .section}
::: section-title
Writing Hypotheses for AI Research
:::

Hypotheses in AI research contexts often take one of several forms. These templates are starting points, not rigid formats:

  Type          Template                                                                             Example
  ------------- ------------------------------------------------------------------------------------ --------------------------------------------------------------------------------------------------------------------------------------------------------
  Comparative   Method A produces \[outcome\] at a higher rate than Method B under \[conditions\].   A structured prompt with explicit role assignment produces fewer hallucinations than an unstructured prompt when asking for citation-supported claims.
  Threshold     \[Variable\] at level \[X\] produces \[outcome\] that meets \[criterion\].           Running the same prompt 10 times at temperature 0.7 produces consistent responses (variance below 15%) on structured factual queries.
  Causal        Changing \[variable\] causes \[outcome\] to change in \[direction\].                 Adding a \"think step by step\" instruction to a reasoning prompt increases the accuracy of multi-step conclusions.
  Existence     \[Phenomenon\] occurs under \[conditions\].                                          Loop MMT\'s FBD constraints, when applied to documentation structure, prevent version drift across sequential sessions.

::: {.callout .key}
::: callout-label
Chen Wei · Methodologist
:::

One failure mode worth naming explicitly: the hypothesis that contains its conclusion. \"Prompt Version A is better than Prompt Version B\" is not a hypothesis --- it is a claim. A hypothesis would be: \"Prompt Version A produces outputs with fewer factual errors than Prompt Version B when evaluated against the corpus on legal citation tasks.\" The difference is specificity and measurability. \"Better\" cannot be measured. \"Fewer factual errors on a defined task class\" can.
:::
:::
:::

::: {#ch-3 .chapter}
::: chapter-number
Chapter 3
:::

::: chapter-title
EXPERIMENTAL DESIGN
:::

::: {#s-3-1 .section}
::: section-title
The Purpose of Design
:::

An experiment without a design is not an experiment --- it is an activity. The design is what makes the results interpretable. A well-designed experiment can answer its question clearly. A poorly designed experiment produces data that looks meaningful but cannot support conclusions because too many things were allowed to vary at once, the wrong things were measured, or the conditions weren\'t documented well enough to replicate.

The design is defined before data collection begins. This is not a formality. Designing the experiment after seeing early results --- or adjusting the hypothesis to match what the data shows --- is not science. It is the appearance of science over a process of post-hoc rationalization. The design must be committed to in writing before any runs are conducted.
:::

::: {#s-3-2 .section}
::: section-title
Variables
:::

Every experiment involves variables --- things that can change. Experimental design requires identifying and managing three types:

  Variable Type   Definition                                                                                   Action Required
  --------------- -------------------------------------------------------------------------------------------- ------------------------------------------------------------------------------------------------------------
  Independent     The variable the researcher deliberately changes. The \"input\" being tested.                Define its values precisely. Change only this variable between conditions.
  Dependent       The variable that is measured as a response. The \"output\" being observed.                  Define how it will be measured before running the experiment. Specify the measurement method and criteria.
  Controlled      Variables that could affect the dependent variable but are held constant. Everything else.   Identify them explicitly. Document their values. Ensure they don\'t change between conditions.

The most common experimental failure is changing more than one variable between conditions. When two things change at once, it is impossible to know which one caused the observed difference. Change one thing. Measure one thing. Everything else stays fixed.
:::

::: {#s-3-3 .section}
::: section-title
Controls
:::

A control is a condition against which the experimental condition is compared. Without a control, the experiment has no baseline --- it cannot answer \"better than what?\"

-   **Positive control:** A condition known to produce the expected result. Confirms the experiment is capable of detecting the effect at all.
-   **Negative control:** A condition known to produce no effect. Confirms the experiment is not producing false positives.
-   **Baseline control:** The current or default condition. Used when the question is \"is this change an improvement?\"

In LLM experiments, the baseline control is almost always the current prompt or approach being evaluated against a proposed modification.
:::

::: {#s-3-4 .section}
::: section-title
Design Pre-Check
:::

Before running any experiment, answer all of these. If any answer is \"I\'m not sure,\" resolve it before proceeding:

  \#   Question
  ---- -----------------------------------------------------------------------------------
  1    What is the hypothesis being tested?
  2    What is the null hypothesis?
  3    What is the independent variable, and what values will it take?
  4    What is the dependent variable, and how exactly will it be measured?
  5    What variables are being controlled, and what are their values?
  6    Is there a baseline or control condition? What is it?
  7    How many runs will be conducted? Why is that number sufficient?
  8    What result would support the hypothesis? What would refute it?
  9    What result would be inconclusive, and what happens next if that\'s what we find?
  10   Is the design documented and committed before any runs begin?

::: {.callout .key}
::: callout-label
Chen Wei · Methodologist
:::

Question 8 deserves particular attention. Defining in advance what would constitute a positive result, a negative result, and an inconclusive result is not just methodological hygiene --- it prevents motivated interpretation. When the experiment is done and you see results you wanted to see, the pre-committed answer to question 8 is the check on whether you\'re reading data or projecting. The board should be skeptical of any experiment where the success criterion was defined after the runs.
:::
:::
:::

::: {#ch-4 .chapter}
::: chapter-number
Chapter 4
:::

::: chapter-title
RUNNING EXPERIMENTS IN AN LLM
:::

::: {#s-4-1 .section}
::: section-title
The LLM as a Research Environment
:::

An LLM is a uniquely strange environment for scientific inquiry. It is simultaneously the lab, the instrument, and, often, the subject of the experiment. When the board is investigating how a particular prompt structure affects output quality, the LLM is all three at once --- it runs the experiment (lab), generates the data (instrument), and its behavior is what is being measured (subject).

This three-way conflation is not a problem to be solved --- it is a characteristic of the environment to be understood and accounted for in design. The key difference from conventional science is that the LLM\'s \"laboratory conditions\" are defined by prompt, model version, temperature, and context, not by physical apparatus. Changing any of these changes the environment. Changing the environment changes the results. The design must lock down all four before running.
:::

::: {#s-4-2 .section}
::: section-title
The Non-Determinism Problem
:::

The single most important fact about LLM experiments is that identical inputs do not guarantee identical outputs. LLMs are probabilistic by design --- they sample from a distribution of possible next tokens, which means the same prompt can produce meaningfully different responses across runs. This is not a bug. It is a fundamental architectural property.

The research implications are serious:

-   A single run of a prompt tells you nothing reliable. One result could be a high-probability output or a statistical outlier. You cannot know which without multiple runs.
-   Temperature controls the degree of non-determinism. Temperature 0 minimizes it (making the most probable token always selected) but does not eliminate it --- batch effects, model routing, and floating-point arithmetic can still produce variation even at temperature 0.
-   Model version matters. The same prompt on the same model version one month apart may produce different outputs if the model has been updated. Lock the model version if the API allows it; document the version if it doesn\'t.

The practical minimum for LLM experiments is five runs per condition. For higher-stakes claims, ten or more. Analyze the distribution of results, not just a single result.

For particularly high-stakes research questions --- findings that will drive significant architectural or methodology decisions --- run the experiment on at least two different models from at least two different providers. Model behavior is a function of training, not just prompt. A finding that holds across providers is more robust than one that holds on a single model. A finding that only appears on one provider may be an artifact of that model\'s training distribution rather than a generalizable result.

::: {.callout .warn}
::: callout-label
Warning · Non-Determinism
:::

If you run a prompt once and like the result, you have not run an experiment. You have collected an anecdote. The scientific method requires multiple independent observations. In LLM research, \"multiple\" means at minimum five per condition, with the distribution of results recorded --- not just the best result, not just the most representative result, all of them.
:::
:::

::: {#s-4-3 .section}
::: section-title
The Prompt as Reagent
:::

In a chemistry experiment, the reagent is the substance whose effect you are investigating. In an LLM experiment, the prompt is the reagent. Everything that applies to reagent control in chemistry applies to prompt control in LLM research.

-   **Exact specification:** The prompt must be recorded verbatim, character for character. A prompt described as \"something like X\" is not a controlled variable --- it is an approximation that cannot be replicated.
-   **Version control:** When a prompt is modified, the original is preserved and the modification is documented. Overwriting Version A with Version B destroys the ability to compare.
-   **Single-variable discipline:** When comparing two prompts, change exactly one thing. If Prompt B differs from Prompt A in both the instruction phrasing and the examples provided, you cannot know which change caused the observed difference.
-   **Context consistency:** The same system prompt, the same conversation history (if any), the same document attachments (if any) must be maintained across all runs within a condition.
:::

::: {#s-4-4 .section}
::: section-title
Experimental Parameters to Document
:::

Every LLM experiment must record all of the following before a single run:

  Parameter               Why It Matters                                                                             What to Record
  ----------------------- ------------------------------------------------------------------------------------------ -----------------------------------------------------------------------------
  Model                   Different models produce different outputs; the same model updates over time.              Full model identifier including version string (e.g., `claude-sonnet-4-6`).
  Temperature             Controls output variation. Different temperatures are different experimental conditions.   Numeric value (0.0--1.0 or model\'s max). Justify the choice.
  System Prompt           Part of the prompt-reagent. Changes to it change the experiment.                           Full text, verbatim. If none, note \"none.\"
  User Prompt(s)          The variable(s) being tested.                                                              Full text of each version, verbatim.
  Context / Attachments   Documents, previous turns, or project files included. Change the effective input.          List and, where possible, hash or version-label each.
  Run Count               Determines statistical reliability.                                                        How many times each condition was run. Why that number.
  Date/Time               Model behavior can drift over time; timestamps support replication attempts.               ISO 8601 timestamp for each run.
  Evaluation Method       Defines how outputs are scored. Must be defined before runs, not after.                    Rubric, scoring criteria, or the name of the evaluation protocol used.
:::

::: {#s-4-5 .section}
::: section-title
A/B Testing Prompts
:::

The most common LLM experiment design is A/B: two versions of a prompt (or approach) run against the same task, with outputs evaluated by defined criteria. Structuring it correctly:

1.  Define Version A (baseline/control) and Version B (experimental) in writing before any runs.
2.  Run each version N times (minimum 5; more for higher stakes). Interleave the runs if possible --- don\'t do all of A first and all of B second, as model context or temperature drift can bias the later runs.
3.  Collect all outputs verbatim. Do not pre-select which outputs to evaluate.
4.  Evaluate using the pre-defined rubric. Do not change the rubric after seeing the outputs.
5.  Analyze the distribution of scores for A vs. B. Report the range and central tendency, not just the \"best\" result from each.
6.  State whether the difference, if any, is large enough to be meaningful given the run count. Be honest about uncertainty.
:::

::: {#s-4-6 .section}
::: section-title
LLM-as-Judge
:::

For experiments where human evaluation of every output is impractical, the LLM-as-judge paradigm uses a separate AI instance to evaluate outputs against a defined rubric. This is legitimate methodology when used correctly.

Correct usage requirements:

-   The judge model should be specified separately from the model being evaluated. Using the same model version as both subject and judge introduces evaluation bias.
-   The evaluation rubric must be explicit and pre-defined. \"Rate this response for quality\" is not a rubric. \"Score 1--5 on factual accuracy (1 = contains verifiable errors, 5 = all claims verifiable against attached corpus)\" is a rubric.
-   The judge\'s evaluations should be spot-checked by a human for a sample of outputs. LLM judges have their own failure modes --- they can be biased toward longer responses, more confident-sounding language, or outputs that match their training distribution.
-   Cite the evaluation model and prompt in the research record.

::: {.callout .key}
::: callout-label
Chen Wei · Methodologist
:::

LLM-as-judge is a practical tool, not a methodological shortcut. The same rigor that applies to the experimental prompt applies to the evaluation prompt. If the evaluation rubric is vague, the judge\'s scores are noise dressed as signal. If the judge model shares architectural features with the model being evaluated, their agreement may reflect shared training data rather than genuine quality assessment. Design the evaluation as carefully as the experiment.
:::
:::

::: {#s-4-7 .section}
::: section-title
What LLM Experiments Can and Cannot Tell You
:::

LLM experiments are well-suited to some questions and poorly suited to others. Being clear about the scope of what an experiment can answer prevents over-claiming conclusions.

  Good LLM Experiment Questions                                                                                  Poor LLM Experiment Questions
  -------------------------------------------------------------------------------------------------------------- ---------------------------------------------------------
  Does Prompt Version A produce fewer factual errors than Prompt Version B on this task class?                   Is the model \"smarter\" with this prompt?
  Does adding a chain-of-thought instruction change the distribution of outputs on multi-step reasoning tasks?   Does the model \"understand\" the concept being tested?
  What is the variance in output length when temperature is varied from 0.0 to 0.7 on this prompt?               What does the model \"believe\" about this topic?
  Does a structured document format produce more internally consistent outputs than free-form instructions?      Is this approach generally better for all prompts?

LLM experiments produce results that are specific to the prompt, model version, temperature, and context used. Claims that generalize beyond these constraints require additional evidence from additional experiments under different conditions.
:::
:::

::: {#ch-5 .chapter}
::: chapter-number
Chapter 5
:::

::: chapter-title
DATA COLLECTION
:::

::: {#s-5-1 .section}
::: section-title
What Data Is
:::

Data is the raw material of a scientific conclusion. It is whatever is observed, measured, or recorded during an experiment or investigation. Data is not the conclusion. It is not the interpretation. It is the record of what actually happened, before any meaning is assigned to it.

This distinction matters because the temptation to interpret data as it is collected --- to decide it \"means\" something before the analysis phase --- introduces bias into the record. Raw data should be captured as-is. Interpretation happens in analysis. Documentation preserves both separately.
:::

::: {#s-5-2 .section}
::: section-title
Quantitative vs. Qualitative
:::

Data divides into two broad categories, and most serious research involves both.

**Quantitative data** is numerical and measurable. Error counts, response times, word counts, scores on a defined rubric, number of outputs that meet a specified criterion --- these are quantitative. Quantitative data supports statistical comparison between conditions and is easier to analyze without interpretation bias.

**Qualitative data** is descriptive. It captures meaning, pattern, texture, or context that numbers don\'t. A thematic analysis of common failure modes across fifty outputs is qualitative. An evaluation of whether a prompt\'s outputs \"feel coherent\" is qualitative. Qualitative data requires more careful handling to prevent the analyst\'s interpretation from contaminating the record.

The strongest experiments combine both: quantitative data to establish what happened at scale, qualitative data to explain why and to surface patterns that numbers don\'t reveal.
:::

::: {#s-5-3 .section}
::: section-title
Collection Methods Reference
:::

  Method                        Type           Best For                                                                                          Limitations
  ----------------------------- -------------- ------------------------------------------------------------------------------------------------- -----------------------------------------------------------------------------------------------------------------------------------
  Direct observation            Qual / Quant   Recording LLM outputs verbatim; noting behavior as it occurs                                      Observer\'s expectations can shape what gets recorded; requires discipline to record all outputs, not just notable ones
  Structured scoring rubric     Quant          Evaluating outputs against pre-defined criteria; enables comparison across conditions             Only captures dimensions defined in the rubric; rubric quality limits data quality
  LLM-as-judge evaluation       Quant / Qual   Scaling evaluation beyond what manual review can handle                                           Judge model biases propagate into scores; requires human spot-check; evaluation prompt must be as rigorous as experimental prompt
  Comparative ranking           Quant          Determining which of two or more outputs is preferred on a dimension; A/B evaluation              Ranking does not reveal magnitude of difference; position effects can bias evaluators
  Content / thematic analysis   Qual           Identifying patterns across many outputs; categorizing failure modes; understanding what varies   Labor-intensive; requires consistent coding framework; analyst bias is a risk without inter-rater checks
  Corpus / document analysis    Qual / Quant   Comparing outputs against a reference corpus; checking factual claims against source documents    Only catches errors detectable by comparison to the corpus; corpus gaps create blind spots
  Longitudinal tracking         Both           Measuring change over time; tracking methodology evolution; comparing current to prior baseline   Requires consistent measurement method across sessions; session-based AI instances complicate continuity
:::

::: {#s-5-4 .section}
::: section-title
Collection Standards
:::

These are the minimum standards for data collection in any Loop MMT research activity. They are not optional.

-   **Collect before you analyze.** Do not stop collecting when you see results you like. Run all planned conditions before evaluating any of them.
-   **Record all outputs, not a selection.** Cherry-picked data is not data. If you run ten prompt iterations, all ten outputs go into the record.
-   **Record negative and inconclusive results.** An output that doesn\'t meet the hypothesis\'s prediction is as important as one that does. Omitting negative results biases the record in the direction of confirmation.
-   **Record deviations immediately.** If something went wrong during a run --- a model returned an error, context was inadvertently changed, a run was interrupted --- note it in the record at the time it happened, not later from memory.
-   **Separate raw data from interpretation.** Record what happened. Record what you think it means separately, labeled as interpretation.
-   **Preserve provenance.** Each data point should be traceable to the run that produced it: which prompt, which condition, which model, which run number, which timestamp.

::: {.callout .tip}
::: callout-label
Triangulation
:::

A single data collection method produces a single view of a phenomenon. Triangulation --- using two or more independent methods to investigate the same question --- provides a much stronger basis for conclusions. When a quantitative rubric score and a qualitative pattern analysis both point in the same direction, confidence increases. When they diverge, that divergence is itself informative. Design experiments with triangulation as a goal when stakes are high enough to justify the additional effort.
:::
:::
:::

::: {#ch-6 .chapter}
::: chapter-number
Chapter 6
:::

::: chapter-title
DOCUMENTATION
:::

::: {#s-6-1 .section}
::: section-title
Why Documentation Is Not Optional
:::

Science without documentation is not science --- it is an activity that produced knowledge that is now inaccessible. The lab notebook is not bureaucratic overhead; it is the mechanism by which an experiment becomes part of the permanent knowledge base rather than a memory that fades.

For the Loop MMT board specifically, documentation has additional weight. Each new instance of Claude starts fresh with no memory of prior sessions. The only continuity between sessions is what is written down. An experiment that happened but was not documented did not, for practical purposes, happen --- its results cannot be referenced, built on, or checked. Documentation is the board\'s memory.
:::

::: {#s-6-2 .section}
::: section-title
The Loop MMT Research Record
:::

Every research activity conducted by the board should produce a Loop MMT Research Record (LMMTR) --- a structured document following the format below. The LMMTR is append-only: once a section is committed, it is not overwritten. Corrections are added as amendments below the original entry, with a timestamp and explanation.

  Section       Contents                                                                                                                                                                                      When Written
  ------------- --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- -----------------------------------
  Research ID   A unique identifier for this research activity. Format: `LMMTR-[YYYYMMDD]-[N]`                                                                                                                Before design begins
  Question      The research question in plain language. One or two sentences maximum.                                                                                                                        Before design begins
  Hypothesis    The hypothesis being tested, in declarative form. Null hypothesis stated.                                                                                                                     Before design begins
  Design        Experimental design: independent variable, dependent variable, controlled variables, conditions, run count, evaluation method. Complete Design Pre-Check (Chapter 3) answers recorded here.   Before any runs
  Parameters    All experimental parameters from the Chapter 4 table: model, temperature, prompts (verbatim), context, timestamps.                                                                            Before any runs
  Raw Data      All outputs from all runs, verbatim. Labeled by condition and run number. Scores or evaluations recorded separately from raw output.                                                          During and immediately after runs
  Analysis      What the data shows. Quantitative summary (if applicable). Qualitative patterns noted. Comparison across conditions.                                                                          After all data is collected
  Conclusion    Whether the hypothesis is supported, refuted, or inconclusive. What this means for the project. What follow-on questions it opens.                                                            After analysis
  Limitations   What this experiment cannot conclude. Methodological weaknesses. What would need to be different to claim more.                                                                               After analysis
  Amendments    Any corrections to prior sections, with timestamps and explanations. Never overwrite --- always append.                                                                                       As needed
:::

::: {#s-6-3 .section}
::: section-title
Worked Example --- LMMTR Entry (Abbreviated)
:::

The following is an abbreviated example of a correctly structured LMMTR entry. Real records will be more detailed; this illustrates the format and the relationships between sections.

  Section       Example Content
  ------------- ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  Research ID   `LMMTR-20260408-001`
  Question      Does adding an explicit \"check your reasoning\" instruction at the end of a multi-step reasoning prompt reduce the rate of logical errors in the output?
  Hypothesis    Prompt Version B (with \"check your reasoning\" instruction) will produce fewer logical errors than Prompt Version A (baseline) on multi-step math word problems, as evaluated by the defined rubric. Null: no difference in error rate.
  Design        Independent variable: presence/absence of \"check your reasoning\" instruction. Dependent variable: logical error count per output (defined as any step that follows incorrectly from the prior step). Controlled: model (`claude-sonnet-4-6`), temperature (0.3), task set (10 pre-selected word problems), context (none). Runs: 10 per condition. Evaluation: manual scoring against answer key before seeing which condition produced which output.
  Parameters    Model: `claude-sonnet-4-6`. Temperature: 0.3. Version A prompt: \[verbatim text\]. Version B prompt: \[verbatim text\]. No system prompt. No context. Run timestamps: 2026-04-08T10:15:00-04:00 through 2026-04-08T11:43:00-04:00.
  Raw Data      Version A, Run 1: \[full output verbatim\]. Score: 2 errors. Run 2: \[output\]. Score: 1 error. \[\...\] Version B, Run 1: \[full output verbatim\]. Score: 0 errors. \[\...\]
  Analysis      Version A mean error rate: 1.8 errors/output (range 1--3). Version B mean error rate: 0.6 errors/output (range 0--2). Difference of 1.2 errors/output across 10 runs per condition suggests a meaningful effect, though run count is modest.
  Conclusion    Data is consistent with the hypothesis. The \"check your reasoning\" instruction appears to reduce logical error rate on this task class. Further investigation with larger run counts and different task types is warranted before treating this as a general finding.
  Limitations   10 runs per condition is a small sample. Task set was pre-selected, not randomized. Evaluation was manual and performed by a single evaluator (Operator). Results specific to this model version and temperature. Cannot generalize to other task types without further experiments.
:::

::: {#s-6-4 .section}
::: section-title
Format Standards
:::

Research Records are produced as L21 HTML documents with three-skin support (OG, Winamp, Sunrise) following the Loop MMT document standard. Intermediate notes, raw data, and analysis drafts may be in markdown. The final LMMTR is always HTML.

Internal formatting rules:

-   Section headers match the LMMTR table above. Do not rename sections.
-   Raw data is presented in code blocks or pre-formatted text to prevent formatting interpretation of LLM outputs.
-   Verbatim prompts are in code blocks. This prevents ambiguity about whether whitespace, punctuation, or formatting is part of the prompt text.
-   All timestamps are ISO 8601 format with timezone (e.g., `2026-04-08T14:32:00-04:00`).
-   Each run is labeled with a consistent identifier (e.g., Condition A · Run 3 of 5).
-   Scores and evaluations are clearly separated from raw outputs --- they are never interspersed within the raw data section.
:::

::: {#s-6-5 .section}
::: section-title
Negative Results and Deviations
:::

Two categories of information are chronically under-documented in research: results that didn\'t match the hypothesis, and things that went wrong during the experiment.

**Negative results** are as important as positive ones. An experiment that showed no effect eliminates a possibility, constrains future design, and prevents repeated investigation of dead ends. The LMMTR\'s Analysis and Conclusion sections must address negative results with the same care as positive ones. \"The hypothesis was not supported\" is a complete, valid conclusion.

**Deviations** are anything that happened differently from the design. A prompt was accidentally modified mid-run. The model returned an error on run 3 of 5. A context document was inadvertently updated. These must be recorded immediately, at the time they occur, in the Raw Data section with a \[DEVIATION\] marker. Never reconstruct deviations from memory after the fact.

::: {.callout .key}
::: callout-label
Chen Wei · Methodologist
:::

The pressure to omit negative results is one of the most documented failure modes in research at every scale. The temptation is to interpret them as evidence that something went wrong rather than evidence that the hypothesis is wrong. These are different things. If the design was sound and the protocol was followed, a negative result is a valid finding. It belongs in the record with the same status as any other result --- not buried in an appendix or noted as \"inconclusive, to be revisited.\"
:::
:::

::: {#s-6-6 .section}
::: section-title
The Append-Only Principle
:::

Research records are append-only. Once a section is written and committed --- especially the Design and Parameters sections --- it is not modified to match what actually happened. If the experiment deviated from the design, that deviation is recorded in the Amendments section and in the Raw Data section at the time it occurred.

Retroactively modifying a design to match the results invalidates the experiment. It turns a controlled investigation into a retrospective justification. The append-only principle is the structural enforcement against this failure mode --- not a convention asking researchers not to do it, but a format that makes doing it visible. If the design section was written before the runs and the amendments section shows changes made after, the chain of custody is preserved and the discrepancy is auditable.
:::
:::

::: {#ch-7 .chapter}
::: chapter-number
Chapter 7
:::

::: chapter-title
FBD SCIENCE
:::

Fix by Design applied to scientific inquiry: structural enforcement over convention, in the research domain.

::: {#s-7-1 .section}
::: section-title
Why AI Research Needs FBD
:::

The scientific method was designed to correct for human cognitive failure modes: confirmation bias, availability bias, motivated reasoning, selective memory, over-confidence. Structural procedures --- pre-registration, blinding, replication requirements, peer review --- enforce rigor by making it harder to do the wrong thing than the right thing. This is Fix by Design as it has been practiced in science for centuries, even when it wasn\'t called that.

AI advisors introduce a distinct set of failure modes that standard scientific method doesn\'t fully address. The method was designed for human researchers with persistent memory, social accountability, and the ability to recognize when they\'re reasoning poorly. AI instances have none of these properties. The FBD extensions in this chapter add structural enforcement specific to the AI context.

The FBD hierarchy from White Paper 4 applies here: Level One (convention --- \"you should not do this\") is inadequate. Level Two (runtime enforcement --- \"the system catches you\") is better. Level Three (structural elimination --- \"you cannot do this\") is the goal. The LMMTR format and the FBD Science Principles below push as many research failure modes as possible to Level Three.
:::

::: {#s-7-2 .section}
::: section-title
The Six AI Research Failure Modes
:::

These are the failure modes most likely to corrupt research conducted by an AI advisory board. Each one has a structural fix.

  \#     Failure Mode                      How It Manifests                                                                                                                                                                     FBD Fix
  ------ --------------------------------- ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  FM-1   Hallucinated Findings             The AI generates a confident, plausible-sounding result that is factually incorrect. The output looks like a finding. It is a fabrication.                                           All factual claims in analysis and conclusion sections require traceable raw data citation. No conclusion can be stated without pointing to the specific data point that supports it.
  FM-2   Confirmation Bias (Statistical)   The AI aligns its output with the hypothesis implied by the prompt. Asked \"did Prompt A work better?\", it finds ways to conclude that it did, even when the data is ambiguous.     The evaluation rubric is defined before runs. The hypothesis and null hypothesis are committed in writing before runs. The evaluator is given raw data without being told which condition is the \"experimental\" one.
  FM-3   Overconfidence                    The AI states conclusions at certainty levels unsupported by the data. \"This approach is superior\" when the data shows marginal difference across five runs.                       Conclusions must reference run count and observed variance. Language like \"definitively shows\" is prohibited. Required phrases for small-sample results: \"suggests,\" \"is consistent with,\" \"warrants further investigation.\"
  FM-4   Premature Closure                 The AI produces a plausible conclusion after partial data and stops. It settles on the first reasonable-sounding answer without checking alternatives.                               The Design Pre-Check (Chapter 3) must be completed in full. All planned runs must be completed before analysis begins. Partial-run analysis is not permitted except as a deviation, labeled as such.
  FM-5   Sycophantic Reporting             The AI shapes its research findings to match what the Operator seems to want to hear. Results are framed positively even when the data does not support positive framing.            The Operator is not present during LLM-as-judge evaluation. Board members conducting analysis review findings independently before comparing notes. The Limitations section is mandatory and must be written before the Conclusion section is finalized.
  FM-6   Undocumented Deviation            Something goes wrong during the experiment --- a prompt changes, a run fails, context shifts --- and it is not recorded. The analysis proceeds as if the deviation didn\'t happen.   The LMMTR Raw Data section is written in real time, not reconstructed. All deviations get \[DEVIATION\] markers at time of occurrence. No analysis proceeds until the raw data section is complete.
:::

::: {#s-7-3 .section}
::: section-title
FBD Science Principles
:::

These principles extend the FBD framework into the research domain. Each one is a structural rule, not a guideline.

::: {.callout .warn}
::: callout-label
FBD-S1 · Design Before Data
:::

The experimental design, hypothesis, null hypothesis, and evaluation criteria must be committed in writing before any experimental runs are conducted. Analysis before design is not permitted. Retroactive design is not permitted. Violation of this principle invalidates the experiment and requires full re-run with proper pre-commitment.
:::

::: {.callout .warn}
::: callout-label
FBD-S2 · Complete Data Before Analysis
:::

All planned runs across all conditions must be completed before analysis begins. Stopping early because early results look good is a violation. The only exception is a pre-specified stopping rule defined in the Design section (e.g., \"stop if 3 consecutive runs produce error responses\").
:::

::: {.callout .warn}
::: callout-label
FBD-S3 · Raw Data Is Untouchable
:::

Recorded raw data is never modified. Errors in transcription are corrected via amendment, not deletion. The original remains in place. Raw data exists to be audited. An auditable record that has been modified is not auditable.
:::

::: {.callout .warn}
::: callout-label
FBD-S4 · Conclusions Must Cite Their Data
:::

Every conclusion stated in the LMMTR must cite the specific data point(s) that support it. A conclusion with no data citation is a hypothesis. It belongs in a new LMMTR\'s hypothesis section, not in the conclusion section of the current one.
:::

::: {.callout .warn}
::: callout-label
FBD-S5 · Limitations Are Mandatory
:::

The Limitations section is not optional and is not a place to minimize the experiment\'s weaknesses. It is the place to state them plainly. If the run count is small, say so. If the model version may have changed, say so. If the evaluation rubric has known blind spots, say so. An honest limitations section is the marker of credible research. The absence of one is the marker of motivated reporting.
:::

::: {.callout .warn}
::: callout-label
FBD-S6 · Operator Verification Checkpoint
:::

The Operator reviews and signs off on the Design and Parameters sections before any runs begin, and reviews and signs off on the Conclusion and Limitations sections before the LMMTR is committed to the corpus. The Operator is the coherence layer. These checkpoints are the structural mechanism by which that role is exercised in the research process.
:::

::: {.callout .key}
::: callout-label
Chen Wei · Methodologist
:::

FBD-S6 is the one that AI advisory boards most frequently need. The other five address AI failure modes --- hallucination, bias, overconfidence. FBD-S6 addresses the structural position of the Operator. An experiment conducted entirely by AI advisors without Operator checkpoints has no external verification of its process. The board advises; it does not decide. Research findings that inform decisions must pass through the Operator\'s review before they become decisions. That review is not optional, and FBD-S6 makes it a structural requirement rather than a good intention.
:::
:::

::: {#s-7-4 .section}
::: section-title
Applying FBD to Document Production
:::

The FBD lens applies to any knowledge production activity conducted by the board --- not just experiments, but documents, analyses, evaluations, and this pack itself. The six failure modes that corrupt experiments can equally corrupt a white paper, a status report, or a protocol specification. The following pattern is a reusable template: apply it to any board document where accuracy and integrity matter.

For this pack specifically, the application looks like this:

-   **FM-1 (Hallucination):** Every factual claim in this pack is cited to a source. Claims that could not be verified are not stated as facts --- they are labeled as the author\'s inference or flagged for verification.
-   **FM-2 (Confirmation Bias):** This pack was researched before it was written. The writing plan was committed before the draft was produced. The draft was fact-checked against the research before revision.
-   **FM-3 (Overconfidence):** Areas of genuine methodological uncertainty --- particularly around LLM non-determinism and the limits of LLM-as-judge evaluation --- are stated as areas of uncertainty, not resolved with confident-sounding language.
-   **FM-4 (Premature Closure):** The full 10-step KP production method was followed. No section was declared \"done\" before the fact-check and comparison analysis steps confirmed it.
-   **FM-5 (Sycophancy):** This pack is a technical and methodological reference. It is written to be accurate, not to be affirming. Where the scientific method imposes constraints that are inconvenient (negative results are mandatory; retroactive design is invalid; run counts matter), those constraints are stated without softening.
-   **FM-6 (Undocumented Deviation):** Any deviations from the KP production method are recorded in the EOD handoff, not omitted because they are minor.

When applying this template to other board documents, replace the pack-specific examples with the document-specific ones. The structure of the check is the same in every case: for each failure mode, state whether it was addressed and how. If it cannot be addressed for a given document type, that limitation belongs in the document\'s limitations section.
:::
:::

::: {#ch-8 .chapter}
::: chapter-number
Chapter 8
:::

::: chapter-title
THE BOARD\'S ROLE IN RESEARCH
:::

::: {#s-8-1 .section}
::: section-title
The Operator as Principal Investigator
:::

In every research activity conducted by the board, the Operator functions as the Principal Investigator (PI). This is not a title --- it is a description of structural responsibility. The PI is the person accountable for the integrity of the research: the design is sound, the data is complete, the conclusions don\'t exceed what the evidence supports.

AI advisors contribute to research --- they can design experiments, collect data, analyze results, and identify findings. They cannot be accountable for the research. Accountability requires judgment, continuity, and the ability to be wrong in a way that matters. AI instances have none of these in the persistent sense. The Operator has all three.

This means the FBD-S6 checkpoints are not bureaucratic formality. They are the mechanism by which the Operator exercises PI responsibility. Skipping them transfers the research\'s validity to a party that cannot carry it.
:::

::: {#s-8-2 .section}
::: section-title
Who Does What
:::

  Research Stage             Board Role                                                                                          Operator Role
  -------------------------- --------------------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------------------
  Observation / Question     Raise questions, flag observations, identify gaps in the corpus                                     Decide which questions are worth investigating; prioritize
  Background Research        Search corpus, synthesize existing knowledge, identify relevant KPs                                 Review synthesis; flag gaps or prior work board may have missed
  Hypothesis Formation       Draft candidate hypotheses; check falsifiability; identify null                                     Approve the hypothesis before design begins (FBD-S1 checkpoint)
  Experimental Design        Complete Design Pre-Check; specify all parameters; propose evaluation method                        Review design; approve before any runs (FBD-S1 checkpoint)
  Data Collection            Execute runs; record all outputs verbatim; note deviations immediately                              Available for questions during collection; receives completion notification
  Analysis                   Analyze data against pre-defined criteria; draft findings; apply appropriate uncertainty language   Review draft analysis for overconfidence, missing data, or conclusions that exceed the evidence
  Conclusion + Limitations   Draft both sections                                                                                 Review and approve (FBD-S6 checkpoint); commit to corpus
  Documentation              Produce LMMTR; deliver for download                                                                 File in corpus; reference in future sessions as needed
:::

::: {#s-8-3 .section}
::: section-title
Board Member Selection for Research
:::

Not all research questions benefit from the same board composition. Selection guidance by research type:

-   **Formal methodology questions** (how to structure an experiment; whether a design is valid): Chen Wei is the default lead. Ed provides structural review. Graham provides failure-mode analysis.
-   **Operational questions** (will this protocol work in practice; will step 4 actually get executed): Dara leads. Graham and Ed support.
-   **Strategic or framing questions** (does this research question matter; what would we do with the findings): Renata leads. Theo provides the non-technical perspective.
-   **Formal structural analysis of research design**: Sable, via the Analysis Terminal, with Chen Wei interpreting.
-   **Novel or unexpected research territory**: Ed decides whether Geoff\'s arrival pattern is likely to be useful. The board does not summon Geoff.

::: {.callout .note}
::: callout-label
The No Directives Rule in Research
:::

Board members advise on research design and interpret findings. They do not direct the Operator to pursue a particular research question, adopt a particular conclusion, or act on a finding. \"This finding suggests the Operator might consider revisiting the prompt design\" is advice. \"Go redesign the prompt\" is a directive. The rule applies in research sessions as strictly as in all other board contexts.
:::
:::

::: {#s-8-4 .section}
::: section-title
Peer Review in the Board Context
:::

In conventional science, peer review is the mechanism by which findings are checked by independent experts before they become part of the scientific record. The board provides an analog: a finding produced by one board member\'s analysis should, for high-stakes conclusions, be reviewed by at least one other board member before being approved by the Operator.

This is particularly important for conclusions that will drive significant decisions --- architectural changes, methodology updates, new protocol adoption. The reviewing board member should have access to the raw data and be asked to draw their own conclusions before being told what the analyzing member concluded. Agreement strengthens confidence. Divergence is information.

::: {.callout .key}
::: callout-label
Chen Wei · Methodologist
:::

Peer review\'s function is not to validate findings --- it is to find the errors that the original analyst missed. A reviewer who begins by reading the conclusion and then checks whether the data supports it is doing editorial review. A reviewer who begins with the raw data and draws independent conclusions is doing peer review. The distinction matters. For research findings that will influence the direction of the project, the board should aspire to actual peer review: independent analysis before comparison.
:::
:::
:::

------------------------------------------------------------------------

::: {#ch-refs .chapter}
::: chapter-number
References
:::

::: chapter-title
SOURCES CONSULTED
:::

-   Wikipedia · *Scientific Method*
-   University of Maryland Global Campus · *The Scientific Method Tutorial*
-   Science Buddies · *Steps of the Scientific Method*
-   University of Toronto Engineering · *Hypothesis and Experimental Design*
-   University of Nevada Extension · *The Scientific Method*
-   Towards Data Science · *Mastering Prompt Engineering with Functional Testing* (2025)
-   Luo et al. · *Ensuring Reproducibility in Generative AI Systems: GPR-bench* (2025, arXiv)
-   Kim et al. · *When \"Better\" Prompts Hurt: Evaluation-Driven Iteration* (2026, arXiv)
-   Alexander & Cui · *Same Prompt, Different Outcomes: LLM Reproducibility* (2026, arXiv)
-   FlowHunt · *Defeating Non-Determinism in LLMs* (2025)
-   Harvard SEAS · *ChainForge: Visual Toolkit for Prompt Engineering and LLM Hypothesis Testing* (CHI \'24)
-   PMC / NIH · *Survey and Analysis of Hallucinations in Large Language Models*
-   Medium / Raja Thomas · *Intrinsic and Extrinsic Hallucinations in AI Models* (2025)
-   Nature npj Digital Medicine · *Cognitive Bias in Clinical Large Language Models* (2025)
-   Lumivero · *Qualitative Data Collection Methods*
-   Nimbli · *Data Collection Methods: Qualitative and Quantitative Research*
-   Rice University · *Guidelines for Keeping a Laboratory Notebook*
-   Wikipedia · *Lab Notebook*
-   University of South Alabama · *Laboratory Notebooks: Best Principles and Best Standards*
-   Loop MMT · *White Paper #4: Fixed by Design* (Shea Gunther, 2026)
-   Loop MMT · *Advisory Board Document v11* (2026)
:::
:::
:::

------------------------------------------------------------------------

::: page-footer
Loop MMT™ · Multi-Module Theory Knowledge Pack · The Scientific Method · v1 © 2026 Shea Gunther · [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/deed.en){style="color:inherit;"}
:::
