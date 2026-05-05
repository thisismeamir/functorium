# Overview

Dependent type theory is a powerful and expressive language, allowing you to express complex mathematical assertions, write complex hardware and software specifications, and reason about both of these in a natural and uniform way. Lean is based on a version of dependent type theory known as the _Calculus of Constructions_, with a countable hierarchy of non-cumulative universes and inductive types. By the end of this note, you will understand much of what this means.

# Simple Type Theory

*Type theory* gets its name from the fact that every expression has an associated type. Here are some examples of how you can declare objects in Lean and check their types:

```lean
def m : Nat := 1

def n : Nat := 0

#check m
#check n + m 
```

The `def` keyword declares new constant symbols into the working environment. In the example above, `def m : [Nat] := 1` defines a new constant `m` of type `[Nat]` whose value is `1`. The `#check` command asks Lean to report their types; in Lean, auxiliary commands that query the system for information typically begin with the hash (#) symbol. The `#eval` command asks Lean to evaluate the given expression. You should try declaring some constants and type checking some expressions on your own. Declaring new objects in this manner is a good way to experiment with the system.

# Types as Objects

What makes simple type theory powerful is that you can build new types out of others. For example, if `a` and `b` are types, `a -> b` denotes the type of functions from `a` to `b`, and `a × b` denotes the type of pairs consisting of an element of `a` paired with an element of `b`, also known as the _Cartesian product_. Note that `×` is a Unicode symbol. The judicious use of Unicode improves legibility, and all modern editors have great support for it. In the Lean standard library, you often see Greek letters to denote types, and the Unicode symbol `→` as a more compact version of `->`.

```lean 
#check Nat → Nat
#check Nat -> Nat
#check Nat × Nat
#check Prod Nat Nat
#check Nat → Nat → Nat
#check Nat → (Nat → Nat)
#check Nat × Nat → Nat
#check (Nat → Nat) → Nat
```

Let's take a look at some basic syntax. You can enter the Unicode arrow `→` by typing `\to` or `\r` or `\->`. You can also use the ASCII alternative `->`, so the expressions `[Nat] -> [Nat]` and `[Nat] → [Nat]` mean the same thing. Both expressions denote the type of functions that take a natural number as input and return a natural number as output. The Unicode symbol `×` for the Cartesian product is entered as `\times`. You will generally use lower-case Greek letters like `α`, `β`, and `γ` to range over types. You can enter these particular ones with `\a`, `\b`, and `\g`.

Given that every expression in Lean has a type, it is natural to ask: what type does `Type` itself have?

```lean
#check Type
```

You have actually com up against one of the most subtle aspects of Lean's typing system. Lean's underlying foundation has an infinite hierarchy of types:

```lean
#check Type
-- Returns Type 1
#check Type 1
-- Returns Type 2
-- and so on
```

Think of `Type 0` as a universe of "small" or "ordinary" types. `Type 1` is then a larger universe of types which contains `Type 0` as an element. The list is infinite: there is a `Type n` for every natural number `n`. `Type` is an abbreviation for `Type 0`

![[Screenshot_5-5-2026_02226_leanprover.github.io.jpeg]]

Some operations, however, need to be polymorphic over type universe. For example, `List \alpha` should make sense for any type `\alpha`, no matter which type universe `\alpha` lives in. This explains the type signature of the function `List`

```lean 
#check List
-- Returns: List.{u} (α : Type u) : Type u
```

To define polymorphic constants, Lean allows you to declare universe variables explicitly using the `universe` command:

```lean
-- This way
universe u
def F (α: Type u): Type u := Prod α α
#check F
-- Or this way:
def L.{x} (β : Type x) : Type x := Prod β β
```


# Functions Abstraction and Evaluation

Lean provides a `fun` (or `\lambda`) keywords to create a function from an expression as follows:

```lean
```