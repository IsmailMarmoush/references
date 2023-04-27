## Books

* https://jaceklaskowski.gitbooks.io/mastering-apache-spark/

## JSON

* https://spark-summit.org/2014/wp-content/uploads/2014/07/Easy-json-Data-Manipulation-Yin-Huai.pdf

## Best Practices

* https://www.gitbook.com/book/databricks/databricks-spark-knowledge-base/details

## Comparisons

* http://stackoverflow.com/questions/37301226/difference-between-dataset-api-and-dataframe

## Videos

* https://spark-summit.org/2014/
* https://spark-summit.org/2015/
* ~~[Getting Started with Apache Spark](https://datastaxacademy.com/courses/getting-started-apache-spark)~~
* ~~[Intro to Apache Spark - Brian Clapper ](https://www.youtube.com/watch?v=PFK6gsnlV5E)~~
* [An Overview of Apache Spark](https://www.youtube.com/watch?v=mL5dQ_1gkiA)
* [Diving into Apache Spark Internals (built with Scala) - Dean Chen](https://www.youtube.com/watch?v=gd4Jqtyo7mM)
* [Getting Started with Spark & Cassandra](https://www.youtube.com/watch?v=_gFgU3phogQ)
* https://academy.datastax.com/demos/datastax-enterprise-46-and-spark-sql
* https://academy.datastax.com/demos/how-spark-master-high-availability-works-dse
* https://academy.datastax.com/demos/how-spark-cassandra-connector-writes-data
* https://academy.datastax.com/demos/datastax-enterprise-new-index-tables-apache-spark
* https://academy.datastax.com/demos/datastax-enterprise-joining-tables-apache-spark
* https://academy.datastax.com/demos/datastax-enterprise-user-interaction-analysis-apache-spark
* https://academy.datastax.com/demos/datastax-enterprise-credit-card-analysis-apache-spark

## Docs

* [Building Spark](http://spark.apache.org/docs/latest/building-spark.html)
* ~~[Spark Introduction](https://www.mapr.com/ebooks/spark/01-what-is-apache-spark.html)~~
* [planet cassandra](http://www.planetcassandra.org/getting-started-with-apache-spark-and-cassandra/)
* [Spark + Cassandra by AlTobey](http://www.planetcassandra.org/blog/installing-the-cassandra-spark-oss-stack/)
* [How to install spark and cassandra](http://www.philchen.com/2015/02/16/how-to-install-apache-spark-and-cassandra-stack-on-ubuntu)
* [Spark Cassandra Connection node level](https://groups.google.com/a/lists.datastax.com/forum/#!topic/spark-connector-user/BlbC_Kj6XTI)
* https://dzone.com/articles/understanding-apache-sparks-execution-model-using?utm_content=buffer911a9&utm_medium=social&utm_source=plus.google.com&utm_campaign=buffer

## Github

* https://github.com/jdauphant/ansible-role-spark/blob/master/tasks/main.yml
* https://github.com/koeninger/spark-cassandra-example

## Tools

* https://github.com/datastax/spark-cassandra-connector
* https://github.com/ibm-et/spark-kernel/
* http://www.spark.tc/how-to-enable-interactive-applications-against-apache-spark
* https://github.com/jplock/docker-zookeeper

## Debugging

* https://github.com/databricks/spark-knowledgebase/blob/master/troubleshooting/connectivity_issues.md

## To be inspected

* http://spark.apache.org/docs/latest/monitoring.html

## Cassandra + Spark

* http://www.planetcassandra.org/getting-started-with-apache-spark-and-cassandra/
* https://databricks.com/blog/2015/06/16/zen-and-the-art-of-spark-maintenance-with-cassandra.html
* http://www.planetcassandra.org/blog/installing-the-cassandra-spark-oss-stack/
* https://github.com/datastax/spark-cassandra-connector

## AWS + SPARK

* http://tech.kinja.com/how-not-to-pull-from-s3-using-apache-spark-1704509219
* https://gist.githubusercontent.com/pjrt/f1cad93b154ac8958e65/raw/7b0b764408f145f51477dc05ef1a99e8448bce6d/S3Puller.scala
* http://stackoverflow.com/questions/24048729/how-to-read-input-from-s3-in-a-spark-streaming-ec2-cluster-application
* http://spark.apache.org/docs/latest/ec2-scripts.html
* http://wiki.apache.org/hadoop/AmazonS3
* https://github.com/zalando/spark-appliance/blob/master/spark.yaml#L153
* http://docs.stups.io/en/latest/user-guide/aws-api.html
* http://docs.stups.io/en/latest/components/senza.html#senza-taupage-auto-scaling-group

## Spark Notebooks

* http://spark-notebook.io/
    * https://groups.google.com/forum/?hl=fr#!searchin/spark-notebook-user/standalone/spark-notebook-user/DFTP2F2vIj8/TPwtwurJZ1YJ
* Hue
* jupyter
* zeppelin

## Coursera Spark Course Notes

* Watch out for non associative reduction operations
* Important Latency Numbers by Jeff Dean & Peter Norvig
* Parallel Reduction operations are reduction ops that can be parallelized, FoldLeft vs Fold
* if you're going to use groupbykey then reduce later, Use reduce by key instead
* if you're going to use certain partitioner, then persist it after it's done
* mapValues instead of map because it uses partitions
* partitioning can bring substantial performance gains, specially in face of shuffling
* use of partitioning before join is useful to avoid shuffling
* Methods that might cause shuffling:(cogroup, groupWith, join, leftOuterJoin, rightOuterJoin, groupByKey, combineByKey,
  reduceByKey, distinct, intersection, repartition,coalesce)
* Lineage Graphs, Directed Asyclic Graph
* Narrow Dependencies between partitions of parent and child RDD, cause no shuffling, while Wide Dependencies cause it.
* Narrow Deps: Map, mapValues, flatMap, Filter, ,mapPartitions, mapPartitionsWithIndex, union, join(partitioned right)
* Wide Deps: cogroup, groupWith, groupByKey, join(not partitioned), leftOuterJoin, rightOuterJoin, groupByKey,
  reduceByKey, combineByKey, distinct, intersection, coalesce
* Method (dependency) on RDD will return
    * Narrow Deps: oneToOneDependency, PruneDependency, RangeDependency.
    * Wide Deps: Shuffle Dependency
* Method (toDebugString) returns visualization of RDD's lineage and other info pertinent to scheduling.
* Lineages graphs are key to fault tolerance in spark
* How spark achieves fault tolerance without having to write to desk:
    * RDDs are immutable
    * usage of HOF on immutable RDDs
* Data Forms
    * Structured data: Database tables
    * SemiStructured data: Json, XML files, csv(maybe)
    * Unstructured data: Log files, Images
* DataFrames are untyped
* DataFrames are like RDDs but relational, and they're equal to tables
* DataFrames created by:
    * Existing RDD
        * By reflectively inferred Schema rdd.toDF(colName)
            * Note: colnames can be created automatically if RDD type is a case class
        * RDD[Rows] => create schema (structType matching structure of Rows) => apply schema to RDD of rows via
          createDataFrame method
    * Reading in a specific data source from file
        * sparkSession.read.json(file.json)
        * csv, parquet, JDBC
* df.createOrReplaceTempView("blabla")

```
sparkSession.sql("select * from blabla where age > 17")
```

* SQL statements: select, from, where, count, having, group by, order by, sort by, distinct, join, left|right|full outer
  join
* groupBy: RelationalGroupedDataset
* agg (min,max, sum, mean etc...)
* catalyst query optimiser
* tungsten data encoder and off heap memory
* Catalyst with DataSets can't optimize all ops like HOF, but it can when doing relational ops like Select
* Tungsten runs under the hood of Datasets and does store and organise data in highly optimized way.
* If your data can't be expressed by case classes/Products and standard SQL data types it may be difficult to ensure
  that a Tungsten encoder exists for your data.
