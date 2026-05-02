# Category Theory: Colimits & Composition Knowledge Pack

**Loop MMT™ · Multi-Module Theory**
v1 · 9 April 2026

---

## About This Document

This Knowledge Pack covers **colimits** and **composition** in category theory — the mathematical framework for combining structured objects while preserving their relationships. The central construction is the **pushout**: it describes what a merged output is, relative to its inputs and their shared origin.

The pack equips AI advisors in Loop MMT conversations with the formal language for document composition, merge protocols, and any situation where distinct components combine through a shared interface. Prerequisites (categories, functors, natural transformations) are covered in Section 1. Colimits are developed from first principles in Sections 2–4.

The core claim: when two documents share a common ancestor and must be merged, the result is a pushout. When divergent states are reconciled, the result is a coequalizer. When accumulated events produce current state, that state is a directed colimit. These are instances of the same mathematical structure operating across different domains.

---

## 1 · Prerequisite Machinery

### Categories

A **category** C has objects, morphisms (arrows) between them, a composition operation, and identities. For morphisms f: A → B and g: B → C, their composite is g ∘ f: A → C. Each object A has an identity id_A: A → A. Composition is associative; identities are neutral.

A category packages two things: the things, and the relationships between them. The relationships are first-class: they compose, they have identities, and they are what functors and natural transformations operate on.

Examples: **Set** (sets and functions), **Grp** (groups and homomorphisms), **Top** (topological spaces and continuous maps), **Vect_k** (vector spaces over a field k, and linear maps). Every poset (P, ≤) is a category with at most one morphism a → b whenever a ≤ b.

### Functors

A **functor** F: C → D maps objects to objects and morphisms to morphisms, preserving composition and identities: F(g ∘ f) = F(g) ∘ F(f) and F(id_A) = id_{F(A)}. A functor is a translation between categories that respects all structural relationships.

A **contravariant functor** C → D reverses arrows: formally, it is a functor C^op → D, where C^op is C with all arrows reversed. The **Hom functor** Hom(A, −): C → Set sends B to the set of morphisms A → B; the contravariant Hom(−, A): C^op → Set sends B to morphisms B → A.

### Natural Transformations

Given functors F, G: C → D, a **natural transformation** η: F ⇒ G assigns to each object A a morphism η_A: F(A) → G(A) such that for every f: A → B in C:

    G(f) ∘ η_A = η_B ∘ F(f)

This **naturality condition** says the transformation commutes with the functors' action on morphisms. When every component η_A is an isomorphism, η is a **natural isomorphism** and F and G are "the same functor up to a consistent change of perspective."

Natural transformations compose vertically (componentwise: (ε ∘ η)_A = ε_A ∘ η_A) and horizontally (between composites of functors). Functors C → D together with natural transformations form the **functor category** [C, D].

> **Historical.** Eilenberg and Mac Lane introduced categories in 1945 to define natural transformations — which was the concept they actually needed. Functors were intermediate scaffolding; categories were scaffolding for the scaffolding. The word "functor" came from the philosopher Rudolf Carnap; "category" from the philosophical tradition of Aristotle, Kant, and C.S. Peirce.

### Diagrams and Cocones

A **diagram** of shape J in C is a functor D: J → C. The category J (the **index category**) specifies the shape; D fills in the shape with objects and morphisms from C. A span (• ← • → •) and a parallel pair (• ⇉ •) are diagram shapes.

A **cocone** under D to an object L consists of morphisms ι_j: D(j) → L, one for each object j in J, such that for every morphism a: j → k in J, ι_k ∘ D(a) = ι_j. A cocone is a consistent collection of maps from the diagram into a single target. The dual notion — maps from a single source into the diagram — is a **cone**.

---

## 2 · Colimits

A **colimit** of a diagram D: J → C is a cocone that is universal — the "tightest" way to wrap the diagram into a single object.

> **Definition.** A colimit of D consists of an object colim D and coprojections ι_j: D(j) → colim D forming a cocone, such that for any other cocone (C, τ_j), there exists a **unique** morphism h: colim D → C with h ∘ ι_j = τ_j for all j. The colimit is initial in the category of cocones: every other cocone factors through it, and does so in exactly one way.

