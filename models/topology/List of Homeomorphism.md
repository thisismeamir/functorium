---
sticker: lucide//list-tree
---
# Examples for Homeomorphism

---
Example 1: Any open ball in $\mathbb{R}^{n}$ is homeomorphic to any other open ball; the homeomorphism can easily be constructed as a composition of translations $x\mapsto x+x_{0}$ and dilations $x \mapsto cx$. Similarly, all spheres in $\mathbb{R}^{n}$ are homeomorphic to each other. These examples illustrate that "size" is not a topological property.

---
Example 2: Let $\mathbb{B}^{n} \subseteq \mathbb{R}^{n}$ be the unit ball, and define a map, $F: \mathbb{B}^{n} \to \mathbb{R}^{n}$ by

$$
F(x) = \frac{x}{1-|x|}.
$$
Direct computation shows that the map $G: \mathbb{R}^{n}\to \mathbb{B}^{n}$ defined by:

$$
G(y) = \frac{y}{1+|y|},
$$
is an inverse for $F$. Thus $F$ is bijective, and since $F$ and $F^{-1}=G$ are both continuous, $F$ is a homemorphism. It follows that $\mathbb{R}^{n}$ is homeomorphic to $\mathbb{B}^{n}$, and thus "boundedness" is not a topological property. 

---

Example 3: Show that the map $\varphi: C \to \mathbb{S}^{2}$ is a homeomorphism by showing that its inverse can be written as below

$$
\varphi^{-1}(x,y,z) = \frac{(x,y,z)}{\max\{|x|,|y|,|z|\}}
$$
