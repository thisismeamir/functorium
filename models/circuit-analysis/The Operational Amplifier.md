# Chapter 6 - The Operational Amplifier
---
**Table of Content**
```toc
    style: number
    min_depth: 1
    max_depth: 6
```
---
## Background
![[Pasted image 20211107095746.png]]
The op amp is a voltage amplifier with two inputs and one output. Two input terminals are denoted by a "$+$" for the ***noninverting input*** and "$-$" for the ***inverting input***. In addition to the output pin and the two inputs, other pins enable power to be supplied to run the transistors in the **IC** and to make external adjustments to balance and compensate the op amp. At this point, we are not concerned with the internal circuitry of the op amp or the IC, but only with the voltage and current relationships that exist between the input and output terminals. Thus, for the time being we will use a simpler electrical symbol.
![[Pasted image 20211107095804.png]]

## The Ideal OP Amp

- **Ideal Op Amp Rules** 
	1. No current ever flows into either input terminal. (Current can flow at the output terminal!)
	
	2. There is no voltage difference between the two input terminals.

> We will find that it is usually a good idea to begin the analysis of an op amp circuit at the input, and proceed from there.


 - Inverting Amplifier
	Let's see this example: This is called an **Inverting Amplifier** we choose to analyze this circuit using KVL, beginning with the input voltage source, with the goal of determining the output $v_{out}$ in terms of the input $v_{in}$ and circuit resistor values. The current labeled $i$ flows only through the two resistors $R_1$ and $R_f$, recalling that ideal op amp rule 1 states that no current flows into the input terminal. Thus, we can write
	![[Pasted image 20211107100933.png]]

	$$
	-v_{in}+R_1i+R_fi+v_{out} = 0
	$$
	which can be rearrenged to obtain an equation that relates the output to the input:
	$$
	v_{out} = v_{in}-(R_1 - R_f)i
	$$
	This is a good time to mention that we have not yet made use of ideal op amp rule 2. Since the noninverting input is grounded, it is at zero volts. By ideal op amp rule 2, the inverting input is therefore also at zero volts! This does not mean that the two inputs are physically shorted together, and we should be careful not to make such an assumption. Rather, the two input voltages simply track each other: if we try to change the voltage at one pin, the other pin will be driven by internal circuitry to the same value. Thus, we can write one more KVL equation:
	$$ -v_{in} +R_1i +0 = 0 $$
	or
	$$i=\frac{v_{in}}{R_1}$$
	combining $v_{out} = v_{in}-(R_1 - R_f)i$ and $i=\frac{v_{in}}{R_1}$ would lead to:
	$$
	v_{out}=-\frac{R_f}{R_1}v_{in}
	$$
	> The fact that the inverting input terminal finds itself at zero volts in this type of circuit configuration leads to what is often referred to as a “virtual ground.” This does not mean that the pin is actually grounded, which is sometimes a source of confusion for students. The op amp makes whatever internal adjustments are necessary to prevent a voltage difference between the input terminals. The input terminals are not shorted together.

