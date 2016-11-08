---
layout: docs
title:  "Count Min Sketch"
section: "data"
source: "algebird-core/src/main/scala/com/twitter/algebird/CountMinSketch.scala"
scaladoc: "#com.twitter.algebird.CountMinSketch.scala"
---

# Count Min Sketch

Count-min sketch is a probablistic data structure that estimates the frequencies of elements in a data stream. Count-min sketches are somewhat similar to Bloom filters; the main distinction is that Bloom filters represent sets, while count-min sketches represent multisets. For more info, see [Wikipedia](https://en.wikipedia.org/wiki/Count%E2%80%93min_sketch).

In Algebird, count-min sketches are represented as the abstract class CMS, along with the CMSMonoid class.

```tut:book
import com.twitter.algebird.CMSHasherImplicits._
val DELTA = 1E-10
val EPS = 0.001
val SEED = 1
val HEAVY_HITTERS_PCT = 0.01
val CMS_MONOID = TopPctCMS.monoid[Long](EPS, DELTA, SEED, HEAVY_HITTERS_PCT)
val data = List(1L, 1L, 3L, 4L, 5L)
val cms = CMS_MONOID.create(data)
cms.totalCount
cms.frequency(1L).estimate
cms.frequency(2L).estimate
cms.frequency(3L).estimate
```

# Sketch Map

A Sketch Map is a generalized version of the Count-Min Sketch that is an approximation of Map[K, V] that stores reference to top heavy hitters. The Sketch Map can approximate the sums of any summable value that has a monoid.

```tut:book
val DELTA = 1E-8
val EPS = 0.001
val SEED = 1
val HEAVY_HITTERS_COUNT = 10

implicit def string2Bytes(i : String) = i.toCharArray.map(_.toByte)

val PARAMS = SketchMapParams[String](SEED, EPS, DELTA, HEAVY_HITTERS_COUNT)
val MONOID = SketchMap.monoid[String, Long](PARAMS)
val data = List( ("1", 1L), ("3", 2L), ("4", 1L), ("5", 1L) )
val sm = MONOID.create(data)
sm.totalValue
MONOID.frequency(sm, "1")
MONOID.frequency(sm, "2")
MONOID.frequency(sm, "3")
```
