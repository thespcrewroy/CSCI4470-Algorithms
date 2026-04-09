# Topological Sort

## Slides: Definition

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/topologicalexample.png" alt="Topological Sort Example" height="700" width="700" />
</p>

- DAG (Directed Acyclic Graph)
    - Directed: edges have direction
    - Acyclic: there should be no cycles because a right to left direction will topological all edges left to right property
- Topolgical sorted output arranges the vertices in a way that if you draw an edge, the edge only goes from left to right
- Utilizes the depth-first search algorithm DFS(G) to produce the output

```
Time Complexity: O(V + E) ~ O(n)
- DFS: O(V + E)
- Linked List of Size v: O(V)
```

## Notes: Example

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/topoex.png" alt="Topological Sort Example" height="700" width="700" />
</p>

**Output orders are based on finish time!**

## Homework: Example

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/hw4-5-1.png" alt="Topological Sort HW" height="700" width="700" />
</p>

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/hw4-5-2.png" alt="Topological Sort HW" height="700" width="700" />
</p>