# Breadth First Search

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/breadth.png" alt="Breadth First Search Example" height="500" width="600" />
</p>

```
Time Complexity: O(V + E)
- O(V): queue operations
- O(E): total time for the loop
```
<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/timeanalysisbfs.png" alt="Breadth First Search Analysis" height="500" width="500" />
</p>

## Notes: Example

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/bfs.png" alt="Breadth First Search Example 1" height="500" width="600" />
</p>

* Proceed along the width of the graph recursively
    * Visit all the children of the parent
    * Visit all the children of one of the children
    * Continue...
* Traverse through all the 1-distance neighbords first
* Go through each vertex only once
* This is **NOT** a unique sequence
* The above implementation uses pre-order traversal


## Slides: Example

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/bfs2.png" alt="Breadth First Search Example 12" height="500" width="600" />
</p>


## Notes: Example

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/bfs3.png" alt="Breadth First Search Example 3" height="500" width="600" />
</p>

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/bfs4.png" alt="Breadth First Search Example 3" height="200" width="500" />
</p>

## Slides: Queue-Based Imlementation

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/queue1.png" alt="Queue Example" height="800" width="800" />
</p>

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/queue2.png" alt="Queue Example" height="800" width="800" />
</p>

## Notes: Implementation

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/bfsimpl.png" alt="BFS Implementation Code" height="500" width="500" />
</p>


1. Coloring the vertices: white, gray, or black.
- White: undiscovered or unvisited
- Gray: visited but sitting in queue
- Black: removed from queue because we finished processing all the neighbors/children
1. Track the distance of the current vertex (u) from the source vertex (s)
- u.d: distance of u from source s
- u.&pi;: parent of u
1. Initialization
- u.color = white (all the vertex except source vertex)
- u.d = &infin;
- u.&pi; = NIL
- s.color = gray
- s.d = 0
- s.&pi; = NIL
- Queue Q = `<s>`
1. Dequeue `s`
- b.color = gray
- b.d = s.d + 1 = 0 + 1 = 1
- b.&pi; = s
- c.color = gray
- c.d = s.d + 1 = 0 + 1 = 1
- c.&pi; = s
- s.color = black
- Queue Q = `<b, c>` <br>
...
1. Final
- f.color = black
- f.d = 4
- f.&pi; = e
- Queue Q = `<>`

## Homework: Implementation

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/hw4-1-1.png" alt="BFS Implementation Theory" height="500" width="700" />
</p>

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/hw4-1-2.png" alt="BFS Implementation Theory" height="500" width="700" />
</p>

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/hw4-1-3.png" alt="BFS Implementation Theory" height="500" width="700" />
</p>


## Proof: &delta;(s, v)

Proof: at the termination of the BFS, u.d converges to &delta;(s, v)

Example of Proof: v.d = &alpha;...  v.d = 5...  v.d = 3;... Done.

- &delta;(s, v): shortest distance from vertex `v` from source `s`
- u.d: distance of vertex `u` from source `s` (number of edges between `v` and `s`)
- The graph must be undirected and **unweighted** (weighted proof needs **Djikstra's Algorithm**

### Lemma 20.1
- Let `G=(V, E)` be directed or undirected graph
- Let S &isin; V be an arbitrary vertex
- Then, for any edge `(u, v)` &isin; E, &delta;(s, v) &le; &delta;(s,u) + 1

### Case 1: &delta;(s, v) = &delta;(s, u) + 1

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/case1.png" alt="BFS Proof Lemma Case 1" height="200" width="200" />
</p>

There is a shortest path from `s` to `v` that goes through `u`: &delta;(s, v) = &delta;(s, u) + 1.

### Case 2: &delta;(s, v) < &delta;(s, u) + 1

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/case2.png" alt="BFS Proof Lemma Case 2" height="200" width="200" />
</p>

The shortest path from `s` to `v` does not go through `u`.

### Case 3 (Rare): &delta;(s, v) = &delta;(s, u) = &alpha;

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/case3.png" alt="BFS Proof Lemma Case 3" height="200" width="200" />
</p>

Vertex `u` is unreachable, so vertex `v` is also unreachable.

### Lemma 20.2

- BFS satisfies v.d &ge; &delta;(s, v) (eq 1) at all times
- Base case is the source vertex `s`
    - v.d = 0 = &delta;(s, s)
    - s.d = &delta;(s, s)
- Assume that (eq 1) works of vertex `u` and we are looking at edge `(u, v)`
  - v.d = u.d + 1 (eq 2)
  - v.d &ge; &delta;(s, u) + 1 (eq 3)
  - &delta;(s, v) &le; &delta;(s, u) + 1 (lemma 20.1)
  - v.d &ge; &delta;(s, v)
  
### Lemma 20.3
<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/lemma3.png" alt="BFS Proof Lemma 20.3" height="200" width="200" />
</p>

**Q = < S >**

**Q = < a, b, d >**
- a.d = 1
- b.d = 1
- d.d = 1

**Q = < d, c, e >**
- d.d = 1 (v<sub>1</sub>)
- c.d = 2
- e.d = 2 (v<sub>r</sub>)

**e.d &le; d.d + 1**

Q = < v<sub>1</sub>, v<sub>2</sub>, ..., v<sub>r</sub> > <br>
v<sub>1</sub>.d &le; v<sub>2</sub>.d &le; ... v<sub>r</sub>.d <br>
v<sub>r</sub>.d &le; v<sub>1</sub>.d + 1
