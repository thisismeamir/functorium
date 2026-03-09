---
sticker: lucide//atom
---

# Domain of Dependence & Cauchy Horizons

An achronal set is a subset of spacetime that exhibits a specific lack of temporal connection. The domain of dependence, built upon achronal sets, defines regions influenced by them, and Cauchy horizons mark boundaries where predictability breaks down.

## Achronal Sets

A subset $S \subseteq M$ (where *M* is a spacetime manifold) is considered **achronal** if no two points within *S* are connected by a timelike curve. This implies that events in an achronal set cannot causally influence each other directly through timelike paths.

## Domain of Dependence: $D^+(S)$ and $D^-(S)$

Given a closed achronal set *S*, we define its **future domain of dependence**, denoted $D^+(S)$, as follows:

$$D^+(S) = \{p \in M \;|\; \text{every past inextendible casual curve through } p \text{ must intersect } S\}$$

Here, "past inextendible casual curve" refers to a causal curve extending indefinitely into the past.  The condition means that any possible path from *p* back in time (allowing for light or slower speeds) *must* eventually reach *S*.

Similarly, the **past domain of dependence**, $D^-(S)$, is defined by replacing "future" with "past":

$$D^-(S) = \{p \in M \;|\; \text{every future inextendible casual curve through } p \text{ must intersect } S\}$$

This means any path from *S* into the future must pass through *p*.  Elements of *S* themselves are included within their respective domains of dependence.

## Cauchy Horizons: $H^+(S)$ and $H^-(S)$

The **boundary** between points that lie within a domain of dependence and those that do not is crucial. This boundary is defined as the **future Cauchy horizon**, $H^+(S)$, for $D^+(S)$:

$$H^+(S) = \partial D^+(S)$$

And the **past Cauchy horizon**, $H^-(S)$, for $D^-(S)$:

$$H^-(S) = \partial D^-(S)$$

**Cauchy horizons** represent points beyond which predictability fails.  Information from within *S* cannot influence regions past these horizons, and conversely, information from beyond the horizons cannot reach *S*. They mark limits on causal accessibility.

---

The set of all points for which can predict what happens by knowing what happens on $S$ is the union $D(s) = D^+(S)\cup D^-(S)$, called simply the domain of dependence. A closed achronal surface $\Sigma$ is said to be a [[Cauchy Surface]]