Colimits are unique up to **unique isomorphism**. If P and Q are both colimits of D, the universal property forces a unique isomorphism P ≅ Q compatible with all coprojections.

> **Caution.** A colimit is not "just a limit with arrows reversed." The duality is real — a colimit in C is a limit in C^op — but the reversal changes what the construction *does*. Limits constrain (they select compatible elements from a product). Colimits glue (they identify related elements in a coproduct). Confusing the two directions is a common source of errors.

### Computing Colimits in Set

In Set, every small colimit exists. For a diagram D: J → Set (with J presented by vertices V and arrows A), the formula is:

    colim D = { (v, d) | v ∈ V, d ∈ D(v) } / ~

where ~ is generated by: (v, d) ~ (w, e) whenever there exists an arrow a: v → w in J with D(a)(d) = e. In words: take the disjoint union of all sets in the diagram, then identify elements that the diagram's functions relate.

> **Intuition.** Limits pick subsets of products. Colimits take quotients of coproducts. A limit is a constrained product; a colimit is a coproduct with identifications.

---

## 3 · The Colimit Zoo

Each diagram shape yields a specific type of colimit. Four shapes account for most applications.

### Initial Object

Colimit of the empty diagram. An **initial object** 0 has a unique morphism 0 → A for every object A. In Set: the empty set ∅. In Grp: the trivial group {e}. Dual: the terminal object.

### Coproduct

Colimit of a discrete diagram (objects, no non-identity arrows). The **coproduct** X ⊔ Y has coprojections ι₁: X → X ⊔ Y, ι₂: Y → X ⊔ Y. Universal property: for any f: X → C and g: Y → C, there exists a unique h: X ⊔ Y → C with h ∘ ι₁ = f and h ∘ ι₂ = g. Equivalently:

    Hom(X ⊔ Y, C) ≅ Hom(X, C) × Hom(Y, C)

A map out of the coproduct is a pair of maps, one from each summand. In Set: disjoint union. In Grp: free product. In Ab: direct sum. In Top: disjoint union with coproduct topology.

### Coequalizer

Colimit of a parallel pair f, g: X ⇉ Y. The **coequalizer** is an object Q with q: Y → Q satisfying q ∘ f = q ∘ g, universal among all such. The coequalizer forces two morphisms to agree by identifying their images. In Set: quotient of Y by the smallest equivalence relation making f(x) ∼ g(x). In Ab: Y / im(f − g). Every coequalizing morphism is an epimorphism.

### Pushout

Colimit of a span Z →f X, Z →g Y. The **pushout** P has maps i₁: X → P, i₂: Y → P with i₁ ∘ f = i₂ ∘ g, universal among all commutative completions of the span. Full treatment in Section 4.

| Type | Diagram Shape | Set | Grp | One-Line Description |
|------|--------------|-----|-----|---------------------|
| Initial object | ∅ | ∅ | {e} | Unique map to everything |
| Coproduct | •  • | Disjoint union | Free product | Sum without identification |
| Coequalizer | • ⇉ • | Quotient by ~ | Quotient group | Force two maps to agree |
| Pushout | • ← • → • | Glued union | Amalgamated free product | Glue along shared piece |

---

## 4 · Pushouts in Depth

### Definition and Universal Property

Given morphisms f: Z → X and g: Z → Y, a **pushout** is an object P with i₁: X → P and i₂: Y → P satisfying:

1. **Commutativity**: i₁ ∘ f = i₂ ∘ g (the two paths from Z to P agree).
2. **Universality**: for any (Q, j₁, j₂) with j₁ ∘ f = j₂ ∘ g, there exists a unique u: P → Q with u ∘ i₁ = j₁ and u ∘ i₂ = j₂.

Z is the shared origin. X and Y are the components being merged. P is the merged result — the smallest object into which both X and Y embed consistently.

### Construction

When coproducts and coequalizers exist, the pushout is built in two steps. Form the coproduct X ⊔ Y. Construct two maps from Z to X ⊔ Y: one via ι₁ ∘ f, the other via ι₂ ∘ g. The pushout is the coequalizer of this pair. In words: take the disjoint union, then identify each element of Z-in-X with the corresponding element of Z-in-Y.

### Worked Example

