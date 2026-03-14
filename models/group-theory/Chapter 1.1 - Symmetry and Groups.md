# Symmetry and Groups
---
**Table of Content**
```toc
    style: number
    min_depth: 1
    max_depth: 6
```
---
## Symmetry and Transformation

---
## Symmetry in Physics
In physics we are interested in the symmetries enjoyed by a given physical system. On a more abstract level, we are interested in the symmetries of the fundamental laws of physics. One of the most revolutionary and astonishing discoveries in the history of physics is that objects do not fall down, but toward the center of the earth. Newton’s law of gravitation does not pick out a special direction: it is left invariant by rotations. The history of theoretical physics has witnessed the discoveries of one unexpected symmetry after another. Physics in the late twentieth century consists of the astonishing discovery that as we study Nature at ever deeper levels, Nature displays more and more symmetries.

> The history of theoretical physics has witnessed the discoveries of one unexpected symmetry after another. Physics in the late twentieth century consists of the astonishing discovery that as we study Nature at ever deeper levels, Nature displays more and more symmetries.

This discussion leads us to abstract the concept of a group

## Groups
A Group $G$ consist of a set of elements $\{g_\alpha\}$ which we could compose together. Given any two elements $g_\alpha$ and $g_\beta$, the product $g_\alpha\cdot g_\beta$ is equal to another element, $g_\gamma$ which is in $G$ as well.

Composition or Multiplication satisfies the following axioms:
1. **Associativity**: Composition is associative: $(g_\alpha\cdot g_\beta)\cdot g_\gamma = g_\alpha\cdot(g_\beta\cdot g_\gamma)$

2. **Existence of the identity**: There exists a group element, known as the identity and denoted by I, such that $I$ . $g_α = g_α$ and $g_α \cdot I = g_α.$.

3. **Existence of the inverse**: For every group element $g_α$, there exists a unique group element, known as the inverse of $g_α$ and denoted by $g^{−1}_α$ , such that $g^{−1}_\alpha \cdot  g_α = I$ and $g_α . g^{−1 }_\alpha = I$.

1. Composition is not required to commute, In this respect, the multiplication of group elements is, in general, like the multiplication of matrices but unlike that of ordinary numbers.
2.  The right inverse and the left inverse are by definition the same.We can imagine mathematical structures for which this is not true, but then these structures are not groups. Recall (or read in the review of linear algebra) that this property holds for square matrices: provided that the inverse $M^{−1}$ of  a matrix $M$ exists, we have $M^{−1}M =MM^{−1} = I$ with I the identity matrix.
3. It is often convenient to denote $I$ by $g_0$.
4. The label $α$ that distinguishes the group element $g_α$ may be discrete or continuous.
5. The group can have finite or infinite elements

## Concept of Subgroup
Given a set of entities $\{g_\alpha\}$  the form a group $G$ if a subset $\{h_\alpha\}$ also form a group $H$ under the same composition then we say that $H\subset G$

## Cyclic Groups
For a finite group $G$, pick some element g and keep multiplying it by itself. In other words, consider the sequence $\{g, g^2 = gg, g^3 = g^2g, \dots \}$. As long as the resulting product is not equal to the identity, we can keep going. Since $G$ is finite, the sequence must end at some point with $g_k = I$. The set of elements $\{I , g, g^2, ... , g^{k−1}\}$ forms a subgroup $Z_k$. Thus, any finite group has a bunch of cyclic subgroups. If $k$ is equal to the number of elements in $G$, then the group $G$ is in fact $Z_k$.

## Lagrange Theorem
Lagrange proved that given a group $G$ with $n$ elements and a subgroup $H$ with $m$ elements then $m$ is a factor of $n$. In other words, $n/m$ is an integer.

## Direct Product of Groups
Given two groups 
$F$ and $G$ (which can be continuous or discrete), whose elements we denote as $f$ and $g$ respectively. We can define another group $H$ as below
$$ H = \{h_\alpha\} 
$$
$$ 
h_\alpha = (f_i,g_j) 
$$
This can be written as:
$$ H = F \otimes G $$
which is known as the direct product of the two groups.
$$
I_H = (I_F,I_G)
$$
the definition and proof of it is not concerned here but it is available in the book.

## Multiplication Table

> In mathematics, a **multiplication table** (sometimes, less formally, a times table) is a mathematical table used to define a multiplication operation for an algebraic system.
> The decimal multiplication table was traditionally taught as an essential part of elementary arithmetic around the world, as it lays the foundation for arithmetic operations with base-ten numbers. Many educators believe it is necessary to memorize the table up to 9 × 9.
> [Wikipedia](https://en.wikipedia.org/wiki/Multiplication%20table)

## Presentations
For large groups, writing down the multiplication table is clearly a losing proposition. Instead, finite groups are defined by their properties. 
which list the elements (sometimes called generators) from which all other elements can be obtained by group multiplication, and the essential relations the generators satisfy. Thus, in a self-evident notation, the groups $Z_4$ and $Z_2 \otimes Z_2$ are defined  by their presentations as follows:
$$ 
Z_4 : \big<A | A^4 = I \big> 
$$
$$
Z_2\otimes Z_2 : \big<A,B | A^2 = B^2 = I, AB = BA \big> 
$$
The two groups are clearly distinct. In particular, $Z_4$ contains only one element that squares to $I$, namely $A^2$.

## Homomorphism and Isomorphism
A map $f: G\rightarrow G'$ of a group $G$ into the group $G'$ is called homomorphism is it preserves the multiplication form of the group $G$. which means
$$
f(g_i)f(g_j) = f(g_ig_j)
$$
This clearly implies $f(I) = I$ which means that the identity of $G$ is mapped to the identity of $G'$
**==A homomorphism becomes *Isomorphism* if the map is one-to-one and onto.==**
