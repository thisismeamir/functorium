# Measurable Spaces and Probability Spaces

Probability theory studies phenomena whose outcome is uncertain: these are called *random phenomena*. Trivial examples can be:

1. Tossing a coin
2. Drawing a card from a deck.

The outcomes of a random phenomena are not necessarily all *equivalent* in the sense that, for some reason, one outcome may be more probable than another. Note that, since by definition non of the possible outcomes can be rules out a priori, Probability theory does not aim to predict the outcome of a random phenomenon but to estimate, in the sense of measuring, the degree of reliability of the individual possible outcomes or the combination of some of them.

This is therefore, the reason that the toolkit of probability theory would be measure theory.

## Measurable Spaces

**Definition:** A *Measurable Space* is a pair $(\Omega, \mathcal{F})$ where:
- $\Omega$ is a non-empty set;
- $\mathcal{F}$ is a $\sigma$-algebra on $\Omega$, that is, $\mathcal{F}$ is a non-empty family of subsets of $\Omega$ that satisfy the following:
	- if $A \in \mathcal{F}$ then $A^{c}\coloneqq \Omega \setminus A \in \mathcal{F}$; (closed under complement)
	- the countable union of elements of $\mathcal{F}$ belongs to $\mathcal{F}$. (closed under countable union)