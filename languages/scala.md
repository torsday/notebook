# Scala

-   General purpose programming language.
-   Full support for functional programming and a very strong static type system.
-   Designed to be concise.
-   Many of Scala's design decisions were inspired by criticism of the shortcomings of Java.
-   Scala source code is intended to be compiled to Java bytecode, so that the resulting executable code runs on a Java virtual machine.
-   Java libraries may be used directly in Scala code and vice versa (language interoperability).
-   Like Java, Scala is object-oriented, and uses a curly-brace syntax reminiscent of the C programming language.
-   Unlike Java, Scala has many features of functional programming languages like Scheme, Standard ML and Haskell, including currying, type inference, immutability, lazy evaluation, and pattern matching. It also has an advanced type system supporting algebraic data types, covariance and contravariance, higher-order types (but not higher-rank types), and anonymous types.
-   Other features of Scala not present in Java include operator overloading, optional parameters, named parameters, raw strings, and no checked exceptions.
-   The name Scala is a portmanteau of "scalable" and "language", signifying that it is designed to grow with the demands of its users.

## Basics

### Variables

```scala
var x = 5       // variable
val y = 8       // constant
val x : Int = 5 // explicit type declaration
```

### Functions

```scala
def doubler(x : Int) : Int =
  x * 2 // implicit return

def doubler(x : Int) : Int = {
  println("Since this has multiple statements, enclose in a block {}")
  x * 2
}

// A polymorphic function is paramaterized on type 'A'
// 'A' is a generic placeholder that can be used in the method signature.
def polymorphic[A](x : A) : A =
  x

// e.g. this function accepts an argument of type 'A' and returns a type 'B'
def polymorphic[A](a : A) : B

// Higher-order functions can take functions as arguments.
// In this examples, it takes a function that accepts 'A' and returns a boolean
def higherOrder[A](a: A, f: (A) => Boolean)
  if (f(a)) println("It's true")
  else println("It's false")

// Returns an anonymous function that accepts 'A' and returns the result of
// composing the functions f and g.
def compose[A](f: A => A, g: A => A) : A =
  (x : A) => f(g(a))

def curry[A, B](a : A, f: (A, B) => C) : B => C =
  (b: B) => f(a, b)

// Lazy (non-strict) evaluation of function arguments
// onTrue and onFalse are no evaluated until called explicitly ('thunks')
def if2[A] (cond: Boolena, onTrue: => A, onFalse => A): A =
  if (cond) onTrue else onFalse
```

## Packages

```scala
// wildcard import
import scala.collection._

// selective import
import scala.collection.{Vector, Sequence}

// renaming import
import scala.collection.{Vector => Vec}
```

## Examples

### Hello World

Make file: `HelloWorld.scala`

```scala
object HelloWorld extends App {
  println("Hello, World!")
}
```

Compile

```sh
scalac HelloWorld.scala
```

Run

```sh
scala HelloWorld
```

### Hello World (OOP)

```scala
object HelloWorld {
  /** 'main' is your entry point into your program.
    * The method signature indicates:
    *   - argument ('args')
    *   - argument type (Array[String])
    *   - return type (Unit, like 'Void')
    */
  def main(args : Array[String]) : Unit {
    println("Hello, world!")
  }
}

object HelloWorld extends App {
  // If you extend App, all statements within this object will be run:
  println("Hello, World")
}
```

### Classes

```scala
class Point(
    val x: Double, val y: Double,
    addToGrid: Boolean = false
) {
  import Point._

  if (addToGrid)
    grid.add(this)

  def this() = this(0.0, 0.0)

  def distanceToPoint(other: Point) =
    distanceBetweenPoints(x, y, other.x, other.y)
}

object Point {
  private val grid = new Grid()

  def distanceBetweenPoints(x1: Double, y1: Double,
      x2: Double, y2: Double) = {
    math.hypot(x1 - x2, y1 - y2)
  }
}
```

---

## Testing

### Unit

-   ScalaTest

---

## References

-   [scala-lang.org](http://www.scala-lang.org)
-   <https://en.wikipedia.org/wiki/Scala_(programming_language)>
-   <http://docs.scala-lang.org/style>
-   <https://twitter.github.io/scala_school>
-   <http://danielwestheide.com/scala/neophytes.html>
