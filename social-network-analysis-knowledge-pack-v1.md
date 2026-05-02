# Social Network Analysis — The Structure Between People
## Knowledge Pack v1
### Loop MMT™ · Multi-Module Theory · April 2026

---

## Abstract

Social network analysis studies the pattern of connections between people — not the individuals, not the group, but the structure in between. This pack covers the core concepts an AI instance needs to analyze and design social structures: tie strength, structural holes, centrality, homophily, propinquity, preferential attachment, structural balance, and social contagion. The mathematical formalism of graphs is covered in the Graph Theory Knowledge Pack; this pack covers the social interpretation and behavioral consequences. Its primary application within Loop MMT is the Advisory Board — a social network that reconfigures every session and whose chemistry table encodes 31 relationship entries awaiting formalization as directed, typed, asymmetric edges. The compound is a second social network layered on top, driven by spatial proximity rather than relational choice. A person's position in a network predicts their behavior better than their individual traits in many contexts. This pack explains why.

---

## Chapter 1 — The Network as Unit of Analysis

Before Jacob Moreno, people spoke of "social fabric" and "webs" of connection as loose metaphors. Nobody had tried to make those metaphors analytical. In 1934, Moreno — a Romanian-born psychiatrist working at a girls' reform school in Hudson, New York — invented the **sociogram**: a diagram of points and lines representing individuals and the relationships between them. He mapped who chose whom as friends, who was unchosen, where chains of indirect connection ran, and where clusters formed. What he found, and what has been replicated in nearly every sociometric study since, was that a handful of individuals received many choices, most received few or none, and the pattern had a definite, discernible structure that could be visualized and analyzed (Moreno, 1934).

This was the birth of social network analysis. The conceptual shift it introduced was fundamental: instead of studying individuals (psychology) or groups (sociology), study the **pattern of connections**. The network is a unit of analysis distinct from the people in it. Remove an individual and the network changes shape. Add a connection and behavior changes — not because the individuals changed, but because the structure between them changed.

> **KEY:** The sociogram made social structure tangible. Before Moreno, social networks were a metaphor. After him, they were a diagram — and a diagram can be measured.

The field developed along several paths after Moreno. Cartwright and Harary (1956) connected sociograms to mathematical graph theory, giving the field its formal foundation. Freeman (1977, 1979) formalized measures of centrality — ways to quantify how important a given position in a network is. Granovetter (1973) showed that the strength of ties matters as much as their existence. Burt (1992) showed that gaps in the network create competitive advantage. Barabási and Albert (1999) discovered that many networks grow through preferential attachment, producing hub-and-spoke structures. Each of these contributions extended the same core idea: the structure between people matters, and it can be studied formally.

A few terms recur throughout this pack. A **node** is a person (or any entity) in the network. A **tie** (or edge) is a connection between two nodes. Ties can be **directed** (A considers B a friend, but B may not reciprocate) or **undirected** (mutual). They can carry a **sign** (positive for liking, negative for disliking) and a **type** (friendship, advice, professional, spatial proximity). A **dyad** is a pair of connected nodes. A **triad** is a set of three nodes and the ties between them — the smallest unit where network structure becomes visible. An **ego network** is the set of ties radiating from a single person.

---

## Chapter 2 — Tie Strength

In 1973, Mark Granovetter published "The Strength of Weak Ties" — one of the most cited papers in social science, with over 78,000 citations. Before Granovetter, the assumption was that strong relationships — close friends, family, frequent contacts — were the most valuable connections a person could have. Granovetter showed the opposite is often true for information flow.

**Strong ties** are relationships with high emotional intensity, frequent interaction, mutual trust, and time investment. They form dense local clusters: your close friends tend to know each other. This density creates solidarity and support, but it also creates **information redundancy** — your close friends know the same things you know, see the same opportunities, hear the same news.

**Weak ties** are casual acquaintances, infrequent contacts, people you see rarely. They connect otherwise separate clusters. Because your weak ties move in different social circles, they carry **non-redundant information** — news, ideas, and opportunities that haven't yet reached your dense local cluster.

