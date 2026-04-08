---
aliases:
  - Fréchet Space
sticker: lucide//atom
---
# Intuition

A $\mathrm{T}_{1}$ space or a frechet space is a topological space in which, for every pair of distinct points, each has a neighborhood not containing the other point. An $\mathrm{R}_{0}$ space is one in which this holds for every pair of topologically distinguishable points.

Intuitively here we separate things up to a distance between them, in $\mathrm{T}_{0}$ we separated things up to them being distinguishable from one another. This one seems more separated than the latter.

# Definition

Let $X$ be a topological space and let $x$ and $y$ be any distinguishable points in $X$. We say that $x$ and $y$ are separated if each lies in a neighborhood that does not contain the other point.
- $X$ is called $\mathrm{T}_{1}$ space if any two distinct points in $X$ are separated.
- $X$ is called $\mathrm{R}_{0}$ space is any two topologically distinguishable points in $X$ are separated.
A $\mathrm{T}_{1}$ space is also called an **accessible space** or a pace with **Fréchet topology** and an $\mathrm{R}_{0}$ is also called a symmetric space. 

A topological space is a $\mathrm{T}_{1}$ space if and only if it is both an $\mathrm{R}_{0}$ space and a [[Kolmogorov Space]] (a space in which distinct points are topologically distinguishable). a topological space is $\mathrm{R}_{0}$ if and only if its [[Kolmogorov Quotient]] is a $\mathrm{T}_{1}$ space.
# Properties

If $X$ is a topological space then the following conditions are equivalent:
- $X$ is a $\mathrm{T}_{1}$ space.
- $X$ is a $\mathrm{T}_{0}$ space and an $\mathrm{R}_{0}$ space.
- Points are closed in $X$; that is, for every point $x \in X$, the singleton set $\{ x \}$ is a closed subset of $X$.
- Every subset of $X$ is the intersection of all the open sets containing it. ==what does this mean?==
- Every finite set is closed. (A finite set is simple one that contains finite number of elements)
- Every cofinite set of $X$ is open (cofinite subset is a subset of $X$ whose complement in $X$ is finite set.)
- For every $x \in X$, the [[Fixed Ultrafilter]] at $x$ converges only to $x$.
- For every subset $S$ of $X$ and every point $x \in X$, $x$ is a limit point of $S$ if and only if every open neighborhood of $x$ contains infinitely many points of $S$.
- Each map from the  [[Sierpiński space]] to $X$ is trivial.
- The map from [[Sierpiński space]] to the single point has the [[Lifting Property]] with respect to the map from $X$ to the single point.

If $X$ is a topological space then the following conditions are equivalent (where $\mathrm{cl}\{ x \}$ denotes the closure of $\{ x \}$)
- $X$ is an $\mathrm{R}_{0}$ space.
- Given any $x \in X$, the closure of $\{ x \}$ contains only the points that are topologically indistinguishable from $x$.
- The [[Kolmogorov Quotient]] of $X$ is $\mathrm{T}_{1}$.
- for any $x,y \in X$ $x$ is in the closure of $\{ y \}$ if and only if $y$ is in the closure of $\{ x \}$.
- The specialization preorder on $X$ is symmetric (and therefore and [[../set-theory/Equivalence Relation|Equivalence Relation]]).
- The sets $\mathrm{cl}\{ x \}$ for $x \in X$ form a partition of $X$ (that is, any two such sets are either identical or disjoint).
- If $F$ is a closed set and $x$ is a point not in $F$, then $F \cap \mathrm{cl}\{ x \} \neq \emptyset$.
- Every [[Neighbourhoods]]of a point $x \in X$ contains $\mathrm{cl}\{ x\}$.
- Every open set is a union of closed sets
- For every $x \in X$, the [[Fixed Ultrafilter]]at $x$ converges only to the points that are topologically distinguishable from $x$.

In any topological space we have, as properties of any two points the following implications:

$$
\text{separated} \implies \text{toplogically distinguishable} \implies \text{distinct}
$$
If the first arrow can be reversed the space is $\mathrm{R}_{0}$. If the second arrow can be reversed the space is $\mathrm{T}_{0}$. If the composite arrow (both of them) can be reversed the space is $\mathrm{T}_{1}$. A space is $\mathrm{T}_{1}$ if and only if it is both $\mathrm{R}_{0}$ and $\mathrm{T}_{0}$.

A finite $\mathrm{T}_{1}$ space is necessarily a discrete space (since every set is closed).

A space that is locally $\mathrm{T}_{1}$, in the sense that each point has a $\mathrm{T}_{1}$ neighborhood (when given the subspace topology), is also $\mathrm{T}_{1}$. Similarly, a space is locally $\mathrm{R}_{0}$ is also $\mathrm{R}_{0}$. In contrast, the coresponding statement does not hold for $\mathrm{T}_{2}$ spaces. For example the line with two origins is not a Hausdorff space but is locally Hausdorff.