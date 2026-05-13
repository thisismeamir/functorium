# Overview

Particles, charged or neutral, can only be sensed by interacting with matter. Detectors usually exploit the following processes:

- ionization and excitation of atoms in media by charged particles;
- Bremsstrahlung: photon radiation emitted by charged particles in the fields of atomic nuclei;
- photon scattering and photon absorption;
- Cherenkov and transition radiation;
- nuclear reactions: hadrons $(p,n,\pi,\alpha, \dots)$ with nuclear matter;
- weak interactions constituting the only possibility to detect neutrinos.

Generally, a particle will undergo more than just one interaction process on its path through matter if it is not absorbed in its first interaction. The probability that a particle interacts with the atoms of a medium is defined by the cross section of a reaction. The definition of the cross section and related terms will be given in the following section.

# Cross Sectiona and Absorption of Particles and Radiation in Matter

The cross sections is a measure for the probability of a particle reaction, which in turn depends on the kind and strength of the interactions between the scattering partners. It can be interpreted as an effective interaction area. 

The cross section $\sigma$ represents the effective area of a target particle 'seen' by an incoming particle beam. We assume for simplicity that the beam particles have to spatial extent. The beam enters the target with area $S$ and length $l$ with a rate $\dot{N}_{\text{in}}$. There are:

$$
N_{T}=\frac{\rho V}{A}N_{A}
$$
particles in the target volume $V=Sl$ where $\rho$ is the target mass density, $A$ the atomic mass per mole of the target particles and $N_{A}$ is Avogadro's number.

![[Pasted image 20260508163516.png]]

The target can consist of any type of particle if $A$ is taken as the corresponding mass per mole.

The particle number density is given by 

$$
n = \frac{N_{T}}{V} = \frac{\rho}{A} N_{A}
$$

The beam sees a total area $N_{T}\sigma$ of target particles. The probability to hit a target particle is $P = \frac{N_{T}\sigma}{S}$. This probability can also be expressed by the scattering or reaction rate $\dot{N}_{R}$ relative to the rate of incoming beam particles $\dot{N}_{\text{in}}$, provided that the target is sufficiently thin such that any change of the beam while passing the target can be neglected:

$$
P = \frac{\dot{N}_{R}}{\dot{N}_{\text{in}}} = \frac{N_{T}\sigma}{S} =n \sigma l.
$$
The cross section can then be expressed as:

$$
\sigma = \frac{\dot{N}_{R}}{\dot{N}_{\text{in}}} \frac{1}{nl}
$$
Hence the reaction rate is proportional to the cross section, the proportionality constant being the luminosity $L$:

$$
\dot{N}_{R}=\sigma L, \ \ L = \dot{N}_{\text{in}}nl
$$
The term luminosity, here defined for a so-called fixed-target experiment, is more commonly used for colliding beams.

![[Pasted image 20260508163743.png]]

If the assumption of a thin target is no longer valid one must take into account that the number of particles $N(x)$ that have thus far not interacted with the target decreases exponentially with the penetration depth $x$:

$$
\frac{\mathrm{d}N}{N} = -n\sigma \mathrm{d}x
$$
which means

$$
N(x) = N_{0} e^{-\mu x}
$$
If the beam particles are absorbed when they interact with target particles then $\mu = n\sigma$ is called the absorption coefficient or linear attenuation coefficient. This equation is known as the Beer-Lambert Law. The mean free path of a particle is defined as:

$$
\lambda = \frac{1}{\mu} = \frac{1}{n\sigma}
$$
The cross section has dimensions of area; its unit is called *barn*:

$$
1 \text{ barn} = 1\text{b} = 10^{-24}\text{cm}^{2}
$$
Since nuclear densities are largely independent of the mass of a nucleus, the nuclear volume is roughly proportional to the number of nucleons $\mathcal{A}$ and the cross-sectional area is proportional to $\mathcal{A}^{2/3}$. Because of the short-range nature of nuclear forces their geometrical area also governs the order of magnitude of their interaction cross sections:

$$
\sigma_{\text{nucl}} \approx \pi r_{0}^{2}\mathcal{A}^{2/3} \approx 45 \text{mb} \mathcal{A}^{2/3}.
$$

