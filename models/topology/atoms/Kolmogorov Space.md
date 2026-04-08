---
sticker: lucide//atom
---
# Kolmogorov Space

In topology and related branches of mathematics, a topological space $X$ is a $\mathrm{T}_{0}$ **Kolmogorov space** (named after Andrey Kolmogorov) if for every pair of distinct point of $X$, at least one of them has a neighborhood not containing the other. In a $\mathrm{T}_{0}$ space, all points are [[Topologically Distinguishable]].

This condition, called the $\mathrm{T}_{0}$ condition, is the weakest of the separation axioms. Nearly all topological spaces normally studied in mathematics are $\mathrm{T}_{0}$ spaces.

# Definition

A $\mathrm{T}_{0}$ space is a topological space in which every pair of distinct points is topologically distinguishable. That is, for any two different points $x$ and $y$ there is an open set that contains one of these points and not the other. More precisely the topological space $X$ is Kolmogorov $\mathrm{T}_{0}$ if and only if:

$$
\forall a,b \in X \land a \neq b, \exists O \in \mathcal{T} : ((a \in O)\land (b \not\in O)) \lor ((a \not\in O) \land (b \in O)) 
$$
Note that topologically indistinguishable points are automatically distinct. On the other hand, if the singleton sets $\{ x \}$ and $\{ y \}$ are separated then the points $x$ and $y$ must be topologically distinct.


$$
\text{separated} \implies \text{topologically distinguishable} \implies \text{distinct}
$$
The property of being topologically distinguishable is, in general, stronger than being distinct but weaker than being separated. In a $\mathrm{T}_{0}$ space, the second arrow above also reverses; points are distinct if and only if they are distinguishable. This is how the $\mathrm{T}_{0}$ axiom fits in with the rest of the separation axioms.

# Examples
## Spaces that are not $\mathrm{T}_{0}$

- Trivial topologies on sets with more than one element are not $\mathrm{T}_{0}$
## Spaces that are $\mathrm{T}_{0}$ but not $\mathrm{T}_{1}$

- The [Zariski topology] on $\text{Spec}(R)$, the [prime spectrum] of a [commutative ring] $R$, is always $\mathrm{T}_{0}$ but generally not $\mathrm{T}_{1}$. The non-closed points correspond to [prime ideals] which are not [maximal]. They are important to the understanding of [schemes].
- The [particular point topology] on any set with at least two elements is $\mathrm{T}_{0}$ but not $\mathrm{T}_{1}$ since the particular point is not closed (its closure is the whole space). An important special case is the [Sierpiński space] which is the particular point topology on the set $\{ 0,1 \}$.
- The [excluded point topology] on any set with at least two elements is $\mathrm{T}_{0}$ but not $\mathrm{T}_{1}$. The only closed point is the excluded point.
- The [Alexandrov topology] on a [partially ordered set] is $\mathrm{T}_{0}$ but will not be $\mathrm{T}_{1}$ unless the order is discrete (agrees with equality). Every finite $\mathrm{T}_{0}$ space is of this type. This also includes the particular point and excluded point topologies as special cases.
- The [right order topology] on a [totally ordered set] is a related example.
- The [overlapping interval topology] is similar to the particular point topology since every non-empty open set includes $0$.
- Quite generally, a topological space $X$ will be $\mathrm{T}_{0}$ if and only if the specialization preorder on _X_ is a [partial order]. However, $X$$ will be $\mathrm{T}_{1}$ if and only if the order is discrete (i.e. agrees with equality). So a space will be $\mathrm{T}_{0}$ but not $\mathrm{T}_{1}$ if and only if the specialization preorder on $X$ is a non-discrete partial order.