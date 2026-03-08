---
sticker: lucide//atom
---
# Range Space and Null Space

Considering a linear transformation from $V$ to $W$ is a function that preserves structure, a linear transformation has two significant sets associated with it: the null space and the range set. In fact, they are subspaces of $V$ and $W$ respectively. 

The range space of a linear transformation consists of all possible output vectors that can be obtained by applying the transformation to input vectors. It represents the span of the transformed vectors in the co-domain. 

On the other hand, the null space of a linear transformation comprises all input vectors that are mapped to the zero vector in the co-domain, forming a subspace of the domain. 

Together, these spaces provide valuable insights into the behavior and properties of the linear transformation. In this section, we will discuss in detail these subspaces and some of the important results associated.

**Definition (Range set and Null set)** Let $V$ and $W$ be vector spaces over the field $\mathbb{K}$, and let $T: V \rightarrow W$ be linear, then range set of $T$, denoted by $R(T)$, is a subset of $W$ consisting of all images of vectors in $V$ under $T$. That is,

$$ \mathcal{R}(T) = \{ T(v) | v \in V \} $$

and the null set or kernel of $T$, denoted by $N(T)$, is the set of all vectors $v \in V$ such that $T(v) = 0$. That is,

$$ \mathcal{N}(T) = \{ v \in V | T(v) = 0 \} $$

**Theorem:**
Let $V$, and $W$ be vector spaces over the field $\mathbb{K}$, and let $T: V\to W$ be a linear transformation. Then $\mathcal{N}(T)$ and $\mathcal{R}(T)$ are subspaces of $V$ and $W$ respectively.

**Proof:**
Let $T:V\to W$ be a linear transformation. We have $\mathcal{N}(T)=\{ v\in V|T(v)=0 \}$. Clearly, $\mathcal{N}(T) \subseteq V$ Now for $v_{1},v_{2} \in \mathcal{N}(T)$ and $\lambda \in \mathbb{K}$, we have:

$$
T(\lambda v_{1}+v_{2}) = \lambda T(v_{1})+ T(v_{2}) = 0 
$$
Therefore, $\lambda v_{1}+v_{2} \in \mathcal{N}(T)$ for all $v_{1},v_{2}\in \mathcal{N}(t)$ and $\lambda \in \mathbb{K}$. Hence $\mathcal{N}(T)$ is a subspace of $V$.

Also we have $\mathcal{R}(T)=\{ T(v) | v \in V \}$. Clearly, $\mathcal{R}(T) \subseteq W$. As $\mathcal{R}(T)$ is range space, for $w_{1},w_{2}\in \mathcal{R}(T)$ there exists $v_{1},v_{2} \in V$ such that $T(v_{1}) = w_{1}$ and $T(v_{2})=w_{2}$. Since $v_{1},v_{2} \in V$ and $V$ is a vector space over the field $\mathbb{K}$, $\lambda v_{1}+v_{2} \in V$, where $\lambda \in \mathbb{K}$ Then

$$
T(\lambda v_{1}+v_{2}) =\lambda T(v_{1}) + T(v_{2}) = \lambda w_{1} + w_{2} \in \mathcal{R}(T)
$$

Hence $\mathcal{R}(T)$ is a subspace of $W$.

## Nullity and Rank

If $\mathcal{N}(T)$ and $\mathcal{R}(T)$ are finite dimensional, the dimensions of $\mathcal{N}(T)$ and $\mathcal{R}(T)$ are called **Nullity** and **Rank** of $T$ respectively. 

If $T$ is a linear transformation from a finite-dimensional vector space $V$ to a vector space $W$. It is clear that, if we know the images of basis elements of $V$, it is easy to calculate the rank.

$$
\mathcal{R}(T) = \mathrm{span}(T(B)) = \mathrm{span}\left\{ T(v_{1}),T(v_{2}), \dots, T(v_{n}) \right\} 
$$
We can also conclude that, if $\dim(V) = n$, then $\mathrm{Rank}(T) \leq n$

**Theorem: Rank-Nullity Theorem**:
Let $V$ be a finite-dimensional vector space over a field $\mathbb{K}$ and let $W$ be a vector space over the same field $\mathbb{K}$. Let $T: V \to W$ be a linear transformation, then:

$$
\mathrm{Nullity}(T) + \mathrm{Rank}(T) = \dim(V)
$$

**Proof:**
Let $V$ and $W$ be finite-dimensional vector spaces over the field $\mathbb{K}$, and let $T$ be a linear transformation from $V$ to $W$. Let $\mathcal{N}(T)$ be the null space of $T$. As $\mathcal{N}(T)$ is a subspace of $V$ and $V$ is finite-dimensional, $\mathcal{N}$ itself is finite-dimensional and hence it has a finite basis, $\{ v_{1},v_{2},\dots,v_{k} \}$. Since these are linearly independent set in $V$, then it can be extended to a basis as well.  We know that:

$$
\mathcal{R}(T) = \mathrm{span}\{T(v_{1}),T(v_{2}),\dots,T(v_{n})\}
$$

But as $T(v_{1}) = T(v_{2})=\dots = T(v_{k}) = 0$, 

$$
\mathcal{R}(T) = \mathrm{span}\{T(v_{k+1}),\dots,T(v_{n}))\}
$$
Now we have to prove that $\{ T(v_{k+1}),T(v_{k+2}),\dots,T(v_{n}) \}$ is linearly independent. Let $\lambda_{k+1}, \lambda_{k+2}, \dots,\lambda_{n}\in \mathbb{K}$ be such that

$$
\lambda_{k+1}T(v_{k+1}) + \lambda_{k+2}T(v_{k+2}) + \dots + \lambda_{n} T(v_{n}) = 0
$$
which implies:
$$
T(\lambda_{k+1}v_{k+1}+\dots+\lambda_{n}v_{n})=0
$$
That is,

$$
\lambda_{k+1}v_{k+1} + \lambda_{k+2}v_{k+2} + \dots +\lambda_{n}v_{n}\in \mathcal{N}(T)
$$
Since $\{ v_{1},v_{2},\dots ,v_{k} \}$ is a basis f $\mathcal{N}(T)$, there exists, $\lambda_{1},\lambda_{2},\dots ,\lambda_{k}\in \mathbb{K}$ such that:


$$
\lambda_{k+1}v_{k+1} + \lambda_{k+2}v_{k+2} + \dots + \lambda_{n}v_{n} = \lambda_{1} v_{1} + \lambda_{2}v_{2} + \dots + \lambda_{k}v_{k}
$$

Since $B$ is a basis for $V$, this implies that $\lambda_{i}=0$ for all $i = 1,2,\dots, n$. Therefore $\{ T(v_{k+1}),T(v_{k+2}),\dots,T(v_{n}) \}$ is linearly independent and hence is a basis of $\mathcal{R}(T)$. Therefore $\mathrm{Rank}(T) = n-k$. And fineally:

$$
\mathrm{Nullity}(T) + \mathrm{Rank}(T) = k + n - k = n = \dim(V)
$$

**Theorem:**
Let $V$ and $W$ be vector spaces over a field $\mathbb{K}$. Let $T:V\to W$ be a linear transformation which is one-one. Then a subset $S$ of $V$ is linearly independent if and only if $T(S)$ is linearly independent.

**Proof:**
- [ ] To be proved later on.


**Useful notes to go on from here: (Though they have not been written yet)**

- [[Row and Column Spaces]]