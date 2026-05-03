# Strongly Connected Component

- Condition: vertex `u` and vertex `v` are in the maximal set of vertices `S`
- There is a path from vertex `u` to vertex `v`
- There is a path from vertex `v` to vertex `u`

```
Time Complexity: O(V + E) ~ O(n)
- DFS(G): O(V + E)
- G^T Construction: O(V + E)
- DFS(G^T): O(V + E)
```

## Notes: Example
<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/sccexample.png" alt="Strongly Connected Component Example" height="700" width="700" />
</p>

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/sccdesc.png" alt="Strongly Connected Component Example Full" height="700" width="700" />
</p>

## Homework: Example
<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/hw4-5.png" alt="BFS Implementation Theory" height="700" width="700" />
</p>

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/hw4big.png" alt="BFS Implementation Theory" height=600" width="800" />
</p>

## Notes: Implementation
- Run DFS(G)
- Construct G<sup>T</sup> which is the transpose of the graph `G`
  - Flip the edges in `G`
  - Convert row to column and column to row of the DFS
- Run the DFS(G<sup>T</sup>) to produce connected component
  - Select the vertices based on the original DFS(G) order

## Notes: Implementation Example

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/sccimpl1.png" alt="BFS Implementation Theory" height=700" width="700" />
</p>

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/sccimpl2.png" alt="BFS Implementation Theory" height=400" width="700" />
</p>
