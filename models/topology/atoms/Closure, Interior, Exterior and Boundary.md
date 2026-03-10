---
sticker: lucide//atom
---
# Closure, Interior, Exterior, and Boundary

![[../../../attachments/Pasted image 20260118153024.png]]

Let $X$ be a topological space and $A \subseteq X$.

**Closure of A (denoted $\overline{A}$):**

$$\overline{A} = \bigcap \{B : B \supseteq A \text{ and } B \text{ is closed in } X\}$$
$\overline{A}$ is the smallest closed set containing $A$.

**Interior of A (denoted Int $A$):**

$$Int A = \bigcup \{C : C \subseteq A \text{ and } C \text{ is open in } X\}$$
Int $A$ is the largest open set contained in $A$.

**Exterior of A (denoted Ext $A$):**

$$Ext A = X \setminus \overline{A}$$

**Boundary of A (denoted $\partial A$):**

$$\partial A = X \setminus (Int A \cup Ext A)$$

For any subset $A \subseteq X$, the whole space $X$ is equal to the disjoint union of Int $A$, Ext $A$, and $\partial A$. The set $A$ always contains all of its interior points and none of its exterior points, and may contain all, some, or none of its boundary points.

## Identifying Where a Point Belongs

Let $X$ be a topological space and let $A\subseteq X$ be any subset:

- A point is in $\text {Int} A$ if and only if it has a neighborhood contained in $A$.
- A point i sin $\text{Ext} A$ if and only if it has a neighborhood contained in $X\setminus A$.
- A point is in $\partial A$ if and only if every neighborhood of it contains both a point of $A$ and a point of $X\setminus A$.
- A point is in $\bar A$ if and only if every neighborhood of it contains points of $A$.
- $\bar A = A\cup \partial A = \text{Int} A \cup \partial A$
- $\text{Int}A$ and $\text{Ext} A$ are open in $X$, while $\bar A$ and $\partial A$ are closed in $X$.

The following is equivalence with one another:

- $A$ is open in $X$
- $A = \text{Int} A$
- $A$ contains non of its boundary points.
- Every point of $A$ has a neighborhood contained in $A$.

On the other hand these are equivalence with one another:

- $A$ is closed in $X$.
- $A=\bar A$
- $A$ contains all of its boundary points.
- Every point of $X\setminus A$ has a neighborhood contained in $X\setminus A$.