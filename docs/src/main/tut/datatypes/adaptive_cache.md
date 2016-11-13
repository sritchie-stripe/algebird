---
layout: docs
title:  "AdaptiveCache"
section: "summer"
source: "algebird-core/src/main/scala/com/twitter/algebird/SummingCache.scala"
scaladoc: "#com.twitter.algebird.SummingCache.scala"
---

# AdaptiveCache

This is a wrapper around SummingCache that attempts to grow the capacity by up to some maximum, as long as there's enough RAM.  It determines that there's enough RAM to grow by maintaining a SentinelCache which keeps caching and summing the evicted values. Once the SentinelCache has grown to the same size as the current cache, plus some margin, without running out of RAM, then this indicates that we have enough headroom to double the capacity.
