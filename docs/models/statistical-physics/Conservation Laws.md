# Conservation Laws

## Approach to Equilibrium

How the gas reaches its final equilibrium. Consider a situation in which the gas is perturbed from the equilibrium form:

$$
f_{1}(\vec{p},\vec{q}) = n \left( \frac{\beta}{2\pi m} \right)^{3 / 2} \exp \left[ - \frac{\beta(\vec{p}-\vec{p}_{0})^{2}}{2m} \right]. 
$$
and follow its relaxation to equilibrium. There is a hierarchy of mechanisms that operate at different time scales.

- The fastest processes are the two body collision of partices in immediate vicinity. Over a time scale of the order $\tau_{c}$, $f_{2}(\vec{q}_{1},\vec{q}_{2},t)$ relaxes to $f_{1}(\vec{q}_{1},t)f_{1}(\vec{q}_{2},t)$ for separations $|\vec{q}_{1}-\vec{q}_{2}| \gg d$. Similar relaxations occur for the higher-order densities $f_{s}$.
- At the next stage, $f_{1}$ relaxes to a *local equilibrium* form as 
$$
  f_{1}(\vec{p},\vec{q}) = \mathcal{N}(\vec{q})\exp \left[ -\vec{\alpha}(\vec{q})\cdot \vec{p} - \beta(\vec{q})\left(  \frac{\vec{p}^{2}}{2m} + U(\vec{q}) \right)  \right] 
$$
	over the time scale of the mean free time $\tau_{\times}$. This is the intrinsic scale set by the collision term on the right-hand side of the Boltzmann equation. After this time interval, quantities conserved in collisions achieve a state of local equilibrium. We can then define at each point a (time-independent) local density by integrating over all momenta as:
$$
	n(\vec{q},t) = \int \mathrm{d}^{3}\vec{p}f_{1}(\vec{p},\vec{q},t),
$$
	as well as a local expectation value for any operator $\mathcal{\mathrm{O}}(\vec{q},\vec{p},t)$:
$$
	\langle \mathcal{\mathrm{O}}(\vec{q},\vec{p},t) \rangle = \frac{1}{n(\vec{q},t)}\int \mathrm{d}^{3}\vec{p}f_{1}(\vec{p},\vec{q},t)\mathcal{O}(\vec{p},\vec{q},t) 
$$
- After the densities and expectation values have relaxed to their local equilibrium forms in the intrinsic time scales $\tau_{c}$ and $\tau_{\times}$, there is a subsequent slower relaxation to global equilibrium over extrinsic time and length scales. This final stage is governed by the smaller streaming terms on the left-hand side of the Boltzmann equation. It is most conveniently expressed in terms of the time evolution of conserved quantities according to hydrodynamic equations.

## Conserved Quantities

Conserved quantities are left unchanged by the two-body collisions, that is they satisfy:

$$

$$