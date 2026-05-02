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
Version Control & Three-Way Merge Algorithms Knowledge Pack
:::

::: build-tag
v1 · 9 April 2026
:::
:::
:::
:::

::: body-wrap
::: toc-title
Contents
:::

-   [About This Document](#ch-abstract)
-   [1 · History](#ch-history)
-   [2 · The Diff Problem](#ch-diff)
-   [3 · Two-Way vs Three-Way](#ch-two-vs-three)
-   [4 · Three-Way Merge](#ch-threeway)
-   [5 · Common Ancestor](#ch-ancestor)
-   [6 · Conflicts](#ch-conflict)
-   [7 · Git's Merge Machinery](#ch-git)
-   [8 · Structured Merge](#ch-structured)
-   [9 · Alternative Paradigms](#ch-alternatives)
-   [10 · Board Connection](#ch-board)
-   [References](#ch-refs)

::: {.content role="main"}
::: {#ch-abstract .abstract-box}
::: abstract-label
About This Document
:::

A reference on version control merging algorithms, centered on the three-way merge — the dominant method for reconciling divergent changes to shared artifacts. Covers two-way diff (the essential subroutine), the formal three-way merge algorithm and its decision table, common ancestor computation, conflict detection and resolution, Git's merge implementation, structured merge on trees and databases, and alternative paradigms including CRDTs, operational transformation, and patch theory.

Built for AI advisors helping human operators with problems involving concurrent modification — source code, structured documents, or protocol state. Draws on 12 sources: foundational algorithms (Myers 1986), formal analysis (Khanna, Kunal, Pierce 2007), and production systems (Git, Dolt, Automerge).
:::

::: {#ch-history .chapter}
::: chapter-number
Section 1
:::

::: chapter-title
History of Version Control
:::

Version control history is a progression from locking to merging. Each generation's collaboration model determined what merge algorithms it needed — or whether it needed them at all.

::: section
::: section-title
First Generation: Local, Single-File (1972–1986)
:::

**SCCS (Source Code Control System)** — Marc Rochkind, Bell Labs, 1972. The first deliberate version control system. Originally written in SNOBOL4 for IBM System/370, rewritten in C for Unix in 1973, publicly released in 1977. Operated on individual files with exclusive locking (one writer at a time). Stored versions using **interleaved deltas** — all versions woven into a single file, giving uniform retrieval time for any revision.

**RCS (Revision Control System)** — Walter F. Tichy, Purdue University, 1982. Key innovation: **reverse deltas**. Stores the most recent version in full; older versions are reconstructed by applying backward diffs. Fast checkout for current revisions, slower for old ones. Still single-file with locking. Introduced the terminology (checkout, checkin, commit, log) and the `,v` file format that CVS and Perforce would later reuse.
:::

::: section
::: section-title
Second Generation: Centralized, Network (1986–2005)
:::

**CVS (Concurrent Versions System)** — Dick Grune, 1984–86 (initial shell scripts 1984–85, full tool by 1986). The system that shifted version control from locking to merging. Built as a frontend to RCS, CVS added: project-level operations across multiple files, client-server networking, and **concurrent editing with merge-on-update**. Multiple developers could modify the same file; conflicts were detected at update time using `rcsmerge`, a three-way merge tool. Non-atomic commits remained a significant limitation.

**Subversion (SVN)** — CollabNet, 2000. Fixed CVS's worst problems: atomic commits, directory versioning, efficient binary handling. Still centralized.
:::

::: section
::: section-title
Third Generation: Distributed (2005–present)
:::

The Linux kernel had used **BitKeeper**, a commercial distributed VCS, since 2002. When BitMover revoked free access in April 2005, Linus Torvalds wrote **Git** in weeks — a fully distributed system where every clone holds the complete history. Content-addressable storage via SHA-1 hashing, snapshot-based versioning, and three-way merge as the default strategy. **Mercurial**, started independently the same month by Matt Mackall, used a similar distributed model with a revlog storage format.

The distributed model made merging central to every workflow. In centralized systems, merging was occasional. In Git, every pull is potentially a merge. Three-way merge went from useful tool to critical infrastructure.
:::

::: {.callout .note}
::: callout-label
Note
:::

Locking (SCCS/RCS) required no merge algorithm — conflicts were prevented by serialization. Concurrent centralized editing (CVS/SVN) required merge at update time. Distributed systems (Git) require merge at every synchronization point. The merge problem scaled with the collaboration model.
:::
:::

::: {#ch-diff .chapter}
::: chapter-number
Section 2
:::

::: chapter-title
The Diff Problem
:::

Three-way merge calls two-way diff as a subroutine. The quality and behavior of the diff algorithm directly affects merge results.

::: section
::: section-title
LCS and SES: The Dual Problem
:::

Given sequences A (length N) and B (length M), two equivalent formulations exist. The **Longest Common Subsequence (LCS)**: the longest sequence obtainable from both A and B by deleting elements while preserving order. The **Shortest Edit Script (SES)**: the minimum insertions and deletions to transform A into B. If L = LCS length and D = SES length, then D = (N + M) − 2L. They are dual: solving one solves the other.
:::

::: section
::: section-title
The Edit Graph
:::

Eugene Myers (1986) unified these as shortest-path problems in an **edit graph**. A lies along the x-axis (0 to N), B along the y-axis (0 to M). Three edge types: **horizontal** (x,y)→(x+1,y) = delete A[x]; **vertical** (x,y)→(x,y+1) = insert B[y]; **diagonal** (x,y)→(x+1,y+1) when A[x]=B[y] = match (free, no edit cost). Any path from (0,0) to (N,M) is a valid edit script. The shortest path (fewest non-diagonal edges) is the SES. The path with the most diagonals traces the LCS.
:::

::: section
::: section-title
Diff Algorithms
:::

| Algorithm | Year | Complexity | Key Property |
|---|---|---|---|
| **Hunt-McIlroy** | 1975 | O(N·M) | First practical file comparison algorithm. Basis for original Unix `diff`. |
| **Myers** | 1986 | O(ND) | Fast when differences are small. Edit graph formulation. Git's default. Linear-space variant via divide-and-conquer. |
| **Patience** | ~2007 | O(N log N + ND) | Matches unique lines first, recurses on gaps. Better diffs for code with many duplicate lines. |
| **Histogram** | ~2010 | Similar to Patience | Extension of patience. Superior speed and output quality. Default in Git's `ort` merge strategy. |
:::

::: {.callout .note}
::: callout-label
Note
:::

Diffs are not unique. Multiple valid edit scripts can exist for the same input pair — they all correctly transform A to B but match different lines. This matters for three-way merge: the LCS matching chosen by the diff subroutine determines which regions are classified as "changed," which affects whether a merge conflicts or resolves cleanly. Different diff algorithms can produce different merge outcomes on the same inputs.
:::
:::

::: {#ch-two-vs-three .chapter}
::: chapter-number
Section 3
:::

::: chapter-title
Two-Way vs Three-Way Merge
:::

A **two-way merge** compares two files (A and B) with no shared history. It sees differences but cannot attribute them. If A has a line that B lacks — was it added by A or deleted by B? Every difference is ambiguous. Every ambiguity is a potential false conflict.

A **three-way merge** adds a third input: **O (the origin)**, the version from which both A and B diverged. O provides attribution. A line in O and A but not B: B deleted it. A line in A but not O or B: A added it. Attribution eliminates the ambiguity that makes two-way merge impractical for real work.

::: {.callout .key}
::: callout-label
The fundamental insight
:::

The common ancestor turns an ambiguous comparison into a directed change-tracking problem. With two inputs you know *what* differs. With three you know *who* changed *what* — and can propagate non-conflicting changes from both sides automatically.
:::
:::

::: {#ch-threeway .chapter}
::: chapter-number
Section 4
:::

::: chapter-title
Three-Way Merge Formalized
:::

::: section
::: section-title
The Three Inputs
:::

- **O (Origin / Base / Ancestor)** — the last version both sides shared
- **A (This / Ours)** — one divergent version
- **B (Other / Theirs)** — the other divergent version

Goal: produce M incorporating every change A made to O and every change B made to O.
:::

::: section
::: section-title
The Diff3 Algorithm
:::

GNU `diff3`, the standard implementation, works in four stages:

1. **Pairwise diff.** Compute diff(O, A) and diff(O, B), finding LCS matchings.
2. **Region identification.** Mark regions where O differs from A, from B, or both. **Coalesce** overlapping changed regions into single chunks.
3. **Classification.** Produce an alternating sequence of **stable chunks** (O = A = B) and **unstable chunks** (at least one version differs).
4. **Decision.** Apply the merge decision table to each unstable chunk.
:::

::: section
::: section-title
The Merge Decision Table
:::

::: {.callout .key}
::: callout-label
Core logic
:::

| O | A | B | Result | Reason |
|---|---|---|--------|--------|
| x | x | x | x | No change. Stable. |
| x | y | x | y | Only A changed → take A. |
| x | x | y | y | Only B changed → take B. |
| x | y | y | y | Both changed identically → take either. |
| x | y | z | **CONFLICT** | Both changed differently → cannot auto-resolve. |

This five-row table is the core of every three-way merge implementation. Rows 1–4 resolve automatically. Row 5 requires human judgment.
:::
:::

::: section
::: section-title
The Khanna-Kunal-Pierce Formalization (2007)
:::

"A Formal Investigation of Diff3" (Sanjeev Khanna, Keshav Kunal, Benjamin C. Pierce; FSTTCS 2007, University of Pennsylvania) was the first rigorous analysis of the diff3 algorithm. Contributions:

- **Formal specification** — a compact reference implementation in half a page of pseudocode.
- **Locality analysis** — investigated the intuition that edits to well-separated regions never conflict. Proved this **wrong in general**.
- **Counterexample** — even with arbitrarily large or unique separating regions, the LCS matching can bridge across them and create unexpected conflicts.

The root cause is that diff3 treats two-way diff as a black box. The matching decisions inside diff have non-local effects that propagate into the merge. In practice this rarely matters — real edits tend to be localized and real documents have enough unique context. But the theoretical guarantee does not hold.
:::
:::

::: {#ch-ancestor .chapter}
::: chapter-number
Section 5
:::

::: chapter-title
Common Ancestor Computation
:::

The ancestor is the single most important input to three-way merge. Everything downstream depends on getting it right.

::: section
::: section-title
Merge Base as Lowest Common Ancestor
:::

In Git's commit DAG, the merge base of two commits is their **lowest common ancestor (LCA)** — the most recent commit reachable from both. Found by walking parent pointers from both commits in breadth-first order until a common commit appears.
:::

::: section
::: section-title
The Criss-Cross Problem
:::

When branches merge into each other and then diverge again, a unique LCA may not exist. The criss-cross topology produces two equally valid candidate ancestors. Choosing one over the other yields different merge results.

Git's solution: **recursive merge**. Merge the candidate ancestors first to construct a **virtual ancestor**, then use that as the base. If the recursive merge itself encounters multiple LCAs, recurse again. Termination is guaranteed because the commit history is finite. In the standard criss-cross case, at most two candidates exist.
:::

::: {.callout .warn}
::: callout-label
Warning
:::

Without a recoverable ancestor, you fall back to two-way merge — which cannot distinguish additions from deletions and generates far more false conflicts. Systems that manage concurrent document modification without version tracking (shared drives, email attachments, manual file copies) face exactly this problem.
:::
:::

::: {#ch-conflict .chapter}
::: chapter-number
Section 6
:::

::: chapter-title
Conflict Detection and Resolution
:::

::: section
::: section-title
What Constitutes a Conflict
:::

Row 5 of the decision table: both A and B modified the same region of O differently. The algorithm cannot determine which change (or what combination) the user intends.
:::

::: section
::: section-title
Resolution Strategies
:::

| Strategy | Mechanism | Typical Context |
|---|---|---|
| **Manual** | Human edits the file directly | Software development (standard) |
| **Ours / Theirs** | Accept one branch wholesale | Automated pipelines, priority branches |
| **Last-writer-wins** | Timestamp determines winner | CRDTs, distributed databases |
| **Semantic** | Language-aware AST-level resolution | Structured merge tools |
:::

::: section
::: section-title
Guaranteed Properties
:::

Three-way merge provides:

- **Stability** — unchanged regions are preserved.
- **Monotonicity** — one-sided changes are always propagated.
- **Agreement idempotency** — identical changes from both sides produce a single clean result.

A property that does **not** hold (Khanna et al. 2007):

- **Locality** — well-separated edits are not guaranteed conflict-free.
:::

::: section
::: section-title
Edge Cases
:::

**Reverted changes:** Three-way merge examines only O, A, and B — not intermediate commits. If branch A modifies and then reverts a line, A's tip matches O. If B independently modifies the same line, the merge takes B's change cleanly — the revert is invisible.

**Semantic conflicts:** A merge can be textually clean but semantically broken. Branch A renames function `foo()` to `bar()`; branch B adds a call to `foo()`. No textual conflict, but the merged code calls a nonexistent function.
:::

::: {.callout .tip}
::: callout-label
Reframe
:::

Conflicts are information, not failures. They mark the boundaries where automated reasoning cannot determine intent. A system that never produces conflicts is either working on non-overlapping changes or silently losing data.
:::
:::

::: {#ch-git .chapter}
::: chapter-number
Section 7
:::

::: chapter-title
Git's Merge Machinery
:::

::: section
::: section-title
Merge Strategies
:::

| Strategy | Description |
|---|---|
| **ort** | Default since v2.33.0. "Ostensibly Recursive's Twin" — a from-scratch rewrite by Elijah Newren. Recursive virtual-ancestor construction, rename detection, histogram diff by default. |
| **resolve** | Simple three-way merge. Single common ancestor only. No rename detection. |
| **octopus** | Merges more than two branches. Refuses to create merges requiring manual resolution. |
| **subtree** | Adjusts tree structure before merging. For nested project hierarchies. |
:::

::: section
::: section-title
Cherry-Pick and Revert as Merge
:::

Git implements cherry-pick using the full three-way merge machinery. To cherry-pick commit C₂ (parent C₁) onto tip Cₘ: merge base = C₁, ours = Cₘ, theirs = C₂. Revert is identical but swaps parent and child.
:::

::: section
::: section-title
Merge vs Rebase
:::

Both use three-way merge internally. A merge takes two tips and their ancestor to produce a merge commit. A rebase replays each commit via cherry-pick. The difference is topological (merge preserves branches, rebase linearizes). The underlying algorithm is the same.
:::
:::

::: {#ch-structured .chapter}
::: chapter-number
Section 8
:::

::: chapter-title
Beyond Text: Structured Merge
:::

::: section
::: section-title
Why Text-Level Merge Is Insufficient
:::

Unstructured merge operates on lines with no semantic awareness. This produces **spurious conflicts** (textually overlapping but semantically independent changes) and misses **semantic conflicts** (textually clean merges that produce broken programs).
:::

::: section
::: section-title
AST-Based Structured Merge
:::

**Structured merge** parses source into Abstract Syntax Trees and merges at the node level. The **Mastery** algorithm (2023) combines top-down pruning with bottom-up matching in linear time. Uses adapted GumTree for tree matching. Distinguishes ordered children (statement sequences) from unordered children (class members). Evaluated on 40,533 real merge scenarios from 78 Java projects.
:::

::: section
::: section-title
Non-Text Applications
:::

**XML:** The 3DM system (Lindholm, DocEng 2004) performs three-way merge on XML document trees.

**Databases:** Dolt implements Git-style three-way merge on relational tables with cell-level diff and merge.

**Formal verification:** Sousa, Dillig, and Lahiri (OOPSLA 2018) demonstrated verified three-way program merge — using program verification to prove merged programs preserve the semantics of both input changes. An active research frontier.
:::
:::

::: {#ch-alternatives .chapter}
::: chapter-number
Section 9
:::

::: chapter-title
Alternative Paradigms
:::

::: section
::: section-title
Operational Transformation (OT)
:::

Real-time collaborative editing (Google Docs). Transforms each user's operations against concurrent operations. Server-authoritative. Does not scale well peer-to-peer.
:::

::: section
::: section-title
CRDTs (Conflict-Free Replicated Data Types)
:::

Formally defined by Shapiro, Preguiça, Baquero, and Zawirski (2011). Data structures where concurrent updates merge deterministically without coordination. Mathematical basis: a **join-semilattice** — merge is associative, commutative, and idempotent. Two approaches: **state-based (CvRDT)** and **operation-based (CmRDT)**. Used by Automerge, Yjs, Redis, Apple Notes, Figma, Zed editor.
:::

::: section
::: section-title
Patch Theory (Darcs)
:::

Patches as algebraic objects that can be **commuted** (reordered). Non-commutable patches are conflicts. Clean merges are provably correct. Practical conflict resolution remains open research.
:::

::: section
::: section-title
Weave Merge
:::

No common ancestor. Tracks line provenance across all versions. Used by BitKeeper. Handles some diff3 edge cases.
:::

| Paradigm | Ancestor? | Real-Time? | Conflict-Free? | Formal Guarantees |
|---|---|---|---|---|
| **Three-way merge** | Required | No | No | Stability, monotonicity |
| **OT** | No | Yes | By design | Convergence |
| **CRDTs** | No | Yes | Yes | Strong eventual consistency |
| **Patch theory** | Implicit | No | No | Provable correctness (clean) |
| **Weave merge** | No | No | No | Handles some edge cases |
:::

::: {#ch-board .chapter}
::: chapter-number
Section 10
:::

::: chapter-title
Board Connection
:::

Three-way merge is a general-purpose reconciliation framework. Its structures map onto Loop MMT's architecture at multiple points.

::: section
::: section-title
The Reconciliation Protocol and the Decision Table
:::

When two instances modify shared corpus documents between handoffs, the result is a three-way merge problem. The last handoff version is O. Each instance's output is A or B. The five-case decision table classifies each divergent section: auto-merge or operator review.
:::

::: section
::: section-title
The Handoff Document as Merge Base
:::

The EOD handoff document is the merge base — the last agreed-upon state. "Derive state, don't maintain it" is structurally identical to the merge-base-first principle: always start from the ancestor, compute diffs forward.
:::

::: section
::: section-title
Append-Only Identity as Grow-Only CRDT
:::

Loop MMT's append-only rule has the algebraic properties of a grow-only CRDT. Append operations commute and are idempotent. This is why append-only data avoids merge conflicts by construction. The event ledger shares this property.
:::

::: section
::: section-title
Conflicts as Protocol Design Signals
:::

A conflict between instances means the protocol's scope boundaries allowed overlapping modifications without coordination. The right response is to redesign the protocol so the conflicting state cannot arise. Fix by Design applied to document management: structural prevention over behavioral discipline.
:::
:::

::: {#ch-refs .chapter}
::: chapter-number
References
:::

::: chapter-title
References
:::

1. Myers, E.W. "An O(ND) Difference Algorithm and Its Variations." *Algorithmica* 1, 251–266 (1986).
2. Khanna, S., Kunal, K., Pierce, B.C. "A Formal Investigation of Diff3." *FSTTCS 2007*, LNCS vol 4855, Springer, 2007.
3. Tichy, W.F. "Design, Implementation, and Evaluation of a Revision Control System." *ICSE'82*, 1982.
4. Hunt, J.W. and McIlroy, M.D. "An Algorithm for Differential File Comparison." Bell Labs Tech Report 41, 1975.
5. Lindholm, T. "A Three-Way Merge for XML Documents." *DocEng 2004*, ACM, 2004.
6. Shapiro, M., Preguiça, N., Baquero, C., Zawirski, M. "Conflict-free Replicated Data Types." *SSS 2011*, Springer, 2011.
7. Mens, T. "A State-of-the-Art Survey on Software Merging." *IEEE Trans. Software Eng.* 28(5), 449–462, 2002.
8. Git Project. "merge-strategies." git-scm.com/docs/merge-strategies.
9. Smith, R. GNU diff3, v2.8.1. GNU diffutils, 2002 (original 1988).
10. "On the methodology of three-way structured merge in version control systems." *Journal of Systems and Software*, 2023.
11. Greenwald, M.B., Khanna, S., Kunal, K., Pierce, B.C., Schmitt, A. "Agreeing to Agree: Conflict Resolution for Optimistically Replicated Data." *DISC 2006*.
12. Sousa, M., Dillig, I., Lahiri, S. "Verified Three-Way Program Merge." *Proc. ACM Program. Lang.* 2(OOPSLA), 2018.
:::
:::
:::

------------------------------------------------------------------------

::: page-footer
Loop MMT™ · Version Control & Three-Way Merge Algorithms · v1 © 2026 Shea Gunther · [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/deed.en){style="color:inherit;"}
:::
