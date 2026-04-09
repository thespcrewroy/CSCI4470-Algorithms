# Prim's Greedy Algorithm

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
3. Dequeue(a)
- Consider neighbors: `b` and `h`
  - b.key = &infin;
  - w(a, b) = 4
  - h.key = &infin;
  - w(a, h) = 8
- If the key value is bigger than weight, then update the key
  - b.key = 4
  - h.key = 8