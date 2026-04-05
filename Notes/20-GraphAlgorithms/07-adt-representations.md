# Graph ADTs

## Slides: Example 1: Flight Connections
<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/weighted.png" alt="Weighted Graph Example" width="800" />
</p>

### 1-D Vertecies Array

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/vertexmatrix.png" alt="Vertices Matrix" height="600" width="300" />
</p>

### 2-D Adjacency Matrix for Edges

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/adjacent.png" alt="Vertices Matrix" width="800" />
</p>

```
Time Complexity: O(V^2)
Space Complexity: O(V + E) = O(V + V^2) = O(V^2)
```

- Preffered for dense graphs: E = O(V^2)
- Can quickly determine if there is an edge between two vertices
- Consumes unecessary significant memory for sparse large graphs


### Adjacency List

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/linked.png" alt="Adjacency List" width="800" />
</p>

```
Space Complexity
- Sparse: E = O(V)
- Dense: E = O(V^2)
```

**Preffered for sparse graphs where E = O(V).**

## Slides: Example 2

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/weighted2.png" alt="Graph 2" height="500" width="500" />
</p>

### Adjacency Matrix

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/adjacent2.png" alt="Adjacency Matrix 2" height="500" width="500" />
</p>

### Adjacency List

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/linked2.png" alt="Adjacency List 2"  width="800" />
</p>

## Slides: Example 3

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/weighted3.png" alt="Graph Example 3" height="500" width="500" />
</p>

### Adjacency Matrix

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/adjacent3.png" alt="Vertices Matrix 3" height="500" width="500" />
</p>

### Adjacency List

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/linked3.png" alt="Adjacency List 3" width="800" />
</p>

## Slides: Example 4: Directed Graph

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/weighted4.png" alt="Graph Example 4" height="500" width="300" />
</p>

### Adjacency Matrix

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/adjacent4.png" alt="Vertices Matrix 4" height="500" width="500" />
</p>
