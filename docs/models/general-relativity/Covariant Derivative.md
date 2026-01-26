# Introduction

In curved manifolds, there exists a problem. Partial derivatives are not good tensor operators. And we would like to have a generalization of them (called the covariant derivative), that is an operator that reduces to the partial derivative in flat space with inertial coordinates, but transforms as a tensor on an arbitrary manifold. 

In flat space in inertial coordinates, the partial derivative operator $\partial_\mu$ is a map from $(k,l)$ tensor fields to $(k,l+1)$ tensor fields, which acts linearly on its arguments and obeys the Leibniz rule on tensor products. But as this is obvious, this derivative depends on the coordinate system used. 

We would like to define an operator that has these properties, but in a way independent of coordinates. So we want:

**Linearity**

$$
\partial_\mu (A+B) = \partial_\mu A +\partial_\mu B
$$

and **Leibniz rule**

$$
\partial_\mu(A\otimes B) = (\partial_\mu A)\otimes B + A\otimes(\partial_\mu B)
$$

to be also true for the new operator $\nabla$. If this operator is going to obey the Leibniz rule, it can always be written as the partial derivatives plus some linear transformation. That is, to take the covariant derivative we first take the partial derivative, and then apply a correction to make the result covariant.

To do so we add the linear term, known as the connection coefficients:

$$
\nabla_\mu V^\nu = \partial_\mu V^\nu +\Gamma^\nu_{\mu\lambda} V^\lambda
$$

Notice that in the second terms the index originally on $V$ has moved to the $\Gamma$, and a new index is summed over. If this is the expression for the covariant derivative of a vector in terms of the partial derivative, we should be able to determine the transformation properties of $\Gamma^\nu_{\mu\lambda}$ by demanding that the left-hand side be a $(1,1)$ tensor. Therefore, we want the following transformation to work:

$$
\nabla_{\mu'} V^{\nu'} = \partial_{\mu'}x^\mu\partial_\nu x^{\nu'} \nabla_{\mu} V^\nu
$$

We have two ways to attack and then equate these:

1. First we start by expanding the right hand side of this equation:

$$
=\partial_{\mu'}x^\mu\partial_\nu x^{\nu'} \partial_\mu V^\nu + \partial_{\mu'}x^\mu\partial_\nu x^{\nu'} \Gamma^{\nu}_{\mu\lambda} V^\lambda 
$$
2. Second we would write the transformation of the left hand side and expand it:

$$
\partial_{\mu'}x^\mu\partial_\nu x^{\nu'} \partial_\mu V^\nu + \partial_{\mu'}x^\mu V^\nu \partial_\mu \partial_\nu x^{\nu'} + \Gamma^{\nu'}_{\mu'\lambda'}\partial_\lambda x^{\lambda'}V^\lambda =
$$

Now we equate these two:

$$\begin{align}
\partial_{\mu'}x^\mu\partial_\nu x^{\nu'} \partial_\mu V^\nu + \partial_{\mu'}x^\mu\partial_\nu x^{\nu'} \Gamma^{\nu}_{\mu\lambda} V^\lambda = 
&\partial_{\mu'}x^\mu\partial_\nu x^{\nu'} \partial_\mu V^\nu + \\ &\partial_{\mu'}x^\mu V^\nu \partial_\mu \partial_\nu x^{\nu'} + \Gamma^{\nu'}_{\mu'\lambda'}\partial_\lambda x^{\lambda'}V^\lambda 

\end{align}
$$

