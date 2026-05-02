# Relaxation


## Notes: Initialization

v.d = &infin; (remaining vertices) <br>
v.&pi; = NIL (remaining vertices) <br>
s.d = 0 (source vertex) <br>

## Notes: Example

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/relax1.png" alt="Relax Step 1" width="600" 
/>

**Initialization**
- u.d = 3 <br>
- v.d = 12 <br>
- w(u,v) = 5 <br>

**Relax Edge (u, v)**
- Currently, the shortest distance to `v` is 12, but it comes from another path
- Thus, we should check if the shortest path that comes from the vertex `u` or not

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/relax2.png" alt="Relax Step 2" height="200" width="200" 
/>

1. v.d = 12
2. u.d + w(u, v) = 3 + 5 = 8
3. v.d > u.d + w(u, v)? Yes
4. Update: v.d = u.d + w(u, v) = 8