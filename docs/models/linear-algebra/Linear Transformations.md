
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
