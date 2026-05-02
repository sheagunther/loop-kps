# Knowledge Pack Production Method v3
## Loop MMT™ · 13 April 2026

---

## About This Document

This is the explicit specification of the method used to produce Knowledge Packs within the Loop MMT corpus. The method was used implicitly across Knowledge Pack Cascade Sessions 1–3 and was codified as a numbered sequence in Session 4 after an instance that lacked the method produced four packs using only two of the ten steps. This document exists so that every future instance has the complete method before production begins.

The method produces approximately eight to nine intermediate documents per pack. One pack per session is the expected pace when the method is followed correctly. The method is non-negotiable — skipping steps produces output that looks correct but has not been verified.

**Provenance:** Codified Session 4 (April 2026) after the surface-quality failure. v2 revised via Lathe Cycle 1, Phase B — added Trigger, FBD Controls, Sequence Position, Four Corners, Pulse Line. Pinned cross-reference versions. Converted from L21 HTML to markdown project format. v3 integrates Source Verification Amendment (Session 55): verification gate added to Step 6.

**FBD Classification:** FBD-KP series (Knowledge Pack Production).

---

## 1. Trigger

**Mandatory** when the board or operator requests production of a new Knowledge Pack. The method applies to every KP — no abbreviated runs.

**Does not apply to:** KP revision (governed by The Kiln v1), KP-format documents that are not reference packs (e.g., the Mirror Pack, which follows KP format but is a methodology document), or casual research queries that don't produce a corpus artifact.

---

## 2. Overview

A Knowledge Pack is a reference document designed to be loaded into AI advisory conversations. It provides comprehensive, concise coverage of a domain — definitions, key concepts, major theorems or principles, historical context, and explicit connections to Loop MMT's structures. Packs are written for AI advisors but should be readable and useful to humans.

The production method exists because the difference between a first-draft pack and a properly verified pack is invisible at the surface. Both look like finished documents. Both contain real research. The difference is in what the verification steps catch: factual errors, structural gaps, missing connections, claims that sound right but aren't, citations that don't check out. A pack that skips verification may be fine. It may also contain errors that propagate into every conversation that loads it. The method is the insurance against that.

> **The core principle:** The code is not the product. The methodology that produced the code is the product. This applies to Knowledge Packs exactly as it applies to software. A pack produced by research-then-write is a different artifact than a pack produced by the ten-step method, even if the content appears identical. The process that produced it determines its reliability.

---

## 3. The Ten Steps

| Step | Name | Input | Output | Purpose |
|------|------|-------|--------|---------|
| 1 | **Research** | Topic scope from board request | Raw research findings | Gather information from trusted, reputable sources |
| 2 | **Compilation** | Raw research | Structured reference document with citations | Organize findings into a usable working document |
| 3 | **Plan** | Compiled research | Writing plan for the pack | Decide structure, section order, scope, depth |
| 4 | **Self-Review Plan** | Writing plan | Revised plan | Catch gaps, ordering problems, scope issues before drafting |
| 5 | **First Draft** | Revised plan + compiled research | Draft 1 (L21 HTML) | Write the pack |
| 6 | **Fact-Check** | Draft 1 | Fact-check report | Verify claims, dates, attributions, definitions |
| 7 | **Second Draft** | Draft 1 + fact-check report | Draft 2 (L21 HTML) | Complete rewrite incorporating corrections |
| 8 | **Comparison Analysis** | Draft 1 + Draft 2 | Analysis report | Document what changed between drafts and why |
| 9 | **Self-Review** | Draft 2 | Final version (L21 HTML) | Comprehensive review; produce the finished pack |
| 10 | **Package** | Final version + all intermediates | Final file + process archive (zip) | Deliver the pack and its full production trail |

---

## 4. Step Detail

### Step 1 — Research

Search across multiple trusted, reputable sources. Use web search to find primary academic sources, authoritative encyclopedias, original papers, and well-regarded textbooks. Do not rely on a single source. The goal is breadth: find the major concepts, the key thinkers, the foundational results, the open questions, and the historical development of the domain.

