# Component-Based Design Knowledge Pack · v1

*Loop MMT™ · 9 April 2026*


> **Abstract**
>
> This pack covers how small, well-defined components compose into complex systems across architecture, software engineering, UX design, and product structure. It traces the principle from Christopher Alexander's pattern languages (1977) through the Gang of Four's composition-over-inheritance doctrine (1994) through Brad Frost's Atomic Design (2013/2016) through modern design token architectures — the subatomic layer of visual decisions that enables theming, multi-brand support, and cross-platform consistency. The Board Connections section maps this framework onto Loop MMT's own compositional hierarchy — Knowledge Packs, Framing Packs, gantries, and the Cadence product line — arguing that the methodology's product structure is itself a design system.
>
> The central thesis: **composition is not assembly. It is building complex systems from simple parts through declared interfaces, where the whole exceeds what any part could produce alone, and where no part needs to know how the whole works.**
>


## The Principle

Composition is the most consequential idea in design. More than aesthetics, more than user empathy, more than any particular style or methodology — composition is what makes complex things work without being complicated.

The idea: build complex behavior from simple, well-defined parts connected through declared interfaces. A button and a text input compose into a search form. A search form and a navigation bar compose into a header. At every level, the composed thing has capabilities that none of its parts have alone. The search form *searches*. Neither the button nor the input can search by itself.

Three related ideas that are not composition:

**Assembly** is putting pre-made things next to each other. Assembly produces a pile. Composition produces a system. The difference is interfaces — in composition, each part declares what it accepts, what it produces, and what it expects from its neighbors.

**Inheritance** is building new things by copying and modifying existing things. It seems efficient — you get all of the parent's behavior for free — but it creates tight coupling. Change the parent and every child may break. The Gang of Four, authors of the most influential software design book ever published, made this their central warning: favor composition over inheritance.

**Stacking** is placing things in proximity without interaction. The Loop MMT Framing Pack Specification draws this distinction sharply: "Composition is not stacking. It is mutual transformation." When a search input and a button compose into a search form, both change — the button becomes a *submit* button, the input becomes a *search* input. Their identities shift to serve the composed purpose. Stacking would just put them next to each other.

The principle operates across every design discipline. The vocabulary changes — patterns, objects, atoms, tokens, packs — but the structural operation is the same.


## History

### Christopher Alexander: Patterns as Composable Solutions (1964–1977)

Christopher Alexander was an architect born in Vienna in 1936, educated at Cambridge and Harvard (where he received the first PhD in architecture), who spent most of his career at Berkeley. He wanted to understand why medieval towns felt alive and modern developments felt dead. His answer, developed across *Notes on the Synthesis of Form* (1964), *A Pattern Language* (1977, with Sara Ishikawa, Murray Silverstein, and others), and *The Timeless Way of Building* (1979), was that good environments are built from *patterns*: recurring solutions to recurring problems, each adapted to its context.

*A Pattern Language* cataloged 253 patterns spanning from regional planning down to construction details. Each pattern followed a consistent format: name, problem description, solution core, and connections to related patterns. The connections were the language — patterns called upon one another, forming a network. A street café (Pattern 88) referenced activity pockets, which referenced building complex, which referenced identifiable neighborhood. You could enter the network at any point and follow the connections to build a coherent design.

Three ideas from Alexander's work matter here.

**Decomposition is the starting move.** You cannot compose what you have not decomposed. Alexander's method begins by breaking complex environments into their smallest functional problems, solving each one, then recomposing the solutions.

**Patterns are hypotheses.** Alexander was explicit: all 253 patterns are tentative, free to evolve under new evidence. He originally wanted to publish the book in a three-ring binder so users could add new patterns, but the binding proved impractical. This means the system is open — it accepts new components without requiring redesign of existing ones.

**The whole has a quality the parts do not.** Alexander called it the "Quality Without a Name" (QWAN) — an emergent sense of wholeness that appears when patterns compose correctly. You cannot find QWAN in any individual pattern. It exists only in their composition. This is a precise description of emergence — the defining property of well-composed systems.

