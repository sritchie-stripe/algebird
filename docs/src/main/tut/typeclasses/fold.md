---
layout: docs
title:  "Fold"
section: "typeclasses"
source: "algebird-core/src/main/scala/com/twitter/algebird/Fold.scala"
scaladoc: "#com.twitter.algebird.Fold"
---

# Fold

Folds are first-class representations of `Traversable.foldLeft`. They have the nice property that they can be fused to work in parallel over an input sequence.
