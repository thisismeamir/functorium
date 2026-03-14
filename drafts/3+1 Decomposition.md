---
sticker: lucide//newspaper
---
# Overview
3+1 decomposition is an alternative view on the equations of general relativity. This view is the basics of numerical relativity and hence it's the most important basis of understanding the algorithms, methods, and simulations that we do.

In this small note we'll investigate and learn it with detailed mathematics. This can be an easy starting point for and undergraduate that has a basic understanding of [[Knowledge Center/Sidenotes/DraftedTheories/General Relativity]].

The normal approaches to general relativity, as a field theory is based on Lagrangian formulation, for some reasons this approach is not necessarily good for numerical relativity. Therefore, a Hamiltonian formulation is preferred. 

The Hamiltonian formulation of general relativity requires a separation of time and space coordinates, known as a $3+1$ decomposition. 

## Introduction
The intrinsically "covariant view" of Einstein's theory of general relativity is based on the concept that all coordinates are equivalent and, hence, the distinction between spatial and time coordinates is more an organizational matter than a strict requirement of the theory. Yet, our experience, and the laws of physics on sufficiently large scales, do suggest that a distinction between the time coordinate and from the spatial ones is the most natural one in describing physical processes.

Furthermore, such a distinction of time and space is the simplest way to exploit a large literature on the numerical solution of hyperbolic partial differential equations as those of relativistic MHD. adopting this principle, we **foliate** spacetime in terms of a set of non-intersecting spacelike hypersurfaces $\Sigma := \Sigma(t)$, each of which is parameterized by a constant value of the coordinate $t$. In this way, the three spatial coordinates are split from the one temporal coordinate and the resulting construction is called the $3+1$ decomposition of spacetime.

