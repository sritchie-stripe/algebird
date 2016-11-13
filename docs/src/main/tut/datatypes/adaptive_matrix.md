---
layout: docs
title:  "Adaptive Matrix"
section: "data"
source: "algebird-core/src/main/scala/com/twitter/algebird/matrix/AdaptiveMatrix.scala"
scaladoc: "#com.twitter.algebird.matrix.AdaptiveMatrix.scala"
---

# AdaptiveMatrix

A Matrix structure that is designed to hide moving between sparse and dense representations. Initial support here is focused on a dense row count with a sparse set of columns.

## Hashing Trick
