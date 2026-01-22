---
sticker: lucide//atom
---
# Chronological Future I<sup>+</sup>(S)

The chronological future, denoted as $I^+(S)$, represents the set of all points in spacetime that can be reached from a given set of events *S* by timelike paths. It's a stricter notion than the causal future and is fundamental to understanding causality in general relativity.

## Definition

Given a set of events *S* within a spacetime manifold $M$ with metric $g_{ab}$, the chronological future $I^+(S)$ is defined as:

$$I^+(S) = \bigcup_{p \in S} I^+_t(p)$$

where $I^+_t(p)$ denotes the future *timelike* light cone of point *p*.  This means that only paths traveling slower than or equal to the speed of light (i.e., timelike paths) are considered when determining what's in the chronological future.

## Mathematical Description

A point $x$ belongs to the chronological future $I^+(S)$ if there exists a timelike curve $\gamma(t)$ connecting a point $p \in S$ to $x$, such that:

$$\gamma(0) = p$$
$$\gamma(1) = x$$

and $\gamma'(t)$ is a timelike vector for all $t$. This condition ensures that the connection between *p* and *x* can be traversed by an object moving at or below the speed of light.

## Properties

*   **Timelike Paths Only:**  Unlike the causal future, $I^+(S)$ only considers paths that are timelike.
*   **Future-Pointing:** All points in $I^+(S)$ have coordinate time greater than or equal to the coordinate time of any point in *S*.
*   **Closed under Timelike Causality:** If $x \in I^+(S)$ and $y$ is a point that can be causally influenced by $x$ via a timelike path, then $y \in I^+(S)$.

## Relation to Other Concepts

*   **Causal Future:**  The chronological future is a subset of the causal future: $I^+(S) \subseteq J^+(S)$. The causal future includes paths that are both timelike and null (lightlike), while the chronological future only considers timelike paths.
*   **Chronological Boundary:** The boundary of $I^+(S)$ consists of points that can be reached from *S* by signals traveling at the speed of light, but not faster.
*   **Closed Timelike Curves (CTCs):**  The existence of CTCs significantly impacts the structure and properties of chronological futures, potentially creating regions where causality is violated.

## Significance

Understanding $I^+(S)$ is crucial for:

*   **Causality Preservation:** Defining a stricter notion of causal influence that excludes lightlike signals.
*   **Black Hole Physics:** Analyzing how information propagates within and around black holes, considering only timelike paths.
*   **Time Travel Scenarios:**  Investigating the potential paradoxes associated with time travel by restricting possible connections to timelike curves.