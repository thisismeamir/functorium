---
sticker: lucide//atom
---
# Systems of Linear Equations and Vector Spaces

A system of linear equations can be represented as a vector equation within a vector space. Consider the following:

**1. General Form:**

A general system of *m* linear equations in *n* variables can be written as:

$$
\begin{aligned}
a_{11}x_1 + a_{12}x_2 + \dots + a_{1n}x_n &= b_1 \\
a_{21}x_1 + a_{22}x_2 + \dots + a_{2n}x_n &= b_2 \\
\vdots \\
a_{m1}x_1 + a_{m2}x_2 + \dots + a_{mn}x_n &= b_m
\end{aligned}
$$

**2. Vector Representation:**

This system can be expressed as a vector equation:

$$ x_1 \mathbf{v}_1 + x_2 \mathbf{v}_2 + \dots + x_n \mathbf{v}_n = \mathbf{b} $$

where:

*   $\mathbf{v}_i$ are vectors in $V$ (typically in $\mathbb{R}^m$), representing the coefficients of each variable.
*   $\mathbf{b}$ is a vector in $V$ representing the constants on the right-hand side of the equations.
*   $x_1, x_2, ..., x_n$ are scalars (elements of a field, often $\mathbb{R}$).

**3. Homogeneous Systems:**

If all $b_i = 0$, the system is homogeneous:

$$ x_1 \mathbf{v}_1 + x_2 \mathbf{v}_2 + \dots + x_n \mathbf{v}_n = \mathbf{0} $$

The solution set of a homogeneous system forms a subspace of $V$. This subspace is spanned by the vectors $\mathbf{v}_1, \mathbf{v}_2, ..., \mathbf{v}_n$.  If these vectors are linearly independent, the subspace is equal to the span of those vectors.

**4. Non-homogeneous Systems:**

For non-homogeneous systems, the solution set (if it exists) is a translation of a subspace. Specifically, if $\mathbf{x}_p$ is a particular solution, then the general solution can be written as:

$$ \mathbf{x} = \mathbf{x}_p + \mathbf{x}_h $$

where $\mathbf{x}_h$ belongs to the solution set of the corresponding homogeneous system (a subspace).

**5. Matrix Representation:**

The system can also be represented using matrices:

$$ A\mathbf{x} = \mathbf{b} $$

where $A$ is an $m \times n$ matrix, $\mathbf{x}$ is a vector in $\mathbb{R}^n$, and $\mathbf{b}$ is a vector in $\mathbb{R}^m$.  The columns of *A* are the vectors $\mathbf{v}_1, ..., \mathbf{v}_n$ from the vector representation.

**6. Connection to Linear Transformations:**

If $A$ represents a linear transformation $T: V \to W$, then solving $Ax = b$ is equivalent to finding vectors in *V*  that are mapped to *b* by *T*.