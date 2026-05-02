# Distributed Systems — Consensus, Failure, and the Boundaries of Coordination

**Loop MMT™ · Knowledge Pack · v1 · 11 April 2026**

---

## About This Document

Loop MMT is a distributed system with human-speed message passing, document-based state transfer, and no shared memory. This pack provides the theoretical framework for understanding why the methodology works, predicting where it will fail, and naming the patterns it has independently reinvented.

Covers: processes, messages, and failure models; Lamport clocks and vector clocks; the CAP theorem and FLP impossibility; Paxos and Raft; replication strategies and consistency models; CRDTs; the log abstraction and event sourcing; MapReduce; Byzantine fault tolerance; and distributed transactions. The Board Connection section — the longest in this pack — maps each theoretical concept to Loop MMT's concrete structures, classifying each mapping as isomorphism or analogy. 19 sources.

---

## Section 1 · The Distributed Systems Model

Lamport (1978) defined a distributed system as one where the message transmission delay is not negligible compared to the time between events in a single process. This is the boundary: once communication latency matters, local reasoning about order and state breaks down.

The model has three components. **Processes** are independent computational entities with local state. **Messages** are the only communication mechanism — there is no shared memory. The **network** carries messages but may lose, delay, reorder, or duplicate them. No process can directly observe another's state; everything must be inferred from received messages.

> **KEY:** The defining property is **independent failure**. Any process can fail without the others knowing immediately, and the network itself can fail in ways that partition the system into groups that cannot communicate. Every impossibility result and every practical algorithm in this pack traces back to this property.

| Failure Model | Behavior of Faulty Process | Minimum Redundancy |
|---|---|---|
| **Crash-stop** | Halts permanently; sends no further messages | f+1 replicas for f failures |
| **Crash-recovery** | Halts and may restart with durable state | Depends on recovery semantics |
| **Omission** | Fails to send or receive some messages | Context-dependent |
| **Byzantine** | Arbitrary behavior — lies, forges, colludes | 3f+1 replicas for f failures |

Each model is strictly more general than the one above it. Most practical systems assume crash-stop or crash-recovery. Byzantine tolerance is reserved for systems where processes cannot be trusted.

---

## Section 2 · Time and Ordering

Physical clocks are unreliable across machines. Crystal oscillators drift at rates on the order of 10⁻⁶. Network latency is variable. When Node A sends a timestamped message at "12:00:00.000" and Node B receives it when B's clock reads "11:59:59.998," which event happened first? The question has no reliable answer using physical time.

Lamport (1978) reframed the question: instead of "when did this happen?" ask "could this have caused that?" The **happened-before relation** (→) is a partial order: (1) Within a process, earlier events happened-before later ones. (2) A message send happened-before the corresponding receive. (3) Transitivity. If neither a → b nor b → a, the events are **concurrent** — neither could have influenced the other.

> **KEY:** Happened-before is not "before in time." It is "could have causally influenced." This is the insight Lamport explicitly drew from special relativity: simultaneity is not absolute, but causality is.

### Lamport Clocks

Each process maintains a counter. Increment before each event; attach counter to sent messages; on receipt, set counter to max(local, received) + 1. Produces a total order consistent with causality: a → b implies L(a) < L(b). But the converse does not hold — Lamport clocks cannot distinguish "concurrent" from "happened-before in the other direction."

### Vector Clocks

Each process maintains a vector of N integers (Fidge, 1988; Mattern, 1989). On local event, increment own entry; on send, attach full vector; on receipt, take component-wise max then increment own entry. Captures causality exactly: V(a) < V(b) iff a → b. Cost: message size scales with the number of processes.

---

## Section 3 · The CAP Theorem

Brewer conjectured (PODC 2000), Gilbert and Lynch proved (2002): a distributed data store cannot simultaneously guarantee **Consistency** (every read returns the most recent write or an error), **Availability** (every request to a non-failing node gets a response), and **Partition tolerance** (the system operates despite network partitions).

