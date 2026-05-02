# Fourier Series & Transform Knowledge Pack · v1

*Loop MMT™ · 9 April 2026*


> **About This Document**
>
> Reference document on Fourier series and the Fourier transform for AI advisory conversations. Covers decomposition of functions into sinusoidal components, convergence behavior, the discrete Fourier transform and FFT, and applications across physics, engineering, and mathematics. This pack is the prerequisite for the Nyquist-Shannon Sampling Theory pack already in the corpus — that pack assumes Fourier decomposition without proving it. This pack provides the machinery.
>
> The board needs this for three reasons. First, it is the formal basis for the sampling theory that underpins the "how many observers" question. Second, it provides vocabulary for talking about signal complexity, bandwidth, and spectral content with precision rather than analogy. Third, the decomposition principle — that any sufficiently well-behaved function can be expressed as a sum of orthogonal components — is the mathematical structure underneath multi-perspective analysis. Full citations appear in the References section.
>


## The Core Idea


### Decomposition

A complicated repeating pattern can be broken into a sum of simple oscillations. Each oscillation has a **frequency** (how fast it repeats), an **amplitude** (how large it is), and a **phase** (where in its cycle it starts). The original pattern is the sum of all these oscillations. The collection of oscillations — with their frequencies, amplitudes, and phases — is the decomposition.

For periodic functions satisfying mild regularity conditions (the Dirichlet conditions, Section 4), this is not an approximation. The sum converges to the original function exactly. The decomposition *is* the function, written in a different language.

The two languages are the **time domain** (the signal as it varies over time or space) and the **frequency domain** (the signal described as a collection of frequencies with their amplitudes and phases). Same information, different representation. Fourier analysis translates between them.


### Why Sinusoids

Sinusoids are **eigenfunctions of linear time-invariant (LTI) systems**. When a sinusoid enters an LTI system, it exits as a sinusoid of the same frequency — the system can change the amplitude and phase but not the frequency or waveform shape. No other function family has this property in general.

The consequence: decompose an input into sinusoids, track what happens to each one independently, and recombine the results to get the output. The system's effect on sinusoids completely determines its effect on everything else.


> **Why it works everywhere**
>
> Fourier analysis is universal because the physical world is dominated by linear systems and near-linear approximations of nonlinear ones. Maxwell's equations, the Schrödinger equation, the heat equation, the wave equation — all linear. Fourier decomposition converts partial differential equations into algebraic equations, one frequency at a time. This is why Fourier appears in every domain that solves differential equations, which is nearly every quantitative domain.
>


### Orthogonality

Two functions are **orthogonal** over an interval if their inner product (the integral of their product over that interval) is zero. Sinusoids at different frequencies are orthogonal over a complete period:

∫₀ᵀ sin(2πmt/T) · sin(2πnt/T) dt = 0   (m ≠ n)

    ∫₀ᵀ cos(2πmt/T) · cos(2πnt/T) dt = 0   (m ≠ n)

    ∫₀ᵀ sin(2πmt/T) · cos(2πnt/T) dt = 0   (all m, n)

This orthogonality makes the decomposition computable. To find how much of a particular frequency is present, multiply the signal by a sinusoid at that frequency and integrate. Orthogonality guarantees that every other frequency contributes zero — only the target frequency responds. Each coefficient is independently determinable.


> **Orthogonality and the board**
>
> Orthogonal components do not interfere with each other's measurement. Any one coefficient can be determined without knowing the others. The advisory analog: truly orthogonal perspectives can be evaluated independently. Ed's structural analysis does not contaminate Theo's spatial reasoning, and vice versa. The degree to which board perspectives are genuinely orthogonal — rather than correlated — determines whether they can be combined without crosstalk.
>


## The Fourier Series


### Periodic Functions and Harmonics

A function f(t) is **periodic** with period T if f(t + T) = f(t) for all t. The **fundamental frequency** is f₀ = 1/T. All frequencies in the Fourier series are integer multiples of f₀ — the **harmonics**. The first harmonic is f₀, the second is 2f₀, the third is 3f₀, and so on.


