---
sticker: lucide//atom
---
# Basics
“The laws of thermodynamics are based on observations of macroscopic bodies, and encapsulate their thermal properties.” (Kardar, p. 35)

“As we shall demonstrate, for discussing equilibrium properties of a macroscopic system, full knowledge of the behavior of its constituent particles is not necessary.” (Kardar, p. 35)

“Statistical mechanics is thus an inherently probabilistic description of the system, and familiarity with manipulations of probabilities is an important prerequisite.” (Kardar, p. 35)

“The entity under investigation is a random variable x, which has a set of possible outcome $\mathcal S \equiv \{x_1,x_2,\dots\}$ . The outcomes may be discrete as in the case of a coin toss, $\mathcal S_{\text{coin}} = \{\text{head}, \text{tail}\}$ , or a dice throw, $\mathcal S_\text{coin} = \{1,2,3,4,5,6\}$ , or continuous as for the velocity of a particle in a gas, $S_{\vec v} = \{-\infty < v_x,v_y,v_z <\infty\}$, or the energy of an electron in a metal at zero temperature,$\mathcal S_\epsilon = \{0 \leq \epsilon\leq \epsilon_F\}$ . An event is any subset of outcomes $E\subset \mathcal S$, and is assigned a probability $p(E)$.” ([Kardar, p. 35](zotero://select/library/items/M9RXQI74)) ([pdf](zotero://open-pdf/library/items/WDMIC9R3?page=47&annotation=AGLTW4VC))


Axiomatically:
1. *Positivity:* $p(E) \geq 0$, that is, all probabilities must be real and non-negative.
2. *Additivity:* $p(A \lor B) = p(A) + p(B)$, if $A$ and $B$ are disconnected events.
3. *Normalization*: $p(\mathcal S) = 1$, that is, the random variable must have some outcome in $\mathcal S$.

## Objective probabilities

Objective probabilities are obtained experimentally from the relative frequency of the occurrence of an outcome in many tests of the random variable. If the random process is repeated $N$ times, and the event $A$ occurs $N_A$ times, then:

$$
p(A) = \lim_{N\rightarrow \infty} \frac{N_A}{N}
$$

## Subjective probabilities

Subjective probabilities provide a theoretical estimate based on the uncertainties related to lack of precise knowledge of outcomes.