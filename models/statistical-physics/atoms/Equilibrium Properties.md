---
sticker: lucide//atom
---
# Equilibrium Properties

What is the nature of equilibrium state described by $f_{1}$. for homogeneous gas? 

## Equilibrium Distribution

After the gas has reached equilibrium, the function $H$ should no longer decrease with time. Since the intergrand is always positive, a necessary condition for $\mathrm{d}H / \mathrm{d}t = 0$ is that:

$$
f_{1}(\vec{p}_{1},\vec{q}_{1})f_{1}(\vec{p}_{2},\vec{q}_{1}) - f_{1}(\vec{p}_{1}',\vec{q}_{1})f_{1}(\vec{p}_{2}',\vec{q}_{1}) =0
$$

that is, at each point $\vec{q}$ we must have

$$
\ln f_{1}(\vec{p}_{1},\vec{q}) + \ln f_{1}(\vec{p}_{2},\vec{q}) = \ln f_{1}(\vec{p}_{1}',\vec{q}) + \ln f_{1}(\vec{p}_{2}',\vec{q}).
$$

The left hand side of the above equation refers to the momenta before a two body collision, and the right-hand side to those after the collision. The equality is thus satisfied by any additive quantity that is conserved during the collision.

There are five such conserved quantities for an elastic collision:
1. Particle number
2. the three components of the net momentum
3. and the kinetic energy.

Therefore, one can write a general solution for $f_{1}$ as:

$$
\ln f_{1}= a(\vec{q}) - \vec{\alpha}(\vec{q})\cdot \vec{p} - \beta(\vec{q})\left( \frac{\vec{p}^{2}}{2m} \right) 
$$

We can easily accommodate the potential energy $U(\vec{q})$ in the above form and set:

$$
f_{1}(\vec{p},\vec{q}) = \mathcal{N}(\vec{q})\exp \left[ -\vec{\alpha}(\vec{q})\cdot \vec{p} - \beta(\vec{q})\left(  \frac{\vec{p}^{2}}{2m} + U(\vec{q}) \right)  \right] 
$$

This is the distribution describing ***local equilibrium***. While this form is preserved *during collisions,* it will evolve in time *away from collisions*, due to the streaming terms, unless $\{\mathcal{H}_{1},f_{1}\}=0$. The latter condition is satisfied for any function of $f_{1}$ that depends only on $\mathcal{H}_{1}$, or any other quantity that is conserved by it. Clearly the above density satisfies this requirement as long as $\mathcal{N}$ and $\beta$ are independent of $\vec{q}$, and $\vec{\alpha} =0$

For normalization

$$
\int \mathrm{d}^{3}\vec{p}\mathrm{d}^{3}\vec{q} f_{1}(\vec{p},\vec{q}) =N
$$

For particles in a box of volume $V$, the potential $U(\vec{q})$ is zero inside the box, and infinite on the outside. The normalization factor can be obtained from above as:

$$
N=\mathcal{N}V\left[ 
\int_{-\infty}^{+\infty}\mathrm{d}p \exp \left( -\alpha_{i} p_{i} - \frac{\beta p_{i}^{2}}{2m} \right) 
\right]^{3} =\mathcal{N}V \left( \frac{2\pi m}{\beta} \right)^{3 /2} \exp \left( \frac{m\alpha^{2}}{2\beta} \right)  
$$

Hence, the properly normalized Gaussian distribution for momenta is:

$$
f_{1}(\vec{p},\vec{q}) = n \left( \frac{\beta}{2\pi m} \right)^{3 / 2} \exp \left[ - \frac{\beta(\vec{p}-\vec{p}_{0})^{2}}{2m} \right]. 
$$

where $\vec{p}_{0}= m\vec{\alpha} / \beta$ is the mean value for the momentum of the gas, which is zero for a stationary box, and $n=N /V$ is the particle density. 

From the Gaussian form of the distribution it can be easily concluded that the variance of each component of the momentum is $\langle p_{i}^{2}\rangle = m / \beta$ and

