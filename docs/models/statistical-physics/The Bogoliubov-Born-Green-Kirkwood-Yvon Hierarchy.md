The full phase space density contains much more information than necessary for description of equilibrium properties. For example, knowledge of the one-particle distribution is sufficient for computing the pressure of a gas. A one-particle density refers to the expectation value of finding any of the $N$ particles at location $\vec{q}$, with momentum $\vec{p}$, at time $t$, which is computed from the full density as:

$$
\begin{align}
f_{1}  (\vec{p},\vec{q},t) &=\left\langle \sum_{i=1}^{N} \delta^3(\vec{p}-\vec{p}_{i})\delta^3(\vec{q}-\vec{q}_{i})  \right\rangle \\
 & =N\int \prod_{i=2}^N \mathrm{d^3\vec{p}_{i}}\mathrm{d^3 \vec{q}_{i}}\rho(\vec{p}_{1}=\vec{p}, \vec{q}_{1}=\vec{q},\vec{p}_{2},\vec{q}_{2},\dots)
\end{align}
$$

To obtain the second identity above, we used the first pair of delta functions to perform one set of integrals, and then assumed that the density is symmetric with respect to permuting the particles. We can extend this to obtain the $s$-particle density:

$$
f_{s}(\vec{p}_{i}, \dots,\vec{q}_{s},t) = \frac{N!}{(N-s)!}\int \prod_{i=s+1}^N\mathrm{d}V_{i}\rho(\mathbf{p},\mathbf{q},t) = \frac{N!}{(N-s)!}\rho_{s}(\vec{p_{1}},\dots,\vec{q}_{s},t)
$$
where $\rho_{s}$ is a standard unconditional PDF for the coordinates of $s$ particles, and $\rho_{N}\equiv \rho$. While $\rho_{s}$ is properly normalized to unity when integrated over all its variables, the $s$-particle density has a normalization of $N!/(N-s)!$. We shall use the two quantities interchangeably.

For evaluating the time evolution of $f_s$, it is convenient to divide the Hamiltonian into:

$$
\mathcal{H} = \mathcal{H}_{s}+\mathcal{H}_{N+s}+\mathcal{H}'
$$

Were the first two include only interactions among each group of particles:

$$
\begin{align}
\mathcal{H}_{s} & =\sum_{n=1}^s \left[ \frac{\vec{p}_{n}^2}{2m}+U(\vec{q}_{n}) \right] + \frac{1}{2}\sum_{(n,m)=1}^s\mathcal{V}(\vec{q}_{n}-\vec{q}_{m}) \\
\mathcal{H}_{N-s}  & = \sum_{i=s+1}^N\left[ \frac{\vec{p}_{i}^2}{2m}+U(\vec{q}_{i}) \right] + \frac{1}{2} \sum_{(i,j)=s+1}^N \mathcal{V}(\vec{q}_{i}-\vec{q}_{j})  
\end{align}
$$

while the interparticle interactions are contained in:

$$
\mathcal{H}' = \sum_{n=1}^s\sum_{i=s+1}^N\mathcal{V}(\vec{q}_{n}-\vec{q}_{i}).
$$

The time evolution of $f_s$ (or $\rho_s$) is obtained as:

$$
\frac{\partial \rho_{s}}{\partial t} = \int \prod_{i=s+1}^N \mathrm{d}V_{i} \frac{\partial \rho}{\partial t} =-\int \prod_{i=s+1}^N \mathrm{d}V_{i} \left\{ 
\rho, \mathcal{H}_{s} +\mathcal{H}_{N-s} + \mathcal{H}'
\right\} 
$$

These terms are not being integrated over the first $s$ terms, therefore for them we have:

$$
\int \prod_{i=s+1}^N \mathrm{d}V_{i} \left\{ \rho, \mathcal{H}_{s} \right\} = \left\{ \left( \int \prod_{i=s+1}^N\mathrm{d}V_{i}\rho \right) , \mathcal{H}_{s} \right\}  = \left\{ \rho_{s}, \mathcal{H}_{s} \right\} 
$$

For the second term we explicitly write the Poisson brackets:

$$
-\int \prod_{i=s+1}^N \mathrm{d}V_{i}\left\{ \rho, \mathcal{H}_{N-s} \right\} =\int \prod_{i=s+1}^N \mathrm{d}V_{i}\sum_{j=1}^N\left[ \frac{\partial \rho}{\partial \vec{p}_{j}}\cdot \frac{\partial \mathcal{H}_{N-s}}{\partial \vec{q}_{j}}- \frac{\partial \rho}{\partial \vec{q}_{j}}\cdot \frac{\partial \mathcal{H}_{N-s}}{\partial \vec{p}_{j}} \right]
$$

Now using the definition of $\mathcal{H}_{N-s}$:

$$
=\int \prod_{i=s+1}^N\mathrm{d}V_{i} \sum_{j=s+1}^N\left[ \frac{\partial \rho}{\partial \vec{p}_{j}}\cdot \left( \frac{\partial U}{\partial \vec{q}_{j}} + \frac{1}{2} \sum_{k=s+1}^N \frac{\partial \mathcal{V}(\vec{q}_{j}-\vec{q}_{k})}{\partial \vec{q}_{j}} \right) -\frac{\partial \rho}{\partial \vec{q}_{j}}\cdot \frac{\vec{p}_{j}}{m} \right]=0 
$$

The last equality is obtained after performing the integration by part: the term multiplying $\partial\rho/\partial\vec{p}_{j}$ has no dependence on $\vec{p}_{j}$. And the third term of the Hamiltonian:

$$
\int \prod_{i=s+1}^N \mathrm{d}V_{i}\sum_{j=1}^N\left[ \frac{\partial \rho}{\partial \vec{p}_{j}}\cdot \frac{\partial \mathcal{H}'}{\partial \vec{q}_{j}}- \frac{\partial \rho}{\partial \vec{q}_{j}}\cdot \frac{\partial \mathcal{H}'}{\partial \vec{p}_{j}} \right] 
$$
substituting the definition we get:

$$
=\int \prod_{i=s+1}^N \mathrm{d}V_{i}\left[ \sum_{n=1}^s \frac{\partial \rho}{\partial \vec{p}_{n}}\cdot \sum_{j=s+1}^N \frac{\partial \mathcal{V}(\vec{q}_{n}-\vec{q}_{j})}{\partial \vec{q}_{n}} + \sum_{j=s+1}^N \frac{\partial \rho }{\partial \vec{p}_{j}}\cdot \sum_{n=1}^s \frac{\partial \mathcal{V}(\vec{q}_{j}-\vec{q}_{n})}{\partial \vec{q}_{j}} \right] 
$$
where the sum over all particles has been subdivided into two groups. Integration by parts shows that the second term in the above expression is zero. The first term involves the sum of $(N-s)$ expressions that are equal by symmetry and simplifies to:

$$
\begin{align}
(N-s) & \int \prod_{i=s+1}^N \mathrm{d}V_{i} \sum_{n=1}^s \frac{\partial \mathcal{V}(\vec{q}_{n}-\vec{q}_{s+1})}{\partial \vec{q}_{n}}\cdot \frac{\partial \rho}{\partial \vec{p}_{n}}  \\
 & =(N-s)\sum_{n=1}^s \int \mathrm{d}V_{s+1} \frac{\partial \mathcal{V}(\vec{q}_{n}-\vec{q}_{s+1})}{\partial \vec{q}_{n}}\cdot \frac{\partial}{\partial \vec{p}_{n}}\left[ \int \prod_{i=s+2}^N \mathrm{d}V_{i}\rho \right] 
\end{align}
$$

Note that the quantity in the square bracket is $\rho_{s+1}$.

Putting all of these together we have:

$$
\frac{\partial \rho_{s}}{\partial t}- \left\{ \mathcal{H}_{s}, \rho_{s} \right\}= (N-s)\sum_{n=1}^s \int \mathrm{d}V_{s+1} \frac{\partial \mathcal{V}(\vec{q}_{n}-\vec{q}_{s+1})}{\partial \vec{q}_{n}}\cdot \frac{\partial \rho_{s+1}}{\partial \vec{p}_{n}}
$$

or in terms of the densities $f_s$,

$$
\frac{\partial f_{s}}{\partial t} - \left\{ \mathcal{H}_{s}, f_{s} \right\} =\sum_{n=1}^s \int \mathrm{d}V_{s+1} \frac{\partial \mathcal{V}(\vec{q}_{n}-\vec{q}_{s+1})}{\partial \vec{q}_{n}}\cdot \frac{\partial f_{s+1}}{\partial \vec{p}_{n}}
$$
In the absence of interactions with other particles, the density $\rho_s$ for a group of $s$ particles evolves as the density of an incompressible fluid, and is described by the streaming terms on the left hand side. However, because of interactions with the remaining $N-s$ particles, the flow is modified by the collision terms on the right-hand side. The collision integral is the sum of terms corresponding to a potential collision of any of the particles in the group of $s$, with any remaining $N-s$ particles.

To describe the probability of finding the additional particle that collides with a member of this group, the result must depend on the joint PDF of $s+1$ particles described by $\rho_{s+1}$. This result in hierarchy of equations in which $\partial \rho_1 / \partial t$ depends on $\rho_2, \partial \rho_2 /\partial t$ depends on $\rho_3$, etc, which is at least as complicated ass the original equation for the full phase space density.