# Algebird's Data Types

Algebird is, first and foremost, a library of data structures for large-scale analytics. Here are the data structures currently implemented:

## Approximate Data Structures

### MinHasher

Podcast link:
Code: https://github.com/twitter/algebird/blob/develop/algebird-core/src/main/scala/com/twitter/algebird/MinHasher.scala

### [Count Min Sketch](https://github.com/twitter/algebird/blob/develop/algebird-core/src/main/scala/com/twitter/algebird/CountMinSketch.scala)

and the more general SketchMap! https://github.com/twitter/algebird/blob/develop/algebird-core/src/main/scala/com/twitter/algebird/SketchMap.scala

#### CMS Hasher

/**
 * The Count-Min sketch uses `d` (aka `depth`) pair-wise independent hash functions drawn from a universal hashing
 * family of the form:
 *
 * `h(x) = [a * x + b (mod p)] (mod m)`
 *
 * As a requirement for using CMS you must provide an implicit `CMSHasher[K]` for the type `K` of the items you want to
 * count.  Algebird ships with several such implicits for commonly used types `K` such as `Long` and [[scala.BigInt]].
 *
 * If your type `K` is not supported out of the box, you have two options: 1) You provide a "translation" function to
 * convert items of your (unsupported) type `K` to a supported type such as [[Double]], and then use the `contramap`
 * function of [[CMSHasher]] to create the required `CMSHasher[K]` for your type (see the documentation of `contramap`
 * for an example); 2) You implement a `CMSHasher[K]` from scratch, using the existing CMSHasher implementations as a
 * starting point.
 */

### [HyperLogLog](https://github.com/twitter/algebird/blob/develop/algebird-core/src/main/scala/com/twitter/algebird/HyperLogLog.scala)

### [HyperLogLogSeries](https://github.com/twitter/algebird/blob/develop/algebird-core/src/main/scala/com/twitter/algebird/HyperLogLogSeries.scala)

HLLSeries can produce a HyperLogLog counter for any window into the past, using a constant factor more space than HyperLogLog.

For each hash bucket, rather than keeping a single max RhoW value, it keeps every RhoW value it has seen, and the max timestamp where it saw that value.  This allows it to reconstruct an HLL as it would be had it started at zero at any given point in the past, and seen the same updates this structure has seen.

### Bloom Filter

### SpaceSaver, ie StreamSummary

https://github.com/twitter/algebird/blob/develop/algebird-core/src/main/scala/com/twitter/algebird/SpaceSaver.scala

## Other Data Structures

## Instances for Scala Types

- IndexedSeq.scala
- MapAlgebra with good helpers
- JavaMonoids
- PriorityQueue aggregator, monoid

### ResetState

### RightFolded

Lets you represent folds as non-commutative monoids.

### RightFolded2

/**
 * This monoid takes a list of values of type In or Out,
 * and folds to the right all the Ins into Out values, leaving
 * you with a list of Out values, then finally, maps those outs
 * onto Acc, where there is a group, and adds all the Accs up.
 * So, if you have a list:
 * I I I O I O O I O I O
 * the monoid is equivalent to the computation:
 *
 * map(fold(List(I,I,I),O)) + map(fold(List(I),O)) + map(fold(List(),O)) +
 *   map(fold(List(I),O)) + map(fold(List(I),O))
 *
 * This models a version of the map/reduce paradigm, where the fold happens
 * on the mappers for each group on Ins, and then they are mapped to Accs,
 * sent to a single reducer and all the Accs are added up.
 */

### SetDiff

Our fun new thing: https://github.com/twitter/algebird/blob/develop/algebird-core/src/main/scala/com/twitter/algebird/SetDiff.scala

### TopK (exact, faster than just doing it)

### Stochastic Gradient Descent

Basically a custom version of RightFolded that folds in your observations to your initial weights.

https://github.com/twitter/algebird/blob/develop/algebird-core/src/main/scala/com/twitter/algebird/SGDMonoid.scala

### Max, Min, First, Last

https://github.com/twitter/algebird/blob/develop/algebird-core/src/main/scala/com/twitter/algebird/OrderedSemigroup.scala

### Interval

### AdaptiveVector

An IndexedSeq that automatically switches representation between dense and sparse depending on sparsity Should be an efficient representation for all sizes, and it should not be necessary to special case immutable algebras based on the sparsity of the vectors. See `DenseVector` and `SparseVector`.

### Affine Function

Represents functions of the kind `f(x) = slope * x + intercept`

### Averaged Value

