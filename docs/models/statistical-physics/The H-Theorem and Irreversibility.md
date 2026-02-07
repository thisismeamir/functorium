# H-Theorem

While it is possible to obtain steady state solutions for the full phase space density $\rho_{N}$, because of time reversal symmetry these solutions are not attractors of generic non-equilibrium densities.  The question is *whether a collection of particles naturally evolve toward an equilibrium state*. Does the unconditional one-particle PDF $\rho_{1}$ suffer the same problem as $\rho_{N}$?

The H-Theorem proves that an approximate $\rho_{1}$, goverend by the Boltzmann equation, does in fact non-reversibly approach an equilibrium form. This theorem states that:

*If $f_{1}(\vec{p},\vec{q},t)$ satisfies the Boltzmann equation, then $\mathrm{d}H / \mathrm{d}t \leq 0$, where*:

$$
H(t) = \int \mathrm{d}^{3}\vec{p}\mathrm{d}^{3}\vec{q}f_{1}(\vec{p},\vec{q},t)\ln f_{1}(\vec{p},\vec{q},t).
$$

The function $H(t)$ is related to the information content of the one-particle PDF. Up to an overall constant, the information content of $\rho_{1} = f_{1} / N$ is given by

$$
I[\rho_{1}] = \langle \ln \rho_{1} \rangle
$$
which is clearly similar to $H(t)$.

*proof:*

The time derivative of $H$ is:

$$
\frac{\mathrm{d}H}{\mathrm{d}t} = \int \mathrm{d}^{3}\vec{p}_{1} \mathrm{d}^{3}\vec{q}_{1} \frac{\partial f_{1}}{\partial t}\left( \ln f_{1} + 1 \right) = \int \mathrm{d}^{3}\vec{p}_{1}\mathrm{d}^{3}\vec{q}_{1} \ln f_{1} \frac{\partial f_{1}}{\partial t} 
$$

The last equality is because:

$$
\int \mathrm{d}V_{1} f_{1} = N \int \mathrm{d}\Gamma \rho = N
$$
is time-independent.