Alexander's work was not widely adopted in architecture (it drew significant criticism for its traditionalism and prescriptiveness). It was transformatively adopted in software, through a chain of influence that reshaped an entire industry.


### The Gang of Four: Composition Formalized for Software (1987–1994)

In 1987, software engineer Ward Cunningham received a copy of *A Pattern Language* from a colleague at Tektronix in Portland, Oregon. He and Kent Beck, then at Apple Computer, recognized that Alexander's compositional framework could address recurring problems in object-oriented software design. They presented the idea at the OOPSLA conference. The reception launched a movement.

In 1994, Erich Gamma, Richard Helm, Ralph Johnson, and John Vlissides published *Design Patterns: Elements of Reusable Object-Oriented Software*. The four authors — known collectively as the Gang of Four (GoF) — cataloged 23 software design patterns in three categories: creational (how objects are made), structural (how objects compose), and behavioral (how objects communicate). The book has sold over 500,000 copies in English and thirteen other languages.

The GoF's most lasting contribution was not the 23 patterns but two principles stated in the introduction:

**"Program to an interface, not an implementation."** Do not depend on how something works internally. Depend on what it promises to do.

**"Favor object composition over class inheritance."** Do not build new things by copying and modifying existing things. Build new things by connecting small things through interfaces.

The second principle is the compositional thesis restated for software. Inheritance, the GoF argued, is "white-box reuse" — internals are visible, coupling is tight, and changes cascade unpredictably. Composition is "black-box reuse" — parts connect through interfaces, neither needs to know the other's internals. In a 2005 interview, Gamma reflected that the principle held up after a decade: "Composition has a nicer property. The coupling is reduced by just having some smaller things you plug into something bigger, and the bigger object just calls the smaller object back."

One GoF pattern deserves special attention: the **Composite** pattern. It lets you compose objects into tree structures representing part-whole hierarchies, where clients treat individual objects and compositions uniformly. A single button and a form containing twenty buttons expose the same interface. The client does not need to know whether it is talking to a leaf or a tree. This is the structural blueprint for every component tree in modern UI development.

The ripple effects extended far beyond design patterns. Cunningham created the first wiki (WikiWikiWeb) to document patterns collaboratively. Beck and Cunningham pioneered Extreme Programming. Both contributed to the Agile Manifesto. Alexander — an architect whose work was in the physical world of buildings and towns — had catalyzed a revolution in how software was designed, built, and managed.


### Brad Frost: Atomic Design for UI (2013–2016)

By the early 2010s, component thinking permeated front-end web development. Twitter released Bootstrap in 2011, giving developers pre-built component libraries. Foundation, Bourbon, and other frameworks followed. Anna Debenham wrote about living style guides. Mailchimp published their UI Patterns. But there was no unified mental model for how components at different scales related to each other — no equivalent of Alexander's pattern network for user interfaces.

Brad Frost provided one. In 2013 he published a blog post, expanded into the book *Atomic Design* (2016, self-published in Pittsburgh), that applied a chemistry metaphor to UI design. Five levels:

**Atoms** — the smallest functional building blocks. Buttons, labels, inputs, color swatches, font definitions. In HTML, they are basic elements that cannot be broken down further without ceasing to function.

**Molecules** — simple groups of atoms functioning together. A label, text input, and button compose into a search form. Each molecule embodies the single responsibility principle: it does one thing well. The molecule can do something none of its atoms can do alone.

**Organisms** — complex UI components composed of molecules and/or atoms and/or other organisms. A header containing a logo (atom), navigation (molecule), and search form (molecule) is an organism. Organisms begin to give the interface its character.

**Templates** — page-level structures arranging organisms into layouts. They are the wireframe: structural skeleton showing how content zones relate, without real content.

**Pages** — specific instances of templates populated with real content. The final test: does the system work when actual data fills it? Pages reveal problems that templates hide — the headline that is nineteen words long, the user avatar that is missing, the edge case that breaks the card layout.

Frost's most important contribution was the directive: **"Build systems, not pages."** Legacy web design treated each page as a separate problem. Atomic Design treated every page as a composition of shared components. This is the same inversion Alexander made: shift from designing the product to designing the system that generates the product.

