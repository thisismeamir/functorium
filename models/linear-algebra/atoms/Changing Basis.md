---
sticker: lucide//atom
---
There are infinitely possible ways to define a set of basis for a vector space. The coordinate representation and the matrix representation depends on the basis that we chose to span the space with. It is important to be able to define relations between these different bases. Since after all the so-called *representations* are *representing* the same thing.

**Theorem**
Let $V$ be a finite-dimensional vector space over the field $\mathbb{K}$ with ordered bases $B_{1}$ and $B_{2}$, and let $P = [I_{V}]^{B_{2}}_{B_{1}}$ where $I_{V}$ is the identity transformation on $V$. Then

- $P$ is invertible
- For any $v \in V$, $[v]_{B_{2}}= P[v]_{B_{1}}$
- If $T$ is a linear operator on $V$, then $[T]_{B_{2}}= P^{-1}[T]_{B_{1}}P.$
$P$ is called the change of coordinate matrix as $P$ changes $B_{1}$ coordinates into $B_{2}$ coordinates and $P^{-1}$ changes $B_{2}$ coordinates into $B_{1}$ coordinates.

**Proof**
- Since $I_{V}$ is invertible, by theorems in [[../Isomorphism of Vector Spaces|Isomorphism of Vector Spaces]] $P$ is invertible.
- For any $v \in V$,
  $$
[v]_{B_{2}} = [I_{V}(v)]_{B_{2}}=[I_{V}]_{B_{1}}^{B_{2}}[v]_{B_{1}} = P[v]_{B_{1}}
$$
- Since $I_{V}T=T=TI_{V}$, by the composition laws of matrices and [[Algebra of Linear Transformations|Algebra of Linear Transformations]]  we have
  $$
P[T]_{B_{1}} = [I_{V}]_{B_{1}}^{B_{2}}[T]_{B_{1}}^{B_{2}} = [I_{V}T]_{B_{1}}^{B_{2}} = [TI_{V}]_{B_{1}}^{B_{2}} = [T]_{B_{2}}^{B_{2}}[I_{V}]_{B_{1}}^{B_{2}} = [T]_{B_{2}}P
$$