### Trigonometric Form

The Fourier series of a periodic function f(t) with period T:

f(t) = a₀/2 + Σₙ₌₁^∞ [aₙ cos(2πnt/T) + bₙ sin(2πnt/T)]

The coefficients are computed by:

a₀ = (2/T) ∫₀ᵀ f(t) dt    (the average value — the DC component)

    aₙ = (2/T) ∫₀ᵀ f(t) cos(2πnt/T) dt

    bₙ = (2/T) ∫₀ᵀ f(t) sin(2πnt/T) dt

The a₀/2 term is the mean value over one period — the level around which everything oscillates. Each subsequent pair (aₙ, bₙ) captures the nth harmonic's contribution.


### Complex Exponential Form

The trigonometric form is intuitive but algebraically heavy. Using Euler's formula e^iθ = cos θ + i sin θ, the series compresses to:

f(t) = Σₙ₌₋∞^∞ cₙ e^i2πnt/T

cₙ = (1/T) ∫₀ᵀ f(t) e^−i2πnt/T dt

Negative frequencies are mathematical bookkeeping, not physical reality. For real-valued signals, c₋ₙ = cₙ* (complex conjugate), which guarantees the imaginary parts cancel. The complex form is preferred in mathematics and engineering because exponential arithmetic is simpler than trigonometric identities, and it generalizes directly to the Fourier transform.

Each cₙ encodes amplitude and phase simultaneously: |cₙ| is the amplitude, arg(cₙ) is the phase, and |cₙ|² is the power at frequency n.


### Example: Square Wave

A square wave alternating between +1 and −1 with period T:

f(t) = (4/π) Σₖ₌₀^∞ [1/(2k+1)] sin(2π(2k+1)t/T)

Only odd harmonics appear; even harmonics are zero by the wave's symmetry. The amplitudes decay as 1/n — slowly. This slow decay is a direct consequence of the discontinuity at the jump between +1 and −1. Sharp features require high-frequency components with significant amplitude. Smooth functions have rapidly decaying coefficients. This regularity-decay relationship is fundamental and returns in Section 4.


## The Fourier Transform


### From Series to Transform

The Fourier series works for periodic functions. Non-periodic functions need the **Fourier transform** — the limiting case as the period T → ∞. As T grows, the harmonic spacing 1/T shrinks toward zero, the discrete sum becomes a continuous integral, and the series coefficients become a continuous spectral density function.


### The Transform Pair

**Forward transform** (time → frequency):

F(ω) = ∫₋∞^∞ f(t) e^−iωt dt

**Inverse transform** (frequency → time):

f(t) = (1/2π) ∫₋∞^∞ F(ω) e^iωt dω

Convention note: the placement of the 1/2π factor varies. Some authors split it as 1/√(2π) on each transform. The physics convention uses ordinary frequency ν (Hz) rather than angular frequency ω (rad/s). Results are identical — only the variable and normalization differ.

F(ω) is the **spectrum** — a complex-valued function of frequency encoding the amplitude and phase of each frequency component as a continuous density, rather than the discrete coefficients of the Fourier series.


### Existence and Extensions

The Fourier transform exists classically for absolutely integrable functions (∫|f(t)| dt < ∞). This excludes periodic functions and constants, which do not decay at infinity. The theory extends to cover these via **distributions** (generalized functions), developed by Laurent Schwartz in the 1940s. The Fourier transform of a constant is a Dirac delta; the transform of a periodic function is a sum of deltas at the harmonics. This extension unifies the Fourier series and the Fourier transform within a single framework.


## Convergence


### Dirichlet Conditions

Sufficient conditions for pointwise convergence were first established by Peter Gustav Lejeune Dirichlet in 1829. The **Dirichlet conditions**: (1) f has finitely many discontinuities per period, each of finite size; (2) f has finitely many extrema per period; (3) f is absolutely integrable over one period. Under these conditions, the Fourier series converges to f(t) at every continuity point. At a jump discontinuity, it converges to the midpoint [f(t⁺) + f(t⁻)]/2.