Frost also stressed that Atomic Design is not a linear process. You do not design all atoms, then all molecules, then all organisms. You work at all five levels simultaneously, moving between abstract and concrete as the problem demands. The five levels are a mental model, not a production sequence.


## Design Tokens: The Subatomic Layer

Below atoms, there is something smaller. Design tokens are named variables that store visual design decisions: colors, spacing, typography, shadows, motion timing. Salesforce's Lightning Design System originated the term, describing tokens as "the visual design atoms of the design system."

Tokens solve the problem of *decision propagation*. When a designer decides the primary brand color is #0F62FE, that decision needs to reach every button, link, and active state across web, iOS, Android, and documentation. Without tokens, that decision is a hex code duplicated across hundreds of files. With tokens, it is a single named variable referenced everywhere and defined once.

The dominant architecture organizes tokens in three layers:

**Primitive tokens** store raw values: `blue-500: #0F62FE`, `spacing-4: 16px`. They define the base palette — the finite set of values selected from the infinite space of possibilities.

**Semantic tokens** assign meaning to primitives: `color-background-primary → blue-500`. They separate what a value *is for* from what a value *is*. This means you can swap the primitive without updating every component.

**Component tokens** encapsulate decisions inside specific components: `button-background → color-background-primary`. They are private to the component. This layer makes components self-contained.

The three layers compose: a primitive feeds a semantic token which feeds a component token which produces a rendered pixel. Change a primitive and the change cascades through the entire system automatically. This is composition applied to visual decisions rather than UI elements — the same structural operation on a different material.

The major commercial design systems all use this architecture. Google's Material 3 pioneered mode-aware semantic tokens. Adobe's Spectrum emphasizes accessibility and localization. Microsoft's Fluent excels at high-contrast mode switching. IBM's Carbon provides granular audit trails. Salesforce's Lightning originated the terminology. The implementations vary; the three-layer compositional structure is shared.

Token architecture also enables multi-brand theming. If a product serves multiple brands — the way a hotel system might serve distinct luxury, business, and economy properties — each brand defines its own primitive tokens while sharing semantic and component layers. The components stay the same. The tokens change. Composition over inheritance, applied to visual identity.


## The Full Stack: What a Design System Contains

The terms "design system," "component library," "pattern library," and "style guide" get used interchangeably. They refer to different layers of the same compositional hierarchy.

A **style guide** documents visual decisions: color codes, typography scales, spacing rules, usage guidance. It is reference documentation for the token layer.

A **component library** is a collection of reusable UI elements built in code. Components are prescriptive — they look and behave in a defined way. In Frost's hierarchy, a component library contains atoms, molecules, and organisms.

A **pattern library** is a collection of solutions to recurring UX problems. Patterns are more abstract than components. A component is a search bar. A pattern is "how users search for content in a large catalog" — which might involve a search bar, filter panels, result cards, and pagination composed together for a specific purpose. Components are things. Patterns are guidance about how to use things.

A **design system** contains all of the above — tokens, assets, components, patterns, documentation — plus governance: contribution guidelines, review processes, a team that maintains the system. The crucial difference is governance. A component library can be used however the consumer chooses. A design system has rules. If you want to change a component or add a pattern, you follow the governance procedures.

This is why open-source component libraries like MUI or React-Bootstrap, despite having extensive documentation, are not design systems. They are building materials. A design system is building materials plus a building code.

Dave House, who worked on the GOV.UK Design System, proposed a useful taxonomy of increasing abstraction:

**Components** are agnostic, reusable objects with defined interfaces. **UI Patterns** bridge components and behavioral guidance. **Behavioral Patterns** document processes and user flows. **Service Patterns** are guiding frameworks for common journeys (e.g., "applying for something"). **Feature Modules** are self-contained units that deliver entire features — import the address-lookup module and you get the full capability.

As you move up this hierarchy, you move from coded deliverables to conceptual guidance. Components can be measured and tested. Service patterns can only be evaluated. This gradient — from concrete and testable to abstract and evaluative — is a general property of compositional systems.


## Composition Mechanics

### Interface Contracts

