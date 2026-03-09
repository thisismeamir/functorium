---
sticker: lucide//atom
---
# Convergence in Discrete Topological Spaces: Eventually Constant Sequences

Let $X$ be a discrete topological space. This means every subset of $X$ is open. Let $(x_i)_{i=1}^\infty$ be a sequence in $X$, and let $x \in X$. We want to show that the only sequences that converge to $x$ are those that are eventually constant, i.e., there exists an integer $N$ such that $x_i = x$ for all $i \geq N$.

**Proof:**

Assume $(x_i)$ converges to $x$ in the discrete topological space. This means by definition of convergence (using neighborhoods), that for every neighborhood $U$ of $x$, there exists an integer $N \in \mathbb{N}$ such that $x_i \in U$ for all $i \geq N$.

Since $X$ is a discrete space, $\{x\}$ is open. Therefore, it serves as a neighborhood of $x$.  By the definition of convergence, there exists an integer $N \in \mathbb{N}$ such that $x_i \in \{x\}$ for all $i \geq N$.

Since $\{x\}$ contains only the element $x$, this implies that $x_i = x$ for all $i \geq N$.  Therefore, the sequence $(x_i)$ is eventually constant.

**Conversely:**

Suppose the sequence $(x_i)$ is eventually constant, meaning there exists an integer $N$ such that $x_i = x$ for all $i \geq N$. We need to show that this implies convergence to $x$.

Let $U$ be any neighborhood of $x$. Since $X$ is discrete, every subset of $X$ is open, so $\{x\} \subseteq U$. Thus, if $i \geq N$, then $x_i = x \in \{x\} \subseteq U$. Therefore, for every neighborhood $U$ of $x$, there exists an integer $N$ such that $x_i \in U$ for all $i \geq N$. This satisfies the definition of convergence.

**Conclusion:**

In a discrete topological space, a sequence converges to $x$ if and only if it is eventually constant.