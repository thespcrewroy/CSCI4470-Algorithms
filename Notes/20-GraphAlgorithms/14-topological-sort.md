# Topological Sort

## Slides: Example

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/topologicalexample.png" alt="Topological Sort Example" height="700" width="700" />
</p>

- Directed: edges have direction
- Acyclic: there should be no cycles because a right to left direction will violate the property of all edges going from left to right
- Topolgical sorted output arranges the vertices in a way that if you draw an edge, the edge only goes from left to right
- Utilized a depth-first search algorithm to produce the output