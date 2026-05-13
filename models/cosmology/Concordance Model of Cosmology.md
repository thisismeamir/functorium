# Overview

The discovery of [[Model of General Relativity|General Relativity]] enabled us, for the first time in history to answer some fundamental questions about the universe as a whole. The success of Big Bang paradigm with a number of observational pillars such:

- Hubble Diagram that measures expansion;
- Light element abundances that are in accord with Big Bang Nucleosynthesis;
- Temperature and Polarization anisotropies in the Cosmic Microwave Background that agree well with theory;
- Multiple probes of large-scale structure that also agree with the concordance model.

This success has come at a price, we are now forced to introduce several ingredients that go beyond the Standard Model of particle physics.

- Dark Matter and Dark Energy, which together dominate the energy budget of the universe over most of its lifetime;
- A mechanism generating the small initial perturbations out of which structure formed, the most popular explanation being inflation.

# A Nutshell History of the Universe

We have solid evidence that the universe is expanding. This means that early in its history the distance between us and distant galaxies was smaller than it is today.

We describe this effect by introducing the scale factor $a$, whose present value is set to $1$ for simplicity. This is not a movement in the sense of objects, while the space expands everything gets further from everything else. It can be demonstrated as the figure below:

![[Pasted image 20260505232535.png]]

A directly related effect is that the physical wavelength of light emitted from a distant object is stretched out proportionally to the scale factor, so that the observed wavelength is larger than the one at which the light was emitted. We define this stretching factor as the redshift $z$:

$$
1 + z \equiv \frac{\lambda_{\text{obs}}}{\lambda_{\text{emit}}} = \frac{a_{\text{obs}}}{a_{\text{emit}}} = \frac{1}{a_{\text{emit}}}
$$
In addition to the scale factor and its evolution, the smooth universe is characterized by one other parameter, its geometry.

There are three possibilities for the universe in terms of curvature and geometry:

1. Euclidean
2. Open Universe
3. Closed Universe.

To understand these three possibilities consider two particles moving in parallel to each other. In a *Euclidean* universe, which is also called a flat universe, the particles behave as Euclid himself expected them to: their trajectories remain parallel as long as they travel freely (no force or gravitation). If the universe is close, the initially parallel particles gradually converge, just as in the case of the $2$-sphere all lines of constant longitude meet at the poles. Finally, in an open universe, the initially parallel paths diverge, as would two marbles rolling of a saddle.

General Relativity provides connection from geometry to energy. Therefore, the total energy density in the universe must determine the geometry; if the density is higher than a critical value, $\rho_{\text{cr}}$, the universe is closed; if the density is lower, it is open, and finally if it is exactly the critical value, it is flat. The latter seems very unlikely with respect to the other two, yet, all observations indicate that the universe is flat to within errors! Inflation provides a natural explanation for why this is the case.

We must therefore, determine the evolution of the scale factor with cosmic time. Again, general relativity provides the connection between this evolution and the energy in the universe.

![[Pasted image 20260505234034.png]]

This figure demonstrates how the universe ages, with the convention that $a$ is $1$ today. Note that the dependence of $a$ on $t$ varies as the universe evolves. At early times, $\alpha \propto t^{1/2}$ while at later times the dependence switches to $\alpha \propto t^{2/3}$. 

How the scale factor varies with time is determined by the evolution of the energy density in the universe. At early times, radiation dominates, while at later times, nonrelativistic matter accounts for most of the energy density. In fact, one way to explore the energy content of the universe is to measure changes in the scale factor.

As a part of this exploration, we now know that $a$ has been growing faster than $t^{2/3}$ very recently, a signal that a new form of energy has come to dominate the late-time cosmological landscape. 

To quantify the change in the scale factor and its relation to the energy it is useful to define the Hubble rate:

$$
H(t) \equiv \frac{1}{a} \frac{\mathrm{d}a}{\mathrm{d}t}
$$
which measures how rapidly the scale factor changes. 

$$
H_{0}\equiv H(t_{0})
$$
Is that value today, which is known as Hubble's constant. Thus, in a Euclidean, matter-dominated universe (not ours!), the product $H_{0}t_{0}$ equals $\frac{2}{3}$.

More generally, general relativity predicts that the scale factor is determined by the Friedmann equation

$$
H^{2}(t) = \frac{8\pi G}{3} \left[ \rho(t) + \frac{\rho_{\text{cr}}-\rho(t_{0})}{a^{2}(t)} \right] 
$$
where $G$ is Newton's constant; $\rho(t)$ is the energy density in the universe as a function of time with $\rho(t_{0})$ its value today. If it were Euclidean, the sum of all the energy densities today would equal the critical density, and the last term would vanish. If the universe is not Euclidean, the curvature contribution scales as $\frac{1}{a^{2}}$. 

To use the Friedmann equation, we must know how the energy density evolves with time. This turns out to be a complicated question because $\rho$ is the sum of several different components, each of which scales differently with time. Consider first nonrelativistic matter, which means that the energy of a given constituent particle is essentially equal to its rest mass energy, which remains constant in time. 

The energy density of a collection of these particles is therefore equal to the rest mass energy times the number density. When the scale factor was smaller, the densities were necessarily larger. 

Since the number density is inversely proportional to volume, it should be proportional to $a^{-3}$. Therefore, the energy density of nonrelativistic matter scales as $a^{-3}$.

Apart from the matter, a sea of massless photons permeates the universe, as first discovered in 1965. These photons have traveled freely since the universe was very young. Today, their wavelength lie in the microwave regime, so they comprise what is called the cosmic microwave background (CMB). The CMB has a perfect black-body spectrum with a very well-measured temperature of $T_{0}=2.726\pm 0.001\text{K}$ today.  Our redshift relation can give us a way to derive how this temperature evolved over the history of the universe:

$$
T(t) = \frac{T_{0}}{a(t)}
$$
