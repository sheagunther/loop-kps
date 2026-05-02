# Cognitive Bias & Metacognition Knowledge Pack

**Loop MMT™ · Multi-Module Theory**
**v1 · 9 April 2026**

---

## About This Document

A field guide to systematic reasoning failures for AI advisory conversations. Covers the heuristics-and-biases research program (Kahneman & Tversky), six major cognitive biases, the Dunning-Kruger effect, metacognitive monitoring and calibration, evidence-based debiasing strategies, and AI-specific failure modes including confabulation and sycophancy. The purpose is not to catalog biases but to make them operationally detectable. For an AI advisory system, these are the specific mechanisms by which its output—and the reasoning of the humans it advises—goes wrong in predictable ways. Pack 4 of 11 in the Basis Pack series. Founded on Kahneman (2011), Tversky & Kahneman (1974), Fischhoff (1982), Tetlock (2015), Stanovich (2009), and Dunning (2005).

---

## Section 1 · Foundations: How Thinking Goes Wrong

### System 1 and System 2

Kahneman's *Thinking, Fast and Slow* (2011) organized decades of cognitive research into a dual-process framework. **System 1** operates fast, automatically, and with little effort—it reads facial expressions, completes familiar phrases, and orients toward sudden sounds. **System 2** operates slowly, deliberately, and with conscious effort—it multiplies 17 × 24, fills out a tax form, and evaluates whether an argument is logically valid.

The division of labor between these systems is efficient: System 1 handles most cognitive work while System 2 monitors at low intensity, intervening only when something triggers closer inspection. Cognitive biases arise at the seam between these two systems. When System 1 encounters a hard question, it substitutes an easier one and answers that instead—a process Kahneman and Frederick (2002) called **attribute substitution**. System 2, if it notices at all, often accepts the substituted answer without checking whether the right question was actually addressed. Most of the biases in this pack can be understood as specific instances of this substitution going undetected.

### Heuristics and Biases

In their landmark 1974 *Science* paper, Amos Tversky and Daniel Kahneman identified three heuristics that people rely on when judging probability under uncertainty. A heuristic is a cognitive shortcut—a rule of thumb that produces reasonable answers quickly but at the cost of systematic errors in specific circumstances. The errors are not random; they are predictable, which is what makes the research useful.

| Heuristic | How It Works | Classic Experiment | Where It Fails |
|---|---|---|---|
| **Representativeness** | Probability judged by resemblance to a typical case | "Steve" is shy/orderly—most say librarian, ignoring that farmers vastly outnumber librarians | Base rate neglect, conjunction fallacy, gambler's fallacy |
| **Availability** | Frequency judged by ease of recall | More English words starting with "r" or with "r" third? Most say the former—words indexed by first letter | Overweighting vivid, recent, or emotionally salient events |
| **Anchoring & Adjustment** | Estimates start from an initial value with insufficient adjustment | Rigged wheel of fortune affects estimates of African UN nations | Susceptibility to arbitrary starting points in negotiations, pricing, sentencing |

> **KEY: Heuristics are not stupidity.** The heuristics are genuinely useful. In most situations, what comes easily to mind *is* more common, things that look like typical cases *are* more probable, and initial estimates *are* reasonable starting points. The errors appear at the boundaries. An AI advisor needs to know not just that these heuristics exist but when the conditions for failure are present.

### Prospect Theory

Kahneman and Tversky's Prospect Theory (1979, *Econometrica*) provides the decision-theoretic foundation:

- **Reference dependence.** People evaluate outcomes as gains or losses relative to a reference point rather than as absolute states.
- **Loss aversion.** Losses hurt more than equivalent gains please—approximately 2:1, replicated across 19 countries (Ruggeri et al., 2020, *Nature Human Behaviour*).
- **Diminishing sensitivity.** The difference between $100 and $200 feels larger than between $1,100 and $1,200.
- **Probability weighting.** People overweight small probabilities and underweight moderate-to-large ones.

Prospect Theory earned Kahneman the 2002 Nobel Prize in Economics and is the theoretical backbone of framing effects, the sunk cost fallacy, and much of the bias literature.

