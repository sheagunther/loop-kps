# Control Theory — Feedback, Stability, and the Mathematics of Guided Systems

**Loop MMT™ · Knowledge Pack · v1 · 10 April 2026**

---

## About This Document

Control theory is the mathematics of systems that regulate their own behavior through feedback. This pack covers: feedback fundamentals, PID control, stability (Lyapunov and BIBO), Kalman's observability and controllability, robustness via gain and phase margins, finite state machines with guarded transitions, cascade control, adaptive control, and failure modes including integrator windup. 10 key results, 5 reference tables, 14 sources. Built for AI advisors who need to reason about system regulation, stability analysis, and the formal specification of collaborative process architectures.

---

## 1 · Feedback: The Fundamental Mechanism

### Open-Loop and Closed-Loop Systems

An **open-loop system** computes its output from its input alone, with no measurement of the result. A motor set to a fixed voltage runs at whatever speed the voltage produces — if the load increases, it slows down and the controller has no way to know or respond.

A **closed-loop (feedback) system** measures its own output and uses the measurement to correct its behavior. The fundamental operation: measure the output, compare it to the desired value (the **setpoint** or **reference**), compute the difference (the **error**), and adjust the input to reduce the error. This measure-compare-adjust cycle is the **feedback loop**.

### Components of a Feedback System

Every feedback control system has: a **plant** (the system being controlled), a **sensor** (measuring the output), a **reference signal** (desired output), a **comparator** (computing error = reference − measured output), and a **controller** (computing the control input from the error). The controller drives the plant; the sensor closes the loop by reporting the plant's output back to the comparator.

> **KEY: Negative feedback enables self-regulation.** In negative feedback, the measured output is subtracted from the reference. When the output exceeds the reference, the error is negative and the controller reduces its input. When the output falls short, the error is positive and the controller increases its input. This self-correcting mechanism is what makes regulation possible without a perfect model of the plant. Feedback compensates for modeling errors, disturbances, and parameter changes — it trades knowledge of the plant for knowledge of the output.

### History

Feedback predates its mathematics. James Watt's centrifugal governor (1788) regulated steam engine speed through purely mechanical feedback. The mathematical theory began with James Clerk Maxwell's "On Governors" (1868). The frequency-domain foundations were laid by Harry Nyquist (1932) and Hendrik Bode (1940s) at Bell Labs, working on telephone amplifier stability. The modern state-space revolution was launched by Rudolf Kalman at the First IFAC Congress in Moscow (1960), introducing controllability, observability, and the algebraic framework that defines the field today.

---

## 2 · PID Control

**PID (Proportional-Integral-Derivative) control** is the dominant feedback algorithm in industry, first commercialized in 1939 and still the most widely deployed controller type. It computes a control output from three terms, each responding to a different temporal aspect of the error:

`u(t) = Kp·e(t) + Ki·∫e(τ)dτ + Kd·de(t)/dt`

where `e(t) = r(t) − y(t)` is the error, and Kp, Ki, Kd are tunable gains.

### The Three Terms

**Proportional (P):** Responds to the present error. Output is `Kp·e(t)` — directly proportional to the current magnitude of the error. Higher Kp gives faster response but cannot eliminate steady-state error and risks overshoot. With proportional control alone, some nonzero error must persist to generate a corrective signal.

**Integral (I):** Responds to accumulated past error. Output is `Ki·∫e(τ)dτ` — proportional to the time-integral of the error. As long as any error persists, the integral grows, eventually driving the steady-state error to zero. This property is called **perfect adaptation**. The cost: integral action slows the system and increases overshoot. It is also the source of integrator windup (Section 9).

**Derivative (D):** Responds to the rate of change of the error — it anticipates where the error is headed. Output is `Kd·de(t)/dt`. If the error is decreasing rapidly, derivative action reduces the control effort to prevent overshoot. In practice, the derivative is almost always filtered because raw differentiation amplifies high-frequency sensor noise.

| Term | Temporal Focus | Rise Time | Overshoot | Settling Time | SS Error |
|------|---------------|-----------|-----------|---------------|----------|
| **P** | Present | Decrease | Increase | Small change | Decrease (not eliminate) |
| **I** | Past | Decrease | Increase | Increase | Eliminate |
| **D** | Future | Minor change | Decrease | Decrease | No effect |

> **TIP: PID as temporal perspectives.** A PID controller integrates three temporal views: P sees where the system is now, I remembers where it has been, D anticipates where it is going. This is the simplest controller that uses past, present, and future information, which explains its near-universal applicability.

### Tuning

Selecting the gains Kp, Ki, Kd for a specific plant is called **tuning**. No single method works for all systems. The **Ziegler-Nichols method** (1942) sets I and D gains to zero, increases P until the system sustains oscillation, and derives all three gains from the critical gain and oscillation period. **Relay autotuning** (Åström & Hägglund) automates identification of the critical point. **Model-based methods** compute optimal gains from a plant model. In practice, tuning is often iterative.

