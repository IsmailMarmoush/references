# Cassandra Notes

* The first value of the primary key is the partition key, second is clustering column
* What is clustering columns ?
    * is what's after primary key, and is used for ordering
* Should always use partition key in the query
* Queries should be in the order of clustering columns
* use `with clustering order` to change the order of clustering columns 