$$
\langle p^{2} \rangle = \langle p_{x}^{2} + p_{y}^{2} + p_{z}^{2} \rangle = \frac{3m}{\beta}  
$$

## Equilibrium Between Two Gases

Consider two different gases (a) and (b), moving in the same potential $U$, and subject to a two-body interaction $\mathcal{V}_{ab}(\vec{q}^{(a)}-\vec{q}^{(b)})$. We can define one-particle densities, $f_{1}^{(a)}$ and $f_{2}^{(b)}$, for the two gases, respectively. 

In terms of a generalized collision integral 

$$
\begin{align}
C_{\alpha,\beta} = - &  \int \mathrm{d}^{3}\vec{p}_{2} \mathrm{d}^{2}\Omega \left| \frac{\mathrm{d}\sigma_{\alpha,\beta}}{\mathrm{d}\Omega} \right| \left| \vec{v}_{1}-\vec{v}_{2} \right| \left[ f_{1}^{(\alpha)}(\vec{p},\vec{q})f_{1}^{(\beta)}(\vec{p}_{2},\vec{q}_{1}) \right. \\
 & \left. -f_{1}^{(\alpha)}(\vec{p}_{1}',\vec{q}_{1})f_{1}^{(\beta)}(\vec{p}_{2}',\vec{q}_{1})\right],
\end{align}
$$

the evolution of these densities is governed by a simple generalization of the Boltzmann equation to:

$$
\begin{cases}
\frac{\partial f_{1}^{(a)}}{\partial t} = - \left\{ f_{1}^{(a)}, \mathcal{H}_{1}^{(a)} \right\} + C_{a,a} + C_{a,b} \\
\frac{\partial f_{1}^{(b)}}{\partial t} =-\left\{ f_{1}^{(b)},\mathcal{H}_{1}^{(b)} \right\} +C_{b,a} + C_{b,b} 
\end{cases}
$$

Stationary distributions can be obtained if all six terms on the right-hand side of these equations are zero. In the absence of interspecies collisions, that is when:

$$
C_{a,b}=C_{b,a} = 0
$$

we can obtain independent stationary distributions:

$$
\begin{cases}
f_{1}^{(a)} \propto \exp \left( -\beta_{a}\mathcal{H}_{1}^{(a)} \right) \\
f_{1}^{(b)} \propto \exp \left( -\beta_{b}\mathcal{H}_{1}^{(b)} \right) 
\end{cases}
$$

Requiring the vanishing of $C_{a,b}$ leads to the additional constraint:

$$
\begin{align}
f_{1}^{(a)}(\vec{p}_{1})f_{1}^{(b)}(\vec{p}_{2}) - f_{1}^{(a)}(\vec{p}_{1}')f_{1}^{(b)}(\vec{p}_{2}')=0, \implies  & \\
\beta_{a}\mathcal{H}_{1}^{(a)}(\vec{p}_{1})+\beta_{b}\mathcal{H}_{1}^{(b)}(\vec{p}_{2}) = \beta_{a} \mathcal{H}_{1}^{(a)}(\vec{p}_{1}') +\beta_{b}\mathcal{H}_{1}^{(b)}(\vec{p}_{2}') & 
\end{align}
$$

Since the total energy is conserved in a collision, the above equation can be satisfied for $\beta_{a}=\beta_{b} =\beta$. This condition implies the equality of the kinetic energies of the two species,

$$
\left\langle  \frac{p_{a}^{2}}{2m_{a}}  \right\rangle = \left\langle  \frac{p_{b}^{2}}{2m_{b}} = \frac{3}{2\beta}  \right\rangle 
$$
The parameter $\beta$ thus plays the role of an *empirical temperature* describing the equilibrium of gases.

## The Equation of State

To complete the identification of $\beta$ with temperature $T$, consider a gas of $N$ particles confined to a box of volume $V$. The gas pressure results from the force exerted by the particles colliding with the walls of the container. Consider a wall element of area $A$ perpendicular to the $x$ direction. The number of particles impacting this area, with momentum in the interval $[\vec{p},\vec{p}+\mathrm{d}\vec{p}]$, over a time period $\delta t$ is:

