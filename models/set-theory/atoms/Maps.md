---
sticker: lucide//atom
---
A map or mapping is a functions in its general sense. These terms may have originated as from the process of making a geographical map. The term map may be used to distinguish some special types of functions, such as homomorphisms. 
# Definitions

Let $X$ and $Y$ be sets. A map (or mapping) $f$ is a rule by which we assign $y\in Y$ for each $x \in X$. We write:

$$
f: X\to Y
$$

If $f$ is defined by some explicit formula, we may write:

$$
f: x \mapsto f(x)
$$
There may be more than two elements in $X$ that correspond to the same $y \in Y$. A subset of $X$ whose elements are mapped to $y\in Y$ under $f$ is called the inverse image of $y$, denoted as

$$
f^{-1}(y)=\{ x \in X | f(x) = y \}.
$$
The set $X$ is called the **domain** of the map while the set $Y$ is called the range of map. The image of the map is:

$$
f(X)=\{ y \in Y | y = f(x) \text{ for some} x \in X \}\subset Y.
$$
The image $f(X)$ is also denoted by $\text{im}f$. 

> [!NOTE]
    > Note that a map cannot be defined completely without specifying the domain and the range. Take $f(x)=\exp x$, for example. If both the domain and the range are $\mathbb{R}$, $f(x)=-1$ has no inverse image. If, however, the domain and the range are the complex plane $\mathbb{C}$, we find $f^{-1}(-1)=\{ (2n+1)\pi i |n \in \mathbb{Z} \}$. The domain $X$ and the range $Y$ are as important as $f$ itself in specifying a map.

If a map satisfies a certain condition it bears a special name:

**Injective (one to one)**
A map $f:X\to Y$ is called injective (or one to one) if $x \neq x'$ implies $f(x)\neq f(x')$.
**Surjective (onto)**
A map $f:X\to Y$ is called surjective (or onto) if for each $y\in Y$ there exists at least one element $x \in X$ such that $f(x)=y$.
**Bijective**
A map $f:X\to Y$ is called bijective if it is both injective and surjective.

**More**
- [[../set-theory/Special Conditions for Maps]]

## Examples

![[../../attachments/Pasted image 20260331163057.png]]

![[../../attachments/Pasted image 20260331163110.png]]

![[../../attachments/Pasted image 20260331163125.png]]

## Special Maps

- A **constant map** $c: X\to Y$ is defined by $c(x)=y_{0}$ where$y_{0}$ is a fixed element in $Y$ and $x$ is an arbitrary element in $X$. 
- Given a map $f:X\to Y,$ we may think of its **restriction** to $A \subset X$, which is denoted as $f|_{A}: A\to Y$. 
- Given two maps $f:X\to Y$ and $g:Y\to Z$, the **composite map** of $f$ and $g$ defined by $g \circ f(x) = g(f(x))$

![[../../attachments/Pasted image 20260331165609.png]]

- A diagram of maps is called commutative if any composite maps between a pair of sets do not depend on how they are composed. This is also used in Category theory [[Commutative Diagrams]]
- If $A\subset X$, and **inclusion map** $i:A\to X$ is defined by $i(a)=a$ for any $a\in A$. An inclusion map is often written as $i: A\hookrightarrow X$. The **identity map** $\mathrm{id}_{X}:X\to X$ is a special case of an inclusion map, for which $A=X$. 
- If $f:X\to Y$ defined by $f:x \mapsto f(x)$ is bijective, there exists an inverse map $f^{-1}:Y\to X$, such that $f^{-1}: f(x)\to x$, which is also bijective. The maps $f$ and $f^{-1}$ satisfy $f\circ f^{-1}=\mathrm{id}_{Y}$ and $f^{-1}\circ f=\mathrm{id}_{X}$. Conversely if $f:X\to Y$ and $g: Y\to X$ satisfy $f \circ g=\mathrm{id}_{Y}$ and $g \circ f=\mathrm{id}_{X}$, then $f$ and $g$ and bijections. [[THSet-Composing Bijective Inverses Results in Identity]]
- [[Continuous Maps]]
- [[Homomorphism]]