Every composable unit needs an interface declaring what it accepts, what it produces, and what invariants it maintains. In software, interfaces are formal (type signatures, API contracts). In design systems, they are semi-formal (props, slots, variants, design tokens). In Loop MMT's Framing Pack system, they are declared in two sections: Composition Interface (what bonds, what repels) and Composition Modifiers (what changes under combination).

Interface quality determines composition quality. Too narrow prevents useful combinations. Too wide permits incoherent ones.

### The Composite Pattern in Practice

The GoF's Composite pattern is the structural basis for component trees. It defines a tree where each node is either a leaf (individual component) or a branch (container of components). Both expose the same interface. A single button and a form containing buttons respond to the same operations. The client does not know — and does not need to know — whether it is interacting with one element or a tree of them.

This uniformity enables building an entire page from a single compositional grammar. The page does not care whether its header is a lone organism or a nested tree of molecules and atoms. It just needs the header to satisfy the header interface.

### Mutual Transformation

When things compose well, both parts change. The Framing Pack Spec generalizes this: composition is mutual transformation. A cat lens composed with a rock lens produces a third perspective that carries properties of both but is identical to neither. In UI terms, a text input composed into a search form is no longer a generic text input — it is a search input, with different affordances, different validation, different user expectations.

This distinguishes composition from stacking (proximity without interaction) and from aggregation (collection without transformation).

### Depth Limits

Composition has practical depth limits. The Framing Pack Spec observes that two lenses compose reliably, three may work if compatible, and beyond three, coherence degrades. This is general to compositional systems: Atomic Design works with about five levels. Token architecture standardizes at three layers. Deeply nested Composite trees become hard to debug.

Each additional level adds analytical power but also cognitive cost. The practical ceiling is wherever cost exceeds benefit — and that ceiling is lower than most designers expect.


## When Composition Fails

**The Bootstrap problem.** When everyone composes from the same library without customization, everything looks the same. Frost observed this with his sci-fi metaphor: in the future, everyone dresses in identical jumpsuits. Shared components ensure consistency — but consistency without identity is uniformity. The solution is theming at the token level or custom organisms that carry brand identity.

**Over-abstraction.** A button decomposed into a "pressable surface," a "label renderer," and a "state manager" is not more useful than a button. It is three things to understand instead of one. The test: if the decomposed parts are never used independently, the decomposition serves nobody. Atoms should be the smallest *functional* unit, not the smallest *possible* unit.

**Combinatorial explosion.** Ten components with three variants each yield thirty variants. Fifteen patterns with two variants each yield thirty patterns. Without governance — a team deciding which combinations are sanctioned — the system becomes an unnavigable parts catalog.

**The abstraction-specificity trade-off.** A highly abstract card component can display a product, a person, or an article. But abstraction means the consumer is always configuring, never just using. Feature modules sacrifice abstraction for specificity: they give you the address-lookup feature, not the parts to build one.

**Premature composition.** Composing before understanding the problem locks you into interfaces that may not serve actual use cases. Alexander's method starts with observation — understanding the recurring problem — before proposing a pattern. Building a component library before understanding the product is answering a question you have not yet heard.


## Board Connections

The Loop MMT product hierarchy maps onto the design system framework with enough structural precision to be called isomorphic, not merely analogous.

| Design System Layer | Loop MMT Equivalent | Why the Mapping Holds |
| --- | --- | --- |
| **Design tokens** (primitives) | FBD principles, session cycle steps, the five Cadence practices | These are the irreducible behavioral primitives — they cannot be decomposed further without losing enforcement power. FBD-1 through FBD-5+ function exactly like tokens: named, immutable design decisions referenced everywhere. |
| **Atoms** (smallest functional unit) | Individual Knowledge Packs, individual protocol documents | Each does one thing well. A Knowledge Pack covers a domain. A protocol governs a process. Complete, self-contained, reusable. |
| **Molecules** (simple functional groups) | Conversation Loading Packs (bundles of documents selected for a specific AI session) | A loading pack is a molecule: multiple atoms (knowledge packs, protocol docs, context files) composed for a single purpose — equipping one conversation. |
| **Organisms** (complex components with internal structure) | Framing Packs | Twelve required sections, declared composition interfaces, mutual transformation under combination. A Framing Pack is a complex component with rich internal structure and formal composability rules. |
| **Templates** (structural scaffolds) | Gantries | Domain-specific scaffolds that hold AI knowledge in the correct position. Include their own verification structure. The gantry shapes how the AI fills in the content — which is exactly what a template does. |
| **Pages** (instantiated products with real content) | "Cadence for [Domain]" bundles | Specific instances of the methodology with real domain content. Cadence for Thesis Writing is a template populated with domain-specific packs, gantries, and verification gates. |
| **Design system governance** | Beta-test gate, board approval process | The board's rule that no untested gantry ships is governance: contribution guidelines preventing incoherent additions to the system. |
| **Multi-brand theming** | Cadence weight classes (Light/Standard/Heavy) | Three configurations of the same system, differentiated at the token level (which documents, how much overhead). The components (the five practices) stay the same. |

