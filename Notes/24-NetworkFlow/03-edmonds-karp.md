# Edmonds-Karp Algorithm

- Similar to the ford-fulkerson algorithm
- Not naive like ford-fulkerson
- Tells you how to select the augmenting path to do the least possible iterations
- Utilizes a BFS-based algorithm as its implementation to find the correct augmented path

```
Time Complexity: [E*(V/2 - 1)]*(V + E) = (VE)*(V + E) = (VE)*(E) = O(VE^2)
- Max Number of Times an Edge Can Become Critical: V/2 - 1
- Number of Edges: E
- Number of Augmenting Paths Found Using BFS: E*(V/2 - 1)
- BFS Runtime: O(V + E)
- E takes over in (V + E) because there are more edes than vertices in a graph
```