---

## 3 · Stability

A feedback system is only useful if it is stable. Stability means that the output remains bounded and converges toward the desired value, rather than oscillating without limit or diverging.

### BIBO Stability

**Bounded-Input Bounded-Output (BIBO) stability:** a system is BIBO stable if every bounded input produces a bounded output. This is an external (input-output) characterization.

For LTI systems with transfer function G(s): BIBO stability holds iff all poles of G(s) lie in the open left half-plane (all poles have strictly negative real parts). Equivalently, the impulse response g(t) must be absolutely integrable: `∫₀^∞ |g(t)|dt < ∞`.

### Lyapunov Stability

Named after **Aleksandr Mikhailovich Lyapunov** (1857–1918), who presented the theory in his 1892 doctoral thesis "The General Problem of Stability of Motion" at Kharkov University (now V.N. Karazin Kharkiv National University).

**Lyapunov stable:** an equilibrium x* is Lyapunov stable if trajectories starting sufficiently close to x* remain close for all future time. Small perturbations don't grow.

**Asymptotically stable:** Lyapunov stable *and* trajectories converge to x* as t → ∞. For LTI systems ẋ = Ax, asymptotic stability holds iff all eigenvalues of A have strictly negative real parts.

**Exponentially stable:** asymptotically stable with a guaranteed minimum decay rate.

### Lyapunov's Direct Method

Construct a scalar **Lyapunov function** V(x) such that V(x) > 0 for all x ≠ 0 (positive definite), V(0) = 0, and dV/dt < 0 along system trajectories (negative definite time derivative). If such a V exists, the equilibrium is asymptotically stable.

For LTI systems ẋ = Ax: the quadratic function V(x) = xᵀPx, where P solves the **Lyapunov equation** AᵀP + PA = −Q (for any positive definite Q), provides a complete stability test.

> **KEY: Stability is about what happens to perturbations.** Every stability concept answers the same question: if the system is disturbed from its desired state, do the disturbances decay (stable), persist (marginally stable), or grow (unstable)?

### Relationship Between Stability Types

**Asymptotic stability → BIBO stability.** If all eigenvalues of A have strictly negative real parts, the system is both asymptotically and BIBO stable.

**BIBO stability does not imply asymptotic stability** in general, because the transfer function reveals only the controllable-and-observable modes. A system can have an unobservable unstable mode that doesn't appear in the transfer function. When the system is both controllable and observable, BIBO stability and asymptotic stability become equivalent for LTI systems.

> **NOTE: Practical stability tests.** The **Routh-Hurwitz criterion** determines stability algebraically from characteristic polynomial coefficients. The **Nyquist stability criterion** determines closed-loop stability from the open-loop frequency response by counting encirclements of (−1, 0).

---

## 4 · Observability and Controllability

Introduced by **Rudolf Emil Kalman** at the First IFAC Congress in Moscow, 1960.

### Controllability

A system is **controllable** if, for any initial state and any desired final state, there exists a control input that transfers the system between them in finite time.

**Kalman Rank Test:** ẋ = Ax + Bu is controllable iff the controllability matrix `𝒞 = [B | AB | A²B | ⋯ | Aⁿ⁻¹B]` has rank n.

### Observability

A system is **observable** if the initial state can be uniquely determined from the output measured over a finite time interval.

**Kalman Rank Test:** ẋ = Ax, y = Cx is observable iff the observability matrix `𝒪 = [C; CA; CA²; ⋯; CAⁿ⁻¹]` has rank n.

| Property | Question | Rank Test | Failure Consequence |
|----------|----------|-----------|-------------------|
| **Controllability** | Can inputs drive the state anywhere? | rank 𝒞 = n | Unreachable states |
| **Observability** | Can outputs reveal the full state? | rank 𝒪 = n | Hidden states |

### Canonical Decomposition

**Kalman's Canonical Structure Theorem** (1963): any LTI system decomposes into four subsystems — (1) controllable and observable, (2) controllable but unobservable, (3) uncontrollable but observable, (4) uncontrollable and unobservable. Only subsystem (1) determines input-output behavior.

### Duality

Controllability and observability are **dual**. The system (A, B) is controllable iff the dual system (Aᵀ, Bᵀ) is observable, where Bᵀ plays the role of the output matrix C. Controller design and observer design are the same mathematical problem viewed from dual perspectives.

> **WARN: Unobservable states can be unstable.** A system can be BIBO stable while containing an internally unstable mode that is unobservable. The system looks stable from outside while harboring a growing instability inside. This is why pole-zero cancellations are dangerous and why full stability analysis requires state-space examination.

---

