---
sticker: lucide//atom
---
## Vector Space Structure of Fields

**Statement:** If $\mathbb{F}$ is a sub-field of a field $\mathbb{K}$, then $\mathbb{K}$ is a vector space over $\mathbb{F}$, with addition and multiplication being the operations in $\mathbb{K}$. Thus, in particular, $\mathbb{C}$ is a vector space over $\mathbb{R}$ and $\mathbb{R}$ is a vector space over $\mathbb{Q}$.

**Proof:**

Let $\mathbb{F} \subseteq \mathbb{K}$ be sub-fields. We want to show that $\mathbb{K}$ is a vector space over $\mathbb{F}$.  To do this, we need to verify the axioms of a vector space. Let $v, w \in \mathbb{K}$ and $a, b \in \mathbb{F}$.

1. **Closure under Addition:** Since $\mathbb{K}$ is a field, $v + w \in \mathbb{K}$.
2. **Closure under Scalar Multiplication:**  Since $\mathbb{F} \subseteq \mathbb{K}$, $a \in \mathbb{K}$, and $\mathbb{K}$ is a field, $av \in \mathbb{K}$.
3. **Associativity of Addition:** $(v + w) + u = v + (w + u)$. This holds because addition in $\mathbb{K}$ is associative, which is part of the definition of a field.
4. **Commutativity of Addition:** $v + w = w + v$.  This holds because addition in $\mathbb{K}$ is commutative, which is part of the definition of a field.
5. **Existence of Additive Identity (Zero Vector):** There exists an element $0 \in \mathbb{K}$ such that $v + 0 = v$ for all $v \in \mathbb{K}$. This is the additive identity in $\mathbb{K}$, and it's part of the field definition.
6. **Existence of Additive Inverse:** For every $v \in \mathbb{K}$, there exists an element $-v \in \mathbb{K}$ such that $v + (-v) = 0$. This is the additive inverse in $\mathbb{K}$, and it's part of the field definition.
7. **Associativity of Scalar Multiplication:** $a(bv) = (ab)v$.  This holds because multiplication in $\mathbb{K}$ is associative, which is part of the definition of a field.
8. **Distributivity of Scalar Multiplication over Field Addition:** $a(v + w) = av + aw$. This holds because multiplication distributes over addition in $\mathbb{K}$, which is part of the definition of a field.
9. **Distributivity of Scalar Multiplication over Field Subtraction:** $(a + b)v = av + bv$.  This holds because multiplication distributes over addition in $\mathbb{K}$, which is part of the definition of a field.
10. **Existence of Multiplicative Identity (Unit Vector):** There exists an element $1 \in \mathbb{F} \subseteq \mathbb{K}$ such that $1v = v$ for all $v \in \mathbb{K}$. This is the multiplicative identity in $\mathbb{K}$, and it's part of the definition of a field.

Since all ten vector space axioms are satisfied, $\mathbb{K}$ is a vector space over $\mathbb{F}$.

**Specific Examples:**

*   **$\mathbb{C}$ as a Vector Space over $\mathbb{R}$:**  Here, $\mathbb{F} = \mathbb{R}$ and $\mathbb{K} = \mathbb{C}$. The addition and scalar multiplication are the standard complex number operations.
*   **$\mathbb{R}$ as a Vector Space over $\mathbb{Q}$:** Here, $\mathbb{F} = \mathbb{Q}$ and $\mathbb{K} = \mathbb{R}$.  The addition and scalar multiplication are the standard real number operations.

