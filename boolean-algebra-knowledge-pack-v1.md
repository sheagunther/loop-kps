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
Boolean Algebra Knowledge Pack
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
-   [1 · Foundations](#ch-foundations)
-   [2 · Laws and Identities](#ch-laws)
-   [3 · Boolean Functions](#ch-functions)
-   [4 · Minimization](#ch-minimization)
-   [5 · Functional Completeness](#ch-completeness)
-   [6 · Digital Logic](#ch-logic)
-   [7 · Connections](#ch-connections)
-   [8 · Laws Quick Reference](#ch-quick-ref)
-   [References](#ch-refs)

::: {.content role="main"}
::: {#ch-abstract .abstract-box}
::: abstract-label
About This Document
:::

This is a reference document on Boolean algebra, designed for AI advisory conversations. It covers the algebraic foundations, all standard identities, canonical forms, minimization techniques, functional completeness, digital logic connections, and the relationships between Boolean algebra and other mathematical structures. All identities are collected in a quick-reference table at the end.

The document draws on 11 sources. Full citations appear in the References section.
:::

::: {#ch-foundations .chapter}
::: chapter-number
Section 1
:::

::: chapter-title
Foundations
:::

::: section
::: section-title
What is Boolean Algebra
:::

A **Boolean algebra** is a set B equipped with two binary operations ∧ (AND, meet, conjunction) and ∨ (OR, join, disjunction), a unary operation ¬ (NOT, complement), and two distinguished elements 0 (false) and 1 (true), satisfying the Huntington axioms. Named after George Boole, who introduced the algebraic approach to logic in 1847. First axiomatized by Edward V. Huntington in 1904.
:::

::: section
::: section-title
The Huntington Axioms
:::

For all a, b, c ∈ B:

  Axiom                ∨ Form                  ∧ Form
  -------------------- ----------------------- -----------------------
  **Commutativity**    a ∨ b = b ∨ a           a ∧ b = b ∧ a
  **Associativity**    (a∨b)∨c = a∨(b∨c)       (a∧b)∧c = a∧(b∧c)
  **Distributivity**   a∨(b∧c) = (a∨b)∧(a∨c)   a∧(b∨c) = (a∧b)∨(a∧c)
  **Identity**         a ∨ 0 = a               a ∧ 1 = a
  **Complement**       a ∨ ¬a = 1              a ∧ ¬a = 0

::: {.callout .warn}
::: callout-label
Both distributive laws hold
:::

In ordinary algebra, multiplication distributes over addition but not vice versa. In Boolean algebra, BOTH ∨ distributes over ∧ AND ∧ distributes over ∨. This is a fundamental difference. The dual distributive law a∨(b∧c) = (a∨b)∧(a∨c) has no analog in ordinary algebra.
:::
:::

::: section
::: section-title
Duality Principle
:::

Every Boolean identity has a **dual** obtained by swapping ∨ with ∧ and 0 with 1. If an identity is valid, its dual is also valid. This means every theorem comes in pairs --- prove one, get the other free.
:::

::: section
::: section-title
XOR and XNOR
:::

The **exclusive OR** (XOR, ⊕) is defined as a ⊕ b = (a ∧ ¬b) ∨ (¬a ∧ b). It outputs 1 when exactly one input is 1. XOR is associative, commutative, and self-inverse (a ⊕ a = 0). The **XNOR** (equivalence) is ¬(a ⊕ b) = (a ∧ b) ∨ (¬a ∧ ¬b) --- it outputs 1 when both inputs match. XOR forms a group structure: (B, ⊕, 0) is an abelian group where every element is its own inverse.
:::
:::

::: {#ch-laws .chapter}
::: chapter-number
Section 2
:::

::: chapter-title
Laws and Identities
:::

All fundamental Boolean identities, derivable from the Huntington axioms:

  Law                   ∨ Form                                         ∧ Form
  --------------------- ---------------------------------------------- -----------------
  **Idempotent**        a ∨ a = a                                      a ∧ a = a
  **Domination**        a ∨ 1 = 1                                      a ∧ 0 = 0
  **Absorption**        a ∨ (a ∧ b) = a                                a ∧ (a ∨ b) = a
  **Involution**        ¬(¬a) = a                                      
  **De Morgan I**       ¬(a ∧ b) = ¬a ∨ ¬b                             
  **De Morgan II**      ¬(a ∨ b) = ¬a ∧ ¬b                             
  **Complement Laws**   a ∨ ¬a = 1                                     a ∧ ¬a = 0
  **Consensus**         (a∧b) ∨ (¬a∧c) ∨ (b∧c) = (a∧b) ∨ (¬a∧c)        
  **XOR definition**    a ⊕ b = (a∧¬b) ∨ (¬a∧b)                        
  **XOR properties**    a ⊕ 0 = a, a ⊕ 1 = ¬a, a ⊕ a = 0, a ⊕ ¬a = 1   

::: {.callout .key}
::: callout-label
De Morgan\'s Laws
:::

De Morgan\'s laws are the single most important tool for manipulating Boolean expressions. They convert between AND and OR by pushing negation through: ¬(a ∧ b) = ¬a ∨ ¬b and ¬(a ∨ b) = ¬a ∧ ¬b. They generalize to any number of variables: ¬(a₁ ∧ a₂ ∧ \... ∧ a_n) = ¬a₁ ∨ ¬a₂ ∨ \... ∨ ¬a_n, and similarly for ∨. Every conversion between SOP and POS, every NAND/NOR implementation, and every complement computation relies on De Morgan.
:::
:::

::: {#ch-functions .chapter}
::: chapter-number
Section 3
:::

::: chapter-title
Boolean Functions
:::

::: section
::: section-title
Truth Tables and Definitions
:::

A **Boolean function** f: {0,1}^n^ → {0,1} maps n binary inputs to one binary output. It is completely specified by a **truth table** with 2^n^ rows. There are 2^2\^n^ distinct Boolean functions of n variables (e.g., 16 functions of 2 variables).
:::

::: section
::: section-title
Canonical Forms
:::

A **minterm** m~i~ is a product term where every variable appears exactly once, either complemented or uncomplemented. It evaluates to 1 for exactly one row of the truth table. A **maxterm** M~i~ is a sum term where every variable appears exactly once; it evaluates to 0 for exactly one row.

**Sum of Products (SOP) / Disjunctive Normal Form (DNF):** f = ∨ of all minterms where f = 1. Written: f(x,y,z) = Σm(i₁, i₂, \...).

**Product of Sums (POS) / Conjunctive Normal Form (CNF):** f = ∧ of all maxterms where f = 0. Written: f(x,y,z) = ΠM(j₁, j₂, \...).

Every Boolean function has a unique canonical SOP and a unique canonical POS. They are complements: if f = Σm(S), then ¬f = Σm(S̄), and f = ΠM(S̄).
:::

::: section
::: section-title
Shannon Expansion
:::

**Shannon\'s expansion theorem:** Any Boolean function can be decomposed around any variable x as:

f(x, \...) = x · f(1, \...) ∨ ¬x · f(0, \...)

where f(1, \...) and f(0, \...) are the **cofactors** of f with respect to x. This is the basis for binary decision diagrams (BDDs), recursive minimization, and the if-then-else normal form. Applied repeatedly, it decomposes any function into its complete minterm expansion.
:::

::: section
::: section-title
Algebraic Normal Form (Zhegalkin Polynomial)
:::

Every Boolean function has a unique representation as a XOR of AND terms (with no complements):

f = a₀ ⊕ a₁x₁ ⊕ a₂x₂ ⊕ \... ⊕ a₁₂x₁x₂ ⊕ \... ⊕ a₁₂\...ₙx₁x₂\...xₙ

where each a~i~ ∈ {0,1}. This is the representation of Boolean functions as polynomials over GF(2) (the field with two elements). The **algebraic degree** of f is the degree of the highest-degree term with a nonzero coefficient.
:::
:::

::: {#ch-minimization .chapter}
::: chapter-number
Section 4
:::

::: chapter-title
Minimization
:::

The goal of Boolean minimization is to find the simplest equivalent expression --- fewest literals, fewest terms, or both. This directly translates to simpler circuits with fewer gates.

::: section
::: section-title
Prime and Essential Prime Implicants
:::

An **implicant** of f is a product term P such that P = 1 implies f = 1. A **prime implicant** is an implicant that cannot be reduced (no literal can be removed while remaining an implicant). An **essential prime implicant** is a prime implicant that covers at least one minterm not covered by any other prime implicant --- it MUST appear in every minimum SOP expression.

::: {.callout .tip}
::: callout-label
Minimization strategy
:::

Step 1: Find all prime implicants. Step 2: Identify essential prime implicants (must be included). Step 3: Cover remaining minterms with the fewest additional prime implicants. K-maps do this visually for ≤ 6 variables; Quine-McCluskey does it systematically for any number.
:::
:::

::: section
::: section-title
Karnaugh Maps (1953)
:::

A **Karnaugh map** is a 2D grid where cells represent minterms and adjacent cells differ by exactly one variable (Gray code ordering). Groups of 1s in power-of-2 rectangles (1, 2, 4, 8, \...) correspond to product terms; larger groups eliminate more variables. The map wraps around at edges (top-bottom and left-right adjacency). Practical for 2--6 variables.

**Don\'t-care conditions** (X) represent input combinations that cannot occur or whose output is irrelevant. They can be treated as 0 or 1 --- whichever yields simpler groupings.
:::

::: section
::: section-title
Quine-McCluskey Algorithm (1952/1956)
:::

A systematic tabular method for finding all prime implicants and selecting a minimum cover. Steps: (1) List all minterms in binary. (2) Group by number of 1s. (3) Compare adjacent groups; combine terms differing by one bit, marking the differing position as \"-\". (4) Repeat until no more combinations. (5) Remaining unchecked terms are prime implicants. (6) Build a prime implicant chart and select minimum cover (covering all minterms with fewest primes). Finding the minimum cover is NP-hard in general.
:::

::: section
::: section-title
Espresso Algorithm (1984)
:::

A heuristic two-level logic minimizer developed at UC Berkeley. Does not guarantee optimal results but produces near-optimal solutions very efficiently for large numbers of variables. Used in practice by most EDA (electronic design automation) tools. Based on iterative expansion, reduction, and irredundant cover operations.
:::
:::

::: {#ch-completeness .chapter}
::: chapter-number
Section 5
:::

::: chapter-title
Functional Completeness
:::

A set of Boolean operations is **functionally complete** if every Boolean function can be expressed using only operations from that set.

  Set              Complete?   Why
  ---------------- ----------- -----------------------------------------------
  {AND, OR, NOT}   Yes         Standard basis; canonical forms use all three
  {AND, NOT}       Yes         OR derived via De Morgan: a∨b = ¬(¬a∧¬b)
  {OR, NOT}        Yes         AND derived via De Morgan: a∧b = ¬(¬a∨¬b)
  {NAND}           Yes         NOT: a↑a = ¬a. AND: ¬(a↑b). OR via De Morgan.
  {NOR}            Yes         NOT: a↓a = ¬a. OR: ¬(a↓b). AND via De Morgan.
  {AND, OR}        No          Cannot produce NOT (both are monotone)
  {XOR, AND}       Yes         NOT: a⊕1 = ¬a. OR: a∨b = (a⊕b)⊕(a∧b)

::: {.callout .key}
::: callout-label
NAND and NOR are universal
:::

NAND and NOR are the only single binary operations that are individually functionally complete. This is why digital circuits can be built entirely from NAND gates or entirely from NOR gates --- a fact of enormous practical importance in chip design. Post\'s classification (1941) provides a complete characterization of which sets of Boolean functions are functionally complete.
:::
:::

::: {#ch-logic .chapter}
::: chapter-number
Section 6
:::

::: chapter-title
Digital Logic
:::

::: section
::: section-title
Logic Gates
:::

  Gate   Operation   Symbol     Output
  ------ ----------- ---------- -----------------------------
  AND    a ∧ b       a · b      1 only if both inputs are 1
  OR     a ∨ b       a + b      1 if either input is 1
  NOT    ¬a          a\' or ā   Inverts the input
  NAND   ¬(a ∧ b)    a ↑ b      0 only if both inputs are 1
  NOR    ¬(a ∨ b)    a ↓ b      1 only if both inputs are 0
  XOR    a ⊕ b       a ⊕ b      1 if inputs differ
  XNOR   ¬(a ⊕ b)    a ⊙ b      1 if inputs match
:::

::: section
::: section-title
Two-Level Circuits
:::

Any Boolean function can be implemented as a **two-level circuit**: SOP → first level of AND gates feeding a second-level OR gate; POS → first level of OR gates feeding a second-level AND gate. Two-level circuits have constant propagation delay (two gate delays) regardless of the number of variables --- the tradeoff is gate count vs. depth.

NAND-NAND implementation is equivalent to AND-OR (SOP). NOR-NOR is equivalent to OR-AND (POS). These follow directly from De Morgan\'s laws and involution.
:::
:::

::: {#ch-connections .chapter}
::: chapter-number
Section 7
:::

::: chapter-title
Connections to Other Structures
:::

::: section
::: section-title
Set Theory
:::

The power set P(S) of any set S forms a Boolean algebra under union (∨), intersection (∧), and set complement (¬), with ∅ as 0 and S as 1. This is the prototypical concrete Boolean algebra.
:::

::: section
::: section-title
Propositional Logic
:::

Boolean algebra is the algebraic semantics of propositional calculus. Boolean variables become propositional variables; AND becomes conjunction; OR becomes disjunction; NOT becomes negation. Tautologies correspond to Boolean expressions equal to 1; contradictions to expressions equal to 0.
:::

::: section
::: section-title
Lattice Theory and Boolean Rings
:::

A Boolean algebra is a **complemented distributive lattice** --- a lattice where every element has a unique complement and both distributive laws hold. This places Boolean algebra within the broader theory of ordered sets and lattices.

Every Boolean algebra has an equivalent **Boolean ring** where XOR serves as addition and AND serves as multiplication. In this ring, every element is idempotent (x² = x) and characteristic is 2 (x + x = 0).
:::

::: section
::: section-title
Stone\'s Representation Theorem (1936)
:::

**Stone\'s theorem:** Every Boolean algebra is isomorphic to the Boolean algebra of clopen (simultaneously closed and open) sets in some compact totally disconnected Hausdorff topological space (a **Stone space**). This deep result shows that every abstract Boolean algebra can be concretely represented as a set algebra --- there is no \"exotic\" Boolean algebra that cannot be modeled by sets.
:::

::: section
::: section-title
Shannon\'s Circuit Theory (1938)
:::

Claude Shannon\'s 1938 master\'s thesis showed that Boolean algebra could model relay and switching circuits, founding the field of digital circuit design. This connection between abstract algebra and electrical engineering is one of the most consequential applications of mathematics in the 20th century.
:::
:::

::: {#ch-quick-ref .chapter}
::: chapter-number
Section 8
:::

::: chapter-title
Laws Quick Reference
:::

  Law                 Identity
  ------------------- -------------------------------------------------
  Identity            a∨0 = a, a∧1 = a
  Domination          a∨1 = 1, a∧0 = 0
  Idempotent          a∨a = a, a∧a = a
  Complement          a∨¬a = 1, a∧¬a = 0
  Involution          ¬(¬a) = a
  Commutative         a∨b = b∨a, a∧b = b∧a
  Associative         (a∨b)∨c = a∨(b∨c), (a∧b)∧c = a∧(b∧c)
  Distributive        a∧(b∨c) = (a∧b)∨(a∧c), a∨(b∧c) = (a∨b)∧(a∨c)
  Absorption          a∨(a∧b) = a, a∧(a∨b) = a
  De Morgan           ¬(a∧b) = ¬a∨¬b, ¬(a∨b) = ¬a∧¬b
  Consensus           (a∧b)∨(¬a∧c)∨(b∧c) = (a∧b)∨(¬a∧c)
  XOR                 a⊕b = (a∧¬b)∨(¬a∧b), a⊕0 = a, a⊕1 = ¬a, a⊕a = 0
  Shannon expansion   f = x·f\|₁ ∨ ¬x·f\|₀
:::

::: {#ch-refs .chapter}
::: chapter-number
References
:::

::: chapter-title
References
:::

1.  Boole, G. *An Investigation of the Laws of Thought*. Walton and Maberly, 1854.
2.  Brayton, R.K. et al. *Logic Minimization Algorithms for VLSI Synthesis*. Kluwer, 1984.
3.  Givant, S. & Halmos, P. *Introduction to Boolean Algebras*. Springer, 2009.
4.  Huntington, E.V. \"Sets of independent postulates for the algebra of logic.\" *Transactions of the AMS* 5 (1904): 288--309.
5.  Karnaugh, M. \"The map method for synthesis of combinational logic circuits.\" *Transactions of the AIEE* 72 (1953): 593--599.
6.  McCluskey, E.J. \"Minimization of Boolean functions.\" *Bell System Technical Journal* 35 (1956): 1417--1444.
7.  Post, E.L. *The Two-Valued Iterative Systems of Mathematical Logic*. Princeton University Press, 1941.
8.  Quine, W.V.O. \"The problem of simplifying truth functions.\" *American Mathematical Monthly* 59 (1952): 521--531.
9.  Shannon, C.E. \"A symbolic analysis of relay and switching circuits.\" *Transactions of the AIEE* 57 (1938): 713--723.
10. Stone, M.H. \"The theory of representations for Boolean algebras.\" *Transactions of the AMS* 40 (1936): 37--111.
11. Whitehead, A.N. *A Treatise on Universal Algebra*. Cambridge University Press, 1898.
:::
:::
:::

------------------------------------------------------------------------

::: page-footer
Loop MMT™ · Multi-Module Theory Boolean Algebra Knowledge Pack · v1 © 2026 Shea Gunther · [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/deed.en){style="color:inherit;"}
:::
