---
sticker: lucide//atom
---
Bartman diagrams, are a notation designed by H. Bartman[^1]. In this notation a machine that executes commands in language $C$ is represented by a reversed triangle.

![[../../../attachments/Pasted image 20260120123120.png]]

A compiler written in language $C$ that compiles from language $A$ to language $B$ is represented by a T shaped box:

![[../../../attachments/Pasted image 20260120123220.png]]

In order to use this compiler it must "stand" on a solid foundation (the machine that executes $C$). Note that the machine diagram element is a triangle so it doesn't need to stand on anything else. It is itself the foundation that everything else will stand.

Alternatively, we can have an interpreter for $C$ running on some other machine or interpreter. Any number of interpreters can be put on top of each other, but at the bottom of it all, we need a "real" machine. 

An interpreter written in language $D$ and interpreting the language $C$ is represented by a rectangle:

![[../../../attachments/Pasted image 20260120123446.png]]

When we want to represent an unspecified program (which can be a compiler an interpreter or something else entirely) written in language $D$, we show as:

![[../../../attachments/Pasted image 20260120123537.png]]

These figures can be combined to represent executions of programs. Some examples are given below:

![[../../../attachments/Pasted image 20260120123620.png]]

An unspecified program written with language $D$ being run on a machine that understands $D$. A clear note is that the diagram elements should match language on their touching face.

![[../../../attachments/Pasted image 20260120123903.png]]

An unspecified program in language $C$ being interpreted with an interpreter of $C$ in language $D$ and executed by a machine that understands $D$.

![[../../../attachments/Pasted image 20260120123909.png]]

This is a diagram of a compiler, that is written in $C$ and being executed on a machine that understands $C$. Is is compiling an unspecified program in language $A$ to language $B$. Compiler diagrams should be regarded as functions, the input is on the left and the output is the same object in a different language at right.

[^1]: Bartman H (1961) An alternative form of the UNCOL diagram. Commun ACM 4(3):142
