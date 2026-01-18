---
sticker: lucide//atom
---
# Topology on the Unit Ball in $\mathbb{R}^n$

Let $n$ be a nonnegative integer. The open unit ball of dimension *n* is defined as:

$$ \mathbb{B}^n = \{x \in \mathbb{R}^n : |x| < 1\} $$

where $|x|$ denotes the Euclidean norm (length) of the vector $x$. We will show that $\mathbb{B}^n$ with the topology inherited from $\mathbb{R}^n$ is a topology.

1.  **The empty set and $\mathbb{B}^n$ are open:**
    *   $\emptyset \subseteq \mathbb{B}^n$, and in $\mathbb{R}^n$, the empty set is always open.
    *   $\mathbb{B}^n \subseteq \mathbb{B}^n$, and in $\mathbb{R}^n$, every set is open (in the discrete topology).

2.  **The intersection of any finite number of open sets in $\mathbb{B}^n$ is open:**
    Let $\{U_1, U_2, ..., U_k\}$ be a finite collection of open sets in $\mathbb{B}^n$. Since each $U_i$ is open in $\mathbb{R}^n$, their intersection $U_1 \cap U_2 \cap ... \cap U_k$ is also open in $\mathbb{R}^n$. Furthermore, since $U_i \subseteq \mathbb{B}^n$ for all *i*, we have $U_1 \cap U_2 \cap ... \cap U_k \subseteq \mathbb{B}^n$. Therefore, the intersection is an open set in $\mathbb{B}^n$.

3.  **The union of any collection of open sets in $\mathbb{B}^n$ is open:**
    Let $\{U_\alpha\}$ be a collection of open sets in $\mathbb{B}^n$. Since each $U_\alpha$ is open in $\mathbb{R}^n$, their union $\bigcup_{\alpha} U_\alpha$ is also open in $\mathbb{R}^n$. Furthermore, since $U_\alpha \subseteq \mathbb{B}^n$ for all $\alpha$, we have $\bigcup_{\alpha} U_\alpha \subseteq \mathbb{B}^n$. Therefore, the union is an open set in $\mathbb{B}^n$.

Since all three axioms are satisfied, $\mathbb{B}^n$ with the topology inherited from $\mathbb{R}^n$ forms a topology.  When $n = 2$, this is often referred to as the open unit disk.