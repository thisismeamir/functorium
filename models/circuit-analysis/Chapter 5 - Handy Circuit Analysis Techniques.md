# Handy Circuit Analysis Techniques
---
**Table of Content**
```toc
    style: number
    min_depth: 1
    max_depth: 6
```
---
The techniques of nodal and mesh analysis described in Chap. 4 are reliable and extremely powerful methods. However, both require that we develop a complete set of equations to describe a particular circuit as a general rule, even if only one current, voltage, or power quantity is of interest. In this chapter, we investigate a variety of different techniques for isolating specific parts of a circuit in order to simplify the analysis. After examining each of these techniques, we focus on how one might go about selecting one method over another.


## Linearity and Superposition
### Linear Elements and Circuits
We define a ***Linear Element*** as a passive element that has a linear *voltage-current* relationship. By a “linear voltage–current relationship” we mean that multiplication of the current through the element by a constant $K$ results in the multiplication of the voltage across the element by the same constant $K$. So far, we have encountered only one passive element ( the resistor), and its voltage-current relationship is:
$$
v(t) = Ri(t)
$$
We define a *linear dependent source* as a dependent current or voltage source whose output current or voltage is proportional only to the first power of a specified current or voltage variable in the circuit (or to the sum of such quantities). 

We now define a *linear circuit* as a circuit composed entirely of independent sources, linear dependent sources, and linear elements. From this definition, it is possible to show1 that “the response is proportional to the source,” or that multiplication of all independent source voltages and currents by a constant K increases all the current and voltage responses by the same factor $K$ (including the voltage or current output of any dependent sources).

### The Superposition principle
>==The most important consequence of linearity is superposition.==

- fundamental concept involved in the superposition principle: to look at each independent source (and the response it generates) one at a time with the other independent sources “turned off” or “zeroed out.”
- If we reduce a voltage source to zero volts, we have effectively made it into a short circuit.. If we reduce a current source to zero amperes, we have effectively created an open circuit.


![[Pasted image 20211103001011.png]]
Thus, the superposition theorem can be stated as:

> In any linear resistive network, the voltage across or the current through any resistor or source may be calculated by adding algebraically all the individual voltages or currents caused by the separate independent sources acting alone, with all other independent voltage sources replaced by short circuits and all other independent current sources replaced by open circuits.

#### Summary of Basic Superposition Procedure 
1. Select one of the independent sources. Set all other independent sources to zero. This means voltage sources are replaced with short circuits and current sources are replaced with open circuits. Leave dependent sources in the circuit.

