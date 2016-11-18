---
layout: docs
title:  "Successible"
section: "typeclasses"
source: "algebird-core/src/main/scala/com/twitter/algebird/Successible.scala"
scaladoc: "#com.twitter.algebird.Successible"
---

# Successible

This is a typeclass to represent things which increase. Note that it is important that a value after being incremented is always larger than it was before. Note that next returns Option because this class comes with the notion of the "greatest" key, which is None. Ints, for example, will cycle if next(java.lang.Integer.MAX_VALUE) is called, therefore we need a notion of what happens when we hit the bounds at which our ordering is violating. This is also useful for closed sets which have a fixed progression.
