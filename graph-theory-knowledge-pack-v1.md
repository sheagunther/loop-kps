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
Graph Theory Knowledge Pack
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
-   [2 · Connectivity](#ch-connectivity)
-   [3 · Directed Graphs](#ch-digraphs)
-   [4 · Trees](#ch-trees)
-   [5 · Shortest Paths](#ch-shortest)
-   [6 · Euler & Hamilton](#ch-euler-hamilton)
-   [7 · Planarity](#ch-planarity)
-   [8 · Graph Coloring](#ch-coloring)
-   [9 · Matchings](#ch-matchings)
-   [10 · Network Flow](#ch-flow)
-   [11 · Spectral Methods](#ch-spectral)
-   [12 · Additional Topics](#ch-additional)
-   [13 · Algorithm Reference](#ch-algo-ref)
-   [14 · Theorem Reference](#ch-theorem-ref)
-   [References](#ch-refs)

::: {.content role="main"}
::: {#ch-abstract .abstract-box}
::: abstract-label
About This Document
:::

This is a reference document on graph theory, designed to be loaded into AI advisory conversations. It provides precise definitions, theorem statements, algorithm descriptions, and the relationships between concepts that advisors need to help the operator work through graph theory problems. It is comprehensive in scope but concise in treatment --- theorems are stated without proof, algorithms are described by purpose, complexity, and limitations rather than pseudocode.

All theorems are attributed to their original authors. The document covers 22 major theorems, 16 algorithms, and draws on 36 sources. Full citations appear in the References section.
:::

::: {#ch-foundations .chapter}
::: chapter-number
Section 1
:::

::: chapter-title
Foundations
:::

::: {#s-graph-def .section}
::: section-title
What is a Graph
:::

A **graph** G = (V, E) consists of a finite set V of **vertices** (also called nodes) and a set E of **edges** connecting pairs of vertices. In a **simple graph**, E is a set of unordered pairs {u, v} with u ≠ v --- no self-loops, no duplicate edges. A **multigraph** allows multiple edges between the same pair and may allow self-loops. A **weighted graph** assigns a numerical weight to each edge. A **directed graph** (digraph) has ordered pairs (u, v) as edges, giving each edge a direction. A **mixed graph** has both directed and undirected edges.
:::

::: {#s-vocab .section}
::: section-title
Basic Vocabulary
:::

A vertex v is **incident** with an edge e if v is an endpoint of e. Two vertices are **adjacent** (neighbors) if an edge connects them, written u \~ v. The **neighborhood** N(v) of a vertex is the set of its neighbors. The **degree** d(v) = \|N(v)\| counts the number of neighbors. An **isolated vertex** has degree 0.

A **subgraph** of G is a graph whose vertices and edges are subsets of those of G. An **induced subgraph** G\[S\] for S ⊆ V includes all edges of G between vertices in S. Two graphs are **isomorphic** if there exists a bijection between their vertex sets that preserves adjacency.
:::

::: {#s-handshaking .section}
::: section-title
Handshaking Lemma
:::

**Theorem (Euler, 1736):** For any graph G = (V, E), the sum of all vertex degrees equals twice the number of edges: ∑ d(v) = 2\|E\|. This follows from double-counting: each edge contributes exactly 1 to the degree of each of its two endpoints.

**Corollary:** Every graph has an even number of odd-degree vertices.

Double-counting is a fundamental proof technique in graph theory. Whenever you need to relate local properties (vertex degrees) to global properties (edge count), the handshaking lemma is the first tool to reach for.
:::

::: {#s-bipartite .section}
::: section-title
Bipartite Graphs
:::

A graph is **bipartite** if its vertices can be partitioned into two disjoint sets X and Y such that every edge connects a vertex in X to a vertex in Y. Equivalently, a graph is bipartite if and only if it contains no odd-length cycle. Equivalently, it is 2-colorable. Bipartiteness can be tested in O(V + E) time using BFS.
:::

::: {#s-families .section}
::: section-title
Common Graph Families
:::

  Name                 Notation   Description                                                  Key Property
  -------------------- ---------- ------------------------------------------------------------ ----------------------------------------
  Complete graph       K~n~       n vertices, every pair adjacent                              n(n−1)/2 edges; (n−1)-regular
  Complete bipartite   K~m,n~     Parts of size m and n, all cross-edges                       mn edges
  Path                 P~n~       n vertices in a line                                         n−1 edges; tree
  Cycle                C~n~       n vertices in a ring                                         n edges; 2-regular
  Petersen graph       ---        10 vertices, 15 edges                                        3-regular; not Hamiltonian; not planar
  Hypercube            Q~n~       2^n^ vertices (binary strings), edge iff differ in one bit   n-regular; bipartite; Hamiltonian
:::

::: {#s-traversal .section}
::: section-title
Graph Traversal: BFS and DFS
:::

**Breadth-First Search (BFS)** explores vertices layer by layer from a source. It discovers shortest paths in unweighted graphs, tests bipartiteness, and finds connected components. Time: O(V + E).

**Depth-First Search (DFS)** explores as deep as possible before backtracking. It detects cycles, computes topological orderings of DAGs, finds articulation points and bridges, and is the basis for Tarjan\'s SCC algorithm. DFS classifies edges as tree edges, back edges (indicating cycles), forward edges, and cross edges. Time: O(V + E).

::: {.callout .tip}
::: callout-label
First move
:::

For almost any graph problem, the first question is: what does BFS or DFS reveal about the structure? Run traversal first, then decide what specialized algorithm to apply.
:::
:::
:::

::: {#ch-connectivity .chapter}
::: chapter-number
Section 2
:::

::: chapter-title
Connectivity
:::

::: {#s-walks .section}
::: section-title
Walks, Trails, Paths
:::

A **walk** in a graph is a sequence of vertices v₁, v₂, ..., v_k where consecutive vertices are adjacent. Edges and vertices may repeat. A **trail** is a walk with no repeated edges. A **path** is a walk with no repeated vertices. A **closed walk** starts and ends at the same vertex; a **cycle** is a closed path (no repeated vertices except start = end, and length ≥ 3).

These distinctions matter. Euler problems concern trails (edges visited once). Hamilton problems concern paths (vertices visited once).
:::

::: {#s-conn-defs .section}
::: section-title
Connectivity Measures
:::

A graph is **connected** if a path exists between every pair of vertices. A **connected component** is a maximal connected subgraph. A **cut vertex** (articulation point) is a vertex whose removal increases the number of components. A **bridge** is an edge whose removal increases the number of components.

The **vertex connectivity** κ(G) is the minimum number of vertices whose removal disconnects G (or reduces it to a single vertex). The **edge connectivity** λ(G) is the minimum number of edges whose removal disconnects G.

**Whitney\'s Inequality:** κ(G) ≤ λ(G) ≤ δ(G), where δ(G) is the minimum vertex degree. A graph is **k-connected** if κ(G) ≥ k, meaning it stays connected after removing any k−1 vertices. It is **k-edge-connected** if λ(G) ≥ k.
:::

::: {#s-menger .section}
::: section-title
Menger\'s Theorem (1927)
:::

**Vertex version:** For non-adjacent vertices u, v in a finite graph, the minimum size of a u-v vertex separator equals the maximum number of pairwise internally vertex-disjoint u-v paths.

**Edge version:** For distinct vertices u, v, the minimum size of a u-v edge cut equals the maximum number of pairwise edge-disjoint u-v paths.

**Global version:** A graph is k-connected if and only if every pair of vertices has at least k internally disjoint paths between them.

::: {.callout .key}
::: callout-label
The connectivity duality
:::

Menger\'s theorem is the foundational min-max result in graph theory. It says that the obstacle to connectivity (minimum cut) is exactly dual to the resource for connectivity (maximum disjoint paths). This same duality pattern appears in Hall\'s marriage theorem, König\'s theorem, and the max-flow min-cut theorem. Recognizing this pattern is the key to solving many graph problems.
:::
:::
:::

::: {#ch-digraphs .chapter}
::: chapter-number
Section 3
:::

::: chapter-title
Directed Graphs
:::

A **directed graph** (digraph) G = (V, E) has edges as ordered pairs (u, v), meaning the edge goes from u to v. The **in-degree** d⁻(v) counts edges into v; the **out-degree** d⁺(v) counts edges out of v. The **underlying graph** is obtained by ignoring edge directions.

::: {#s-strong-conn .section}
::: section-title
Strong and Weak Connectivity
:::

A digraph is **weakly connected** if its underlying undirected graph is connected. It is **strongly connected** if for every pair of vertices u, v, there exist directed paths from u to v and from v to u. A **strongly connected component** (SCC) is a maximal strongly connected subgraph.

**Tarjan\'s algorithm** finds all SCCs in O(V + E) using a single DFS pass with a stack. The **condensation** of a digraph replaces each SCC with a single vertex, producing a DAG.
:::

::: {#s-dags .section}
::: section-title
DAGs and Topological Order
:::

A **directed acyclic graph (DAG)** contains no directed cycles. A digraph is a DAG if and only if it admits a **topological ordering** --- a linear ordering of vertices such that for every edge (u, v), u precedes v. A topological ordering can be computed in O(V + E) via DFS (reverse of finish times) or by repeatedly removing vertices with in-degree 0.

DAGs model dependencies: tasks, prerequisites, build systems, causal relationships.
:::

::: {#s-tournaments .section}
::: section-title
Tournaments
:::

A **tournament** is a complete directed graph --- every pair of vertices has exactly one directed edge between them. Every tournament has a Hamiltonian path (this can be proved by induction). Tournaments model round-robin competitions.
:::
:::

::: {#ch-trees .chapter}
::: chapter-number
Section 4
:::

::: chapter-title
Trees
:::

::: {#s-tree-def .section}
::: section-title
Definition and Characterizations
:::

A **tree** is a connected acyclic graph. A **forest** is an acyclic graph (a disjoint union of trees). A **leaf** is a vertex of degree 1. Every tree with at least two vertices has at least two leaves.

::: {.callout .key}
::: callout-label
The tree equivalence theorem
:::

For a graph T with n vertices, the following are equivalent: (1) T is a tree (connected and acyclic). (2) T is connected with exactly n−1 edges. (3) T is acyclic with exactly n−1 edges. (4) T is connected, and removing any edge disconnects it. (5) T is acyclic, and adding any edge creates exactly one cycle. (6) There is exactly one path between any two vertices. Any one of these properties can serve as the definition --- the others follow.
:::
:::

::: {#s-spanning .section}
::: section-title
Spanning Trees and MST
:::

A **spanning tree** of a connected graph G is a subgraph that is a tree containing all vertices of G. Every connected graph has at least one spanning tree.

A **minimum spanning tree (MST)** of a weighted connected graph is a spanning tree with minimum total edge weight. Key algorithms:

  Algorithm        Strategy                                                                             Complexity       Best For
  ---------------- ------------------------------------------------------------------------------------ ---------------- --------------------------
  Kruskal (1956)   Sort edges by weight; add greedily, skip if creates cycle (union-find)               O(E log E)       Sparse graphs
  Prim (1957)      Grow tree from a vertex; always add cheapest edge to a new vertex (priority queue)   O(E + V log V)   Dense graphs
  Borůvka (1926)   Each component selects cheapest outgoing edge simultaneously; repeat                 O(E log V)       Parallel implementations

**Cayley\'s Formula:** The number of distinct labeled trees on n vertices is n^n−2^.

**Matrix Tree Theorem (Kirchhoff, 1847):** The number of spanning trees of a graph equals any cofactor of its Laplacian matrix L = D − A.
:::
:::

::: {#ch-shortest .chapter}
::: chapter-number
Section 5
:::

::: chapter-title
Shortest Paths
:::

The **shortest path** between two vertices in a weighted graph is the path with minimum total edge weight. Two problem variants: **single-source shortest paths (SSSP)** finds shortest paths from one source to all other vertices; **all-pairs shortest paths (APSP)** finds shortest paths between every pair.

::: {#s-sp-algos .section}
::: section-title
Algorithm Selection
:::

  Condition                                Algorithm                       Complexity
  ---------------------------------------- ------------------------------- ------------------
  Unweighted SSSP                          BFS                             O(V + E)
  Non-negative weights, SSSP               Dijkstra                        O(E + V log V)
  Negative weights allowed, SSSP           Bellman-Ford                    O(VE)
  Need to detect negative cycles           Bellman-Ford                    O(VE)
  APSP, dense graph                        Floyd-Warshall                  O(V³)
  APSP, sparse graph, possible negatives   Johnson                         O(V² log V + VE)
  DAG                                      Topological sort + relaxation   O(V + E)
:::

::: {#s-dijkstra .section}
::: section-title
Dijkstra\'s Algorithm (1959)
:::

Greedy algorithm. Maintains a set of vertices whose final shortest-path distance is known. At each step, selects the unvisited vertex with smallest tentative distance, marks it as visited, and relaxes its outgoing edges. Requires non-negative edge weights.

::: {.callout .warn}
::: callout-label
Negative weights
:::

Dijkstra\'s algorithm is not correct when negative-weight edges are present. It may produce incorrect shortest-path distances because the greedy assumption --- that a visited vertex\'s distance is final --- breaks when a later path through a negative edge could produce a shorter route. Use Bellman-Ford instead.
:::
:::

::: {#s-bellman-ford .section}
::: section-title
Bellman-Ford Algorithm (1958)
:::

Relaxes all edges V−1 times. After V−1 iterations, all shortest-path distances are finalized (assuming no negative cycles). A V-th iteration that still finds an improvement indicates a negative-weight cycle reachable from the source.
:::

::: {#s-floyd .section}
::: section-title
Floyd-Warshall (1962)
:::

Dynamic programming over intermediate vertices. For each triple (i, k, j), checks if routing through k improves the i→j distance. Handles negative weights but not negative cycles. Time: O(V³), space: O(V²).
:::
:::

::: {#ch-euler-hamilton .chapter}
::: chapter-number
Section 6
:::

::: chapter-title
Eulerian and Hamiltonian Graphs
:::

::: {#s-euler .section}
::: section-title
Eulerian Graphs
:::

**Euler\'s Theorem:** A connected graph has an **Eulerian circuit** (a closed trail visiting every edge exactly once) if and only if every vertex has even degree. It has an **Eulerian trail** (not necessarily closed) if and only if it has exactly zero or two vertices of odd degree.

**Directed version (König):** A directed graph whose underlying undirected graph is connected has an Eulerian circuit if and only if every vertex has in-degree equal to out-degree. (For a balanced digraph --- one where in-degree equals out-degree at every vertex --- weak connectivity implies strong connectivity, so the circuit traverses the entire graph.)

**Hierholzer\'s algorithm** constructs an Eulerian circuit in O(E) time.
:::

::: {#s-hamilton .section}
::: section-title
Hamiltonian Graphs
:::

A graph has a **Hamiltonian cycle** if there exists a cycle visiting every vertex exactly once. Unlike the Eulerian case, there is no known simple necessary and sufficient condition --- determining whether a graph is Hamiltonian is NP-complete.

**Sufficient conditions:** Dirac\'s theorem (1952) --- if every vertex has degree ≥ n/2, then G has a Hamiltonian cycle. Ore\'s theorem (1960) --- if d(u) + d(v) ≥ n for every pair of non-adjacent vertices u, v, then G has a Hamiltonian cycle. Ore\'s theorem generalizes Dirac\'s.
:::

::: {.callout .key}
::: callout-label
Euler vs. Hamilton
:::

Euler: visits every *edge* exactly once. Polynomial --- check vertex degrees. Hamilton: visits every *vertex* exactly once. NP-complete --- no simple characterization. This is one of the sharpest tractability boundaries in graph theory: changing \"edge\" to \"vertex\" takes us from O(E) to NP-complete.
:::
:::

::: {#ch-planarity .chapter}
::: chapter-number
Section 7
:::

::: chapter-title
Planarity
:::

A graph is **planar** if it can be drawn in the plane with no edge crossings. A particular crossing-free drawing is a **plane graph**. The connected regions of the plane created by a plane graph are called **faces**, including one unbounded exterior face.

::: {#s-euler-formula .section}
::: section-title
Euler\'s Formula (1752)
:::

For a connected plane graph with v vertices, e edges, and f faces: **v − e + f = 2**.

**Corollaries** (for simple connected planar graphs with v ≥ 3): e ≤ 3v − 6. If the graph is triangle-free: e ≤ 2v − 4. Every planar graph has a vertex of degree ≤ 5. The average degree is strictly less than 6.

These corollaries are the primary tools for proving a graph is NOT planar: if the edge count exceeds the bound, the graph cannot be planar.
:::

::: {#s-kuratowski .section}
::: section-title
Characterization Theorems
:::

**Kuratowski\'s Theorem (1930):** A graph is planar if and only if it contains no subgraph that is a subdivision of K₅ or K₃,₃. (A subdivision replaces edges with paths.)

**Wagner\'s Theorem (1937):** A graph is planar if and only if it has no K₅ or K₃,₃ as a minor. (A minor is obtained by deleting vertices/edges and contracting edges.)

Planarity can be tested in O(V) time using algorithms by Hopcroft-Tarjan (1974) or Boyer-Myrvold (2004).
:::

::: {#s-four-color .section}
::: section-title
Coloring Planar Graphs
:::

**Four Color Theorem (Appel & Haken, 1976):** Every planar graph is 4-colorable. The proof required computer verification of 1,936 configurations; a simpler proof checking 633 configurations was given by Robertson, Seymour, Sanders, and Thomas in 1997.

The **Five Color Theorem** (Heawood, 1890) is easier to prove and states every planar graph is 5-colorable.
:::

::: {#s-duals .section}
::: section-title
Dual Graphs and the Robertson-Seymour Theorem
:::

Given a plane graph G, its **dual graph** G\* has a vertex for each face of G and an edge for each edge of G separating two faces. The dual of a planar graph is planar.

The **Robertson-Seymour Theorem** (proved across a series of 23 papers, 1983--2004) states that every minor-closed class of graphs is characterized by a finite set of forbidden minors. This deep result generalizes Wagner\'s theorem.
:::
:::

::: {#ch-coloring .chapter}
::: chapter-number
Section 8
:::

::: chapter-title
Graph Coloring
:::

::: {#s-vertex-color .section}
::: section-title
Vertex Coloring
:::

A **proper vertex coloring** assigns colors to vertices so no two adjacent vertices share a color. The **chromatic number** χ(G) is the minimum number of colors needed. Basic facts: χ(G) = 1 iff G is edgeless; χ(G) = 2 iff G is bipartite; χ(G) ≤ Δ(G) + 1 always (greedy algorithm).
:::

::: {#s-brooks-vizing .section}
::: section-title
Brooks\' and Vizing\'s Theorems
:::

**Brooks\' Theorem (1941):** For a connected graph that is neither a complete graph nor an odd cycle, χ(G) ≤ Δ(G). This improves the greedy bound by 1 for all but two families.

**Edge coloring:** The **chromatic index** χ\'(G) is the minimum number of colors to color edges so no two edges sharing a vertex have the same color.

**Vizing\'s Theorem (1964):** For any simple graph, Δ(G) ≤ χ\'(G) ≤ Δ(G) + 1. Graphs achieving χ\' = Δ are **Class 1**; those requiring Δ + 1 are **Class 2**.

**König\'s Line Coloring Theorem (1916):** Every bipartite graph is Class 1 --- χ\'(G) = Δ(G).

::: {.callout .key}
::: callout-label
Brooks and Vizing --- the bound-improvement pair
:::

Brooks improves the vertex coloring bound from Δ+1 to Δ (exceptions: K_n, odd cycles). Vizing pins the edge coloring bound to either Δ or Δ+1 (no exceptions, but determining which class is NP-complete in general). For bipartite graphs, König settles the edge coloring question completely.
:::
:::

::: {#s-chromatic-poly .section}
::: section-title
Chromatic Polynomial and Perfect Graphs
:::

The **chromatic polynomial** P(G, k) counts the number of proper vertex colorings using at most k colors. Example: P(K_n, k) = k(k−1)(k−2)···(k−n+1).

A graph is **perfect** if for every induced subgraph H, χ(H) = ω(H) (chromatic number equals clique number). The **Strong Perfect Graph Theorem** (Chudnovsky et al., 2006): A graph is perfect if and only if neither it nor its complement contains an odd cycle of length ≥ 5 as an induced subgraph. All bipartite graphs are perfect.
:::
:::

::: {#ch-matchings .chapter}
::: chapter-number
Section 9
:::

::: chapter-title
Matchings
:::

::: {#s-match-def .section}
::: section-title
Definitions
:::

A **matching** M is a set of pairwise non-adjacent edges --- no two share a vertex. A vertex incident to an edge in M is **matched**; otherwise **unmatched**. A **maximal** matching cannot be extended. A **maximum** matching has the most edges possible. A **perfect** matching matches every vertex.

::: {.callout .warn}
::: callout-label
Maximal ≠ Maximum
:::

A maximal matching is one where no edge can be added. A maximum matching is one with the most edges. Every maximum matching is maximal, but not vice versa. A maximal matching can be as small as half the size of a maximum matching.
:::

**Berge\'s Theorem (1957):** A matching M is maximum if and only if there is no M-augmenting path (a path whose edges alternate between not-in-M and in-M, starting and ending at unmatched vertices).
:::

::: {#s-hall-konig .section}
::: section-title
Hall\'s and König\'s Theorems
:::

**Hall\'s Marriage Theorem (1935):** A bipartite graph G = (X ∪ Y, E) has a matching covering all of X if and only if for every S ⊆ X, \|N(S)\| ≥ \|S\| (Hall\'s condition). Corollary: every k-regular bipartite graph has a perfect matching.

**König\'s Theorem (1931):** In a bipartite graph, the maximum matching size equals the minimum vertex cover size. A **vertex cover** is a set of vertices touching every edge.

**Tutte\'s Theorem (1947):** A graph G has a perfect matching if and only if for every S ⊆ V, the number of odd components of G − S is at most \|S\|. This generalizes Hall\'s theorem to non-bipartite graphs.
:::

::: {#s-match-algo .section}
::: section-title
Algorithms
:::

  Algorithm                         Setting                                                  Complexity
  --------------------------------- -------------------------------------------------------- ------------
  Hopcroft-Karp (1973)              Maximum bipartite matching                               O(√V · E)
  Edmonds\' Blossom (1965)          Maximum matching, general graphs                         O(V² · E)
  Hungarian / Kuhn-Munkres (1955)   Minimum-weight bipartite matching (assignment problem)   O(V³)
:::

::: {.callout .key}
::: callout-label
The equivalence web
:::

Hall\'s marriage theorem, König\'s theorem, Menger\'s theorem, Dilworth\'s theorem (on partially ordered sets), and the max-flow min-cut theorem are all logically equivalent --- each can be derived from any other. When facing a problem, recognizing it as an instance of any one of these results lets you apply whichever formulation is most natural.
:::
:::

::: {#ch-flow .chapter}
::: chapter-number
Section 10
:::

::: chapter-title
Network Flow
:::

::: {#s-flow-def .section}
::: section-title
Flow Networks
:::

A **flow network** is a directed graph G = (V, E) with a **source** s and **sink** t, and a capacity function c: E → ℝ⁺. A **flow** f assigns non-negative values to edges satisfying: (1) capacity constraint --- f(e) ≤ c(e) for all edges, and (2) conservation --- flow into each non-source, non-sink vertex equals flow out. The **value** \|f\| is the total flow out of s.

The **residual graph** G_f has edges with remaining capacity (forward edges with c(e) − f(e) \> 0 and backward edges with f(e) \> 0). An **augmenting path** is an s-t path in G_f.
:::

::: {#s-maxflow .section}
::: section-title
Max-Flow Min-Cut Theorem (Ford & Fulkerson, 1956)
:::

An **s-t cut** partitions V into S (containing s) and T (containing t). The cut\'s **capacity** is the sum of capacities of edges from S to T. The theorem: in any flow network, the maximum flow value equals the minimum cut capacity. Equivalently, a flow is maximum if and only if its residual graph has no augmenting path.

This is the \"master theorem\" of the equivalence web: it generalizes Menger\'s theorem (unit capacities give disjoint paths), which in turn implies Hall\'s and König\'s theorems.
:::

::: {#s-flow-algos .section}
::: section-title
Algorithms
:::

  Algorithm               Augmenting Path Strategy       Complexity
  ----------------------- ------------------------------ ----------------------------------------------
  Ford-Fulkerson (1956)   Any path (DFS)                 O(E · \|f\*\|) --- depends on max flow value
  Edmonds-Karp (1972)     Shortest path (BFS)            O(V · E²)
  Dinic (1970)            Level graph + blocking flows   O(V² · E)

**Integrality Theorem:** If all capacities are integers, there exists a maximum flow with integer flow on every edge.
:::

::: {#s-flow-apps .section}
::: section-title
Applications
:::

Bipartite matching reduces to max-flow: add source s connected to all left vertices, sink t connected to all right vertices, all capacities 1. By integrality, the max flow gives a maximum matching. Other applications: edge-disjoint paths, project selection, image segmentation, network reliability.
:::
:::

::: {#ch-spectral .chapter}
::: chapter-number
Section 11
:::

::: chapter-title
Spectral Methods
:::

::: {#s-adj-matrix .section}
::: section-title
Adjacency Matrix
:::

For a graph with n vertices, the **adjacency matrix** A is n×n with A\_{ij} = 1 if i \~ j, 0 otherwise. A is real and symmetric, so by the spectral theorem it has n real eigenvalues (with multiplicities) and an orthonormal basis of eigenvectors. For a d-regular graph, all eigenvalues lie in \[−d, d\] with d as the largest eigenvalue.
:::

::: {#s-laplacian .section}
::: section-title
Laplacian Matrix
:::

The **Laplacian** L = D − A where D is the diagonal degree matrix. Key properties: L is symmetric and positive semidefinite. For any vector x ∈ ℝⁿ, x^T^Lx = ∑~(i,j)∈E~ (x_i − x_j)². The smallest eigenvalue is always 0, with constant eigenvector (1,...,1).

The **algebraic connectivity** (Fiedler value) is the second-smallest eigenvalue λ₂. The graph is connected if and only if λ₂ \> 0. More generally, the multiplicity of eigenvalue 0 equals the number of connected components.

A connected d-regular graph is bipartite if and only if −d is an eigenvalue of A (equivalently, 2d is an eigenvalue of L).
:::

::: {#s-expanders .section}
::: section-title
Matrix Tree Theorem and Expanders
:::

**Matrix Tree Theorem:** The number of spanning trees of G equals any cofactor of L. Equivalently, (1/n)·∏ λ_i over all nonzero eigenvalues of L.

**Expander graphs** are sparse graphs with strong connectivity properties, characterized by a large spectral gap (the difference between the first and second eigenvalues of A for regular graphs). They appear in error-correcting codes, randomized algorithms, and network design.
:::
:::

::: {#ch-additional .chapter}
::: chapter-number
Section 12
:::

::: chapter-title
Additional Topics
:::

::: {#s-ramsey .section}
::: section-title
Ramsey Theory
:::

**Ramsey\'s Theorem (1930):** For positive integers r and s, there exists a minimum integer R(r,s) --- the **Ramsey number** --- such that any 2-coloring of the edges of K~R(r,s)~ contains a monochromatic K~r~ or K~s~. The most famous value: R(3,3) = 6 (any 2-coloring of K₆ contains a monochromatic triangle). Most Ramsey numbers are unknown; Erdős famously remarked that if aliens demanded we compute R(5,5), we should marshal all our computing resources, but if they demanded R(6,6), we should prepare for war.
:::

::: {#s-turan .section}
::: section-title
Extremal Graph Theory
:::

**Turán\'s Theorem (1941):** The maximum number of edges in a K~r+1~-free graph on n vertices is achieved by the **Turán graph** T(n,r), the complete r-partite graph with parts as equal as possible. This is the founding result of extremal graph theory.
:::

::: {#s-complexity .section}
::: section-title
Computational Complexity Landscape
:::

  Polynomial (P)                       NP-Complete                         Intermediate / Open
  ------------------------------------ ----------------------------------- --------------------------------------------
  Eulerian circuit (degree check)      Hamiltonian cycle                   Graph isomorphism (quasi-poly, Babai 2016)
  Bipartite matching (Hopcroft-Karp)   k-coloring, k ≥ 3                   
  Planarity testing (O(V))             Maximum clique                      
  Max flow (Edmonds-Karp, Dinic)       Maximum independent set             
  2-coloring (BFS)                     Vertex cover (general graphs)       
  MST (Kruskal, Prim)                  Subgraph isomorphism                
  Shortest paths (Dijkstra, etc.)      Traveling salesman (optimization)   

::: {.callout .tip}
::: callout-label
Before optimizing, check tractability
:::

If a graph problem is NP-complete, there is no known polynomial algorithm. Check this table before investing effort in an exact solution --- for NP-complete problems, consider approximation algorithms, heuristics, or special-case restrictions (e.g., vertex cover is NP-complete in general but polynomial on bipartite graphs via König\'s theorem).
:::
:::
:::

::: {#ch-algo-ref .chapter}
::: chapter-number
Section 13
:::

::: chapter-title
Algorithm Reference
:::

  Algorithm           Problem                                                        Complexity         Limitation
  ------------------- -------------------------------------------------------------- ------------------ ----------------------------------------------
  BFS                 Shortest path (unweighted), bipartiteness, components          O(V + E)           Unweighted only for shortest paths
  DFS                 Cycles, topological sort, SCCs, bridges, articulation points   O(V + E)           ---
  Dijkstra            SSSP (non-negative weights)                                    O(E + V log V)     No negative weights
  Bellman-Ford        SSSP (any weights), negative cycle detection                   O(VE)              Slower than Dijkstra
  Floyd-Warshall      APSP                                                           O(V³)              No negative cycles
  Johnson             APSP (sparse graphs)                                           O(V² log V + VE)   Requires Bellman-Ford preprocessing
  Kruskal             MST                                                            O(E log E)         Needs union-find; best for sparse
  Prim                MST                                                            O(E + V log V)     Needs priority queue; best for dense
  Hierholzer          Eulerian circuit                                               O(E)               Requires all even degrees
  Ford-Fulkerson      Max flow                                                       O(E · \|f\*\|)     May not terminate with irrational capacities
  Edmonds-Karp        Max flow                                                       O(VE²)             ---
  Dinic               Max flow                                                       O(V²E)             ---
  Hopcroft-Karp       Max bipartite matching                                         O(√V · E)          Bipartite only
  Edmonds\' Blossom   Max matching (general)                                         O(V²E)             Micali-Vazirani (1980) achieves O(√V·E)
  Hungarian           Min-weight bipartite matching                                  O(V³)              Bipartite only
  Tarjan              Strongly connected components                                  O(V + E)           Directed graphs only
:::

::: {#ch-theorem-ref .chapter}
::: chapter-number
Section 14
:::

::: chapter-title
Theorem Quick Reference
:::

  Theorem                       Statement (compressed)                                                     Related
  ----------------------------- -------------------------------------------------------------------------- ----------------------------------
  Handshaking Lemma             ∑ d(v) = 2\|E\|                                                            Euler\'s theorem on trails
  Euler\'s Theorem (trails)     Eulerian circuit ↔ all even degrees                                        Handshaking
  Menger (vertex)               Min vertex separator = max disjoint paths                                  Max-flow min-cut, Hall, König
  Menger (edge)                 Min edge cut = max edge-disjoint paths                                     Max-flow min-cut
  Euler\'s Formula (planar)     v − e + f = 2                                                              Kuratowski, Wagner
  Kuratowski (1930)             Planar ↔ no subdivision of K₅ or K₃,₃                                      Wagner, Euler\'s formula
  Wagner (1937)                 Planar ↔ no K₅ or K₃,₃ minor                                               Kuratowski, Robertson-Seymour
  Four Color Theorem            Every planar graph is 4-colorable                                          Five Color Thm, Euler\'s formula
  Brooks (1941)                 χ(G) ≤ Δ unless K_n or odd cycle                                           Vizing
  Vizing (1964)                 Δ ≤ χ\'(G) ≤ Δ + 1                                                         Brooks, König line coloring
  König line coloring (1916)    Bipartite ⇒ χ\' = Δ                                                        Vizing, König matching
  Hall (1935)                   Bipartite matching covers X ↔ \|N(S)\| ≥ \|S\| ∀S⊆X                        König, Menger, Dilworth
  König (1931)                  Bipartite: max matching = min vertex cover                                 Hall, Menger, max-flow min-cut
  Tutte (1947)                  Perfect matching ↔ odd components of G−S ≤ \|S\| ∀S                        Hall (bipartite case)
  Max-flow min-cut (1956)       Max flow value = min cut capacity                                          Menger, Hall, König
  Dirac (1952)                  d(v) ≥ n/2 ∀v ⇒ Hamiltonian cycle                                          Ore
  Ore (1960)                    d(u)+d(v) ≥ n for non-adj ⇒ Hamiltonian                                    Dirac
  Cayley\'s Formula             Labeled trees on n vertices: n^n−2^                                        Matrix Tree Theorem
  Matrix Tree Theorem           Spanning trees = any cofactor of L                                         Cayley, Laplacian
  Turán (1941)                  Max edges in K~r+1~-free graph = Turán graph                               Ramsey theory
  Ramsey (1930)                 R(r,s) exists: 2-coloring of K~R(r,s)~ forces monochromatic K~r~ or K~s~   Turán
  Strong Perfect Graph (2006)   Perfect ↔ no odd hole or odd antihole                                      König (bipartite case)
  Robertson-Seymour             Every minor-closed class has finite forbidden minors                       Wagner, Kuratowski
:::

::: {#ch-refs .chapter}
::: chapter-number
References
:::

::: chapter-title
References
:::

1.  Appel, K. & Haken, W. \"Every planar map is four colorable.\" *Bulletin of the AMS* 82.5 (1976): 711--712.
2.  Babai, L. \"Graph isomorphism in quasipolynomial time.\" *Proceedings of STOC* (2016): 684--697.
3.  Berge, C. \"Two theorems in graph theory.\" *Proceedings of the National Academy of Sciences* 43.9 (1957): 842--844.
4.  Biggs, N. *Algebraic Graph Theory*, 2nd ed. Cambridge University Press, 1993.
5.  Biggs, N., Lloyd, E.K. & Wilson, R.J. *Graph Theory 1736--1936*. Oxford University Press, 1986.
6.  Bollobás, B. *Modern Graph Theory*. Springer, 1998.
7.  Bondy, J.A. & Murty, U.S.R. *Graph Theory with Applications*. Elsevier, 1976.
8.  Brooks, R.L. \"On colouring the nodes of a network.\" *Proc. Cambridge Philosophical Society* 37 (1941): 194--197.
9.  Chudnovsky, M., Robertson, N., Seymour, P. & Thomas, R. \"The strong perfect graph theorem.\" *Annals of Mathematics* 164 (2006): 51--229.
10. Deo, N. *Graph Theory with Applications to Engineering and Computer Science*. Prentice-Hall, 1974.
11. Diestel, R. *Graph Theory*, 6th ed. Springer (GTM 173), 2025.
12. Dijkstra, E.W. \"A note on two problems in connexion with graphs.\" *Numerische Mathematik* 1 (1959): 269--271.
13. Dilworth, R.P. \"A decomposition theorem for partially ordered sets.\" *Annals of Mathematics* 51.1 (1950): 161--166.
14. Dinic, E.A. \"Algorithm for solution of a problem of maximum flow in networks with power estimation.\" *Soviet Mathematics Doklady* 11 (1970): 1277--1280.
15. Dirac, G.A. \"Some theorems on abstract graphs.\" *Proceedings of the London Mathematical Society* 2 (1952): 69--81.
16. Edmonds, J. \"Paths, trees and flowers.\" *Canadian Journal of Mathematics* 17 (1965): 449--467.
17. Edmonds, J. & Karp, R.M. \"Theoretical improvements in algorithmic efficiency for network flow problems.\" *Journal of the ACM* 19.2 (1972): 248--264.
18. Euler, L. \"Solutio problematis ad geometriam situs pertinentis.\" *Commentarii Academiae Scientiarum Petropolitanae* 8 (1741): 128--140.
19. Ford, L.R. & Fulkerson, D.R. *Flows in Networks*. Princeton University Press, 1962.
20. Fiedler, M. \"Algebraic connectivity of graphs.\" *Czechoslovak Mathematical Journal* 23.2 (1973): 298--305.
21. Hall, P. \"On representatives of subsets.\" *Journal of the London Mathematical Society* 10.1 (1935): 26--30.
22. Hopcroft, J.E. & Karp, R.M. \"An n^5/2^ algorithm for maximum matchings in bipartite graphs.\" *SIAM Journal on Computing* 2.4 (1973): 225--231.
23. Johnson, D.B. \"Efficient algorithms for shortest paths in sparse networks.\" *Journal of the ACM* 24.1 (1977): 1--13.
24. Kirchhoff, G. \"Ueber die Auflösung der Gleichungen, auf welche man bei der Untersuchung der linearen Vertheilung galvanischer Ströme geführt wird.\" *Annalen der Physik* 148.12 (1847): 497--508.
25. König, D. \"Gráfok és mátrixok.\" *Matematikai és Fizikai Lapok* 38 (1931): 116--119.
26. Kuratowski, K. \"Sur le problème des courbes gauches en topologie.\" *Fundamenta Mathematicae* 15 (1930): 271--283.
27. Menger, K. \"Zur allgemeinen Kurventheorie.\" *Fundamenta Mathematicae* 10 (1927): 96--115.
28. Micali, S. & Vazirani, V. \"An O(√\|V\|·\|E\|) algorithm for finding maximum matching in general graphs.\" *Proceedings of FOCS* (1980): 17--27.
29. Ore, O. \"Note on Hamilton circuits.\" *American Mathematical Monthly* 67 (1960): 55.
30. Ramsey, F.P. \"On a problem of formal logic.\" *Proc. London Mathematical Society* 30 (1930): 264--286.
31. Robertson, N., Sanders, D., Seymour, P. & Thomas, R. \"The four-colour theorem.\" *Journal of Combinatorial Theory, Series B* 70 (1997): 2--44.
32. Turán, P. \"On an extremal problem in graph theory.\" *Matematikai és Fizikai Lapok* 48 (1941): 436--452.
33. Tutte, W.T. \"The factorization of linear graphs.\" *Journal of the London Mathematical Society* 22 (1947): 107--111.
34. Vizing, V.G. \"On an estimate of the chromatic class of a p-graph.\" *Diskret. Analiz.* 3 (1964): 25--30.
35. Wagner, K. \"Über eine Eigenschaft der ebenen Komplexe.\" *Mathematische Annalen* 114 (1937): 570--590.
36. West, D.B. *Introduction to Graph Theory*, 2nd ed. Prentice Hall, 2001.
37. Whitney, H. \"Congruent graphs and the connectivity of graphs.\" *American Journal of Mathematics* 54 (1932): 150--168.
:::
:::
:::

------------------------------------------------------------------------

::: page-footer
Loop MMT™ · Multi-Module Theory Graph Theory Knowledge Pack · v1 © 2026 Shea Gunther · [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/deed.en){style="color:inherit;"}
:::
