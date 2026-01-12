# Introduction

Set-theoretic foundation has two *layers*:

1. **The deductive system of first order logic**
2. **Axioms of a particular theory, such as ZFC**. 

Thus, set theory is not only about sets, but also about the toggle between sets (as objects of the second layer) and propositions (objects of the first layer).

Type theory on the other hand, is its own deductive system: it need not to be formulated inside any *superstructure*, such as first-order logic. Instead of the two basic notions of set theory (sets and propositions), type theory has one basic notion, **Types**.

Propositions (statements which we can prove, disprove, assume, negate, and so one) are identified with particular types, via the correspondence shown below:

| Types               | Logic                | Sets                       | Homotopy          |
| ------------------- | -------------------- | -------------------------- | ----------------- |
| $A$                 | porposition          | set                        | space             |
| $a:A$               | proof                | element                    | point             |
| $B(x)$              | predicate            | family of sets             | fibration         |
| $b(x):B(x)$         | conditional proof    | family of elements         | section           |
| $0,1$               | $\bot,\top$          | $\emptyset, \{\emptyset\}$ | $\emptyset, *$    |
| $A+B$               | $A\lor B$            | disjoint union             | coproduct         |
| $A\times B$         | $A\land B$           | set of pairs               | product space     |
| $A\rightarrow B$    | $A\Rightarrow B$     | set of functions           | function space    |
| $\sum_{(x:A)}B(x)$  | $\exists_{x:A}B(x)$  | disjoint sum               | total space       |
| $\prod_{(x:A)}B(x)$ | $\forall_{x:A} B(x)$ | product                    | space of sections |
| $\text{Id}_A$       | $=$                  | $\{(x,x) \vert x\in A\}$   | path space $A^I$  |

Thus the mathematical activity of *proving a theorem* is identified with a special case of mathematical activity of *constructing an object*. In this case, an inhabitant of a type that represents a proposition.

Informally, a deductive system is a collection of **rules** for deriving things called **judgments**. 

The deductive system of first-order logic (on which set theory is based) has *only one judgment*. That is, each proposition $A$ gives rise to a judgment *"$A$ has a proof"*. A  rule of first-order logic such as *" From $A$ and $B$ infer $A\land B$"*  actually means that given the judgements *"$A$ has a proof"* and *"$B$ has a proof"*, we may deduce that *"$A\land B$ has a proof"*.

The basic judgement of type theory, is $a:A$ and pronounced as *"the term $a$ has type $A$"*. When $A$ is a type representing a proposition, then $a$ may be called a ***witness*** to the provability of $A$, or ***evident*** of the truth of $A$. In this case, the judgement $a:A$ is derivable in type theory precisely when the analogous judgment ($A$ has a proof) is derivable in first-order logic.

Looking differently, if we treat types more like a set than like a proposition, then we may regard $a:A$ as analogous to $a\in A$ in set-theory. However, there's an essential difference. In particular, when working in type theory, we cannot make statements such as:

*if $a:A$ then it is not the case that $b:B$.*

And we can not disprove the judgement $a:A$.

“A good way to think about this is that in set theory, “membership” is a relation which may or may not hold between two pre-existing objects “a” and “A”, while in type theory we cannot talk about an element “a” in isolation: every element by its very nature is an element of some type, and that type is (generally speaking) uniquely determined.” ([pdf](zotero://open-pdf/library/items/526IU7BX?page=38&annotation=A9FCW2TP))

A last difference between type theory and set theory is the treatment of equality. *The familiar notion of equality in mathematics is a proposition*. Since in type theory, propositions are types, this means that equality is a type: for elements $a,b: A$ (that is, both $a:A$ and $b:A$) we have a type $a=_A b$.  When this is inhabited, we say that $a$ and $b$ are **(propositionally) equal**.

However, in type theory there's also a need for an equality *judgement*, existing at the same level as the judgement $x:A$. This is called **judgmental equality** or **definitional equality**, and we write it as $a\equiv b$ or $a\equiv_A b$. It is helpful to think of this as *equal by definition*. 

For example, if we define a function $f:\mathbf{N} \rightarrow \mathbf{N}$ by the equation $f(x) = x^2$, then the expression $f(3)$ is equal to $3^2$ ***by definition***.

It doesn't make sense to negate or assume an equality-by-definition; we cannot say *if $x$ is equal to $y$ by definition, then $z$ is not equal to $w$ by definition*. Whether or not two expressions are equal by definition is just a matter of expanding out the definitions; in particular, it is algorithmically decidable.

As type theory becomes more complicated, judgmental equality can get more subtle than this, but it is a good intuition to start from.

The reason we *want* a judgmental notion of equality is so that it can control the other form of judgment, $a:A$. 

For instance, suppose we have given a proof that $3^2 = 9$, meaning that we've shown for some $p$ that $p:(3^2 = 9)$. Then the same witness $p$ ought to count as a proof that $f(3) = 9$ since $f(3)$ is $3^2$ ***by definition***.

The best way to represent this is with a rule saying that given the judgments $a:A$ and $A\equiv B$, we may derive the judgment $a:B$.

Thus, type theory will be a deductive system based on two forms of judgment:
$$
a:A
$$
Meaning *$a$ is an object of type $A$.* and:
$$
a \equiv_A b
$$
Meaning $a$ and $b$ are definitionally equal objects of type $A$.

Judgments may depend on ***assumptions*** of the form $x:A$, where $x$ is a variable and $A$ is a type. The collection of all such assumptions is called the ***context***.

If the type $A$ in an assumption $x:A$ represents a proposition, then the assumption is a type-theoretic version of a *hypothesis*: we assume that the proposition $A$ holds. When types are regarded as propositions, we may omit the names of their proofs. Note that under this meaning of the word *assumption*, we can assume a propositional equality, but we cannot assume a judgmental equality $x\equiv y$, since it is not a type that can have an element.