Camille Jordan later generalized this to functions of **bounded variation** (the Dirichlet-Jordan test) — any bounded variation function is the difference of two monotone functions, a strictly larger class. Any signal physically producible in a laboratory satisfies these conditions.


### Stronger Results

The Dirichlet conditions govern pointwise convergence. Deeper results address other modes:

**L² (mean-square) convergence.** The Riesz-Fischer theorem (Frigyes Riesz and Ernst Fischer, independently, 1907) established that every square-integrable function's Fourier series converges in the L² norm. This result placed Fourier analysis on the rigorous foundation of Hilbert space theory — the space of square-integrable functions and the space of square-summable coefficient sequences are isomorphic.

**Almost-everywhere pointwise convergence.** Nikolai Luzin conjectured in 1913 that L² Fourier series converge pointwise almost everywhere. This stood open for over fifty years. In 1923, Andrey Kolmogorov showed the result fails for L¹ functions, constructing an integrable function whose Fourier series diverges everywhere — demonstrating that some regularity beyond mere integrability is needed. Lennart Carleson proved Luzin's conjecture in 1966, establishing that L² is sufficient. Richard Hunt later extended the result to Lp for all p > 1.


### The Gibbs Phenomenon

At a jump discontinuity, partial sums of the Fourier series overshoot the function value. The overshoot is given by the **Wilbraham constant**:

w = (1/2)(2·Si(π)/π − 1) ≈ 0.08949

where Si(x) = ∫₀ˣ (sin t / t) dt is the sine integral. The overshoot is approximately **8.95% of the jump height**. Adding more terms makes the ringing narrower but does not reduce the peak — it persists at the same height no matter how many harmonics are included. The partial sums converge in energy (L²) but not uniformly at discontinuities.

The phenomenon was first analyzed by Henry Wilbraham in 1848. His paper was forgotten. J. Willard Gibbs rediscovered it in 1899, and Maxime Bôcher named it in 1906. It is more accurately called the Wilbraham-Gibbs phenomenon.


> **Practical consequences**
>
> Truncating a Fourier series to N terms introduces deterministic ringing near every discontinuity. In signal processing: ringing near sharp transitions. In imaging: halo artifacts near edges. In spectral analysis: energy spreading across bins (spectral leakage). The magnitude is predictable (~9% of the jump). **Windowing functions** (Hamming, Hanning, Blackman, Kaiser) reduce the ringing by smoothing the truncation, at the cost of reduced frequency resolution. **Fejér summation** — averaging the partial sums (Cesàro means) rather than taking them directly — eliminates the Gibbs overshoot entirely, at the cost of broader spectral peaks. Both are uncertainty-principle tradeoffs.
>


### Coefficient Decay Rate

A function's smoothness determines how fast its Fourier coefficients fall off:


| Function Regularity | Coefficient Decay | Example |
| --- | --- | --- |
| Discontinuous | ~1/n | Square wave |
| Continuous, not differentiable | ~1/n² | Triangle wave |
| k-times differentiable | ~1/n^k+1 | Smooth bumps with finite derivatives |
| Infinitely differentiable (C^∞) | Faster than any 1/n^k | Gaussian |
| Analytic (convergent Taylor series) | Exponential: ~e^−αn | Smooth periodic functions |

This is a deep duality: regularity in one domain maps to decay rate in the other. Sharp features carry a heavy spectral footprint — substantial amplitude at high frequencies. Smooth features concentrate their energy in low frequencies.


> **Bandwidth-regularity duality**
>
> A function's effective bandwidth is set by its roughness. Smooth functions are narrowband; rough functions are wideband. This is why the Nyquist rate depends on bandwidth — bandwidth measures complexity, and complexity is ultimately how much local variation exists. The coefficient decay rate is the formal statement of this relationship.
>


## Properties That Matter


### Linearity

