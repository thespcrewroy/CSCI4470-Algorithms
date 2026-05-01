# Cut

## Notes: Definition

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/cut.png" alt="Cut" height="500" />
</p>

> (a,h), (b,h), (b,c), (c,d), (d,f), (f,e) are edges crossing the cut

- A cut `(s, v - s)` of an unidrected graph `G(V, E)` is a partition of vertices `v`.
- Any edge you add accross the cut will not form a cycle
- Any edge added within a cut will form a cycle
- edge `E(u, v)` crosses the cut `(s, v - s)` if one of its endpoints is in `s` and the other end point is in `v - s`.

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/respect.png" alt="Cut Respect"  />
</p>

A cut respects a set `A` of edges if no edges in `A` crosses the cut.

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/lightedge.png" alt="Light"  />
</p>


- A light edge is the minimum weight edge out of all the edges crossing the cut.
- This edge becomes the safe edge
- Find the safe edge, add to spanning tree, and iterate

## Homework: Minimum Weight Edge

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/hw4-7.png" alt="Ligh Edge Examplet"  />
</p>