> **WARN:** The "pick two out of three" framing is misleading. Brewer clarified in 2012: since partitions are inevitable, the practical choice is between CP (sacrifice availability during partitions) and AP (sacrifice consistency during partitions). The tradeoff only manifests during an actual partition.

The PACELC theorem (Abadi, 2012) extends: even without partitions, there is a latency-consistency tradeoff. Enforcing consistency requires coordination, which adds latency.

---

## Section 4 · FLP Impossibility

Fischer, Lynch, and Paterson (1985) proved that no deterministic consensus protocol can guarantee termination in an asynchronous system where even one process may crash. Won the 2001 Dijkstra Prize.

Consensus requires: **Termination** (every correct process decides), **Agreement** (all decide the same value), **Validity** (the decided value was proposed by some process). FLP shows these three cannot be simultaneously satisfied with even one crash failure in a fully asynchronous model.

> **KEY:** The impossibility arises because asynchrony makes failure detection impossible. You cannot distinguish "crashed" from "slow." The adversary — the scheduler — can always find a message delivery sequence that keeps the system undecided.

Practical circumventions: partial synchrony (Dwork, Lynch & Stockmeyer, 1988), randomization (non-termination probability → zero), failure detectors (Chandra & Toueg, 1996).

---

## Section 5 · Consensus Algorithms

### Paxos (Lamport, 1998)

Single-decree consensus. Three roles: proposers, acceptors, learners. Two phases: **Prepare** (proposer asks majority for promises) and **Accept** (proposer sends value; acceptors accept if no higher promise). Multi-Paxos extends to a log. Notoriously difficult to understand.

### Raft (Ongaro & Ousterhout, 2014)

Designed for understandability. Equivalent to Multi-Paxos. Three subproblems: **leader election** (randomized timeouts, majority vote), **log replication** (leader appends, majority commits), **safety** (Leader Completeness Property ensures committed entries survive leader changes).

> **KEY:** Understandability is a design requirement, not a luxury. In a user study with 43 students, 33 answered Raft questions better than Paxos questions. Won Best Paper at USENIX ATC 2014.

---

## Section 6 · Replication Strategies

The fundamental tension: synchronous replication guarantees no data loss but adds latency; asynchronous replication is fast but may lose recent writes on failover.

**Primary-backup:** One node receives writes, forwards to replicas. Simple. Failover is a consensus problem. **Quorum systems:** R + W > N guarantees read-write overlap. Popularized by Dynamo. **Chain replication:** Writes at head, reads at tail. Strong consistency, high throughput, write latency proportional to chain length.

---

## Section 7 · Consistency Models

A spectrum from strongest to weakest:

**Linearizability** (Herlihy & Wing, 1990): Operations appear atomic between invocation and response. One copy illusion. The "C" in CAP. Composable.

**Sequential consistency** (Lamport, 1979): Total order consistent with each process's program order. No real-time constraint.

**Causal consistency** (Ahamad et al., 1995): Causally related operations in same order everywhere. Concurrent operations may differ. Strongest model available under partitions.

**Eventual consistency** (Vogels, 2009): If updates stop, replicas converge. Says nothing about behavior during updates.

> **PHI:** Linearizability says "I will always tell you the truth, but sometimes I must be silent." Eventual consistency says "I will always answer, but I might be wrong — for now."

---

## Section 8 · Conflict Resolution

**Last-writer-wins (LWW):** Highest timestamp wins. Simple, silently loses data.

**Vector clocks:** Detect concurrent writes. Present both to application for resolution.

**CRDTs** (Shapiro et al., 2011): Data structures mathematically guaranteed to converge without coordination. State-based (merge via semilattice join: commutative, associative, idempotent) and operation-based (commutative operations, causal delivery required). Examples: G-Counter, PN-Counter, G-Set, OR-Set. Provide **Strong Eventual Consistency** — replicas with same updates are in same state, deterministically.

