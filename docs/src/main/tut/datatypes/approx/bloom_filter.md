---
layout: docs
title:  "Bloom Filter"
section: "data"
source: "algebird-core/src/main/scala/com/twitter/algebird/BloomFilter.scala"
scaladoc: "#com.twitter.algebird.BloomFilter"
---

# Bloom Filter

```tut:book
import com.twitter.algebird._
val NUM_HASHES = 6
val WIDTH = 32
val SEED = 1
val bfMonoid = new BloomFilterMonoid(NUM_HASHES, WIDTH, SEED)
val bf = bfMonoid.create("1", "2", "3", "4", "100")
val approxBool = bf.contains("1")
val res = approxBool.isTrue
```
