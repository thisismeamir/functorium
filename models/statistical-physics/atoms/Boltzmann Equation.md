---
sticker: lucide//atom
---
As we've derived [[The Bogoliubov-Born-Green-Kirkwood-Yvon Hierarchy]], to estimate the relative importance of the different terms appearing in it let us examine the first two equations in the hierarchy,

$$
\left[ \frac{\partial}{\partial t}- \frac{\partial U}{\partial \vec{q}_{1}}\cdot \frac{\partial}{\partial \vec{p}_{1}}+ \frac{\vec{p}_{1}}{m}\cdot \frac{\partial}{\partial \vec{q}_{1}} \right]f_{1} = \int \mathrm{d}V_{2} \frac{\partial \mathcal{V}(\vec{q}_{1}-\vec{q}_{2})}{\partial \vec{q}_{1}}\cdot \frac{\partial f_{2}}{\partial \vec{p}_{1}} 
$$
and

$$
\begin{align}

\left[ \frac{\partial}{\partial t}- \frac{\partial U}{\partial \vec{q}_{1}}\cdot \frac{\partial}{\partial \vec{p}_{1}}- \frac{\partial U}{\partial \vec{q}_{2}}\cdot \frac{\partial}{\partial \vec{p}_{2}}+ \frac{\vec{p}_{1}}{m}\cdot \frac{\partial}{\partial \vec{q}_{1}} + \frac{\vec{p}_{2}}{m}\cdot \frac{\partial}{\partial \vec{q}_{2}} - \frac{\partial \mathcal{V}(\vec{q}_{1}-\vec{q}_{2})}{\partial \vec{q}_{1}}\cdot \left[  \frac{\partial}{\partial \vec{p}_{1}}-\frac{\partial}{\partial \vec{p}_{2}} \right]  \right]f_{2}  \\
= \int \mathrm{d}V_{3}\left[ \frac{\partial \mathcal{V}(\vec{q}_{1}-\vec{q}_{3})}{\partial \vec{q}_{1}} \cdot \frac{\partial}{\partial \vec{p}_{1}}+ \frac{\partial \mathcal{V}(\vec{q}_{2}-\vec{q}_{3})}{\partial \vec{q}_{2}}\cdot \frac{\partial}{\partial \vec{p}_{2}} \right] f_{3} 
\end{align}
$$

Note that two of the streaming terms in this equation $\partial \mathcal{V}(\vec{q}_{1}-\vec{q}_{2})/\partial \vec{q}_{1}$ and $\partial \mathcal{V}(\vec{q}_{2}-\vec{q}_{1})/\partial \vec{q}_{2}$ are combined since:

$$
\frac{\partial \mathcal{V}(\vec{q}_{1}-\vec{q}_{2})}{\partial \vec{q}_{1}} = -\frac{\partial \mathcal{V}(\vec{q}_{1}-\vec{q}_{2})}{\partial \vec{q}_{2}}
$$
*Time scales:* all terms within square bracket in the above equations have dimensions of inverse time, and we estimate their relative magnitudes by dimensional analysis, using typical velocities and length scales. 

For terms involving the external potential $U$, or the interatomic potential $\mathcal V$, an appropriate length scale can be extracted from the range of variations of the potential.

The terms proportional to:

$$
\frac{1}{\tau_{U}} \sim \frac{\partial U}{\partial \vec{q}}\cdot \frac{\partial}{\partial \vec{p}}
$$
involve spatial variations of the external potential $U(\vec{q})$, which take place over macroscopic distances $L$. We shall refer to the associated time $\tau_{U}$ as an extrinsic time scale, as it can be made arbitrarily long by increasing system size. 

From the terms involving the interatomic potential $\mathcal{V}$, we can extract two additional time scales, which are intrinsic to the gas under study. In particular, the *collision duration*

$$
\frac{1}{\tau_{c}}\sim \frac{\partial \mathcal{V}}{\partial \vec{q}}\cdot \frac{\partial}{\partial \vec{p}}
$$
is the typical time over which two particles are within the effective range $d$ of their interaction. 


There are also collision terms on the right-hand side of the equations, which depend on $f_{s+1}$ and lead to an inverse time scale:

$$
\frac{1}{\tau_{\times}}\sim \int \mathrm{d}V \frac{\partial \mathcal{V}}{\partial \vec{q}}\cdot \frac{\partial}{\partial \vec{p}} \frac{f_{s+1}}{f_{s}}\sim \int \mathrm{d}V \frac{\partial \mathcal{V}}{\partial \vec{q}}\cdot \frac{\partial}{\partial \vec{p}} N \frac{\rho_{s+1}}{\rho_{s}}
$$

The integrals are only non-zero over the volume of the interparticle potential $d^{3}$. The term $f_{s+1}/f_s$ is related to the probability of finding another particle per unit volume, which is roughly the particle density. We thus obtain the *mean free time*:

$$
\tau_{\times} \approx \frac{\tau_{c}}{n d^{3}}\approx \frac{1}{nvd^{2}}
$$
which is the typical distance a particle travels between collisions. For short-range interactions, $\tau_{\times}\approx 10^{-8}$ is much longer than $\tau_{c}$, and the collision terms on the right-hand side are smaller by a factor of $nd^3\approx 10^{-4}$.