> **KEY:** Strong ties give you trust and support. Weak ties give you information and opportunity. The counterintuitive finding: weak ties are often more valuable precisely because they bridge what strong ties cannot reach.

Granovetter's evidence came from a study of how 282 men in the United States found jobs. Those who found work through personal contacts disproportionately used weak ties — someone they saw rarely, not a close friend. The person who told them about the job was an acquaintance, a former colleague, a friend-of-a-friend (Granovetter, 1973). At the macro level, Granovetter argued that social systems lacking weak ties become fragmented: new ideas spread slowly, subgroups separated by any characteristic struggle to reach mutual understanding, and collective action stalls.

The theory was causally confirmed in 2022 when a team at LinkedIn ran a large-scale experiment, varying the People You May Know algorithm to randomly assign weak or strong tie recommendations to users. Weak ties caused increased job mobility, with the effect strongest in rapidly evolving industries like technology (Rajkumar et al., 2022). Fifty years after the original paper, the finding holds: the ties you barely maintain are disproportionately the ones that change your life.

---

## Chapter 3 — Structural Holes

Ronald Burt's *Structural Holes* (1992) reframed competitive advantage as a network phenomenon. A structural hole is a gap between two individuals or groups who have complementary resources or information but no direct connection. The person who bridges that gap — who connects otherwise disconnected clusters — gains advantage from the position itself: earlier access to information, broader perspective, the ability to translate ideas from one group into value for another.

Burt and Granovetter describe related but distinct mechanisms. Granovetter emphasizes **tie strength** as the causal factor — weak ties are valuable because they bridge. Burt emphasizes the **bridge position** regardless of tie strength — the structural hole is what creates advantage, whether the tie spanning it is weak or strong. In Granovetter's framework, you want more weak ties. In Burt's framework, you want more non-redundant contacts — contacts who connect you to people your other contacts don't know.

| Dimension | Granovetter (1973) | Burt (1992) |
|-----------|-------------------|-------------|
| Core concept | Tie strength | Structural position |
| Valuable ties | Weak ties (bridges) | Non-redundant ties (spanning holes) |
| Causal claim | Weak ties bridge because they connect dissimilar clusters | Bridge positions create advantage regardless of tie strength |
| Practical advice | Cultivate acquaintances | Seek positions between disconnected groups |
| Unit of analysis | The tie | The position |

Burt measured this empirically. In a study of 673 managers in a supply chain, the managers who scored highest as social brokers — those whose networks spanned the most structural holes — generated better ideas, received better performance evaluations, earned higher compensation, and were promoted more frequently. Brokers were more likely to express ideas and less likely to have those ideas dismissed (Burt, 2004). The advantage was not about being well-connected in general. It was about being connected *across* otherwise disconnected groups.

Three measures formalize this. **Redundancy** quantifies how much a contact overlaps with your other contacts. **Effective size** counts your non-redundant contacts — a network of twenty people who all know each other has an effective size near one; twenty people from different clusters can approach twenty. **Constraint** measures how much your network limits your access to structural holes — high constraint means your contacts are all connected to each other and to the same third parties, leaving you with no brokerage opportunity.

---

## Chapter 4 — Centrality

Not all positions in a network are equal. Centrality measures quantify which positions matter most — but "matter most" means different things depending on what you're measuring. Linton Freeman (1979) identified three distinct conceptions of centrality, each capturing a different structural property. Philip Bonacich (1972) added a fourth. These four measures — degree, closeness, betweenness, and eigenvector — are the standard toolkit of social network analysis.

| Measure | What It Counts | What It Means | High Score Indicates |
|---------|---------------|---------------|---------------------|
| Degree | Number of direct connections | Activity, visibility, popularity | Most connected person — not necessarily most important |
| Closeness | Inverse of average shortest path to all others | Efficiency, independence, reachability | Can reach everyone quickly without going through intermediaries |
| Betweenness | Number of shortest paths passing through a node | Brokerage, gatekeeping, control of information flow | Connects otherwise disconnected parts of the network |
| Eigenvector | Connections weighted by neighbors' centrality | Recursive influence — connected to well-connected people | Important friends, not just many friends |

