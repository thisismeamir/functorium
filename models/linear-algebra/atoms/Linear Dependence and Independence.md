---
sticker: lucide//atom
---

# Linear Combination

Assume we have a vector space $V$ over a field $\mathbb K$. Let $v_1,\dots,v_n\in V$ and $\lambda_1,\dots,\lambda_n\in \mathbb K$. Then the vector:
$$
v = \lambda_1v_1 + \dots+\lambda_nv_n
$$
is called a linear combination of vectors and the scalars $\lambda_i$ are called the coefficients of the linear combination. If all the coefficients are zero, then $v=0$, which is trivial. Now suppose that there exists a non-trivial representation for $0$, that is, there exists scalars $\lambda_i$ not all zero such that a linear combination of the given vectors equals zero.

What it means is that in a sense some vectors work against the others and result in canceling them out. We say that the vectors $v_i$ are ***linearly dependent***. In other words, the vectors $v_i$ are linearly dependent if and only if there exists scalars $\lambda_i$ not all zero such that:
$$
\lambda_1 v_1 + \dots + \lambda_n v_n = 0
$$
This way we can define *linearly independent*. Easily, when they are not dependent.
$$
\text{if} \ \lambda_1v_1 + \dots+\lambda_2v2 = 0, \text{then} \ \lambda_i = 0
$$

for all $i$. Can we find a set of linearly independent vectors? Clearly, any subset of vectors that contain $0$ vector can't be a candidate since $\lambda$ for $0$ can be chosen arbitrarily. And any subset that contains one element (not the zero) is linearly independent.

Another way to think about it is to consider the case that a subset of $V$ is linearly dependent, if and only if, at least on vector in the subset can be written as a linear combination of others. Let this vector be $w$, then obviously choosing $\lambda_w = -1$ would make the equation defined earlier zero, hence the case of all $\lambda_i =0$ for linear independence is not true.

This in terms give us the fact that a subset of a vector space $V$ containing two non-zero vectors is linearly dependent if and only if one vector is a scalar multiple of the other.

Also considering subsets:

Let $V$ be a vector space over a field $\mathbb K$, and let $W_1\subseteq W_2 \subseteq V$. If $W_1$ is linearly dependent, then $W_2$ is linearly dependent as well. And if $W_2$ is linearly independent then $W_1$ is also linearly independent. We can say:

> Any super set of a linearly dependent set is linearly dependent and any subset of a linearly independent set is linearly independent.