# The Scala Language

> Note this document is divided between here and the scala-samples project.
> The concepts are hopefully ordered from simplest to most complex.

# Changes

https://www.scala-lang.org/news/2.12.0-RC1#either-is-now-right-biased

# Tips

* for Public API use explicit return types.
* uniform access principle `instance.value`
* eq, ne as java ==
* == in scala calls equals
* check predef
* Prefer Seq
* Rename import (e.g Seq=> ImmutableList) and then can change it
* http://docs.scala-lang.org/overviews/collections/performance-characteristics.html

# Scala Keywords

```
abstract,case, catch, class,def,do,else,extends,false, final, finally, for, forSome, if, implicit, import, lazy, match, new, null, object, override, package, private, protected, return, sealed, super, this, throw, trait, try, true, type, val, var, while, with, yield, , -, :, =, =>, <-, <:, <%, >:, #, @
```

# Scala Data Types

* Byte
    * 8 bit signed value. Range from -128 to 127
* Short
    * 16 bit signed value. Range -32768 to 32767
* Int
    * 32 bit signed value. Range -2147483648 to 2147483647
* Long
    * 64 bit signed value. -9223372036854775808 to 9223372036854775807
* Float
    * 32 bit IEEE 754 single-precision float
* Double
    * 64 bit IEEE 754 double-precision float
* Char
    * 16 bit unsigned Unicode character. Range from U+0000 to U+FFFF
* String
    * A sequence of Chars
* Boolean
    * Either the literal true or the literal false
* Unit
    * Corresponds to no value
* Null
    * null or empty reference
* Nothing
    * The subtype of every other type; includes no values
* Any
    * The supertype of any type; any object is of type Any
* AnyRef
    * The supertype of any reference type

# Functions

## Functions And Methods [ok]

[Sandrasi VIP post](http://sandrasi-sw.blogspot.com/2012/03/understanding-scalas-partially-applied.html)

### A method in Scala [ok]

just like in Java, is a part of a class (or object) and it has a complete signature: name, arguments, return type.

### A Scala function [ok]

on the other hand is in fact a class. There is a series of traits in Scala, each of them represents a function with
various number of arguments: Function0 for parameterless functions, Function1 for functions with one parameter,
Function2 for functions with two parameters, and so on up until Function22.

### A function literal or anonymous function [ok]

is an alternate syntax to define functions. Instead of creating a new class that mixes in one of the FunctionN traits
and then overriding the apply method, we can just simply list the named function parameters in parentheses, then write a
right arrow, and then } the body of the function. For example: `(a: Int, b: Int) => a  h'+ b`

### A function value [ok]

is an instance of some class that extends one of the FunctionN traits. A function literal, for example, is first
compiled into a class that mixes in a FunctionN trait and then instantiated runtime.

```
val add = (a: Int, b: Int) => a + b
add(1, 2) // returns 3
```

### Partial Functions [ok]

Is a function that is defined for subset of x, one example is try catch - Read the Article

## Default Parameter values [ok]

http://docs.scala-lang.org/tutorials/tour/default-parameter-values.html

## Nested Functions [ok]

http://www.scala-lang.org/old/node/116.html

## Polymorphic Methods [ok]

http://docs.scala-lang.org/tutorials/tour/polymorphic-methods.html

## Currying [ok]

http://docs.scala-lang.org/tutorials/tour/currying.html

```
def add(x:Int, y:Int) = x + y
# is a normal function

def add(x:Int) = (y:Int) => x + y
# is a curried function.The return value is a function expression.

def add(x:Int)(y:Int) = x + y
# is syntactic sugar
```

### Currying Use cases [ok]

implicits rand example while(cond)(body)
while(cond){body}

## Closure Function [ok]

A closure is a function, whose return value depends on the value of one or more variables declared outside this
function.
http://www.tutorialspoint.com/scala/scala_closures.htm

## Automatic Type-Dependent Closure Construction [ok]

http://www.scala-lang.org/old/node/138

