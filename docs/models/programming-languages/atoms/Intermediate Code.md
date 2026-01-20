---
sticker: lucide//atom
---
z# Intermediate Codes

Early compilers generated machine-specific code directly from a high-level program. This eases machine-specific optimizations, but it makes it more difficult to port the compiler to a different machine. So the basic idea of intermediate codes is to get the user code, transform it into an intermediate code, which then uses the compilers backend to transform it into machine specific binary.

Generally speaking compiler have two parts, a front end which is from lexer, parser and up to the intermediate code. And a backend which is from that code to binaries. It is notable that this architecture enables the same front-end for different backends therefore, not only machine-specific compilers can be produced, but also they can be produced for different languages (with different front ends that provide the same intermediate language).

When porting the compiler to a different machine, only the latter part needs to be rewritten. Furthermore, compilers for different high-level languages can use the same intermediate language, so the phase that translates from intermediate language to machine language needs to be written only once. It is also possible to implement the intermediate language with an interpreter instead of a compiler. If the intermediate language is simple to decode, the interpretation overhead can be quite small.

“If you want to translate M different high-level languages to N different machines, direct translation requires M × N compilers. If there is a common intermediate language, you need only M compilers from high-level languages to the intermediate language and N compilers from the intermediate language to the different machines.” (Ægidius Mogensen, 2022, p. 26) M + N vs M * N

## Intermediate Language Can be Optimized

You can also do many optimizations in the intermediate languages, and these can be shared between all the compilers. Theoretically, the compilers from high-level languages to the intermediate language can be very simple, and the compilers from the intermediate language to machine language ditto, since almost all of the complexity can be done as simplification and optimization of the intermediate code. In practice, it is not quite that simple.

“If the intermediate language is relatively high-level, it can be easy to compile high-level languages to this, but it becomes more difficult to compile the intermediate language to machine language. Conversely, a low-level intermediate language can be easy to compile to machine language, but more difficult to generate from a high-level language. Additionally, it is no help that the intermediate language is high-level if the abstractions used in the intermediate language are a poor fit for the high-level language.” (Ægidius Mogensen, 2022, p. 26)

