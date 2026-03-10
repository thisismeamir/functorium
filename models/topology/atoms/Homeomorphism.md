---
sticker: lucide//atom
---
# Definition

If $X$ and $Y$ are topological spaces, a *homeomorphism* from $X$ to $Y$ is a bijective map:

$$
\varphi: X\to Y
$$
such that both $\varphi$ and $\varphi^{-1}$ are continuous. If there exists a homeomorphism between two topological spaces (for example here between $X$ and $Y$), we say that $X$ and $Y$ are ***homeomorphic*** or ***topologically equivalent***. Sometimes abbreviated $X \approx Y$.

> [!IMPORTANT]
    > Homeomorphic is an equivalence relation on the class of all topological spaces

The homeomorphism relation is the most fundamental relation in topology (the notion of sameness between two spaces is of course of this importance). In fact what we consider topological property, is something that is preserved by homeomorphisms. 

**Theorem:**
Let $(X_{1},\mathcal{T}_{1})$ and $(X_{2},\mathcal{T}_{2})$ be topological spaces and let $f: X_{1}\to X_{2}$ be a bijective map. Show that $f$ is a homeomorphism if and only if $f(\mathcal{T}_{1}) = \mathcal{T}_{2}$  in the sense that, $U \in \mathcal{T}_{1}$ if and only if $f(U)\in \mathcal{T}_{2}$.

**Proof:**
- [ ] Proof is to be written later.

**Theorem:**
Suppose $f: X\to Y$ is a homeomorphism and $U \subseteq X$ is an open subset. $f(U)$ is open in $Y$ and the restriction $f|_{U}$ is a homeomorphism from $U$ to $f(U)$.

**Proof:**
- [ ] Left for later on

If we take into account [[Finer and Courser Topologies|Finer and Courser Topologies]] one can find the following theorem:

**Theorem:**
Let $\mathcal{T}_{1}$ and $\mathcal{T}_{2}$ be topologies on the same set $X$. The identity map of $X$ is continuous as a map from $(X,\mathcal{T}_{1})$ to $(X,\mathcal{T}_{2})$ if and only if $\mathcal{T}_{1}$ is finer than $\mathcal{T}_{2}$, and is a homeomorphism if and only if $\mathcal{T}_{1} = \mathcal{T}_{2}$.

**Proof:**
- [ ] Left for later

- [[../List of Homeomorphism]]

> [!IMPORTANT]
    > In the definition of homeomorphism, it is important to note that although the assumption that $\varphi$ is bijective guarantees that the inverse map $\varphi^{-1}$ exists for set theoretic reasons, continuity of $\varphi^{-1}$ is not automatic

**A good example for the important callout above:**
Let $X$ be the half-open interval $[0,1)\subseteq \mathbb{R}$, and let $\mathbb{S}^{1}$ be the unit circle in $\mathbb{C}$ (both with their Euclidean metric topologies as usual). Define a map $a:X\to \mathbb{S}^{1}$ by $a(s) = e^{2\pi i s}$. Show that $a$ is continuous and bijective but not a homeomorphism.

---

- [[Open Map]]
- [[Local Homeomorphism]]