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
* Traverse through all the 1-distance neighbords first
* Go through each vertex only once
* This is **NOT** a unique sequence
* The above implementation uses pre-order traversal
