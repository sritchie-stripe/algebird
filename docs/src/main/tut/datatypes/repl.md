---
layout: docs
title:  "Learning Algebird at the REPL"
section: "data"
---

# Learning Algebird Monoids at the REPL

- [Overview](#overview)
- [Preliminaries](#prelim)
- [Max](#max)
- [Min](#min)
- [General - Adding and Multiplication of collections](#general)

## <a id="overview" href="#overview"></a> Overview

The goal of this page is to show you how easy it is to learn and experiment with Algebird data structures with a REPL. Most of the examples are taken from Algebird tests.

It is helpful to have a conceptual understanding of Algebird. Check out the tutorials at [Resources for Learners]({{ site.baseurl }}/resources_for_learners.html).

## <a id="prelim" href="#prelim"></a> Preliminaries

Clone the repository:

```
$ git clone https://github.com/twitter/algebird.git
$ cd algebird
$ ./sbt "project algebird-core" console
```

Import algebird:

```tut
import com.twitter.algebird._
```

## <a id="max" href="#max"></a> Max

Example from <http://www.michael-noll.com/blog/2013/12/02/twitter-algebird-monoid-monad-for-large-scala-data-analytics/>

```tut
import com.twitter.algebird.Operators._
Max(10) + Max(30) + Max(20)

case class TwitterUser(val name: String, val numFollowers: Int) extends Ordered[TwitterUser] {
  def compare(that: TwitterUser): Int = {
    val c = this.numFollowers - that.numFollowers
    if (c == 0) this.name.compareTo(that.name) else c
  }
}
```

Let's have a popularity contest on Twitter.  The user with the most followers wins!

```tut
val barackobama = TwitterUser("BarackObama", 40267391)
val katyperry = TwitterUser("katyperry", 48013573)
val ladygaga = TwitterUser("ladygaga", 40756470)
val miguno = TwitterUser("miguno", 731) // I participate, too.  Olympic spirit!
val taylorswift = TwitterUser("taylorswift13", 37125055)
val winner: Max[TwitterUser] = Max(barackobama) + Max(katyperry) + Max(ladygaga) + Max(miguno) + Max(taylorswift)

assert(winner.get == katyperry)
```

## <a id="min" href="#min"></a> Min

```tut
Min(10) + Min(20) + Min(30)
import com.twitter.algebird.Operators._
Min(10) + Min(20) + Min(30)
```

## <a id="general" href="#general"></a> General - Adding and Multiplication of collections

```tut:book
val data2 = Map(1 -> 1, 2 -> 1)
val data1 =  Map(1 -> 3, 2 -> 5, 3 -> 7, 5 -> 1)
data1 + data2
import com.twitter.algebird.Operators._
data1 + data2
data1 * data2
Set(1,2,3) + Set(3,4,5)
List(1,2,3) + List(3,4,5)
Map(1 -> 3, 2 -> 4, 3 -> 1) * Map(2 -> 2)
Map(1 -> Set(2,3), 2 -> Set(1)) + Map(2 -> Set(2,3))
```
