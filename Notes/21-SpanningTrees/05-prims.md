# Prim's Greedy Algorithm

## Notes: Definition
- Greedy Algorithm: pick the cheapest edge that connects a vertex inside the tree to a vertex outside the tree.
- Take the sum of all the edges you added to determine the cost
- Optimal for dense graphs where E &#8494; V<sup>2</sup>
- Utilizes a minimum prioirity queue in its implementation

```
Time Complexity: O(Elog(V)) 
```

## Notes: Prim's Time Complexity Analysis

```
(V + E)log(V)
V + E ~ E (for dense graphs)
O(Elog(V))
```

**Complete Graph Time Complexity: O(Elog(V))**

## Notes: Example

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/primwalk2.png" alt="Prim Walkthrough" width="500"  />
</p>

**Initialization**
- b.key = &alpha;
- b.&pi; = NIL
- h.key = &alpha;
- h.&pi; = NIL

**a.key = 0**
<p align="left">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/minqueue1.png" alt="Min Prioirty Queue 1" height="150" width="150"  />
</p>


## Homework: Example

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/hw4-6.png" alt="Prim's Algo Example"  />
</p>

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/hw4-6-2.png" alt="Prim's Algo Example"  />
</p>

## Notes: Implementation Example

- Create a minimum priority queue with all the vertices
- You are using the key parameter to create the heap

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/primgraph.png" alt="Prim Use Case"  />
</p>

1. Choose Start_Vertex
- a.key = 0
2. Initialization (true for all vertices except one)
- b.key = &infin;
- b.&pi; = NIL <br>
...
- e.key = &infin;
- e.&pi; = NIL

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/heap1.png" alt="Prim Use Case"  />
</p>

3. Dequeue(a)
- Consider neighbors: `b` and `h`
  - b.key = &infin;
  - w(a, b) = 4
  - h.key = &infin;
  - w(a, h) = 8
- If the key value is bigger than weight, then update the key
  - b.key = 4
  - h.key = 8

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/heap2.png" height="400" width="400" alt="Prim Use Case"  />
</p>

4. Dequeue(b)
- Consider neighbors: `h` and `c`
  - h.key = 8
  - w(b, h) = 11
  - c.key = 2
  - w(b, c) = 8
- If the key value is bigger than weight, then update the key
  - h.key = 8
  - c.key = 8

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/heap3.png" alt="Prim Use Case"  />
</p>

5. Dequeue(c)
- Consider neighbors: `i`, `f`, and `d`
  - i.key = &infin; 
  - w(c, i) = 2
  - f.key = &infin;
  - w(c, f) = 4
  - d.key = &infin;
  - w(c, d) = 7

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/heap4.png" alt="Prim Use Case"  />
</p>