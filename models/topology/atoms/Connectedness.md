---
sticker: lucide//atom
---
# Definition

A topological space is said to be connected if it is not the union of two disjoint nonempty open sets. A set is open if it contains no point lying on its boundary; thus, in an informal, intuitive sense, the fact that a space can be partitioned into disjoint open sets suggests that the boundary between the two sets is not part of the space, and thus splits it into separate pieces.

A Connected space is a topological space that cannot be represented as the union of two or more disjoint non-empty open subsets. Connectedness is one of the principal topological properties that distinguish topological spaces.

# Formal Definition

A topological space $X$ is said to be disconnected if it is the union of two disjoint non-empty open sets. Otherwise, $X$ is said to be connected. A subset of a topological space is said to be connected if it is connected under its subspace topology. 

**Proposition**
For a topological space $X$ the following are equivalent:

- $x$ is connected, that is, it cannot be divided into two disjoint non-empty open sets.
- The only subsets of $X$ which are both open and closed are $X$ and empty set.
- The only subsets of $X$ with empty boundary are $X$ and the empty set.
- $X$ cannot be written as the union of two non-empty separated sets.
- All continuous functions from $X$ to $\{ 0,1 \}$ are constant, where $\{ 0,1 \}$ is the two-point space endowed with [[atoms/Discrete Topology|Discrete Topology]].
- All discrete-valued continuous maps on $X$ are constant.

# Other forms of Connectedness 

- [[Path Connectedness]]


# Theorems 

- [[atoms/Main Theorem of Connectedness]]
- Every path-connected space is connected.
- In a locally path-connected space, every open connected set is path-connected.
- Every locally path-connected space is locally connected.
- A locally path-connected space is path-connected if and only if it is connected.
- The closure of a connected subset is connected. Furthermore, any subset between a connected subset and its closure is connected.
- The connected components are always [closed](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/Closed_set "Closed set") (but in general not open)
- The connected components of a locally connected space are also open.
- The connected components of a space are disjoint unions of the path-connected components (which in general are neither open nor closed).
- Every [quotient](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/Quotient_space_\(topology\) "Quotient space (topology)") of a connected (resp. locally connected, path-connected, locally path-connected) space is connected (resp. locally connected, path-connected, locally path-connected).
- Every [product](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/Product_topology "Product topology") of a family of connected (resp. path-connected) spaces is connected (resp. path-connected).
- Every open subset of a locally connected (resp. locally path-connected) space is locally connected (resp. locally path-connected).
- Every [manifold](zim://6112eb33-9137-7530-79f2-04ea02fbb402.zim/Manifold "Manifold") is locally path-connected.
- Arc-wise connected space is path connected, but path-wise connected space may not be arc-wise connected
- Continuous image of arc-wise connected set is arc-wise connected.

# Simply Connected

A **loop** in a topological space $X$ is a continuous map $f:[0,1]\to X$ such that $f(0)=f(1)$. If any loop in $X$ can be continuously shrunk to a point then $X$ is called simply connected.