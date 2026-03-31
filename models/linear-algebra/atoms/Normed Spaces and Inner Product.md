---
sticker: lucide//atom
---
Let $V$ be a vector space over the field $\mathbb{K}$, where $\mathbb{K}$ is either $\mathbb{R}$ or $\mathbb{C}$. Norm is a real-valued function on $V$ ($\lVert \cdot \rVert:V\to \mathbb{R}$) satisfying the following three conditions:

- **N1**: $\lVert v \rVert \geq 0$, and $\lVert v \rVert=0 \iff v=0$.
- **N2**: $\lVert \lambda v \rVert=\lvert \lambda \rvert\lVert v \rVert$
- **N3**: $\lVert u + v \rVert \leq \lVert u \rVert + \lVert v \rVert$

Then $V$ together with a norm defined on it, denoted by $(V, \lVert \cdot \rVert)$ is called *Normed Linear Space*.

---

We can also define subspaces for this new space: Let $(V, \lVert \cdot \rVert)$ be a normed linear space. A subspace of $V$ is a vector subspace $W$ of $V$ with the same norm as that of $V$. The norm on $W$ is said to be induced by the norm on $V$.

- [[THLinAlg-Every Normed Space is a Metric Space]]