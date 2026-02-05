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

- Under the action of time reversal, $(\mathbf p, \mathbf q, t)\rightarrow (-\mathbf p, \mathbf q, -t)$, the Poisson bracket $\{\rho, \mathcal H\}$ changes sign, The equation we derived implies that the density reverses its evolution. That is: $\rho(\mathbf p, \mathbf q, t)= \rho(-\mathbf p , \mathbf q, -t)$.