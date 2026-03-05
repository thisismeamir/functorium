---
sticker: lucide//atom
---
# Differential Forms And this Follows

Differential forms are an essential part of modern mathematics and physics formulations. One of the principal applications of Differential forms in modern mechanics is the mathematical description of observables: *infinitesimal measurements, which, when integrated, yield a value that can be verified through real world experiments, at least in principle*.[^1]

Differential forms are a natural choice when one requires that measurements satisfy:

1. **Covariance, that is invariance under coordinate transformation**
2. **Covariance under differentiation, which is crucial since the time evolution of most systems is described by differential equations**
3. **Measurements are obtained by integration from the infinitesimal quantities employed to describe time evolution**

The first implies that differential forms have to be tensors, objects whose physical manifestation does not change under coordinate transformations, and the second requirement implies that these have to be anti-symmetric, leading to differential forms, anti-symmetric tensors that are ready to be integrated.

> Thus, differential forms can be seen as a modern formulation of classical infinitesimals.

Differential forms utility mostly comes from exterior calculus, the calculus of differential or exterior forms, that provides the operators for working with forms, such as the [[Wedge Product]] and [[Exterior Derivative]].

Exterior calculus can be thought of as a generalization of vector calculus in $\mathbb{R}^{3}$. But in contrast to it, exterior calculus is defined on arbitrary dimensional, possibly curved manifolds, and even in $\mathbb{R}^{3}$ it elucidates much of the structure that is obfuscated in classical vector calculus.

- [[Model of Exterior Algebra]]
- [[Model of Exterior Calculus]]

Differential forms are not only useful in mathematical descriptions of mechanics in continuum but also there have been found use for them in numerical computation as well. For example you can check out [Finite element exterior calculus: from Hodge theory to numerical stability](https://www.ams.org/journals/bull/2010-47-02/S0273-0979-10-01278-4/home.html)
and [Discrete Differential Forms for Computational Modeling](http://portal.acm.org/citation.cfm?id=1198666).

## Differential Forms in $\mathbb{R}^{3}$ 

Differential forms are naturally defined on manifolds, and this provides on of the most important advantages of the concept compared to the classical formalism of vector calculus. 

**1-Forms**: A 1-form $\alpha \in \Omega^{1}(\mathbb{R}^{3})$ can be thought of as a vector-valued object that is naturally integrated along


[^1]: C. Lessig, ‘A Primer on Differential Forms’, May 20, 2012, _arXiv_: arXiv:1206.3323. doi: [10.48550/arXiv.1206.3323](https://doi.org/10.48550/arXiv.1206.3323).