## Function Implicit Parameters [ok]

http://docs.scala-lang.org/tutorials/tour/implicit-parameters.html

## Named Parameters [ok]

http://docs.scala-lang.org/tutorials/tour/named-parameters.html

# Types

## Unified Types [ok]

http://www.scala-lang.org/old/node/128
In contrast to Java, all values in Scala are objects (including numerical values and functions). Since Scala is
class-based, all values are instances of a class.

## Local Type Inference [ok]

http://www.scala-lang.org/old/node/127

* Scala Compiler is able to infer types without explicitly writing them
* Compiler can't infer Recursive functions
* If your function is public API it's best to declare your return type

## Type Parameterization [ok]

http://stackoverflow.com/questions/12551674/what-is-meant-by-parameterized-type

Type parameterization allows you to write **Generic Classes** and traits. For example, sets are generic and take a type
parameter: they are defined as Set[T]. As a result, any particular set instance might be a Set[String], a Set[Int],
etc.—but it must be a set of something. Unlike Java, which allows raw types, Scala requires that you specify type
parameters. Variance defines inheritance relationships of parameterized types, such as whether a Set[String], for
example, is a subtype of Set[AnyRef].

## Type Ascription [ok]

* The word "Ascription" meaning: The attribution of something to a cause.
* Type ascription is just telling the compiler what type you expect out of an expression, from all possible valid types.
* It usually makes passing varargs work
*

http://stackoverflow.com/questions/2087250/what-is-the-purpose-of-type-ascriptions-in-scala

## Upper Type Bounds [ok]

An upper type bound `T <: Animal `  
Declares that type variable T refers to a subtype of type Animal. It's like the following java :

```
class K [T extends Animal] {

}
k[Dog]
```

## Lower Type Bounds [ok]

An upper type bound `T >: A`
Declares that type variable T refers to a supertype of type A.

## ~~View Bounds (deprecated)~~

http://stackoverflow.com/questions/4465948/what-are-scala-context-and-view-bounds

## Type Variances [ok]

http://docs.scala-lang.org/tutorials/tour/variances.html
http://stackoverflow.com/questions/4531455/whats-the-difference-between-ab-and-b-in-scala

```
class Foo[+A] // A covariant class
class Bar[-A] // A contravariant class
class Baz[A]  // An invariant class
```

In Scala, however, generic types have by default nonvariant (or, “rigid”) subtyping.Prefixing a formal type parameter
with a + indicates that subtyping is covariant (flexible) in that parameter. By adding this single character, you are
telling Scala that you want Queue[String], for example, to be considered a subtype of Queue[AnyRef].

```
trait Queue[+T] { ... }
```

There is also a prefix -, which indicates contravariant subtyping. If Queue were defined like this:
`trait Queue[-T] { ... }` then if T is a subtype of type S, this would imply that Queue[S] is a sub- type of Queue[T] (
which in the case of queues would be rather surprising!). Whether a type parameter is covariant, contravariant, or
nonvariant is called the parameter’s variance .

## Type Classes Pattern [notyet]

Similar to Adapter pattern, a pattern that allows you to design your programs to be open for extension without giving up
important information about concrete types.
http://danielwestheide.com/blog/2013/02/06/the-neophytes-guide-to-scala-part-12-type-classes.html

## Path dependent Types [notyet]

http://danielwestheide.com/blog/2013/02/13/the-neophytes-guide-to-scala-part-13-path-dependent-types.html

## Abstract type members [notyet]

http://danielwestheide.com/blog/2013/02/13/the-neophytes-guide-to-scala-part-13-path-dependent-types.html

## Structural Subtyping (scala's version of Duck Typing) [ok]

> If it was "walks" like a duck and "quacks" like a duck, then it's a duck

* http://alvinalexander.com/scala/how-to-use-duck-typing-in-scala-structural-types

# Objects & Classes

## Companion objects[ok]

> an object can access all private members of its companion class, just as a class can access all private members of its
> companion object.

