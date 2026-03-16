---
sticker: lucide//atom
---
The idea of [[Inverse of Linear Transformations]] can be used to identify the similarity between vector spaces. For example, a vector in $\mathbb{R}^{4}$ can be observed as a $2\times 2$ matrix in $\mathbb{M}_{2\times 2}(\mathbb{R})$ as their vector addition and scalar multiplication can be associated of vector spaces in an identical manner.

These types of vector spaces are considered isomorphic. Isomorphism shows two things are basically the same thing, viewed in different representation, or structure.

## Definition:

Let $V$ and $W$ be vector spaces over the field $\mathbb{K}$, then $V$ is said to be isomorphic to $W$ if there exists an invertible linear transformation from $V$ to $W$. That is, if there exists a one-one and onto linear transformation from $V$ to $W$.


For finite-dimensional spaces over the same field. We can show that the only matter for them to be isomorphic is so that their dimensions are equal.

![[../../attachments/Pasted image 20260316095004.png]]

**Corollary**
Let $V$ be a vector space over the field $\mathbb{K}$ with $\dim(V) = n$. Then $V$ is isomorphic to $K^{n}$ over $\mathbb{K}$.

When we have the bases. As we know from earlier a linear transformation can be completely defined by just defining how it maps the bases to other bases. Since every other vector would be represented by the bases in the first space and then transformed easily to the other one. Theorem below shows that for a linear transformation between such spaces to be invertible, is only the matter of being able to invert the bases correctly.

![[../../attachments/Pasted image 20260316095640.png]]![[../../attachments/Pasted image 20260316095706.png]]

In [[atoms/Matrix Representation|Matrix Representation]], we've talked about how going from and $n$ dimensional space to an $m$ dimensional space in a transformation can be represented by a matrix, now we show that the space of all linear transformations from $V$ to $W$ is identical to  the space of all $m\times n$ matrices:

![[../../attachments/Pasted image 20260316100342.png]]![[../../attachments/Pasted image 20260316100355.png]]