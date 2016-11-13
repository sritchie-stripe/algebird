---
layout: docs
title:  "Min Plus Algebra"
section: "data"
source: "algebird-core/src/main/scala/com/twitter/algebird/MinPlus.scala"
scaladoc: "#com.twitter.algebird.MinPlus.scala"
---

# Min Plus Algebra

/*
 * The Min-Plus algebra, or tropical semi-ring is useful for computing shortest
 * paths on graphs:
 * @see <a href="http://en.wikipedia.org/wiki/Min-plus_matrix_multiplication">Min-plus Matrix Product"</a>
 * The shortest path from i->j in k or less steps is ((G)^k)_{ij}
 * @see <a href="http://en.wikipedia.org/wiki/Tropical_geometry">Tropical Geometry</a>
 * @see <a href="http://en.wikipedia.org/wiki/Semiring">Semiring definition</a>
 */