The Fourier transform is linear: ℱ{af + bg} = aF + bG. The spectrum of a mixture is the mixture of the spectra. Components contribute independently.


### The Convolution Theorem

**Convolution in one domain equals multiplication in the other.** If h = f ∗ g (where (f ∗ g)(t) = ∫ f(τ) g(t−τ) dτ), then H(ω) = F(ω) · G(ω).

Convolution is the mathematical operation describing how a system transforms its input — an integral for every output point. Multiplication is trivial. The Fourier transform converts the hard computation into an easy one: transform both functions, multiply pointwise, transform back.

This is how filtering works in practice. A filter's frequency response H(ω) specifies how each frequency is amplified or attenuated. Applying the filter to a signal is multiplication in the frequency domain.


> **Beyond signal processing**
>
> Any operation where the output at a point is a weighted average of nearby input values is a convolution: blurring an image, smoothing data, computing a moving average, propagating a wave. The convolution theorem gives every one of these a frequency-domain interpretation. This is not merely a computational shortcut — it is a structural statement about how linear operations work.
>


### Parseval's Theorem

Energy is conserved across domains:

∫₋∞^∞ |f(t)|² dt = (1/2π) ∫₋∞^∞ |F(ω)|² dω

Total energy in the time domain equals total energy in the frequency domain. |F(ω)|² is the **power spectral density** — how the signal's energy is distributed across frequencies.


### The Uncertainty Principle

A function cannot be simultaneously concentrated in both time and frequency. With σₜ and σω denoting the standard deviations of the time and frequency distributions:

σₜ · σω ≥ 1/2

This is the **Gabor limit** (Dennis Gabor, 1946). A short pulse has a wide spectrum; a pure tone extends forever in time. The Gaussian achieves the minimum product — it is the most simultaneously concentrated function possible in both domains.

The Heisenberg uncertainty principle Δx · Δp ≥ ℏ/2 is a special case. Position-space and momentum-space wavefunctions are Fourier transform pairs, related by the de Broglie relation p = ℏk. The quantum uncertainty is Fourier uncertainty applied to matter waves.


> **A mathematical identity, not a measurement limitation**
>
> The uncertainty principle is not about imperfect instruments. It is a theorem about the Fourier transform. A function sharply localized in one domain is *necessarily* spread in the other — this is a structural property of the mathematics, not a constraint imposed by physical measurement.
>


### Shift Properties

**Time shift:** shifting f(t) by t₀ multiplies F(ω) by e^−iωt₀. The magnitude spectrum is unchanged — only phases shift. A signal's frequency content does not depend on when it occurs.

**Frequency shift (modulation):** multiplying f(t) by e^iω₀t shifts the spectrum to F(ω − ω₀). This is the principle behind AM radio: multiply audio by a carrier sinusoid to move its spectrum to the transmission frequency.


## The DFT & FFT


### The Discrete Fourier Transform

Computers operate on finite, discrete data. The **Discrete Fourier Transform (DFT)** acts on N samples:

X[k] = Σₙ₌₀^N−1 x[n] e^−i2πkn/N    (k = 0, 1, ..., N−1)

x[n] = (1/N) Σₖ₌₀^N−1 X[k] e^i2πkn/N

N time-domain samples become N frequency-domain values. The transform is exact — no approximation. Frequency bins correspond to frequencies k/(NT) where T is the sampling interval. For real inputs, only the first N/2 + 1 bins are independent; the rest are conjugate symmetric.


### The Fast Fourier Transform

Computing the DFT directly requires N² complex multiplications. The **Fast Fourier Transform (FFT)** exploits symmetries in the complex exponential to compute the identical result in O(N log N) operations. For N = 10⁶, this is the difference between ~10¹² operations and ~2 × 10⁷ — roughly the difference between days and milliseconds on a workstation.

