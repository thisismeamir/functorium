---
sticker: lucide//atom
---
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
\mathcal{X}(\vec{p}_{1},\vec{q},t) +\mathcal{X}(\vec{p}_{2},\vec{q},t) = \mathcal{X}(\vec{p}_{1}',\vec{q},t) + \mathcal{X}(\vec{p}_{2}',\vec{q},t),
$$

For such quantities we have:

$$
J_{\mathcal{X}}(\vec{q},t) = \int \mathrm{d}^{3}\vec{p}\mathcal{X}(\vec{p},\vec{q},t) \left. \frac{\mathrm{d}f_{1}}{\mathrm{d}t} \right\vert_{\text{coll.}}(\vec{p},\vec{q},t)= 0
$$

*Proof* Using the form of the collision integral, we have

$$
J_{\mathcal{X}} =-\int \mathrm{d}^{3}\vec{p}_{1}\mathrm{d}^{3}\vec{p}_{2}\mathrm{d}^{2}\vec{b} |\vec{v}_{1}-\vec{v}_{2}| [f_{1}(\vec{p}_{1})f_{1}(\vec{p}_{2})-f_{1}(\vec{p}_{1}')f_{1}(\vec{p}_{2}')]\mathcal{X}(\vec{p}_{1})
$$
We now perform the same set of changes of variables that were used in the proof of the $H$-theorem. The first step is averaging after exchange of the dummy variables $\vec{p}_{1}$ and $\vec{p}_{2}$, leading to

$$
J_{\mathcal{X}}=-\frac{1}{2}\int \mathrm{d}^{3}\vec{p}_{1}\mathrm{d}^{3}\vec{p}_{2}\mathrm{d}^{2}\vec{b}|\vec{v}_{1}-\vec{v}_{2}| [f_{1}(\vec{p}_{1})f_{1}(\vec{p}_{2})-f_{1}(\vec{p}_{1}')f_{1}(\vec{p}_{2}')][\mathcal{X}(\vec{p}_{1})+\mathcal{X}(\vec{p}_{2})]
$$

Next change variables from the originators $(\vec{p}_{1},\vec{p}_{2},\vec{b})$ to the products $(\vec{p}_{1}',\vec{p}_{2}',\vec{b}')$ of the collision. After relabeling the integration variables the above equation is transformed to:

$$
\begin{align}
J_{\mathcal{X}} =  & -\frac{1}{2}\int \mathrm{d}^{3}\vec{p}_{1}\mathrm{d}^{3}\vec{p}_{2}\mathrm{d}\vec{b} |\vec{v}_{1}-\vec{v}_{2}| \\
 & [f_{1}(\vec{p}_{1}')f_{1}(\vec{p}_{2}')-f_{1}(\vec{p}_{1})f_{1}(\vec{p}_{2})][\mathcal{X}(\vec{p}_{1}')+\mathcal{X}(\vec{p}_{2}')]
\end{align}
$$

Averaging the last two equations leads to:

$$
\begin{align}
J_{\mathcal{X}}=- & \frac{1}{4}\int \mathrm{d}^{3}\vec{p}_{1}\mathrm{d}^{3}\vec{p}_{2}\mathrm{d}^{2}\vec{b} |\vec{v}_{1} \vec{v}_{2}| \\
 & [f_{1}(\vec{p}_{1})f_{1}(\vec{p}_{2})-f_{1}(\vec{p}_{1}')f_{1}(\vec{p}_{2}')][\mathcal{X}(\vec{p}_{1}) + \mathcal{X}\vec{p}_{2}-\mathcal{X}(\vec{p}_{1}')\mathcal{X}(\vec{p}_{2}')]
\end{align}
$$

which is zero from our first assumption.

Let us explore the consequences of this result for the evolution of expectation values involving $\mathcal{X}$. Substituting for the collision term in $J_{\mathcal{X}}$ introduced initially, the streaming terms on the left-hand side of the Boltzmann equation lead to:

$$
J_{\mathcal{X}}(\vec{q},t) = \int \mathrm{d}^{3}\vec{p}\mathcal{X(\vec{p},\vec{q},t)}\left[ \partial_{t}+ \frac{p_{\alpha}}{m}\partial_{\alpha} +F_{\alpha} \frac{\partial}{\partial p_{\alpha}} \right]f_{1}(\vec{p},\vec{q},t)=0 
$$

We can manipulate the above equation into the form:

$$
\int \mathrm{d}^{3}\vec{p}\left\{ \left[ \partial_{t} + \frac{p_{\alpha}}{m}\partial_{\alpha}+F_{\alpha} \frac{\partial}{\partial p_{\alpha}} \right] (\mathcal{X} f_{1}) - f_{1}\left[ \partial_{t} +\frac{p_{\alpha}}{m}\partial_{\alpha} + F_{\alpha} \frac{\partial}{\partial p_{\alpha}} \right]\mathcal{X}  \right\}=0 
$$

The third term is zero, as it is a complete derivative. The expectation values then becomes:

$$
\partial_{t}(n\langle \mathcal{X} \rangle )+\partial_{\alpha}\left( n \left\langle \frac{p_{\alpha}}{m}\mathcal{X} \right\rangle  \right) -n \langle \partial_{t}\mathcal{X} \rangle -n \left\langle \frac{p_{\alpha}}{m}\partial_{\alpha}\mathcal{X} \right\rangle -nF_{\alpha} \left\langle \frac{\partial \mathcal{X}}{\partial p_{\alpha}} \right\rangle =0
$$

- [ ] TODO: I have to refine this note, and also continue it from Kardar.