Let Z = {a, b}, X = {a, b, c}, Y = {a, b, d} in Set, with f and g the inclusions. The coproduct X ⊔ Y has six elements: {a_X, b_X, c, a_Y, b_Y, d}. The coequalizer identifies a_X with a_Y and b_X with b_Y. Result: P = {a, b, c, d}. When Z is the intersection and f, g are inclusions, the pushout is the union.

### Pasting Lemma

Given two adjacent commutative squares, if the left is a pushout, then the outer rectangle is a pushout if and only if the right square is a pushout. Complex gluings decompose into sequences of simple pushouts. The converse fails: the outer rectangle and right square being pushouts does not guarantee the left square is one.

### Pushouts Across Categories

**Top**: Pushouts build CW complexes. Attaching a disk along its boundary is a pushout. Spheres, tori, projective spaces are assembled this way.

**Grp**: The pushout of homomorphisms f: H → G and g: H → K is the free product with amalgamation G *_H K. The Seifert–van Kampen theorem says π₁ preserves pushouts of inclusions.

**CRing**: The pushout of ring homomorphisms via a common ring C is the tensor product A ⊗_C B.

> **The Pushout Principle.** A pushout is characterized by what it *does* — how other objects map out of it — not by what it *is* internally. Two constructions satisfying the same universal property are uniquely isomorphic. The correctness of a merge can be verified structurally: does it satisfy the universal property? If yes, it is the right answer regardless of how it was built.

---

## 5 · Theorems & Structure

### Cocompleteness

A category has all finite colimits if and only if it has finite coproducts and coequalizers — or equivalently, pushouts and an initial object. Two building blocks generate the entire colimit zoo. Set, Grp, Ab, Top, and most standard categories are cocomplete.

### Colimit ⊣ Diagonal

The diagonal functor Δ: C → C^J sends an object A to the constant diagram at A. When C has J-shaped colimits, the colimit functor is left adjoint to Δ:

    Hom(colim D, A) ≅ Nat(D, ΔA)

Morphisms out of the colimit correspond bijectively to cocones over the diagram.

### Preservation of Colimits

If F ⊣ G (F is left adjoint to G), then F preserves all colimits. Dually, G preserves all limits. Mnemonic: **RAPL** — Right Adjoints Preserve Limits. Dual: left adjoints preserve colimits.

> **Consequence.** Free constructions (left adjoints to forgetful functors) always preserve colimits. The free group on a disjoint union is the free product of the free groups.

### Yoneda Lemma

For a locally small category C, an object A, and a functor F: C^op → Set:

    Nat(Hom(−, A), F) ≅ F(A)

The **Yoneda embedding** y: C → [C^op, Set] is full and faithful. It preserves limits but not colimits in general.

### Kan Extensions and Free Cocompletion

A **left Kan extension** of F along K is the "best approximation" from D. Colimits are a special case: the colimit of F is its left Kan extension along C → 1. Mac Lane: "The notion of Kan extension subsumes all the other fundamental concepts of category theory."

The presheaf category [C^op, Set] is the **free cocompletion** of C — the universal way to add all small colimits.

---

## 6 · Compositionality & Applications

Fong and Spivak frame category theory as the mathematics of compositionality. Colimits are the primary mechanism.

### Cospans

A **cospan** from A to B is A → N ← B. Two cospans compose by pushout: A → N ← B and B → M ← C yield A → P ← C where P is the pushout of N ← B → M. Associativity follows from the pasting lemma.

### Circuits

Circuits modeled as cospans of finite sets. Wiring terminals is a pushout — identified terminals become one. The colimit describes interconnection topology.

### Databases

Schema integration via pushout. Shared sub-schema Z; two schemas X, Y; integrated schema is pushout P. Universal property ensures P is the smallest consistent target.

### Topology

CW complexes built by iterated pushouts. Each cell attachment is a pushout in Top. Seifert–van Kampen computes fundamental groups of glued spaces.

---

## 7 · Board Connection

The categorical structures in this pack are not analogies for Loop MMT's architecture — they are the same structures.

### Document Merge as Pushout

Two documents sharing a common ancestor form a span: ancestor Z, documents X and Y, with morphisms encoding how each extends Z. The merged document is the pushout P.

