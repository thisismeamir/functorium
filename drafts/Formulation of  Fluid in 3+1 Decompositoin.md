---
sticker: lucide//newspaper
---
*This document should be read after [[3+1 Decomposition]].*

# Considering A Fluid
Assume a fluid with four-velocity $u$, the spatial four-velocity measured by the [[Eulerian Observers]] will be given by the ratio between the projection of $u$ in the space orthogonal to $n$. Or in mathematical terms:
$$
\gamma^i_{\cdot \mu} u^\mu = u^i
$$
to the Lorentz factor of $u$ as measured by $n$:
$$
-n_\mu u^\mu = \alpha u^t
$$
Therefore:
$$
v : = \frac{\gamma\cdot u}{-n\cdot u}
$$
$$
\begin{matrix} v^t = 0, & v^i = \frac{\gamma^i_{\cdot\mu}u^\mu}{\alpha u^t} = \frac{1}{\alpha}\left(\frac{u^i}{u^t} + \beta^i\right)\\
v_t = \beta_i v^i, & v_i  = \frac{\gamma_{i\mu}u^\mu}{\alpha u^t} = \frac{\gamma_{ij}}{\alpha}\left(\frac{u^j}{u^t} + \beta^j \right)
\end{matrix}
$$
Using now the normalization condition: 
$$
u^\mu u_\mu = -1
$$
 and indicating with $W$ the Lorentz Factor, we obtain:
$$
\begin{matrix}
\alpha u^t = -n\cdot u = \frac{1}{\sqrt{1- v^i v_i}} = W, & u_t = W(-\alpha + \beta_i v^i)
\end{matrix}
$$ ^lr99f5
So that the components can be re-written as:
$$
\begin{matrix} v^i = \frac{u^i}{W} + \frac{\beta^i}{\alpha} = \frac1\alpha \left(\frac{u^i}{u^t} + \beta^i\right), & v_i = \frac{u_i}{W} = \frac{u_i}{\alpha u^t}
\end{matrix}
$$
Where in the last equality we have exploited the fact that $\gamma_{ij} u^j = u_i \beta_i W/\alpha$.  And at the end we can express the four-velocity as:
$$
u^\mu = W (n^\mu + v^\mu)
$$
which highlights the split of the four-velocity into a temporal and a spatial part.

The three different unit four-vectors in a 3+1 decomposition of spacetime are shown in figure below, which should be compared with the figure in [[3+1 Decomposition]]. The four-vectors $n,t$ and $u$ represent the unit timelike normal, the time-coordinate basis vector and the fluid four-velocity, respectively. Also shown are the associated worldlines, namely, the normal line representing the worldline of an Eulerian Observer, the coordinate line representing the worldline of a coordinate element, and the fluidline. The figure also reports the spatial projection of $v$ of the fluid four-vector $u$, thus, highlighting that $v$ is the three-velocity as measured by the normal observer.

![[Pasted image 20241024192936.png]]