## Decomposition
### Construction of Metric and normal vector
Given such constant-time hypersurface, $\Sigma_t$, belonging to the foliation $\Sigma$, we can introduce a timelike four-vector $n$ normal to the hypersurface at each event in spacetime and such that its dual one-form $\Omega := \nabla_t$ is parallel to the gradient of the coordinate $t$.
$$
n_\mu = A \Omega_\mu = \nabla_\mu t
$$
with $n_\mu = \{A,0,0,0\}$ and $A$ a constant to be determined. If we now require that the four-vector $n$ defines an observer and thus that it measures the corresponding four-velocity, then from the normalization condition on timelike four-vectors, $n^\mu n_\mu = -1$.
$$
\begin{align}
n^\mu n_\mu &= g^{\mu\nu} n_\mu n_\nu \\
&= g^{00} A^2 \\
&= -\frac1{\alpha^2}A^2,
\end{align}
$$
where we defined $g^{00} = -\frac{1}{\alpha^2}$. Now that:
$$
\begin{align}
-\frac{1}{\alpha^2}A^2 &= -1\\
A &= \pm\alpha\\
\end{align}
$$
$$
\left\{
\begin{matrix}+ & \text{ Past Direction} \\
- & \text{ Future Direction}
\end{matrix}
\right.
$$
and thus:
$$
A = -\alpha
$$
to showcase the future. Using this normal vector we can define the spatial metric for the hypersurface:
$$
\begin{matrix}
\gamma_{\mu\nu} = g_{\mu\nu} + n_\mu n_\nu , & \gamma^{\mu\nu} = g^{\mu\nu} + n^\mu n^\nu
\end{matrix}
$$
here $\gamma^{0\mu} = 0, \gamma_{ij} = g_{ij}$ but in general  $\gamma^{ij} \not = g^{ij}$. It's important to note that:
$$
\gamma^{ij}\gamma_{jk} = \delta^i_k
$$
Which means that these are the inverse of each other, so that the spacial metric can be used for raising and lowering indices of purely spacial vectors and tensors.

The spatial metric and the hypersurface vector provide us a good toolkit to decompose any tensors into a purely spatial part and a purely timelike part.

1. To obtain the spatial part we contract with the spatial projection operator:
$$
\gamma^{\mu}_{\cdot\nu} := g^{\mu\alpha}\gamma_{\alpha\nu}=g^\mu_{\cdot\nu} + n^\mu n_\nu = \delta^{\mu}_\nu + n^\mu n_\nu
$$
2. To obtain the timelike part we contract with the time projection operator:
$$
N^\mu_{\cdot \nu} := -n^\mu n_\nu
$$
The two projectors are orthogonal:
$$
\gamma^\alpha_{\cdot \nu}N^\mu_{\cdot \nu} = 0
$$
Therefore, a general four-vector can be decomposed as:
$$
U^\mu = \gamma^\mu_{\cdot \nu}U^\nu + N^{\mu}_{\cdot \nu}U^\nu
$$
Note that the spatial part is still a four-vector but now $V^t = 0$ whereas it has the covariant time component, $V_t = g_{\mu t} V^{\mu}$, which is non-zero in general. Analogous considerations can be done about tensors of any rank.

## Construction of time vector
We already know that the unit normal $n$ to a spacelike hypersurface $\Sigma_t$ does not represent the direction along which the time coordinate changes, that is, it is not the direction of the time derivative. Indeed, if we compute the contraction of the two tensors we get a non-unit value:
$$
n^\mu \Omega\mu = \frac1A n^\mu n_\mu = \frac1\alpha \not = 1
$$
Thus we introduce a time-vector, along which to carry out the time evolutions and that is dual to the surface one-form $\Omega$. Such a vector is just the time coordinate basis vector and is defined as the linear superposition of a purely temporal part and of a purely spatial one, namely:
$$
t = e_t =\partial_t := \alpha n +\beta
$$
Here $\beta$ is a purely spatial vector and it's usually referred to as the shift vector and will be another building block of the metric in 3+1 decomposition.

![[Pasted image 20241024181900.png]]

We can check that $t$ is a coordinate basis vector by verifying that:
$$
t^\mu \Omega_\mu = \alpha n^\mu \Omega_\mu + \beta^\mu \Omega_\mu = \frac\alpha\alpha = 1
$$
Using the components of $n$, 
$$
\begin{matrix} n_\mu= (-\alpha, 0,0,0), & n^\mu = \frac1\alpha (1, -\beta),\end{matrix}
$$
we can now express the generic line element in the 3+1 decomposition:
$$
ds^2 = -(\alpha^2 -\beta_i\beta^i)dt^2 + 2\beta_i dx^i dt + \gamma_{ij}dx^i dx^j
$$
This clearly shows that to measure the proper time we just have a $\beta^i = 0$.
$$
d\tau^2 = \alpha^2(t, x^j)dt^2
$$
while the shift vector measures the change of coordinates of a point from one to another hypersurface:
$$
x^i_{t+dt}= x^i_t - \beta^i(t,x^j)dt
$$
This can be related to the metric covariant and contravariant components:
$$
\begin{matrix}
g_{\mu\nu} = \begin{pmatrix}-\alpha^2 + \beta_i \beta^i & \beta_i\\ \beta_i & \gamma_{ij}\end{pmatrix}, & g^{\mu\nu} = \begin{pmatrix}-\frac{1}{\alpha^2} & \frac{\beta^i}{\alpha^2} \\
\frac{\beta^i}{\alpha^2} & \gamma^{ij} - \frac{\beta^i\beta^j}{\alpha^2}
\end{pmatrix}
\end{matrix}
$$
An important identity is then derivable from this:
$$
\sqrt{-g} = \alpha\sqrt{\gamma}
$$
The unit timelike normal $n$ can be associated to the four-velocity of a special class  of observers, which are referred to as normal or [[Eulerian Observers]]
## Mathematical Properties
We start off by decomposing the metric as below:
$$
\begin{align}
g_{00} &= -\alpha^2 + \gamma^{ij}\beta_i\beta_j\\
g_{0i} &= \beta_i\\
g_{ij} &= \gamma_{ij} 
\end{align}
$$
This decomposition of the metric replaces the 10 independent metric components by the **lapse function** $\alpha(x)$, the shift vector $\beta_i(x)$, and the symmetric spatial metric $\gamma_{ij}(x)$. The inverse spacetime metric components are:
$$
\begin{align}
g^{00} &= -\frac{1}{\alpha^2}\\
g^{0i} &= \frac{\beta^i}{\alpha^2}\\
g^{ij} &= \gamma^{ij} - \frac{\beta^i\beta^j}{\alpha^2}
\end{align}$$
The $3+1$ decomposition separates the treatment of time and space coordinates. In place of four dimensional gradients, we use time derivatives and three-dimensional gradients. Thus, as an example:
$$
\nabla_j A^i = \partial_j A ^i + \gamma^i_{jk}A^{k}
$$
where:
$$
\gamma^i_{jk} \equiv \frac12 \gamma^{il} \left(\partial_j\gamma_{kl} + \partial_k \gamma_{jl} + \partial_l \gamma_{jk}\right)
$$

## Intrinsic and Extrinsic Curvature of Hyper-surfaces
In $3+1$ decomposition spacetime is described as a set of three-dimensional hyper-surfaces of constant time. These hyper-surfaces have intrinsic curvature, given by the three dimensional Riemann tensor:
$$
\!^{(3)}R^{i}_{lkm} = \partial_k \gamma^i_{lm} -\partial_m\gamma^i_{kl} +\gamma^i_{kn}\gamma^n_{lm} - \gamma^i_{mn}\gamma^n_{kl}
$$
In addition to the intrinsic curvature, the hyper-surfaces of constant time has an extrinsic curvature $K_{ij}$ arising from its embedding in four-dimensional spacetime.
$$
K_{ij} = \frac1{2\alpha}(\nabla_i\beta_j + \nabla_j \beta_i - \partial_t\gamma_{ij})
$$
The full spacetime (4 dimensional) curvature is then obviously related to the extrinsic and intrinsic curvature of the hyper-surfaces. This relation has been established using the [[Gauss-Codazzi Equations]].
$$
\!^{(4)}R^0_{\cdot jkl} = -\frac1\alpha \left(\nabla_k K_{jl} -\nabla_l K_{jk}\right)
$$
and 
$$
\!^{(4)}R^i_{\cdot jkl} = \!^{(3)}R^i_{\cdot jkl} - \!^{(4)}R^0_{\cdot jkl}\beta^i + K^i_{\cdot k} K_{jl} - K^i_{\cdot l}K_{jk}. 
$$
The other components of the four-dimensional Riemann tensor are:
$$
\!^{(4)}R^0_{\cdot i0j} = -\frac1\alpha \partial_t K_{ij} - K_i^{\cdot k}K_{jk}-\frac1\alpha\nabla_i\nabla_j\alpha\left[\nabla_j\left(\beta^kK_{ik}\right) + K_{jk}\nabla_i\beta^k\right]
$$
and
$$

\!^{(4)}R^k_{\cdot i0j} = 
\!^{(4)}R^k_{\cdot ilj}\beta^l + \left[
\!^{(4)}R^0_{\cdot ilj}\beta^l - 
\!^{(4)}R^0_{\cdot i0j}
\right]\beta^k + \alpha\left[
\nabla^k K_{ij} -\nabla_i K^k_{\cdot j}
\right]
$$
These equations can be combined to give:
$$
\begin{align}
\!^{(4)}R_{ijkl} =\  &\!^{(3)}R_{ijkl} + K_{ik}K_{jl} - K_{jl}K_{jk},\\
\!^{(4)}R_{0jkl} =\ &\!^{(4)}R_{ijkl}\beta^i +\alpha (\nabla_k K_{jl} - \nabla_lK_{jk})= \!^{(4)}R_{kl0j}\\
\!^{(4)}R^{0j}_{\cdot \cdot kl} = \ &\alpha\partial_t K_{ij}+\alpha^2 K_i^{\cdot k}K_{jk} + \alpha\nabla_i\nabla_j \alpha + \\ &\alpha\beta^k\nabla_kK_{ij} - \alpha\nabla_i(\beta^k K_{jk})- \alpha\nabla_j(\beta^kK_{ik})+ \!^{(4)}R_{kilj}\beta^k\beta^l\end{align}
$$
and 
$$
\begin{align}
\!^{(4)}R^{ij}_{kl} &= \!^{(3)}R^{ij}_{kl}+ K^i_{\cdot k} K^j_{\cdot l} - K^{i}_{\cdot l}K^j_{\cdot k} + \frac4\alpha \beta^{[u}\nabla_{[k}K^{j]}_{\cdot l]},\\
\!^{(4)}R^{0j}_{\cdot \cdot kl} &= -\frac1\alpha (\nabla_k K^j_{\cdot l} - \nabla_l K^j_{\cdot k})\\
\!^{(4)}R^{0i}_{0j} &= -\frac 1\alpha\partial_t K^i_{\cdot j} +K^i_{\cdot k} K^k_{\cdot j} - \frac1\alpha \nabla^i\nabla_j \alpha + \frac1\alpha \nabla_j (\beta^k K^i_{\cdot k}) - \frac1\alpha (\nabla_k\beta^i)K^k_{\cdot j}
\end{align}
$$
From these one obtains the four-dimensional Einstein tensor components:
$$
\begin{align}
G^{00} = &-\frac{\mathcal{H}}{2\alpha^2 \sqrt\gamma}\\
G^{0i} = &\frac{\alpha \mathcal{H}^i + \beta^i\mathcal{H}}{2\alpha^2\sqrt \gamma}\\
G^{ij} = &-\frac{\beta^i\beta^j \mathcal{H}}{2\alpha^2 \sqrt \gamma} + \frac{1}{\alpha \sqrt\gamma}\partial_t(\sqrt \gamma P^{ij}) + \!^{(3)}R^{ij} - \frac12 \!^{(3)} R\gamma^{ij}\\
&-\frac1\alpha(\nabla^i\nabla^j - \gamma^{ij}\nabla^2)\alpha + \frac1\alpha \nabla_k ( \beta^i P^{jk} + \beta^j P^{ik} - \beta^k P^{ij})\\
&+2P^{i}_{\cdot k}P^{jk} - PP^{ij} - \frac12\left(P_{kl}P^{kl} - \frac12 P^2\right)\gamma^{ij}\end{align}
$$
where:
$$
\begin{align}
\mathcal{H} &= \sqrt\gamma\left[ 
K_{ij}K^{ij} - K^2 - \!^{(3)}R
\right]\\
\mathcal{H}^i &= 2\sqrt\gamma\nabla_j \left(K^{ij}- K\gamma^{ij}\right) \\
K &= \gamma_{ij}K^{ij}\\
P^{ij} &= K\gamma^{ij} - K^{ij}
\end{align}
$$
Components of the four-dimensional Riemann and Einsteins tensors are raised and lowered using the four-dimensional metric; however, components of all other quantities, including $K_{ij}$ and the three-dimensional Riemann tensor, are raised and lowered using the $\gamma_{ij}$ metric. The four-dimensional Ricci scalar obeys:
$$
\sqrt{-g} \ \!^{(4)}R = \alpha\sqrt\gamma\left[K_{ij}K^{ij} - K^2 + \!^{(3)}R\right] - 2\partial_t (\sqrt\gamma K) + 2\partial_i\left[\sqrt \gamma (K\beta^i - \nabla^i\alpha)\right]
$$


###### Jump to Next [[ADM Formulation]]

---
#introductory #theory 

###### References:
[Hamiltonian Formulation of General Relativity](https://web.mit.edu/edbert/GR/gr11.pdf)
[Gauss Codazzi Equations](https://en.wikipedia.org/wiki/Gauss%E2%80%93Codazzi_equations)