The first terms on both side would cancel each other. And we would solve for $\Gamma^{\nu'}_{\mu'\lambda'}$.

$$
\Gamma^{\nu'}_{\mu'\lambda'} = \partial_{\lambda'}x^\lambda\partial_{\mu'}x^\mu \partial_{\nu}x^{\nu'}\Gamma^{\nu}_{\mu\lambda}-\partial_{\lambda'}x^\lambda \partial_{\mu'}x^\mu \partial^2_{\mu\lambda}x^{\nu'}
$$

This is not, of course, the tensor transformation law. That's okay because *connection coefficients are not the components of a tensor*. They are purposefully constructed to be non-tensorial, but in such a way that the covariant derivative transforms as a tensor. the extra terms in the transformation of the partials and the $\Gamma$'s exactly cancel.

By similar reasoning one can find the covariant derivative of other sorts of tensors. But there is no reason as yet that the matrices representing this transformation should be related to the coefficients found here. So for example, in general case:

$$
\partial_\mu w_\mu = \partial_\mu w_\nu + \tilde\Gamma^\lambda_{\mu\nu} w_\lambda
$$

and $\tilde\Gamma$ is a new set of matrices for each $\mu$. Here we need to introduce two new properties that we would like our covariant derivative to have, in addition to linearity and the Leibniz rule.

**commutativity with contractions:**

$$
\nabla_\mu (T^{\lambda}_{\lambda\rho})
$$

**Reduces to the partial derivative on scalars**

$$
\nabla_\mu \phi =\partial_\mu \phi
$$

There is no way to "derive" these things as true, we just demand our covariant derivative to have these properties. the commutativity is equivalent to say that the Kronecker delta is covariantly constant:

$$
\nabla_\mu\delta^\lambda_\sigma = 0
$$

What these imply? Let us assume we have a scalar, $v^\lambda w_\lambda$:

$$
\nabla_\mu (v^\lambda w_\lambda) =(\nabla_\mu w_\lambda)v^\lambda + w_\lambda(\nabla_\mu v^\lambda)
$$

Resulting in:

$$
\underbrace{v^\lambda \partial_\mu w_\lambda + w_\lambda\partial_\mu v^\lambda}_{=\partial_\mu(w_\lambda v^\lambda)} + \tilde\Gamma^\sigma_{\mu\lambda}w_\sigma v^\lambda + \Gamma^\lambda_{\mu\sigma}v^\sigma w_\lambda
$$

Using the scalar reduction property we can equate this to $\partial_{\mu}(w_\lambda v^\lambda)$, therefore:


$$
\tilde\Gamma^\sigma_{\mu\lambda}w_\sigma v^\lambda + \Gamma^\lambda_{\mu\sigma}v^\sigma w_\lambda
=0
$$

Setting $\lambda\rightarrow\sigma$ and $\sigma\rightarrow\lambda$ for one of the terms we get:

$$
\tilde \Gamma^\sigma_{\mu\lambda} =-\Gamma^\sigma_{\mu\lambda}
$$

This implies that for one-forms we can use the same coefficients but with a minus sign:

$$
\nabla_\mu w_\nu = \partial_\mu w_\nu -\Gamma^{\lambda}_{\mu\nu}w_\lambda
$$

Also notice that, given a connection specified, we can immediately form another connection simply by permuting the lower indices. That is, the set of coefficients will also transform according to transformation found, so they determine a distinct connection. There's thus a tensor we can associate with any given connection, known as the torsion tensor, defined by:


$$
T^\lambda_{\mu\nu} = \Gamma^\lambda_{\mu\nu} -\Gamma^{\lambda}_{\nu\mu} = 2\Gamma^\lambda_{[\mu\nu]}
$$
It is clear that the torsion is anti-symmetric in its lower indices, and a connection that is symmetric in its lower indices is known as "torsion free". But, still there's infinitely many connections that can be defined and thus infinitely many covariant derivatives. In general this is fine, but there's a specific connection that shines for us physicists and is *metric compatible*. 

Therefore, we establish two more properties we wish our connections have:

**Torsion Free**
$$
\Gamma^\lambda_{\mu\nu}=\Gamma^{\lambda}_{(\mu\nu)}
$$
**Metric Compatibility**
$$
\nabla_\rho g_{\mu\nu} =0
$$

> A connection is metric compatible if the covariant derivative of the metric with respect to that connection is everywhere zero.


These two implies some interesting properties. First, it's easy to show that both the Levi-Civita tensor and the inverse metric also have zero covariant derivative,

$$
\begin{align}
\nabla_\lambda \epsilon_{\mu\nu\rho\sigma} &= 0\\
\nabla_\rho g^{\mu\nu} &=0 
\end{align}
$$
Next, a metric-compatible covariant derivative commutes with raising and lowering indices.

$$
g_{\mu\lambda}\nabla_{\rho} V^\lambda = \nabla_\rho(g_{\mu\lambda} V^\lambda)=\nabla_{\rho}V_\mu
$$

With non-metric-compatible connections we would have to be very careful about index placement when taking a covariant derivative.

We can show that there's only one connection with such capabilities by finding its components based on the metric components:

$$
\begin{align}
\nabla_{\rho} g_{\mu\nu} &=0\\
\nabla_{\mu} g_{\rho\nu} &=0\\
\nabla_{\nu} g_{\mu\rho} &=0
\end{align}
$$
Extending these and then adding the first two together and subtracting the third, with some additional calculations can give us the following expression of the connection in terms of the metric:

$$
\Gamma^\sigma_{\mu\nu} = \frac12 g^{\sigma\rho}(\partial_\mu g_{\nu\rho} +\partial_\nu g_{\rho\mu} - \partial_\rho g_{\mu\nu})
$$

First, note that in ordinary flat space there's an implicit connection we use all the time. The coefficients of the Christoffel connection in flat space vanish in Cartesian coordinates, but not in curvilinear coordinate systems. Contrawise, even in a curved space it is still possible to make the Christoffel symbol vanish at any one point. Of course this can only be established at a point, not in some neighborhood of the point.

The other interesting property is that the formula for the divergence of a vector has a simplified form. The covariant divergence of $V^\mu$ is given by:

$$
\nabla_\mu V^\mu = \partial_\mu V^\mu + \Gamma^\mu_{\mu\lambda} V^\lambda
$$

It is straightforward to show that the Christoffel connection satisfies:

$$
\Gamma^\mu_{\mu\lambda} = \frac{1}{\sqrt{|g|}}\partial_\mu (\sqrt{|g|})
$$
and we therefore have:

$$
\nabla_\mu V^\mu = \frac{1}{\sqrt{|g|}}\partial_\mu (\sqrt{|g|}V^\mu)
$$We use the Christoffel covariant derivative in the curved-space version of Stoke's theorem. If $V^\mu$ is a vector field over a region $\Sigma$ with boundary $\partial \Sigma$, the Stoke's theorem is:

$$
\int_\Sigma \nabla_\mu V^\mu \sqrt{|g|}\mathrm d^{n}x = \int_{\partial \Sigma}n_\mu V^\mu \sqrt{|\gamma|}\mathrm d^{n-1}x
$$

where $n_\mu$ is normal to $\partial \Sigma$, and $\gamma_{ij}$ is the induced metric on $\partial \Sigma$. If the connection weren't metric-compatible or torsion-free, there would be additional terms in this equation.
