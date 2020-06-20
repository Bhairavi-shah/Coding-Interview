Depth-First Search (DFS) and Depth-First Traversal
====================

- method for exploring a tree or graph. 
- you go as deep as possible down one path before backing up and trying a different one.

Steps:
1. Starting with the root.
2. We'd go down the first path we find until we hit a dead end
3. Then we'd do the same thing again - go down a path until we hit a dead end
4. And again until we reach the end

Advantages
----------
- generally requires less memory than breadth-first
- can be easily implemented with recursion

Disadvantages
-------------
- doesn't necessarily find the shortest path to a node, while breadth-first search does