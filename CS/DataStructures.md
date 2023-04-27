# Data Structures

## References

* [Rob teaches CS310, Data Structures in Java at San Diego State University](https://www.youtube.com/playlist?list=PLpPXw4zFa0uKKhaSz87IowJnOTzh9tiBk)

## [Arrays](https://en.wikipedia.org/wiki/Array_data_structure)

* [Associative array](https://en.wikipedia.org/wiki/Associative_array)
    * Hash table
    * Self-balancing binary search tree
    * unbalanced binary search tree
    * Sequential container of key-value pairs (e.g. association list)
* [Bit array](https://en.wikipedia.org/wiki/Bit_array)
    * Bitset in Java
* [Circular buffer](https://en.wikipedia.org/wiki/Circular_buffer)
    * buffer start in memory
    * buffer end in memory, or buffer capacity
    * start of valid data (index or pointer)
    * end of valid data (index or pointer), or amount of data currently in the buffer (integer)
    * increment_address_one = (address + 1) % Length
    * decrement_address_one = (address + Length - 1) % Length
* [Dynamic array](https://en.wikipedia.org/wiki/Dynamic_array)
    * Java ArrayList
* [Lookup table](https://en.wikipedia.org/wiki/Lookup_table)
    * can be used for memoization
* [Parallel array](https://en.wikipedia.org/wiki/Parallel_array)
    * int ages[]   = {0, 17, 2, 52, 25};
    * char *names[] = {"None",     "Mike",    "Billy",    "Tom",      "Stan"};
    * int parent[] = {0 /*None*/, 3 /*Tom*/, 1 /*Mike*/, 0 /*None*/, 3 /*Tom*/};
* [Sorted array](https://en.wikipedia.org/wiki/Sorted_array)
    * Normal sorted array
* [Sparse matrix](https://en.wikipedia.org/wiki/Sparse_matrix)
    * Matrices with very high number of zeros
* [Iliffe vector](https://en.wikipedia.org/wiki/Iliffe_vector)
    * Multidimentional array
* [Variable-length array](https://en.wikipedia.org/wiki/Variable-length_array)
    * allocating an array with a small defined size,
    * "USING VLA'S IS ACTIVELY STUPID! It generates much more code, and much slower code (and more fragile code), than
      just using a fixed key size would have done." Linus Torvalds
    * With the Linux 4.20 kernel, Linux kernel is effectively VLA-free."

## Lists

* [Array list](https://en.wikipedia.org/wiki/Array_list)
    * dynamic array, growable array, resizable array, dynamic table, mutable array, or array list
* [Linked list](https://en.wikipedia.org/wiki/Linked_list)
* [Doubly linked list](https://en.wikipedia.org/wiki/Doubly_linked_list)
    * Has a prev and next, the start and end have null prev and next respectively
* [Self-organizing list](https://en.wikipedia.org/wiki/Self-organizing_list)
    * used in LFU (Least frequently used) algorithm for caching
* [Skip list](https://en.wikipedia.org/wiki/Skip_list)
    * insert (log n) , searching (log n)

## Stack

* [Stack aka LIFO](https://en.wikipedia.org/wiki/Stack_(abstract_data_type))

## Queues

* [Queue](https://en.wikipedia.org/wiki/Queue_(abstract_data_type))
    * [Double-ended queue](https://en.wikipedia.org/wiki/Double-ended_queue)
* [Priority queue](https://en.wikipedia.org/wiki/Priority_queue)
    * [Double-ended priority queue](https://en.wikipedia.org/wiki/Double-ended_priority_queue)

## Hash Tables

* http://stackoverflow.com/questions/730620/how-does-a-hash-table-work

### Hash Questions

* Find symmetric pairs in an array
* Trace complete path of a journey
* Find if an array is a subset of another array
* Check if given arrays are disjoint

### Hash-based structures

* [Distributed hash table](https://en.wikipedia.org/wiki/Distributed_hash_table)
    * is a distributed system that provides a lookup service similar to a hash table: key-value pairs are stored in a
      DHT, and any participating node can efficiently retrieve the value associated with a given key.
* [Hash list](https://en.wikipedia.org/wiki/Hash_list)
    * A hash list is typically a list of hashes of the data blocks in a file or set of files.
* [Hash table](https://en.wikipedia.org/wiki/Hash_table)
    * a hash table (hash map) is a data structure that implements an associative array abstract data type, a structure
      that can map keys to values.
* [Hash tree](https://en.wikipedia.org/wiki/Hash_tree_(disambiguation))
    * In computer science, a hash tree (or hash trie) is a persistent data structure that can be used to implement sets
      and maps, intended to replace hash tables in purely functional programming.
    * In its basic form, a hash tree stores the hashes of its keys, regarded as strings of bits, in a trie, with the
      actual keys and (optional) values stored at the trie's "final" nodes.
    * [Hash array mapped trie](https://en.wikipedia.org/wiki/Hash_array_mapped_trie)
      and [concurrent hash-trie or Ctrie](https://en.wikipedia.org/wiki/Ctrie) are refined versions of this data
      structure, using particular type of trie implementations.

## Set

* [Set](https://en.wikipedia.org/wiki/Set_(abstract_data_type))
    * Java offers the Set interface to support sets (with the HashSet class implementing it using a hash table), and the
      SortedSet sub-interface to support sorted sets (with the TreeSet class implementing it using a binary search tree)
      .

## Graphs

### Introduction

* Graphs can be either directed or undirected
* The graph can also have cycles (or not). An "acyclic graph" is one without cycles.

### Graphs Questions

* Implement Breadth and Depth First Search
* Check if a graph is a tree or not
* Count the number of edges in a graph
* Find the shortest path between two vertices

### Types

* [Graph](https://en.wikipedia.org/wiki/Graph_(data_structure))
* [graph](https://en.wikipedia.org/wiki/Graph_(discrete_mathematics))
* [Adjacency list](https://en.wikipedia.org/wiki/Adjacency_list)
    * Vertices are stored as records or objects, and every vertex stores a list of adjacent vertices.
    * This data structure allows the storage of additional data on the vertices.
    * Additional data can be stored if edges are also stored as objects, in which case each vertex stores its incident
      edges and each edge stores its incident vertices.
* [Adjacency matrix](https://en.wikipedia.org/wiki/Adjacency_matrix)
    * A two-dimensional matrix, in which the rows represent source vertices and columns represent destination vertices.
    * Data on edges and vertices must be stored externally. Only the cost for one edge can be stored between each pair
      of vertices.
* [Directed graph](https://en.wikipedia.org/wiki/Directed_graph)
* [Directed acyclic graph](https://en.wikipedia.org/wiki/Directed_acyclic_graph)
* [Multigraph](https://en.wikipedia.org/wiki/Multigraph)

## Trees

### Introduction

* A Tree is a type of graph
* a tree is a connected graph without cycles.
* Complete vs Full Tree
    * Full tree: Every non leaf has two children
    * Complete tree: last row is filled from left to right, and might not be all filled with children,
* Balanced vs unbalanced Trees
    * "not terribly imbalanced: It's balanced enough to ensure O( log n) times for insert and find, but it's not
      necessarily as balanced as it could be.
    * Two common types of balanced trees are red-black trees (pg 639) and AVL trees (pg 637).
* n nodes in tree -> (log2 (n+1)) -1
* Removing elements
    * swap with the predecessor or successor
    * Predecessor is the biggest smaller number under the root, left then all right
    * Successor is the smallest bigger number than the root, right then all left

### Important Trees

* Binary Tree
* Binary Search Tree
* Balanced Tree
* AVL Tree
    * Difference in height between left and right must be <=1
    * right leg -> left rotation
    * left leg -> right rotation
    * right left leg ->  right left rotation
    * left right leg -> left right rotation
* Red Black Tree
    * Rules
        * Every node is red or black
        * Root is always black
        * new insertions are always red
        * every path from root to a leaf has the same number of black nodes
        * no path can have two consecutive red nodes
        * a path can have two consecutive black nodes
        * nulls are black
        * black aunt : rotate
        * red aunt : flip color
* N-ary Tree
* 2–3 Tree

### Tree Questions:

* Find the height of a binary tree
* Find kth maximum value in a binary search tree
* Find nodes at “k” distance from the root
* Find ancestors of a given node in a binary tree

### Trie (Prefix tree) Questions

* Count total number of words in Trie
* Print all words stored in Trie
* Sort elements of an array using Trie
* Form words from a dictionary using Trie
* Build a T9 dictionary

### Types

* [Tree](https://en.wikipedia.org/wiki/Tree_(data_structure))
* [Search trees](https://en.wikipedia.org/wiki/Search_tree)
* [Trie or Prefix tree](https://en.wikipedia.org/wiki/Trie) (Seen)
    * [Hash tree](https://en.wikipedia.org/wiki/Hash_tree_(persistent_data_structure)) (Seen)
    * A trie is a variant of an n-ary tree in which characters are stored at each node. Each path down the tree may
      represent a word
* [Radix tree](https://en.wikipedia.org/wiki/Radix_tree)
    * In computer science, a radix tree (also radix trie or compact prefix tree) is a data structure that represents a
      space-optimized trie (prefix tree) in which each node that is the only child is merged with its parent.
    * The result is that the number of children of every internal node is at most the radix r of the radix tree, where r
      is a positive integer and a power x of 2, having x ≥ 1
* [Merkle tree](https://en.wikipedia.org/wiki/Merkle_tree)

## Binary trees

* [Binary tree](https://en.wikipedia.org/wiki/Binary_tree)
    * Binary Tree vs. Binary Search Tree
        * A binary search tree is a binary tree in which every node fits a specific ordering property;
          " all left descendants   <= n < all right descendants ". This must be true for each node n
    * Complete Binary Tree
        * Every level is fully filled except perhaps the last level, left to right (if one last level node is filled
          with right only, then it's not a complete binary tree)
    * Full Binary tree
        * A full binary tree is a binary tree in which every node has either zero or two children. That is, no nodes
          have only one child.
    * Perfect Binary Trees
        * A perfect binary tree is one that is both full and complete. All leaf nodes will be at the same level, and
          this level has the maximum number of nodes.
    * Binary tree Traversal
        * In order traversal: traverse left, visit node, traverse right
        * Pre order traversal( same as DFS): visit node, traverse left, traverse right
        * post order traversal: traverse left, traverse right, visit node
    * Min or Max heap
        * A min-heap is a complete binary tree (that is, totally filled other than the rightmost elements on the last
          level)
          where each node is smaller than its children. The root, therefore, is the minimum element in the tree.
        * A priority Queue ADT uses heap as its implementation
* [Binary search tree](https://en.wikipedia.org/wiki/Binary_search_tree)
    * [AVL tree](https://en.wikipedia.org/wiki/AVL_tree)
        * AVL is a self-balancing binary search tree
* [Red–black tree](https://en.wikipedia.org/wiki/Red%E2%80%93black_tree)
* [Self-balancing binary search tree](https://en.wikipedia.org/wiki/Self-balancing_binary_search_tree)

## B-trees

B-tree is used when the data is being stored in the disk it reduces the access time by reducing the height of the tree
and increasing the branches in the node.
https://techdifferences.com/difference-between-b-tree-and-binary-tree.html

* [B-tree](https://en.wikipedia.org/wiki/B-tree)
* [2-3 tree](https://en.wikipedia.org/wiki/2-3_tree)
* [2-3-4 tree](https://en.wikipedia.org/wiki/2-3-4_tree)

## Multiway trees

* [Ternary tree](https://en.wikipedia.org/wiki/Ternary_tree)
* [K-ary tree](https://en.wikipedia.org/wiki/K-ary_tree)

## Heap

### Introduction

* [Heap](https://en.wikipedia.org/wiki/Heap_(data_structure))
* A heap is a specialized tree-based data structure which is essentially an almost complete tree that satisfies the heap
  property:
    * In a **max heap**, for any given node C, if P is a parent node of C, then the key (the value) of P is greater than
      or equal to the key of C.
    * In a **min heap**, the key of P is less than or equal to the key of C.

### Types

* [Binary heap](https://en.wikipedia.org/wiki/Binary_heap)
    * [B-heap](https://en.wikipedia.org/wiki/B-heap)
* [Binomial heap](https://en.wikipedia.org/wiki/Binomial_heap)
    * [Weak heap](https://en.wikipedia.org/wiki/Weak_heap)
* [Fibonacci heap](https://en.wikipedia.org/wiki/Fibonacci_heap)
* [Pairing heap](https://en.wikipedia.org/wiki/Pairing_heap)

# Data Structures in Java

## Binary Operations

* https://www.theserverside.com/tutorial/Java-7-and-Binary-Notation
* https://stackoverflow.com/questions/5263187/print-an-integer-in-binary-format-in-java
* https://www.youtube.com/watch?v=4Qls3vRA_F4
* https://www.youtube.com/watch?v=lUzQtTLCglk

## Enumeration

The Enumeration interface defines the methods by which you can enumerate (obtain one at a time) the elements in a
collection of objects. This legacy interface has been superseded by Iterator. Although not deprecated, Enumeration is
considered obsolete for new code.
[Java enumeration](https://www.tutorialspoint.com/java/java_enumeration_interface.htm)

## BitSet

Bits with operations on them

## dictionary

A key - value store abstract class.

### Hashtable

### Properties

### Vector

### Stack