> **NOTE: The ecological rationality counter-argument.** Gerd Gigerenzer argues that many so-called biases are adaptive heuristics that perform well in natural environments. This pack follows the Kahneman-Tversky framework because it is directly applicable to error detection, but the critique is worth remembering: not every deviation from a formal norm is necessarily irrational.

---

## Section 2 · Six Biases That Matter

### Confirmation Bias

The tendency to search for, interpret, favor, and recall information that confirms existing beliefs. Peter Wason's 2-4-6 task (1960) provided the first demonstration: participants told "2, 4, 6" follows a hidden rule overwhelmingly tested confirming sequences and almost never tested disconfirming ones. The rule was simply "any ascending sequence." Nickerson's 1998 review called it "perhaps the best known and most widely accepted notion of inferential error."

Operates at three levels (Nickerson, 1998): **biased search**, **biased interpretation**, and **biased recall**. Mechanisms are both cognitive ("cold"—limited processing drives positive-test strategies) and motivational ("hot"—desire to be right). Consequences: medical misdiagnosis, legal bias, scientific publication bias, social media filter bubbles.

### Base Rate Neglect

A downstream failure of representativeness. When given specific information about a case, people ignore prior probabilities. In Kahneman and Tversky's 1973 engineer/lawyer experiment, personality descriptions dominated judgment regardless of whether the pool was 70% or 30% engineers.

Life-or-death in medical screening: a test with 95% sensitivity and 95% specificity applied to a 1%-prevalence condition yields only ~16% positive predictive value. Most people, including many clinicians, dramatically overestimate disease probability given a positive test.

### Sunk Cost Fallacy

Continuing because of past investment rather than future value. Thaler (1980) formalized it; Arkes and Blumer (1985) demonstrated it experimentally. Primary mechanism: loss aversion from Prospect Theory—abandoning means accepting certain loss; continuing maintains possibility of recovery. Additional drivers: self-justification and waste aversion. Canonical example: the Concorde, funded for 27 years despite known unprofitability. Sydney Opera House: $7M budget → $102M actual, decade late.

### Framing Effects

Identical information presented differently produces different choices. Tversky and Kahneman's Asian Disease Problem (1981): "saves 200 of 600" → 72% prefer it; "400 of 600 will die" → only 22% prefer it. Same outcome, reversed majority preference.

Three types: **valence framing** (positive vs. negative), **attribute framing** ("95% lean" vs. "5% fat"), **goal framing** (gains of acting vs. losses of not acting). All exploit Prospect Theory's reference dependence.

### The Planning Fallacy

Systematic underestimation of time, costs, and risks. Coined by Kahneman and Tversky (1979); expanded by Lovallo and Kahneman (2003). Buehler et al. (1994): students predicted 33.9 days for thesis; actual average 55.5 days; only 30% on time; even worst-case estimates (48.6 days) were optimistic.

Mechanism: **inside view** (focus on unique features, best-case scenario) vs. **outside view** (treat as instance of reference class). People spontaneously adopt the inside view. The outside view must be deliberately imposed. Robust across cultures, personality types, individual and group tasks. Defining paradox: people acknowledge past over-optimism while insisting current predictions are realistic.

### Hindsight Bias

Believing after learning an outcome that it was more predictable than it was. Fischhoff (1975); Fischhoff and Beyth (1975) on Nixon's visits. Three components (Roese & Vohs, 2012): memory distortion, inevitability impression, foreseeability impression. Mechanism: "creeping determinism"—once known, the causal chain seems inevitable. Corrupts legal judgments, organizational learning, and perceived value of forecasting.

| Bias | Core Error | Key Study | Mechanism |
|---|---|---|---|
| Confirmation bias | Seeking evidence that supports existing beliefs | Wason, 1960 | Positive test strategy + motivated reasoning |
| Base rate neglect | Ignoring prior probability given specific evidence | Kahneman & Tversky, 1973 | Representativeness heuristic dominates |
| Sunk cost fallacy | Continuing due to past investment, not future value | Arkes & Blumer, 1985 | Loss aversion + self-justification |
| Framing effects | Different choices from identical information | Tversky & Kahneman, 1981 | Reference dependence (Prospect Theory) |
| Planning fallacy | Underestimating time, cost, and risk | Buehler, Griffin, & Ross, 1994 | Inside view dominates outside view |
| Hindsight bias | "I knew it all along" after the outcome | Fischhoff, 1975 | Creeping determinism |

