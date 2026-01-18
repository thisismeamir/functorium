---
sticker: lucide//atom
---
# Equivalence of Convergence Definitions: Metric Spaces

Let $(X, d)$ be a metric space, where $d: X \times X \to [0, \infty)$ is a distance function satisfying the usual properties (non-negativity, identity of indiscernibles, symmetry, and triangle inequality). Let $(x_i)_{i=1}^\infty$ be a sequence in $X$, and let $x \in X$. We will show that the topological definition of convergence (using neighborhoods) is equivalent to the metric space definition of convergence.

**1. Topological Definition:**  A sequence $(x_i)$ converges to $x$ if for every neighborhood $U$ of $x$, there exists an integer $N \in \mathbb{N}$ such that $x_i \in U$ for all $i \geq N$.

**2. Metric Space Definition:** A sequence $(x_i)$ converges to $x$ if for every $\epsilon > 0$, there exists an integer $N \in \mathbb{N}$ such that $d(x_i, x) < \epsilon$ for all $i \geq N$.

**Proof of Equivalence:**

**(a) Topological Definition implies Metric Space Definition:**

Assume the topological definition holds.  We want to show that the metric space definition also holds. Let $\epsilon > 0$ be given. Consider the neighborhood $U = \{x \in X : d(x, x) < \epsilon\}$. This is an open ball centered at $x$ with radius $\epsilon$, and thus a neighborhood of $x$.

By the topological definition, there exists an integer $N \in \mathbb{N}$ such that $x_i \in U$ for all $i \geq N$.  Since $U = \{y \in X : d(y, x) < \epsilon\}$, this implies that $d(x_i, x) < \epsilon$ for all $i \geq N$. Therefore, the metric space definition holds.

**(b) Metric Space Definition implies Topological Definition:**

Assume the metric space definition holds. We want to show that the topological definition also holds. Let $U$ be an arbitrary neighborhood of $x$.  We need to find an integer $N \in \mathbb{N}$ such that $x_i \in U$ for all $i \geq N$.

For each $\epsilon > 0$, let $U_\epsilon = \{y \in X : d(y, x) < \epsilon\}$.  Then $U_\epsilon$ is a neighborhood of $x$. Since the metric space definition holds, there exists an integer $N_\epsilon \in \mathbb{N}$ such that $d(x_i, x) < \epsilon$ for all $i \geq N_\epsilon$. This means $x_i \in U_\epsilon$ for all $i \geq N_\epsilon$.

Now, since $U$ is a neighborhood of $x$, there exists some $\epsilon > 0$ such that $U_\epsilon = \{y \in X : d(y, x) < \epsilon\} \subseteq U$.  Let $N = N_\epsilon$. Then for all $i \geq N$, we have $d(x_i, x) < \epsilon$, which implies $x_i \in U_\epsilon \subseteq U$. Therefore, $x_i \in U$ for all $i \geq N$.  Thus, the topological definition holds.

We have shown that under the assumption of a metric space, the topological definition of convergence is equivalent to the metric space definition of convergence. This demonstrates how topology generalizes and abstracts fundamental concepts from analysis while retaining their essential properties.