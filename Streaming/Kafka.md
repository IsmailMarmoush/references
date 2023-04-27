# Kafka

Kafka is a distributed messaging engine.

* scalable
* fault tolerant
* high-performance
* Low latency
* powerful streaming platform for processing real-time streams of events.

## Introduction

* [Introduction to Kafka james ward](https://www.youtube.com/watch?v=UEg40Te8pnE)
* [Exactly once semantics](https://www.confluent.io/blog/exactly-once-semantics-are-possible-heres-how-apache-kafka-does-it/)
* https://jack-vanlightly.com/blog/2017/12/15/rabbitmq-vs-kafka-part-4-message-delivery-semantics-and-guarantees
* https://medium.com/@ajmalbabu/kafka-0-9-0-clients-db1f43257d30
* https://community.cloudera.com/t5/Community-Articles/Understanding-Kafka-Consumer-partition-assignment-and/ta-p/248419
* https://www.confluent.io/blog/put-several-event-types-kafka-topic/
* https://www.confluent.io/blog/event-sourcing-cqrs-stream-processing-apache-kafka-whats-connection/
* https://groups.google.com/forum/#!topic/confluent-platform/XQTjNJd-TrU
* https://github.com/reactor/reactor-kafka/blob/master/reactor-kafka-samples/src/main/java/reactor/kafka/samples/SampleProducer.java
* https://github.com/reactor/reactor-kafka/blob/master/reactor-kafka-samples/src/main/java/reactor/kafka/samples/SampleConsumer.java
* https://medium.com/@stephane.maarek/the-kafka-api-battle-producer-vs-consumer-vs-kafka-connect-vs-kafka-streams-vs-ksql-ef584274c1e

## Kafka UI

* https://towardsdatascience.com/overview-of-ui-tools-for-monitoring-and-management-of-apache-kafka-clusters-8c383f897e80
* https://github.com/provectus/kafka-ui
* https://github.com/tchiotludo/akhq
* https://github.com/obsidiandynamics/kafdrop

## Kafka APIs

* https://kafka.apache.org/documentation/#api

## Kafka at most once Delivery

* Registration using the `subscribe()` method call.
* Do not provide the second optional listener parameter when subscribing the consumer
* Set ‘enable.auto.commit’ to true.
* Set ‘auto.commit.interval.ms’ to a lower timeframe.
* And do not make call to consumer.commitSync(); from the consumer.
    * With this configuration of consumer, Kafka would auto commit offset at the specified interval.

## Kafka at least once delivery

* Registration using the `subscribe()` method call.
* Do not provide the second optional listener parameter when subscribing the consumer
* Set ‘enable.auto.commit’ to false
* Or, set ‘enable.auto.commit’ to true with ‘auto.commit.interval.ms’ to a higher number.
* Consumer should now then take control of the message offset commits to Kafka by making the following call
  consumer.commitSync();

## Kafka Exactly once Delivery

* **First way**
    * Registration using the subscribe method call
    * Provide listener which can be used to set offset
    * Set enable.auto.commit = false
    * Don’t make call to consumer.commitSync(); after processing message.
    * Implement a ConsumerRebalanceListener and within the listener perform `consumer.seek(topicPartition,offset);` to
      start reading from a specific offset of that topic/partition.
    * While processing the messages, get hold of the offset of each message.
        * Store the processed message’s offset in an atomic way along with the processed message using
          atomic-transaction.
        * When data is stored in relational database atomicity is easier to implement.
        * For non-relational data-store such as HDFS store or No-SQL store one way to achieve atomicity is as follows:
            * Store the offset along with the message.
        * Implement idempotent as a safety net.

* **Second way**
    * Registration of consumer to Kafka with an assign method call.
        * When a consumer is registered with an assign method call, Kafka does not offer an automatic re-balance of the
          consumers.
    * Register consumer to specific partition using ‘assign’ call.
    * On start up of the consumer seek to specific message offset by calling consumer.seek(topicPartition,offset);
    * While processing the messages, get hold of the offset of each message.
        * Store the processed message’s offset in an atomic way along with the processed message using
          atomic-transaction.
        * When data is stored in relational database atomicity is easier to implement.
        * For non-relational data-store such as HDFS store or No-SQL store one way to achieve atomicity is as follows:
            * Store the offset along with the message.
    * Implement idempotent as a safety net.

## References

* https://www.youtube.com/watch?v=7JYEEx7SBuE
* https://www.confluent.io/blog/intro-to-ksqldb-sql-database-streaming/
* https://docs.confluent.io/platform/current/streams/introduction.html
* https://docs.confluent.io/platform/current/streams/developer-guide/interactive-queries.html#streams-developer-guide-interactive-queries
* https://docs.confluent.io/platform/current/streams/quickstart.html
* https://www.confluent.io/blog/kafka-streams-vs-ksqldb-compared/
* https://kafka-tutorials.confluent.io/kafka-console-consumer-read-specific-offsets-partitions/kafka.html
* https://github.com/JavaCodeStream/kafka-beginners/blob/2966575780e3bddd00eaa0f3371a9e5cfb00179c/kafka-streams-filter-tweets/src/main/java/com/github/simplesteph/kafka/tutorial4/StreamsFilterTweets.java
* https://docs.confluent.io/platform/current/ksqldb/overview.html
* https://docs.confluent.io/platform/current/streams-ksql.html
* https://github.com/memoria-io/jutils/commit/d9405e244ed2f1cc06e03de69d0b4e61bf6e06b3
* https://github.com/search?q=KafkaStreams+streams&type=code
* https://www.jesse-anderson.com/2019/10/why-i-recommend-my-clients-not-use-ksql-and-kafka-streams/