![[../../../attachments/Pasted image 20260206165337.png]]

>The mean free time between collisions is estimated by requiring that there is only one other particle in the volume swept in time $\tau_{\times}$.

# Boltzmann Equation

The Boltzmann equation is obtained for short-range interactions in the dilute regime by exploiting $\tau_{c}/\tau_{\times}\approx nd^{3} \ll 1$. It is obvious that the first equation is different than others, because it lacks the collision terms on the left-hand side. For all other equations, the right-hand side is smaller by a factor of $nd^{3}$, while the first it may indeed dominate the left-hand side. Thus a possible approximation scheme is to truncate the equations after the first two, by setting the right-hand side of the second equation to zero.

This implies that the two-body density evolves as in an isolated two-particle system. The relatively simple mechanical processes that govern this evolution result in streaming terms for $f_{2}$ that are proportional to both $\tau_{U}^-1$ and $\tau_{c}^{-1}$. 

The two sets of terms can be more or less treated independently: the former describe the evolution of the center of mass of the two particles, while the latter govern the dependence on relative coordinates.

The density $f_{2}$ is proportional to the joint PDF $\rho_{2}$ for finding one particle at $(\vec{p}_{1},\vec{q}_{1})$ and another at $(\vec{q}_{2},\vec{p}_{2})$, at the same time $t$. It is reasonable to expect that at distances much larger than the range of the potential $\mathcal{V}$, the particles are independent, meaning:

$$
\begin{cases}
\rho_{2}(\vec{p}_{1},\vec{p}_{2},\vec{q}_{1},\vec{q}_{2}) \to \rho_{1}(\vec{p}_{1},\vec{q}_{1})\rho_{1}(\vec{p}_{2},\vec{q}_{2}), & \text{or} \\
f_{2}(\vec{p}_{1},\vec{p}_{2},\vec{q}_{1},\vec{q}_{2}) \to f_{1}(\vec{p}_{1},\vec{q}_{1})f_{1}(\vec{p}_{2},\vec{q}_{2}), & \text{for } |\vec{q}_{1}-\vec{q}_{2}| \gg d
\end{cases}
$$

This statement should be true even for situations out of equilibrium. For the collision term on the right-hand side, we actually need the precise dependence of $f_{2}$ on the relative coordinates and momenta at separations to $d$. *At time intervals longer than $\tau_{c}$, the "steady state" behavior of $f_{2}$ at small relative distances is obtained by equating the largest streaming terms in the second BBGKY equation, that is:*

$$
\left[ \frac{\vec{p}_{1}}{m}\cdot \frac{\partial}{\partial \vec{q}_{1}} + \frac{\vec{p}_{2}}{m}\cdot \frac{\partial}{\partial \vec{q}_{2}} - \frac{\partial \mathcal{V}(\vec{q}_{1}-\vec{q}_{2})}{\partial \vec{q}_{1}}\cdot \left( \frac{\partial}{\partial \vec{p}_{1}}- \frac{\partial}{\partial \vec{p}_{2}} \right)  \right] f_{2} =0
$$

We expect $f_{2}(\vec{q}_{1},\vec{q}_{2})$ to 
- have slow variations over the center of mass coordinate $\vec{Q}=(\vec{q}_{1}+\vec{q}_{2})/2$, 
- and large variations over the relative coordinate $\vec{q}=\vec{q}_{2}-\vec{q}_{1}$. 
Therefore, $\partial f_{2} / \partial \vec{q} \gg \partial f_{2} / \partial \vec{Q}$, and $\partial f_{2} /\vec{q}_{2} \approx -\partial f_{2} / \partial \vec{q}_{1} \approx \partial f_{2} / \partial \vec{q}$, leading to:

$$
\frac{\partial \mathcal{V}(\vec{q}_{1}-\vec{q}_{2})}{\partial \vec{q}_{1}}\cdot \left( \frac{\partial}{\partial \vec{p}_{1}}- \frac{\partial}{\partial \vec{p}_{2}} \right) f_{2} = -\left(  \frac{\vec{p}_{1}-\vec{p}_{2}}{m} \right)\cdot \frac{\partial}{\partial \vec{q}}f_{2} 
$$

The above equation provides a precise mathematical expression for how $f_{2}$ is constrained along the trajectories that describe the collision of the two particles. The collision term on the right-hand side of the first BBGKY equation can now be written as:

$$
\begin{align}
\left.\frac{\mathrm{d}f_{1}}{\mathrm{d}t}\right|_{\text{coll.}} = & \int \mathrm{d}^3\vec{p}_{2}\mathrm{d}^3\vec{q}_{2} \frac{\partial \mathcal{V}(\vec{q}_{1}-\vec{q}_{2})}{\partial \vec{q}_{1}}\cdot \left( \frac{\partial}{\partial \vec{p}_{1}}- \frac{\partial}{\partial \vec{p}_{2}} \right) f_{2} \\
 & \approx \int \mathrm{d}^3\vec{p}_{2} \mathrm{d}^3\vec{q} \left( \frac{\vec{p}_{2}-\vec{p}_{1}}{m} \right) \cdot \frac{\partial}{\partial \vec{q}}f_{2}(\vec{p}_{1},\vec{q}_{1},\vec{p}_{2},\vec{q}_{2};t)
\end{align}
$$
