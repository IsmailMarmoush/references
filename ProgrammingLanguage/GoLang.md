# Installation

```
# Download binary and unzip
# Set paths
export GOROOT=$SOURCES/go
export GOPATH=$SOURCES/go_path
export PATH=$PATH:$GOROOT:$GOROOT/bin:$GOPATH/bin
# Install Essentials
go get -u golang.org/x/tools/cmd/...
go get -u github.com/golang/lint/golint
```

# Questions

* Go Path for all or specific projects ?
* Do you use defer ?
* What's the use of pointers in Go, if there is no pointer arithmetic.
* Why cap grew to 2 instead of one in line 10 , (the second print ) https://tour.golang.org/moretypes/15
* Why nil map is never reassigned

# Testing

```
# To run tests for all packages I have !
go test github.com/ismailmarmoush/...
```

# Interfaces

If any type A that has methods one of them implements interface B methods, then A can be passed to a function that has
interface B argument

```

```

# Design Patterns

# Pointers and (Methods, Interfaces)

* In general, all methods on a given type should have either value or pointer receivers, but not a mixture of both. (
  We'll see why over the next few pages.)
* There is an error in the example code on line 22. Vertex (the value type) doesn't implement Abser because the Abs
  method is defined only on *Vertex (the pointer type).

# First Impression Pros

* I like the clear error messages so far, with line and column numbers !
* I like the int16 etc types
* I like there are no semicolons
* I like that it has math complex notations even if I hate imaginary numbers
* Tutorial is damn simple !
* Syntax is a bit strange but also simple and short
* If it is as simple as it looks, I'd feel super productive with it
* With such syntax I feel close to Algorithms implementations without a huge fear I used to have when wanted to
  implement any algorithm in Scala.
* "Go has only one looping construct, the for loop."  I love this !
* Scala is a productivity killer, for a developer who want to get shit done, it might be good for a college student who
  has all the time in the world to learn.
* I never liked that there is always a library in Java for anything needed to be done, I wanted to have the excuse to
  implement things on my and understand algorithms behind it.
* I needed the strictness and simplicity of Java, without verbosity or JVM
* I needed a language that compiles to machine code and super fast !
* Golang testing is damn awesome man !!  it makes you learn very good stuff , I love the conventions just naming the the
  method TestXxx !! or Example or Benchmark, these are the things that actually matter , the scientists who made it
  thought well of what is actually needed to make great apps I press save on Atom and tests runs !! and tells me the
  coverage and highlights the part of the if statement that wasn't tested !!! msh mmken bgd,, it takes ages for a damn
  test to run in scala
* standardization and opinionism is not bad and it has already been there
*

# First Impression Cons

* Panicking !, where are the objects and classes ?!
