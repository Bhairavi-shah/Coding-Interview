Graph
=====

- It is a data structure
- Organizes items in an interconnected network
- Each item is a "node" (or vertex)
- Nodes are connected by "edges"

#### Strengths
- Representing links

#### Weakness
- Scaling challenges

Terminology
-----------

### Directed or undirected
    In directed graphs, edges point from the node at one end to the node at the other end.
    In undirected graphs, the edges simply connect the nodes at each end.

### Cyclic or acyclic
    A graph is cyclic if it has atleast one cycle (an unbroken series of nodes with no repeating nodes or edges that connects back to itself).
    A graph without cycles are acyclic.

### Weighted or unweighted
    If a graph is weighted, each edge has a "weight" (such as cost or distance etc).
    If no weights, then it is a unweighted graph.

### Legal coloring
    A graph coloring is when you assign colors to each node in a graph.
    A legal coloring means no adjacent nodes have the same color.

Representations
---------------

1. Edge list
        A list of all the edges in the graph:
        ```python
                graph = [[0, 1], [1, 2], [1, 3], [2, 3]]
        ```
2. Adjacency list
   A list where the index represents the node and the value at that index is a list of the node's neighbors:
   ```python
            graph = [
                        [1],
                        [0, 2, 3],
                        [1, 3],
                        [1, 2],
                    ]
        OR
            graph = {
                        0: [1],
                        1: [0, 2, 3],
                        2: [1, 3],
                        3: [1, 2],
                    }
   ```
3. Adjacency matrix
    A matrix of 0s and 1s indicating whether node x connects to node y (0 means no, 1 means yes).
    ```python
            graph = [
                        [0, 1, 0, 0],
                        [1, 0, 1, 1],
                        [0, 1, 0, 1],
                        [0, 1, 1, 0],
                    ]
    ```

Algorithms
----------

1.  BFS (Breadth-first search)
2.  DFS (Depth-first search)
3.  Dijkstra's Algorithm
4.  Topological Sort
5.  Minimum Spanning Tree