The compositional structure extends further. The free-base-plus-paid-domain-packs business model is Pareto-optimal bundling — selecting well-distributed points on the segment-coverage vs. complexity Pareto front. Each bundle represents a point on the front where no other bundle strictly dominates it. The number and position of bundles correspond to covering the customer space without overwhelming it with choices.

The Loop MMT document corpus itself functions as a pattern language in Alexander's sense. Documents call upon one another: the Interaction Guide references the Handoff Standard, which references the Self-Review Protocol, which references the Coding Standards. You can enter the corpus at any point and follow the references to build a coherent understanding. The corpus has the network property that Alexander considered essential — it is not a list of documents but a web of interconnected solutions.

And the deepest structural parallel: Alexander's patterns are hypotheses. They evolve. Loop MMT's documents follow append-only identity — historical content is locked, evolution happens through accumulated session notes as permanent append entries. The system accepts new components (new packs, new protocols, new Framing Pack lenses) without requiring redesign of existing ones. The corpus, like Alexander's pattern language and like a well-designed component library, is an open compositional system.


## References

| Source | Used For |
| --- | --- |
| Alexander, Christopher, Sara Ishikawa, and Murray Silverstein. *A Pattern Language: Towns, Buildings, Construction*. Oxford University Press, 1977. | History, The Principle |
| Alexander, Christopher. *Notes on the Synthesis of Form*. Harvard University Press, 1964. | History |
| Alexander, Christopher. *The Timeless Way of Building*. Oxford University Press, 1979. | History |
| Gamma, Erich, Richard Helm, Ralph Johnson, and John Vlissides. *Design Patterns: Elements of Reusable Object-Oriented Software*. Addison-Wesley, 1994 (copyright 1995). | History, Composition Mechanics |
| Gamma, Erich. Interview with Bill Venners, "Design Principles from Design Patterns." artima.com, 2005. | History |
| Frost, Brad. *Atomic Design*. Self-published, 2016. atomicdesign.bradfrost.com. | History, Design Tokens, When Composition Fails |
| Salesforce. "Design Tokens." Lightning Design System documentation. lightningdesignsystem.com. | Design Tokens |
| Bellenger, Luis. "Design Token-Based UI Architecture." martinfowler.com, 2024. | Design Tokens |
| Curtis, Nathan. "Naming Tokens in Design Systems" and "Tokens in Design Systems." EightShapes/Medium, 2017–2020. | Design Tokens |
| House, Dave. "Patterns in Design Systems." Medium, 2024. | The Full Stack |
| Yllobre, Carlos. "Understanding the Parts of a Design System." Prototypr, 2023. | The Full Stack |
| Mehaffy, Michael. "The Pattern Technology of Christopher Alexander." *Metropolis*, 2011. | History |
| Wikipedia. "A Pattern Language," "Pattern language," "Design Patterns." Accessed April 2026. | History, fact verification |
| Loop MMT corpus: Framing Pack Spec v1, Cadence v3, White Paper 3 v2, Multi-Objective Optimization / Pareto Theory KP v1, Good Design KP v1. | Board Connections |
| Dovey, Kim. "The Pattern Language and its Enemies." *Design Studies* 11(1), 1990. | History (criticism) |