> One exception where the similarity between Scala and Java breaks down concerns protected static members. A protected
> static member of a Java class C can be accessed in all subclasses of C. By contrast, a protected member in a companion
> object makes no sense, as singleton objects don’t have any subclasses.

## Package Objects[ok]

http://www.scala-lang.org/docu/files/packageobjects/packageobjects.html

## Stateful objects[ok]

Normal objects with var fields

## Inner Classes[ok]

http://www.scala-lang.org/old/node/115.html

## Generic Classes[ok]

http://docs.scala-lang.org/tutorials/tour/generic-classes.html

## Mixin Class Composition[ok]

http://docs.scala-lang.org/tutorials/tour/mixin-class-composition.html

## Sealed Classes[ok]

A sealed class cannot have any new subclasses added except the ones in the same file. This is very useful for pattern
matching, because it means you only need to worry about the subclasses you already know about. What’s more, you get
better compiler support as well. If you match against case classes that inherit from a sealed class, the compiler will
flag missing combinations of patterns with a warning message.

The @unchecked annotation has a special meaning for pattern matching. If a match’s selector expression carries this
annotation, exhaustivity checking for the patterns that follow will be suppressed.

## Enumeration[ok]

http://www.scala-lang.org/api/current/index.html#scala.Enumeration
Use sealed case object
http://underscore.io/blog/posts/2014/09/03/enumerations.html

```
object WeekDay {
  sealed trait EnumVal
  case object Mon extends EnumVal
  case object Tue extends EnumVal
  case object Wed extends EnumVal
  case object Thu extends EnumVal
  case object Fri extends EnumVal
  val daysOfWeek = Seq(Mon, Tue, Wed, Thu, Fri)
}
```

## Composition and Inheritance[not yet]

> The recommended convention is to use a parameterless method whenever there are no parameters and the method accesses
> mutable state only by reading fields of the containing object (in particular, it does not change mutable state). This
> convention supports the uniform access principle,1 which says that client code should not be affected by a decision to
> implement an attribute as a field or method.

## Name Spaces[ok]

Java’s four namespaces are fields, methods, types, and packages. By contrast, Scala’s two namespaces are:

1. values (fields, methods, packages, and singleton objects)
2. types (class and trait names)

## Extractor Objects[ok, needs revisit]

* http://danielwestheide.com/blog/2012/11/21/the-neophytes-guide-to-scala-part-1-extractors.html
* http://danielwestheide.com/blog/2012/11/28/the-neophytes-guide-to-scala-part-2-extracting-sequences.html
  Usually, implementing your own extractors is only necessary if you want to extract something from a type you have no
  control over, or if you need additional ways of pattern matching against certain data. For example, a common usage of
  extractors is to extract meaningful values from some string. As an exercise, think about how you would implement and
  use a URLExtractor that takes String representations of URLs. w

## Pattern Matching[ok]

* http://danielwestheide.com/blog/2012/12/05/the-neophytes-guide-to-scala-part-3-patterns-everywhere.html
  fieldConfig match { case f @ FieldConfig(fn, ft, _, _) if fn == fieldName =>
  case _ =>  ??? }

## Partial Matching[ok VIP]

