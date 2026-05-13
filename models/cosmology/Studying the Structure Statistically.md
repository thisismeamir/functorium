# Toolkit: Studying Structure Statistically

## Why Fourier Space?

Working in **[[Fourier space]]** decomposes a field into modes of different wavelengths — each mode labeled by a **[[wavenumber]]** $k \sim 1/\lambda$. This is powerful because:

- Large $k$ → small scales; small $k$ → large scales. They separate cleanly.
- In the linear regime, different Fourier modes **evolve independently** — they don't mix. This makes the equations of motion far simpler.
- It turns convolutions in real space into simple multiplications in Fourier space.
- Physical processes (e.g. [[Silk damping]], [[baryon acoustic oscillations]]) imprint characteristic scales, which show up as features at specific $k$ values — much easier to identify in Fourier space than in real space.

## The Two-Point Correlation Function

For a random field like the galaxy distribution, the most natural question is: _"If I find a galaxy at position $\mathbf{x}$, how likely am I to find another one at position $\mathbf{x} + \mathbf{r}$?"_ This is the **[[two-point correlation function]]**:

$$\xi(\mathbf{r}) = \langle \delta(\mathbf{x}), \delta(\mathbf{x} + \mathbf{r}) \rangle$$

It measures **excess clustering** relative to a random (Poisson) distribution. It is the most important statistic because:

- For a [[Gaussian random field]] — which the primordial perturbations are predicted to be — the two-point function contains **all the statistical information**. Higher-order correlations add nothing new.
- It is directly measurable from surveys and directly predictable from theory.

## The Galaxy Density Field and Power Spectrum

Define the **[[overdensity field]]**:

$$\delta_g(\mathbf{x}) = \frac{n_g(\mathbf{x}) - \bar{n}_g}{\bar{n}_g}$$

By construction $\langle \delta_g \rangle = 0$. Its Fourier transform $\tilde{\delta}_g(\mathbf{k})$ encodes how much structure exists at each scale $k$.

The **[[galaxy power spectrum]]** $P_g(k)$ is defined via:

$$\langle \tilde{\delta}_g(\mathbf{k}), \tilde{\delta}_g^*(\mathbf{k}') \rangle = (2\pi)^3, \delta_D^{(3)}(\mathbf{k} - \mathbf{k}'), P_g(k)$$

Unpacking this:

- The angle brackets $\langle \cdots \rangle$ denote an **ensemble average** — an average over many realizations of the universe (in practice, over many regions of the survey).
- The **[[Dirac delta]] $\delta_D^{(3)}(\mathbf{k} - \mathbf{k}')$** enforces that different Fourier modes are **uncorrelated** — a consequence of statistical homogeneity ([[translational invariance]]).
- $P_g(k)$ depends only on the magnitude $k = |\mathbf{k}|$, not direction — a consequence of statistical isotropy.
- So $P_g(k)$ simply measures the **variance** of fluctuations at scale $k$: large $P_g$ means lots of structure at that scale.

## CMB: Spherical Harmonics Instead of Fourier Modes

The CMB temperature is a **2D field on the celestial sphere**, so Fourier modes are not the natural basis. Instead, one expands in **[[spherical harmonics]]** $Y_\ell^m(\theta, \phi)$:

$$\frac{\Delta T}{T}(\hat{n}) = \sum_{\ell, m} a_{\ell m}, Y_\ell^m(\hat{n})$$

The analog of the power spectrum is then $C_\ell$, a function of **[[multipole moment]]** $\ell$ rather than wavenumber $k$. Roughly, $\ell \sim \pi / \theta$, so large $\ell$ corresponds to small angular scales. The two-point function is again the key statistic for the same reason — primordial perturbations are Gaussian.

---

# From Smooth Early Universe to Clustered Late Universe

## The Contrast Problem

The CMB shows fractional temperature fluctuations of only $\delta T / T \sim 10^{-5}$ at $z \simeq 1100$. Yet today the universe is **highly inhomogeneous** — galaxies, clusters, filaments, and voids span many orders of magnitude in density contrast. How did such rich structure emerge from such a smooth beginning?

## Gravitational Instability

The answer is **[[gravitational instability]]**. The mechanism is conceptually simple but extraordinarily powerful:

1. The early universe had tiny overdense regions — patches where $\delta \rho / \rho \sim 10^{-5}$.
2. These regions exert a slightly stronger gravitational pull than their surroundings.
3. Nearby matter falls in, making the region denser.
4. A denser region pulls harder, attracting yet more matter.
5. This is a **runaway process** — a positive feedback loop driven purely by gravity.

Over cosmic time (~13.8 Gyr), these tiny seeds collapsed into the sites of **galaxy formation**, **galaxy clusters**, and the **[[cosmic web]]** of filaments and voids we observe today.

> In the linear regime, overdensities grow as $\delta \propto a(t)$ in a matter-dominated universe — the **[[linear growth factor]]**. Once $\delta \sim 1$, the perturbation goes nonlinear and collapses, eventually virializing into a bound structure ([[Press-Schechter theory]]).

The fact that $10^{-5}$ fluctuations at recombination produce the observed universe today is one of the great quantitative successes of [[ΛCDM]].
