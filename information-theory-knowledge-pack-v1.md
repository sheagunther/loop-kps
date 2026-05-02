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
Information Theory Knowledge Pack
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
-   [1 · Entropy](#ch-entropy)
-   [2 · Joint, Conditional, Mutual](#ch-joint)
-   [3 · KL Divergence](#ch-divergence)
-   [4 · Source Coding](#ch-source)
-   [5 · Channel Coding](#ch-channel)
-   [6 · Rate-Distortion](#ch-rate-distortion)
-   [7 · Differential Entropy](#ch-differential)
-   [8 · Entropy Rate](#ch-entropy-rate)
-   [9 · Applications](#ch-applications)
-   [10 · Key Results](#ch-results-ref)
-   [References](#ch-refs)

::: {.content role="main"}
::: {#ch-abstract .abstract-box}
::: abstract-label
About This Document
:::

Reference document on Shannon\'s information theory for AI advisory conversations. Covers entropy, mutual information, source coding, channel coding, rate-distortion theory, and key applications. Founded on Shannon\'s 1948 paper and standard references (Cover & Thomas, MacKay). Draws on 8 sources.
:::

::: {#ch-entropy .chapter}
::: chapter-number
Section 1
:::

::: chapter-title
Shannon Entropy
:::

The **information content** (surprise) of an event with probability p is I(x) = −log₂ p(x) bits. Rare events carry more information; certain events carry none. The **Shannon entropy** of a discrete random variable X with probability mass function p is the expected information content:

H(X) = −∑~x~ p(x) log₂ p(x)

**Properties:** (1) H(X) ≥ 0, with equality iff X is deterministic. (2) H(X) ≤ log₂\|𝒳\| with equality iff X is uniformly distributed. (3) H is concave in the distribution p. (4) For binary X with P(X=1) = p: H(X) = H₂(p) = −p log p − (1−p) log(1−p) (the binary entropy function).

::: {.callout .key}
::: callout-label
What entropy measures
:::

Entropy is the average number of yes/no questions needed to determine the value of X, or equivalently, the minimum average number of bits per symbol needed to encode X losslessly. It measures *uncertainty* before observing X, and *information gained* after observing X. These are the same quantity.
:::
:::

::: {#ch-joint .chapter}
::: chapter-number
Section 2
:::

::: chapter-title
Joint, Conditional, and Mutual Information
:::

::: section
::: section-title
Joint and Conditional Entropy
:::

**Joint entropy:** H(X,Y) = −∑ p(x,y) log p(x,y). **Conditional entropy:** H(Y\|X) = −∑ p(x,y) log p(y\|x) --- the average remaining uncertainty about Y after observing X.

**Chain rule:** H(X,Y) = H(X) + H(Y\|X) = H(Y) + H(X\|Y). Generalizes: H(X₁,\...,X_n) = ∑ H(X_i \| X₁,\...,X\_{i-1}).

**Conditioning reduces entropy:** H(Y\|X) ≤ H(Y), with equality iff X and Y are independent. Knowing something never increases uncertainty on average.
:::

::: section
::: section-title
Mutual Information
:::

**Mutual information:** I(X;Y) = H(X) − H(X\|Y) = H(Y) − H(Y\|X) = H(X) + H(Y) − H(X,Y). It measures the information that X and Y share --- the reduction in uncertainty about X from observing Y (and vice versa). I(X;Y) ≥ 0, with equality iff X ⊥ Y (independent). I(X;Y) = I(Y;X) (symmetric).

**Data processing inequality:** If X → Y → Z forms a Markov chain, then I(X;Z) ≤ I(X;Y). Processing data cannot increase information. In particular, for any function f: I(X; f(Y)) ≤ I(X;Y).
:::
:::

::: {#ch-divergence .chapter}
::: chapter-number
Section 3
:::

::: chapter-title
KL Divergence and Cross-Entropy
:::

**Kullback-Leibler divergence** (relative entropy): D(p‖q) = ∑ p(x) log(p(x)/q(x)). Measures the \"cost\" of using distribution q to encode data from distribution p --- the extra bits needed beyond optimal. D(p‖q) ≥ 0 (Gibbs\' inequality), with equality iff p = q.

::: {.callout .warn}
::: callout-label
Not a metric
:::

KL divergence is NOT symmetric: D(p‖q) ≠ D(q‖p) in general. It also does not satisfy the triangle inequality. Despite being called a \"divergence,\" it is not a distance in the metric sense.
:::

**Cross-entropy:** H(p,q) = −∑ p(x) log q(x) = H(p) + D(p‖q). The average number of bits needed to encode data from p using a code optimized for q. Minimizing cross-entropy over q is equivalent to minimizing KL divergence, which is why cross-entropy is the standard loss function in machine learning classification.

**Mutual information as KL divergence:** I(X;Y) = D(p(x,y) ‖ p(x)p(y)) --- the KL divergence between the joint distribution and the product of marginals. This measures how far X and Y are from independence.
:::

::: {#ch-source .chapter}
::: chapter-number
Section 4
:::

::: chapter-title
Source Coding (Data Compression)
:::

::: section
::: section-title
Prefix Codes and Kraft\'s Inequality
:::

A **prefix-free code** (instantaneous code) is one where no codeword is a prefix of another --- it can be decoded symbol by symbol without ambiguity. **Kraft\'s inequality** (Kraft 1949): A prefix-free code with codeword lengths l₁, \..., l_n exists if and only if ∑ 2^−l_i^ ≤ 1. The **Kraft-McMillan inequality** extends this to all uniquely decodable codes.
:::

::: section
::: section-title
Shannon\'s Source Coding Theorem (1948)
:::

**Theorem:** For a source with entropy H, the minimum achievable average codeword length L satisfies H ≤ L \< H + 1 (for single-symbol coding). For block coding of n symbols: H ≤ L_n/n \< H + 1/n. As n → ∞, the average bits per symbol approaches H. Entropy is the fundamental limit of lossless compression.
:::

::: section
::: section-title
AEP and Typical Sets
:::

The **Asymptotic Equipartition Property (AEP):** For iid random variables X₁,\...,X_n: −(1/n) log p(X₁,\...,X_n) → H(X) in probability. This means long sequences fall into a **typical set** of approximately 2^nH^ sequences, each with probability approximately 2^−nH^. The typical set contains almost all the probability mass but is an exponentially small fraction of all possible sequences (when H \< log\|𝒳\|). Compression works because we only need to index the typical set.
:::

::: section
::: section-title
Practical Codes
:::

  Code                       Type                            Optimality
  -------------------------- ------------------------------- ------------------------------------------------------------------------
  **Huffman (1952)**         Prefix-free, symbol-by-symbol   Optimal among all prefix codes for given distribution
  **Arithmetic coding**      Stream-based                    Approaches H more closely than Huffman; handles fractional bit lengths
  **Lempel-Ziv (1977/78)**   Dictionary-based, universal     Asymptotically optimal without knowing the source distribution
:::
:::

::: {#ch-channel .chapter}
::: chapter-number
Section 5
:::

::: chapter-title
Channel Coding (Reliable Communication)
:::

::: section
::: section-title
Channel Capacity
:::

A **discrete memoryless channel** is defined by a conditional probability p(y\|x). The **channel capacity** is C = max~p(x)~ I(X;Y) --- the maximum mutual information over all possible input distributions. C represents the maximum rate (bits per channel use) at which information can be transmitted reliably.
:::

::: section
::: section-title
Shannon\'s Noisy Channel Coding Theorem (1948)
:::

::: {.callout .key}
::: callout-label
The most important theorem in information theory
:::

For a channel with capacity C, reliable communication (error probability → 0 as block length → ∞) is achievable at any rate R \< C. Conversely, for R \> C, reliable communication is impossible --- the error probability is bounded away from zero. Shannon proved existence (random coding achieves capacity) but did not provide constructive codes. Practical codes approaching capacity (turbo codes, LDPC) were not discovered until the 1990s.
:::
:::

::: section
::: section-title
Key Channel Capacities
:::

  Channel                                             Capacity
  --------------------------------------------------- ---------------------------------------
  Binary Symmetric Channel (BSC), error prob ε        C = 1 − H₂(ε)
  Binary Erasure Channel (BEC), erasure prob ε        C = 1 − ε
  AWGN (bandwidth W, signal power S, noise power N)   C = W log₂(1 + S/N) (Shannon-Hartley)
:::

::: section
::: section-title
Fano\'s Inequality
:::

**Fano\'s inequality:** If X is estimated as X̂ from Y, with error probability P_e = P(X ≠ X̂), then H(X\|Y) ≤ H₂(P_e) + P_e log(\|𝒳\| − 1). This provides a lower bound on error probability given the conditional entropy --- it is the key tool for proving converse (impossibility) results in coding theory.
:::
:::

::: {#ch-rate-distortion .chapter}
::: chapter-number
Section 6
:::

::: chapter-title
Rate-Distortion Theory
:::

For **lossy compression**, the question is: what is the minimum rate (bits per symbol) to represent a source with average distortion at most D? The **rate-distortion function** R(D) = min I(X; X̂), minimized over all conditional distributions p(x̂\|x) satisfying E\[d(X, X̂)\] ≤ D. For a Gaussian source with squared-error distortion: R(D) = ½ log(σ²/D) for D ≤ σ², and R(D) = 0 for D \> σ². R(D) is convex, decreasing, and reaches 0 at the distortion equal to the source variance.
:::

::: {#ch-differential .chapter}
::: chapter-number
Section 7
:::

::: chapter-title
Differential Entropy
:::

For continuous random variables with density f: h(X) = −∫ f(x) log f(x) dx. Unlike discrete entropy, differential entropy can be negative and is not invariant under coordinate transformations. **Maximum entropy:** Among all distributions with mean μ and variance σ², the Gaussian N(μ, σ²) maximizes differential entropy: h(X) ≤ ½ log(2πeσ²), with equality iff X is Gaussian. This result underpins the Shannon-Hartley capacity formula for the Gaussian channel.
:::

::: {#ch-entropy-rate .chapter}
::: chapter-number
Section 8
:::

::: chapter-title
Entropy Rate
:::

For a stochastic process {X_n}, the **entropy rate** is H̃ = lim~n→∞~ (1/n) H(X₁,\...,X_n) when the limit exists. For stationary processes, this equals lim H(X_n \| X\_{n-1},\...,X₁). For iid processes: H̃ = H(X₁). For stationary Markov chains: H̃ = −∑ π_i ∑ p\_{ij} log p\_{ij}, where π is the stationary distribution. The entropy rate determines the fundamental compression limit for the process.
:::

::: {#ch-applications .chapter}
::: chapter-number
Section 9
:::

::: chapter-title
Applications
:::

  Domain             Application of Information Theory
  ------------------ --------------------------------------------------------------------------------------------------------------------------------------------------------
  Data compression   ZIP, gzip (LZ), JPEG (DCT + Huffman), MP3/AAC (psychoacoustic + entropy coding)
  Error correction   CDs (Reed-Solomon), deep space (turbo/LDPC), 5G (polar codes)
  Cryptography       Perfect secrecy (Shannon 1949): key entropy ≥ message entropy. Unicity distance.
  Machine learning   Cross-entropy loss, KL divergence for variational inference, mutual information for feature selection
  Statistics         Fisher information: I_F(θ) = E\[(d/dθ log f(X;θ))²\]. Cramér-Rao bound: Var(θ̂) ≥ 1/I_F(θ). Connects to differential entropy via de Bruijn\'s identity.
  Physics            Boltzmann entropy S = k_B ln W (thermodynamic analog). Landauer\'s principle: erasing 1 bit costs ≥ k_B T ln 2 energy.
  Neuroscience       Neural coding efficiency, information transmission rates in sensory systems
:::

::: {#ch-results-ref .chapter}
::: chapter-number
Section 10
:::

::: chapter-title
Key Results Reference
:::

  Result                         Statement
  ------------------------------ ---------------------------------------------------------------------
  Entropy definition             H(X) = −∑ p(x) log p(x) ≥ 0
  Maximum entropy                H(X) ≤ log\|𝒳\|, equality iff uniform
  Chain rule                     H(X,Y) = H(X) + H(Y\|X)
  Conditioning reduces entropy   H(Y\|X) ≤ H(Y)
  Mutual information             I(X;Y) = H(X) + H(Y) − H(X,Y) ≥ 0
  Gibbs\' inequality             D(p‖q) ≥ 0, equality iff p = q
  Data processing inequality     X→Y→Z ⇒ I(X;Z) ≤ I(X;Y)
  Kraft\'s inequality            Prefix code exists iff ∑ 2^−l_i^ ≤ 1
  Source coding theorem          H ≤ optimal avg. code length; achievable within ε with block coding
  AEP                            −(1/n) log p(x₁,\...,x_n) → H(X)
  Channel capacity               C = max I(X;Y); reliable comm. iff R \< C
  Shannon-Hartley                C = W log₂(1 + S/N) for AWGN
  Fano\'s inequality             H(X\|Y) ≤ H₂(P_e) + P_e log(\|𝒳\|−1)
  Rate-distortion                R(D) = min I(X;X̂) s.t. E\[d\] ≤ D
  Gaussian max entropy           h(X) ≤ ½ log(2πeσ²), equality iff Gaussian
:::

::: {#ch-refs .chapter}
::: chapter-number
References
:::

::: chapter-title
References
:::

1.  Cover, T.M. & Thomas, J.A. *Elements of Information Theory*, 2nd ed. Wiley, 2006.
2.  Fano, R.M. *Transmission of Information*. MIT Press, 1961.
3.  Gallager, R.G. *Information Theory and Reliable Communication*. Wiley, 1968.
4.  Huffman, D.A. \"A method for the construction of minimum-redundancy codes.\" *Proc. IRE* 40.9 (1952): 1098--1101.
5.  Kraft, L.G. \"A device for quantizing, grouping, and coding amplitude-modulated pulses.\" MS thesis, MIT, 1949.
6.  MacKay, D.J.C. *Information Theory, Inference, and Learning Algorithms*. Cambridge University Press, 2003.
7.  Shannon, C.E. \"A mathematical theory of communication.\" *Bell System Technical Journal* 27 (1948): 379--423, 623--656.
8.  Shannon, C.E. \"Communication theory of secrecy systems.\" *Bell System Technical Journal* 28 (1949): 656--715.
:::
:::
:::

------------------------------------------------------------------------

::: page-footer
Loop MMT™ · Multi-Module Theory Information Theory Knowledge Pack · v1 © 2026 Shea Gunther · [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/deed.en){style="color:inherit;"}
:::
