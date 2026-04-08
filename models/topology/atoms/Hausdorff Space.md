---
sticker: lucide//atom
---
# Hausdorff Spaces

The definition of topological spaces is wonderfully flexible, and can be used to describe a rich assortment of concepts of "space". However, without further qualification, arbitrary topological spaces are far too general for most purposes, because they include some spaces whose behavior contradicts many of our basic spatial intuitions.

The problem with these spaces is that there are too few open subsets, so neighborhoods do not have the same intuitive meaning they have in metric spaces. 

A Topological space $X$ is said to be a *Hausdorff space* if given any pair of distinct points $p_{1},p_{2}\in X$, there exist neighborhoods $U_{1}$ of $p_{1}$ and $U_{2}$ of $p_{2}$ with $U_{1} \cap U_{2} = \emptyset$. 

> *Points can be separated by open subsets*

---

## Examples
![[../../../attachments/Pasted image 20260309224034.png]]![[../../../attachments/Pasted image 20260309224048.png]]

[[atoms/Non-Hausdorff Spaces]]

Because every metric space is Hausdorff, it follows that these spaces are not metrizable. 

**Proposition**
Let $X$ be a Hausdorff space.
- Every finite subset of $X$ is closed.
- If a sequence $(p_{i})$ in $X$ converges to a limit $p \in X$, the limit is unique.

# Definition

Points $x$ and $y$ in a topological space $X$ can be separated by neighborhoods if there exists a neighborhood $U$ of $x$ and a neighborhood $V$ of $y$ such that $U$ and $V$ are disjoint ($V \cap U = \emptyset$). $X$ is a Hausdorff space if any two distinct points in $X$ are separated by neighborhoods. This condition is the third separation axiom, which is why Hausdorff spaces are called $\mathrm{T}_{2}$ spaces. The name separated space is also used for them.

A related by weaker notion is that of a preregular space. $X$ is a preregular space if any two topologically distinguishable points can be separated by disjoint neighborhoods. Preregular space is also called and $\mathrm{R}_{1}$ space.

The relationship between these two conditions is as follows. A topological space is Hausdorff if and only if it is both preregular and Kolmogorov. Meaning, topologically distinguishable points are separated by neighborhoods and distinct points are topologically distinguishable. A topological space is preregular if and only if its [[../Kolmogorov Quotient|Kolmogorov Quotient]] is Hausdorff.
# Properties

For a topological space $X$, the following are equivalent.
- $X$ is a Hausdorff space.
- Limits of [[Nets]]in $X$ are unique.
- Limits of [[Filters]]on $X$ are unique.
- A singleton set $\{ x \}\subset X$ is equal to the intersection of all closed neighborhoods of $x$. A closed neighborhood of $x$ is a closed set that contains an open set containing $x$.)
- The diagonal $\Delta=\{ (x,x)| x \in X \}$ is closed as a subset of the product space $X \times X$.
- Any injection from the discrete space with two points to $X$ has a [[Lifting Property]] with respect to the map from the finite topological space with two open points and one closed point to a single point. ==what?==

Subspaces and products of Hausdorff spaces are Hausdorff, but [[../Quotient Space (Topology)|Quotient Space (Topology)]] of Hausdorff spaces need not to be Hausdorff. In fact, every topological space can be realized as the quotient of some Hausdorff space.

Hausdorff spaces are [[../ Fréchet Space|Fréchet Space]] as well, meaning each singleton is a closed set. Similarly, preregular spaces are $\mathrm{R}_{0}$. Every Hausdorff space is a [[Sober Space]] although the converse is in general not true.

Another property of Hausdorff spaces is that each compact set ([[Compactness]]) is a closed set. For non-Hausdorff spaces, it can be that each compact set is a closed set or not.

The definition of Hausdorff spaces says that points can be separated by neighborhoods. It turns out that this implies something which is seemingly stronger: 

> *in a Hausdorff space every pair of disjoint compact sets can also be separated by neighborhoods, in other words there is a neighborhood of one set and a neighborhood of the other, such that the two neighborhoods are disjoint. This is an example of the general rule that compact sets often behave like points.*

Compactness condition together with preregularity often imply stronger separation axioms. For example, any [[Locally Compact]] preregular space is [[Completely Regular]]. Compact preregular spaces are normal, meaning that they satisfy [[Urysohns Lemma]]and the [[Tietze Extension Theorem]] and have partitions of unity subordinate to locally finite open covers. The Hausdorff versions of these statements are: Every locally compact Hausdorff space is [[../Tychonoff Space]], and every Compact Hausdorff space is [[../Normal Hausdorff Space]].

## Maps in Hausdorff

Let $f:X\to Y$ be a function and let $\ker(f)\triangleq \{ (x,x') |f(x)=f(x') \}$ be its kernel regarded as a subspace of $X \times X$.

- If $f$ is continuous and $Y$ is Hausdorff then $\ker(f)$ is a closed set.
- If $f$ is open surjection and $\ker(f)$ is a closed set then $Y$ is Hausdorff.
- If $f$ is a continuous, open surjection then $Y$ is Hausdorff if and only if $\ker(f)$ is a closed set.

If $f,g:X\to Y$ are continuous maps and $Y$ is a Hausdorff space then the equalizer $\mathrm{eq}(f,g)=\{ x | f(x) = g(x) \}$ is a closed set in $X$.  It follows that if $Y$ is Hausdorff and $f$ and $g$ agree on a dense subset of $X$ then $f=g$. In other words, continuous functions into Hausdorff spaces are determined by their values on dense subsets.

Let $f:X\to Y$ be a closed surjection such that $f^{-1}(y)$ is compact for all $y \in Y$. Then $X$ is Hausdorff so is $Y$.

Let $f:X\to Y$ be a quotient map with $X$ a compact Hausdorff space. The the following are equivalent:
- $Y$ is Hausdorff.
- $f$ is a closed map.
- $\ker(f)$ is a closed set.
# More Discussion

A $\mathrm{T}_{2}$ space or separated space or Hausdorff space, is a topological space where distinct points have disjoint neighborhoods. Of the many separation axioms that can be imposed on a topological space, the "Hausdorff condition" is the most frequently used and discussed. It implies the uniqueness of limits, sequences, nets and filters.


Hausdorff spaces are named after one of the founders of topology Felix Hausdorff. In his original definition of a topological space he included the Hausdorff condition as an axiom.