The algorithm has a long pedigree. Carl Friedrich Gauss used an equivalent procedure around 1805 to interpolate the orbits of the asteroids Pallas and Juno. His work was unpublished, written in Latin, and found posthumously (collected works, 1866). The technique was independently rediscovered by Danielson and Lanczos in 1942 (who did not analyze its asymptotic complexity). James Cooley and John Tukey published the modern formulation in 1965 — Tukey reportedly conceived the idea during a meeting of President Kennedy's Science Advisory Committee, where the topic was detecting Soviet nuclear tests via seismographic arrays.

The FFT is not a different transform. It is an efficient algorithm for computing the DFT exactly. Its publication transformed digital signal processing, imaging, telecommunications, and scientific computing from theoretically possible to practically feasible.


> **Feasibility vs. possibility**
>
> The FFT is the canonical example of an algorithm that made an entire field practical without changing any of its mathematics. Before the FFT, Fourier analysis of large datasets required computational resources that did not exist. The algorithm did not add new theory — it made existing theory usable. When the board evaluates whether something is "possible," the distinction between mathematical possibility and computational feasibility is frequently the distinction that matters.
>


### Resolution Limits

The DFT of N samples at sampling rate fs has **frequency resolution** Δf = fs/N = 1/(total observation time). Two frequencies closer than Δf cannot be distinguished. Longer observation windows give finer frequency resolution; higher sampling rates extend the frequency range but do not improve resolution.

This is the discrete uncertainty principle: frequency resolution × observation time ≥ 1. Fine frequency discrimination requires patience.


## Where Fourier Shows Up


### Acoustics

Every sound is a superposition of sinusoids. Musical timbre — why a violin sounds different from a clarinet on the same note — is determined by which harmonics are present and at what relative amplitudes. The human cochlea performs an approximate Fourier decomposition mechanically, with different positions along the basilar membrane resonating at different frequencies. Audio compression (MP3, AAC) transforms audio to the frequency domain and discards components the ear cannot perceive.


### Optics and Imaging

A lens performs a Fourier transform optically — the light field at the focal plane is the Fourier transform of the input field. This is wave optics, not metaphor. Diffraction patterns are Fourier transforms of aperture shapes. The Abbe diffraction limit on optical resolution is a direct consequence of finite aperture cutting off high spatial frequencies. JPEG compression uses the Discrete Cosine Transform, a real-valued DFT variant.


### Quantum Mechanics

Position-space and momentum-space wavefunctions are Fourier transform pairs. The Heisenberg uncertainty principle is the Fourier uncertainty principle applied to this pair via the de Broglie relation. Energy eigenstates are the Fourier modes of quantum time evolution — the Hamiltonian is diagonal in the energy eigenbasis, exactly as a classical system's transfer function is diagonal in the Fourier basis.


### Heat Conduction

Fourier invented the series to solve this problem. Temperature distributions decompose into spatial harmonics, each decaying exponentially in time at a rate proportional to the square of its frequency. Sharp thermal gradients (high-frequency content) vanish fastest; broad temperature variations (low frequency) persist longest. A hot pan loses its edge-heat quickly but retains bulk warmth — that is frequency-dependent decay.


### Number Theory

The DFT over finite groups (ℤ/nℤ) underpins results in number theory. Dirichlet used Fourier analysis on finite groups — via what are now called Dirichlet characters — to prove that there are infinitely many primes in any arithmetic progression with coprime first term and common difference. The Poisson summation formula, which bridges Fourier series and transforms, appears throughout analytic number theory in lattice-point counting and the theory of theta functions.


### Partial Differential Equations

Separation of variables in PDE theory produces Fourier series naturally. The wave equation, heat equation, Laplace equation, and Schrödinger equation all admit solutions as superpositions of sinusoidal modes, each evolving independently. Fourier analysis is not one technique among many for PDEs — it is the foundational method that makes the subject tractable.


### Time-Series Analysis

The **periodogram** (|DFT|² of a time series) estimates the power spectrum and can reveal periodicities invisible in raw data. The **Wiener-Khinchin theorem** states that the power spectrum equals the Fourier transform of the autocorrelation function — connecting spectral analysis directly to the statistical structure of random processes.


## What Goes Wrong


