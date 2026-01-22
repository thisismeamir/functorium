---
sticker: lucide//atom
---

A basis of a vector space is a subset of the vector space which can be used to uniquely represent each vector in the given space. 

To start introducing basis we must first define the span of a set:

## Span of a Set

Let $S=\{v_1,v_2,\dots,v_n\}$ be a subset of a vector space $V$. Then the span of $S$, denoted by $\text{span}(S)$, is the set consisting of all linear combinations of the vectors in $S$. That is,

$$
\text{span}(S) = \{\lambda_1 v_1 + \lambda_2v_2+\dots+\lambda_n vn | \lambda_i \in \mathbb K\}
$$
For convenience, we define $\text{span}(\phi) = \{0\}$.

A subset $S$ of a vector space $V$ spans (or generates) $V$, if $\text{span}(S)=V$. If there exists a finite subset $S$ of $V$ such that $S$ spans $V$, then $V$ is called finite-dimensional vector space, otherwise, it's called infinite-dimensional vector space. 

$\text{span}(S)$ is a subspace of $V$, since what it contains are all the linear combinations of a subset of $V$, therefore, closure is assured.

## Basis

Let $V$ be a vector space over a field $\mathbb K$. If a set $B\subseteq V$ is linearly independent and $\text{span}(B) = V$, then $B$ is a called a basis for $V$. If the basis has some specific order, then it is called an ordered basis.

**Theorem**
Let $V$ be a finite-dimensional vector space over a field $\mathbb{K}$ and $S = \{v_1, v_2, ..., v_n\}$ spans $V$. Then $S$ can be reduced to a basis $B$ of $V$.

**Proof:** Let $V$ be a finite-dimensional vector space over a field $\mathbb{K}$ and $S = \{v_1, v_2, ..., v_n\}$ spans $V$. Let $S_\sigma = \{v_{\sigma 1}, v_{\sigma 2}, ..., v_{\sigma \alpha}\}$ denote the set of all non-zero elements of $S$. Now, we will construct a linearly independent set $B$ from $S$, with span$ (B) = S$. Pick the element $v_{\sigma 1} \in S_\sigma$. If $v_{\sigma 2} = \lambda v_{\sigma 1}$ for some $\lambda \in \mathbb{K}$, then $v_{\sigma 2} \notin B$, otherwise $v_{\sigma 2} \in B$. Now consider $v_{\sigma 3} \in S_\sigma$. If $v_{\sigma 3} = \lambda_1 v_{\sigma 1} + \lambda_2 v_{\sigma 2}$ for some $\lambda_1, \lambda_2 \in \mathbb{K}$, then $v_{\sigma 3} \notin B$, otherwise $v_{\sigma 3} \in B$. Proceeding like this, after $\sigma_\alpha$ steps we will get a linearly independent set with span$ (B) = V$.

**Corollary**
Every finite-dimensional vector space $V$ has a basis.

**Proof:** Let $V$ be a finite-dimensional vector space. Then there exists a finite subset $S$ of $V$ with span$ (S) = V$. Then $S$ can be reduced to a basis.

**Theorem**
Let $V$ be a vector space over a field $\mathbb{K}$. If $B = \{v_1, v_2, ..., v_n\}$ is a basis for $V$, then any $v \in V$ can be uniquely expressed as a linear combination of vectors in $B$.

**Proof:**

Let $B$ be a basis of $V$ and $v \in V$. Suppose that $v$ can be expressed as a linear combination of vectors in $B$ as:

$$ v = \lambda_1 v_1 + \lambda_2 v_2 + ... + \lambda_n v_n $$

and as

$$ v = \mu_1 v_1 + \mu_2 v_2 + ... + \mu_n v_n $$

where $\lambda_i, \mu_i \in \mathbb{K}$ for all $i = 1, 2, ..., n$. Subtracting the second expression from first, we get:

$$ 0 = (\lambda_1 - \mu_1)v_1 + (\lambda_2 - \mu_2)v_2 + ... + (\lambda_n - \mu_n) v_n $$

Since $B$ is linearly independent, this implies that $\lambda_i - \mu_i = 0$ for all $i = 1, 2, ..., n$. That is, $\lambda_i = \mu_i$ for all $i = 1, 2, ..., n$.

**Theorem**
Let $V$ be a finite-dimensional vector space over a field $\mathbb{K}$ and $B$ be a basis of $V$. Then basis is a minimal spanning set in $V$. That is, if $B$ is a basis of $V$, there does not exist a proper subset of $B$ that spans $V$.

**Proof:**

Let $V$ be a finite-dimensional vector space over a field $\mathbb{K}$ and $B = \{v_1, v_2, ..., v_n\}$ be a basis of $V$. Let $S$ be a proper subset of $B$ that spans $V$. Since $S \subset B$ and $S \neq B$, there exists at least one element $v$ such that $v \in B$ and $v \notin S$. Rearrange the elements of $B$ so that the first $k$ elements are also elements of $S$ and the remaining $n-k$ elements belong to only $B$. Now take any element $v_{k+i} \in B$ where $i \in \{1, 2, ..., n-k\}$. Since $\text{span}(S) = V$ and $v_{k+i} \in V$, there exists $\lambda_1, \lambda_2, ..., \lambda_k \in \mathbb{K}$ such that $v_{k+i} = \lambda_1 v_1 + \lambda_2 v_2 + ... + \lambda_k v_k$. This can also be written as $v_{k+i} = \lambda_1 v_1 + \lambda_2 v_2 + ... + \lambda_k v_k + 0 v_{k+1} + ... + 0 v_n$. Also, as $v_{k+i} \in B$, $v_{k+i}$ can be represented as a linear combination of elements of $B$ by taking 1 as the coefficient for $v_{k+i}$ and 0 as the coefficient for all elements in $B$ other than $v_{k+i}$. This is a contradiction to the fact that representation for any element with respect to a basis must be unique.