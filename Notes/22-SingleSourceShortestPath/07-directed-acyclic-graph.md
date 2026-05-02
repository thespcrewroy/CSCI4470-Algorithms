# DAG Algorithm

- Applies only to directed acyclic graphs, so by definition it cannot have a negative cycle
- Not all graphs in the real world fit the DAG definition (disadvantage)
- Negative edge wieghts are allowed (advantage)
- Utilizes topological sort or DFS-based algorithm as its implementation
- Fast (advantage)

```
Time Complexity: θ(V + E)
```

## Example

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/dag2.png" alt="DAG Example" height="500" width="500" 
/>

Go in alphabetical order <br>

|   | u.d | u.f |
|---|-----|-----|
| a | 1 | 10 |
| b | 2 | 9 |
| c | 3 | 6 |
| d | 4 | 5 |
| e | 7 | 8 |

Topological Sort Order: < a, b, e, c, d > <br>
Relax the edges in topological order.
