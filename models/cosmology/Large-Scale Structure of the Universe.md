---
sticker: lucide//atom
---
# Large-Scale Structure of the Universe

## Overview

The existence of [[large-scale structure]] in the universe was established well before the detection of [[CMB]] anisotropies. Galaxy surveys of the local universe clearly demonstrated that galaxies are not distributed homogeneously — they cluster, forming filaments, voids, and walls.

The number of galaxies and volume covered by such surveys has grown exponentially over time.

## Key Observation

Galaxies are not distributed randomly. The universe has structure on large scales. To understand this structure, we must develop the tools to study **perturbations** around the smooth [[FLRW]] background.

![[Pasted image 20260513162656.png]]
## Linear vs. Nonlinear Perturbations

To compare theory with observations, we must stay within regimes describable by **small (linear) perturbations**. The intermediate processes — collapse of matter into a [[galaxy]], [[star formation]], [[planet formation]], geology, etc. — are far too complex to be captured by linear theory.

- On **small scales** (< ~[[10 Mpc]]), density perturbations have grown **nonlinear** in the late universe: fractional density fluctuations $\delta \rho / \rho \gtrsim 1$.
- On **large scales**, perturbations remain small — these regions are still in the **linear regime**.

## Why CMB and Large-Scale Structure?

[[CMB]] anisotropies are small because they originated at early times, when perturbations were still tiny. This makes two observational windows ideal for comparison with linear perturbation theory:

1. **CMB anisotropies** — a snapshot of perturbations at [[recombination]]
2. **Large-scale structure** — galaxy distributions on scales $\gtrsim 10 , \text{Mpc}$

## Toolkit

It is important to develop tools that help us compare maps of the universe that we have. For this purpose, it is often useful to take the Fourier transform of the distribution in question; working in Fourier space makes it easier to separate large from small scales. (Me: Why?)

The most important statistic in the cases of both the CMB and the large-scale structure is the two-point function, short-hand for two-point correlation function (Me: What is that?). When measured using Fourier Space fields, it is called the power spectrum.

Consider the number density of galaxies in the SDSS survey. If the density of galaxies as a function of position is $n_{g}(x)$, and its mean over the whole survey is $\bar{n}_{g}$, then we can characterize the inhomogeneities with $\delta_{g}(x) = (n_{g}(x) - \bar{n}_{g}) /\bar{n}_{g}$, or its Fourier transform $\tilde{d}\delta_{g}(k)$.  By construction, the mean of the field $\delta_{g}(x)$ is equal to zero. We then consider the galaxy power spectrum $P_{g}(k)$ which is defined via:
$$
\langle \tilde{\delta}_{g}(k)\tilde{\delta}_{g}^{\ast} (k')  \rangle = (2\pi)^{3} \delta_{D}^{(3)}(k-k')P_{g}(k) 
$$
(Me: Explain this further)

The best measure of anisotropies in CMB also is the two-point function (Me: Why?), of the intensity on the sky in this case. There is a technical difference because the CMB temperature is a two-dimensional field, measured everywhere on the sky. Then instead of Fourier transforming the CMB temperature, then, one typically expands it in spherical harmonics, a basis appropriate for a 2D field on the surface of a sphere. Therefore the power spectrum of the CMB is a function of the multipole moment $l$, not wave number $k$. 

## Difference of the Early and Late Universe

One key difference between the map of the CMB and that of the structure in the current universe is the contrast, or amplitude of structure. The very early universe was very smooth while maps of the current universe as depicted in above suggests that the universe is very inhomogeneous.  (Me: Go further about how is this possible, The simple answer, and most powerful is that gravity forced more and more matter into overdense regions, so that a region starting out with only a small density evolved to become much denser than the homogeneous universe today and in fact the site at which a galaxy formed). 