Concretely: a lens derived from a knowledge pack (Z) is extended into a routing table section (X) and a dashboard specification (Y). The merge protocol computes the pushout — the document incorporating both extensions, identifying shared content once. The universal property guarantees P is the smallest consistent merge. Any other valid merge factors through P uniquely.

The merge protocol's "target architecture" step is colimit computation.

### Event Ledger as Directed Colimit

The event ledger's successive states form a directed diagram. The current state — derived from the full history — is its directed colimit. "Derive state, don't maintain it" = computing the colimit from the diagram.

### Reconciliation as Coequalizer

Two instances producing divergent outputs define a parallel pair. The reconciliation protocol produces the coequalizer — minimum identifications to achieve agreement.

### Universal Properties and Fix by Design

A universal property defines an object by external behavior, not internal construction. Two objects satisfying the same universal property are uniquely isomorphic. This is Fix by Design in categorical form: correctness is structural, not conventional.

| Loop MMT Structure | Categorical Concept | Mapping |
|-------------------|-------------------|---------|
| Document merge | Pushout | Shared ancestor + two extensions → merged output |
| Event ledger state | Directed colimit | Append-only history → current derived state |
| Reconciliation | Coequalizer | Two divergent readings → canonical version |
| Merge procedure | Coproduct + coequalizer | Pushout = disjoint union then identify shared parts |
| Fix by Design | Universal property | Correctness by structure, not by inspection |

---

## 8 · Historical Context

Category theory was introduced in Eilenberg and Mac Lane's 1945 paper "General Theory of Natural Equivalences" (Trans. AMS, 58, 231–294). Presented to the AMS September 8, 1942; received by editors May 15, 1945.

The motivation was formalizing "natural" constructions. To define natural transformations, they needed functors; to define functors, they needed categories. As they wrote: "The whole concept of a category is essentially an auxiliary one; our basic concepts are essentially those of a functor and of natural transformation."

Category theory extends Emmy Noether's program (Noether was Mac Lane's teacher): understand structures through their structure-preserving maps.

For ~15 years after 1945, categories were convenient language. Three developments changed this: Daniel Kan's adjoint functors (1958), Alexander Grothendieck's categorical foundations for algebraic geometry, and F. William Lawvere's categorical logic (1963).

Applied category theory — categorical modeling of real-world systems — is more recent. Fong and Spivak's "Seven Sketches in Compositionality" (2018/2019) is a landmark, demonstrating categorical models of databases, circuits, dynamical systems, and design.

---

## Duality Table

| Limit Concept | Colimit Concept |
|--------------|----------------|
| Terminal object | Initial object |
| Product | Coproduct |
| Equalizer | Coequalizer |
| Pullback (fiber product) | Pushout (amalgamated sum) |
| Inverse limit | Direct limit |
| Cone | Cocone |
| Right adjoint preserves limits | Left adjoint preserves colimits |
| Hom(A, −) preserves limits | Hom(−, A) sends colimits to limits |

---

## References

**Awodey, Steve.** *Category Theory*. 2nd ed. Oxford Logic Guides 49. Oxford University Press, 2010.

**Borceux, Francis.** *Handbook of Categorical Algebra*, Vol. 1: Basic Category Theory. Cambridge University Press, 1994.

**Eilenberg, Samuel and Saunders Mac Lane.** "General Theory of Natural Equivalences." *Transactions of the American Mathematical Society* 58 (1945): 231–294.

**Fong, Brendan and David I. Spivak.** *An Invitation to Applied Category Theory: Seven Sketches in Compositionality*. Cambridge University Press, 2019. arXiv:1803.05316.

**Leinster, Tom.** *Basic Category Theory*. Cambridge University Press, 2014. arXiv:1612.09375.

**Mac Lane, Saunders.** *Categories for the Working Mathematician*. 2nd ed. Springer, 1997.

**Marquis, Jean-Pierre.** "Category Theory." *Stanford Encyclopedia of Philosophy*. First published 1996; substantive revision 2019.

**nLab contributors.** Entries: pushout, coequalizer, natural transformation, Yoneda embedding, colimit. Accessed April 2026.

**Riehl, Emily.** *Category Theory in Context*. Dover, 2016.

---

Loop MMT™ · Multi-Module Theory · Category Theory: Colimits & Composition Knowledge Pack · v1 © 2026 Shea Gunther · CC BY-NC 4.0
