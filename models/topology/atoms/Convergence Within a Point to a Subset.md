---
sticker: lucide//atom
---
# Convergence to a Point within a Subset

Let $X$ be a topological space, $A \subseteq X$, and $(x_i)_{i=1}^\infty$ be a sequence of points in $A$ such that the sequence converges to a point $x \in X$. We want to show that $x \in A$.

**Proof:**

Since $(x_i)$ is a sequence in $A$, we have $x_i \in A$ for all $i \in \mathbb{N}$.  By definition of convergence, for every neighborhood $U$ of $x$, there exists an integer $N \in \mathbb{N}$ such that $x_i \in U$ for all $i \geq N$.

Consider the neighborhood $A$ itself. Since $A$ is a subset of $X$, it may or may not be open. However, we don't need to assume anything about whether A is open. We only know that $x_i \in A$ for all i.

Since $(x_i)$ converges to $x$, there exists an integer $N \in \mathbb{N}$ such that $x_i \in A$ for all $i \geq N$.  This implies that $x_N, x_{N+1}, x_{N+2}, ...$ are all elements of $A$.

Now, consider the neighborhood $A$ itself. Since $(x_i)$ converges to $x$, there exists an integer $N$ such that $x_i \in A$ for all $i \geq N$.  This means that $x_N \in A$. Because $x_i$ is a sequence converging to x, we know that the limit point x must be in any neighborhood of x. Therefore, since $A$ is a neighborhood of $x$, it follows that $x \in A$.

**Alternative Proof (using closure):**

We know that if a sequence $(a_i)$ converges to a point $x$, then $x$ belongs to the closure of the set containing the sequence. In this case, the sequence is in $A$, so we have $x \in \overline{A}$. Since $A \subseteq X$, it follows that $x \in A$.

**Conclusion:**

If a sequence $(x_i)$ in a subset $A$ of a topological space $X$ converges to a point $x \in X$, then $x \in A$.