Research should include enough source material that the subsequent compilation step has real work to do. If research produces only a thin sketch, the rest of the pipeline has nothing to verify against. Five or more distinct searches across different aspects of the topic is a reasonable minimum. Use `web_fetch` for primary sources — original papers, key encyclopedia entries, authoritative overviews — where full-page depth matters. Use `web_search` snippets for breadth coverage and to identify which sources are worth fetching in full. Manage context budget actively: full-page fetches consume significantly more context than search snippets.

### Step 2 — Compilation

Organize the raw research into a structured reference document. Group findings by subtopic. Include citations for every claim — author, title, publication, year. Flag areas where sources disagree. Identify gaps where more research may be needed. This document is the working foundation for everything that follows. If a fact isn't in the compilation, it shouldn't appear in the pack without explanation.

### Step 3 — Plan

Draft a writing plan for the Knowledge Pack. This includes: proposed section structure, the order of topics, what each section will cover, what depth is appropriate for each area, which concepts need callouts or reference tables, explicit planning for the Board Connection section (which domain concepts map to which Loop MMT structures, and why), what the abstract will say, and what the references section will need to cover. The plan is a blueprint, not an outline — it should contain enough detail that someone else could write the pack from it.

### Step 4 — Self-Review Plan

Review the plan for gaps, ordering problems, scope creep, missing topics, and structural issues. Check the plan against the compiled research — is every major finding represented? Is anything in the plan that isn't supported by the research? Revise the plan based on the review. The revised plan is the input to the first draft.

### Step 5 — First Draft

Write the Knowledge Pack in L21 HTML format from the revised plan and compiled research. This is the first full document: complete with all sections, TOC sidebar, three-skin CSS, callout system, reference tables, Board Connection section, citations, and references. It should be a complete, deliverable document — not a rough draft. The distinction between Draft 1 and the final version is not completeness but verification.

**Prerequisite:** The instance must have an L21 template pack loaded (any existing Knowledge Pack) or the L21 Technical Reference v1 available before beginning the draft. L21 format requires: sticky header with skin switcher, TOC sidebar with scroll-tracking, three-skin CSS (OG, Winamp, Sunrise), abstract box, chapter/section hierarchy, callout system (tip, warn, key, note), ref-tables, monospace font system via CSS variables, and a footer with copyright.

### Step 6 — Fact-Check

Design a fact-check approach first — think through how the process should work before executing it. The approach should be smart and designed to catch all errors, not a mechanical line-by-line read. Strategies include: verifying dates and attributions against original sources, checking that definitions match accepted usage, confirming that theorem statements are correctly stated, testing that historical claims are accurate, and cross-referencing claims between sections for internal consistency.

**Critical:** The fact-check is not proofreading. It is a verification of the truth-value of every substantive claim in the document. An error in a Knowledge Pack propagates into every conversation that loads it. The fact-check is the primary defense against that.

**Source verification gate (FBD-SV1/SV2):** When the Knowledge Pack makes claims about external verifiable sources (code sections, regulations, technical specifications, academic citations), the fact-check pass must use `web_search` and `web_fetch` to retrieve the actual source text and confirm claims against it. Verified claims are tagged with `.src` class references in the document. Unverified claims are tagged `.src-none`. A Verification Ledger chapter is added per FBD-SV2. This is not optional enrichment — it is a gate. The fact-check is not complete until every verifiable claim is either confirmed or explicitly marked unverified.

### Step 7 — Second Draft

Write a **completely new draft** of the Knowledge Pack. This is not an edit of Draft 1. It is a new document written from scratch using the fact-check report and Draft 1 as inputs. The purpose of a full rewrite is to force re-engagement with the material. Editing polishes the surface. Rewriting reconstructs the understanding. Structural problems that survive editing often do not survive rewriting because the writer must rebuild the logic from the ground up.

> **Why rewrite instead of edit:** Editing preserves the frame of the first draft. If the first draft organized material in a way that obscures a connection or buries an important concept, editing will preserve that structure. Rewriting allows the second draft to find a better structure — one informed by everything the fact-check revealed. The two drafts are independent samples of how to present the same material. Their differences are information.

