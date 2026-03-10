---
sticker: lucide//atom
---

# Open Set

A set $O$ within a topological space $(X,\tau)$ is considered open if it is a subset of $X$ and contains its every point in a neighborhood contained entirely within $X$. Formally:

$$ O \subseteq X $$

and for every $x \in O$, there exists an open neighborhood $N$ such that $x \in N \subseteq O$.

Equivalently, a set $O$ is open if it can be expressed as the union of open sets in $\tau$. That is:

$$ O = \bigcup_{i \in I} U_i $$

where each $U_i \in τ$.

In $\mathbb{R}$ with the standard Euclidean topology, an open set is a set where for every point in the set, there exists an interval $(a, b)$ such that $x \in (a, b) \subseteq O$.  For example, $(0, 1)$ is an open set.

A set is closed if its complement is open.

# The Main Idea

The main idea behind defining the notion of open sets is the [[Open Subset Criterion for Continuity|open subset criterion for continuity]]. It shows that continuous functions between metric spaces can be detected knowing only the open subsets of both spaces. This observation is motivating, thus, we make the following definition:

If $X$ is a set, *a topology on $X$* is a collection $\mathcal T$ of subsets of $X$ satisfying the following properties:

1. $X$ and $\emptyset$ are elements of $\mathcal T$.
2. $\mathcal T$ is closed under the finite intersections: if $U_1,\dots,U_n$ are elements of $\mathcal T$, then their intersection $U_1\cap\dots\cap U_n$ is an elements of $\mathcal T$.
3. $\mathcal T$ is closed under arbitrary unions: if $(U_\alpha)_{\alpha\in A}$ is any (finite or infinite) family of elements of $\mathcal T$, their union $\large\cup_{\alpha\in A} U_\alpha$ is an element of $\mathcal T$.

A pair $(X,\mathcal T)$ consisting of a set $X$ together with a topology $\mathcal T$ is called a *topological space*. Once $X$ is endowed with a specific topology, the elements of $X$ are usually called its **points**, and the sets that make up the topology are called the *open sets of $X$*. 

Notion of open subsets gives us a qualitative measure of *nearness*, as opposed to quantitative metric space definition.

If $X$ is a topological space (omitting the $\mathcal T$ for simpler terminology, nothing has changed) and $p\in X$, a **neighborhood of $p$** is just any open subset of $X$ containing $p$. More generally, if $K\subseteq X$, a *neighborhood of the subset $K$* is an open subset containing $K$.

[[../List of Topologies]]

# Properties

Here we mention some brief properties that a topology can have:

1. A subset $A$ of a topological space $X$ is said to be dense in $X$ if $\bar A = X$, for notation and definitions you can look up [[Closure, Interior, Exterior and Boundary]]
