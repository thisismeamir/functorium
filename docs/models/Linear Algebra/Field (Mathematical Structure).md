---
sticker: lucide//atom
---
A field is a set $F$ equipped with two binary operators. Addition $+$ and multiplication $\cdot$. These binary operations have certain features for us to call the structure a field:

### Addition

For addition operator we seek the following properties. 

**Closure:** The operator must have the following signature.

$$
+ : F\times F \rightarrow F
$$

This means that the addition operator takes to elements of the set $F$ and always returns an element of the set $F$. Another way to put it would be:

$$
\forall a,b\in F ; \left(a+b = c\in F\right)
$$

**Associativity:** Order of applying addition operator should not matter. Which means:

$$
(a + b)  + c = a+ (b+c)
$$

**Commutativity:** Also the inputs of the operator are not ordered. Therefore switching them doesn't change the outcome.

$$
a + b = b + a
$$

**Additive Identity:** There's an element in $F$ such that it's addition with any other element of $F$ would be equal to that element. We typically show that (since we're mostly only working with number fields) with $0$. 

$$
\exists 0 \in F ; a + 0 = 0 + a = a
$$

**Additive Inverse:** For each element of the set $F$, there's another element, such that the addition of the two would result in the additive identity. Again since we mostly work with number fields these are usually shown with $-$ sign. And further more we might also drop the operator sign to and define subtraction notation.

$$
\forall a \in F, \exists -a \in F; a + (-a) = (-a)+a = a-a = 0
$$

### Multiplication

**Closure:** Again we expect that the multiplication of two elements returns another element of the field:

$$
\forall a, b\in F; a\cdot b = c \in F
$$

**Associativity:** It is also important that our multiplication is also associative:

$$
a \cdot (b\cdot c) = (a\cdot b)\cdot c
$$

**Commutativity:** The order for this operator also doesn't matter:

$$
a\cdot b = b\cdot a
$$

**Multiplication Identity:** There's an element in $F$, usually denoted with $1$ that for all elements in $F$:

$$
\forall a \in F ; a \cdot 1  = a
$$

**Multiplication Inverse:** For each element in $F$ except $0$ there exists another element in $F$ such that:

$$
a \cdot a^{-1} = 1
$$

**Distributivity of Multiplication Operator over Addition Operator:** For these two operators, multiplication can be distributed over addition, this means:

$$
a\cdot (b+c) = (a\cdot b) + (a\cdot c)
$$
