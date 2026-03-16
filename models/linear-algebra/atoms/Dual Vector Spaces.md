---
sticker: lucide//atom
---
A linear functional is a map from the vector space, to the field that is associated it with. Mathematical we have:

**Definition**
Let $V$ be a vector space over the field $\mathbb{K}$. A function $f: V\to \mathbb{K}$ is said to be a linear functional, if:

$$
f(\lambda v_{1}+v_{2}) = \lambda f(v_{1})+f(v_{2})
$$
for all $v_{1},v_{2}\in V$ and $\lambda \in \mathbb{K}$. The set of all linear functionals on $V$ forms a vector space, called the **Dual Space of $V$**, and is denoted by $V^{\ast}$.


The dual space is connected to the vector space that is it built upon. For example we can define a unique basis in the dual space given a basis in the vector space that satisfies a crucial relationship.

**Theorem**
Let $V$ be a finite-dimensional vector space over the field $\mathbb{K}$, and let $B = \{ v_{1},v_{2},\dots,v_{n} \}$ be a basis of $V$. Then there exists a unique basis $B^\ast =\{ f_{1},f_{2},\dots,f_{n} \}$ for $V^\ast$, where $f_{i}$ is given by:

$$
f_{i}(v_{j}) \begin{cases}
1,  & \text{if } i =j \\
0, & \text{otherwise}
\end{cases}
$$
Then for each linear functional $f$ on $V$, we have $f = \sum _{i=1}^{n} f(v_{i})f_{i}$ and for each vector $v \in V$, we have $v = \sum_{i=1}^{n}f_{i}(v)v_{i}$.

**Proof**
First we will prove that $B^\ast = \{ f_{1},f_{2},\dots ,f_{n} \}$, where $f_{i}$ is given by
$$
f_{i}(v_{j}) =\begin{cases}
1, & \text{if } i=1 \\
0, & \text{otherwise}
\end{cases}
$$
is linearly independent. Let $\lambda_{1},\lambda_{2},\dots, \lambda_{n}\in \mathbb{K}$ be such that
$$
\lambda_{1}f_{1}+\lambda_{2}f_{2}+\dots+\lambda_{n}f_{n} =0
$$
i.e., $(\lambda_{1}f_{1}+\lambda_{2}f_{2}+\dots+\lambda_{n}f_{n})$ for all $v\in V$. Then,
$$
(\lambda_{1}f_{1}+\lambda_{2}f_{2} + \dots+\lambda_{n}f_{n})(v_{i})=0 \implies \lambda_{i}=0, \forall i =1,2,\dots,n
$$
Thus $\{ f_{1},f_{2},\dots,f_{n} \}$ is linearly independent. It is true that $\dim(V)=\dim(V^\ast)$. Hence $B^\ast=\{ f_{1},f_{2},\dots,f_{n} \}$ is a basis for $V^\ast$, called the **dual basis** of $B$. By definition itself $B^\ast$ is unique. Now, for any linear functional $f \in V^\ast$, these exists $\lambda_{1},\lambda_{2},\dots,\lambda_{n}\in \mathbb{K}$ such that $f = \sum _{i=1}^{n}\lambda_{i}f_{i}$. Then
$$
f(v_{j}) = \sum _{i=1}^{n} \lambda_{i}f_{i}(v_{j}) = \lambda_{j}, \forall j=1,2,\dots,n
$$
Thus for each linear functional $f$ on $V$, we have $f=\sum _{i=1}^{n}f(v_{i})f_{i}$. Similarly, for each $v\in V$, there exist scalars $\lambda_{1},\lambda_{2},\dots, \lambda_{n}\in \mathbb{K}$ such that $v = \sum_{i=1}^{n}\lambda_{i}v_{i}$. Then

$$
f_{j}(v) = f_{j}\left( \sum _{i=1}^{n} \lambda_{i}v_{i} \right) =\sum _{i=1}^{n}\lambda_{i}f_{j}(v_{i}) =\lambda_{j}, \forall j=1,2,\dots,n
$$
Hence for any $v\in V$, we have:

$$
v = \sum _{i=1}^{n}f_{i}(v)v_{i}.
$$
