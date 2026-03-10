---
sticker: lucide//atom
---
> [!IMPORTANT]
    > Liouville's Theorem states that the phase space density $\rho(\Gamma, t)$ behaves like an incompresible fluid.

![[../../../attachments/Pasted image 20260204163840.png]]

Assume the evolution of $d\mathcal N$ pure states in an infinitesimal volume $\mathrm d \Gamma = \prod_{i=1}^N\mathrm d^3\vec p_i\mathrm d^3\vec q_i$ around the point $(\mathbf p, \mathbf q)$. After an interval $\delta t$ these states have moved to the vicinity of another point $(\mathbf p', \mathbf q')$. Which in terms of components can be written as:

$$
q_\alpha' = q_\alpha + \dot q_{\alpha}\delta t +\mathcal O(\delta t^2)
$$
and 

$$
p_\alpha' = p_\alpha + \dot p_{\alpha}\delta t +\mathcal O(\delta t^2)
$$
As shown in the picture above the original volume element $\mathrm d \Gamma$ is in the shape of a hypercube of sides $\mathrm d p_\alpha, \mathrm dq_\alpha$. In the time interval $\delta t$ it gets distorted, and the projected sides of the new volume element are given by:

$$
\begin{cases}
\mathrm d q_\alpha' = \mathrm d q_\alpha + \frac{\partial \dot q_\alpha}{\partial q_\alpha}\mathrm d q_\alpha \delta t + \mathcal O(\delta t^2)\\
\mathrm d p_\alpha' = \mathrm dp_\alpha + \frac{\partial \dot p_\alpha}{\partial p_\alpha}\mathrm dp_{\alpha}\delta t+\mathcal O(\delta t^2)
\end{cases}
$$
Now our new volume element becomes:

$$
\mathrm dq_\alpha'\cdot \mathrm dp_\alpha' = \mathrm d q_\alpha\cdot\mathrm dp_\alpha \left[
1 + \left(
\frac{\partial \dot q_{\alpha}}{\partial q_\alpha} + \frac{\partial \dot p_\alpha}{\partial p_\alpha}
\right)\delta t + \mathcal O(\delta t^2)
\right]
$$
Now, the time evolution of coordinates and momenta are governed by the canonical equations:

$$
\begin{align}
\dot p_{\alpha} &= -\frac{\partial \mathcal H}{\partial q_\alpha}\\
\dot q_\alpha &= \frac{\partial \mathcal H}{\partial p_\alpha}
\end{align}
$$

Thus we can substitute the middle terms in the brackets with:

$$
\begin{align}
\frac{\partial \dot p_\alpha}{\partial p_\alpha} &= -\frac{\partial^2  \mathcal H}{\partial p_\alpha \partial q_\alpha}\\
\frac{\partial \dot q_\alpha}{\partial q_\alpha} &= \frac{\partial^2 \mathcal H}{\partial q_\alpha \partial p_\alpha}
\end{align}
$$

Noticing these two terms cancel out we find out that the projected area is unchanged for any pair of coordinates, and hence the volume element is unaffected.

$$
\mathrm d \Gamma' = \mathrm d \Gamma
$$

All the pure states $\mathrm d \mathcal N$ originally in the vicinity of $(\mathbf p, \mathbf q)$ are transported to the neighborhood of $(\mathbf p',\mathbf q')$, but occupy exactly the same volume. The ration $\mathrm d \mathcal N / \mathrm d \mathcal \Gamma$ is left unchanged, and $\rho$ behaves like the density of an incompressible fluid. This condition (the incompressibility of the density) can be written in differential form as:

$$
\frac{\mathrm d \rho}{\mathrm d t} = \frac{\partial \rho}{\partial t} + \sum_{\alpha = 1}^{3N}\left(
\frac{\partial \rho}{\partial p_\alpha}\cdot \frac{\mathrm d p_\alpha}{\mathrm d t}+\frac{\partial \rho}{\partial q_\alpha}\cdot \frac{\mathrm dq_\alpha}{\mathrm d t} 
\right)= 0
$$

Again by substituting the canonical equations we get:

$$
\frac{\partial \rho}{\partial t} = \sum_{\alpha= 1}^{3N}\left(
\frac{\partial \rho}{\partial p_\alpha}\cdot \frac{\partial \mathcal H}{\partial q_\alpha} - \frac{\partial \rho}{\partial q_\alpha}\cdot\frac{\partial \mathcal H}{\partial p_\alpha} 
\right) = -\{\rho, \mathcal H\}
$$

# Consequences of Liouville's Theorem:

Under the action of time reversal, $(\mathbf p, \mathbf q, t)\rightarrow (-\mathbf p, \mathbf q, -t)$, the Poisson bracket $\{\rho, \mathcal H\}$ changes sign, The equation we derived implies that the density reverses its evolution. That is: $\rho(\mathbf p, \mathbf q, t)= \rho(-\mathbf p , \mathbf q, -t)$.

---

The time evolution of the ensemble average is given by:
$$
\begin{align}
\frac{\mathrm{d}\left\langle \mathcal{O} \right\rangle}{\mathrm{d}t} &=\int \mathrm{d}\Gamma \frac{\partial \rho(\mathbf{p},\mathbf{q},t)}{\partial t}\mathcal{O}\left( \mathbf{p},\mathbf{q} \right) \\ &= \sum_{\alpha=1}^{3N} \mathrm{d} \Gamma \mathcal{O}(\mathbf{p},\mathbf{q})\left( \frac{\partial \rho}{\partial p_{\alpha}}\cdot \frac{\partial \mathcal{H}}{\partial q_{\alpha}}- \frac{\partial \rho}{\partial q_{\alpha}}\cdot \frac{\partial \mathcal{H}}{\partial p_{\alpha}} \right)  
\end{align}
$$
The partial derivatives of $\rho$ in the above equation can be removed by using the method of integration by parts, that is, $\int f \rho' = -\int \rho f'$ since $\rho$ vanishes on the boundaries of the integrations, leading to:

$$
\begin{align}
\frac{\mathrm{d} \left\langle O \right\rangle}{\mathrm{d}t}&=-\sum_{\alpha=1}^{3N}\int \mathrm{d}\Gamma \rho \left[ \left( 
\frac{\partial \mathcal{O}}{\partial p_{\alpha}}\cdot \frac{\partial \mathcal{H}}{\partial q_{\alpha}} - \frac{\partial \mathcal{O}}{\partial q_{\alpha}}\cdot \frac{\partial \mathcal{H}}{\partial p_{\alpha}}
\right) + \mathcal{O}\left( \frac{\partial^{2}\mathcal{H}}{\partial p_{\alpha}\partial q_{\alpha}}- \frac{\partial^{2}\mathcal{H}}{\partial q_{\alpha}\partial p_{\alpha}} \right)  \right] \\
&= -\int \mathrm{d}\Gamma \rho \{\mathcal{H},\mathcal{O}\}= \left\langle \left\{ \mathcal{O},\mathcal{H} \right\}  \right\rangle
\end{align}
$$
Note that the total time derivative cannot be taken inside the integral sign, that is:
$$
\frac{\mathrm{d}\left\langle \mathcal{O} \right\rangle}{\mathrm{d}t} \neq \int \mathrm{d}\Gamma \frac{\mathrm{d}\rho(\mathbf{p},\mathbf{q},t)}{\mathrm{d}t}\mathcal{O}(\mathbf{p},\mathbf{q})
$$

This common mistake yields $\mathrm{d}\left\langle O \right\rangle / \mathrm{d}t = 0$.

--- 

If the members of the ensemble correspond to an equilibrium macroscopic state, the ensemble averages must be independent of time. This can be achieved by a stationary density $\partial \rho_{\text{eq}} / \partial t=0$, that is by requiring:

$$
\left\{ \rho_{\text{eq}},\mathcal{H} \right\} 
$$
A possible solution to the above equation is for $\rho_{\text{eq}}$ to be a function of $\mathcal{H}$, that is, $\rho_{\text{eq}}(\mathbf{p},\mathbf{q})=\rho(\mathcal{H}(\mathbf{p},\mathbf{q}))$. It is then easy to verify that $\left\{ \rho(\mathcal{H}),\mathcal{H} \right\}=\rho'(\mathcal{H})\left\{ \mathcal{H},\mathcal{H} \right\}=0$. This solution implies that the value of $\rho$ is constant on surfaces of constant energy $\mathcal{H}$, in phase space. *This is indeed the basic assumption of statistical mechanics*.

There may be additional conserved quantities associated with the Hamiltonian that satisfy $\left\{ L_{n},\mathcal{H} \right\}=0$. In the presence of such quantities, a stationary density exists for any function of the form $\rho_{\text{bfp},\mathbf{q}}=\rho(\mathcal{H}(\mathbf{p},\mathbf{q}),L_{1}(\mathbf{p},\mathbf{q}),\dots)$. Clearly the value is not changed during the evolution of the system since:

$$
\begin{align}
\frac{\mathrm{d}L_{n}(\mathbf{q},\mathbf{p})}{\mathrm{d}t}&\equiv \frac{L_{n}(\mathbf{p}(t+\mathrm{d}t),\mathbf{q}(t+\mathrm{d}t))-L_{n}(\mathbf{p}(t),\mathbf{q}(t))}{\mathrm{d}t} \\
 &=\sum_{\alpha=1}^{3N}\left( \frac{\partial L_{n}}{\partial p_{\alpha}}\cdot \frac{\partial p_{\alpha}}{\partial t}+\frac{\partial L_{n}}{\partial q_{\alpha}}\cdot \frac{\partial q_{\alpha}}{\partial t} \right)  \\
 &=-\sum_{\alpha=1}^{3N}\left( \frac{\partial L_{n}}{\partial p_{\alpha}}\cdot \frac{\partial \mathcal{H}}{\partial q_{\alpha}}- \frac{\partial L_{n}}{\partial q_{\alpha}}\cdot \frac{\partial \mathcal{H}}{\partial p_{\alpha}} \right) =\left\{ L_{n},\mathcal{H} \right\}=0 
\end{align}
$$
Hence, the functional dependence of $\rho_{{\text{eq}}}$ on these quantities merely indicates that all accessible states, that is, those that can be connected without violating any conservation law, are equally likely.

---

The above postulate for $\rho_{\text{eq}}$ answers the first question posed at [[Introduction to Kinetic Theory of Gases]], however, in order to answer the second question, and to justify the basic assumption of statistical mechanics, we need to show that non-stationary densities converge into the stationary solution $\rho_{\text{eq}}$.

This contradicts the time reversal symmetry noted in the first point about Liouville's theorem. The best that can be hope for is to show that the solutions $\rho(t)$ are in the neighbourhood of $\rho_{\text{eq}}$ the majority of the time, so that time averages are dominated by the stationary solution. This brings us to [[The Problem of Ergodicity]],