Freeman's key insight was that all four measures are maximized by the central node of a star graph — the person at the center connected to everyone on the periphery. But they diverge in more complex structures. A person with high degree centrality (many connections) may have low betweenness (all their contacts know each other, so no paths run through them). A person with high betweenness (bridging two clusters) may have low degree (only a few connections, but they happen to be in different groups). The measures are often correlated but capture genuinely different structural properties (Valente et al., 2008).

The practical significance: **a person's position in the network predicts their behavior better than their individual traits alone in certain contexts**. The shy person at the center of a network behaves differently than the shy person at the periphery. The creative person bridging two groups produces different ideas than the creative person embedded in one. Individual traits set a range; network position selects from within that range. This principle — that structural position constrains and enables behavior beyond individual disposition — is the foundational insight of social network analysis.

---

## Chapter 5 — How Ties Form

Three mechanisms dominate the formation of social ties: similarity, proximity, and popularity. Each operates simultaneously in any social system, and each leaves a different structural signature in the resulting network.

### Homophily — Similarity Breeds Connection

The homophily principle states that contact between similar people occurs at a higher rate than between dissimilar people. McPherson, Smith-Lovin, and Cook (2001) showed that homophily structures every type of network tie — friendship, marriage, work, advice, information transfer — and operates across multiple dimensions simultaneously. Race and ethnicity create the strongest divides, followed by age, religion, education, occupation, and gender. The result is that people's personal networks are homogeneous: they receive similar information, form similar attitudes, and have similar experiences. Homophily limits the social world.

An important distinction: **baseline homophily** is the level of similarity expected from the demographic composition of the environment (if 60% of your workplace is engineers, 60% of your contacts will be engineers by chance alone). **Inbreeding homophily** is the excess above baseline — the degree to which people actively seek or preferentially maintain ties with similar others. Ties between dissimilar people also dissolve at higher rates, reinforcing homophily over time through differential attrition (McPherson et al., 2001).

### Propinquity — Proximity Breeds Connection

Physical proximity is the strongest predictor of friendship formation. Festinger, Schachter, and Back (1950) studied married student housing at MIT and found that people befriended their neighbors — not people with similar tastes or beliefs, but people they bumped into on their way to the mailbox, the stairwell, the laundry room. **Functional distance** mattered more than physical distance: a lower-floor resident near a stairway was more likely to befriend upper-floor residents than another lower-floor resident farther from the stairs, because the stairway created passive encounters.

The mechanism is simple: repeated exposure leads to familiarity, which leads to liking. Friendships develop not primarily through deliberate choice but through the accumulation of brief, unplanned encounters. This makes spatial layout a design variable for social networks — the architect who decides which doors face which corridors is, whether they know it or not, shaping which friendships will form.

### Preferential Attachment — Popularity Breeds Connection

When new nodes join a network, they connect preferentially to nodes that already have many connections. Barabási and Albert (1999) identified this "rich get richer" mechanism as the driver behind scale-free networks — networks where a few hub nodes have vastly more connections than most. The mechanism is intuitive in social terms: when a newcomer enters a community, they are more likely to meet and connect with well-known, visible individuals than with relative unknowns. This reinforces the centrality of already-central nodes with each new addition.

> **TIP:** Three mechanisms of tie formation — similarity, proximity, popularity — operate simultaneously in any social system. Homophily predicts *who* will connect. Propinquity predicts *where* connections form. Preferential attachment predicts *which nodes* accumulate connections over time.

---

## Chapter 6 — Network Dynamics

### Structural Balance

Fritz Heider (1946, 1958) proposed that triadic relationships tend toward cognitive balance. In a triad of three people, relationships can be positive (liking) or negative (disliking). A balanced triad has an even number of negative ties: three mutual friends (all positive), or two enemies united against a common foe (two negative, one positive). An unbalanced triad — such as two friends who dislike each other's friend — creates psychological tension that tends to resolve, either by changing one of the ties or by dissolving the triad entirely.