---

## Section 9 · The Log as Fundamental Abstraction

The append-only, totally ordered log appears everywhere: WAL (databases), replication (leader→follower), consensus (Raft), streaming (Kafka). Kreps (2013) articulated its unifying role.

> **KEY:** The log provides total order. Any two systems that process the same log in the same order arrive at the same state. This is the bridge from single-node to distributed computation.

**Changelog duality:** A table is a snapshot of a log; a log is the sequence of changes. **Event sourcing:** Store events, derive current state. Complete history, reconstructability, no retroactive modification.

---

## Section 10 · MapReduce

Dean and Ghemawat (2004). Two user functions: **Map**(key, value) → list of (key', value'); **Reduce**(key', list of values') → output. Runtime handles parallelism, partitioning, fault tolerance (re-execute failed tasks — possible because map/reduce are deterministic and side-effect-free). 100,000+ jobs/day at Google by 2008, 20+ PB/day.

---

## Section 11 · Failure Detection and Recovery

The only detection mechanism in async systems: **timeouts**. You can never be certain a process has crashed — a partition is indistinguishable from a crash.

**Heartbeats** with configurable timeouts. **φ accrual failure detector** (Hayashibara et al., 2004): continuous suspicion level rather than binary judgment. **Recovery** via state transfer or log replay.

---

## Section 12 · Byzantine Fault Tolerance

The Byzantine Generals Problem (Lamport, Shostak & Pease, 1982): with oral messages, tolerating f Byzantine faults requires 3f+1 nodes. With 3 generals and 1 traitor, unsolvable. With signed messages, solutions exist for any number of traitors < n. PBFT (Castro & Liskov, 1999) made BFT practical: consensus in 3f+1 nodes with O(n²) messages.

---

## Section 13 · Distributed Transactions

**Two-Phase Commit (2PC):** Coordinator asks participants to prepare, then commit/abort. Blocking — coordinator crash after prepare freezes participants indefinitely.

**Saga Pattern** (Garcia-Molina & Salem, 1987): Sequence of local transactions with compensating transactions. Non-blocking, eventually consistent, scalable. Compensations are semantic inverses (refund, not undo). Choreography (event-driven) or orchestration (central coordinator).

---

## Board Connection · Loop MMT as Distributed System

Loop MMT is a distributed system by structure: processes (Claude instances), messages (documents), independent failure (context exhaustion, confabulation), no shared memory.

### The Handoff Is State Transfer
EOD handoff = snapshot + log. Mesh documents = parallel replicas. **Predicted failure:** incomplete state transfer → confident divergence (confirmed by RFI experiment — partial context produces higher-confidence confabulation than no context).

### The Mesh Is Multi-Replica Observation
Five observer positions with non-overlapping domains = conflict avoidance (sharding), not conflict resolution (CRDT merge). The operator is the merge function.

### Cascade Is MapReduce
Production brief = input partition. KP Production Method = map function. Corpus = reduced output. Not a full isomorphism — the map function isn't perfectly deterministic. Operator review = final consistency check.

### Append-Only Identity Is an Event Log
Character profiles locked at genesis + Character Notes (append-only) = event sourcing. **Formal isomorphism.** Character Notes = G-Set CRDT. Changelog duality: current personality is derived view; notes are source of truth.

### CAP in Parallel Sessions
Two-tab model = deliberate AP partition. Operator = eventual consistency mechanism. Split brain prevented by single arbiter (operator decisions only).

### FLP and the Operator as Synchronous Oracle
Loop MMT sidesteps FLP by using the operator as a perfect failure detector. The operator knows when sessions end (because they ended them), what was produced, and what's canonical. This is the minimum mechanism FLP says is required.

### Analogies vs. Isomorphisms