### Spectral Leakage

The DFT implicitly assumes the N-sample window repeats periodically. When the signal is not an exact integer number of periods within the window, the periodic extension has artificial discontinuities at the boundaries, spreading each frequency's energy into neighboring bins. This is **spectral leakage**.

The DFT computes correctly — it is faithfully transforming the windowed signal. The issue is that the windowed signal differs from the original. Rectangular windowing is implicit multiplication in time, which is convolution with a sinc in frequency, which smears every spectral peak. Windowing functions (Hamming, Hanning, Blackman) taper the edges, trading leakage for wider main lobes. Another instance of the uncertainty principle.


### Nonstationarity

The Fourier transform assumes stationarity — that spectral content does not change over time. A chirp (frequency increasing over time) has a Fourier transform that shows which frequencies are present but not when. For time-varying signals, the **Short-Time Fourier Transform (STFT)** applies the DFT to short overlapping windows, producing a spectrogram. Resolution trades off per the uncertainty principle: short windows give good time resolution but poor frequency resolution; long windows give the reverse. Wavelet transforms offer a multi-resolution alternative — short windows at high frequencies, long windows at low frequencies.


### Nonlinear Systems

Fourier analysis requires linearity. When a system is nonlinear, superposition fails — analyzing each frequency independently no longer predicts behavior. Nonlinear systems generate frequencies not present in the input (intermodulation products, harmonic distortion). Fourier can describe the output of a nonlinear system but cannot predict it from the input spectrum alone.

For mildly nonlinear systems, perturbation theory applies Fourier analysis to a linearized approximation. Strongly nonlinear systems require different tools: phase-space methods, bifurcation theory, and the techniques covered in the Chaos Theory KP in the corpus.


## History


### Timeline


| Year | Person | Contribution |
| --- | --- | --- |
| ~1805 | Gauss | Unpublished FFT-like algorithm for computing trigonometric interpolation coefficients. Used to determine asteroid orbits (Pallas, Juno). Written in Latin; published posthumously 1866 in collected works. |
| 1807 | Fourier | Read memoir on heat conduction to the Paris Institute (21 December). Committee — Lagrange, Laplace, Monge, Lacroix — acknowledged novelty but denied publication. Lagrange specifically objected to trigonometric series representing arbitrary functions. |
| 1822 | Fourier | Published *Théorie analytique de la chaleur*. He had won the Institute's 1811 prize with an expanded version of the memoir, though even the prize committee's report critiqued his rigor. |
| 1829 | Dirichlet | First rigorous convergence proof for Fourier series under sufficient conditions (piecewise monotone functions). |
| 1848 | Wilbraham | First to analyze the overshoot at discontinuities. The paper was promptly forgotten. |
| 1854 | Riemann | Habilitationsschrift on trigonometric series. The Riemann integral was partly motivated by Fourier convergence questions. Published posthumously 1867. |
| 1899 | Gibbs | Rediscovered the discontinuity overshoot; published in *Nature*. |
| 1906 | Bôcher | Named the overshoot "Gibbs phenomenon." |
| 1907 | Riesz, Fischer | Independently established the L² isomorphism between functions and Fourier coefficients. Placed Fourier analysis on Hilbert space foundations. |
| 1913 | Luzin | Conjectured that L² Fourier series converge pointwise almost everywhere. |
| 1923 | Kolmogorov | Constructed an L¹ function whose Fourier series diverges everywhere — the negative result showing L² regularity is needed. |
| 1946 | Gabor | "Theory of communication" — the uncertainty principle for signals. |
| 1965 | Cooley & Tukey | Published the FFT algorithm. O(N²) → O(N log N). Revolutionized digital signal processing. |
| 1966 | Carleson | Proved Luzin's conjecture: Fourier series of L² functions converge pointwise a.e. Extended by Hunt to L^p (p > 1). |