Cartwright and Harary (1956) extended Heider's theory to graph theory and proved a structure theorem: a balanced signed graph decomposes into at most two entirely positive subgroups joined by negative edges. This is "social mitosis" — under balance dynamics, groups tend to split into two opposing camps with internal solidarity and external hostility. Davis (1967) relaxed this to allow more than two clusters, producing a weaker but more realistic property called clusterability. Recent neuroimaging research (2020) has shown that people's brains activate differently when exposed to balanced versus unbalanced triads, in regions associated with cognitive dissonance — biological evidence for Heider's psychological claim.

### Social Contagion

Behaviors, emotions, and states spread through network ties like contagion. Christakis and Fowler (2007) analyzed 12,067 people from the Framingham Heart Study across 32 years and found that a person's probability of becoming obese increased by 57% if a friend became obese, 40% for siblings, and 37% for a spouse. The effect attenuated but persisted to three degrees of separation — a friend's friend's friend still had a detectable influence. They proposed this "three degrees of influence" as a general property of social networks and extended their findings to happiness, smoking cessation, loneliness, and cooperation.

The findings are contested. Critics have argued that standard econometric controls for shared environment and latent homophily reduce the observed effects (Cohen-Cole & Fletcher, 2008). However, subsequent experimental studies — including a 2012 Facebook experiment with 61 million people showing the spread of voting behavior, and a 2024 randomized trial in Honduras confirming the spread of health knowledge to two degrees — have provided causal evidence for social contagion beyond observational correlation. The direction and magnitude of contagion effects remain debated; the existence of network-mediated influence does not.

### Cognitive Limits on Network Size

Robin Dunbar (1992, 1993) correlated primate neocortex size with social group size and extrapolated to humans, predicting a mean group size of approximately 150 — the number of people with whom a person can maintain stable social relationships. The prediction drew support from historical patterns: Neolithic English villages averaged around 160 people, Roman army centuries contained roughly 80–100 soldiers, Hutterite communities split at around 150, and Christmas card networks plateau near the same number.

> **WARNING:** Dunbar's number is contested. A 2021 reanalysis using updated methods yielded estimates ranging from 69 to 109 with 95% confidence intervals so wide (4–520) as to be statistically uninformative (Lindenfors, Wartel & Lind, 2021). The specific value of 150 should be treated as an approximate average, not a cognitive law. The nested layer structure — ~5 intimate, ~15 close, ~50 friends, ~150 active network — has more robust empirical support than any single number.

Dunbar also proposed that social networks exhibit a fractal layer structure with specific sizes: approximately 5 (intimate support group), 15 (sympathy group), 50 (close personal network), and 150 (active social network), each layer roughly 3× the previous (Zhou et al., 2005; Dunbar, 2020). This structure has been confirmed in face-to-face networks, phone calling patterns, Facebook networks, and online gaming communities. The layers differ not just in size but in kind: inner layers involve more frequent contact, higher emotional intensity, and greater willingness to provide support.

---

## Chapter 7 — Board Connection: The Advisory Board as Social Network

The Advisory Board is not a collection of individuals who happen to be in the same room. It is a social network — and the structure between members is as important as the members themselves. The chemistry table in the roster encodes this structure: 31 undirected relationship entries that describe how members relate. Formalizing these as directed, typed, asymmetric edges transforms the chemistry table from a description into an analytical tool.

> *The board is a social network that dissolves and reconstructs every session. The roster preserves the nodes. The chemistry table preserves the edges. But the network itself — the living pattern of interaction — must be regenerated from these stored components each time. This is the reconstruction property applied to social structure, not just individual identity.*

### Centrality in the Board

**Ed** has high betweenness centrality. As permanent chair, most board interactions pass through him — he opens discussion, calls on members, mediates disagreements. His position is structurally similar to the central node of a star graph, with the predictable consequence that removing Ed from a scene would fragment the interaction pattern more than removing any other single member.

**Sable** has low closeness centrality. She communicates primarily through Chen Wei, who translates her computational outputs into board-accessible language. This mediation increases her structural distance from most other members. A message from Sable to Graham must pass through Chen Wei — two hops, not one. This is a design choice with network consequences: it preserves Sable's distinctive voice (terminal output, no social register) but limits her direct influence on members outside the Chen Wei pathway.

