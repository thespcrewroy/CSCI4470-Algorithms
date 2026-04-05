# Breadth First Search

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/breadth.png" alt="Breadth First Search Example" height="500" width="600" />
</p>

```
Time Complexity: O(V + E)
```

## Notes: Example

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/bfs.png" alt="Depth First Search Example 1" height="500" width="600" />
</p>

* Proceed along the width of the graph recursively
    * Visit all the children of the parent
    * Visit all the children of one of the children
    * Continue...
* Go to the children of the current vertex that have not been visited
* If there are no more valid neighbors to go to (dead-end), backtrack to the parent
* Visit the child that is the closest to the former path you took that led to the dead-end
* This is **NOT** a unique sequence
* The above implementation uses pre-order traversal
