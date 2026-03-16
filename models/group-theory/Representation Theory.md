# Chapter 2.1 - Representation Theory
---
**Table of Content**
```toc
    style: number
    min_depth: 1
    max_depth: 6
```
---
## What is Representation ?
The notion of representing group elements by matrices is both natural and intuitive. Given a group, the idea is to associate each element g with a $d ⊗ d$ matrix $D(g)$ such that:
$$
D(g_1)D(g_2) = D(g_1g_2)
$$
$D(g)$ represents $g$ and if we can do it for all $g\in G$ it is said that these matrices furnish or provide a representation of $G$ the size of the matrices $d$ is known as the dimension of the representation.
\
The requirement (1) says that the set of matrices $D(g)$ “reflects” or “mirrors” the multiplicative table of the group. In words, the product $g_1g_2$ of two group elements $g_1$and $g_2$ is represented by the product of the matrices representing $g_1$ and $g_2$ respectively.
$$
\begin{matrix}
g_1 & \ & \cdot & \ &g_2 & \ & = &\ & g_1\cdot g_2
\\
\downarrow & \ & \downarrow & \ & 
\downarrow & \ &\ &\ & \downarrow
\\
D(g_1) & \ & \cdot & \ &D(g_2) & \ & = &\ & D(g_1\cdot g_2)
\end{matrix}
$$
> Note that the symbol $\cdot$ denotes two distinct concepts: in the top row, the composition, or more colloquially, the multiplication, of two group elements; in the bottom row, the multiplication of two matrices.

## Group  Elements and the Matrices that Represent Them
physicists often confound group elements with the matrices that represent them.
> Very roughly speaking, the representation of a group is like a photograph or a map of the group, to the extent that it preserves the multiplicative structure of the group. A photo or a map of a village is of course not the village itself, but it shows accurately how various buildings and geographical features are situated relative to one another.

## Introduction to Representation Theory
Now that we know what a representation is, we can naturally think of many questions. Does every group G have a representation? How many representations does it have? An infinite number, perhaps? What are some general properties of representations? How do we characterize these representations and distinguish among them?

Recall the notion of equivalence classes [[Finite Groups]]. 

We have a partial answer to the question that Does every group has a representation. We learned in chapter I.2 that every finite group is isomorphic to a subgroup of $S_n$, and since $S_n$ has a matrix representation, every finite group can be represented by matrices. 

As for continuous groups, in the list of examples given in chapter I.1, almost all groups—the rotation groups and the Lorentz group, for example—are defined in terms of matrices, so a fortiori they can be represented by matrices. An exception appears to be the additive group of real numbers. How in the world could addition be represented by multiplication? An exception appears to be the additive group of real numbers. *How in the world could addition be represented by multiplication?*
**Consider the $2$-dimensional matrix**
$$
D(u)=\begin{matrix}
1 & 0 \\ u & 1 
\end{matrix}
$$
Multiplication of these matrices would result:
$$
D(u)D(v) = D(u+v)
$$
Indeed, the Lorentz group mentioned in chapter I.1 also defines a 2-dimensional representation of the additive group, since $D(φ_1)D(φ_2) = D(φ_1 + φ_2)$. (Recall that $φ$ represents the boost angle.) You may have realized that this representation of addition secretly also involves the exponential function.

To answer the second question that introduced this section, namely, how many representations a group might have, we are first obliged to mention that, in representation theory, the trivial representation $D(g) = 1$, for every $g ∈ G$, also counts as a perfectly valid representation. The basic requirement ($D(g_1)D(g_2) = D(g_1g_2)$) of being a representation is certainly satisfied, since $D(g_1)D(g_2) = 1 . 1= 1= D(g_1g_2).$
Some readers might chuckle: in our photo analogy, the entire village appears as a single dot. Yes indeed, this representation is trivial, hence the name. But as you will see, in the representation theory to be developed in this chapter and the next, it is important to include it. This is perhaps reminiscent of the introduction of the number $0$in the history of mathematics.
Here the notion of *faithful* versus *unfaithful* representations naturally suggests itself. To use a more mathematical language, we say that a $d$-dimensional representation is a map of the group $G$ into some subgroup of $GL(d, C)$. The requirement ($D(g_1)D(g_2) = D(g_1g_2)$) merely says that the map is homomorphic. But if in addition the map is isomorphic, that is, one-to-one, then the representation is faithful. Otherwise, it is unfaithful.

