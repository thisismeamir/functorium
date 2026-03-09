---
sticker: lucide//atom
---
# Euclidean Space

Euclidean space, denoted as $\mathbb{R}^n$, is the set of all n-tuples of real numbers.  It's a fundamental concept in geometry and analysis.

## Definition

$$\mathbb{R}^n = \{ (x_1, x_2, ..., x_n) \mid x_i \in \mathbb{R} \}$$

For example:
*  $\mathbb{R}^1$ is the set of real numbers itself.
*  $\mathbb{R}^2$ represents the Cartesian plane.
*  $\mathbb{R}^3$ represents ordinary three-dimensional space.

## Vector Operations

Elements of $\mathbb{R}^n$ are called vectors.  Vector addition and scalar multiplication are defined as follows:

**Addition:** For $\mathbf{u} = (u_1, u_2, ..., u_n)$ and $\mathbf{v} = (v_1, v_2, ..., v_n)$:
$$
\mathbf{u} + \mathbf{v} = (u_1 + v_1, u_2 + v_2, ..., u_n + v_n)
$$

**Scalar Multiplication:** For $c \in \mathbb{R}$ and $\mathbf{u} = (u_1, u_2, ..., u_n)$:
$$
c\mathbf{u} = (cu_1, cu_2, ..., cu_n)
$$

## Euclidean Distance

The Euclidean distance between two points $\mathbf{x} = (x_1, x_2, ..., x_n)$ and $\mathbf{y} = (y_1, y_2, ..., y_n)$ in$\mathbb{R}^n$is given by:

$$
d(\mathbf{x}, \mathbf{y}) = \sqrt{\sum_{i=1}^{n} (x_i - y_i)^2}
$$

This can also be written as $\| \mathbf{x} - \mathbf{y} \|$ using the Euclidean norm.

## Inner Product

The inner product (or dot product) of two vectors $\mathbf{u} = (u_1, u_2, ..., u_n)$ and$\mathbf{v} = (v_1, v_2, ..., v_n)$ is defined as:

$$
\langle \mathbf{u}, \mathbf{v} \rangle = \sum_{i=1}^{n} u_i v_i = u_1v_1 + u_2v_2 + ... + u_nv_n
$$

The inner product is related to the Euclidean distance by:

$$
\langle \mathbf{u}, \mathbf{v} \rangle = \| \mathbf{u} \| \| \mathbf{v} \| \cos{\theta}
$$

where $\theta$ is the angle between $\mathbf{u}$ and $\mathbf{v}$.

## Basis

$\mathbb{R}^n$ can be equipped with a standard basis, typically denoted as $\{ \mathbf{e}_1, \mathbf{e}_2, ..., \mathbf{e}_n \}$, where $\mathbf{e}_i = (0, 0, ..., 1, 0, ..., 0)$ with the '1' in the i-th position.  Any vector can be expressed as a linear combination of these basis vectors.

## Subspaces

A subspace of $\mathbb{R}^n$ is a subset that is closed under addition and scalar multiplication.