# Bellman Ford Algorithm

- Allows negative edge weights
- Reports an error if `G={V, E}` contains a negative weight cycle (advantage)
- Expensive in cost compared to the other two SSSP algorithms (disadvantage)
- **Relax all the `E` edges `(V - 1)` times** to converge to shortest distance (v.d = &infin; -> &delta;(s, v))

```
Time Complexity: O(V*E)
```