$$
\mathrm{d}\mathcal{N}(\vec{p}) - (f_{1}(\vec{p})\mathrm{d}^{3}\vec{p})(Av_{x}\delta t).
$$

The final factor in the above expression is the volume of a cylinder of height $v_{x}\delta t$ perpendicular to the area element $A$. Only particles within this cylinder are close enough to impact the wall during $\delta t$. 

As each collision imparts a momentum $2p_{x}$ to the wall, the force exerted is:

$$
F = \frac{1}{\delta t}\int _{-\infty}^{0}\mathrm{d}p_{x} \int _{-\infty}^{\infty} \mathrm{d}p_{y} \int _{-\infty}^{\infty}\mathrm{d}p_{z}f_{1}(\vec{p}) \left( A \frac{p_{x}}{m}\delta t \right) (2p_{x}).
$$

Using this one can define pressure as:

$$
P = \frac{f}{A} = \int \mathrm{d}^{3}\vec{p} f_{1}(\vec{p}) \frac{p_{x}^{2}}{m}= \frac{1}{m} \int \mathrm{d}^{3}\vec{p} p_{x}^{2}n\left( \frac{\beta}{2\pi m} \right)^{3 / 2} \exp \left( - \frac{\beta p^{2}}{2m} \right) = \frac{n}{\beta}
$$

Using the $f_{1}$ in equilibrium. Comparing with the standard equation of state $PV = Nk_{B}T$, for an ideal gas, lead to the identification, $\beta = 1 / k_{B}T$.

## Entropy

The Boltzmann H-function is closely related to the information content of the one-particle PDF $\rho_{1}$. We can also define a corresponding Boltzmann entropy,

$$
S_{B}(t) = -k_{B}H(t)
$$

where the constant $k_{B}$ reflects the historical origins of entropy. The H-theorem implies that $S_{B}$ can only increase with time in approaching equilibrium.  It has the further advantage of being defined through the definition of $H$ function in [[The H-Theorem and Irreversibility]], for situations that are clearly out of equilibrium. For a gas in equilibrium in a box of volume $V$,  from the definition of $f_1$, we compute:

$$
\begin{align}
H &  = V \int \mathrm{d}^{3}\vec{p}f_{1}(\vec{p})\ln f_{1}(\vec{p}) \\
 & = V\int \mathrm{d}^{3}\vec{p} \frac{N}{V}(2\pi m k_{B}T)^{-3 / 2} \exp \left( - \frac{p ^{2}}{2mk_{B}T} \right)\left[ \ln \left( \frac{n}{(2\pi mk_{B}T)^{3 / 2}} \right) - \frac{p^2}{2mk_{B}T} \right]  \\
 & =N\left[ \ln \left( \frac{n}{(2\pi mk_{B}T)^{3/ 2}} \right) -\frac{3}{2}  \right] 
\end{align}
$$

The entropy is now identified as:

$$
S_{B}= - k_{B}H= Nk_{B}\left[ \frac{3}{2}+\frac{3}{2}\ln(2\pi mk_{B}T) - \ln \left( \frac{N}{V} \right)  \right].
$$

The thermodynamic relation, $T\mathrm{d}S_B = \mathrm{d}E + P\mathrm{d}V$ implies:

$$
\begin{align}
\left. \frac{\partial E}{\partial T} \right\vert_{V} = T \left. \frac{\partial S_{B}}{\partial T} \right\vert_{V} = \frac{3}{2}Nk_{B}, &  \\
P+ \left. \frac{\partial E}{\partial V} \right\vert_{T} = T \left. \frac{\partial S_{B}}{\partial V} \right\vert_{T} = \frac{Nk_{B}T}{V}
\end{align}
$$

The usual properties of monatomic ideal gas, $PV=Nk_{B}T$, and $E=3Nk_{B}T/2$, can now be obtained from the above equations. Also note that for this classical gas, the zero temperature limit of the entropy is not independent of the density $n$, in violation of the third law of thermodynamics.