---
layout: docs
title:  "Predecessible"
section: "typeclasses"
source: "algebird-core/src/main/scala/com/twitter/algebird/Predecessible.scala"
scaladoc: "#com.twitter.algebird.Predecessible"
---

# Predecessible

This is a typeclass to represent things which are countable down. Note that it is important that a value prev(t) is always less than t. Note that prev returns Option because this class comes with the notion that some items may reach a minimum key, which is None.
