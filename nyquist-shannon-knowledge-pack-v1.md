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
Nyquist-Shannon Sampling Theory
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
-   [1 · Signals & Bandwidth](#ch-signals)
-   [2 · Sampling as a Process](#ch-sampling)
-   [3 · The Theorem](#ch-theorem)
-   [4 · Aliasing](#ch-aliasing)
-   [5 · Perfect Reconstruction](#ch-reconstruction)
-   [6 · Practical Realities](#ch-practical)
-   [7 · Oversampling & Why It Helps](#ch-oversampling)
-   [8 · Multidimensional Sampling](#ch-multidimensional)
-   [9 · Compressed Sensing](#ch-compressed)
-   [10 · History](#ch-history)
-   [11 · Board Connection](#ch-board)
-   [References](#ch-refs)

::: {.content role="main"}
::: {#ch-abstract .abstract-box}
::: abstract-label
About This Document
:::

This document covers the Nyquist-Shannon sampling theorem --- the formal statement of how many samples are needed to reconstruct a continuous signal without information loss. The tomography pack (Graham/Geoff) covers angular sampling for reconstruction from projections. This pack provides the general theorem that underlies all sampling problems, giving the board the actual mathematics rather than reasoning by analogy from the Radon transform.

The theorem answers the question: \"How many observers is enough?\" It also explains what happens when there aren\'t enough (aliasing), what you gain from having more than enough (oversampling), and what you can do when you can\'t get enough (compressed sensing). Full citations appear in the References section.
:::

::: {#ch-signals .chapter}
::: chapter-number
Section 1
:::

::: chapter-title
Signals & Bandwidth
:::

::: {#s-signal-def .section}
::: section-title
What Is a Signal
:::

A **signal** is a function that varies over time, space, or some other continuous domain. An audio waveform is a function of time. An image is a function of spatial position. A temperature profile is a function of location. Signals carry information encoded in how they vary.
:::

::: {#s-fourier .section}
::: section-title
Frequency Decomposition
:::

Any signal can be decomposed into a sum of sinusoids at different frequencies, amplitudes, and phases. This is the Fourier decomposition. A pure tone is a single sinusoid. Music is a sum of many sinusoids. An image\'s sharpness comes from its high-frequency components; its broad shapes come from low-frequency components.

The **spectrum** of a signal is the set of frequencies present in it, together with their amplitudes and phases. The spectrum is the frequency-domain representation of the signal, as opposed to the time-domain (or space-domain) representation.
:::

::: {#s-bandwidth .section}
::: section-title
Bandwidth and Band-Limiting
:::

A signal is **band-limited** if its spectrum is zero above some maximum frequency B. No frequency component higher than B is present. The **bandwidth** is the range of frequencies the signal occupies. For a baseband signal (lowest frequency is 0), bandwidth equals the maximum frequency B.

Band-limiting is the critical assumption of the sampling theorem. Real-world signals are never perfectly band-limited --- there is always some energy at arbitrarily high frequencies. But for practical purposes, most signals have a frequency above which the remaining energy is negligible. The sampling theorem applies exactly to the idealized band-limited case and approximately (with controlled error) to the practical case.
:::
:::

::: {#ch-sampling .chapter}
::: chapter-number
Section 2
:::

::: chapter-title
Sampling as a Process
:::

::: {#s-sampling-def .section}
::: section-title
What Sampling Does
:::

**Sampling** converts a continuous signal into a discrete sequence of values by measuring the signal at regularly spaced points. The **sampling rate** (or sampling frequency) `f`~`s`~ is the number of samples taken per unit time. The **sampling interval** `T = 1/f`~`s`~ is the time between consecutive samples.

Sampling appears to discard vast amounts of information --- between any two samples, the continuous signal has infinitely many values that are not measured. The question is whether this discarded information can be recovered. The sampling theorem says yes, under specific conditions.
:::

::: {#s-sampling-frequency .section}
::: section-title
What Sampling Does in the Frequency Domain
:::

In the frequency domain, sampling a signal at rate `f`~`s`~ creates periodic copies (aliases) of the signal\'s spectrum, centered at integer multiples of `f`~`s`~. The sampled signal\'s spectrum is the original spectrum replicated at \..., `−2f`~`s`~, `−f`~`s`~, 0, `f`~`s`~, `2f`~`s`~, \.... If the copies don\'t overlap, the original spectrum can be isolated by a low-pass filter and the signal perfectly recovered. If the copies do overlap, the overlapping regions are corrupted --- this is aliasing.
:::
:::

::: {#ch-theorem .chapter}
::: chapter-number
Section 3
:::

::: chapter-title
The Theorem
:::

::: {#s-theorem-statement .section}
::: section-title
Formal Statement
:::

**Nyquist-Shannon Sampling Theorem:** If a continuous-time signal `x(t)` is band-limited to bandwidth B --- that is, its Fourier transform is zero for all frequencies `|f| > B` --- then `x(t)` is completely determined by its samples taken at any rate `f`~`s`~` > 2B`.

The minimum sampling rate `f`~`s`~` = 2B` is called the **Nyquist rate**. The frequency `f`~`s`~`/2` is called the **Nyquist frequency** --- it is the highest frequency that can be faithfully represented at sampling rate `f`~`s`~.

The reconstruction formula (Whittaker-Shannon interpolation) is:

`x(t) = ∑`~`n=−∞`~^`∞`^` x[n] · sinc(f`~`s`~`·t − n)`

where `sinc(u) = sin(πu)/(πu)` and `x[n] = x(n/f`~`s`~`)` are the sample values. Each sample generates a sinc function centered at the sample point; the sum of all these sinc functions reconstructs the original continuous signal exactly.

::: {.callout .key}
::: callout-label
What the theorem says and doesn\'t say
:::

The theorem says: if you sample fast enough, you lose nothing. It doesn\'t say: if you sample too slowly, you necessarily lose everything. It provides a sufficient condition for perfect reconstruction. Below the Nyquist rate, reconstruction may still be possible with additional information (see Section 9: Compressed Sensing), but the general guarantee is lost.
:::
:::

::: {#s-two-samples .section}
::: section-title
The Intuition: Two Samples Per Cycle
:::

The Nyquist rate requires at least two samples per cycle of the highest frequency present. Why two? A sinusoid has two degrees of freedom: amplitude and phase. Two samples per cycle are the minimum needed to determine both. With only one sample per cycle, a sinusoid of a given frequency cannot be distinguished from a DC signal. With fewer than two, multiple different sinusoids produce the same sample values --- they are aliases of each other.
:::
:::

::: {#ch-aliasing .chapter}
::: chapter-number
Section 4
:::

::: chapter-title
Aliasing
:::

::: {#s-aliasing-def .section}
::: section-title
What Aliasing Is
:::

**Aliasing** occurs when a signal is sampled below its Nyquist rate. Frequency components above the Nyquist frequency `f`~`s`~`/2` are not captured correctly --- they appear in the reconstructed signal as lower-frequency components that were not in the original signal. High-frequency energy \"folds back\" into the representable frequency range, masquerading as legitimate low-frequency content.

The alias of a frequency `f` at sampling rate `f`~`s`~ is `f − k·f`~`s`~ for the integer k that places the result in the range `[0, f`~`s`~`/2]`. For example, at `f`~`s`~` = 8 kHz`, a 9 kHz tone aliases to 1 kHz. A 15 kHz tone aliases to 1 kHz as well. Both are indistinguishable from a genuine 1 kHz signal in the sampled data.
:::

::: {#s-aliasing-irreversible .section}
::: section-title
Aliasing Is Irreversible
:::

Once aliasing has occurred in the sampled data, it cannot be undone. The aliased components are mixed with genuine low-frequency components and there is no mathematical way to separate them. This is why aliasing is the central hazard in digital signal processing --- it is not a distortion that can be filtered out after the fact. It is an information-theoretic collapse: two different signals map to the same samples.

::: {.callout .warn}
::: callout-label
The anti-aliasing principle
:::

To prevent aliasing, you must ensure that no frequency content above `f`~`s`~`/2` exists in the signal before sampling. This is done with an **anti-aliasing filter** --- a low-pass filter applied before the analog-to-digital converter that removes all content above the Nyquist frequency. The filter must be applied in the analog domain, before sampling, because once the signal is sampled, it is too late.
:::
:::
:::

::: {#ch-reconstruction .chapter}
::: chapter-number
Section 5
:::

::: chapter-title
Perfect Reconstruction
:::

::: {#s-sinc-interpolation .section}
::: section-title
The Sinc Interpolation Formula
:::

When the sampling theorem is satisfied, the original signal is recovered by convolving the samples with the sinc function. Each sample `x[n]` generates a sinc function `sinc(f`~`s`~`·t − n)`. At the sample point `t = n/f`~`s`~, the sinc equals 1; at all other sample points, it equals 0. Between sample points, the sinc functions overlap and their sum fills in the continuous signal exactly.

This is the reconstruction formula from Section 3. In the frequency domain, it is equivalent to applying an ideal low-pass filter that passes all frequencies below `f`~`s`~`/2` and blocks everything above --- extracting the original spectrum from the periodic replicas created by sampling.
:::

::: {#s-ideal-filter .section}
::: section-title
The Ideal Filter Problem
:::

Perfect reconstruction requires an ideal low-pass filter with a perfectly sharp cutoff at the Nyquist frequency. Such a filter has an infinite impulse response (the sinc function extends to infinity in both directions) and is therefore non-causal --- it depends on future samples. No physical system can implement it exactly. This is why the sampling theorem guarantees perfect reconstruction *in principle* but not in practice. Practical reconstruction uses approximate filters with finite length, introducing small errors that decrease with oversampling (Section 7).
:::
:::

::: {#ch-practical .chapter}
::: chapter-number
Section 6
:::

::: chapter-title
Practical Realities
:::

::: {#s-practice .section}
::: section-title
Why Practice Differs from Theory
:::

Real systems never sample at exactly the Nyquist rate. Several factors force higher rates:

**Anti-aliasing filter design:** An ideal brick-wall filter at `f`~`s`~`/2` is impossible to build. Real filters have a transition band --- a range of frequencies between the passband (fully passed) and the stopband (fully blocked). The sampling rate must be high enough that the transition band falls outside the signal\'s bandwidth.

**Component tolerances:** Real hardware has frequency response variations. A safety margin above the Nyquist rate protects against components drifting into aliasing territory.

**Quantization:** Real ADCs represent each sample as a finite number of bits, introducing quantization noise. Higher sampling rates spread quantization noise across a wider frequency range, reducing the noise density within the signal band.

**Jitter:** Real sampling clocks are not perfectly periodic. Sample-time jitter introduces noise that increases with signal frequency. Higher sampling rates reduce the impact of jitter on reconstruction accuracy.

  Application          Signal Bandwidth   Nyquist Rate   Typical Actual Rate   Oversampling Factor
  -------------------- ------------------ -------------- --------------------- ---------------------
  CD audio             20 kHz             40 kHz         44.1 kHz              1.1×
  Professional audio   20 kHz             40 kHz         96 kHz                2.4×
  Telephone            3.4 kHz            6.8 kHz        8 kHz                 1.2×
  Medical ultrasound   \~15 MHz           \~30 MHz       40--80 MHz            1.3--2.7×
:::
:::

::: {#ch-oversampling .chapter}
::: chapter-number
Section 7
:::

::: chapter-title
Oversampling & Why It Helps
:::

::: {#s-oversampling .section}
::: section-title
More Samples Than Necessary
:::

**Oversampling** means sampling at a rate significantly higher than the Nyquist rate. The theorem guarantees that the Nyquist rate is sufficient; oversampling provides more samples than strictly necessary. The extra samples are not \"wasted\" --- they buy practical advantages:

**Relaxed anti-aliasing requirements:** With 2× oversampling, the transition band of the anti-aliasing filter can be as wide as the signal bandwidth itself, making the filter much easier to build.

**Noise reduction:** Oversampling by factor k reduces in-band noise by `√k` (equivalent to gaining `½ log₂(k)` bits of effective resolution). This is because quantization noise is spread across a wider band, and only the in-band portion matters.

**Robustness to errors:** Oversampled systems degrade gracefully when samples are lost or corrupted, because the remaining samples still exceed the Nyquist rate. An exactly-Nyquist-rate system has no margin --- losing even one sample can cause errors.

::: {.callout .tip}
::: callout-label
The oversampling principle
:::

More measurements than the theoretical minimum does not increase the information content (the Nyquist rate already captures everything), but it increases robustness, reduces noise, and simplifies the reconstruction process. The minimum is for perfect conditions; real conditions require a margin.
:::
:::
:::

::: {#ch-multidimensional .chapter}
::: chapter-number
Section 8
:::

::: chapter-title
Multidimensional Sampling
:::

::: {#s-2d-sampling .section}
::: section-title
Images and Spatial Signals
:::

The sampling theorem extends naturally to multiple dimensions. A 2D signal (image) with maximum spatial frequency B in each direction requires a sampling rate of at least 2B samples per unit length in each direction. The pixel spacing must be at most `1/(2B)` to avoid spatial aliasing.

In tomography, the extension is more subtle. The Radon transform\'s sampling requirements involve both the number of projections (angular sampling) and the number of detector elements per projection (spatial sampling). The rule of thumb --- projections ≈ pixels across the object --- is the 2D Nyquist condition applied to the polar grid of the Fourier Slice Theorem. Insufficient angular sampling causes radial streak artifacts; insufficient detector sampling causes spatial aliasing within each projection.

For a signal sampled on a non-rectangular grid (like the polar grid of tomographic data), the sampling density must be sufficient everywhere in the frequency domain to prevent spectral overlap. Regions of the frequency domain with sparser coverage require more samples to compensate --- this is why the corners of k-space in MRI, far from the origin, are most vulnerable to aliasing.
:::
:::

::: {#ch-compressed .chapter}
::: chapter-number
Section 9
:::

::: chapter-title
Compressed Sensing
:::

::: {#s-cs-core .section}
::: section-title
Below-Nyquist Recovery with Prior Knowledge
:::

**Compressed sensing** (Candès, Romberg, and Tao, 2006; Donoho, 2006) proves that signals can be recovered from far fewer samples than the Nyquist rate requires --- if the signal is **sparse** in some basis. A signal is sparse if it can be represented using far fewer non-zero coefficients than its total dimensionality. Most natural signals are sparse in some transform domain (images in the wavelet domain, audio in the frequency domain, etc.).

The key insight: if you know the signal is sparse but don\'t know which coefficients are non-zero, you can recover the signal from O(k log(n/k)) random measurements, where k is the sparsity and n is the signal dimension. This can be dramatically fewer than the n measurements required by Nyquist.

Compressed sensing trades prior knowledge (sparsity) for measurement density. The more you know about the structure of the signal, the fewer samples you need. If you know nothing (the signal could be anything band-limited), the Nyquist rate is the best you can do. If you know the signal is sparse, you can do much better.

::: {.callout .key}
::: callout-label
The general principle
:::

The number of samples needed to reconstruct a signal depends on the signal\'s complexity, not its bandwidth alone. Bandwidth sets the upper bound (Nyquist). Structural constraints (sparsity, smoothness, known patterns) lower the actual requirement. The more structure, the fewer samples. This is the formal version of the intuition that \"if you already know what to expect, you need fewer measurements to confirm it.\"
:::
:::
:::

::: {#ch-history .chapter}
::: chapter-number
Section 10
:::

::: chapter-title
History
:::

::: {#s-history-timeline .section}
::: section-title
Key Events
:::

  Year       Person                         Contribution
  ---------- ------------------------------ -------------------------------------------------------------------------------------------------------------------------------------------------------
  1915       E. T. Whittaker                Published the interpolation formula for band-limited functions using sinc functions
  1928       Harry Nyquist                  Established the minimum sampling rate for telegraph signals (the Nyquist rate), though he did not explicitly formulate the reconstruction problem
  1933       Vladimir Kotelnikov            Independently proved the sampling theorem in the Soviet Union; his work was not widely known in the West for decades
  1935       J. M. Whittaker                Extended his father\'s interpolation results
  1946       Dennis Gabor                   Published related results in \"Theory of communication\"
  1948--49   Claude Shannon                 Proved the theorem as Theorem 13 in \"A Mathematical Theory of Communication,\" connecting it to information theory. Cited Whittaker\'s earlier work.
  2006       Candès, Romberg, Tao; Donoho   Compressed sensing --- proved sub-Nyquist recovery is possible for sparse signals

::: {.callout .note}
::: callout-label
Note on naming
:::

The theorem has been independently discovered by at least five people across three decades and two continents. It is variously called the Nyquist-Shannon, Whittaker-Shannon, Nyquist-Shannon-Kotelnikov, or cardinal theorem of interpolation. This is a case study in Stigler\'s Law --- no scientific discovery is named after its original discoverer.
:::
:::
:::

::: {#ch-board .chapter}
::: chapter-number
Section 11
:::

::: chapter-title
Board Connection
:::

::: {#s-board-how-many .section}
::: section-title
How Many Observers Is Enough
:::

The sampling theorem provides the formal framework for answering the question the tomography pack approaches by analogy. The mapping:

  Sampling Theory          Advisory Board
  ------------------------ ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  Continuous signal x(t)   The full, continuous session state --- everything that was understood and decided
  Bandwidth B              The complexity of the session --- how much variation in perspective and detail the session contains
  Sampling rate f~s~       The number and frequency of observation points --- board members, document types, review stages
  Nyquist rate 2B          The minimum number of independent observations needed to reconstruct the session without losing information
  Aliasing                 What happens when there aren\'t enough observers --- high-complexity aspects of the session appear as something simpler than they actually are, and the distortion is undetectable
  Anti-aliasing filter     Scope limiting --- constraining session complexity to what the available observers can faithfully capture
  Oversampling             Having more observers than the theoretical minimum --- buys robustness, noise reduction, and easier reconstruction
  Compressed sensing       Using structural knowledge (the Standard, the protocols, the templates) to reconstruct with fewer observers than Nyquist would require
:::

::: {#s-board-implications .section}
::: section-title
Design Implications
:::

**Session complexity determines observer count.** A simple session (low bandwidth) can be faithfully captured by fewer documents and fewer review stages. A complex session (high bandwidth) requires proportionally more. The Nyquist rate for session reconstruction is not fixed --- it depends on the session.

**Aliasing in sessions is undetectable without ground truth.** If the session is undersampled --- too few documents, too few perspectives --- the reconstructed session will appear simpler than the actual session was. Nuances, edge cases, and subtle decisions will be replaced by plausible but incorrect simplifications. And you won\'t know it happened, because aliased content looks like genuine low-frequency content.

**The Standard is an anti-aliasing filter.** By constraining sessions to follow structured protocols, the Standard limits the \"bandwidth\" of sessions --- it ensures that session complexity doesn\'t exceed what the document mesh can faithfully capture. Templates, field tables, and routing conventions are all forms of bandwidth limiting.

**The board is oversampled by design.** Ten board members for a session that might be adequately captured by three is not waste --- it is oversampling. The extra perspectives buy robustness (if one board member\'s analysis is wrong, the others catch it), noise reduction (multiple perspectives average out individual biases), and easier reconstruction (the new instance has redundant information to work with).

**Structured documents enable compressed sensing.** The protocols, templates, and document standards are prior knowledge about the structure of sessions. With this prior knowledge, fewer measurements (fewer documents) suffice for reconstruction than would be needed for an unstructured session. This is exactly the compressed sensing principle: structural constraints trade for measurement density.

::: {.callout .key}
::: callout-label
The formal answer
:::

How many observers is enough? At least twice the session\'s \"bandwidth\" --- twice the number of independent dimensions along which the session varies. The Standard keeps bandwidth manageable. The board oversamples for robustness. The structured document formats enable compressed-sensing-style reconstruction from less than Nyquist. This is now the actual theorem, not an analogy from tomography.
:::
:::
:::

::: {#ch-refs .chapter}
::: chapter-number
References
:::

::: chapter-title
References
:::

::: section
::: section-title
Foundational Works
:::

Whittaker, E. T. (1915). On the functions which are represented by the expansions of the interpolation theory. *Proceedings of the Royal Society of Edinburgh*, 35, 181--194.

Nyquist, H. (1928). Certain topics in telegraph transmission theory. *Transactions of the AIEE*, 47(2), 617--644.

Kotelnikov, V. A. (1933). On the transmission capacity of \"ether\" and wire in electrocommunications. *Proceedings of the First All-Union Conference on the Technological Reconstruction of the Communications Sector*. (In Russian.)

Shannon, C. E. (1949). Communication in the presence of noise. *Proceedings of the IRE*, 37(1), 10--21.

Shannon, C. E. (1948). A mathematical theory of communication. *Bell System Technical Journal*, 27(3), 379--423.
:::

::: section
::: section-title
Compressed Sensing
:::

Candès, E. J., Romberg, J. K., & Tao, T. (2006). Robust uncertainty principles: Exact signal reconstruction from highly incomplete frequency information. *IEEE Transactions on Information Theory*, 52(2), 489--509.

Donoho, D. L. (2006). Compressed sensing. *IEEE Transactions on Information Theory*, 52(4), 1289--1306.

Mishali, M. & Eldar, Y. C. (2009). Blind multiband signal reconstruction: Compressed sensing for analog signals. *IEEE Transactions on Signal Processing*, 57(3), 993--1009.
:::

::: section
::: section-title
Textbooks and References
:::

Oppenheim, A. V. & Willsky, A. S. (1997). *Signals and Systems*. 2nd ed. Prentice Hall.

Proakis, J. G. & Manolakis, D. G. (2006). *Digital Signal Processing: Principles, Algorithms, and Applications*. 4th ed. Prentice Hall.

Unser, M. (2000). Sampling --- 50 years after Shannon. *Proceedings of the IEEE*, 88(4), 569--587.

Wikipedia contributors. (2026). Nyquist--Shannon sampling theorem. *Wikipedia, The Free Encyclopedia*.
:::
:::
:::
:::

------------------------------------------------------------------------

::: page-footer
Loop MMT™ · Multi-Module Theory Nyquist-Shannon Sampling Theory Knowledge Pack · v1 © 2026 Shea Gunther · [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/deed.en){style="color:inherit;"}
:::
