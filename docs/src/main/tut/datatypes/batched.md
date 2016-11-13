---
layout: docs
title:  "Batched"
section: "summer"
source: "algebird-core/src/main/scala/com/twitter/algebird/Batched.scala"
scaladoc: "#com.twitter.algebird.Batched.scala"
---

/**
 * Batched: the free semigroup.
 *
 * For any type `T`, `Batched[T]` represents a way to lazily combine T
 * values as a semigroup would (i.e. associatively). A `Semigroup[T]`
 * instance can be used to recover a `T` value from a `Batched[T]`.
 *
 * Like other free structures, Batched trades space for time. A sum of
 * batched values defers the underlying semigroup action, instead
 * storing all values in memory (in a tree structure). If an
 * underlying semigroup is available, `Batched.semigroup` and
 * `Batch.monoid` can be configured to periodically sum the tree to
 * keep the overall size below `batchSize`.
 *
 * `Batched[T]` values are guaranteed not to be empty -- that is, they
 * will contain at least one `T` value.
 */
