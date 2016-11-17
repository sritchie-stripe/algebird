---
layout: docs
title:  "Type Classes"
section: "typeclasses"
position: 1
---

## Index

{% for x in site.pages %}
{% if x.section == 'typeclasses' %}
- [{{x.title}}]({{site.baseurl}}{{x.url}})
{% endif %}
{% endfor %}


# Typeclasses

The good stuff.

# Syntax

talk about operators https://github.com/twitter/algebird/blob/develop/algebird-core/src/main/scala/com/twitter/algebird/Operators.scala


## Hash128

A typeclass to represent hashing to 128 bits. Used for HLL, but possibly other applications.

## Aggregator

Crucial - prepare, agg, present

### Preparer

/**
 * Preparer is a way to build up an Aggregator through composition using a
 * more natural API: it allows you to start with the input type and describe a series
 * of transformations and aggregations from there, rather than starting from the aggregation
 * and composing "outwards" in both directions.
 *
 * Uses of Preparer will always start with a call to Preparer[A], and end with a call to
 * monoidAggregate or a related method, to produce an Aggregator instance.

https://github.com/twitter/algebird/blob/develop/algebird-core/src/main/scala/com/twitter/algebird/Preparer.scala

## Fold

Folds are first-class representations of "Traversable.foldLeft." They have the nice property that they can be fused to work in parallel over an input sequence.

## Buffered

Represents something that consumes I and may emit O. Has some internal state that may be used to improve performance. Generally used to model folds or reduces (see BufferedReduce)

### BufferedReduce

Version of this that never emits on put... Used in `sumOption` for the generated tuple semigroups and case class semigroups and `BufferedSumAll`.

## StatefulSummer

/**
 * A Stateful summer is something that is potentially more efficient
 * (a buffer, a cache, etc...) that has the same result as a sum:
 * Law 1: Semigroup.sumOption(items) ==
 *   (Monoid.plus(items.map { stateful.put(_) }.filter { _.isDefined }, stateful.flush) &&
 *     stateful.isFlushed)
 * Law 2: isFlushed == flush.isEmpty
 * @author Oscar Boykin
 */
