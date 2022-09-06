# Graphs

**Graph** is a non-linear data structure that can be looked at as a collection of vertices (or nodes) potentially connected by line segments named edges.

### Common Terminology:

1. `Vertex` - A vertex, also called a “node”, is a data object that can have zero or more adjacent vertices.
2. `Edge` - An edge is a connection between two nodes.
3. `Neighbor` - The neighbors of a node are its adjacent nodes, i.e., are connected via an edge.
4. `Degree` - The degree of a vertex is the number of edges connected to that vertex.


## Directed vs Undirected

An **Undirected Graph** is a graph where each edge is undirected or bi-directional. This means that the undirected graph does not move in any direction.

A **Directed Graph** also called a **Digraph** is a graph where every edge is directed.


a **Digraph** has direction. Each node is directed at another node with a specific requirement of what node should be referenced next.

## Complete vs Connected vs Disconnected

The three different types are completed, connected, and disconnected.

### Complete Graphs :

A complete graph is when all nodes are connected to all other nodes.

### Connected Graphs :

A connected graph is graph that has all of `vertices`/`nodes` have at least one edge.

![](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/assets/ConnectedGraph.PNG)

### Disconnected

A **disconnected** graph is a graph where some vertices may not have edges.

![](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/assets/DisconnectedGraph.PNG)

## Acyclic vs Cyclic

### Acyclic Graph

An acyclic graph is a directed graph without cycles.

A cycle is when a node can be traversed through and potentially end up back at itself.

![](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/assets/threeAcyclic.png)

A directed acyclic graph is also called a **DAG**. This can also be represented as what we know as a tree.

### Cyclic Graphs

A Cyclic graph is a graph that has cycles.

A cycle is defined as a path of a positive length that starts and ends at the same vertex.

![](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/assets/cyclic.PNG)

## Graph Representation

We represent graphs through:

1. Adjacency Matrix
2. Adjacency List

### **Adjacency Matrix**

An Adjacency matrix is represented through a 2-dimensional array. If there are n vertices, then we are looking at an n x n Boolean matrix

## Weighted Graphs

A weighted graph is a graph with numbers assigned to its edges. These numbers are called weights. This is what a weighted graph looks like:

![](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/assets/weightGraph.PNG)

In Adjacency Matrix :

![](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/assets/weightMatrix.PNG)

In Adjacency List :

![](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/assets/weightList.PNG)

## Breadth First

In a breadth first traversal, you are starting at a specific vertex/node. This node must be specified when calling the BreadthFirst() method. The breadth first traversal of a graph is like that of a tree, with the exception that graphs can have cycles. Traversing a graph that has cycles will result in an infinite loop….this is bad. To prevent such behavior, we need to have some way to keep track of whether a vertex has been “visited” before. Upon each visit, we’ll add the previously-unvisited vertex to a visited set, so we know not to visit it again as traversal continues.

## Depth First

In a depth first traversal, our approach is a bit different than the approach used for breadth first. While the breadth first traversal uses a Queue to visit all children at a given level, the depth first traversal uses a Stack to visit all children of a given subtree. (This differs from our approach to tree traversal, where we visit nodes via recursive calls. Recursive calls use a call stack internally.)

# Real World Uses of Graphs

1. GPS and Mapping
2. Driving Directions
3. Social Networks
4. Airline Traffic
5. Netflix uses graphs for suggestions of products


# References

- ## [Graphs](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/graphs.html)
