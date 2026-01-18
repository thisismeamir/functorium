---
sticker: lucide//atom
---
# Topology on the Unit Interval

Let $I$ be the unit interval in $\mathbb{R}$, defined as $I = [0, 1] = \{x \in \mathbb{R} : 0 \le x \le 1\}$.  To show that $I$ with the standard topology inherited from $\mathbb{R}$ is a topology, we must verify that it satisfies the three axioms of a topology:

1.  **The empty set and *I* are open:**
    *   $\emptyset \subseteq I$, and in $\mathbb{R}$, the empty set is always open.
    *   $I \subseteq I$, and in $\mathbb{R}$, every set is open (in the discrete topology).

2.  **The intersection of any finite number of open sets in *I* is open:**
    Let $\{U_1, U_2, ..., U_n\}$ be a finite collection of open sets in $I$. Since each $U_i$ is open in $\mathbb{R}$, their intersection $U_1 \cap U_2 \cap ... \cap U_n$ is also open in $\mathbb{R}$.  Furthermore, since $U_i \subseteq I$ for all *i*, we have $U_1 \cap U_2 \cap ... \cap U_n \subseteq I$. Therefore, the intersection is an open set in *I*.

3.  **The union of any collection of open sets in *I* is open:**
    Let $\{U_\alpha\}$ be a collection of open sets in $I$. Since each $U_\alpha$ is open in $\mathbb{R}$, their union $\bigcup_{\alpha} U_\alpha$ is also open in $\mathbb{R}$.  Furthermore, since $U_\alpha \subseteq I$ for all $\alpha$, we have $\bigcup_{\alpha} U_\alpha \subseteq I$. Therefore, the union is an open set in *I*.

Since all three axioms are satisfied, $I = [0, 1]$ with the standard topology inherited from $\mathbb{R}$ forms a topology.