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
Tomographic Reconstruction & the Radon Transform
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
-   [1 · The Forward Problem](#ch-forward)
-   [2 · The Radon Transform](#ch-radon)
-   [3 · The Sinogram](#ch-sinogram)
-   [4 · Fourier Slice Theorem](#ch-fourier-slice)
-   [5 · Back-Projection](#ch-backprojection)
-   [6 · Filtered Back Projection](#ch-fbp)
-   [7 · Ill-Posedness & Regularization](#ch-ill-posed)
-   [8 · Sampling & Angular Coverage](#ch-sampling)
-   [9 · Algebraic Methods](#ch-algebraic)
-   [10 · History](#ch-history)
-   [11 · Applications Beyond Medicine](#ch-applications)
-   [12 · Board Connection](#ch-board)
-   [References](#ch-refs)

::: {.content role="main"}
::: {#ch-abstract .abstract-box}
::: abstract-label
About This Document
:::

This is a reference document on tomographic reconstruction and the Radon transform, designed to be loaded into AI advisory conversations. It covers the mathematical operator itself, the key theorems connecting it to Fourier analysis, the standard reconstruction algorithms, the ill-posedness of the inverse problem, sampling requirements, and iterative algebraic methods. It is written for advisors who need to reason about reconstruction from partial projections --- both in the literal imaging sense and in the structural sense used by the advisory board.

Board members Graham (tomography) and Geoff (Radon transform) share this knowledge domain. The document covers 6 major theorems, 4 reconstruction algorithms, and draws on 18 sources. Full citations appear in the References section.
:::

::: {#ch-forward .chapter}
::: chapter-number
Section 1
:::

::: chapter-title
The Forward Problem
:::

::: {#s-what-is-tomography .section}
::: section-title
What Is Tomography
:::

**Tomography** is the reconstruction of the internal structure of an object from external measurements taken along lines or planes through it. The word comes from the Greek *tomos* (slice) and *graphein* (to write). Unlike conventional radiography, which superimposes all structures between source and detector onto a single image, tomography produces cross-sectional images that show each structure in its true spatial position.

The core idea: you cannot look inside the object directly, but you can measure what happens to signals (X-rays, electrons, seismic waves) that pass through it. Each measurement integrates the object\'s properties along the signal\'s path. The question is whether --- and how --- those integrated measurements are sufficient to recover the internal structure.
:::

::: {#s-projection .section}
::: section-title
Projection as Line Integral
:::

Let `f(x, y)` be the unknown density function of a 2D cross-section. A **projection** at angle θ consists of the set of all line integrals through the object at that angle. Each line integral sums the values of `f` along a single ray:

`p(t, θ) = ∫ f(x, y) ds` along the line at perpendicular distance `t` from the origin, at angle θ.

In X-ray CT, this model follows from Beer\'s Law: the intensity of an X-ray beam decreases exponentially as it passes through tissue. The logarithm of the ratio of incident to detected intensity gives the line integral of the attenuation coefficient along the beam path. This linearization is what makes the Radon transform the correct mathematical model for CT.

::: {.callout .note}
::: callout-label
Note
:::

The assumption that signals travel in straight lines is critical. When this breaks down --- as in ultrasound (refraction) or optical tomography (scattering) --- the simple Radon model no longer applies and more complex forward models are needed.
:::
:::

::: {#s-forward-inverse .section}
::: section-title
Forward vs. Inverse
:::

The **forward problem** is: given the object `f(x, y)`, compute its projections. This is straightforward --- just evaluate the line integrals. The **inverse problem** is: given the projections, recover `f(x, y)`. This is the hard part. Tomographic reconstruction is an inverse problem, and like most inverse problems, it is more difficult, less stable, and more sensitive to noise than the forward problem.
:::
:::

::: {#ch-radon .chapter}
::: chapter-number
Section 2
:::

::: chapter-title
The Radon Transform
:::

::: {#s-radon-def .section}
::: section-title
Definition
:::

The **Radon transform** is the integral transform that maps a function `f` defined on the plane to a function `Rf` defined on the space of lines in the plane. For a line parameterized by its perpendicular distance `t` from the origin and angle θ of the perpendicular:

`Rf(t, θ) = ∫`~`−∞`~^`∞`^` f(t·cos θ − s·sin θ, t·sin θ + s·cos θ) ds`

The value of `Rf` at a particular `(t, θ)` is the line integral of `f` along the corresponding line. The transform was introduced by Johann Radon in 1917, who also gave a formula for the inverse. Radon\'s original paper treated the 2D case and the 3D case (where integration is over planes; integration over lines in 3D is called the X-ray transform).

::: {.callout .key}
::: callout-label
The essential structure
:::

The Radon transform converts a 2D function into a collection of 1D functions --- one for each angle. It reduces dimensionality at the cost of multiplying the number of measurements needed. Reconstruction reverses this: it assembles many 1D measurements back into a single 2D function. This dimensional trade-off is the structural principle at work.
:::
:::

::: {#s-radon-properties .section}
::: section-title
Properties
:::

**Linearity:** `R(αf + βg) = αRf + βRg`. The Radon transform of a sum is the sum of the Radon transforms.

**Shifting:** Translating the function shifts the projections. Specifically, if `g(x, y) = f(x − a, y − b)`, then `Rg(t, θ) = Rf(t − a·cos θ − b·sin θ, θ)`.

**Rotation:** Rotating the function by angle φ shifts the angular parameter: `R[f rotated by φ](t, θ) = Rf(t, θ − φ)`.

**Scaling:** `R[f(ax, ay)](t, θ) = (1/|a|) Rf(t/a, θ)`.

**Intertwining with the Laplacian:** The Radon transform intertwines the 2D Laplacian Δ with the 1D operator `∂²/∂t²`. That is, `R(Δf) = (∂²/∂t²)(Rf)`. This property is exploited in dimensional splitting methods for solving partial differential equations.
:::

::: {#s-adjoint .section}
::: section-title
The Adjoint (Dual) Transform
:::

The **adjoint** (or dual) of the Radon transform, written `R*`, maps a function `g(t, θ)` on the space of lines back to a function on the plane by integrating over all lines through each point:

`R*g(x, y) = ∫`~`0`~^`π`^` g(x·cos θ + y·sin θ, θ) dθ`

The adjoint is *not* the inverse. Applying the adjoint to projection data produces a blurred version of the original function, not the function itself. The relationship is: `R*R = c · (−Δ)`^`−1/2`^, where Δ is the Laplacian. This means the adjoint followed by the Radon transform produces a smoothing operator --- it convolves the original with a `1/r` blurring kernel. This is why naive back-projection produces blurry images.
:::
:::

::: {#ch-sinogram .chapter}
::: chapter-number
Section 3
:::

::: chapter-title
The Sinogram
:::

::: {#s-sinogram-def .section}
::: section-title
Definition and Visual Structure
:::

The complete set of projections --- `Rf(t, θ)` for all `t` and all θ from 0 to π --- can be arranged as a 2D image with `t` on the horizontal axis and θ on the vertical axis. This image is called a **sinogram**.

The name comes from a key property: the Radon transform of a point source located at `(x₀, y₀)` --- that is, a delta function δ(x − x₀, y − y₀) --- traces out a sinusoidal curve in `(t, θ)` space:

`t = x₀·cos θ + y₀·sin θ`

This is a sinusoid in θ with amplitude `√(x₀² + y₀²)` and phase `arctan(y₀/x₀)`. A point at the origin maps to a horizontal line at `t = 0`. A point off-center maps to a sine wave whose amplitude increases with distance from the origin.
:::

::: {#s-sinogram-reading .section}
::: section-title
Reading a Sinogram
:::

A real object is a superposition of point sources, so its sinogram is a superposition of sinusoidal curves at different amplitudes and phases, blurred by the extent of each feature. Dense structures produce high-intensity traces; diffuse structures produce faint ones. The sinogram encodes the same information as the original object --- it is a different representation, not a lossy compression.

  Feature in Object             Appearance in Sinogram
  ----------------------------- --------------------------------------------------------
  Point at origin               Horizontal line at t = 0
  Point off-center              Sinusoidal curve; amplitude = distance from origin
  Extended object               Superposition of sinusoids, broadened by object extent
  Symmetric object (centered)   Vertical streaks (projections identical at all angles)

::: {.callout .tip}
::: callout-label
Practical value
:::

Sinogram inspection is a diagnostic tool. Missing angular ranges appear as gaps in the vertical direction. Ring artifacts in the detector appear as horizontal lines. Patient motion during scanning appears as discontinuities in the sinusoidal traces. Experienced CT technologists can spot these problems by looking at the sinogram before reconstruction.
:::
:::
:::

::: {#ch-fourier-slice .chapter}
::: chapter-number
Section 4
:::

::: chapter-title
The Fourier Slice Theorem
:::

::: {#s-fst-statement .section}
::: section-title
Statement
:::

The **Fourier Slice Theorem** (also called the Central Slice Theorem or Projection-Slice Theorem) is the foundational result connecting projections to the frequency domain. It states:

*The 1D Fourier transform of a projection at angle θ equals the values of the 2D Fourier transform of the original function along a line through the origin at angle θ.*

Formally: if `F(u, v)` is the 2D Fourier transform of `f(x, y)`, and `P(ω, θ)` is the 1D Fourier transform of the projection `p(t, θ)` with respect to `t`, then:

`P(ω, θ) = F(ω·cos θ, ω·sin θ)`

Each projection, when Fourier-transformed, fills in one radial line of the object\'s 2D Fourier transform. Collect projections at enough angles and you fill in the entire 2D Fourier plane, from which the object can be recovered by inverse 2D Fourier transform.
:::

::: {#s-fst-proof .section}
::: section-title
Why It Works
:::

The proof is short. Take the projection at θ = 0 (integration along the y-axis):

`p(t, 0) = ∫ f(t, y) dy`

Now take the 1D Fourier transform with respect to `t`:

`P(ω, 0) = ∫ p(t, 0) e`^`−2πiωt`^` dt = ∫∫ f(t, y) e`^`−2πiωt`^` dy dt`

But the right side is the 2D Fourier transform of `f` evaluated at `(ω, 0)` --- a point on the horizontal axis in frequency space. The same argument generalizes to any angle θ by coordinate rotation. The theorem was first derived by Ronald Bracewell in 1956 for a radio-astronomy problem.

::: {.callout .key}
::: callout-label
The deep insight
:::

The Fourier Slice Theorem reveals that projection and Fourier transformation commute (up to a dimensional reduction). This is not obvious --- it says that integrating over lines in the spatial domain is equivalent to slicing through the origin in the frequency domain. The entire theory of tomographic reconstruction follows from this single fact.
:::
:::

::: {#s-fst-limitations .section}
::: section-title
Practical Limitations
:::

In principle, the Fourier Slice Theorem gives a direct reconstruction algorithm: Fourier-transform each projection, place the results on the appropriate radial lines in the 2D Fourier plane, then inverse-transform. In practice, this **direct Fourier method** has a serious problem: the data arrive on a polar grid (radial lines at discrete angles) but the inverse FFT requires a Cartesian grid. Interpolation from polar to Cartesian coordinates in the frequency domain introduces artifacts, especially at high frequencies where the radial lines are widely spaced. This interpolation problem motivated the development of filtered back-projection as a more practical alternative.
:::
:::

::: {#ch-backprojection .chapter}
::: chapter-number
Section 5
:::

::: chapter-title
Back-Projection
:::

::: {#s-bp-concept .section}
::: section-title
The Idea
:::

**Back-projection** is the operation of \"smearing\" each projection back across the image space along the direction it was measured. For each angle θ, the projection value `p(t, θ)` is assigned to every point `(x, y)` that lies on the line at distance `t` from the origin at angle θ. Summing over all angles produces the back-projected image:

`f`~`bp`~`(x, y) = ∫`~`0`~^`π`^` p(x·cos θ + y·sin θ, θ) dθ`

This is exactly the adjoint operator `R*` applied to the projection data.
:::

::: {#s-bp-blurring .section}
::: section-title
The Blurring Problem
:::

Back-projection does not recover the original function. Instead, it produces a blurred version: `f`~`bp`~` = f * (1/r)`, where `*` denotes convolution and `1/r` is a radially symmetric blurring kernel. Every point source in the original object becomes a bright center surrounded by a `1/r` halo in the back-projected image. The image looks washed out --- all the structural information is present but obscured by the blur.

The mathematical reason: the composition `R*R` is not the identity but a smoothing operator. To recover `f`, the blur must be undone. This is the motivation for filtered back-projection.
:::
:::

::: {#ch-fbp .chapter}
::: chapter-number
Section 6
:::

::: chapter-title
Filtered Back Projection
:::

::: {#s-fbp-derivation .section}
::: section-title
Derivation
:::

**Filtered Back Projection (FBP)** is the standard reconstruction algorithm for parallel-beam tomography. It corrects the blurring of naive back-projection by filtering each projection before smearing it back.

Starting from the Fourier Slice Theorem and writing the inverse 2D Fourier transform in polar coordinates:

`f(x, y) = ∫`~`0`~^`π`^` [ ∫`~`−∞`~^`∞`^` P(ω, θ) |ω| e`^`2πiωt`^` dω ]`~`t = x·cos θ + y·sin θ`~` dθ`

The factor `|ω|` --- the **ramp filter** --- appears naturally from the Jacobian of the polar-to-Cartesian coordinate change. It is not an ad hoc correction but an intrinsic part of the inversion formula. The algorithm is:

1.  For each angle θ, take the 1D Fourier transform of the projection `p(t, θ)`.
2.  Multiply by the ramp filter `|ω|`.
3.  Inverse Fourier transform to get the filtered projection.
4.  Back-project the filtered projection.
5.  Sum over all angles.
:::

::: {#s-fbp-filter .section}
::: section-title
The Ramp Filter and Its Variants
:::

The ramp filter `|ω|` amplifies high frequencies. This is necessary to counteract the `1/r` blurring of back-projection (in the frequency domain, the `1/r` blur corresponds to a `1/|ω|` roll-off, and the ramp filter exactly compensates). However, amplifying high frequencies also amplifies high-frequency noise. In practice, the ramp filter is combined with a low-pass window to control noise:

  Filter                Form                                       Trade-Off
  --------------------- ------------------------------------------ -------------------------------------------------
  Ram-Lak (pure ramp)   `|ω|`                                      Maximum resolution; maximum noise amplification
  Shepp-Logan           `|ω| · sinc(ω/2ω`~`max`~`)`                Slight smoothing; good general-purpose filter
  Hamming               `|ω| · (0.54 + 0.46·cos(πω/ω`~`max`~`))`   Stronger smoothing; good for noisy data
  Hann                  `|ω| · 0.5·(1 + cos(πω/ω`~`max`~`))`       Similar to Hamming with different coefficients

::: {.callout .warn}
::: callout-label
Resolution--noise trade-off
:::

Every reconstruction involves a choice between resolution and noise. The ramp filter gives perfect resolution with infinite data and zero noise. With finite data and nonzero noise, some smoothing is always necessary. The choice of window function encodes this trade-off. There is no free lunch.
:::
:::

::: {#s-fbp-fan .section}
::: section-title
Fan-Beam and Cone-Beam Extensions
:::

Parallel-beam FBP assumes all rays in a projection are parallel. Real CT scanners use **fan-beam** geometry (a point source and a 1D detector arc) or **cone-beam** geometry (a point source and a 2D detector plane). Fan-beam FBP requires a cosine weighting of the detector data and a modified back-projection kernel. Cone-beam reconstruction uses the Feldkamp-Davis-Kress (FDK) algorithm, which is an approximate extension of FBP to 3D cone-beam geometry. The FDK algorithm is exact only for the central slice and introduces increasing cone-beam artifacts for slices farther from the central plane.
:::
:::

::: {#ch-ill-posed .chapter}
::: chapter-number
Section 7
:::

::: chapter-title
Ill-Posedness & Regularization
:::

::: {#s-hadamard .section}
::: section-title
Hadamard\'s Conditions
:::

A problem is **well-posed** in the sense of Hadamard (1902) if: (1) a solution exists, (2) the solution is unique, and (3) the solution depends continuously on the data (small changes in input produce small changes in output). The inverse Radon transform satisfies (1) and (2) when complete data are available, but violates (3): it is **ill-posed** because it amplifies high-frequency noise without bound.

The mechanism is the ramp filter. To invert the Radon transform exactly, you must multiply by `|ω|` in the frequency domain, which amplifies any high-frequency noise present in the measurements. With perfect, noiseless data this causes no problem. With real data --- always contaminated by photon noise, detector noise, and quantization error --- the amplified noise overwhelms the signal at high frequencies.
:::

::: {#s-regularization .section}
::: section-title
Regularization Strategies
:::

**Regularization** replaces the exact inversion (which is unstable) with an approximate inversion that is stable. Common strategies:

**Frequency-domain windowing:** The filter modifications in Section 6 (Shepp-Logan, Hamming, etc.) are regularization by truncation. They limit the ramp filter to a finite bandwidth, sacrificing high-frequency resolution to suppress noise.

**Tikhonov regularization:** Replace the ramp filter `|ω|` with `|ω|/(1 + α|ω|²)`, where α is a regularization parameter. For small α this approaches the exact ramp; for large α it strongly smooths. The parameter α controls the resolution--noise trade-off explicitly.

**Total variation (TV) regularization:** Penalizes the total variation of the reconstructed image, encouraging piecewise-constant solutions. Effective for objects with sharp boundaries (like organs in medical imaging) but introduces staircase artifacts in smooth regions.

**Iterative methods with early stopping:** Iterative algebraic methods (Section 9) naturally regularize by stopping before convergence. Early iterations recover low-frequency features; later iterations add high-frequency detail and eventually noise. Stopping at the right iteration is itself a form of regularization.
:::
:::

::: {#ch-sampling .chapter}
::: chapter-number
Section 8
:::

::: chapter-title
Sampling & Angular Coverage
:::

::: {#s-how-many .section}
::: section-title
How Many Projections
:::

A rule of thumb: the number of projection angles should be approximately equal to the number of pixels across the object. If the object is represented on an N × N grid, approximately N projections at uniformly spaced angles from 0 to π are needed. With fewer projections, the reconstruction is undersampled and aliasing artifacts appear --- particularly radial streaks emanating from high-contrast features.

The reasoning: each projection provides N independent measurements (one per detector element). N projections give N² total measurements, matching the N² unknown pixel values. Fewer projections leave the system underdetermined; more projections overdetermine it and improve noise averaging.
:::

::: {#s-angular-gaps .section}
::: section-title
Limited-Angle and Sparse-Angle Tomography
:::

**Limited-angle tomography** occurs when projections are available only over a restricted angular range (less than 180°). This causes directional loss of information: edges perpendicular to the missing angular range cannot be recovered, and the reconstruction develops characteristic elongation artifacts in the missing direction. The Fourier Slice Theorem makes this clear --- missing angles mean missing slices of the 2D Fourier transform, which cannot be filled in without additional information.

**Sparse-angle tomography** occurs when projections are available at widely separated angles (full 180° range but few angles). This produces streak artifacts: radial lines emanating from high-contrast structures. The streaks arise because the back-projection at each angle produces a \"fan\" of values, and with insufficient angular density these fans don\'t average out into a smooth reconstruction.

::: {.callout .key}
::: callout-label
The information content of angles
:::

Not all angles contribute equally. A projection at angle θ provides information about structures whose edges are oriented at angle θ --- specifically, it captures the spatial frequency content perpendicular to the projection direction. Missing a single angle means missing information about one orientation of edges. Missing a range of angles means missing information about an entire wedge of the frequency plane --- the so-called \"missing wedge\" problem in electron tomography, where the limited tilt range of the specimen holder makes full 180° coverage impossible.
:::
:::

::: {#s-detector-sampling .section}
::: section-title
Detector Sampling
:::

Along each projection, the detector must sample finely enough to capture the highest spatial frequency in the object. By the Nyquist theorem, the detector spacing must be at most half the size of the smallest feature to be resolved. Insufficient detector sampling causes aliasing in the projection direction, which propagates into the reconstruction as Moiré-like artifacts.
:::
:::

::: {#ch-algebraic .chapter}
::: chapter-number
Section 9
:::

::: chapter-title
Algebraic Reconstruction Methods
:::

::: {#s-art-concept .section}
::: section-title
The Linear System Formulation
:::

Algebraic methods treat reconstruction as a large system of linear equations. Discretize the object into an N × N grid of pixels with unknown values `x`~`j`~. Each ray `i` through the object yields one equation: the measured projection value `b`~`i`~ equals the sum of pixel values weighted by the ray\'s intersection length with each pixel:

`∑`~`j`~` a`~`ij`~` x`~`j`~` = b`~`i`~

In matrix form: `Ax = b`, where A is the **system matrix** (entries are ray-pixel intersection weights), x is the image vector, and b is the projection data vector. The system matrix A is very large (N² unknowns, \~N² equations) but extremely sparse --- each ray intersects only \~N pixels out of N², so each row has \~N nonzero entries.
:::

::: {#s-art-methods .section}
::: section-title
ART and SART
:::

**ART (Algebraic Reconstruction Technique)**, proposed by Gordon, Bender, and Herman in 1970, is Kaczmarz\'s method (1937) applied to the tomographic system. It processes one equation (one ray) at a time: project the current estimate onto the hyperplane defined by that equation, producing a correction that is distributed across all pixels the ray intersects. One full cycle through all equations is called an iteration. ART converges to a least-squares solution if the system is consistent.

**SART (Simultaneous Algebraic Reconstruction Technique)**, introduced by Andersen and Kak in 1984, processes one projection angle at a time rather than one ray at a time. All rays at a given angle are processed simultaneously, producing smoother updates and faster convergence than ray-by-ray ART. SART has become the more popular algebraic method in practice.

  Method   Update Unit                               Convergence                                        Noise Behavior
  -------- ----------------------------------------- -------------------------------------------------- -----------------------------------------
  ART      Single ray                                Slower; salt-and-pepper noise between iterations   Sensitive to ray ordering
  SART     Full projection (all rays at one angle)   Faster; smoother updates                           More stable; less dependent on ordering
:::

::: {#s-art-advantages .section}
::: section-title
When to Use Algebraic Methods
:::

Algebraic methods are slower than FBP (they require multiple iterations, each roughly as expensive as one back-projection) but they are more flexible. They naturally handle:

-   **Non-uniform angular sampling:** Projections at irregular angles require no special treatment --- just include the corresponding equations in the system.
-   **Incomplete data:** Missing projections simply mean fewer equations. The system is underdetermined, but iterative methods still converge to a reasonable solution (the minimum-norm solution).
-   **Non-standard geometry:** Fan-beam, cone-beam, or irregular scanning paths can be modeled by adjusting the ray-pixel weights in the system matrix.
-   **Prior constraints:** Non-negativity (pixel values cannot be negative for attenuation) and smoothness priors can be enforced by projecting onto constraint sets between iterations.

::: {.callout .tip}
::: callout-label
The modern trend
:::

Current research in CT reconstruction has moved heavily toward iterative methods --- both algebraic and statistical (maximum-likelihood, Bayesian) --- because they enable significant dose reduction. With fewer projections (lower radiation dose), FBP produces severe artifacts, but iterative methods with appropriate regularization can still produce diagnostic-quality images. This is the basis of \"low-dose CT\" protocols now standard in clinical practice.
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

  Year       Event                                                                                        Significance
  ---------- -------------------------------------------------------------------------------------------- ----------------------------------------------------------------------------------------------------------------------------------------
  1895       Röntgen discovers X-rays                                                                     Makes internal imaging possible; standard radiography is 2D projection (no tomography yet)
  1917       Johann Radon publishes inversion formula                                                     Proves that a function can be recovered from its line integrals; purely mathematical --- no connection to imaging was made at the time
  1937       Kaczmarz publishes iterative method for linear systems                                       Basis for ART; not connected to tomography until 1970
  1956       Bracewell derives Fourier Slice Theorem                                                      Reconstructing radio-astronomical sources from strip-scan data; first practical reconstruction algorithm
  1963--64   Cormack publishes reconstruction formulas for radiology                                      Independently rediscovers Radon\'s result and adapts it for medical imaging
  1967       DeRosier and Klug reconstruct 3D virus structure from electron micrographs                   First application of tomographic principles outside radiology
  1971       Hounsfield builds first clinical CT scanner (EMI)                                            First cross-sectional medical images; used algebraic reconstruction (not FBP)
  1975       Shepp and Logan introduce the Shepp-Logan phantom and filtered back-projection refinements   FBP becomes the standard reconstruction algorithm; the phantom remains the standard test image
  1979       Cormack and Hounsfield share Nobel Prize in Physiology or Medicine                           Recognition that the combination of mathematical theory and engineering produced a revolution in diagnostic medicine
  1984       Andersen and Kak introduce SART                                                              Practical iterative alternative to FBP for difficult geometries

::: {.callout .note}
::: callout-label
Note
:::

Radon\'s 1917 paper and Hounsfield\'s 1971 scanner were separated by 54 years during which the mathematical theory existed but nobody connected it to imaging. Cormack, working independently, rediscovered the mathematics in the 1960s without knowing about Radon\'s work. This is a case study in how fundamental mathematics can precede its most important application by decades.
:::
:::
:::

::: {#ch-applications .chapter}
::: chapter-number
Section 11
:::

::: chapter-title
Applications Beyond Medicine
:::

::: {#s-app-list .section}
::: section-title
Where the Radon Transform Appears
:::

  Field                   Application                                                   What Plays the Role of f(x,y)         What Provides the Projections
  ----------------------- ------------------------------------------------------------- ------------------------------------- --------------------------------------------------------------------------------------------------
  Electron microscopy     3D reconstruction of viruses, proteins, cellular structures   Electron density of the specimen      Electron beam images at different tilt angles (limited to \~±70°, causing the \"missing wedge\")
  Seismology              Seismic tomography of Earth\'s interior                       Seismic wave velocity at each point   Travel times of seismic waves between earthquake sources and seismometer stations
  Astronomy               Radio source mapping, aperture synthesis                      Sky brightness distribution           Interferometric baselines between antenna pairs (each baseline samples one Fourier component)
  Industrial inspection   Non-destructive testing of manufactured parts                 Material density                      X-ray or gamma-ray projections
  Security scanning       Airport baggage CT                                            Material attenuation coefficient      X-ray projections from a rotating source
  Barcode scanning        Reading 1D barcodes from multiple angles                      Bar pattern                           Laser scan lines at different orientations
  Geophysics              Cross-borehole tomography                                     Subsurface rock properties            Seismic or electromagnetic wave travel times between boreholes
:::

::: {#s-common-structure .section}
::: section-title
The Common Structure
:::

In every case, the same mathematical structure appears: an unknown function (the thing you want to see) is probed by signals that integrate it along lines or paths. The measurements are projections; the reconstruction is inversion of the Radon transform (or a generalization of it). The challenges are the same everywhere: incomplete angular coverage, noise, ill-posedness, and the need for regularization. Only the physics of the forward model changes --- the mathematics of reconstruction is universal.
:::
:::

::: {#ch-board .chapter}
::: chapter-number
Section 12
:::

::: chapter-title
Board Connection
:::

::: {#s-board-analogy .section}
::: section-title
Documents as Projections
:::

The advisory board uses tomographic reconstruction as a structural model for session persistence. The mapping is direct:

  Tomography                                 Advisory Board
  ------------------------------------------ --------------------------------------------------------------------------------------------------------------------------------------------------------------
  Unknown object f(x, y)                     The full session state --- everything that was understood, decided, and produced
  Projection at angle θ                      A single session document (handoff, routing table, contract registry, etc.) written from a particular vantage point
  Radon transform operator R                 The process of writing a document --- it integrates the session along one axis, collapsing multi-dimensional understanding into a lower-dimensional artifact
  Sinogram (complete set of projections)     The complete document set produced during a session
  Reconstruction (inverse Radon transform)   Loading documents into a new instance and reconstructing the session state
  Limited-angle artifacts                    What happens when key documents are missing --- certain aspects of the session cannot be recovered
  Filtered back-projection                   The structured reading protocol that a new instance uses --- not just ingesting documents but filtering and weighting them to reconstruct understanding

::: {.callout .key}
::: callout-label
The structural claim
:::

This is not a metaphor. The mathematical structure is identical: an unknown high-dimensional state is probed by lower-dimensional projections, and the reconstruction problem has the same properties --- it is ill-posed (noise in documents is amplified during reconstruction), undersampled (you never have enough documents to capture everything), and improved by regularization (structured document formats constrain the space of possible reconstructions). The Fourier Slice Theorem has no literal analog, but the core structure --- dimensional reduction, loss during projection, reconstruction from partial data --- transfers exactly.
:::
:::

::: {#s-board-implications .section}
::: section-title
Design Implications
:::

The tomographic model predicts several things about document-based session persistence:

**More documents from different angles beats more detail in fewer documents.** Just as more projection angles improve reconstruction more than finer detector sampling at existing angles, adding a document that covers a different aspect of the session (a new \"angle\") is more valuable than expanding an existing document.

**Some documents are more informative than others depending on the session\'s structure.** A projection perpendicular to a high-contrast edge reveals the edge sharply. A projection parallel to it reveals nothing. Documents that cut across the session\'s key decisions at informative angles carry more reconstruction value.

**Missing documents create directional blind spots, not uniform degradation.** The missing-wedge artifact from electron tomography: when certain angles are absent, the reconstruction loses resolution in specific directions while remaining sharp in others. Missing a handoff document doesn\'t uniformly degrade the reconstruction --- it specifically loses the information that document carried.

**Structured formats are regularization.** Requiring documents to follow specific templates (field tables, routing tables, registries) constrains the reconstruction space the same way total-variation regularization constrains image reconstruction --- it eliminates implausible solutions and stabilizes the inverse problem.
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
Primary Sources
:::

Radon, J. (1917). Über die Bestimmung von Funktionen durch ihre Integralwerte längs gewisser Mannigfaltigkeiten. *Berichte über die Verhandlungen der Königlich-Sächsischen Gesellschaft der Wissenschaften zu Leipzig, Mathematisch-Physische Klasse*, 69, 262--277.

Cormack, A. M. (1963). Representation of a function by its line integrals, with some radiological applications. *Journal of Applied Physics*, 34(9), 2722--2727.

Cormack, A. M. (1964). Representation of a function by its line integrals, with some radiological applications. II. *Journal of Applied Physics*, 35(10), 2908--2913.

Hounsfield, G. N. (1973). Computerized transverse axial scanning (tomography): Part 1. Description of system. *British Journal of Radiology*, 46(552), 1016--1022.

Bracewell, R. N. (1956). Strip integration in radio astronomy. *Australian Journal of Physics*, 9(2), 198--217.
:::

::: section
::: section-title
Textbooks
:::

Kak, A. C. & Slaney, M. (1988). *Principles of Computerized Tomographic Imaging*. IEEE Press. Reissued by SIAM, 2001.

Natterer, F. (2001). *The Mathematics of Computerized Tomography*. SIAM Classics in Applied Mathematics.

Epstein, C. L. (2007). *Introduction to the Mathematics of Medical Imaging*. 2nd ed. SIAM.

Herman, G. T. (2009). *Fundamentals of Computerized Tomography: Image Reconstruction from Projections*. 2nd ed. Springer.
:::

::: section
::: section-title
Key Papers
:::

Gordon, R., Bender, R., & Herman, G. T. (1970). Algebraic reconstruction techniques (ART) for three-dimensional electron microscopy and X-ray photography. *Journal of Theoretical Biology*, 29(3), 471--481.

Shepp, L. A. & Logan, B. F. (1974). The Fourier reconstruction of a head section. *IEEE Transactions on Nuclear Science*, 21(3), 21--43.

Andersen, A. H. & Kak, A. C. (1984). Simultaneous algebraic reconstruction technique (SART): a superior implementation of the ART algorithm. *Ultrasonic Imaging*, 6(1), 81--94.

Kaczmarz, S. (1937). Angenäherte Auflösung von Systemen linearer Gleichungen. *Bulletin International de l\'Académie Polonaise des Sciences et des Lettres*, 35, 355--357.

Feldkamp, L. A., Davis, L. C., & Kress, J. W. (1984). Practical cone-beam algorithm. *Journal of the Optical Society of America A*, 1(6), 612--619.

DeRosier, D. J. & Klug, A. (1968). Reconstruction of three dimensional structures from electron micrographs. *Nature*, 217, 130--134.
:::

::: section
::: section-title
Historical and Expository
:::

Gabor, D. (1948). A new microscopic principle. *Nature*, 161, 777--778.

Hadamard, J. (1902). Sur les problèmes aux dérivées partielles et leur signification physique. *Princeton University Bulletin*, 13, 49--52.

Wikipedia contributors. (2025). Radon transform. *Wikipedia, The Free Encyclopedia*.

Wikipedia contributors. (2025). Projection-slice theorem. *Wikipedia, The Free Encyclopedia*.
:::
:::
:::
:::

------------------------------------------------------------------------

::: page-footer
Loop MMT™ · Multi-Module Theory Tomographic Reconstruction & the Radon Transform Knowledge Pack · v1 © 2026 Shea Gunther · [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/deed.en){style="color:inherit;"}
:::
