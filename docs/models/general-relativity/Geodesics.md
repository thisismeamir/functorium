
A geodesic is the curved-space generalization of the notion of a straight line in Euclidean space. A straight line is a path that [[Parallel Transportation|parallel transports]] its own tangent vector. The tangent vector to a path $x^\mu(\lambda)$ is $dx^\mu/d\lambda$. The condition that it be parallel transported is thus:

$$
\frac{\mathrm D}{\mathrm\lambda}\frac{\mathrm d x^\mu}{\mathrm d\lambda} = 0
$$

expanding this is a more common equation for the geodesics:

$$
\frac{\mathrm d^2 x^\mu}{\mathrm d \lambda^2} + \Gamma^\mu_{\rho\sigma} \frac{\mathrm d x^\rho}{\mathrm d\lambda}\frac{\mathrm d x^\sigma}{\mathrm d\lambda} = 0
$$

This is the *geodesic eqaution*. We can easily see that it reproduces the usual notion of straight lines if the connection coefficients are the Christoffel symbols in Euclidean space; in that case we can choose Cartesian coordinates in which $\Gamma^{\mu}_{\rho\sigma} =0$, and the geodesic equation becomes: 

$$
\frac{\mathrm d^2 x^\mu}{\mathrm d \lambda^2} =0
$$

## Deriving by Calculus of Variation

Another way to define straightness is the shortest path between two points. To go on with this definition we must start by having the functional:

$$
\tau = \int \left(-g_{\mu\nu} \frac{\mathrm d x^\mu}{\mathrm d\lambda}\frac{\mathrm d x^\nu}{\mathrm d\lambda}\right)^{1/2}\mathrm d \lambda
$$
If we choose to have $\tau$ extermumed we would start by doing the calculus of variation on the functional:

$$
\delta \tau = \int\delta\sqrt{-f}\mathrm d \lambda
$$
resulting:

$$
= -\int \frac12 (-f)^{-1/2} \delta f\mathrm d \lambda
$$
It makes things easier if we now specify that our parameter time is $\tau$ itself, since this would mean that the tangent vector is the velocity $U^\mu$. This fixes the value of $f$. Thus we have:

$$
\delta \tau = -\frac12 \int \delta f \mathrm d\tau
$$

Therefore we must use variation of:

$$
\delta\left(g_{\mu\nu} \frac{\mathrm d x^\mu}{\mathrm d\tau}\frac{\mathrm d x^\nu}{\mathrm d\tau}\right)
$$

This of course obey the Euler-Lagrange equations but evaluating them involves repeated application of the chain rule, and it is just as simple to directly consider the change in the integral under infinitesimal variations of the path:

$$
\begin{align}
x^\mu &\rightarrow \delta x^\mu \\
g_{\mu\nu} &\rightarrow g_{\mu\nu} + (\partial_\sigma g_{\mu\nu})\delta x^\sigma.
\end{align}
$$

The second line comes from Taylor expansion in curved spacetime, which as you can see, uses the partial derivative, not the covariant derivative. This is because we are simply thinking of the components of $g_{\mu\nu}$ as functions on spacetime in some specific coordinate system. 

[^1]: 
