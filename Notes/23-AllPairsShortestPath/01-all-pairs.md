# All Pairs Shortest Path Problem

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/allpairs.png" alt="All Pair Shortest Path Problem" width="600" 
/>

## Algorithmic Solutions
1. Run Bellman-Ford on all the vertices
- Time complexity: `O(VE)`
- Time complexity on APSP: `O(V^2E)`
- E&alpha;V^2 when the graph is dense
- true time complexity on APSP: `O(V^4)`
- Very costly (disadvantage)
2. Solution A (unnamed algorithm)
- Time complexity: `O(V^4)`
- Dynamic programming based solution
3. Floyd-Warshall
- Time Complexity: `O(V^3)`
- Dynamic programming based solution
4. Johnson's Algorithm
- Time complexity: `O(VElog(V))`
- Runs Djikstra's (`O(Elog(V)`) on all the vertices `V`
- Suggests a reweighing scheme that convertts negative weights to positive
- Best solution for sparse graphs