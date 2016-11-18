---
layout: docs
title:  "Adaptive Vector"
section: "data"
source: "algebird-core/src/main/scala/com/twitter/algebird/AdaptiveVector.scala"
scaladoc: "#com.twitter.algebird.AdaptiveVector"
---

### AdaptiveVector

An IndexedSeq that automatically switches representation between dense and sparse depending on sparsity Should be an efficient representation for all sizes, and it should not be necessary to special case immutable algebras based on the sparsity of the vectors. See `DenseVector` and `SparseVector`.