## Character is a Function of Class
Now that we know that a given group can have many different representations, let us label the different representations by a superscript $r , s , ...$ , and write $D^{(r)}(g)$ for the matrix representing the element $g$ in the representation $r$. Given a representation $D^{(r)}(g)$ , define the important concept of the character $\chi^{(r)}$ of the representation by $χ^{(r)}(g) ≡ \text{tr} D^{(r)}(g)$ . The character, as the name suggests, helps characterize the representation.
\
Nominally, the character depends on $r$ and $g$. Recall from chapter I.2, however, that the elements of a group can be divided up into equivalence classes. Two elements $g_1$ and $g_2$ are equivalent $(g1 ∼ g2)$ if there exists another element $f$ such that:
$$
g_1 = f^{-1}g_2f
$$
We then find:
$$
\chi^{(r)} (g_1) = \text{tr} D^{(r)}(g_1) =\text{tr} D^{(r)}(f^{-1}g_2f) = \text{tr} D^{(r)}(f^{-1})D^{(r)}(g_2)D^{(r)}(f)  =\text{tr}  D^{(r)}(g_2) = \chi^{(r)}(g_2)
$$
Thus:
$$
\chi^{(r)}(c) = \text{tr} D^{(r)}(g) \ \ \ \ \ \ 
\text{for} g \in c
$$
Here $c$ denotes the equivalence class of which the element $g$ is a member. The trace on the right hand side does not depend on $g$ as such, but only on the class that $g$ belongs to. All the elements of a given equivalence class have the same character.

We can now proudly utter perhaps the most memorable statement in group theory: ***“Character is a function of class.”***

## Equivalent Representations
As for how many representations a group might have, we all agree, first of all, that two representations, $D(g)$ and $D'(g)$, are really the same representation (more formally, the two representations are equivalent) if they are related by a similarity transformation.
$$
D'(g) = S^{-1}D(g)S
$$
As explained in the review of linear algebra, $D(g)$ and $D'(g)$ are essentially the same matrix, merely written in two different bases, with the matrix $S$ relating one set of basis vectors to the other set. 
If we are given two representations, how do we decide whether they are equivalent or not? Taking the trace of one and once again using the cyclicity of the trace, we obtain:
$$
\chi'(c) = \text{tr}D'(g) = \text{tr} S^{-1}D(g)S = \text{tr} D(g) S^{-1}S = \chi(c)
$$
where $g$ is a member of the class $c$. Thus, if there exists some class $c$ for which$χ'(c) \not = χ(c)$, we can conclude immediately that the two representations are in fact different. What if $χ'(c) =χ(c)$ for all c? If this holds for only one or two $c$, physicists of the “black sheep school of thought” might still admit that it could be a coincidence, but for all $c$?
\
Most “reasonable” theoretical physicists would say that it is strong circumstantial evidence indicating that the two representations are in fact the same. 
Indeed, physicist intuition is right. We will see in the next chapter that various theorems state that for two different representations r and s, the characters $χ^{(r)}(c)$ and $χ^{(s)}(c)$ are “more different than different”: they are orthogonal in some well-defined sense.

## Reducible or irreducible representation
Now we come to the all-important notion of whether a given representation is **reducible** or **irreducible**. For the sake of definiteness, focus on $SO(3)$. We have the trivial 1-dimensional representation $D^{(1)}(g) = 1$ and the 3-dimensional defining representation $D^{(3)}(g)$. Are there other representations? 
Can you give me an 8-dimensional representation? “Sure,” you say, “you want an 8-dimensional representation for $SO(3)$. I give you an 8-dimensional representation. Here it is:”
$$
D(f)
\begin{pmatrix}
D^{(1)}(g)  & 0 & 0 & 0
\\
0 & D^{(1)}(g) & 0 & 0
\\
0&0&D^{(3)}(g) & 0
\\
0&0&0& D^{(3)}(g) 
\end{pmatrix}
$$

By the way, a matrix with this form is said to be block diagonal: it contains smaller matrices along its diagonal, with all other entries equal to zero. Note that the symbol $0$ in this matrix carries several different meanings: *it could denote a 1-by-1 matrix with its single entry equal to zero, or a 1-by-3 rectangular matrix with all its entries equal to zero, or a 3-by-1 rectangular matrix with all its entries  equal to zero, or a 3-by-3 square matrix with all its entries equal to zero.*
Ah, you have stacked two copies of $D^{(1)}(g)$ and two of $D^{(3)}(g)$ together. Indeed, by this cheap trick, you could construct representations with any dimension. 
\
You and I, being reasonable people, should agree that $D(g)$ does not count as a “new” representation. The representation $D(g)$ is known as **reducible**, and usually written as a direct sum of  the representations it reduces into: in our example, $D(g) =D^{(1)}(g)⊕D^{(1)}(g) ⊕D^{(3)}(g)⊕ D^{(3)}(g)$.
> **Representations that are not reducible are called irreducible. Clearly, we should focus on irreducible, rather than reducible, representations.**

It is clear as day that $D(g)$ in the form given above is reducible. But that ugly dude mentioned earlier could come along again and present you with a set of matrices $D'(g) = S^{−1}D(g)S$. If he chooses a particularly messy $S$, all those zeroes in the *block diagonal* would get filled in, and we would have a hard time recognizing that $D'(g)$ is reducible.

