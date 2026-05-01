# Kruskal's Greedy Algorithm

## Slides: Definition

1. Sort the edges by increasing edge weight
2. Pick the first edge and add it to the solution
3. Keep adding edges if they DO NOT form a cycle
4. Stop when you reach all the vertices

- Greedy Algorithm: pick the lowest edge (safe edge) at any given moment
- Take the sum of all the edges you added to determine the cost
- Optimal for sparse graphs, where E ~ V
- Utilizes a disjoint set data structure (DSDS) in its implementation

```
Time Complexity: Elog(E) + Elog(V) = Elog(V) + Elog(V) = (2E)log(V) = O(Elog(V))
```

## Notes: Kruskal's DSDS Implementation Cost Analysis

```
Time Complexity: O((V + 3E) α (V))
- DSDS: O(m α (n))
- Make_Set: O(V) for all vertices
- Find_SET: O(2E) for all edges
- Union: O(E) for all the edges
```

```
DSDS Time Complexity: O(m α (n)) = O(Elog(V))
- There are more edges than vertices so `V + 3E ~ O(E)`
- &alpha;(n): log() in the worst case
```

- m: total number of MakeSet, FindSet, and Union operations: V + 3E
- n: total number of MakeSet operations: V
- &alpha;(n): usually constant, but is log() in the worst case

## Notes: Kruskal's Time Complexity Analysis


```
Average Cost: Elog(E) + Elog(V)
- Sorting Edges: O(Elog(E))
- Using DSDS to Detect Cycles: O(Elog(V))
```

```
Elog(V) + Elog(E)
E α V^2
Elog(V) + Elog(V^2)
Elog(V) + 2Elog(V)
3Elog(V)
O(Elog(V))
```

**Complete Graph Time Complexity: O(Elog(V))**

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