### DecayedValue

Time-decaying value.

### DecayedVector

Lets you build container classes with DecayedValue.

### Min Plus Algebra
/*
 * The Min-Plus algebra, or tropical semi-ring is useful for computing shortest
 * paths on graphs:
 * @see <a href="http://en.wikipedia.org/wiki/Min-plus_matrix_multiplication">Min-plus Matrix Product"</a>
 * The shortest path from i->j in k or less steps is ((G)^k)_{ij}
 * @see <a href="http://en.wikipedia.org/wiki/Tropical_geometry">Tropical Geometry</a>
 * @see <a href="http://en.wikipedia.org/wiki/Semiring">Semiring definition</a>
 */

### HashingTrickMonoid, or FeatureHashing

From [wiki](https://en.wikipedia.org/wiki/Feature_hashing)

> In machine learning, feature hashing, also known as the hashing trick[1] (by analogy to the kernel trick), is a fast and space-efficient way of vectorizing features, i.e. turning arbitrary features into indices in a vector or matrix. It works by applying a hash function to the features and using their hash values as indices directly, rather than looking the indices up in an associative array.

Paper: http://alex.smola.org/papers/2009/Weinbergeretal09.pdf
Post by @jhoon: http://jeremydhoon.github.io/2013/03/19/abusing-hash-kernels-for-wildly-unprincipled-machine-learning/

PR to algebird https://github.com/twitter/algebird/pull/154

### Approximate

Set, Boolean, Numeric.

## Combinators

### Eventually

Lets you switch between two representations of a thing. You use an `Either` type as the underlying data structure.

## Priority

Use if you need, say, a Monoid, but you can handle a semigroup.
https://github.com/twitter/algebird/blob/develop/algebird-core/src/main/scala/com/twitter/algebird/Priority.scala

### Combinator

Combinator on semigroups, useful for sketching combinations...

### Generated Abstract Algebra

Semigroup, Monoid, Group, Ring for tuples. Also note Generated Product Algebra, why we need this and Tuple vs Product.

### SumAll (summers)

### BufferedSumAll (summesr)

### SummingQueue - used as intermediate buffer in SB realtime (buffer)

### SummingCache (buffer)
/**
 * A Stateful Summer on Map[K,V] that keeps a cache of recent keys
 */

#### SummingWithHitsCache

#### SummingIterator (stateful summer + iter combo)

### AdaptiveCache

This is a wrapper around SummingCache that attempts to grow the capacity by up to some maximum, as long as there's enough RAM.  It determines that there's enough RAM to grow by maintaining a SentinelCache which keeps caching and summing the evicted values. Once the SentinelCache has grown to the same size as the current cache, plus some margin, without running out of RAM, then this indicates that we have enough headroom to double the capacity.

### Batched (free semigroup)

## Matrix Math

### AdaptiveMatrix
/**
 * A Matrix structure that is designed to hide moving between sparse and dense representations
 * Initial support here is focused on a dense row count with a sparse set of columns
 */

## Statistics (in subpackage)

## First Five Moments

https://github.com/twitter/algebird/blob/develop/algebird-core/src/main/scala/com/twitter/algebird/MomentsGroup.scala

### Gaussian Distribution

### StatisticsMonoid

OHHH this is for tracking stats, metrics etc on your monoid calls.

https://github.com/twitter/algebird/blob/1520068ae296d65ce3c4af7a0dc40137349f76f0/algebird-core/src/main/scala/com/twitter/algebird/statistics/Statistics.scala


## Helpers

### Bytes

A wrapper for `Array[Byte]` that provides sane implementations of `hashCode`, `equals`, and `toString`.  The wrapped array of bytes is assumed to be never modified.

Note: Unfortunately we cannot make [[Bytes]] a value class because a value class may not override the `hashCode` and `equals` methods (cf. SIP-15, criterion 4).

=Alternatives=

Instead of wrapping an `Array[Byte]` with this class you can also convert an `Array[Byte]` to a `Seq[Byte]` via
Scala's `toSeq` method:

```
val arrayByte: Array[Byte] = Array(1.toByte)
val seqByte: Seq[Byte] = arrayByte.toSeq
```

Like [[Bytes]], a `Seq[Byte]` has sane `hashCode`, `equals`, and `toString` implementations.

Performance-wise we found that a `Seq[Byte]` is comparable to [[Bytes]]. For example, a `CMS[Seq[Byte]]` was measured to be only slightly slower than `CMS[Bytes]` (think: single-digit percentages).