**Variant — Prior Draft Comparison:** When a draft-quality version of the same topic exists from a prior session (e.g., the Session 4 speed-run drafts), it can be included as additional comparison material at Step 8. The primary comparison remains Draft 1 vs. Draft 2 from the current production run; the prior draft provides a third data point showing what the full method changed relative to the fast method.

### Step 8 — Comparison Analysis

Compare Draft 1 and Draft 2 systematically. The analysis report should include: a summary of structural changes (sections added, removed, reorganized), a list of factual corrections made, an assessment of whether the rewrite improved clarity and accuracy or introduced new issues, and a count of substantive vs. cosmetic changes. This report serves two purposes: it verifies that the fact-check findings were actually incorporated, and it creates a record of what the process discovered. If the two drafts are nearly identical, either the fact-check found nothing (unlikely) or the rewrite didn't engage deeply enough.

### Step 9 — Self-Review

Comprehensive review of Draft 2. Check for: factual accuracy, internal consistency, completeness against the compiled research, quality of the Board Connection section, correctness of citations, clarity of exposition, appropriate use of callouts and reference tables, and adherence to L21 format standards. Produce the final version incorporating all corrections.

### Step 10 — Package

Deliver the final version of the Knowledge Pack for download. Also deliver a zip archive containing every document created during the process — from the Step 1 research findings through to the final version. The zip should include a copy of the final version so the archive is self-contained. The operator receives two copies of the final file: one standalone, one in the archive.

---

## 5. Artifact Inventory

A complete run of the method produces the following documents:

| # | Document | From Step | Format |
|---|----------|-----------|--------|
| 1 | Research findings | Step 1 | Text/markdown |
| 2 | Research compilation | Step 2 | Text/markdown |
| 3 | Writing plan | Step 3 | Text/markdown |
| 4 | Revised plan | Step 4 | Text/markdown |
| 5 | Draft 1 | Step 5 | L21 HTML |
| 6 | Fact-check report | Step 6 | Text/markdown |
| 7 | Draft 2 | Step 7 | L21 HTML |
| 8 | Comparison analysis | Step 8 | Text/markdown |
| 9 | Final version | Step 9 | L21 HTML |

Nine documents per pack. The zip archive at Step 10 contains all nine. Total deliverables per pack: one standalone final HTML file plus one zip containing nine files. Nine is the standard count for a clean run — additional research passes, supplementary fact-check searches, or iterative plan revisions may increase it.

---

## 6. Constraints & Traps

**Context Window Pressure.** Nine documents plus the research material plus the conversation itself will press against context limits. The expected pace is one pack per session for this reason. Do not attempt to produce multiple packs using the full method in a single session — the quality of the later steps degrades as context fills.

**The Surface-Quality Trap.** A pack produced by skipping steps 2–4 and 6–9 looks like a finished document. It has sections, citations, callouts, reference tables. The problem is invisible. The pack may be correct, or it may contain errors that the skipped steps would have caught. This is the most dangerous failure mode because it produces no signal. The operator discovered this in Session 4 — four packs were produced at speed, all looked correct, and the process gap was only visible when compared against the method specification. The method exists to prevent this.

**Editing vs. Rewriting.** Step 7 requires a complete rewrite, not an edit. The temptation to open Draft 1, fix the fact-check findings, and call it Draft 2 is strong — it's faster and feels sufficient. It is not sufficient. Editing preserves the first draft's frame, including its structural weaknesses. Rewriting forces reconstruction of the logic from the compiled research and fact-check findings. The comparison at Step 8 only has value if the two drafts are genuinely independent.

**Citation Discipline.** Every substantive claim in a Knowledge Pack must be traceable to a source. Claims that "sound right" but have no citation are the primary vector for factual errors. If a claim can't be cited, it should be flagged as the author's interpretation and marked accordingly. The References section of the final pack should contain only sources that were actually consulted — no padding, no aspirational citations.

---

## 7. FBD Controls

