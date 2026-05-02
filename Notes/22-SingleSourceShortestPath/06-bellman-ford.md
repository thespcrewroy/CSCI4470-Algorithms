# Bellman Ford Algorithm

- Allows negative edge weights
- Reports an error if `G={V, E}` contains a negative weight cycle (advantage)
- Expensive in cost compared to the other two SSSP algorithms (disadvantage)
- **Relax all the `E` edges `(V - 1)` times** to converge to shortest distance (v.d = &infin; -> &delta;(s, v))

```
Time Complexity: O(V*E)
```

## Example 

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/nig2.png" alt="Bellman Ford Example" height="500" width="500" 
/>

- You can pick and choose to start from any vertex
- However, it is best practice to pick the source vertex `a`
- We may not run it the full `(V - 1)` iterations
- We will run in alphabetical order, starting from source `a`

**StartVertex = F**