# Kruskal's Greedy Algorithm

## Slides: Definition

1. Sort the edges by increasing edge weight
2. Pick the first edge and add it to the solution
3. Keep adding edges if they DO NOT form a cycle
4. Stop when you reach all the vertices

- Greedy Algorithm: pick the lowest edge (safe edge) at any given moment
- Take the sum of all the edges you added to determine the cost
- Ideal for sparse graphs, where all edges can be checked easily
- Utilizes a disjoint set data structure (DSDS) in its implementation

```
Time Complexity: Elog(E) + Elog(V)
```

## Homework: Example
<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/hw4-6.png" alt="Kruskal's Algo Example"  />
</p>

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/hw4-6-1-1.png" alt="Kruskal's Algo Example"  />
</p>

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/hw4-6-1-2.png" alt="Kruskal's Algo Example"  />
</p>


