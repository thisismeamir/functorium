---
sticker: lucide//atom
---
# Metric Topology

A metric $d:X\times X\to \mathbb{R}$ is a function that satisfies the conditions:
- $d(x,y) = d(y,x)$.
- $d(x,y)\geq 0$ where the equality holds if and only if $x=y$. 
- $d(x,y)+d(y,z) \geq d(x,z)$
for any $x,y,z \in X$. If $X$ is endowed with a metric $d$, $X$ is made into a topological space whose open sets are given by *open discs*,

$$
U_{\epsilon}(X) =\{ y \in X | d(x,y)< \epsilon \}
$$
and all their possible unions. The topology $\mathcal{T}$ thus defined is called the metric topology determined by $d$. The topological space $(X, \mathcal{T})$ is called a metric space.

## Proof

- [[THTop-Metric Space is a Topological Space]]
- [ ] Proof is to be done