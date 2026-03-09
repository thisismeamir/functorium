---
sticker: lucide//atom
---

It is important to look in specific to functions on vector spaces that preserve the structure. An important class of such functions called linear transformations. We can say that a linear transformation is a function between two vector spaces that preserve algebraic operations.

Let $V$ and $W$ be vector spaces over the field $\mathbb K$. A linear transformation $T$ from $V$ into $W$ is a function that:

- $\forall v_1,v_2 \in V, T(v_1 + v_2) = T(v_1) + T(v_2)$
- $\forall v \in V and \lambda \in \mathbb K, T(\lambda v) = \lambda T(v)$.

The first one is called the additive property and the second is called the homogeneity property. Written to gether:

$$
T(\lambda_1 v_1 + \lambda _2v_2) = \lambda_1 T(v_1) + \lambda_2 T(v_2)
$$
is called the principle of superposition. A linear transformation from $V$ to itself is called a linear operator.

From these two one can derive that:

- If $T$ is linear, then $T(0)=0$.
- $T$ is linear if and only if $T(\lambda v_1 + v_2) = \lambda T(v_1) + T(v_2)$ for all $v_1,v_2\in V$ and $\lambda \in\mathbb K$.
- If $T$ is linear, then $T(v_1 - v_2) = T(v_1)-T(v_2)$ for all $v_1,v_2\in V$
- Let $\{v_i\}$ be a linearly dependent set in $V$, then $\{T(v_i)\}$ is a linearly dependent set in $W$.


**Theorem:**
Let $V$ and $W$ be vector spaces over the field $\mathbb{K}$ and $T:V\to W$ be a function:

- If $T$ is linear, then $T(0)=0$.
- $T$ is linear if and only if $T(\lambda v_{1}+v_{2})=\lambda T(v_{1}) + T(v_{2})$ for all $v_{1},v_{2}\in V$ and $\lambda \in \mathbb{K}$.
- If $T$ is linear, then $T(v_{1}-v_{2})=T(v_{1})-T(v_{2})$ for all $v_{1},v_{2}\in V$.
- $T$ is linear if and only if, for $v_{1},v_{2},\dots,v_{n}\in V$ and $\lambda_{1}, \lambda_{2}, \dots, \lambda_{n} \in \mathbb{K}$ we have
  $$
T\left( \sum_{i=1}^{n}\lambda_{i}v_{i} \right) = \sum_{i=1}^{n}\lambda_{i}T(v_{i})
$$

- Let $\{ v_{1},v_{2},\dots ,v_{n} \}$ be a linearly dependent set in $V$, then $\{ T(v_{1}), T(v_{2}),\dots,T(v_{n}) \}$ is linearly dependent set in $W$.

**Proof:**
- [ ] Prove this theorem later on. I did it on paper but writing it here is a waste of time.

**Theorem:**
Let $V$ be a finite-dimensional vector space over the field $\mathbb{K}$ with basis $\{ v_{1},v_{2},v_{3}\dots,v_{n} \}$. Let $W$ be a vector space over the same field $\mathbb{K}$ and $\{ w_{1},w_{2},\dots,w_{n} \}$ be an arbitrary set of vectors in $W$, then there exists exactly one linear transformation $T:V\to W$ such that $T(v_{i})=w_{i}$, where $i=1,2,\dots, n$.

**Proof:**
- [ ] Prove this theorem later on.