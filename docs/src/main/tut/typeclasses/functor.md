---
layout: docs
title:  "Functor"
section: "typeclasses"
source: "algebird-core/src/main/scala/com/twitter/algebird/Functor.scala"
scaladoc: "#com.twitter.algebird.Functor"
---

# Functor

Note - don't use this, use cats.

/**
 * Simple implementation of a Functor type-class.
 *
 * Laws Functors must follow:
 *  map(m)(id) == m
 *  map(m)(f andThen g) == map(map(m)(f))(g)
 */
