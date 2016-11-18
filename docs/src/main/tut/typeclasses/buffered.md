---
layout: docs
title:  "Buffered"
section: "typeclasses"
source: "algebird-core/src/main/scala/com/twitter/algebird/BufferedOperation.scala"
scaladoc: "#com.twitter.algebird.Buffered"
---

# Buffered

Represents something that consumes I and may emit O. Has some internal state that may be used to improve performance. Generally used to model folds or reduces (see BufferedReduce)

## BufferedReduce

Version of this that never emits on put... Used in `sumOption` for the generated tuple semigroups and case class semigroups and `BufferedSumAll`.
