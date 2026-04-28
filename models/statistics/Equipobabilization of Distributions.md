This is a genuinely interesting foundational question. Let me think through it carefully.

## The Core Idea

You're asking: given any probability space $(\Omega, \mathcal{F}, P)$, can we always find a "re-encoding" into an equiprobable space $(\Omega', \mathcal{F}', P')$ where $P'$ is uniform, plus some structure that recovers the original probabilities?

The answer is **yes**, and there are several ways to do it — each with different flavors and usefulness.

---

## Construction 1: The Unit Interval (Classic)

The most well-known version of this is the **Borel isomorphism / uniform representation theorem**:

> For any atomless probability space $(\Omega, \mathcal{F}, P)$, there exists a measurable bijection to $([0,1], \mathcal{B}, \lambda)$ where $\lambda$ is the Lebesgue (uniform) measure.

So $[0,1]$ with uniform measure _is_ your universal equiprobable space. The "structure" is the measurable map $\phi: \Omega \to [0,1]$, and you recover events via preimages $\phi^{-1}$.

This already works as a theory — it's the foundation of **inverse CDF / quantile methods** in simulation.

---

## Construction 2: Your "New Elementary Events" Framing

You can make this more explicit. Given $(\Omega, \mathcal{F}, P)$, define:

$$\Omega' = {(\omega, u) : \omega \in \Omega,\ u \in [0, P({\omega})]}$$

for discrete spaces, where each original elementary event $\omega$ with probability $p_\omega$ gets "inflated" into a continuous interval of length $p_\omega$. Then:

- $\Omega'$ carries uniform measure on $[0,1]$
- The map $\pi: \Omega' \to \Omega$ given by $\pi(\omega, u) = \omega$ is the "structure"
- $P(A) = \lambda(\pi^{-1}(A))$ for all events $A$

This is essentially the **probability integral transform**, recast constructively.

For continuous distributions, the structure is just the CDF: $\phi(\omega) = F(\omega)$, and the new elementary events are points in $[0,1]$.

---

## Construction 3: A Category-Theoretic View

You can formalize this as a **functor** between categories:

- Objects: probability spaces
- Morphisms: measure-preserving maps

The "equiprobabilization" is a functor $E$ sending every space to $([0,1], \lambda)$, with the CDF/quantile map as the natural transformation. The "structure" lives in the morphism, not the space itself.

This is related to the **Giry monad** and categorical probability theory.

---

## When Does It Fail or Get Subtle?

|Case|Issue|
|---|---|
|Spaces with **atoms** (point masses)|You need to "split" atoms — intervals replace points|
|**Discrete finite** spaces|Works perfectly; just partition $[0,1]$ into intervals|
|Non-measurable sets|The isomorphism requires measurability assumptions|
|**Conditional probability**|Structure must track the fiber, not just the base|

The atomic case is the interesting one — it forces you to introduce a continuous "sub-structure" even for inherently discrete problems, which can feel unnatural.

---

## Is It Useful?

**Yes, in several concrete ways:**

1. **Monte Carlo simulation** — this is exactly what inverse CDF sampling does. Every random variable is simulated by pushing a uniform draw through $F^{-1}$.
    
2. **Coupling arguments** — representing two distributions on a common uniform space lets you compare them directly (e.g. proving stochastic dominance).
    
3. **Optimal transport** — Monge/Kantorovich problems are essentially about finding the _best_ structure map $\phi$ between the uniform space and target, under a cost.
    
4. **Information theory** — entropy measures how "non-uniform" a distribution is; your construction quantifies the structural complexity needed to encode the deviation from uniformity.
    
5. **Randomness extraction** — in theoretical CS, extractors convert weak random sources into near-uniform bits. Your framework is precisely the theoretical underpinning.
    

---

## What Would Make This a Novel Theory?

The classical machinery covers the existence of such maps. What's _less_ developed is a **systematic algebra of the "structure maps"** themselves — e.g.:

- When do two different probability spaces have _isomorphic_ structure maps?
- Can you compose structure maps to relate non-uniform spaces to each other via the uniform space as an intermediary?
- What's the minimal complexity of the structure needed to represent a given distribution?

That last question connects to **Kolmogorov complexity** and might be the most fertile direction if you want to develop something genuinely new.