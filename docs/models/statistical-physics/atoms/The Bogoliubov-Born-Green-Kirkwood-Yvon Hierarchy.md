---
sticker: lucide//atom
---
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

## Interpretation and Physical Meaning of the BBGKY Hierarchy

The BBGKY hierarchy expresses how reduced descriptions of a many-particle system evolve in time when the underlying dynamics is fully Hamiltonian. Each equation governs the time evolution of an $s$ -particle distribution function $f_s$ , but its structure reveals a fundamental limitation: **no finite-level description is dynamically closed** in the presence of interactions.

---

### 1. Streaming vs. Correlation Dynamics

The left-hand side of the hierarchy,  
$$  
\frac{\partial f_s}{\partial t} - {\mathcal{H}_s, f_s},  
$$ 
represents the evolution of the $s$ -particle distribution under the assumption that the $s$  particles form a closed subsystem. This term describes **free streaming** in reduced phase space — the advection of probability density along trajectories generated by the internal Hamiltonian $\mathcal{H}_s$ .

The right-hand side captures everything that violates this closed-system picture. It accounts for the **influence of the remaining $N - s$  particles** through interaction forces, averaged over their unknown degrees of freedom. This term therefore encodes how unobserved particles induce momentum changes in the observed subsystem.

---

### 2. Hierarchy as Information Flow

Each equation in the hierarchy couples $f_s$  to $f_{s+1}$ . This reflects a structural fact about interacting many-body systems:  
**correlations of order $s$  cannot evolve independently of correlations of order $s+1$ .**

In this sense, the hierarchy describes an _information cascade_ across particle numbers:

- $f_1$  contains one-body statistics,
    
- $f_2$  contains two-body correlations,
    
- $f_3$  contains three-body correlations,
    
- and so on.
    

The BBGKY equations track how higher-order correlation information continuously feeds into lower-order dynamics.

---

### 3. Collision Term as Conditional Force Averaging

The so-called “collision term” on the right-hand side should not be interpreted as literal binary collisions. Instead, it represents a **conditional average force** exerted by untracked particles on tracked ones. The force on particle $n$  depends on the position of particle $s+1$ , and its statistical effect is weighted by the joint distribution $f_{s+1}$ . Thus, the hierarchy encodes how microscopic interaction forces shape macroscopic evolution through correlated statistics.

---

### 4. Exactness and Reversibility

The BBGKY hierarchy is an **exact reformulation** of Liouville’s equation. It introduces no approximations and preserves full time-reversal symmetry. Any irreversibility or dissipation that appears in later kinetic theories arises only after additional assumptions are imposed — particularly assumptions that truncate the hierarchy or discard correlations.

---

### 5. Role in Kinetic Theory

The hierarchy provides the structural framework from which kinetic equations are derived. Practical theories require closing the hierarchy by expressing higher-order distributions in terms of lower-order ones. This closure step introduces approximations about correlation structure, temporal memory, or molecular chaos. The resulting closed equation for $f_1$  forms the starting point for [[Boltzmann Equation]] and its refinements.

---

### 6. Conceptual Summary

The BBGKY hierarchy formalizes the following principle:

> **No finite description of an interacting many-body system is dynamically complete.**  
> Every reduced description leaks information into higher-order correlations.

Rather than providing a closed dynamical law, the hierarchy exposes the exact structure of this leakage and thereby defines the precise boundary between microscopic dynamics and macroscopic kinetic theory.

#hello
