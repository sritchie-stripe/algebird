---
layout: docs
title:  "Semigroup"
section: "typeclasses"
source: "algebird-core/src/main/scala/com/twitter/algebird/Semigroup.scala"
scaladoc: "#com.twitter.algebird.Semigroup.scala"
---

## Semigroup

Given a set S and an operation `+`, we say that `(S, +)` is a *semigroup* if it satisfies the following properties for any x, y, z &isin; S:

- *Closure*: `x + y` &isin; S
- *Associativity*: `(x + y) + z = x + (y + z)`

We also say that *S forms a semigroup under **.

#### Examples of Semigroups

- Strings form a semigroup under concatenation.
