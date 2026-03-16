# Basic Components and Electric Circuits
## Table of Contents

```toc
    style: number
    min_depth: 1
    max_depth: 6
```
---
Circuit analysis has long been a traditional introduction to theart of problem solving from an engineering perspective, even for those whose interests lie outside electrical engineering. There are many reasons for this, but one of the best is that in today’s world it’s extremely unlikely for any engineer to encounter a system that does not in some way include electrical circuitry. As circuits become smaller and require less power, and power sources become smaller and cheaper, embedded circuits are seemingly everywhere. Since most engineering situations require a team effort at some stage, having a working knowledge of circuit analysis therefore helps to provide everyone on a project with the background needed for effective communication.

----
## Units and Scales
The most frequently used system of units is the one adopted by the National Bureau of Standards in 1964; it is used by all major professional engineering societies and is the language in which today’s textbooks are written.
This is the International System of Unit (**SI**).

| SI Base Unit              |          |        |
| ------------------------- | -------- | ------ |
| Base Quantity             | Name     | Symbol |
| Length                    | meter    | m      |
| Mass                      | kilogram | kg     |
| Time                      | second   | s      |
| Electric current          | ampere   | A      |
| Thermodynamic Temperature | kelvin   | K      |
| Amount of Substance       | mole     | mol    |
| Luminous Intensity        | candela  | cd     |


## Charge, Current, Voltage, Power, And Energy
### Charge
One of the most fundamental concepts in electric circuit analysis is that of charge conservation.We know from basic physics that there are two types of charge: positive (corresponding to a proton) and negative (corresponding to an electron). For the most part, this text is concerned with circuits in which only electron flow is relevant. There are many devices (such as batteries, diodes, and transistors) in which positive charge motion is important to understanding internal operation, but external to the device we typically concentrate on the electrons which flow through the connecting wires. Although we continuously transfer charges between different parts of a circuit, we do nothing to change the total amount of charge. In other words, we neither create nor destroy electrons (or protons) when running electric circuits. Charge in motion represents a current.
> The SI Unit for charge is coulomb(**C**). It is defined in terms of the ampere by counting the total charge that passes through an arbitrary cross section of a wire during an interval of one second.

With this we can find a single electron charge as $-1.602\times 10^{-19}$ and for proton it's the opposite charge.

### Current
The idea of “transfer of charge” or “charge in motion” is of vital importance to us in studying electric circuits because, in moving a charge from place to place, we may also transfer energy from one point to another. The familiar cross-country power-transmission line is a practical example of a device that transfers energy. Of equal importance is the possibility of varying the rate at which the charge is transferred in order to communicate or transfer information. This process is the basis of communication systems such as radio, television, and telemetry.

- The current present in a discrete path, such as a metallic wire, has both a 1234 56 78 t(s) numerical value and a direction associated with it; it is a measure of the rate at which charge is moving past a given reference point in a specified direction.
	$$
	i = \frac{dq}{dt}
	$$
	

### Voltage 
let us suppose that a dc current is sent into terminal $A$, through the general element, and back out of terminal $B$. Let us also assume that pushing charge through the element requires an expenditure of energy. We then say that an electrical voltage (or a potential difference) exists between the two terminals, or that there is a voltage “across” the element. Thus, the voltage across a terminal pair is a measure of the work required to move charge through the element. The unit of voltage is the volt,4 and 1 volt is the same as 1 J/C.

### Power
We have already defined power, and we will represent it by P or p. If one joule of energy is expended in transferring one coulomb of charge through the device in one second, then the rate of energy transfer is one watt. The absorbed power must be proportional both to the number of coulombs transferred per second (current) and to the energy needed to transfer one coulomb through the element (voltage). Thus,
$$ p=vi$$

### Energy
if Power is ($J/s$) Then to find how many joules were used in a certain word we would write:
$$
w(t) = \int_{t_0}^tpdt = \int_{t_0}^tvi \ dt
$$

## Voltage and Current Sources
We define each component with the relation it's voltage has with it's current.
- If the voltage and current have linear relation we call it a resistor.
- If the voltage is proportional to the derivative of current it's an inductor.
- If the voltage is proportional to the integral of current it's a capacitor.
- If there is no relation between voltage and current it's an independent source.

### Independent Voltage Source
![[Pasted image 20211012092843.png]]
An independent Voltage Source is a source that it's voltage does not depend on any other component in the circuit.
![[Pasted image 20211012093153.png]]
> Independent Voltage Source is an ideal device that does not exist in real world .


### Independent Current Source
![[Pasted image 20211012093932.png]]
An independent Current Source is a source that it's current does not depend on any other component in the circuit.

### Dependent Sources
![[Pasted image 20211012094038.png]]
There are four types of dependent sources, 
1.	***Voltage-Controlled Current Source:*** The current of the source depends on the voltage of another component.
		
2. ***Current-Controlled Current Source:*** The current of the source depende on the current of another component or wire.
		
3. ***Current-Controlled Voltage Source:*** The voltage of the source depends on the current of another component or wire
		
4. ***Voltage Controlled Voltage Source:*** The Voltage of the source depends on the voltage of another component.

## Network and Circuit
The interconnection between two or more electrical elements is called a network, if the network happens to have at least one closed path then it is also a circuit.
> All circuits are networks but not all networks are circuits

![[Pasted image 20211012094737.png]]

A network that contains at least one active element, such as an independent voltage or current source, is an **active network**. A network that does not
contain any active elements is a **passive network**.




## Ohm's Law
Ohm's law states that the voltage of a conductor is linearly proportional to the current flows in it. or mathematically:
$$
v = Ri
$$ 
where $v$ is the voltage (volt), $i$ is the current (Amper), and $R$ is called the resistance of the conductor the unit of this is Ohm which is written as  ($V/A$)  or $\Omega$.
![[Pasted image 20211012095933.png]]
Linear Resistors are ideal components just like independent sources. but a really good approximation of the physical world.

### Power Assumption
$$ p = vi = i^2R = v^2/R $$


---
[[__Electronics]] 