## 5 · Robustness: Gain and Phase Margins

**Gain margin (GM):** how much the open-loop gain can increase before closed-loop instability. Measured at the phase crossover frequency (phase = −180°). Standard: **GM ≥ 6 dB** (factor of 2).

**Phase margin (PM):** how much additional phase lag the system tolerates at the gain crossover frequency (gain = 0 dB). PM ≈ 30° → ~35–40% overshoot; PM ≈ 45° → ~20–25% overshoot; PM ≈ 60° → ~10% overshoot. Approximate damping ratio: ζ ≈ PM/100 for PM in 30°–70°. Standard: **PM ≥ 45°**.

> **KEY: You cannot maximize both robustness and performance.** Wider margins mean more tolerance for uncertainty but slower response. Making a system arbitrarily robust is easy (reduce gain). Making it fast is easy (increase gain). Doing both is impossible. Every design is a point on the robustness-performance tradeoff curve.

Both margins must be adequate. A system can have excellent GM but poor PM (or vice versa). For MIMO systems, advanced tools (disk margins, μ-analysis, H∞) provide stronger guarantees.

---

## 6 · State Machines and Guarded Transitions

A **finite state machine (FSM)** consists of: a finite set of states, inputs, a transition function, and an initial state. At any instant the system occupies exactly one state. **Moore machines** produce output from state alone; **Mealy machines** from state and input.

A **guarded transition** fires only when both the trigger event occurs *and* a guard condition is true. Guards encode prerequisites and prevent premature transitions.

> **TIP: FSMs make requirements structural.** Modeling a process as an FSM with guarded transitions forces every transition requirement into a formal predicate. "When should we move to the next phase?" becomes a guard that either holds or doesn't. This is Fix by Design applied to process specification.

**Hybrid systems** combine continuous dynamics within states and discrete transitions between states. Most real-world controlled processes are hybrid.

---

## 7 · Cascade and Hierarchical Control

**Cascade control** nests a fast inner loop inside a slower outer loop. The outer controller's output becomes the inner controller's setpoint.

| Rule | Why |
|------|-----|
| Inner loop ≥3–4× faster than outer | Prevents destructive interaction between loops |
| Inner must causally influence outer | No causal link means no corrective path |
| Tune inner first | Outer loop sees closed inner loop as its actuator |
| Inner handles fast disturbances | Catches perturbations before they propagate |
| Outer handles slow disturbances | Manages drift and long-term tracking |

**Benefits:** Better disturbance rejection, faster response, improved precision. **Costs:** Additional complexity, second sensor, more tuning. Extends naturally to three or more levels with timescale separation at each.

---

## 8 · Adaptive Control

**Model Reference Adaptive Control (MRAC):** A reference model specifies desired behavior. An adjustment law modifies controller parameters to make the actual system track the reference model. Stability proven via Lyapunov methods. Developed by Parks (1966), Monopoli (1974).

**Self-Tuning Regulators (STR):** Online parameter estimator identifies the plant; controller parameters computed from the estimated model. Developed by Åström and Wittenmark at Lund University (1973).

**Gain Scheduling:** Pre-computed gain sets switched based on operating conditions. Common in aerospace. Not truly adaptive but handles known parameter variations.

> **WARN: Convergence and stability are not guaranteed.** If parameters change faster than the estimator tracks, if the input lacks **persistent excitation**, or if the plant class exceeds the algorithm's assumptions, adaptive controllers can fail in ways fixed controllers cannot.

---

## 9 · Control System Failure Modes

### Integrator Windup

When an actuator saturates, the feedback loop breaks — but the integral term keeps accumulating error. When the error reverses, the oversized integral causes massive overshoot. **Anti-windup methods:** (1) Clamping — freeze integrator at limits. (2) Back-calculation — feedback from actuator saturation discharges the integral. (3) Conditional integration — disable integral when saturated.

### Other Failure Modes

| Failure Mode | Mechanism | Countermeasure |
|-------------|-----------|---------------|
| **Integrator windup** | Integral accumulates during saturation | Anti-windup: clamping, back-calculation, conditional integration |
| **Actuator saturation** | Physical limits clip control signal | Output limiting, constraint-aware control, stay in linear range |
| **Sensor failure** | Measurement lost or corrupted | Redundant sensors, state estimators, fault detection |
| **Time delay** | Late feedback adds phase lag | Smith predictor, time-stamping, delay-aware design |

---

## 10 · Key Results Reference