> **On Fourier's memoir**
>
> Lagrange believed that functions with discontinuities could not be represented by trigonometric series. He was wrong in a narrow mathematical sense — the series does converge, with the Gibbs caveat at jumps — but his demand for rigor was productive. The tension between Fourier's boldness and the committee's skepticism drove sixty years of foundational work in real analysis. Dirichlet's convergence proof, Riemann's integral, the Riesz-Fischer theorem, and Carleson's theorem are all downstream consequences of the questions Fourier's claim raised but could not answer. Fourier asserted the result before the proof existed. The proof required inventing most of modern analysis.
>


## Board Connection


### Decomposition as Advisory Method

Fourier decomposition models what multi-perspective analysis does. The board takes a complex question (the signal) and decomposes it into perspectives (frequency components) that can be evaluated independently (orthogonality) and recombined into a complete answer (synthesis).

Two properties determine whether the decomposition is working:

**Orthogonality of perspectives.** If two members' analyses are correlated — they see the same things for the same reasons — they are not independent components. The decomposition gains less than the headcount suggests. Ed's structural analysis and Chen Wei's formal analysis are approximately orthogonal: genuinely different angles on the same problem. Ed and Graham have higher correlation — both are systems people. Theo and Margaux are strongly orthogonal to everyone else: neither is a computer scientist, and their contributions lie in dimensions the rest of the board does not naturally occupy.

**Completeness of the basis.** A complete basis can represent any function in its domain. If the board's perspectives have blind spots — categories of problems no member would naturally notice — the basis is incomplete and certain aspects of the problem will go unanalyzed. Margaux's addition corrected a gap (naming/branding). Sable corrected another (formal computational analysis). Each addition increased the basis's representational power.


### Convergence and Reconstruction

When a fresh instance loads an EOD handoff and reconstructs session state, it is performing reconstruction from finite Fourier coefficients. The mapping:


| Fourier Concept | Session Reconstruction |
| --- | --- |
| Number of terms N | Number of documents and perspectives available to the new instance |
| Coefficient decay rate | Document quality. Well-structured documents = fast decay (faithful reconstruction with fewer). Messy or incomplete documents = slow decay (many needed). |
| Gibbs phenomenon | Reconstruction artifacts at session "discontinuities" — sharp pivots, reversed decisions, abandoned assumptions |
| Windowing | The EOD handoff as window function — its framing determines where reconstruction ringing occurs |
| Spectral leakage | Adjacent session context bleeding into the current reconstruction, creating signals that were not part of the actual session |


> **Gibbs at the handoff boundary**
>
> The Gibbs phenomenon predicts that reconstruction is worst exactly where the signal changes most abruptly. For session reconstruction: the moments where the project pivoted, where a decision reversed prior direction, where an assumption was abandoned. These are the discontinuities. The new instance will overshoot near these points — constructing a story that exaggerates the magnitude of the pivot or smooths it into a gradual evolution that never happened. The ~9% overshoot heuristic: expect reconstruction of sharp transitions to be roughly 10% wrong in magnitude. The handoff document's job is to flag discontinuities explicitly so the instance knows where to expect its own artifacts.
>


### Fixed by Design Through Fourier

**Bandwidth management.** The Standard constrains session complexity. In Fourier terms, this is bandwidth-limiting. A bandwidth-limited signal requires fewer samples for faithful reconstruction (Nyquist). If sessions had unbounded complexity, no finite set of handoff documents would be sufficient. The Standard is both an anti-aliasing filter and a bandwidth limiter.

**Orthogonal enforcement.** FBD principles that enforce separation of concerns — routing logic separate from presentation, event ledger separate from derived state — are enforcing orthogonality between components. Orthogonal components can be modified, tested, and reconstructed independently. Entangled components produce crosstalk: changing one corrupts the measurement of others.

**Decay rate as a quality metric.** The regularity-decay duality provides a formal quality measure. Well-structured documents are "smooth" — their information varies gradually and predictably — and reconstruct faithfully from fewer terms. Documents with internal inconsistencies, unstated assumptions, or abrupt shifts are "rough," requiring much more supporting context for faithful reconstruction. A document that stands alone has low effective bandwidth. A document that requires extensive supplementary material has high bandwidth. Sable's analysis terminal can quantify this: the decay rate of a document's "spectral" representation — how quickly its essential content can be captured with decreasing levels of summary — is a proxy for structural quality.


