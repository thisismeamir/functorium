
After we've defined [[Covariant Derivative]], we must think of the use of it as well. Since we've constructed it based off our desire to make it a tensor, we should make sure that it inherits features we want. We think of derivative as a way of qualifying how fast something is changing. In the case of tensors, the crucial issue is *"changing with respect to what?"*.

An ordinary function defines a number at each point in spacetime, and it is straightforward to compare two different numbers, and it is straightforward to compare two different numbers, so we shouldn't be surprised that the partial derivative of functions remained valid on arbitrary manifolds.

But a tensor is a map from vectors and 1-forms to the field (real numbers, complex numbers). Since we have successfully constructed a covariant derivative, can we think of it as somehow measuring the rate of change of tensors?

The answer turns out to be yes! The covariant derivative quantifies the instantaneous rate of change of a tensor field in comparison to what the tensor would be if it were "parallel transported". In other words, a connection defines a specific way of keeping a tensor constant, on the basis of which we can compare nearby tensors.

# What is Parallel Transportation

We're used to comparing vectors in flat space, assuming two vectors are in two different places, it is actually very natural to compare vectors at different points. The reason why it is natural is because it makes sense, in flat space, to move a vector from one point to another while keeping it constant. Then, once we get the vector from one point to another, we can do the usual operations allowed in a vector space.

This concept of moving a vector along a path, keeping constant all the while, is known as parallel transport. It requires a connection to be well defined; the intuitive manipulation of vectors in flat space makes implicit use of the Christoffel connection on this space. 

The important difference between flat and curved spaces is that in the curved one, *the result of parallel transporting a vector from one point to another will depend on the path taken between the points*.

It therefore appears as if there is no natural way to uniquely move a vector from one tangent space to another; We can always parallel-transport it, but the result depends on the path, and there is no natural choice of which path to take.

Despite this, Parallel transport is supposed to be the curved-space generalization of the concept of "keeping the vector constant" as we move it along a path; similarly for a tensor of arbitrary rank.

## Formulation

Given a curve $x^\mu(\lambda)$, the requirement of constancy of a tensor $T^{\mu_1\dots\mu_k}_{\nu_1\dots\nu_l}$ along this curve in flat space is simply that the components be constant:

$$
\frac{\mathrm d}{\mathrm d\lambda}T^{\mu_1\dots\mu_k}_{\nu_1\dots\nu_l} = \frac{\mathrm dx^\mu}{\mathrm d\lambda}\frac{\partial}{\partial x^\mu}T^{\mu_1\dots\mu_k}_{\nu_1\dots\nu_l} = 0
$$

To make this tensorial, we simply replace this partial derivative by a covariant one, and define the *directional covariant derivative* as:

$$
\frac{\mathrm D}{\mathrm d\lambda} =\frac{\mathrm dx^\mu}{\mathrm d \lambda}\nabla_\mu
$$
We therefore, define **parallel transport** of the tensor $T$ along the path $x^\mu(\lambda)$ to be the requirement that the covariant derivative of $T$ along the path vanishes.

$$
\left(\frac{\mathrm D}{\mathrm d \lambda} T\right)^{\mu_1\dots\mu_k}_{\nu_1\dots\nu_l} =0
$$

This is a well-defined tensor equation, known as the equation of parallel transport. We can look at the parallel transport equation as a first-order differential equation defining an initial-value problem. Given a tensor at some place there will be a unique continuation of the tensor to other points along the path such that the continuation solves the equation of parallel transport. Then we say that such a tensor is parallel-transported.

The notion of parallel transportation, as obvious, relies on the [[Christoffel Symbol]]and the connection defined. If the connection is metric-compatible, the metric is always parallel transported with respect to it.

$$
\frac{\mathrm D}{\mathrm d\lambda} g_{\mu\nu} = 0
$$
It the follows that the inner product of two parallel-transported vectors is preserved. That is:
$$

\frac{\mathrm D}{\mathrm d\lambda}(g_{\mu\nu}V^\mu W^\nu) = \left(\frac{\mathrm D}{\mathrm d\lambda} g_{\mu\nu}\right) V^\mu W^\nu + g_{\mu\nu} \left(\frac{\mathrm D}{\mathrm d\lambda} V^\mu\right)W^\nu + g_{\mu\nu} V^\mu\left(\frac{\mathrm D}{\mathrm d\lambda} W^\nu\right) =0  
$$

This means that parallel transport with respect to metric-compatible connection preserves the norm of vectors, the sense of orthogonality, and so on.

