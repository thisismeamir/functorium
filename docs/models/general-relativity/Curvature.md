# Informally

Curvature informally can be thought of as deviation from flatness. But what is flatness, and is anything crooked, curved is to be answered here. Clearly curvature depends somehow on the metric, which defines the geometry of our manifold; but it is not immediately clear how we should attribute curvature to any given metric.

All the ways in which curvature manifests itself rely on something called a "*connection*", which gives us a way of relating vectors in the tangent spaces of nearby points. There's a unique connection that we can construct from the metric that is known as [[Christoffel Symbol]].

$$
\Gamma^\alpha_{\mu\nu} = \frac{1}{2}g^{\alpha\sigma}\left(
\partial_\mu g_{\nu\sigma} + \partial_{\nu} g_{\sigma\mu} - \partial_{\sigma} g_{\mu\nu}
\right)
$$

It should be noted that this is **Not** a tensor. That's why we've called it a symbol. The fundamental use of a connection is to take a *covariant derivative* $\nabla_\mu$ which is a generalization of the partial derivative. The covariant derivative of a vector field $V^\mu$ is given by:

$$
\nabla_{\mu} V^\nu = \partial_{\mu} V^\nu + \Gamma^{\nu}_{\mu\sigma}V^\sigma
$$

The connection also appears in the definition of geodesics, which is a generalization of the notion of a straight line. A parameterized line is said to be a geodesic if it obeys the geodesic equation:

$$
\frac{\mathrm d^2x^\mu}{\mathrm d \lambda^2} + \Gamma^\mu_{\rho\sigma}\frac{\mathrm d x^\rho}{\mathrm d \lambda}\frac{\mathrm d x^\sigma}{\mathrm d \lambda} =0
$$
Where here $\lambda$ is the parameter of $x$.

Finally the technical expression of curvature is contained in the Riemann tensor, a $(1,3)$ tensor obtained from the connection by;

$$
R^\rho_{\sigma\mu\nu}=\partial_{\mu}\Gamma^\rho_{\nu\sigma} - \partial_v \Gamma^\rho_{\mu\sigma} + \Gamma^\rho_{\mu\lambda}\Gamma^{\lambda}_{\nu\sigma} - \Gamma^\rho_{\nu\lambda}\Gamma^\lambda_{\mu\sigma}
$$
Everything we want to know about the curvature is within this tensor. And it will vanish if and only if the metric is perfectly flat. The Einstein's equation of general relativity relates parts of this tensor to the energy-momentum tensor.


