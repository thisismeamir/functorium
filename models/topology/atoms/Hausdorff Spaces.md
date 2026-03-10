---
sticker: lucide//atom
---
# Hausdorff Spaces

The definition of topological spaces is wonderfully flexible, and can be used to describe a rich assortment of concepts of "space". However, without further qualification, arbitrary topological spaces are far too general for most purposes, because they include some spaces whose behavior contradicts many of our basic spatial intuitions.

The problem with these spaces is that there are too few open subsets, so neighborhoods do not have the same intuitive meaning they have in metric spaces. 

A Topological space $X$ is said to be a *Hausdorff space* if given any pair of distinct points $p_{1},p_{2}\in X$, there exist neighborhoods $U_{1}$ of $p_{1}$ and $U_{2}$ of $p_{2}$ with $U_{1} \cap U_{2} = \emptyset$. 

> *Points can be separated by open subsets*

---

## Examples
![[../../../attachments/Pasted image 20260309224034.png]]![[../../../attachments/Pasted image 20260309224048.png]]

[[atoms/Non-Hausdorff Spaces]]

Because every metric space is Hausdorff, it follows that these spaces are not metrizable. 

**Proposition**
Let $X$ be a Hausdorff space.
- Every finite subset of $X$ is closed.
- If a sequence $(p_{i})$ in $X$ converges to a limit $p \in X$, the limit is unique.
