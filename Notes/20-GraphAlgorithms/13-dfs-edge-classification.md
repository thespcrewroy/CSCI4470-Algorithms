# DFS Edge Classification

## Notes: Tree Edge
**Tree Edge:** normal edge that takes you from parent to child.

## Notes: Back Edge
An edge hat takes you from child to parent.

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/blackedge.png" alt="Edge Types" height="500" width="300" />
</p>

## Notes: Cross Edge
An edge that connects vertex `u` with vertex `v` where vertex `u` and vertex `v` are in the same depth first tree that are not ancestor/descendent of each other. They can also be in different depth-first trees.

## Notes: Forward Edge
An edge that goes from parent `u` to descendent `v` that is not a tree edge.

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/forwardedge.png" alt="Edge Types" height="500" width="300" />
</p>

There is a forward edge from `a` to `c`.


## Notes: Example

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/dfsexample9.png" alt="DF Tree" height="600" width="600" />
</p>

### Depth-First Tree
<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/dftree2.png" alt="DF Tree" height="500" width="500" />
</p>

### DFS Edge Classification
<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/dfsedgeclassification.png" alt="Edge Types" height="550" width="550" />
</p>

## Homework: Example

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/hw4-2.png" alt="BFS Implementation Theory" height="500" width="700" />
</p>

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/hw4-2-2.png" alt="BFS Implementation Theory" height="500" width="700" />
</p>

## Notes: Coloring for Edge(u, v)

- If `v` is white, then edge(u, v) is a tree edge
- If `v` is gray, then edge(u, v) is a back edge
- If `v` is black, then edge(u, v) is a cross or forward edge
