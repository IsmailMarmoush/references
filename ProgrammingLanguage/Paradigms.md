## Programming Paradigm VS Design Pattern VS APP Architecture

http://stackoverflow.com/questions/4787799/difference-between-programming-paradigm-design-pattern-and-application-architec

**Programming Paradigm:**
Something like "Functional Programming", "Procedural Programming", and "Object Oriented Programming". The programming
paradigm and the languages that use them inform how the code gets written. For example, in Object Oriented programming
the code is divided up into classes (sometimes a language feature, sometimes not (e.g. javascript)), and typically
supports inheritance and some type of polymorphism. The programmer creates the classes, and then instances of the
classes (i.e. the objects) to carry out the operation of the program. In functional languages, the state changes on the
computer are very heavily controlled by the language itself. Functions are first class objects, although not all
languages where functions are first class objects are functional programming language (this topic is one of good debate)
. Code written with a functional languages involves lots of nested functions, almost every step of the program is new
function invocation. For procedural programming, C programs and bash scripting are good examples, you just say do step
1, do step 2, etc, without creating classes and whatnot.

**Design Pattern:**
A design pattern is a useful abstraction that can be implemented in any language. It is a "pattern" for doing things.
Like if you have a bunch of steps you want to implement, you might use the 'composite' and 'command' patterns so make
your implementation more generic. Think of a pattern as an established template for solving a common coding task in a
generic way.

**Application Architecture:**
Takes into consideration how you build a system to do stuff. So, for a web application, the architecture might involve x
number of gateways behind a load balancer, that asynchronously feed queues. Messages are picked up by y processes
running on z machines, with 1 primary db and a backup slave. Application architecture involves choosing the platform,
languages, frameworks used. This is different than software architecture, which speaks more to how to actually implement
the program given the software stack.

## Programming Paradigms

[Action](http://en.wikipedia.orghttp://en.wikipedia.org/wiki/Action_language)
[Agent-oriented](http://en.wikipedia.org/wiki/Agent-oriented_programming "Agent-oriented programming")
[Automata-based](http://en.wikipedia.org/wiki/Automata-based_programming "Automata-based programming")
[Concurrent computing](http://en.wikipedia.org/wiki/Concurrent_computing "Concurrent computing")

* [Relativistic programming](http://en.wikipedia.org/wiki/Relativistic_programming "Relativistic programming")

[Data-driven](http://en.wikipedia.org/wiki/Data-driven_programming "Data-driven programming")
[Declarative](http://en.wikipedia.org/wiki/Declarative_programming "Declarative programming") (
contrast: [Imperative](http://en.wikipedia.org/wiki/Imperative_programming "Imperative programming"))

* [Constraint](http://en.wikipedia.org/wiki/Constraint_programming "Constraint programming")
* [Dataflow](http://en.wikipedia.org/wiki/Dataflow_programming "Dataflow programming")
    * [Flow-based](http://en.wikipedia.org/wiki/Flow-based_programming "Flow-based programming")
    * Cell-oriented ([spreadsheets](http://en.wikipedia.org/wiki/Spreadsheet "Spreadsheet"))
    * [Reactive](http://en.wikipedia.org/wiki/Reactive_programming "Reactive programming")
* [Functional](http://en.wikipedia.org/wiki/Functional_programming "Functional programming")
    * [Functional logic](http://en.wikipedia.org/wiki/Functional_logic_programming "Functional logic programming")
* [Logic](http://en.wikipedia.org/wiki/Logic_programming "Logic programming")
    * [Abductive logic](http://en.wikipedia.org/wiki/Abductive_logic_programming "Abductive logic programming")
    * [Answer set](http://en.wikipedia.org/wiki/Answer_set_programming "Answer set programming")
    * [Concurrent logic](http://en.wikipedia.org/wiki/Concurrent_logic_programming "Concurrent logic programming")
    * [Constraint logic](http://en.wikipedia.org/wiki/Constraint_logic_programming "Constraint logic programming")
        * [Concurrent constraint logic](http://en.wikipedia.org/wiki/Concurrent_constraint_logic_programming "Concurrent constraint logic programming")
    * [Functional logic](http://en.wikipedia.org/wiki/Functional_logic_programming "Functional logic programming")
    * [Inductive logic](http://en.wikipedia.org/wiki/Inductive_logic_programming "Inductive logic programming")

[End-user programming](http://en.wikipedia.org/wiki/End-user_development "End-user development")
[Event-driven](http://en.wikipedia.org/wiki/Event-driven_programming "Event-driven programming")

* [Service-oriented](http://en.wikipedia.org/wiki/Service-oriented_architecture "Service-oriented architecture")
* [Time-driven](http://en.wikipedia.org/wiki/Time-driven_programming "Time-driven programming")

[Expression-oriented](http://en.wikipedia.org/wiki/Expression-oriented_programming_language "Expression-oriented programming language")
[Feature-oriented](http://en.wikipedia.org/wiki/Feature-oriented_programming "Feature-oriented programming")
[Function-level](http://en.wikipedia.org/wiki/Function-level_programming "Function-level programming") (
contrast: [Value-level](http://en.wikipedia.org/wiki/Value-level_programming "Value-level programming"))
[Generic](http://en.wikipedia.org/wiki/Generic_programming "Generic programming")
[Imperative](http://en.wikipedia.org/wiki/Imperative_programming "Imperative programming") (
contrast: [Declarative](http://en.wikipedia.org/wiki/Declarative_programming "Declarative programming"))

* [Literate](http://en.wikipedia.org/wiki/Literate_programming "Literate programming")
* [Procedural](http://en.wikipedia.org/wiki/Procedural_programming "Procedural programming")

[Language-oriented](http://en.wikipedia.org/wiki/Language-oriented_programming "Language-oriented programming")

* [Natural language programming](http://en.wikipedia.org/wiki/Natural_language_programming "Natural language programming")
* [Discipline-specific](http://en.wikipedia.org/wiki/Service-oriented_modeling#Discipline-specific_modeling "Service-oriented modeling")
* [Domain-specific](http://en.wikipedia.org/wiki/Domain-specific_language "Domain-specific language")
* [Grammar-oriented](http://en.wikipedia.org/wiki/Grammar-oriented_programming "Grammar-oriented programming")
    * [Dialecting](http://en.wikipedia.org/wiki/Dialecting "Dialecting")
* [Intentional](http://en.wikipedia.org/wiki/Intentional_programming "Intentional programming")
  [Metaprogramming](http://en.wikipedia.org/wiki/Metaprogramming "Metaprogramming")
* [Automatic](http://en.wikipedia.org/wiki/Automatic_programming "Automatic programming")
* [Reflective](http://en.wikipedia.org/wiki/Reflection_(computer_programming) "Reflection (computer programming)")
    * [Attribute-oriented](http://en.wikipedia.org/wiki/Attribute-oriented_programming "Attribute-oriented programming")
* [Homoiconic](http://en.wikipedia.org/wiki/Homoiconicity "Homoiconicity")
* [Template](http://en.wikipedia.org/wiki/Template_metaprogramming "Template metaprogramming")
    * [Policy-based](http://en.wikipedia.org/wiki/Policy-based_design "Policy-based design")

[Non-structured](http://en.wikipedia.org/wiki/Non-structured_programming "Non-structured programming") (
contrast: [Structured](http://en.wikipedia.org/wiki/Structured_programming "Structured programming"))

* [Array](http://en.wikipedia.org/wiki/Array_programming "Array programming")

[Nondeterministic](http://en.wikipedia.org/wiki/Nondeterministic_programming "Nondeterministic programming")
[Parallel computing](http://en.wikipedia.org/wiki/Parallel_computing "Parallel computing")

* [Process-oriented](http://en.wikipedia.org/wiki/Process-oriented_programming "Process-oriented programming")

[Point-free style](http://en.wikipedia.org/wiki/Tacit_programming "Tacit programming")

* [Concatenative](http://en.wikipedia.org/wiki/Concatenative_programming_language "Concatenative programming language")

[Semantic](http://en.wikipedia.org/wiki/Semantic-oriented_programming "Semantic-oriented programming")
[Structured](http://en.wikipedia.org/wiki/Structured_programming "Structured programming") (
contrast: [Non-structured](http://en.wikipedia.org/wiki/Non-structured_programming "Non-structured programming"))

* [Block-structured](http://en.wikipedia.org/wiki/Block_(programming) "Block (programming)")
* [Modular](http://en.wikipedia.org/wiki/Modular_programming "Modular programming") (
  contrast: [Monolithic](http://en.wikipedia.org/wiki/Monolithic_application "Monolithic application"))
* [Object-oriented (OOP)](http://en.wikipedia.org/wiki/Object-oriented_programming "Object-oriented programming")
    * [Class-based](http://en.wikipedia.org/wiki/Class-based_programming "Class-based programming")
    * [Concurrent](http://en.wikipedia.org/wiki/Concurrent_object-oriented_programming "Concurrent object-oriented programming")
    * [Prototype-based](http://en.wikipedia.org/wiki/Prototype-based_programming "Prototype-based programming")
    * By [separation of concerns](http://en.wikipedia.org/wiki/Separation_of_concerns "Separation of concerns"):
        * [Aspect-oriented](http://en.wikipedia.org/wiki/Aspect-oriented_programming "Aspect-oriented programming")
        * [Role-oriented](http://en.wikipedia.org/wiki/Role-oriented_programming "Role-oriented programming")
        * [Subject-oriented](http://en.wikipedia.org/wiki/Subject-oriented_programming "Subject-oriented programming")
* [Recursive](http://en.wikipedia.org/wiki/Recursion_(computer_science) "Recursion (computer science)")

[Value-level](http://en.wikipedia.org/wiki/Value-level_programming "Value-level programming") (
contrast: [Function-level](http://en.wikipedia.org/wiki/Function-level_programming "Function-level programming"))
[Probabilistic](http://en.wikipedia.org/wiki/Probabilistic_programming_language "Probabilistic programming language")
[Concept](http://en.wikipedia.org/wiki/Concept_programming "Concept programming")

# Functional Programming

## Functional Design Patterns

* ~~[David Sankel: Monoids, Monads, and Applicative Functors: Repeated Software Patterns
  ](https://www.youtube.com/watch?v=DiisKQAkGM4)~~

### Category Theory Family

https://en.wikibooks.org/wiki/Haskell/Category_theory
http://etorreborre.blogspot.de/2011/06/essence-of-iterator-pattern.html

### Monoids (ok)

* a o b = b o a
* e o x = x o e = x
* Monoids scale very well (Map reduce)
* Monoids compose with functions , optionals etc
* Monoids are very common

### Functors

* A functor is a class template` Functor <T>` with a Single template parameter (T) and a callable (map)
* Functor has following props:
    * `map(f,a) => Functor <U>` where "a" is functor instance and f is function
    * if f(t)==t for all values of t of type T, then map(f,a)==a for all values of a of type` Functor <T>`
    * map(g,map(f,a))  same as map(gf,a)
* Functors are like containers
* map applices a functor to the container resulting in a new container with the same type but the value inside might
  change

### Applicatives

### Applicative Functor

* `ApplicativeFunctor<T>` is a functor with two extra operations:
    * pure(t) where t is of type T results in a vlue of type `Applicative<T>`
    * pure wraps a value into the container
    * apply(applic functor function, applic functor value) is just like map except the function is already in the
      applicative
    * apply applies a contained function to a contained value to get a contained result
    * note that apply can be extended to n argument functions

### Monads

* A monad (`Monad <T>`) is an applicative functor with an extra operation join (flat in scala)
* join (a) where is of type `Monad<Monad<T>>` results in a value of type `Monad<T>`
* Collections supporting map and flatMap are referred to as monadic. Most Scala collections are monadic, and operating
  on them using map and flatMap operations, or using for-comprehensions is referred to as monadic-style. People will
  often refer to the monadic nature of a collection (or other container) using the word monad, eg. the “List monad”.
* https://stackoverflow.com/questions/28139259/why-do-we-need-monads
* https://mttkay.github.io/blog/2014/01/25/your-app-as-a-function/
* https://mttkay.github.io/blog/2014/01/25/monads-your-app-as-a-function-part-2/

### Monadic Bind Operator

### Semigroup

### Comonads

### Arrow

### Category

# Effective Scala and Style

* ~~[Principle of Least Power](http://www.lihaoyi.com/post/StrategicScalaStylePrincipleofLeastPower.html)~~
* [effective scala video](https://www.youtube.com/watch?v=YZxL0alO1yc)
* [Scala Style for SBT](http://www.scalastyle.org/sbt.html)
* [Scala Style for Eclipse](http://www.scalastyle.org/downloads/kepler-0.7.0/site/)
* [Twitter Effective Scala](http://twitter.github.io/effectivescala/)
* [Twitter Effective Scala youtube](https://www.youtube.com/watch?v=JZSJ6P6IpWs)
* ~~[Package Objects details](http://naildrivin5.com/scalatour/wiki_pages/PackageObjects/)~~
* ~~[Package Objects SOF](http://stackoverflow.com/questions/3400734/package-objects)~~
* https://github.com/alexandru/scala-best-practices
* http://docs.scala-lang.org/style/
* https://github.com/puffnfresh/wartremover
* [Error Handling](http://longcao.org/2015/06/15/easing-into-functional-error-handling-in-scala)

# Analytics Tools

* https://blog.codacy.com/review-of-scala-static-analysis-tools-11afa6451146
* https://github.com/wartremover/wartremover
* https://github.com/sksamuel/scapegoat