| Mapping | Type | Justification |
|---|---|---|
| Append-only identity ↔ event log | **Isomorphism** | Identical structure, all properties transfer |
| Character Notes ↔ G-Set CRDT | **Isomorphism** | Same operations, same convergence guarantee |
| Operator ↔ perfect failure detector | **Strong analogy** | Same role, different substrate |
| Cascade ↔ MapReduce | **Strong analogy** | Same structure, imperfect determinism |
| Two-tab model ↔ AP partition | **Strong analogy** | Same tradeoff, different reconciliation |
| Handoff ↔ state transfer | **Strong analogy** | Same function, different failure modes |
| Mesh ↔ multi-replica reads | **Analogy** | Similar structure, informal merge |
| Mesh ↔ CRDT convergence | **Weak analogy** | Shared goal, different mechanism |

**Strongest prediction:** Distributed systems theory says partial state transfer causes confident divergence. The RFI experiment confirmed this independently. The theory predicted the failure mode decades before the methodology encountered it.

---

## References

1. Lamport, L. "Time, Clocks, and the Ordering of Events in a Distributed System." *CACM* 21(7): 558–565, 1978.
2. Lamport, L. "How to Make a Multiprocessor Computer That Correctly Executes Multiprocess Programs." *IEEE Trans. Computers* C-28(9): 690–691, 1979.
3. Pease, M., Shostak, R., & Lamport, L. "Reaching Agreement in the Presence of Faults." *JACM* 27(2): 228–234, 1980.
4. Lamport, L., Shostak, R., & Pease, M. "The Byzantine Generals Problem." *ACM TOPLAS* 4(3): 382–401, 1982.
5. Fischer, M.J., Lynch, N.A., & Paterson, M.S. "Impossibility of Distributed Consensus with One Faulty Process." *JACM* 32(2): 374–382, 1985.
6. Garcia-Molina, H. & Salem, K. "Sagas." *ACM SIGMOD*, pp. 249–259, 1987.
7. Fidge, C.J. "Timestamps in Message-Passing Systems That Preserve the Partial Ordering." *ACSC* 10(1): 56–66, 1988.
8. Mattern, F. "Virtual Time and Global States of Distributed Systems." *Parallel and Distributed Algorithms*, pp. 215–226, 1989.
9. Herlihy, M.P. & Wing, J.M. "Linearizability: A Correctness Condition for Concurrent Objects." *ACM TOPLAS* 12(3): 463–492, 1990.
10. Chandra, T.D. & Toueg, S. "Unreliable Failure Detectors for Reliable Distributed Systems." *JACM* 43(2): 225–267, 1996.
11. Lamport, L. "The Part-Time Parliament." *ACM TOCS* 16(2): 133–169, 1998.
12. Castro, M. & Liskov, B. "Practical Byzantine Fault Tolerance." *OSDI*, 1999.
13. Gilbert, S. & Lynch, N. "Brewer's Conjecture and the Feasibility of Consistent, Available, Partition-Tolerant Web Services." *ACM SIGACT News* 33(2): 51–59, 2002.
14. Dean, J. & Ghemawat, S. "MapReduce: Simplified Data Processing on Large Clusters." *OSDI*, pp. 137–150, 2004.
15. DeCandia, G. et al. "Dynamo: Amazon's Highly Available Key-Value Store." *SOSP*, pp. 205–220, 2007.
16. Vogels, W. "Eventually Consistent." *ACM Queue* 6(6): 14–19, 2009.
17. Shapiro, M., Preguiça, N., Baquero, C., & Zawirski, M. "Conflict-free Replicated Data Types." *SSS 2011*, Springer, pp. 386–400, 2011.
18. Kreps, J. "The Log: What Every Software Engineer Should Know About Real-Time Data's Unifying Abstraction." 2013.
19. Ongaro, D. & Ousterhout, J. "In Search of an Understandable Consensus Algorithm." *USENIX ATC*, pp. 305–319, 2014.

---

*Loop MMT™ · Distributed Systems Knowledge Pack · v1*
*11 April 2026 · © 2026 Shea Gunther · CC BY-NC 4.0*
