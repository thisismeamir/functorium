---
sticker: lucide//atom
---
# Tensor Densities: Weight and Transformation to Tensors

Tensor densities, as previously defined, differ from tensors due to an additional factor in their transformation law – a determinant-like term. This factor introduces a concept known as "weight."  It's possible to transform a tensor density into a true tensor by compensating for this weight.

**Weight of a Tensor Density:**

The *weight* (or degree) of a tensor density, denoted by $w$, is defined as the power of the determinant factor that appears in its transformation law. Specifically, if we have:

$$
T_{\alpha_1 \dots \alpha_m}^{\beta_1 \dots \beta_n} = J \tilde{T}_{\alpha_1 \dots \alpha_m}^{\beta_1 \dots \beta_n}
$$

where $J = |\frac{\partial x^{\mu}}{\partial x'^{\mu'}}|\epsilon_{\mu_1\mu_2\dots\mu_n}\tilde{\epsilon}_{\mu_1'\mu_2'\dots\mu_n'}$, then the weight of the tensor density *T* is:

$$
w = 1
$$

In this case, $J$ includes a determinant factor $|\frac{\partial x^{\mu}}{\partial x'^{\mu'}}|$.  A general tensor density can have different powers of this determinant. A density with $J = \left( |\frac{\partial x^{\mu}}{\partial x'^{\mu'}}|\right)^k$ would have weight *k*.

**Transforming a Tensor Density to a Tensor:**

To transform a tensor density into a true tensor, one must divide the tensor density by the appropriate power of the determinant factor.  Let $T$ be a tensor density with components $T_{\alpha_1 \dots \alpha_m}^{\beta_1 \dots \beta_n}$ and weight *w*. Then the corresponding tensor $\tilde{T}$ is obtained as:

$$
\tilde{T}_{\alpha_1 \dots \alpha_m}^{\beta_1 \dots \beta_n} = \frac{T_{\alpha_1 \dots \alpha_m}^{\beta_1 \dots \beta_n}}{|\frac{\partial x^{\mu}}{\partial x'^{\mu'}}|^w}
$$

This operation effectively removes the determinant-like factor from the transformation law, resulting in a standard tensor transformation.  The new object $\tilde{T}$ now transforms as:

$$
\tilde{T}_{\alpha_1 \dots \alpha_m}^{\beta_1 \dots \beta_n} = \tilde{T}_{\alpha_1 \dots \alpha_m}^{\beta_1 \dots \beta_n}
$$

**Example:**

Consider a tensor density $T_{\mu\nu}$ with weight *w*.  Its transformation law is:

$$
T_{\mu' \nu'} = J T_{\mu\nu}
$$

where $J = |\frac{\partial x^{\mu}}{\partial x'^{\mu'}}|\epsilon_{\mu\nu}\tilde{\epsilon}_{\mu'\nu'}$. To transform it into a tensor, we divide by the weight:

$$
\tilde{T}_{\mu' \nu'} = \frac{T_{\mu' \nu'}}{|\frac{\partial x^{\mu}}{\partial x'^{\mu'}}|^w}
$$

Now $\tilde{T}$ transforms as a standard tensor:

$$
\tilde{T}_{\mu' \nu'} = M^{\mu'}_{\alpha'}M^{\nu'}_{\beta'} \tilde{T}_{\alpha\beta}
$$

where $M^{\mu'}_{\alpha'}$ is the coordinate transformation matrix.  The determinant factor has been eliminated, and the transformation follows the standard tensor transformation rule.