---
sticker: lucide//atom
---
# Cauchy Surfaces and Global Hyperbolicity

A Cauchy surface provides a complete snapshot of spacetime, allowing for prediction of events everywhere. Spacetimes possessing such surfaces are termed globally hyperbolic, signifying a high degree of predictability.

## Cauchy Surface Definition

A closed achronal surface *l* is defined as a **Cauchy surface** if its domain of dependence, $D(l)$, encompasses the entire manifold *M*:

$$D(l) = M$$

This condition implies that every point in spacetime can be influenced by information originating from events on the Cauchy surface *l*.  Conversely, any event on *l* can influence all points in spacetime.

## Global Hyperbolicity

A spacetime *M* is said to be **globally hyperbolic** if it possesses a Cauchy surface. The existence of a Cauchy surface guarantees that the spacetime's causal structure is well-behaved and allows for consistent predictions about future events given knowledge of past events on the surface.

## Implications

*   **Predictability:**  If a spacetime is globally hyperbolic, knowing the state of affairs on the Cauchy surface *l* at one time allows complete determination of the state of affairs everywhere in spacetime at all times.
*   **Well-Posedness of Initial Value Problems:** Global hyperbolicity ensures that initial value problems are well-posed, meaning solutions exist and depend continuously on initial data.
*   **Absence of Closed Timelike Curves (CTCs):**  Globally hyperbolic spacetimes generally do not contain closed timelike curves (CTCs), which would violate causality and make prediction impossible. While the absence of CTCs is *necessary* for global hyperbolicity, it's not sufficient; a spacetime can lack CTCs but still not be globally hyperbolic.

---

Any set $\Sigma$ that is closed, achronal, and has no edge, is called a **Partial Cauchy Surface**. A partial Cauchy surface can fail to be an actual Cauchy surface either through its own fault of through a fault of the spacetime. One possibility is that we have just chosen a bad hypersurface. 
 
A somewhat non-trivial way for a Cauchy horizon to arise is through the appearance of **closed timelike curves**. In [[../../classical-mechanics/Model of Newtonian Framework|Newtonian Framework]], causality is enforced by the relentless forward march of an [[../../classical-mechanics/atoms/Absolute Time|Absolute Time]]. In special relativity things are even more restrictive; not only must you move forward in time, but the speed of light provides a limit on how swiftly you may move through space.

In general relativity it remains true that you must stay within your forward light cone; however, this becomes strictly a local notion, as globally the curvature of spacetime might "tilt" light cones from one place to another. It becomes possible in principle for light cones to be sufficiently distorted that an observer can move on a forward directed path that is everywhere timelike and yer intersects itself at a point in its "past". This is a closed timelike curve. A good, mathematical example of this (that is an actual GR solution) is the [[Misner Space]].


