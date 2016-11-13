---
layout: docs
title:  "Scala Collections"
section: "data"
---

- IndexedSeq.scala
- MapAlgebra with good helpers
- PriorityQueue aggregator, monoid

# Adding and Multiplication of collections

```tut:book
val data2 = Map(1 -> 1, 2 -> 1)
val data1 =  Map(1 -> 3, 2 -> 5, 3 -> 7, 5 -> 1)
import com.twitter.algebird.Operators._
data1 + data2
data1 * data2
Set(1,2,3) + Set(3,4,5)
List(1,2,3) + List(3,4,5)
Map(1 -> 3, 2 -> 4, 3 -> 1) * Map(2 -> 2)
Map(1 -> Set(2,3), 2 -> Set(1)) + Map(2 -> Set(2,3))
```
