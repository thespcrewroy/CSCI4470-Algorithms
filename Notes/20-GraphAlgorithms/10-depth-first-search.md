# Depth First Search

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/depth.png" alt="Depth First Search Example" height="500" width="600" />
</p>

```
Time Complexity: O(V + E)
- Stack Time: O(V)
- Neighbors Visiting Time: O(E)
```

## Notes: Example

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/dfs1.png" alt="Depth First Search Example 1" height="500" width="600" />
</p>

* From any given vertex, you can go to any neighbor of that vertex
* If you choose to go left, keep going left, and vice versa for right
* Go to the children of the current vertex that have not been visited
* If there are no more valid neighbors to go to (dead-end), backtrack to the parent
* Visit the child that is the closest to the former path you took that led to the dead-end
* This is **NOT** a unique sequence
* The above implementation uses pre-order traversal

## Slides: Example

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/dfs2.png" alt="Depth First Search Example 2" height="500" width="600" />
</p>

## Stack-Based Imlementation

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/stack1.png" alt="Breadth First Search Example" height="500" width="600" />
</p>

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/stack2.png" alt="Breadth First Search Example" height="500" width="600" />
</p>

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/stack3.png" alt="Breadth First Search Example" height="500" width="600" />
</p>

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/stack4.png" alt="Breadth First Search Example" height="500" width="600" />
</p>

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/stack5.png" alt="Breadth First Search Example" height="500" width="600" />
</p>