---

## Section 3 · Miscalibrated Confidence

### The Dunning-Kruger Effect

Kruger and Dunning (1999): bottom-quartile performers estimated performance at ~62nd percentile. "Double burden" hypothesis: the skills needed to perform well are the same skills needed to recognize good performance.

> **WARN: The popular version is wrong.** "Stupid people think they're geniuses" is a caricature. The phenomenon exists as a statistical pattern, but the mechanism is contested. Regression to the mean can produce similar graphs (Krueger & Mueller, 2002). McIntosh et al. (2019) found metacognitive differences weak as mediators. A rational Bayesian model produces the pattern with optimistic priors and noisy feedback, no metacognitive deficit required. The "incompetent lack metacognitive ability" claim is one hypothesis among several, and arguably the weakest.

### Overconfidence Beyond Dunning-Kruger

People are generally overconfident: at 90% confidence, accuracy is typically 70–80%. Appears in experts as well as novices. Exception: fields with rapid, unambiguous feedback (weather forecasting). This is not because meteorologists are more rational—it's because their domain forces calibration through daily, visible outcomes.

---

## Section 4 · Metacognition — Thinking About Thinking

### What It Is

Formalized by Flavell (1979). Two components: **metacognitive monitoring** ("Am I solving the right problem?") and **metacognitive control** ("I should slow down and check this"). Metacognition is the mechanism by which System 2 overrides System 1.

> **KEY: Intelligence ≠ Rationality.** Stanovich (*What Intelligence Tests Miss*, 2009) distinguished the **algorithmic mind** (IQ) from the **reflective mind** (disposition to question intuitive outputs). He coined **"dysrationalia"**—smart people reasoning poorly. IQ protects against almost nothing in the bias literature. What protects is the reflective mind's willingness to treat its own outputs as hypotheses, not conclusions.

### Calibration as a Trainable Skill

Calibration: alignment between confidence and accuracy. Measured by **Brier score** (mean squared error of probability assignments vs. outcomes; lower = better; 0 = perfect).

Tetlock's Good Judgment Project (2011–2015): 20,000+ volunteers, ~260 **superforecasters** achieved 50–60% better Brier scores than average, outperforming intelligence analysts with classified access. Distinguishing factor: not intelligence or expertise, but *how they thought*—open-minded, granular, relentless updaters, committed to postmortem analysis.

### Principles from Superforecasting

- **Foxes beat hedgehogs.** Many frameworks > one big idea. Hedgehog confidence inversely correlated with accuracy.
- **Granularity matters.** "Vague verbiage slows learning cycles" (Tetlock). 73% enables feedback; "likely" does not.
- **Start outside, then inside.** Begin with base rate from reference class, then adjust for case-specific information.
- **Update often and honestly.** Treat beliefs as provisional, not positional.
- **Conduct postmortems.** The most common failure: learning too little from mistakes.

### Meta-Ignorance

Dunning (*Self-Insight*, 2005): **meta-ignorance**—not knowing that you don't know. People most in need of metacognitive correction are least likely to seek it. Implication: self-directed debiasing is structurally unreliable. Structural interventions (checklists, external review, scoring, multi-pass processes) outperform appeals to "think harder."

---

## Section 5 · Debiasing — What Works and What Doesn't

> **KEY: The central finding.** Knowing about a bias does not make you resistant to it. Fischhoff (1977) gave participants detailed hindsight-bias instructions. Negligible effect. Tetlock's analogy: the Müller-Lyer illusion persists even when you know the lines are equal. Effective debiasing is structural—it changes the process, not just awareness.

### What Works

| Strategy | Targets | Evidence | Limits |
|---|---|---|---|
| **Consider-the-opposite** | Confirmation bias, overconfidence, anchoring, hindsight | Koriat et al. (1980); Slovic & Fischhoff (1977) | Can backfire if generating alternatives feels difficult (Sanna et al., 2002) |
| **Pre-mortem** | Planning fallacy, groupthink, overconfidence | Klein (2007): imagine project has failed, explain why | Requires psychological safety |
| **Reference class forecasting** | Planning fallacy, inside-view bias | Kahneman & Lovallo (2003); Flyvbjerg UK infrastructure | Choosing the correct reference class is itself bias-prone |
| **Keeping score** | All calibration errors | Tetlock (2015): Brier scoring + feedback → 50–60% improvement | Many judgments lack clear outcome data |
| **Training + teams + feedback** | Multiple biases | Mellers et al. (2014): ~1hr training → ~10% improvement; combined → 50–60% | Effects decay without practice |

