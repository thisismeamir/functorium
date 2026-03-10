---
sticker: lucide//atom
---

The basic idea in bootstrapping is to use compilers to compile themselves or other compilers. We do, however, need a solid foundation in the form of the machine on which to run the compilers.

It often happens that a compiler does exist for the desired source language, it just does not run on the desired machine. 

## Understanding with an Example

Assume, we want a compiler for $ML$ to $x86$ machine code and want this to run on an $x86$ machine. We have access to an $ML$ compiler that generates $ARM$ machine code and runs on an $ARM$ machine, which we also have access to. 

One way of obtaining the desired compiler would be to do binary translation, to write a compiler from $ARM$ machine code to $x86$ machine code. This will allow the translated compiler to run on an $x86$ but it will still generate $ARM$ code. We can use the $ARM$-to-$x86$, compiler to translate this into $x86$ afterwards, but this introduces several problems:

- Adding an extra pass makes the compilation process take longer.
- Some efficiency will be lost in the translation.
- We still need to make the $ARM$-to-$x86$ compiler run on the $x86$ machine.

A better solution is to write an $ML$-to-$x86$ compiler in $ML$. We can compile this using the $ML$ compiler on the $ARM$ machine.

![[../../../attachments/Pasted image 20260120125149.png]]

Now, we can run the $ML$-to-$x86$ compiler on the $ARM$ and let it compile itself.

![[../../../attachments/Pasted image 20260120125257.png]]

We have now obtained the desired compiler. Note that the compiler can now be used to compile itself directory on the $x86$ platform. This can be useful if the compiler is later extended or, simply, as a partial test of correctness: If the compiler, when compiling itself, yields a different object code than the one obtained with abode process it must contain an error. The converse is not true, even if the same target is obtained, there may still be errors in the compiler.

This bootstrapping process relies on an existing compiler for the desired language, but it runs on a different machine. It is, hence, often called "half bootstrapping". When no existing compiler is available, er need to use more complicated process called "full bootstrapping".

# Full Bootstrapping

A common method is to write a QAD ("quick and dirty") compiler using an existing language. This compiler needs not to generate code for the desired target machine, nor does it have to generate good code, as long as the generated code is correct. The important thing is that it allows programs in the new language to be executed. Additionally, the "real" compiler is written in the new language and will be bootstrapped using the QAD compiler.

## Understanding with an Example

Let us assume we design a new language "$M+$". We, initially, write a compiler for $M+$ to $ML$ in $ML$. The first step is to compile this so it can run on some machine.

![[../../../attachments/Pasted image 20260120134935.png]]

The QAD compiler can now be used to compiler the "real" compiler:

![[../../../attachments/Pasted image 20260120140128.png]]

The result is an $ML$ program, which we need to compile:

![[../../../attachments/Pasted image 20260120140233.png]]

The result of this is a compiler with the desired functionality, but it will probably run slowly. The reason is that it has been compiled by using the QAD compiler (in combination with the $ML$ compiler). A better result can be obtained by letting the generated compiler compile itself:

![[../../../attachments/Pasted image 20260120140740.png]]

This yields a compiler with the same functionality as the above it will generate the same code, but, since the "real" compiler has been used to compile it, it will probably run fast.

> [!NOTE]
    > The need for this extra step might be a bit clearer if we had let the "real" compiler generate $x86$ code instead, as it would then be obvious that the last step is required to get the compiler to run on the same machine that it targets. But the simple case underscores a point: **Bootstrapping might not be complete even if a compiler with the right functionality has been obtained**.

Instead of writing a QAD compiler, we can write a QAD interpreter. In our example, we could write an $M+$ interpreter in $ML$. We would first need to compiler this:

![[../../../attachments/Pasted image 20260120145057.png]]

We can then use this to run the $M+$ compiler directly:

![[../../../attachments/Pasted image 20260120145130.png]]

Since the "real" compiler has been used to do the compilation, nothing new will be gained by using the generated compiler to compile itself, though this step can still be used as a test.

Though bootstrapping with an interpreter requires fewer steps than bootstrapping with a compiler, this should not really be a consideration, as the computers will do all the work in these steps. 

What is important is the amount of code that needs to be written by hand. For some languages, a QAD compiler will be easier to write than a QAD interpreter, and for others it's the opposite. The relative ease/difficulty may also depend on the language used to implement the QAD interpreter/compiler.

## Incremental Bootstrapping

It is also possible to build the new language and its compiler incrementally. The first step is to write a compiler for a small subset of the language, using that same subset to write it. This first compiler must be bootstrapped in one of the ways discussed earlier, but thereafter the following process is done repeatedly:

1. Extend the language subset slightly.
2. Extend the compiler so it compiles the extended subset, but without using the new features in the compiler.
3. Use the previous compiler to compile the new.

In each step, the features introduced in the previous step can be used in the compiler. Even when the full language is implemented, the process can be continued to improve the quality of the compiler.

# Choosing a Language To Write a Compiler

The purpose of bootstrapping is to obtain a compiler written in the language that is compiles. After bootstrapping is complete, there is no need for other compilers or other languages, and bootstrapping is a good test for the compiler. But there are also disadvantages.

- The language that we need to compile might not be very suitable for writing a compiler, so writing the compiler in this language adds a burden to the programmer. And if compilers for other languages are readily available, it is no great problem to rely on these, and a potential source of error is avoided.
- If a compiler made by bootstrapping fails to produce correct code for a particular feature, this can be caused both by an error in the part of the compiler that handles this feature, or by the parts of the compiler that is used to compile the code that handles the feature. 
  
  This makes it harder to track an error than if you can rely on the correctness of an existing compiler.

The following features can help development of a new compiler easier. So if there happen to be a language that supports these features, it would be a good choice to write the compiler in them.

- Existence of lexer and parser generators or good libraries for writing lexer and parsers.
- A module system that allows specification of interfaces between the different components of the compiler.
- Good support for manipulating tree-structured data. This implies automatic memory management (garbage collection), pattern-matching on compound values, and a not too verbose syntax for building compound data.

