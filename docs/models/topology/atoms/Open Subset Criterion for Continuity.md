---
sticker: lucide//atom
---
# Open Subset Criterion for Continuity

Let *f*: *X* → *Y* be a function between topological spaces *(X, τ)* and *(Y, σ)*.  The function *f* is continuous if and only if the inverse image of every open set in *Y* is an open set in *X*.

Formally:

$$ f^{-1}(V) \in τ $$

for all $V \in σ$.

Here, $f^{-1}(V)$ denotes the preimage of *V*, defined as:

$$ f^{-1}(V) = \{ x \in X \mid f(x) \in V \} $$

This criterion provides an alternative to the $\epsilon$-$\delta$ definition of continuity for functions between metric spaces, and generalizes it to arbitrary topological spaces.