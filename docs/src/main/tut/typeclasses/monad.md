---
layout: docs
title:  "Monad"
section: "typeclasses"
source: "algebird-core/src/main/scala/com/twitter/algebird/Monad.scala"
scaladoc: "#com.twitter.algebird.Monad"
---

# Monad

(Note - don't use this, use cats.)

Simple implementation of a Monad type-class. Subclasses only need to override apply and flatMap, but they should override map, join, joinWith, and sequence if there are better implementations.

Laws Monads must follow:

identities:

```scala
flatMap(apply(x))(fn) == fn(x)
flatMap(m)(apply _) == m
```

associativity on flatMap (you can either flatMap f first, or f to g):

```scala
flatMap(flatMap(m)(f))(g) == flatMap(m) { x => flatMap(f(x))(g) }
```