1. Relabel voltages and currents using suitable notation (e.g., $v′$, $i_2''$ 	dent sources to avoid confusion.

3. Analyze the simplified circuit to find the desired currents and/or voltages.

4. Repeat steps 1 through 3 until each independent source has been considered.

5. Add the partial currents and/or voltages obtained from the separate analyses. Pay careful attention to voltage signs and current directions when summing.

6. Do not add power quantities. If power quantities are required, calculate only after partial voltages and/or currents have been summed.

---
Unfortunately, it usually turns out that little if any time is saved in analyzing a circuit containing one or more dependent sources by use of the superposition principle, for there must always be at least two sources in operation: one independent source and all the dependent sources. ==We must constantly be aware of the limitations of superposition. It is applicable only to linear responses, and thus the most common nonlinear==

## Source Transformations
### Practical Voltage And Current Sources

The concept of ideal sources. Does not exist in the real world. There are some contradictions happen if you have an ideal source (current or voltage) In a circuit.
![[Pasted image 20211103185108.png]]
Therefore, there are some practical sources. That we have to use instead in real world. 
The Practical Voltage source is a combination of an ideal source and a resistor in series:
$$ v_L = v_s -R_s i_L$$
Same thing for current sources:
![[Pasted image 20211103190106.png]]
$$ i_L = i_s\frac{v_L}{R_p}$$

![[Pasted image 20211103185832.png]]

## Equivalent Practical Sources

It may be *no surprise* that we can improve upon models to increase their accuracy; at this point we now have a practical voltage source model and also a practical current source model. Before we proceed, however, let’s take a moment to compare. One is for a circuit with a voltage source and the other, with a current source, but the graphs are indistinguishable!

It turns out that this is no coincidence. In fact, we are about to show that a practical voltage source can be electrically equivalent to a practical current source—meaning that a load resistor $R_L$ connected to either will have the same $v_L$ and $i_L$. This means we can replace one practical source with the other and the rest of the circuit will not know the difference.

![[Pasted image 20211103190629.png]]

A simple calculation can show that:
$$
v_L = v_s\frac{R_L}{R_s+R_L}
$$

A similar calculation can show that for:
![[Pasted image 20211103190825.png]]
$$V_L = \bigg(i_s \frac{R_p}{R_p+R_L}\bigg) \cdot R_L$$

#### Summary of Source Transformation
1. A common goal in source transformation is to end up with either all current sources or all voltage sources in the circuit. This is especially true if it makes nodal or mesh analysis easier.
2. Repeated source transformations can be used to simplify a circuit by allowing resistors and sources to eventually be combined.
3. The resistor value does not change during a source transformation, but it is not the same resistor. This means that currents or voltages associated with the original resistor are irretrievably lost when we perform a source transformation.
4. If the voltage or current associated with a particular resistor is used as a controlling variable for a dependent source, it should not be included in any source transformation. The original resistor must be retained in the final circuit, untouched.
5. If the voltage or current associated with a particular element is of interest, that element should not be included in any source transformation. The original element must be retained in the final circuit, untouched.
6. In a source transformation, the head of the current source arrow corresponds to the “+” terminal of the voltage source.
7. A source transformation on a current source and resistor requires that the two elements be in parallel.
8. A source transformation on a voltage source and resistorrequires that the two elements be in series.


## THÉVENIN AND NORTON EQUIVALENT CIRCUITS
Now that we have been introduced to source transformations and the superposition principle, it is possible to develop two more techniques that will greatly simplify the analysis of many linear circuits. The first of these theorems is named after L. C. Thévenin, a French engineer working in telegraphy who published the theorem in 1883; the second may be considered a corollary of the first and is credited to E. L. Norton, a scientist with the Bell Telephone Laboratories.
![[Pasted image 20211107000315.png]]

Assume we want to find the voltage across and the current through a resistor $R_L$, Thévenin’s theorem tells us that it is possible to replace everything except the load resistor with an independent voltage source in series with a resistor; the response measured at the load resistor will be unchanged. Using Norton’s theorem, we obtain an equivalent composed of an independent current source in parallel with a resistor.

### Thévenin Theorem
1. Given any linear circuit, rearrange it in the form of two networks, $A$ and $B$, connected by two wires. Network $A$ is the network to be simplified; $B$ will be left untouched.
2. Disconnect network $B$. Define a voltage $v_{oc}$ as the voltage now appearing across the terminals of network $A$.
3. Turn off or “zero out” every independent source in network $A$ to form an inactive network. Leave dependent sources unchanged.
4. Connect an independent voltage source with value $v_{oc}$ in series with the inactive network. Do not complete the circuit; leave the two terminals disconnected.
5. Connect network $B$ to the terminals of the new network $A$. All currents and voltages in $B$ will remain unchanged.


>Note that if either network contains a dependent source, its control variable must be in the same network.

- The only restriction that we must impose on $A$ or $B$ is that all dependent sources in $A$ have their control variables in $A$, and similarly for $B$.
- No restrictions are imposed on the complexity of $A$ or $B$; either one may contain any combination of independent voltage or current sources, linear dependent voltage or current sources, resistors, or any other circuit elements which are linear.
- The deactivated network $A$ can be represented by a single equivalent resistance $R_{TH}$, which we will call the Thévenin equivalent resistance. This holds true whether or not dependent sources exist in the inactive A network, an idea we will explore shortly.

- A Thévenin equivalent consists of two components: a voltage source in series with a resistance. Either may be zero, although this is not usually the case.

### Norton's Theorem
1. Given any linear circuit, rearrange it in the form of two networks, $A$ and $B$, connected by two wires. Network $A$ is the network to be simplified; $B$ will be left untouched. As before, if either network contains a dependent source, its controlling variable must be in the same network.
2. Disconnect network $B$, and short the terminals of $A$. Define a current is $i_{sc}$ as the current now flowing through the shorted terminals of network $A$.
3. Turn off or “zero out” every independent source in network $A$ to form an inactive network. Leave dependent sources unchanged.
4. Connect an independent current source with value is $i_{sc}$ in parallel with the inactive network. Do not complete the circuit; leave the two terminals disconnected.
5. Connect network $B$ to the terminals of the new network $A$. All currents and voltages in $B$ will remain unchanged.

## Maximum Power Transfer
![[Pasted image 20211107013421.png]]
Considering this simple circuit the power delivered to the load resistor is:
$$
p_L =i_L^2R_L = \frac{v^2_sR_L}{(R_s+R_L)^2}
$$
to find the resistance where the power is maximum we have:
$$\frac{dp_L}{dR_L} = 0 $$
which leads to:
$$ R_s = R_L $$

> An independent voltage source in series with a resistance $R_s$ (or an independent current source in parallel with a resistance $R_s$) delivers maximum power to a load resistance $R_L$ such that $R_L = R_s$.

We should pause here and mention that it is not uncommon for the maximum power theorem to be misinterpreted. It is designed to help us select an optimum load in order to maximize power absorption. If the load resistance is already specified, however, the maximum power theorem is of no assistance. If for some reason we can affect the size of the Thévenin equivalent resistance of the network connected to our load, setting it equal to the load does not guarantee maximum power transfer to our predetermined load. A quick consideration of the power lost in the Thévenin resistance will clarify this point.

## Selecting an  Approach : Summary of different techniques

In Chap. 3, we were introduced to Kirchhoff’s current law (KCL) and Kirchhoff’s voltage law (KVL). These two laws apply to any circuit we will ever encounter, provided that we take care to consider the entire system that the circuits represent. 

The reason for this is that KCL and KVL enforce charge and energy conservation, respectively, which are fundamental principles. Based on KCL, we developed the very powerful method of nodal analysis. A similar technique based on KVL (unfortunately only applicable to planar circuits) is known as mesh analysis and is also a useful circuit analysis approach. For the most part, this text is concerned with developing analytical skills that apply to linear circuits. 

If we know a circuit is constructed of only linear components (in other words, all voltages and currents are related by linear functions), then we can often simplify circuits before employing either mesh or nodal analysis. Perhaps the most important result that comes from the knowledge that we are dealing with a completely linear system is that the principle of superposition applies: given a number of independent sources acting on our circuit, we can add the contribution of each source independently of the other sources. This technique is pervasive throughout the field of engineering, and we will encounter it often. 

In many real situations, we will find that although several “sources” are acting simultaneously on our “system,” typically one of them dominates the system response. Superposition allows us to quickly identify that source, provided that we have a reasonably accurate linear model of the system. However, from a circuit analysis standpoint, unless we are asked to find which independent source contributes the most to a particular response, we find that rolling up our sleeves and launching straight into either nodal or mesh analysis is often a more straightforward tactic. The reason for this is that applying superposition to a circuit with 12 independent sources will require us to redraw the original circuit 12 times, and often we will have to apply nodal or mesh analysis to each partial circuit, anyway. 

The technique of source transformations, on the other hand, is often a very useful tool in circuit analysis. Performing source transformations can allow us to consolidate resistors or sources that are not in series or parallel in the original circuit. Source transformations may also allow us to convert all or at least most of the sources in the original circuit to the same type (either all voltage sources or all current sources), so nodal or mesh analysis is more straightforward. Thévenin’s theorem is extremely important for a number of reasons.

In working with electronic circuits, we are always aware of the Thévenin equivalent resistance of different parts of our circuit, especially the input and output resistances of amplifier stages. The reason for this is that matching of resistances is often the best route to optimizing the performance of a given circuit. We have seen a small preview of this in our discussion of maximum power transfer, where the load resistance should be chosen to match the Thévenin equivalent resistance of the network to which the load is connected. In terms of day-to-day circuit analysis, however, we find that converting part of a circuit to its Thévenin or Norton equivalent is almost as much work as analyzing the complete circuit. Therefore, as in the case of superposition, Thévenin’s and Norton’s theorems are typically applied only when we need specialized information about part of our circuit.