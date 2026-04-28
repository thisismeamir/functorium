---
aliases:
  - "Rocq: Data and Functions"
sticker: lucide//atom
---
# Data and Functions

## Enumerated Types

One notable thing about Rocq is that its set of built-in features is extremely small. For example, instead of the usual palette of atomic data types (boolean, integers, strings, etc.), Rocq offers a powerful mechanism for defining new data types from scratch, with all these familiar types as instances.

Naturally, the Rocq distribution also comes with an extensive standard library providing definitions of booleans, numbers, and many common data structures like lists and has tables. But there's nothing magic or primitive about these library definitions. 

## Days of Week

To see how the datatype definition mechanism works, let's start with a very simple example. The following declaration tells Rocq that we are defining a set of data values -- a _type_.

```rocq
Inductive day : Type :=
	| monday
	| tuesday
	| wednesday
	| thursday
	|friday
	|saturday
	|sunday.
```

The new type is called day, and its members are monday, tuesday, etc.

Having defined day, we can write functions that operate on days.

```rocq
Definition nextWorkingDay (d: day) : day :=
match d with
	| monday => tuesday
	| tuesday => wednesday
	| wednesday => thursday
	| thursday => friday
	| friday => monday
	| saturday => monday
	| sunday => monday
end.
```

Note that the argument and return types of this function are explicitly declared on the first line. Like most functional programming languages, Rocq can often figure out these types for itself when they are not given explicitly -- i.e., it can do _type inference_ -- but we'll generally include them to make reading easier.