> Going back to the definition of the trivial representation $D^{(1)}(g) = 1$, you might have wondered why we used $1$ and not the $k ⊗ k$ identity matrix $I_k$ for some arbitrary positive integer k. The answer is that the representation would then be reducible unless $k = 1$. The representation $D(1)$may be trivial, but it is not reducible.

> ***One goal of representation theory is to develop criteria to determine whether a given representation is irreducible or not and to enumerate all possible irreducible representations. Since every group has an infinity of reducible representations, the real question is to figure out how many irreducible representations it has.***

## Restriction to Subgroup
When restricted to a subgroup $H$, an irreducible representation of $G$ will in general not be an irreducible representation of $H$. It will, in all likelihood, decompose, or fall apart, into a bunch of irreducible representations of $H$. The reason is clear: there may well exist a basis in which $D(h)$ is block diagonal (that is, has the form such as that shown above) for all $h\in H$, but there is no reason in general to expect that $D(g)$, for all $g$ in $G$ but not in $H$, would also be block diagonal. 
\
Simply stated, there are, by definition, fewer elements in $H$ than in $G$. How an irreducible representation of a group G decomposes upon restriction of $G$ to a subgroup $H$ will be a *leitmotifin* this book.

## Unitary Representation
The all-important unitarity theorem states that finite groups have unitary representations, that is to say, $D^\dagger(g)D(g) = I$ for all $g$ and for all representations. 
\
In practice, this theorem is a big help in finding *representations* of *finite groups*. **As a start, we can eliminate some proposed representations by merely checking if the listed matrices are unitary or not.**
\
At this point, our friend Dr. Feeling strolls by.
> “Let’s get an intuitive feel for this theorem,” he says helpfully. Suppose the representation $D(g)$is 1-by-1, that is, merely a complex number $re^{iθ}$ . Back in chapter I.1, we showed that in a finite group, if we keep multiplying $g$ by itself, eventually it has to come back to the identity: $g^k = I$ for some integer $k$.But $g^k$ is represented by $D(g^k)$ = $D^k(g)$ = $r^ke^{ikθ}$. No way this could get back to 1 if $r \not= 1$. But if $r = 1$, then $D^†(g)D(g) = e^{−iθ}e^{iθ} = 1$; that is, $D(g)$ is unitary. This, in essence, is why the theorem must be true.

### Proof of the Unitarity Theorem
The three sums are actually the same sum; they differ only by having the terms rearranged.
$$
\sum_{g\in G} f(g) = \sum_{g\in G} f(gg') = \sum_{g\in G} f(g'g)
$$
We are now ready to prove the unitarity theorem. Suppose that a given representation $\tilde D(g)$ is nonunitary. Define
$$
H = \sum_{g\in G} \tilde D(g)^\dagger \tilde D(g)
$$
now:
$$
\tilde D(g')^\dagger H \tilde D(g') = \sum_{g\in G} \tilde D(g')^\dagger \tilde D(g)^\dagger \tilde D(g) \tilde D(g') = \sum_g (\tilde D(g)\tilde D(g'))^\dagger (\tilde D(g)\tilde D(g')) = \sum \tilde D(gg')^\dagger \tilde D(gg') = H
$$
The last equality holds because of the rearrangement lemma. The matrix H is remarkably “invariant.”
Since $H$ is hermitean, there exists a unitary matrix $W$ such that $ρ^2 =W^†HW$ is diagonal and real. We now show that in addition, the diagonal elements are not only real but also positive.
To show this, we invoke a theorem, cited in the review of linear algebra, that for any matrix M, the matrix $M^†M$ has non-negative eigenvalues. Let $ψ$ be the column vector with $1$ in the $j$th entry and $0$ everywhere else. Then:
$$
(\rho^2)_{jj}=\psi^\dagger\rho^2\psi = \psi^\dagger W^\dagger H W\psi = \sum_g (\psi^\dagger W^\dagger)\tilde D(g)^\dagger D\tilde D(g) ( W\psi) = \sum_g \phi(g)^\dagger\phi(g) > 0
$$ 
because: 
![[Pasted image 20211211092309.png]]

## Compact versus non-Compact groups
![[Pasted image 20211211092755.png]]
![[Pasted image 20211211092816.png]]
![[Pasted image 20211211092825.png]]

## Product Representation
![[Pasted image 20211211093049.png]]
![[Pasted image 20211211093116.png]]
![[Pasted image 20211211093320.png]]
![[Pasted image 20211211093343.png]]
![[Pasted image 20211211093400.png]]
As usual c denotes the equivalence class since the character only depends on that
![[Pasted image 20211211093502.png]]
Finally, let me quote what Wigner said about the article that von Neumann gave him: “Soon I was lost in the enchanting world of vectors and matrices, wave functions and operators. This reprint was my primary introduction to representation theory, and I was charmed by its beauty and clarity. I saved the article for many years out of a certain piety that these things create.” I hope that you find it equally enchanting.