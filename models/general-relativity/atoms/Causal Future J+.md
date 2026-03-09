---
sticker: lucide//atom
---
# Causal Future $J^+(S)$

The causal future, denoted as $J^+(S)$, is a concept in general relativity that describes the region of spacetime influenced by a set of events. It represents all points that can be reached from a given set of initial events by light or anything traveling at or below the speed of light.

## Definition

Given a set of events *S* within a spacetime manifold $M$ with metric $g_{ab}$, the causal future $J^+(S)$ is defined as:

$$J^+(S) = \bigcup_{p \in S} I^+ (p)$$

where $I^+$ denotes the future light cone and $\bigcup$ represents the union over all points *p* in the set *S*.  In simpler terms, it's the collection of all future light cones emanating from each event within the set *S*.

## Mathematical Description

Mathematically, a point $x \in J^+(S)$ if there exists a null vector $\ell$ such that:

$$t_x - t_p = \sum_{a} \ell^a  g_{ap}$$

for some $p \in S$, where $t_x$ and $t_p$ are the coordinate times at points *x* and *p*, respectively, and $g_{ap}$ is the metric tensor. This equation states that there's a light ray (or slower-than-light signal) connecting point *p* in set *S* to point *x*.

## Properties

*   **Future-Pointing:**  $J^+(S)$ contains only points with coordinate time greater than or equal to the coordinate time of any event in *S*.
*   **Causal Set:** $J^+(S)$ is a causal set, meaning that if $x \in J^+(S)$ and $y$ is any point such that $x$ can causally influence $y$, then $y \in J^+(S)$.
*   **Closed under Causality:** If $x, y \in J^+(S)$, it does not necessarily follow that $y \in J^+(x)$. However, if *x* is in the future light cone of a point in *S*, then any event influenced by *x* must also be in the causal future of *S*.

## Relation to Other Concepts

*   **Future Light Cone:**  $J^+(S)$ generalizes the concept of a single point's future light cone. It represents the combined influence of multiple events.
*   **Causal Boundary:** The boundary of $J^+(S)$ consists of points that can be reached from *S* by signals traveling at the speed of light.
*   **Closed Timelike Curves (CTCs):**  The existence of CTCs can significantly alter the structure and properties of causal futures, potentially leading to violations of causality.

## Significance

Understanding $J^+(S)$ is crucial for:

*   **Causality Analysis:** Determining which events can influence others in a spacetime.
*   **Black Hole Physics:** Analyzing how information escapes (or doesn't) from black hole event horizons.
*   **Time Travel Scenarios:** Investigating the potential consequences of time travel and CTCs on causality.