---
sticker: lucide//atom
---
In algebra, a homomorphism is a structure preserving map between two algebraic structures of the same type. The word _homomorphism_ comes from the Ancient Greek language: [ὁμός](https://en.wiktionary.org/wiki/%E1%BD%81%CE%BC%CF%8C%CF%82#Ancient_Greek "wikt:ὁμός") (_homos_) meaning "same" and [μορφή](https://en.wiktionary.org/wiki/%CE%BC%CE%BF%CF%81%CF%86%CE%AE#Ancient_Greek "wikt:μορφή") (_morphe_) meaning "form" or "shape". However, the word was apparently introduced to mathematics due to a (mis)translation of German _[ähnlich](https://en.wiktionary.org/wiki/%C3%A4hnlich#German "wikt:ähnlich")_ meaning "similar" to ὁμός meaning "same". The term "homomorphism" appeared as early as 1892, when it was attributed to the German mathematician Felix Klein (1849–1925).

# Definition

A homomorphism is a map between two algebraic structures of the same type (two groups, two fields, two vector spaces), that preserves the operations of the structures. Formally, a map $f:A\to B$ preserves an operation $\mu$ of arity $k$; defined on both $A$ and $B$ if 

$$
\forall a_{i} \in A , i=1,2,\dots,k : f(\mu_{A} a_{1}a_{2}\dots a_{k}) = \mu_{B} f(a_{1})f(a_{2})\dots f(a_{k})
$$
If all the operations in the structure holds then $f$ is a homomorphism. The operations that must be preserved by a homomorphism include $0$-ary operations, that is the constants. In particular, when an identity element is required by the type of structure, the identity element of the first structure must be mapped to the corresponding identity element of the second structure.

**Examples**
- A semigroup homomorphism is a map between that preserves the semigroup operation.
- A monoid homomorphism is a map between monoids that preserves the monoid operation and maps the identity element of the first monoid to that of the second monoid (the identity element is a 0-ary operation.
- A [[Group Homomorphism]] is a map between groups that preserves the group operation. This implies that the group homomorphism maps the identity element of the first group to the identity element of the second group, and maps the ivnerse of an element of the first group to the inverse of the image of this element. Thus a semigroup homomorphism between groups is necessarily a group homomorphism.
- A ring homomorphism is a map between rings that preserves the ring addition, the ring multiplication, and the multiplicative identity. Whether the multiplicative identity is to be preserved depends upon the definition of _ring_ in use. If the multiplicative identity is not preserved, one has a rng homomorphism.
- A [[../linear-algebra/atoms/Linear Transformations|Linear Map]] is a homomorphism of [[../linear-algebra/atoms/Vector Spaces|Vector Spaces]]; that is, a group homomorphism between vector spaces that preserves the abelian group structure and scalar multiplication.
- A module homomorphism, also called a linear map between modules, is defined similarly.
- An algebra homomorphism is a map that preserves the algebra operations.

[[Isomorphism]]