---
sticker: lucide//atom
---
# Quotient Space in Topology

The quotient space of a topological space under a given [[../set-theory/Equivalence Relation|Equivalence Relation]] is a new topological space constructed by endowing the [[../../set-theory/Quotient Set]] of the original topological space with the quotient topology, that is, with the [[atoms/Finer and Courser Topologies|finest topology]] that makes continuous the canonical projection map (the function that maps points to their equivalence classes). In other words, a subset of a quotient space is open if and only f its preimage under the canonical projection map is open in the original topological space.

Intuitively speaking, the points of each equivalence class are identified or "glued together" for forming a new topological space.

# Definition

Let $X$ be a topological space, and let $\sim$ be an equivalence relation on $X$. The quotient set $Y =X/\sim$ is the set of equivalence classes of elements of $X$. The equivalence class of $x \in X$ is denoted $[x]$.

The construction of $Y$ defines a canonical surjection $q: X\to Y, x\mapsto [x]$. A quotient space under $\sim$ is the set $Y$ equipped with the quotient topology, whose open sets are those subsets $U \subseteq Y$ whose preimage $q^{-1}(U)$ is open. In other words, $U$ is open in the quotient topology on $X/ \sim$ if and only if:

$$
\{  x \in X : [x] \in U\}
$$
is open in $X$. similarly, a subset $S \subseteq Y$ is closed if and only if $\{ x \in X: [x] \in S \}$ is closed in $X$. 

The quotient topology is the [[Final Topology]]on the quotient set, with respect to the map $x\mapsto [x]$.