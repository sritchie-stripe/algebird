---
layout: docs
title:  "RightFolded"
section: "data"
source: "algebird-core/src/main/scala/com/twitter/algebird/RightFolded.scala"
scaladoc: "#com.twitter.algebird.RightFolded.scala"
---

# RightFolded

Lets you represent folds as non-commutative monoids.

# RightFolded2

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
