---
sticker: lucide//atom
---
# Levi-Civita Symbol

The Levi-Civita symbol, denoted by $\epsilon_{ijk}$, is a totally antisymmetric tensor used in various areas of mathematics and physics, particularly in vector calculus and differential geometry. It's defined as follows:

**Definition:**

$$
\epsilon_{ijk} = \begin{cases}
+1 & \text{if } (i, j, k) \text{ is an even permutation of } (1, 2, 3) \\
-1 & \text{if } (i, j, k) \text{ is an odd permutation of } (1, 2, 3) \\
0 & \text{if any two indices are equal}
\end{cases}
$$

**Examples:**

*   $\epsilon_{123} = +1$  (identity)
*   $\epsilon_{132} = -1$ (transposition of two indices)
*   $\epsilon_{213} = -1$
*   $\epsilon_{312} = +1$
*   $\epsilon_{111} = \epsilon_{222} = \epsilon_{333} = 0$
*   $\epsilon_{122} = 0$

**Properties:**

1.  **Totally Antisymmetric:**
    $$
    \epsilon_{ijk} = - \epsilon_{jik} = \epsilon_{kij} = - \epsilon_{ikj} = \epsilon_{jki} = - \epsilon_{ji k}
    $$

2.  **Cycle Sum:**
    $$
    \epsilon_{ijk} + \epsilon_{jkl} + \epsilon_{kjl} = 0
    $$

3. **Product Rule (Vector Calculus):** The curl of a vector field $\mathbf{F}$ can be expressed as:
   $$
   \nabla \times \mathbf{F} = \epsilon_{ijk} F^k \hat{\mathbf{e}}_i
   $$
   where $F^k$ is the *k*-th component of $\mathbf{F}$, and $\hat{\mathbf{e}}_i$ are the unit vectors in Cartesian coordinates.

4. **Scalar Triple Product:** The scalar triple product of three vectors $\mathbf{a}$, $\mathbf{b}$, and $\mathbf{c}$ can be expressed as:
   $$
   \mathbf{a} \cdot (\mathbf{b} \times \mathbf{c}) = \epsilon_{ijk} a^i b^j c^k
   $$

**Generalization to *n* Dimensions:**

For *n*-dimensional space, the Levi-Civita symbol is defined as:

$$
\epsilon_{i_1 i_2 ... i_n} = \begin{cases}
+1 & \text{if } (i_1, i_2, ..., i_n) \text{ is an even permutation of } (1, 2, ..., n) \\
-1 & \text{if } (i_1, i_2, ..., i_n) \text{ is an odd permutation of } (1, 2, ..., n) \\
0 & \text{if any two indices are equal}
\end{cases}
$$

The properties of antisymmetry and the cycle sum generalize to *n* dimensions.