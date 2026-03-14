---
sticker: lucide//newspaper
---
We start by expressing the Faraday tensor and the dual of the Faraday tensor in Maxwell's equations and respectively as:
$$
\begin{align}
F^{\mu\nu} &= n^\mu E^\nu - n^\nu E^\mu - \sqrt{-g}\eta^{\mu\nu\lambda\delta}n_\lambda B_\delta\\
\!^*F^{\mu\nu} &= n^\mu B^\nu -n^\nu B^\mu - \sqrt{-g}\eta^{\mu\nu\lambda\delta}n_\lambda E_\delta
\end{align}
$$
The spatial components (measured by the Eulerian observer) of the electric and magnetic fields are:
$$
\begin{matrix}
E^i := F^{i\nu}n_\nu = \alpha F^{it}, & B^i :=\!^*F^{i\nu}n_\nu = \alpha^*F^{it}
\end{matrix}
$$
Going back to the definition of total current density and recalling that the conduction in terms of what is otherwise referred to as Ohm's law:
$$
J^i = qv^i + \frac W\eta\left[ 
E^i + \frac{1}{\sqrt\gamma}\eta^{ijk}v_j B_k - (v_kE^i)v^i
\right]
$$
where $\eta$ is the resistivity and is the inverse of the scalar term of the conductivity tensor $\eta:=\frac1\sigma$, and $\eta_{ijk}$ is Levi-Civita antisymmetric symbol. Note  that we have ignored the Hall or dynamo terms for simplicity. 

Assume we have the ideal MHD condition:
$$
F^{\mu\nu}u_\nu = 0
$$
we can obtain the explicit and algebraic expression between the electric and magnetic fields:
$$
E^i = \sqrt\gamma\eta^{ijk} B_j v_k
$$
This results, underlies the passive role of dependent quantity for the electric field in the ideal MHD equations. Then using the definition in [[General Relativistic Magnetohydrodynamics]]. We can obtain transformation between magnetic four-vector field in the fluid frame $b^\mu$ and the magnetic four-vector field in the Eulerian frame $B^\mu$.
$$
\begin{matrix}
b^t = \frac w\alpha(B^i v_i),& b^i = \frac1W(B^i+\alpha b^tu^i)
\end{matrix}
$$
Using this we can express the dual Faraday tensor in terms of magnetic four-vector field in the Eulerian frame:
$$
\!^8F^{\mu\nu} = \frac1W(B^\mu u^\nu- B^\nu u^\mu)
$$
and the scalar:
$$
b^2 = \frac{B^2+\alpha^2(b^t)^2}{W^2} = \frac{B^2}{W^2} + (B^iv_i)^2
$$

