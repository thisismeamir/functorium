---
sticker: lucide//newspaper
---
Given the importance of [[Conservative Formulations of GRMHD equations for numerical simulations]] to obtain a well-posed system of equations , more than 30 years ago the group of Valencia started to develop Eulerian 3+1 formulations of the relativistic hydrodynamic and MHD equations written in conservative forms. Because of this these formulations are often referred to as the *Valencia formulations*.

 1. The first step taken in this direction was casting the special-relativistic hydrodynamics equations into a conservative formulation.
 2. After that the same thing was done with the equations of [[General Relativistic Magnetohydrodynamics]].
 3. Finally, the equations of GRMHD were cast in [[Eulerian Conservative Formulation]]. 

## Continuity equation in 3+1 conserved generic (curved) spacetime. 

Starting from the continuity equation:
$$
\nabla_\mu \rho u^\mu = 0
$$
we can write:
$$
\nabla_\mu \rho u^\mu 
= \frac{1}{\sqrt{-g}}\partial_\mu (\sqrt{-g}\rho u^\mu)
= \frac{1}{\sqrt{-g}}\left[\partial_t (\sqrt{-g}\rho u^t) + \partial_i (\sqrt{-g}\rho u^i)\right] =0 
$$
Which, after introducing the conserved rest-mass density in the Eulerian frame, 
$$
D := \rho u^\mu n_\mu = \rho\alpha u^t = \rho W
$$
can be written in the conservative form:
$$
\partial_t(\sqrt{\gamma} D) + \partial_i \left[
\sqrt\gamma D(\alpha v^i -\beta^i)
\right] =0
$$
We can also define the transport velocity:
$$
\mathcal{V} = \alpha v^i - \beta^i
$$
and thus
$$
\boxed{\partial_t(\sqrt{\gamma} D) + \partial_i \left[
\sqrt\gamma D\mathcal V^i
\right] =0 }
$$
This equation represents the 3+1 conservative form of the continuity equation in a generic (curved) spacetime.

## 3+1 conservative form of energy-momentum equations
It is useful to write the energy-momentum tensor in terms of quantities measured by the Eulerian observer; before writing the 3+1 conservative form of the energy-momentum equations. For this we can define the conserved total energy density $\mathcal U$ as the full projection of the energy-momentum tensor $T^{\mu\nu}$ along the unit normal $n$ to the spatial hypersurface $\Sigma_t$. 
$$
\begin{align}
\mathcal U &:= n_\mu n_\nu  T^{\mu\nu}\\
&= \rho h W^2 - p \frac12 \left[
B^2(1+v^2)-(B^j v_j)^2
\right]
\end{align}
$$
Similarly, the three-momentum density measured by the Eulerian observer is defined as the mixed parallel-transverse component of the energy-momentum tensor.
$$
\begin{align}
\mathcal S_i &:= \gamma^\mu_{\cdot i} n^\nu T_{\mu\nu}\\
&=\rho h W^2 v_i + B^2 v_i - (B^j v_j)B_i
\end{align}
$$
while the purely spatial part of the energy-momentum tensor is given by:
$$
\begin{align}
W^{ij} &:= \gamma^i_{\cdot \mu}\gamma^j_{\cdot \nu}T^{\mu\nu}\\
& = S^i v^j + p_{\text{tot}}\gamma^{ij} - \frac{B^i B^j}{W^2} - (B^kv_k)v^iB^j
\end{align}
$$
The corresponding four-dimensional definitions are given respectively by:
$$
\begin{matrix}
W^{\alpha\beta} := \gamma^\alpha_{\cdot\mu}\gamma^\beta_{\cdot\nu}T^{\mu\nu}, & \text{and} & S_\alpha := \gamma^{\mu}_{\cdot \alpha}n^\nu T_{\nu\mu}
\end{matrix}
$$
and allow us to rewrite the energy-momentum tensor in its generic 3+1 decomposition.