| ID | Name | Rule |
|----|------|------|
| FBD-KP1 | Full method mandatory | All ten steps execute for every KP. No abbreviated runs. Steps 2–4 and 6–9 are where verification happens — skipping them produces unverified output indistinguishable from verified output. |
| FBD-KP2 | Rewrite, not edit | Step 7 is a complete rewrite from scratch. Editing Draft 1 preserves structural weaknesses the fact-check was designed to expose. |
| FBD-KP3 | Citation traceability | Every substantive claim must be traceable to a source. Uncitable claims flagged as author interpretation. No aspirational citations. |
| FBD-KP4 | One pack per session | Context window pressure degrades later steps. Multi-pack sessions produce unverified output at steps 6+. |
| FBD-KP5 | Draft independence | Draft 1 and Draft 2 must be independently written. Comparison Analysis (Step 8) has no value if Draft 2 is a derivative edit of Draft 1. |

---

## 8. Sequence Position

**What comes before:** Board or operator requests a KP topic. The instance loads this method specification and the L21 Technical Reference v1 before beginning.

**What the KP Production Method does:** Produces a verified, citable Knowledge Pack through a ten-step pipeline of research, drafting, verification, rewriting, and comparison.

**What comes after:** The finished KP enters the corpus. Future revisions are governed by The Kiln v1. The KP is loaded into advisory conversations as reference material.

**Relationship to other protocols:**
- **Self-Review Protocol v8:** Step 9 is a self-review. The KP Production Method's self-review predates the formal Self-Review Protocol and uses a domain-specific review (factual accuracy, citation correctness, Board Connection quality) rather than the generic four-file cycle.
- **The Kiln v1:** Governs KP revision. The Production Method governs KP creation. Different lifecycle stages.
- **L21 Technical Reference v1:** Defines the format specification for KP HTML output (Steps 5, 7, 9).
- **Writing Standards v5:** Governs prose quality. The Four Corners check applies at Step 9.

---

## 9. Four Corners

- **FBD:** Five controls (FBD-KP1 through KP5). FBD-KP1 (full method mandatory) and FBD-KP2 (rewrite not edit) are load-bearing — they prevent the two dominant failure modes: step-skipping and frame-preservation.

- **FWW(C):** The comparison analysis (Step 8) is the hidden engagement mechanism — watching what the rewrite discovered that the first draft missed is genuinely interesting. The ten-step structure itself has a rhythm: research → organize → plan → check → write → verify → rewrite → compare → review → package. Chaos lives in Step 6 (fact-check) — you don't know what it will find.

- **STP:** The artifact inventory (Section 5) is the trust mechanism. Nine documents, all retained, all delivered. The operator can trace any claim from the final pack back through the drafts to the compiled research to the original sources. Full provenance chain.

- **SNR:** The method specification is longer than most protocols because it carries step-level detail that instances need to execute correctly. The Constraints & Traps section (Section 6) could be folded into step detail but stays separate because the traps are cross-cutting — they apply to the method as a whole, not to individual steps.

---

## 10. Pulse Line Specification

**Measures:** Steps completed, artifact count, fact-check finding count, Draft 1 vs Draft 2 substantive change count.

**Format:**
```
[PULSE] KP Production: [Topic]. Steps [N]/10 complete. [N] artifacts produced. Fact-check: [N] findings. Comparison: [N] substantive, [N] cosmetic changes.
```

**Example:**
```
[PULSE] KP Production: Game Theory. Steps 10/10 complete. 9 artifacts produced. Fact-check: 7 findings. Comparison: 12 substantive, 4 cosmetic changes.
```

---

## 11. History

| Version | Date | Session | Change |
|---------|------|---------|--------|
| v1 | 8 April 2026 | S37 | Codified from implicit practice after Session 4 surface-quality failure. Ten-step pipeline, artifact inventory, constraints. |
| v2 | 12 April 2026 | S51 | Lathe Cycle 1 revision. Added Trigger, FBD Controls (FBD-KP1–KP5), Sequence Position, Four Corners, Pulse Line. Pinned cross-references (L21 Technical Reference v1, Self-Review Protocol v8, The Kiln v1, Writing Standards v5). Converted from L21 HTML to markdown. |
| v3 | 13 April 2026 | S55-amd | Source Verification Amendment integrated. Added verification gate language to Step 6 (FBD-SV1/SV2). Fact-check pass now requires source retrieval and explicit verified/unverified tagging for external claims. |

---

*Loop MMT™ · Knowledge Pack Production Method · v3 · © 2026 Shea Gunther · CC BY-NC 4.0*