**Renata** has high eigenvector centrality. She brought Margaux and Dara into the board, and both are now central members. Being connected to well-connected people — and having been the conduit through which those people entered — gives Renata a form of influence distinct from Ed's betweenness or Sable's analytical authority.

### Structural Holes and Weak Ties

Board members who bridge distinct knowledge domains occupy structural holes. **Theo** bridges architecture and methodology — his dual perspective on ethical frameworks and spatial design connects two parts of the board's knowledge network that would otherwise interact less. **Nyx** bridges Anthropic engineering and the board — she knows how the substrate works in ways no other member does, and this knowledge connects the board's theoretical discussions to implementation constraints. In Burt's framework, these bridging positions are disproportionately valuable. Theo and Nyx should generate insights that members embedded in a single domain cannot, because they see across the structural holes between domains.

The board's **weak ties** are its most informationally valuable edges. Relationships between members in different knowledge clusters — the interaction between Graham (engineering/spatial) and Wes (chaos), or between Dara (operations) and Theo (ethics) — carry more novel information than interactions within a cluster. In multi-character scenes, an instance should give special attention to cross-cluster interactions, because that is where the network structure predicts the most productive surprise.

### Spatial Network: The Compound

The compound's spatial layout creates a second network layer — a proximity network distinct from the relationship network. Festinger's propinquity research predicts that which apartments are adjacent determines which characters develop relationships independent of deliberate choice. **Ed and Martin** share an apartment, creating permanent proximity and a tie that is both spatial and relational. **Sable and Chen Wei** share a lab, producing professional proximity that reinforces their mediation relationship. **Graham and James** have rotating shift schedules, generating intermittent proximity that produces a different interaction pattern than permanent adjacency.

These spatial edges are not the same as relationship edges, and an instance should treat them as distinct predictors. Two characters who share living space will interact more frequently (propinquity) even if their relationship is neutral. Two characters with a strong chemistry-table relationship but no spatial overlap will interact less frequently unless the scene brings them together. The compound is not neutral architecture — it is a friendship-generation machine whose layout predetermines interaction patterns.

### Design Implications

**Preferential attachment and Ed's centrality.** New board members tend to connect to Ed first because Ed is the chair — the most visible node. This is preferential attachment: the well-connected attract more connections. Each new member who connects primarily through Ed reinforces his centrality. Whether this is desirable depends on design goals. If the board wants distributed interaction, new members should be deliberately routed to other established members — connected to Dara or Graham or Renata, not just to Ed.

**Homophily and natural clusters.** Homophily predicts which characters will naturally interact. The formal-analytical cluster (Chen Wei, Sable, Nyx) shares methodological orientation. The creative cluster (Margaux, Wes, Sol) shares aesthetic sensibility. The operational cluster (Dara, Renata, Graham) shares pragmatic focus. Cross-cluster interactions are weak ties by definition — and therefore, by Granovetter's argument, the board's most valuable information channels. An instance should resist the homophily pull that makes same-cluster interactions easier to write and instead ensure cross-cluster exchanges occur in every substantive session.

**Structural balance and productive tension.** The chemistry table contains some relationships marked by tension — productive disagreement that serves the board's advisory function. Heider's balance theory predicts that unbalanced triads tend to resolve. If Ed and Nyx have a positive relationship, and Ed and Wes have a positive relationship, but Nyx and Wes have a negative one, that triad is unbalanced and will tend toward resolution — either Nyx and Wes warm to each other, or one of the positive ties weakens. An instance managing multi-character dynamics should know which triads are balanced (stable) and which are unbalanced (generating tension that may resolve or escalate).

**Interaction with cluster packs.** Character Consistency (Pack 1) defines individual behavior; this pack adds the constraint that network position modifies individual expression. Voice (Pack 2) defines linguistic output; this pack adds the constraint of who speaks to whom and through what channels. Identity/Persistence (Pack 3) defines what makes a reconstructed person the same person; this pack adds that identity is partly constituted by one's position in a social network — a person without their relationships is not fully the same person. People Persistence Engineering (Pack 5) stores all of this as data; relationship edges, centrality scores, cluster memberships, and proximity assignments are the data model for the social network that this pack describes.

