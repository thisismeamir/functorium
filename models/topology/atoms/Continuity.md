---
sticker: lucide//atom
---
# Continuity of Maps: Open vs. Closed Preimages

Let $X$ and $Y$ be topological spaces, and let $f: X \rightarrow Y$ be a map.

**Definition (via open sets):**  The map $f$ is continuous if for every open subset $U \subseteq Y$, its preimage $f^{-1}(U)$ is open in $X$. Here, $f^{-1}(U) = \{x \in X : f(x) \in U\}$.

**Definition (via closed sets):** The map $f$ is continuous if and only if the preimage of every closed subset is closed.  That is, for every closed set $C \subseteq Y$, its preimage $f^{-1}(C)$ is closed in $X$. Here, $f^{-1}(C) = \{x \in X : f(x) \in C\}$.

Let $X$, $Y$, and $Z$ be topological spaces.

- Every constant map $f: X\rightarrow Y$ is continuous.
- The identity map $\text{Id}_X: X\rightarrow X$ is continuous.
- If $f:X\rightarrow Y$ is continuous, so is the restriction of $f$ to any open subset of $X$.
- If $f: X\rightarrow Y$ and $g: Y\rightarrow Z$ are both continuous, then so is their composition $g \circ f:X\rightarrow Z$.

- [ ] TODO: Proving these above
## Local Criterion for Continuity

![[../../../attachments/Pasted image 20260118160821.png]]

Let $f: X \rightarrow Y$ be a map between topological spaces.

**Proposition:** A map $f: X \rightarrow Y$ is continuous if and only if for each point $x \in X$, there exists a neighborhood $V_x$ of $x$ such that the restriction of $f$ to $V_x$, denoted $f|_{V_x}$, is continuous.

**Implication 1 (If $f$ is continuous, then locally continuous):** If $f$ is continuous, we can simply choose each neighborhood $V_x$ to be $X$ itself.  Then $f|_{V_x} = f|_X = f$, and since $f$ is continuous, it is also continuous on $X$.

**Implication 2 (If locally continuous, then $f$ is continuous):** Suppose $f$ is continuous in a neighborhood of each point. Let $U \subseteq Y$ be any open subset; we must show that $f^{-1}(U)$ is open in $X$.  Let $x \in f^{-1}(U)$. Then $f(x) \in U$, and by the assumption, there exists a neighborhood $V_x$ of $x$ such that $f|_{V_x}$ is continuous.

Since $f|_{V_x}$ is continuous, $(f|_{V_x})^{-1}(U)$ is open in $V_x$.  We have:

$$
(f|_{V_x})^{-1}(U) = \{ x \in V_x : f(x) \in U\} = f^{-1}(U) \cap V_x
$$

Therefore, $(f|_{V_x})^{-1}(U)$ is a neighborhood of $x$ contained in $f^{-1}(U)$.  This implies that $f^{-1}(U)$ is open in $X$.

The continuity of a map can be characterized by its local behavior; it suffices to check continuity on neighborhoods around each point.