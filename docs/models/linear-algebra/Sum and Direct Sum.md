# Sum

The union of two subspaces, need not to be a subspace itself. Therefore, analogous to union of subsets in set theory, we define a new concept called the sum of subspaces and analogous to disjoint union of subsets we introduce direct sums.

Let $W_1,\dots,W_n$ be subspaces of a vector space over a field $\mathbb K$, then their sum $W_1 + \dots+W_n = \{w_1 + \dots + w_n | w_i \in W_i\}$ is a subspace of $V$ and it is the smallest subspace of $V$ containing $W_i$s.

This is since $W_i$s are subspaces of $V$, $0\in W_i$ for all of them. Then 

$$
0 = 0+0+\dots+0\in W_1 + \dots+W_n
$$

Now let $v,w\in W_1 + \dots+W_n$ and $\lambda \in \mathbb K$, then $v = v_1+\dots+v_n$ and $w=w_1+\dots+w_n$ where $v_i,w_i\in W_i$ As each $W_i$ is a subspace of $V$, $v_i+w_i\in W_i$ and $\lambda v_i\in W_i$ Hence:

$$
v+w = \sum_{i=1}^n (v_i+w_i)\in W_1+\dots+W_n
$$
and 

$$
\lambda v = \sum_{i=1}^n\lambda v_i \in W_1 + \dots+W_n
$$
Therefore $W_1 + \dots+W_n$ is a subspace of $V$. Since $w_i\in W_i$ can be written as $w_i = 0 + \dots + 0 + w_i + 0 +\dots +0 \in W_1 + \dots+W_n$, $W_1 + \dots+W_n$ contains each $W_i$.

- [ ] Prove that this is the smallest subset.

# Direct Sum

Let $V$ be a vector space over a field $\mathbb K$ and $W_1,W_2,\dots,W_n$ are subspaces of $V$. If every element in $V$ can be uniquely represented as a sum of elements in $W_1, W_2,\dots,W_n$, then $V$ is called the direct sum of $W_1,W_2,\dots,W_n$ and is denoted as $V = W_1\oplus \dots\oplus W_m$.

- [ ] Read the theorems of *A Course in Linear Algebra and write and prove them here*.

