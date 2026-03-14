# Voltage and Current Laws
---
**Table of Content**
```toc
    style: number
    min_depth: 1
    max_depth: 6
```
---
## Nodes, Paths, Loops and Branches
Let’s focus our attention on the current–voltage relationships in simple networks of two or more circuit elements. The elements will be connected by wires (sometimes referred to as “leads”), which have zero resistance. Since the network then appears as a number of simple elements and a set of connecting leads, it is called a lumped-parameter network. A more difficult analysis problem arises when we are faced with a distributed-parameter network, which contains an essentially infinite number of vanishingly small elements. We will concentrate on lumped-parameter networks in this text.
> A point at which two or more elements have connect is called a **node**


> Suppose that we start at one node in a network and move through a simple element to the node at the other end. We then continue from that node through a different element to the next node, and continue this movement until we have gone through as many elements as we wish. If no node was encountered more than once, then the set of nodes and elements that we have passed through is defined as a ***path***. If the node at which we started is the same as the node on which we ended, then the path is, by definition, a closed path or a **Loop***

## Kirchhof's Current Law and Voltage Law
### Current Law
> The algebraic sum of  the currents entering any node  is zero.

This law represents a mathematical statement of the fact that charge cannot accumulate at a node. A node is not a circuit element, and it certainly cannot store, destroy, or generate charge. Hence, the currents must sum to zero.

### Voltage Law
Current is related to the charge flowing through a circuit element, whereas voltage is a measure of potential energy difference across the element. These are often confused early on as a student learns circuit analysis, for some reason. There is a single unique value for any voltage in circuit theory. Thus, the energy required to move a charge from point A to point B in a circuit must have a value independent of the path chosen to get from A to B (there is often more than one such path). We may assert this fact through Kirchhoff’s voltage law (abbreviated KVL):
> The algebraic sum of the voltages around any closed path is zero.

## Single Loop Circuits
All of the elements in a circuit that carry the same current are said to be connected in series.
==Note that elements may carry equal currents and not be in series; two 100 W light bulbs in neighboring houses may very well carry equal currents, but
they certainly do not carry the same current and are not connected in series.==

- from simple conservation of energy, we expect that the sum of the absorbed power for each element of a circuit should be zero. In other words, at least one of the quantities should be negative (neglecting the trivial case where the circuit is not operating). Stated another way, the sum of the supplied power for each element should be zero. More pragmatically, the sum of the absorbed power equals the sum of the supplied power, which seems reasonable enough at face value.

## The Single-Node-Pair Circuit
> Elements in a circuit having a common voltage across them are said to be connected in parallel.

## Series and Parallel Connected Sources
![[Pasted image 20211020222925.png]]
It turns out that some of the equation writing that we have been doing for series and parallel circuits can be avoided by combining sources. Note, however, that all the current, voltage, and power relationships in the remainder  of the circuit will be unchanged. For example, several voltage sources in series may be replaced by an equivalent voltage source having a voltage equal to the algebraic sum of the individual sources. Parallel current sources may also be combined by algebraically adding the individual currents, and the order of the parallel elements may be rearranged as desired.

combining voltage sources in parallel and current sources in series is not possible because of physical impossibility.

## Resistors in Series and Parallel
It is often possible to replace relatively complicated resistor combinations with a single equivalent resistor. This is useful when we are not specifically interested in the current, voltage, or power associated with any of the individual resistors in the combinations. All the current, voltage, and power relationships in the remainder of the circuit will be unchanged.

for resistors in series we have:
$$ 
v_s =\sum_i v_i
$$
$$
v_s = \sum_j R_ji = i\sum_j R_j
$$
therefore series of resistors can be written as one resistor which is equal to:
$$
R_{eq} = \sum_jR_j
$$
for resistors in parallel since:
$$ i_s = \sum_j\frac{v}{R_j}$$
$$ \frac1{R_{eq}} = \sum_j \frac{1}{R_j}$$

## Voltage and Current Division

Using the way we find:
$$
i = \frac v{R_1+R_2}
$$ 
thus:
$$ v_2 = iR_2 = (\frac v {R_1+R_2})R_2$$
or more generally we can write:
$$
v_k = \frac{R_k}{\sum_n R_n}v
$$
also there is a similar approach to find the current in a parallel resistors situation:
$$
i_2 = \frac v{R_2} = \frac{iR_1\parallel R_2}{R_2} = \frac i{R_2}\frac{R_1R_2}{R_1+R_2}
$$
or more generally:
$$
i_k = i \frac{\frac1{R_k}}{}