---
sticker: lucide//atom
---
# The Kolmogorov Quotient

[[Topologically Distinguishable|Topological indistinguishability]] of points is an [[../set-theory/Equivalence Relation|Equivalence Relation]]. No matter what topological space $X$ might be to begin with, the [[Quotient Space (Topology)]] under this equivalence relation is always $\mathrm{T}_{0}$. This quotient space is called the Kolmogorov quotient of $X$, which we will denote $\mathrm{KQ}(X)$. 

Of course, if $X$ was $\mathrm{T}_{0}$ to begin with, then $\mathrm{KQ}(X)$ and $X$ are naturally homeomorphic. Categorically, Kolmogorov spaces are a reflective subcategory of topological spaces, and the Kolmogorov quotient is the reflector.

Topological spaces _X_ and _Y_ are **Kolmogorov equivalent** when their Kolmogorov quotients are homeomorphic. Many properties of topological spaces are preserved by this equivalence; that is, if _X_ and _Y_ are Kolmogorov equivalent, then _X_ has such a property if and only if _Y_ does. On the other hand, most of the _other_ properties of topological spaces _imply_ $\mathrm{T}_{0}$-ness; that is, if _X_ has such a property, then _X_ must be $\mathrm{T}_{0}$. Only a few properties, such as being an [indiscrete space](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/Indiscrete_space "Indiscrete space"), are exceptions to this rule of thumb. Even better, many [structures](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/Structure_\(mathematics\) "Structure (mathematics)") defined on topological spaces can be transferred between $X$ and $\mathrm{KQ}(X)$. The result is that, if you have a non-$\mathrm{T}_{0}$ topological space with a certain structure or property, then you can usually form a $\mathrm{T}_{0}$ space with the same structures and properties by taking the Kolmogorov quotient.