* [pattern matching anonymous functions, and partial matching](http://danielwestheide.com/blog/2012/12/12/the-neophytes-guide-to-scala-part-4-pattern-matching-anonymous-functions.html)

# Traits

http://www.scala-lang.org/old/node/126
http://www.tutorialspoint.com/scala/scala_traits.htm

## Explicitly Typed Self References (aka Self Types) and Usage in cake pattern

*
~~[Best Explanation of Dependency Injection using cake,implicits, reader monad](http://blog.originate.com/blog/2013/10/21/reader-monad-for-dependency-injection/)~~
* ~~[Understanding Selftypes](http://marcus-christie.blogspot.com.eg/2014/03/scala-understanding-self-type.html)~~
* ~~[Explicitly Typed Self References](http://www.scala-lang.org/old/node/124)~~
*
~~[Extending a trait vs Self type](http://stackoverflow.com/questions/1990948/what-is-the-difference-between-self-types-and-trait-subclasses)~~
* http://jonasboner.com/real-world-scala-dependency-injection-di/
* [Cake Pattern from black lagoon](https://www.youtube.com/watch?v=yLbdw06tKPQ)
* http://docs.scala-lang.org/tutorials/tour/self-types.html

# API Related

## Sequence Comprehensions Or For expressions

http://www.scala-lang.org/old/node/111
http://www.artima.com/pins1ed/for-expressions-revisited.html

## Error Handling with Try

* http://danielwestheide.com/blog/2012/12/26/the-neophytes-guide-to-scala-part-6-error-handling-with-try.html
* https://tersesystems.com/2012/12/27/error-handling-in-scala/

## Option, some

* [http://danielwestheide.com/blog/2012/12/19/the-neophytes-guide-to-scala-part-5-the-option-type.html](http://danielwestheide.com/blog/2012/12/19/the-neophytes-guide-to-scala-part-5-the-option-type.html)
*
~~[http://blog.orbeon.com/2011/04/scalas-optionsomenone.html](http://blog.orbeon.com/2011/04/scalas-optionsomenone.html)~~
* [http://tonymorris.github.io/blog/posts/scalaoption-cheat-sheet/](http://tonymorris.github.io/blog/posts/scalaoption-cheat-sheet/)
*
~~[http://www.brunton-spall.co.uk/post/2011/12/02/map-map-and-flatmap-in-scala/](http://www.brunton-spall.co.uk/post/2011/12/02/map-map-and-flatmap-in-scala/)~~
* [http://www.tutorialspoint.com/scala/scala_options.htm](http://www.tutorialspoint.com/scala/scala_options.htm)
* http://danielwestheide.com/blog/2012/12/19/the-neophytes-guide-to-scala-part-5-the-option-type.html

## Equals Method

> The only cases where == does not directly call equals is for Java’s boxed numeric classes such as Integer or Long. In
> Java, a new Integer(1) does not equal a new Long(1) even though for primitive values 1 == 1L. Since Scala is a more
> regular language than Java it was necessary correct this discrepancy by special-casing the == method for these
> classes.
> Likewise, the ## method provides a Scala version of hashing that is the same as Java’s hashCode, except for boxed
> numeric types, where it works consistently with ==. For instance new Integer(1) and new Long(1) hash the same with ##
> even though their Java hashCodes are different.

## Regular Expression Patterns

http://www.tutorialspoint.com/scala/scala_regular_expressions.htm

## Collections

https://www.youtube.com/watch?v=uiJycy6dFSQ

### Implementing Lists

https://www.artima.com/pins1ed/implementing-lists.html

## Strict and lazy Transformers (Views)

http://www.scala-lang.org/docu/files/collections-api/collections_42.html

Collections have quite a few methods that construct new collections. Examples are map, filter or ++. We call such
methods transformers because they take at least one collection as their receiver object and produce another collection
in their result.

There are two principal ways to implement transformers. One is strict, that is a new collection with all its elements is
constructed as a result of the transformer. The other is non-strict or lazy, that is one constructs only a proxy for the
result collection, and its elements get constructed only as one demands them.

As an example of a non-strict transformer consider the following implementation of a lazy map operation:

```
def lazyMap[T, U](coll: Iterable[T], f: T => U) = new Iterable[T] {
  def iterator = coll.iterator map f
}
```

Note that lazyMap constructs a new Iterable without stepping through all elements of the given collection coll. The
given function f is instead applied to the elements of the new collection's iterator as they are demanded. Scala
collections are by default strict in all their transformers, except for Stream, which implements all its transformer
methods lazily. However, there is a systematic way to turn every collection into a lazy one and vice versa, which is
based on collection views. A view is a special kind of collection that represents some base collection, but implements
all transformers lazily.