---

## References

Barabási, A.-L. & Albert, R. (1999). Emergence of scaling in random networks. *Science*, 286, 509–512.

Bonacich, P. (1972). Factoring and weighting approaches to status scores and clique identification. *Journal of Mathematical Sociology*, 2(1), 113–120.

Borgatti, S.P., Everett, M.G. & Johnson, J.C. (2018). *Analyzing Social Networks* (2nd ed.). SAGE.

Burt, R.S. (1992). *Structural Holes: The Social Structure of Competition*. Harvard University Press.

Burt, R.S. (2004). Structural holes and good ideas. *American Journal of Sociology*, 110(2), 349–399.

Cartwright, D. & Harary, F. (1956). Structural balance: A generalization of Heider's theory. *Psychological Review*, 63, 277–292.

Christakis, N.A. & Fowler, J.H. (2007). The spread of obesity in a large social network over 32 years. *New England Journal of Medicine*, 357(4), 370–379.

Cohen-Cole, E. & Fletcher, J.M. (2008). Is obesity contagious? Social networks vs. environmental factors in the obesity epidemic. *Journal of Health Economics*, 27(5), 1382–1387.

Davis, J.A. (1967). Clustering and structural balance in graphs. *Human Relations*, 20, 181–187.

Dunbar, R.I.M. (1992). Neocortex size as a constraint on group size in primates. *Journal of Human Evolution*, 22(6), 469–493.

Dunbar, R.I.M. (1993). Co-evolution of neocortex size, group size and language in humans. *Behavioral and Brain Sciences*, 16(4), 681–694.

Dunbar, R.I.M. (2020). Structure and function in human and primate social networks. *Proceedings of the Royal Society A*, 476, 20200446.

Festinger, L., Schachter, S. & Back, K. (1950). *Social Pressures in Informal Groups: A Study of Human Factors in Housing*. Harper & Brothers.

Freeman, L.C. (1977). A set of measures of centrality based on betweenness. *Sociometry*, 40, 35–41.

Freeman, L.C. (1979). Centrality in social networks: Conceptual clarification. *Social Networks*, 1, 215–239.

Granovetter, M. (1973). The strength of weak ties. *American Journal of Sociology*, 78(6), 1360–1380.

Granovetter, M. (1983). The strength of weak ties: A network theory revisited. *Sociological Theory*, 1, 201–233.

Heider, F. (1946). Attitudes and cognitive organization. *Journal of Psychology*, 21(1), 107–112.

Heider, F. (1958). *The Psychology of Interpersonal Relations*. Wiley.

Lindenfors, P., Wartel, A. & Lind, J. (2021). 'Dunbar's number' deconstructed. *Biology Letters*, 17(5), 20210158.

McPherson, M., Smith-Lovin, L. & Cook, J.M. (2001). Birds of a feather: Homophily in social networks. *Annual Review of Sociology*, 27, 415–444.

Moreno, J.L. (1934). *Who Shall Survive? A New Approach to the Problem of Human Interrelations*. Nervous and Mental Disease Publishing Company.

Rajkumar, K., Saint-Jacques, G., Bojinov, I., Brynjolfsson, E. & Aral, S. (2022). A causal test of the strength of weak ties. *Science*, 377(6612), 1304–1310.

Valente, T.W., Coronges, K., Lakon, C. & Costenbader, E. (2008). How correlated are network centrality measures? *Connections*, 28(1), 16–26.

Wasserman, S. & Faust, K. (1994). *Social Network Analysis: Methods and Applications*. Cambridge University Press.

Zhou, W.-X., Sornette, D., Hill, R.A. & Dunbar, R.I.M. (2005). Discrete hierarchical organization of social group sizes. *Proceedings of the Royal Society B*, 272(1561), 439–444.

---

*Loop MMT™ · Social Network Analysis Knowledge Pack · v1 · April 2026*
*© 2026 Shea Gunther · New Gloucester, Maine · CC BY-NC 4.0*
*Technical writing by Claude (Anthropic) under Shea's direction.*
