---
layout: docs
title:  "Metric"
section: "typeclasses"
source: "algebird-core/src/main/scala/com/twitter/algebird/Metric.scala"
scaladoc: "#com.twitter.algebird.Metric"
---

## Metric

A Metric[V] m is a function (V, V) => Double that satisfies the following properties:

1. m(v1, v2) >= 0
2. m(v1, v2) == 0 iff v1 == v2
3. m(v1, v2) == m(v2, v1)
4. m(v1, v3) <= m(v1, v2) + m(v2, v3)

If you implement this trait, make sure that you follow these rules.
