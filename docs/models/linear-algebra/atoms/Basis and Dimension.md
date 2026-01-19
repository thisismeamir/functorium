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