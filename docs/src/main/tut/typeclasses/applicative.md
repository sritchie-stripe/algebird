---
layout: docs
title:  "Applicative"
section: "typeclasses"
source: "algebird-core/src/main/scala/com/twitter/algebird/Applicative.scala"
scaladoc: "#com.twitter.algebird.Applicative"
---

# Applicative

Note - don't use this, use cats.

/**
 * Simple implementation of an Applicative type-class.
 * There are many choices for the canonical second operation (join, sequence, joinWith, ap),
 * all equivalent. For a Functor modeling concurrent computations with failure, like Future,
 * combining results with join can save a lot of time over combining with flatMap. (Given two
 * operations, if the second fails before the first completes, one can fail the entire computation
 * right then. With flatMap, one would have to wait for the first operation to complete before
 * failing it.)
 *
 * Laws Applicatives must follow:
 *  map(apply(x))(f) == apply(f(x))
 *  join(apply(x), apply(y)) == apply((x, y))
 *  (sequence and joinWith specialize join - they should behave appropriately)
 */
