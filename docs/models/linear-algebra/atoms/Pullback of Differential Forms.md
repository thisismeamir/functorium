---
sticker: lucide//atom
---
## Pullback of Differential Forms

The pullback operation allows us to transport differential forms between manifolds via smooth maps. This is crucial for relating geometry and analysis on different spaces.

### Definition of the Pullback Operator

Let *f: M → N* be a smooth map between two manifolds *M* and *N*. Let ω be a k-form on *N*, and let *X* be a vector field on *M*. The pullback operator, denoted by *f<sup>*</sup>*, maps differential forms from *N* to *M*:

$$
f^* : T^*(N) \rightarrow T^*(M)
$$

The pullback of ω is defined such that for any point *p ∈ M* and vectors *v<sub>1</sub>, ..., v<sub>k</sub> ∈ T<sub>p</sub>M*:

$$
(f^*ω)(v_1, ..., v_k) = ω(df(v_1), ..., df(v_k))
$$

where *df(v)* denotes the pushforward of the vector *v* by the map *f*.  Equivalently, it can be defined via the pullback of vector fields: If *Y* is a vector field on *N*, then *f<sup>*</sup>Y = Y ∘ f*, and *f<sup>*</sup>ω(v<sub>1</sub>, ..., v<sub>k</sub>) = ω(f<sup>*</sup>v<sub>1</sub>, ..., f<sup>*</sup>v<sub>k</sub>)*.

### Pulling Back a Form Along a Map

Consider the map *f: ℝ² → ℝ³* given by *f(x, y) = (x², y²)*. Let ω be the 1-form on ℝ³ defined as *ω = z dx + x dy*. Then the pullback of ω to ℝ² is:

$$
f^*ω = (x²) dx + (y²) dy
$$

This demonstrates how the form's components are transformed according to the map.

### Properties of the Pullback Operator

*   **Linearity:** *f<sup>*</sup>(aω + bζ) = a f<sup>*</sup>ω + b f<sup>*</sup>ζ* for any scalars *a, b* and forms ω, ζ.
*   **Functoriality:**  If *g: N → P* is another map, then *(g ∘ f)^* = g^*f<sup>*</sup>*. This means the order of pullbacks matters.

### Geometric Interpretation of Pullback

The pullback can be viewed as a coordinate transformation for differential forms. When we change coordinates on a manifold, the components of a form transform according to the Jacobian matrix of the coordinate map. The pullback operator encapsulates this transformation rule in a concise manner.