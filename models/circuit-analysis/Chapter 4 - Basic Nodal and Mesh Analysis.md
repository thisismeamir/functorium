# Basic Nodal and Mesh Analysis
---
**Table of Content**
```toc
    style: number
    min_depth: 1
    max_depth: 6
```
---
## Nodal Analysis
We begin our study of general methods for methodical circuit analysis by considering a powerful method based on KCL, namely nodal analysis.
We will now let the number of nodes increase and correspondingly provide one additional unknown quantity and one additional equation for each added node. An N-node circuit will need $(N − 1)$ voltages and $(N − 1)$ equations. Each equation is a simple ***KCL*** equation.

---
Consider the circuit below (a). First we simplify is a little bit so that unnecessary nodes disappear (b). then we choose a reference node, it can be any node we want (c) then we have to find oder nodes voltage difference with this reference node (d).
![[Pasted image 20211024103154.png]]

We now apply KCL to nodes 1 and 2. We do this by equating the total current entering the node to the total current leaving the node through the several resistors. Thus,
$$
3.1 = \frac {v_1}2 + \frac{v_1-v_2}5
$$
and at node 2:
$$
-(-1.4) = \frac{v_2}1 +\frac{v_2-v_1}5
$$
We have to equations and two unknowns so this could be easily solved and the voltage of each can be found easily.

==note at this point that there is more than one way to write the KCL equations for nodal analysis.== 

> Is one way better than any other? Every instructor and every student develops a personal preference, and at the end of the day the most important thing is to be consistent. The authors prefer constructing KCL equations for nodal analysis in such a way as to end up with all resistor terms on one side and all current source terms on the other. Specifically,

$$
\boxed{
\begin{equation}
\begin{split}
\sum & \text{currents leaving the node through resistors}
\\
&= \sum \text{currents entering the node from current sources}
\end{split}
\end{equation}
}
$$

### Summary of Nodal Analysis

1. **Select a reference node.** The number of terms in your nodal equations can be minimized by selecting the reference node as the one with the greatest number of branches connected to it.

2. **Count and label the voltage at each node in the circuit**, relative to the reference node you have selected.

3. **Write a KCL equation for each of the non-reference nodes.** Sum the currents flowing out of the node through resistors on one side of the equation. On the other side, sum the currents flowing into a node from sources. Pay close attention to minus signs.

4. **Express any additional unknowns in terms of appropriate nodal voltages.** This situation can occur if voltage sources or dependent sources appear in our circuit.

5. **Organize the equations**. Group terms according to nodal voltages.

6. **Solve the system of equations for the nodal voltages.**

## The Supernode
Imagine there is a voltage source that you cannot get rid of. For example consider nodes 2 and 3 in the figure below.
![[Pasted image 20211024111239.png]]
The easier method is to treat node 2, node 3, and the voltage source together as a supernode and apply KCL to both nodes at the same time; This is okay because if the total current leaving node 2 is zero and the total current leaving node 3 is zero, then the total current leaving the combination of the two nodes is zero. Note that any current defined within the supernode will simply cancel in our KCL expressions; for example, the current leaving node 2 will be equal and opposite to the current leaving node 3.

The concept of the supernode uses a more general definition for KCL.
> ==**KCL: The algebraic sum of the currents entering any node or closed surface is zero.**==

### Summary of Supernode Analysis
1. Select a reference node. The number of terms in your nodal equations can be minimized by selecting the reference node as the one with the greatest number of branches connected to it.

2. Count and label the voltage at each node in the circuit, relative to the reference node you have selected.

3. If the circuit contains voltage sources, form a supernode around each one. This is done by enclosing the source, its two terminals, and any other elements connected between the two terminals within a broken-line enclosure.

4. Write a KCL equation for each of the nonreference nodes and for each supernode that does not contain the reference node. Sum the currents flowing out of the node/supernode through resistors on one side of the equation. On the other side, sum the currents flowing into a node/supernode from sources. Pay close attention to minus signs.

5. Relate the voltage across each voltage source to nodal voltages. This is accomplished by simple application of KVL; one such equation is needed for each supernode defined.

6. Express any additional unknowns in terms of appropriate nodal voltages. This situation can occur if voltage sources or dependent sources appear in our circuit.

7. Organize the equations. Group terms according to nodal voltages.

8. Solve the system of equations for the nodal voltages.

## Mesh Analysis
Another way to do your circuit analysis is using the KVL. As we have seen, nodal analysis is a straightforward analysis technique when only current sources are present, and voltage sources are easily accommodated with the supernode concept. Still, Nodal Analysis is based on KCL but **Mesh Analysis** is based on KVL. Although only strictly speaking applicable to what we will shortly define as a planar circuit, it can in many cases prove simpler to apply than nodal analysis.

---
If it is possible to draw the diagram of a circuit on a plane surface in such a way that no branch passes over or under any other branch, then that circuit is said to be a ***planar circuit***.
![[Pasted image 20211024172607.png]]
Here (a) and (c) are planar while (b) is not.

