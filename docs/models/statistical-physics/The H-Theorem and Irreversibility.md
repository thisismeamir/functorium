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

is time-independent. The time integral can be substituted using the Boltzmann equation:

$$
\begin{align}

\frac{\partial f_{1}}{\partial t}  & =\left[ \frac{\partial}{\partial \vec{q}_{1}} U(\vec{q}_{1}) \frac{\partial}{\partial \vec{p}_{1}} + \frac{\vec{p}_{1}}{n} \frac{\partial}{\partial \vec{q}_{1}} \right]f_{1}  \\
 & -\int \mathrm{d}^{3}\vec{p}_{2}\mathrm{d}^{2}\Omega \left| \frac{\mathrm{d}\sigma}{\mathrm{d}\Omega} \right| \left| \vec{v_{1}}-\vec{v_{2}} \right| \\
 & \cdot\left[ f_{1}(\vec{p}_{1},\vec{q}_{1},t)f_{1}(\vec{p}_{2},\vec{q}_{2},t)-f_{1}(\vec{p}_{1}',\vec{q}_{1},t)f_{1}(\vec{p}_{2}',\vec{q}_{1},t) \right]  
\end{align}
$$

Resulting in:

$$
\begin{align}
\frac{\mathrm{d}H}{\mathrm{d}t} =  & \int \mathrm{d}^{3}\vec{p}_{1}\mathrm{d}^{3}\vec{q}_{1} \ln f_{1} \left( \frac{\partial U}{\partial \vec{q}_{1}}\cdot \frac{\partial f_{1}}{\partial \vec{p}_{1}} - \frac{\vec{p}_{1}}{m}\cdot \frac{\partial f_{1}}{\partial \vec{q}_{1}} \right) \\
 & -\int \mathrm{d}^{3}\vec{p}_{1}\mathrm{d}^{3}\vec{q}_{1}\mathrm{d}^{3}\vec{p}_{2}\mathrm{d}^{2}\sigma \left| \vec{v}_{1}-\vec{v}_{2} \right| \left[ f_{1}(\vec{p}_{1},\vec{q}_{1})f_{1}(\vec{p}_{2},\vec{q}_{1})\right. \\
 & \left. -f_{1}(\vec{p}_{1}',\vec{q}_{1})f_{1}(\vec{p}_{2}',\vec{q}_{1}) \right]\ln f_{1}(\vec{p}_{1},\vec{q}_{1})   
\end{align}
$$

where we shall interchangeably use $\mathrm{d}^{2}\sigma, \mathrm{d}^{2}\vec{b},$ or $\mathrm{d}^{2}\Omega |\mathrm{d}\sigma / \mathrm{d}\Omega$ for the differential corss-section. The streaming terms in the above expression are zero, as shown through successive integration by parts:

$$
\begin{align}
\int \mathrm{d}^{3}\vec{p}_{1}\mathrm{d}^{3}\vec{q}_{1} \ln f_{1} \frac{\partial U}{\partial \vec{q}_{1}}\cdot \frac{\partial f_{1}}{\partial \vec{p}_{1}} & = - \int \mathrm{d}^{3}\vec{p}_{1}\mathrm{d}^{3}\vec{q}_{1} \frac{\partial}{\partial \vec{p}_{1}}\left( \ln f_{1} \frac{\partial U}{\partial \vec{q}_{1}} \right) f_{1} \\
 & = \int \mathrm{d}^{3}\vec{p}_{1}\mathrm{d}^{3}\vec{q}_{1}f_{1} \frac{\partial}{\partial \vec{p}_{1}} \frac{\partial U}{\partial \vec{q}_{1}} = 0,
\end{align}
$$

Same thing can be achieved for the other streaming term:

$$
\begin{align}
\int \mathrm{d}^{3}\vec{p}_{1}\mathrm{d}^{3}\vec{q}_{1}\ln f_{1} \frac{\vec{p}_{1}}{m}\cdot \frac{\partial f_{1}}{\partial\vec{q}_{1}} &  = -\int \mathrm{d}^{3}\vec{p}_{1}\mathrm{d}^{3}\vec{q}_{1}f_{1} \frac{\vec{p}_{1}}{m}\cdot \frac{1}{f_{1}} \frac{\partial f_{1}}{\partial \vec{q}_{1}}  \\
 & = \mathrm{d}^{3}\vec{p}_{1}\mathrm{d}^{3}\vec{q}_{1} f_{1} \frac{\partial}{\partial \vec{q}_{1}} \frac{\vec{p}_{1}}{m} =0
\end{align}
$$

The collision term involves integration over dummy variables $\vec{p}_{1}$and $\vec{p}_{2}$. The labels (1) and (2) can thus be exchanged without any change in the value of the integral.

Averaging the resulting two expression gives:

$$
\begin{align}
\frac{\mathrm{d}H}{\mathrm{d}t}   = -\frac{1}{2} & \int \mathrm{d}^{3}\vec{p}_{1}\mathrm{d}^{3}\vec{q}\mathrm{d}^{3}\vec{p}_{2}\mathrm{d}^{2}\vec{b}  \left| \vec{v}_{1}-\vec{v}_{2} \right| \left[ f_{1}(\vec{p}_{1})f_{1}(\vec{p}_{2})- \right.  \\
 & \left. f_{1}(\vec{p}_{1}')f_{1}(\vec{p}_{2}') \right]\ln (f_{1}(\vec{p}_{1})f_{1}\vec{p}_{2}) 
\end{align}
$$

We would like to change the variable of integration from the coorindates describing the initators of the collision, to those of their products. The explicit functional forms describing this transformation are complicated because of the dependence of the solid angle $\hat{\Omega}$ on $\vec{b}$ and $|\vec{p}_{2}-\vec{p}_{1}|$. 

However, we assured that the Jacobian of the transformation is unity because of time reversal symmetry; since for every collision there is an inverse one obtained by reversing the momenta of the products. 

In terms of the new coordinates:

$$
\begin{align}
\frac{\mathrm{d}H}{\mathrm{d}t} = -\frac{1}{2} & \int \mathrm{d}^{3}\vec{q}\mathrm{d}^{3}\vec{p}_{1}'\mathrm{d}^{3}\vec{p}_{2}'\mathrm{d}^{2}\vec{b} |\vec{v}_{1}-\vec{v}_{2}|  \\
 & \left[ f_{1}(\vec{p}_{1})f_{1}(\vec{p}_{2})- f_{1}(\vec{p}_{1}')f_{1}(\vec{p}_{2}') \right] \ln(f_{1}(\vec{p}_{1})f_{1}(\vec{p}_{2}))
\end{align}
$$

where we should now regard $(\vec{p}_{1},\vec{p}_{2})$ in the above equation as functions of the integration variables $(\vec{p}_{1}',\vec{p}_{2}',\vec{b}')$. As noted earlier, 

$$
|\vec{v}_{1} -\vec{v}_{2}| = |\vec{v}_{1}'-\vec{v}_{2}'|
$$

for any elastic collision, and we can use these quantities interchangeably. Finally, we relable the dummy integration variables such that the primes are removed. Noting that the functional dependence of $(\vec{p}_{1}, \vec{p}_{2}, \vec{b})$ on $(\vec{p}_{1}',\vec{p}_{2}',\vec{b}')$ is exactly the same as its inverse, we obtain:

$$
\begin{align}
\frac{\mathrm{d}H}{\mathrm{d}t} =  & -\frac{1}{2}\int \mathrm{d}^{3}\vec{q}\mathrm{d}^{3}\vec{p}_{1}\mathrm{d}^{3}\vec{p}_{2}\mathrm{d}^{3}\vec{b} |\vec{v}_{1} - \vec{v}_{2}| \\
  &  \left[ f_{1}(\vec{p}_{1}')f_{1}(\vec{p}_{2}') -f_{1}(\vec{p}_{1})f_{1}(\vec{p}_{2}) \right] \ln(f_{1}(\vec{p}_{1}')f_{1}(\vec{p}_{2}')) 
\end{align}
$$

Averaging this and the one earlier results in:

$$
\begin{align}
\frac{\mathrm{d}H}{\mathrm{d}t} = - & \frac{1}{4} \int \mathrm{d}^{3}\vec{q}\mathrm{d}^{3}\vec{p}_{1}\mathrm{d}^{3}\vec{p}_{2}\mathrm{d}^{2}\vec{b}|\vec{v}_{1}-\vec{v}_{2}| \left[ f_{1}(\vec{p}_{1})f_{1}(\vec{p}_{2}) - f_{1}(\vec{p}_{1}')f_{1}(\vec{p}_{2}') \right] \\
  & \left[ \ln(f_{1}(\vec{p}_{1})f_{1}(\vec{p}_{2})) - \ln(f_{1}(\vec{p}_{1}')f_{1}(\vec{p}_{2}')) \right]
\end{align}
$$

Since the integrand is always positive:

$$
\frac{\mathrm{d}H}{\mathrm{d}t} \leq 0.
$$
*Irreversiblity:* The second law is an empirical formulation of the vast number of everyday observations that support the existence of an *arrow of time*. Reconciling the reversiblity laws of physics governing the microscopic domain with the observed irreversiblity of macroscopic phenomena is a fundamental problem. 

Of course, not all microscopic laws of physics are reversible: weak nuclear interactions violate time reversal symmetry, and the collapse of the wave function in the the act of observation is also irreversible. 

The former interactions in fact do not play any significant role in everyday observations that lead to the second law. There are proponents of the view that the reversibility of the currently accepted microscopic equations of motion is indicative of their inadequacy. However, the advent of powerful computers has made it possible *to simulate the evolution of collections of large numbers of particles, governed by classical, reversible equations of motion.* 

The Boltzmann equation is the first formula we have encountered that is clearly not time reversible. We can thus ask the question of how we obtained this result from the Hamiltonian equations of motion.

- [ ] This section needs refinement and continues much more. (Reading from kardar chapter 3 section 5)