| # | Result | Statement |
|---|--------|-----------|
| 1 | **PID Control Law** | u(t) = Kp·e(t) + Ki·∫e(τ)dτ + Kd·de(t)/dt |
| 2 | **BIBO Stability** | LTI system BIBO stable iff all poles in open LHP |
| 3 | **Lyapunov's Direct Method** | V(x) > 0, dV/dt < 0 → asymptotically stable (1892) |
| 4 | **Kalman Controllability** | rank [B, AB, ..., Aⁿ⁻¹B] = n (1960) |
| 5 | **Kalman Observability** | rank [C; CA; ...; CAⁿ⁻¹] = n (1960) |
| 6 | **Canonical Decomposition** | Four subsystems; only controllable-and-observable determines I/O (1963) |
| 7 | **Nyquist Criterion** | Closed-loop stability from open-loop encirclements of (−1, 0) (1932) |
| 8 | **Gain and Phase Margins** | GM ≥ 6 dB, PM ≥ 45° for robustness |
| 9 | **Cascade Control** | Fast inner loop inside slow outer loop; inner ≥3× faster |
| 10 | **Controllability-Observability Duality** | (A, B) controllable ↔ (Aᵀ, Bᵀ) observable (1960) |

---

## 11 · Board Connection: Control Theory and Loop MMT

The Session 32 collaborative process architecture is a control system. **Plant:** Claude instance. **Controller:** process architecture (phase gates, Ed's thread management). **Sensor:** instrument panel. **Reference:** session goal from handoff. **Error:** gap between current state and specification.

**PID mapping:** P = current error from spec. I = accumulated tech debt. D = rate of quality change (context pressure slope). "Pay tech debt immediately" is anti-windup.

**Phase gates as FSM:** Diverge → Converge → Formalize → Verify, each transition guarded by explicit conditions (sufficient breadth, board alignment, document completeness). Fix by Design — the machine checks guards, not memory.

**Cascade:** Inner loop (Ed's thread management, minutes) → middle loop (phase management, session segments) → outer loop (project management, days/weeks). Timescale separation is large and structurally favorable.

**Observability:** Instrument panel must surface all critical state. Missing measures create unobservable modes — the operator cannot control what they cannot see.

**Controllability:** Operator inputs (goals, thread direction, phase commands, wrap-and-handoff) must reach all important states. Unreachable states are uncontrollable modes to minimize.

**Perturbation stability:** Shea Walks (step disturbance), Thread Storms (high-frequency, handled by inner loop), Geoff (unmeasured disturbance requiring adequate gain margin). Empirically stable; gain margins not yet formally measured.

**Failure analogs:** Integrator windup → context saturation (anti-windup = wrap-and-handoff). Actuator saturation → per-response output limits. Sensor failure → missing observer documents. Time delay → inter-session latency (handoff document as Smith predictor).

> **PHI: Can this be formalized?** The mappings are structural, not metaphorical. The process has measurable state, observable outputs, controllable inputs, and dynamics. It can in principle be specified as a hybrid control system. Whether formalization yields useful stability proofs is open — the plant is nonlinear and poorly characterized. But qualitative application of control principles has already improved the methodology's robustness.

---

## References

1. Åström, K.J. and Murray, R.M. (2008/2021). *Feedback Systems*, 2nd ed. Princeton. Open access.
2. Åström, K.J. and Wittenmark, B. (1973). "On Self-Tuning Regulators." *Automatica*, 9:185–199.
3. Åström, K.J. (2021). "History of Adaptive Control." In *Encyclopedia of Systems and Control*, Springer.
4. Åström, K.J. and Rundqwist, L. (1989). "Integrator Windup and How to Avoid It." *Proc. ACC*, Vol. 2, pp. 1693–1698.
5. Doyle, J.C., Francis, B.A., and Tannenbaum, A.R. (1992). *Feedback Control Theory*. Macmillan.
6. Franklin, G.F., Powell, J.D., and Emami-Naeini, A. (2015). *Feedback Control of Dynamic Systems*, 7th ed. Pearson.
7. Kalman, R.E. (1960). "On the General Theory of Control Systems." *Proc. First IFAC Congress*, Moscow, pp. 481–492.
8. Kalman, R.E. (1963). "Mathematical Description of Linear Dynamical Systems." *SIAM J. Control*, 1:152–192.
9. Lyapunov, A.M. (1892). "The General Problem of Stability of Motion." Doctoral thesis, Kharkov.
10. Maxwell, J.C. (1868). "On Governors." *Proc. Royal Society London*, 16:270–283.
11. Nyquist, H. (1932). "Regeneration Theory." *Bell System Tech. J.*, 11:126–147.
12. Ogata, K. (2010). *Modern Control Engineering*, 5th ed. Prentice Hall.
13. Sterman, J.D. (2000). *Business Dynamics*. McGraw-Hill.
14. Tehrani, K.A. and Mpanda, A. (2012). "PID Control Theory." In *Introduction to PID Controllers*, IntechOpen.

---

*Loop MMT™ · Control Theory Knowledge Pack · v1 · 10 April 2026*
*© 2026 Shea Gunther · CC BY-NC 4.0*
