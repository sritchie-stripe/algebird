---
layout: docs
title:  "SummingIterator"
section: "data"
source: "algebird-core/src/main/scala/com/twitter/algebird/SummingIterator.scala"
scaladoc: "#com.twitter.algebird.SummingIterator"
---

# SummingIterator

Creates an Iterator that emits partial sums of an input Iterator[V]. Generally this is useful to change from processing individual Vs to possibly blocks of V @see SummingQueue or a cache of recent Keys in a V=Map[K,W] case: @see SummingCache.
