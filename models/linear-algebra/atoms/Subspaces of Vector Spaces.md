# Subspaces of Vector Spaces

A *subset* $W$ of a vector space $V$ over a field $\mathbb K$ is called a subspace of $V$ if $W$ is a vector space over $\mathbb K$ with the operations of addition and scalar multiplication defined on $V$.

If $V$ is a vector space, then $V$ and $\{0\}$ are subspaces of $V$ called trivial subspaces. A subspace $W$ of $V$ is called proper subspace if $V\not = W$. Otherwise it is called an improper subspace. 

To check whether a subset if a subspace, we don't have to verify all the conditions of vector spaces. The following theorem gives the set of conditions that are to be verified.

Let $V$ be a vector space over a field $\mathbb{K}$. A subset $W$ of $V$ is a subspace if and only if the following three conditions hold for the operations defined in $V$:

(a) $0 \in W$.
(b) $w_1 + w_2 \in W$ whenever $w_1, w_2 \in W$.
(c) $\lambda w \in W$ whenever $\lambda \in \mathcal{K}$ and $w \in W$.

**Proof:** Suppose that $W$ is a subspace of $V$. Then $W$ is a vector space with the operation addition and scalar multiplication defined on $V$. Therefore, (b) and (c) are satisfied. And by the uniqueness of identity element in a vector space, $0 \in W$.

Conversely, suppose that the conditions (a), (b), and (c) are satisfied. We have to show that $W$ is a vector space with the operations defined on $V$. Since $W$ is a subset of the vector space $V$, the conditions of being a vector space are automatically satisfied by the elements in $W$. Therefore, $W$ is a subspace of $V$.

> [!NOTE]
    > Condition (a) can be derived from condition (c) with $\lambda = 0$. However, condition (a) can still be used to identify subsets that are not subspaces.

To check whether a subset of a vector space is a subspace, we verify only the closure properties of vector addition and scalar multiplication in the given set. Therefore this 
## Example: Subspaces in R²

Let $V = \mathbb{R}^2 = \{ (x_1, x_2) | x_1, x_2 \in \mathbb{R} \}$.  $V$ is a vector space over $\mathbb{R}$. Consider $W_1 = \{ (x_1, x_2) | x_1 + x_2 = 0 \}$ and $W_2 = \{ (x_1, x_2) | x_1 + x_2 = 1 \}$. Then $W_1$ is a subspace of $V$.

(a) Clearly, the additive identity $(0, 0)$ is in $W_1$.
(b) Take two elements $(x_1, x_2), (y_1, y_2) \in W_1$. Then $x_1 + x_2 = 0$ and $y_1 + y_2 = 0$. This implies that $(x_1, x_2) + (y_1, y_2) = (x_1 + y_1, x_2 + y_2) \in W_1$ as $x_1 + y_1 + x_2 + y_2 = 0$.
(c) Take $(x_1, x_2) \in W_1$ and $\lambda \in \mathbb{R}$. Then $x_1 + x_2 = 0$. This implies that $\lambda (x_1, x_2) = (\lambda x_1, \lambda x_2) \in W_1$ as $\lambda x_1 + \lambda x_2 = \lambda(x_1 + x_2) = 0$.

However, $W_2$ is not a subspace of $\mathbb{R}^2$ because the zero vector does not belong to $W_2$.

$W_1$ and $W_2$ represent two lines on the plane.

**Note:** The only non-trivial proper subspaces of $\mathbb{R}^2$ are straight lines passing through the origin.

---

The next theorem gives a method to construct new subspaces from known subspaces.

## Constructing Subspaces from known Subspaces

Let $W_1$ and $W_2$ be two subspaces of a vector space $V$ over a field $\mathbb{K}$, then their intersection $W_1 \cap W_2 = \{w | w \in W_1 \text{ and } w \in W_2\}$ is a subspace of $V$.

**Proof:** Since $W_1$ and $W_2$ are subspaces of $V$, $0 \in W_1$ and $0 \in W_2$. Therefore, $0 \in W_1 \cap W_2$.

Let $v, w \in W_1 \cap W_2$, then
$$ v \in W_1 \text{ and } v \in W_2 $$
$$ w \in W_1 \text{ and } w \in W_2 $$
Therefore, $v + w \in W_1$ and $v + w \in W_2$ as $W_1$ and $W_2$ are subspaces.
Thus, $v + w \in W_1 \cap W_2$.

For $\lambda \in \mathbb{K}$ and $w \in W_1 \cap W_2$,
$$ w \in W_1 \text{ and } w \in W_2 $$
Therefore, $\lambda w \in W_1$ and $\lambda w \in W_2$ as $W_1$ and $W_2$ are subspaces.
Thus, $\lambda w \in W_1 \cap W_2$.

Therefore, $W_1 \cap W_2$ is a subspace of $V$.

The above result can be extended to any number of subspaces. As we have shown that the intersection of subspaces is again a subspace, it is natural to ask whether the union of subspaces is again a subspace. It is clear that the union of two subspaces need not be a subspace of $V$ (Fig. 2.2).

![[../../../attachments/Pasted image 20260119100355.png]]

## Union of Subspaces Can Become a Subspace as Well

Let $V$ be a vector space over the field $\mathbb K$ and let $W_1$, and $W_2$ be subspaces of $V$. Then $W_1\cup W_2$ is a subspace of $V$ if and only if either $W_1\subseteq W_2$ or $W_2\subseteq W_1$.

**Proof:** Let $W_1$ and $W_2$ be subspaces of $V$. 
Suppose that either 
$$
W_1\subseteq W_2
$$
or vice versa. Then $W_1\cup W_2$ is either $W_1$ or $W_2$. In either case, the union is a subspace of $V$. Conversely suppose that $W_1 \cup W_2$ is a subspace of $V$ and that:
$$
W_1\not\subseteq W_2 \land W_2\not\subseteq W_1
$$
Then there exists at least one element $w_1\in W_1$ such that $w_1 \not \in W_2$ and also $w_2\in W_2$ such that $w_2\not\in W_1$. As in union we know that both of them are in the set, $w_1,w_2 \in W_1\cup W_2$.

Since $W_1\cup W_2$ is a subspace of $V$, then:
$$
w_1+w_2 \in W_1\cup W_2
$$
Then:
$$
w_1 + w_2 \in W_1 \lor w_1+w_2 \in W_2
$$
Suppose $w_1+w_2\in W_1$. Since $w_1\in W_1$ then $W_1$ is a subspace, $-w_1\in W_1$ and hence $(-w_1) + w_1 + w_2 \in W_1$ and thus $w_2\in W_1$ which is a contradiction. This contradiction would also be raised for the case $w_1 + w_2\in W_2$. Therefore our assumption is wrong. That is $W_1\cup W_2$ is not a subspace.