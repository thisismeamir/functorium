---
sticker: lucide//atom
---
# Approach to Equilibrium and Thermodynamic Potentials

“The time evolution of systems toward equilibrium is governed by the second law of thermodynamics.” (Kardar, p. 16)

“What about out-of-equilibrium systems that are not adiabatically isolated, and may also be subject to external mechanical work?” (Kardar, p. 16)

**Enthalpy** is the appropriate function when there is no heat exchange ($\bar d Q = 0$), and the system comes to mechanical equilibrium with *a constant external force*. The minimum equilibrium principle merely formulates the observation that stable mechanical equilibrium is obtained by minimizing the net potential energy of the system *plus the external agent*. 

For any set of displacements $x$, at constant (externally applied) generalized forces $J$, the work input to the system is $\bar d W \leq \mathbf J \cdot \delta \mathbf x$ (Equality is achieved for a quasi-static change with $\mathbf J = \mathbf J_i, but there is generally some loss of the external work to dissipation). Since $\bar d Q = 0$ using the first law, $\delta E\leq \mathbf J\cdot \delta \mathbf x$. and $\delta H \leq 0$ where $H = E - \mathbf J\cdot \mathbf x$ is the enthalpy. The variations of $H$ i  equilibrium are given by:
$$dH = dE - d(\mathbf J \cdot \mathbf x) = TdS - \mathbf x \cdot d\mathbf J $$
The coordinate $(S,\mathbf J)$ is the natural choice for describing the enthalpy, and it follows from this equation that:

$$
x_i = \left.-\frac{\partial H}{\partial \mathbf J_i}\right\vert_{S,J_{j\not = i}}
$$

Variations of the enthalpy with temperature are related to heat capacities at constant force, for example:

$$
C_P = \left.\frac{\bar d Q}{dT}\right\vert_P = \left.\frac{dH}{dT}\right\vert_P 
$$

> [!NOTE]
> Note, however, that a change of variables is necessary to express $H$ in terms of $T$, rather than the more natural variable $S$

**Helmholtz free energy** is useful for isothermal transformations in the absence of mecchanical work ($\bar d W = 0$ ). It is rather similar to enthalpy, with $T$ taking the place of $J$. From Clausius's theorem, the heat intake of a system at a constant temperature satisfies $\bar d Q \leq T\delta S$ . Hence $\delta E = \bar d Q + \bar d W  \leq T\delta S$, and: 

$$\delta F \leq 0  \ \ \ \ \text{where} \ \ \ \ F = E -TS$$
is the Helmholtz free energy. Since:

$$
dF = dE - d(TS) = TdS + \mathbf J\cdot d \mathbf x - SdT - TdS = -SdT +\mathbf J\cdot d\mathbf x
$$
The coordinate set $(T,\mathbf x)$ is most suitable for describing free energy.  The equilibrium forces and entropy can be obtained by:

$$

J_i = \left.\frac{\partial F}{\partial x_i}\right\vert_{T,x_{j\not=i}} \ \ \ , \ \ \ S = \left.-\frac{\partial F}{\partial T}\right\vert_{x}.
$$
The internal energy can also be calculated from $F$:
$$
E + F+TS = F-T \left.\frac{\partial F}{\partial T}\right\vert_{x} = -\left.T^2\frac{\partial (F/T)}{\partial T}\right\vert_{x}
$$

**Gibbs free energy** applies to isothermal transformations involving mechanical work at constant external force. The natural inequalities for work and heat input into the system are given by $\bar d W \leq \mathbf J\cdot \delta \mathbf x$ and $\bar d Q \leq T\delta S$. Hence $\delta E \leq T\delta S + \mathbf J \cdot \delta \mathbf x$, leading to

$$
\delta G \leq 0  \ \ \ \text{where} \ \ \ G = E-TS - \mathbf J\cdot \mathbf x
$$
is the Gibbs free energy. Variations of $G$ are given by:

$$
d G = dE - d(TS) - d(\mathbf J \cdot \mathbf x) = TdS + \mathbf J\cdot d\mathbf x - SdT -TdS - \mathbf x\cdot d\mathbf J - \mathbf J \cdot d \mathbf x 
$$
which gives out:

$$
dG = -SdT - \mathbf x \cdot d\mathbf J
$$
and most easily expressed in terms of $T$ and $\mathbf J$ 

Until now we've used the assumption that the number of particles does not change in our system, and in equilibrium between two phases, the number of particles in a given constituent may change. The change in the number of particles necessarily involves changes in the internal energy, which is expressed in terms of a chemical work $\bar d W = \mu \cdot d \mathbf N$. The vector $N$ is just a list of number of particles of each species, and $\mu$ is the associated chemical potentials that measure the work necessary to add additional particles to the system.

For chemical equilibrium in circumstances that involve no mechanical work, the appropriate state function is the grand potential given by:

$$
\mathcal {G} = E - TS - \mathbf \mu \cdot \mathbf N
$$

The grand potential is minimized in chemical equilibrium, and its variations in general satisfy:

$$
d\mathcal G = -SdT + \mathbf J \cdot d\mathbf x - \mathbf N \cdot d\mu 
$$

The following sections of chapter 1, I didn't write note for, I list topics and you do exactly what you're doing as before:
