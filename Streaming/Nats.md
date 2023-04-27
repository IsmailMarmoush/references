# Nats

* [Nats Intro, Message Delivery Patterns](https://youtu.be/SLb4rdI5lIM?t=11m15s)
* [NATS Intro – Colin Sullivan & Waldemar Quevedo, Synadia](https://www.youtube.com/watch?v=Y9bDY_oE80w)

## DNA

* Performance and Scalability
* Simplicity
* Security
* Availability

## what's not in Nats

* Message guarantees in core Nats
* Transactions
* Message schemas
* Last Will and Testament
    * https://www.hivemq.com/blog/mqtt-essentials-part-9-last-will-and-testament/
* Message groups

## Message Delivery

* Core nats provides at most once delivery guarantees
* Nats streaming provides at least once delivery guarantees.

## Nats Streaming

* At least once delivery
* Replay by time or sequence number offset
* Last/initial value caching ?
* Durable subscribers
    * Client picking up where it left off
* Rate matching per subscriber (backpressure messages to consumers)
* Memory, file, DB storage
* High availability through fault tolerant or clustered confiruations
* Scale through partitioning

## References

* https://github.com/nats-io/nats.java
* https://docs.nats.io/nats-concepts/jetstream/streams#:~:text=Streams%20%2D%20NATS%20Docs&text=Streams%20are%20'message%20stores'%2C,in%20the%20defined%20storage%20system
  .
* https://nats.io/blog/jetstream-java-client-03-consume/
* https://github.com/nats-io/nats.java/tree/main/src/examples/java/io/nats/examples/jetstream
* https://github.com/nats-io/nats.java/blob/main/src/examples/java/io/nats/examples/jetstream/NatsJsPushSubBasicAsync.java
* https://github.com/nats-io/nats.java/blob/5e56917429ece3421839cd56dde30c6a9170e81f/README.md
* https://nats.io/blog/jetstream-java-client-03-consume/
* https://nats.io/blog/jetstream-java-client-02-publish/
* https://hub.docker.com/_/nats