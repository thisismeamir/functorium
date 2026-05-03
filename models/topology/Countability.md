# Motivation

In topology as well as other areas of mathematics, we deal with a lot of infinite sets. However, as we will gradually discover, some infinite sets are bigger than others. Countably infinite sets, while infinite, are "small" in a very definite sense. In fact they are the smallest infinite sets. Countable sets are convenient to work with because you can list their elements, making it possible to do inductive proofs, for example.


# Counting

The subject of countability and uncountability is about the sizes of sets, and how we compare those sizes. This is something you probably take for granted when dealing with finite sets.

When dealing with infinite sets you cannot just count both sets and describe their sizes with integers you then can compare. 

**Definition:** Given two sets $A$ and $B$, 

- We say $A$ has the same cardinality as $B$ if there exists a bijection $f: A\to B$. This is usually denoted by $|A| =|B|$.
- We say that $A$ has cardinality smaller than or equal to $B$ if there exists an injection $f:A\to B$, or equivalently if there exists a surjection $g:B\to A$. This is usually denoted by $|A| \leq |B|$.
- If there is an injection $f:A\to B$ and there is no surjection from $A$ to $B$, we say that $A$ has smaller cardinality than $B$, and write $|A|<|B|$.
