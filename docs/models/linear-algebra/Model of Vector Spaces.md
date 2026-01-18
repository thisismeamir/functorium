---
sticker: lucide//hash
---
# Definition of Vector Spaces

A vector is an object of the vector space. This is not a recursive argument, because we define what is means to have a vector space, and the structure and operations that it has, therefore explaining what a vector is becomes just the mere fact that if we can construct with a set of objects and defined operations and fields a structure that can be called a vector space, then those objects can be called vectors.

Before getting into Vector spaces it is useful to know the notion of a field.

[[atoms/Field (Mathematical Structure)]]
## Vector Spaces

A linear vector space $\mathcal V$ is then defined as a collection of objects $v$ called vectors, for which there exists:

1. A definite rule for forming the vector sum, denoted $\mathbf v+\mathbf w$.
2. A definite rule for multiplication by scalars, denoted with $a \cdot \mathbf v$

With the following features:

- The result of these operations is another elements of the space, which is the same as closure that we've discussed earlier.
- Scalar multiplication is distributive in the vector addition:
  $$ a\cdot (\mathbf v + \mathbf w) = (a\cdot \mathbf v) + (a\cdot \mathbf w)$$
- Scalar multiplication is associative.
- Addition is commutative.
- Addition is associative.
- There exists a null vector $\mathbf 0$ obeying $\mathbf v + \mathbf 0 = \mathbf v$.
- For every vector $\mathbf v$ there exists an inverse under addition, $-\mathbf v$ such that $\mathbf v + (-\mathbf v) = \mathbf 0$.

The numbers (scalars) are called the field over which the vector space is defined. If the field consists of all real numbers, we have a real vector space, if they are complex, we have a complex vector space. The vectors themselves are neither real or complex; the adjective applies only to the scalars. Let us note that the above axioms imply:

- $\mathbf 0$ is unique. [[atoms/Uniqueness of Zero element in Vector Space]]
- $0\mathbf v = \mathbf 0$ (notice that the left hand side $0$ is a scalar and the right hand side is a vector).
- $- \mathbf v = -1\cdot \mathbf v$.
- [[atoms/Uniqueness of Additive Inverse for Each Element]].

One can find many examples that are vector spaces for this we have some mentions in [[Model of Examples of Linear Algebra]]

# Subspaces

A subset $W$ of a vector space $V$ over a field $\mathbb K$ is called a *subspace* of $V$ if $W$ is a vector space over $\mathbb K$ with the operations of addition and scalar multiplication defined on $V$.

**Trivial Subspaces:** For a vector spaces $V$ there exists at least two subspaces, known as trivial subspaces. These are $V$ itself and $\{0\}$. The latter is also called the *zero subspace* of $V$. 

To check that a subset is a subspace, we don't have to verify all the conditions again. The following gives the set of conditions that are to be verified:

1. $0\in W$: The identity of addition should be inside the subset.
2. $w_1 + w_2 \in W$, whenever $w_1,w_2\in W$.
3. $\lambda w\in W$ whenever, $\lambda \in \mathbb F$ and $w\in W$.