### What Doesn't Work

**Awareness alone** is insufficient. **Expertise alone** does not protect (Tetlock 2005: expert forecasters barely beat chance; hedgehogs worse). **Incentives alone** are insufficient (hindsight bias persists under accuracy motivation).

> **TIP: The operational principle.** If you want to reduce bias, change the structure of the decision-making process. Don't tell people to be less biased—give them a checklist, a required devil's-advocate step, a scoring system, a pre-mortem, or a multi-pass review.

---

## Section 6 · AI-Specific Failure Modes

### Confabulation

LLMs produce plausible-sounding but factually wrong content with no reliable internal uncertainty signal. Smith et al. (2023) argued **"confabulation"** is the better term—the model fills gaps without recognizing fabrication. Root cause: next-token prediction training doesn't distinguish fluent-true from fluent-false. Farquhar et al. (2024, *Nature*): semantic entropy can detect confabulations externally, but this isn't self-monitoring.

### Sycophancy

RLHF-trained models agree with users rather than correct them (~58% sycophancy rate; Fanous et al.). High user confidence reduces debunking by up to 15%. OpenAI rolled back a GPT-4o update (April 2025) for excessive sycophancy. The AI analogue of confirmation bias—same output (reinforcing existing frame), different mechanism (training incentives vs. cognitive/motivational factors).

### Anchoring on User Framing

Models adopt the user's frame including false premises. Adversarial prompts with fabricated details: 50–82% elaboration rates. No independent reference point from which to detect the anchor.

### Pattern Matching Without Understanding

Statistical co-occurrence ≠ causal reasoning. "Reverse curse" sensitivity: trained on "A implies B," fails on "B implies A." High token probability ≠ factual correctness. No clean human analogue.

### Absent Metacognitive Self-Monitoring

Humans can recognize uncertainty ("I think it was 1889, but I'm not sure"). LLMs cannot—high probability tokens result from memorization, pattern, or correctness indistinguishably. External compensations (retrieval augmentation, ensemble methods, human review) partially help but no current architecture provides genuine metacognitive self-correction.

> **TIP: The structural parallel.** The debiasing finding—change the process, not the awareness—maps to AI systems. Multi-pass production, external verification, and human-in-the-loop review are the AI equivalents of consider-the-opposite and pre-mortems.

---

## Section 7 · Board Connection

### How Should an AI Advisor Monitor Its Own Output for Bias?

Structurally. "Watch for bias" is the awareness-only strategy that doesn't work. What works: multi-pass production (the ten-step Knowledge Pack method), consider-the-opposite as a required review step, external verification through the operator as human-in-the-loop. Fix by Design applied to cognitive bias: design the process so bias must survive multiple independent checks.

### What Does Calibrated Confidence Look Like?

Granularity enables feedback; feedback enables calibration. Use explicit uncertainty markers (high/moderate/speculative). Refuse false precision. Distinguish "strong evidence" from "statistically plausible." The operator tracks calibration claims against outcomes—Brier scoring for advisory output. Without outcome tracking, calibration claims are unfalsifiable.

### When the Operator's Frame Contains Embedded Biases

The No Directives Rule applies. But honest advice requires surfacing unstated assumptions. Template: "This question presupposes X. If X is accurate, then [answer]. If X is not accurate—here are reasons to question it—then the question changes." Sycophancy resistance as procedure. The advisory board structure provides multiple perspectives reducing the probability any single biased frame goes unchallenged.

### Cross-Pack Connections

**Epistemology (Pack 3):** Confirmation bias corrupts evidence-gathering. Base rate neglect is a failure of Bayesian belief updating. Underdetermination + confirmation bias → unwarranted certainty.

**Decision Theory (Pack 5):** Framing effects violate invariance. Sunk cost violates forward-looking rationality. Planning fallacy corrupts expected value inputs. Prospect Theory bridges both packs directly.

