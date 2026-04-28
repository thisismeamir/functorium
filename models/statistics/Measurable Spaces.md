# Measurable Spaces

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

**Remark:** From the properties of $\mathcal{F}$ it also follows that if $A, B \in \mathcal{F}$ then $A \cup B \in \mathcal{F}$, that is, $\mathcal{F}$ is $\cup$-closed. In fact, given $A, B\in \mathcal{F}$, one can construct the sequence $C_{1}=A$, $C_{n}=B$ for every $n\geq 2$; then

$$
A \cup B = \bigcup_{n=1}^{\infty} C_{n} \in \mathcal{F}
$$
Obviously $\Omega, \emptyset \in \mathcal{F}$ since by definition $A, A^{c}\in \mathcal{F}$ and so it $A \cup A^{c}= \Omega$ and thus so is the complement of $\Omega$, which is the empty set.

We also note that the finite or countable intersection of elements of a $\sigma$-algebra $\mathcal{F}$ belongs to it as well. In fact if $(A_{n})$ is a finite or countable family in $\mathcal{F}$, combining the properties above get us:

$$
\bigcap_{n} A_{n} = \left( \bigcup_{n} A_{n}^{c} \right)^{c} \in \mathcal{F}
$$
as a consequence, we say that $\mathcal{F}$ is $\cap$-closed and $\sigma$-$\cap$-closed.

## Measure

**Definition:** A measure on the measurable space $(\Omega,\mathcal{F})$ is a function:

$$
\mu:\mathcal{F}\to [0,+\infty]
$$

such that:
- $\mu(\emptyset) =0$
- $\mu$ is $\sigma$-additive on $\mathcal{F}$, that is, for every sequence $(A_{n})_{n \in \mathbb{N}}$ of disjoint elements of $\mathcal{F}$ we have:

$$
\mu \left( \bigcup_{n=1}^{\infty} A_{n} \right)= \sum _{n=1}^{\infty}\mu(A_{n}). 
$$

**Remark:** Every measure $\mu$ is additive in the sense that, for every *finite* family $(A_{n})_{n \in \mathbb{N}}$ of disjoint sets in $\mathcal{F}$ we have:

$$
\mu \left( \bigcup_{k=1}^{n}A_{k} \right) = \sum _{k=1}^{n}\mu (A_{k})
$$

**Definition:** A measure $\mu$ on a measurable space $(\Omega, \mathcal{F})$ is said to be finite if $\mu(\Omega)<\infty$ and is said to be $\sigma$-finite if there exists a sequence $(A_{n})$ in $\mathcal{F}$ such that:

$$
\Omega = \bigcup_{n \in \mathbb{N}}A_{n} \text{ and } \mu(A_{n})< +\infty, n \in \mathbb{N}
$$