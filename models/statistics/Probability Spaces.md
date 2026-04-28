# Probability

**Definition:** A measure space $(\Omega, \mathcal{F}, \mu)$ in which $\mu(\Omega)=1$ is called a ***probability space***: in this case, we usually use the letter $P$ instead of $\mu$ and say that $P$ is a probability measure.

In a probability space $(\Omega, \mathcal{F}, P)$, each element $\omega \in \Omega$ is called an **outcome**; each $A \in \mathcal{F}$ is called an **event**, and the number $P(A)$ is called **probability of** $A$.

Moreover, we say that $\Omega$ is the sample space and $\mathcal{F}$ is the $\sigma$-algebra of events.

## Discrete and Continuous Probabilities

When $\Omega$ is finite or countable, we always assume $\mathcal{F}=\mathcal{P}(\Omega)$ and say that $(\Omega, \mathcal{P}(\Omega), P)$ or more simply $(\Omega,P)$ is a discrete probability space. If instead $\Omega$ is uncountable, we speak of a continuous (or general) probability space.

This explains why mathematically we have defined an event a a subset of $\Omega$. In particular, an event with a single outcome is called an *elementary event*.


---

**Remark:** The sample space $\Omega$ is, by definition, a generic non-empty set; it is legitimate to ask what sense it makes to assume such a degree of generality. In fact, we will see that in classic problems, $\Omega$ will simply be a finite set or the Euclidean space $\mathbb{R}^{d}$. However, in the most interesting applications, it may also happen that $\Omega$ is a functional space. Often, $\Omega$ will also have a certain structure, for example, that of a metric space, to have some useful tools for development of the theory.

---

## Uniform Probability

Let $\Omega$ be finite. For each $A \subseteq \Omega$, let $|A|$ denote the cardinality of $A$ and set
$$
P(A)=\frac{|A|}{|\Omega|}
$$
Then $P$ is a probability measure, called uniform probability. By definition, we have:

$$
P(\{ \omega \})=\frac{1}{|\Omega|}, \omega \in \Omega
$$
that is, each outcome is equiprobable. The uniform probability corresponds to the classical concept of probability according to Laplace.


I've had an idea here about some new mathematical theory:
- [[Equipobabilization of Distributions]]

---

**Remark:** In a discrete probability space, consider the function:

$$
p: \Omega \to[0,1], p(\omega) = P(\{ \omega\}), \omega \in \Omega
$$
It is clear that $p$ is a non-negative function that has the property

$$
\sum _{\omega \in \Omega}p(\omega)= \sum _{\omega \in \Omega}P(\{ \omega \}) = P(\Omega) =1
$$
Note that the sums in this equation are series without non-negative terms and therefore, their value does not depend on the order of the addends. The second quality in it is a consequence of the $\sigma$-additivity of $P$.

In fact, there is a bijective relationship between $p$ and $P$ in the sense that, given any non-negative function $p$ such that $\sum _{\omega \in \Omega}p(\omega)=1$, and setting:
$$
P(A)\coloneqq\sum _{\omega \in A}p(\omega), A\subseteq \Omega
$$
then $P$ is a discrete probability on $\Omega$.
*In other words, a discrete probability is uniquely defined by the probabilities of individual elementary events.*

---

## Negligible and Almost Certain Sets

**Definition:** In a probability space, we say that:
- A subset $N$ of $\Omega$ is negligible for $P$ if $N\subseteq A$ with $A\in \mathcal{F}$ such that $P(A)=0$;
- A subset $C$ of $\Omega$ is almost certain for $P$ if its complement is negligible or, equivalently, if there exists $B\in \mathcal{F}$ such that $B\subseteq C$ and $P(B)=1$.