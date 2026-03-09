---
sticker: lucide//atom
---
As we've discussed in [[atoms/Basis and Dimension|Basis and Dimension]], one can find a set of vectors in a vector space $V$ that are:

1. Linearly independent
2. Span the vector space

Afterwards, any element of the vector space can be uniquely represented as a linear combination of these vectors.

$$
\mathbf v= c_1 \mathbf e_1 + c_2 \mathbf e_2 + \dots + c_n \mathbf e_n
$$

where $\mathbf e_i \in B$ the set of basis chosen. 
## Representing Vectors

As we've discussed, generally speaking vectors are just objects in a vector space. Therefore, having a representation of them can be a hard task. Fortunately, now with the discussion of basis, assuming that we've agreed upon a specific set of basis (because generally infinitely many sets can be a basis for our vector space), and assuming the set $B$ is ordered in a way we've agreed upon.  We can write a vector as an array of coordinates in some specific basis:

$$
\mathbf v = \begin{bmatrix} c_1,c_2,\dots,c_m\end{bmatrix}_B
$$
This is not a matrix as we'll discover that a column vector representing a vector can be more beneficial in terms of matrix operations are useful and meaningful in that case.


Therefore, we can use matrices as representation tools for vectors, representing them as column matrices:

$$
[\mathbf v]_B = \begin{bmatrix}
c_1 \\ c_2 \\ \vdots \\ c_n
\end{bmatrix} 
$$

Where the dimension of the vector space is $n$. This is generally called the *Coordinate Vector of $\mathbf v$* since the cells depend on what basis we've got. 

It is obvious to see that for each $\mathbf e_i\in B$ we can write:

$$
[\mathbf e_i] = \begin{bmatrix} 0 \\ \vdots \\ 1 \\ \vdots \\ 0 \end{bmatrix}
$$

Since it is linearly independent of other basis vectors.