- We define a mesh as a loop that does not contain any other loops within it.
![[Pasted image 20211024174018.png]]
take this as an example writing KVL for the left-hand mesh:
$$
-42+6i_1+3(i_1-i_2) = 0
$$
and right-hand mesh:
$$
-3(i_1-i_2) +4i_2 - 10 = 0
$$
solving these equations would easily lead to the currents you are trying to find; If our circuit contains M meshes, then we expect to have M mesh currents and therefore will be required to write M independent equations.
Now let us consider this same problem in a slightly different manner by using mesh currents. We define a mesh current as a current that flows only around the perimeter of a mesh. If we call the left-hand mesh of our problem mesh 1, then we may establish a mesh current i1 flowing in a clockwise direction about this mesh. A mesh current is indicated by a curved arrow that almost closes on itself and is drawn inside the appropriate mesh, as shown in Fig.
![[Pasted image 20211024174412.png]]
 
> A mesh current may often be identified as a branch current, as $i_1$ and $i_2$ have been identified in this example. This is not always true, however, for consideration of a square nine-mesh network soon shows that the central mesh current cannot be identified as the current in any branch.

### Summary of Basic Mesh Analysis
1. Determine if the circuit is a planar circuit. If not, perform nodal analysis instead.

2. Count and label each mesh current in the circuit. Redraw the circuit if necessary. Generally, defining all mesh currents to flow clockwise results in a simpler analysis.

3. Write a KVL equation around each mesh. Begin with a convenient node and proceed in the direction of the mesh current. Pay close attention to minus signs. If a current source lies on the periphery of a mesh, no KVL equation is needed since the mesh current is already defined!

4. Express any additional unknowns in terms of appropriate mesh currents. This situation can occur if current sources or dependent sources appear in our circuit.

5. Organize the equations. Group terms according to mesh currents.

6. Solve the system of equations for the mesh currents.

## Supermesh
A better technique is one that is quite similar to the supernode approach in nodal analysis. There we formed a supernode, completely enclosing the voltage source inside the supernode and reducing the number of nonreference nodes by 1 for each voltage source. Now we create a “supermesh” from two meshes that have a current source as a common element; the current source is in the interior of the supermesh. We thus reduce the number of meshes by 1 for each current source present. If the current source lies on the perimeter of the circuit, then the single mesh in which it is found is ignored. Kirchhoff’s voltage law is thus applied only to those meshes or supermeshes in the reinterpreted network.

### Summary of Super Mesh Analysis
1. Determine if the circuit is a planar circuit. If not, perform nodal analysis instead.

2. Count and label each mesh current in the circuit. Redraw the circuit if necessary. Generally, defining all mesh currents to flow clockwise results in a simpler analysis.

3. If the circuit contains current sources shared by two meshes, form a supermesh to enclose both meshes. A highlighted enclosure helps when writing KVL equations.

4. Write a KVL equation around each mesh/supermesh. Begin with a convenient node and proceed in the direction of the mesh current. Pay close attention to minus signs. If a current source lies on the periphery of a mesh, no KVL equation is needed since the mesh current is already defined!

5. Relate the current flowing from each current source to mesh currents. This is accomplished by simple application of KCL; one such equation is needed for each supermesh defined.

6. Express any additional unknowns in terms of appropriate mesh currents. This situation can occur if current sources or dependent sources appear in our circuit.

7. Organize the equations. Group terms according to mesh currents.

8. Solve the system of equations for the mesh currents.

## Nodal vs. Mesh Analysis Comparison
Now that we have examined two distinctly different approaches to circuit analysis, it seems logical to ask if there is ever any advantage to using one over the other. ***If the circuit is nonplanar, then there is no choice: only nodal analysis may be applied.***
Provided that we are indeed considering the analysis of a planar circuit, however, there are situations where one technique has a small advantage over the other. If we plan to use nodal analysis, then a circuit with N nodes will lead to at most (N − 1) KCL equations. Each supernode defined will further reduce this number by 1. If the same circuit has M distinct meshes, then we will obtain at most M KVL equations; each supermesh will reduce this number by 1. 
![[Pasted image 20211030185003.png]]

Based on these facts, we should select the approach that will result in the smaller number of simultaneous equations. If one or more dependent sources are included in the circuit, then each controlling quantity may influence our choice of nodal or mesh analysis. For example, a dependent voltage source controlled by a nodal voltage does not require an additional equation when we perform nodal analysis. Likewise, a dependent current source controlled by a mesh current does not require an additional equation when we perform mesh analysis.

What about the situation where a dependent voltage source is controlled by a current? Or the converse, where a dependent current source is controlled by a voltage? Provided that the controlling quantity can be easily related to mesh currents, we might expect mesh analysis to be the more straightforward option. Likewise, if the controlling quantity can be easily related to nodal voltages, nodal analysis may be preferable. 

One final point in this regard is to keep in mind the location of the source; current sources which lie on the periphery of a mesh, whether dependent or independent, are easily treated in mesh analysis; voltage sources connected to the reference terminal are easily treated in nodal analysis. When either method results in essentially the same number of equations, it may be worthwhile to also consider what quantities are being sought. Nodal analysis results in direct calculation of nodal voltages, whereas mesh analysis provides currents. If we are asked to find currents through a set of resistors, for example, after performing nodal analysis, we must still invoke Ohm’s law at each resistor to determine the current.