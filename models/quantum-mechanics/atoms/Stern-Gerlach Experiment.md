# Stern-Gerlach Experiment
#stern-gerlach #experimental #quantum-mechanics

Stern-Gerlach experiment, originally conceived by O. Stern in 1921 and carried out in Frankfurt by him in collaboration with W. Gerlach in 1922. (This is closely related to the second chapter of *Making Sense of Quantum Mechanics* by Jean Bricmont).

This experiment shows in an extreme way the need to change and depart from the concepts of classical physics. Certainly, a two-state system of the Stern-Gerlach type is the least classical and most quantum mechanical system. A solid understanding of problems involving two-state systems will turn out to be rewarding to any serious student of quantum mechanics.

![[../../../attachments/Pasted image 20251117092638.png]]

First, silver ($\text{Ag}$) atoms are heated in an oven, which has a small hole through which some of the silver atoms escape. The beam, then goes through a collimator and is then subjected to an inhomogeneous magnetic field produced by a pair of pole pieces, one of which has a very sharp edge. 

## Thought Process

We want to work out the effect of the magnetic field on the trajectory the silver atoms would take For our purpose the following oversimplified model of the silver atom suffices. The silver atom is made up of a nucleus and $47$ electrons, where $46$ out of $47$ electrons can be visualized as forming a spherically symmetrical electron cloud with no net angular momentum.

If we ignore the nuclear spin which is irrelevant to our discussion, we see that the atom as a whole does have an angular momentum, which is due solely to the spin, the (intrinsic) angular momentum of the single 47th electron. The $47$ electrons are attached to the nucleus, which is $\sim 2\times 10^5$  times heavier than the electron; as a result the heavy atom as a whole possesses a magnetic moment equal to the spin magnetic moment of that single electron.

More mathematically the magnetic moment $\mu$ of the atom is
$$
\mu \propto S.
$$
Because the interaction energy of the magnetic moment with the magnetic field is just $-\mu\cdot \mathbf{B}$, the $z-$component of the force experience by the atom is given by
$$
F_z = \frac{\partial}{\partial z}(\mu\cdot\mathbf{B}) \simeq \mu_z \frac{\partial B_z}{\partial z},
$$
where we have ignored the components of $\mathbf{B}$ in directions other than the $z$-direction. Now, we've got two possible expectations:
1. $\mu_z > 0$ which means $(S_z < 0)$, so that the atom experiences an upward force,
2. $\mu_z < 0$ which means $(S_z>0)$, in which the atom experiences a downward force.
Either way, since the atom as a whole is very heavy, we expect that the classical concept of trajectory can be legitimately applied, a point which can be justified using the Heisenberg uncertainty principle. In summary, the apparatus "measures" the $z$-component of $\mathbf{\mu}$.

If electron were to be a classical object, or more accurately, if spin of the electron were to be a classical property, we'd expect all sorts of values for it. Since the atoms in the oven are randomly oriented (meaning there's not preferred direction). Therefore, we'd expect $-|\mu|< \mu_i <|\mu|$ for a random atom $i$. **What we expect to see is a continuous bundle of beams coming out of the apparatus**.

Instead, what we experimentally observe is that two "spots" are observed, corresponding to one "up" and one "down" orientation. In other words, the apparatus splits the original silver beam from the oven into two distinct components, a phenomenon referred to in the early days of quantum theory as "*space quantization*".

> The "quantization" of the electron spin angular momentum is the first important feature we deduce from the Stern-Gerlach experiment. 

## Stern Gerlach in Sequence

### The First Arrangement

![[../../../attachments/Pasted image 20251117103330.png]]

For the first arrangement, we do nothing special. Assume the naming convention $SG_z$ as the Stern-Gerlach apparatus in the $z$ direction (measuring the $\mu_z$). We filter the atoms coming from the first apparatus, keeping only $S_z+$ (means Spin in $z$ direction with value *up*). If we then put another $SG_z$ that with only atoms whose spin are $S_z+$ in it, we get no $S_z-$ (means spin in $z$ direction with value *down*). No wonder!

### The Second Arrangement

![[../../../attachments/Pasted image 20251117104150.png]]

In the second arrangement, we're still not doing anything controversial. Consider that after the first $SG_z$, once again I filter the beams of a specific outcome, and give them as an input to another apparatus. This time $SG_x$ (Stern-Gerlach Apparatus for measuring $\mu_x$ ). What I'd expect to see (apart from the quantization of spins) is to get about the same numbers of $S_x+$ as I get $S_z-$. Still, no wonder!

### Third Apparatus

![[../../../attachments/Pasted image 20251117104223.png]]

Lastly, I'd also filter the atoms coming out of the second apparatus $SG_x$ for a specific spin in $x$ value and feed them to another $SG_z$, the same apparatus we had at the beginning of this experiment. This time, I'd expect to see only $SG_z+$ atoms, which I filtered earlier.

It is observed experimentally that two components emerge from the third apparatus, not one; This is a complete surprise because after the atoms emerged from the first apparatus, we made sure that the $S_z-$ component was completely blocked. How is it possible that the $S_z-$ component which, we thought, we eliminated earlier reappears?

> This example is often used to illustrate that in quantum mechanics we cannot determine both $S_z$ and $S_x$ simultaneously. More precisely, we can say that the selection of the $S_x+$ beam by the second apparatus $SG_x$ completely destroys any *previous* information about $S_z$.

