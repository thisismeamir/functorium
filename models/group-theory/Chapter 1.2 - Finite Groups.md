# Finite Groups
---
**Table of Content**
```toc
    style: number
    min_depth: 1
    max_depth: 6
```
---
## Permutation groups and Caley's theorem.
A theorem due to Cayley states that any finite group $G$ with $n$ elements is isomorphic (that is, identical) to a subgroup of $S_n$. 
*proof*
$$ G = \{g_1,g_2,g_3,...,g_n\} \Rightarrow \{g_ig_1,...g_ig_n\} $$
this multiplication (because the group is closed with it's multiplication) is causing amount of permutation, now because of *once and only once rule*  $g_iG$ is again the group $G$ but with a permutation which means that it is isomorphic to $S_n$ subgroup.

## Cycles and Transpositions
> As is often the case in mathematics and physics, a good notation is half the battle.

The permutation $(a_1a_2a_3...a_k)$ is known as a cycle of length $k$ and cyclically permutes $a_1\rightarrow a_2\rightarrow a_3\rightarrow \dots\rightarrow a_k\rightarrow a_1$; A cycle of length 2 is called a Transposition, more informally and exchange.
Any permutation $P$ can be written as a combination of cycles of various lengths, including cycles with length 1 (which means that one object is not being changed in permutation.). with none of the cycles containing any number in common. *This is sometimes called as resolving $P$ into cycles.* 

## Rules of Multiplying Permutations
Theorem: Any permutation can be written as a product of 2-cycles, that is, exchanges or transpositions.

> This merely expresses the everyday intuition that a permutation can be performed in steps, exchanging two objects at a time. In some sense, exchanges are the “atoms” out of which permutations are built.

1. If two 2-cycles do not have a "number" in common, for example, $(12)$ and $(45)$, they commute and we have nothing more to say

2. $(12)(23 = (123)$. (This was already shown earlier, if we simply rename the numbers; we had $(14)(42) = (142)$. Note that since $(32) = (23)$, we can adopt the convention, when multiplying two 2-cycles, to match the head of one 2-cycle to the tail of the other 2-cycle.

3. We need hardly to mention that $(12)(21) = I$.

4. $(12)(23)(34)=(12)(234) = \begin{pmatrix}1&2&3&4 \\ 1&3&4&2\\ 2&3&4&1\end{pmatrix}$
5. $(123)(345)=(12)(23)(34)(45)=(12)(234)(45)=(12345)$ And so it goes for bigger cycles.

Indeed, we now see in hindsight that the preceding theorem is trivial. Since any permutation can be decomposed into 2-cycles, these rules allow us to multiply permutations together.

## Square Root of the Identity
The theory of finite groups is a rich subject with many neat theorems. You have already seen Lagrange’s theorem. Here is another theorem for you to cut your teeth on. Many of us were astonished to learn in school that there is another number besides $1$ that would square to $1$, namely, $−1$. Is there an analogous phenomenon for groups? 
*Theorem: Let G be a group of even order, that is, $G$ has an **even number** of elements. There exists at least one element $g$, which is not the identity $I$, that also squares to the identity $g^2 = I$.*

## Equivalence Classes
Given a group G, distinct group elements are of course not the same, but there is a sense that some group elements might be essentially the same. The notion of equivalence class makes this hunch precise.

---
Before giving a formal definition, let us provide some intuitive feel for what "*essentially the same*" might mean. Consider $SO(3)$ we might think that rotation through $17\degree$ and $71\degree$ are in no way essentially the same, but the rotation through $17\degree$ around the x-axis and $17\degree$ around z-axis are essentially the same, we could just call the x-axis the z-axis.

In a group $G$, two elements $g$ and $g'$ are said to be equivalent $(g \thicksim g')$ if there exists another element $f$ such that: $g' = f^{-1}gf$.
This transformation $g\rightarrow g'$ is like a similarity transformation in linear algebra, and we will call it as so.

Since equivalence is transitive (friend of a friend is a friend); That is, $g \thicksim g'$ and $g'\thicksim g''$ imply that $g \thicksim g''$
—we can gather all the elements that are equivalent into equivalence classes. The number of elements in a given equivalence class $c$, denoted by $n_c$ plays a crucial role in the representation theory to be discussed in part II.
#### Three facts about classes
1. In an abelian world, everybody is in a class by himself or herself. 
2. In any group, the identity is always proudly in its own private class of one. 
3. Consider a class $c$ consisting of $\{ g_1,\dots,g_{n_c}\}$ Then the inverse pf these $n_{c}$ elements also form a class which we denote by $\bar c$

## Cycle Structure and Partition of Integers
As we already explained s permutation can be written as $n_j$ $j$-cycles, for instance (xxxxx)(xxxxx)(xx)(x) consists of $n_5=2$, $n_4=0$, $n_3=0$, $n_2=1$, $n_1=1$ cycles which using $\sum_j jn_j$ one can find the number of elements, As was remarked earlier, normally, the 1-cycles are not shown explicitly, a convention we have elsewhere followed.
> Question: Given a cycle structure characterized by the integers $n_j$ , determine the number of permutations in $S_n$ with this cycle structure.
	
$$ 
	N(n_1,\dots,n_j) = \frac{n!}{\prod_j j^{n_j}{n_j!}} $$



## The Dihedral group
There are of course many other finite groups besides the permutation groups. we already mentioned the set of transformations that leave the n-sided regular polygon invariant, forming a group known as the dihedral group $D_n$.

The group is generated by the rotation $R$ through $2π/n$ and the reflection $r$ through a median. For $n$ odd (think equilateral triangle and pentagon), a median is a straight line going through the center of the polygon from one vertex to the midpoint of the opposite side. For $n$ even (think square and hexagon), there are two types of median: a median is a straight line through the center of the polygon going from one vertex to another, or going from the midpoint of a side to another midpoint. There are always $n$ medians. 

![[Pasted image 20211109100707.png]]

## The Quarternionic Group
Some readers may have heard that Hamilton generalized the imaginary unit i by adding two other units j and k satisfying the multiplication rules:
$$ \begin{matrix}
i^2 = j^2 = k^2 = -1
\\
ij=-ji=k
\\
jk=-kj =i
\\
ki=-ik=j
\end{matrix}
$$
The quarternionic group $Q$ consists of eight elements: 
$$ \{ i,j,k,-i,-k,-j,1,-1\}$$
with group multiplication given by Hamilton’s rules. 

## Coxeter Groups
One more example. A Coxeter group is presented by
$$
\big< a_1,a_2,\dots,a_k|(a_i)^2 = I ,  \ (a_ia_j)^{n_{ij}}=I, \ n_{ij} \ge 2, \ \ \text{with} \ i,j = 1,2,3,\dots, k\big> 
$$

In other words, each generator squares to the identity (note that this does not mean that every group element squares to the identity), and for every pair of generators, there exists an integer $n_{ij} \ge 2$ such that $(a_ia_j)n_{ij} = I$. The $a_i$s correspond to reflections. As you can see, the Coxeter groups are inspired by the kaleidoscope.

## Invariant Subgroup
We know what a subgroup is, but now let us talk about a very special kind of subgroup, known as an invariant subgroup. Let $H$, consisting of elements $\{h1, h2, ...\}$, be a subgroup of $G$. Take any element $g$ not in $H$. Then the set of elements $\{g^{−1}h_1g, g^{−1}h_2g, ...\}$ forms a subgroup (exercise!), which we naturally denote by $g^{−1}Hg$. In general, the subgroups $H$ and $g^{−1}Hg$ are distinct. But if $H$ and $g^{−1}Hg$ are the same for all $g ∈ G$ (note the emphasis on “all”) then $H$ is called an invariant subgroup. In other words, $H$ is invariant if the two lists $\{h_1, h_2, ...\}$ and ${g^{−1}h_1g, g^{−1}h_2g, ...}$ are the same for any $g$. In other words, similarity transformations generated by the group elements of $G$ leave $H$ unchanged. (The jargon guy tells us that an invariant subgroup is also known as a normal subgroup. I prefer the term “invariant subgroup” as being more informative.)
 
We denote:
1.  $G$ has  an invariant subgroup $H$: $G \rhd H$ 
2.  $H$ is an invariant subgroup of $G$: $H \lhd G$

## Derived Subgroup
Given a group $G$, grab two elements $a, b$, and calculate:
$$\big<a,b\big> \equiv a^{-1}b^{-1}ab=(ba)^{-1}(ab) $$
the objects $\big<a,b\big>$ as $a$ and $b$ range over all the elements in the group. These objects, together with the products of these objects with each other, that is, group elements o fthe form $x_ix_j\dots x_k$, constitute a subgroup of $G$, known as the derived subgroup $D$.

> Note: A group that doesn't have any invariant subgroup is said to be simple

> “We want to express the notion of a group being simple, ofnot containing smaller pieces. The naive first thought is that the group should not contain any subgroup, but subgroups are a dime a dozen. As we saw in chapter I.1, we could take any element g: it and its integer powers would form a cyclic subgroup. So, a garden variety cyclic subgroup does not count; any decent-sized group would be full of them. But an invariant subgroup is sort of special. Finding V inside A4 is sort of like physicists finding quarks inside a hadron!”

## Invariant Subgroups, Cosets, and the Quotient Group
Assume $G \rhd H$ therefore all the equivalence members of a $h_i$ are also in $H$, this is a very special thing to happen, as we will use them to construct objects which are called *cosets* and another group called *quotient group*.
For an element g, consider the set of elements $\{gh_1, gh_2, ...\}$, which we will denote by $gH$. We have a whole bunch of such sets, $g_aH$, $g_bH$, ... . We can naturally multiply two of these sets together: simply multiply each group element in the set $g_aH$ by every group element in the set $g_bH$ and look at the resulting set:
$$
(g_ah_i)(g_bh_j) = g_a(g_bg_b^{-1})h_ig_bh_j = g_ag_b(g_b^{-1}h_ig_b)h_j = g_ag_bh_lh_j
$$

The objects $gH$, which our friend the jargon guy tells us are called left cosets, close under multiplication:
$$
(g_aH)(g_bH) = (g_ag_bH)
$$
The natural question is whether they form a group.
Sure! Indeed, equation above maps the pair $g_a$ and $g_b$ to the product $g_ag_b$. Thus, the identity of this group is $IH =H$, namely, $H$ itself, since $(IH)(gH) = gH$. The inverse of $gH$ is $g^{−1}H$, since $(g^{−1}H)(gH) = (gH)(g^{−1}H) = IH =H$. I will let you show associativity.


Thus, if a group $G$ has an invariant subgroup $H$, then we can construct another group consisting of left cosets $gH$, a group known as the **quotient group** and written as $Q=G/H$. 


Why quotient?Well, if $N(G)$ denotes the number of elements in $G$ and $N(H)$ the number of elements in $H$, each coset $\{g_aH\}$ contains $N(H)$ elements of $G$. 


Hence there can only be $N(Q) =N(G)/N(H)$ cosets. It is entirely reminiscent of how we first learned to divide, by putting, say, oranges into separate baskets. 

The number of elements in $Q$ is: $N(Q) =N(G)/N(H)$ (*strong shades of Lagrange’s theorem*). In general, $Q$ is not a subgroup of $G$.


There is nothing special about the left, of course. We could equally well have played with the right cosets, namely, the sets $\{h_1g, h_2g, ...\}= Hg$. Indeed, if $H \lhd G$, then the left cosets $gH$ and right cosets $Hg$ are manifestly the same.

