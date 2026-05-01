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

## Notes: Example

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/dfs3.png" alt="Depth First Search Example 3" height="500" width="600" />
</p>

## Slides: Stack-Based Imlementation

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/stack1.png" alt="Stack Example" height="500" width="600" />
</p>

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/stack2.png" alt="Stack Example" height="500" width="600" />
</p>

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/stack3.png" alt="Stack Example" height="500" width="600" />
</p>

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/stack4.png" alt="Stack Example" height="500" width="600" />
</p>

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/stack5.png" alt="Stack Example" height="500" width="600" />
</p>

## Notes: Implementation
<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/dfsexample.png" alt="DFS Example" height="300" width=300" />
</p>

- time: global variable that starts with value of 0 and will get updated
- u.d: discover time of vertex `u`. Assign when vertex becomes gray.
- u.f: finish time of vertex `u`. Assign when vertex becomes black.

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/dfsimpltable.png" alt="DFS Implementation Example" height="500" width="500" />
</p>

## Notes: Implementation Example

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/dfstraversal.png" alt="DFS Traversal" height="700" width=700" />
</p>

## Homework: Implementation Example

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/hw4-2-1.png" alt="BFS Implementation Theory" height="1000" width="1000" />
</p>

## Notes: Parenthesis Theorem

- [u.d, u.f]: discover time and finish time of vertex `u`
- [v.d, v.f]: discover time and finish time of vertex `v`
- White: undiscovered or unvisited
- Gray: visited but sitting in stack
- Black: removed from stack because we finished processing all the neighbors/children

During DFS Traversal
1. The interval [u.d, u.f] is nested inside the interval [v.d, v.f] or vice versa. Then, `u` and `v` are ancestors/descendents of each other.
2. The intervals [u.d, u.f] and [v.d, v.f] are completely disjoint. Then, `u` and `v` are not ancestors/descendents of each other. Happens for disconnected graphs.


## Homework: Parenthesis Theorem

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/hw4-3-1.png" alt="Parenthesis Theorem HW" height="700" width="700" />
</p>

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/hw4-3-2.png" alt="Parenthesis Theorem HW" height="700" width="700" />
</p>

## Notes: White Path Theorem

- During DFS, you are at vertex `a`
- There is a path from vertex `a` to vertex `d`
- If intermediate vertices (b & c) are white, then `d` is a descendent of `a`

### `d` is a Descendant of `a`
<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/whitepath1.png" alt="White Path Theorem" height="400" width=200" />
</p>

### `d` is Not a Descendant of `a`

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/whitepath2.png" alt="White Path Theorem" height="400" width=200" />
</p>

`d` is the descendent of `e`, and not `a`