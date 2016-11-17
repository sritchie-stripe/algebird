---
layout: docs
title:  "Successible"
section: "typeclasses"
source: "algebird-core/src/main/scala/com/twitter/algebird/Successible.scala"
scaladoc: "#com.twitter.algebird.Successible.scala"
---

## StatefulSummer

/**
 * A Stateful summer is something that is potentially more efficient
 * (a buffer, a cache, etc...) that has the same result as a sum:
 * Law 1: Semigroup.sumOption(items) ==
 *   (Monoid.plus(items.map { stateful.put(_) }.filter { _.isDefined }, stateful.flush) &&
 *     stateful.isFlushed)
 * Law 2: isFlushed == flush.isEmpty
 * @author Oscar Boykin
 */
