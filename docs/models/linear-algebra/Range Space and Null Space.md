# Range Space and Null Space

Considering a linear transformation from $V$ to $W$ is a function that preserves structure, a linear transformation has two significant sets associated with it: the null space and the range set. In fact, they are subspaces of $V$ and $W$ respectively. The range space of a linear transformation consists of all possible output vectors that can be obtained by applying the transformation to input vectors. It represents the span of the transformed vectors in the co-domain. On the other hand, the null space of a linear transformation comprises all input vectors that are mapped to the zero vector in the co-domain, forming a subspace of the domain. Together, these spaces provide valuable insights into the behavior and properties of the linear transformation. In this section, we will discuss in detail these subspaces and some of the important results associated.

**Definition 3.2 (Range set and Null set)** Let $V$ and $W$ be vector spaces over the field $\mathbb{K}$, and let $T: V \rightarrow W$ be linear, then range set of $T$, denoted by $R(T)$, is a subset of $W$ consisting of all images of vectors in $V$ under $T$. That is,

$$ R(T) = \{ T(v) | v \in V \} $$

and the null set or kernel of $T$, denoted by $N(T)$, is the set of all vectors $v \in V$ such that $T(v) = 0$. That is,

$$ N(T) = \{ v \in V | T(v) = 0 \} $$

