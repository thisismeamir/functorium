---
sticker: lucide//atom
---
# Tensor Densities

Tensor densities are objects that transform according to a rule similar to tensors, but with an additional multiplicative factor involving the determinant of a coordinate transformation matrix. This distinction arises when considering how quantities change between different coordinate systems.

**Transformation Law:**

Given two coordinate systems, $x^{\mu}$ and $x'^{\mu}$, and an *n*-dimensional tensor density $T$, its components transform as:

$$
T_{\alpha_1 \dots \alpha_m}^{\beta_1 \dots \beta_n} = J \tilde{T}_{\alpha_1 \dots \alpha_m}^{\beta_1 \dots \beta_n}
$$

where:

*   $T_{\alpha_1 \dots \alpha_m}^{\beta_1 \dots \beta_n}$ are the components of the tensor density in coordinate system $x^{\mu}$.
*   $\tilde{T}_{\alpha_1 \dots \alpha_m}^{\beta_1 \dots \beta_n}$ are the components of the tensor density in coordinate system $x'^{\mu}$.
*   $J = \frac{\partial x^\mu}{\partial x'^{\mu'}} \tilde{\epsilon}_{\mu_1\mu_2\dots\mu_n} \epsilon_{\mu_1'\mu_2'\dots\mu_n'}$ is a Jacobian factor, which depends on the coordinate transformation and the Levi-Civita symbol.

**Connection to the Levi-Civita Symbol:**

The Levi-Civita symbol $\epsilon_{\mu_1\mu_2\dots\mu_n}$ (or $\tilde{\epsilon}_{\mu_1'\mu_2'\dots\mu_n'}$) plays a crucial role in defining this transformation law.  It appears as part of the Jacobian factor $J$.

**General Formula:**

For any matrix $M^\mu_{\ \mu'}$:

$$
\tilde \epsilon_{\mu_1'\mu_2'\dots\mu_n'}|M| = \epsilon_{\mu_1\mu_2\dots\mu_n}M^{\mu_1}_{\mu_1'}M^{\mu_2}_{\mu_2'}\dots M^{\mu_n}_{\mu_n'}
$$

**Coordinate Transformations:**

Consider the transformation between coordinate systems $x^\mu$ and $x'^\mu$. Setting $M^\mu_{\ \mu'} = \frac{\partial x^\mu}{\partial x'^{\mu'}}$:

$$
\tilde \epsilon_{\mu_1'\mu_2'\dots\mu_n'} = \left|\frac{\partial x^{\mu'}}{\partial x^\mu}\right| \epsilon_{\mu_1\mu_2\dots\mu_n} \frac{\partial x^{\mu_1}}{\partial x'^{\mu_1}} \frac{\partial x^{\mu_2}}{\partial x'^{\mu_2}} \dots \frac{\partial x^{\mu_n}}{\partial x'^{\mu_n}}
$$

This equation demonstrates how the Levi-Civita symbol transforms under a coordinate change, incorporating a determinant factor. The inverse transformation follows similarly:

$$
\epsilon_{\mu_1\mu_2\dots\mu_n} = \left|\frac{\partial x}{\partial x'}\right| \tilde{\epsilon}_{\mu_1'\mu_2'\dots\mu_n'} \frac{\partial x'^{\mu_1}}{\partial x^{\mu_1}} \frac{\partial x'^{\mu_2}}{\partial x^{\mu_2}} \dots \frac{\partial x'^{\mu_n}}{\partial x^{\mu_n}}
$$

**Distinction from Tensors:**

Unlike tensors, which transform with a simple coordinate transformation matrix, tensor densities are multiplied by a factor involving the determinant of the transformation. This difference reflects their behavior under changes in volume element during coordinate transformations.

- [[Tensor Densities - Weight and Transformation to Tensors]]