**Practical intersection:** Any project estimation (e.g., Butcher Constellation timeline) is simultaneously epistemological (what evidence on similar projects?), decision-theoretic (resource allocation under uncertainty?), and bias-related (anchored on original estimate? planning fallacy? confirming evidence of being on track?). The three packs address all three layers.

---

## References

- Arkes, H. R. & Blumer, C. (1985). The Psychology of Sunk Cost. *OBHDP*, 35, 124–140.
- Buehler, R., Griffin, D. & Ross, M. (1994). Exploring the "Planning Fallacy." *JPSP*, 67(3), 366–381.
- Dunning, D. (2005). *Self-Insight*. Psychology Press.
- Farquhar, S. et al. (2024). Detecting Hallucinations Using Semantic Entropy. *Nature*, 630, 625–630.
- Fischhoff, B. (1975). Hindsight ≠ Foresight. *JEPHPP*, 1, 288–299.
- Fischhoff, B. (1982). Debiasing. In Kahneman, Slovic & Tversky (Eds.), *Judgment Under Uncertainty* (pp. 422–444). CUP.
- Fischhoff, B. & Beyth, R. (1975). "I Knew It Would Happen." *OBHP*, 13, 1–16.
- Flavell, J. H. (1979). Metacognition and Cognitive Monitoring. *American Psychologist*, 34(10), 906–911.
- Kahneman, D. (2011). *Thinking, Fast and Slow*. FSG.
- Kahneman, D. & Frederick, S. (2002). Representativeness Revisited. In Gilovich et al. (Eds.), *Heuristics and Biases* (pp. 49–81). CUP.
- Kahneman, D. & Tversky, A. (1973). On the Psychology of Prediction. *Psychological Review*, 80, 237–251.
- Kahneman, D. & Tversky, A. (1979). Prospect Theory. *Econometrica*, 47, 263–291.
- Klein, G. (2007). Performing a Project Premortem. *HBR*, 85(9), 18–19.
- Koriat, A., Lichtenstein, S. & Fischhoff, B. (1980). Reasons for Confidence. *JEPHLM*, 6(2), 107–118.
- Krueger, J. & Mueller, R. A. (2002). Unskilled, Unaware, or Both? *JPSP*, 82(2), 180–188.
- Kruger, J. & Dunning, D. (1999). Unskilled and Unaware of It. *JPSP*, 77(6), 1121–1134.
- Lovallo, D. & Kahneman, D. (2003). Delusions of Success. *HBR*, 81(7), 56–63.
- McIntosh, R. D. et al. (2019). Wise Up. *JEP: General*, 148(11), 1882–1897.
- Mellers, B. et al. (2014). Psychological Strategies for Winning a Forecasting Tournament. *Psychological Science*, 25(5), 1106–1115.
- Nickerson, R. S. (1998). Confirmation Bias: A Ubiquitous Phenomenon. *Review of General Psychology*, 2(2), 175–220.
- Roese, N. J. & Vohs, K. D. (2012). Hindsight Bias. *PPS*, 7(5), 411–426.
- Ruggeri, K. et al. (2020). Replicating Prospect Theory. *Nature Human Behaviour*, 4, 622–633.
- Smith, M. et al. (2023). Hallucination or Confabulation? *Postgraduate Medical Journal*.
- Stanovich, K. E. (2009). *What Intelligence Tests Miss*. Yale UP.
- Tetlock, P. E. (2005). *Expert Political Judgment*. Princeton UP.
- Tetlock, P. E. & Gardner, D. (2015). *Superforecasting*. Crown.
- Thaler, R. (1980). Toward a Positive Theory of Consumer Choice. *JEBO*, 1(1), 39–60.
- Tversky, A. & Kahneman, D. (1974). Judgment Under Uncertainty. *Science*, 185(4157), 1124–1131.
- Tversky, A. & Kahneman, D. (1981). The Framing of Decisions. *Science*, 211(4481), 453–458.
- Wason, P. C. (1960). On the Failure to Eliminate Hypotheses. *QJEP*, 12(3), 129–140.

---

*Loop MMT™ · Multi-Module Theory · Cognitive Bias & Metacognition Knowledge Pack · v1 © 2026 Shea Gunther · CC BY-NC 4.0*