### The Uncertainty Principle in Practice

The board cannot simultaneously achieve high resolution in "what" and "when." A session that examines a problem in fine structural detail (high frequency resolution) requires extended discussion (long observation window). A quick triage (short window) can detect that something is wrong but not pinpoint what (low frequency resolution).

This is structural, not a process failure. Sessions that attempt deep analysis within a short window violate the uncertainty principle and produce artifacts — apparent precision unsupported by the observation time. The board should declare the mode: long-window analysis or short-window triage. Mixing modes produces the advisory equivalent of spectral leakage: apparent findings that are actually artifacts of the mismatch between the question's complexity and the time allocated.


## References


### Foundational Works

Fourier, J. B. J. (1822). *Théorie analytique de la chaleur*. Paris: Firmin Didot. English translation by Alexander Freeman, 1878.

Dirichlet, P. G. L. (1829). Sur la convergence des séries trigonométriques qui servent à représenter une fonction arbitraire. *Journal für die reine und angewandte Mathematik*, 4, 157–169.

Wilbraham, H. (1848). On a certain periodic function. *The Cambridge and Dublin Mathematical Journal*, 3, 198–201.

Riemann, B. (1854/1867). Über die Darstellbarkeit einer Function durch eine trigonometrische Reihe. *Abh. der Königlichen Gesellschaft der Wissenschaften zu Göttingen*, 13. Habilitationsschrift 1854; published posthumously 1867.

Gibbs, J. W. (1899). Fourier's series. *Nature*, 59, 200 and 606.

Riesz, F. (1907). Sur les systèmes orthogonaux de fonctions. *Comptes rendus*, 144, 615–619.

Fischer, E. (1907). Sur la convergence en moyenne. *Comptes rendus*, 144, 1022–1024.

Gabor, D. (1946). Theory of communication. *Journal of the IEE*, 93(26), 429–457.

Carleson, L. (1966). On convergence and growth of partial sums of Fourier series. *Acta Mathematica*, 116, 135–157.


### The FFT

Cooley, J. W. & Tukey, J. W. (1965). An algorithm for the machine calculation of complex Fourier series. *Mathematics of Computation*, 19(90), 297–301.

Heideman, M. T., Johnson, D. H., & Burrus, C. S. (1984). Gauss and the history of the Fast Fourier Transform. *IEEE ASSP Magazine*, 1(4), 14–21.


### Textbooks

Stein, E. M. & Shakarchi, R. (2003). *Fourier Analysis: An Introduction*. Princeton University Press.

Oppenheim, A. V. & Willsky, A. S. (1997). *Signals and Systems*. 2nd ed. Prentice Hall.

Körner, T. W. (1988). *Fourier Analysis*. Cambridge University Press.

Katznelson, Y. (2004). *An Introduction to Harmonic Analysis*. 3rd ed. Cambridge University Press.


### Historical Sources

Hewitt, E. & Hewitt, R. (1979). The Gibbs-Wilbraham phenomenon: An episode in Fourier analysis. *Archive for History of Exact Sciences*, 21, 129–160.

Grattan-Guinness, I. (1972). *Joseph Fourier, 1768–1830*. MIT Press.


### Corpus Cross-References

**Nyquist-Shannon Sampling Theory KP** — depends on this pack. The sampling theorem concerns band-limited functions; band-limiting is a frequency-domain constraint that this pack defines.

**Information Theory KP** — Shannon's continuous channel capacity theorems use Fourier-domain arguments. The water-filling theorem for optimal power allocation is a frequency-domain optimization.

**Chaos Theory KP** — Fourier analysis of chaotic systems reveals broadband spectra with no dominant frequencies — the spectral signature of aperiodicity. The failure of Fourier to find structure is itself the diagnostic.
