# Idea

In metric spaces, not all open subsets are created equal. Among open subsets, the open balls are the most fundamental (begin defined directly in terms of the metric), and all other open subsets are defined in terms of those. As a consequence most definitions and proofs focus on the open balls rather than arbitrary open subsets.

Most topological spaces do not come naturally equipped with any special open subset like the metric space. Nevertheless, in many specific situations, it is useful to single out a collection of certain open subsets, such that all other open subsets are unions of the selected ones.

# Definition

Let $X$ be a topological space. A collection $\mathcal{B}$ of subsets of $X$ is called a basis for the topology $X$ if the following two conditions hold:
- Every element of $\mathcal{B}$ is an open subset of $X$.
- Every open subset of $X$ is the union of some collection of elements of $\mathcal{B}$.
It is important to observe that the empty set is the union of the empty collection of elements of $\mathcal{B}$. If the topology on $X$ is understood, sometimes we will just say $\mathcal{B}$ is a basis for $X$.

## Basis Criterion 

If a subset $U \subseteq X$ satisfies the following statement, we say that it satisfies the basis criterion with respect to $\mathcal{B}$.

Suppose $X$ is a topological space, and $\mathcal{B}$ is a basis for its topology. A subset $U \subseteq X$ is open if and only if it satisfies:

for each $p \in U$, there exists $B \in \mathcal{B}$ such that $p \in B \subseteq U$.

# Continuity of Maps

When we have a basis for a topology it is sufficient and often easier to check continuity of maps into the topology using only basis subsets. Formally:

Let $X$ and $Y$ be topological spaces and let $\mathcal{B}$ be a basis for $Y$. A map $f:X\to Y$ is continuous if and only if for every basis subset $B \in \mathcal{B}$, the subset $f^{-1}(B)$ is open in $X$.

