# Properties of Shortest Path and Relaxation


## Triangle Inequality Property

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/triangle.png" alt="Triangle Inequality Property" height="200" width="200" 
/>

- This property is also in BFS
- Let source be `s`, with edge `(u, v)` &isin; E.
- The shortest-path distance is written as &delta;(x, y).
- Triangle inequality in shortest paths: &delta;(s, v) &le; &delta;(s, u) + w(u, v)
- Why this is true (from the sketch):
	- Consider path `P1`: a shortest path from `s` to `v` with length &delta;(s, v).
	- Consider path `P2`: go from `s` to `u` using a shortest path, then take edge `(u, v)`.
	- Length of `P2` is &delta;(s, u) + w(u, v).
	- Since `P1` is shortest, P1 &le; P2.
	- Therefore, &delta;(s, v) &le; &delta;(s, u) + w(u, v).
- Equality case: If a shortest path from `s` to `v` ends with edge `(u, v)`, then &delta;(s, v) = &delta;(s, u) + w(u, v).
- Strict inequality case: If the best route to `v` does not go through `u`, then &delta;(s, v) &lt; &delta;(s, u) + w(u, v).
- This property is the key justification for edge relaxation in shortest-path algorithms.


## Upper Bound Property

- For every vertex `v`, the current estimate `v.d` is always an upper bound on the true shortest-path distance: v.d &ge; &delta;(s, v).
- In other words, the algorithm may overestimate the distance to `v`, but it should never underestimate it.
- This is why relaxation only improves estimates: when we relax an edge `(u, v)`, we update `v.d` only if `u.d + w(u, v)` is smaller.
- If `u.d` is already an upper bound on &delta;(s, u), then `u.d + w(u, v)` is also an upper bound on &delta;(s, v).
- So relaxation keeps distance estimates valid while moving them closer to the true shortest-path values.


## Convergence Property

- If u.d = &delta;(s, u) and (u, v) is an edge on a shortest path from `s` to `v`, then relaxing `(u, v)` makes v.d = &delta;(s, v).
- In other words, once the estimate for `u` is exact, relaxing the correct outgoing edge can make `v` exact too.
- Repeated relaxations eventually converge to the true shortest-path distances when the right edges are processed.

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/convergence.png" alt="Convergence Property" height="200" width="200" 
/>

- `u.d` stays at `3`, which matches &delta;(s, u).
- Relaxing edge `(u, v)` updates `v.d` from `12` down to `8`, which matches &delta;(s, v).



## Path Relaxation Property

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/pathrel1.png" alt="Path Relaxation Property Initial" height="200" width="400" 
/>

- v<sub>0</sub> is a source vertex
- Relax the edges from vertex v<sub>0</sub>, v<sub>1</sub>, v<sub>2</sub> in this order
- Then, v<sub>3</sub>.d will converge to shortest distance &delta;(v<sub>0</sub>, v<sub>3</sub>)

**Relax Edge From v<sub>0</sub> to v<sub>1</sub>**

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/pathrel2.png" alt="Path Relaxation Property Setp 1" height="200" width="200" 
/>

- v<sub>0</sub>.d = 0
- v<sub>1</sub>.d = &infin;
- v<sub>1</sub>.d = -1 = &delta;(v<sub>0</sub>, v<sub>1</sub>) (update)
