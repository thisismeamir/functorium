---
sticker: lucide//atom
---
# A Nutshell History of the Universe

## General Relativity as a Cosmological Tool

The discovery of [[General Relativity]] enabled, for the first time, answers to fundamental questions about the universe as a whole. The [[Big Bang]] paradigm rests on several observational pillars:

- The [[Hubble diagram]], measuring cosmic expansion
- [[Big Bang Nucleosynthesis|Light element abundances]] consistent with BBN predictions
- [[CMB]] temperature and polarization anisotropies in agreement with theory
- Multiple probes of [[large-scale structure]] consistent with the [[concordance model]] ($\Lambda$CDM)

This success comes at a cost — we are forced to introduce ingredients beyond the [[Standard Model]] of particle physics:

- **[[Dark Matter]]** and **[[Dark Energy]]**, which together dominate the energy budget over most of cosmic history
- A mechanism generating the small initial perturbations that seeded structure — the leading candidate being **[[inflation]]**

## The Scale Factor and Expansion

The universe is expanding. Early in its history, distances between objects were smaller. We encode this in the **[[scale factor]]** $a(t)$, normalized to $a(t_0) = 1$ today. This is not motion through space — space itself expands, carrying everything with it.

A direct consequence: the physical wavelength of light stretches proportionally to $a$, giving rise to **[[cosmological redshift]]**:

$$1 + z \equiv \frac{\lambda_\text{obs}}{\lambda_\text{emit}} = \frac{a_\text{obs}}{a_\text{emit}} = \frac{1}{a_\text{emit}}$$


## Geometry of the Universe

Beyond the scale factor, the smooth universe is characterized by its **[[spatial curvature]]**. There are three possibilities:

| Geometry             | Curvature | Parallel paths                                 |
| -------------------- | --------- | ---------------------------------------------- |
| **Flat** (Euclidean) | $k = 0$   | Stay parallel                                  |
| **Closed**           | $k = +1$  | Converge (like lines of longitude on a sphere) |
| **Open**             | $k = -1$  | Diverge (like lines on a saddle)               |

GR connects geometry to energy density. If $\rho > \rho_\text{cr}$, the universe is closed; if $\rho < \rho_\text{cr}$, open; if $\rho = \rho_\text{cr}$, flat. All current observations point to a **flat universe** — something inflation explains naturally.

## The Friedmann Equation

The evolution of $a(t)$ is governed by the energy content of the universe via the **[[Friedmann equation]]**:

$$H^2(t) = \frac{8\pi G}{3}\left[\rho(t) + \frac{\rho_\text{cr} - \rho(t_0)}{a^2(t)}\right]$$

where the **[[Hubble rate]]** is defined as:

$$H(t) \equiv \frac{1}{a}\frac{da}{dt}, \qquad H_0 \equiv H(t_0)$$

The curvature term scales as $a^{-2}$; for a flat universe it vanishes exactly.

## Energy Components and Their Scaling

Different components of $\rho$ scale differently with $a$:

- **[[Nonrelativistic matter]]:** number density $\propto a^{-3}$, so $\rho_m \propto a^{-3}$
- **[[Radiation]] (photons):** $\rho_r \propto a^{-4}$ (one extra factor from redshifting of energy)
- **[[Dark energy]] / [[Cosmological constant]]:** $\rho_\Lambda \approx \text{const}$

This drives distinct epochs:

- **Early universe:** radiation-dominated, $a \propto t^{1/2}$
- **Later:** matter-dominated, $a \propto t^{2/3}$
- **Recent times:** $a$ growing _faster_ than $t^{2/3}$ — evidence that [[dark energy]] now dominates

## The CMB Temperature

The universe is filled with a sea of massless photons — the **[[CMB]]** — with a present-day temperature:

$$T_0 = 2.726 \pm 0.001 , \text{K}$$

From the redshift relation, the temperature evolves as:

$$T(t) = \frac{T_0}{a(t)}$$

So the early universe was much hotter — at $z \simeq 1100$, $T \sim 3000,\text{K}$, the threshold for [[recombination]].
