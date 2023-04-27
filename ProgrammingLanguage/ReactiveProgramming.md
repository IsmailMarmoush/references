# Reactive programming

## Reactive Programming and Reactive Streams

* ~~[Reactive streams in Java](https://springframework.guru/reactive-streams-in-java/)~~
*
~~[Notes on Reactive Programming](https://spring.io/blog/2016/06/07/notes-on-reactive-programming-part-i-the-reactive-landscape)~~
* [Advanced Reactive Libraries Generations](https://akarnokd.blogspot.com/2016/03/operator-fusion-part-1.html)
* [Java 8 Streams vs RxJava Streams](https://stackoverflow.com/questions/30216979/difference-between-java-8-streams-and-rxjava-observables)

## Streams and Futures

* `Future<T>`: Blocking not a stream
* `CompeletableFuture<T>`: non-blocking but not a stream
* `Stream<T>`: blocking, stream
* InputStream, Outputstream: blocking, stream, as soon as we have anything with latency it will block (examples HTTP,
  IO)

## Project Reactor

* https://projectreactor.io/learn
* http://projectreactor.io/docs/core/release/reference/#intro-reactive
* https://akarnokd.blogspot.com/
* https://github.com/reactor/reactor-core/blob/master/src/docs/asciidoc/advancedFeatures.adoc
* https://stackoverflow.com/questions/61654947/how-to-dynamically-add-elements-to-reactor-hot-flux-from-another-method
* https://github.com/artshell/ReactorExamples/blob/master/src/main/java/com/artshell/reactor/operators/FluxGenerate.java

## Reactor based libraries

* https://r2dbc.io/
    * https://github.com/r2dbc
    * https://r2dbc.io/drivers/
    * https://spring.io/blog/2018/12/07/reactive-programming-and-relational-databases
    * http://www.julienviet.com/reactive-pg-client/guide/java/
* http://rsocket.io/
* https://docs.cloudfoundry.org/concepts/overview.html

## Examples

https://github.com/matn7/spring-reactive/tree/e02761095c0b397308000a86c4c95a56956c573d/src/test/java/com/pandatronik/learnreactivespring/fluxandmonoplayground
https://github.com/zengularity/1001echanges/tree/2faaa4fc9ff51db507bb8271e8a2ac861dc4a2e6/backend/src/main/java/com/fabernovel/milleunechanges/rest

## Functional Reactive Programming

- Declarative (contrast: [Imperative Programming](https://en.wikipedia.org/wiki/Imperative_programming ))
    - [Functional Programming](https://en.wikipedia.org/wiki/Functional_programming )
        - [Functional logic Programming](https://en.wikipedia.org/wiki/Functional_logic_programming )
        - [Purely functional Programming](https://en.wikipedia.org/wiki/Purely_functional_programming )
    - [Logic Programming](https://en.wikipedia.org/wiki/Logic_programming )
        - [Abductive logic Programming](https://en.wikipedia.org/wiki/Abductive_logic_programming )
        - [Answer set Programming](https://en.wikipedia.org/wiki/Answer_set_programming )
        - [Concurrent logic Programming](https://en.wikipedia.org/wiki/Concurrent_logic_programming )
        - [Functional logic Programming](https://en.wikipedia.org/wiki/Functional_logic_programming )
        - [Inductive logic Programming](https://en.wikipedia.org/wiki/Inductive_logic_programming )
    - [Constraint Programming](https://en.wikipedia.org/wiki/Constraint_programming )
        - [Constraint logic Programming](https://en.wikipedia.org/wiki/Constraint_logic_programming )
            - [Concurrent constraint logic Programming](https://en.wikipedia.org/wiki/Concurrent_constraint_logic_programming )
    - [Dataflow Programming](https://en.wikipedia.org/wiki/Dataflow_programming )
        - [Flow-based Programming](https://en.wikipedia.org/wiki/Flow-based_programming )
        - Cell-oriented ([spreadsheets](https://en.wikipedia.org/wiki/Spreadsheet ))
        - [Reactive](https://en.wikipedia.org/wiki/Reactive_programming )
            - Reactive has three approaches: Imperative, OO, functional
            -

            *
            ~~[What is functional reactive programming](https://stackoverflow.com/questions/1028250/what-is-functional-reactive-programming)~~
