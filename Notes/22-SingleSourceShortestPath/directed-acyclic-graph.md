# DAG Algorithm

- Applies only to directed acyclic graphs
- By definition cannot have a negative cycle
- Not all graphs in the real world fit the DAG definition (disadvantage)
- Negative edge wieghts are allowed (advantage)
- Utilizes topological sort or DFS-based algorithm as its implementation
- Fast (advantage)

```
Time Complexity: θ(V + E)
```