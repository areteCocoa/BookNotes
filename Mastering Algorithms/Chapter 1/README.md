# Chapter 1: Introduction
Pages 3-10 


- Algorithm: A well-defined procuedure for solving a problem
- Data Structure: Conceptual organizations of information
  - Go hand in hand with algorithms because algorithms use them for efficiency

## An Introduction to Data Structures
- Most common are linked lists, stacks, queues, sets, hash tables, trees, heaps, priority queues
and graphs
- Three reasons to use data structures: efficiency, abstraction and reusability

### Efficiency
- Can make some algorithms more efficient
- Searching a hash table is much faster than searching (traversing) a linked list

### Abstraction
- Allow for more abstraction in algorithm implementation
  - Makes it easier to talk about
- Implement stack before so that the implementation of the algorithm is less concerned with
the implementation of the stack and more with the implementation of the algorithm

### Reusability
- Reusable because they are modular and context free
  - Modular because of the prescribed interface through which the data of the data structure is restricted
    - Only access data through the interface definition
  - Context-free because they can be used with a variety of data types and in any situation
    - Don't require specific situation or context
    - Use void pointers in C to store data of any type

- Operations: actions performed on the data structure
- Abstract Datatype: A data structure with basic operations
- Public Interface: The operations of an abstract datatype

## Introduction to Algorithms
- Well defined procedure for solving a problem
- Like data structures, three reasons for using algorithms: efficiency, abstraction and reusability

### Efficiency
- Certain problems occur often in computing, many different and more efficient ways of solving these problems
  - Sorting a very well explored area of algorithms

### Abstraction
- Seemingly complicated problems can be distilled into smaller ones for which well-known algorithms exist
- Trying to find the shortest way to route a packet between two gateways on the internet
  - Realize just a variation of the 'single-pair shortest-paths problem' (Ch 16) it can be approached as such

### Reusability
- Since many algorithms solve generalizations of more complicated problems, can be used in many different contexts
  - Efficient means of solving small problems let us efficiently solve large problems

## General Approaches in Algorithms Design
- Algorithms can be sorted by their approach to solving the problem
  - Some defy this definition, some combine multiple approaches

### Randomized algorithms
- Rely on statistical properties of random numbers
- Example: Quicksort (Chapter 12)
  - Find what we think the median is
  - Partition group of data into smaller than the median and larger than the median
  - Repeat until one item per group, then they're sorted
  - Relies on partitions being of equal size
    - Instead of calculating median, randomly select some items of group and estimate median

### Divide-and-conquer algorithms
- Three steps: Divide, Conquer and Combine
- Divide into smaller and more manageable pieces
- Process each small division with some operation
- Combine the processed divisions
- Example: Mergesort (Chapter 12)
  - Divide data in half until all groups of one
  - Begin merging groups of one into groups of two in the sorted order
  - Continue merging until one large, sorted group

### Dynamic-programming solutions
- Similar to divide and conquer in that solve the problem by breaking large problem into small
sub-problem to be combined later
- In divide-and-conquer, subproblems independent and solved with recursion and combine results
with results of other subproblems.
- In dynamic-programming solutions, subproblems not independent and many share subproblems with
each other
- Important because can solve shared problems once where divide-and-conquer will solve multiple times
- No algorithms in this book use this type

### Greedy algorithsm
- Make decisions that look best in the moment; decisions that are locally optimal in hope that they
will be globally optimal
- Not always the most optimal, but are sometimes
- Huffman coding, an algorithm for data compression (Ch 14)
  - Most signifigant part is building a 'Huffman Tree'
    - Proceed from leaf nodes upward
  - Put each symbol to compress and their frequencies in the root node of their own binary trees (Ch 9)
  - Merge two trees with smallest frequencies and store sum of frequencies in the new tree's root
  - At end, final tree root contains total number of symbols in the data and leaf nodes contain original
  symbols and their frequencies
  - Greedy because it continuously searches for two trees that are the best search at the time of the search

### Approximation algorithms
- Do not compute optimal results but instead results that are "good enough"
- Use for problems that are computationally expensive but too signifigant to give up on
- 'Traveling-Salesman Problem' (Ch 16)
  - Salesman that needs to visit a number of cities
  - Determine the route that uses every city exactly once and is shortest
  - Find closest point to current point until they're all filled
- Heuristic algorithm: less than optimal strategy that we accept because optimal strategty is not feasible

## A Bit About Software Engineering
- Algorithms and Data Structures are important to good software engineering
- Some concepts here can be merged into software engineering

### Modularity
- Development of black boxes, implementations that have no awareness of level above them
- Fundamental ideas of data hiding and encapsulation
- Well enforced by object-oriented languages, can still be applied to non-OO languages

### Readability
- Can make programs more readable using aptly named identifiers and self-documenting code and writing
good comments

### Simplicity
- 'complex' != 'intelligent'
- Algorithms in this book show the power of simplicity
- Although long research goes into developing algorithms, final form of them is quite simple

### Consistency
- Establish conventions and stick with them
- Fosters readability and simplicity

## How to Use This Book
- Used to be textbook or reference