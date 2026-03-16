---
sticker: lucide//atom
---
# Algebra of Linear Transformations

Linear Transformation themselves can be extended to a rigid structure. We will define addition and scalar multiplication in the set of all linear transformations from $V$ to $W$ as in the following theorem. Later, we will also prove that the set of all such linear transformations forms a vector space with respect to these operations.

**Theorem**
Let $V$ and $W$ be vector spaces over the field $\mathbb{K}$. Let $T_{1}$ and $T_{2}$ be linear transformations from $V$ into $W$. We define:

$$
(T_{1}+T_{2})(v) = T_{1}(v) + T_{2}(v)
$$
is a linear transformation from $V$ into $W$. If $\xi \in \mathbb{K}$, the function $(\xi T)$ defined by $(\xi T)(v) = \xi (T(v))$ is a linear transformation from $V$ into $W$.

**Proof**

Let $v_{1},v_{2}\in V$ and $\lambda \in \mathbb{K}$. Then since $T_{1}$ and $T_{2}$ are linear transformations from $V$ into $W$,

$$
\begin{align}
(T_{1}+T_{2})(\lambda v_{1}+v_{2})  & = T_{1}(\lambda v_{1}+v_{2}) + T_{2}(\lambda v_{1}+v_{2})  \\
 & =\lambda T_{1}(v_{1}) + T_{1}(v_{2}) + \lambda T_{2}(v_{1}) + T_{2}(v_{2}) \\
 & =\lambda \left( T_{1}(v_{1}) + T_{2}(v_{1}) \right) +T_{1}(v_{2})+T_{2}(v_{2}) \\
 & =\lambda(T_{1}+T_{2})(v_{1}) + (T_{1}+T_{2}) (v_{2}) 
\end{align}
$$
Therefore $T_{1}+T_{2}$ is a linear transformation. Now for any linear transformation $T$ from $V$ into $W$ and $\xi \in \mathbb{K}$,

$$
\begin{align}
(\xi T)(\lambda v_{1}+v_{2})  &  = \xi(T(\lambda v_{1}+v_{2})) \\
 & =\xi(\lambda T(v_{1}) + T(v_{2})) \\
 & =(\xi \lambda)T(v_{1})+\xi T(v_{2}) \\
 & =\lambda(\xi T)(v_{1}) + (\xi T)(v_{2})
\end{align}
$$
Therefore, $\xi T$ is a linear transformation from $V$ into $W$.

We've shown that a linear transformation can be represented by a matrix. Now These two operations can correlate with plus and multiplication of scalar operations known in matrices as well. 

![[../../../attachments/Pasted image 20260316093518.png]]
![[../../../attachments/Pasted image 20260316093554.png]]
## Linear Transformations Form a Vector Space

**Theorem**
Let $V$ and $W$ be vector spaces over a field $\mathbb{K}$. Then the set of all linear transformations from $V$ to $W$, denoted by $\mathcal{L}(V,W)$, is a vector space with respect to addition and scalar multiplication defined above.

**Proof**
- [ ] Later we should prove all the axiom definitions of a vector space holds for this space as well.

![[../../../attachments/Pasted image 20260316092511.png]]![[../../../attachments/Pasted image 20260316092536.png]]

**Theorem**
Let $U, V$ and $W$ be vector spaces over the field $\mathbb{K}$. Let $T_{1}$ be a linear transformation from $U$ to $V$ and $T_{2}$ a linear transformation from $V$ int $W$. Then the composed function $T_{2}T_{1}$ defined by:

$$
(T_{2}T_{1})(u) =T_{2}(T_{1}(u))
$$
is a linear transformation from $U$ to $W$.

**Proof**
Let $u_{1},u_{2} \in U$ and $\lambda \in \mathbb{K}$. Then

$$
\begin{align}
(T_{2}T_{1})(\lambda u_{1} + u_{2})  & = T_{2}(T_{1}(\lambda u_{1}+u_{2})) \\
 & = T_{2}(\lambda T_{1}(u_{1}) + T_{1}(u_{2})) \\
 & =\lambda \left[ T_{2}(T_{1}(u_{1})) \right] +T_{2}(T_{1}(u_{2})) \\
 & =\boxed{\lambda(T_{2}T_{1})(u_{1}) + (T_{2}T_{1})(u_{2})}
\end{align}
$$
Therefore, $T_{2}T_{1}$ is a linear transformation from $V$ to $W$.


Now below we have the proof that this composition is analogous to the matrix multiplication defined generally.

![[../../../attachments/Pasted image 20260316093401.png]]